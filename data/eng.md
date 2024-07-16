# ⛩️

## 参考

🔍 
* https://dba.stackexchange.com
* https://roadmap.sh/postgresql-dba
📚
* Kleppmann data intensive applications
* Reis fundamentals of data eng

## 进步

ICEBERG 🔍 email
https://www.youtube.com/watch?v=cI9zu5Rk_bQ
https://www.youtube.com/watch?v=PkBApqCfNqA
https://www.youtube.com/playlist?list=PLM15UEjiveml7UnWEqqrLqbWKXSaClR2Z
https://www.youtube.com/playlist?list=PL-gIUf9e9CCtGr_zYdWieJhiqBG_5qSPa
https://www.youtube.com/watch?v=Hh1MkMBAqqI
https://www.youtube.com/watch?v=6tjSVXpHrE8
https://www.youtube.com/watch?v=nWwQMlrjhy0
https://www.youtube.com/watch?v=ifXpOn0NJWk
https://medium.com/expedia-group-tech/a-short-introduction-to-apache-iceberg-d34f628b6799
* _table format_: 
* _Iceberg_: SQL for table formats https://iceberg.apache.org/ https://www.thoughtworks.com/radar/platforms?blipid=202203012 https://news.ycombinator.com/item?id=34342190
* https://medium.com/expedia-group-tech/a-short-introduction-to-apache-iceberg-d34f628b6799
> Table formats have slowly been stealing the spotlight across the big data space as projects like Apache Hudi, Delta Lake and Apache Iceberg mature and disrupt the tried-and-tested legacy data lake technologies in use at most companies worldwide.
> The project [Iceberg] was originally developed at Netflix to solve long-standing issues with their usage of huge, petabyte-scale tables. It was open-sourced in 2018 as an Apache Incubator project and graduated from the incubator on the 19th of May 2020.

* Arrow partitioning https://r4ds.hadley.nz/arrow#partitioning
* NYC taxi dataset, Parquet https://duckdb.org/2021/12/03/duck-arrow.html https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page https://tech.marksblogg.com/billion-nyc-taxi-rides-redshift.html https://iceberg.apache.org/spark-quickstart/#creating-a-table
* 📻 Macey https://softwareengineeringdaily.com/2019/07/23/data-engineering-with-tobias-macey/ https://www.dataengineeringpodcast.com/six-year-retrospective-episode-361
* course https://www.youtube.com/playlist?list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb https://r4ds.hadley.nz/

---

* start with data eng https://uwekorn.com/2019/10/19/taking-duckdb-for-a-spin.html https://adamdrake.com/command-line-tools-can-be-235x-faster-than-your-hadoop-cluster.html facets https://datasette.io/for/exploratory-analysis plugins https://datasette.io/tools https://datasette.io/plugins Timescale https://aliramadhan.me/2024/03/31/trillion-rows.html https://www.freecodecamp.org/learn/data-analysis-with-python/#data-analysis-with-python-course https://www.youtube.com/watch?v=v65n9yQWfVs https://www.youtube.com/watch?v=qowFCmaNFp4
* https://www.thenile.dev/blog/things-dbs-dont-do
* Conery + query sandbox https://tedconbeer.com/ https://github.com/ankane/blazer
* https://news.ycombinator.com/item?id=40488844&utm_term=comment
* datagolf https://datagolf.com/tour-standings https://datagolf.com/field-updates https://datagolf.com/datagolf-rankings https://datagolf.com/api-access
> https://www.linkedin.com/in/matthew-courchene-2a19587b/ https://www.globalgolfpost.com/featured/data-gold/ https://www.sloansportsconference.com/people/matthew-courchene https://golf.com/news/features/data-golf-analytics-new-level-pay-attention-gamblers/ https://twitter.com/DataGolf/status/1779890636537094231
> read on sports better, stats
* steampipe https://news.ycombinator.com/item?id=40343131
* https://news.ycombinator.com/item?id=39338626
* https://news.ycombinator.com/item?id=37222191
* https://news.ycombinator.com/item?id=35478240

* _24_: try harlequin
* _22_: basic xsv/miller/Pandas
* _21_: put together basic data eng notes
* _18_: find visidata

# 🖲️ ADMIN

CHECKLIST https://www.lastweekinaws.com/blog/aurora-vs-rds-an-engineers-guide-to-choosing-a-database/
* install dbms
* maintenance
* monitoring
* security patches
* make backups

SECURITY
* read-only access https://pgexercises.com/about.html
* `statement_timeout` to prevent long-running queries https://pgexercises.com/about.html https://www.postgresql.org/docs/13/runtime-config-client.html
* clear settings from connection after each statement https://pgexercises.com/about.html https://www.pgbouncer.org/
* _row-level_: limit user to specific rows https://pganalyze.com/blog/postgres-row-level-security-django-python https://news.ycombinator.com/item?id=30700899
* StrongDM records remote access sessions https://softwareengineeringdaily.com/2019/07/23/data-engineering-with-tobias-macey/

TIMEZONES
* client sould specify their timezone before querying https://hakibenita.com/sql-dos-and-donts#be-aware-of-timezones
* relational has problems w/ this https://increment.com/software-architecture/architecture-for-generations/ https://en.wikipedia.org/wiki/Temporal_database#Example https://retool.com/blog/formatting-and-dealing-with-dates-in-sql/

## backup

🗄 
* `it.md` backups
* `system.md` distributed

* short answer: dump every hour to S3 https://blog.codepen.io/2014/05/27/013-backups/ 5:00
* hard drive health: 2% annual fail rate https://drewdevault.com/2020/04/22/How-to-store-data-forever.html DriveDX https://binaryfruit.com/drivedx/usb-drive-support Wear_Leveling_Count https://superuser.com/q/1037644 SMART https://en.wikipedia.org/wiki/Self-Monitoring,_Analysis_and_Reporting_Technology https://news.ycombinator.com/item?id=11110902
* version control data: DVC https://github.com/iterative/dvc https://realpython.com/python-data-version-control/ Dolt https://github.com/dolthub/dolt
> people don't really care about this https://news.ycombinator.com/item?id=22731928
* diff https://github.com/datafold/data-diff
* https://news.ycombinator.com/item?id=38961463
* _snapshot_: backup whole table
* _date-based_: backup portion of table i.e. acts as an immutable log
* _cold storage_: infrequent reads/writes https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* _hot storage_: frequent reads/writes https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* _deduplication_: only touch new data (vs. entire file)
* _durability_: data exists https://news.ycombinator.com/item?id=26428688
* _reliability_: data available
* _redundant_: same data stored multiple places e.g. RAID https://drewdevault.com/2020/04/22/How-to-store-data-forever.html

## replicate

📙 Kleppmann ch. 5
🗄️
* `dbms.md` Mongo
* `system.md` distributed
* `sql.md` migrations

* https://github.com/bruin-data/ingestr
* _replication_: same data on diff nodes 📙 Kleppmann [199] https://news.ycombinator.com/item?id=37066284
* secondaries only accept writes from primary 📙 Bradshaw [236]
* very slow if synchronous https://lethain.com/distributed-systems-vocabulary/
* _lag_: when secondaries fall behind primary 📙 Bradshaw [235]
* will refuse read requests to avoid serving stale data
* _RAID_: form of replication https://www.kalzumeus.com/2010/04/20/building-highly-reliable-websites-for-small-companies/ https://news.ycombinator.com/item?id=28405695 use ZFS/Zed https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* backup https://github.com/benbjohnson/litestream https://github.com/maxpert/marmot https://news.ycombinator.com/item?id=30883015 SQLite for edge computing https://news.ycombinator.com/item?id=33081159
* using Redis https://andrewbrookins.com/python/scaling-django-with-postgres-read-replicas/
* Cassandra https://stackoverflow.com/questions/17348558/does-an-update-become-an-implied-insert
* always use write db vs. read replica to avoid creating 2 records
* http://eradman.com/posts/pubsub-pgoutput.html
* https://news.ycombinator.com/item?id=31341392
* cutover
> There's an ongoing sync job as well, so writes that land on the old database are pushed to the new one, so low risk of data loss.
* replicate Postgres to SQLite on the edge https://github.com/zknill/sqledge

## perf

📙 Winand sql perf https://use-the-index-luke.com/
🗄️
* `dbms.md` indexing
* `telemetry.md` perf

METRICS
* CPU utilization
* QPS (queries per second)

TACTICS
* use larger instance (lower CPU utilization) https://www.figma.com/blog/how-figma-scaled-to-multiple-databases/
* read replica (higher QPS) https://www.figma.com/blog/how-figma-scaled-to-multiple-databases/

---

* https://www.crunchydata.com/blog/is-your-postgres-ready-for-production
@ https://www.figma.com/blog/how-figma-scaled-to-multiple-databases/
* should `explain analyze` be here?

EXPLAIN
* plan hints https://news.ycombinator.com/item?id=35963572
> In some circumstances, you have knowledge of your data that the optimizer does not have, or cannot have. You might be able to improve the performance of a query by providing additional information to the optimizer https://hakibenita.com/sql-dos-and-donts#add-faux-predicates
* `explain`: view preflight execution plan  https://thoughtbot.com/blog/reading-an-explain-analyze-query-plan https://dataschool.com/sql-optimization/optimization-using-explain/ "returns the steps a database will take to execute a query" https://render.com/blog/postgresql-slow-query-to-fast-via-stats
* how to interpret https://render.com/blog/postgresql-slow-query-to-fast-via-stats
* adds overhead caused by the Volcano model https://www.ongres.com/blog/explain_analyze_may_be_lying_to_you/
* `analyze`: update table stats after bulk index https://sqlfordevs.com/table-maintenance-bulk-modification
* `explain analyze`: view postflight analysis 📙 Evans 25 https://jaywhy13.hashnode.dev/that-time-postgresql-said-no-thanks-i-dont-need-your-index
* `seq scan`:  query plan doesn't use an index 📙 Evans 25
* aka full table scan https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data
* making sense of Postgres output https://www.pgmustard.com/docs/explain https://explain.depesz.com/
* more precision yields faster query plan
> The query fetches sales that were modified before 2019. There is no index on this field, so the optimizer generates an execution plan to scan the entire table. Let's say you have another field in this table with the time the sale was created. Since it's not possible for a sale to be modified before it was created, adding a similar condition on the created field won't change the result of the query. However, the optimizer might use this information to generate a better execution plan https://hakibenita.com/sql-dos-and-donts#add-faux-predicates
```diff
FROM sale
WHERE modified < '2019-01-01 asia/tel_aviv'
+ AND created < '2019-01-01 asia/tel_aviv'
```

https://www.timescale.com/blog/13-tips-to-improve-postgresql-insert-performance/

* queries: avoid `distinct`, `having`, subqueries, `*` https://dataschool.com/sql-optimization/optimize-your-sql-query/
* query plan
* use indexes
* https://github.com/ankane/pghero
* https://klotzandrew.com/blog/quickly-debugging-postgres-problems
* _QPS (queries per second)_: https://www.youtube.com/watch?v=kEShMV4VfWE
* https://stackoverflow.com/a/11275107/6813490/ 
* https://numeracy.co/blog/life-of-a-sql-query
* https://www.digitalocean.com/community/tutorials/how-to-use-mysql-query-profiling

## shard

📙 Kleppmann ch. 6 https://en.wikipedia.org/wiki/Partition_(database)
🗄️ `dbms.md` Mongo

* _partition_: diff data on diff nodes 📙 Kleppmann 199
* why: horizontal scaling, put more frequently accessed data on better hardware or more geographically proximate 📙 Bradshaw [289]
* aka sharding https://news.ycombinator.com/item?id=28776786 📙 Bradshaw [289] Kleppmann [199]
* avoid by scaling vertically as long as you can 📙 Conery imposter 343 https://news.ycombinator.com/item?id=28430852
* howto https://github.blog/2021-09-27-partitioning-githubs-relational-databases-scale/ 📙 Conery imposter 343
* https://stackoverflow.com/questions/20771435/database-sharding-vs-partitioning https://medium.com/@jeeyoungk/how-sharding-works-b4dec46b3f6 https://news.ycombinator.com/item?id=28425379
* _shard_: node in cluster 📙 Bradshaw [290]

# 🧮 ANALYTICS

🗄
* `protocols.md` file fmt
* `telemetry.md` analytics

DATASETS
* general: https://ourworldindata.org/ https://www.wikidata.org/ https://datasetsearch.research.google.com/ https://www.kaggle.com/datasets https://datausa.io/ https://www.splitgraph.com/
* art https://news.ycombinator.com/item?id=28445761
* baseball https://jamesrledoux.com/projects/open-source/introducing-pybaseball/ https://www.thedrummeyangle.com/post/an-introduction-to-pybaseball-using-python-to-analyze-baseball-data https://www.datacamp.com/tutorial/scikit-learn-tutorial-baseball-1
* census https://www.ipums.org/
* finance: https://github.com/ranaroussi/yfinance
* housing: https://www.zillow.com/research/data/
* India https://www.dataforindia.com/
* literature: ratings http://fastml.com/goodbooks-10k-a-new-dataset-for-book-recommendations/ https://github.com/zygmuntz/goodbooks-10k https://bookbrainz.org/ text http://www.jessamyn.com/barth/index.html https://en.wikisource.org/ https://news.ycombinator.com/item?id=1394077
* music: https://musicbrainz.org/ https://www.kaggle.com/datasets/nolanbconaway/24169-pitchfork-reviews/data https://pudding.cool/2024/03/greatest-music/
* population: https://simplemaps.com/data
* scientific: https://news.ycombinator.com/item?id=27365755
* weather https://github.com/blaylockbk/Herbie

## BI

🗄
* `math.md` graphs
* `math.md` stat / distributions

* _business intelligence (BI)_: explorer (for non-devs) + graphs
* SQL-by-mouse https://briefer.cloud/blog/posts/self-serve-bi-myth/

TOOLS
* _Blazer_: https://github.com/ankane/blazer
* _Dataherald_: query using natural language via LLM https://github.com/Dataherald/dataherald
* _Datalens_: Docker https://news.ycombinator.com/item?id=37657772
* _Evidence_: 🎯 borked VS Code outliner https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=37663111
* _Lightdash_: https://github.com/lightdash/lightdash
* _Kviklet_: queries + perms https://github.com/kviklet/kviklet
* _Metabase_: popular https://news.ycombinator.com/item?id=30323131
* _Poli_: local, Java https://github.com/shzlw/poli
* _PyGWalker_: https://github.com/Kanaries/pygwalker
* _Quary_: VS Code extension https://github.com/quarylabs/quary
* _Redash_: cloud deploy https://github.com/getredash/redash
* _Tableau_: via Pandas https://github.com/Kanaries/pygwalker Markdown https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=39519145
* _SQL Explorer_: 🎯 https://github.com/explorerhq/django-sql-explorer
> Write SQL, share results, do some analysis, get insight. No surprises. https://news.ycombinator.com/item?id=40857589
* _Superset_: popular https://news.ycombinator.com/item?id=37657772 https://github.com/apache/superset
* _Taipy_: https://github.com/Avaiga/taipy

## dataframe (?)

🗄️ `sql.md` design

---

https://calpaterson.com/bank-python.html
https://tibble.tidyverse.org/
https://dplyr.tidyverse.org/

📚
* McKinney https://wesmckinney.com/book/
* VanderPlas https://jakevdp.github.io/PythonDataScienceHandbook/

ZA
* tables https://posit-dev.github.io/great-tables
* _dataframe_: result set + operations https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://github.com/go-gota/gota/blob/master/dataframe/dataframe.go
* Dataframe Interchange Protocol, Dataframe API Standard https://ponder.io/how-the-python-dataframe-interchange-protocol-makes-life-better/ https://ponder.io/why-are-there-so-many-python-dataframes/ https://pythonspeed.com/articles/polars-pandas-interopability/
* _series_: rows from a single column https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://pandas.pydata.org/docs/user_guide/10min.html#getting

### 🏹 Arrow

📜 https://arrow.apache.org/
🗄️ `protocols.md` file fmt / serialization

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

### 🦢 Ibis

📜 https://ibis-project.org/

* dataframe API
* transpiles to SQL i.e. works with SQL-based query engines (BigQuery, Clickhouse, Postgres, Snowflake)
* compiles to Python i. e https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
* dataframe API that can use Polars/Pandas query engine or transpile to SQL and run against relational dbms https://talkpython.fm/episodes/show/462/pandas-and-beyond-with-wes-mckinney

### 🐻‍❄️ Polars

📜 https://docs.pola.rs/ https://docs.pola.rs/api/python/stable/reference/index.html

* faster than Pandas https://pola.rs/posts/benchmarks/

COOKBOOK
* za
```python
# IO
pl.read_csv(path/to/csv, ignore_errors=True)
pl.write_csv(path/to/csv, ignore_errors=True)

# MALFORMATTED COLUMN HEADERS
no_whitespace_or_period_delimit = r"^[^\s.-]+$"
violations = [col for col in df.columns if bool(re.match(no_whitespace_or_period_delimit, col)) is False]
assert len(violations) > 0

# PREDICATES
df.filter(pl.col(COL) == VAL)
df.filter(pl.col(COL).str.contains(REGEX).alias('regex'))
```
* null/empty col
```python
# EMPTY COLUMNS
null_col_df = [col for col in df.columns if df[col].null_count() == df.height]
assert bool(null_col_df) is True

# NULLS
df.filter(pl.col(COL).is_null())

# VALUE NOT PRESENT IN COLUMN
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == 0

# VALUE PRESENT IN EVERY COLUMN RECORD
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == lines_set.height
```

---

* Deltabase, DeltaDB https://github.com/uname-n/deltabase https://pythonbytes.fm/episodes/show/397/so-many-pycon-videos
* design vs. Pandas https://news.ycombinator.com/item?id=35429555
* guide https://realpython.com/polars-python/
* design: query engine with dataframe frontend https://pola.rs/posts/polars_birds_eye_view/ https://blog.jetbrains.com/pycharm/2024/07/polars-vs-pandas/
* can use some Pandas libraries https://pythonspeed.com/articles/polars-pandas-interopability/
* better than Pandas: query in Python or SQL, no dependencies, sensible pip install (vs. conda) https://github.com/pola-rs/polars better perf https://pola.rs/posts/benchmarks/ less memory usage https://pythonspeed.com/articles/polars-memory-pandas/
* worse than Pandas: not meant for Excel-like operations
> Pandas was originally written to replace excel in financial/econometric modeling, not as a replacement for sql. Models written solely in the long relational style are near unmaintainable for constantly evolving models with hundreds of data sources and thousands of interactions being developed and tuned by teams of analysts and engineers. https://news.ycombinator.com/item?id=35429555

### 🐼 Pandas

> 📍 https://github.com/lux-org/lux
📜 https://pandas.pydata.org/docs/
📙 McKinney data analysis https://wesmckinney.com/book/
🔍 howto https://github.com/jvns/pandas-cookbook https://github.com/kxzk/an-embarrassment-of-pandas https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf
📹 guide https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS

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

## spreadsheet (Excel)

🗄 `python.md` REPL

PRO / CON
* good REPL for single table https://www.ultorg.com/
* bad at n tables
> Whether in finance, engineering, operations, or the life sciences, you are likely working with tables of data in spreadsheets, CSV files, or an external database. Spreadsheets are excellent tools for managing a single table of data. They are a poor fit for database tasks, however, where data must be combined and queried in many different ways. https://www.ultorg.com/
* bad at UX, hence Airtable https://luttig.substack.com/p/dont-forget-microsoft Airtable is bad? https://news.ycombinator.com/item?id=26448985 Airtable let's you attach images, documents https://github.com/nocodb/nocodb https://news.ycombinator.com/item?id=34127804 https://gitlab.com/baserow/baserow more Airtable https://teable.io/ https://www.hytradboi.com/2022/why-airtable-is-easy-to-learn-and-hard-to-outgrow
* bad at collaboration, hence Google Sheets https://luttig.substack.com/p/dont-forget-microsoft
* criticism https://betonit.substack.com/p/spreadsheets-letters-from-a-quant https://www.natemeyvis.com/writing/on-bryan-caplans-spreadsheets/

ALTERNATIVES
* _visicalc_: predecessor to Lotus123, Excel http://www.paulgraham.com/mac.html
* _UltOrg_: spreadsheet on top of dbms https://news.ycombinator.com/item?id=30868696 🔍 `Ultorg beta`
* TUI https://github.com/andmarti1424/sc-im
* OSS https://github.com/gristlabs/grist-core
* webapp https://equals.app/ https://rowzero.io/ https://rows.com/
* in Python https://pyspread.gitlab.io/ https://news.ycombinator.com/item?id=40284219

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
* Visual Basic https://retool.com/visual-basic/

## techniques

🗄️
* `math.md` graphs
* `math.md` stat/distributions

* _predicate pushdown_: filter out via where clause https://stackoverflow.com/a/58235274/6813490
* _projection pushdown_: having a small select clause (i.e. don't `select *`) = minimize columns read https://duckdb.org/2021/12/03/duck-arrow.html

---

https://amaizehayes.bearblog.dev/


* https://rodriguezanton.com/philly-pd-incident-data-exploration-with-geopandas/
* https://ibis-project.org/tutorials/ibis-for-sql-users#top-k-operations
> can you do any of this in visidata?
* https://hakibenita.com/sql-for-data-analysis#descriptive-statistics
* https://medium.com/epfl-extension-school/advanced-exploratory-data-analysis-eda-with-python-536fa83c578a `EDA.pdf`
* https://realpython.com/python-for-data-analysis/
* dedupe https://github.com/moj-analytical-services/splink https://sqlfordevs.com/delete-duplicate-rows
* view missing https://github.com/ResidentMario/missingno
* https://hakibenita.com/sql-for-data-analysis#descriptive-statistics
* https://hakibenita.com/sql-for-data-analysis#sampling
* stats https://github.com/capitalone/dataprofiler
* can use R from command line https://missing.csail.mit.edu/2020/data-wrangling/ https://www.r-project.org/
* _reservoir sampling_: https://en.wikipedia.org/wiki/Reservoir_sampling https://github.com/BurntSushi/xsv
* _facet_: https://datasette.io/for/exploratory-analysis https://stackoverflow.com/questions/5321595/what-is-faceted-search

# 🏗️ ENG

## pipelines

* `data/sql.md` migrations

---

* https://sre.google/sre-book/table-of-contents/ chapter 26
* clean up https://news.ycombinator.com/item?id=34578324 https://en.wikipedia.org/wiki/Instruction_pipelining https://joblib.readthedocs.io/en/latest/index.html https://news.ycombinator.com/item?id=34578324 https://arpit.substack.com/p/how-grab-stores-and-processes-millions https://news.ycombinator.com/item?id=34483402 visidata https://www.visidata.org/blog/2020/ten/
* mv/copy from one db to another https://news.ycombinator.com/item?id=39525071 https://github.com/bruin-data/ingestr
* _transform_: 名 step that remodels data to dimensionsal https://www.youtube.com/watch?v=M8oi7nSaWps 3:30 https://news.ycombinator.com/item?id=34578324
* e.g. head/tail, add/rm col, type conversion, join https://www.youtube.com/watch?v=llRLh8cM7QI 15:50
* _ETL_: mv fact tables to dimensionsal 📙 Conery 323
* howto https://www.youtube.com/watch?v=v65n9yQWfVs
* _ELT_: cp facts tables, then mv to dimensionsal https://www.youtube.com/watch?v=voC0ewDeltA 4:00
* howto https://docs.meltano.com/getting-started/meltano-at-a-glance
* allows analysts to do the transformations they need vs. having to figure it out up front https://www.youtube.com/watch?v=qqlbYDfqeI4 7:00

TOOLS
* _Amphi_: https://github.com/amphi-ai/amphi-etl
* _Airbyte_: pull from data source https://www.youtube.com/watch?v=l48zwwRSGeA
* workflow https://www.youtube.com/watch?v=qqlbYDfqeI4 11:00-11:15
* plain text vs. crappy GUI tools for analysts https://www.youtube.com/watch?v=M8oi7nSaWps 5:45 https://www.youtube.com/watch?v=qqlbYDfqeI4 9:40
* _amphi_: https://news.ycombinator.com/item?id=40723356
* _DLT_: https://github.com/dlt-hub/dlt
* _DBT_: tool for transforms https://www.youtube.com/watch?v=l48zwwRSGeA 6:15
* why: schema introspection, testing https://highgrowthengineering.substack.com/p/why-is-dbt-so-important- https://news.ycombinator.com/item?id=33846087
> modern data stack of Fivetran + dbt + Snowflake https://luttig.substack.com/p/dont-forget-microsoft
* create views via ETL in Snowflake (at UM)
* data ingestion from Snowflake using Snowpipe https://docs.snowflake.com/en/user-guide/data-load-snowpipe-intro.html
* util https://github.com/dbt-labs/dbt-utils
* metrics https://news.ycombinator.com/item?id=30938109
* _petl_: transforms https://petl.readthedocs.io/en/stable/
* if petl can only handle thousands of records, why not just use Pandas? https://www.youtube.com/watch?v=llRLh8cM7QI 9:30 25:00

### clean

🗄️ `languages.md` R / tidyverse

---

* anonymize/differential privacy https://www.youtube.com/watch?v=PC0bF5tstvI
* _Zingg_: entity resolution i.e. fix data integrity problems https://github.com/zinggAI/zingg

SANITIZATION https://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data
* https://developer.wordpress.org/apis/security/sanitizing/ https://developer.wordpress.org/apis/security/data-validation/ https://developer.wordpress.org/apis/security/escaping/
* _validation_: compare against rules
* Cerberus https://github.com/pyeve/cerberus https://hector.dev/2020/12/29/validating-data-in-python-with-cerberus.html
* BYO https://realpython.com/primer-on-python-decorators/#more-real-world-examples https://blog.drewolson.org/declarative-validation
* https://github.com/pyjanitor-devs/pyjanitor
* _filter_: rm validation violations
* _escape_: convert validation violations
* _sanitize_: validate + filter/escape
* _parameterize_: sanitization for SQL https://security.stackexchange.com/a/143925

### test

* compare data across tables https://github.com/datafold/data-diff https://github.com/paulfitz/daff
* _Pandera_: type checking for dataframes https://endjin.com/blog/2023/03/a-look-into-pandera-and-great-expectations-for-data-validation https://www.peterbaumgartner.com/blog/testing-for-data-science/ https://www.union.ai/blog-post/pandera-joins-union-ai
> From there, I create v2 of the schema, which adds Checks to the columns. Checks are information we gain after exploring the data - for example, whether a column should always be positive, whether the column name should be formatted a certain way, or whether a column should only contain certain values (e.g. a bool represented as a 0/1 int). https://www.peterbaumgartner.com/blog/testing-for-data-science/
* _GX (Great Expectations)_: assert against schema https://github.com/great-expectations/great_expectations https://softwareengineeringdaily.com/2020/02/17/great-expectations-data-pipeline-testing-with-abe-gong/
> If we're expecting to repetedly read in new data, I would recommend exploring Great Expectations. The killer feature of Great Expectations is that it will generate a template of tests for the data based on a sample set of data we give it, like pandera's `infer_schema` on steroids. Again, this is only a starting point for adding in future tests (or expectations), but can be really helpful in generating basic things to test. https://www.peterbaumgartner.com/blog/testing-for-data-science/
* alternatives https://github.com/socialpoint-labs/sqlbucket https://github.com/sodadata/soda-core
```python
validator.expect_column_values_to_not_be_null(column="passenger_count")
validator.expect_column_values_to_be_between(column="congestion_surcharge", min_value=0, max_value=1000)
```

## query engines

---

SEMANTICS
> https://github.com/pola-rs/polars
> Ibis is a dataframe frontend to query engines https://ibis-project.org/
> read all his posts https://maximilianmichels.com/page/4/ https://apache.org/index.html#projects-list
> is Spark a query engine? seems like query engine + streaming + a bunch other stuff i.e. a congeries https://ibis-project.org/install
> Spark: data manipulation for ML model training https://www.reddit.com/r/apachespark/comments/16zzabh/distributed_sql_query_engine_apache_spark_vs/?rdt=45095

ALTERNATIVES
* cloud: petabytes in single query and comes back in seconds/minutes e.g. Snowflake 📻 Macey 32:20
* just use CLIs https://news.ycombinator.com/item?id=39136472
* _Clickhouse_: https://tech.marksblogg.com/clickhouse-prometheus-grafana.html https://tech.marksblogg.com/install-clickhouse-faster.html https://tech.marksblogg.com/faster-clickhouse-imports-csv-parquet-mysql.html https://tech.marksblogg.com/billion-nyc-taxi-rides-clickhouse-cluster.html
* _BigQuery_: really fast https://tech.marksblogg.com/billion-nyc-taxi-rides-bigquery.html https://dataschool.com/sql-optimization/bigquery-optimization
* _Hydra_: use Postgres https://github.com/hydradatabase/hydra
* _Orc_: https://tech.marksblogg.com/faster-csv-to-orc-conversions.html
* _Postgres_: https://news.ycombinator.com/item?id=39263760 https://brandur.org/warehouse https://tech.marksblogg.com/billion-nyc-taxi-rides-postgresql.html https://news.ycombinator.com/item?id=27109960
> I've also heard arguments that row-oriented systems like MySQL and PostgreSQL can fit the needs of analytical workloads as well as their traditional transactional workloads. Both of these offerings can do analytics and if you're looking at less than 20 GB of data it's probably not worth the effort of having multiple pieces of software running your data platform. https://tech.marksblogg.com/is-hadoop-dead.html
* _Snowflake_: users/investors like them https://news.ycombinator.com/item?id=24265041 https://dataschool.com/sql-optimization/snowflake/ https://www.youtube.com/watch?v=xojAXXRo_S0 OSS https://news.ycombinator.com/item?id=38038239
* apparently a lot faster and easier to manage than a Hadoop installation https://news.ycombinator.com/item?id=24641481 
* can build dashboards off queries
* _Trino_: https://github.com/trinodb/trino https://ibis-project.org/ https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html

### ⦊ Presto

---

* _Presto_: distributed query engine https://tech.marksblogg.com/presto-parquet-airpal.html https://tech.marksblogg.com/billion-nyc-taxi-rides-hive-presto.html Kafka https://tech.marksblogg.com/presto-connectors-kafka-mongodb-mysql-postgresql-redis.html
* beat out Apache Drill https://news.ycombinator.com/item?id=23250314 📙 Beaulieu [303] https://news.ycombinator.com/item?id=29063090

### 🦆 DuckDB

---

> DuckDB is a single file SQL database. https://csvbase.com/blog/6

> DuckDB is a new analytical data management system that is designed to run complex SQL queries within other processes. DuckDB has bindings for R and Python, among others. DuckDB can query Arrow datasets directly and stream query results back to Arrow. This integration allows users to query Arrow data using DuckDB's SQL Interface and API, while taking advantage of DuckDB's parallel vectorized execution engine, without requiring any extra data copying. Additionally, this integration takes full advantage of Arrow's predicate and filter pushdown while scanning datasets. https://duckdb.org/2021/12/03/duck-arrow.html

https://duckdb.org/

* https://tech.marksblogg.com/duckdb-1b-taxi-rides.html
* embedded
* role in ecosystem https://wesmckinney.com/blog/looking-back-15-years/
* for analytics https://news.ycombinator.com/item?id=24531085 https://news.ycombinator.com/item?id=23287278
* own flavor of SQL https://duckdb.org/2022/05/04/friendlier-sql.html
* https://softwareengineeringdaily.com/2022/03/18/duckdb-with-hannes-muleisen/
* https://softwaredaily.wpenginepowered.com/wp-content/uploads/2022/03/SED1439-DuckDB-with-Hannes-Muhleisen.pdf
* https://kadekillary.work/note/duckdb/
* https://tech.marksblogg.com/popular-airline-passenger-routes-2023.html
* interop btw other databases https://duckdb.org/2024/01/26/multi-database-support-in-duckdb.html
* https://news.ycombinator.com/item?id=39141652
* https://www.nikolasgoebel.com/2024/05/28/duckdb-doesnt-need-data.html

### ✰ Spark

---

https://www.amazon.com/gp/product/1098103653
https://www.amazon.com/gp/product/1617297208
https://www.amazon.com/gp/product/1492045527

BASICS
* _Spark_: Pandas + distributed
* RDD = collection of obj https://www.youtube.com/watch?v=XrpSRCwISdk [3:30]
* dataframe = table https://www.youtube.com/watch?v=XrpSRCwISdk [3:30]
* similar interface as Pandas https://www.youtube.com/watch?v=XrpSRCwISdk [10:20]
* architecture: driver/lib -> executor -> operates on data https://www.youtube.com/watch?v=XrpSRCwISdk [5:10]
* used for ML https://tech.marksblogg.com/is-hadoop-dead.html
* _pyspark_: Python API to Spark https://www.youtube.com/watch?v=XrpSRCwISdk https://spark.apache.org/docs/latest/api/python/index.html
* _Databricks_: Spark aaS from creators of Spark 🔍 see ChatGPT convo

HADOOP
* _Hadoop_: parallelization for large data 🗄 `infra.md` EMR https://aosabook.org/en/v1/hdfs.html
* kinda part of Spark, kinda not
> At some point, the Spark community tried to distance itself from the Hadoop ecosystem. They didn't want to be seen as built on legacy software nor as some sort of "add-on" for Hadoop. Given the level of integration Spark has with the rest of the Hadoop ecosystem and given the 100s of libraries from other Hadoop projects being used by Spark I don't subscribe to the belief that Spark is its own thing. https://tech.marksblogg.com/is-hadoop-dead.html
* no one uses anymore? https://news.ycombinator.com/item?id=30595026 https://tech.marksblogg.com/architecting-modern-data-platforms-book-review.html https://tech.marksblogg.com/is-hadoop-dead.html
> Whereas Hadoop and big data targeted analytics applications, often in the data warehousing space, the low latency nature of Kafka makes it applicable for the kind of core applications that directly power a business 📙 Narkhede kafka 
* setup https://tech.marksblogg.com/hadoop-up-and-running.html
* you probably don't need it https://www.benkuhn.net/hard/
* relationship to other projects like Presto, Clickhouse https://tech.marksblogg.com/is-hadoop-dead.html
* _HDFS_: distributed file system http://aosabook.org/en/hdfs.html
* pools all disks from cluster
* files replicated across nodes (not all nodes; two additional copies)
* _MapReduce_: map (split query into chunks, execute in parallel) reduce (merge results) 📙 Kleppmann 46
* map (match) reduce (group) https://www.practical-mongodb-aggregations.com/intro/history.html
* also a query language 📙 Kleppmann 46
* PRQL = alternative query language https://news.ycombinator.com/item?id=30060784

## warehouse

📙 Kleppmann [90-95]

---

DATA TYPES
* _hot storage_: in-mem
* _cold storage_: analytics, archives https://github.com/tembo-io/pg_tier
* _data tiering_: moving cold data to (cheaper) cold storage https://github.com/tembo-io/pg_tier

DATA SIZE
* MB = Excel, nGB-1TB = Postgres, >5TB = Hadoop https://www.chrisstucchio.com/blog/2013/hadoop_hatred.html
* typical dbms can fit 100M records in single table https://news.ycombinator.com/item?id=36038321
* _big data_: can't fit into normal dbms
* _small data_: can fit on a phone (so, half a terabyte) https://simonwillison.net/2021/Jul/22/small-data/
* complete works of Shakespeare only 5.5 MB 📙 Conery [345]
* ways of thinking about data sizes: 1MB vs. 1M seconds (12 days) 1GB vs. 1B seconds (31 years) 1TB vs. 1T seconds (317 centuries) 📙 Conery [345]
> the term Big Data is so over-used and under-defined that it is not useful in a serious engineering discussion. 📙 Kleppmann 1.9
> There are diminishing returns to the amount of information you can extract from data. The tenth gigabyte is worth much less than the second gigabyte. https://www.evanmiller.org/small-data.html

SCHEMAS
* _star schema_: fact table at center
* _snowflake schema_: like star schema but more normalized
* less popular bc harder to query 📙 Kleppmann 95
* _fact table_: transactions 📙 Kleppmann 93
* w/ many FK to other dimensions 📙 Kleppmann 95
* _dimension_: non-transactional tables 📙 Kleppmann 94 https://tech.marksblogg.com/data-fluent-for-postgresql.html

TYPES https://news.ycombinator.com/item?id=34342190
* _data source_: where you're getting the data https://dataschool.com/data-governance
* _lakehouse_: https://softwareengineeringdaily.com/2022/08/25/lakehouse-data-stack-with-raj-bains-2/
* _lake_: 类似 file system https://www.youtube.com/watch?v=V0GvZ_KAI70 https://news.ycombinator.com/item?id=32336977
* table format = structure of files (Parquet) that make up lake https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html
* slower to access, has metadata (when was it produced, who owns it), batch writes, most reads will be humans doing analysis or exploration
* less expensive bc optimizing for large volume i.e. can use slower object storage 📻 Macey 31:30
* _warehouse_: analytics db e.g. Redshift
https://news.ycombinator.com/item?id=37146532&utm_term=comment
family https://news.ycombinator.com/item?id=37520374
> interesting at UM that they had an insights db, essentially a db for warehouse workloads but for the product vs. analysis
> Circa 2010, there was only one full-time analyst at the company working on data, and his laptop was effectively the company’s data warehouse. https://medium.com/airbnb-engineering/how-airbnb-achieved-metric-consistency-at-scale-f23cc53dea70
* typically different dbms from OLAP e.g. Redshift, BigQuery, Hive, Presto 📙 Kleppmann 93
* keeps more data in memory 📻 Macey 24:30
* more expensive bc optimizing for large volume and speed of access 📻 Macey 31:30
* streaming https://www.thoughtworks.com/radar/techniques?blipid=202203008
> A streaming SQL engine keeps queries’ results up to date without ever having to recalculate them, even as the underlying data changes. To explain this, imagine a simple query, such as SELECT count(*) FROM humans . A normal SQL engine (such as Postgres’s, MySQL’s) would need to go over all the different humans every time you ran that query- which could be quite costly and lengthy given our ever changing population count. With a streaming SQL engine, you would define that query once, and the engine would constantly keep the resulting count up to date as new humans were born and the old / sickly ones died off, without ever performing a recalculation of counting all humans in the world. https://news.ycombinator.com/item?id=37965319
* _mart_: subset of warehouse
* uses star schema 📙 Conery 324
* _catalog_: manifest (desc, location) 📻 Macey 5:15 https://data.world/solutions/product-overview/ https://softwareengineeringdaily.com/2022/12/14/the-enterprise-data-catalog/
* Collibra https://www.thoughtworks.com/radar/platforms?blipid=202203049
* https://github.com/open-metadata/OpenMetadata https://github.com/datahub-project/datahub

OLTP
> If you have a transactional need for your dataset it's best to keep this workload isolated with a transactional data store. This is why I expect MySQL, PostgreSQL, Oracle and MSSQL to be around for a very long time to come. https://tech.marksblogg.com/is-hadoop-dead.html
* data: application
* access pattern: writes 📙 Kleppmann [90]
* schema: DIY
* model: relational
* consumers: users

OLAP
> But would you like to see a 4-hour outage at Uber because one of their Presto queries produced unexpected behaviour? Would you like to be told your company needs to produce invoices for the month so the website will need to be switched off for a week so there are enough resources available for the task? Analytical workloads don't need to be coupled with transactional workloads. You can lower operational risks and pick better-suited hardware by running them on separate infrastructure. https://tech.marksblogg.com/is-hadoop-dead.html
* data: from n data sources (application, analytics) 📙 Kleppmann [92]
* access pattern: reads (aggregates) 📙 Kleppmann [90-92] 🗄 `sql.md` tables/views
* schema: star
* model: maybe non-relational 📙 Kleppmann [93,101]
* consumers: DBA, BI, ML https://softwareengineeringdaily.com/2021/07/14/data-science-on-aws-implementing-ai-and-ml-pipelines-on-aws-with-chris-fregly/

# 🛠️ TOOLING

🗄️ `protocols.md` file fmt

> Analysis, even SQL-based analysis, isn't like design, where a handful of people create stuff and everyone else is a consumer, with clear lines between them. It's much, much fuzzier. Though analysts were always our first adopters, lots of people—PMs, engineers, marketing managers, executives, support agents, operations leads, and all job titles in between—periodically wrote queries. These people occupied the middle part of the distribution between analysts and non-analysts that we thought would be vacant. Users weren't bimodal like we expected, but continuous. https://benn.substack.com/p/work-like-an-analyst

API / CODE GENERATION 🗄️ `src.md` API
* https://github.com/directus/directus
* Postgrest https://github.com/PostgREST/postgrest https://news.ycombinator.com/item?id=30132947 https://github.com/prest/prest
* GraphQL https://www.graphile.org/postgraphile/ 
* query SQLite over HTTP https://news.ycombinator.com/item?id=30636796
* ROAPI https://github.com/roapi/roapi https://tech.marksblogg.com/roapi-rust-data-api.html
* Datasette https://www.youtube.com/watch?v=pTr1uLQTJNE https://www.hytradboi.com/2022/datasette-a-big-bag-of-tricks-for-solving-interesting-problems-using-sqlite
* DBCore https://github.com/eatonphil/dbcore https://notes.eatonphil.com/generating-a-rest-api-from-a-database.html
* Octo https://github.com/octoproject/octo-cli
* https://github.com/thevahidal/soul

CONVERSION / GENERATION
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

## entry (dataclerk)

---

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

## explorer (visidata)

🔍 https://stackoverflow.com/questions/tagged/visidata
📜
* repo https://github.com/saulpw/visidata
* docs https://www.visidata.org/man/
* guide https://jsvine.github.io/intro-to-visidata/
* ref https://jsvine.github.io/visidata-cheat-sheet/en/

META
* undo: `U`
* 🚧 file conversion doesn't work, used csvkit instead 🗄️ query-sandbox, capp
> due to `vd` not being callable? https://github.com/saulpw/visidata/issues/1406 `sh: /Users/zach/.local/bin/vd: bad interpreter: /Users/zach/Library/Application: no such file or directory`

⬇️ ATTR https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/
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

⏭ RECORDS
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

📬 SAVE
* save current row: `Y`
* save selected rows: `gY`
* pull values into new sheet https://www.youtube.com/watch?v=yhunJc8Nu4g 3:00
* create sheet from selected records: `"` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with

💾 SESSION / CMDLOG
* save cmdlog: `ctrl s`
* save session: `CTRL d` https://www.visidata.org/docs/save-restore/
* restore session: `vd - <file>`

🔖 SHEETS
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

⚙️ CONFIG
* fs: `~/.visidatarc` https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* cache: `~/.visidata`

---

* conf: default to col full expansion

* dealing with large files https://jsvine.github.io/intro-to-visidata/intermediate/large-files/
* plugin for get duplicates https://jsvine.github.io/intro-to-visidata/advanced/extending-visidata/?highlight=duplicate
* pass cells to function https://www.youtube.com/watch?v=yhunJc8Nu4g 5:00

attr
* key: `!`; pins + certain cmd only apply to them https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-designate-key-columns
* aggregates: sum `z +` https://www.youtube.com/watch?v=yhunJc8Nu4g 4:20
* set type: `~` string `#` int `$` currency https://www.visidata.org/docs/graph/
* set value `g=` https://www.youtube.com/watch?v=yK3qgOIx4x0 3:20
> so even if underlying attr type is non-numeric can change type in sheet

misc
* create: sheet `A` attr `za` record `a` n records `ga` https://www.youtube.com/watch?v=yK3qgOIx4x0 0:25 1:30
* load data: `vd <file>` https://www.visidata.org/docs/loading/ https://www.visidata.org/formats/
* convert data: `vd <.json/csv> -b -o <name>.db` 🗄 export sheet
* config: `shift o` global options sheet `z shift o` sheet-specific `~/.visidatrc` persistent https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* cmd log: view `D` save `ctrl s` play `vd -p cmd_log.vd` https://www.youtube.com/watch?v=yK3qgOIx4x0 5:20 stored at `~/.visidata/history`
* help: `ctrl h` jumps to man page https://jsvine.github.io/intro-to-visidata/basics/getting-out-of-trouble/
* available cmds: `z ctrl h`
* graphing https://www.youtube.com/watch?v=Ozap_numsjI https://www.visidata.org/docs/graph/ https://www.youtube.com/watch?v=j0qn8OIiV-w
> check out deciles from aggregates
* munge delimited data https://www.youtube.com/watch?v=yhunJc8Nu4g
* _melt_: mv from 1 record n attr to n records 1 attr https://www.youtube.com/watch?v=yhunJc8Nu4g 2:30

* rf using Paul's playlist https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
* `:q` to exit vd itself vs. just quitting a sheet https://github.com/saulpw/visidata/issues/538 https://github.com/saulpw/visidata/issues/483 https://github.com/saulpw/visidata/issues/389 https://github.com/saulpw/visidata/issues/212
* connect to postgres https://www.visidata.org/formats/#postgres
* sort col `[` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#how-to-sort-rows
* filter col `| <filter>` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with

attributes
* _go to_: ❓ https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching0
* _set type_: https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-set-column-types https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#manipulating-columns-from-the-columns-sheet

filter
* _joins_: https://jsvine.github.io/intro-to-visidata/intermediate/joining-sheets/
* _aggregation_: https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#adding-aggregators https://sqlfordevs.com/multiple-aggregates-in-one-query?ref=Newsletter
* _aggregate on column_: https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#one-off-calculations

* load subset of file https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#from-the-command-line
* select random subset https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#select-a-random-sample-of-rows

* _select all records that match on current cell_: `| <val>` https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#by-matching-patterns
* _filter on selected_: `"` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#using-frequency-tables-to-select-and-filter-for-multiple-values
* https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#via-expressions

## munge (xsv, et al.)

🗄️
* `shell.md` munge
* `protocols.md` file fmt

CSVKIT 📜 https://github.com/wireservice/csvkit https://csvkit.readthedocs.io/en/latest/
```sh
in2csv $EXCEL > $CSV
```

XSV 📜 https://github.com/BurntSushi/xsv
```sh
fmt $TSV > $CSV  # Capp
count songs.csv # count records
headers -j $CSV # get headers
split -s <records_per_file> <output-dir> <csv> # split into n files
select "header" <csv> # all from header
search -i -s "header" "query" <csv> # search within header (case insensitive)
stats <table> | xsv table # stats (sum, min, max)
xsv sample 50 full.csv > sample.csv # get sampled subset
xsv slice -i 0 csv | xsv flatten # get line of data and display as two columns
```

MILLER 📜 https://miller.readthedocs.io/en/latest/glossary https://miller.readthedocs.io/en/latest/reference-verbs/
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
filter '$header == "value"' example.csv # select * where header = val
filter '$header1 == "value-foo"' && '$header2 == "value-bar"' example.csv
filter 'is_null($header)' example.csv # https://miller.readthedocs.io/en/latest/reference-dsl-builtin-functions/
filter '$earnings > 0.0' example.csv

# IO
--icsv    # input csv
--tsv     # input tsv
--opprint # output pprint
--c2p     # combine --icsv and --opprint https://miller.readthedocs.io/en/latest/keystroke-savers/#short-format-specifiers-including-c2p
--csv     # IO csv

# CONFIG (.mlrrc) https://miller.readthedocs.io/en/latest/customization/
--list-color-names # view colors https://miller.readthedocs.io/en/latest/output-colorization/
c2p  # --c2p
allow-ragged-csv-input  # if data line fields > header line, insert empty val instead of err (CSV header/data length mismatch)
```

## REPL (dbcli)

DBCLI 📜 https://litecli.com/ https://www.pgcli.com
* open with env var: `cli -h`
* exit: `exit`, `\q`
* list tables: `\dt`
* help: `\?`
* autocomplete: `ctrl e`
* autocomplete: `ctrl e`
* clear screen: `ctrl l`
* _metacommand_: preceded w/ backslash https://www.pgcli.com/commands
* set pager to bat: `pager = less -SRXF` https://www.pgcli.com/docs
* _named query_: snippet, saved query https://www.pgcli.com/named_queries.md
* syntax: `f` (litecli) `n` (pgcli)
* list: `\f` https://github.com/dbcli/pgcli/issues/1236
* save: `\fs <name> <query>` https://github.com/dbcli/pgcli/issues/938
* save w/ param: `\fs <name> <query where foo = $1>` https://github.com/dbcli/pgcli/issues/938
> broken in sandbox: could be pager, Python version, config (try default config installed in $HOME) https://github.com/dbcli/pgcli/search?q=codec&type=issues
* use: `\f <name>`
* use w/ param: `\f <name> "arg"`
* rm: `\fd <name>` https://litecli.com/favorites/

## TUI (harlequin)

TUI
* _dadbod_: harlequin for Neovim https://github.com/kristijanhusak/vim-dadbod-ui https://www.youtube.com/watch?v=NhTPVXP8n7w
* _harlequin_: ✅ query editor https://harlequin.sh
* _GoBang_: perpetual alpha https://github.com/TaKO8Ki/gobang
* _rainfrog_: Postgres https://github.com/achristmascarl/rainfrog

GUI
* NoSQL: Table Plus https://news.ycombinator.com/item?id=22908224 DbGate https://github.com/dbgate/dbgate
* SQLite: DB4S https://github.com/sqlitebrowser/sqlitebrowser https://github.com/coleifer/sqlite-web
* Postgres: pgAdmin, PGweb https://github.com/centerofci/mathesar
* _Beekeeper_: $7/month https://www.beekeeperstudio.io/
* _Datagrip_: $25/month, ERD
* _Datasette_: 🎯 SQLite only https://github.com/simonw/datasette/issues/670
* _DBeaver_: OSS, ERD https://stackoverflow.com/a/48397209
* _Ultorg_: 🎯 $35/month, queryless joins, very interesting interface https://www.hytradboi.com/2022/ultorg-a-user-interface-for-relational-databases

FEATURES
* autocomplete https://www.jvt.me/posts/2024/06/07/sql-workflow/
* follow FKs https://github.com/Wisser/Jailer https://github.com/centerofci/mathesar
* data catalog https://harlequin.sh
* ERD https://databasediagram.com/ https://drawdb.vercel.app/
* _query editor_: save, autocomplete
* _results viewer_: result set

---

* compare queries across dbms https://github.com/rickbergfalk/sqlpad

HARLEQUIN 📜 https://harlequin.sh
> need to first fix the visidata command in Makefile to generate SQLite db from CSV
> or try this https://github.com/danvergara/dblab
* have to import CSV files after opening harlequin? import via data catalog? via `conn_str = ["local.db"]`? https://github.com/tconbeer/harlequin/discussions/314
* profiles: sqlite, duckdb, postgres
* Django https://adamj.eu/tech/2024/05/07/django-harlequin/

# 🟨 ZA

ROLES
* _data scientist_: analytics
> data scientist's job is to launder management's intuition using quantitative methods https://news.ycombinator.com/item?id=34694926
* _data engineer_: shepard (ETL) librarian (catalog) https://www.youtube.com/watch?v=qqlbYDfqeI4 1:45
> But if data analytics usually means extracting insights from existing data, data engineering means the process of building infrastructure to deliver, store and process the data. https://khashtamov.com/en/how-to-become-a-data-engineer/
* vs. web dev https://tech.marksblogg.com/is-hadoop-dead.html
> The above projects often aren't advertised in a way that web developers would be exposed to them. This is why someone could spend years working on new projects that are at the bottom of their S-curve in terms of both growth and data accumulated and largely never see a need for data processing outside of what could fit in RAM on a single machine.
> Web Development was a big driver in the population growth of coders over the past 25 years. Most people that call themselves a coder are most often building web applications. I think a lot of the skillsets they possess overlap well with those needed in data engineering but often distributed computing, statistics and storytelling are lacking.
> Websites often don't produce much load with any one user and often the aim is to keep the load on servers supporting a large number of users below the maximum hardware thresholds. The data world is made up of workloads where a single query is trying its best to maximize a large number of machines in order to finish as quickly as possible while keeping the infrastructure costs down.
> Companies producing PBs of data often have a queue of experienced consultants and solutions providers at their door. I've rarely seen anyone plucked out of web development by their employer and brought into the data platform engineering space; it's almost always a lengthy, self-retraining exercise.

## stream

---

STREAMING / BLOCKING 🗄 `computation.md` serialization
* https://www.scattered-thoughts.net/
* https://github.com/ynqa/sig
* blocking
* https://ossinsight.io/blog/why-we-choose-tidb-to-support-ossinsight/
* async https://www.b-list.org/weblog/2022/aug/16/async https://www.youtube.com/watch?v=bw1qeMoFBmw https://www.youtube.com/watch?v=0z74b3c63GA
* batch: TQ, Airflow
> port from `db.md`
* streaming: Kafka https://www.youtube.com/watch?v=qi7uR3ItaOY 🗄 site/drafts/ddd.md
* https://simonwillison.net/2021/Jul/1/pagnis/ https://news.ycombinator.com/item?id=38167423
* forum software in 500 lines or less https://news.ycombinator.com/item?id=33153152
> what is the relationship bte Kafka and faust? https://www.youtube.com/watch?v=Ik1PBbCWcTc
> is flink streaming or batch? https://github.com/apache/flink https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html
> what is windowing? https://www.scattered-thoughts.net/writing/against-sql
batch vs. streaming https://robertheaton.com/2020/02/08/pfab9-batch-vs-stream-processing/ 📙 Kleppmann section 3 🗄 `application.md` WebSocket
> 📍 batch to ETL, streaming to where?
* _batch_: more than one at a time 📍 Kleppmann chapter 9
* requires fewer trips to data source
* higher memory consumption
> Since the data in parsed_messages is essentially the same as that in raw_log but in a different form, parsed_messages probably takes up about the same amount of memory again as raw_log. We’re therefore using at least 20MB of memory to process a 10MB file.
```ruby
raw_log = File.read("samplelog.txt")
parsed_messages = parse_raw_log(raw_log)
message_stats = calculate_stats(parsed_messages)
```
* temporal data, virtual time https://www.hytradboi.com/2022/working-with-virtual-time-in-sql https://github.com/frankmcsherry/blog/blob/master/posts/2021-02-11.md
* _stream processing_: one at a time 📙 Kleppmann ch. 10 🗄 `system.md` Kafka
* libraries: https://github.com/robinhood/faust https://github.com/apache/flink
* sources: clickstream, IoT sensors, time series
* https://www.hytradboi.com/2022/a-faster-inner-dev-loop-for-stream-processing
* lower memory consumption
> Once the block has finished executing, the Ruby interpreter is able to garbage collect the data for both the raw line and processed message, since it can see that the program won’t reference them again. This means that the Ruby interpreter can reuse the piece of memory in which they were stored.
```ruby
stats = {}
File.open("samplelog.txt").each_line do |l|
  message = parse_raw_log_line(l)
  stats = add_message_to_stats(message, stats)
end
```
