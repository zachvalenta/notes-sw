# ⛩️

## 参考

📚
* McKinney https://wesmckinney.com/book/
* VanderPlas https://jakevdp.github.io/PythonDataScienceHandbook/

## 进步

TOOLING
* compare https://github.com/capitalone/datacompy https://www.thoughtworks.com/radar/languages-and-frameworks/datacompy
* visualize https://github.com/man-group/dtale
* diff https://www.youtube.com/watch?v=5Rc9xkeHth0
* GPU acceleration https://www.youtube.com/watch?v=86nMARKN7ho https://www.youtube.com/watch?v=Aumh3evLSKc https://www.youtube.com/watch?v=PH7ExhXYkxQ
* tables rendered to HTML https://posit-dev.github.io/great-tables

# ⚙️ DESIGN

* _dataframe_: result set + operations https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://github.com/go-gota/gota/blob/master/dataframe/dataframe.go

---

https://news.ycombinator.com/item?id=42193043
https://www.youtube.com/watch?v=cgWHPTx0wjw
https://calpaterson.com/bank-python.html
https://tibble.tidyverse.org/
https://dplyr.tidyverse.org/ https://calmcode.io/course/dplyr-verbs/introduction

ZA
* Dataframe Interchange Protocol, Dataframe API Standard https://ponder.io/how-the-python-dataframe-interchange-protocol-makes-life-better/ https://ponder.io/why-are-there-so-many-python-dataframes/ https://pythonspeed.com/articles/polars-pandas-interopability/

## 🦢 Ibis

📜 https://ibis-project.org/

to Jack 24.12.10 https://www.youtube.com/watch?v=8MJE3wLuFXU
> different semantics/interface than Pandas though so would assume - maybe even for simple stuff - you're not porting from Pandas but rather rewriting
> one way around the pandas/polars interop problem (and others like it) https://ibis-project.org/
> relatively new-ish but from the guy who wrote Pandas (Wes McKinney)
> SQL is the longest lasting thing that still gets used for new projects (sorry, C) but it's kinda like Bash in that it's ugly/verbose to read and harder to write than ORM/dataframe code. tons of SQL out in the world so great use case for LLMs (like regex) but Ibis a great compromise, SQL becomes akin to compiler output, you can always dig into the assembly if need be [yes, compilers output bytecode, IR, etc.] but in most cases you're can happily plug away in a much better DSL. https://www.scattered-thoughts.net/writing/against-sql

* dataframe API
* https://calmcode.io/course/ibis/introduction
* transpiles to SQL i.e. works with SQL-based query engines (BigQuery, Clickhouse, Postgres, Snowflake) https://realpython.com/podcasts/rpp/201/
* compiles to Python i. e https://talkpython.fm/episodes/transcript/462/pandas-and-beyond-with-wes-mckinney
* dataframe API that can use Polars/Pandas query engine or transpile to SQL and run against relational dbms https://talkpython.fm/episodes/show/462/pandas-and-beyond-with-wes-mckinney
* https://www.youtube.com/watch?v=C4aUG9poN6E https://us.pycon.org/2024/schedule/presentation/55/index.html

## 🐋 Narwhals

---

> First up: we are completely rewriting how our Plotly.py library talks to dataframes in the 6.0 release. Instead of relying on the Pandas API, we are using Narwhals which provides an abstraction layer over several kinds of tabular data. This means faster, more efficient handling of tabular data and serious performance gains for data apps at scale. You'll notice with this change that Plotly.py no longer has to do in-memory copying when you hand it something like a Polars dataframe. https://plotly.com/blog/plotly-dash-major-release/
* _Narwhal_: API for dataframes https://pythonbytes.fm/episodes/show/402/how-to-monetize-your-blog https://realpython.com/podcasts/rpp/224/ https://github.com/benrutter/wimsey
> Chances are, you’ve never heard of Narwhals. That’s because it’s a tool targeted at tool builders, rather than at end users. Specifically, it allows library maintainers to support multiple dataframe libraries as inputs, without having to make any of them required. https://pola.rs/posts/lightweight_plotting/

# 🐼 PANDAS

📜 https://pandas.pydata.org/docs/
📙 McKinney data analysis https://wesmckinney.com/book/
🔍
* https://github.com/jvns/pandas-cookbook
* https://github.com/kxzk/an-embarrassment-of-pandas
* https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf
* https://web.archive.org/web/20230127194856/https://scribe.citizen4.eu/pandas-illustrated-the-definitive-visual-guide-to-pandas-c31fa921a43

SEMANTICS
* _series_: a column, all rows from a single column https://www.youtube.com/watch?v=zmdjNSmRXF4 [10:00] https://pandas.pydata.org/docs/user_guide/10min.html#getting
* `name`: series header
* _index_: row number https://realpython.com/pandas-reset-index/

DESIGN
> Pandas was originally written to replace Excel in financial/econometric modeling, not as a replacement for SQL. https://news.ycombinator.com/item?id=35429555
* impl: built on NumPy arrays i.e. core operations carried out in C https://en.wikipedia.org/wiki/Pandas_(software) https://realpython.com/fast-flexible-pandas/#but-i-heard-that-pandas-is-slow
* style: method chaining https://github.com/pyjanitor-devs/pyjanitor

---

PERF
* https://hakibenita.com/sql-for-data-analysis#sql-vs-pandas-performance
* https://pythonspeed.com/memory
* https://realpython.com/fast-flexible-pandas

## DML

```python
col in df.columns  # existence
df[df['id'] == 42]  # subset based on equality i.e. all rows where ID = 42
```

---

SELECT
```python
df.col   # get col https://pandas.pydata.org/docs/user_guide/10min.html#getting
df[0:3]  # get row
df.col.isin(myl) # bool for each row
df.index[df.col.isin(myl)] # row index for True bool
df.drop(df.index[df.col.isin(myl)]) # drop row indexes for rows matching list el
df.columns # all col
df[["col1", "col2"]] # n col
df.iloc[3] # get row by row index
df.iloc[3, 17] # get row by row index + col index e.g. row 3 col 17
df.iloc[[3, 42]] # get n row by row index e.g. rows 3 and 42
```

FILTER
```python
df[df['entity_id'].isin(descendants['id'])]
df.query('entity_id in @descendants.id')
```
```txt
Let's break down how query() with the @ prefix works:

The query string 'entity_id in @descendants.id' is a pandas query expression
@ tells pandas to look for the variable in the Python namespace, outside the DataFrame
So @descendants.id refers to the id column/attribute of a descendants DataFrame/object that exists in your code

Without @, pandas would look for descendants.id inside the DataFrame you're querying. With @, it looks in the outer scope.
```

```python
# ITERATION https://stackoverflow.com/questions/16476924/how-to-iterate-over-rows-in-a-dataframe-in-pandas https://stackoverflow.com/questions/50267185/iterate-over-pandas-series don't iterate https://realpython.com/pandas-iterate-over-rows/
for series in df.iterrows():

# PREDICATE
df[df["company"] == "ABC corp"]  # equality
df[df["earnings"] > 0]  # comparison
df[(df["col1"] >= 1) & (df["col1"] <=1 )]  # uses indexing https://stackoverflow.com/a/13616382

# GROUPING 📙 McKinney [291]
for gk, grp in df.groupby("isrc"):

# CSV PER GROUP https://stackoverflow.com/a/50818244
df = pd.DataFrame(pd.read_csv("paintings.csv"))
path = os.path.join(os.getcwd(), "output_dir")
for i, (name, group) in enumerate(df.groupby("ARTIST")):
    group.to_csv("{}/{}.csv".format(path, name.replace(" ", "").lower()))

# VERIFY TOTALS PER GROUP
invalid = list()
for _, (foo, group) in enumerate(df.groupby("foo")):
    if int(group["bar"].sum()) != 100:
        invalid.append(foo)
log.info("foo count - invalid: {}".format(len(invalid)))

myl = [foo, bar]

# SHAPE https://stackoverflow.com/a/35523946
df.shape[0]  # count rows
df.shape[1]  # count col

# PERSIST FOO W/ VALID BAR
verified = df.drop(df.index[df.foo.isin(invalid)])
log.info("count - verified: {}".format(len(set(verified.foo))))
verified.to_csv(os.path.join(os.getcwd(), out_file))
```

## IO

BASIC
```python
df = pd.DataFrame(pd.read_csv(fpath))
get_sample(df, frac=0.1, random_state=42)  # reproducible 10% sample
df.to_csv(fpath, index=False)  # drop index
```

COLUMN SELECTION/CREATION
```python
# CHOOSE
pd.read_csv(fpath, usecols=['col1', 'col2', 'col3'])
# SET ORDER
df = df[['col1', 'col2', 'col3']]
# CREATE DERIVED, MV NAMES
df = (
    pd.read_csv()
    .assign(csn=lambda df: 'CS' + df['id'])
    .rename(columns={'manufacturer': 'mfg', 'manufacturer_part_number': 'mpn'})
)
```

TYPING
```python
# CASTING
pd.read_csv(fpath, dtype={'foo': str})
# DROP NULLS W/IN COL
pd.read_csv(fpath).dropna(subset=['foo'])
pd.read_csv(fpath, na_filter=True, subset=['foo'])
# DROP DUPES W/IN COL
drop_duplicates(subset=['foo'])
# DROP NULLS ACROSS COLS
df = pd.read_csv(fpath).dropna()
```

---

* failed attempt to get VS Code Jupyter extension stdout to be userful
```python
def rtbl(df, title="Debug Output"):
    """Render Pandas DataFrame as an HTML table using tabulate."""
    if df.empty:
        print(f"{title}: (Empty DataFrame)")
        return
    # Generate tabulate HTML table
    html_table = tabulate(df, headers="keys", tablefmt="html")
    # Wrap it inside a scrollable div for better display in Jupyter
    styled_table = f"""
    <div style="overflow-x: auto; max-width: 100%;">
        <h4 style="font-family: sans-serif;">{title}</h4>
        {html_table}
    </div>
    """
    display(HTML(styled_table))  # ✅ Ensures Jupyter renders it correctly

df = pd.DataFrame({"id": [1, 2], "name": ["Alice", "Bob"]})
rtbl(df, title="User Data")
```

# 🐻‍❄️ POLARS

📜 https://docs.pola.rs/ https://docs.pola.rs/api/python/stable/reference/index.html
📙 https://realpython.com/polars-python/


---

dealing with nulls https://realpython.com/polars-missing-data/
https://www.emilyriederer.com/post/py-rgo-2025/

BIG PICTURE
* query engine with dataframe frontend https://pola.rs/posts/polars_birds_eye_view/ https://blog.jetbrains.com/pycharm/2024/07/polars-vs-pandas/
* compared to Pandas: query optimization, group by https://labs.quansight.org/blog/dataframe-group-by https://pola.rs/posts/benchmarks/
* https://www.youtube.com/watch?v=q3o2IdFQTOE
* https://news.ycombinator.com/item?id=35429555
* better semantics than Pandas? https://arilamstein.com/blog/2024/09/04/why-im-switching-to-polars/
* https://calmcode.io/course/polars/introduction
* https://calmcode.io/course/pandas-pipe/introduction

INTEROP
* converting Pandas to Polars https://www.youtube.com/watch?v=B2Ljp2Fb-l0
* can use some Pandas libraries https://pythonspeed.com/articles/polars-pandas-interopability/

PRO / CON
* better than Pandas: query in Python or SQL, no dependencies, sensible pip install (vs. conda) https://github.com/pola-rs/polars better perf https://pola.rs/posts/benchmarks/ less memory usage https://pythonspeed.com/articles/polars-memory-pandas/
* worse than Pandas: not meant for Excel-like operations
> Pandas was originally written to replace excel in financial/econometric modeling, not as a replacement for sql. Models written solely in the long relational style are near unmaintainable for constantly evolving models with hundreds of data sources and thousands of interactions being developed and tuned by teams of analysts and engineers. https://news.ycombinator.com/item?id=35429555

ZA
* Deltabase, DeltaDB https://github.com/uname-n/deltabase https://pythonbytes.fm/episodes/show/397/so-many-pycon-videos
* plotting https://pola.rs/posts/lightweight_plotting/ https://realpython.com/python-news-october-2024/
> couldn't get this to work; try `pipx inject`

## IO

WRITE
* operations are immutable i.e. capture updates with assignment (`df = df.operations()`)
```python
# literal
df.with_columns(pl.lit('ALCO').alias('buyline'))

# interpolated and concatenated
df.with_columns((f'{prefix}' + pl.col('mpn').cast(str)).alias('sku'))

# interpolated - predicate
df.with_columns(
    pl.when(pl.col('sku').is_null())
    .then(f'{prefix}' + pl.col('mpn').cast(str))
    .otherwise(pl.col('sku'))
    .alias('sku')
)
```
* more type casting / coercion / interpolation
```python
# Polars cast() is equivalent to pandas astype()
# Int64 matches the target schema's type
# Safer than pl.col('id').str.to_int() which can fail on non-numeric strings

# String parsing
str.to_int(), str.to_float()
# Numeric casting
cast(pl.Int32), cast(pl.Float64)
#Type coercion
coalesce(), fill_null()
```

READ
* strategy pattern for `.read_csv|parquet|excel` (excel requires `fastexcel`)
```python
# get value of cell (errs if more than one value)
pdr_for_brand['sku-prefix'].item()

# read_csv faster when you can skip entire columns and save on overhead of setting up query plan
df = pl.read_csv(file, columns=['col1', 'col2'])

# scan_csv creates lazy df = build up ops before actually loading data = Polars can optimize query plan rather than executing ops sequentially 🗄️ `data/internals.md` query engine > query plan
df = pl.scan_csv(file)
   .filter(pl.col('col1') > 0)
   .select(['col1', 'col2'])
   .groupby('col1').agg(pl.col('col2').mean())
   .collect()

# get schema without loading the whole table
pl.scan_csv('data/catalog.csv', separator=',', infer_schema_length=100).collect_schema()

# stream for lower memory consumption 🗄️ `architecture.md`
for chunk in pl.read_csv("data.csv", rechunk=True).iter_chunks(size=10000):
    process_chunk(chunk)

# PRNG for reproducible sample 🗄️ `algos.md`
pl.scan_parquet("data.parquet").sample(n=1000, seed=42).collect()

# working around non-standard data
pl.read_csv(
    filepath,
    separator='\t',
    encoding='latin-1',
    skip_rows=42,
    ignore_errors=True,
    infer_schema_length=None,
    quote_char=None,
    truncate_ragged_lines=True,
)

# MALFORMATTED COLUMN HEADERS
no_whitespace_or_period_delimit = r"^[^\s.-]+$"
violations = [col for col in df.columns if bool(re.match(no_whitespace_or_period_delimit, col)) is False]
assert len(violations) > 0

# convert pandas
pl.from_pandas(df)

# skip null columns
null_col_to_skip = ['Alternate Part Number', 'GTIN', 'Lead Time (Days)']
df = pl.read_csv(path/to/data)
df.select([col for col in df.columns if col not in null_col_to_skip])

# drop bad columns
pl.read_csv('catalog.csv').drop(['', 'Unnamed: 0']).write_csv('catalog.csv')

# alias on read
pl.scan_csv('products.csv').select([
    pl.col('capp_stock_number').alias('csn'),
    pl.col('manufacturer_part_number').alias('mpn'),
]).collect()

# read TSV
df = pl.read_csv(
    'products.tsv',
    separator='\t',
    encoding='latin-1',
    infer_schema_length=None,
    quote_char=None,
    truncate_ragged_lines=True
)
```

## EDA

```python
df.drop_nulls(subset=['col1', 'col2'])  # drop nulls from col
```

---


```python
df.unique(subset=['csn', 'matched_product_id'])  # dedupe
df.columns
df.schema
df.schema.keys()
col_series = df["column_name"]
col_list = df["column_name"].to_list()

first_values = df['column_name'].head(5)
unique_values = df['column_name'].unique()

# col has empty values
series.is_null().any()
# any empty columns
null_col_df = [col for col in df.columns if df[col].null_count() == df.height]
assert bool(null_col_df) is True
# find null columns
df.filter(pl.col(COL).is_null())
# value not present in column
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == 0
# value present in every column record
assert df.filter(pl.col('b_line').str.to_lowercase().str.contains(query)).height == lines_set.height
```

## predicates

```python
# EQUALITY
bar.filter(pl.col('mfg') == 'samsung')
bar.filter(pl.col('mfg').str.to_lowercase() == brand.lower())  # case insensitive
# inequality
ecl.filter(pl.col('buyline') != pl.col('priceline'))
# COMPARISON
bar.filter(pl.col('price') > 300)

# CHAINED
bar.filter((pl.col('mfg') == 'samsung') & (pl.col('price') > 400))
ecl.filter(
    (pl.col('mfg') == 'Trerice') &
    (pl.col('buyline') != pl.col('priceline'))
)


# KEYWORD SEARCH
bar.filter(pl.col('mfg').str.contains('foo').alias('regex'))
# CASE INSENSITIVE
df.filter(pl.col('description').str.contains(fr'(?i){brand}')) # newer version of Polars has `flags` kwarg
```

## joins

---

```txt
Pandas by default uses left joins and handles the key matching differently - it maintains the left table's row count and only brings in matched columns from the right.
```


* multi
```python
res = (prod
.join(pc, on='id')  # add mfg
.join(entity, left_on='id', right_on='product_id') # add epn
.join(mars, left_on='pn', right_on='mfr_pn')  # match epn
)
```
```sql
from product join prod_class on product.id = prod_class.id
join entity on product.id = entity.product_id
join mars on entity.pn = mars.mfr_pn
```

```txt
Polars drops the right-side join key unless explicitly retained.
Since matched_product_id was only used for joining, it was removed.
Now, product_id is correctly preserved because we selected it explicitly in catalog.select([...]).

Polars follows these rules when handling columns with the same name in joins:

If on='id' is used, Polars keeps a single id column from the left table.
If left_on='id', right_on='id' is used, Polars renames the right-side column by appending _right.
If multiple tables have id but are joined differently, only the first id from the leftmost table survives unless explicitly selected.
```

how=left for left join

```python
# basic
foo.join(bar, left_on='id', right_on='mpn')

# predicate
foo.join(bar, left_on='id', right_on='mpn').filter(pl.col('foo_price') != pl.col('bar_price'))
foo.join(bar, left_on='id', right_on='mpn').filter(pl.col('manufacturer').is_in(['apple', 'motorola']))

# relative complement
bar.join(foo, left_on='mpn', right_on='id', how='anti')
```

---

🗄️ startup.py https://github.com/zachvalenta/capp-crud
```python
def smart_join(dt, tt, did, tid):
    """
    Some annoyances with Polars joins that this solves for me:
    * output doesn't locate with the join keys next to each other
    * output doesn't locate with the join keys next to each other

    :param dt: drive table
    :param tt: through table
    :param did: drive table ID
    :param tid: through table ID
    """
    joined = dt.join(tt.with_columns(pl.col(tid).alias('tid')), left_on=did, right_on=tid)
    joined.select(joined.columns[0], joined.columns[-1], *joined.columns[1:-1])
```

```python
foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc")
foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc").select(["sku", "bar_upc", "foo_price", "bar_price"])

joined = foo.join(bar.with_columns(pl.col("upc").alias("bar_upc")), left_on="sku", right_on="upc")
joined.select(joined.columns[0], joined.columns[-1], *joined.columns[1:-1])

select([
    "name",  # specify your desired column order
    "age",
    "id"
])

foo.join(df2, on="id").filter(pl.col("price") != pl.col("Sell Price"))
```

JOINS
```python
# BASIC
joined = capp.join(neuco, on="id", how="left")  # JK same name
joined = df1.join(df2, left_on="Part_ID", right_on="part_id")  # JK dif name

# RECONCILIATION
# 📍 update this to show what the price is
df1 = pl.DataFrame({"id": [1, 2, 3], "price": [100.0, 200.0, 300.0]})
df2 = pl.DataFrame({"id": [1, 2, 3], "price": [100.0, 250.0, 300.0]})
df1.join(df2, on="id").filter(pl.col("price") != pl.col("Sell Price"))

missing_records = capp.join(
    neuco,
    left_on=["Part_ID", "Product Item"],  # Join on both keys
    right_on=["part_id", "product_item"],
    how="left"
)

# only keeps join key from the driving table (as least in output)
df1 = pl.DataFrame({"Part_ID": [1, 2, 3], "name": ["a", "b", "c"]})
df2 = pl.DataFrame({"part_id": [1, 2, 4], "value": [10, 20, 30]})
joined = df1.join(df2, left_on="Part_ID", right_on="part_id")
# need to alias join key from through table to see it in output
joined = df1.join(df2.with_columns(pl.col("part_id").alias("df2_part_id")), left_on="Part_ID", right_on="part_id")

# trying to make it more clear in a join which attr belong to which table
df1_tagged = df1.select([pl.all().prefix("table1_")])
df2_tagged = df2.select([pl.all().prefix("table2_")])
joined = df1_tagged.join(df2_tagged, left_on="table1_Part_ID", right_on="table2_Part_ID") # adjust join key names to match prefixed names
```
