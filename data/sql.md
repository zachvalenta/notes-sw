# ⛩️

## 参考

🔍 https://dba.stackexchange.com
📚
* Beaulieu learning sql
* Conery curious moon
* Evans star https://sql-playground.wizardzines.com/
* Faroult art of sql
* Karwin sql antipatterns https://pragprog.com/cms/errata/bksqla-errata/
* Molinaro sql cookbook

## 进步

https://roadmap.sh/sql
https://gvwilson.github.io/sql-tutorial/
* Bealieau: port notes to digital copy, domains

* grouping 📙 Evans 8, Beaulieu ch. 8
* testing SQL https://news.ycombinator.com/item?id=34602318 

INTERVIEWING
* https://github.com/alexeygrigorev/data-science-interviews/blob/master/technical.md
* https://leetcode.com/problemset/database/
* https://www.hackerrank.com/domains/sql
* https://www.youtube.com/channel/UCW8Ews7tdKKkBT6GdtQaXvQ/videos

* _23_: port Beaulieu to paper copy, rf, read rest of Beaulieu
* _21_: semantics (migrations, tables), `query-sandbox`, litecli config
* _20_: start `sjk`, Flask-SQLAlchemy (pagination, 1-m w/ backrefs, Marshmallow for nested serializers), visidata
* _19_: 📙 Beaulieu chapters 1-5 and 10; Flask-SQLAlchemy (FK, through table, raw SQL) SQLite (FK support) SQLAlchemy (core, parameterized queries)
* _18_: Flyway for Dark Canary, modeling course
* _17_: subqueries for Case

# 🚧 DDL

🗄
* `db.md` modeling
* `db.md` utils

COMMANDS
```sql
-- DB/TABLE
CREATE DATABASE <db>;  -- `sqlite3 local.db`
CREATE TABLE test_table ();
DROP TABLE <table>;
DROP DATABASE <db>;

-- ATTR
ALTER TABLE <table> ADD <col> <type>;  -- add
ALTER TABLE <table> ALTER COLUMN <col> TYPE <type> -- update type https://news.ycombinator.com/item?id=40286403
UPDATE <table> set <col>=concat('prependThis_', <col>)  -- update name
ALTER TABLE <table> DROP COLUMN <col>; -- rm
DESCRIBE mytable; -- list constraints/indexes
SHOW CREATE TABLE <tab>; -- MySQL version https://serverfault.com/q/231952 https://stackoverflow.com/a/201678
PRAGMA index_list('<tab>') -- SQLite version https://stackoverflow.com/a/49311235
```

## constraints

📙 Beaulieu chapter 13

* _constraint_: rule for attr type/value 📙 Beaulieu [30]

TYPES
* _not null_: https://www.semicolonandsons.com/episode/data-integrity-null-constraint-check-constraint
* interpolation https://hakibenita.com/sql-for-data-analysis#interpolation
* _unique_: prevents dupes values in column https://stackoverflow.com/a/21049722/6813490 https://www.semicolonandsons.com/episode/foreign-keys-and-uniqueness-constraints
* _default_: value that will be inserted in the absence of an explicit value in an insert / update statement https://stackoverflow.com/a/11862246/6813490
```sql
CREATE TABLE test_table (
    foo default 'this is the default value', -- https://www.youtube.com/watch?v=lnfrcHdE_HI 3:15
```
* _check_: value for attr must satisfy boolean expression https://www.semicolonandsons.com/episode/data-integrity-null-constraint-check-constraint 📙 Beaulieu [30]
```sql
-- https://www.postgresql.org/docs/12/ddl-constraints.html#DDL-CONSTRAINTS-CHECK-CONSTRAINTS
CREATE TABLE products (
    product_no integer,
    name text,
    price numeric CHECK (price > 0)
);
```

PRIMARY KEY (PK) 🗄 indexing `connolly.pdf`
* _candidate key_: key(s) that could serve as PK https://stackoverflow.com/a/12813385 📙 Winand [5]
* _primary key_: attr w/ unique constraint that serves as ID of record 📙 Beaulieu [6]
* _composite key_: n keys unique together used as PK
* use in pre-sorted tables (sorted by key vs. time of insertion) for faster lookups https://sqlfordevs.com/sorted-table-faster-range-scan range scan unique scan skip scan https://sqlfordevs.com/sorted-table-faster-range-scan
* slower than surrogate https://news.ycombinator.com/item?id=2786238
* https://github.com/aswinkarthik/csvdiff
* https://sirupsen.com/napkin/problem-5
* _compound key_: composite key + all keys also FK https://en.wikipedia.org/wiki/Composite_key
* e.g. join table https://www.youtube.com/watch?v=vsGDtnBCwgg
* sometimes used interchangeably w/ 'composite' https://dba.stackexchange.com/a/3137/201798 https://www.youtube.com/watch?v=lnfrcHdE_HI 1:40
```sql

```
* _natural key_: attr that goes together with other attr in table (vs. surrogate key) https://news.ycombinator.com/item?id=40580549
* _surrogate key_: unrelated to table attr https://stackoverflow.com/a/36773462
* typically auto-incremented but doesn't necessarily have to be 📙 Beaulieu [34]
```sql

```
* _sequence_: https://stackoverflow.com/a/1649128 📙 Beaulieu [34] Karwin ch. 4
* don't expose via API, use uuid https://0of1.com/blog/posts/django-staples/
* auto-increment https://retool.com/blog/how-to-work-with-auto-increment-in-sql-query/ aka identity column https://www.sqltutorial.org/sql-identity/
```sql

```

FOREIGN KEY (FK)
* _foreign key_: constraint enforcing reference to another table's PK 📙 Beaulieu [33,39]
```sql
foreign key (band) references bands (band_id)
```
* aka referential integrity aka prevent garbage in garbage out https://www.postgresql.org/docs/8.3/tutorial-fk.html
* _parent_: table to which FK refers 📙 Beaulieu [40] https://sqlite.org/foreignkeys.html#fk_basics
* _child_: table w/ FK 📙 Beaulieu [40] 5.82
* can be self-referencing? 📙 Beaulieu 5.93
* find FK referencing table ` SELECT * FROM information_schema.TABLE_CONSTRAINTS WHERE CONSTRAINT_SCHEMA='tableName' AND CONSTRAINT_TYPE='FOREIGN KEY'`
* bad when it comes to sharing and migrations? https://github.com/github/gh-ost/issues/331#issuecomment-266027731
* https://www.semicolonandsons.com/episode/foreign-keys-and-uniqueness-constraints
* _dangling identifier_: bad FK bc pointing to no longer extant ID

## migrations

🗄
* `data/eng.md` pipelines
* `django.md` migrations
* `system.md` deployment, compatibility
* `lang/python/django/migrations-sandbox`

DATA
* _data migration_: DML i.e. change data itself
* prod data in lower env is bad? https://www.thoughtworks.com/radar/techniques/production-data-in-test-environments
* backsies https://news.ycombinator.com/item?id=30788768
* dry run https://adamj.eu/tech/2022/10/13/dry-run-mode-for-data-imports-in-django/
* _fixture_: data migration using serialization
* _factory_: data migration using ORM obj https://github.com/FactoryBoy/factory_boy/

SCHEMA
* _schema migration_: DDL i.e. change schema (alongside related change in src) https://en.wikipedia.org/wiki/Schema_migration
* https://news.ycombinator.com/item?id=40186752
* no needs to manually alter tables https://realpython.com/django-migrations-a-primer/#ensuring-model-definitions-and-the-database-schema-in-sync
* can be generated from model changes https://realpython.com/django-migrations-a-primer/#avoiding-repetition
* version controllable https://realpython.com/django-migrations-a-primer/#tracking-database-schema-change-in-version-control
* aids deployment (easy rollback to previous) 🗄 `system.md` deployment
* don't run on app start https://pythonspeed.com/articles/schema-migrations-server-startup/
* BYO https://news.ycombinator.com/item?id=24577239
* moving to a difference schema entirely
```txt
There was zero downtime over the course of development. So, at no point in time could we stop support for the old model, migrate, and then start with the new model. Here’s how that worked:

* Update everything that reads the data model to support both the old and new models.
* Update everything that updates the data model to support both.
* Update everything that creates to use the new model.
* Run a task to migrate existing data to the new model.
* Once everything above is stable on prod (we waited a sprint), drop support of the old data model.
* Rename the fields in the old data model so that anything that still depends on them will break.
* (TODO) Actually delete the old data model.

This makes development much more involved than the traditional “flip a switch” approach. Namely, we have two parallel codebases live for a period of time. But, there are some advantages:

* No downtime.
* Other developers don’t have to ask “Do I develop X feature against the new model or old?”. They develop it against whatever code is currently checked in.
* You can safely roll back at any time.
* You can migrate data incrementally.
```

---

https://github.com/pressly/goose
https://github.com/amacneil/dbmate#alternatives
* SQLite https://news.ycombinator.com/item?id=31249823
* https://github.com/fabianlindfors/reshape
* linear migrations https://github.com/adamchainz/django-linear-migrations?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_89

failover, failback https://www.highgo.ca/2023/04/10/setting-up-postgresql-failover-and-failback-the-right-way/

schema migrations - scenarios
* https://www.caktusgroup.com/blog/2021/05/25/django-migrations-and-deployment
* _rollback_: https://about.gitlab.com/blog/2020/09/16/year-of-kubernetes/
> We learned in the process of moving from VMs to Kubernetes that it was extremely beneficial for us to have an easy way to move traffic between the old and new infrastructure, and to keep legacy infrastructure available for rollback in the first few days after the migration.
> And if what you care about is downtime, your first thought shouldn’t be "how do I reduce deployment downtime from 1 second to 1ms", it should be "how can I ensure database schema changes don’t prevent rollback if I screw something up." - https://pythonspeed.com/articles/dont-need-kubernetes/
> Applying a schema migration to a production database is always a risk...the migration process needs a high level of discipline, thorough testing and a sound backup strategy. https://en.wikipedia.org/wiki/Template:Database https://en.wikipedia.org/wiki/Schema_migration
* _rm attr_: instead of dropping can just hide from interface https://www.reddit.com/r/django/comments/47k7kl/how_do_i_make_a_migration_without_dropping_columns/
* _add attr_: nullable or add default for old records; if nullable, need to update API if you don't want to return those null values; defaults not recommended [Kleppmann 4.130]
> in Django, if you add default at model level, the old records are still null, yes? so you'd still have to update API to handle those, as you would if you'd made the attr nullable
> in Django, how do people handle the one-off default for existing data? before you have prod data, foo values seem fine, but curious to hear a discussion on this topic
```diff
class Foo(models.Model):
    bar = models.CharField(max_length=255)
+   baz = models.CharField(max_length=255, null=True)
```
```sh
+----+---------+----------+
| id | bar     | baz      |
+----+--------------------+
| 1  | bar val | <null>   |
| 2  | bar val | baz val  |
+----+--------------------+
```

* _sink_: https://www.tarynpivots.com/post/migrating-40tb-sql-server-database/ https://github.blog/2020-02-14-automating-mysql-schema-migrations-with-github-actions-and-more/ pivot https://news.ycombinator.com/item?id=39353502

Flyway https://flywaydb.org/documentation/ https://github.com/zachvalenta/flyway-tutorial
* how it works
> It's semi automatic because it does not find out what has actually changed in your model. You need to write actual SQL scripts that have versions. It will create a separate table to keep track what version you have in your data base and that execute the script automatically up to the point where the latest version is reached.
* _alternatives_: Liquibase https://return.co.de/blog/articles/java-development-fast/ https://github.com/amacneil/dbmate
* _CLI_: db you're connected to, what migrations need to be run; selects subset of `flyway_schema_history`; can change name of `flyway_schema_history` in `flyway.conf > flway.table`
* _config_: `flyway.conf` unless overriden from CLI
* _directory structure_: `flyway` (CLI; bash script gathers input and then runs Flyway, itself a Java app) `lib` (actual Flyway application) `sql` (ur scripts here)
* _migration script location_: `classpath:db/migration` (in src) `libexec/sql` (in local Flyway install)
* _naming conventions_: whole numbers or timestamps, pad your numbers, don't alter in `flyway.conf`
* _types_: versioned (default) repeatable https://flywaydb.org/getstarted/repeatable undo https://flywaydb.org/getstarted/undo just make a new migration file (vs. using `flyway repair`) ['How to Correct a Mistake in a Migration']
* _versions_: looks at `version` table; version numbers https://flywaydb.org/documentation/migrations#naming
* _with Java_: if you drop tables and rerun app, run `mvn clean install` before rerun (think something cached between runs (in `target`?) indicating that scripts have already been run --> this is weird bc Flyway should look to version table in the database for that)

## modeling

🔍 https://drawsql.app/templates
📙 Kent data/reality https://www.amazon.com/Data-Reality-Perspective-Perceiving-Information/dp/1935504215

* enum > FK https://um-t.slack.com/archives/C037G1E0EF2/p1686167018278999
* modeling payments https://news.ycombinator.com/item?id=36775098
* https://news.ycombinator.com/item?id=41146239&utm_term=comment

ACCESS PATTERNS
* _access pattern_: how you have to query based on schema https://calpaterson.com/non-relational-beartraps.html
* what you're prioritizing e.g. read/write vs. aggregations 📻 Macey 6:10
* _upsert_: insert or update 📙 Bradshaw [46]
* _get-or-create_: `get_or_create()` in Django
* aka find_create_find https://um-t.slack.com/archives/C037G1E0EF2/p1668542221060969

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

1-1
* = sole ownership
* impl: attr, separate table https://support.airtable.com/hc/en-us/articles/218734758#onetoone
* example: person-SSN, country-capital https://stackoverflow.com/a/15037461

1-M
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

M-M
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

IMPORTANCE
> Data models are perhaps the most important part of developing software, because they have such a profound effect: not only on how the software is written, but also how we think about the problem that we are solving. 📙 Kleppmann [31]
> This is one reason it's so important to model your domain correctly: if, for example, you make something a property of A when it should be a property of B, the penalty is often that operations that formerly required checking all the As or all the Bs now require checking all the As and all the Bs. https://www.natemeyvis.com/writing/on-quadratic-complexity/
> Take data access patterns very seriously!...it's easy to turn something that should be logarithmic time into polynomial time https://calpaterson.com/activerecord.html

SEMANTICS
* _domain_: thing you're trying to model https://calpaterson.com/non-relational-beartraps.html
* _schema_: model of thing https://calpaterson.com/non-relational-beartraps.html
* general usage: table names + column name/type https://news.ycombinator.com/item?id=22723277
* Postgres usage: container for obj such as table or view https://news.ycombinator.com/item?id=22721914

NORMALIZATION
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

## typing

📜 https://www.postgresql.org/docs/current/datatype.html
🗄 `db.md` SQLite/design
📙 Beaulieu chapter 7

TYPES
* _char_: fixed e.g. state abbreviations 📙 Beaulieu [20]
* _varchar_: variable 📙 Beaulieu [21]
* _blob_: `text` in Postgres, `longtext` in MySQL https://news.ycombinator.com/item?id=40317485
* _datetime_: https://stackoverflow.com/q/1933720 as integer https://stackoverflow.com/a/17227196 🗄 `sjk/golf`
* _integer_: 
> The type integer is the common choice, as it offers the best balance between range, storage size, and performance. The smallint type is generally only used if disk space is at a premium. The bigint type is designed to be used when the range of the integer type is insufficient. https://www.postgresql.org/docs/current/datatype-numeric.html#DATATYPE-INT
* _boolean_: 
* _numeric_: int (normal stuff) bigint (item number, GUID) float (precision) [Beaulieu 2.21] 🗄 `math.md` encoding
* avoid non-floating point types unless stricty necessary https://www.sqlstyle.guide/#choosing-data-types
* avoid vendor-specific data types https://www.sqlstyle.guide/#choosing-data-types
* type conversion https://news.ycombinator.com/item?id=28259104
```sql
-- casting
select cast (avg(price) as integer) as "average sale price" from house;
-- timestamp https://pgexercises.com/questions/basic/date.html non-overlapping times https://sqlfordevs.com/non-overlapping-time-ranges?ref=Newsletter
YYYY-MM-DD HH:MM:SS  -- fmt
where foo_date > '1962-07-03' -- compare
-- user names
family_name, other_given_names  -- https://www.youtube.com/watch?v=458KmAKq0bQ 7:30 https://www.w3.org/International/questions/qa-personal-names
```

NULL 📙 Beaulieu [32,82]
* _null_: absence of a value e.g. `termination_date` for newly hired employee
* wat: an expression can be null but never equal null 📙 Beaulieu [82]
```sql
null != null  -- true 📙 Beaulieu [82]
select (0 is not null) and ('' is not null)  -- true
```

MATH
* integer division yields integer (`select 51/2` = `25`) 🗄 FUQ - percent
* cast to float for precision division https://hakibenita.com/sql-dos-and-donts#be-careful-when-dividing-integers
* for decimals, multiply something by 1.0 (`select 1.0*51 / 2` = `25.5`)
* boolean: `0` falsy `1` truthy https://selectstarsql.com/beazley.html
```sh
select 0 or 1  # 1
```
* avoid doing math w/ floating point https://dba.stackexchange.com/questions/76391/sum-of-double-precision-gives-weird-results
```sql
select track, sum(share), count(*) from splits group by track having sum(share) > 100.0;
foo_isrc,200.0,4
bar_isrc,100.0,10
baz_isrc,100.0,4
qux_isrc,200.0,2

select track, sum(share), count(*) from splits group by track having cast(sum(share) as int) > 100.0;
foo_isrc,200.0,4
qux_isrc,200.0,2
```

# 🚜 DML

CLAUSES
* _clause_: part of select statement 📙 Beaulieu [47]
* _select_: what attr to incl in result set 📙 Beaulieu [49]
* _from_: what tables and how they're linked 📙 Beaulieu [53]
* _where_: filter 📙 Beaulieu [58]

EXECUTION ORDER
* before execution, dbms checks query 1) perms 2) syntax 📙 Beaulieu [41]
* only `select` is mandatory https://hakibenita.com/sql-for-data-analysis#basics
* types of execution order: syntactical/logical (e.g. no `where` after `having`) and actual (e.g. `limit` query engine will limit first) 📙 Bradshaw 166
* syntactical/logical order 📙 Evans 5, 14 https://jvns.ca/blog/2019/10/03/sql-queries-don-t-start-with-select/
* order of tables in join don't matter 📙 Beaulieu [95]
```text
├── from
├── predicates
│   └── where
│   └── group by
│   └── having
├── select
│   └── window functions 📙 Evans [14]
│   └── order by 📙 Evans [13]
│   └── limit
```

SUBQUERIES 📙 Beaulieu ch. 9
* _subquery_: query contained within another query 📙 Beaulieu [53]
* _containing query_: query that wraps subquery 📙 Beaulieu [54]
* _scalar subquery_: return single val from subquery https://learnsql.com/blog/subquery-vs-join/
* more readable but generally slower than joins https://stackoverflow.com/a/2577224
* more thinkable than joins https://stackoverflow.com/a/2577188
```sql
containing_query = (subquery)  -- 1 (scalar)
containing_query in (subquery)  -- n
```

CRUD
```sql
-- 1 attr, 1 val
INSERT INTO danzi(customer) VALUES ('alice');
-- 1 attr, n val
INSERT INTO danzi(customer) VALUES ('alice'), ('bob');
-- n attr, 1 val
INSERT INTO danzi(customer, price) VALUES ('alice', 15)
-- n attr, n val
INSERT INTO danzi(customer, price) VALUES ('alice', 15), ('bob', 10);

UPDATE <tab> SET <col>=0 WHERE id=3;
DELETE FROM <tab> WHERE id=3;
```

## functions

FUNCTION
* _function_: built-in function provided by dbms
* has return value https://stackoverflow.com/a/771959
* e.g. SQLite `substr()`

PROC
* _procedure_: user-defined function
* no return value https://stackoverflow.com/a/771959
* aka stored procedure
* impl via procedural language availble in dbms
* too many and you've got business logic split btw application and db https://news.ycombinator.com/item?id=24845300

TRIGGER
* _trigger_: hook e.g. on record update write previous state to archive/audit table https://www.youtube.com/watch?v=LFIAqFt9z2s
* alternative to audit table is abadoning update-in-place entirely https://www.hytradboi.com/2022/baking-in-time-at-the-bottom-of-the-database
* avoid data updates by tracking things from which current info can be derived i.e. DOB instead of age
```sql
--  https://github.com/jOOQ/sakila/blob/main/sqlite-sakila-db/sqlite-sakila-schema.sql
CREATE TRIGGER actor_trigger AFTER INSERT ON actor
 BEGIN
  UPDATE actor SET last_update = DATETIME('NOW') WHERE rowid = new.rowid;
 END
;
```

AGGREGATE 📙 Beaulieu ch. 8
* _aggregate_: function that returns single val from result set https://www.postgresql.org/docs/12/tutorial-agg.html 🗄 scalar
* operates on whole table or on group 📙 Beaulieu 8.149
* can't use in WHERE clause
* can't layer https://stackoverflow.com/a/2436957
* _count_: ignores null https://hakibenita.com/sql-dos-and-donts#be-careful-when-counting-nullable-columns
```sql
select
    count(distinct addr) as "listings",
    cast (avg(price) as integer) as "avg",
    max(price) as "high",
    min(price) as "low"
from house
```
* operates on grouped result vs. table result set
```sql
select track, count(*) from splits group by track;
```
* counting groups 📍 📙 Beaulieu [149]
```sql
# SPLITS W/ SHARES < 100%: 66
select count(*) over (), track, sum(share), count(*) from splits group by track having cast(sum(share)as int) < 100;
```

## grouping

📙 Beaulieu ch. 8
🗄 `math.md` stat

GROUP BY
* _group by_: rs w/ 1 record for each group 📙 Evans [8]
* group data by column value 📙 Beaulieu [60]
* aka binning https://hakibenita.com/sql-for-data-analysis#binning
* aka pivot table https://hakibenita.com/sql-for-data-analysis#pivot-tables https://realpython.com/how-to-pandas-pivot-table/
```sql
-- only columns worth selecting are the grouped by column and aggregates
select count(*) from executions group by "First Name" 
select "First Name", count(*) from executions group by "First Name" 
select "First Name", count(*) from executions group by "First Name" order by 2 desc

-- can't usefully access non-aggregated columns
-- e.g. this query will bring back an execution age for one of the prisoners in the group, but what good is that?
select "Age at Execution" from executions group by "First Name" 
```
* 📍 practice https://www.helenanderson.co.nz/sql-aggregate-functions/
* 📍 rollup https://hakibenita.com/sql-for-data-analysis#subtotals
* 📍 rolling https://ponder.io/python-for-finance-pandas-resample-groupby-and-rolling/
* https://stackoverflow.com/a/24767207
```sql
select col, count(*) from tab group by col
```

PARTITION BY
* _partition_: group by but retain individual records w/ group https://stackoverflow.com/a/2404574
* can do in DDL? https://www.postgresql.org/docs/10/ddl-partitioning.html#DDL-PARTITIONING-DECLARATIVE
* group created for aggregation 📙 Molinaro
* this tutorial is just ok https://www.youtube.com/watch?v=6trOvsL80Oo
* https://www.youtube.com/watch?v=EPUayNC5ku4
* used for bulk deletes in audit table https://sqlfordevs.com/partition-delete-old-rows

WINDOW FUNCTIONS 📙 Evans 14-16
* _window_: reference value in previous row 📙 Evans 14
* introduced to SQL in 2005 https://www.youtube.com/watch?v=H6OTMoXjNiM 0:30
```sql
-- syntax
expression OVER (window)
-- functions https://twitter.com/b0rk/status/1179419244808851462/photo/1
lag() sum() ntile() row_number()
```
* link to partition by https://twitter.com/b0rk/status/1179419244808851462/photo/1
* https://www.postgresql.org/docs/9.1/tutorial-window.html
* 📙 Winand 156
* https://www.youtube.com/watch?v=XBE09l-UYTE
* types https://www.helenanderson.co.nz/sql-window-functions-part-1/
* running total https://learnsql.com/blog/what-is-a-running-total-and-how-to-compute-it-in-sql/ https://learnsql.com/blog/sql-non-equi-joins-examples/
* https://hakibenita.com/sql-for-data-analysis#running-and-cumulative-aggregation

## joins

📙 Beaulieu ch. 5, 10

BASICS
* _join_: include attr from n tables in result set 📙 Beaulieu [88]
* for-loop combining records from diff tables based on condition
```sql
select deal.deal_id, house.addr
from deal
    join house on deal.house = house.house_id
    join renter on deal.renter = renter.renter_id
```
* _driving table_: starting point of join 📙 Beaulieu [95]
* _through table_: tables included in the join

CONDITIONS
```sql
-- WHERE: old syntax 📙 Beaulieu [91]
select * from employee, lob where employee.lob_id = lob.id
-- ON: new syntax (SQL92), portable across dbms 📙 Beaulieu [92]
select * from employee, lob on employee.lob_id = lob.id
-- USING_: use w/ equi join if tables have attr w/ same name 📙 Beaulieu [90] https://www.neilwithdata.com/join-using
select * from employee, lob using (lob_id)
```
* no condition = cartesian result set 📙 Beaulieu [35]

---

todo
* https://antonz.org/sql-join/
* https://news.ycombinator.com/item?id=36575784
* https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/
* https://github.com/enochtangg/quick-SQL-cheatsheet#joins
* https://news.ycombinator.com/item?id=27760154
* https://alexpetralia.com/posts/2017/7/19/more-dangerous-subtleties-of-joins-in-sql


INNER/OUTER, LEFT/RIGHT
* _inner_: result set doesn't include rows for which the join fails 📙 Beaulieu [90]
* dbms default 📙 Beaulieu [90]
* most common type 📙 Evans 10
```sql
-- 📍 ADD TO LITECLI.CONF
select r.name, h.addr
from house as h
    join renter as r
    on r.district = h.district
```
* _outer_: result set does include rows for which join fails 📙 Beaulieu [90]
```sql
```
* _left_: left table determines count of result set 📙 Beaulieu 10.187
* right table provides match if found 📙 Evans 11-12
```sql
select r.name, d.deal_id
from renter as r
    join deal as d
    on r.renter_id = d.renter
+--------------+---------+
| name         | deal_id |
+--------------+---------+
| helen boss   | 1       |
| tom white    | 2       |
| sofia brown  | 3       |
| michael lane | 4       |
+--------------+---------+

select r.name, d.deal_id
from renter as r
    left join deal as d
    on r.renter_id = d.renter
+---------------+---------+
| name          | deal_id |
+---------------+---------+
| helen boss    | 1       |
| michael lane  | 4       |
| susan sanders | <null>  |
| tom white     | 2       |
| sofia brown   | 3       |
+---------------+---------+
```
* _right_: right table determines count of result set 📙 Beaulieu 10.187
```sql
select d.deal_id, r.renter
from renter as r
    right join deal as d
    on r.renter_id = d.renter
+---------------+---------+
| name          | deal_id |
+---------------+---------+
| helen boss    | 1       |
| michael lane  | 4       |
| susan sanders | <null>  |
| tom white     | 2       |
| sofia brown   | 3       |
+---------------+---------+
```

SELF, CROSS, NATURAL, EQUI
* _multi_: use same table n times 📙 Beaulieu [96]
* need to use multiple aliases 📙 Beaulieu [97]
```sql
-- pass
```
* _self_: two instances of same table 📙 Beaulieu [98]
```sql
-- pass
```
* _cross_: generates cartesian product due to lack of `on` clause 📙 Beaulieu [89] Takahashi [42] 🗄 `math.md` set theory
```sql
select * from house join deal
```
* _natural_: don't specify `on` clause 📙 Beaulieu [198]
* server figures out (which it will only do if there's matching attr name across tables) 📙 Beaulieu 10.198
* don't use!
```sql
-- pass
```
* _equi_: equality 📙 Beaulieu [94-digital-copy]
```sql
-- pass
```
* _non-equi_: membership https://learnsql.com/blog/sql-non-equi-joins-examples/ 📙 Beaulieu [94-digital-copy]
```sql
-- TRICK FOR BOTH OF THESE IS USING A NON-EQUI JOIN TO UNMATCH PERMUTATIONS 🗄 `MATH.MD` SET THEORY
SELECT r1.name, r1.district, r2.name, r2.district
FROM renter as r1
    JOIN renter r2 ON r1.district = r2.district
    AND r1.renter_id < r2.renter_id
-- FIND DUPES
select h1.house_id, h1.addr as "first occurence", h2.house_id, h2.addr as "second occurence"
from house as h1
    join house as h2 on h1.addr = h2.addr
    and h1.house_id < h2.house_id
-- RECOMMENDATIONS
select r.name, h.house_id, h.district, h.addr, h.bedrooms, h.price
from renter as r
join house as h
    on r.district = h.district
    and h.price between r.rent_min and r.rent_max
    and r.bedrooms <= h.bedrooms
where h.house_id not in (select house from deal)
```

## operations

🗄 `language.md` semantics

RELATIONAL 📙 Takahashi [43]
* _projection_: filter on attr i.e. `SELECT` https://stackoverflow.com/a/1031101 📙 Takahashi [43] Beaulieu [44-5]
* _selection_: filter on value i.e. `WHERE` 📙 Beaulieu [52-54]
* _division_: extract records that exist in both numerator/denomenator table but only the columns that exist only in numerator 📙 Takahashi [45]
* + join

SET 🗄 `math.md` set theory 📙 Beaulieu ch. 6
* combine inputs to produce output [Takahashi 2.39]
* except https://github.com/enochtangg/quick-SQL-cheatsheet#1-finding-data-queries
* https://github.com/enochtangg/quick-SQL-cheatsheet#find
```sql
-- DATA
-- customers: alice bob candace erin
-- employees: bob david frank

-- FMT
-- SELECT person FROM customer
-- <KEYWORD>
-- SELECT person FROM employee

UNION
-- el from both incl dupes https://stackoverflow.com/a/49928
-- alice, bob, bob, candace, david, erin, frank

UNION ALL
-- el from both minus dupes https://hakibenita.com/sql-dos-and-donts#know-the-difference-between-union-and-union-all
-- alice, bob, candace, david, erin, frank

INTERSECT
-- el shared [Beaulieu 6.100]
-- bob

MINUS
-- el unique to first set; aka difference [Bhargava 8.150]
-- alice, candace, erin
```

## predicates

📙 Beaulieu ch. 4

* _predicate_: filter https://www.postgresql.org/docs/13/functions-comparison.html https://use-the-index-luke.com/sql/explain-plan/oracle/filter-predicates
* _condition_: clause in predicate 📙 [67]
* group w/ parentheses 📙 Beaulieu [59]

WHERE / HAVING
* _where_: condition on individual records
* occurs before `group by` https://www.helenanderson.co.nz/sql-aggregate-functions/
* _having_: condition on group 📙 Beaulieu [149]
* occurs after `group by` https://stackoverflow.com/a/9253267
```sql
-- comparison operator 📙 Beaulieu 4.63
where num >= 5

-- identity operator
where num is not null

-- membership; how subqueries work 📙 Beaulieu 4.71
where "name" in ('alice', 'bob');

-- range; is inclusive 📙 Beaulieu [75]
where num between 3000 and 5000;
```

FUQ
```sql
-- MULTIPLE CONDITIONS
select foo
from dsp
join files
on dsp.id = files.id
where dsp.bar='bar' and files.baz='baz'

-- STRING TRUTHY/FALSY
select count(*) from executions where height != ''

-- PERCENTAGE OF ATTR W/ VAL https://stackoverflow.com/a/3919859
select
    (select count(height) from executions where height = '') * 100
    /
    (select count(height) from executions)
```

GLOBBING
* not portable across DBMS 📙 Karwin [15]
* wildcards: `_` single char `%` n char 📙 Beaulieu [80]
```sql
-- '%query%' = contained anywhere
-- https://github.com/enochtangg/quick-SQL-cheatsheet#1-finding-data-queries
select artists, genres from artist where genres like '%rock%'

LIKE 'foo%'; -- starts w/ 'foo'; '%' is n char [Beaulieu 4.74-5]
LIKE '%foo'; -- ends w/ 'foo'
LIKE '_foo'; -- has a single char before 'foo'
LIKE '%foo%'; -- contains anywhere https://pgexercises.com/questions/basic/where3.html

ILIKE 'Foo'; -- case sensitive
ILIKE 'foo'; -- case insensitive https://docs.djangoproject.com/en/3.1/ref/models/querysets/#iexact

where RIGHT(<col>, 3); -- 📍 slice right: select subset of string ending with index n [Beaulieu 3.59]
where LEFT(<col>, 1) = 'T'; -- attr starts w/ 'T' -- left: select subset of string starting with index n [Beaulieu 4.73]
```

## select

DISTINCT
* _ALL_: default (which is why you never see it) 📙 Beaulieu [52]
* _DISTINCT_: dedupe
* slow for large result set bc have to sort 📙 Beaulieu [52]
* works on records, not columns https://discuss.codecademy.com/t/can-we-apply-distinct-to-a-select-query-with-multiple-columns/349723
```sql
--
-- DEDUPE W/ N COLUMNS
--

-- can't just use distinct bc works on records, not columns
-- i.e. result set valid bc each record different e.g. 5 rose st + house_id 1 != 5 rose st + house_id 3
select distinct house_id, addr from house
+----------+-----------------+
| house_id | addr            |
+----------+-----------------+
| 1        | 5 rose street   |
| 2        | 12 main street  |
| 3        | 5 rose street   |
+----------+-----------------+

-- the other approach here is using group by https://stackoverflow.com/a/12632129 📙 Molinaro
select house_id, addr from house group by addr
+----------+-----------------+
| house_id | addr            |
+----------+-----------------+
| 2        | 12 main street  |
| 3        | 5 rose street   |
| 4        | 3 nice street   |
+----------+-----------------+


SELECT saleprice, saledate
FROM   sales
GROUP  BY saleprice, saledate
HAVING count(*) = 1 

SELECT MIN(id) FROM sales
GROUP BY saleprice, saledate
HAVING COUNT(id) = 1
```

ALIASES
* _alias_: shorthand for identifier
* need n aliases if using same table more than once 📙 Beaulieu 5.92
* `AS` not necessary but advisable 📙 Beaulieu [51] used about half the time [57] https://www.sqlstyle.guide/#aliasing-or-correlations
```sql
select first_name || ' ' || last_name as full_name  -- column alias
    from people as p  -- table alias
    order by full_name  -- can be used in other commands

-- result set labelling
select count(addr) as "listings", max(price) as "high", min(price) as "low" from house
```

ZA
* syntax: select (attrs) from (tables) where (records) 📙 Molinaro 1.1
* _compound query_: combines multiple `SELECT` 📙 Beaulieu [105]
* _scalar query_: query that returns single cell https://stackoverflow.com/a/20425116
* TOP: LIMIT for MySQL https://github.com/enochtangg/quick-SQL-cheatsheet#1-finding-data-queries 📙 Evans 13
* _ordinal notation_: refer to columns in select as ordinals https://stackoverflow.com/q/2253040
```sql
-- DESC: must be final clause
-- ASC: default, which is why you never see it 📙 Beaulieu [63]
select "First Name", count(*) from executions group by "First Name" order by count(*) desc

-- concatenate https://pgexercises.com/questions/joins/threejoin.html
SELECT concat(mem.fname, ' ', mem.lname) as member  -- Postgres
SELECT mem.fname || ' ' || mem.lname as member  -- other dbms

-- case statements https://pgexercises.com/questions/basic/classify.html https://pgexercises.com/questions/joins/threejoin2.html
SELECT NAME,
	CASE
        WHEN (monthlymaintenance > 100)
        THEN 'expensive'
        ELSE 'cheap'
        END
    AS cost
FROM cd.facilities;  
```

# 🟨️ ZA

DESIGN 🗄️ `eng.md` dataframe
* boring and durable https://josephg.com/blog/databases-have-failed-the-web
* outdated and awkward https://news.ycombinator.com/item?id=33034351 https://news.ycombinator.com/item?id=39539252 https://news.ycombinator.com/item?id=41347188
> The relational data model enables those things. None of them require the language to be SQL...LINQ, spark, flink, kafka streams, pandas, dataframes are all widely used examples of an expression-based language-embedded approach to relational queries. https://www.scattered-thoughts.net/writing/against-sql
> SQL is the most popular to communicate with databases but isn't always the easiest to write. I've been writing SQL statements since the 1990s and even in 2024, I can find myself needing to refer to documentation and spending 30 minutes or more getting more complex statements to run as I wish. https://tech.marksblogg.com/heavyiq-faa-ai-llm-gpu-database.html
* ISO, ANSI standard 📙 Beaulieu [86-87]
* SQL92 📙 Beaulieu [91]
* SQL2023 http://peter.eisentraut.org/blog/2023/04/04/sql-2023-is-finished-here-is-whats-new

SEMANTICS
* _object_: anything e.g. table, user, trigger https://docs.oracle.com/cd/B19306_01/server.102/b14200/sql_elements007.htm https://github.com/jOOQ/sakila/blob/ee1a637656aec2d82183ab451c56a3845315e761/mysql-sakila-db/mysql-sakila-drop-objects.sql ownership model https://www.red-gate.com/simple-talk/uncategorized/postgresql-basics-object-ownership-and-default-privileges/
* _collation_: order in which char in character set are sorted 📙 Beaulieu [77]
* _enumeration attack_: https://sqlfordevs.com/uuid-prevent-enumeration-attack
* _fuzzy matching_: merging n datasets that don't have a common UUID e.g. merging contacts based on name https://pbpython.com/record-linking.html
* _deterministic matching_: https://github.com/zinggAI/zingg
* _virtual column_: https://news.ycombinator.com/item?id=31396578

STYLE 📜 https://www.sqlstyle.guide/
* ✅ constraints next to the attr they constrain https://www.sqlstyle.guide/#layout-and-order
> this seems to violate parsing rules for SQLite 🗄 `golf`
* ✅ suffixes https://www.sqlstyle.guide/#uniform-suffixes
* ✅ uppercase keywords https://www.sqlstyle.guide/#reserved-words
* indentation along root keywords (select, from, where) https://www.sqlstyle.guide/#indentation https://www.sqlstyle.guide/#spaces
* white space / tabs not significant
* ✅ ubiquitous language ❌ but no Hungarian notation https://news.ycombinator.com/item?id=24403236 
* ✅ starts w/ char, use underscores where you'd use a space in natural language https://www.sqlstyle.guide/#naming-conventions
* ❌ _Hungarian notation_: type in signature https://www.sqlstyle.guide/#tables https://news.ycombinator.com/item?id=24403236
* ❌ through table as concatentation of its constituents https://www.sqlstyle.guide/#tables
* ❌ `id` as PK https://www.sqlstyle.guide/#columns https://github.com/jOOQ/jOOQ/tree/master/jOOQ-examples/Sakila
* ✅ singular for attr https://www.sqlstyle.guide/#columns

DCL
* _get current user_: `select current_user;` or `select user();`
* _create user_: `CREATE USER alice WITH PASSWORD '1234';` `CREATE USER '<name>'@'localhost';
* scope reads to currrent user https://news.ycombinator.com/item?id=23308945
* give user perms to db
```sql
GRANT ALL PRIVILEGES ON <dbName>.* to '<userName>'@'localhost' WITH GRANT OPTION; 
FLUSH PRIVILEGES;
```
* test user privileges
```sql
mysql -u user_name
USE db_name;
CREATE TABLE test_table (c CHAR(20));
INSERT INTO test_table(name, age) values('zach', 31);
SELECT * FROM test_table;
DROP TABLE test_table;
```

## commands

SEMANTICS 🗄 `language.md` semantics
* _command_: keyword + identifier
* _keyword_: part of SQL lang spec; not case sensitive
* _identifier_: value (cell, attribute); case-sensitive
* quotes: single for value, double for attr https://stackoverflow.com/q/1992314
```sql
SELECT "from" FROM foo WHERE something = 'val';
```
* _query_: `SELECT` command 📙 Karwin [6]
* _statement_: non-`SELECT` commands 📙 Karwin [6]

TYPES
* _DCL_: control; user perms https://stackoverflow.com/a/44898661
* _DDL_: definition; table structure and inter-table relationships https://stackoverflow.com/a/2578207
* _DML_: manipulation; CRUD

KEYWORDS https://www.postgresql.org/docs/8.1/sql-keywords-appendix.html https://www.sqlstyle.guide/#reserved-keyword-reference
* _reserved_: word that cannot use as identifier e.g. `create`
* _non-reserved_: word that you can use as identifier but should use backtickets for e.g. `assertion`, `name`
* _keyword_: reserved + non-reserved; case-insensitive
> As a general rule, if you get spurious parser errors for commands that contain any of the listed key words as an identifier you should try to quote the identifier to see if the problem goes away. - https://www.postgresql.org/docs/8.1/static/sql-keywords-appendix.html

## pedagogy

* tldr: better at SQL if data 1) local 2) interesting
* small databases https://news.ycombinator.com/item?id=34558054
* example databases: Spanish, Sakila https://github.com/jOOQ/sakila/blob/main/sqlite-sakila-db/sqlite-sakila-schema.sql 📙 Beaulieau [41]

CONNECT TO ACTUAL SERVER
* https://data.stackexchange.com/help
* https://sqlpd.com/
* https://news.ycombinator.com/item?id=30631477

PLAYGROUNDS
* PG exercises https://github.com/zachvalenta/pg-exercises
* https://jvns.ca/blog/2023/04/17/a-list-of-programming-playgrounds/

BAKED DATA
* Datasette https://csvbase.com/ fetching https://github.com/fatiando/pooch
* SQL.js https://selectstarsql.com/frontmatter.html#technicals https://github.com/sql-js/sql.js https://github.com/NUKnightLab/sql-mysteries
* https://news.ycombinator.com/item?id=34558054 https://news.ycombinator.com/item?id=34630153
* https://sqlbolt.com/
* https://dataschool.com/learn-sql/basic-practice/
* https://sql-playground.wizardzines.com/

GET DATA
* general https://github.com/awesomedata/awesome-public-datasets https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks https://corgis-edu.github.io/corgis/csv/ https://www.data-is-plural.com/archive/ https://redis.com/blog/datasets-for-test-databases/
* JSON https://github.com/jdorfman/awesome-json-datasets
* csv https://github.com/secretGeek/awesomecsv#data
* 📍 more in 🗄 `ml.md`? put these there? Paul Swanson videos?
> put in ML
* PG Exercises https://pgexercises.com/gettingstarted.html https://github.com/AlisdairO/pgexercises/issues/28
* executions https://selectstarsql.com/frontmatter.html#dataset
* housing https://www.zillow.com/research/data/
* music https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks
* shootings https://catalog.data.gov/dataset/nypd-shooting-incident-data-historic
* verbos https://github.com/ghidinelli/fred-jehle-spanish-verbs
* HN https://github.com/dogsheep/hacker-news-to-sqlite https://news.ycombinator.com/submitted?id=luu
* movies https://simonwillison.net/2019/Feb/25/sqlite-utils/ https://github.com/jdorfman/awesome-json-datasets
* music https://corgis-edu.github.io/corgis/csv/music/ 

## SQLAlchemy

📜 https://docs.sqlalchemy.org/en/20/
🗄 `django.md` db

* https://aosabook.org/en/v2/sqlalchemy.html
* overly complex https://news.ycombinator.com/item?id=34541452
* people hate the docs https://news.ycombinator.com/item?id=34540251 https://news.ycombinator.com/item?id=34542075 https://news.ycombinator.com/item?id=34578772 https://news.ycombinator.com/item?id=34540960
* migrations: Alembic https://news.ycombinator.com/item?id=34549578

ORMS
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

QUERY BUILDERS
* reverse query builder https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202203030 https://github.com/kyleconroy/sqlc https://preslav.me/2023/03/07/reasons-against-sqlc/
* _query builder_: what it sounds like i.e. cares about physical tables, doesn't care about objects i.e. not an ORM https://github.com/stephenafamo/bob
* BYO https://death.andgravity.com/query-builder-how
* _aiosql_: https://github.com/nackjicholson/aiosql load sql file into Python and run queries as methods https://github.com/nackjicholson/aiosql
* _csql_: https://news.ycombinator.com/item?id=24866377
* _hashquery_: https://news.ycombinator.com/item?id=40132424 https://hashquery.dev/ https://github.com/hashboard-hq/hashquery
* _pypika_ https://github.com/kayak/pypika https://github.com/zachvalenta/query-sandbox/blob/main/queries.py
* _records_: just write SQL https://github.com/kennethreitz/records
* _spyql_: https://github.com/dcmoura/spyql https://news.ycombinator.com/item?id=30074787

ALTERNATIVES
* _dataset_: lightweight https://dataset.readthedocs.io/en/latest/index.html 
* _orator_: from the guy who did Poetry https://github.com/sdispater/orator
* _Peewee_: https://github.com/coleifer/peewee not for async https://fastapi.tiangolo.com/advanced/sql-databases-peewee/
* _SQLmodel_: SQLAlchemy wrapper https://github.com/tiangolo/sqlmodel
* _Tortoise_: async https://github.com/tortoise/tortoise-orm

----

* https://lucumr.pocoo.org/2011/7/19/sqlachemy-and-you/
* https://talkpython.fm/episodes/show/344/sqlalchemy-2.0

SQLALCHEMY http://aosabook.org/en/sqlalchemy.html https://docs.sqlalchemy.org/en/13/ https://www.sqlalchemy.org/library.html#tutorials
* https://blog.miguelgrinberg.com/post/what-s-new-in-sqlalchemy-2-0
* https://talkpython.fm/episodes/show/344/sqlalchemy-2.0
* https://realpython.com/python-sqlite-sqlalchemy/
* tutorial https://www.youtube.com/watch?v=5SSC6nU314c
* create table `create_all` https://docs.sqlalchemy.org/en/14/core/metadata.html#creating-and-dropping-database-tables
* _core_: manages connection pool and dialects (diff dbms); fine to just use core https://news.ycombinator.com/item?id=10270605
* _JSONField_: https://amercader.net/blog/beware-of-json-fields-in-sqlalchemy/
* _core - components_: engine, connection, session https://stackoverflow.com/a/42772654/6813490 event system https://www.sqlalchemy.org/features.html
* _ORM_: niceties on top of core https://www.sqlalchemy.org/features.html
* _row object_: record https://stackoverflow.com/q/1958219
* _unit of work_: writes changes all at once, similar to how Hibernate does it https://www.sqlalchemy.org/features.html
* build queries from functions https://www.sqlalchemy.org/features.html
* built on PEP249 (DBAPI) https://www.python.org/dev/peps/pep-0249/
* _not async_: even if your app framework if
* `bulk_save_objects` doesn't seem to work when it comes to backrefs https://github.com/zachvalenta/flask-skeleton/commit/548c36088dfe595fccabeb67fa11c7254e847948#diff-c61c1bc5b0486cc6e721bee29c28fe33R17
* search expressions w/ engine https://stackoverflow.com/questions/3325467/sqlalchemy-equivalent-to-sql-like-statement
* _parameterized query_: `select foo from bar where baz = :bazid` https://docs.sqlalchemy.org/en/13/core/tutorial.html#using-textual-sql https://stackoverflow.com/a/18808942/6813490 apparently should use a session https://stackoverflow.com/a/22084672/6813490
* compared to Django https://apirobot.me/posts/introduction-to-sqlalchemy-orm-for-django-developers
* sessions
> This is not at all how SQLAlchemy's ORM component works. In SQLAlchemy you have an object called the “session”. It basically encapsulates a transaction. However it does more. Each object is tracked by primary key in this session. As such each object only exists once by primary key. As such you can safely make a lot of queries and you never have things out of sync. When you commit the session it will send all changes at once to the database in correct order, if you rollback the session nothing happens instead. - http://lucumr.pocoo.org/2011/7/19/sqlachemy-and-you/

BACKREF
* used for 1-M
* adds virtual column to obj from parent table that enforces constraint on child table itself https://flask-sqlalchemy.palletsprojects.com/en/2.x/models/?highlight=backref https://docs.sqlalchemy.org/en/13/orm/backref.html#linking-relationships-with-backref
```python
# PARENT
class Concert(db.Model):
    concert_id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.Text)
    performances = db.relationship("Performance", backref="concert")

# backref = no change to underlying table
+-----+------------+---------+---------+------------+----+
| cid | name       | type    | notnull | dflt_value | pk |
+-----+------------+---------+---------+------------+----+
| 0   | concert_id | INTEGER | 1       | <null>     | 1  |
| 1   | name       | TEXT    | 0       | <null>     | 0  |
+-----+------------+---------+---------+------------+----+

# rather, gets virtual column i.e. query run on obj creation to fetch all child obj that reference parent https://www.youtube.com/watch?v=cYWiDiIUxQc 15:20
Concert.query.get(1).performances

# CHILD
class Performance(db.Model):
    perf_id = db.Column(db.Integer, primary_key=True)
    concert_id = db.Column(db.Integer, db.ForeignKey("concert.concert_id"))

# FK = adds constraint via column on underlying table
+-----+------------+---------+---------+------------+----+
| cid | name       | type    | notnull | dflt_value | pk |
+-----+------------+---------+---------+------------+----+
| 0   | perf_id    | INTEGER | 1       | <null>     | 1  |
| 1   | concert_id | INTEGER | 0       | <null>     | 0  |
+-----+------------+---------+---------+------------+----+
# physical column reflected in ORM obj
Performance.query.get(1).concert_id  # 1
# but also gets virtual column as well
Performance.query.get(1).concert  # id 1 name Glastonbury
```

* snippets
```python
###
# JOINS https://stackoverflow.com/q/19841877/6813490 https://stackoverflow.com/q/6044309/6813490
###

outer = (
    db.session.query(Artist, Song)
    .outerjoin(Song, Artist.artist_id == Song.artist_id)
    .all()
)
outer_pages = (
    db.session.query(Artist, Song)
    .outerjoin(Song, Artist.artist_id == Song.artist_id)
    .paginate()
)

inner = (
    db.session.query(Artist, Song).join(Song, Artist.artist_id == Song.artist_id).all()
)

# pull values out of result set obj https://stackoverflow.com/a/42093713/6813490
# irl you'd want to use Marshmallow for this
class Artist(db.Model):
    artist_id = db.Column(db.Integer, primary_key=True)

class Song(db.Model):
    song_id = db.Column(db.Integer, primary_key=True)
    artist_id = db.Column(db.Integer, db.ForeignKey('artist.artist_id'), nullable=False)

artists = [Artist(artist_name='Massive Attack'), Artist(artist_name='Nas')]
songs = [Song(song_name='One Love', artist_id=2), Song(song_name='One Love', artist_id=1)]

query = "select artist_name, song_name from song s inner join artist a on s.artist_id = a.artist_id where artist_name='Massive Attack'"
for x in db.engine.execute(query):
    print(x)  # ('Massive Attack', 'One Love')

@app.route("api")
def get_foo():
    query = "select col1, col2 from foo"
    rs = db.engine.execute(query).fetchall()
    marshalled_rs = [x[0, 1] for x in rs]
    return jsonify({"results": marshalled_rs})

# saving from repl https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database 'shell'
# unable to persist a record using Flask-SQLAlchemy from the Python REPL, but the same code works fine when run as a script.

# APP.PY

import os
from dotenv import find_dotenv, load_dotenv
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

load_dotenv(find_dotenv())
basedir = os.path.abspath(os.path.dirname(__file__))
db_path = os.path.join(basedir, os.getenv("DATABASE"))
db_uri = "sqlite:///" + db_path

app = Flask(__name__)
app.config["SQLALCHEMY_TRACK_MODIFICATIONS"] = False
app.config["SQLALCHEMY_DATABASE_URI"] = db_uri
db = SQLAlchemy(app)

class Thing(db.Model):
    thing_id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(30))
    description = db.Column(db.Text)

    def __repr__(self):
        return f"id {self.thing_id} name {self.name} desc {self.description}"
    
# DB_SEED.PY

#!/usr/bin/env python
from app import db, Thing

db.drop_all()
db.create_all()
thing = Thing(name="thing1", description="thing-1-desc")
db.session.add(thing)
db.session.commit()
print(f"new thing {Thing.query.all()} \n")
```
```sh
# Running the script persists a record
$ poetry run python db_seed.py
new thing [id 1 name thing1 desc thing-1-desc]
# When I try to do the same thing from inside the Python REPL, however, the record isn't created
>>> from app import db, Thing
>>> db.drop_all()
>>> db.create_all()
>>> thing = Thing(name="thing1", description="thing-1-desc")
>>> db.session.add(thing)
>>> db.session.commit()
>>> Thing.query.all()
[]
```

## tables

TYPES
* _table_: set of related rows
* _permanent_: table in storage 📙 Beaulieu [53]
* impl as heap or b-tree https://calpaterson.com/activerecord.html
* _derived_: return from subquery and held in memory 📙 Beaulieu [53]
* _temporary_: table in mem 📙 Beaulieu [53] aka non-persistent 📙 Beaulieu [8]
* _result set (rs)_: temp table returned from query 📙 Beaulieu [8] Evans [4]
* intermediate rs created at each stage in join 📙 Beaulieu [90-digital-copy]
* _virtual_: created using `create view` cmd 📙 Beaulieu [53]
* _intemediate_: table instaniated for a job and then deleted https://hakibenita.com/sql-tricks-application-dba#implement-complete-processes-using-with-and-returning
* _scalar table_: table w/ single column and single row https://pgexercises.com/questions/basic/agg2.html
* _temporal_: https://news.ycombinator.com/item?id=29733854 https://news.ycombinator.com/item?id=29735695 https://stackoverflow.com/questions/50199752/comparing-csv-entries-against-entries-in-postgresql-table-using-python 

COMPONENTS 📙 Beaulieu [1.6]
* _entity_: thing you're trying to describe e.g. customer, order, et al. 📙 Beaulieu [8]
* _column_: aka attribute
* _row_: aka record
* _value_: aka cell, field

VIEWS 📙 Beaulieu chapter 14
* _view_: pre-computed partial query (e.g. `where is_active = 0`) recomputed as more full query w/ additional user filtering 📙 Kleppmann [101]
* doesn't hold any data itself 📙 Beaulieu [55]
* restrict users to subset of data https://stackoverflow.com/a/4378291/6813490
* simplifies queries for users but lose info about relationships 📙 Beaulieu [56] https://dataschool.com/sql-optimization/views/
* for some dbms (SQLite) you can't write using views https://sqlite.org/omitted.html
* _materialized view_: actual data i.e. cached version of the table https://news.ycombinator.com/item?id=34186098
* faster queries but needs to be manually maintained so not typically used in OLTP 📙 Kleppmann [102]
* _data cube_: type of materialized view used in OLAP, precomputed for speed results 📙 Kleppmann [102] https://hakibenita.com/sql-for-data-analysis#cube
* not often used limited query flexiblity 📙 Kleppmann [103]

CTE
* _CTE (common table expression)_: one-off view
```sql
with  -- https://github.com/enochtangg/quick-SQL-cheatsheet#find https://hakibenita.com/sql-tricks-application-dba#implement-complete-processes-using-with-and-returning
```
* recursion http://www.jeffwidman.com/blog/ https://dba.stackexchange.com/q/14490 https://medium.com/swlh/recursion-in-sql-explained-graphically-679f6a0f143b https://aiven.io/blog/solving-the-knapsack-problem-in-postgresql https://pgexercises.com/questions/recursive/ https://bofh.org.uk/2019/02/25/baking-with-emacs/
* https://github.com/enochtangg/quick-SQL-cheatsheet#find
* https://hakibenita.com/sql-for-data-analysis#common-table-expressions https://hakibenita.com/sql-for-data-analysis#sql-vs-pandas-performance 
* https://news.ycombinator.com/item?id=34603691
