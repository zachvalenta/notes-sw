# ⛩️

## 参考

🗄️ `protocols.md`
> All models are wrong, but some are useful - George Box 📙 Zuckerman simons [245]
> Good programmers worry about data structures. https://softwareengineering.stackexchange.com/q/163185
📚
* Alexopoulos semantic https://www.amazon.com/gp/product/1492054275
* Kent data/reality https://www.amazon.com/Data-Reality-Perspective-Perceiving-Information/dp/1935504215

## 进步

* structures taxonomy https://chatgpt.com/c/6706989f-02a4-8004-9933-bbe525f36b55 https://www.interviewcake.com/data-structures-reference https://roadmap.sh/datastructures-and-algorithms
* modeling taxonomy

---

https://swizec.com/blog/why-software-only-moves-forward/

🔍 https://drawsql.app/templates
* enum > FK
* modeling payments https://news.ycombinator.com/item?id=36775098
* https://news.ycombinator.com/item?id=41146239&utm_term=comment

ACCESS PATTERNS
* _access pattern_: how you have to query based on schema https://calpaterson.com/non-relational-beartraps.html
* what you're prioritizing e.g. read/write vs. aggregations 📻 Macey 6:10
* _upsert_: insert or update 📙 Bradshaw [46]
* _get-or-create_: `get_or_create()` in Django, aka find_create_find

IMPORTANCE
> Data models are perhaps the most important part of developing software, because they have such a profound effect: not only on how the software is written, but also how we think about the problem that we are solving. 📙 Kleppmann [31]
> This is one reason it's so important to model your domain correctly: if, for example, you make something a property of A when it should be a property of B, the penalty is often that operations that formerly required checking all the As or all the Bs now require checking all the As and all the Bs. https://www.natemeyvis.com/writing/on-quadratic-complexity/
> Take data access patterns very seriously!...it's easy to turn something that should be logarithmic time into polynomial time https://calpaterson.com/activerecord.html

SEMANTICS
* _domain_: thing you're trying to model https://calpaterson.com/non-relational-beartraps.html
* _schema_: model of thing https://calpaterson.com/non-relational-beartraps.html
* general usage: table names + column name/type https://news.ycombinator.com/item?id=22723277
* Postgres usage: container for obj such as table or view https://news.ycombinator.com/item?id=22721914

# 🏺 DATA STRUCTURES

🔍 https://xlinux.nist.gov/dads/
📙 Conery ch. 7
🗄
* `dbms.md` non-relational
* `dbms.md` internals / datastructures
* `eng.md` store / schemas
* `education.md` design / information design
* `languages.md` typing
* `science.md` metascience / categories
* `sql.md` modeling

review data structures
* Python collections https://www.30secondsofcode.org/python/p/1 https://realpython.com/python-data-structures/
* array https://www.youtube.com/watch?v=QJNwK2uJyGs
* linked list https://www.youtube.com/watch?v=odW9FU8jPRQ https://news.ycombinator.com/item?id=33473497 https://docs.python.org/3/glossary.html#term-list https://nullprogram.com/blog/2024/07/31/
* stack https://www.youtube.com/watch?v=I5lq6sCuABE
* queue https://www.youtube.com/watch?v=mDCi1lXd9hc
* probabilistic https://www.youtube.com/watch?v=VjFS-_H10bw @ 15:00 https://pypi.org/project/datasketch/

OPERATIONS https://github.com/jamiebuilds/itsy-bitsy-data-structures https://www.interviewcake.com/concept/python3/array
* _lookup_: read
* _insert_: add anywhere
* _delete_: rm anywhere
* _unshift_: add to start
* _push_: add to end
* _shift_: rm from start
* _pop_: rm from end

ADT VS. DATA STRUCTURE
* _abstract data type (ADT)_: interface https://stackoverflow.com/a/1692961 https://en.wikipedia.org/wiki/Abstract_data_type#Examples
* _data structure_: impl https://en.wikipedia.org/wiki/Data_structure https://realpython.com/python-heapq-module/#what-are-heaps
* everything is an ADT e.g. arrays in C stored contiguously in mem but are still types i.e. objects https://stackoverflow.com/questions/50450578/how-are-arrays-implemented-in-c
> when students learn data structures they (1) learn how they work theoretically (2) use off-the-shelf data structures to solve problems and (3) sometimes implement these data structures from scratch. However, I don’t often see classes exploring the off-the-shelf implementations https://akshayr.me/blog/articles/python-dictionaries
* http://infolab.stanford.edu/~ullman/focs.html
* IC bottom up https://www.interviewcake.com/article/python3/data-structures-coding-interview @ RAM https://drewdevault.com/2016/05/28/Understanding-pointers.html
* stack https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-stacks 
* queue https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-queues
* linked list https://medium.com/outco/reversing-a-linked-list-easy-as-1-2-3-560fbffe2088 https://www.youtube.com/watch?v=FSsriWQ0qYE https://realpython.com/courses/working-linked-lists-python/
* array https://medium.com/@bsurajbh/implementing-arrays-with-python-7586206f0b13

PROBABILISTIC
* _probabilistic data structures_: CAP theorem but w/ accuracy, functionality, efficiency https://www.youtube.com/watch?v=VjFS-_H10bw 9:15
* _hyperlog_: https://will-keleher.com/about.html
* _hyperloglog_: distinct el in set https://www.youtube.com/watch?v=VjFS-_H10bw 10:00 https://redis.com/redis-best-practices/counting/hyperloglog/

LINKED LIST https://realpython.com/linked-lists-python/ https://news.ycombinator.com/item?id=26620598
* singly or doubly linked https://lwn.net/Articles/827180/
* _memory_: discontiguous locations = sequential access [2.30]
* _O(1)_: write [Bhargava 2.28] delete [ibid]
* _O(n)_: read [Bhargava 2.28]
> seems like mutative operations only O(1) if items tracked and if everything not the first/last index is untracked then shouldn't it be O(n)? [Bhargava 2.30]
* _piece table_: append-only list used for editing text https://darrenburns.net/posts/piece-table/ https://news.ycombinator.com/item?id=36312488 https://cdacamar.github.io/data%20structures/algorithms/benchmarking/text%20editors/c++/editor-data-structures/
* diff than rope? https://github.com/cessen/ropey https://github.com/prompt-toolkit/pyvim https://web.eecs.utk.edu/~azh/blog/challengingprojects.html
* Myers diff https://github.com/aymanbagabas/go-udiff

## array

ADT/DS
* _ADT_: el in sequence w/ random access, supports all operations 📙 Bhargava 2.30 https://www.interviewcake.com/concept/python3/array
* _impl_: contiguous memory locations

complexity
* _O(1)_: lookup [Bhargava 2.28] push/pop [ibid 5.90]
* _O(n)_: insert (esp. unshift) delete [Bhargava 2.28] slice https://www.interviewcake.com/concept/python3/slice

types
* _one-dimensional (1d)_: `[42, 3, 7]`
* _n-dimensional (nd)_: `[[42, 3, 7], [4, 13]]`

za
* _static array_: manual memory
* _dynamic array_: memory managed; autoresize on backing store overflow (create new larger array, cp over existing); Java `ArrayList` Python `list`; same Big O as array except pushes that require resizing, which are O(n) https://www.interviewcake.com/concept/python3/dynamic-array
* _backing store_: free space in dynamic array https://danluu.com/algorithms-interviews/
* _array slice_: use array subset to form new array; example of out-of-place 🗄 `language.md` memory/stack; O(n) in both time and space https://www.interviewcake.com/concept/python3/slice

## *FO

QUEUES
* _enqueue_: add to queue https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
* _dequeue_: rm from queue
* _head_: first item in the queue i.e. oldest item https://www.youtube.com/watch?v=RSY85SLXzwk 0:50

---

* _dequeue_: *FO; either; push to each pop from each https://stackoverflow.com/a/38812944/6813490 https://hamatti.org/posts/rotating-turn-order-with-deque/
```python
pass
```

* _stack_: LIFO; post-it https://stackabuse.com/stacks-and-queues-in-python/ https://realpython.com/how-to-implement-python-stack/
```python
stack = [42, 'abc']
stack.append('alice')  # push
stack.pop()  # pop
```

* _queue_: FIFO https://dbader.org/blog/queues-in-python 🔍 cf. 'rotate array'
* _priority queue_: impl w/ heap https://realpython.com/python-heapq-module/
> is_empty checks whether the queue is empty. add_element adds an element to the queue. pop_element pops the element with the highest priority.
```python
queue = [42, 'abc']  # slow bc list is dynamic array https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-queues
queue.append('alice')  # push
queue.pop(0)  # shift

queue = deque([42, 'abc'])  # faster
queue.append('alice')  # push aka queue
queue.popleft()  # shift aka enque
```

## map

---

* mind map https://en.wikipedia.org/wiki/Mind_map
* concept map https://en.wikipedia.org/wiki/Concept_map https://cmap.ihmc.us/docs/learn.php

hash tables
* https://realpython.com/python-hash-table/
https://docs.python.org/3/glossary.html#term-dictionary
https://stackoverflow.com/questions/2061222/what-is-the-true-difference-between-a-dictionary-and-a-hash-table
* https://www.youtube.com/watch?v=jalSiaIi8j4
* https://www.fluentpython.com/extra/internals-of-sets-and-dicts/
* https://courses.arpitbhayani.me/hash-table-internals/ https://realpython.com/python-hash-table/
* intersection of two lists https://jvns.ca/blog/2021/09/10/hashmaps-make-things-fast/
* https://calpaterson.com/how-a-sql-database-works.html 📙 Kleppmann 72
* https://news.ycombinator.com/item?id=24232752
* https://thepythoncorner.com/dev/hash-tables-understanding-dictionaries/
* https://www.youtube.com/watch?v=2Ti5yvumFTU
* https://github.com/jamiebuilds/itsy-bitsy-data-structures/blob/master/itsy-bitsy-data-structures.js
* https://www.youtube.com/watch?v=5cU1ILGy6dM
* http://paulmouzas.github.io/2014/12/31/implementing-a-hash-table.html

* ADT: reference array via key https://calpaterson.com/how-a-sql-database-works.html
* impl: BST, red-black https://jvns.ca/blog/2017/09/09/data-structure--the-treap-/

hash tables 🗄 `security.md` `python.md`
* _hash table_: hash function + array to put the results in [Bhargava 5.76-8, 5.90-2, 11.213]
* hashing https://blog.codinghorror.com/url-shortening-hashes-in-practice/
* aka map, dictionary, associative array https://docs.python.org/3/glossary.html#term-dictionary
* alternatives incl. BST, skip list https://stackoverflow.com/a/301822 📙 Skiena 12.1

bloom filter https://www.youtube.com/watch?v=qZNJTh2NEiU https://www.youtube.com/watch?v=V3pzxngeLqw
* _bloom filter_: like a hash table except takes up a lot less space and false positives are possible
* use case is to see whether item already part of a very large set e.g. whether a key exists in a database 📙 11.210-11
* https://vprusso.github.io/blog/2017/bloom-filters-and-pokemon/ 📙 Kleppmann 79 https://onatm.dev/2020/08/10/let-s-implement-a-bloom-filter/ http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html https://luminousmen.com/post/building-a-bloom-filter

https://tenthousandmeters.com/blog/python-behind-the-scenes-10-how-python-dictionaries-work/
* _operations_: lookup, insert, delete
* _O(1)_: Bhargava 5.90
* _hash aggregate_: aggregate keys e.g. A 1 B 2 A 4 -> A 5 B 2 https://veekaybee.github.io/2021/06/06/hashaggregate/

# 🗺️ NON

🗄️ `algos.md` data structures
📙 Kleppmann ch. 2

> There are data stores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Kafka), so the boundaries between the categories are becoming blurred 📙 Kleppmann [12]

* modeling from different angles https://www.openmymind.net/2011/7/5/Rethink-your-Data-Model/

---

* Datomic (Hickey), datalog/prolog https://news.ycombinator.com/item?id=21742222 https://kevinlynagh.com/newsletter/2022_04_on_datalog_application_databases/ https://news.ycombinator.com/item?id=31154039 https://news.ycombinator.com/item?id=35094017 https://news.ycombinator.com/item?id=35727967 https://clojure.org/news/2023/08/04/next-rich https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need https://news.ycombinator.com/item?id=41642969
* can be a problem is you need to change the PK https://calpaterson.com/non-relational-beartraps.html
> Changing the primary key of a table is a surprisingly common activity. In truth, it's pretty easy to pick something that initially looks like it will be unique but which later turns out to not be unique...Unfortunately, in many non-relational database systems the primary key is "special". For example, Dynamo-style systems will use the primary key to decide which of the partitions the record will go on.
* _polyglot persistence_: using multiple types of data stores 📙 Kleppmann 2.29 because choosing just one is no fun :) https://old.reddit.com/r/learnpython/comments/glbuog/whats_is_your_decision_process_between_csv_json/
* _block_: https://news.ycombinator.com/item?id=27200177
* immutable https://github.com/codenotary/immudb

## column

🧠 https://chatgpt.com/c/6733b515-87bc-8004-aa84-3164a319fd4d

---

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

DBMS https://en.wikipedia.org/wiki/List_of_column-oriented_DBMSes
* Cassandra https://stackoverflow.com/q/13010225 https://www.youtube.com/watch?v=J-cSy5MeMOA 📙 Kleppmann 99 https://news.ycombinator.com/item?id=28292369 https://simonwillison.net/2021/Aug/24/how-discord-stores-billions-of-messages/
* _Bigtable_: wide table = document store in SQL https://en.wikipedia.org/wiki/Wide-column_store
* _HBase_: Hadoop db

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

## vector

🧠 https://chatgpt.com/c/6733b490-8d1c-8004-aa20-c1c6722b0247

---

* for recommendation systems, NLP
* _ChromaDB_: https://www.youtube.com/watch?v=QSW2L8dkaZk&list=PL58zEckBH8fA-R1ifTjTIjrdc3QKSk6hI&pp=iAQB
* Pinecone, Milvus, Chroma, Weaviate, FAISS https://zackproser.com/blog/vector-databases-compared
* LanceDB https://www.youtube.com/watch?v=hB7sGE0W8CI
* https://news.ycombinator.com/item?id=41985176
* https://news.ycombinator.com/item?id=35550567 https://garybake.com/vector_databases.html Pinecone https://news.ycombinator.com/item?id=35826929 https://code.dblock.org/2023/06/16/getting-started-with-vector-dbs-in-python.html https://news.ycombinator.com/item?id=37747534 https://realpython.com/chromadb-vector-database/ https://github.com/asg017/sqlite-vec https://github.com/qdrant/qdrant https://www.youtube.com/watch?v=awIm3rQOBxE

# 🕸️ RELATIONAL

📙 https://www.manning.com/books/grokking-relational-database-design

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

## ORM

---

* _ORM (object-relational mapper)_: obj as frontend to relational data store
* why: dbms portability, terseness, getting data into obj https://monadical.com/posts/why-use-orm.html https://news.ycombinator.com/item?id=37118633
* why not: SQL is more durable, more help on SO, easier for complicated relationships https://news.ycombinator.com/item?id=21961214 https://eli.thegreenplace.net/2019/to-orm-or-not-to-orm/ https://sirupsen.com/stop-relying-on-your-orm-and-learn-sql https://news.ycombinator.com/item?id=36497613
* write thin DSL over ORM vs. modifying default ORM methods https://rtpg.co/2016/09/12/orms-are-scary.html
* _data mapper_: https://en.wikipedia.org/wiki/SQLAlchemy https://www.openmymind.net/2011/11/18/I-Just-Dont-Like-Object-Mappers/
* _active record_: wrapper (row + DSL) https://www.martinfowler.com/eaaCatalog/activeRecord.html http://calpaterson.com/activerecord.html https://github.com/sdispater/orator
* ActiveRecord for Golang https://github.com/volatiletech/sqlboiler
* _N+1 problem_: https://roadmap.sh/backend https://macwright.org/2020/05/10/spa-fatigue.html https://stackoverflow.com/q/97197/6813490 https://www.sqlalchemy.org/features.html https://tech.yplanapp.com/2016/09/26/introducing-django-perf-rec/ https://www.youtube.com/watch?v=uCbFMZYQbxE https://github.com/jmcarp/nplusone https://news.ycombinator.com/item?id=26151302 https://fly.io/blog/introducing-litefs/ https://github.com/superfly/litefs
> The 1+N database anti-pattern is common: fetch some rows from the database then re-fetch specific rows to get all the items. An ORM can hide this away and make you not realize it is happening. https://suor.github.io/blog/2023/03/26/ban-1-plus-n-in-django/
* solved with eager loading https://news.learnenough.com/eager-loading
* _impedance mismatch_: difficulty of object-relational mapping [Kleppmann 1.33] multiple ways to aproach http://blogs.tedneward.com/post/the-vietnam-of-computer-science/
> In the database community it has been conventional wisdom for nearly half a century now (basically since the invention of the relational model) that in designing your database schema you should be careful to avoid any kind of redundancy. That's what database normalization theory is all about. For some unfathomable reason, the same kind of thinking is never (or almost never) applied to software construction, even though it would be as beneficial (possibly even more so) as it is for databases. So, before we countinue our discussion, it's a good idea to talk a bit about redundancy, and to explain what's so harmful about it. https://www.cell-lang.net/relations.html

# 🟨 ZA

## taxonomy

🧠 https://chatgpt.com/c/672d1eca-8194-8004-a7bb-ab67c03b2a58

* design process https://www.amazon.com/gp/product/0136788041

---

ONTOLOGY https://chatgpt.com/c/67324db1-c8f8-8004-bb93-3f516203f81b
> semantic web, ML https://owlready2.readthedocs.io/en/latest/intro.html
* https://www.amazon.com/gp/product/1484265513
* https://www.amazon.com/gp/product/0262527812

relational to graph https://www.amazon.com/gp/product/1804618039 https://www.amazon.com/gp/product/1492044075
knowledge graph https://www.amazon.com/gp/product/1098127102
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
