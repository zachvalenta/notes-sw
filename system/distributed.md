# ⛩️

## 参考

🗄
* `computation.md` state machines
* `eng.md` replicate
* `infra.md` queues
* `math.md` complexity theory
📚
* https://books.google.com/books?id=jZgSAAAAQBAJ https://bsky.app/profile/nhuck.bsky.social/post/3lcb57fmhes23
* Arpaci ch. 48-50
* Galvin dinosaur chapter 17
* Jeffrey distributed
* Kleppmann data intensive
* Petrov ch. 8-14
* Takada fun/profit http://book.mixu.net/distsys/index.html
* ⭐️ Tornow https://www.manning.com/books/think-distributed-systems

## 进步

* start here https://www.achaq.dev/blog/distributed-systems-state-machines-special-relativity

# 🤝 CONSENSUS

🗄️ `svc/src.md` concurrency
📙 Kleppmann ch. 8-9

---

* https://entropicthoughts.com/data-consistency-is-overrated
* https://www.youtube.com/watch?v=nH4qjmP2KEE
* https://jamesg.blog/2024/08/18/consensus-modeling-python/
* https://sre.google/sre-book/table-of-contents/ chapter 23
* https://lethain.com/distributed-systems-vocabulary/
* https://news.ycombinator.com/item?id=28425379

* _distributed locks_: https://hazelcast.com/blog/long-live-distributed-locks/
* _Lamport timestamp_: https://towardsdatascience.com/understanding-lamport-timestamps-with-pythons-multiprocessing-library-12a6427881c6
* _Lamport clock_: https://martinfowler.com/articles/patterns-of-distributed-systems/lamport-clock.html
* _Byzantine generals problem_: achieve consensus when some actors are unreliable https://en.wikipedia.org/wiki/Byzantine_fault
* _Reed-Solomon_: way to protect messages against damage or partial arrival https://news.ycombinator.com/item?id=27491219
* _semaphore_: synchronization primative, 类似 mutex/lock https://greenteapress.com/wp/semaphores/ https://danluu.com/programming-books/ https://en.wikipedia.org/wiki/Semaphore_(programming) https://sqlfordevs.com/transaction-locking-prevent-race-condition
* on having more than one primary 📙 Bradshaw [243]
* locks for task, Shedlock https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202203061

## CRDT

---

CONFLICT RESOLUTION
* _operational transform_: funnel changes through central server, this is what Google Docs uses, a bunch of algorithms have been applied and found to fail
* _CRDT_: maintain each user's data in format that clients can resolve themselves https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type
> CRDT is a collection of data types that all share a very nice property: they can always be merged. It’s not always the perfect merge, and not everything can be made into a CRDT, but IF you can put your data into a CRDT, you can be sure: all merges will go without conflicts. https://tonsky.me/blog/crdt-filesync/
* local-first https://tonsky.me/blog/crdt-filesync/
> Prefers keeping your data local but it still goes to the internet occasionally to sync with other users, fetch data, back up, etc.  If it doesn't go to the internet at all, it's just local software. If it doesn't work offline with data it already has, then it's just normal cloud software. You all know the type - sorry, Dave, I can't play the song I just downloaded because your internet disappeared for one second
* syncing without CRDT https://tonsky.me/blog/crdt-filesync/
> But what happens if you change the state on two machines? Well, you get a conflict file:
```sh
foo.md
foo-conflict-20240705-0981234.md
```
* syncing with CRDT https://tonsky.me/blog/crdt-filesync/
> We can solve conflicts by opening both files, merging states, and saving back to the original file.
* BYO https://github.com/tonsky/crdt-filesync https://automerge.org/ https://github.com/jackyzha0/bft-json-crdt
* https://www.thoughtworks.com/radar/languages-and-frameworks/electric

more crdt
* https://softwareengineeringdaily.com/2017/12/08/decentralized-objects-with-martin-kleppman/ https://www.inkandswitch.com/local-first.html https://github.com/xi-editor/xi-editor/issues/1187#issuecomment-491473599 https://news.ycombinator.com/item?id=37764581 https://martin.Kleppmann.com/2020/07/06/crdt-hard-parts-hydra.html https://caolan.uk/articles/inside-a-collaborative-text-editor/ vs OT (operational transformations) https://news.ycombinator.com/item?id=24176455 https://news.ycombinator.com/item?id=24617542 https://news.ycombinator.com/item?id=24790170 https://www.youtube.com/watch?v=Paau_t0aZKw https://automerge.org/ https://vlcn.io/blog/gentle-intro-to-crdts.html https://github.com/alangibson/awesome-crdt https://github.com/jackyzha0/bft-json-crdt

## Paxos

## Raft

* _leader election_: Raft algorithm https://www.micahlerner.com/2020/05/08/understanding-raft-consensus.html Paxos https://news.ycombinator.com/item?id=24906225
Raft https://raft.github.io/
* start here https://pyvideo.org/pygotham-2017/an-introduction-to-the-raft-distributed-consensus-algorithm.html https://news.ycombinator.com/item?id=31416812 https://notes.eatonphil.com/distributed-postgres.html https://news.ycombinator.com/item?id=35246228
* BYO https://eli.thegreenplace.net/2020/implementing-raft-part-1-elections/ https://github.com/streed/simpleRaft https://github.com/bbbilibili/raft-1----python https://github.com/erewok/raft-py https://github.com/xwhan/Raft-python https://github.com/jackyzha0/miniraft
* https://www.micahlerner.com/2020/05/08/understanding-raft-consensus.html https://www.micahlerner.com/2020/05/09/understanding-raft-consensus-part-2.html
* https://www.confluent.io/blog/why-replace-zookeeper-with-kafka-raft-the-log-of-all-logs/
* https://www.hytradboi.com/2025/2016d6c4-b08d-40b3-af2f-67926ca8521f-enough-with-all-the-raft

## VSR

🗄️ `dbms.md` TigerBeetle

= viewstamped replication
> If you have not heard of VSR, don't worry: Paxos and Raft have been the consensus protocols people use. Joran Dirk Greef, the author of TigerBeetle, a fast and robust financial accounting database, has only recently popularized VSR. One of the great features of VSR is that its essential operation is relatively easy to grasp, whereas Paxos and Raft are notoriously complex. 📙 Enberg latency

# 🏦 TRANSACTIONS

🗄
* `design-patterns.md` unit of work
* `data/internals.md` storage
📚
* Bradshaw ch. 8
* Kleppmann ch. 7

📍 rf re: 'dbms taxnomy'

* _serializability_: ordered transactions https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html

---

> A mistake we made in the first few months of operation that has some cost today was not carefully delimiting the boundaries of database transactions. In Wave’s codebase, the SQLAlchemy database session is a request-global variable; it implicitly begins a new database transaction any time a DB object’s attribute is accessed, and any function in Wave’s codebase can call commit on the session, causing it to commit all pending updates. This makes it difficult to control the time at which database updates occur, which increases our rate of subtle data-integrity bugs, as well as making it harder to lean on the database to build things like idempotency keys or a transactionally-staged job drain. It also increases our risk of accidentally holding open long-running database transactions, which can make schema migrations operationally difficult. https://danluu.com/simple-architectures/

https://www.hytradboi.com/2025/38d3ed59-9167-4853-9366-d43ea802ec26-reliable-serverless-needs-distributed-transactions
https://hakibenita.com/django-nested-transaction
* https://jepsen.io/analyses/mysql-8.0.34
https://sqlfordevs.com/transaction-locking-prevent-race-condition
https://blog.thibaut-rousseau.com/blog/sql-transactions-in-go-the-good-way/

transactions & isolation levels 📙 Beaulieu 12
* https://retool.com/blog/isolation-levels-and-locking-in-relational-databases/ https://jahfer.com/posts/innodb-locks/ https://www.postgresql.org/docs/9.5/transaction-iso.html
* _transaction_: unit of work https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html https://sqlite.org/transactional.html https://news.ycombinator.com/item?id=33934694
* _commit_: save change; happens in two phases http://dbmsmusings.blogspot.com/2019/01/its-time-to-move-on-from-two-phase.html
* _serializable_: transactions only execute concurrently if end result is same as them executing sequentially
* repeatable read: 
* DDL changes can be transactional as well https://news.ycombinator.com/item?id=28077797

## ACID

📙 Kleppmann 7, section 2 🗄 `django.md` design https://lethain.com/distributed-systems-vocabulary/

* https://www.youtube.com/watch?v=yaQ5YMWkxq4
* _atomic_: transaction succeeds/fails as an entire unit https://brandur.org/postgres-atomicity
* NoSQL kinda does http://aosabook.org/en/nosql.html
> Most NoSQL systems pick performance over full ACID guarantees, but do provide guarantees at the key level: two operations on the same key will be serialized, avoiding serious corruption to key-value pairs. For many applications, this decision will not pose noticeable correctness issues, and will allow quick operations to execute with more regularity. It does, however, leave more considerations for application design and correctness in the hands of the developer.
* _consistent_: transaction changes db from one valid state to another 
* eventual consistency 📝 Vogel https://dl.acm.org/doi/10.1145/1435417.1435432
* semantics https://lethain.com/distributed-systems-vocabulary/
* _isolated_: protection from dirty read
* no transaction affects another happening at the same time 📙 Conery 335
* _durable_: successful transaction will survive hardware fault e.g. server restart 📙 Kleppmann 226
* nothing can change transaction except another update 📙 Conery 335
* uses `fsync` http://aosabook.org/en/nosql.html https://sirupsen.com/napkin/problem-10-mysql-transactions-per-second

## CAP theorem

---

Petrov ch. 11

🗄 `modeling.md` probabilistic data structures

* https://www.youtube.com/watch?v=_RbsFXWRZ10 https://softwareengineeringdaily.com/2023/07/25/cap-theorem/
* _CAP theorem_: tradeoffs if network partition
* _consistency_: ACID
* eventually consistent https://cloudonaut.io/my-mental-model-of-aws/
* _availability_: res for req
* _partition tolerance_: works offline 📙 Conery 336
* C: refuse to incoming reads/writes
* A, P: (db remains available but other cluster members becoming inconsistent)
* choose consistency 📙 `evans-linux.pdf` 2

## consistency

🧠 https://chatgpt.com/c/6717a9cd-1f04-8004-8686-4758cb6fe382

* _sequential consistency_: everyone sees changes in the same order, but they might not see them at the exact same time
* _strong consistency_: everyone sees the same data instantly
* _eventual consistency_: when db gets write operation, responds w/ ack and then does write when it gets time, meaning one node could receive write, ack, write it, and then need time to propagate write to other nodes, which means during that time the system would be in a state of inconsistency
* benefit: you can put lots of processing power behind your db so the walltime of inconsistent states should be very short; aka 'AP system' 📙 Conery 337-8

---

more on time https://www.hytradboi.com/2025/9dc496a2-a5ca-4d41-a5e6-7b74bf409415-use-of-time-in-distributed-databases---dont-fall-behind-the-times

```txt
What it means: Everyone sees the same data instantly.
Example: You post a picture on Instagram, and as soon as you do, everyone who checks your profile sees it right away.
Analogy: Imagine a classroom where every student gets a copy of the same note at the exact same moment.
Use Case: Online banking — if you transfer money, both you and the bank need to see the same account balance immediately.

What it means: Everyone sees changes in the same order, but they might not see them at the exact same time.
Example: If you send two messages (“Hi” then “How are you?”), everyone will see them in that order, even if there’s a slight delay.
Analogy: In a game of "telephone," every player hears the previous person’s words in sequence, but each message takes time to pass along.
Use Case: Collaborative editing tools, where the sequence of changes matters, even if they’re slightly delayed.

What it means: Everyone will eventually see the same data, but not right away.
Example: You update your Twitter bio, but it takes a minute or two for everyone to see the change.
Analogy: Imagine delivering a package — it might take time, but the recipient will eventually get it.
Use Case: Social media feeds, where it's okay if some users see an update a bit late

Strong consistency = Instant and same for everyone.
Sequential consistency = Changes happen in the same order but not necessarily at the same time.
Eventual consistency = Everyone will see the same data, but it might take a while.
```

* https://jepsen.io/consistency
* https://www.youtube.com/watch?v=rpqsSkTIdAw
* eventually consistent = eventually corrupt https://www.youtube.com/watch?v=h8cyPIEfxQY 7:45
* https://robertovitillo.com/what-every-developer-should-know-about-database-consistency/

## locks

* _lock_: db disallows other processes to access object (table, row, etc.)
* 'held' by transaction https://jahfer.com/posts/innodb-locks/
* handle at app level by throwing error https://lincolnloop.com/blog/distributed-locking-django/
* _latch_: lightweight lock 📙 Kleppmann 82
* _dirty read_: read uncommitted data
* e.g. transaction 1 updates a row, transaction 2 reads the updated row before transaction 1 commits the update, transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed https://retool.com/blog/whats-an-acid-compliant-database/

## retry

🗄️ `algos.md` recursion

---

🗄️ `security.md` DOS
💻 https://github.com/zachvalenta/DOS-lab
🧠 DOS https://claude.ai/chat/dec00ad7-12fc-4879-bccf-86db78d879d2
📹 https://www.youtube.com/watch?v=BxikFuvaT1Y @ 3:30

* _backoff_: time btw retry https://www.youtube.com/watch?v=BxikFuvaT1Y [3:20]

LIBS
* _recur_: https://github.com/dbohdan/recur
* _retry_: https://calmcode.io/shorts/retry.py
* _stamina_: https://github.com/hynek/stamina https://calmcode.io/course/stamina/introduction https://www.youtube.com/watch?v=BxikFuvaT1Y
* _tenacity_: https://github.com/jd/tenacity

# 🟨 ZA

SEMANTICS
* _centralized_: you own all the servers https://drewdevault.com/2020/09/20/The-potential-of-federation.html
* _peer to peer (p2p)_: you only own your serverr
* _federation_: servers work together but not p2p https://lwn.net/Articles/687294/ https://github.com/mastodon/mastodon
* _distributed system_: no shared memory, no shared clock https://news.ycombinator.com/item?id=26089683 https://www.warpstream.com/blog/the-case-for-shared-storage
* https://danluu.com/butler-lampson-1999/
* needs coordination across network/cores 📙 Jeffrey distributed [4]
* hard https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
> You need whole new categories of instrumentation and logging to getting understanding that isn't quite as good as what you'd get from the logs of a monolithic application. https://pythonspeed.com/articles/dont-need-kubernetes/
* why: availability, durability, flexibility, locality https://news.ycombinator.com/item?id=29006223
> What happens when that database fails? Are you OK losing some data, or do you want the data to be synchronously replicated off the machine and be available somewhere else after failure? Distribution isn't only about scale, it's also about availability.
> What happens when that database loses some data? Do you want an up-to-the second backup, or point-in-time recovery? Or are you OK restoring last night's backup? Distribution isn't only about scale, it's also about durability.
> What happens when you need to run an expensive business process ad-hoc? Do you want it to be easy to scale out reads, or to export that data to an analytics system? Or are you OK building something else to handle that case? Distribution isn't only about scale, it's also about flexibility.
> What happens when you want to serve customers in one market, and make sure that their data stays local for regulatory compliance reasons or latency? Are you OK with having separate databases? Distribution isn't only about scale, it's also about locality.
* _sidecar_: run in separate process
> A very general solution could be to wrap the code we need in some kind of server interface and run it as a separate process; this kind of process is called a sidecar - it's launched specifically to provide additional functionality for another process. Whichever inter-process communication (IPC) mechanism we use, the benefits of this approach are many - isolation, security, language independence, etc. In today's world of containers and orchestration this approach is becoming increasingly more common; this is why many of the links about sidecars lead to k8s and other containerized solutions. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* _new SQL_: relational semantics + non-relational scaling
* more resistant to CAP theory resistant SQL i.e. seems to shard more finely so that in network partition some very high % of cluster can remain available i.e. trade-off still there just minimized to the point that most users won't notice https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37

---

* mesh, service weaver https://serviceweaver.dev/blog/quick_intro.html
* _Jepsen analysis_: standard safety in distributed/transactional systems https://news.ycombinator.com/item?id=8385970 https://news.ycombinator.com/item?id=26645654 https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html
* _GFS (Google File System)_: https://www.micahlerner.com/2020/03/22/understanding-googles-file-system.html

## blockchain

📙 https://www.manning.com/books/grokking-bitcoin
🔗 https://a16zcrypto.com/

* design https://unwttng.com/what-is-a-blockchain https://a16z.com/2018/02/10/crypto-readings-resources/
* https://cdixon.org/2018/02/18/why-decentralization-matters
> Blockchains are special computers that anyone can access but no one owns. https://twitter.com/cdixon/status/1442201642338643969
* BYO https://news.ycombinator.com/item?id=27594943 https://norswap.com/blockchain-how/ https://hackernoon.com/learn-blockchains-by-building-one-117428612f46 
* history: https://danromero.org/crypto-reading/
* design: size of chain makes fraud difficult bc would have tamper with block, then re-write proceeding blocks on all nodes
* _blockchain_: db distributed over p2p network w/ each node holding entire db https://danielmiessler.com/study/blockchain/
* _smart contract_: app using blockchain
* _oracle_: data ingestion onto chain

## caching

📙 Christian chapter 4
🗄
* `http.md` caching
* `system/infra.md` proxy

* _cache_: tmp storage for read; e.g. browser (SQLite) network (CDN) db (connection pool); can cache to either memory or disk https://danielmiessler.com/blog/nginx-caching-tempfs/
* _buffer_: tmp storage for write
> Python's standard out is buffered (meaning that it collects some of the data "written" to standard out before it writes it to the terminal). Calling sys.stdout.flush() forces it to "flush" the buffer, meaning that it will write everything in the buffer to the terminal, even if normally it would wait before doing so. https://stackoverflow.com/questions/10019456/usage-of-sys-stdout-flush-method
* _eviction_: rm item based on usage e.g. LRU
* _expiration_: rm item based on TTL
* _thrashing_: when computation continuously interrupted by context switch of cache items from one program to another resulting in no computation being done
* _cache stampede_: user req for item not in cache, code begins to generate, during generation other reqs for same item, code begins n generations, server falls over https://github.com/viccon/sturdyc
* avoid by putting flag in cache to say "hey, I'm working on creating this item"

---

https://www.openmymind.net/Do-More-In-Process-Caching/
https://www.openmymind.net/Caching-Your-Worst-Best-Friend/
* _LFU_: 
> alternative https://adriacabeza.github.io/2024/07/12/caffeine-cache.html
* _LRU_: ensures cache full/hot as possible; used by application caches https://calpaterson.com/ttl-hell.html https://jamesg.blog/2024/08/18/time-based-lru-cache-python/ https://danluu.com/2choices-eviction/ https://www.openmymind.net/Writing-An-LRU-Cache/
```python
# There's nothing wrong with the above code but it only allows for strategy #1: never invalidate https://calpaterson.com/ttl-hell.html
from functools import lru_cache
@lru_cache(maxsize=1000)
def get_slow_thing_v1(thing_id):
    thing = get_slow_thing_from_a_database_layer(thing_id)
    return thing
```
* _update-on-write_: update cache item on db write
> Sometimes you want to cache something that will change. For example, your application's User object: username, email address, postal address, etc. This data is bound to change over time but is also accessed extremely frequently, often on every request or as part of every operation. The best approach here is to update the cache whenever you update the data in your persistent store.
* flush buffer https://stackoverflow.com/questions/3167494/how-often-does-python-flush-to-a-file https://stackoverflow.com/questions/29712445/what-is-the-use-of-buffering-in-pythons-built-in-open-function
* _contention free_: https://github.com/maypok86/otter
* _namespace_: add timestamp key (210526) to item key (user-bob) https://calpaterson.com/ttl-hell.html

* e.g. Python writerow
* _flush_: write buffer to disk https://stackoverflow.com/a/15042890
* _memoization_: cache at function level https://stackoverflow.com/a/6469470 https://news.ycombinator.com/item?id=31434078
* _cold_: infrequently used data
* _hot_: frequently used data
* _cache hit_: can pull from cache
> A cache hit is hopefully much more than twice as fast as a cache miss. https://calpaterson.com/ttl-hell.html
* _cache miss_: have to go to db
> It's important never to require a cache hit - even as a soft requirement. Evictions can happen at inconvenient times - such as when some other part of the system is under load - and there mustn't be any negative consequences to a cache miss. https://calpaterson.com/ttl-hell.html
* _cache invalidation_: https://news.ycombinator.com/item?id=26686770 https://blog.cerebralab.com/The_second_hardest_thing_in_programming_-_Part_1

IDEAS https://calpaterson.com/ttl-hell.html
> Using a cache often changes the implicit complexity class of the system - downwards, and towards constant time.
> There's a snobbery about application level caches. It's more respectable to rewrite the program in a "systems programming language" (read: fast, compiled, for the serious) than to apply Memcache liberally to your PHP app (read: a "band-aid", apache2, used only by jokers).
> One particularly naughty thing to do is to store web sessions only in the cache. A cache miss then becomes an involuntary logout for the hapless user who has done nothing wrong and transgressed no one. Instead, use strategy #2 above and store the web-sessions in your database, using your cache just as a speedup.
> One tip: it's best to start by looking to invalidate. To paraphrase someone: "ask not of what you can cache - ask of what you can invalidate". If you can't invalidate something reliably, it's unlikely that you can cache it in the first place.

* https://www.youtube.com/watch?v=wh98s0XhMmQ
* design https://www.youtube.com/watch?v=bFf-A27Rc9s
https://danluu.com/cache-incidents/
https://danluu.com/intel-cat/
https://csvbase.com/blog/8
https://www.youtube.com/watch?v=dGAgxozNWFE

---

* https://softwareengineeringdaily.com/2023/08/08/database-caching-with-ben-hagan/
* TTL https://news.ycombinator.com/item?id=26620730 https://calpaterson.com/ttl-hell.html
* Cloudflare do image compression per browser (e.g. webp for Chrome) https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#44:00
https://healeycodes.com/webdev/python/beginners/tutorial/2019/07/07/introduction-to-caching-with-python.html

in Python
* BYO https://dbader.org/blog/python-memoization use a decorator https://github.com/realpython/python-guide/blob/1d5905d5d7e25ebf11cda50d3d93ac636c87a993/docs/writing/structure.rst#decorators
* built-in LRU cache https://datawhatnow.com/things-you-are-probably-not-using-in-python-3-but-should/
* https://adamj.eu/tech/2021/01/21/simple-in-memory-caching-of-django-models-with-cachetools/

in general

> A good example of a piece of functionality that is better handled with decoration is memoization or caching: you want to store the results of an expensive function in a table and use them directly instead of recomputing them when they have already been computed. This is clearly not part of the function logic. [Hitchhiker's Guide 3.1.6]

* https://www.openmymind.net/Caching-Your-Worst-Best-Friend/
* https://bhavaniravi.com/blog/caching-in-python 
* https://ieftimov.com/post/when-why-least-frequently-used-cache-implementation-golang/ 
* http://danluu.com/2choices-eviction/
* https://www.digitalocean.com/community/tutorials/web-caching-basics-terminology-http-headers-and-caching-strategies

## service discovery

🗄 consensus

---

📍
* https://www.youtube.com/watch?v=S7bsPbJvBzU
* try out Consul locally https://learn.hashicorp.com/tutorials/consul/get-started-install?in=consul/getting-started

* _service discovery_: registry of available services https://www.youtube.com/watch?v=Vv4HpLfqAz4 9:45
* aka configuration store https://github.com/zalando/patroni
* e.g. Zookeeper, etcd, Consul https://stackoverflow.com/a/48652680
* vs. static config of available services https://www.youtube.com/watch?v=Vv4HpLfqAz4 10:00
* like DNS https://www.youtube.com/watch?v=Vv4HpLfqAz4 1:35

ZOOKEEPER https://www.youtube.com/watch?v=Vv4HpLfqAz4
* high level: distributed KV store [8:35]
* impl: tree/hierarchical data model 类似 file system [8:50]
* features: service discovery + leader election https://www.youtube.com/watch?v=AS5a91DOmks 0:45
* used by: Kafka (previously) FoundationDB (itself a distributed KV store) https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html
* _znode_: node in tree [9:20]
* _node_: server in Zookeeper cluster [9:30]
