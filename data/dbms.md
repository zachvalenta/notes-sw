# ⛩️

## 参考

📚
* Connolly database systems
* Takahashi manga databases

## 进步

* page, heap https://news.ycombinator.com/item?id=41159180 https://blog.sylver.dev/build-your-own-sqlite-part-1-listing-tables
* physical storage https://drew.silcock.dev/blog/how-postgres-stores-data-on-disk/

* _22_: 📙 Bradshaw ch. 1/4/7/10/14/18
* _20_: Postgres with Django (psycopg, Docker) 📙 Kleppmann section 1

# 🔬️ INTERNALS

🗄 `design.md` distributed
📚
* Petrov database internals
* Kleppmann ch. 3

---

SQL engines https://chatgpt.com/share/6706c793-1428-8004-af11-613cff56c5af https://news.ycombinator.com/item?id=34189422

ACID https://www.youtube.com/watch?v=GAe5oB742dw

CMU https://www.youtube.com/playlist?list=PLSE8ODhjZXjbohkNBWQs_otTrBTrjyohi https://www.youtube.com/playlist?list=PLSE8ODhjZXjasmrEd2_Yi1deeE360zv5O

https://supabase.com/blog/postgres-bloat

* _correlation_: correlation btw storage on disk and order of rows https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data
* locks https://news.ycombinator.com/item?id=35981238&utm_term=comment https://leontrolski.github.io/pglockpy.html

ASYNC
* Django: not yet supported https://docs.djangoproject.com/en/3.2/topics/async/
* Encode `databases`; adds async to SQLAlchemy https://www.encode.io/databases/database_queries/ https://fastapi.tiangolo.com/advanced/async-sql-databases/
* Postgres: can use async functions that underly synchronous `PQexec` https://www.postgresql.org/docs/9.5/libpq-async.html

BYO 📙 Dibernardo, Kleppmann
* https://www.youtube.com/watch?v=5Pc18ge9ohI
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

* _wire protocol_: protocol for db client-server https://datastation.multiprocess.io/blog/2022-02-08-the-world-of-postgresql-wire-compatibility.html https://github.com/crate/crate
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

## data structures

🗄️ `algos.md` data structures

---

* _b-tree_: most popular 📙 Kleppmann 83 Winand vii Petrox ch. 2,4,6
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
* _LSM tree_: faster for writes 📙 Kleppmann 83 Petrov ch. 7 https://news.ycombinator.com/item?id=35634673
* compress more easily 📙 Kleppmann 84
* used in Cassandra, LevelDB 📙 Kleppmann 79, 85 https://nakabonne.dev/posts/write-tsdb-from-scratch/ 🗄 `algos.md` trees
* _BRIN_: https://hakibenita.com/sql-tricks-application-dba#index-columns-with-high-correlation-using-brin

STORAGE ENGINES 🗄 `design.md` transactions
* _journal_: journaling i.e. keep track of transactions? https://fly.io/blog/sqlite-internals-rollback-journal/
* _storage engine_: handle transactions, maintain index https://stackoverflow.com/a/39204302
* row-oriented vs. column-oriented 📙 Kleppmann 586
* log-structured (Riak Bitcask) 📙 Kleppmann 72
> RocksDB uses a log structured database engine, written entirely in C++, for maximum performance. Keys and values are just arbitrarily-sized byte streams. https://rocksdb.org/
* page-oriented 📙 Kleppmann 70 https://sirupsen.com/napkin/problem-6 https://news.ycombinator.com/item?id=32250426
* _Berkeley DB_: https://corecursive.com/066-sqlite-with-richard-hipp/
* _InnoDB_: MySQL; locks table row during transaction
* _MyISAM_: locks whole table https://stackoverflow.com/a/5414622/6813490 
* _WiredTiger_: Mongo 📙 Bradshaw [6]
* _OrioleDB_: for Postgres https://github.com/orioledb/orioledb/
> OrioleDB is a new storage engine for PostgreSQL. Our teams use PostgreSQL a lot, but its storage engine was originally designed for hard drives. Although there are several options to tune for modern hardware, it can be difficult and cumbersome to achieve optimal results. OrioleDB addresses these challenges by implementing a cloud-native storage engine with explicit support for solid-state drives (SSDs) and nonvolatile random-access memory (NVRAM). To try the new engine, first install the enhancement patches to the current table access methods and then install OrioleDB as a PostgreSQL extension. We believe OrioleDB has great potential to address several long-pending issues in PostgreSQL, and we encourage you to carefully assess it. https://www.thoughtworks.com/radar/platforms?blipid=202210068

## indexing

📚
* Bradshaw ch. 5
* Winand https://use-the-index-luke.com/
* https://sqlfordevs.com/ebooks/indexing
🗄
* `algos.md` search engine
* `vim.md` ctags

> When I worked in ads I would often need to debug issues using production logs, and would use Dremel to run a distributed scan of very large amounts of data at interactive speeds. Because queries were relatively rare, an index would have been far more expensive to maintain. https://www.jefftk.com/p/you-dont-always-need-indexes

START HERE
* https://calpaterson.com/how-a-sql-database-works.html
* https://www.jefftk.com/p/you-dont-always-need-indexes
* make invisible > delete https://sqlfordevs.com/invisible-index-before-delete
* https://news.ycombinator.com/item?id=35978757&utm_term=comment
* Postgres has partial indexes
* notes for Karwin chapter 13
> mention of caching? https://hakibenita.com/sql-tricks-application-dba#always-load-sorted-data
* https://dataschool.com/sql-optimization/how-indexing-works/
* BRIN https://hakibenita.com/sql-tricks-application-dba#index-columns-with-high-correlation-using-brin https://www.highgo.ca/2020/06/22/types-of-indexes-in-postgresql/ https://en.wikipedia.org/wiki/Block_Range_Index https://hakibenita.com/postgresql-correlation-brin-multi-minmax
* https://www.youtube.com/watch?v=HubezKbFL7E
* Beaulieu chapter 13, 15
* Faroult 3
* https://github.com/BurntSushi/xsv
* https://news.ycombinator.com/item?id=32250426
* ghost conditions https://sqlfordevs.com/ghost-conditions-for-unindexed-columns

BASICS
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

TYPES https://www.highgo.ca/2020/06/22/types-of-indexes-in-postgresql/
* _covering_: store additional columns in index https://hakibenita.com/django-32-exciting-features#covering-indexes
> A covering index is when you have an index and it has multiple columns in the index and you’re doing a query on just the first couple of columns in the index and the answer you want is in the remaining columns in the index. When that happens, the database engine can use just the index. It never has to refer to the original table, and that makes things go faster if it only has to look up one thing. https://corecursive.com/066-sqlite-with-richard-hipp/
* _primary_: keeping track of order of entry i.e. having a primary key 📙 Kleppmann 85
* _partial_: normal index + `WHERE` clause https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions https://hakibenita.com/sql-tricks-application-dba https://dataschool.com/sql-optimization/partial-indexes/ 📙 Bradshaw [5]
* _secondary_: https://calpaterson.com/non-relational-beartraps.html 📙 Kleppmann [85] Bradshaw [5]
* _multicolumn_: aka concatenated 📙 Kleppmann 87 https://dataschool.com/sql-optimization/multicolumn-indexes/

## logging

* _log_: append-only data file; used to deal w/ concurrency 📙 Kleppmann 71
* _segment_: chunk of log; immutable 📙 Kleppmann 73
* _compaction_: rm dupe keys from log; done by plucking most recent update for key and writing to new, smaller segment file; done in background while continuing to use existing segments for read/write 📙 Kleppmann 73
* fsync log instead of fsyncing data itself to increase throughput? http://aosabook.org/en/nosql.html
> Several data structures, such as B+Trees, help NoSQL systems quickly retrieve data from disk. Updates to those structures result in updates in random locations in the data structures' files, resulting in several random writes per update if you fsync after each update. To reduce random writes, systems such as Cassandra, HBase, Redis, and Riak append update operations to a sequentially-written file called a log. While other data structures used by the system are only periodically fsynced, the log is frequently fsynced. By treating the log as the ground-truth state of the database after a crash, these storage engines are able to turn random updates into sequential ones. While NoSQL systems such as MongoDB perform writes in-place in their data structures, others take logging even further. Cassandra and HBase use a technique borrowed from BigTable of combining their logs and lookup data structures into one log-structured merge tree. Riak provides similar functionality with a log-structured hash table. CouchDB has modified the traditional B+Tree so that all changes to the data structure are appended to the structure on physical storage. These techniques result in improved write throughput, but require a periodic log compaction to keep the log from growing unbounded.

TYPES
* _command log_: log commands to change state but not incremental changes
* _append-only log_: immutability at the db level; conflict w/ GDPR https://www.bloorresearch.com/2018/02/append-databases-gdpr-conundrum/
* _write-ahead log (WAL)_: log changes in state before update so you can recover if failure (power, OS, hw) https://softwareengineeringdaily.com/wp-content/uploads/2018/06/SED613-Database-Reliability-Engineering.pdf BYO https://github.com/khonsulabs/okaywal logical decoding messages https://www.infoq.com/articles/wonders-of-postgres-logical-decoding-messages/ https://pgdash.io/blog/taming-postgresql-wal-file-growth.html https://news.ycombinator.com/item?id=41851051 https://simonwillison.net/2022/Oct/23/datasette-gunicorn
* used in b-tree 📙 Kleppmann 84
* individual entries known as frames https://news.ycombinator.com/item?id=26583558
* turn off if you're just doing a transformation https://hakibenita.com/sql-tricks-application-dba#use-unlogged-tables-for-intermediate-data

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

* Postgres
> When modeling a Postgres database, you probably don’t give much thought to the order of columns in your tables. After all, it seems like the kind of thing that wouldn’t affect storage or performance. But what if I told you that simply reordering your columns could reduce the size of your tables and indexes by 20%? This isn’t some obscure database trick — it’s a direct result of how Postgres aligns data on disk.

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

## query engine

🔗 https://pganalyze.com/blog/how-postgres-chooses-index

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
* _query plan_: output from query optimizer = imperative steps to impl declarative SQL https://www.youtube.com/watch?v=IwahVdNboc8 https://dataschool.com/sql-optimization/what-is-a-query-plan/
* _execution plan_: query plan chosen by optimizer 📙 Beaulieu [46]
> There is a trade-off between the amount of time spent figuring out the best query plan and the quality of the choice https://en.wikipedia.org/wiki/Query_optimization
* _query hint_: explicitly tell optimizer what to do 📙 Beaulieu 3.42 https://en.wikipedia.org/wiki/Hint_(SQL)
* Postgres doesn't support https://wiki.postgresql.org/wiki/Todo
* _query engine_: executes query plan https://en.wikipedia.org/wiki/Presto_(SQL_query_engine) https://news.ycombinator.com/item?id=27006476

# 🟩 MONGO

📙 Bradshaw guide
🎓 https://university.mongodb.com/dashboard
📜
* Mongo https://www.mongodb.com/docs/manual
* PyMongo https://pymongo.readthedocs.io/en/stable/tutorial.html

---

lookups
> workaround for $$ notation just eliminate aliasing?
* dot nota
```js
// dot notation: reference subdocument key 📙 Bradshaw [63] https://www.mongodb.com/docs/manual/core/document/#dot-notation
db.people.find({"name.first": "bob"})

// field path ($) = dot notation for stage's input documents 📙 Bradshaw [173]
{$project: {amount: "$funding_rounds.amount"}}

// variable notation ($$) = reference variable in expression 📙 Bradshaw [174]
{
    $project: {
        rounds: {$filter: {
            input: "$funding_rounds",
            as: "round",  // variable definition
            cond: {$gte: ["$$round.raised_amount", "$1M"]}  // reference
        }}
    }
}
```

queries
* _query document_: arg to `find()`, `aggregate()` 📙 Bradshaw [53]
* _cursor_: return from aggregation
* iterator, also a connection object 📙 Bradshaw [66]
* lazy evaluation i.e. cursor doesn't query db until all operators evaluated 📙 Bradshaw [66]
* only fetches 100 results or 4 MB on evaluation
* `hasNext()`: bool on whether next el to fetch 📙 Bradshaw [66]
* `next()`: fetches next el
* _immortal_: cursor that you explicitly need to iterate fully through or kill 📙 Bradshaw [71]
* _projection_: specify keys to return per document i.e. select 📙 Bradshaw [196]
* via dict keys in PyMongo
* do last bc expensive operation and want to run on as few documents as possible 📙 Bradshaw [166]
* _mongoexport_: output result set to file https://stackoverflow.com/a/47450934
> have code for this from a UM ticket

semantics
* _field_: key
* _normal collection_: size dynamic 📙 Bradshaw [151]
* _capped collection_: size static 📙 Bradshaw [151]
* _natural order_: order of documents on disk https://www.mongodb.com/docs/v4.4/reference/method/db.collection.findOne/

monitoring
* slow queries
> Anyone know if we have the equivalent of a mongo slow query log, or some other way to identify slow queries?
> usually you can spot slow mongo in API traces that have a long span for pymongo.get_socket. but yeah, it doesn't tell you which query. so if there are a bunch that it could be, I've had to run an explain on each one. mongodb has slow query logs though.
* `db.currentOp()` connection id, operation id, seconds running 📙 Bradshaw [371]
* stats: `db.stats()` and `db.col.stats()`
* some long-running ops are not normal queries but for replication 📙 Bradshaw [375]
* profiler will slow down db, can set it to only observe queries that take long than 100ms 📙 Bradshaw [376,378]
* _acknowledged write_: waits until previous write completed vs. just sitting in an os buffer 📙 Bradshaw [376]
* _phantom writes_: write waiting in the os buffer after you've already stopped client from sending further writes 📙 Bradshaw [376]

za
* implementation http://aosabook.org/en/nosql.html
* certification https://university.mongodb.com/certification/developer/about exam https://university.mongodb.com/certification/exam-prep
* indexes 📙 Bradshaw [384] `db.col.getIndexes()`
* _mongod_: server daemon; port 27107 📙 Bradshaw [227,290]
* _MongoEngine_: ODM i.e. doesn't return dicts like PyMongo https://stackoverflow.com/a/41323384
* _Mongo tools_: https://github.com/mongodb/homebrew-brew `brew install mongodb-database-tools`
* _Beanie_: ODM https://talkpython.fm/episodes/show/349/meet-beanie-a-mongodb-odm-pydantic
* _Atlas_: managed Mongo
* _Charts_: Atlas + visualization

replication 🗄 `system.md` data
* _replica set_: cluster 📙 Bradshaw [227]
* changing normal mongod server to replica set involves downtime so just config as 1-server set from start 📙 Bradshaw [231]
* connection config comes from primary 📙 Bradshaw [230]
* 1 primary (writes) n secondaries (replication)
* if primary unavailable secondaries elect new primary 📙 Bradshaw [227,235,243,244]
* secondaries become primary due to priority + election algorithm 📙 Bradshaw [244]
* need majority to elect primary bc don't want two primary in event of network partition 📙 Bradshaw [241]
* _data node_: node that holds data 📙 Bradshaw [247]
* _arbiter_: secondary holding no data whose only point is to participate in elections for 2-member replica sets 📙 Bradshaw [246]
* generally shouldn't be used [247]
* _passive_: secondaries w/ priority of 0 i.e. can never become primary 📙 Bradshaw [244]
* _hidden member_: secondary that doesn't get requests routed to it and won't get replicated to often 📙 Bradshaw [245]
* for low-powered servers

partition 🗄 `system.md` data
* _mongos_: routing process in front of sharding cluster 📙 Bradshaw [290,293]
* can shard on single machine 📙 Bradshaw [291]
* _shard key_: field used to chuck data e.g. if `username` then alice-candace, david-fred, etc. 📙 Bradshaw [294]
* Postgres https://github.com/ankane/pgslice

## aggregation

📜
* https://docs.mongodb.com/manual/aggregation/
* https://www.practical-mongodb-aggregations.com

grouping https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/group/
* output document per group by `_id` 📙 Bradshaw [189] https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/group/#group-title-by-author
```js
// regular syntax
$group : { 
    _id : "$author",  // group
    books: { $push: "$title" }  // accumulator
}

// label syntax; neither Bradshaw [193] nor the docs explain https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/group/#optimization-to-return-the-first-document-of-each-group
$group : { 
    _id : { author: "$author"},
    books: { $push: "$title" }
}
```
* _accumulator_: mostly SQL aggregates (min/mix/avg) + misc functionality (push) https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/group/#std-label-accumulators-group
* can run w/out grouping e.g. count https://www.mongodb.com/docs/upcoming/reference/operator/aggregation/group/#count-the-number-of-documents-in-a-collection
* _push_: add el to list as obj added to group 📙 Bradshaw [194]
* only works in group stage 📙 Bradshaw [196]
* _addToSet_: push + no dupes 📙 Bradshaw [186]

operations
* array expressions: filter, slice, `$arrayElemAt` 📙 Bradshaw [181,184,186]
* _filter_: comparison operator for projection stage of aggregation 📙 Bradshaw [181]
```js
$project: {
    items: {
        $filter: {
            input: "$items",
            as: "item",
            cond: { $gte: [ "$$item.price", 100 ] }
        }
    }
}
db.sales.aggregate([
   {
   }
])
```
* find doesn't require projection for this so idky aggregation does
* _match_: predicate; earlier the better 📙 Bradshaw [165,180]
* _unwind_: create output document for each el in array field 📙 Bradshaw [174]
```diff
- {
-    k: v,
-    k: [1,2]
- }
+ {
+    k: v,
+    k: [1]
+ }
+ {
+    k: v,
+    k: [2]
+ }
```
* _lookup_: left outer join https://www.mongodb.com/docs/manual/reference/operator/aggregation/lookup/
```js
db.orders.aggregate([             // FROM orders
    {
        $lookup: {
            from: "inventory",    // JOIN inventory
            localField: "item",   // ON orders.item
            foreignField: "sku",  // = inventory.sku
            as: "inventory_docs"  // stdout alias
        }
    }
])
```

semantics
https://www.singer.io/ pipeline, taps
* _aggregation_: operation on a pipeline 📙 Bradshaw [166]
* _pipeline_: array of stages 📙 Bradshaw [166]
* same idea as UNIX pipes 📙 Bradshaw [162]
* introduced w/ version 3.2 📙 Bradshaw [5]
* preceded by MapReduce https://www.practical-mongodb-aggregations.com/intro/history.html
* no SSoT for how to do things btw `find()` and `aggregate()`
* _stage_: input document + operator = output document 📙 Bradshaw [162,166]
* can have multiple of the same type 📙 Bradshaw [180]
* each stage takes input from previous stage 📙 Bradshaw [161]
* input and output of each stage also a document 📙 Bradshaw [161]

## find

📜 Mongo https://www.mongodb.com/docs/manual/crud/

---

* key exists: `list(db.col.find({"ur_key": {"$exists": False}}))`
* syntax: `db.col.find(query)`
* get collections `sorted(db.collection_names())`

basic
* can't refer to another key in document e.g. `find({"balance": "this.profit - this.loss})` 📙 Bradshaw [55]
* null 📙 Bradshaw [57]
* regex 📙 Bradshaw [58]
```sh
# SELECT * FROM TAB
db.col.find()

# SELECT * FROM TAB LIMIT 1
db.col.findOne()  # for n, returns 1 according to natural order https://www.mongodb.com/docs/v4.4/reference/method/db.collection.findOne/
db.col.find_one() # same as mongosh? https://github.com/mongodb/mongo-python-driver/blob/6e99bf451503825577213ef148ec6b519a41257b/pymongo/collection.py#L1388

# SELECT * FROM TAB LIMIT N
db.col.find().limit(n)  # for pagination 📙 Bradshaw [69] can also use slice() or skip() 📙 Bradshaw [60,67]

# COUNT https://stackoverflow.com/a/4415593
db.col.find().count()

# SORT
db.col.find().sort({age: 1})  # asc
db.col.find().sort({age: -1}) # desc
```

predicates
* can use `$where` queries but shouldn't bc slower, use `$expr` instead 📙 Bradshaw [65]
```sh
# SELECT * FROM TAB WHERE COL = VAL 📙 Bradshaw [54]
{f:v}
# NESTED
{f1.f2: v}

# MEMBERSHIP 📙 Bradshaw [56]
{f: {$in: [a, b]}}
# EXACT MATCH ON N 📙 Bradshaw [59]
{f: { $all: [a, b]}}

# LOGICAL OPERATORS 
{f1: v, f2: v}
# `[]` for empty list https://stackoverflow.com/a/25142571
{$and: [{f1: {$eq: null}}, {f2: {$ne: null}}]}  # 📙 Bradshaw [56] https://stackoverflow.com/a/69314784

# EQUALITY
db.col.find({likes: 0})
# INEQUALITY
db.col.find({likes: {$ne: 1}})

# COMPARISON 📙 Bradshaw [55]
db.post.find({likes: {$gt: 1}})
```

* find all active artists using big_corp as pg
```js
// feed artist IDs into Mongo
db.subs.findOne({"pg": "big_corp", "status": "active", "artist_id": {$in: [list_of_artist_ids]}})
```

## shell

🗄 utils/GUIs

workflows
* _iPython_: write in driver language (PyMongo), run in REPL
* ✅ good at reuse
* ❌ slow for sketching
* need for work bc can only access some collections via corpus obj
* _RoboMongo_: https://github.com/Studio3T/robomongo https://www.practical-mongodb-aggregations.com/intro/getting-started.html
* _Compass_: write in GUI query editor, run in GUI https://www.mongodb.com/products/compass
* ❌ doesn't work with server versions before 3.6
* ✅ good at sketching simple queries
* ❌ bad at sketching complex queries bc bad editing (no Vim or syntax highlighting)
* ❌ bad at reuse
* ✅ good at aggregations https://www.practical-mongodb-aggregations.com/intro/getting-started.html#mongodb-compass-gui
* _DbGate_: queryless via GUI, run in GUI
* ✅ good at sketching
* ❌ bad at reuse
* _mongosh_: write in text editor, run in terminal
* ❌ slow at sketching bc vim mode in readline never seems to work
* ✅ text editor = Vim, syntax highlighting but 1) slow 2) ephemeral
* ✅ text editor = Vim, syntax highlighting but 1) slow 2) ephemeral

REPL
* mongorc
```js
function foo(value){return [{$match: {"key": `${value}`}}]}
db.col.aggregate(foo(arg))
```
* `edit`: for writing more complex queries/aggregations https://stackoverflow.com/a/28074078
* not actually a good solution bc will fail silently if parsing error
```js
// edit q
{
    $and: [
        { "id": "foo" },
        { "other_col_id": { $ne: "bar"} } 
    ]
},
// edit p
{"thing1": 1, "thing2":1, "_id":0}
// run
db.col.find(q, p)
```

MONGO CLI
* warning https://docs.mongodb.com/v4.4/mongo/#start-the-mongo-shell-and-connect-to-mongodb
* install as standalone https://github.com/mongodb/homebrew-brew#installing-only-the-shell-or-the-database-tools
```sh
$ brew tap mongodb/brew
$ brew install mongodb-community-shell
```
* prompt: display host/user https://www.mongodb.com/docs/manual/tutorial/configure-mongo-shell/#customize-prompt-to-display-database-and-hostname https://stackoverflow.com/a/21417240

MONGOSH CLI https://docs.mongodb.com/mongodb-shell 
* methods https://docs.mongodb.com/mongodb-shell/reference/methods/
* config: if you're connecting to remote, mongo will still use config on local https://docs.mongodb.com/mongodb-shell/run-commands/#.mongoshrc.js-file https://stackoverflow.com/a/11397470
* enhanced https://github.com/TylerBrock/mongo-hacker
```sh
# shell history https://docs.mongodb.com/mongodb-shell/logs/#view-mdb-shell-command-history
~/.mongodb/mongosh/.mongosh_repl_history
# shell logs https://docs.mongodb.com/mongodb-shell/logs/#view-the-log-for-the-session
~/.mongodb/mongosh/
# clear console
cls

# connect https://docs.mongodb.com/mongodb-shell/connect/
mongo -u user -p pw 127.0.0.1:6017/db
mongosh --port 27017

# view connection info https://docs.mongodb.com/mongodb-shell/connect/#verify-current-connection
db.getMongo()          # Mongo shell
db.collection_names()  # PyMongo REPL https://stackoverflow.com/a/9805506

db  # view current db
show dbs  # view all dbs
use <db>  # switch/create db
show collections  # view collections
```

# 🗺️ NON-RELATIONAL

🗄️ `algos.md` data structures
📙 Kleppmann ch. 2

> There are data stores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Kafka), so the boundaries between the categories are becoming blurred 📙 Kleppmann [12]

* modeling from different angles https://www.openmymind.net/2011/7/5/Rethink-your-Data-Model/

---

* _vector_: for recommendation systems, NLP https://news.ycombinator.com/item?id=35550567 https://garybake.com/vector_databases.html Pinecone https://news.ycombinator.com/item?id=35826929 https://code.dblock.org/2023/06/16/getting-started-with-vector-dbs-in-python.html https://news.ycombinator.com/item?id=37747534 https://realpython.com/chromadb-vector-database/ https://github.com/asg017/sqlite-vec https://github.com/qdrant/qdrant https://www.youtube.com/watch?v=awIm3rQOBxE
* Datomic (Hickey), datalog/prolog https://news.ycombinator.com/item?id=21742222 https://kevinlynagh.com/newsletter/2022_04_on_datalog_application_databases/ https://news.ycombinator.com/item?id=31154039 https://news.ycombinator.com/item?id=35094017 https://news.ycombinator.com/item?id=35727967 https://clojure.org/news/2023/08/04/next-rich https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need https://news.ycombinator.com/item?id=41642969
* can be a problem is you need to change the PK https://calpaterson.com/non-relational-beartraps.html
> Changing the primary key of a table is a surprisingly common activity. In truth, it's pretty easy to pick something that initially looks like it will be unique but which later turns out to not be unique...Unfortunately, in many non-relational database systems the primary key is "special". For example, Dynamo-style systems will use the primary key to decide which of the partitions the record will go on.
* _polyglot persistence_: using multiple types of data stores 📙 Kleppmann 2.29 because choosing just one is no fun :) https://old.reddit.com/r/learnpython/comments/glbuog/whats_is_your_decision_process_between_csv_json/
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

---

📙 Kleppmann 2.28-42

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
* _Lungo_: 🎯 embedded, Mongo compatible Golang impl https://github.com/256dpi/lungo
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

* _EdgeDB_: graph-relational = no impedance mismatch but still relational https://news.ycombinator.com/item?id=30290225
* written in Python on top of Postgres https://talkpython.fm/episodes/show/355/edgedb-building-a-database-in-python
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
* _triple-store_: subject (vertex) predicate, object (value or another vertex) 📙 Kleppmann 2.55 used by Datomic (Datalog query language) 📙 ibid 2.50, 60, 63 https://github.com/instantdb/instant
* _RDF (resource description framework)_: triple store for semantic web 📙 Kleppmann 2.57 SPARQL query language 📙 ibid 59 https://twobithistory.org/2020/01/05/foaf.html
* _types_: https://stackoverflow.com/a/59532041/6813490
* visualization https://github.com/shahinrostami/chord https://github.com/plotly/falcon
* _sink_: https://github.com/brettkromkamp/contextualise https://www.youtube.com/watch?v=GekQqFZm7mA https://www.denizcemonduygu.com/philo/ http://aosabook.org/en/500L/dagoba-an-in-memory-graph-database.html https://pragprog.com/book/pwrdata/seven-databases-in-seven-weeks-second-edition

## key

---

REDIS 📙 https://www.openmymind.net/2012/1/23/The-Little-Redis-Book/
> just use postgres https://martinheinz.dev/blog/105
* https://www.youtube.com/watch?v=WQ61RL1GpEE
* https://www.youtube.com/watch?v=5TRFpFBccQM
* implementation http://aosabook.org/en/nosql.html
* https://github.com/dragonflydb/dragonfly
* test/mock https://github.com/cunla/fakeredis-py
* use Postgres as impl https://github.com/alash3al/redix
* governance https://news.ycombinator.com/item?id=23689549
* key expiration https://news.ycombinator.com/item?id=30099572
* alternative https://github.com/dragonflydb/dragonfly https://github.com/buraksezer/olric#installing
* embedded https://github.com/symisc/vedis https://news.ycombinator.com/item?id=19464144
> You can either set Redis up as a "data-structures" server or you set it up right as a cache. You can't do both. If you choose to use Redis as your cache, ensure that the cache instance is only serving as your cache. Your inter-system message bus should be on a different Redis with a different configuration. https://calpaterson.com/ttl-hell.html

MEMCACHED
* _is?_: volatile cache https://news.ycombinator.com/item?id=23689549 aka application caching layer
* _how?_: distributed hash table i.e. n instances of app share 1 distributed instance of memcached
* _why?_: so you don't have to read from db
* _disadvantages_: doesn't track cache misses; meant for simple data, not tables or objects; not durable http://aosabook.org/en/nosql.html
* _sink_: https://realpython.com/python-memcache-efficient-caching/ https://github.com/thadeusb/flask-cache Django has OOB support for memcached https://docs.djangoproject.com/en/2.1/topics/cache/

* _KV store_: hash map + persistence 📙 Kleppmann [72]
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
* _Lin_: https://github.com/lindb/lindb
* _Timescale_: built on Postgres https://blog.timescale.com/blog/how-postgresql-aggregation-works-and-how-it-inspired-our-hyperfunctions-design-2/ https://softwareengineeringdaily.com/2021/06/28/timescale-time-series-databases-with-mike-freedman/
* _tstorage_: embedded https://github.com/nakabonne/tstorage BYO https://nakabonne.dev/posts/write-tsdb-from-scratch/ https://news.ycombinator.com/item?id=27730854
* _Whisper_: embedded db for Graphite https://github.com/graphite-project/whisper

# 🐘 POSTGRES

📙 Suzuki postgres internals https://www.interdb.jp/pg/
📜
* general https://www.postgresql.org/docs/current/index.html
* guide http://postgresguide.com/
* wiki https://wiki.postgresql.org/wiki/Main_Page
* design https://news.ycombinator.com/item?id=35599118 Stonebraker https://dsf.berkeley.edu/papers/ERL-M85-95.pdf

HOW TO https://gist.github.com/cpursley/c8fb81fe8a7e5df038158bdfe0f06dbb https://news.ycombinator.com/item?id=39273954
* monitor / metrics https://github.com/CrunchyData/pgmonitor-extension
* duckdb extension https://motherduck.com/blog/pg_duckdb-postgresql-extension-for-duckdb-motherduck/ https://github.com/duckdb/pg_duckdb
* copy btw tables https://ongres.com/blog/fastest_way_copy_data_between_postgres_tables/
* embed https://github.com/electric-sql/pglite
* perf, memory https://news.ycombinator.com/item?id=40642803
* generate `create table` from existing table https://github.com/lacanoid/pgddl
* Elasticsearch https://github.com/paradedb/paradedb
* serverless https://neon.tech/ https://news.ycombinator.com/item?id=31536827
* embedded for testing https://github.com/electric-sql/pglite https://news.ycombinator.com/item?id=39960537
* sharding https://github.com/postgresml/pgcat
* Snowflake, DuckDB, Clickhouse https://github.com/scottpersinger/pgwarehouse
* result set to CSV https://stackoverflow.com/a/1517692
* high availability https://github.com/zalando/patroni
* upgrade: pg_upgrade https://about.gitlab.com/blog/2020/09/11/gitlab-pg-upgrade/
* delete data from table: `DELETE FROM <tab>` https://www.postgresql.org/docs/11/dml-delete.html
* drop all tables: `DROP SCHEMA <schema> CASCADE`
* get date from timestamp: `SELECT date(startime) FROM bookings` https://stackoverflow.com/a/6133147
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

SEMANTICS
* _cluster_: server instance managing n databases https://www.postgresql.org/docs/12/tutorial-concepts.html https://www.crunchydata.com/blog/postgres-databases-and-schemas
* _foreign data wrapper_: access data from another data store e.g. document store for a relational db https://github.com/pgspider/sqlite_fdw
* `json`: text field; slow to search
* JSON schema https://github.com/supabase/pg_jsonschema
* `jsonb`: binary; slower writes, faster reads https://pganalyze.com/blog/postgres-jsonb-django-python
```sql
-- all keys for json obj
select jsonb_object_keys(json_col) from table
-- nested key
select json_col -> 'top_level_key' ->> 'nested_key' from table
```
* _system columns_: ctid, xmin, xmax https://www.youtube.com/watch?v=AveRgUrC7FM

UTILS
* lint https://github.com/sbdchd/squawk
* generate harmful workloads https://github.com/lesovsky/noisia
* generate test data https://news.ycombinator.com/item?id=26564168 https://hakibenita.com/sql-for-data-analysis#generating-data
* tmp db for testing: https://eradman.com/posts/schema-definition.html https://github.com/eradman/ephemeralpg/ https://stackoverflow.com/questions/14314026/embedded-postgresql-for-java-junit-tests 🗄 `testing.md`
* show view's underlying query `select pg_get_viewdef('my_vw')` https://stackoverflow.com/a/25738887/6813490

---

misc
* fuzzy match https://news.ycombinator.com/item?id=26236772
* local dev https://jamey.thesharps.us/2019/05/29/per-project-postgres/
* chaos https://github.com/lesovsky/noisia
* config https://news.ycombinator.com/item?id=25024224
* cron https://github.com/citusdata/pg_cron
* debug https://iamsafts.com/posts/postgres-gin-performance/
* functions https://blog.jonudell.net/2021/08/05/the-tao-of-unicode-sparklines/
* gotchas https://wiki.postgresql.org/wiki/Don%27t_Do_This https://news.ycombinator.com/item?id=26709019
* internals http://www.interdb.jp/pg/ https://postgrespro.com/blog/pgsql/5969985 https://lwn.net/SubscriberLink/934940/3abb2d4086680b78/
* typing https://www.postgresql.org/docs/current/datatype.html 🗄 `sql.md` typing
* stored procedures https://www.postgresql.org/docs/current/xplang.html https://dev.nextthought.com/blog/2018/09/getting-started-with-pgsql-plpythonu.html 

* _anonymize_: https://postgresql-anonymizer.readthedocs.io/en/latest/
* _audit_: https://github.com/pgaudit/pgaudit https://supabase.com/blog/2022/03/08/audit https://news.ycombinator.com/item?id=36004925&utm_term=comment https://news.ycombinator.com/item?id=30615470 https://blog.sequin.io/all-the-ways-to-capture-changes-in-postgres/ change data capture (CDC) https://news.ycombinator.com/item?id=40276768
* _backup_: https://www.crunchydata.com/blog/introduction-to-postgres-backups https://github.com/2ndquadrant-it/barman/ https://github.com/ankane/pgsync https://github.com/postgrespro/pg_probackup https://pgbackrest.org/index.html https://github.com/aiven/pghoard https://github.com/orgrim/pg_back https://www.youtube.com/watch?v=kbCytSYPh0E https://github.com/EnterpriseDB/barman https://github.com/pgmoneta/pgmoneta
* _benchmarking_: https://github.com/ankane/pghero https://blog.codeship.com/tuning-postgresql-with-pgbench/ https://softwareengineeringdaily.com/2022/09/22/automatic-database-tuning/
> Benchmarking is a dark art of deceiving yourself with highly precise numbers. And benchmarketing datastores is even more fraught. Every single flipping database benchmark I've ever seen has been covered in a layer of asterisks and qualifications, and the comments on HN are full of "if you'd just set this flag when compiling it, you'd get 3% more speed out of reads, and the fact that the people running this didn't do this is proof that they were paid off and that they actively sell shady NFT scams of deranged yacht rock Harambe memes. https://wafris.org/blog/rearchitecting-for-sqlite
* _diagram_: https://pgmodeler.io/ https://github.com/akarki15/dbdot
* _extensions_: https://news.ycombinator.com/item?id=23821112 https://github.com/zombodb/pgx https://tech.marksblogg.com/postgresql-extension-rust.html distributed https://github.com/citusdata/citus ydb https://news.ycombinator.com/item?id=31081272 https://tech.marksblogg.com/postgresql-extension-rust.html https://github.com/tcdi/pgx
* _GUI_: pgadmin https://retool.com/blog/best-postgresql-guis-in-2020/
* _GraphQL_: https://github.com/graphile/postgraphile
* _import_: pgloader https://www.twilio.com/blog/sqlite-postgresql-complicated https://github.com/dimitri/pgloader https://www.youtube.com/watch?v=DA1Trq51JZs https://www.youtube.com/watch?v=yDtgk_OLHUc http://www.postgresqltutorial.com/import-csv-file-into-posgresql-table/ https://stackoverflow.com/questions/2987433/how-to-import-csv-file-data-into-a-postgresql-table/2987451#2987451 https://mattsegal.dev/restore-django-local-database.html https://bigmachine.io/all/importing-a-csv-into-postgresql-like-a-pro/
* _logs_: https://github.com/darold/pgbadger
* _monitoring_: https://minervadb.xyz/postgresql-dba-daily-checklist/ https://pgstats.dev/ https://info.crunchydata.com/blog/postgresql-monitoring-for-application-developers-dba-stats https://klotzandrew.com/blog/quickly-debugging-postgres-problems https://github.com/lesovsky/pgcenter Vivid Cortex https://github.com/lob/pg_insights https://github.com/cybertec-postgresql/pgwatch2 https://github.com/cybertec-postgresql/pgwatch2 https://pganalyze.com/ https://github.com/dalibo/temboard
* _queries_: https://news.ycombinator.com/item?id=22432254 explain http://www.helenanderson.co.nz/sql-query-tweaks/ `pg_stat_statements` https://pgdash.io/blog/postgres-features.html https://github.com/mgartner/pg_flame
* _search_: https://czep.net/17/full-text-search.html https://www.imagescape.com/blog/2020/03/11/website-search-using-django-and-postgresql-trigrams 🗄 `algos.md` FTS
* _scheduling_: https://github.com/cybertec-postgresql/pg_timetable

## auth

* _role_: Postgres equivalent of a user, necessary to connect 📙 Conery [4.5] https://www.postgresql.org/docs/8.1/user-manag.html
* are complex https://news.ycombinator.com/item?id=40186752
* _role creation_: PG will create role/db matching Linux user that installed PG; sometimes this doesn't happen w/ Homebrew 📙 Conery 4.4 0:15
* _list roles_: `\du`
* _connection string_: `postgresql://user:pass@host:port/db` https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/#docker https://flask-sqlalchemy.palletsprojects.com/en/2.x/config/#connection-uri-format
* _pure authentication_: Linux user matching PG role can log into that role 📙 Conery 4.3 2:30
* login
```sh
# same syntax for both pgcli and psql
# defaults to user/role and db matching Linux user name https://www.postgresql.org/docs/12/tutorial-accessdb.html
psql -d <db> -U <user>
$ whoami  # alice
$ pgcli  # role (alice) db (alice)
```

---

install https://superuser.com/a/1501253
```sh
# as root
$ apt-get install postgresql postgresql-client postgresql-contrib

# shows that psql and CLI work, both should fail w/ error that Postgres doesn't have user named root
$ psql
$ createdb

# only role in db in `postgres`
# installing PG also creates os user of `postgres`
# idky switching to `postgres` also switches directory to `/root`
$ su postgres
$ createdb scifi
$ psql scifi
```

* macos installation and start https://www.postgresql.org/docs/12/installation-platform-notes.html#INSTALLATION-NOTES-MACOS https://postgresapp.com/ https://stackoverflow.com/a/18832331 🗄 `brew/postgres*.log`
```sh
# start manually
pg_ctl -D /usr/local/var/postgres start
# start on os startup w/ Homebrew
brew services start postgresql
```

* Docker image: roles only set during initializatio https://hub.docker.com/_/postgres if you update auth credentials `docker-compose down -v` might not be enough, may need to rm image as well https://stackoverflow.com/q/53820456 https://github.com/docker-library/postgres/issues/537
```sh
# debug cmd
docker-compose exec <service> env # env var ingested?
docker-compose exec <service> psql -U <user> # can you log in?
```
```yaml
services:
  db:
    image: "postgres:11"  # which image to use; unlike 'web', we're not building this one ourselves
    command: ["postgres", "-c", "log_statement=all", "-c", "log_destination=stderr"]  # logs https://stackoverflow.com/a/59313245
    environment:
      - POSTGRES_HOST  # defaults to service name i.e. 'db' https://www.youtube.com/watch?v=A9bA5HpOk30 6:50 can set manually as well https://stackoverflow.com/a/52543774
      - POSTGRES_DB=zjv_db
      - POSTGRES_USER=zjv_user  # creates role https://stackoverflow.com/q/46669759
      - POSTGRES_PASSWORD=zjv_pw  # cannot be empty or undefined
      - POSTGRES_HOST_AUTH_METHOD=trust  # allow connections w/out password https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
    volumes:  # create dir in WORKDIR (pg_data) and map to where PG stores data https://www.youtube.com/watch?v=A9bA5HpOk30 2:30
      - pg_data:/var/lib/postgresql/data/  # or does this create file in CWD on local machine? https://www.youtube.com/watch?v=A9bA5HpOk30 9:25

volumes:  # yj
  pg_data:
```

* app tier ingestion of env
```conf
# Flask
DB_USER=zjv_user
DB_PW=zjv_pw
DB_NAME=zjv_db
```
```python
# Django https://docs.djangoproject.com/en/3.1/ref/settings/#databases
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'HOST': 'db',
        'PORT': 5432,  # docker images defaults to 5432 so we don't need to specify in docker-compose.yml
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
    }
}
# Flask
user = os.getenv("DB_USER")
pw = os.getenv("DB_PW")
name = os.getenv("DB_NAME")
app.config["SQLALCHEMY_DATABASE_URI"] = f"postgresql://{user}:{pw}@db:5432/{name}"
```

## CLI

cmd
* Postgres specific cmd: `\h`


---

* SQL/psql tips https://psql-tips.org/psql_tips_143.html https://news.ycombinator.com/item?id=34909670
> psql more specific about semicolons? `DELETE FROM $TABLE` works in pgcli but need semicolon in psql

* _change output_: `\pset`
* _set var_: `\set`

psql https://tomcam.github.io/postgres/ https://mydbanotebook.org/psql_tips_all.html
* conf: `.psqlrc` https://www.digitalocean.com/community/tutorials/how-to-customize-the-postgresql-prompt-with-psqlrc-on-ubuntu-14-04 https://robots.thoughtbot.com/improving-the-command-line-postgres-experience https://robots.thoughtbot.com/an-explained-psqlrc
* connect: `-d <db> -U <user> -h <host> -p <port>`; defaults (user=root, host=localhost, port=5432) https://startcodingnow.com/psql-in-docker-compose/
* connect after login: `\c <db>`
* connection info: `\conninfo`
* https://stackoverflow.com/questions/41591386/postgresql-column-does-not-exist-but-it-actually-does

CLI util (psql, postgres, pg_dump, createdb/dropdb) https://gist.github.com/apolloclark/ea5466d5929e63043dcf
* _postgresql-client_: CLI for backups
* create: `createdb <db>` (if 0 doesn't write to stdout) https://www.postgresql.org/docs/12/tutorial-createdb.html comes w/ PG installation https://www.postgresql.org/docs/12/tutorial-createdb.html
* rm: `dropdb <db>`
* dump: `pg_dump <db> > <file>` https://www.postgresql.org/docs/11/backup-dump.html
* load: `psql -f <file>`; https://www.postgresql.org/docs/11/backup-dump.html#BACKUP-DUMP-RESTORE might need to create db beforehand (idk if way to dump such that db automatically created on load, also don't know if safer to use `-d <db>` to ensure loaded to correct db but `verbos` db worked without it) https://raw.githubusercontent.com/ghidinelli/fred-jehle-spanish-verbs/master/jehle_verb_postgresql.sql
* start/status: `pg_ctl`
* version: `postgres -V`

## psycopg

* _driver_: lib for (db) connection https://stackoverflow.com/a/8588766 
* _psycopg_: Python driver for Posgres
* impl https://www.varrazzo.com/blog/2020/03/06/thinking-psycopg3/
* _psycopg2_: uninstallable w/ Poetry even w/ Brew install of Postgres https://realpython.com/flask-by-example-part-2-postgres-sqlalchemy-and-alembic/
* _psycopg2-binary_: installable w/ Poetry, problem with pipenv https://github.com/pypa/pipenv/issues/4073
* reasons for split https://github.com/psycopg/psycopg2/issues/674
* seems like people just use psycopg2-binary instead of psycopg2 http://www.dark-hamster.com/programming/how-to-solve-error-on-installing-psycopg2-using-pip-by-using-psycopg2-binary-instead/ https://gitlab.com/mailman/mailman/commit/3b2a3e199601961b8b195d4a7713e170ce6f9935
* erred out w/ `python:3-alpine` even with installing `psycopg2-binary` as separate dep https://stackoverflow.com/q/60461406
```log
Collecting psycopg2-binary==2.8.5
  Downloading psycopg2-binary-2.8.5.tar.gz (381 kB)
    Error: pg_config executable not found.
    pg_config is required to build psycopg2 from source.
    If you prefer to avoid building psycopg2 from source, please install the PyPI
    'psycopg2-binary' package instead.
```
* worked with new image and installing psycopg2-binary as separate dep in Dockerfile https://github.com/psycopg/psycopg2/issues/684#issuecomment-538423955
```diff
- FROM python:3-alpine
+ FROM python:3.6-slim
+ RUN pip install psycopg2-binary
```
* SQLAlchemy seems to have psycopg as sub dep, but still need to install as standalone https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
```ini
[[package]]
name = "sqlalchemy"

[package.extras]
postgresql = ["psycopg2"]
postgresql_psycopg2binary = ["psycopg2-binary"]
```
```log
web_1  | 172.18.0.1 - - [25/Jun/2020 18:54:01] "GET /healthcheck HTTP/1.1" 200 -
web_1  | [2020-06-25 18:54:13,597] ERROR in app: Exception on /get-things [GET]
web_1  | Traceback (most recent call last):
web_1  |   File "/usr/local/lib/python3.8/site-packages/sqlalchemy/util/_collections.py", line 1020, in __call__
web_1  | During handling of the above exception, another exception occurred:
web_1  | Traceback (most recent call last):
web_1  |     import psycopg2
web_1  | ModuleNotFoundError: No module named 'psycopg2'
```

# 🟦 SQLITE

📜 https://sqlite.org/docs.html
🛠 https://github.com/simonw/sqlite-utils
🔗 https://tech.marksblogg.com/sqlite3-tutorial-and-guide.html

USAGE
* atuin
* iPython

---

ZA
* vector https://github.com/asg017/sqlite-vec
* https://news.ycombinator.com/item?id=40637303
* single-tenant i.e each user gets own db https://news.ycombinator.com/item?id=38171322
* transactions for perf https://news.ycombinator.com/item?id=36583317
* _APSW_: alternative to Python's sqlite3 https://github.com/litements/s3sqlite
* db file extension incl. `.db` and `.sqlite` https://www.visidata.org/ https://sqlite.org/fileformat.html
* can do blob https://stackoverflow.com/q/29008721/6813490 https://www.youtube.com/watch?v=TLgVEBuQURA
* GUI: https://sqlitebrowser.org/ https://github.com/pawelsalawa/sqlitestudio
* backups https://github.com/benbjohnson/litestream https://news.ycombinator.com/item?id=34517474 https://github.com/maxpert/marmot https://litestream.io/alternatives/cron/ https://news.ycombinator.com/item?id=31152490 https://news.ycombinator.com/item?id=31318708

HOWTO
* ERD https://github.com/Dicklesworthstone/sqlalchemy_data_model_visualizer https://gitlab.com/Screwtapello/sqlite-schema-diagram
* diff changes / changelog https://news.ycombinator.com/item?id=38110286&utm_term=comment
* tuning https://news.ycombinator.com/item?id=35547819 https://news.ycombinator.com/item?id=39955288
* config (journal, wal, timeout) https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html https://avi.im/blag/2021/fast-sqlite-inserts/
* migrations: https://news.ycombinator.com/item?id=22367104
* perf https://news.ycombinator.com/item?id=26103776 https://kerkour.com/sqlite-for-servers https://fractaledmind.github.io/2024/04/15/sqlite-on-rails-the-how-and-why-of-optimal-performance/
* diff databases https://news.ycombinator.com/item?id=31256704
* corrupt a database https://news.ycombinator.com/item?id=31214131

## CLI

📜 https://sqlite.org/cli.html

* cmd
```sh
# OPEN /  CLOSE
sqlite3 / .quit
# CREATE EMPTY
sqlite3 <name.db>
# OPEN / RELOAD https://github.com/dbcli/litecli/issues/76
.open <file>

# SHOW FILE
l
# LIST DB
.da  # .databases (litecli)
# LIST TABLES
.tables
# DESCRIBE SCHEMA
.schema <table>

# COLUMNS AND HEADERS https://sqlite.org/cli.html#changing_output_formats https://dba.stackexchange.com/a/40672
.mode column  # overrides `.mode csv`
.headers on
.width  # https://dba.stackexchange.com/a/40672

# QUERY CSV https://news.ycombinator.com/item?id=28299729
.mode csv
.import my.csv <alias>
select * from alias
```

za
* config location: `~/.sqliterc`
* cmd history: `~/.sqlite_history`
* archives https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html
```sh
# dump
sqlite3 my_database .dump | gzip -c > my_database.dump.gz
# restore
cat my_database.dump.gz | sqlite3 my_database
```

---

config
* default file location: pgcli(`~/.config/litecli/config`) sqlite()
* specify config file: `litecli --liteclirc <conf> <db_file>` 🗄 `query-sandbox`

db files
* create db file from script: interactive `sqlite3; .read seed.sql` https://sqlite.org/cli.html#special_commands_to_sqlite3_dot_commands_ interactive `sqlite3 test.db < test_schema.sql` https://stackoverflow.com/q/42245816/6813490 http://flask.pocoo.org/docs/0.12/tutorial/dbinit/#tutorial-dbinit

## design

📜 https://sqlite.org/quirks.html

COMPONENTS
* _SQLite_: library https://tech.marksblogg.com/sqlite3-tutorial-and-guide.html
* Go port https://simonwillison.net/2022/Jan/30/a-cgo-free-port-of-sqlite/
* plumbing https://jvns.ca/blog/2014/09/27/how-does-sqlite-work-part-1-pages/ https://jvns.ca/blog/2014/10/02/how-does-sqlite-work-part-2-btrees/
* _sqlite3_: CLI
* _sqlite3_: also the name of the Python lib/driver https://github.com/zachvalenta/sqlite3-demo https://github.com/zachvalenta/bookcase-sjk https://sebastianraschka.com/Articles/2014_sqlite_in_python_tutorial.html

STRONG POINTS https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html https://www.sqlite.org/whentouse.html
* stability https://news.ycombinator.com/item?id=41347188
* dbms in a C library
* ACID-compliant
* multithreaded https://sqlite.org/threadsafe.html
* reads parallelized 
* writes concurrent
> This means that writers queue up. Each application does its database work quickly and moves on, and no lock lasts for more than a few milliseconds
* file-based/serverless = good for unreliable network (smartphone, airplane)
* db files can deal w/ TB https://news.ycombinator.com/item?id=24178013
* faster than filesystem https://news.ycombinator.com/item?id=41085376

LIMITATIONS
* auth https://news.ycombinator.com/item?id=36922518
* files https://news.ycombinator.com/item?id=32146245
* schema changes require downtime, PRAGMA https://news.ycombinator.com/item?id=31152490
* doesn't support right join or full outer join https://sqlite.org/omitted.html added for 3.9 https://sqlite.org/releaselog/3_39_0.html
* only support single user 📙 Osborn 6.33 https://news.ycombinator.com/item?id=31152490
* data types differ from other dbms, problem for porting?
* no perms, security 📙 Takahashi 1.19 no users 📙 ibid 1.20

EXTENSIONS
* fewer functions than other dbms
* bundled https://github.com/nalgeon/sqlean https://github.com/zachvalenta/golf
* _FTS4_: extension for search https://simonwillison.net/2019/Jan/7/exploring-search-relevance-algorithms-sqlite/ https://www.philipotoole.com/building-a-highly-available-search-engine-using-sqlite/ 🗄 `algos.md` FTS
* JSON https://dba.stackexchange.com/questions/122198/is-it-possible-to-store-and-query-json-in-sqlite https://news.ycombinator.com/item?id=30486052

TYPES
* types: text, blob, null, int (whole num) real (decimal)
* _class_: type for cell https://stackoverflow.com/a/3388158
* _affinity_: type for attr
> The type affinity of a column is the recommended type for data stored in that column. The important idea here is that the type is recommended, not required. Any column can still store any type of data. It is just that some columns, given the choice, will prefer to use one storage class over another. The preferred storage class for a column is called its "affinity". - https://www.sqlite.org/datatype3.html#type_affinity
* _manifest typing_: type information scoped to cell instead of column (as in most other dbms)
* dynamic vs. static https://www.sqlite.org/datatype3.html https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html
* can ️lead to problems when porting to other DBMS
* avoid type conversion https://news.ycombinator.com/item?id=28259104
```sql
CREATE TABLE tIssue (
    id   INTEGER PRIMARY KEY NOT NULL CHECK (typeof(id) = 'integer'),
    col1 BLOB NOT NULL                CHECK (typeof(col1) = 'blob'),
    col2 TEXT                         CHECK (typeof(col2) = 'text' OR col2 IS NULL)
);
```

constraints
* _PK_: `integer primary key` will autoincrement https://stackoverflow.com/a/8519985/6813490
* just points to `rowid` https://stackoverflow.com/a/7906029/6813490
* typically don't need `autoincrement` https://sqlite.org/autoinc.html https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html
* `rowid`: default attr on all tables https://www.sqlite.org/rowidtable.html https://sqlite.org/withoutrowid.html
* _FK_: `pragma foreign_keys = on;`; have to turn on each time you connect https://sqlite.org/foreignkeys.html https://stackoverflow.com/a/9937992/6813490 🗄 `bookcase`
* FK w/ SQLAlchemy: w/ Flask https://fastapi.tiangolo.com/tutorial/sql-databases/ https://www.youtube.com/watch?v=lnfrcHdE_HI https://stackoverflow.com/questions/38792722/flask-foreign-key-constraint https://stackoverflow.com/questions/2614984/sqlite-sqlalchemy-how-to-enforce-foreign-keys have access to engine http://flask-sqlalchemy.palletsprojects.com/en/2.x/quickstart/#road-to-enlightenment
> rn Flask-SQLA will happily violate FK or just leave null 
* `pragma`: cmd to set env var

# 🟨 ZA

TAXNOMY https://dbdb.io/ https://nchammas.com/writing/database-access-patterns
* data structures e.g. relational, document
* scale e.g. single node, distributed
* storage e.g. relational, column store
* consistency guarantee
* transaction isolation 🗄 `system.md` transactions
* _temporality_: real-time vs. historical 📻 Macey 8:30
* _embedded_: https://en.wikipedia.org/wiki/List_of_in-memory_databases https://www.openmymind.net/2011/2/10/Do-Relational-Database-Vendors-Care-About-Devs/
* _client-server_: when you have multiple clients (vs. multithreaded) or need thousands of writes/second https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html

## MySQL

* TUI: https://github.com/charles-001/dolphie
* MariaDB is done https://news.ycombinator.com/item?id=27922687 https://news.ycombinator.com/item?id=35467243
* CLI: https://www.mycli.net/docs flags https://dev.mysql.com/doc/refman/8.0/en/mysql-command-options.html
* GUI: https://sequelpro.com/
* no suppport previously for checking constraints https://www.youtube.com/watch?v=lnfrcHdE_HI 4:45 https://dev.mysql.com/doc/refman/8.0/en/create-table-check-constraints.html
```sql
-- current db
select database();
-- list db
show databases;
-- use db
use <name>;
-- tables
show tables;
```
```sh
# LOGIN
mysql -h <host> -u <user> -p
# CMD FROM SHELL
mysql -u <user> -e <cmd>
# RUN SCRIPT
mysql -u <user> <dbname> < script.sql
# DUMP LOCAL https://github.com/zachvalenta/flyway-tutorial/blob/master/db-backup.sh
mysqldump -u <user> <db> > backup.sql
# DUMP REMOTE https://github.com/zachvalenta/flyway-tutorial/blob/master/db-restore.sh
mysqldump -h <host> -u <user> --single-transaction -p <db> > backup.sql
# LOAD
mysql -u <user> -e "DROP DATABASE IF EXISTS $DB; CREATE DATABASE $DB;
mysql -u $USER $DB < $BACKUP.sql
```

## Oracle

* apparently still much more feature rich than Postgres https://news.ycombinator.com/item?id=24582937
* CLI: seems like you need an account and the docs are shoddy https://dba.stackexchange.com/questions/65032/connect-to-sql-plus-from-command-line-using-connection-string but maybe this will work https://github.com/xo/usql
* account: same as work / phone 123456789 / ABC Corp 100 Commerce Blvd Orlando FL 32801
* GUI: SQL Developer; comment `CMD ALT /` exec `CTRL /`
* Oracle dev https://stackoverflow.com/users/146325/apc
* _Sybase_: SAP counterpart
