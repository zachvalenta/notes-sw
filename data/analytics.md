# ⛩️

## 参考

🛣️ https://roadmap.sh/data-analyst
> A number of companies (large crossover funds, startups, etc.) in The Diff network are looking for data scientists that love wrangling and analyzing alt. data to help inform investment decisions. (Remote) https://www.thediff.co/archive/longreads-open-thread-96/
🗄
* `protocols.md` file fmt
* `telemetry.md` analytics
📚
* Asboth grounded analyst https://www.manning.com/books/the-well-grounded-data-analyst
* Khalil https://www.manning.com/books/effective-data-analysis
* Massaron https://www.manning.com/books/advanced-analytics-for-business https://www.youtube.com/watch?v=scY7PTxNSr4
* ⭐️ Tuckfield https://nostarch.com/dive-data-science
* Wickham https://r4ds.hadley.nz/

## 进步

CAPP
- [x] ✅ Datasette
> add AI
- [x] ❌ Preset: CSV upload goofiness, ok to connect Steersman read-replica?
- [x] ❌ Hex: powerful but too much for business users
- [ ] Metabase: work through free trial

* canonical datasets
* where to store your data (email? google drive? repo/csvbase? ⭐️ hugging face? metadata mgmt?)

* _21_: litecli config
* _20_: start with visidata

# 📊 BI

🗄
* `architecture.md` no code, baked data
* `doc.md` viz > chart
* `math.md` stat / distributions
* `python/feedback.md` notebooks

INTERESTING
* _Briefer_: https://github.com/briefercloud/briefer
* pricing: free self-host | $130/month https://docs.briefer.cloud/deployment/vm
* great docs, SQL/notebook centric
* design https://pythonbytes.fm/episodes/show/405/oh-really
* smart team, SQL-by-mouse https://briefer.cloud/blog/posts/self-serve-bi-myth/
* _dash_: build charts for sites https://www.youtube.com/watch?v=GW95sNvygDE 📜 https://dash.plotly.com/ 💻 https://github.com/zachvalenta/capp-dasher
* tables https://genderpaygap.pythonanywhere.com/ https://dash-example-index.herokuapp.com/grid https://dash.plotly.com/datatable https://chatgpt.com/c/6749d1ba-9d0c-8004-a11f-bf5a0ba55f1c
* callback = update chart
* control = hit callback https://dash.plotly.com/tutorial#controls-and-callbacks
* Dash Design Kit (DDK) = no need for HTML/CSS
* _Metabase_: 🎯 popular https://news.ycombinator.com/item?id=30323131 https://retool.com/blog/top-sql-guis-for-your-data-warehouse-snowflake-bigquery-redshift https://news.ycombinator.com/item?id=37661872 https://www.youtube.com/watch?v=j_4vI2bm6-8

MAYBE
* _Hex_: free to start, great UI but kinda overwhelming https://hex.tech/ https://retool.com/blog/top-sql-guis-for-your-data-warehouse-snowflake-bigquery-redshift
* _Lightdash_: $800/month https://github.com/lightdash/lightdash
* _Preswald_: https://github.com/StructuredLabs/preswald https://github.com/StructuredLabs/preswald/issues/143
* _Redash_: no pricing https://github.com/getredash/redash
* _Tableau_: https://news.ycombinator.com/item?id=30323131 https://news.ycombinator.com/item?id=39519145

NOTEBOOKS
* _Evidence_: borked VS Code outliner https://github.com/evidence-dev/evidence https://news.ycombinator.com/item?id=37663111 https://news.ycombinator.com/item?id=37661872
* _PyGWalker_: 🎯 https://github.com/Kanaries/pygwalker https://github.com/Kanaries/graphic-walker https://graphic-walker.kanaries.net/
* _Quary_: VS Code extension https://github.com/quarylabs/quary
* _Taipy_: for pipelines? https://github.com/Avaiga/taipy https://www.youtube.com/watch?v=phhnakHSNEE

MORE SPECIFIC USE CASES
* _perspective_: streaming https://github.com/finos/perspective https://perspective.finos.org/
* _SQL Explorer_: Django https://github.com/explorerhq/django-sql-explorer
> Write SQL, share results, do some analysis, get insight. No surprises. https://news.ycombinator.com/item?id=40857589

MEH
* _Blazer_: too close to Datasette https://github.com/ankane/blazer
* _Data Formulator_: probably going nowhere https://github.com/microsoft/data-formulator https://news.ycombinator.com/item?id=41907719
* _Dataherald_: 💀 AI query https://github.com/Dataherald/dataherald
* _Datalens_: run locally, from Yandex https://datalens.tech/ https://news.ycombinator.com/item?id=37657772
* _Looker_: Google https://www.cobry.co.uk/looker-vs-looker-studio
* _Poli_: 💀 https://github.com/shzlw/poli
* _shiny_: R https://rstudio.github.io/shinydashboard https://training.talkpython.fm/courses/reactive-web-dashboards-with-shiny-for-data-science https://www.maximum-progress.com/p/economics-is-a-field-of-software
* _streamlit_: interesting paradigm https://streamlit.io/ Hugging Face integration https://huggingface.co/docs/hub/spaces

SPACE
* _business intelligence (BI)_: SQL (devs) + explorer (non-devs) + charting
* SQL-by-mouse https://briefer.cloud/blog/posts/self-serve-bi-myth/
> Analysis, even SQL-based analysis, isn't like design, where a handful of people create stuff and everyone else is a consumer, with clear lines between them. It's much, much fuzzier. Though analysts were always our first adopters, lots of people - PMs, engineers, marketing managers, executives, support agents, operations leads, and all job titles in between - periodically wrote queries. These people occupied the middle part of the distribution between analysts and non-analysts that we thought would be vacant. Users weren't bimodal like we expected, but continuous. https://benn.substack.com/p/work-like-an-analyst

## 📼 Datasette

📜 https://datasette.io/

EXTENSIONS
* mgmt https://datasette.io/plugins/datasette-packages
```sh
poetry run datasette install datasette-dashboards
poetry run datasette uninstall datasette-dashboards
```
* _dashboards_: ✅ https://datasette.io/plugins/datasette-dashboards https://github.com/zachvalenta/datasette-for-BI
* homepage i.e. doesn't go to dashboards by default https://datasette-dashboards-demo.vercel.app/
* alternatives https://datasette.io/plugins/datasette-nteract-data-explorer

ZA
* customizing CSS https://docs.datasette.io/en/stable/custom_templates.html
* maybe has autocomplete? https://github.com/simonw/datasette/issues/1614

---

datasette install datasette-dashboards

BASICS
* https://calmcode.io/course/datasette/introduction
* https://datasette.io/for/exploratory-analysis
* SQLite only https://github.com/simonw/datasette/issues/670

EXTENSIONS
* UI: homepage https://datasette.io/plugins/datasette-homepage-table https://github.com/cldellow/datasette-ui-extras https://datasette.io/plugins/datasette-hovercards https://datasette.io/plugins/datasette-sitemap https://datasette.io/plugins/datasette-query-links https://datasette.io/plugins/datasette-css-properties
* saved queries https://github.com/datasette/datasette-queries
* hosting https://datasette.io/plugins/datasette-publish-vercel https://datasette.io/plugins/datasette-publish-fly https://datasette.io/plugins/datasette-scale-to-zero https://datasette.io/plugins/datasette-gunicorn https://datasette.io/plugins/datasette-codespaces
* auth https://datasette.io/plugins/datasette-redirect-forbidden https://datasette.io/plugins/datasette-auth0 https://datasette.io/plugins/datasette-matomo https://datasette.io/plugins/datasette-ephemeral-tables https://datasette.io/plugins/datasette-permissions-sql https://datasette.io/plugins/datasette-mask-columns https://github.com/kviklet/kviklet
* charts https://datasette.io/plugins/datasette-plot https://datasette.io/plugins/datasette-seaborn https://datasette.io/plugins/datasette-statistics
* markdown https://datasette.io/plugins/datasette-render-markdown
* AI https://datasette.io/plugins/datasette-column-inspect https://datasette.io/plugins/datasette-jupyterlite https://datasette.io/plugins/datasette-export-notebook https://datasette.io/plugins/datasette-chatgpt-plugin https://datasette.io/plugins/datasette-explain https://datasette.io/plugins/datasette-query-assistant https://datasette.io/plugins/datasette-ml https://datasette.io/plugins/datasette-llm-embed https://datasette.io/plugins/datasette-enrichments-gpt https://datasette.io/plugins/datasette-openai
* search https://datasette.io/plugins/datasette-search-all https://datasette.io/plugins/datasette-configure-fts https://datasette.io/plugins/datasette-ripgrep https://datasette.io/plugins/datasette-jq https://datasette.io/plugins/datasette-faiss https://datasette.io/plugins/datasette-jellyfish
* web https://datasette.io/plugins/datasette-cors
* comments https://datasette.io/plugins/datasette-comments
* views https://datasette.io/plugins/datasette-create-view https://datasette.io/plugins/datasette-saved-queries
* IO https://datasette.io/plugins/datasette-export https://datasette.io/plugins/datasette-import https://datasette.io/plugins/datasette-export-database https://datasette.io/plugins/datasette-upload-dbs https://datasette.io/plugins/datasette-chronicle
* telemetry https://datasette.io/plugins/datasette-tail https://datasette.io/plugins/datasette-schema-versions https://datasette.io/plugins/datasette-pyinstrument https://datasette.io/plugins/datasette-query-history https://datasette.io/plugins/datasette-total-page-time https://datasette.io/plugins/datasette-psutil https://datasette.io/plugins/datasette-sentry https://datasette.io/plugins/datasette-visible-internal-db
* audio! https://datasette.io/plugins/datasette-mp3-audio

* https://github.com/simonw/datasette-upload-csvs
* https://github.com/simonw/dclient
* https://github.com/simonw/sqlite-utils-ask
* https://github.com/datasette/datasette-query-assistant

## 💄 Great Tables

📜 https://posit-dev.github.io/great-tables

RUNTIME
* input: df
* output: render by Jupyter kernel https://github.com/posit-dev/great-tables/issues/619
> Typically we use Great Tables in an notebook environment or within a Quarto document. Tables won't print to the console, but using the show() method on a table object while in the console will open the HTML table in your default browser. https://github.com/posit-dev/great-tables

VISUAL DESIGN https://www.youtube.com/watch?v=M5zwlb8OzS0 @ 10:30 Polars selectors https://claude.ai/chat/84ed4940-251f-468b-9282-4f5565127e9c
* icons for quick parse
* bar charts for magnitude
* spans for grouping
* color highlight individual rows
* color highlight for heatmap
* footnotes for context
* background reading https://www.youtube.com/watch?v=M5zwlb8OzS0 [5:30]

MORE TALKS
* https://www.youtube.com/watch?v=JRW2jm8aNiI
* https://www.youtube.com/watch?v=15ICWSJ0sGk

## Holoviz

https://holoviz.org/
https://awesome-panel.github.io/holoviz-quarto/

## 🔵 Quarto

📜 https://quarto.org/ 

* no Marimo support https://github.com/quarto-dev/quarto-cli/discussions/9362
* built around Jupyter kernel
> Typically we use Great Tables in an notebook environment or within a Quarto document. Tables won't print to the console, but using the show() method on a table object while in the console will open the HTML table in your default browser. https://github.com/posit-dev/great-tables

---

* Markdown flavor `.qmd`
* https://www.peterbaumgartner.com/blog/reporting-with-quarto/
* uses Pandoc
* latex https://news.ycombinator.com/item?id=42102262
* Racket https://docs.racket-lang.org/pollen/Backstory.html

## 🪶 Superset

📜 https://superset.apache.org/

```sh
# SETUP TO RUN CONTAINERS
brew install docker
brew install docker-compose
brew install colima
colima start
# SUPERSET
git clone --depth=1  https://github.com/apache/superset.git
docker-compose up --build
# build blew up bc needed lots of mem
# what you'd do if you had a machine with more free memory
colima stop
colima start --memory 4 --cpu 4
```

* _Preset_: hosted Superset https://preset.io/
* pricing: free for 5 users, $20/user/month
* catch-22 around using CSVs where they needed to be uploaded to a database but you couldn't create database without creds
* bad customer support

---

* https://news.ycombinator.com/item?id=37657772
* https://news.ycombinator.com/item?id=37661872

# 💿 DATA

🗄️
* query sandbox
* Capp machine

## canonical

💻 `OLAP.md` schemas

OLAP
* _Great Tables_: https://posit-dev.github.io/great-tables/reference/#built-in-datasets
* _NYC taxi dataset_: https://mattpo.pe/posts/sql-llvm/
* _TPC-DS_: star https://news.ycombinator.com/item?id=42231325 https://trilogydata.dev/demo/ https://duckdb.org/docs/extensions/tpcds.html https://www.tpc.org/tpcds/ 🧠 https://chatgpt.com/c/67b8ba50-2efc-8004-84d8-50f8618f82b8

ML
* _Iris_: https://www.youtube.com/results?search_query=iris+dataset https://docs.pola.rs/user-guide/misc/visualization/#altair
```python
from sklearn.datasets import load_iris
path = "docs/assets/data/iris.csv"
```

OLTP
* https://github-to-sqlite.dogsheep.net/github https://github.com/dbcli/litecli/pull/217#discussion_r1976694809
* _Chinook_: https://github.com/lerocha/chinook-database
* _Datacharmer_: needs port https://github.com/datacharmer/test_db
* _Northwind_: https://github.com/pthom/northwind_psql
* _Sakila_: https://github.com/jOOQ/sakila https://sq.io/docs/tutorial https://posit-dev.github.io/great-tables/blog/design-philosophy/index.html#footnotes
```txt
TABLES
* film: contains details of movies (title, length, rating, description)
* actor: contains information about actors (first name, last name)
* inventory: represents available copies of each movie in the store
* rental: keeps track of movie rentals (customer, rental date, return date)
* customer: information about customers (name, email, and active status)
* staff: represents employees who manage the rentals
* payment: stores the payment transactions for rentals
* category: represents different movie categories (comedy, drama)

FEATURES
* frequent reads and writes: the rental and payment tables simulate frequent transactions common in real-world oltp systems
* concurrency and transactions: multiple users (represented by customers/staff) frequently update and read the database, making it suitable for practicing transaction handling (e.g., BEGIN TRANSACTION, COMMIT, and ROLLBACK)
* indexes and query performance: you can demonstrate how primary keys, foreign keys, and indexes optimize lookups and joins
* entity-relationship design: it’s a well-normalized schema (3rd normal form) with many-to-one and many-to-many relationships, useful for teaching joins
```

## sets

---

* _csvbase_: 🎯 https://csvbase.com/ https://csvbase.com/blog/10


🗄️ `api.md` public
🛠️ BYO https://calmcode.io/labs/drawdata
🌱 https://www.noahpinion.blog/p/why-cant-the-us-build-ships https://github.com/trailofbits/graphtage/graphs/contributors
🔍 https://ourworldindata.org/ https://www.wikidata.org/ https://datasetsearch.research.google.com/ https://www.kaggle.com/datasets https://datausa.io/ https://www.splitgraph.com/ https://calmcode.io/datasets

ART
* music: https://musicbrainz.org/ https://www.kaggle.com/datasets/nolanbconaway/24169-pitchfork-reviews/data https://pudding.cool/2024/03/greatest-music/
* viz https://news.ycombinator.com/item?id=28445761
* movies https://www.theringer.com/2024/9/23/24252627/biggest-takeaways-netflix-data-dump-2024-streaming IMDb Parents Guide https://www.theringer.com/movies/2024/10/24/24276810/sex-in-movies-decline-international-market-gen-z-intimacy-coordinators-anora https://news.ycombinator.com/item?id=42050260
* literature: ratings http://fastml.com/goodbooks-10k-a-new-dataset-for-book-recommendations/ https://github.com/zygmuntz/goodbooks-10k https://bookbrainz.org/ text http://www.jessamyn.com/barth/index.html https://en.wikisource.org/ https://news.ycombinator.com/item?id=1394077 Hemingway, Faulkner https://news.ycombinator.com/item?id=42429606

ECON
* finance https://github.com/ranaroussi/yfinance https://calmcode.io/datasets
* housing https://www.zillow.com/research/data/
* India https://www.dataforindia.com/

GOV
* politics/voting https://www.slowboring.com/p/breaking-down-the-election-results https://www.govtrack.us/congress/bills/119/hr30 https://github.com/unitedstates/congress
* https://en.wikipedia.org/wiki/Congressional_Research_Service https://www.noahpinion.blog/p/why-cant-the-us-build-ships
* census https://www.ipums.org/ https://www.edwest.co.uk/p/how-many-people-live-in-britain
* population: https://simplemaps.com/data
* national https://github.com/bundesAPI/deutschland

NATURAL WORLD
* scientific https://news.ycombinator.com/item?id=27365755
* weather https://github.com/blaylockbk/Herbie https://news.ycombinator.com/item?id=42467449

SPORTS
* diet, sleep https://calmcode.io/datasets
* https://www.statmuse.com/
* baseball https://en.wikipedia.org/wiki/Bill_James https://jamesrledoux.com/projects/open-source/introducing-pybaseball/ https://www.thedrummeyangle.com/post/an-introduction-to-pybaseball-using-python-to-analyze-baseball-data https://www.datacamp.com/tutorial/scikit-learn-tutorial-baseball-1
* basketball https://craftednba.com/ https://cleaningtheglass.com/ https://cleaningtheglass.com/stats/player/4231/onoff#tab-team_efficiency https://sportradar.com/ https://www.youtube.com/watch?v=boct75srdbE
* football https://x.com/theStevenRuiz/status/1838644108685963386
* soccer https://statsbomb.com/news/statsbomb-release-free-euro-2024-data

---

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

## regression

💻 https://github.com/zachvalenta/regress
📙 Takashi manga regression

---

DIMENSIONAL ANALYSIS
* _dimension_: metadata; used in econometrics 📙 Bueno [25]
```python
import csv
from collections import defaultdict
data = [
    {'Product': 'Tablet', 'Region': 'West', 'Sales': 5000},
    {'Product': 'Laptop', 'Region': 'East', 'Sales': 10000},
    {'Product': 'Laptop', 'Region': 'East', 'Sales': 12000},
    {'Product': 'Phone', 'Region': 'East', 'Sales': 9000},
    {'Product': 'Phone', 'Region': 'West', 'Sales': 8000},
]
sales_summary = defaultdict(int)
for record in data:
    product = record['Product']
    region = record['Region']
    sales = record['Sales']
    sales_summary[(product, region)] += sales
for (product, region), total_sales in sales_summary.items():
    print(f"Product: {product}, Region: {region}, Total Sales: {total_sales}")
```

* basic example
```python
# house size (sq ft) and prices (in $1000s)
house_sizes = [500, 750, 1000, 1250, 1500, 1750, 2000]
house_prices = [150, 200, 250, 300, 350, 400, 450]

# calc means
mean_x = sum(house_sizes) / len(house_sizes)
mean_y = sum(house_prices) / len(house_prices)

# calc slope (m) and intercept (b)
numerator = sum((x - mean_x) * (y - mean_y) for x, y in zip(house_sizes, house_prices))
denominator = sum((x - mean_x) ** 2 for x in house_sizes)
m = numerator / denominator
b = mean_y - m * mean_x
print(f"slope (m): {m}")
print(f"intercept (b): {b}")

# predict prices based on the linear regression equation
def predict(x):
    return m * x + b

# test predictions
test_sizes = [600, 800, 1200, 1600, 1800]
predicted_prices = [predict(size) for size in test_sizes]
for size, price in zip(test_sizes, predicted_prices):
    print(f"House size: {size} sqft -> Predicted price: ${price:.2f}k")
```

## seed

🗄️ `test.md` db

---

> pull in `make-seed-data` from Capp repo

```text
Can you make me some sample data?

FOO
id,mpn,mfg,price
1,IMQL,apple,150
2,6Z6G,samsung,200
3,S3OW,motorola,350

BAR
id,mfg,price
IMQL,apple,125
6Z6G,samsung,200
S3OW,motorola,325

* table FOO mpn maps to table BAR id
* their are some price differenece btw the records
* each table should have 10 records
```

# 🛠️ TOOLING

🔗 https://github.com/mgramin/awesome-db-tools
🗄️ `protocols.md` file fmt

## EDA

🗄️ `dataframes.md` pretty print
💻 https://github.com/zachvalenta/wd
> just learn how to use visidata better

IN THE RIGHT DIRECTION
```sh
datasette inspect db.sqlite
```
* https://docs.datasette.io/en/stable/facets.html
* https://cran.r-project.org/web/packages/data.table/vignettes/datatable-reshape.html
* https://github.com/lux-org/lux
*️ https://github.com/vanna-ai/vanna
* https://www.visidata.org/docs/api/

FIND NULL COLS
> rn polars/pandas seems like the most straightforward option, maybe write CLI for this and add to fkfind
* _visidata_: histogram
* _xsv_: frequency
```sh
xsv select 'Manufacturer Name' results.csv | xsv frequency

field,value,count
Manufacturer Name,NMS - Not Manufacturer Specific,723
Manufacturer Name,Banner Engineering Corp.,445
Manufacturer Name,TBD - To Be Determined,384
Manufacturer Name,(NULL),190
```
FIND DUPES
```sql
select entity.pn, count(*) from entity
group by pn having count(*) > 1;
```

---

is AI just bad at this? https://chiraaggohel.com/posts/llms-eda/

> there's got to be a less manually way to do this -> I have a bunch of CSVs. Is there an automated way to: figure out where all the foreign keys are and document the schema with a plaintext ERD?

FKFIND
* https://code.visualstudio.com/docs/datascience/data-wrangler
* https://github.com/zachvalenta/capp-datalab#entity
* pypi pkg, Rust CLI, sqlite extension <https://github.com/pyo3/pyo3>
```txt
SQLite allows custom functions, virtual tables, and collation sequences using dynamically loaded extensions (.so files). You can:
* Write an SQLite extension in Rust using pyo3 to call Python.
* Use rusqlite to write native Rust extensions.
* Use pysqlite3 for Python-based function injection.

Approach:
* Write a Rust-based shared library using pyo3.
* Use sqlite3_create_function() to expose Python-backed SQL functions.
* Compile the Rust extension (.so file) and load it in SQLite using .load.
```
```sql
-- SEE ALL POTENTIAL JOIN KEYS BETWEEN TABLES
select column_name, data_type 
from information_schema.columns 
where table_name in ('mars', 'products', 'catalog');
```

EDA JOINS + SQL FROM SHELL
* ❓ _sqlite_: + litecli
* ❌ _polars_: truncated output
* 📍 _duckdb_: data loading problem
* 🫤 _visidata_: save joins output as file + inspect manually
* _q_: no joins https://github.com/harelba/q
* _sq_: no joins https://github.com/neilotoole/sq https://news.ycombinator.com/item?id=41760697 
* _dsq_: maybe joins https://github.com/multiprocessio/dsq
> dsq lets you pass multiple CSV files as positional arguments. Each file is treated as a separate table (with the table name inferred from the filename) so you can write a query like:
```sql
SELECT a.col1, b.col2 FROM a AS a
  JOIN b AS b
    ON a.id = b.id;
```
```sh
dsq "SELECT a.col1, b.col2 FROM a AS a JOIN b AS b ON a.id = b.id;" a.csv b.csv
```

## generate

https://github.com/zachvalenta/capp-crudite
https://github.com/zachvalenta/capp-looker
https://github.com/zachvalenta/capp-the-crud

https://datasette.io/plugins/sqlite-fastrand

CONVERSION / GENERATION
* tabular to JSON https://github.com/jazzband/tablib
* JSON to tabular https://duckduckgo.com/?q=json+to+pandas&ia=web
* https://hakibenita.com/sql-for-data-analysis#generating-data
* import from 3rd party: Dogsheep https://datasette.substack.com/p/dogsheep-personal-analytics-with
* Visidata
* Posgres https://news.ycombinator.com/item?id=24189582
* https://github.com/simonw/sqlite-utils
```sh
# https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 20:25
curl www.api.com | jq foo | sqlite-utils insert foo.db bar_table
```

## entry (dataclerk)

🗄️ EDA > fkfind

> Are there any CLI/TUI tools in which you can enter data directy to a database but with the caveat that the tool would figure out the schema for you? Let me give you an example. Imagine you have a database for books. There are tables for authors, book, genres, publishers, etc. When you open this tool, you don't have to remember all the fields you need to fill out or foreign key constraints. The tool would simply provide a form, you'd input the information you needed to. Anything that could be a dropdown (maybe genres?) would be, otherwise you'd simply type in the rest, with appropriate warnings if you were violating a foreign key constraints or type constraints (e.g. if you failed to put an integer for publication_year).
```txt
Core mechanics of existing tools:
* Schema introspection (reading DB structure)
* Form generation (converting schema to UI)
* Validation (enforcing constraints)
* API layer (how the tool talks to the DB):
- Direct DB connection (pgcli)
- REST (PostgREST)
- GraphQL (Hasura)

The "shape" of the problem is essentially: Schema → UI → API → DB.
Each tool optimizes for different parts of this pipeline, but none fully optimizes for data entry specifically.
```
```txt
The closest match to what you're describing is nocodb - it's a bit heavier than what you want (runs as a web service) but:
* Auto-detects relationships
* Builds forms dynamically
* Handles constraints
* Provides dropdowns for foreign keys

However, I think there's a gap in the tooling space here. The ideal tool would be:
* CLI/TUI first
* Schema-aware but not schema-first
* Smart defaults + constraint inference
* Progressive disclosure of complexity

Have you considered building this? The core components would be:
* Schema inference engine
* Constraint detector
* Form generator
* DB connector
```

---

PEDAGOGY 🗄️ `architecture.md` serverless > baked data
* https://selectstarsql.com/frontmatter.html#dataset
* https://pgexercises.com/gettingstarted.html https://github.com/AlisdairO/pgexercises/issues/28
* https://sql-playground.wizardzines.com/
* https://www.crunchydata.com/developers/tutorials
* https://sqlime.org/
* tldr: better at SQL if data 1) local 2) interesting
* small databases https://news.ycombinator.com/item?id=34558054
* example databases: Spanish, Sakila https://github.com/jOOQ/sakila/blob/main/sqlite-sakila-db/sqlite-sakila-schema.sql 📙 Beaulieau [41]
* connect to actual server: https://data.stackexchange.com/help https://sqlpd.com/ https://news.ycombinator.com/item?id=30631477
* playgrounds: PG exercises https://github.com/zachvalenta/pg-exercises https://jvns.ca/blog/2023/04/17/a-list-of-programming-playgrounds/

* https://github.com/Mozzo1000/booklogr
* https://tomcritchlow.com/2023/01/27/small-databases/
* https://realpython.com/contact-book-python-textual/
* Airtable?
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

## GUI (dbeaver)

🗄️ `python/feedback.md` notebook

OPTIONS
* NoSQL: Table Plus https://news.ycombinator.com/item?id=22908224 DbGate https://github.com/dbgate/dbgate
* SQLite: charting https://github.com/sqlitebrowser/sqlitebrowser https://github.com/coleifer/sqlite-web https://sqlitestudio.pl/
* Postgres: pgAdmin, PGweb https://github.com/centerofci/mathesar
* _Beekeeper_: $7/month https://www.beekeeperstudio.io/
* _Datagrip_: 🎯 $45/month with AI, ERD https://www.jetbrains.com/datagrip/
* _DBeaver_: OSS, ERD https://dbeaver.io/ https://stackoverflow.com/a/48397209
* _Mathesar_: 🎯 web app to make using Postgres friendly https://github.com/mathesar-foundation/mathesar
* _Outerbase_: browser https://github.com/outerbase/studio https://news.ycombinator.com/item?id=42320032
* _Ultorg_: 🎯 $35/month, queryless joins, very interesting interface https://www.hytradboi.com/2022/ultorg-a-user-interface-for-relational-databases
* _WhoDB_: 🎯 AI https://whodb.clidey.com/docs/

## 🍞 miller

🗄️ `os/tools.md` string processing
📜 https://miller.readthedocs.io/en/latest/glossary https://miller.readthedocs.io/en/latest/reference-verbs/

PIPELINES
```sh
cat $CSV | mlr --csv put '$col = int($col)' > $CSV  # cast type from int to float
filter 'is_null($col)' $CSV                         # filter nulls https://miller.readthedocs.io/en/latest/reference-dsl-builtin-functions/
filter '$header != ""' $CSV                         # filter out nulls
mlr --csv filter '$col != ""' $CSV                  # filter out empty strings
mlr --csv filter '$price_list != ""' final.csv
mlr --csv filter '$price_list != ""' final.csv
mlr --csv filter '$price_source != ""' then filter '$mpn_score == 100' $CSV  # chained
```

CONFIG https://miller.readthedocs.io/en/latest/customization/
* `$HOME/.mlrrc`
```sh
--list-color-names # view colors https://miller.readthedocs.io/en/latest/output-colorization/
c2p  # --c2p
allow-ragged-csv-input  # if data line fields > header line, insert empty val instead of err (CSV header/data length mismatch)

# IO
--icsv    # input csv
--tsv     # input tsv
--opprint # output pprint
--c2p     # combine --icsv and --opprint https://miller.readthedocs.io/en/latest/keystroke-savers/#short-format-specifiers-including-c2p
--csv     # IO csv
```

---

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
filter '$header == "value"' $CSV # select * where header = val
filter '$header1 == "value-foo"' && '$header2 == "value-bar"' example.csv
filter 'is_null($header)' example.csv # https://miller.readthedocs.io/en/latest/reference-dsl-builtin-functions/
filter '$earnings > 0.0' example.csv
```

## 💿 REPL (dbcli)

📜 https://www.dbcli.com/

---

ALTERNATIVES
* CLI query https://github.com/neilotoole/sq https://github.com/PeepDB-dev/peepdb
* https://github.com/theseus-rs/rsql
* usql as alternative https://news.ycombinator.com/item?id=42161987

* exit: `exit`, `\q`
* open with env var: `cli -h`
* list tables: `\dt`
* help: `\?`
* autocomplete: `ctrl e`
* clear screen: `ctrl l`
* _metacommand_: preceded w/ backslash https://www.pgcli.com/commands
* set pager to bat: `pager = less -SRXF` https://www.pgcli.com/docs
* _named query_: snippet, saved query https://www.pgcli.com/named_queries.md https://simonwillison.net/2024/Dec/3/datasette-queries/
* syntax: `f` (litecli) `n` (pgcli)
* list: `\f` https://github.com/dbcli/pgcli/issues/1236
* save: `\fs <name> <query>` https://github.com/dbcli/pgcli/issues/938
* save w/ param: `\fs <name> <query where foo = $1>` https://github.com/dbcli/pgcli/issues/938
> broken in sandbox: could be pager, Python version, config (try default config installed in $HOME) https://github.com/dbcli/pgcli/search?q=codec&type=issues
* use: `\f <name>`
* use w/ param: `\f <name> "arg"`
* rm: `\fd <name>` https://litecli.com/favorites/

### litecli

🗄️
* `OLTP.md` SQLite > CLI
* `python/pkg.md` venv
💻
* https://github.com/dbcli/litecli/pull/216
* https://github.com/dbcli/litecli/pull/217

* dot commands
```sh
.schema       # all schemas
.schema $TBL  # schema for table
.tables       # list tables
.databases    # list databases
```
* open db: `litecli $DB`
* config: `~/.config/litecli/config` https://litecli.com/config/
* query to CSV
```sh
litecli db.sqlite -e "select eid, mfg, mpn, apn, buyline, priceline, year_sales, last_sale, list_price, list_price_effective_date, date_created, date_updated, gross_profit from products where buyline like '%dongan%'" --csv > dongan-products.csv
```

---

LLM
* https://amjith.com/blog/2024/introducing-llm-to-litecli/
* https://amjith.com/blog/2025/llm-in-litecli-1/
* https://amjith.com/blog/2025/llm-in-litecli-2/
* https://github.com/dbcli/litecli/issues?q=llm

### pgcli

```sh
# install https://github.com/dbcli/pgcli/issues/1413#issuecomment-2028781741
$ pipx install pgcli
$ pipx inject pgcli psycopg_binary
# connect
pgcli postgresql://$USER:$PW@$HOST:$PORT/$DB
# dump table to CSV
\COPY (SELECT * FROM $TBL LIMIT 100) TO '$TBL.csv' WITH CSV HEADER;
# as snippet
[alias_dsv]
$TBL = "\COPY (SELECT * FROM {0} LIMIT 100) TO '{0}.csv' WITH CSV HEADER"
\d $TBL product_template
```

## spreadsheet (Excel)

🗄
* `finance/corporate.md` accounting > tooling
* `python.md` REPL

DESIGN
* good REPL for single table https://www.ultorg.com/
* bad at n tables
> Whether in finance, engineering, operations, or the life sciences, you are likely working with tables of data in spreadsheets, CSV files, or an external database. Spreadsheets are excellent tools for managing a single table of data. They are a poor fit for database tasks, however, where data must be combined and queried in many different ways. https://www.ultorg.com/
* bad at UX, hence Airtable https://luttig.substack.com/p/dont-forget-microsoft Airtable is bad? https://news.ycombinator.com/item?id=26448985 Airtable let's you attach images, documents https://github.com/nocodb/nocodb https://news.ycombinator.com/item?id=41503251 https://news.ycombinator.com/item?id=34127804 https://gitlab.com/baserow/baserow more Airtable https://teable.io/ https://www.hytradboi.com/2022/why-airtable-is-easy-to-learn-and-hard-to-outgrow
* bad at collaboration, hence Google Sheets https://luttig.substack.com/p/dont-forget-microsoft
* criticism https://betonit.substack.com/p/spreadsheets-letters-from-a-quant https://www.natemeyvis.com/writing/on-bryan-caplans-spreadsheets/

ALTERNATIVES
* BYO https://jamesg.blog/2024/08/21/spreadsheet-engine/
* TUI https://github.com/andmarti1424/sc-im
* OSS https://github.com/gristlabs/grist-core
* webapp https://equals.app/ https://rows.com/
* in Python https://pyspread.gitlab.io/ https://news.ycombinator.com/item?id=40284219
* _Google Sheets_: https://github.com/nithinmurali/pygsheets
* _IronCalc_: https://news.ycombinator.com/item?id=42095292 https://github.com/ironcalc/ironcalc
* _rowzero_: https://rowzero.io/ https://grantslatton.com/
* _pysheets_: 🎯 uses pyodide https://pysheets.app/about https://realpython.com/podcasts/rpp/226/
* _sc-im_: 🎯 clone TUI https://github.com/andmarti1424/sc-im
* _visicalc_: predecessor to Lotus123, Excel http://www.paulgraham.com/mac.html
* _SocialCalc_: pre-visicalc? https://aosabook.org/en/v1/socialcalc.html https://aosabook.org/en/posa/from-socialcalc-to-ethercalc.html
* _UltOrg_: spreadsheet on top of dbms https://news.ycombinator.com/item?id=30868696 🔍 `Ultorg beta`

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
* Visual Basic https://retool.com/visual-basic/ https://retool.com/blog/the-history-and-legacy-of-visual-basic

## ⚛️ sqlite-utils

🛠️ https://github.com/simonw/sqlite-utils

IMPORT CSV TO TABLE
```sh
sqlite-utils insert db.sqlite $TABLE $CSV --csv

# just tried to import this CSV
.import entity-pn.csv entity_pn

# got this error
entity-pn.csv:177587 expected 0 columns but found 3 - ignored

# Strange, since when do i need to spec out the exact number of columns, seems like something that should just work. Is there a way you can config sqlite to do type inference on a sample subset of data and just figure it out. Imagine if you had to manually configure the column names and types every time you loaded a pandas dataframe. Barbaric!
```

other use cases
```sh
$DB "SELECT * FROM $TBL LIMIT 5" --json      # RS as JSON
query $DB "SELECT COUNT(*) FROM $TBL"        # RS to stdout
transform $DB $TBL --rename $COL foo         # rename column
insert $DB $TBL $CSV --csv; serve $DB        # serve table as API
insert $DB $TBL $CSV --csv --pk=id --upsert  # upsert
rows $DB $TBL --csv > $CSV                   # export
schema $DB                                   # validate schema
```

## TUI

🗄️ `OLAP.md` metadata

BYO / REQUIREMENTS
* query editor: vi mode readline
* automcomplete https://www.jvt.me/posts/2024/06/07/sql-workflow/
* ERD 🗄 `info.md` viz / entities / ERD
* schema documentation https://www.querybook.org/ https://github.com/quarylabs/quary
* analytics guide
* notebooks https://github.com/electroly/sqlnotebook
* AI https://whodb.clidey.com/docs/ https://whodb.clidey.com/docs/usage-houdini/what-is-houdini
* numeric pane navigation
* _query editor_: save, autocomplete
* _results viewer_: result set

FEATURES
* follow FKs https://github.com/Wisser/Jailer https://github.com/centerofci/mathesar
* data catalog https://harlequin.sh

TUI
* _dblab_: no readline https://github.com/danvergara/dblab
* _dadbod_: harlequin for Neovim https://github.com/kristijanhusak/vim-dadbod-ui https://www.youtube.com/watch?v=NhTPVXP8n7w
* _lazysql_: keybindings look goofy https://github.com/jorgerojas26/lazysql
* _GoBang_: 💀 https://github.com/TaKO8Ki/gobang
* _rainfrog_: Postgres https://github.com/achristmascarl/rainfrog https://www.youtube.com/watch?v=qURrmEzsKH8

HARLEQUIN 📜 https://harlequin.sh
* good UI (example of non-cartoonish Textual)
* ❌ query editor: no vi readline
* ❌ docs not searchable
* bad default keybindings (c.f. 'data catalog') https://harlequin.sh/docs/getting-started/usage
* need config to get Vim keybindings (dunno if you can nav btw panes like lazygit) https://harlequin.sh/docs/keymaps/index https://harlequin.sh/docs/keymaps/config https://github.com/tconbeer/harlequin/discussions/422
* can't open CSV from CLI https://github.com/tconbeer/harlequin/discussions/314
* config profiles for diff dbms
* use in Django https://adamj.eu/tech/2024/05/07/django-harlequin/

## ❎ xsv

🗄️ `os/tools.md` string processing
📜 https://github.com/BurntSushi/xsv

```sh
# MUNGE
$ fmt $TSV > $CSV

# DML
$ headers $CSV          # get headers with index
$ headers -j $CSV       # get headers w/out index
$ select "header" $CSV  # select all from header

# EDA
$ xsv sample 50 $CSV                 # get sampled subset
$ stats $CSV | xsv table             # stats (sum, min, max)
$ xsv slice -i 0 $CSV | xsv flatten  # get line of data and display as two columns
product_id                            684148
ord_id                                S1468706
bill_to_customer_id                   1204
unit_cost                             74.06
unit_price                            88.65
ship_date                             2013-11-22
```

---

```sh
count songs.csv # count records
split -s <records_per_file> <output-dir> <csv> # split into n files
search -i -s "header" "query" $CSV # search within header (case insensitive)
```

# 🟦 VISIDATA

🗄️ `protocols.md` CSV
🔍 https://stackoverflow.com/questions/tagged/visidata
📜
* repo https://github.com/saulpw/visidata
* docs https://www.visidata.org
* guide https://jsvine.github.io/intro-to-visidata/
* ref https://jsvine.github.io/visidata-cheat-sheet/en/

COMMANDS
* command prompt: `SPACE` https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/
* help: `ctrl h` jumps to man page https://jsvine.github.io/intro-to-visidata/basics/getting-out-of-trouble/
* available cmds: `z ctrl h`
* copy current cell: `syscopy-cell`

STATE
* create: sheet `A` attr `za` record `a` n records `ga` https://www.youtube.com/watch?v=yK3qgOIx4x0 [0:25,1:30]
* undo: `U`
* save current sheet: `CTRL S`
> super slow for half GB TSV file
* save current row: `Y`
* save selected rows: `gY`

CMDLOG
* stored at `~/.visidata/history`
* play: `vd -p cmd_log.vd` https://www.youtube.com/watch?v=yK3qgOIx4x0 [5:20]
* view: `D`
* save: `ctrl s`

SESSION
* save session: `CTRL d` https://www.visidata.org/docs/save-restore/
* restore session: `vd - <file>`

CONFIG https://github.com/zachvalenta/dotfiles/blob/7f843714b3c3d6eb531dfb292e91214c051ef82e/db/.visidatarc
* fs: `~/.visidatarc` https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* cache: `~/.visidata`
* config: `shift o` global options sheet `z shift o` sheet-specific `~/.visidatrc` persistent https://jsvine.github.io/intro-to-visidata/advanced/configuring-visidata/
* formats: Parquet, CSV https://www.visidata.org/docs/formats/ `.parquet` extension only https://github.com/saulpw/visidata/issues/2712
* sources: Postgres, Clickhouse https://www.visidata.org/blog/2022/connect-visidata-to-sql-databases-with-vdsql/
* turn off status messages https://github.com/saulpw/visidata/issues/2567 https://github.com/saulpw/visidata/issues/2621
* turn off DOS newline / carriage return https://github.com/saulpw/visidata/issues/387

---

https://cosimameyer.com/post/2024-09-05-pythonistr-a-match-made-in-data-heaven/
https://github.com/cosimameyer/overviewpy

* dealing with large files https://jsvine.github.io/intro-to-visidata/intermediate/large-files/
* plugin for get duplicates https://jsvine.github.io/intro-to-visidata/advanced/extending-visidata/?highlight=duplicate
* pass cells to function https://www.youtube.com/watch?v=yhunJc8Nu4g 5:00

* load data: `vd <file>` https://www.visidata.org/docs/loading/ https://www.visidata.org/formats/
* convert data: `vd <.json/csv> -b -o <name>.db` 🗄 export sheet
* graphing https://www.youtube.com/watch?v=Ozap_numsjI https://www.visidata.org/docs/graph/ https://www.youtube.com/watch?v=j0qn8OIiV-w
> check out deciles from aggregates
* munge delimited data https://www.youtube.com/watch?v=yhunJc8Nu4g
* _melt_: mv from 1 record n attr to n records 1 attr https://www.youtube.com/watch?v=yhunJc8Nu4g 2:30

* rf using Paul's playlist https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
https://www.youtube.com/playlist?list=PLxu7QdBkC7drrAGfYzatPGVHIpv4Et46W
* `:q` to exit vd itself vs. just quitting a sheet https://github.com/saulpw/visidata/issues/538 https://github.com/saulpw/visidata/issues/483 https://github.com/saulpw/visidata/issues/389 https://github.com/saulpw/visidata/issues/212
* connect to postgres https://www.visidata.org/formats/#postgres
* load subset of file https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#from-the-command-line
* select random subset https://jsvine.github.io/intro-to-visidata/intermediate/large-files/#select-a-random-sample-of-rows

## DML

JOINS
* load multiple CSVs: `vd $CSV1 $CSV2`
* mark col as key: `!`
* select col from meta sheet
* start join prompt: `&` https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/#join-the-two-frequency-tables

EDA
* histogram: `F`
* group by: go to col > histogram > rm percent/histogram col https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/#count-the-number-of-collisions-per-state
* histogram of keyed col: `gF`

SEARCH
* regex: `/`
* regex exact: `^`
> you got burned by searching `valid` when column values had both `valid` and `invalid` i.e. you needed to search `^valid`

FILTER
* `|`: regex + select https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/ https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with

SELECT
* `"`: mv selected records to own sheet https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#using-frequency-tables-to-select-and-filter-for-multiple-values
* `s`: select single
* `u`: unselect single
* `gs`: select all
* `gu`: unselect all
* `gt`: select everything that did *not* match filter https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/

## attr

📜 https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/

NAV
* goto: `c $COL_REGEX`
* scroll: `hl`, `gh/gl`
* mv: `H/L`

HIDE/EXPAND https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-expand-shrink-and-remove-columns
> can set to specific column width
* hide/unhide: `-` / `gv`
* expand: `_` single `g_` all
* shrink by 1/2: `z-`
* expand json: `()`

CREATE/UPDATE
* create blank: `za` https://jsvine.github.io/intro-to-visidata/intermediate/creating-new-columns
* rename: `^`
* type: `~` text `%` float `#` int `$` currency `@` date https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-set-column-types https://www.visidata.org/docs/graph/ https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-set-column-types https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#manipulating-columns-from-the-columns-sheet
> need to set type for sort to work correctly

---

* key: `!`; pins + certain cmd only apply to them https://jsvine.github.io/intro-to-visidata/basics/understanding-columns/#how-to-designate-key-columns

AGGREGATION
* `z+` https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#one-off-calculations
* sum `z +` https://www.youtube.com/watch?v=yhunJc8Nu4g 4:20
* set value `g=` https://www.youtube.com/watch?v=yK3qgOIx4x0 3:20
> so even if underlying attr type is non-numeric can change type in sheet
* https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#adding-aggregators https://sqlfordevs.com/multiple-aggregates-in-one-query https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#one-off-calculations

* sort col `[` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#how-to-sort-rows
* _go to_: ❓ https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching0
* _joins_: https://jsvine.github.io/intro-to-visidata/intermediate/joining-sheets/

* _select all records that match on current cell_: `| <val>` https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#by-matching-patterns
* https://jsvine.github.io/intro-to-visidata/basics/navigating-visidata/#how-to-move-via-searching https://jsvine.github.io/intro-to-visidata/basics/understanding-rows/#via-expressions

## records

---

* command mode + set col to set all values for column? couldn't figure out how to do this
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

## sheets

TYPES
* columns: `C`

SEMANTICS
* _sheet_: god component https://jsvine.github.io/intro-to-visidata/basics/understanding-sheets/
* _source sheet_: actual data
* _derived sheet_: derived data off source sheet

ZA
* _rename_: `SPACE` + `rename-sheet` https://jsvine.github.io/intro-to-visidata/practical/distinctive-birds/#rename-the-filtered-sheet

---

* pull values into new sheet https://www.youtube.com/watch?v=yhunJc8Nu4g 3:00
* create sheet from selected records: `"` https://jsvine.github.io/intro-to-visidata/basics/sorting-and-filtering/#filtering-selected-rows-with
* _meta sheet_: combo columns `C` sheets `S` summary `I`
* frequency `F` combo frequency `gF` https://jsvine.github.io/intro-to-visidata/basics/summarizing-data/#multi-column-frequencies
* pivot table https://jsvine.github.io/intro-to-visidata/intermediate/reshaping-data/#creating-pivot-tables
* reload/reset `ctrl r`
* toggle `ctrl 6`
* save `ctrl s` https://www.youtube.com/watch?v=j0qn8OIiV-w 4:30
* exit: `q` single `gq` all `gs` view recently exited
* rm: `d`
* view deleted `gS`
