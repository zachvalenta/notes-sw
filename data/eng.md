# ⛩️

## 参考

🔍 
* https://dba.stackexchange.com
* https://roadmap.sh/postgresql-dba
* https://github.com/DataExpert-io/data-engineer-handbook
📚
* Kleppmann data intensive applications
* Reis fundamentals of data eng

## 进步

* _24_: try harlequin, lots of rf
* _22_: basic xsv/miller/Pandas
* _21_: put together basic data eng notes
* _18_: find visidata

https://news.ycombinator.com/item?id=42078067
> We love Postgres for its simplicity, power, and rich ecosystem. But engineers have to still get bogged down with heavyweight and expensive OLAP systems when connecting an analytics data stack.
> Postgres is amazing at OLTP queries, but not for OLAP queries (large data scans and aggregations). Even in this case, we’ve still heard from countless scaling startups that they still try to use only a read replica to run analytics workloads since they don’t want to deal with the data engineering complexity of the alternative. This actually works surprising well initially, but starts to break for them as they scale or when integrating multiple data sources. Adding lots of indexes to support analytics also slows down their transactional write performance.
> When growing out of “just use Postgres”, companies have to understand and wrangle complex ETL pipelines, CDC processes, and data warehouses — adding layers of complexity that defeat the simplicity that undermines their initial choice for Postgres as their data storage in the first place.
> We thought there had to be a better way, so we’re building BemiDB. It’s designed to handle complex analytical queries at scale without the usual overhead. It’s a single binary that automatically syncs with Postgres data and is Postgres-compatible, so it’s like querying standard Postgres and works with all existing tools.
> Under the hood, we use Apache Iceberg (with Parquet data files) stored in S3. This allows for bottomless inexpensive storage, compressed data in columnar files, and an open format that guarantees compatibility with other data tools.
> We embed DuckDB as the query engine for in-memory analytics that work for complex queries. With efficient columnar storage and vectorized execution, we’re aiming for faster results without heavy infra. BemiDB communicates over the Postgres wire protocol to make all querying Postgres-compatible.
> We want to simplify data stacks for companies that use Postgres by reducing complexity (single binary and S3), using non-proprietary data formats (Iceberg open tables), and removing vendor lock-in (open source). We'd love to hear your feedback! What do you think?

> taxonomy: backup/replicate part of pipelines?
* streaming, backups https://github.com/shayonj/pg_flo
* https://www.cs.cmu.edu/~pavlo/blog/index.html
* https://github.com/bytebase/bytebase
* https://ngrok.com/blog-post/how-we-built-ngroks-data-platform https://github.com/amalshaji/portr
* https://www.youtube.com/@jayzern/videos
* Arrow partitioning https://r4ds.hadley.nz/arrow#partitioning
* NYC taxi dataset, Parquet https://duckdb.org/2021/12/03/duck-arrow.html https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page https://tech.marksblogg.com/billion-nyc-taxi-rides-redshift.html https://iceberg.apache.org/spark-quickstart/#creating-a-table https://mattpo.pe/posts/sql-llvm/
* 📻 Macey https://softwareengineeringdaily.com/2019/07/23/data-engineering-with-tobias-macey/ https://www.dataengineeringpodcast.com/six-year-retrospective-episode-361
* course https://www.youtube.com/playlist?list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb https://r4ds.hadley.nz/
* start with data eng https://uwekorn.com/2019/10/19/taking-duckdb-for-a-spin.html https://adamdrake.com/command-line-tools-can-be-235x-faster-than-your-hadoop-cluster.html facets https://datasette.io/for/exploratory-analysis plugins https://datasette.io/tools https://datasette.io/plugins Timescale https://aliramadhan.me/2024/03/31/trillion-rows.html https://www.freecodecamp.org/learn/data-analysis-with-python/#data-analysis-with-python-course https://www.youtube.com/watch?v=v65n9yQWfVs https://www.youtube.com/watch?v=qowFCmaNFp4
* https://www.thenile.dev/blog/things-dbs-dont-do
* Conery + query sandbox https://tedconbeer.com/ https://github.com/ankane/blazer
* https://news.ycombinator.com/item?id=40488844&utm_term=comment
* datagolf https://datagolf.com/tour-standings https://datagolf.com/field-updates https://datagolf.com/datagolf-rankings https://datagolf.com/api-access
> https://www.linkedin.com/in/matthew-courchene-2a19587b/ https://www.globalgolfpost.com/featured/data-gold/ https://www.sloansportsconference.com/people/matthew-courchene https://golf.com/news/features/data-golf-analytics-new-level-pay-attention-gamblers/ https://twitter.com/DataGolf/status/1779890636537094231
> read on sports better, stats
* steampipe https://news.ycombinator.com/item?id=40343131 OS metrics queryable from SQL https://github.com/osquery/osquery
* https://news.ycombinator.com/item?id=39338626
* https://news.ycombinator.com/item?id=37222191
* https://news.ycombinator.com/item?id=35478240
* https://www.ssp.sh/brain/data-engineering/
* Cassandra https://news.ycombinator.com/item?id=41683293

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

# 🖲️ ADMIN

> I tell non-technical people that the site reliability engineer job is about creating automation to do what a system administrator would otherwise do. https://entropicthoughts.com/the-reinforcing-nature-of-toil

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

> Backups don't matter, only restores matter. https://alexgaynor.net/2024/sep/09/signatures-are-like-backups/
🗄 
* `it.md` backup
* `system.md` distributed

* short answer: dump every hour to S3 https://blog.codepen.io/2014/05/27/013-backups/ 5:00 https://simonwillison.net/about/#subscribe

---

* _DR (disaster recovery)_: https://www.lastweekinaws.com/blog/the-cold-hard-truth-about-your-cloud-dr-strategy/?ck_subscriber_id=512830619
* https://drewdevault.com/2019/01/13/Backups-and-redundancy-at-sr.ht.html
* https://github.com/eduardolat/pgbackweb
* hard drive health: 2% annual fail rate https://drewdevault.com/2020/04/22/How-to-store-data-forever.html DriveDX https://binaryfruit.com/drivedx/usb-drive-support Wear_Leveling_Count https://superuser.com/q/1037644 SMART https://en.wikipedia.org/wiki/Self-Monitoring,_Analysis_and_Reporting_Technology https://news.ycombinator.com/item?id=11110902
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

* postgres https://github.com/xataio/pgstream https://news.ycombinator.com/item?id=42383136
* https://github.com/bruin-data/ingestr
* _replication_: same data on diff nodes 📙 Kleppmann [199] https://news.ycombinator.com/item?id=37066284
* secondaries only accept writes from primary 📙 Bradshaw [236]
* very slow if synchronous https://lethain.com/distributed-systems-vocabulary/
* _lag_: when secondaries fall behind primary 📙 Bradshaw [235]
* will refuse read requests to avoid serving stale data
* _RAID_: form of replication https://www.kalzumeus.com/2010/04/20/building-highly-reliable-websites-for-small-companies/ https://news.ycombinator.com/item?id=28405695 use ZFS/Zed https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* _ZFS_: https://eradman.com/posts/zfs-quickstart.html
* backup https://github.com/benbjohnson/litestream https://github.com/maxpert/marmot https://news.ycombinator.com/item?id=30883015 SQLite for edge computing https://news.ycombinator.com/item?id=33081159
* using Redis https://andrewbrookins.com/python/scaling-django-with-postgres-read-replicas/
* Cassandra https://stackoverflow.com/questions/17348558/does-an-update-become-an-implied-insert
* always use write db vs. read replica to avoid creating 2 records
* http://eradman.com/posts/pubsub-pgoutput.html
* https://news.ycombinator.com/item?id=31341392
* cutover
> There's an ongoing sync job as well, so writes that land on the old database are pushed to the new one, so low risk of data loss.
* replicate Postgres to SQLite on the edge https://github.com/zknill/sqledge

## shard

📙 Kleppmann ch. 6 https://en.wikipedia.org/wiki/Partition_(database)
🗄️ `dbms.md` Mongo

* _partition_: diff data on diff nodes 📙 Kleppmann 199
* pruning https://eradman.com/posts/partition-pruning.html
* why: horizontal scaling, put more frequently accessed data on better hardware or more geographically proximate 📙 Bradshaw [289]
* aka sharding https://news.ycombinator.com/item?id=28776786 📙 Bradshaw [289] Kleppmann [199]
* avoid by scaling vertically as long as you can 📙 Conery imposter 343 https://news.ycombinator.com/item?id=28430852
* howto https://github.blog/2021-09-27-partitioning-githubs-relational-databases-scale/ 📙 Conery imposter 343
* https://stackoverflow.com/questions/20771435/database-sharding-vs-partitioning https://medium.com/@jeeyoungk/how-sharding-works-b4dec46b3f6 https://news.ycombinator.com/item?id=28425379
* _shard_: node in cluster 📙 Bradshaw [290]

## version control

🧠 https://chatgpt.com/c/673a8de0-7cd8-8004-9325-7943f380d4d7

* people don't really care about this https://news.ycombinator.com/item?id=22731928
* _DVC_ https://github.com/iterative/dvc https://www.youtube.com/watch?v=ITvSs23lTQE https://realpython.com/python-data-version-control/
* _Dolt_ https://github.com/dolthub/dolt

# 🌊 PIPELINE

📙 Cayla https://www.manning.com/books/data-preparation-handbook
🗄
* `data/sql.md` migrations
* `infra.md` task queue, workflow engine

---

* Bruin, Cue https://news.ycombinator.com/item?id=42442812
* https://www.youtube.com/watch?v=kGT4PcTEPP8
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
* _Airbyte_: pull from data source https://www.youtube.com/watch?v=l48zwwRSGeA https://www.youtube.com/watch?v=bXql-XSwD_s
* _bonobo_: 💀 https://github.com/python-bonobo/bonobo https://www.pythonpodcast.com/bonobo-with-romain-dorgueil-episode-143/
* _amphi_: https://github.com/amphi-ai/amphi-etl https://news.ycombinator.com/item?id=40723356
* _DLT_: https://github.com/dlt-hub/dlt https://www.youtube.com/watch?v=eMbhyOECpcE
* _DBT_: tool for transforms https://www.youtube.com/watch?v=l48zwwRSGeA 6:15 https://www.youtube.com/watch?v=O-tyUOQccSs
* Piperider https://github.com/InfuseAI/piperider https://www.youtube.com/watch?v=03MyOkIo8Hg
* workflow https://www.youtube.com/watch?v=qqlbYDfqeI4 11:00-11:15
* for unstructured https://news.ycombinator.com/item?id=42043948
* plain text vs. crappy GUI tools for analysts https://www.youtube.com/watch?v=M8oi7nSaWps 5:45 https://www.youtube.com/watch?v=qqlbYDfqeI4 9:40
* https://www.youtube.com/watch?v=UVI30Vxzd6c https://www.youtube.com/watch?v=4eCouvVOJUw https://www.youtube.com/watch?v=iMxh6s_wL4Q
* why: schema introspection, testing https://highgrowthengineering.substack.com/p/why-is-dbt-so-important- https://news.ycombinator.com/item?id=33846087
> modern data stack of Fivetran + dbt + Snowflake https://luttig.substack.com/p/dont-forget-microsoft
* create views via ETL in Snowflake (at UM)
* data ingestion from Snowflake using Snowpipe https://docs.snowflake.com/en/user-guide/data-load-snowpipe-intro.html
* util https://github.com/dbt-labs/dbt-utils
* metrics https://news.ycombinator.com/item?id=30938109
* _petl_: transforms https://petl.readthedocs.io/en/stable/
* if petl can only handle thousands of records, why not just use Pandas? https://www.youtube.com/watch?v=llRLh8cM7QI 9:30 25:00
* _Prefect_: https://www.youtube.com/watch?v=W-rMz_2GwqQ https://www.youtube.com/playlist?list=PL3MmuxUbc_hKqamJqQ7Ew8HxptJYnXqQM https://www.youtube.com/watch?v=ISLV9JyqF1w

## clean

🗄️
* `languages.md` R / tidyverse
* `python/core.md` pydantic

* _Autolabel_: https://github.com/refuel-ai/autolabel https://www.youtube.com/watch?v=TjzeaHjmiGM
* _Cleanlab_: https://github.com/cleanlab/cleanlab https://www.youtube.com/watch?v=QHaT_AiUljw

---

* https://blog.codepen.io/2023/02/01/399-data-munging/
* unstructured https://news.ycombinator.com/item?id=41236273
* anonymize/differential privacy https://www.youtube.com/watch?v=PC0bF5tstvI

SANITIZATION https://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data
* https://developer.wordpress.org/apis/security/sanitizing/ https://developer.wordpress.org/apis/security/data-validation/ https://developer.wordpress.org/apis/security/escaping/
* https://github.com/pyjanitor-devs/pyjanitor
* URL: urllib, urlparse https://github.com/gruns/furl
* _validation_: compare against rules (email, IP address) https://martinheinz.dev/blog/96
* _filter_: rm validation violations
* _escape_: convert validation violations
* _sanitize_: validate + filter/escape
* _parameterize_: sanitization for SQL https://security.stackexchange.com/a/143925

## test

https://www.milesmcbain.com/posts/assertive-programming-for-pipelines/
* _data contract_: https://github.com/benrutter/wimsey
* https://pycon-archive.python.org/2024/schedule/presentation/46/index.html
* compare data across tables https://github.com/datafold/data-diff https://github.com/paulfitz/daff 
* _Pandera_: type checking for dataframes https://endjin.com/blog/2023/03/a-look-into-pandera-and-great-expectations-for-data-validation https://www.peterbaumgartner.com/blog/testing-for-data-science/ https://www.union.ai/blog-post/pandera-joins-union-ai https://www.youtube.com/watch?v=Ax4pWz6kUDw
> From there, I create v2 of the schema, which adds Checks to the columns. Checks are information we gain after exploring the data - for example, whether a column should always be positive, whether the column name should be formatted a certain way, or whether a column should only contain certain values (e.g. a bool represented as a 0/1 int). https://www.peterbaumgartner.com/blog/testing-for-data-science/
* _GX (Great Expectations)_: assert against schema https://github.com/great-expectations/great_expectations https://softwareengineeringdaily.com/2020/02/17/great-expectations-data-pipeline-testing-with-abe-gong/ https://www.youtube.com/watch?v=8K6bU_AlUb8
> If we're expecting to repetedly read in new data, I would recommend exploring Great Expectations. The killer feature of Great Expectations is that it will generate a template of tests for the data based on a sample set of data we give it, like pandera's `infer_schema` on steroids. Again, this is only a starting point for adding in future tests (or expectations), but can be really helpful in generating basic things to test. https://www.peterbaumgartner.com/blog/testing-for-data-science/
* alternatives https://github.com/socialpoint-labs/sqlbucket https://github.com/sodadata/soda-core
```python
validator.expect_column_values_to_not_be_null(column="passenger_count")
validator.expect_column_values_to_be_between(column="congestion_surcharge", min_value=0, max_value=1000)
```

## reconciliation

* _Zingg_: entity resolution i.e. fix data integrity problems https://github.com/zinggAI/zingg

# 📦 STORE

📚
* Kleppmann [90-95]
* Serra https://www.amazon.com/Deciphering-Data-Architectures-Warehouse-Lakehouse/dp/1098150767

> Every company I worked at prior to Stripe built huge walls around their data warehouse. This resulted in a severely limited flow of information through the organization, forcing teams to use their intuition more than data analysis, since the data team would always have a miles-long backlog of requests to fulfill. Stripe is the fist place I've worked where the data warehouse is open to everyone to query and extract information that is relevant to their job. Of course, there are still strict access controls and auditing around company data, but access to relevant datasets are granted by default to team members. https://steinkamp.us/posts/2022-11-10-what-i-learned-at-stripe

STORAGE
* _data source_: where you're getting the data https://dataschool.com/data-governance
* _hot storage_: in-mem
* _cold storage_: analytics, archives https://github.com/tembo-io/pg_tier
* _data tiering_: moving cold data to (cheaper) cold storage https://github.com/tembo-io/pg_tier

SCHEMAS
* _star schema_: fact table at center
* _snowflake schema_: like star schema but more normalized
* less popular bc harder to query 📙 Kleppmann 95
* _fact table_: transactions 📙 Kleppmann 93
* w/ many FK to other dimensions 📙 Kleppmann 95
* _dimension_: non-transactional tables 📙 Kleppmann 94 https://tech.marksblogg.com/data-fluent-for-postgresql.html

SIZE
* MB = Excel, nGB-1TB = Postgres, >5TB = Hadoop https://www.chrisstucchio.com/blog/2013/hadoop_hatred.html
* typical dbms can fit 100M records in single table https://news.ycombinator.com/item?id=36038321
* _big data_: can't fit into normal dbms
* _small data_: can fit on a phone (so, half a terabyte) https://simonwillison.net/2021/Jul/22/small-data/
* complete works of Shakespeare only 5.5 MB 📙 Conery [345]
* ways of thinking about data sizes: 1MB vs. 1M seconds (12 days) 1GB vs. 1B seconds (31 years) 1TB vs. 1T seconds (317 centuries) 📙 Conery [345]
> the term Big Data is so over-used and under-defined that it is not useful in a serious engineering discussion. 📙 Kleppmann 1.9
> There are diminishing returns to the amount of information you can extract from data. The tenth gigabyte is worth much less than the second gigabyte. https://www.evanmiller.org/small-data.html

## ⭕️ factors

🗄️
* `modeling.md`
* `system.md` architecture

https://dbdb.io/ https://nchammas.com/writing/database-access-patterns
* data structures e.g. relational, document
* scale e.g. single node, distributed
* storage e.g. relational, column store
* consistency guarantee
* transaction isolation 🗄 `system.md` transactions
* _temporality_: real-time vs. historical 📻 Macey 8:30
* _embedded_: https://en.wikipedia.org/wiki/List_of_in-memory_databases https://www.openmymind.net/2011/2/10/Do-Relational-Database-Vendors-Care-About-Devs/
* _client-server_: when you have multiple clients (vs. multithreaded) or need thousands of writes/second https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html

## houses

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

### taxonomy

---

https://www.smalldatasf.com/2024
https://karenjex.blogspot.com/2024/09/optimising-your-database-for-analytics.html

> Some high level context for those less familiar with the Lakehouse storage system space. For various reasons, several companies moved from data warehouses to data lakes starting around 7-10 years ago. Data lakes are better for ML / AI workloads, cheaper, more flexible, and separate compute from storage. With a data warehouse, you need to share compute with other users. With data lakes you can attach an arbitrary number of computational clusters to the data. Data lakes were limited in many regards. They were easily corrupted (no schema enforcement), required slow file listings when reading data, and didn't support ACID transactions. https://news.ycombinator.com/item?id=34345408
* https://news.ycombinator.com/item?id=34342190
* https://www.databricks.com/blog/2020/01/30/what-is-a-data-lakehouse.html

🏭 WAREHOUSE
* = structured for analytics e.g. Redshift
* mart = subset of warehouse; uses star schema 📙 Conery [324]
* CDO https://news.ycombinator.com/item?id=37146532
* family https://news.ycombinator.com/item?id=37520374
> interesting at UM that they had an insights db, essentially a db for warehouse workloads but for the product vs. analysis
> Circa 2010, there was only one full-time analyst at the company working on data, and his laptop was effectively the company’s data warehouse. https://medium.com/airbnb-engineering/how-airbnb-achieved-metric-consistency-at-scale-f23cc53dea70
* typically different dbms from OLAP e.g. Redshift, BigQuery, Hive, Presto 📙 Kleppmann 93
* keeps more data in memory 📻 Macey 24:30
* more expensive bc optimizing for large volume and speed of access 📻 Macey 31:30

💧 LAKE
* = structured + unstructed for analytics 类似 file system e.g. Redshift
* https://www.youtube.com/watch?v=PpGivTOyawY
* https://www.youtube.com/watch?v=V0GvZ_KAI70 https://news.ycombinator.com/item?id=32336977
* table format = structure of files (Parquet) that make up lake https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html
* slower to access, has metadata (when was it produced, who owns it), batch writes, most reads will be humans doing analysis or exploration
* less expensive bc optimizing for large volume i.e. can use slower object storage 📻 Macey 31:30

🏝️ LAKEHOUSE
* =
* https://softwareengineeringdaily.com/2022/08/25/lakehouse-data-stack-with-raj-bains-2/

### options

* _csvbase_: 🎯 https://csvbase.com/ https://csvbase.com/blog/10
* _Deltalake_: lakehouse https://news.ycombinator.com/item?id=34345408
* _Hudi_: lakehouse https://news.ycombinator.com/item?id=34345408
* _Iceberg_: lakehouse https://news.ycombinator.com/item?id=34345408
* _Redshift_: warehouse https://aws.amazon.com/redshift/
* _Snowflake_:

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
* AWS S3 tables https://meltware.com/2024/12/04/s3-tables.html
* https://medium.com/expedia-group-tech/a-short-introduction-to-apache-iceberg-d34f628b6799
> Table formats have slowly been stealing the spotlight across the big data space as projects like Apache Hudi, Delta Lake and Apache Iceberg mature and disrupt the tried-and-tested legacy data lake technologies in use at most companies worldwide.
> The project [Iceberg] was originally developed at Netflix to solve long-standing issues with their usage of huge, petabyte-scale tables. It was open-sourced in 2018 as an Apache Incubator project and graduated from the incubator on the 19th of May 2020.

## metadata (Datahub)

📙 https://www.amazon.com/gp/product/1098138864

DATAHUB 📜 https://github.com/datahub-project/datahub https://datahubproject.io/
> data lineage from source to processing to consumption. https://www.thoughtworks.com/radar/platforms/summary/datahub
* features: perms/ACL, lineage, search, notes https://chatgpt.com/share/66e4a4fd-83c4-8004-b112-7935b341365d
* fka OpenMetadata https://github.com/open-metadata/OpenMetadata

---

> promising! https://github.com/zillow/intake-nested-yaml-catalog

ZA
* _catalog_: manifest (desc, location) 📻 Macey 5:15 https://data.world/solutions/product-overview/ https://softwareengineeringdaily.com/2022/12/14/the-enterprise-data-catalog/
* Collibra https://www.thoughtworks.com/radar/platforms?blipid=202203049
* OpenMetadata https://www.youtube.com/watch?v=mtUBhreZ70k

OPTIONS https://chatgpt.com/c/670d2ddc-9e9c-8004-a9a5-1852da15b853
* _Amundsen_: https://github.com/amundsen-io/amundsen
* _Atlas_: https://atlas.apache.org/
* _Marquez_: https://github.com/MarquezProject/marquez
* _OpenLineage_: https://github.com/OpenLineage/OpenLineage

# 🔍 QUERY ENGINES

🗄️
* `aws.md` compute > Athena
*️ `data/dbms.md` query engine
* `telemetry.md` Clickhouse

* _CrateDB_: https://github.com/crate/crate https://www.youtube.com/watch?v=mGxm1WPR3O8
> Modest CrateDB clusters can ingest tens of thousands of records per second without breaking a sweat. You can run ad-hoc queries using standard SQL. CrateDB's blazing-fast distributed query execution engine parallelizes query workloads across the whole cluster.

---

start here https://pycon-archive.python.org/2024/schedule/presentation/109/index.html

SEMANTICS
> https://github.com/pola-rs/polars
> Ibis is a dataframe frontend to query engines https://ibis-project.org/
> read all his posts https://maximilianmichels.com/page/4/ https://apache.org/index.html#projects-list
> is Spark a query engine? seems like query engine + streaming + a bunch other stuff i.e. a congeries https://ibis-project.org/install
> Spark: data manipulation for ML model training https://www.reddit.com/r/apachespark/comments/16zzabh/distributed_sql_query_engine_apache_spark_vs/?rdt=45095

ALTERNATIVES
* cloud: petabytes in single query and comes back in seconds/minutes e.g. Snowflake 📻 Macey 32:20
* just use CLIs https://news.ycombinator.com/item?id=39136472
* _BigQuery_: really fast https://tech.marksblogg.com/billion-nyc-taxi-rides-bigquery.html https://dataschool.com/sql-optimization/bigquery-optimization
* _Hydra_: use Postgres https://github.com/hydradatabase/hydra
* _Postgres_: https://news.ycombinator.com/item?id=39263760 https://brandur.org/warehouse https://tech.marksblogg.com/billion-nyc-taxi-rides-postgresql.html https://news.ycombinator.com/item?id=27109960
> I've also heard arguments that row-oriented systems like MySQL and PostgreSQL can fit the needs of analytical workloads as well as their traditional transactional workloads. Both of these offerings can do analytics and if you're looking at less than 20 GB of data it's probably not worth the effort of having multiple pieces of software running your data platform. https://tech.marksblogg.com/is-hadoop-dead.html
* _Snowflake_: users/investors like them https://news.ycombinator.com/item?id=24265041 https://dataschool.com/sql-optimization/snowflake/ https://www.youtube.com/watch?v=xojAXXRo_S0 OSS https://news.ycombinator.com/item?id=38038239 📙 https://www.manning.com/books/snowflake-data-engineering
* apparently a lot faster and easier to manage than a Hadoop installation https://news.ycombinator.com/item?id=24641481 
* can build dashboards off queries
* _Trino_: https://github.com/trinodb/trino https://ibis-project.org/ https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html

## ☢️ DataFusion

📜 https://datafusion.apache.org/ https://github.com/apache/datafusion

* used by Logfire, no indexes https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python

## 🦆 DuckDB

📜 https://duckdb.org/docs/ https://github.com/duckdb/duckdb
📙 Needham https://www.manning.com/books/duckdb-in-action

DESIGN
* design: columnar
* data sources: CSV, Excel, Google Sheets, Parquet, S3, Postgres, SQLite, Iceberg https://duckdb.org/docs/data/data_sources.html https://duckdb.org/community_extensions/extensions/gsheets.html

CLI
* install: Homebrew
* config fs: `$HOME/.duckdbrc`
* extensions
```sh
INSTALL sqlite;  # $HOME/.duckdb/extensions
```
* from-first syntax https://duckdb.org/docs/sql/query_syntax/from.html#from-first-syntax
* commands https://duckdb.org/docs/api/cli/overview.html
```sh
.exit
.tables
.schema $TABLE
```
* CSV https://duckdb.org/docs/data/csv/overview.html
```sh
duckdb stat-explore.db  # create db

# create table, will be automatically added to db
CREATE TABLE signups AS SELECT * FROM 'signups.csv'
.import $CSV $TABLE

.open path/to/stat-explore.db  # set as default
```

LIB
* query dataframes
```python
import duckdb
import pandas as pd
df = pd.DataFrame(pd.read_csv($FILE))  # create df
con = duckdb.connect()  # connect to DuckDB
con.register("my_df", df)  # register df with DuckDB
my_query = """ SELECT * FROM my_df """  # use registered df in query
query_res = con.execute(my_query).df()  # exec query
query_res.to_parquet('file/path.parquet')  # save
```

---

> DuckDB is a single file SQL database. https://csvbase.com/blog/6
> DuckDB is a new analytical data management system that is designed to run complex SQL queries within other processes. DuckDB has bindings for R and Python, among others. DuckDB can query Arrow datasets directly and stream query results back to Arrow. This integration allows users to query Arrow data using DuckDB's SQL Interface and API, while taking advantage of DuckDB's parallel vectorized execution engine, without requiring any extra data copying. Additionally, this integration takes full advantage of Arrow's predicate and filter pushdown while scanning datasets. https://duckdb.org/2021/12/03/duck-arrow.html
* interop btw other databases https://duckdb.org/2024/01/26/multi-database-support-in-duckdb.html
* role in ecosystem https://wesmckinney.com/blog/looking-back-15-years/
* for analytics https://news.ycombinator.com/item?id=24531085 https://news.ycombinator.com/item?id=23287278
* own flavor of SQL https://duckdb.org/2022/05/04/friendlier-sql.html
* BigFrame = BigQuery for dataframes https://www.youtube.com/watch?v=R6RYEKC0gW0 https://github.com/googleapis/python-bigquery-dataframes
* https://news.ycombinator.com/item?id=39141652
* https://www.nikolasgoebel.com/2024/05/28/duckdb-doesnt-need-data.html
* https://www.youtube.com/watch?v=yi2zgenIZm4
* https://pycon-archive.python.org/2024/schedule/presentation/130/index.html
* https://changelog.com/news/big-data-is-dead-analytics-is-alive-LGl0
* https://softwareengineeringdaily.com/2024/08/08/duckdb-with-hannes-muhleisen/
* https://www.youtube.com/watch?v=MCa0fAyfiRM
* https://www.youtube.com/watch?v=JoVHITW_WeE
* https://tech.marksblogg.com/duckdb-1b-taxi-rides.html
* https://softwareengineeringdaily.com/2022/03/18/duckdb-with-hannes-muleisen/
* https://softwaredaily.wpenginepowered.com/wp-content/uploads/2022/03/SED1439-DuckDB-with-Hannes-Muhleisen.pdf
* https://kadekillary.work/note/duckdb/
* https://tech.marksblogg.com/popular-airline-passenger-routes-2023.html

## ⦊ Presto

---

> That’s now rapidly changing; on the back-end, most modern enterprise software (e.g. Salesforce, Jira, etc.) now have good APIs for exporting data. ETL + data lakes are on the rise: Presto, for example, facilitates cross-database joins that weren’t possible just a few years ago. https://retool.com/blog/erp-for-engineers

* _Presto_: distributed query engine https://tech.marksblogg.com/presto-parquet-airpal.html https://tech.marksblogg.com/billion-nyc-taxi-rides-hive-presto.html Kafka https://tech.marksblogg.com/presto-connectors-kafka-mongodb-mysql-postgresql-redis.html
* beat out Apache Drill https://news.ycombinator.com/item?id=23250314 📙 Beaulieu [303] https://news.ycombinator.com/item?id=29063090

## ✰ Spark

---

alternative https://github.com/marsupialtail/quokka 
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
* _Databricks_: Spark aaS from creators of Spark; lakehouse, autoscaling, model training, interactive notebooks

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
