# ⛩️

## 参考

🛣️ https://roadmap.sh/data-analyst
> A number of companies (large crossover funds, startups, etc.) in The Diff network are looking for data scientists that love wrangling and analyzing alt. data to help inform investment decisions. (Remote) https://www.thediff.co/archive/longreads-open-thread-96/
🗄
* `protocols.md` file fmt
* `telemetry.md` analytics
📚
* Khalil https://www.manning.com/books/effective-data-analysis
* Massaron https://www.manning.com/books/advanced-analytics-for-business https://www.youtube.com/watch?v=scY7PTxNSr4
* Wickham https://r4ds.hadley.nz/

## 进步

# 🧮 DATAFRAMES

🗄️
* `eng.md` pipeline > test
* `sql.md` design

TOOLING
* compare https://github.com/capitalone/datacompy https://www.thoughtworks.com/radar/languages-and-frameworks/datacompy
* visualize https://github.com/man-group/dtale
* diff https://www.youtube.com/watch?v=5Rc9xkeHth0
* GPU acceleration https://www.youtube.com/watch?v=86nMARKN7ho https://www.youtube.com/watch?v=Aumh3evLSKc https://www.youtube.com/watch?v=PH7ExhXYkxQ

ZA
* _dataframe_: result set + operations https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://github.com/go-gota/gota/blob/master/dataframe/dataframe.go

---

design https://news.ycombinator.com/item?id=42193043 https://www.youtube.com/watch?v=cgWHPTx0wjw
Dask dataframe https://www.youtube.com/watch?v=bbtK3aCQ3C0
https://calpaterson.com/bank-python.html
https://tibble.tidyverse.org/
https://dplyr.tidyverse.org/ https://calmcode.io/course/dplyr-verbs/introduction

📚
* McKinney https://wesmckinney.com/book/
* VanderPlas https://jakevdp.github.io/PythonDataScienceHandbook/

ZA
* tables https://posit-dev.github.io/great-tables
* Dataframe Interchange Protocol, Dataframe API Standard https://ponder.io/how-the-python-dataframe-interchange-protocol-makes-life-better/ https://ponder.io/why-are-there-so-many-python-dataframes/ https://pythonspeed.com/articles/polars-pandas-interopability/

## 🏹 Arrow

📜 https://arrow.apache.org/
🗄️ `protocols.md` file fmt / serialization
📹 https://www.youtube.com/watch?v=I0RtuAiBPh0

* in-memory format for columnar data https://news.ycombinator.com/item?id=29010103 https://github.com/adriangb/pgpq
> This question comes up quite often. Parquet is a _file_ format, Arrow is a language-independent _in-memory_ format. You can e.g. read a parquet file into a typed Arrow buffer backed by shared memory, allowing code written in Java, Python, or C++ (and many more!) to read from it in a performant way (i.e. without copies). https://news.ycombinator.com/item?id=29010103
* also includes algos for querying
>  But the Arrow project contains more than just the format: The Arrow C++ library, which is accessible in Python, R, and Ruby via bindings, has additional features that allow you to compute efficiently on datasets. https://duckdb.org/2021/12/03/duck-arrow.html
* emerged from Pandas
> We needed to create a way to represent data that was not tied to a specific programming language. And that could be used for a very efficient interchange between components. And the idea is that you would have this immutable, this kind of constant data structure, which is like it's the same in every programming language. And then you can use that as the basis for writing all of your algorithms. So as long as it's arrow, you have these reusable algorithms that process arrow data. https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
> Pandas historically persisted string columns as objects, which was wildly inefficient. The new string[pyarrow] column type is around 3.5 times more efficient from what I've seen. https://news.ycombinator.com/item?id=34968769
* decoupled Pandas from numpy
> While NumPy has been good enough to make pandas the popular library it is, it was never built as a backend for dataframe libraries, and it has some important limitations. https://datapythonista.me/blog/pandas-20-and-the-arrow-revolution-part-i
* used by Polars https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
* can query using DuckDB bc Duck's  https://duckdb.org/2021/12/03/duck-arrow.html https://news.ycombinator.com/item?id=35426155

## 🦢 Ibis

📜 https://ibis-project.org/

to Jack 24.12.10 https://www.youtube.com/watch?v=8MJE3wLuFXU
> different semantics/interface than Pandas though so would assume - maybe even for simple stuff - you're not porting from Pandas but rather rewriting
> one way around the pandas/polars interop problem (and others like it) https://ibis-project.org/
> relatively new-ish but from the guy who wrote Pandas (Wes McKinney)
> SQL is the longest lasting thing that still gets used for new projects (sorry, C) but it's kinda like Bash in that it's ugly/verbose to read and harder to write than ORM/dataframe code. tons of SQL out in the world so great use case for LLMs (like regex) but Ibis a great compromise, SQL becomes akin to compiler output, you can always dig into the assembly if need be [yes, compilers output bytecode, IR, etc.] but in most cases you're can happily plug away in a much better DSL. https://www.scattered-thoughts.net/writing/against-sql

* dataframe API
* https://calmcode.io/course/ibis/introduction
* transpiles to SQL i.e. works with SQL-based query engines (BigQuery, Clickhouse, Postgres, Snowflake) https://realpython.com/podcasts/rpp/201/
* compiles to Python i. e https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
* dataframe API that can use Polars/Pandas query engine or transpile to SQL and run against relational dbms https://talkpython.fm/episodes/show/462/pandas-and-beyond-with-wes-mckinney
* https://www.youtube.com/watch?v=C4aUG9poN6E https://us.pycon.org/2024/schedule/presentation/55/index.html

## 🐋 Narwhals

---

> First up: we are completely rewriting how our Plotly.py library talks to dataframes in the 6.0 release. Instead of relying on the Pandas API, we are using Narwhals which provides an abstraction layer over several kinds of tabular data. This means faster, more efficient handling of tabular data and serious performance gains for data apps at scale. You'll notice with this change that Plotly.py no longer has to do in-memory copying when you hand it something like a Polars dataframe. https://plotly.com/blog/plotly-dash-major-release/
* _Narwhal_: API for dataframes https://pythonbytes.fm/episodes/show/402/how-to-monetize-your-blog https://realpython.com/podcasts/rpp/224/ https://github.com/benrutter/wimsey
> Chances are, you’ve never heard of Narwhals. That’s because it’s a tool targeted at tool builders, rather than at end users. Specifically, it allows library maintainers to support multiple dataframe libraries as inputs, without having to make any of them required. https://pola.rs/posts/lightweight_plotting/

## Pandas

> 📍 https://github.com/lux-org/lux
📜 https://pandas.pydata.org/docs/
📙 McKinney data analysis https://wesmckinney.com/book/
🔍 howto https://github.com/jvns/pandas-cookbook https://github.com/kxzk/an-embarrassment-of-pandas https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf
📹 guide https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS

SEMANTICS
* _series_: a column, all rows from a single column https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://pandas.pydata.org/docs/user_guide/10min.html#getting
* `name`: series header
* _index_: row number https://realpython.com/pandas-reset-index/

BASICS
```python
# LOAD
import pandas as pd
df = pd.DataFrame(pd.read_csv($FILE))

# SELECT
df.col   # get col https://pandas.pydata.org/docs/user_guide/10min.html#getting
df[0:3]  # get row
df.col.isin(myl) # bool for each row
df.index[df.col.isin(myl)] # row index for True bool
df.drop(df.index[df.col.isin(myl)]) # drop row indexes for rows matching list el
df.columns # all col
df[["col1", "col2"]] # n col
df.iloc[3] # get row by row index
df.iloc[3, 17] # get row by row index + col index e.g. row 3 col 17
df.iloc[[3, 42]] # get n row by row index e.g. rows 3 and 42
```

---

DESIGN
> Pandas was originally written to replace excel in financial/econometric modeling, not as a replacement for SQL. https://news.ycombinator.com/item?id=35429555
* https://web.archive.org/web/20230127194856/https://scribe.citizen4.eu/pandas-illustrated-the-definitive-visual-guide-to-pandas-c31fa921a43
* perf https://hakibenita.com/sql-for-data-analysis#sql-vs-pandas-performance https://pythonspeed.com/memory https://realpython.com/fast-flexible-pandas
* style: method chaining https://github.com/pyjanitor-devs/pyjanitor
* impl: built on NumPy arrays i.e. core operations carried out in C https://en.wikipedia.org/wiki/Pandas_(software) https://realpython.com/fast-flexible-pandas/#but-i-heard-that-pandas-is-slow

---

```python
# ITERATION https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas https://stackoverflow.com/questions/50267185/iterate-over-pandas-series don't iterate https://realpython.com/pandas-iterate-over-rows/
for series in df.iterrows():

# PREDICATE
df[df["company"] == "ABC corp"]  # equality
df[df["earnings"] > 0]  # comparison
df[(df["col1"] >= 1) & (df["col1"] <=1 )]  # uses indexing https://stackoverflow.com/a/13616382

# GROUPING 📙 McKinney [291]
for gk, grp in df.groupby("isrc"):

# CSV PER GROUP https://stackoverflow.com/a/50818244
df = pd.DataFrame(pd.read_csv("paintings.csv"))
path = os.path.join(os.getcwd(), "output_dir")
for i, (name, group) in enumerate(df.groupby("ARTIST")):
    group.to_csv("{}/{}.csv".format(path, name.replace(" ", "").lower()))

# VERIFY TOTALS PER GROUP
invalid = list()
for _, (foo, group) in enumerate(df.groupby("foo")):
    if int(group["bar"].sum()) != 100:
        invalid.append(foo)
log.info("foo count - invalid: {}".format(len(invalid)))

myl = [foo, bar]

# SHAPE https://stackoverflow.com/a/35523946
df.shape[0]  # count rows
df.shape[1]  # count col

# PERSIST FOO W/ VALID BAR
verified = df.drop(df.index[df.foo.isin(invalid)])
log.info("count - verified: {}".format(len(set(verified.foo))))
verified.to_csv(os.path.join(os.getcwd(), out_file))
```

# 🐻‍❄️ POLARS

📜 https://docs.pola.rs/ https://docs.pola.rs/api/python/stable/reference/index.html
📙 https://realpython.com/polars-python/

## design

---

BIG PICTURE
* query engine with dataframe frontend https://pola.rs/posts/polars_birds_eye_view/ https://blog.jetbrains.com/pycharm/2024/07/polars-vs-pandas/
* compared to Pandas: query optimization, group by https://labs.quansight.org/blog/dataframe-group-by https://pola.rs/posts/benchmarks/
* https://www.youtube.com/watch?v=q3o2IdFQTOE
* https://news.ycombinator.com/item?id=35429555
* better semantics than Pandas? https://arilamstein.com/blog/2024/09/04/why-im-switching-to-polars/
* https://calmcode.io/course/polars/introduction
* https://calmcode.io/course/pandas-pipe/introduction

INTEROP
* converting Pandas to Polars https://www.youtube.com/watch?v=B2Ljp2Fb-l0
* can use some Pandas libraries https://pythonspeed.com/articles/polars-pandas-interopability/

PRO / CON
* better than Pandas: query in Python or SQL, no dependencies, sensible pip install (vs. conda) https://github.com/pola-rs/polars better perf https://pola.rs/posts/benchmarks/ less memory usage https://pythonspeed.com/articles/polars-memory-pandas/
* worse than Pandas: not meant for Excel-like operations
> Pandas was originally written to replace excel in financial/econometric modeling, not as a replacement for sql. Models written solely in the long relational style are near unmaintainable for constantly evolving models with hundreds of data sources and thousands of interactions being developed and tuned by teams of analysts and engineers. https://news.ycombinator.com/item?id=35429555

ZA
* Deltabase, DeltaDB https://github.com/uname-n/deltabase https://pythonbytes.fm/episodes/show/397/so-many-pycon-videos
* plotting https://pola.rs/posts/lightweight_plotting/ https://realpython.com/python-news-october-2024/
> couldn't get this to work; try `pipx inject`

## IO

```python
# read_csv faster when you can skip entire columns and save on overhead of setting up query plan
df = pl.read_csv(file, columns=['col1', 'col2'])

# scan_csv creates lazy df = build up ops before actually loading data = Polars can optimize query plan rather than executing ops sequentially 🗄️ `data/internals.md` query engine > query plan
df = pl.scan_csv(file)
   .filter(pl.col('col1') > 0)
   .select(['col1', 'col2'])
   .groupby('col1').agg(pl.col('col2').mean())
   .collect()

# stream for lower memory consumption 🗄️ `architecture.md`
for chunk in pl.read_csv("data.csv", rechunk=True).iter_chunks(size=10000):
    process_chunk(chunk)

# PRNG for reproducible sample 🗄️ `algos.md`
pl.scan_parquet("data.parquet").sample(n=1000, seed=42).collect()

# working around non-standard data
pl.read_csv(
    filepath,
    separator='\t',
    encoding='latin-1',
    skip_rows=42,
    ignore_errors=True,
    infer_schema_length=None,
    quote_char=None,
    truncate_ragged_lines=True,
)

# MALFORMATTED COLUMN HEADERS
no_whitespace_or_period_delimit = r"^[^\s.-]+$"
violations = [col for col in df.columns if bool(re.match(no_whitespace_or_period_delimit, col)) is False]
assert len(violations) > 0
```

## EDA

```python
df.columns
df.schema
df.schema.keys()
col_series = df["column_name"]
col_list = df["column_name"].to_list()

first_values = df["column_name"].head(5)
unique_values = df["column_name"].unique()

# empty columns
null_col_df = [col for col in df.columns if df[col].null_count() == df.height]
assert bool(null_col_df) is True
# null columns
df.filter(pl.col(COL).is_null())
# value not present in column
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == 0
# value present in every column record
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == lines_set.height
```

## predicates

```python
# equality
bar.filter(pl.col('mfg') == 'samsung')
# comparison
bar.filter(pl.col('price') > 300)
# chained
bar.filter((pl.col('mfg') == 'samsung') & (pl.col('price') > 400))
# keyword search
bar.filter(pl.col('mfg').str.contains('pp').alias('regex'))
```

## joins

---

```python
# basic
foo.join(bar, left_on="id", right_on="mpn")

# predicate
foo.join(bar, left_on="id", right_on="mpn").filter(pl.col("foo_price") != pl.col("bar_price"))
foo.join(bar, left_on="id", right_on="mpn").filter(pl.col("manufacturer").is_in(["apple", "motorola"]))

# relative complement
bar.join(foo, left_on="mpn", right_on="id", how="anti")
```

---

🗄️ startup.py https://github.com/zachvalenta/capp-crud

```python
foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc")
foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc").select(["sku", "bar_upc", "foo_price", "bar_price"])

joined = foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc")
joined.select(joined.columns[0], joined.columns[-1], *joined.columns[1:-1])

select([
    "name",  # specify your desired column order
    "age",
    "id"
])

foo.join(df2, on="id").filter(pl.col("price") != pl.col("Sell Price"))
```

JOINS
```python
# BASIC
joined = capp.join(neuco, on="id", how="left")  # JK same name
joined = df1.join(df2, left_on="Part_ID", right_on="part_id")  # JK dif name

# RECONCILIATION
# 📍 update this to show what the price is
df1 = pl.DataFrame({"id": [1, 2, 3], "price": [100.0, 200.0, 300.0]})
df2 = pl.DataFrame({"id": [1, 2, 3], "price": [100.0, 250.0, 300.0]})
df1.join(df2, on="id").filter(pl.col("price") != pl.col("Sell Price"))

missing_records = capp.join(
    neuco,
    left_on=["Part_ID", "Product Item"],  # Join on both keys
    right_on=["part_id", "product_item"],
    how="left"
)

# only keeps join key from the driving table (as least in output)
df1 = pl.DataFrame({"Part_ID": [1, 2, 3], "name": ["a", "b", "c"]})
df2 = pl.DataFrame({"part_id": [1, 2, 4], "value": [10, 20, 30]})
joined = df1.join(df2, left_on="Part_ID", right_on="part_id")
# need to alias join key from through table to see it in output
joined = df1.join(df2.with_columns(pl.col("part_id").alias("df2_part_id")), left_on="Part_ID", right_on="part_id")

# trying to make it more clear in a join which attr belong to which table
df1_tagged = df1.select([pl.all().prefix("table1_")])
df2_tagged = df2.select([pl.all().prefix("table2_")])
joined = df1_tagged.join(df2_tagged, left_on="table1_Part_ID", right_on="table2_Part_ID") # adjust join key names to match prefixed names
```

# 🛠️ TOOLING

🗄️ `protocols.md` file fmt

SQL FROM SHELL
* _dsq_: https://github.com/multiprocessio/dsq
* _q_: https://github.com/harelba/q
* _sq_ https://github.com/neilotoole/sq https://news.ycombinator.com/item?id=41760697 

CONVERSION / GENERATION
* tabular to JSON https://github.com/jazzband/tablib
* JSON to tabular https://duckduckgo.com/?q=json+to+pandas&ia=web
* https://hakibenita.com/sql-for-data-analysis#generating-data
* import from 3rd party: Dogsheep https://datasette.substack.com/p/dogsheep-personal-analytics-with
* Visidata
* Posgres https://news.ycombinator.com/item?id=24189582
* https://github.com/simonw/sqlite-utils
```sh
# https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 20:25
curl www.api.com | jq foo | sqlite-utils insert foo.db bar_table
```

LINTING
* https://github.com/alanmcruickshank/sqlfluff https://www.thoughtworks.com/radar/tools?blipid=202203065
* https://www.eversql.com/sql-syntax-check-validator/
* https://github.com/purcell/sqlint
* https://github.com/darold/pgFormatter
* https://sqlfum.pt/

## BI (dash)

🗄
* `architecture.md` no code, baked data
* `doc.md` viz > chart
* `math.md` stat / distributions
* `python/feedback.md` notebooks

> Analysis, even SQL-based analysis, isn't like design, where a handful of people create stuff and everyone else is a consumer, with clear lines between them. It's much, much fuzzier. Though analysts were always our first adopters, lots of people - PMs, engineers, marketing managers, executives, support agents, operations leads, and all job titles in between - periodically wrote queries. These people occupied the middle part of the distribution between analysts and non-analysts that we thought would be vacant. Users weren't bimodal like we expected, but continuous. https://benn.substack.com/p/work-like-an-analyst

DASH https://dash.plotly.com/ https://www.youtube.com/watch?v=GW95sNvygDE 💻 https://github.com/zachvalenta/capp-dasher
* tables https://genderpaygap.pythonanywhere.com/ https://dash-example-index.herokuapp.com/grid https://dash.plotly.com/datatable https://chatgpt.com/c/6749d1ba-9d0c-8004-a11f-bf5a0ba55f1c
* _callback_: update chart https://dash.plotly.com/tutorial#controls-and-callbacks
* _control_: hit callback
* _Dash Design Kit (DDK)_: no need for HTML/CSS

---

CANDIDATES FOR CAPP https://chatgpt.com/c/674796f6-286c-8004-b0d5-6ae4d0decccc
* https://github.com/finos/perspective https://perspective.finos.org/
* https://github.com/datasette/datasette-queries
* Metabase

* Claude data analysis tool
* AI / plain English https://news.ycombinator.com/item?id=41907719

* _business intelligence (BI)_: explorer (for non-devs) + graphs
* SQL-by-mouse https://briefer.cloud/blog/posts/self-serve-bi-myth/

TOOLS / DASHBOARDS
* RAG https://github.com/vanna-ai/vanna
* _Blazer_: https://github.com/ankane/blazer
* _Briefer_: https://github.com/briefercloud/briefer https://pythonbytes.fm/episodes/show/405/oh-really
* _Dataherald_: query using natural language via LLM https://github.com/Dataherald/dataherald
* _Datalens_: 🎯 run locally https://datalens.tech/ https://news.ycombinator.com/item?id=37657772
* _Evidence_: borked VS Code outliner https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=37663111 https://news.ycombinator.com/item?id=37661872
* _Hex_: https://hex.tech/ https://retool.com/blog/top-sql-guis-for-your-data-warehouse-snowflake-bigquery-redshift
* _Lightdash_: Kubernetes https://github.com/lightdash/lightdash
* _Looker_: Looker Studio is the free dashboard component
> Everything builds on top of Looker. Looker Studio is a way to access and build reports on that trusted, underlying data model. https://www.cobry.co.uk/looker-vs-looker-studio
* _Kviklet_: queries + perms https://github.com/kviklet/kviklet
* _Metabase_: 🎯 popular https://news.ycombinator.com/item?id=30323131 https://retool.com/blog/top-sql-guis-for-your-data-warehouse-snowflake-bigquery-redshift https://news.ycombinator.com/item?id=37661872
* _Poli_: local, Java https://github.com/shzlw/poli
* _PyGWalker_: https://github.com/Kanaries/pygwalker
* _Quary_: VS Code extension https://github.com/quarylabs/quary
* _Redash_: cloud deploy https://github.com/getredash/redash
* _Retool_: 🎯 https://retool.com/blog/how-to-build-a-sql-gui
* _Tableau_: via Pandas https://github.com/Kanaries/pygwalker Markdown https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=39519145
* _Shiny_: https://training.talkpython.fm/courses/reactive-web-dashboards-with-shiny-for-data-science https://www.maximum-progress.com/p/economics-is-a-field-of-software
* _SQL Explorer_: 🎯 https://github.com/explorerhq/django-sql-explorer
> Write SQL, share results, do some analysis, get insight. No surprises. https://news.ycombinator.com/item?id=40857589
* _Superset_: 🎯 popular https://news.ycombinator.com/item?id=37657772 https://github.com/apache/superset https://news.ycombinator.com/item?id=37661872
* _Taipy_: https://github.com/Avaiga/taipy

## entry (dataclerk)

🧠 Django-based? https://chatgpt.com/c/673b721c-4174-8004-8973-6e0ccc5bad2c

---

* https://tomcritchlow.com/2023/01/27/small-databases/
* https://realpython.com/contact-book-python-textual/
* Airtable?
* schema introspection https://highgrowthengineering.substack.com/p/why-is-dbt-so-important-
* https://github.com/centerofci/mathesar 🗄 dataclerk
* repos that need: golf, bookcase

TAXONOMY
* _personal data warehouse_: generated personal data https://simonwillison.net/2020/Nov/14/personal-data-warehouses/
* these always seem like a waste of time https://krausefx.com//blog/how-i-put-my-whole-life-into-a-single-database
* _personal database_: hand curated https://tomcritchlow.com/2022/01/26/electric-tables/ https://bofh.org.uk/2019/02/25/baking-with-emacs/

STATUS QUO
* user: web app
* admin: script/proc, visidata, GUI https://realpython.com/python-contact-book/#step-5-creating-new-contacts
* back office: ask admin, use Basedash https://softwareengineeringdaily.com/2020/10/12/basedash-low-code-database-editor-with-max-musing/ https://www.basedash.com/

IMPL
* check out the help section of pgcli, pgcli can now autocomplete joins?
* https://github.com/k1LoW/tbls
* parser https://news.ycombinator.com/item?id=32560039
* visidata for now and add constraints later?
* https://github.com/szktkfm/mdtt
* https://stackoverflow.com/questions/2732356/list-of-all-tables-with-a-relationship-to-a-given-table-or-view
* https://stackoverflow.com/questions/8094156/know-relationships-between-all-the-tables-of-database-in-sql-server
* https://stackoverflow.com/questions/5499003/sqlite-list-all-foreign-keys-in-a-database
```python
# https://stackoverflow.com/a/59171912
SELECT * FROM pragma_foreign_key_list('reading');
# next step is running this from sqlite3
```

## GUI (dbeaver)

🗄️ `python/feedback.md` notebook

---

OPTIONS
* NoSQL: Table Plus https://news.ycombinator.com/item?id=22908224 DbGate https://github.com/dbgate/dbgate
* SQLite: DB4S https://github.com/sqlitebrowser/sqlitebrowser https://github.com/coleifer/sqlite-web https://sqlitestudio.pl/
* Postgres: pgAdmin, PGweb https://github.com/centerofci/mathesar
* _Beekeeper_: $7/month https://www.beekeeperstudio.io/
* _Datagrip_: 🎯 $10/month, ERD https://www.jetbrains.com/datagrip/
* _Datasette_: 🎯 SQLite only https://github.com/simonw/datasette/issues/670 https://github.com/simonw/datasette-upload-csvs https://github.com/simonw/dclient https://github.com/datasette/datasette-create-view https://github.com/simonw/sqlite-utils-ask https://github.com/datasette/datasette-query-assistant https://calmcode.io/course/datasette/introduction
* _DBeaver_: OSS, ERD https://dbeaver.io/ https://stackoverflow.com/a/48397209
* _Outerbase_: 🎯 browser https://github.com/outerbase/studio https://news.ycombinator.com/item?id=42320032
* _Ultorg_: 🎯 $35/month, queryless joins, very interesting interface https://www.hytradboi.com/2022/ultorg-a-user-interface-for-relational-databases

FEATURES
* notebooks https://github.com/electroly/sqlnotebook
* autocomplete https://www.jvt.me/posts/2024/06/07/sql-workflow/
* follow FKs https://github.com/Wisser/Jailer https://github.com/centerofci/mathesar
* data catalog https://harlequin.sh
* ERD 🗄 `info.md` viz / entities / ERD
* _query editor_: save, autocomplete
* _results viewer_: result set

## 🍞 miller

🗄️ `os/tools.md` string processing
📜 https://miller.readthedocs.io/en/latest/glossary https://miller.readthedocs.io/en/latest/reference-verbs/

FILTERING
```sh
filter '$header != ""' $CSV  # filter out nulls
```

CONFIG https://miller.readthedocs.io/en/latest/customization/
* `$HOME/.mlrrc`
```sh
--list-color-names # view colors https://miller.readthedocs.io/en/latest/output-colorization/
c2p  # --c2p
allow-ragged-csv-input  # if data line fields > header line, insert empty val instead of err (CSV header/data length mismatch)

# IO
--icsv    # input csv
--tsv     # input tsv
--opprint # output pprint
--c2p     # combine --icsv and --opprint https://miller.readthedocs.io/en/latest/keystroke-savers/#short-format-specifiers-including-c2p
--csv     # IO csv
```

---

```sh
# BASICS
cat $FILE # select *
head -n 5 $FILE # limit
sort -f $COL $FILE  # sort on col
cut -o -f "col1","col2" $FILE # select col = -o -f col
cut -x -f "col1","col2" $FILE # ignore col = -x -f co l
put '$COL1 = "foo"' then put '$COL2 = "bar"' $FILE_CURRENT > $FILE_UPDATED  # add col
head -n 20 then cut -o -f "id","artist" then sort -f "artist" $FILE # chaining

# PREDICATES, GROUPING
uniq -g <header> <csv> | wc -l # uniq for header
most-frequent -f col -n 1000 example.csv # most frequent value by header
most-frequent -f col -n 1000 example.csv | mlr --opprint sort -f col # most frequent value by header + group by header
--c2p cut -o -f "21.08","21.09" then put '${total} = ${21.08} + ${21.09}' <csv> # put = computed fields; ${field} for fields w/ spaces
filter '$header == "value"' $CSV # select * where header = val
filter '$header1 == "value-foo"' && '$header2 == "value-bar"' example.csv
filter 'is_null($header)' example.csv # https://miller.readthedocs.io/en/latest/reference-dsl-builtin-functions/
filter '$earnings > 0.0' example.csv
```

## REPL (dbcli)

📜 https://www.dbcli.com/

---

usql as alternative https://news.ycombinator.com/item?id=42161987
🛠️ CLI query https://github.com/neilotoole/sq https://github.com/PeepDB-dev/peepdb

* open with env var: `cli -h`
* exit: `exit`, `\q`
* list tables: `\dt`
* help: `\?`
* autocomplete: `ctrl e`
* autocomplete: `ctrl e`
* clear screen: `ctrl l`
* _metacommand_: preceded w/ backslash https://www.pgcli.com/commands
* set pager to bat: `pager = less -SRXF` https://www.pgcli.com/docs
* _named query_: snippet, saved query https://www.pgcli.com/named_queries.md https://simonwillison.net/2024/Dec/3/datasette-queries/
* syntax: `f` (litecli) `n` (pgcli)
* list: `\f` https://github.com/dbcli/pgcli/issues/1236
* save: `\fs <name> <query>` https://github.com/dbcli/pgcli/issues/938
* save w/ param: `\fs <name> <query where foo = $1>` https://github.com/dbcli/pgcli/issues/938
> broken in sandbox: could be pager, Python version, config (try default config installed in $HOME) https://github.com/dbcli/pgcli/search?q=codec&type=issues
* use: `\f <name>`
* use w/ param: `\f <name> "arg"`
* rm: `\fd <name>` https://litecli.com/favorites/

## 🌱 seed

🗄️ `test.md` db

---

> pull in `make-seed-data` from Capp repo

```text
Can you make me some sample data?

FOO
id,mpn,mfg,price
1,IMQL,apple,150
2,6Z6G,samsung,200
3,S3OW,motorola,350

BAR
id,mfg,price
IMQL,apple,125
6Z6G,samsung,200
S3OW,motorola,325

* table FOO mpn maps to table BAR id
* their are some price differenece btw the records
* each table should have 10 records
```

## spreadsheet (Excel)

🗄
* `finance/corporate.md` accounting > tooling
* `python.md` REPL

DESIGN
* good REPL for single table https://www.ultorg.com/
* bad at n tables
> Whether in finance, engineering, operations, or the life sciences, you are likely working with tables of data in spreadsheets, CSV files, or an external database. Spreadsheets are excellent tools for managing a single table of data. They are a poor fit for database tasks, however, where data must be combined and queried in many different ways. https://www.ultorg.com/
* bad at UX, hence Airtable https://luttig.substack.com/p/dont-forget-microsoft Airtable is bad? https://news.ycombinator.com/item?id=26448985 Airtable let's you attach images, documents https://github.com/nocodb/nocodb https://news.ycombinator.com/item?id=41503251 https://news.ycombinator.com/item?id=34127804 https://gitlab.com/baserow/baserow more Airtable https://teable.io/ https://www.hytradboi.com/2022/why-airtable-is-easy-to-learn-and-hard-to-outgrow
* bad at collaboration, hence Google Sheets https://luttig.substack.com/p/dont-forget-microsoft
* criticism https://betonit.substack.com/p/spreadsheets-letters-from-a-quant https://www.natemeyvis.com/writing/on-bryan-caplans-spreadsheets/

ALTERNATIVES
* BYO https://jamesg.blog/2024/08/21/spreadsheet-engine/
* TUI https://github.com/andmarti1424/sc-im
* OSS https://github.com/gristlabs/grist-core
* webapp https://equals.app/ https://rows.com/
* in Python https://pyspread.gitlab.io/ https://news.ycombinator.com/item?id=40284219
* _IronCalc_: https://news.ycombinator.com/item?id=42095292 https://github.com/ironcalc/ironcalc
* _rowzero_: https://rowzero.io/ https://grantslatton.com/
* _pysheets_: 🎯 uses pyodide https://pysheets.app/about https://realpython.com/podcasts/rpp/226/
* _sc-im_: 🎯 clone TUI https://github.com/andmarti1424/sc-im
* _visicalc_: predecessor to Lotus123, Excel http://www.paulgraham.com/mac.html
* _UltOrg_: spreadsheet on top of dbms https://news.ycombinator.com/item?id=30868696 🔍 `Ultorg beta`

📊 EXCEL
* ubiquity https://news.ycombinator.com/item?id=26386419 https://www.wsj.com/articles/stop-using-excel-finance-chiefs-tell-staffs-1511346601 https://news.ycombinator.com/item?id=28595155 https://dataingovernment.blog.gov.uk/2019/06/10/improving-how-we-manage-spreadsheet-data/ https://medium.com/backchannel/a-spreadsheet-way-of-knowledge-8de60af7146e https://www.theverge.com/c/24133822/microsoft-excel-spreadsheet-competition-championship
* porting to Python https://www.youtube.com/watch?v=llgTl9BDuKw
* with SQL https://sheetsql.io/
* transpile to Python https://news.ycombinator.com/item?id=40457631
* praise https://www.reifyworks.com/writing/2017-01-25-i-was-wrong-about-spreadsheets-and-im-sorry
> Excel in my opinion is the most successful software application in history. https://subset.so/blog/excel-2-0 https://news.ycombinator.com/item?id=30868696
> Slightly overrated by users and wildly underrated by anyone who spends most of their time using more powerful tools https://diff.substack.com/p/inside-the-house-report-on-big-tech-6a6
> It blew my mind how many business critical processes were managed with excel spreadsheets being shared via email chains. It is incredible how flexible and effective Excel is for such a wide variety of use-cases. https://benadam.me/thoughts/my-experience-at-amazon/
* write to google sheets https://jacobian.org/til/gspread-dictwriter/
* from Excel to Python https://talkpython.fm/episodes/show/288/10-tips-to-move-from-excel-to-python https://talkpython.fm/episodes/show/200/escaping-excel-hell-with-python-and-pandas
* _workbook_: entire document
* _sheet_: sub-document
* can't open more than 1 million rows in single tab but can script so that Excel will break larger file into multiple tabs.
* row limit of 65k for xls files https://stackoverflow.com/a/45741831
* libraries https://www.xlwings.org/ https://realpython.com/openpyxl-excel-spreadsheets-python/ https://github.com/python-excel/xlrd https://github.com/dgorissen/pycel
* generate https://github.com/jazzband/tablib https://github.com/zachvalenta/csv-convert
* use from Python https://github.com/xlwings/xlwings
* use from Golang https://github.com/qax-os/excelize
* Visual Basic https://retool.com/visual-basic/ https://retool.com/blog/the-history-and-legacy-of-visual-basic

## TUI (harlequin)

TUI
* _dadbod_: harlequin for Neovim https://github.com/kristijanhusak/vim-dadbod-ui https://www.youtube.com/watch?v=NhTPVXP8n7w
* _harlequin_: ✅ query editor https://harlequin.sh
* _GoBang_: perpetual alpha https://github.com/TaKO8Ki/gobang
* _rainfrog_: Postgres https://github.com/achristmascarl/rainfrog

---

* compare queries across dbms https://github.com/rickbergfalk/sqlpad
* AI https://whodb.clidey.com/

HARLEQUIN 📜 https://harlequin.sh
> need to first fix the visidata command in Makefile to generate SQLite db from CSV
> or try this https://github.com/danvergara/dblab
* have to import CSV files after opening harlequin? import via data catalog? via `conn_str = ["local.db"]`? https://github.com/tconbeer/harlequin/discussions/314
* profiles: sqlite, duckdb, postgres
* Django https://adamj.eu/tech/2024/05/07/django-harlequin/

## ❎ xsv

🗄️ `os/tools.md` string processing
📜 https://github.com/BurntSushi/xsv

```sh
# MUNGE
fmt $TSV > $CSV

# DML
headers $CSV # get headers with index
headers -j $CSV # get headers w/out index
select "header" $CSV # select all from header
```

---

```sh
count songs.csv # count records
split -s <records_per_file> <output-dir> <csv> # split into n files
search -i -s "header" "query" $CSV # search within header (case insensitive)
stats <table> | xsv table # stats (sum, min, max)
xsv sample 50 full.csv > sample.csv # get sampled subset
xsv slice -i 0 csv | xsv flatten # get line of data and display as two columns
```

# 🟦 VISIDATA

🗄️ `protocols.md` CSV
🔍 https://stackoverflow.com/questions/tagged/visidata
* help: `ctrl h` jumps to man page https://jsvine.github.io/intro-to-visidata/basics/getting-out-of-trouble/
* available cmds: `z ctrl h`
📜
* repo https://github.com/saulpw/visidata
* docs https://www.visidata.org
* guide https://jsvine.github.io/intro-to-visidata/
* ref https://jsvine.github.io/visidata-cheat-sheet/en/

STATE
* create: sheet `A` attr `za` record `a` n records `ga` https://www.youtube.com/watch?v=yK3qgOIx4x0 [0:25,1:30]
* undo: `U`
* save current sheet: `CTRL S`
> super slow for half GB TSV file
* save current row: `Y`
* save selected rows: `gY`

CMDLOG
* stored at `~/.visidata/history`
* play: `vd -p cmd_log.vd` https://www.youtube.com/watch?v=yK3qgOIx4x0 [5:20]
* view: `D`
* save: `ctrl s`

SESSION
* save session: `CTRL d` https://www.visidata.org/docs/save-restore/
* restore session: `vd - <file>`

CONFIG https://github.com/zachvalenta/dotfiles/blob/7f843714b3c3d6eb531dfb292e91214c051ef82e/db/.visidatarc
* fs: `~/.visidatarc` https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* cache: `~/.visidata`
* config: `shift o` global options sheet `z shift o` sheet-specific `~/.visidatrc` persistent https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* formats: Parquet, CSV https://www.visidata.org/docs/formats/
* sources: Postgres, Clickhouse https://www.visidata.org/blog/2022/connect-visidata-to-sql-databases-with-vdsql/
* turn off status messages https://github.com/saulpw/visidata/issues/2567 https://github.com/saulpw/visidata/issues/2621
* turn off DOS newline / carriage return https://github.com/saulpw/visidata/issues/387

---

https://datasette.io/for/exploratory-analysis
https://cosimameyer.com/post/2024-09-05-pythonistr-a-match-made-in-data-heaven/
https://github.com/cosimameyer/overviewpy

* dealing with large files https://jsvine.github.io/intro-to-visidata/intermediate/large-files/
* plugin for get duplicates https://jsvine.github.io/intro-to-visidata/advanced/extending-visidata/?highlight=duplicate
* pass cells to function https://www.youtube.com/watch?v=yhunJc8Nu4g 5:00

* load data: `vd <file>` https://www.visidata.org/docs/loading/ https://www.visidata.org/formats/
* convert data: `vd <.json/csv> -b -o <name>.db` 🗄 export sheet
* graphing https://www.youtube.com/watch?v=Ozap_numsjI https://www.visidata.org/docs/graph/ https://www.youtube.com/watch?v=j0qn8OIiV-w
> check out deciles from aggregates
* munge delimited data https://www.youtube.com/watch?v=yhunJc8Nu4g
* _melt_: mv from 1 record n attr to n records 1 attr https://www.youtube.com/watch?v=yhunJc8Nu4g 2:30

* rf using Paul's playlist https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
* `:q` to exit vd itself vs. just quitting a sheet https://github.com/saulpw/visidata/issues/538 https://github.com/saulpw/visidata/issues/483 https://github.com/saulpw/visidata/issues/389 https://github.com/saulpw/visidata/issues/212
* connect to postgres https://www.visidata.org/formats/#postgres
* load subset of file https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#from-the-command-line
* select random subset https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#select-a-random-sample-of-rows

## attr

https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/

* agg: set type (`%` for float) `z+` + agg https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#one-off-calculations
* goto: `c $COL_REGEX`
* search records: `/`
* nav: `hl`, `gh/gl`
* rename: `^`
* mv: `H/L`
* create blank: `za` https://jsvine.github.io/intro-to-visidata/intermediate/creating-new-columns
* hide/unhide: `-` / `gv`
* expand width to fit text: `_` (single) `g_` (all)
* shrink by 1/2: `z-`
* expand json: `()`

---

* key: `!`; pins + certain cmd only apply to them https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-designate-key-columns
* aggregates: sum `z +` https://www.youtube.com/watch?v=yhunJc8Nu4g 4:20
* set type: `~` string `#` int `$` currency https://www.visidata.org/docs/graph/
* set value `g=` https://www.youtube.com/watch?v=yK3qgOIx4x0 3:20
> so even if underlying attr type is non-numeric can change type in sheet

* sort col `[` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#how-to-sort-rows
* filter col `| <filter>` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with
* _go to_: ❓ https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching0
* _set type_: https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-set-column-types https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#manipulating-columns-from-the-columns-sheet
* _joins_: https://jsvine.github.io/intro-to-visidata/intermediate/joining-sheets/
* _aggregation_: https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#adding-aggregators https://sqlfordevs.com/multiple-aggregates-in-one-query?ref=Newsletter
* _aggregate on column_: https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#one-off-calculations

* _select all records that match on current cell_: `| <val>` https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#by-matching-patterns
* _filter on selected_: `"` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#using-frequency-tables-to-select-and-filter-for-multiple-values
* https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#via-expressions

## records

---

* null = those yellow crossed out circles https://www.visidata.org/docs/rows/
* mv: `SHIFT j/k`
* sort: `[]`
* page: `ctrl b/f`
* select: `s/u` (single) `gs/gu` (all)
* rm: `d` (doesn't work for selected)
* goto: `zr <num>`
> can use Vim https://www.youtube.com/watch?v=yhunJc8Nu4g
* edit: `e` https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#editing-row-cells
* edit w/ regex: `g*` https://www.youtube.com/watch?v=l2Bpmm0yAGw 4:24 https://www.visidata.org/docs/edit/

## sheets

---

* pull values into new sheet https://www.youtube.com/watch?v=yhunJc8Nu4g 3:00
* create sheet from selected records: `"` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with
* _sheet_: god component https://jsvine.github.io/intro-to-visidata/basics/understanding-sheets/
* _meta sheet_: combo columns `C` sheets `S` summary `I`
* frequency `F` combo frequency `gF` https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#multi-column-frequencies
* pivot table https://jsvine.github.io/intro-to-visidata/intermediate/reshaping-data/#creating-pivot-tables
* _source sheet_: actual data
* _derived sheet_: derived data off source sheet
* reload/reset `ctrl r`
* toggle `ctrl 6`
* save `ctrl s` https://www.youtube.com/watch?v=j0qn8OIiV-w 4:30
* exit: `q` single `gq` all `gs` view recently exited
* rm: `d`
* view deleted `gS`
