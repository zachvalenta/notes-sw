# ⛩️

## 参考

🔍 
* https://dba.stackexchange.com
* https://roadmap.sh/postgresql-dba
📚
* Connolly database systems
* Kleppmann data intensive applications
* Takahashi manga databases

## 进步

* _24_: try harlequin
* _22_: basic xsv/miller/Pandas
* _21_: put together basic data eng notes
* _20_: 📙 Kleppmann section 1
* _18_: find visidata

# 🏗️ DATA ENG

🗄
* `infra.md` queues

TYPES OF DATA
* _hot storage_: in-mem
* _cold storage_: analytics, archives https://github.com/tembo-io/pg_tier
* _data tiering_: moving cold data to (cheaper) cold storage https://github.com/tembo-io/pg_tier
* _dataset_: actual data (vs. schema) https://pgexercises.com/gettingstarted.html
* _dummy data_: fake/seed data for development; https://github.com/zachvalenta/flask-CRUD/blob/master/db_seed.py https://github.com/joke2k/faker#providers https://mimesis.name/ https://mockaroo.com/ https://github.com/Qovery/replibyte
* _synthetic data_: real data but anonymized https://softwareengineeringdaily.com/2021/02/16/synthetic-data-with-ian-coe-andrew-colombi-and-adam-kamor/ https://gretel.ai/blog/what-is-synthetic-data

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

BACKUPS 🗄 `it.md` backups `system.md` data
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

TRADITIONAL DBA https://www.lastweekinaws.com/blog/aurora-vs-rds-an-engineers-guide-to-choosing-a-database/
* install dbms
* maintenance
* monitoring
* security patches
* make backups

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
* data eng https://news.ycombinator.com/item?id=37222191
* https://news.ycombinator.com/item?id=35478240
* 📻 Macey https://softwareengineeringdaily.com/2019/07/23/data-engineering-with-tobias-macey/ https://www.dataengineeringpodcast.com/six-year-retrospective-episode-361
* https://benn.substack.com/p/work-like-an-analyst
* https://github.com/DataTalksClub/data-engineering-zoomcamp?utm_campaign=explore-email
* "data driven" https://news.ycombinator.com/item?id=34694926
* https://www.crunchydata.com/blog/is-your-postgres-ready-for-production
* https://news.ycombinator.com/item?id=35438192&utm_term=comment
* https://github.com/calpaterson/csvbase
* https://news.ycombinator.com/item?id=40352686

INDUSTRY
* _data engineer_: shepard (ETL) librarian (catalog) https://www.youtube.com/watch?v=qqlbYDfqeI4 1:45
> But if data analytics usually means extracting insights from existing data, data engineering means the process of building infrastructure to deliver, store and process the data. https://khashtamov.com/en/how-to-become-a-data-engineer/
* vs. web dev https://tech.marksblogg.com/is-hadoop-dead.html
> The above projects often aren't advertised in a way that web developers would be exposed to them. This is why someone could spend years working on new projects that are at the bottom of their S-curve in terms of both growth and data accumulated and largely never see a need for data processing outside of what could fit in RAM on a single machine.
> Web Development was a big driver in the population growth of coders over the past 25 years. Most people that call themselves a coder are most often building web applications. I think a lot of the skillsets they possess overlap well with those needed in data engineering but often distributed computing, statistics and storytelling are lacking.
> Websites often don't produce much load with any one user and often the aim is to keep the load on servers supporting a large number of users below the maximum hardware thresholds. The data world is made up of workloads where a single query is trying its best to maximize a large number of machines in order to finish as quickly as possible while keeping the infrastructure costs down.
> Companies producing PBs of data often have a queue of experienced consultants and solutions providers at their door. I've rarely seen anyone plucked out of web development by their employer and brought into the data platform engineering space; it's almost always a lengthy, self-retraining exercise.

## big data

📙 Kleppmann ch. 10

just use CLIs https://news.ycombinator.com/item?id=39136472

FACTORS
* size: can't fit into normal dbms
* velocity: challenges processor to keep up
* variety: polyglot https://www.youtube.com/watch?v=KRcecxdGxvQ 📙 Kleppmann 18

SIZE
* MB = Excel, nGB-1TB = Postgres, >5TB = Hadoop https://www.chrisstucchio.com/blog/2013/hadoop_hatred.html
* typical dbms has ~20 record table size limit https://news.ycombinator.com/item?id=36038321
* _small data_: can fit on a phone (so, half a terabyte) https://simonwillison.net/2021/Jul/22/small-data/
* complete works of Shakespeare only 5.5 MB 📙 Conery 345
* ways of thinking about data sizes: 1MB vs. 1M seconds (12 days) 1GB vs. 1B seconds (31 years) 1TB vs. 1T seconds (317 centuries) 📙 Conery 345
> the term Big Data is so over-used and under-defined that it is not useful in a serious engineering discussion. 📙 Kleppmann 1.9
> There are diminishing returns to the amount of information you can extract from data. The tenth gigabyte is worth much less than the second gigabyte. https://www.evanmiller.org/small-data.html

TOOLS
* _Hadoop_: parallelization for large data 🗄 `infra.md` EMR
* no one uses anymore? https://news.ycombinator.com/item?id=30595026 https://tech.marksblogg.com/architecting-modern-data-platforms-book-review.html https://tech.marksblogg.com/is-hadoop-dead.html
> Whereas Hadoop and big data targeted analytics applications, often in the data warehousing space, the low latency nature of Kafka makes it applicable for the kind of core applications that directly power a business 📙 Narkhede kafka 
* setup https://tech.marksblogg.com/hadoop-up-and-running.html
* you probably don't need it https://www.benkuhn.net/hard/
* relationship to other projects like Presto, Clickhouse https://tech.marksblogg.com/is-hadoop-dead.html
* _MapReduce_: map (split query into chunks, execute in parallel) reduce (merge results) 📙 Kleppmann 46
* map (match) reduce (group) https://www.practical-mongodb-aggregations.com/intro/history.html
* also a query language 📙 Kleppmann 46
* PRQL = alternative query language https://news.ycombinator.com/item?id=30060784
* _HDFS_: distributed file system http://aosabook.org/en/hdfs.html
* pools all disks from cluster
* files replicated across nodes (not all nodes; two additional copies)
* _pyspark_: Python API to Spark https://www.youtube.com/watch?v=XrpSRCwISdk
* _Spark_: Pandas + distributed
* _RDD_: collection of obj https://www.youtube.com/watch?v=XrpSRCwISdk [3:30]
* _dataframe_: table https://www.youtube.com/watch?v=XrpSRCwISdk [3:30]
* architecture: driver/lib -> executor -> operates on data https://www.youtube.com/watch?v=XrpSRCwISdk [5:10]
* similar interface as Pandas https://www.youtube.com/watch?v=XrpSRCwISdk [10:20]
* used for ML https://tech.marksblogg.com/is-hadoop-dead.html
* kinda part of Hadoop, kinda not https://tech.marksblogg.com/is-hadoop-dead.html
> At some point, the Spark community tried to distance itself from the Hadoop ecosystem. They didn't want to be seen as built on legacy software nor as some sort of "add-on" for Hadoop. Given the level of integration, Spark has with the rest of the Hadoop ecosystem and given the 100s of libraries from other Hadoop projects being used by Spark I don't subscribe to the belief that Spark is its own thing.

## BI

🗄
* `algos.md` ML / data science
* `education.md` design / information design

* https://news.ycombinator.com/item?id=40132424&utm_term=comment https://hashquery.dev/ https://github.com/hashboard-hq/hashquery
* data analyst tooling sucks as much as SQL vendors https://softwareengineeringdaily.com/2020/03/09/dbt-data-build-tool-with-tristan-handy/ 11:00 
* _Lightdash_: BI for dbt https://github.com/lightdash/lightdash
* Blazer https://github.com/ankane/blazer
* reporting https://github.com/evidence-dev/evidence
* _business intelligence (BI)_: exploration (for non-devs), reports
* ChartIO https://news.ycombinator.com/item?id=22548217
* Looker: more legacy? https://www.youtube.com/watch?v=M8oi7nSaWps 0:30 OSS version https://github.com/lightdash/lightdash
* Lux https://softwareengineeringdaily.com/2021/05/27/data-exploration-with-a-new-python-library-with-doris-lee/ https://github.com/lux-org/lux
* Tableau: via Pandas https://github.com/Kanaries/pygwalker Markdown https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=39519145
* Superset, Datalens also popular here https://news.ycombinator.com/item?id=37657772
* https://news.ycombinator.com/item?id=30323131
* OSS: Redash https://github.com/getredash/redash Poli https://github.com/shzlw/poli
* Minerva https://medium.com/airbnb-engineering/how-airbnb-achieved-metric-consistency-at-scale-f23cc53dea70
> Metrics store, sometimes referred to as headless business intelligence (BI), is a layer that decouples metrics definitions from their usage in reports and visualizations. Traditionally, metrics are defined inside the context of BI tools, but this approach leads to duplication and inconsistencies as different teams use them in different contexts. By decoupling the definition in the metrics store, we get clear and consistent reuse across BI reports, visualizations and even embedded analytics. This technique is not new; for example, Airbnb introduced Minerva a year ago. However, we're now seeing considerable traction in the data and analytics ecosystem with more tools supporting metrics stores out of the box. https://www.thoughtworks.com/radar/techniques?blipid=202210028

## OLAP

🗄 `infra.md` analytics

TAXONOMY 📙 Kleppmann [90-95]
* _data source_: where you're getting the data https://dataschool.com/data-governance
* _lakehouse_: https://softwareengineeringdaily.com/2022/08/25/lakehouse-data-stack-with-raj-bains-2/ https://www.databricks.com/
* _lake_: 类似 file system https://www.youtube.com/watch?v=V0GvZ_KAI70 https://news.ycombinator.com/item?id=32336977
* table format = structure of files (Parquet) that make up lake https://medium.com/expedia-group-tech/a-short-introduction-to-apache-iceberg-d34f628b6799
* Iceberg = SQL for table formats https://iceberg.apache.org/ https://www.thoughtworks.com/radar/platforms?blipid=202203012
* slower to access, has metadata (when was it produced, who owns it), batch writes, most reads will be humans doing analysis or exploration
* less expensive bc optimizing for large volume i.e. can use slower object storage 📻 Macey 31:30
* _warehouse_: analytics db
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

WAREHOUSE DBMS
* cloud: petabytes in single query and comes back in seconds/minutes e.g. Snowflake 📻 Macey 32:20
> I hear people arguing "a dataset can fit in memory". RAM capacity, even on the Cloud, has grown a lot recently. There are EC2 instances with 2 TB of RAM. RAM can typically be used at 12-25 GB/s depending on the architecture of your setup. Using RAM alone won't provide any failure recovery if the machine suffers a power failure. To add to this, the cost per GB will is tremendous compared to using disks. https://tech.marksblogg.com/is-hadoop-dead.html
* can always use Postgres https://brandur.org/warehouse https://tech.marksblogg.com/billion-nyc-taxi-rides-postgresql.html https://news.ycombinator.com/item?id=27109960
> I've also heard arguments that row-oriented systems like MySQL and PostgreSQL can fit the needs of analytical workloads as well as their traditional transactional workloads. Both of these offerings can do analytics and if you're looking at less than 20 GB of data it's probably not worth the effort of having multiple pieces of software running your data platform. https://tech.marksblogg.com/is-hadoop-dead.html
* _DuckDB_: embedded https://duckdb.org/ for analytics https://news.ycombinator.com/item?id=24531085 https://news.ycombinator.com/item?id=23287278 own flavor of SQL https://duckdb.org/2022/05/04/friendlier-sql.html https://softwareengineeringdaily.com/2022/03/18/duckdb-with-hannes-muleisen/ https://softwaredaily.wpenginepowered.com/wp-content/uploads/2022/03/SED1439-DuckDB-with-Hannes-Muhleisen.pdf https://kadekillary.work/note/duckdb/ https://tech.marksblogg.com/popular-airline-passenger-routes-2023.html interop btw other databases https://duckdb.org/2024/01/26/multi-database-support-in-duckdb.html https://news.ycombinator.com/item?id=39141652&utm_term=comment https://www.nikolasgoebel.com/2024/05/28/duckdb-doesnt-need-data.html
* _Clickhouse_: https://tech.marksblogg.com/clickhouse-prometheus-grafana.html https://tech.marksblogg.com/install-clickhouse-faster.html https://tech.marksblogg.com/faster-clickhouse-imports-csv-parquet-mysql.html https://tech.marksblogg.com/billion-nyc-taxi-rides-clickhouse-cluster.html
* _Presto_: distributed query engine https://tech.marksblogg.com/presto-parquet-airpal.html https://tech.marksblogg.com/billion-nyc-taxi-rides-hive-presto.html Kafka https://tech.marksblogg.com/presto-connectors-kafka-mongodb-mysql-postgresql-redis.html
* beat out Apache Drill https://news.ycombinator.com/item?id=23250314 📙 Beaulieu [303] https://news.ycombinator.com/item?id=29063090
* _BigQuery_: really fast https://tech.marksblogg.com/billion-nyc-taxi-rides-bigquery.html https://dataschool.com/sql-optimization/bigquery-optimization
* _Hydra_: use Postgres https://github.com/hydradatabase/hydra
* _Orc_: https://tech.marksblogg.com/faster-csv-to-orc-conversions.html
* _Postgres_: https://news.ycombinator.com/item?id=39263760
* _Snowflake_: users/investors like them https://news.ycombinator.com/item?id=24265041 https://dataschool.com/sql-optimization/snowflake/ https://www.youtube.com/watch?v=xojAXXRo_S0 OSS https://news.ycombinator.com/item?id=38038239
* apparently a lot faster and easier to manage than a Hadoop installation https://news.ycombinator.com/item?id=24641481 
* can build dashboards off queries
* _Redshift_: https://tech.marksblogg.com/billion-nyc-taxi-rides-redshift.html https://dataschool.com/sql-optimization/optimizing-data-queries-with-redshift/
* _Superset_: https://github.com/apache/superset https://medium.com/airbnb-engineering/how-airbnb-achieved-metric-consistency-at-scale-f23cc53dea70

## pipelines

🗄 logging

SCHEMAS
* _star schema_: fact table at center
* _snowflake schema_: like star schema but more normalized
* less popular bc harder to query 📙 Kleppmann 95
* _fact table_: transactions 📙 Kleppmann 93
* w/ many FK to other dimensions 📙 Kleppmann 95
* _dimension_: non-transactional tables 📙 Kleppmann 94 https://tech.marksblogg.com/data-fluent-for-postgresql.html

PIPELINES
* clean up https://news.ycombinator.com/item?id=34578324 https://en.wikipedia.org/wiki/Instruction_pipelining https://joblib.readthedocs.io/en/latest/index.html https://news.ycombinator.com/item?id=34578324 https://arpit.substack.com/p/how-grab-stores-and-processes-millions https://news.ycombinator.com/item?id=34483402 visidata https://www.visidata.org/blog/2020/ten/
* mv/copy from one db to another https://news.ycombinator.com/item?id=39525071 https://github.com/bruin-data/ingestr
* _transform_: 名 step that remodels data to dimensionsal https://www.youtube.com/watch?v=M8oi7nSaWps 3:30 https://news.ycombinator.com/item?id=34578324
* e.g. head/tail, add/rm col, type conversion, join https://www.youtube.com/watch?v=llRLh8cM7QI 15:50
* testing: validate integrity https://github.com/great-expectations/great_expectations https://softwareengineeringdaily.com/2020/02/17/great-expectations-data-pipeline-testing-with-abe-gong/ https://github.com/socialpoint-labs/sqlbucket
* _ETL_: mv fact tables to dimensionsal 📙 Conery 323
* howto https://www.youtube.com/watch?v=v65n9yQWfVs
* _ELT_: cp facts tables, then mv to dimensionsal https://www.youtube.com/watch?v=voC0ewDeltA 4:00
* howto https://docs.meltano.com/getting-started/meltano-at-a-glance
* allows analysts to do the transformations they need vs. having to figure it out up front https://www.youtube.com/watch?v=qqlbYDfqeI4 7:00

TOOLS
* _Airbyte_: pull from data source https://www.youtube.com/watch?v=l48zwwRSGeA
* workflow https://www.youtube.com/watch?v=qqlbYDfqeI4 11:00-11:15
* plain text vs. crappy GUI tools for analysts https://www.youtube.com/watch?v=M8oi7nSaWps 5:45 https://www.youtube.com/watch?v=qqlbYDfqeI4 9:40
* _DLT_: https://github.com/dlt-hub/dlt
* _DBT_: tool for transforms https://www.youtube.com/watch?v=l48zwwRSGeA 6:15 https://news.ycombinator.com/item?id=33846087
* create views via ETL in Snowflake (at UM)
* data ingestion from Snowflake using Snowpipe https://docs.snowflake.com/en/user-guide/data-load-snowpipe-intro.html
* metrics https://news.ycombinator.com/item?id=30938109
* why does everyone love it so much? https://highgrowthengineering.substack.com/p/why-is-dbt-so-important-
> Fivetran as the best-in-class E and L, and dbt as the corresponding T. https://luttig.substack.com/p/dont-forget-microsoft
* _GX (Great Expectations)_: https://github.com/great-expectations/great_expectations
* alternative https://github.com/sodadata/soda-core https://www.thoughtworks.com/radar/tools?blipid=202210008
> Great Expectations is a framework that allows you to craft built-in controls that flag anomalies or quality issues in data pipelines. 
* Pandera https://endjin.com/blog/2023/03/a-look-into-pandera-and-great-expectations-for-data-validation
* _petl_: transforms https://petl.readthedocs.io/en/stable/
* if petl can only handle thousands of records, why not just use Pandas? https://www.youtube.com/watch?v=llRLh8cM7QI 9:30 25:00 https://petl.readthedocs.io/en/stable/
* _Zingg_: entity resolution i.e. fix data integrity problems https://github.com/zinggAI/zingg

# 🗺️ NON-RELATIONAL

> There are data stores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Kafka), so the boundaries between the categories are becoming blurred 📙 Kleppmann [12]

* modeling from different angles https://www.openmymind.net/2011/7/5/Rethink-your-Data-Model/

* _EdgeDB_: graph-relational = no impedance mismatch but still relational https://news.ycombinator.com/item?id=30290225
* written in Python on top of Postgres https://talkpython.fm/episodes/show/355/edgedb-building-a-database-in-python

---

* _vector_: for recommendation systems, NLP https://news.ycombinator.com/item?id=35550567 https://garybake.com/vector_databases.html Pinecone https://news.ycombinator.com/item?id=35826929 https://code.dblock.org/2023/06/16/getting-started-with-vector-dbs-in-python.html https://news.ycombinator.com/item?id=37747534 https://realpython.com/chromadb-vector-database/
* Datomic (Hickey), datalog/prolog https://news.ycombinator.com/item?id=21742222 https://kevinlynagh.com/newsletter/2022_04_on_datalog_application_databases/ https://news.ycombinator.com/item?id=31154039 https://news.ycombinator.com/item?id=35094017 https://news.ycombinator.com/item?id=35727967 https://clojure.org/news/2023/08/04/next-rich https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need
* can be a problem is you need to change the PK https://calpaterson.com/non-relational-beartraps.html
> Changing the primary key of a table is a surprisingly common activity. In truth, it's pretty easy to pick something that initially looks like it will be unique but which later turns out to not be unique...Unfortunately, in many non-relational database systems the primary key is "special". For example, Dynamo-style systems will use the primary key to decide which of the partitions the record will go on.
* _polyglot persistence_: using multiple types of data stores 📙 Kleppmann 2.29 because choosing just one is no fun :) https://old.reddit.com/r/learnpython/comments/glbuog/whats_is_your_decision_process_between_csv_json/
* _CRDT_: https://news.ycombinator.com/item?id=37764581 https://blog.acolyer.org/2019/11/20/local-first-software/ https://martin.Kleppmann.com/2020/07/06/crdt-hard-parts-hydra.html https://caolan.uk/articles/inside-a-collaborative-text-editor/ vs OT (operational transformations) https://news.ycombinator.com/item?id=24176455 https://news.ycombinator.com/item?id=24617542 https://news.ycombinator.com/item?id=24790170 https://www.youtube.com/watch?v=Paau_t0aZKw https://automerge.org/ https://vlcn.io/blog/gentle-intro-to-crdts.html https://github.com/alangibson/awesome-crdt
* _block_: https://news.ycombinator.com/item?id=27200177
* immutable https://github.com/codenotary/immudb

## column

📙 Kleppmann chapter 3
🗄 `computation.md` encoding/CSV, Parquet

* _column store_: not row-oriented (like OLTP)
* can do in Sqlite? https://news.ycombinator.com/item?id=39207570&utm_term=comment
* 不明觉厉 https://news.ycombinator.com/item?id=36571110
* e.g. instead of looking for all `price` values by iterating over every sale record, just grab `price` column 📙 Kleppmann 96
* ❓ stores data differently on disk https://nchammas.com/writing/database-access-patterns
* in order to reconstruct a row, everything in row must be stored as nth in column 📙 Kleppmann 100
> Neither Parquet nor ORC files existed prior to 2012. These file formats were instrumental in making analytics fast on Hadoop. Prior to these formats, workloads were largely row-oriented. If you needed to transform TBs of data and could do so in a parallel fashion then Hadoop did a good job of that. MapReduce was a framework often used for this purpose. What columnar storage offered was a way to analyse TBs of data in seconds. This proved to be a more valuable proposition to more businesses. Data Scientists may only need a small amount of data to produce insights but they'll need to look over a data lake with potentially PBs of data to pick out what they need first. Columnar analytics is key for them to build the data fluency needed to know what to cherry-pick. https://tech.marksblogg.com/is-hadoop-dead.html
* _wide column store_: ❓

dbms https://en.wikipedia.org/wiki/List_of_column-oriented_DBMSes
* Cassandra https://stackoverflow.com/q/13010225 https://www.youtube.com/watch?v=J-cSy5MeMOA 📙 Kleppmann 99 https://news.ycombinator.com/item?id=28292369 https://simonwillison.net/2021/Aug/24/how-discord-stores-billions-of-messages/
* _Bigtable_: wide table = document store in SQL https://en.wikipedia.org/wiki/Wide-column_store
* _HBase_: Hadoop db

## document

📙 Kleppmann 2.28-42

document store
* _document_: JSON "obj"
* replaces row as paradigm 📙 Bradshaw [3]
* _schema_: structure of document https://docs.mongodb.com/realm/schemas/
* not fixed i.e. inconsistent intra-collection 📙 Bradshaw [3]
* _document reference_: UUID 📙 Kleppmann 3.38
* _field_: key
* _subdocument_: document key whose value is itself a document https://youtu.be/SM9gJv08dm0 1:20
* aka embedded 📙 Bradshaw [174]
* _collection_: group of documents

design
* 1-M w/in document itself
* M-M via document reference 📙 Kleppmann 3.38
* joins https://news.ycombinator.com/item?id=22834036
* good for 1-M or no relationships 📙 Kleppmann 2.49
* flexiblity: schema per doc aka schemaless/schema-on-read, obviates need for migrations 📙 Kleppmann 2.63, 4.111
* easier to scale/shard apparently, locality 📙 Kleppmann 2.32
* transactions only at level of single document https://docs.mongodb.com/v3.4/core/write-operations-atomicity/
* easy to have dupes 📙 Kleppmann 2.33
* hands off processing to application, so it's both slower in dev time and execution time 📙 Bradshaw [8]

dbms
* BYO https://notes.eatonphil.com/documentdb.html https://github.com/marsupialtail/quokka https://news.ycombinator.com/item?id=34189422
* _CouchDB_: good at replication https://www.dataengineeringpodcast.com/couchdb-document-database-episode-124/ 7:15 
* _Mongo_: OSS alternative https://github.com/FerretDB/FerretDB https://pythonbytes.fm/episodes/show/318/gil-how-we-will-miss-you
* _Postgres_: JSON
* _TinyDB_: embedded https://github.com/msiemens/tinydb
* alternatives https://github.com/256dpi/lungo https://github.com/vincentdchan/PoloDB
* not atomic but potential workaround https://tinydb.readthedocs.io/en/latest/extensions.html#tinyrecord
```python
from tinydb import TinyDB, Query
db = TinyDB("/path/to/db.json")
q = Query()
```

HIERARCHICAL
* _hierarchical database_: document store + tree structure i.e. child only has one parent 📙 Takahashi [39] Beaulieu [2]
* too rigid for a data store https://stratechery.com/2016/oracles-cloudy-future/ https://twobithistory.org/2017/12/29/codd-relational-model.html
* e.g. file system, DNS https://www.postgresql.org/docs/12/tutorial-concepts.html 📙 Kleppmann 2.36-38
* used in Zookeeper https://www.youtube.com/watch?v=Vv4HpLfqAz4 8:50
* can be done in relational as well https://hoverbear.org/blog/postgresql-hierarchical-structures/
* _IMS_: https://twobithistory.org/2017/10/07/the-most-important-database.html

## graph

* _network database_: similar to graph https://stackoverflow.com/a/52325525 📙 Takahashi [2.39]
* anything that would have ever been network is now SQL https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37 📙 Kleppmann [2.36]

DBMS
* embedded w/ Datalog https://news.ycombinator.com/item?id=33518320 https://github.com/cozodb/cozo
* Mongo offers as well https://www.mongodb.com/databases/mongodb-graph-database
* SQLite, Postgres https://news.ycombinator.com/item?id=35386948
* _Age_: Postgres extension https://github.com/apache/age
* _Janus_: distributed, OSS https://github.com/JanusGraph/janusgraph
* _SQLite_: https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need
* _Tao_: distributed https://news.ycombinator.com/item?id=29045443 https://www.micahlerner.com/2021/10/13/tao-facebooks-distributed-data-store-for-the-social-graph.html

QUERY LANGUAGES
* _Cypher_: declarative
* _GQL_: emerging standard https://stackoverflow.com/q/13824962 https://www.youtube.com/watch?v=h8cyPIEfxQY 11:30
* _Gremlin_: wrapper over Neo4J Java API

---

* https://www.hytradboi.com/2022/how-to-query-almost-everything
* https://www.kaseyklimes.com/notes/2019/10/16/an-augmented-mind-designing-a-personal-knowledge-base-with-notion
* _use cases_: good at relationships btw heterogenous data ("does Alice follow Bob?") w/out a million joins  📙 Kleppmann 2.49, 2.63 bad at aggregates or anything that deals w/ a few attr over many records; used for networks (IAM, knowledge mgmt, Git, recommendation engine) https://www.youtube.com/watch?v=h8cyPIEfxQY 14:30
* _dbms_: Tiger Graph, Dgraph https://softwareengineeringdaily.com/2021/01/19/dgraph-native-graphql-database-with-manish-jain/ Memgraph, Terminus db, Neo4J https://media.pragprog.com/titles/pwrdata/neo4j.pdf embedded https://github.com/CodyKochmann/graphdb https://github.com/dpapathanasiou/simple-graph cache for dgraph https://github.com/dgraph-io/ristretto
* _OGM_: ORM for graphs https://www.youtube.com/watch?v=h8cyPIEfxQY 12:30

* _property graph_: vertex (id, dict of properties, and list of incoming/outgoing edges) edge (id, dict of properties, start/end vertices and descriptive label) 📙 Kleppmann 2.50
* _triple-store_: subject (vertex) predicate, object (value or another vertex) 📙 Kleppmann 2.55 used by Datomic (Datalog query language) 📙 ibid 2.50, 60, 63
* _RDF (resource description framework)_: triple store for semantic web 📙 Kleppmann 2.57 SPARQL query language 📙 ibid 59 https://twobithistory.org/2020/01/05/foaf.html
* _types_: https://stackoverflow.com/a/59532041/6813490
* visualization https://github.com/shahinrostami/chord https://github.com/plotly/falcon
* _sink_: https://github.com/brettkromkamp/contextualise https://www.youtube.com/watch?v=GekQqFZm7mA https://www.denizcemonduygu.com/philo/ http://aosabook.org/en/500L/dagoba-an-in-memory-graph-database.html https://pragprog.com/book/pwrdata/seven-databases-in-seven-weeks-second-edition

## key

---

REDIS 📙 https://www.openmymind.net/2012/1/23/The-Little-Redis-Book/
* implementation http://aosabook.org/en/nosql.html
* test/mock https://github.com/cunla/fakeredis-py
* use Postgres as impl https://github.com/alash3al/redix
* governance https://news.ycombinator.com/item?id=23689549
* key expiration https://news.ycombinator.com/item?id=30099572
* alternative https://github.com/dragonflydb/dragonfly https://github.com/buraksezer/olric#installing
> You can either set Redis up as a "data-structures" server or you set it up right as a cache. You can't do both. If you choose to use Redis as your cache, ensure that the cache instance is only serving as your cache. Your inter-system message bus should be on a different Redis with a different configuration. https://calpaterson.com/ttl-hell.html

MEMCACHED
* _is?_: volatile cache https://news.ycombinator.com/item?id=23689549 aka application caching layer
* _how?_: distributed hash table i.e. n instances of app share 1 distributed instance of memcached
* _why?_: so you don't have to read from db
* _disadvantages_: doesn't track cache misses; meant for simple data, not tables or objects; not durable http://aosabook.org/en/nosql.html
* _sink_: https://realpython.com/python-memcache-efficient-caching/ https://github.com/thadeusb/flask-cache Django has OOB support for memcached https://docs.djangoproject.com/en/2.1/topics/cache/

* _KV store_: hash map + persistence 📙 Kleppmann [72]
* options: Redis, Bitcask
* distributed KV store used for service discovery (etcd) ()
* used for metadata, counters
> ZippyDB serves a number of use cases, ranging from metadata for a distributed filesystem, counting events for both internal and external purposes, to product data that’s used for various app features https://engineering.fb.com/2021/08/06/core-data/zippydb/
* impl: hash index; faster not bc they don't have to go to disk but bc don't have to translate in-mem data structure to something that can be written to disk 📙 Kleppmann [89]
* typed values allow for in/decrement, push/pop from list
* used for caching db result set e.g. memcached 📙 Kleppmann [89] https://github.com/akrylysov/pogreb
* dbms: embedded https://github.com/patx/pickledb https://github.com/spacejam/sled https://github.com/charmbracelet/skate https://github.com/dgraph-io/badger disk for storage https://github.com/peterbourgon/diskv
* RocksDB, memcached used as storage for distributed KV https://github.com/bitleak/kvrocks https://engineering.fb.com/2021/08/06/core-data/zippydb/ https://www.micahlerner.com/2021/05/31/scaling-memcache-at-facebook.html
* BYO: https://aosabook.org/en/500L/dbdb-dog-bed-database.html https://notes.eatonphil.com/2023-05-25-raft.html Bitcask https://github.com/avinassh/py-caskdb
> In short, keys are stored in a hash table in RAM, k/v pairs are written to log files. Dead simple, but powerful enough. https://news.ycombinator.com/item?id=31306678

za
* _object store_: KV in which K is ID and V is blob (file, binary) 🗄 `infra.md` AWS/S3
* can only create/update, not append https://stackoverflow.com/a/47524241
* sink https://ceph.io/ceph-storage/ https://github.com/minio/minio https://stackoverflow.com/questions/56627446/docker-compose-how-to-use-minio-in-and-outside-of-the-docker-network https://alexwlchan.net/2020/08/s3-keys-are-not-file-paths
* _flat file_: meant for config, no way to represent relationships or handle concurrency (e.g. prevent dirty read); some structure via delimiters, new lines https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37

## time series

🗄
* `math.md` graphs / uplot
* `infra.md` analytics

todo
* Postgres https://tembo.io/blog/pg-timeseries
* https://www.youtube.com/watch?v=nT6UsVgJ0xw
* https://www.youtube.com/watch?v=Z6pghPlZ1vQ
* time-weighted average https://blog.timescale.com/blog/what-time-weighted-averages-are-and-why-you-should-care/?
* https://www.honeycomb.io/blog/time-series-database/
* https://news.ycombinator.com/item?id=28901063
* https://www.influxdata.com/blog/start-python-influxdb
* Homebrew analytics https://docs.brew.sh/Analytics

basics
* _time series_: KV in which K is time https://en.wikipedia.org/wiki/Time_series_database
* used for monitoring 🗄 `system.md` https://github.com/VictoriaMetrics/VictoriaMetrics
* _panel data_: timeseries for individuals https://en.wikipedia.org/wiki/Panel_data

libs
* _darts_: https://github.com/unit8co/darts/
* _kats_: https://github.com/facebookresearch/kats
* _sktime_: https://github.com/alan-turing-institute/sktime

dbms
* _Influx_: https://softwareengineeringdaily.com/2019/08/21/time-series-databases-with-rob-skillington/ https://softwareengineeringdaily.com/2021/08/19/influxdata-time-series-data-with-russ-savage/
* _Husky_: event store https://www.datadoghq.com/blog/engineering/husky-deep-dive/
* _Timescale_: built on Postgres https://blog.timescale.com/blog/how-postgresql-aggregation-works-and-how-it-inspired-our-hyperfunctions-design-2/ https://softwareengineeringdaily.com/2021/06/28/timescale-time-series-databases-with-mike-freedman/
* _tstorage_: embedded https://github.com/nakabonne/tstorage BYO https://nakabonne.dev/posts/write-tsdb-from-scratch/ https://news.ycombinator.com/item?id=27730854
* _Whisper_: embedded db for Graphite https://github.com/graphite-project/whisper

# 🔬️ PLUMBING

📙 Petrov database internals
🗄
* `dbms.md` Postgres
* `system.md` distributed

---

CMU https://www.youtube.com/playlist?list=PLSE8ODhjZXjbohkNBWQs_otTrBTrjyohi https://www.youtube.com/playlist?list=PLSE8ODhjZXjasmrEd2_Yi1deeE360zv5O

https://supabase.com/blog/postgres-bloat

* _correlation_: correlation btw storage on disk and order of rows https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data
* locks https://news.ycombinator.com/item?id=35981238&utm_term=comment https://leontrolski.github.io/pglockpy.html

ASYNC
* Django: not yet supported https://docs.djangoproject.com/en/3.2/topics/async/
* Encode `databases`; adds async to SQLAlchemy https://www.encode.io/databases/database_queries/ https://fastapi.tiangolo.com/advanced/async-sql-databases/
* Postgres: can use async functions that underly synchronous `PQexec` https://www.postgresql.org/docs/9.5/libpq-async.html

SECURITY
* read-only access https://pgexercises.com/about.html
* `statement_timeout` to prevent long-running queries https://pgexercises.com/about.html https://www.postgresql.org/docs/13/runtime-config-client.html
* clear settings from connection after each statement https://pgexercises.com/about.html https://www.pgbouncer.org/
* _row-level_: limit user to specific rows https://pganalyze.com/blog/postgres-row-level-security-django-python https://news.ycombinator.com/item?id=30700899
* StrongDM records remote access sessions https://softwareengineeringdaily.com/2019/07/23/data-engineering-with-tobias-macey/

TIMEZONES
* client sould specify their timezone before querying https://hakibenita.com/sql-dos-and-donts#be-aware-of-timezones
* relational has problems w/ this https://increment.com/software-architecture/architecture-for-generations/ https://en.wikipedia.org/wiki/Temporal_database#Example https://retool.com/blog/formatting-and-dealing-with-dates-in-sql/

BYO 📙 Dibernardo, Kleppmann
* https://tontinton.com/posts/database-fundementals
* https://github.com/spandanb/learndb-py
* https://build-your-own.org/database
* https://build-your-own.org/
* https://github.com/weinberg/SQLToy https://news.ycombinator.com/item?id=26811279 https://github.com/joaoh82/rust_sqlite https://github.com/auxten/go-sqldb https://github.com/erikgrinaker/toydb/blob/master/docs/references.md?utm_source=pocket_mylist https://github.com/codecrafters-io/build-your-own-x#build-your-own-database
* https://architecturenotes.co/things-you-should-know-about-databases/
* https://www.hytradboi.com/
* https://cstack.github.io/db_tutorial/
* https://github.com/eatonphil/gosql
* https://notes.eatonphil.com/database-basics.html
* https://notes.eatonphil.com/database-basics-expressions-and-where.html
* https://notes.eatonphil.com/database-basics-indexes.html
* https://notes.eatonphil.com/database-basics-a-database-sql-driver.html

## connections

* _wire protocol_: protocol for db client-server https://datastation.multiprocess.io/blog/2022-02-08-the-world-of-postgresql-wire-compatibility.html
* e.g. can translate Mongo protocol to SQL and store in Postgres https://github.com/FerretDB/FerretDB https://pythonbytes.fm/episodes/show/318/gil-how-we-will-miss-you

order
* 1 auth 📙 Beaulieu 3.41
* 2 assigned connection ID 📙 Beaulieu 3.41

---

* how rows are stored https://ketansingh.me/posts/how-postgres-stores-rows/
* _connection_: has an ID 📙 Beaulieu [45]
* _connection pool_: cache for connections https://en.wikipedia.org/wiki/Connection_pool
* _pool_: group of open connections we keep around for when the app needs them (vs. opening a new one w/ each request or using a single one for each req) 📙 Conery IH 252 https://brettwooldridge.github.io/HikariCP/ https://brandur.org/postgres-connections
* uses TCP/IP as connection protocol
* _at dbms level_: process per connection (Postgres) coroutine per connection (RethinkDB) https://news.ycombinator.com/item?id=12649712
> The PostgreSQL server can handle multiple concurrent connections from clients. To achieve this it starts (“forks”) a new process for each connection. From that point on, the client and the new server process communicate without intervention by the original postgres process. Thus, the master server process is always running, waiting for client connections, whereas client and associated server processes come and go. - https://www.postgresql.org/docs/12/tutorial-arch.html
* _serialization_: query responses typically in binary and parsed by language specific API 📙 Kleppmann 4.128
* _sink_: https://www.usegolang.com/ in Flask https://stackoverflow.com/questions/16311974/connect-to-a-database-in-flask-which-approach-is-better https://flask.palletsprojects.com/en/1.1.x/tutorial/database/ https://github.com/questionlp/api.wwdt.me https://brandur.org/postgres-connections

## indexing

📚
* Bradshaw ch. 5
* Winand https://use-the-index-luke.com/
* https://sqlfordevs.com/ebooks/indexing
🗄
* internals/explain
* `algos.md` search engine
* `vim.md` ctags

start here
* https://www.jefftk.com/p/you-dont-always-need-indexes
* make invisible > delete https://sqlfordevs.com/invisible-index-before-delete
* https://news.ycombinator.com/item?id=35978757&utm_term=comment
* Postgres has partial indexes
* notes for Karwin chapter 13
> mention of caching? https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data
* https://calpaterson.com/how-a-sql-database-works.html
* https://dataschool.com/sql-optimization/how-indexing-works/
* BRIN https://hakibenita.com/sql-tricks-application-dba#index-columns-with-high-correlation-using-brin https://www.highgo.ca/2020/06/22/types-of-indexes-in-postgresql/
* https://www.youtube.com/watch?v=HubezKbFL7E
* Beaulieu chapter 13, 15
* Faroult 3
* https://github.com/BurntSushi/xsv
* https://news.ycombinator.com/item?id=32250426
* ghost conditions https://sqlfordevs.com/ghost-conditions-for-unindexed-columns

basics
* _index_: binning vs. full table scan 📙 Evans 24
```sql
CREATE INDEX idx_fk_country_id ON city(country_id) -- https://github.com/jOOQ/sakila/blob/main/sqlite-sakila-db/sqlite-sakila-schema.sql
```
* impl: metadata as tree
* subset of data (vs. concordance)
* why: faster reads but slower writes 📙 Kleppmann [71] Karwin [6]
> If you need to access data quickly, you index it...that's 90% of what you need to know https://www.bennadel.com/blog/3467-the-not-so-dark-art-of-designing-database-indexes-reflections-from-an-average-software-engineer.htm
* _vacuum_: 📍 https://news.ycombinator.com/item?id=29858083
* _reindex_: 📍 https://news.ycombinator.com/item?id=29858083

types https://www.highgo.ca/2020/06/22/types-of-indexes-in-postgresql/
* _covering_: store additional columns in index https://hakibenita.com/django-32-exciting-features#covering-indexes
> A covering index is when you have an index and it has multiple columns in the index and you’re doing a query on just the first couple of columns in the index and the answer you want is in the remaining columns in the index. When that happens, the database engine can use just the index. It never has to refer to the original table, and that makes things go faster if it only has to look up one thing. https://corecursive.com/066-sqlite-with-richard-hipp/
* _primary_: keeping track of order of entry i.e. having a primary key 📙 Kleppmann 85
* _partial_: normal index + `WHERE` clause https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions https://hakibenita.com/sql-tricks-application-dba https://dataschool.com/sql-optimization/partial-indexes/ 📙 Bradshaw [5]
* _secondary_: https://calpaterson.com/non-relational-beartraps.html 📙 Kleppmann [85] Bradshaw [5]
* _multicolumn_: aka concatenated 📙 Kleppmann 87 https://dataschool.com/sql-optimization/multicolumn-indexes/

data structures
* _b-tree_: most popular 📙 Kleppmann 83 Winand vii
* sorted keys, pointers to range of keys on disk 📙 Kleppmann 80
* bad for filtering? https://sirupsen.com/napkin/problem-13-filtering-with-inverted-indexes
* diff than hash index bc in memory and updates in place (vs. append-only) 📙 Kleppmann 80
> Several data structures, such as B+Trees, help NoSQL systems quickly retrieve data from disk. Updates to those structures result in updates in random locations in the data structures' files, resulting in several random writes per update if you fsync after each update. http://aosabook.org/en/nosql.html
* _bitmap index_: used for low-cardinality columns https://en.wikipedia.org/wiki/Bitmap_index https://www.youtube.com/watch?v=5imhr4ye3Tw 📙 Kleppmann 97, 561
* semantic confusion? https://en.wikipedia.org/wiki/Bitmap https://github.com/RoaringBitmap/roaring
* bitmap scan https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data https://spacelift.io/blog/tricking-postgres-into-using-query-plan
* _hash index_: in-mem hash table
* V location in physical storage e.g. append-only log as in Riak Bitcask 📙 Kleppmann 72
* hash table must fit in memory 📙 Kleppmann 75 https://hakibenita.com/postgresql-hash-index
* _SSTable (sorted string)_: hash index but sorted keys 📙 Kleppmann 76
* doesn't need to have all keys in memory 📙 Kleppmann 77
* impl w/ LSM tree 📙 Kleppmann 78
* _LSM tree_: faster for writes 📙 Kleppmann 83 https://news.ycombinator.com/item?id=35634673
* compress more easily 📙 Kleppmann 84
* used in Cassandra, LevelDB 📙 Kleppmann 79, 85 https://nakabonne.dev/posts/write-tsdb-from-scratch/ 🗄 `algos.md` trees
* _BRIN_: https://hakibenita.com/sql-tricks-application-dba#index-columns-with-high-correlation-using-brin

## internals

parse -> plans -> engine https://pganalyze.com/blog/how-postgres-chooses-index
* _database engine_: container for components https://www.sqlite.org/draft/queryplanner.html https://www.practical-mongodb-aggregations.com/intro/introducing-aggregations.html
* lexer: lex, yac https://news.ycombinator.com/item?id=30086374 https://www.interdb.jp/pg/index.html
* _parser_: https://github.com/reata/sqllineage 🗄 `language.md` compiler
* https://tokern.io/blog/open-source-sql-parsers/
* transpile btw Presto, Hive Spark https://github.com/tobymao/sqlglot
* _query optimizer_: generates query plans, picks execution plan 📙 Beaulieu [46] https://news.ycombinator.com/item?id=30855639
* returns hints 📙 Beaulieu [46]
* aka querry planner 📙 Bradshaw [167]
> decides which parts of the query to execute in which order and which indexes to use 📙 Kleppmann 37
* cost-based 📙 Kleppmann 427 https://blog.jooq.org/10-cool-sql-optimisations-that-do-not-depend-on-the-cost-model/ https://pghintplan.osdn.jp/pg_hint_plan.html
* ❓ virtual machine https://news.ycombinator.com/item?id=32750676
* _query plan_: output from query optimizer imperative steps to impl declarative SQL https://www.youtube.com/watch?v=IwahVdNboc8 https://dataschool.com/sql-optimization/what-is-a-query-plan/
* _execution plan_: query plan chosen by optimizer 📙 Beaulieu [46]
> There is a trade-off between the amount of time spent figuring out the best query plan and the quality of the choice https://en.wikipedia.org/wiki/Query_optimization
* _query hint_: explicitly tell optimizer what to do 📙 Beaulieu 3.42 https://en.wikipedia.org/wiki/Hint_(SQL)
* Postgres doesn't support https://wiki.postgresql.org/wiki/Todo
* _query engine_: executes query plan https://en.wikipedia.org/wiki/Presto_(SQL_query_engine) https://news.ycombinator.com/item?id=27006476

explain 🗄 indexing
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

STORAGE ENGINES 🗄 `system.md` transactions
* _journal_: journaling i.e. keep track of transactions? https://fly.io/blog/sqlite-internals-rollback-journal/
* _storage engine_: handle transactions, maintain index https://stackoverflow.com/a/39204302
* row-oriented vs. column-oriented 📙 Kleppmann 586
* log-structured (Riak Bitcask) 📙 Kleppmann 72
* page-oriented 📙 Kleppmann 70 https://sirupsen.com/napkin/problem-6 https://news.ycombinator.com/item?id=32250426
* _Berkeley DB_: https://corecursive.com/066-sqlite-with-richard-hipp/
* _InnoDB_: MySQL; locks table row during transaction
* _MyISAM_: locks whole table https://stackoverflow.com/a/5414622/6813490 
* _WiredTiger_: Mongo 📙 Bradshaw [6]
* _OrioleDB_: for Postgres https://github.com/orioledb/orioledb/
> OrioleDB is a new storage engine for PostgreSQL. Our teams use PostgreSQL a lot, but its storage engine was originally designed for hard drives. Although there are several options to tune for modern hardware, it can be difficult and cumbersome to achieve optimal results. OrioleDB addresses these challenges by implementing a cloud-native storage engine with explicit support for solid-state drives (SSDs) and nonvolatile random-access memory (NVRAM). To try the new engine, first install the enhancement patches to the current table access methods and then install OrioleDB as a PostgreSQL extension. We believe OrioleDB has great potential to address several long-pending issues in PostgreSQL, and we encourage you to carefully assess it. https://www.thoughtworks.com/radar/platforms?blipid=202210068

## logging

* _log_: append-only data file; used to deal w/ concurrency 📙 Kleppmann 71
* _segment_: chunk of log; immutable 📙 Kleppmann 73
* _compaction_: rm dupe keys from log; done by plucking most recent update for key and writing to new, smaller segment file; done in background while continuing to use existing segments for read/write 📙 Kleppmann 73
* fsync log instead of fsyncing data itself to increase throughput? http://aosabook.org/en/nosql.html
> Several data structures, such as B+Trees, help NoSQL systems quickly retrieve data from disk. Updates to those structures result in updates in random locations in the data structures' files, resulting in several random writes per update if you fsync after each update. To reduce random writes, systems such as Cassandra, HBase, Redis, and Riak append update operations to a sequentially-written file called a log. While other data structures used by the system are only periodically fsynced, the log is frequently fsynced. By treating the log as the ground-truth state of the database after a crash, these storage engines are able to turn random updates into sequential ones. While NoSQL systems such as MongoDB perform writes in-place in their data structures, others take logging even further. Cassandra and HBase use a technique borrowed from BigTable of combining their logs and lookup data structures into one log-structured merge tree. Riak provides similar functionality with a log-structured hash table. CouchDB has modified the traditional B+Tree so that all changes to the data structure are appended to the structure on physical storage. These techniques result in improved write throughput, but require a periodic log compaction to keep the log from growing unbounded.

types
* _command log_: log commands to change state but not incremental changes
* _append-only log_: immutability at the db level; conflict w/ GDPR https://www.bloorresearch.com/2018/02/append-databases-gdpr-conundrum/
* _write-ahead log (WAL)_: log changes in state before update so you can recover if failure (power, OS, hw) https://softwareengineeringdaily.com/wp-content/uploads/2018/06/SED613-Database-Reliability-Engineering.pdf BYO https://github.com/khonsulabs/okaywal logical decoding messages https://www.infoq.com/articles/wonders-of-postgres-logical-decoding-messages/ https://pgdash.io/blog/taming-postgresql-wal-file-growth.html
* used in b-tree 📙 Kleppmann 84
* individual entries known as frames https://news.ycombinator.com/item?id=26583558
* turn off if you're just doing a transformation https://hakibenita.com/sql-tricks-application-dba#use-unlogged-tables-for-intermediate-data

## perf

📙 Winand sql perf https://use-the-index-luke.com/

---

* should `explain analyze` be here?

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

# 🛠️ TOOLING

🗄 `shell.md` munge

ZA
* compare queries across dbms https://github.com/rickbergfalk/sqlpad
* compare data across tables https://github.com/datafold/data-diff https://github.com/paulfitz/daff

API / CODE GENERATION
* https://github.com/directus/directus
* Postgrest https://github.com/PostgREST/postgrest https://news.ycombinator.com/item?id=30132947 https://github.com/prest/prest
* GraphQL https://www.graphile.org/postgraphile/ 
* query SQLite over HTTP https://news.ycombinator.com/item?id=30636796
* ROAPI https://github.com/roapi/roapi https://tech.marksblogg.com/roapi-rust-data-api.html
* Datasette https://www.youtube.com/watch?v=pTr1uLQTJNE https://www.hytradboi.com/2022/datasette-a-big-bag-of-tricks-for-solving-interesting-problems-using-sqlite
* DBCore https://github.com/eatonphil/dbcore https://notes.eatonphil.com/generating-a-rest-api-from-a-database.html
* Octo https://github.com/octoproject/octo-cli
* https://github.com/thevahidal/soul

AGGREGATE/ANALYSIS
* dedupe https://github.com/moj-analytical-services/splink https://sqlfordevs.com/delete-duplicate-rows
* view missing https://github.com/ResidentMario/missingno
* https://hakibenita.com/sql-for-data-analysis#descriptive-statistics
* https://hakibenita.com/sql-for-data-analysis#sampling
* reservoir sampling https://en.wikipedia.org/wiki/Reservoir_sampling https://github.com/BurntSushi/xsv
* stats https://github.com/capitalone/dataprofiler
* can use R from command line https://missing.csail.mit.edu/2020/data-wrangling/ https://www.r-project.org/

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

SANITIZATION https://codex.wordpress.org/Validating_Sanitizing_and_Escaping_User_Data
* munge https://realpython.com/python-for-data-analysis/
* _validation_: compare against rules
* Pydantic https://www.pythonpodcast.com/pydantic-data-validation-episode-263/ https://github.com/shopnilsazal/validus https://blog.couchbase.com/validate-json-documents-in-python-using-pydantic/
* Cerberus https://github.com/pyeve/cerberus https://hector.dev/2020/12/29/validating-data-in-python-with-cerberus.html
* BYO https://realpython.com/primer-on-python-decorators/#more-real-world-examples https://blog.drewolson.org/declarative-validation
* _filter_: rm validation violations 
* _escape_: convert validation violations
* _sanitize_: validate + filter/escape
* _parameterize_: sanitization for SQL https://security.stackexchange.com/a/143925

## dataclerk

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
* documentation https://github.com/k1LoW/tbls
* parser https://news.ycombinator.com/item?id=32560039
* visidata for now and add constraints later?
* ERD?
* https://github.com/szktkfm/mdtt
* https://stackoverflow.com/questions/2732356/list-of-all-tables-with-a-relationship-to-a-given-table-or-view
* https://stackoverflow.com/questions/8094156/know-relationships-between-all-the-tables-of-database-in-sql-server
* https://stackoverflow.com/questions/5499003/sqlite-list-all-foreign-keys-in-a-database
```python
# https://stackoverflow.com/a/59171912
SELECT * FROM pragma_foreign_key_list('reading');
# next step is running this from sqlite3
```

## dbcli

📜
* https://litecli.com/
* https://www.pgcli.com

CMD
* open with env var: `cli -h`
* exit: `exit`, `\q`
* list tables: `\dt`
* help: `\?`
* autocomplete: `ctrl e`
* autocomplete: `ctrl e`
* clear screen: `ctrl l`
* _metacommand_: preceded w/ backslash https://www.pgcli.com/commands
* set pager to bat: `pager = less -SRXF` https://www.pgcli.com/docs

NAMED QUERIES
* 📍 open PR: print query on usage (less_chatty?)
* _named query_: snippet, saved query https://www.pgcli.com/named_queries.md
* syntax: `f` (litecli) `n` (pgcli)
* list: `\f` https://github.com/dbcli/pgcli/issues/1236
* save: `\fs <name> <query>` https://github.com/dbcli/pgcli/issues/938
* save w/ param: `\fs <name> <query where foo = $1>` https://github.com/dbcli/pgcli/issues/938
> broken in sandbox: could be pager, Python version, config (try default config installed in $HOME) https://github.com/dbcli/pgcli/search?q=codec&type=issues
* use: `\f <name>`
* use w/ param: `\f <name> "arg"`
* rm: `\fd <name>` https://litecli.com/favorites/

## harlequin

📜 https://harlequin.sh

> try this instead https://github.com/quarylabs/quary

* have to import CSV files after opening harlequin? import via data catalog? via `conn_str = ["local.db"]`? https://github.com/tconbeer/harlequin/discussions/314
* profiles: sqlite, duckdb, postgres
* Django https://adamj.eu/tech/2024/05/07/django-harlequin/

## miller

📜 https://miller.readthedocs.io/en/latest/glossary https://miller.readthedocs.io/en/latest/reference-verbs/

BASICS
```sh
# select *
cat <csv>

# limit
head -n 5 <csv>

# select col = -o -f col
cut -o -f "col1","col2" <csv>

# ignore col = -x -f co l
cut -x -f "col1","col2" <csv>

# chaining
head -n 20 then cut -o -f "id","artist" then sort -f "artist" <csv>
```

PREDICATES, GROUPING
```sh
# uniq for header
uniq -g <header> <csv> | wc -l

# select * where header = val
filter '$header == "value"' example.csv
filter '$header1 == "value-foo"' && '$header2 == "value-bar"' example.csv
filter 'is_null($header)' example.csv # https://miller.readthedocs.io/en/latest/reference-dsl-builtin-functions/
filter '$earnings > 0.0' example.csv

# most frequent value by header
most-frequent -f col -n 1000 example.csv

# most frequent value by header + group by header
most-frequent -f col -n 1000 example.csv | mlr --opprint sort -f col

# put = computed fields
# ${field} for fields w/ spaces
--c2p cut -o -f "21.08","21.09" then put '${total} = ${21.08} + ${21.09}' <csv>
```

IO
```sh
--icsv    # input csv
--opprint # output pprint
--c2p     # combine --icsv and --opprint https://miller.readthedocs.io/en/latest/keystroke-savers/#short-format-specifiers-including-c2p
--csv     # IO csv
```

CONFIG https://miller.readthedocs.io/en/latest/customization/
* view colors: `--list-color-names` https://miller.readthedocs.io/en/latest/output-colorization/
* `.mlrrc`
```sh
c2p  # --c2p
allow-ragged-csv-input  # if data line fields > header line, insert empty val instead of err (CSV header/data length mismatch)
```

## Pandas

---

Pandas, arrow, Polars, Ibis https://talkpython.fm/episodes/show/462/pandas-and-beyond-with-wes-mckinney https://ibis-project.org/
* McKinney https://wesmckinney.com/book/

tables https://posit-dev.github.io/great-tables https://posit-dev.github.io/great-tables/blog/design-philosophy/

📜 https://pandas.pydata.org/docs/
📹 https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS https://talkpython.fm/episodes/show/358/understanding-pandas-visually-with-pandastutor
🔍 
* https://kadekillary.work/posts/embarrassment-of-pandas/
* https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf https://github.com/maxhumber/redframes
* https://github.com/jvns/pandas-cookbook
* https://web.archive.org/web/20230127194856/https://scribe.citizen4.eu/pandas-illustrated-the-definitive-visual-guide-to-pandas-c31fa921a43
📚
* VanderPlas https://jakevdp.github.io/PythonDataScienceHandbook/

semantics
* _dataframe_: table https://www.youtube.com/watch?v=zmdjNSmRXF4 10:00
* _series_: 1d array https://pandas.pydata.org/docs/user_guide/10min.html#getting https://pandas.pydata.org/docs/user_guide/dsintro.html#series

* dataframes
```python
# load
import pandas as pd
df = pd.DataFrame(pd.read_csv("filename.csv"))  # https://kadekillary.work/posts/csvs-pandas/

# iteration https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas https://stackoverflow.com/questions/50267185/iterate-over-pandas-series don't iterate https://realpython.com/pandas-iterate-over-rows/
for series in df.iterrows():

# predicate
df[df["company"] == "ABC corp"]  # equality
df[df["earnings"] > 0]  # comparison
df[(df["col1"] >= 1) & (df["col1"] <=1 )]  # uses indexing https://stackoverflow.com/a/13616382
```

* grouping
```python
# iteration 📙 McKinney [291]
for gk, grp in df.groupby("isrc"):
    pass

# csv per group https://stackoverflow.com/a/50818244
df = pd.DataFrame(pd.read_csv("paintings.csv"))
path = os.path.join(os.getcwd(), "output_dir")
for i, (name, group) in enumerate(df.groupby("ARTIST")):
    group.to_csv("{}/{}.csv".format(path, name.replace(" ", "").lower()))

# verify totals per group
invalid = list()
for _, (foo, group) in enumerate(df.groupby("foo")):
    if int(group["bar"].sum()) != 100:
        invalid.append(foo)
log.info("foo count - invalid: {}".format(len(invalid)))
```

snippets
```python
myl = [foo, bar]

# SHAPE https://stackoverflow.com/a/35523946
df.shape[0]  # count - rows
df.shape[1]  # count - col

# SELECT
df.col   # get col https://pandas.pydata.org/docs/user_guide/10min.html#getting
df[0:3]  # get row

# bool for each row
df.col.isin(myl)
# row index for True bool
df.index[df.col.isin(myl)]
# drop row indexes for rows matching list el
df.drop(df.index[df.col.isin(myl)])

# all col
df.columns
# n col
df[["col1", "col2"]]
# get row by row index
df.iloc[3]
# get row by row index + col index e.g. row 3 col 17
df.iloc[3, 17]
# get n row by row index e.g. rows 3 and 42
df.iloc[[3, 42]]

# persist foo w/ valid bar
verified = df.drop(df.index[df.foo.isin(invalid)])
log.info("count - verified: {}".format(len(set(verified.foo))))
verified.to_csv(os.path.join(os.getcwd(), out_file))
```

za
* DataFrame protocol https://ponder.io/how-the-python-dataframe-interchange-protocol-makes-life-better/ https://ponder.io/why-are-there-so-many-python-dataframes/
* `inplace` https://sourcery.ai/blog/pandas-inplace/
* _Polars_: https://news.ycombinator.com/item?id=35423569 https://github.com/pola-rs/polars https://pythonspeed.com/articles/polars-memory-pandas/ https://www.confessionsofadataguy.com/replacing-pandas-with-polars-a-practical-guide/ https://realpython.com/polars-python/ https://pythonspeed.com/articles/polars-pandas-interopability/ https://pola.rs/posts/polars_birds_eye_view/
* method chaining https://github.com/pyjanitor-devs/pyjanitor
* validation https://github.com/pandera-dev/pandera
* perf https://hakibenita.com/sql-for-data-analysis#sql-vs-pandas-performance https://pythonspeed.com/memory
* test https://github.com/pandera-dev/pandera https://www.peterbaumgartner.com/blog/testing-for-data-science/
* version: 1.15 works w/ Python 3.6 https://pypi.org/project/numpy/#history 🗄 `ml/grok-ml`

## spreadsheet

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
* ubiquity https://news.ycombinator.com/item?id=26386419 https://www.wsj.com/articles/stop-using-excel-finance-chiefs-tell-staffs-1511346601 https://news.ycombinator.com/item?id=28595155 https://dataingovernment.blog.gov.uk/2019/06/10/improving-how-we-manage-spreadsheet-data/ https://medium.com/backchannel/a-spreadsheet-way-of-knowledge-8de60af7146e
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

## visidata

🔍 https://stackoverflow.com/questions/tagged/visidata
📜
* docs http://visidata.org/docs/
* guide https://jsvine.github.io/intro-to-visidata/
* ref https://jsvine.github.io/visidata-cheat-sheet/en/

* null = those yellow crossed out circles https://www.visidata.org/docs/rows/

⬇️ ATTR https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/
* search: `/`
* nav: `hl`, `gh/gl`
* rename: `^`
* mv: `H/L`
* create blank: `za` https://jsvine.github.io/intro-to-visidata/intermediate/creating-new-columns
* hide/remove: `-` / `gv`
* expand width to fit text: `_` (single) `g_` (all)
* shrink by 1/2: `z-`
* expand json: `()`

⏭ RECORDS
* mv: `SHIFT j/k`
* sort: `[]`
* page: `ctrl b/f`
* select: `s/u` (single) `gs/gu` (all)
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

---

* alternatives https://github.com/mathaou/termdbms https://github.com/chrisbra/csv.vim
* EDA
> When you get a fresh data set, the first thing you usually want to do is get familiar with it. Some people call this "Exploratory data analysis" [EDA]. https://hakibenita.com/sql-for-data-analysis#descriptive-statistics https://medium.com/epfl-extension-school/advanced-exploratory-data-analysis-eda-with-python-536fa83c578a

* visidata config: default to col full expansion
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

## xsv

📜 https://github.com/BurntSushi/xsv

```sh
# count records
count songs.csv

# get headers
headers songs.csv

# split into n files
split -s <records_per_file> <output-dir> <csv>

# all from header
select "header" <csv>

# search within header (case insensitive)
search -i -s "header" "query" <csv>

# stats (sum, min, max)
stats <table> | xsv table

# get sampled subset
xsv sample 50 full.csv > sample.csv

# get line of data and display as two columns
xsv slice -i 0 csv | xsv flatten
```

## UI

TUI
* _dadbod_: harlequin for Neovim https://github.com/kristijanhusak/vim-dadbod-ui https://www.youtube.com/watch?v=NhTPVXP8n7w
* _harlequin_: ✅ query editor https://harlequin.sh
* _GoBang_: perpetual alpha https://github.com/TaKO8Ki/gobang
* _visidata_: ✅ data exploration

GUI
* NoSQL: Table Plus https://news.ycombinator.com/item?id=22908224 DbGate https://github.com/dbgate/dbgate
* SQLite: DB4S https://github.com/sqlitebrowser/sqlitebrowser https://github.com/coleifer/sqlite-web
* Postgres: pgAdmin, PGweb https://github.com/centerofci/mathesar
* _Beekeeper_: $7/month https://www.beekeeperstudio.io/
* _Datagrip_: $25/month, ERD
* _DBeaver_: OSS, ERD https://stackoverflow.com/a/48397209
* _Ultorg_: 🎯 $35/month, queryless joins, very interesting interface https://www.hytradboi.com/2022/ultorg-a-user-interface-for-relational-databases

FEATURES
* data entry: https://github.com/centerofci/mathesar 🗄 dataclerk
* follow FKs: https://github.com/Wisser/Jailer https://github.com/centerofci/mathesar
* _data catalog_: dbs, tables https://harlequin.sh
* _ERD_: https://databasediagram.com/ https://drawdb.vercel.app/
* _query editor_: save, autocomplete
* _results viewer_: result set
