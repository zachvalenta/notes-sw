# ⛩️

## 参考

## 进步

🧠
* https://chatgpt.com/c/67472f38-4118-8004-9450-bba188df94a6
* https://claude.ai/chat/6eb1a816-587f-418a-b092-fd10f9aa9d1d
* https://claude.ai/chat/d612d9f5-c512-4d9d-8596-2d3c701e2bab

I have this rough taxonomy of serde:

DATA
* Avro
* CSV
* Parquet

IPC
* Cap'n Proto
* Protobuf
* Thrift

WIRE
* BSON
* JSON
* MessagePack

Does this seem roughly correct?

Where would Arrow fit into the serde picture of data vs. IPC vs. wire

* _24_: own doc, start to grok data/IPC/wire, first use of Parquet
* _22_: jless, start thinking about serde as its own thing

# 🏛️ COLUMNAR

```sh
Row-oriented:
record1: name,age,city
record2: name,age,city

Column-oriented:
names: [name1,name2,...]
ages:  [age1,age2,...]
cities: [city1,city2,...]
```

```python
from dataclasses import dataclass
from typing import List

# Array of Structs (Row-oriented)
@dataclass
class Person:
    name: str
    age: int
    city: str

class PeopleRowBased:
    def __init__(self):
        self.records: List[Person] = []
    
    def add(self, name: str, age: int, city: str):
        self.records.append(Person(name, age, city))
    
    def get_record(self, index: int) -> Person:
        return self.records[index]
    
    def get_ages(self) -> List[int]:
        return [person.age for person in self.records]

# Struct of Arrays (Column-oriented)
class PeopleColumnBased:
    def __init__(self):
        self.names: List[str] = []
        self.ages: List[int] = []
        self.cities: List[str] = []
    
    def add(self, name: str, age: int, city: str):
        self.names.append(name)
        self.ages.append(age)
        self.cities.append(city)
    
    def get_record(self, index: int) -> Person:
        return Person(
            self.names[index],
            self.ages[index],
            self.cities[index]
        )
    
    def get_ages(self) -> List[int]:
        return self.ages

# Usage example and performance demonstration
if __name__ == "__main__":
    import timeit
    
    # Setup data
    row_based = PeopleRowBased()
    col_based = PeopleColumnBased()
    
    for i in range(1_000_000):
        row_based.add(f"Person{i}", i % 100, f"City{i % 50}")
        col_based.add(f"Person{i}", i % 100, f"City{i % 50}")
    
    # Compare performance of column access
    row_time = timeit.timeit(lambda: row_based.get_ages(), number=100)
    col_time = timeit.timeit(lambda: col_based.get_ages(), number=100)
    
    print(f"Time to get all ages 100 times:")
    print(f"Row-based: {row_time:.4f} seconds")
    print(f"Column-based: {col_time:.4f} seconds")
```

> Earlier projects that added columnar storage to Postgres (e.g., Citus, Timescale) only solved part of the problem. Columnar data formats improve retrieving data from storage. However, a DBMS cannot fully exploit those formats if it still uses a row-oriented query processing model (e.g., Postgres). Using DuckDB provides both columnar storage and vectorized query processing. https://www.cs.cmu.edu/~pavlo/blog/2025/01/2024-databases-retrospective.html

---

already old! https://db.cs.cmu.edu/projects/future-file-formats/
📙 Kleppmann chapter 3
🗄 `computation.md` encoding/CSV, Parquet

used for time series databases

* _column store_: not row-oriented (like OLTP)
* can do in Sqlite? https://news.ycombinator.com/item?id=39207570&utm_term=comment
* 不明觉厉 https://news.ycombinator.com/item?id=36571110
* e.g. instead of looking for all `price` values by iterating over every sale record, just grab `price` column 📙 Kleppmann 96
* ❓ stores data differently on disk https://nchammas.com/writing/database-access-patterns
* in order to reconstruct a row, everything in row must be stored as nth in column 📙 Kleppmann 100
> Neither Parquet nor ORC files existed prior to 2012. These file formats were instrumental in making analytics fast on Hadoop. Prior to these formats, workloads were largely row-oriented. If you needed to transform TBs of data and could do so in a parallel fashion then Hadoop did a good job of that. MapReduce was a framework often used for this purpose. What columnar storage offered was a way to analyse TBs of data in seconds. This proved to be a more valuable proposition to more businesses. Data Scientists may only need a small amount of data to produce insights but they'll need to look over a data lake with potentially PBs of data to pick out what they need first. Columnar analytics is key for them to build the data fluency needed to know what to cherry-pick. https://tech.marksblogg.com/is-hadoop-dead.html
* _wide column store_: ❓
* CMU, Pavlo https://www.youtube.com/watch?v=fr5lIchF6pw
* vectorized execution https://talkpython.fm/episodes/transcript/491/duckdb-and-python-ducks-and-snakes-living-together

DBMS https://en.wikipedia.org/wiki/List_of_column-oriented_DBMSes
* Cassandra https://stackoverflow.com/q/13010225 https://www.youtube.com/watch?v=J-cSy5MeMOA 📙 Kleppmann 99 https://news.ycombinator.com/item?id=28292369 https://simonwillison.net/2021/Aug/24/how-discord-stores-billions-of-messages/
* _Bigtable_: wide table = document store in SQL https://en.wikipedia.org/wiki/Wide-column_store
* _HBase_: Hadoop db

## 🏹 Arrow

📜 https://arrow.apache.org/
🗄️ `protocols.md` file fmt / serialization
📹 https://www.youtube.com/watch?v=I0RtuAiBPh0

* in-memory format for columnar data https://news.ycombinator.com/item?id=29010103 https://github.com/adriangb/pgpq
> This question comes up quite often. Parquet is a _file_ format, Arrow is a language-independent _in-memory_ format. You can e.g. read a Parquet file into a typed Arrow buffer backed by shared memory, allowing code written in Java, Python, or C++ (and many more!) to read from it in a performant way (i.e. without copies). https://news.ycombinator.com/item?id=29011463
* also includes algos for querying
>  But the Arrow project contains more than just the format: The Arrow C++ library, which is accessible in Python, R, and Ruby via bindings, has additional features that allow you to compute efficiently on datasets. https://duckdb.org/2021/12/03/duck-arrow.html
* emerged from Pandas
> We needed to create a way to represent data that was not tied to a specific programming language. And that could be used for a very efficient interchange between components. And the idea is that you would have this immutable, this kind of constant data structure, which is like it's the same in every programming language. And then you can use that as the basis for writing all of your algorithms. So as long as it's arrow, you have these reusable algorithms that process arrow data. https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
> Pandas historically persisted string columns as objects, which was wildly inefficient. The new string[pyarrow] column type is around 3.5 times more efficient from what I've seen. https://news.ycombinator.com/item?id=34968769
* decoupled Pandas from numpy
> While NumPy has been good enough to make pandas the popular library it is, it was never built as a backend for dataframe libraries, and it has some important limitations. https://datapythonista.me/blog/pandas-20-and-the-arrow-revolution-part-i
* used by Polars https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
* can query using DuckDB bc Duck's  https://duckdb.org/2021/12/03/duck-arrow.html https://news.ycombinator.com/item?id=35426155

## 📐 Parquet

🗄️ `computation.md` info theory > compression

---

DESIGN https://csvbase.com/blog/3
* faster
* smaller
* typed
* columnar

ZA
* _ORC_: Parquet for Hive ecosystem https://tech.marksblogg.com/faster-csv-to-orc-conversions.html
* used by Databricks, Trino
* slower writes than Parquet, better compression

* Vortex https://news.ycombinator.com/item?id=41839773
* https://www.crunchydata.com/blog/pg_parquet-an-extension-to-connect-postgres-and-parquet
* https://r4ds.hadley.nz/arrow#sec-parquet
* partition elimination https://duckdb.org/2021/12/03/duck-arrow.html
* https://pythonspeed.com/articles/best-file-format-for-pandas/
* https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
* _Parquet_: column-oriented file format, like CSV https://www.youtube.com/watch?v=H_dLfHETO0g https://news.ycombinator.com/item?id=35418933 https://news.ycombinator.com/item?id=29010103
* easier to use now vs. CSV https://news.ycombinator.com/item?id=30595026
* use to build no-code API https://tech.marksblogg.com/roapi-rust-data-api.html
* pyarrow https://www.blog.pythonlibrary.org/2024/05/06/how-to-read-and-write-parquet-files-with-python/

# 🚣‍♀️ ROW-ORIENTED

```txt
CSV's row orientation makes it:
Great for: adding/reading full records, sequential scans
Poor for: column-based analytics, updating single fields across many records
```

## 🪶 Avro

> previous answers were talking about schema evolution but I didn't follow
> Avro really shines when you're storing large amounts of row-oriented data that needs to evolve over time. Think data warehouse rather than application data.

```txt
PARQUET
* Column-oriented
* Better for analytics (WHERE/GROUP BY on specific columns)
* Better compression (similar values grouped together)
* Excellent for data warehouse queries

AVRO
* Row-oriented
* Better for streaming/record processing
* Better for serializing/deserializing full records
* More suitable for ETL pipelines

Classic example:

* Ingest data as Avro (easy record-by-record processing)
* Land it in warehouse as Parquet (efficient querying)

Avro > Parquet:
* processing records one at a time
* need to read/write full rows frequently
* building ETL pipelines
* using Kafka (which has native Avro support)

Parquet > Avro:
* doing analytics on specific columns
* need efficient compression
* querying subsets of columns
* using tools like Athena/BigQuery
```

```txt
Stream data with Avro
Store in Parquet
Load into Arrow for processing
Pass Arrow buffers between Python/R/etc.
```

---

* https://avro.apache.org/docs/current/
* better than CSV bc handles typing, cells missing data
* CSV disadvantages: inferred data types https://www.youtube.com/watch?v=SZX9DM_gyOE 1:20
* SQL disadvantages: flat
* competes with Thrift, Protocol Buffers https://avro.apache.org/docs/current/
* Python tutorial https://avro.apache.org/docs/current/gettingstartedpython.html
* https://www.youtube.com/watch?v=kq_JCVcHJLE

## 🟢 CSV

🗄️ `analytics.md` visidata

TOOLS
```sh
python -c "import random; print('\n'.join(str(random.randint(10, 99)) if random.random() > 0.2 else str(random.randint(100, 999)) for _ in range(20)))"
```
* _moderncsv_: editor https://www.moderncsv.com/ 🗄️ `data/analytics.md` visidata
* _csvdiff_: ✅ diff https://github.com/aswinkarthik/csvdiff
* _csview_: ✅ cat https://github.com/wfxr/csview
* _csvlens_: ✅ less/pager https://github.com/YS-L/csvlens https://news.ycombinator.com/item?id=38889820
* _tabiew_: cat https://github.com/shshemi/tabiew

QUERY
* _csvq_: https://github.com/mithrandie/csvq
* _qsv_: https://github.com/jqnatividad/qsv
* _sq_: query with SQL https://github.com/neilotoole/sq
* _textql_: query with SQL https://github.com/dinedal/textql

SEMANTICS
* _header line_: line with col names https://miller.readthedocs.io/en/latest/glossary/#header-line
* header not always first line, detection non-trivial https://news.ycombinator.com/item?id=28299015
* _data line_: line with data https://miller.readthedocs.io/en/latest/customization/
* _field_: value, either in header line or data line https://miller.readthedocs.io/en/latest/10min/#handling-field-names-with-spaces

DESIGN
* no firm spec https://peps.python.org/pep-0305/#abstract
* better for streaming bc each line of file is valid CSV (unlike JSON) https://jfhr.me/consider-using-csv/
* gaining in popularity https://twobithistory.org/2017/09/21/the-rise-and-rise-of-json.html#fnref:2 
* some parsers don't impl escaping rules correctly 📙 Kleppmann 4.145
* comments: no standard from RFC 4180, parser can set https://stackoverflow.com/a/14428538 https://stackoverflow.com/a/1961018
* newline / carriage return https://github.com/saulpw/visidata/issues/387
* _DSV_: same as `.dat` https://en.wikipedia.org/wiki/Delimiter-separated_values https://www.thoughtspot.com/blog/csv-vs-delimited-flat-files-how-choose
* _TSV_: https://news.ycombinator.com/item?id=40622760

CONVERSION 🧠 https://claude.ai/chat/a054673f-3567-4e7c-bac6-3441cc692f47
* _csvkit_: install broken via pyenv https://github.com/zachvalenta/logs-capp/blob/main/pyenv/pipx/csvkit.log#L36 https://github.com/wireservice/csvkit https://csvkit.readthedocs.io/en/latest/
```sh
in2csv $EXCEL > $CSV
```
* _visidata_: broken (didn't work for Capp interview, query-sandbox)
* bc...pyenv issue? `vd` not callable? https://github.com/saulpw/visidata/issues/1406 `sh: /Users/zach/.local/bin/vd: bad interpreter: /Users/zach/Library/Application: no such file or directory`

# 👋 IPC

💡 optimized for serialization speed
🔗 https://en.wikipedia.org/wiki/Inter-process_communication

## Capn Proto

---

* _Capn Proto_: https://capnproto.org/
* sustainable? https://github.com/capnproto/capnproto/issues/2067

## protobuf

🗄️ `api.md` RPC
🧠 https://chatgpt.com/c/673cf346-ae54-8004-84c2-fd989e922c51

* _wireman_: client https://github.com/preiter93/wireman

---

* beware https://news.ycombinator.com/item?id=42799245
* convert/query https://github.com/dflemstr/rq
* like BSON https://bsonspec.org/ https://github.com/bufbuild/buf
* https://vincent.bernat.ch/en/blog/2023-dynamic-protobuf-golang
* https://news.ycombinator.com/item?id=36798824
* curl for https://github.com/qaware/protocurl https://news.ycombinator.com/item?id=34866155
* compared to docarray, JSON https://docarray.jina.ai/get-started/what-is/#comparing-to-alternatives
* features that JSON doesn't have like versioning, types 📙 Jeffrey distributed [5]
* in Python https://www.fluentpython.com/extra/parsing-binary-struct/ https://www.blog.pythonlibrary.org/2023/08/30/an-intro-to-protocol-buffers-with-python/

## Thrift

📜 https://thrift.apache.org/

# 🛜 WIRE

💡 optimized for readability|compactness
🗄 `python/stdlib.md` serde

* _serialize_: convert obj to interchange fmt
* _deserialize_: convert interchange fmt to obj
* _schema_: mapping of obj to interchange fmt structure
* you typically want to specify
> Pickles are implicit: they serialize everything in your objects, even data you didn’t want to serialize. For example, you might have an attribute that is a cache of computation that you don’t want serialized. Pickle doesn’t have a convenient way to skip that attribute. https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html

## BSON

---

> ❓ how is BSON more binary than JSON itself? https://stackoverflow.com/questions/3554325/why-is-it-called-bson 📙 Kleppmann ch. 4
* e.g. HTTP/2 https://news.ycombinator.com/item?id=27431998
* db res in binary which is parsed by language-specific API 📙 Kleppmann 4.128
📙 Kleppmann 4.117, 4.122, 4.130
* _BSON_: binary JSON + SQL datatypes https://bsonspec.org/
* can be less space efficient due to datatypes https://en.wikipedia.org/wiki/BSON#Efficiency
* faster to parse https://bsonspec.org/faq.html
* datatypes: JSON + date, binary, num (int, long, float) https://youtu.be/SM9gJv08dm0 2:25

## MessagePack

📜 https://msgpack.org/
📙 Kleppmann [4.116]

FEATURES
* drop-in replacement for JSON (same data types)
> MessagePack structured communication enables extensions in any language. https://neovim.io/
* binary = optimized for compactness
* no schema validation

USAGE
* high-throughput message queues
* time series data
* video game state sync
* Neovim

## 🟡 JSON

🛠 https://github.com/burningtree/awesome-json
🗄️
* `algos.md` tree
* `dbms.md` JSON
* `python/stdlib.md` serde
* `telemetry.md` logging

OPERATIONS
* fmt: `python3 -m json.tool music-lib.json > music-lib-fmt.json` https://orbifold.xyz/check-in-json.html
* to SQL https://github.com/simonw/claude-to-sqlite
* _csv-diff_: diff https://github.com/simonw/csv-diff
* _dasel_: edit https://github.com/TomWright/dasel
* _jo_: ✅ generate https://github.com/jpmens/jo
> just use Python https://news.ycombinator.com/item?id=30224063
* _graphtage_: ❌ diff https://github.com/trailofbits/graphtage broken https://github.com/trailofbits/graphtage/issues/91 🗄️ `shell.md` file / diff

### design

📜 http://www.json.org/
🗄️ `telemetry.md` logging / JSONL

* basic
```json
{"a": "b"}

{
    "topLevel": "val",
    "myList": [1,2,3],
    "topObj": {
        "foo": false
    }
}
```

NUMBERS
* types: int, floating point, exponential notation
* use strings to represent monetary amounts
* use strings for big ints
* no leading zeros
* largest safe int `2^53 - 1` (`9007199254740991`) 📜 IEEE-754 double-precision floating-point

ZA
* benefits: readable, tooling, mindshare 📙 Jeffrey distributed [4]
* line-oriented datasets (ndjson, JSON Lines)? https://github.com/asg017/sqlite-lines

---

* https://seriot.ch/projects/parsing_json.html
* objs: colloquially (start/end w/ braces) https://youtu.be/SM9gJv08dm0 0:30 literally (doesn't exist) http://benalman.com/news/2010/03/theres-no-such-thing-as-a-json/
* typing: str, bool, array, num (int/float considered the same, which can be problem w/ large numbers) 📙 Kleppmann [144]
* no comments https://stackoverflow.com/a/4183018
* no binary strings 📙 Kleppmann [144]
* history https://twobithistory.org/2017/09/21/the-rise-and-rise-of-json.html
* as output for Unix utils https://blog.kellybrazil.com/2019/11/26/bringing-the-unix-philosophy-to-the-21st-century/ https://github.com/kellyjonbrazil/jc https://news.ycombinator.com/item?id=22608045 https://kellyjonbrazil.github.io/jc/
* for sharing logic btw frontend/backend https://news.ycombinator.com/item?id=27306263

### in databases

---

https://eradman.com/posts/json-in-sql.html
https://news.ycombinator.com/item?id=41914845

SQLITE
* https://dba.stackexchange.com/questions/122198/is-it-possible-to-store-and-query-json-in-sqlite
* https://news.ycombinator.com/item?id=30486052

POSTGRES
* write rows as JSON obj to file
```sql
SELECT foo.x, bar.y, baz.z
SELECT json_agg(json_build_object('x', foo.x, 'y', bar.y, 'z', baz.z))

-- write stdout to file (only seemed to work for psql, not pgcli)
\o output.json  -- start
\o  -- stop
```
* write IDs as quoted, delimited string to text file
```sql
\o artist-ids.txt
SELECT '"' || foo.x || '",'
\o
```
* `json`: text field; slow to search
* `jsonb`: binary; slower writes, faster reads https://pganalyze.com/blog/postgres-jsonb-django-python
```sql
-- all keys for json obj
select jsonb_object_keys(json_col) from table
-- nested key
select json_col -> 'top_level_key' ->> 'nested_key' from table
```

### query (jq)

ALTERNATIVES
* SQLite CLI
* DuckDB https://www.pgrs.net/2024/03/21/duckdb-as-the-new-jq/ https://news.ycombinator.com/item?id=35009612 https://duckdb.org/2023/03/03/json.html 
* in Python! https://github.com/jmespath/jmespath.py
* _jaq_: rewrite https://github.com/01mf02/jaq
* _jello_: 🎯 Python syntax https://github.com/kellyjonbrazil/jello https://github.com/kellyjonbrazil/jellex
* _jmespath_: https://github.com/jmespath/jp https://github.com/birchb1024/frangipanni/blob/cf997721e2c5793e062d1c16908d7ddf2a325173/frangipanni.go
* _jnv_: 🎯 interactive https://github.com/ynqa/jnv
* _jqp_: TUI https://github.com/noahgorstein/jqp 
* _jsonata_: https://jsonata.org/ https://www.stedi.com/blog/jsonata-playground
* _qq_: ⭐️ https://github.com/JFryy/qq/
* _mistql_: Python and CLI https://www.mistql.com/
* _sq_: https://news.ycombinator.com/item?id=41760697

JQ 📜 https://stedolan.github.io/jq/manual 
* intro https://earthly.dev/blog/jq-select/
* guide https://sequoia.makes.software/parsing-json-at-the-cli-a-practical-introduction-to-jq-and-more
```sh
# test dats
curl https://api.github.com/repos/stedolan/jq/issues?per_page=5 | jq
cat foo.json | jq

jq .  # pretty print
jq -r  # unquoted/raw output https://stackoverflow.com/a/44656583
jq '.[4]'  # get el in array
jq ' .key.subkey'  # get key
jq '.[4].title'  # get key from el in array
jq '.[].title'  # get key from every el in array
jq '.title'  # get key from streams of obj
jq '.[].reactions|select(.total_count>8)'  # filter
jq '.[]|select(.num_receipts>0)|select(.is_migrated == true)|.artist_id'  # filter
```

### view (jless)

💡 drilldown as a general category (fs, JSON, trees) https://github.com/xgi/castero

JLESS 📜 https://jless.io/
* theme https://github.com/PaulJuliusMartinez/jless/issues/4
* commands
```sh
# GOTO
H    # parent
g    # top
gg   # bottom

# NAV
j/k  # scroll children
J/K  # scroll parents
CTRL d/u  # page

# DISPLAY
space | h/l  # collapse/expand
c  # collapse all
pp  ## print
zz  # center
```

---

* https://github.com/fioncat/otree
* https://github.com/gulyasm/jsonui
* _JSON Viewer_: browser syntax highlighting https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh
* _JSON crack_: visualize https://github.com/AykutSarac/jsoncrack.com https://jsoncrack.com/
* _json4u_: jsoncrack clone https://news.ycombinator.com/item?id=41634356
