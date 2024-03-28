# ⛩️

## 参考

🔍 
* https://dba.stackexchange.com
* https://roadmap.sh/postgresql-dba

## 进步

* _22_: 📙 Bradshaw ch. 1/4/7/10/14/18
* _20_: Postgres with Django (psycopg, Docker)

# 🟩 MONGO

📙 Bradshaw guide
🎓 https://university.mongodb.com/dashboard
📜
* Mongo https://www.mongodb.com/docs/manual
* PyMongo https://pymongo.readthedocs.io/en/stable/tutorial.html

---

* `skip` https://github.com/tommyboytech/t3/pull/14059 monitoring https://um-t.slack.com/archives/CC11T8R3L/p1683919099438149
* analyzing Mongo queries https://um-t.slack.com/archives/CC11T8R3L/p1679613455293999

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

# 🐘 POSTGRES

📙 Suzuki postgres internals https://www.interdb.jp/pg/
📜
* general https://www.postgresql.org/docs/current/index.html
* guide http://postgresguide.com/
* wiki https://wiki.postgresql.org/wiki/Main_Page
* design https://news.ycombinator.com/item?id=35599118 Stonebraker https://dsf.berkeley.edu/papers/ERL-M85-95.pdf

HOW TO https://gist.github.com/cpursley/c8fb81fe8a7e5df038158bdfe0f06dbb https://news.ycombinator.com/item?id=39273954
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

ZA
* single-tenant i.e each user gets own db https://news.ycombinator.com/item?id=38171322
* transactions for perf https://news.ycombinator.com/item?id=36583317
* WAL https://simonwillison.net/2022/Oct/23/datasette-gunicorn
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
* perf https://news.ycombinator.com/item?id=26103776 https://kerkour.com/sqlite-for-servers
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

components
* _SQLite_: library https://tech.marksblogg.com/sqlite3-tutorial-and-guide.html
* Go port https://simonwillison.net/2022/Jan/30/a-cgo-free-port-of-sqlite/
* plumbing https://jvns.ca/blog/2014/09/27/how-does-sqlite-work-part-1-pages/ https://jvns.ca/blog/2014/10/02/how-does-sqlite-work-part-2-btrees/
* _sqlite3_: CLI
* _sqlite3_: also the name of the Python lib/driver https://github.com/zachvalenta/sqlite3-demo https://github.com/zachvalenta/bookcase-sjk https://sebastianraschka.com/Articles/2014_sqlite_in_python_tutorial.html

strong points https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html
* dbms in a C library
* ACID-compliant
* multithreaded https://sqlite.org/threadsafe.html
* reads parallelized 
* writes concurrent
> This means that writers queue up. Each application does its database work quickly and moves on, and no lock lasts for more than a few milliseconds
* file-based/serverless = good for unreliable network (smartphone, airplane)
* db files can deal w/ TB https://news.ycombinator.com/item?id=24178013

limitations
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

types
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
