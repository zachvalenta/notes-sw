# ⛩️

## 参考

> All models are wrong, but some are useful - George Box 📙 Zuckerman simons [245]
🗄
*️ `OLAP.md` factors
* `data/internals.md`
* `science.md` metascience / categories
* `sql.md` schema / approaches
📚
* Alexopoulos semantic https://www.amazon.com/gp/product/1492054275
* Kent data/reality https://www.amazon.com/Data-Reality-Perspective-Perceiving-Information/dp/1935504215

## 进步

https://swizec.com/blog/why-software-only-moves-forward/

🔍 https://drawsql.app/templates
* enum > FK
* modeling payments https://news.ycombinator.com/item?id=36775098
* https://news.ycombinator.com/item?id=41146239&utm_term=comment

IMPORTANCE
> Data models are perhaps the most important part of developing software, because they have such a profound effect: not only on how the software is written, but also how we think about the problem that we are solving. 📙 Kleppmann [31]
> This is one reason it's so important to model your domain correctly: if, for example, you make something a property of A when it should be a property of B, the penalty is often that operations that formerly required checking all the As or all the Bs now require checking all the As and all the Bs. https://www.natemeyvis.com/writing/on-quadratic-complexity/
> Take data access patterns very seriously!...it's easy to turn something that should be logarithmic time into polynomial time https://calpaterson.com/activerecord.html

SEMANTICS
* _domain_: thing you're trying to model https://calpaterson.com/non-relational-beartraps.html
* _schema_: model of thing https://calpaterson.com/non-relational-beartraps.html
* general usage: table names + column name/type https://news.ycombinator.com/item?id=22723277
* Postgres usage: container for obj such as table or view https://news.ycombinator.com/item?id=22721914

https://news.ycombinator.com/item?id=42245927
abstraction and math https://neugierig.org/content/dfw/

# 🗺️ NON

📙 Kleppmann ch. 2
🗄️ `data/graphs.md`

> There are data stores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Kafka), so the boundaries between the categories are becoming blurred 📙 Kleppmann [12]

* modeling from different angles https://www.openmymind.net/2011/7/5/Rethink-your-Data-Model/

---

* Datomic (Hickey), datalog/prolog https://news.ycombinator.com/item?id=21742222 https://kevinlynagh.com/newsletter/2022_04_on_datalog_application_databases/ https://news.ycombinator.com/item?id=31154039 https://news.ycombinator.com/item?id=35094017 https://news.ycombinator.com/item?id=35727967 https://clojure.org/news/2023/08/04/next-rich https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need https://news.ycombinator.com/item?id=41642969
* can be a problem is you need to change the PK https://calpaterson.com/non-relational-beartraps.html
> Changing the primary key of a table is a surprisingly common activity. In truth, it's pretty easy to pick something that initially looks like it will be unique but which later turns out to not be unique...Unfortunately, in many non-relational database systems the primary key is "special". For example, Dynamo-style systems will use the primary key to decide which of the partitions the record will go on.
* _polyglot persistence_: using multiple types of data stores 📙 Kleppmann 2.29 because choosing just one is no fun :) https://old.reddit.com/r/learnpython/comments/glbuog/whats_is_your_decision_process_between_csv_json/
* _block_: https://news.ycombinator.com/item?id=27200177
* immutable https://github.com/codenotary/immudb

## document

---

📙 Kleppmann 2.28-42

https://news.ycombinator.com/item?id=42103788

> The thrust of it is that databases that are in the same genre as DynamoDB - which includes Cassandra and MongoDB - are fantastic if - and this is a load bearing if: You know exactly what your app needs to do, up-front. You know exactly what your access patterns will be, up-front. You have a known need to scale to really large sizes of data. You are okay giving up some level of consistency. This is because this sort of database is basically a giant distributed hash map. The only operations that work without needing to scan the entire database are lookups by partition key and scans that make use of a sort key. Whatever queries you need to make, you need to encode that knowledge in one of those indexes before you store it. You want to store users and look them up by either first name or last name? Well you best have a sort key that looks like `$FIRST_NAME $LAST_NAME>`. Your access patterns should be baked into how you store your data. If your access patterns change significantly, you might need to reprocess all of your data. https://mccue.dev/pages/8-16-24-just-use-postgres

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

DBMS
* BYO https://notes.eatonphil.com/documentdb.html
* _CouchDB_: good at replication https://www.dataengineeringpodcast.com/couchdb-document-database-episode-124/ 7:15 
* _Dante_: 🎯 embedded https://github.com/senko/dante
* _DocumentDB_: https://github.com/microsoft/documentdb
* _Lungo_: 🎯 embedded, Mongo compatible Golang impl https://github.com/256dpi/lungo
* _JameSQL_: 🎯 embedded https://github.com/capjamesg/jamesql
* _Mongo_: OSS alternative https://github.com/FerretDB/FerretDB https://pythonbytes.fm/episodes/show/318/gil-how-we-will-miss-you
* _Polo_: embedded https://github.com/vincentdchan/PoloDB
* _Postgres_: JSON
* _TinyDB_: 🎯 embedded https://github.com/msiemens/tinydb
* not atomic but potential workaround https://tinydb.readthedocs.io/en/latest/extensions.html#tinyrecord

HIERARCHICAL
* _hierarchical database_: document store + tree structure i.e. child only has one parent 📙 Takahashi [39] Beaulieu [2]
* too rigid for a data store https://stratechery.com/2016/oracles-cloudy-future/ https://twobithistory.org/2017/12/29/codd-relational-model.html
* e.g. file system, DNS https://www.postgresql.org/docs/12/tutorial-concepts.html 📙 Kleppmann 2.36-38
* used in Zookeeper https://www.youtube.com/watch?v=Vv4HpLfqAz4 8:50
* can be done in relational as well https://hoverbear.org/blog/postgresql-hierarchical-structures/
* _IMS_: https://twobithistory.org/2017/10/07/the-most-important-database.html

## graph

---

* _PGQ_: property graph queries https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
> SQL now supports defining read-only queries on graphs. This allows an application to declare a property graph structure over existing tables. It is left up to the DBMS to decide whether to create an auxiliary data structure (e.g., adjacency matrix) for the property graph or just keep track of the meta-data. You can then write graph traversal queries in SQL using the MATCH keyword. The syntax builds on existing languages (e.g., Neo4j's Cypher, Oracle’s PGQL, and TigerGraph’s GSQL), and shares aspects of the emerging GQL standard. As of January 2024, the only DBMS that I am aware of that supports SQL/PGQ features is Oracle. There is an experimental branch of DuckDB that also supports SQL/PGQ.
> SQL/PGQ is a big deal. However, I do not foresee it being an immediate deathblow for graph DBMSs, as there are already several ways to translate graph-oriented queries to SQL. Some DBMSs, including SQL Server and Oracle, provide built-in SQL extensions that make storing and querying graph data easier. Amazon Neptune is a graph-oriented veneer on top of their Aurora MySQL offering. Apache AGE provides an OpenCypher interface on top of PostgreSQL. I expect other major OLAP systems (e.g., Snowflake, Redshift, BigQuery) will support SQL/PGQ in the near future.
> Adding SQL/PGQ in a DBMS is not as simple as adding support for the new syntax. There are several engineering considerations to ensure graph queries perform well. For example, graph queries perform multi-way joins to traverse the graph. But a problem arises when the intermediate results for these joins are larger than the base tables. A DBMS must use a worst-case optimal join (WCOJ) algorithm to execute such joins more efficiently than the usual hash join used when joining two tables. Another important technique is to use factorization to avoid materializing redundant intermediate results during joins. This type of compression helps the DBMS avoid blowing out its memory with the same join record over and over again.

* Tiger Graph, Dgraph https://softwareengineeringdaily.com/2021/01/19/dgraph-native-graphql-database-with-manish-jain/ Memgraph, Terminus db, embedded https://github.com/CodyKochmann/graphdb https://github.com/dpapathanasiou/simple-graph cache for dgraph https://github.com/dgraph-io/ristretto

* _Neo4J_ https://media.pragprog.com/titles/pwrdata/neo4j.pdf https://calmcode.io/course/neo4j/introduction

https://danluu.com/yegge-predictions/
DBMS
* embedded w/ Datalog https://news.ycombinator.com/item?id=33518320 https://github.com/cozodb/cozo
* Mongo offers as well https://www.mongodb.com/databases/mongodb-graph-database
* SQLite, Postgres https://news.ycombinator.com/item?id=35386948
* _Age_: Postgres extension https://github.com/apache/age
* _EdgeDB_: graph-relational = no impedance mismatch but still relational https://news.ycombinator.com/item?id=30290225
* written in Python on top of Postgres https://talkpython.fm/episodes/show/355/edgedb-building-a-database-in-python
* _Janus_: distributed, OSS https://github.com/JanusGraph/janusgraph
* _SQLite_: https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need
* _Tao_: distributed https://news.ycombinator.com/item?id=29045443 https://www.micahlerner.com/2021/10/13/tao-facebooks-distributed-data-store-for-the-social-graph.html
* _network database_: similar to graph https://stackoverflow.com/a/52325525 📙 Takahashi [2.39]
* anything that would have ever been network is now SQL https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37 📙 Kleppmann [2.36]

QUERY LANGUAGES
* _Cypher_: declarative
* _GQL_: emerging standard https://stackoverflow.com/q/13824962 https://www.youtube.com/watch?v=h8cyPIEfxQY 11:30
* _Gremlin_: wrapper over Neo4J Java API
## key

---

EMBEDDED
* disk for storage https://github.com/peterbourgon/diskv
* _pickledb_: https://github.com/patx/pickledb
* _sled_: https://github.com/spacejam/sled
* _skate_: https://github.com/charmbracelet/skate
* _badger_: https://github.com/dgraph-io/badger

* _KV store_: hash map + persistence 📙 Kleppmann [72]
* distributed KV store used for service discovery (etcd) ()
* used for metadata, counters
> ZippyDB serves a number of use cases, ranging from metadata for a distributed filesystem, counting events for both internal and external purposes, to product data that’s used for various app features https://engineering.fb.com/2021/08/06/core-data/zippydb/
* impl: hash index; faster not bc they don't have to go to disk but bc don't have to translate in-mem data structure to something that can be written to disk 📙 Kleppmann [89]
* typed values allow for in/decrement, push/pop from list
* used for caching db result set e.g. memcached 📙 Kleppmann [89] https://github.com/akrylysov/pogreb
* RocksDB, memcached used as storage for distributed KV https://github.com/bitleak/kvrocks https://engineering.fb.com/2021/08/06/core-data/zippydb/ https://www.micahlerner.com/2021/05/31/scaling-memcache-at-facebook.html
* RocksDB alternative https://github.com/cockroachdb/pebble
* BYO: https://aosabook.org/en/500L/dbdb-dog-bed-database.html https://notes.eatonphil.com/2023-05-25-raft.html Bitcask https://github.com/avinassh/py-caskdb
> In short, keys are stored in a hash table in RAM, k/v pairs are written to log files. Dead simple, but powerful enough. https://news.ycombinator.com/item?id=31306678

za
* _object store_: KV in which K is ID and V is blob (file, binary) 🗄 `infra.md` AWS/S3
* can only create/update, not append https://stackoverflow.com/a/47524241
* sink https://ceph.io/ceph-storage/ https://github.com/minio/minio https://stackoverflow.com/questions/56627446/docker-compose-how-to-use-minio-in-and-outside-of-the-docker-network https://alexwlchan.net/2020/08/s3-keys-are-not-file-paths
* _flat file_: meant for config, no way to represent relationships or handle concurrency (e.g. prevent dirty read); some structure via delimiters, new lines https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37

## time series

📙 https://www.manning.com/books/time-series-forecasting-using-foundation-models
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
* https://github.com/man-group/arctic https://github.com/man-group/ArcticDB https://www.youtube.com/watch?v=-QwbIM6lxIw
* _Influx_: https://softwareengineeringdaily.com/2019/08/21/time-series-databases-with-rob-skillington/ https://softwareengineeringdaily.com/2021/08/19/influxdata-time-series-data-with-russ-savage/
* _Husky_: event store https://www.datadoghq.com/blog/engineering/husky-deep-dive/
* _Lin_: https://github.com/lindb/lindb
* _Timescale_: built on Postgres https://blog.timescale.com/blog/how-postgresql-aggregation-works-and-how-it-inspired-our-hyperfunctions-design-2/ https://softwareengineeringdaily.com/2021/06/28/timescale-time-series-databases-with-mike-freedman/
* _tstorage_: embedded https://github.com/nakabonne/tstorage BYO https://nakabonne.dev/posts/write-tsdb-from-scratch/ https://news.ycombinator.com/item?id=27730854
* _Whisper_: embedded db for Graphite https://github.com/graphite-project/whisper

# 🕸️ RELATIONAL

📙 Hao https://www.manning.com/books/grokking-relational-database-design
🗄️ `sql.md` schema / approaches

COMPONENTS 📙 Beaulieu [1.6]
* _entity_: thing you're trying to describe e.g. customer, order, et al. 📙 Beaulieu [8]
* _attribute_: column 📙 Hao grokking
* _row_: aka record
* _value_: aka cell, field

RELATIONS
* _relationship_: what ties tables together https://twobithistory.org/2017/12/29/codd-relational-model.html
* _relational model_: Codd 📙 Kent data/reality [155] Beaulieu [5]
* relational algebra https://news.ycombinator.com/item?id=39753749
> when embedding would result in duplication of data but would not provide sufficient read performance advantages to outweigh the implications of the duplication.
> to represent more complex many-to-many relationships
> to model large hierarchical data sets
> In the database community it has been conventional wisdom for nearly half a century now (basically since the invention of the relational model) that in designing your database schema you should be careful to avoid any kind of redundancy. That's what database normalization theory is all about. https://www.cell-lang.net/relations.html
* _denormalization_: when speed more of a concern 📙 Conery imposter [320] Kleppmann [491] Manga [62]
* _denormalized query engine_: subset of data for search https://speakerdeck.com/simon/the-denormalized-query-engine-design-pattern https://simonwillison.net/2020/Dec/19/dogsheep-beta/
* _locality_: proximity of data relevant to an entity 📙 Kleppmann [32] 🗄 `db.md` document
* _embeded_: NoSQL https://www.mongodb.com/docs/manual/core/data-model-design/
> you have "contains" relationships between entities
> you have one-to-many relationships between entities, in these relationships the "many" or child documents always appear with or are viewed in the context of the "one" or parent documents.
> embedding provides better performance for read operations, as well as the ability to request and retrieve related data in a single database operation.

## 1-1

* = sole ownership
* impl: attr, separate table https://support.airtable.com/hc/en-us/articles/218734758#onetoone
* example: person-SSN, country-capital https://stackoverflow.com/a/15037461
* less common than you'd think https://www.b-list.org/weblog/2024/aug/27/highlander-problem/

## 1-M

aka fanout https://jmduke.com/posts/post/django-extract-epoch/
> The "fan-out" happens because a single post can be associated with multiple events, creating a "many" side for every "one" post.
> This pattern is common in systems where activities or logs are recorded for a parent entity (e.g., likes/comments on posts, purchases related to a user, etc.), allowing detailed tracking and aggregation of related data.

* = ownership
```sql
CREATE TABLE team(
    team_id INTEGER PRIMARY KEY,
);

CREATE TABLE player(
    player_id INTEGER PRIMARY KEY,
    team_id INTEGER,
    FOREIGN KEY (team_id) REFERENCES team(team_id)
);
```

## M-M

* = collaboration
* aka join table, junction table https://stackoverflow.com/a/3419868
```sql
CREATE TABLE band(
    band_id INTEGER PRIMARY KEY,
);

CREATE TABLE musician(
    musician_id INTEGER PRIMARY KEY,
);

CREATE TABLE band_musician(
    bm_id INTEGER PRIMARY KEY,
    band INTEGER,
    musician INTEGER,
    FOREIGN KEY (band) REFERENCES band(band_id)
    FOREIGN KEY (musician) REFERENCES band(musician_id)
);
```

## normalization

* _normalization_: process of extracting entities from other entities https://en.wikipedia.org/wiki/Database_normalization#Normal_forms

ANOMOLIES
* _delete_: delete causes loss of other important info e.g. if employee and project_id in same table, rm employee also removes project

FORMS
* _form_: step in normalization
* avoids redundancy (no `author` in `book` bc you'd repeat Jane Austen for each novel)
* saves space (no dupes) 📙 Kleppmann [33]
* howto: one big mess and decompose from there, think of example queries
* _1NF_: 1 value for each attr
* aka atomic 📙 Takahashi [58] Winand [6]
```sql
-- pre-1NF: n values for each record
insert into danzi(item) values ('quesidilla, churro');

-- 1NF: 1 value for each record
insert into danzi(item) values ('quesidilla');
insert into danzi(item) values ('churro');
```
* _2NF_: non-PK must be related to PK 📙 Conery imposter 316 Takahashi 3.63 https://stackoverflow.com/a/724032
* symptom is redundancy (value repeats across records w/out reference to FK) and therefore anomaly (value could be mispelled) 📙 Karwin [289]
```sql
-- TITLE dependent on COURSE_ID but unrelated to SEMESTER_ID
CourseID | SemesterID | #Places  | Title        |
------------------------------------------------|
IT101    |   2009-1   | 100      | Programming  |
IT101    |   2009-2   | 100      | Programming  |
IT102    |   2009-1   | 200      | Databases    |
IT102    |   2010-1   | 150      | Databases    |
IT103    |   2009-2   | 120      | Web Design   |
```
* _3NF_: don't get difference from 2NF 📙 Conery imposter 318 Karwin 291
* the generally accepted level of normalization 📙 Winand 1.4
* https://stackoverflow.com/a/724013/6813490 https://www.mikealche.com/software-development/a-humble-guide-to-database-schema-design
```sql
-- todo
```
* _5NF (Boyce-Codd)_: when you're going too far 📙 Winand [5]

# 🖼️ REPR

## ERD


* d2 https://d2lang.com/tour/sql-tables 🗄️ `architecture.md`
```txt
catalog: {
  shape: sql_table
  product_id: int {constraint: foreign_key}
  sku: string {constraint: foreign_key}
  manufacturer: string {constraint: foreign_key}
  list price: float
}

entity: {
  shape: sql_table
  product_id: int {constraint: foreign_key}
  entity_id: int
  part_number: int
}

prod_class: {
  shape: sql_table
  product_id: int {constraint: foreign_key}
  manufacturer: string
}

products: {
  shape: sql_table
  product_id: int
  csn: string
  sku: string
  description: string
}

catalog.manufacturer -> prod_class.manufacturer
catalog.product_id -> products.product_id
catalog.sku -> products.sku
entity.product_id -> products.product_id
prod_class.product_id -> products.product_id
```

---

🗄 `analytics.md` tooling / GUI 🧠 https://chatgpt.com/c/673ce0d8-543c-8004-93c3-90df2d298ecf
> can use d2 https://github.com/zekenie/d2-erd-from-postgres https://terrastruct.com/blog/post/generate-diagrams-programmatically/
* symbols 📙 Karwin [7]
* SQLite https://github.com/Dicklesworthstone/sqlalchemy_data_model_visualizer https://gitlab.com/Screwtapello/sqlite-schema-diagram
* Django https://github.com/pikhovkin/django-schema-viewer
* _databasediagram_: https://databasediagram.com/
* _dbdocs_: 🎯 https://dbdocs.io/
* _drawdb_: https://drawdb.vercel.app/
* _DrawSQL_: https://drawsql.app/me-195/diagrams/testing123
* _erd_: https://github.com/BurntSushi/erd
* _excalidraw_: https://excalidraw.com/ https://gist.github.com/zachvalenta/f4c2226b991b69d129fe7d1d40119f43
* _GraphViz_: w/ pydantic + dataclasses https://pythonbytes.fm/episodes/show/403/a-machine-learning-algorithm-walks-into-a-bar
* wrapper https://news.ycombinator.com/item?id=42044771
* _quickdatabasediagrams_: https://app.quickdatabasediagrams.com/#/
* _sketchviz_: uses GraphViz https://sketchviz.com/graphviz-examples

## UML

> can use d2 https://d2lang.com/tour/uml-classes
* https://www.amazon.com/UML-Distilled-Standard-Modeling-Language/dp/0321193687 https://yuml.me/diagram/scruffy/class/draw
* aka class diagram
* PlantUML
* alternative syntax 📙 Evans domain-driven [42]
* can be used for ERD in Mongo https://stackoverflow.com/q/11323841 https://stackoverflow.com/q/6010408

# 🟨 ZA

## access patterns

* _access pattern_: how you have to query based on schema https://calpaterson.com/non-relational-beartraps.html
* what you're prioritizing e.g. read/write vs. aggregations 📻 Macey [6:10]
* _upsert_: insert|update 📙 Bradshaw [46]
* _resolve_: `get_or_create()` in Django

## taxonomy

🧠 https://chatgpt.com/c/672d1eca-8194-8004-a7bb-ab67c03b2a58

* design process https://www.amazon.com/gp/product/0136788041

---

ONTOLOGY
> semantic web, ML https://owlready2.readthedocs.io/en/latest/intro.html
* https://www.stephendiehl.com/posts/bfo/
* https://www.amazon.com/gp/product/1484265513
* https://www.amazon.com/gp/product/0262527812
* OWL files

relational to graph https://www.amazon.com/gp/product/1804618039 https://www.amazon.com/gp/product/1492044075
knowledge graph https://www.amazon.com/gp/product/1098127102 https://www.manning.com/books/knowledge-graphs-applied
semantic https://www.amazon.com/gp/product/1492054275

❗️ https://en.wikipedia.org/wiki/Information_science https://en.wikipedia.org/wiki/Ontology_(information_science)
🔗 https://en.wikipedia.org/wiki/Data_modeling

https://en.wikipedia.org/wiki/Domain_model
https://www.amazon.com/gp/product/1573875864

```sh
# start here https://en.wikipedia.org/wiki/Three-schema_approach
├── Conceptual # https://en.wikipedia.org/wiki/Conceptual_schema
│   └── Entity-Relationship (ER) # https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model https://en.wikipedia.org/wiki/Relational_Model/Tasmania https://en.wikipedia.org/wiki/Information_model
│   └── Object-Oriented  # https://en.wikipedia.org/wiki/Object%E2%80%93role_modeling
│   └── Semantic Data # https://www.amazon.com/gp/product/1492054275 https://en.wikipedia.org/wiki/Semantic_data_model semantic web https://en.wikipedia.org/wiki/Semantic_technology https://en.wikipedia.org/wiki/Relational_Model/Tasmania
│       ├── Ontologies
│       ├── Taxonomies
│       ├── Conceptual Graphs # https://en.wikipedia.org/wiki/Conceptual_graph https://en.wikipedia.org/wiki/Concept_map
├── Logical # https://en.wikipedia.org/wiki/Logical_schema
│   └── Relational
│   └── Object-Relational # https://en.wikipedia.org/wiki/Object%E2%80%93relational_mapping
│   └── Hierarchical
│   └── Network
├── Physical  # https://en.wikipedia.org/wiki/Physical_schema
│   └── Database Schema Design
│   └── Indexing and Optimization
│   └── Partitioning and Replication
├── Dimensional
│   └── Star Schema
│   └── Snowflake Schema
│   └── Fact and Dimension Tables
├── Graph
│   └── Node and Edge
│   └── Property Graph
│   └── RDF (Resource Description Framework)
├── Temporal
│   └── Historical
│   └── Time-Series 
├── NoSQL
│   └── Key-Value Store
│   └── Document Store
│   └── Column-Family Store 
│   └── Graph Store
├── Object-Oriented Data
│   └── Classes and Inheritance
│   └── Encapsulation and Polymorphism
```

* https://www.amazon.com/gp/product/1573875864 https://www.hedden-information.com/
```txt
Hierarchical taxonomies – for browsing topics tagged to content
Faceted taxonomies – for filtering or refining results by topical aspects
Thesauri – for consistent indexing and accurate retrieval of large numbers of documents
Metadata schema – for effective content management, organization, and retrieval
Ontologies – for modeling semantic relationships between defined classes and their entities
Book indexes – for indicating page numbers of topics and names in printed books
```
