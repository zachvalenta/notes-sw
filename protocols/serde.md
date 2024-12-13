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

# 💿 DATA

💡 optimized for storage and queries

## Avro

> Avro really shines when you're storing large amounts of row-oriented data that needs to evolve over time. Think data warehouse rather than application data.

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

### conversion

---

https://claude.ai/chat/a054673f-3567-4e7c-bac6-3441cc692f47

CSVKIT 📜 https://github.com/wireservice/csvkit https://csvkit.readthedocs.io/en/latest/
* install broken via pyenv https://github.com/zachvalenta/logs-capp/blob/main/pyenv/pipx/csvkit.log#L36
```sh
in2csv $EXCEL > $CSV
```

BROKEN FILE CONVERSION 🚧 file conversion doesn't work
* using csvkit instead 🗄️ query-sandbox, capp
* cause: `vd` not being callable? https://github.com/saulpw/visidata/issues/1406 `sh: /Users/zach/.local/bin/vd: bad interpreter: /Users/zach/Library/Application: no such file or directory`
* cause: pyenv issue
```sh
$ vd foo.xlsx -b -o foo.csv

saul.pw/VisiData v3.0.2
opening foo.xlsx as xlsx
I wonder what they'll do next!
saving 1 sheets to foo.csv as csv
```
```sh
$ cat foo.csv
```
```csv
sheet,nRows,nCols,active
Cateogry_Updates,1,2,True
Sheet1,1048575,5,False
Sheet2,1048575,2,False
```

## 📐 Parquet

🗄️ `computation.md` info theory > compression

---

DESIGN https://csvbase.com/blog/3
* faster
* smaller
* typed
* columnar

ZA
* _ORC_: Parquet for Hive ecosystem

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

---

* https://seriot.ch/projects/parsing_json.html
* objs: colloquially (start/end w/ braces) https://youtu.be/SM9gJv08dm0 0:30 literally (doesn't exist) http://benalman.com/news/2010/03/theres-no-such-thing-as-a-json/
* typing: str, bool, array, num (int/float considered the same, which can be problem w/ large numbers) 📙 Kleppmann [144]
* no comments https://stackoverflow.com/a/4183018
* no binary strings 📙 Kleppmann [144]
* history https://twobithistory.org/2017/09/21/the-rise-and-rise-of-json.html
* as output for Unix utils https://blog.kellybrazil.com/2019/11/26/bringing-the-unix-philosophy-to-the-21st-century/ https://github.com/kellyjonbrazil/jc https://news.ycombinator.com/item?id=22608045 https://kellyjonbrazil.github.io/jc/
* for sharing logic btw frontend/backend https://news.ycombinator.com/item?id=27306263

### query (jq)

ALTERNATIVES
* SQLite CLI
* DuckDB https://www.pgrs.net/2024/03/21/duckdb-as-the-new-jq/ https://news.ycombinator.com/item?id=35009612 https://duckdb.org/2023/03/03/json.html 
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
