# ⛩️

## 参考

📜 https://docs.python.org/dev/library/index.html
📙 Van Rossum ch. 10-11
📈 https://pythonwheels.com/
🔍 https://github.com/vinta/awesome-python

## 进步

* https://cjolowicz.github.io/posts/hypermodern-python-01-setup/ https://talkpython.fm/episodes/show/362/hypermodern-python-projects
* https://www.b-list.org/weblog/2022/may/13/boring-python-dependencies/ https://www.b-list.org/weblog/2022/dec/19/boring-python-code-quality/
* https://talkpython.fm/episodes/show/327/little-automation-tools-in-python
* https://github.com/nickolaj-jepsen/fnug

* _24_: split from `python.md`, lib (ward)
* _21_: rf pdb, doctest basics

# 🧫 CQ

⭐️ https://github.com/stars/zachvalenta/lists/code-quality

---

CODE STATS
* Python2 https://chatgpt.com/c/6717c005-9560-8004-8240-a612fd00792e
* stats: https://github.com/boyter/scc https://github.com/XAMPPRocky/tokei https://github.com/k1LoW/octocov
* dead code: https://github.com/jendrikseipp/vulture https://github.com/sobolevn/flake8-eradicate
> does ruff do this?
* security: https://github.com/PyCQA/bandit https://pyup.io/ (uses same vulnerability db as pipenv) pysa https://github.com/facebook/pyre-check https://news.ycombinator.com/item?id=24083432 https://github.com/DataDog/guarddog

## docs

---

https://rdrn.me/postmodern-python/

LIB
* _pdoc_: thing that pdoc3 forked from https://github.com/mitmproxy/pdoc
* _pdoc3_: https://pdoc3.github.io/pdoc/ some controversy https://github.com/pdoc3/pdoc/issues/64 https://github.com/pdoc3/pdoc/issues/87 even worse than first blush, apparently he is a fascist https://news.ycombinator.com/item?id=20800157
* _pdocs_: https://github.com/timothycrosley/pdocs/issues/3
* _portray_: built on pdoc3 https://github.com/timothycrosley/portray/
* _pydoc_: https://docs.python.org/3/library/pydoc.html https://stackoverflow.com/a/13043765/6813490 
* _pycco_: pretty but don't see use case https://pycco-docs.github.io/pycco/ https://realpython.com/generating-code-documentation-with-pycco/
* _Sphinx_: `sphinx-apidoc` 缺点 RST, not geared towards APIs https://realpython.com/courses/documenting-python-projects-sphinx-read-the-docs/ can now use Markdown https://www.youtube.com/watch?v=YclYtM56qjo&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=38

DOCSTRING https://github.com/copyleftdev/x12-edi-tools
* tooling https://switowski.com/blog/plugins-for-python-in-vscode/
* _triple quoted string (TQS)_: https://docs.python.org/3/glossary.html
* _doctring_: TQS as first line of class/function https://github.com/econchick/interrogate https://www.fluentpython.com/lingo/#docstring
* how to read: module (`help("doctest")`) function (`help(my_func)` or `my_func.__doc__`)
* parsed by doc libraries e.g. pdoc
* use TQS in lieu of multi-line comment https://stackoverflow.com/a/7696966
```python
def foo(my_arg):
    # basic
    """
    basic docstring
    """

    # PyCharm convention https://stackoverflow.com/a/40596167
    """
    This line is for an overview.

    :param req: request from web framework
    :return: what this function is returning
    """
```

## lint / fmt

🗄️ `core.md` style

RUFF 📜 https://github.com/astral-sh/ruff
* meant to replace black, isort
```sh
check  # lint
check --fix  # fix lint err
```

ZA
* ignore line: `# NOQA` https://flake8.pycqa.org/en/2.6.0/config.html#per-code-line 
* custom via AST e.g. enforce docs https://docs.python.org/3/library/inspect.html#retrieving-source-code
* lint exceptions https://github.com/guilatrova/tryceratops

ALTERNATIVES
* fmt code blocks in doc files https://github.com/asottile/blacken-docs
* fmt based on recent changes https://github.com/akaihola/darker
* _flake8_: https://flake8.pycqa.org/
```sh
flake8 src test # lint multiple dir 🗄️ algos
flake8 exclude = */__init__.py  # all __init__
flake8 --isolated  # can use from shell, but it might be picking up config file somewhere, so this worked to get back to defaults
```
```conf
[flake8]  # .flake8 https://ljvmiranda921.github.io/notebook/2018/06/21/precommits-using-black-and-flake8/
max-complexity = 10
max-line-length = 88
ignore =  # http://flake8.pycqa.org/en/latest/user/configuration.html
    E203,  # play nice w/ Black https://github.com/psf/black/issues/1029
    E402  # workaround for flattened Flask project structure
    W503  # rule dated on line break? https://www.flake8rules.com/rules/W503.html https://dev.to/m1yag1/how-to-setup-your-project-with-pre-commit-black-and-flake8-183k
per-file-ignores =  # https://stackoverflow.com/a/54454433/6813490
    db_shell.py:F401  # give user access to all models from REPL
```
* _pycodestyle_: style rules; used in ruff https://github.com/PyCQA/pycodestyle https://406.ch/writing/how-ruff-changed-my-python-programming-habits/
* _pyflakes_: style rules; used in ruff https://github.com/PyCQA/pyflakes
* _pyupgrade_: upgrade syntax for future Python versions https://github.com/asottile/pyupgrade

## logging

🗄
* `python/runtime.md` REPL
* `telemetry` logging

---

https://rednafi.com/python/no_hijack_root_logger/
icecream for print debugging https://github.com/gruns/icecream
* people don't use format/f-strings in logging
* https://monadical.com/posts/ins-and-outs-of-logging-in-python-part-one.html
* logs sent by default to `sys.stdout` i.e. they're buffered https://stackoverflow.com/a/51362214/6813490 https://realpython.com/python-flush-print-output/
* pretty stdout https://github.com/onelivesleft/PrettyErrors
* can unbuffer w/ `PYTHONUNBUFFERED=1` https://docs.python.org/3/using/cmdline.html?highlight=pythonunbuffered#envvar-PYTHONUNBUFFERED
* this shows up in Docker, Docker won't show logs from Flask dev server in real-time unless logs set to unbuffered although I don't know why https://github.com/sclorg/s2i-python-container/issues/157 https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
* add logs without updating source https://github.com/yiblet/inquest
* _libraries_: https://stackoverflow.com/a/51362214 https://github.com/Delgan/loguru https://github.com/BNMetrics/logme https://github.com/hynek/structlog https://github.com/itamarst/eliot stdlib https://docs.python.org/3/howto/logging.html https://docs.python.org/3/howto/logging-cookbook.html GUI https://github.com/busimus/cutelog

## profiling

📙 Beazley ch. 14
🗄
* `feedback.md` debug
* `linux.md` tracing
* `telemetry.md`

PG http://paulgraham.com/popular.html
> It might be a good idea to have an active profiler - to push performance data to the programmer instead of waiting for him to come asking for it.
> Part of the problem here is social. Language designers like to write fast compilers. That's how they measure their skill. They think of the profiler as an add-on, at best. But in practice a good profiler may do more to improve the speed of actual programs written in the language than a compiler that generates fast code. Here, again, language designers are somewhat out of touch with their users. They do a really good job of solving slightly the wrong problem.
> A good language, as everyone knows, should generate fast code. But in practice I don't think fast code comes primarily from things you do in the design of the language. As Knuth pointed out long ago, speed only matters in certain critical bottlenecks. And as many programmers have observed since, one is very often mistaken about where these bottlenecks are. So, in practice, the way to get fast code is to have a very good profiler, rather than by, say, making the language strongly typed. You don't need to know the type of every argument in every call in the program. You do need to be able to declare the types of arguments in the bottlenecks. And even more, you need to be able to find out where the bottlenecks are.

---

OPTIONS
* https://github.com/nakabonne/gosivy
* _austin_: frame stack sampler https://github.com/P403n1x87/austin https://github.com/P403n1x87/austin-tui
* _cProfile_: 🎯 https://www.pythonmorsels.com/cli-tools/ https://martinheinz.dev/blog/64 https://hakibenita.com/django-rest-framework-slow
* _fastero_: 🎯 timeit alternative https://github.com/wasi-master/fastero
* _Fil_: https://pythonspeed.com/products/filmemoryprofiler/ https://pythonspeed.com/articles/memory-profiler-data-scientists/
* _instruments_: https://registerspill.thorstenball.com/p/did-you-know-about-instruments
* _line profiler_: https://github.com/pyutils/line_profiler https://news.ycombinator.com/item?id=41910590
* _memray_: 🎯 https://github.com/bloomberg/memray https://textual.textualize.io/blog/2024/02/20/remote-memory-profiling-with-memray/ https://realpython.com/podcasts/rpp/128/ https://talkpython.fm/episodes/show/425/memray-the-endgame-python-memory-profiler https://news.ycombinator.com/item?id=41910590
* _phlare_: https://martinheinz.dev/blog/89
* _pyflame_: https://medium.com/zendesk-engineering/hunting-for-memory-leaks-in-python-applications-6824d0518774 
* _pyspy_: https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* _pyinstrument_: https://news.ycombinator.com/item?id=41910590
* _pyroscope_: https://grafana.com/blog/2023/04/19/how-to-troubleshoot-memory-leaks-in-go-with-grafana-pyroscope/
* _pystack_: https://talkpython.fm/episodes/show/419/debugging-python-in-production-with-pystack https://martinheinz.dev/blog/101
* _tracy_: https://github.com/wolfpld/tracy
* _speedscope_: https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* _Sciagraph_: https://news.ycombinator.com/item?id=31826872
* _Valgrind_: https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* _timeit_: 🎯 https://www.pythonmorsels.com/cli-tools/
```python
# try this instead

# The "timeit" module lets you measure the execution
# time of small bits of Python code
# https://www.youtube.com/watch?v=EcGWDNlGTNg
import timeit
timeit.timeit('"-".join(str(n) for n in range(100))', number=10000)
timeit.timeit('"-".join([str(n) for n in range(100)])', number=10000)
timeit.timeit('"-".join(map(str, range(100)))', number=10000)

# https://stackoverflow.com/a/7523810/6813490
from timeit import Timer
# doesn't manifest savings in small collections
names_list = ['alice', 'bob', 'candace']
names_set = set(['alice', 'bob', 'candace'])

# setup large collection of numbers and see what happens then
def lookup_list(l):
    return 'alice' in l
def lookup_set(s):
    return 'alice' in s
def cast_to_timer(func, args):
	return Timer(lambda: func(args))
def timeit_ms(func):
	return print(func.timeit(number=1000))
if __name__=='__main__':
    timeit_ms(cast_to_timer(lookup_list, names_list))
    timeit_ms(cast_to_timer(lookup_set, names_set))
```

* profile CPython https://instagram-engineering.com/profiling-cpython-at-instagram-89d4cbeeb898
* performance tests https://treyhunner.com/2024/06/a-beautiful-python-monstrosity/
* ebpf https://coroot.com/blog/engineering/instrumenting-python-gil-with-ebpf/
* https://www.pythonmorsels.com/cli-tools/
* https://www.youtube.com/watch?v=CjG_Ub_gCL4
* https://github.com/nakabonne/ali/releases/tag/v0.7.0
* Zig ttps://www.youtube.com/watch?v=ug-KuDlMTYw
* `sys.settrace` https://github.com/plasma-umass/slipcover https://nedbatchelder.com/blog
* https://www.youtube.com/watch?v=bGAVrtb_tFs https://www.brendangregg.com/
* https://blog.mattstuchlik.com/2024/02/16/counting-syscalls-in-python.html
* https://www.freecodecamp.org/news/python-debugging-handbook/
* https://madebyme.today/blog/python-dict-vs-curly-brackets/
* https://superfastpython.com/benchmark-execution-time/ https://www.bwplotka.dev/2024/go-microbenchmarks-benchstat/
* https://stackabuse.com/why-does-python-code-run-faster-in-a-function/
* https://realpython.com/python-profiling/
* https://adamj.eu/tech/2023/07/23/python-profile-section-cprofile/
* https://realpython.com/python312-perf-profiler/
* https://functiontrace.com/
* Rust, Cython https://pythonspeed.com/articles/faster-text-processing/ https://www.equalto.com/blog/rust-in-anger-high-performance-web-applications
* https://news.ycombinator.com/item?id=36605730
* https://www.petermcconnell.com/posts/perf_eng_with_py12/
* benchmark https://pythonspeed.com/articles/faster-json-library/ https://eli.thegreenplace.net/2023/common-pitfalls-in-go-benchmarking/
```sh
time $CMD  # https://news.ycombinator.com/item?id=30224063
```
* https://adamj.eu/tech/2023/03/02/django-profile-and-improve-import-time/
https://github.com/DataDog/go-profiler-notes

* `py3 -m trace --trace example.py`
* https://pythonspeed.com/articles/measuring-python-performance/
* https://switowski.com/blog/how-to-benchmark-python-code/
* https://codesolid.com/how-do-i-profile-python-code/
* https://tinkering.xyz/fmo-optimization-story/
* https://tech.marksblogg.com/faster-python.html https://www.peterbaumgartner.com/blog/intro-to-just-enough-cython-to-be-useful/ https://github.com/tonybaloney/perflint https://rednafi.github.io/reflections/pre-allocated-lists-in-python.html
* https://github.com/pyroscope-io/pyroscope
* https://flamegraph.com/ https://github.com/laixintao/flameshow
* profiling CLI, `time` https://news.ycombinator.com/item?id=30224063
* profiling async https://github.com/aviramha/capara
* https://pythonspeed.com/memory/
* https://github.com/pythonprofilers/memory_profiler https://news.ycombinator.com/item?id=27025829
* https://github.com/csurfer/pyheat
* https://github.com/joerick/pyinstrument
* https://www.youtube.com/watch?v=1EZ8oqjLun0
* https://medium.com/statch/speeding-up-python-code-with-nim-ec205a8a5d9c
* https://github.com/joerick/pyinstrument
* https://hakibenita.com/django-rest-framework-slow
* https://github.com/brandtbucher/specialist
* https://github.com/robusta-dev/WhyProfiler
* `time` https://hacker-tools.github.io/program-introspection/
* https://github.com/joerick/pyinstrument
* https://github.com/P403n1x87/austin https://talkpython.fm/episodes/show/265/why-is-python-slow 54:00
* _flamegraph_: visualization for CPU usage https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions
* sink: https://www.blog.pythonlibrary.org/2020/04/14/an-overview-of-profiling-tools-for-python/ https://www.roguelynn.com/words/tracing-fast-and-slow/ https://pythonspeed.com/articles/blocking-cpu-or-io/ https://pythonspeed.com/articles/custom-python-profiler/ https://pythonspeed.com/articles/live-debugging-python/ https://www.markkeller.dev/2018-07-14-optimize_python/ https://jvns.ca/blog/2017/12/02/taking-a-sabbatical-to-work-on-ruby-profiling-tools/ pyspy https://jvns.ca/blog/2018/12/23/2018--year-in-review/ https://www.youtube.com/watch?v=d5SGUscT2GA https://jvns.ca/blog/2017/12/17/how-do-ruby---python-profilers-work-/ https://github.com/ionelmc/python-hunter https://wsvincent.com/algorithms-binary-search/ https://wsvincent.com/python-optimizations-with-guido/ https://realpython.com/python-f-strings/ https://github.com/airspeed-velocity/asv
* pyperf, timeit https://medium.com/@martin.heinz/python-cli-tricks-that-dont-require-any-code-whatsoever-e7bdb9409aeb https://log.beshr.com/python-311-speedup-part-1/
* benchmark: https://github.com/sharkdp/hyperfine https://github.com/egoist/dum
* can use hyperfine under the hood https://github.com/dandavison/magit-delta https://github.com/sharkdp/hyperfine
* https://blog.usejournal.com/how-to-create-your-own-timing-context-manager-in-python-a0e944b48cf8 https://martinheinz.dev/blog/13 https://realpython.com/python-timer/

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
# CONTEXT MANAGER https://www.fluentpython.com/lingo/#context_manager https://www.pythonmorsels.com/creating-a-context-manager/
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

## process exec

🔗 https://martinheinz.dev/blog/98
🗄️ `infra.md` IaC / remote execution

OPTIONS
* `os.system`
* `subprocess`
* _sh_: https://github.com/amoffat/sh https://martinheinz.dev/blog/96
* _suby_: https://github.com/pomponchik/suby
* _Sultan_: https://github.com/aeroxis/sultan https://stackoverflow.com/a/56842257/6813490

# 🔬 TEST

🗄️ `test.md`
⭐️ https://github.com/stars/zachvalenta/lists/test

## behave

📜 https://behave.readthedocs.io/en/latest/ https://github.com/behave/behave

* alternative https://github.com/pytest-dev/pytest-bdd 
* same syntax as Cucumber https://stackoverflow.com/a/52027041
* few commits but seems active https://github.com/behave/behave/projects/4#card-50138436)
* Django integration: https://behave.readthedocs.io/en/latest/usecase_django.html https://whoisnicoleharris.com/2015/03/19/bdd-part-two.html https://semaphoreci.com/community/tutorials/setting-up-a-bdd-stack-on-a-django-application
> we got around at work bc we're just using to hit our deployed endpoints

CLI
```sh
# view stdout https://stackoverflow.com/a/28551235/6813490 https://stackoverflow.com/a/41969164/6813490
behave --no-capture --no-color --tags @foo

# exclude tag
--tags ~@tag1        # single
--tags ~@tag1, tag2  # n
```

PROJECT SETUP
```sh
# default https://behave.readthedocs.io/en/latest/gherkin.html?highlight=directory#feature-testing-layout
├── features
│   └── foo.feature
│   └── bar.feature
│   └──── steps
│   └─────── baz.py

# with config https://behave.readthedocs.io/en/latest/behave.html?highlight=configuration#configuration-files
├── bdd
│   └── features
│   └──── foo.feature
│   └── steps
│   └──── foo.py

# .behaverc
[behave]
paths=dj_app/bdd
```

STEP SYNTAX
```python
from behave import given, then

@given('we have behave installed')
def step_impl(context):
    pass

@then('behave will test them for us!')  # actual identifier in decorator
def step_impl(context):  # function identifier identical; must take `context` as arg
    assert context.failed is False  # vanilla assertions
```

## coverage

📜 https://coverage.readthedocs.io/

* alternative https://www.youtube.com/watch?v=X9aXWeLC_C0 https://github.com/plasma-umass/slipcover
* design https://nedbatchelder.com/blog/202406/coverage_at_a_crossroads.html
* `.coverage`: result files; read by `coverage report` and `coverage html`
* pytest-cov` also has `--cov-fail-under=MIN` arg you could pass as a normal pipeline step https://github.com/pytest-dev/pytest-cov
* pretty slow https://www.drmaciver.com/2017/09/python-coverage-could-be-fast/
* impl https://talkpython.fm/episodes/transcript/178/coverage.py @ 42:00 https://www.pythoninsight.com/2018/03/how-does-coverage-measurement-work-in-python/
```sh
# syntax: `coverage run` replaces whatever was executing tests (`python`, `python manage.py`)
coverage run -m unittest discover -v
# what files to cover is combination of source/include/omit https://stackoverflow.com/q/1628996
poetry run coverage run --source='api' --omit='*/migrations/*.py' manage.py test api
poetry run coverage run --source='api' --omit='*/migrations*'  # all from dir
poetry run coverage run --source='api' --omit='*/migrations*,api/apps.py'  # omit n
# use .coverage for terminal summary
coverage report
# create htmlcov from .coveragerc and open report
coverage html && coverage htmlcov/index.html
```

## doctest

---

https://hamatti.org/posts/document-intended-usage-through-tests-with-doctest/
* https://rdrn.me/postmodern-python/
* `ELLIPSIS` 📙 Ramalho [7]
* _doctest_: docstring + test https://www.fluentpython.com/lingo/#doctest
> [key feature] they look like transcripts of interactive Python console sessions, so you can easily try out the demonstrations yourself 📙 Ramalho [xviii]
* as TDD-as-design tool bc favors small functions that require minimal setup
* keep docstring aligned to src
* run: `python -m doctest -v my_mod.py`
```python
def foo(a, b):
    """
    >>> foo(2, 3)
    5
    """
    return a + b
```

## mocks

---

[mock cookbook](https://chase-seibert.github.io/blog/2015/06/25/python-mocking-cookbook.html) + https://www.toptal.com/python/an-introduction-to-mocking-in-python + https://medium.com/@yeraydiazdiaz/what-the-mock-cheatsheet-mocking-in-python-6a71db997832 + https://realpython.com/python-mock-library/
* https://medium.com/ryans-dev-notes/python-mock-and-magicmock-b3295c2cc7eb
* https://thoughtbot.com/upcase/test-doubles
https://thoughtbot.com/upcase/test-doubles
* fake
* mock --> have an example from Python Cookbook with stdout https://www.youtube.com/watch?v=Ldlz4V-UCFw  https://pythonspeed.com/articles/verified-fakes/
* spy
* _monkey patch_: changing code at runtime https://www.fluentpython.com/lingo/#monkey_patching https://news.ycombinator.com/item?id=34611969

* https://medium.com/@yeraydiazdiaz/what-the-mock-cheatsheet-mocking-in-python-6a71db997832

https://romantomjak.com/posts/testing-python-code-that-makes-http-requests.html
https://talkpython.fm/episodes/show/287/testing-without-dependencies-mocking-in-python https://quii.gitbook.io/learn-go-with-tests/testing-fundamentals/working-without-mocks

## pytest

📜 https://docs.pytest.org/en/latest/contents.html#toc

PLUGINS
* randomize execution order https://github.com/pytest-dev/pytest-randomly 
* port ward output to pytest https://github.com/darrenburns/ward/blob/master/ward/_terminal.py https://docs.pytest.org/en/7.1.x/how-to/writing_plugins.html#writing-your-own-plugin https://github.com/nicoddemus/pytest-rich/tree/main
* _pluggy_: framework for write plugins https://ward.readthedocs.io/en/latest/guide/plugins.html https://pluggy.readthedocs.io/en/latest/

STDOUT
* long-running tests https://calmcode.io/labs/pytest-duration-insights https://github.com/pytest-dev/pytest-reportlog https://github.com/koaning/pytest-duration-insights
* test Markdown snippets https://calmcode.io/labs/mktestdocs
* https://pypi.org/project/pytest-testdox/
* https://github.com/darrenburns/pytest-clarity
* summary reports https://docs.pytest.org/en/latest/usage.html#detailed-summary-report
* info in tracebacks https://docs.pytest.org/en/latest/usage.html#modifying-python-traceback-printing
* `-s` see print statements https://stackoverflow.com/a/55950781/6813490
* `-v` see each test that executed https://github.com/darrenburns/pytest-clarity https://github.com/Teemu/pytest-sugar https://github.com/numirias/pytest-json-report
* group related tests https://pypi.org/project/pytest-testdox/
```python
@pytest.mark.describe("doing stuff")  # can also use mark.it()
def test_doing_this():
    pass
def test_doing_that():
    pass
```
```sh
doing stuff
 [x] doing this
 [x] doing that
```

---

MARKS
* _mark_: decorator to add metadata
* skip test `pytest.skip('WIP')` https://github.com/box/flaky https://danluu.com/wat/
* params https://docs.pytest.org/en/6.2.x/parametrize.html
> these less readable to me

ZA
* plugins https://blog.pecar.me/pytest-plugin
* matchers: https://github.com/hamcrest/PyHamcrest https://github.com/mwilliamson/python-precisely https://changelog.com/gotime/159 https://github.com/corbym/gocrest
* _non-fatal assertions_: continue execution if assertion fails https://github.com/okken/pytest-check unittest https://stackoverflow.com/a/5028110 pytest parameters https://stackoverflow.com/a/36760045
* does pytest/unittest use `trace` module?
* better than unittest bc easier assertions, parameterization, function-based https://github.com/renzon/pytest-vs-unittest https://www.b-list.org/weblog/2020/feb/03/how-im-testing-2020/
* will pick up modules prepended w/ `test_` otherwise on you to specify
* run in parallel https://github.com/pytest-dev/pytest-xdist https://tech.marksblogg.com/faster-django-testing.html
* xfail https://blog.ganssle.io/articles/2021/11/pytest-xfail.html

CLI
* freezes terminal if encounters breakpoint, workaround w/ `pytest -s --pdb`
* `pytest.set_trace()` is deprecated and doesn't work w/ pdbpp https://github.com/pdbpp/pdbpp/issues/392 https://docs.pytest.org/en/latest/historical-notes.html#pytest-set-trace 
```sh
###
# BIN vs. MOD
###
pytest             # bin
python3 -m pytest  # module

###
# SCOPE https://stackoverflow.com/a/54493489
###
test_mod.py             # module
test_mod.py::test_func  # func
-m slow                 # marker
-k <expression>         # regex

###
# ARGS
###
--lf           # only runs tests that failed on last attempt
--testmon      # only runs tests affect by recent code change https://github.com/anapaulagomes/pytest-picked https://github.com/tarpas/pytest-testmon
--durations=n  # show n slowest setups/tests
--setup-show   # show setup of fixtures while executing tests.

###
# DEBUG
###
--pdb    # use w/ pdb.set_trace() https://docs.pytest.org/en/latest/how-to/failures.html#dropping-to-pdb-python-debugger-on-failures 🗄 `sw/algos/algos`
--trace  # use w/ individual func when pdb not working (this happened at work once, idky)
-s       # necessary for pdbpp to work https://stackoverflow.com/a/3418597
-l       # locals https://hackebrot.github.io/pytest-tricks/debug_test_failures/
```

CONFIG
```python
class Test():
    __test__ = False  # tells pytest to not collect this class https://stackoverflow.com/a/42534950/6813490
    foo = 'foo'
```
```conf
# suppress all
pytest --disable-pytest-warnings

# suppress warnings by type https://stackoverflow.com/a/53218641/6813490 https://github.com/zachvalenta/create-python-app/blob/master/pytest.ini
[pytest]
filterwarnings =
    ignore::DeprecationWarning
```

FIXTURES
* https://betterstack.com/community/guides/testing/pytest-fixtures-guide/
* session https://nedbatchelder.com/text/test3/test3.html#39 
* parameterize: aka table-driven https://arslan.io/2022/12/04/functional-table-driven-tests-in-go/ https://nedbatchelder.com/text/test3/test3.html#41 cannot use module scoped data https://github.com/pytest-dev/pytest/issues/349
* set module scope for data https://stackoverflow.com/a/47885205 https://docs.pytest.org/en/latest/how-to/fixtures.html#scope-sharing-fixtures-across-classes-modules-packages-or-session
```python
@pytest.fixture(scope="module")
def data():
    return { "my_data": 42 }

def test_use_data(data):
    assert return_it(arg=data["my_data"]) == 42
```
* xunit for fixture/factory https://docs.pytest.org/en/latest/how-to/xunit_setup.html
```python
def setup_module():
    print('before entire mod')

def teardown_module():
    print('after entire mod')

def setup_function():
    print('before each func')
    
def teardown_function():
    print('after each func')

def test_foo():
    pass
```

## tox

* test against multiple Python versions
* https://hynek.me/articles/turbo-charge-tox/
* _nox_: https://sethmlarson.dev/nox-pyenv-all-python-versions https://github.com/wntrblm/nox https://hynek.me/articles/why-i-like-nox https://hynek.me/articles/why-i-like-nox/
* parallelize https://blog.sentry.io/2022/11/14/how-we-run-our-python-tests-in-hundreds-of-environments-really-fast/ split list https://realpython.com/how-to-split-a-python-list-into-chunks/
* https://realpython.com/python-testing/#testing-in-multiple-environments https://www.andreagrandi.it/2019/02/21/skipping-tests-depending-python-version/ https://www.b-list.org/weblog/2020/feb/03/how-im-testing-2020/
```sh
# run for n dirs
tox -e py27 -- path/here/ path/there
# run for module
tox -e py27 -- path/here/foo.py
# run for class
tox -- path/to/foo.py::FooClass
# run for func
tox -- path/to/foo.py::FooClass::test_foo
# run test for all versions
tox -- tests/util/dicts_test.py
```

## unittest

📜 stdlib chapter 26 📙 Beazley ch. 14

---

* _advantages_: `unittest` assertions > Python OOB `assert` keyword bc useful logging https://stackoverflow.com/a/2958183/6813490
* _config_: tests prepended with `test_`; `discover` requires `__init__.py` in sub-directory https://stackoverflow.com/a/6672873/6813490
* _disadvantages_: seems to be fading in popularity, projects based on it are going away https://github.com/jarus/flask-testing too many assertions https://docs.python.org/3/library/unittest.html#classes-and-functions
* `error` vs. `failure`: exception vs. test case
* _fixtures_: `setUp` (run before each test case) `tearDown` (typically don't need to fuss with this)
* _history_: during Python 2.7 used to be called `unittest2` https://realpython.com/python-testing/
* _parameterize_: https://stackoverflow.com/a/34094/6813490
* run
```sh
py3 -m unittest discover -v  # all tests recursively
py3 -m unittest tests.test_sut  # all tests in module
py3 -m unittest tests.test_sut.TestSUT.test_sanity  # single test in module
```
* snippet
```python
# skip test
@unittest.skip("skip this test")

# class-based syntax
import unittest
class TestSUT(unittest.TestCase):
  def test_foo(self):
    self.assertEqual(True, True)

# test error thrown
def test_miss_entry_raises_KeyError(self):
  phonebook = Phonebook()
  with self.assertRaises(KeyError):
    phonebook.lookup('missing')

# test exit code https://stackoverflow.com/a/15672165
with self.assertRaises(SystemExit) as x:
  ur_method()
self.assertEqual(x.exception.code, 1)
```

## ward

📜 https://github.com/darrenburns/ward

* downside: symbols don't show up in VS Code
* tags = pytest marks https://ward.readthedocs.io/en/latest/guide/writing_tests.html#descriptive-testing
* fixtures https://blog.thea.codes/my-python-testing-style-guide/

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
* _bullet_: https://github.com/Mckinsey666/bullet
* repos https://github.com/zachvalenta/news https://github.com/zachvalenta/capp-prod-cat/blob/link-nodes/tree_viz.py 🗄️ `git.md` Github / search
* control flow https://github.com/shkey/killurp/blob/141d411d353ab46edf362ff6a33bfe9c5a5ad211/killurp.py#L8 https://github.com/chroma-core/chroma-migrate/blob/2a6e61ee7f2d717281075512b308c40616033189/chroma_migrate/cli.py#L2
* _questionary_: https://github.com/tmbo/questionary 
* _prompt-toolkit_: used by pgcli, http-prompt https://github.com/j-bennet/wharfee/blob/master/setup.py https://github.com/wasi-master/fastero

OUTPUT
* animation 🎯 https://github.com/ChrisBuilds/terminaltexteffects https://realpython.com/python-rich-package/
* colors https://github.com/timofurrer/colorful https://github.com/erikrose/blessings
* syntax highlighting https://github.com/pygments/pygments
* tables https://github.com/astanin/python-tabulate https://realpython.com/python-rich-package/
* progress bar https://realpython.com/python-rich-package/ https://github.com/rsalmei/alive-progress https://github.com/tqdm/tqdm
```python
if i % 100 == 0:
    progress = ((i + 1) / float(len(qd))) * 100.0
    print('%.2f%%' % progress)
```

## TUI (Textual)

🗄️
* `ml.md` clients > Elia
* `os/tools.md` browsr

HOWTO
* publish to web https://github.com/Textualize/textual-web
* run examples
```sh
python -m pip install --user textual
cd /Users/zvalenta/Desktop/textual/examples
python json_tree.py
```

ZA
* inherently slow? both browsr and elia crawl on open

ALTERNATIVES
* _blessed_: https://github.com/jquast/blessed
* _asciimatics_: https://github.com/peterbrittain/asciimatics
* _urwid_: used by pudb, Zulip http://urwid.org/ https://github.com/zulip/zulip-terminal/blob/main/zulipterminal/ui_tools/boxes.py
* _pytermgui_: https://github.com/bczsalba/pytermgui

---

* https://realpython.com/contact-book-python-textual/
* functionality: tables, color, layout
* _Textual_: complaints https://news.ycombinator.com/item?id=35123383 animation https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#demonstrating-animation dropdown https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#dropdown-autocompletion-menu file manager https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#a-file-manager-powered-by-textual graphics https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#pixel-art layout https://textual.textualize.io/blog/2022/12/11/version-060/#placeholder tabs https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#tabs-with-animated-underline testing https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#developer-console https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#snapshot-testing-for-terminal-apps example https://github.com/learnbyexample/TUI-apps/tree/main/CLI-Exercises https://www.blog.pythonlibrary.org/2024/02/06/creating-a-modal-dialog-for-your-tuis-in-textual/

# 🕸️ WEB

📙 Beazley ch. 11
🗄
* `application.md` utils
* `language.md` frameworks

## frameworks

🛠️ debug HTTP requests https://github.com/cle-b/httpdbg

FRAMEWORKS
> Web development is often broad, not deep - problems span many domains. https://docs.djangoproject.com/en/2.0/intro/whatsnext/
> A framework is a text where you fill in the blanks. The framework defines the grammar, you bring some of the words. https://blog.startifact.com/posts/framework-patterns.html
* components: HTTP, routes, ORM
* BYO https://itsthejoker.github.io/spiderweb-the-tiny-web-framework/ https://www.destroyallsoftware.com/screencasts/catalog https://www.youtube.com/watch?v=7kwnjoAJ2HQ https://testdriven.io/courses/python-web-framework/ https://www.amazon.com/dp/1937785637 https://rubyonrails.org/doctrine/ https://github.com/itsthejoker/spiderweb/ https://github.com/iklobato/LightAPI https://news.ycombinator.com/item?id=41914544 https://dev.to/brunociccarino/how-i-wrote-express-go-in-19-hours-3ndh

WSGI
* interface btw app server and framework bc pre-WSGI which framework you picked determined which web server you could use https://www.pythonpodcast.com/episode-43-wsgi-2/ [8:00]
> The Web Server Gateway Interface (or "WSGI" for short) is a standard interface between web servers and Python web application frameworks. By standardizing behavior and communication between web servers and Python web frameworks, WSGI makes it possible to write portable Python web code that can be deployed in any WSGI-compliant web server. WSGI is documented in PEP 3333. https://docs.python-guide.org/scenarios/web/#wsgi
* _interface_: contract e.g. "app server will do these things in this way as specified by WSGI and app framework will hook into them in this way as specified by WSGI and that way gunicorn will work with any WSGI-compliant app framework and Flask will work with any-WSGI compliant app server"
* _constraints_: single-threaded https://stackoverflow.com/a/32217701 doesn't do async or WebSockets https://pythonbytes.fm/episodes/show/48/garbage-collection-and-memory-management-in-python https://www.pythonpodcast.com/episode-43-wsgi-2/ @ 18:00
* _supported by_: servers (gunicorn, uWSGI, mod_wsgi) frameworks (Flask, Django, Falcon, Pyramid)
* https://stackoverflow.com/a/38685758/6813490 https://talkpython.fm/episodes/show/13/flask-web-framework-and-much-much-more @ 30:00 https://djangodeconstructed.com/2018/02/15/how-a-request-becomes-a-response-diving-deeper-into-wsgi

ASGI
* _ASGI_: async alternative to WSGI
* frameworks: Django (Channels) Quart (Flask on async) Twisted (don't think actually ASGI but does async) new (Sanic, Starlette, FastAPI built on Starlette)
* servers: uvicorn, Daphne
* FastAPI https://github.com/pomponchik/cbfa
* sink: https://www.youtube.com/watch?v=7kwnjoAJ2HQ @ 10:55 Django moving this way https://docs.djangoproject.com/en/dev/releases/3.0/ async db https://github.com/encode/orm https://github.com/django/asgiref https://www.pythonpodcast.com/django-channels-and-the-asynchronous-web-with-andrew-godwin-episode-180/ https://github.com/florimondmanca/awesome-asgi  https://pythonbytes.fm/episodes/show/148/the-asgi-revolution-is-upon-us

RSGI
* _RSGI_: for Rust https://github.com/emmett-framework/granian/blob/master/docs/spec/RSGI.md 🗄️ `infra.md` granian

## HTML (scrapy)

🗄 `html-css.md`

aaS
* _ScrapingBee_: https://www.scrapingbee.com/
* _Zenrows_: https://www.zenrows.com/solutions/scraper-api

---

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
* https://github.com/projectdiscovery/katana
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

## serde

📙 Beazley ch. 6
🗄
* `protocols.md` serde
* `svc/django.md` DRF

ALTERNATIVES
* dataclasses
* _orjson_: fast https://github.com/ijl/orjson
* _pickle_: https://docs.python.org/3/library/persistence.html no one uses any more https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html
* _pydantic_: https://docs.pydantic.dev/latest/concepts/serialization/ https://news.ycombinator.com/item?id=14477434

### JSON

📜 https://docs.python.org/3/library/json.html

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

# 🟨 ZA

* auth: https://authlib.org/
* browser: `webbrowser` https://dev.to/dmahely/one-bash-command-to-start-the-day-2fni
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

* rise of 3rd-party packages, dead batteries http://pyfound.blogspot.com/2019/05/amber-brown-batteries-included-but.html https://www.python.org/dev/peps/pep-0594/ provisional API https://docs.python.org/3/glossary.html#term-provisional-API

* _hashing_: passlib https://passlib.readthedocs.io/en/stable/ https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis
```python
# https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis
import hashlib as hl
sha = hl.sha256()
sha.update(b'hey')
sha.hexdigest()  # 'fa690b82061edfd2852629aeba8a8977b57e40fcb77d1a7a28b26cba62591204'
```
* _markdown_: https://pypi.org/project/markdown2/ used this one for `m2h` https://github.com/Python-Markdown/markdown had issues with ampersands in URLs, see repo commit `43e` https://stackoverflow.com/a/20593644/6813490 https://stackoverflow.com/questions/39086/search-and-replace-a-line-in-a-file-in-python
* _networking_: Scapy https://www.youtube.com/watch?v=EnuF9ZR6MVc psutil https://matt.sh/netmatt#_what-if-we-replaced-90s-c-netstat-with-python
* _notifications_: https://github.com/notifiers/notifiers
* _photos_: https://github.com/sedthh/pyxelate 
* _PDF_: https://realpython.com/pdf-python/ https://github.com/Halolegend94/pdf4py

## datetime

🗄️ `application.md` NTP
🛠️ https://github.com/python-humanize/humanize

---

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
