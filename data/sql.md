# ⛩️

## 参考

🔍 https://dba.stackexchange.com
📚
> https://sql.programmable.net/dashboard
* Beaulieu learning sql
* Conery curious moon
* Evans star https://sql-playground.wizardzines.com/
* Faroult art of sql
* Karwin sql antipatterns https://pragprog.com/cms/errata/bksqla-errata/
* Molinaro sql cookbook

## 进步

REWRITE SJK FOR BOTH MODELING AND USING SQL
* canonical datasets for OLTP https://news.ycombinator.com/item?id=42231325 Sakila https://sq.io/docs/tutorial
* * NYC taxi dataset https://mattpo.pe/posts/sql-llvm/

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
* _21_: semantics (migrations, tables), `query-sandbox`
* _20_: start `sjk`, Flask-SQLAlchemy (pagination, 1-m w/ backrefs, Marshmallow for nested serializers)
* _19_: 📙 Beaulieu chapters 1-5 and 10; Flask-SQLAlchemy (FK, through table, raw SQL) SQLite (FK support) SQLAlchemy (core, parameterized queries)
* _18_: Flyway for Dark Canary, modeling course
* _17_: subqueries for Case

# 🚧 DDL

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

### schema awareness

💡 core insight: let the data tell you what it is, rather than forcing it into predetermined boxes
🗄️
* `modeling.md`
* `OLAP.md` pipelines
* `stat.md` outlier detection

* _schema on-read_: enforce contraints on write
* _schema on-write_: don't enforce contraints on write i.e. cobble things together on read
```python
class Catalog:
    """
    >>> cat = Catalog()
    >>> cat.add_product({'sku': 1234, 'name': 'foo'})
    >>> cat.add_product({'sku': 5678, 'name': 'bar'}, mode='strict')
    >>> cat.get_product(sku=1234)
    """
    def __init__(self):
        self.products = []

    def __repr__(self):
        return f'{self.products}'

    def _validate_product(self, product, mode):
        required = {'sku', 'name'}
        if mode == 'strict':
            required |= {'price'}
        missing = required - set(product)
        if missing:
            raise ValueError(f"missing required fields: {' '.join(missing)}")

    def add_product(self, product, mode='flex'):
        self._validate_product(product, mode)
        self.products.append(product)

    def get_product(self, sku):
        defaults = {'price': None}
        for product in self.products:
            if product['sku'] == sku:
                return {**defaults, **product}
        return None
```
* _schema-first_: define upfront
* _schema-aware_: learns schema
```sh
# infers: book title (text), author name (text), year (integer)
add-book "Snow Crash" "Neal Stephenson" 1992

# "there's a publisher field now. Should I update the schema? Y/N"
# On Y: Adds publisher column, leaves it NULL for previous entries
add-book "Neuromancer" "William Gibson" 1984 "Ace Books"

# "I notice you're adding categories. Should these be: single text field with comma-separated values | separate table with a many-to-many relationship?"
add-book "Dune" "Frank Herbert" 1965 "Chilton Books" "sci-fi, politics"
```
* _constraint inference_: pattern detection
* start permissive, get strict only when patterns emerge i.e. opposite of traditional db design where you define everything upfront
```sh
# distribution: if every book year is between 1900-2024
system: "should i enforce year >= 1900?"

# normalization: if you enter "ace books" multiple times
System: "I notice 'Ace Books' appears often. Make it a foreign key?"

# typing: if ISBN field always matches \d{13}|\d{10}
System: "This looks like an ISBN. Add format validation?"
```

### primary key (PK)

🗄 indexing `connolly.pdf`

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
-- TODO
```
* _natural key_: attr that goes together with other attr in table (vs. surrogate key) https://news.ycombinator.com/item?id=40580549
* _surrogate key_: unrelated to table attr https://stackoverflow.com/a/36773462
* typically auto-incremented but doesn't necessarily have to be 📙 Beaulieu [34]
```sql
-- TODO
```
* _sequence_: https://stackoverflow.com/a/1649128 📙 Beaulieu [34] Karwin ch. 4
* don't expose via API, use uuid https://0of1.com/blog/posts/django-staples/
* auto-increment https://retool.com/blog/how-to-work-with-auto-increment-in-sql-query/ aka identity column https://www.sqltutorial.org/sql-identity/
```sql
-- TODO
```

### foreign key (FK)

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

💻 `lang/python/django/migrations-sandbox`
🗄
*️ `api.md` schema
* `architecture.md` factors > compatibility
* `infra.md` deployment
* `task-mgmt.md` Task Warrior > database https://github.com/zachvalenta/dotfiles-mini23/blob/main/cli/taskwarrior.sql
* `data/eng.md` pipelines
* `django.md` migrations

TOOLS
* pgroll, squitch https://news.ycombinator.com/item?id=42388973

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

https://news.ycombinator.com/item?id=41935730
https://github.com/xataio/pgroll
https://xata.io/blog/migrations-and-exclusive-locks
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

## typing

📜 https://www.postgresql.org/docs/current/datatype.html
🗄 `db.md` SQLite/design
📙 Beaulieu chapter 7

storing PDFs https://news.ycombinator.com/item?id=42059639
> able to store Markdown?

TYPES
* money https://www.youtube.com/watch?v=lxVzLAHnPOE https://news.ycombinator.com/item?id=41776878
* _char_: fixed e.g. state abbreviations 📙 Beaulieu [20]
* _varchar_: variable 📙 Beaulieu [21]
* _blob_: `text` in Postgres, `longtext` in MySQL https://news.ycombinator.com/item?id=40317485
* _datetime_: https://stackoverflow.com/q/1933720 as integer https://stackoverflow.com/a/17227196 🗄 `sjk/golf` https://news.ycombinator.com/item?id=42364372
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
-- timestamp https://pgexercises.com/questions/basic/date.html non-overlapping times https://sqlfordevs.com/non-overlapping-time-ranges more on times https://simonwillison.net/2024/Nov/27/storing-times-for-human-events
YYYY-MM-DD HH:MM:SS  -- fmt
where foo_date > '1962-07-03' -- compare
-- user names
family_name, other_given_names  -- https://www.youtube.com/watch?v=458KmAKq0bQ 7:30 https://www.w3.org/International/questions/qa-personal-names
```

NULL 📙 Beaulieu [32,82]
* https://jirevwe.github.io/sql-nulls-are-weird.html
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
DELETE FROM <tab> WHERE id=3;  -- https://notso.boringsql.com/posts/deletes-are-difficult/
```

## execution order

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

## functions

💡 better to have this in application code https://www.youtube.com/watch?v=atwwf0qWpYg [20:30]

FUNCTION
* _function_: built-in function provided by dbms
* has return value https://stackoverflow.com/a/771959
* e.g. SQLite `substr()`

### proc

* _procedure_: user-defined function
* no return value https://stackoverflow.com/a/771959
* aka stored procedure
* impl via procedural language availble in dbms
* too many and you've got business logic split btw application and db https://news.ycombinator.com/item?id=24845300

### trigger

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

### aggregate

📙 Beaulieu ch. 8

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
* _group by_: rs w/ 1 record for each group 📙 Evans [8] https://labs.quansight.org/blog/dataframe-group-by
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

🗄
* `language.md` semantics
* `math.md` set theory > operations

RELATIONAL 📙 Takahashi [43]
* _projection_: filter on attr i.e. `SELECT` https://stackoverflow.com/a/1031101 📙 Takahashi [43] Beaulieu [44-5]
* _selection_: filter on value i.e. `WHERE` 📙 Beaulieu [52-54]
* _division_: extract records that exist in both numerator/denomenator table but only the columns that exist only in numerator 📙 Takahashi [45]
* + join

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

## subqueries

📙 Beaulieu ch. 9

* _subquery_: query contained within another query 📙 Beaulieu [53]
* _containing query_: query that wraps subquery 📙 Beaulieu [54]
* _scalar subquery_: return single val from subquery https://learnsql.com/blog/subquery-vs-join/
* more readable but generally slower than joins https://stackoverflow.com/a/2577224
* more thinkable than joins https://stackoverflow.com/a/2577188
```sql
containing_query = (subquery)  -- 1 (scalar)
containing_query in (subquery)  -- n
```

# 🟨️ ZA

SEMANTICS
* _object_: anything e.g. table, user, trigger https://docs.oracle.com/cd/B19306_01/server.102/b14200/sql_elements007.htm https://github.com/jOOQ/sakila/blob/ee1a637656aec2d82183ab451c56a3845315e761/mysql-sakila-db/mysql-sakila-drop-objects.sql ownership model https://www.red-gate.com/simple-talk/uncategorized/postgresql-basics-object-ownership-and-default-privileges/
* _collation_: order in which char in character set are sorted 📙 Beaulieu [77]
* _enumeration attack_: https://sqlfordevs.com/uuid-prevent-enumeration-attack
* _fuzzy matching_: merging n datasets that don't have a common UUID e.g. merging contacts based on name https://pbpython.com/record-linking.html
* _deterministic matching_: https://github.com/zinggAI/zingg
* _generated column_: col whose value generated based on other columns https://chatgpt.com/c/6734cd95-6754-8004-b89c-8d25d8da8048 https://news.ycombinator.com/item?id=31396578
* virtual = doesn't store computed value, stored = does store computed value
> same as a virtual table https://llm.datasette.io/en/stable/logging.html
* in Django https://realpython.com/podcasts/rpp/227/ https://www.paulox.net/2023/11/07/database-generated-columns-part-1-django-and-sqlite/#tldr
* _enrichment_: https://simonwillison.net/2024/Dec/5/datasette-enrichments-llm/

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
```sql
-- SQLite and SQL Server use brackets instead of quotes/backticks for this https://llm.datasette.io/en/stable/logging.html
CREATE TABLE [conversations] (
  [id] TEXT PRIMARY KEY,
  [name] TEXT,
  [model] TEXT
);
```
* _keyword_: reserved + non-reserved; case-insensitive
> As a general rule, if you get spurious parser errors for commands that contain any of the listed key words as an identifier you should try to quote the identifier to see if the problem goes away. - https://www.postgresql.org/docs/8.1/static/sql-keywords-appendix.html

## replacement

🗄️ `eng.md` dataframes
> SQL was here before you were born and will be here when you die https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html

---

CMU
* https://news.ycombinator.com/item?id=35599118
* Stonebraker https://dsf.berkeley.edu/papers/ERL-M85-95.pdf https://drewdevault.com/2021/08/05/In-praise-of-Postgres.html
* Pavlo https://db.cs.cmu.edu/papers/2024/whatgoesaround-sigmodrec2024.pdf

> the creation of SQL at IBM Research by Don Chamberlain and Ray Boyce (RIP). Originally known as SEQUEL (Structured English QUEry Language) https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
> Don Chamberlin details his early work with Ray Boyce designing the relational language SQL. After meeting E.F. (Ted) Codd at a symposium at the IBM T.J. Watson Research Center in Yorktown Heights, New York, in 1972, Boyce and Chamberlin believed that it should be possible to design a relational language that would be accessible to users without formal training in mathematics or computer programming. https://ieeexplore.ieee.org/document/6359709

> This past year saw the latest incarnation of the ISO/IEC 9075 specification, better known as SQL:2023. The update includes many "nice to haves" that deal with frustrations and inconsistencies in various SQL dialects (e.g., ANY_VALUE). Two enhancements to SQL that further erode the need for alternative data models and query languages are worth mentioning here. Remember that just because the SQL specification includes something does not mean that your favorite relational DBMS will immediately support these new features. https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
> SQL is not perfect, of course, and it is not truly portable since every DBMS has its quirks, proprietary features, and non-standard extensions. https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html

REPLACEMENTS
* Ibis
* https://medium.com/schkn/sql-is-dead-hail-to-flux-8e8498756049
* _PRQL_: pipelined SQL alternative, all new syntax https://news.ycombinator.com/item?id=36866861 https://news.ycombinator.com/item?id=42231325
* _Malloy_: all new syntax, semantic focus https://news.ycombinator.com/item?id=30053860 https://news.ycombinator.com/item?id=42231325
* _preql_: much more ambitious, all new syntax https://news.ycombinator.com/item?id=26447070 https://news.ycombinator.com/item?id=42231325
* _Trilogy_: dimension tables, canonical dataset for OLTP https://news.ycombinator.com/item?id=42231325

* boring and durable https://josephg.com/blog/databases-have-failed-the-web
* outdated and awkward https://news.ycombinator.com/item?id=33034351 https://news.ycombinator.com/item?id=39539252 https://news.ycombinator.com/item?id=41347188 https://buttondown.com/hillelwayne/archive/queryability-and-the-sublime-mediocrity-of-sql/
> The relational data model enables those things. None of them require the language to be SQL...LINQ, spark, flink, kafka streams, pandas, dataframes are all widely used examples of an expression-based language-embedded approach to relational queries. https://www.scattered-thoughts.net/writing/against-sql
> SQL is the most popular to communicate with databases but isn't always the easiest to write. I've been writing SQL statements since the 1990s and even in 2024, I can find myself needing to refer to documentation and spending 30 minutes or more getting more complex statements to run as I wish. https://tech.marksblogg.com/heavyiq-faa-ai-llm-gpu-database.html
* attempts at rewrite https://news.ycombinator.com/item?id=42231325 https://github.com/totalhack/zillion
* ISO, ANSI standard 📙 Beaulieu [86-87]
* SQL92 📙 Beaulieu [91]
* SQL2023 http://peter.eisentraut.org/blog/2023/04/04/sql-2023-is-finished-here-is-whats-new
* testing and business logic https://news.ycombinator.com/item?id=42828883

## style

TABLES
* case: lower + snake
* avoid reserved words

---

📜 https://www.sqlstyle.guide/
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

LINTING
* https://github.com/alanmcruickshank/sqlfluff https://www.thoughtworks.com/radar/tools?blipid=202203065
* https://www.eversql.com/sql-syntax-check-validator/
* https://github.com/purcell/sqlint
* https://github.com/darold/pgFormatter
* https://sqlfum.pt/

## tables

YPES
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

### CTE

* _CTE (common table expression)_: one-off view
```sql
with  -- https://github.com/enochtangg/quick-SQL-cheatsheet#find https://hakibenita.com/sql-tricks-application-dba#implement-complete-processes-using-with-and-returning
```
* recursion http://www.jeffwidman.com/blog/ https://dba.stackexchange.com/q/14490 https://medium.com/swlh/recursion-in-sql-explained-graphically-679f6a0f143b https://aiven.io/blog/solving-the-knapsack-problem-in-postgresql https://pgexercises.com/questions/recursive/ https://bofh.org.uk/2019/02/25/baking-with-emacs/
* https://news.ycombinator.com/item?id=42230384
* https://github.com/enochtangg/quick-SQL-cheatsheet#find
* https://hakibenita.com/sql-for-data-analysis#common-table-expressions https://hakibenita.com/sql-for-data-analysis#sql-vs-pandas-performance 
* https://news.ycombinator.com/item?id=34603691

### views

📙 Beaulieu chapter 14

* late-binding https://eradman.com/posts/late-binding-views.html
* _view_: pre-computed partial query (e.g. `where is_active = 0`) recomputed as more full query w/ additional user filtering 📙 Kleppmann [101]
* doesn't hold any data itself 📙 Beaulieu [55]
* restrict users to subset of data https://stackoverflow.com/a/4378291/6813490
* simplifies queries for users but lose info about relationships 📙 Beaulieu [56] https://dataschool.com/sql-optimization/views/
* for some dbms (SQLite) you can't write using views https://sqlite.org/omitted.html
* _materialized view_: actual data i.e. cached version of the table https://news.ycombinator.com/item?id=34186098
* faster queries but needs to be manually maintained so not typically used in OLTP 📙 Kleppmann [102]
* _data cube_: type of materialized view used in OLAP, precomputed for speed results 📙 Kleppmann [102] https://hakibenita.com/sql-for-data-analysis#cube
* not often used limited query flexiblity 📙 Kleppmann [103]
