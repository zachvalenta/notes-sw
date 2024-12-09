# ⛩️

## 参考

📜 https://docs.python.org/dev/library/index.html
📙 Van Rossum ch. 10-11
📈 https://pythonwheels.com/
🔍 https://github.com/vinta/awesome-python

## 进步

* _24_: split from `python.md`

# 🤖 OS

📙 Beazley ch. 13

STDOUT
* `print()`: implicitly adds `\n` under the hood; workaround is `print('hello zv', end="")`
* `stderr.flush()`
> Python's standard out is buffered (meaning that it collects some of the data "written" to standard out before it writes it to the terminal). Calling sys.stdout.flush() forces it to "flush" the buffer, meaning that it will write everything in the buffer to the terminal, even if normally it would wait before doing so.

---

```python
# check Python version from script https://stackoverflow.com/a/1093331/6813490
sys.version

# mkdir in cwd
os.mkdir(os.path.join(os.getcwd(), dir_name))

# get filenames https://stackoverflow.com/a/50876889/6813490

#########

# env
os.environ  # get all
os.environ[]  # get 1 - throws err
os.environ.get()  # get 1 - no err
os.getenv("target", "default")  # get 1 - defaults if target not found

# misc
shutil.make_archive(root_dir=dir_to_tar, base_name=tarball_name, format='zip')  # make zip
tarballs = [os.base.pathname(x) for x in glob(f"{Path.cwd().joinpath('foo')}/*.tar.gz")] # grab file names sans full path https://stackoverflow.com/a/55439309/6813490 https://stackoverflow.com/a/20384686/6813490
```

* _exit code_: `sys.exit(0)` or `os._exit(0)` https://stackoverflow.com/a/49950466/6813490
* _create temp dir/file_: dir (`dir` here specifies location, not sure how to name) `tempfile.mkdtemp(dir='.')` put file in temp dir `tempfile.mkstemp(dir='mytempdir')`
* iterate
```python
with open('foo.txt') as f:
    for line in f.readlines():
        print(line)
```
* iterate and update https://stackoverflow.com/a/20593644/6813490
```python
import fileinput

with fileinput.FileInput(filename, inplace=True, backup='.bak') as file:
    for line in file:
        print(line.replace(text_to_search, replacement_text), end='')
```

## files

📙 Beazley ch. 5
https://www.fluentpython.com/lingo/#file-like_object

* _file obj_: obj exposing a file-oriented API (`read()`, `write()`) https://docs.python.org/dev/glossary.html#term-file-object
* aka file-like obj, stream
```python
f = open("hey.md")
# read flushes some sort of buffer
f.read()  # 'hey zjv\n'
f.read()  # ''

# seek https://calpaterson.com/s3.html https://docs.python.org/dev/library/io.html#io.TextIOWrapper.seek https://chatgpt.com/c/6709235d-dbf8-8004-a0bb-0a6c7ce5b7b6
```

CSV
```python
# READ
with open("input.csv", mode="r") as f:
    reader = csv.reader(f)
    for row in reader:
        pass

def load_csv(filename):
    """Load CSV file into a list of dictionaries"""
    records = []
    with open(filename, 'r') as f:
        reader = csv.DictReader(f)
        for row in reader:
            records.append(row)
    return records

# WRITE
with open("output.csv", mode="w") as f:
    writer = csv.writer(f)
    writer.writerow(["foo", "bar"])  # headers
    writer.writerows(myl)
```

---

```python
os.path.isfile(f)  # check if file
os.path.exists(f)  # check if file exists
os.listdir()  # list files in dir

open(path, mode).read()  # read - modes include w (write) r (read)
open('ur-file.txt', 'w').close()  # create empty
print(open(path, mode).read())  # print
open(path, mode).read().split(" ")  # tokenize https://stackoverflow.com/a/55723307/6813490
f.readline()   # first line https://stackoverflow.com/a/19044550

###
# CONTEXT MANAGER https://www.fluentpython.com/lingo/#context_manager https://www.pythonmorsels.com/creating-a-context-manager/ https://hamatti.org/posts/write-more-pythonic-code-with-context-managers/
# clean up unmanaged resources (like file streams)
# simple way to wrap a try/except/finally block in a reusable function https://tuckerchapman.com/til/python-context-manager/
# r (read; default) b (binary) w (create new) w+ (create new if doesn't exist https://stackoverflow.com/a/2967249
# BYO https://rednafi.github.io/digressions/python/2020/03/26/python-contextmanager.html
###
with open('data.txt', 'w') as f:
    data = 'some data to be written to the file'
    f.write(data)
```

* _zip/tar_: https://github.com/BuzonIO/zipfly
* DictWriter expects a list of dictionaries
```python
# ❌
artists_1371 = artists_1025 - artists_1124
with open("03-artists-1371.csv", "w") as csv_1371:
    writer = csv.DictWriter(csv_1371, fieldnames=["artist"])
    writer.writeheader()
    for el in foo:
        writer.writerow(el)
    
# ✅
artists_1371 = artists_1025 - artists_1124
artists = [dict(artist=x) for x in artists_1371]
with open("03-artists-1371.csv", "w") as csv_1371:
    writer = csv.DictWriter(csv_1371, fieldnames=["artist"])
    writer.writeheader()
    for el in artists:
        writer.writerow(el)

# ❌ how to write string to single header vs. iterate string across n headers?
with open("03-artists-1371.csv", "w") as csv_1371:
    writer = csv.writer(csv_1371)
    writer.writerow(["artist"])
    for el in artists_1371:
        print(type(el))
        writer.writerow(el)
        
# ✅ write list of strings
with open("um_only.csv", mode="w") as f:
    writer = csv.writer(f)
    writer.writerow(["isrc"])  # takes iterable
    for dl in um_only:
        writer.writerow([dl])  # takes iterable
```
* parse Click file
```python
def parse_click_file(f):
    return [
        {"foo": row["FOO"], "bar": row["BAR"], "baz": row["BAZ"]}
        for row in csv.DictReader(f)
    ]
```
* CSV
```python
# read
with open(file_path, mode="r", encoding="utf-8-sig") as f:
    reader = csv.DictReader(f)
    headers = reader.fieldnames
    for row in reader:
        do_something(row[header])

# write
with open(file_path, "w") as f: 
    headers = ["SKU", "name", "earnings"]
    writer = csv.DictWriter(f, fieldnames=headers) 
    writer.writeheader()
    for dl in data_lines:
        writer.writerow(dl)

# read from + write to
with open(file_path, "w") as csv_out: 
    with open(file_path, mode="r") as csv_in:
        reader = csv.DictReader(csv_in)
        writer = csv.DictWriter(csv_out, fieldnames=reader.headers + ["header_for_out"]) 
        writer.writeheader()
        for row in reader:
            data_line = OrderedDict(do_something(row))
            writer.writerow(data_line)

# write list of dict to file
with open(file_path, "w") as f: 
    headers = ["SKU", "name", "earnings"]
    writer = csv.DictWriter(f, fieldnames=headers) 
    writer.writeheader()
    for dl in data_lines:
        writer.writerow(dl)

# create output headers and link to input headers
def generate_headers(headers):
    headers_IO = od()
    for header in headers:
        if "TOTAL AMOUNT" in header:
            mmyy = "ta_{}".format("_".join(header.split(" ")[2:]).lower())
            headers_IO[mmyy] = header
    return headers_IO

# create output headers based on date range and link to input headers
def generate_headers(year, month, day):
    headers = od()
    month_start = dt.date(year, month, day)
    month_previous_dt = dt.datetime.utcnow().replace(day=1) - delta(days=1)
    month_previous = month_previous_dt.date()
    while month_start <= month_previous:
        k = "out_{}".format(month_start.strftime("%Y%m")[2:])
        v = "in {}".format(month_start.strftime("%b %Y").upper())
        headers[k] = v
        month_start += delta(months=1)
    return headers

# add generated headers to hard-coded
generated = generate_headers(reader.fieldnames)
writer = csv.DictWriter(csv_out, fieldnames=get_headers(generated=generated.keys()))
def get_headers(generated):
    return [
        "foo",
        "bar",
    ] + generated

# sum across generated headers
gen_rows, total = sum_gen(gen=generated, row=row)
def sum_gen(gen, row):
    total = 0
    rows = od()
    # k = output header, v = input header
    # e.g. "out_nov_21" : "IN NOV 21"
    for k, v in gen.items():
        # row = "id":"id", "IN NOV 21": "42", "IN DEC 21": "7"
        rows[k] = row[v]  # out_nov_21: 42
        if row[v] != "":
            total += float(row[v])
    return rows, round(total, 2)
```

* HTTP
```python
# write response
res = requests.get(url)
with open(file_name, mode="wb") as f:
    f.write(res.content)

# read IO https://stackoverflow.com/a/21843713
byte = io.BytesIO(res.content).read()
text = byte.decode("utf-8-sig")
string_obj = io.StringIO(text)
reader = csv.DictReader(string_obj)
for row in reader:
```

## pathlib

📜 https://docs.python.org/3/library/pathlib.html#correspondence-to-tools-in-the-os-module

* _path-like object_: https://docs.python.org/3/glossary.html#term-path-like-object

```python
# ACCESS
Path.cwd()
Path.cwd().parent
Path.cwd().parent / 'subdir'

# ASSERTIONS
Path.exists(Path.cwd())
Path.is_dir(Path.cwd() / 'sub1' / 'sub2')
Path.is_file(Path.cwd() / 'sub1' / 'sub2' / 'foo.csv')
```

---

https://realpython.com/python313-new-features/#improved-globbing-of-files-and-directories
* https://realpython.com/python-pathlib/
* https://treyhunner.com/2018/12/why-you-should-be-using-pathlib/
* https://treyhunner.com/2019/01/no-really-pathlib-is-great/

* _why path libs are useful_: avoid dealing with different directory delimiters per OS [Sweigart automate 8.174]
* _how to represent paths_: Python can represent paths as strings (like os) https://realpython.com/python-pathlib/#the-problem-with-python-file-path-handling but Pathlib doesn't https://snarky.ca/why-pathlib-path-doesn-t-inherit-from-str/ in Python 2 binary and textual data were implicitly compatible and that caused problems https://snarky.ca/why-pathlib-path-doesn-t-inherit-from-str/
* _Pathlib_: most functionality in `path`

```python
from pathlib import Path

cwd = Path.cwd()  # get cwd
file_names = [x.name for x in cwd.glob("**/*.csv")]  # get CSV filenames https://docs.python.org/3/library/pathlib.html#basic-use

# dir
Path.cwd()  # $CWD
Path.home()  # ~
os.listdir()  # ls

basepath = path.dirname(__file__)
austen = path.abspath(path.join(basepath, "..", "austen.json"))  # file from parent dir https://stackoverflow.com/a/4381638

austen = os.path.join(os.path.dirname(__file__), "austen.json")  # file from CWD - can occlude but flaky if open w/ just `open(file)`, although doesn't seem like it should be, maybe not a problem w/ pathlib https://stackoverflow.com/a/1315401 
with open(austen) as f:
    return json.load(f)

Path.cwd().joinpath('foo').mkdir()  # mkdir named 'foo'
Path.cwd().joinpath('foo').mkdir(exist_ok=True)  # mkdir - don't err out if already exists (won't overwrite, just won't do anything)
Path.cwd().joinpath('foo').mkdir(parents=True)  # mkdir - make all necessary subdirectories

Path.home().joinpath("Desktop").exists()  # check if dir exists
Path.home().joinpath("Desktop").joinpath("foo.txt").is_dir()  # check if file is dir
path_to_file.rename(path_to_new_location.joinpath('file-name-at-new-location.txt'))  # mv

Path.unlink(path_to_file)  # rm file
Path.rmdir(path_to_dir)  # rmdir - empty https://docs.python.org/3/library/pathlib.html#pathlib.Path.rmdir 
shutil.rmtree(path)  # rmdir - not empty https://stackoverflow.com/a/303225/6813490 https://stackoverflow.com/a/25172642/6813490
```

shutil is good now https://www.bitecode.dev/p/python-313-what-didnt-make-the-headlines

## process exec

🔗 https://martinheinz.dev/blog/98
🗄️ `infra.md` IaC / remote execution

OPTIONS
* `os.system`
* `subprocess`
* _sh_: https://github.com/amoffat/sh https://martinheinz.dev/blog/96
* _suby_: https://github.com/pomponchik/suby
* _Sultan_: https://github.com/aeroxis/sultan https://stackoverflow.com/a/56842257/6813490

# 💻 UI

🗄
* `golang.md` CLI
* `shell.md` design

GUI
* _Gooey_: https://github.com/chriskiehl/Gooey
* _Kivy_: https://github.com/kivy/kivy
* _pyautogui_: control mouse/keyboard https://github.com/asweigart/pyautogui
* _pyqt_: https://build-system.fman.io/pyqt5-tutorial
* _PySimpleGUI_:  https://github.com/PySimpleGUI/PySimpleGUI
* _tkinter_: https://www.youtube.com/watch?v=xqDonHEYPgA

## CLI (Click)

📜 https://click.palletsprojects.com/en/8.1.x

* `python script.py`
```python
#!/usr/bin/env python
import click

@click.command()
def main():
    print("hello world")

if __name__ == "__main__":
    main()
```

command + arg
```python
# run: python script.py hello alice

@click.group()
def cli():
    pass

@cli.command()
@click.argument("person")
def hello(person):
    print(f"hi, {person}")

@cli.command()
@click.argument("person")
def goodbye(person):
    print(f"goodbye, {person}")
```

---

* port Click app to TUI https://github.com/Textualize/trogon

ALTERNATIVES
* `sys.argv`
* optparse
* docopt
* https://github.com/tiangolo/typer https://rahulpai.co.uk/smart-clis-with-typer.html
* interactive https://github.com/Aperocky/replbuilder
* Rust https://saadmk11.github.io/blog/posts/build-python-cli-tool-with-rust/
* CLI from obj: https://github.com/google/python-fire https://github.com/chriskiehl/Gooey https://github.com/BstLabs/py-dynacli

INTERPRETER / SHEBANG
```sh
# https://realpython.com/run-python-scripts/#using-the-script-filename
#!/usr/bin/python --> explicit path
#!/usr/bin/env python --> use whatever python on $PATH
```

ARGPARSE
* rich for output https://github.com/hamdanal/rich-argparse
* testing: https://github.com/dbader/photosorter/blob/master/test_sorter.py https://www.youtube.com/watch?v=ApTZib0L2X8 4:00
* `description`: one-liner on purpose of CLI http://dustinrcollins.com/testing-python-command-line-apps
* `action=store_true`: boolean https://stackoverflow.com/a/15008806/6813490 https://stackoverflow.com/a/36710639/6813490
* `metavar=''`: avoid weird upppercasing https://docs.python.org/3/library/argparse.html#metavar
* scaffold
```python
def parse():
    parser = ArgumentParser()
    parser.add_argument("-f", "--file", help="file")
    parser.add_argument("-s", "--start", help="start trim")
    parser.add_argument("-e", "--end", help="end trim")
    if len(argv) == 1:
        parser.print_help()
        exit()
    return parser.parse_args()

args = parse()
main(file=args.file, start=args.start, end=args.end)
```

MORE CLICK
* args vs. options https://click.palletsprojects.com/en/8.1.x/parameters/
* types: str, int https://click.palletsprojects.com/en/8.1.x/parameters/#parameter-types
> I'm not using these semantically, using options in lieu of args bc options have better syntax on command invocation
```python
# ARGS: python path/to/script.py path/to/file
@click.command()
@click.argument("in-file", type=click.Path(exists=True))
def main(in_file):
    """input file"""  # https://click.palletsprojects.com/en/8.1.x/documentation/

# OPTIONS: python path/to/script.py -in-file path/to/file
@click.command()
@click.option("-in-file", required=True, type=str, help="input file")
def main(in_file):
```
* read from anywhere, write to local dir
```python
# run: python script.py -in_path path/to/file.txt -out_file new_file.txt
@click.command()
@click.option("-in_path", required=True, type=str, help="path to input file")
@click.option("-out_file", required=True, type=str, help="output filename")
def main(in_path, out_file):
    path_input = os.path.normpath(in_path)
    path_output = os.path.join(os.getcwd(), out_file)
    with open(path_output, mode="w") as csv_out:
        with open(path_input, mode="r") as csv_in:
```

## IO (rich)

RICH 📜 https://github.com/Textualize/rich https://github.com/zachvalenta/dotfiles-mini23/blob/main/python/python_startup.py
* html https://github.com/willmcgugan/willmcgugan/blob/master/willmcgugan.py
* to try: repr for obj https://rich.readthedocs.io/en/latest/pretty.html#rich-repr-protocol
https://rich.readthedocs.io/en/latest/introduction.html#ipython-extension
```python
from rich import print as rp  # print
from rich import pretty; pretty.install()  # default to Rich print in REPL
from rich import inspect
inspect(superhero, methods=True)  # more limited version of stdlib inspect

# EXCEPTIONS
from rich.console import Console
console = Console()
from rich.traceback import install
install(show_locals=True)

raise RuntimeError("hey there")  # normal output (contra examples)?

try:  # Rich output
    do_something()
except Exception:
    console.print_exception(show_locals=True)
```

INPUT 🗄 `security.md` sanitization
```python
ur_in = input()
```
* Textual https://github.com/darrenburns/textual-autocomplete
* _bullet_: https://github.com/Mckinsey666/bullet Golang alternative https://github.com/charmbracelet/huh
* repos https://github.com/zachvalenta/news https://github.com/zachvalenta/capp-prod-cat/blob/link-nodes/tree_viz.py 🗄️ `git.md` Github / search
* control flow https://github.com/shkey/killurp/blob/141d411d353ab46edf362ff6a33bfe9c5a5ad211/killurp.py#L8 https://github.com/chroma-core/chroma-migrate/blob/2a6e61ee7f2d717281075512b308c40616033189/chroma_migrate/cli.py#L2
* _questionary_: https://github.com/tmbo/questionary 
* _prompt-toolkit_: used by pgcli, http-prompt https://github.com/j-bennet/wharfee/blob/master/setup.py https://github.com/wasi-master/fastero

OUTPUT
* animation 🎯 https://github.com/ChrisBuilds/terminaltexteffects https://realpython.com/python-rich-package/
* colors https://github.com/timofurrer/colorful https://github.com/erikrose/blessings
* syntax highlighting https://github.com/pygments/pygments
* tables https://github.com/astanin/python-tabulate https://realpython.com/python-rich-package/

## TUI (Textual)

🗄️
* `ml.md` clients > Elia
* `os/tools.md` browsr

HOWTO
* debug https://www.pythonpapers.com/p/how-to-debug-your-textual-application
* publish to web https://github.com/Textualize/textual-web
* file tree https://github.com/willmcgugan/terminal-tree
* run examples
```sh
python -m pip install --user textual
cd /Users/zvalenta/Desktop/textual/examples
python json_tree.py
```

ALTERNATIVES
> Textual inherently slow? Both browsr and elia crawl on open. Find Golang-like alternative
> prefer the way Golang/Rust TUI libs look (gocui, ratatui) https://github.com/charmbracelet/bubbles
* _blessed_: https://github.com/jquast/blessed
* _asciimatics_: https://github.com/peterbrittain/asciimatics
* _urwid_: used by pudb, Zulip http://urwid.org/ https://github.com/zulip/zulip-terminal/blob/main/zulipterminal/ui_tools/boxes.py
* _pytermgui_: https://github.com/bczsalba/pytermgui

PROJECTS THAT USE
* https://github.com/thetacom/hexabyte

---

* close to CSS, Tailwind https://calmcode.io/labs/tuilwind-css
* https://realpython.com/contact-book-python-textual/
* functionality: tables, color, layout
* _Textual_: complaints https://news.ycombinator.com/item?id=35123383 animation https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#demonstrating-animation dropdown https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#dropdown-autocompletion-menu file manager https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#a-file-manager-powered-by-textual graphics https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#pixel-art layout https://textual.textualize.io/blog/2022/12/11/version-060/#placeholder tabs https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#tabs-with-animated-underline testing https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#developer-console https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#snapshot-testing-for-terminal-apps example https://github.com/learnbyexample/TUI-apps/tree/main/CLI-Exercises https://www.blog.pythonlibrary.org/2024/02/06/creating-a-modal-dialog-for-your-tuis-in-textual/

# 🕸️ WEB

📙 Beazley ch. 11

## HTTP (requests)

📜 https://requests.readthedocs.io/en/latest/

* alternatives: https://www.speakeasy.com/post/python-http-clients-requests-vs-httpx-vs-aiohttp https://github.com/search?utf8=%E2%9C%93&q=aiohttp https://github.com/encode/httpx single-file https://github.com/slingamn/mureq https://github.com/jawah/niquests
```python
# data = dict(form), json.dumps(string) https://stackoverflow.com/a/42121407 https://requests.readthedocs.io/en/latest/api/#requests.request
# json = dict(json) https://requests.readthedocs.io/en/latest/user/quickstart https://stackoverflow.com/a/26344315
res = requests.post(url, data=data)
res.raise_for_status()  # raise exception for 400/500 https://requests.readthedocs.io/en/master/user/quickstart/#json-response-content
```
* mock requests https://github.com/jamielennox/requests-mock
* file download https://realpython.com/python-download-file-from-url/
* timeouts https://findwork.dev/blog/advanced-usage-python-requests-timeouts-retries-hooks/ https://robertovitillo.com/default-timeouts/
```python
# BASICS
requests.get(url)
requests.post(url, data=data)
requests.put(url, data=data)

# VIEW RES
res =requests.get("https://httpstat.us/502")
res.text
res.url

# DOWNLOAD FILE
with open("tmp.text", "wb") as f:
    f.write(res.content)

# DOWNLOAD FILE WITH AUTH TOKEN https://stackoverflow.com/a/44699717
res = requests.get(
    'https://gitlab.com/zachvalenta/pre-commit-test/repository/archive.tar.gz?ref=master',
    headers={'PRIVATE-TOKEN': 'urPrivateToken'}
)
if res.url == "https://gitlab.com/users/sign_in":
    print("set token")
    os._exit(0)
with open(r'zjv_test.tar.gz', 'wb') as f:
    f.write(res.content)

# UPLOAD FILE https://2.python-requests.org/en/master/user/quickstart/#post-a-multipart-encoded-file https://2.python-requests.org/en/master/user/advanced/#post-multiple-multipart-encoded-files
my_file = {"file": open("foo.txt", "rb")}  # idk if 'file' significant here
requests.post(url, files=my_file)  # PUT also works fine

# RM FILE
res = requests.delete(url, auth=(user, pw))
```

## scraping

🗄 `html-css.md`

aaS
> have to use headless browser for SPAs? https://github.com/zackproser/pageripper-v2 https://zackproser.com/blog/api-cicd-pulumi-github
* _ScrapingBee_: https://www.scrapingbee.com/
* _Zenrows_: https://www.zenrows.com/solutions/scraper-api

LIBS
* _katana_: https://github.com/projectdiscovery/katana
* _scrapling_: https://github.com/D4Vinci/Scrapling

---

in golang 17k sites in 10 mins https://medium.com/@tonywangcn/27-6-of-the-top-10-million-sites-are-dead-6bc7805efa85
* Instant Data Scraper https://news.ycombinator.com/item?id=34069680
https://github.com/blacknon/pydork

https://github.com/MechanicalSoup/MechanicalSoup
* follow redirects
* follow links
* submit forms

BeautifulSoup 📜 https://www.crummy.com/software/BeautifulSoup/bs4/doc/
* parse HTML
* can also do scraping
* way to simulate an API for a site that doesn't have one
* install: `pip install beautifulsoup4`
* ampersand issue https://stackoverflow.com/a/7188419/6813490
```python
# insert: add element inside of another element https://www.crummy.com/software/BeautifulSoup/bs4/doc/#insert
div.insert(1, ul)

# https://www.crummy.com/software/BeautifulSoup/bs4/doc/#append
# https://www.crummy.com/software/BeautifulSoup/bs4/doc/#extend
# CSS https://stackoverflow.com/a/53635461
# add at end https://stackoverflow.com/a/4320313/6813490
```

scrape
* _scrape_: 
* Scrapy
* table data https://www.visidata.org/blog/2020/ten/#4-scrape-html-table-data-from-a-webpage
* _Git scraping_: version control your scrapes https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 16:15
* _crawlee_: https://github.com/apify/crawlee

parse
* BeautifulSoup
* filter on selector like jq https://github.com/mgdm/htmlq
* summary data https://github.com/buriy/python-readability

* pup https://github.com/ericchiang/pup https://sequoia.makes.software/parsing-json-at-the-cli-a-practical-introduction-to-jq-and-more/

---

https://news.ycombinator.com/item?id=40033490
https://datasette.io/tools/shot-scraper
* _crawler_: recursively navigates pages via links e.g. GoogleBot, BingBot https://www.interviewcake.com/question/python3/compress-url-list https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html
> Crucially, I would not have it crawling the entire web from the outset. Instead, it should crawl a whitelist of domains, or “tier 1” domains. These would be the limited mainly to authoritative or high-quality sources for their respective specializations, and would be weighed upwards in search results. Pages that these sites link to would be crawled as well, and given tier 2 status, recursively up to an arbitrary N tiers. https://drewdevault.com/2020/11/17/Better-than-DuckDuckGo.html
> A significant portion of the web is cut off from you if your crawler is not famous. Google has a huge competitive advantage in this regard, a lot of site owners allow just GoogleBot (and maybe BingBot), making it an extremely tedious process for an unknown crawler to get whitelisted on these sites. https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html
> We were told that this would take between 1 and 2 years to complete, and would cost a minimum of $1 billion (Again, this was 2013!). Needless to say, this was not a very enticing proposition. https://0x65.dev/blog/2019-12-05/a-new-search-engine.html
https://news.ycombinator.com/item?id=39810378
https://github.com/geziyor/geziyor

muffet
```sh
$ muffet http://zachvalenta.com/

http://www.zachvalenta.com/about.html
	403	https://stackoverflow.com/users/6813490/zach-valenta
fhttp://www.zachvalenta.com/blog-hiring.html
	404 (following redirect https://jobs.x-team.com/finished)	https://join.x-team.com/finished
	503	https://news.ycombinator.com/item?id=12262405
	error when reading response headers: small read buffer. Increase ReadBufferSize. Buffer size=4096, contents: "HTTP/1.1 200 OK\r\nDate: Fri, 10 Feb 2023 21:12:45 GMT\r\nPerf: 7626143928\r\nExpiry: Tue, 31 Mar 1981 05:00:00 GMT\r\nPragma: no-cache\r\nServer: tsa_b\r\nSet-Cookie: guest_id_marketing=v1%3A167606356583841901; "..."ww.gstatic.com/recaptcha/ https://client-api.arkoselabs.com/ https://www.google-analytics.com https://twitter.com https://app.link https://accounts.google.com/gsi/client https://appleid.cdn-apple.com/"	https://twitter.com/patio11/status/936619640012226560
http://www.zachvalenta.com/1988-norman-design-of-everyday-things.html
	403	https://www.blinkist.com/en/
http://www.zachvalenta.com/1996-fielding-bridget-jones.html
	404	https://www.zachvalenta.com/notes/1811-austen-sense-sensibility.html
```

* https://pythonbytes.fm/episodes/show/319/css-style-queries-for...-json
* change detection! https://github.com/dgtlmoon/changedetection.io
* Instant Data Scraper https://news.ycombinator.com/item?id=34069680
* sessions, cookies https://github.com/MechanicalSoup/MechanicalSoup
* _shot-scraper_: automated screenshots https://github.com/simonw/shot-scraper
🔗 https://realpython.com/python-web-scraping-practical-introduction/

* _scale_: Scraping Hub https://blog.scrapinghub.com/web-scraping-at-scale-lessons-learned-scraping-100-billion-products-pages
* _legal_: anti-bot counter measures to actual legal hot water ('crawling' is the preferre nomenclature, 'scraping' has a bad rep)  https://benbernardblog.com/web-scraping-and-crawling-are-perfectly-legal-right/

alternatives
* https://github.com/jamesturk/spatula
* https://github.com/codelucas/newspaper/ https://www.pythonpodcast.com/newspaper-data-extraction-episode-280/ https://github.com/maxhumber/gazpacho https://github.com/howie6879/aspider https://github.com/MontFerret/ferret

Scrapy
* _Scrapy_: framework, not lib 🗄 `language.md` req are async
* _scraper_: portion of data (for some other use); small data sets
* _crawler_: all the data (to index as is); big data sets
* _spider_: impl; how your want to scrape site; different types https://blog.scrapinghub.com/web-scraping-at-scale-lessons-learned-scraping-100-billion-products-pages

* help: `scrapy`
* init project: `scrapy startproject foo` -> has same gotcha as Flask!
* run - REPL: `scrapy shell`
* run - script: `scrapy crawl <spider_name>` (from dir holding `scrapy.cfg)
* make request: `fetch(<URL>)`
* select DOM element from response: `response.css('<selector>')`
* extract text from DOM element: `response.css('<selector>').extract()`
* rm tags: `from w3lib.html import remove_tags` 🔗 https://stackoverflow.com/a/33309310/6813490
* rm newline: `.replace('\n', '')` 🔗 https://stackoverflow.com/a/1249740
* to break through lifecyle https://stackoverflow.com/a/35871117/6813490 https://stackoverflow.com/a/7969243/6813490

Selenium
* other browser automation tool https://github.com/checkly/headless-recorder
* why? dynamic content https://stackoverflow.com/questions/6682503/click-a-button-in-scrapy https://stackoverflow.com/questions/17975471/selenium-with-scrapy-for-dynamic-page https://stackoverflow.com/questions/30345623/scraping-dynamic-content-using-python-scrapy
* Firefox driver https://github.com/mozilla/geckodriver/releases
* find binary https://stackoverflow.com/a/40208762/6813490 https://stackoverflow.com/a/22130211/6813490
* docs https://selenium-python.readthedocs.io/waits.html https://www.seleniumhq.org/docs/
* inspect autocomplete https://stackoverflow.com/q/34911553/6813490
* cannot select el by text https://stackoverflow.com/q/1520429
* `By.CSS_SELECTOR` https://stackoverflow.com/a/40708217
* dropdown not inspectable in dev tools https://stackoverflow.com/questions/34911553/not-able-to-inspect-debug-autocomplete-option-elements
* finding binary https://stackoverflow.com/a/22130211/6813490
* tutorial https://intoli.com/blog/running-selenium-with-headless-chrome/

## serde

📙 Beazley ch. 6
🗄
* `protocols.md` serde
* `svc/django.md` DRF

ALTERNATIVES
* dataclasses
* _jiter_: 🎯 written in Rust by works with Python objs https://github.com/pydantic/jiter https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python
* _msgspec_: 🎯 https://github.com/jcrist/msgspec 🗄️ pydantic
* _orjson_: https://github.com/ijl/orjson
* _pickle_: ❌  https://docs.python.org/3/library/persistence.html no one uses any more https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html
* _pydantic_: https://docs.pydantic.dev/latest/concepts/serialization/ https://news.ycombinator.com/item?id=14477434

### JSON

📜 https://docs.python.org/3/library/json.html
🛠️ flatten https://github.com/simonw/json-flatten

BASICS
* dump = ser, load = de 
* singular for file write, plural for string
```python
# SER
import json
data = {"name": "Alice", "age": 42}
json.dumps(data)  # as string '{"name": "Alice", "age": 42}'
with open("data.json", "w") as f:
    json.dump(data, f)  # file write

# DE
with open("data.json", "r") as f:
    data = json.load(f)  # file load
data = json.loads('{"name": "Alice", "age": 42}')  # as dict
```

FMT
```sh
# in file https://orbifold.xyz/check-in-json.html
# ❓ should be able to do this aside from CLI, right?
python -m json.tool myfile.json > myfile.json.formatted
```
```python
# stdout
print(json.dumps(item, indent=4, sort_keys=True))  # only works when keys are primitives https://stackoverflow.com/a/47007417 https://stackoverflow.com/a/55179673
```

### Marshmallow

📜 https://marshmallow.readthedocs.io/en/stable/

* _1-M_: https://stackoverflow.com/a/37802227/6813490 https://stackoverflow.com/a/44511616/6813490 https://marshmallow.readthedocs.io/en/latest/nesting.html 
* _filter nested_: https://stackoverflow.com/q/57851811/6813490
* _sink_: https://www.kimsereylam.com/python/2019/10/25/serialization-with-marshmallow.html https://www.pythonpodcast.com/marshmallow-data-validation-episode-200/

* _alternatives_: https://news.ycombinator.com/item?id=14477434 stdlib https://news.ycombinator.com/item?id=14477434

libs for Flask
* _1 - Marshmallow_: base library https://github.com/marshmallow-code/marshmallow
* _2 - Marshmallow-SQLAlchemy_: lib for SQLAlchemy https://github.com/marshmallow-code/marshmallow-sqlalchemy
* _3 - Flask-Marshmallow_: lib for Flask-SQLAlchemy https://github.com/marshmallow-code/flask-marshmallow
> ❓ need both 2 and 3 to work w/ Flask https://www.youtube.com/watch?v=kRNXKzfYrPU 7:00 or just base lib? https://marshmallow.readthedocs.io/en/2.x-line/examples.html#quotes-api-flask-sqlalchemy

* Flask how to
```python
# CONNECT TO MODELS
# declaration must come after model https://stackoverflow.com/questions/59455520/flask-sqlalchemy-marshmallow-error-on-relationship-one-to-many
class Artist(db.Model):
    artist_id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(30))
    songs = db.relationship("Song", backref="artist")

    def __repr__(self):
        return f"id {self.artist_id} name {self.name}"

class ArtistSchema(ma.ModelSchema):
    class Meta:
        model = Artist

# nested
class SongSchema(ma.ModelSchema):
    class Meta:
        model = Song

    artist = ma.Nested(ArtistSchema)

# INIT
# Flask-SQLAlchemy before Flask-Marshmallow https://flask-marshmallow.readthedocs.io/en/latest/
db = SQLAlchemy(app)
ma = Marshmallow(app)

# SERIALIZE
# initialization must be <model>_schema
artist_schema = ArtistSchema()  # 1
artist_schema = ArtistSchema(many=True)  # n
artist_schema = ArtistSchema(only=("name", "songs"))  # subset

# DESERIALIZE https://marshmallow.readthedocs.io/en/3.0/quickstart.html#deserializing-objects-loading
# validate https://www.cameronmacleod.com/blog/better-validation-flask-marshmallow https://medium.com/bitproject/recently-i-created-a-restful-api-with-flask-where-my-models-had-many-parameters-75da1db870b7
```

## SGI

🗄️
* `application.md` utils
* `infra.md` web servers
🛠️ debug HTTP requests https://github.com/cle-b/httpdbg

WSGI
* interface btw app server and framework bc pre-WSGI which framework you picked determined which web server you could use https://www.pythonpodcast.com/episode-43-wsgi-2/ [8:00]
> The Web Server Gateway Interface (or "WSGI" for short) is a standard interface between web servers and Python web application frameworks. By standardizing behavior and communication between web servers and Python web frameworks, WSGI makes it possible to write portable Python web code that can be deployed in any WSGI-compliant web server. WSGI is documented in PEP 3333. https://docs.python-guide.org/scenarios/web/#wsgi
* _interface_: contract e.g. "app server will do these things in this way as specified by WSGI and app framework will hook into them in this way as specified by WSGI and that way gunicorn will work with any WSGI-compliant app framework and Flask will work with any-WSGI compliant app server"
* _constraints_: single-threaded https://stackoverflow.com/a/32217701 doesn't do async or WebSockets https://pythonbytes.fm/episodes/show/48/garbage-collection-and-memory-management-in-python https://www.pythonpodcast.com/episode-43-wsgi-2/ @ 18:00
* _supported by_: servers (gunicorn, uWSGI, mod_wsgi) frameworks (Flask, Django, Falcon, Pyramid)
* https://stackoverflow.com/a/38685758/6813490 https://talkpython.fm/episodes/show/13/flask-web-framework-and-much-much-more @ 30:00 https://djangodeconstructed.com/2018/02/15/how-a-request-becomes-a-response-diving-deeper-into-wsgi

ASGI
* _ASGI_: async alternative to WSGI
* frameworks: Django (Channels) Quart (Flask on async) https://talkpython.fm/blog/posts/talk-python-rewritten-in-quart-async-flask/ Twisted (don't think actually ASGI but does async) new (Sanic, Starlette, FastAPI built on Starlette)
* servers: uvicorn, Daphne
* FastAPI https://github.com/pomponchik/cbfa
* sink: https://www.youtube.com/watch?v=7kwnjoAJ2HQ @ 10:55 Django moving this way https://docs.djangoproject.com/en/dev/releases/3.0/ async db https://github.com/encode/orm https://github.com/django/asgiref https://www.pythonpodcast.com/django-channels-and-the-asynchronous-web-with-andrew-godwin-episode-180/ https://github.com/florimondmanca/awesome-asgi  https://pythonbytes.fm/episodes/show/148/the-asgi-revolution-is-upon-us

RSGI
* _RSGI_: for Rust https://github.com/emmett-framework/granian/blob/master/docs/spec/RSGI.md 🗄️ `infra.md` granian

# 🟨 ZA

* auth: https://authlib.org/
* config/env var: https://github.com/theskumar/python-dotenv https://github.com/sloria/environs https://github.com/facebookresearch/hydra https://rednafi.github.io/digressions/python/2020/06/03/python-configs.html less popular cousin https://github.com/sloria/environs
```python
import os
from dotenv import load_dotenv, find_dotenv
load_dotenv(find_dotenv())  # if `.env` present in project
os.getenv("FOO_VAR")
```
* cron / scheduling / daemon: https://github.com/zachvalenta/pypub https://github.com/maxhumber/hickory https://docs.python.org/3/library/sched.html https://github.com/dbader/schedule https://github.com/dbader/schedule https://schedule.readthedocs.io/en/stable/faq.html#how-to-continuously-run-the-scheduler-without-blocking-the-main-thread https://towardsdatascience.com/scheduling-all-kinds-of-recurring-jobs-with-python-b8784c74d5dc
* URL: urllib, urlparse https://github.com/gruns/furl
* validation (email, IP address) https://martinheinz.dev/blog/96

---

* `eval()`: take string and evaluate as if expression from language

* rise of 3rd-party packages, dead batteries http://pyfound.blogspot.com/2019/05/amber-brown-batteries-included-but.html https://www.python.org/dev/peps/pep-0594/ provisional API https://docs.python.org/3/glossary.html#term-provisional-API PEP 594 https://conroy.org/breaking-python-packages

* _hashing_: passlib https://passlib.readthedocs.io/en/stable/ https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis passlib is bad now? https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek
```python
# https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis
import hashlib as hl
sha = hl.sha256()
sha.update(b'hey')
sha.hexdigest()  # 'fa690b82061edfd2852629aeba8a8977b57e40fcb77d1a7a28b26cba62591204'
```
* _markdown_: https://pypi.org/project/markdown2/ used this one for `m2h` https://github.com/Python-Markdown/markdown had issues with ampersands in URLs, see repo commit `43e` https://stackoverflow.com/a/20593644/6813490 https://stackoverflow.com/questions/39086/search-and-replace-a-line-in-a-file-in-python
* _networking_: Scapy https://www.youtube.com/watch?v=EnuF9ZR6MVc psutil https://matt.sh/netmatt#_what-if-we-replaced-90s-c-netstat-with-python
* _notifications_: https://github.com/notifiers/notifiers https://ntfy.sh/ https://www.phillylinux.org/talks.html
* _photos_: https://github.com/sedthh/pyxelate 
* _PDF_: https://realpython.com/pdf-python/ https://github.com/Halolegend94/pdf4py

## datetime

🗄️ `application.md` NTP
🛠️ https://github.com/python-humanize/humanize

```python
from datetime import datetime
print(f"today's date is {datetime.now().strftime('%y%m%d')}")  ## YYMMDD
```
* _pdd_: ✅ diff https://github.com/jarun/pdd
```sh
pdd 0 0 60 --add  # 60 days from today
```

---

* great Golang library, parser https://github.com/olebedev/when
* holidays https://github.com/GothenburgBitFactory/holidata
https://realpython.com/python-packages/#dateutil-for-working-with-dates-and-times
https://drewdevault.com/2014/06/28/Python-datetime-sucks.html
📙 Beazley ch. 3
https://pypi.org/project/pytz/ https://blog.ganssle.io/articles/2018/03/pytz-fastest-footgun.html https://github.com/crsmithdev/arrow https://github.com/timofurrer/maya https://github.com/sdispater/pendulum https://github.com/dateutil/dateutil parser https://github.com/wanasit/chrono

* mock with freezegun https://martinheinz.dev/blog/96
* str fmt: `dt.now().strftime("%y.%m.%d-%H:%M:%S")` https://stackoverflow.com/a/51262245
* get last day of month https://stackoverflow.com/a/43663/6813490
* distance btw 2 dates
```python
from datetime import datetime as dt
abs((dt.strptime("2021-09-09", "%Y-%m-%d") - dt.strptime("2023-01-06", "%Y-%m-%d")).days)
abs((dt.strptime("2023-01-01", "%Y-%m-%d") - dt.today()).days)
>>>
```
* string to datetime https://stackoverflow.com/a/27914405
```python
from datetime import datetime as dt
dt.strptime("22-05", '%y-%m')
dt.strptime("05-22", '%m-%y')
dt.strptime("2022-May", '%Y-%b')
dt.strptime("20220501", '%Y%m%d')
```

```python
# iterate months in range https://stackoverflow.com/a/35651063
import datetime as dt
from dateutil.relativedelta import relativedelta as delta
def iter_months(year, month, day):
    month_start = dt.date(year, month, day)
    month_previous_dt = dt.datetime.utcnow().replace(day=1) - delta(days=1)
    month_previous = month_previous_dt.date()
    while month_start <= month_previous:
        do_something()
        month_start += delta(months=1)

# string to date
nov_2019 = dt.strptime("2019 Nov", "%Y %b")  # datetime.datetime(2019, 11, 1, 0, 0)
nov_2019.strftime("%Y %m")  # "22 03"

datetime.date(2021, 12, 1).strftime("%b %Y").upper()

month_start = "2019 11"
month_end = dt.now().strftime("%Y %m")  # "22 03"

start = dt.date(2019,11,1)
end = dt.now()

# create timestamp
from datetime import datetime as dt
dt.now().isoformat()
ts = int(dt.timestamp(dt.today()))
import time
ts = int(time.time())

# timestamp to Python https://docs.python.org/3/library/datetime.html#datetime.date.fromtimestamp
dt.date.fromtimestamp(ts)
date.fromisoformat('2019-12-04')  # not in 2.7

# formatting https://strftime.org/ https://stackoverflow.com/a/48947064
this_month = dt.now().strftime('%m')

# pad string https://stackoverflow.com/a/339024
last_month = str(int(this_month) - 1).rjust(2, '0')
two_months_ago = str(int(this_month) - 2).rjust(2, '0')

# compare timestamp to current time
# timezones + currency https://github.com/pycountry/pycountry
from datetime import datetime, timezone
now = datetime.now(timezone.utc)  # https://stackoverflow.com/a/25662061

from dateutil import parser
task = parser.isoparse("2021-06-04T18:10:19.885484Z")
# datetime.datetime(2021, 6, 4, 18, 10, 19, 885484, tzinfo=tzutc())

diff = now - task
diff.seconds
```

## git

📜 https://gitpython.readthedocs.io/en/stable/tutorial.html https://github.com/gitpython-developers/GitPython

https://github.com/jelmer/dulwich

```python
# clone https://stackoverflow.com/a/41252521 https://stackoverflow.com/a/34424094
# clone_from https://github.com/search?q=clone_from+gitpython&type=Code https://gitpython.readthedocs.io/en/stable/reference.html#git.repo.base.Repo.clone_from
from pathlib import Path
from git import Git, Repo

# download repo as tarball
res = requests.get(
    'https://gitlab.com/zachvalenta/pre-commit-test/repository/archive.tar.gz?ref=master',
    headers={'PRIVATE-TOKEN': access_token}
)
if res.url == "https://gitlab.com/users/sign_in":
    print("set token")
    os._exit(0)
with open(r'zjv_test.tar.gz', 'wb') as f:
    f.write(res.content)

# ssh
path = Path.cwd().joinpath('cloned-repo')
path.mkdir(exist_ok=True)
pk = Path.home().joinpath('.ssh/id_rsa')
with Git().custom_environment(GIT_SSH_COMMAND=f"ssh -i {pk}"):
    Repo.clone_from(
        url='git@github.com:zachvalenta/flask-CRUD.git', 
        branch='master',
        to_path=path, 
    )

# access token
path = Path.cwd().joinpath('cloned-repo')
path.mkdir(exist_ok=True)
Repo.clone_from(
    url='https://username:access_token@gitlab.com/gnachman/iterm2.git',
    branch='master',
    to_path=path, 
)

# commit hash https://stackoverflow.com/a/31957784/6813490
repo = Repo(path_to_cloned_repo)
repo.git.rev_parse(repo.head.object.hexsha, short=1)

# diff commits
# clients need `.git` on file system https://www.christianengvall.se/check-for-changes-on-remote-origin-git-repository/ https://stackoverflow.com/a/16315536/6813490 https://gitpython.readthedocs.io/en/stable/reference.html#git.remote.Remote https://github.com/gitpython-developers/GitPython/issues/373
# Gitlab needs access token, not deploy key
res = subprocess.Popen('git ls-remote origin -h refs/heads/master', shell=True, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
res.stdout

# get branch from remote https://stackoverflow.com/a/60735120
from pathlib import Path
from git import Repo
p = Path.cwd()
repo = Repo(p)
repo.git.ls_remote("--heads", "origin", "master")
```

## math

📙 Beazley ch. 3
🔗 https://github.com/cosmologicon/pywat
🛠️ https://github.com/python-humanize/humanize

---

* currency: https://github.com/pycountry/pycountry
* unit conversion: https://pint.readthedocs.io/en/0.10.1/

sum https://jcarlosroldan.com/post/329/my-latest-tils-about-python

RANDOM
* https://realpython.com/courses/generating-random-data-python/
* https://eli.thegreenplace.net/2010/01/22/weighted-random-generation-in-python
```python
from random import choice, randint, sample

choice([True, False])  # pick one
choice([True, False])  # pick one
randint(1, 10)  # pick one from range
sample(["hey", "hi", "hello", "hiya"], 2)  # pick n
''.join([choice(string.ascii_letters + string.digits) for n in range(32)])  # random string
```
```python
import string
from random import choices, choice

char = string.ascii_letters + string.digits  # 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'

# choices - return subset https://www.youtube.com/watch?v=rGQKHpjMn_M @ 13:15
choices(char, k=3)  # ['F', 'g', 'z']
''.join(choices(char, k=3))  # '1d3'

# choice - return single el
choice(char)  # 'z'
choice(char, k=3)
Traceback (most recent call last):
  File "<input>", line 1, in <module>
    choice(char, k=3)
TypeError: choice() got an unexpected keyword argument 'k'
```

FLOATING POINT ARITHMETIC 📙 Van Rossum ch. 15
* comparing floats: `math.isclose(0.1 + 0.2, 0.3)` https://davidamos.dev/the-right-way-to-compare-floats-in-python/
> You can specify the relative tolerance with the rel_tol keyword argument of math.isclose() which defaults to 1e-9. In other words, if abs(a - b) is less than 1e-9 * max(abs(a), abs(b)), then a and b are considered "close" to each other. This guarantees that a and b are equal to about nine decimal places.
* rounding https://stackoverflow.com/a/43661374
```python
# rm decimal
int(1.9)  # 1

# round to closest
round(1.9)  # 2
round(1.94, 1)  # 1.9

# round down
math.floor(1.9)  # 1

# round up
math.ceil(1.1)  # 2
```

* use `localcontext` when dealing w/ decimals https://orbifold.xyz/numbers.html

```python
###
# INTS & FLOATS https://davidamos.dev/the-right-way-to-compare-floats-in-python/ 📙 Van Rossum ch. 15
###

# increment operators https://stackoverflow.com/a/15376520

# + -> calls __add__()
num = 0
num + 1
num  # 0
# += -> calls __iadd__(), can't use in return statement
num = 0
num += 1
num  # 1

def inc(num):
    return num + 1 # ✅
    return num += 1  # ❌

###################################################

# main types
# integers are objects https://pythonspeed.com/articles/python-integers-memory/
int()  # can be as big as your memory can deal with https://realpython.com/python-data-types/#integers
float()

# can also represent binary and complex
0b10  # 2  https://realpython.com/python-data-types/#integers
42+7j  # <class 'complex'> https://realpython.com/python-data-types/#complex-numbers [Saha 1.6]

# conversions -> can't convert float string to int [Saha 1.8]
float('1')  # 1.0
int('1')  # 1
float('1.0')  # 1.0
int('1.0')  # ValueError

# validate floats
1.0.is_integer()  # True
1.3.is_integer()  # False

# integers turn to floats if division https://orbifold.xyz/numbers.html
4/3

# avoid floats with floor division operator [Saha 1.2]
4//3

# variables holding integers btw -5 and 256 are just references to existing obj in Python integer cache https://wsvincent.com/python-wat-integer-cache/ https://arpitbhayani.me/blogs/python-caches-integers
a = 8
b = 8
id(a)  # 4304845536
id(b)  # 4304845536

# negative infinity https://www.interviewcake.com/article/python/big-o-notation-time-and-space-complexity
float("-inf")

# square root via exponent operator [Saha 1.3]
8 ** (1/3)
```

* rounding
```sh
# rounding works as expected
python -c 'print(round(0.0273, 3))'   # 0.027
python -c 'print(round(0.0273, 2))'   # 0.03

# division rounds down when there is a remainder
python -c 'print(14 / 5)'             # 2
python -c 'print(5 / 10)'             # 0

# workaround
python -c 'print(float(15) / float(365))'  # 0.041095890411
```

## regex

🗄
* `algos/algos`
* `algos/python-regex.pdf`
* `algos.md` regex
🔗
* http://xahlee.info/python/python_regex_flags.html
* https://docs.python.org/3/howto/regex.html

---

https://leanpub.com/regexpython/

```python
regex = re.compile(r"foo/([^\s]+)")  # capture anything up to white space
match = regex.search(string_to_query)
if not match:
  return False
version = match.group(1)
```

* methods
```python
import re

regex = re.compile(r"zach")  # ❓ why compile?
regex.search("zach another thing zach 1234").group()  # first match
regex.findall("zach another thing zach 1234")  # all matches
```
* https://github.com/tfeldmann/simplematch
* _alternatives_: https://github.com/kootenpv/textsearch https://github.com/r1chardj0n3s/parse
* _best practices_: use raw strings (c.f. 'strings') verbose mode https://docs.python.org/2/library/re.html#re.VERBOSE
* _match_: what your regex matched
* _group_: portion of match available if you've used groups in your regex https://stackoverflow.com/a/29108/6813490
* `sub`: https://stackoverflow.com/a/16720752/6813490
* `.match()`: apparently good for searching telephone numbers, anything that's not a sentence https://howchoo.com/g/zdvmogrlngz/python-regexes-findall-search-and-match but otherwise no one uses https://stackoverflow.com/questions/180986/what-is-the-difference-between-re-search-and-re-match inconsistent w/ how regex work in Perl, sed, grep https://stackoverflow.com/a/37363575/6813490 allegedly faster than `search()` but not so! https://stackoverflow.com/a/49710946/6813490
