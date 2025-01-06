# ⛩️

## 参考

📙 Shaw python internals https://www.amazon.com/dp/1775093344

## 进步

# 🐍 CPYTHON

📙 Shaw cpyton internals
🗄 `language.md` compilers

---


* auditing hooks https://stackoverflow.com/questions/63350394/how-to-set-up-and-use-python-audit-hooks https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP
> Python auditing hooks, introduced in version 3.8 through PEP 578, provide an excellent mechanism for monitoring and adding security to Python applications. These hooks can be used to detect and log specific runtime events, such as imports, file access, and network connections. The sys.addaudithook() function allows developers to register callbacks that will be triggered when certain events occur. For example, you can monitor file access or network requests made by third-party libraries to detect suspicious behavior or security vulnerabilities in real-time.

* `__pycache__`: holds bytecode in the form of `.pyc` https://stackoverflow.com/a/28365204/6813490 speeds up module loading https://docs.python.org/3/tutorial/modules.html#compiled-python-files suppress creation of with `export PYTHONDONTWRITEBYTECODE=1` more on bytecode https://blog.jse.li/posts/pyc/ https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md `python -m compileall` https://www.pythonmorsels.com/cli-tools/

* tabs vs. spaces https://www.pythonmorsels.com/cli-tools/#tabnanny

https://github.com/brandtbucher/specialist
Shannon plan, PEP 659, adaptive interpreter https://realpython.com/python311-new-features/#faster-code-execution

misc
* _portable_: https://www.scylladb.com/2019/02/14/the-complex-path-for-a-simple-portable-python-interpreter-or-snakes-on-a-data-plane/
* _optimization_: minimize function calls and obj attr lookup https://gregoryszorc.com/blog/2019/01/10/what-i've-learned-about-optimizing-python/
* why Python doesn't have `main()` https://news.ycombinator.com/item?id=23904313
* _sink_: https://realpython.com/cpython-source-code-guide https://hackernoon.com/has-the-python-gil-been-slain-9440d28fa93d https://realpython.com/run-python-scripts/#whats-the-python-interpreter https://snarky.ca/what-is-the-core-of-the-python-programming-language

* going faster https://talkpython.fm/episodes/show/339/making-python-faster-with-guido-and-mark
* https://www.freecodecamp.org/news/hacking-together-a-simple-graphical-python-debugger-efe7e6b1f9a8/ https://github.com/puremourning/vimspector
https://tenthousandmeters.com/blog/python-behind-the-scenes-6-how-python-object-system-works/
CPython 🗄 `cpython-internals.pdf` https://talkpython.fm/episodes/show/240/a-guided-tour-of-the-cpython-source-code https://github.com/python/cpython https://news.ycombinator.com/item?id=34570315
* _components_: stdlib in Python, core objects and IO in C
* _PVM_: virtual machine https://leanpub.com/insidethepythonvirtualmachine/read
* _CPython_: https://www.fluentpython.com/lingo/#CPython compiler (reference impl of lang spec) + PVM https://eli.thegreenplace.net/2010/09/18/python-internals-symbol-tables-part-1#id5; core written in C https://docs.python-guide.org/starting/which-python/#implementations libs written in Python https://realpython.com/python-logging-source-code/ how to contribute https://pythonbytes.fm/episodes/show/37/rule-over-the-shells-with-sultan internals https://log.beshr.com/python-311-speedup-part-1/
* _PEM_: execution model
* compiled to bytecode https://www.pythoninsight.com/2018/09/python-basics-bytecode/ https://snarky.ca/not-unravelling-generator-expressions/
* executes in the PVM https://realpython.com/run-python-scripts/#how-does-the-interpreter-run-python-scripts https://stackoverflow.com/q/441824/6813490 https://leanpub.com/insidethepythonvirtualmachine/read https://stackoverflow.com/q/6889747/6813490
* simplistic interpreter = C extensions = Python for datascience https://lucumr.pocoo.org/2018/7/13/python/
* can write extensions in Rust https://towardsdatascience.com/nine-rules-for-writing-python-extensions-in-rust-d35ea3a4ec29 https://github.com/RustPython/RustPython
* _bytecode_: https://opensource.com/article/18/4/introduction-python-bytecode https://nullprogram.com/blog/2019/02/24/ https://snarky.ca/unravelling-attribute-access-in-python/ https://www.youtube.com/watch?v=QU158nGABxI 23:00 28:30 https://docs.python.org/3/glossary.html#term-bytecode
* compiler execution flow: Python src to bytecode, VM runs bytecode https://eli.thegreenplace.net/2012/03/23/python-internals-how-callables-work https://eli.thegreenplace.net/2010/06/30/python-internals-adding-a-new-statement-to-python/
> CPython bytecode is evaluated by the the mammoth function PyEval_EvalFrameEx in Python/ceval.c. The function is scary but it's nothing more than a fancy dispatcher of opcodes.

## alternatives

---

* unique insofar as has to fit many use cases (web, CLI, security) https://talkpython.fm/episodes/show/265/why-is-python-slow 47:00
* things that need to be fast will be written in C https://talkpython.fm/episodes/show/265/why-is-python-slow 50:00
* _pypy_: JIT, supports Python 2 https://news.ycombinator.com/item?id=22928030 http://aosabook.org/en/pypy.html https://ao.gl/when-your-python-code-is-much-faster-with-pypy/ https://www.reddit.com/r/Python/comments/bv50uz/is_anyone_using_pypy_on_production/ https://realpython.com/pypy-faster-python/ https://avi.im/blag/2021/fast-sqlite-inserts/ 📙 Beazly 595
* pypy is dead https://news.ycombinator.com/item?id=33330706
* _numba_: just add annotation https://news.ycombinator.com/item?id=34148455 https://talkpython.fm/episodes/show/265/why-is-python-slow 37:00 https://news.ycombinator.com/item?id=30205848 📙 Beazly 595 https://calmcode.io/course/numba/introduction
* _pyjion_: https://talkpython.fm/episodes/show/340/time-to-jit-your-python-with-pyjion
* _Cython_: write Python, get perf of C++ 🗄 'executables' https://www.peterbaumgartner.com/blog/intro-to-just-enough-cython-to-be-useful/ 
* other transpiled-to-C https://news.ycombinator.com/item?id=29253039 https://github.com/zanellia/prometeo
* _others_: Jython (Java) Iron Python (.NET) call Go from Python https://opendatagroup.github.io/development/2019/06/13/go-ffi.html
* _HPy_: 💀 replacement C API for CPython, out of steam https://hpyproject.org/ https://github.com/hpyproject/hpy https://news.ycombinator.com/item?id=41755183
> Much faster on alternative implementations such as PyPy, GraalPy.
> Debug mode: in debug mode, you can easily identify common problems such as memory leaks, invalid lifetime of objects, invalid usage of APIs. Have you ever forgot a Py_INCREF or Py_DECREF? The HPy debug mode can be activated at runtime to detect these mistakes for you on universal binaries.
> Nicer API: the standard Python/C API shows its age. HPy is designed to overcome some of its limitations, be more consistent, produce better quality extensions and to make it harder to introduce bugs.
> Evolvability: As nicely summarized in PEP 620 the standard Python/C API exposes a lot of internal implementation details which makes it hard to evolve the C API. HPy doesn't have this problem because all internal implementation details are hidden.
* _SPy_: https://www.youtube.com/watch?v=hnQ0oJ_yXlw

## compilation

STAGES https://www.youtube.com/watch?v=QU158nGABxI 25:30
* parse https://www.pythonpodcast.com/cpython-parser-replacement-episode-285/
* compile
* execute (interpreter loop)

* actually compiled https://realpython.com/build-a-blog-from-scratch-django/
* foreign functions https://arturdryomov.dev/posts/python-foreign-functions-and-steam/
* production build won't run asserts https://docs.python.org/3/using/configure.html#python-debug-build
* _Cinder_ https://news.ycombinator.com/item?id=36621027

### JIT

---

> A just-in-time, or JIT, compiler provides a kind of middle ground, where the interpreter may choose to compile some code while a program is running in order to speed it up. In Python 3.13, there’s a new, experimental JIT compiler. The fact that it’s experimental means that it’s present in Python’s source code, but it’s not enabled by default. Python’s JIT compiler is based on an algorithm called copy-and-patch. The interpreter will look for patterns in your code that match pre-compiled templates and fill in the machine code with specific information like memory addresses of variables. https://realpython.com/python313-new-features/
* _perf_: https://pycon-archive.python.org/2024/schedule/presentation/69/index.html
* https://news.ycombinator.com/item?id=41677131
* https://realpython.com/python313-free-threading-jit/
* https://drew.silcock.dev/blog/everything-you-need-to-know-about-python-3-13/

## extensions

📙 Beazley ch. 15

> Python was really designed originally, from what I understand, to be a kind of glue language between different C programs. https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python

---

* howto https://kenschutte.com/python-swap-ints/
* simplistic interpreter = C extensions = Python for datascience https://lucumr.pocoo.org/2018/7/13/python/
* can write extensions in Rust https://towardsdatascience.com/nine-rules-for-writing-python-extensions-in-rust-d35ea3a4ec29 https://github.com/RustPython/RustPython https://blog.jerrycodes.com/python-trends-in-2023/ https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/ https://github.com/fulcrum-so/ziggy-pydust https://pythonspeed.com/articles/intro-rust-python-extensions https://pythonspeed.com/articles/intro-rust-python-extensions/
* Rust https://rustpython.github.io/
* using other language in Python e.g. Julia https://www.peterbaumgartner.com/blog/incorporating-julia-into-python-programs/

### 🦀 PyO3

📜 https://github.com/pyo3/pyo3

```python
#[pyfunction]
fn single_name_to_first_last_names() -> &PyAny {}
```
* https://www.youtube.com/watch?v=UilujdubqVU
> PyO3 is a Rust crate that allows you to write Python modules in Rust. It handles type conversion between Python and Rust, making it easy to call Rust functions from Python. You can use PyO3 to wrap Rust logic (including ORM operations) and expose it as a Python module.

MATURIN
> Maturin simplifies the process of compiling Rust code into Python-compatible packages. This tool builds Rust libraries as Python packages (wheels) that can be installed and imported like any other Python module.
> Cargo is the thing that Rust people will be using to compile these things. But you can't just use that on your own because you need the whole pip installing kind of side of things. So you can use Cargo and just create an extension module, but then you need to like give it the right name and copy it into the right place. So there's a bit of kind of gluing that needs to happen. And that is what Maturin is for. https://talkpython.fm/episodes/show/487/building-rust-extensions-for-python

> One point I want to make is, I think that's really interesting, David, to say that, hey, there's this whole equivalent of PyPI called Cargo, or you can get these libraries just like we can, I mean, sorry, that you install with Cargo, that you can get all these pre-built, pre-tested libraries and maybe just put a wrapper on them and do some amazing stuff. https://talkpython.fm/episodes/show/487/building-rust-extensions-for-python

CAN BE SLOWER THAN PYTHON https://pythonspeed.com/articles/faster-text-processing/
* overhead from obj conversion e.g strings (Rust uses UTF, CPython doesn't)
* Python APIs quite optimized, CPython's C can beat Rust e.g. CPython string repr differs based on contents, can use optimized impl specifically for ASCII

---

* https://us.pycon.org/2024/schedule/presentation/113/index.html
* https://pycon-archive.python.org/2024/schedule/presentation/113/index.html
* https://pythonspeed.com/articles/python-extension-performance/
* https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust

# 🌐 ECOSYSTEM

STDLIB
* new batteries in Rust https://baincapitalventures.com/insight/why-more-python-developers-are-using-rust-for-building-libraries/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* how libs get in https://github.com/hukkin/tomli/issues/141#issuecomment-997999824

PEPS https://peps.python.org/
* _0_: establish what a PEP is
* _8_: style guide
* _20_: Zen of Python
* _387_: no promise of backwards comptability https://news.ycombinator.com/item?id=26826158

## contributing

* https://medium.com/@Captain_Joannah/so-you-want-to-contribute-to-cpython-gather-here-5a2694148ca4
* http://emilyemorehouse.com/blog/015-my-path-to-becoming-a-python-core-developer/
* http://lukasz.langa.pl/cv/
* https://paper.dropbox.com/doc/Contributing-to-CPython--AuND60K_lABiNS7PHp0KZ9hoAg-JlgnduI6kw9MJIaGPpN9G
* https://mariatta.ca/posts/perks-of-python-core/
* https://nedbatchelder.com/blog/201306/explaining_descriptors.html
> Please give me space and don't shove. IMO some of the past posts on this subject are border-line abusive, leaving me feeling hounded and degraded (especially with respect to my writing style). Please be kind and let me continue to improve my contribution at my own pace. https://bugs.python.org/issue17894

## design

---

* https://snarky.ca/tag/syntactic-sugar/
📜 https://docs.python.org/3/faq/design.html
* has no formal spec https://www.pythonpodcast.com/cpython-formal-specification-episode-288/
* _Python_: language spec; very much tied to CPython e.g. metaclasses https://news.ycombinator.com/item?id=23698846
* history: origins in ABC https://www.fluentpython.com/lingo/#ABC
* readabillity: indentation for statement grouping via significant white space vs. semi-colons https://news.ycombinator.com/item?id=34936023
* simplicity: `python -m this` https://peps.python.org/pep-0020/ `python -m antigravity` https://xkcd.com/353/
* pain points: binaries, import system, version management, packaging, browser, native (mobile, desktop), speed (not built for multi-core https://twitter.com/mitsuhiko/status/1091802711908106240)
* https://lukeplant.me.uk/blog/posts/pythons-disappointing-superpowers/

## usage

💡 second-best for everything

* why not: typing, concurrency, perf
> Python (which was the right initial choice because of our founding CTO’s technical background, but its concurrency support, performance, and extensive dynamism make us question whether it’s the right choice for a large-scale backend codebase). None of these was a major mistake, and for some (e.g. Python) the downsides are minimal enough that it’s cheaper for us to continue to pay the increased maintenance burden than to invest in migrating to something theoretically better, but if we were starting a similar codebase from scratch today we’d think hard about whether they were the right choice. https://danluu.com/simple-architectures/
* popularity https://realpython.com/preview/python-news-november-2024/
* in the browser: pyodide https://pycon-archive.python.org/2024/schedule/presentation/92/index.html https://github.com/pyscript/pyscript
* teaching: Jupyter
* web: Django, Flask, FastAPI
* sys admin: Ansible, scripting
* ML: data science, pytorch
* security: network hacking, scraping
* microcontrollers
* industrial automation https://www.pythonpodcast.com/episode-114-industrial-automation-with-jonas-neubert/
* finance https://www.openbb.co/
* architecture https://talkpython.fm/episodes/show/342/python-in-architecture-as-in-actual-buildings
* GPU simulation https://news.ycombinator.com/item?id=40680737
* game engine https://github.com/kitao/pyxel https://blog.garambrogne.net/pyxel-initiation-en.html https://github.com/Broderick-Westrope/tetrigo
* mesh analysis https://github.com/pyvista/pyvista
* browser https://www.youtube.com/watch?v=Vh77_2-Z0vc

## governance

* corporate: internal language team at Google https://news.ycombinator.com/item?id=40176338
* quasi-official: PyPA, PyCQA
* people: Donald Stuft (PyPA) Raymond Hettinger (core) Tim Peters (Zen of Python `import this`, Timsort) Armin Ronacher (Flask) Brett Cannon (core) Nick Coghlan (core) Eli Bendersky (Google, buddies w/ Coghlan) https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* _Steering Council_: https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* _PSF_: https://simonwillison.net/2024/Sep/18/board-of-the-python-software-foundation/

# 🧱 IMPORTS

* `sys.path`: module search path = $CWD, `PYTHONPATH`, stdlib, `site-packages`
* _PYTHONPATH_: user modules
* _site-packages_: pip installs
```python
# or just view with pip CLI
import pkg_resources
for pkg in pkg_resources.working_set:
    print(pkg.key, pkg.version)
```

---

import linter https://talkpython.fm/episodes/show/487/building-rust-extensions-for-python
📙 Beazley ch. 10
📰 `py-repetitive-paths.md`
> didn't you email Robert Heaton about this?
📜 https://docs.python.org/3/reference/import.html https://docs.python.org/3/library/imp.html

NAMING
* _classes_: camel case
* _modules_: start w/ letter or underscore
* _pkg_: all seem to use hyphens instead of underscores https://stackoverflow.com/a/36611371
* case is significant https://www.python.org/dev/peps/pep-0008/#descriptive-naming-styles

ZA
* pkgutil https://docs.python.org/3/library/pkgutil.html https://chatgpt.com/share/19cfacb1-05ac-4339-a6c8-a8aa4bac6a80

* list user imported https://github.com/zachvalenta/algo-sandbox/blob/master/repl.py https://github.com/zachvalenta/dotfiles-mini23/blob/main/python/python_startup.py
* https://www.pythonmorsels.com/cli-tools/#how-m-works
> This is called an "import side effect" and most modules avoid import side effects. Fun Easter egg modules like antigravity and this are the exception. Modules that avoid import side effects need a different mechanism to change their behavior when run as a command-line script or when imported as a module. Python uses a __name__ variable to distinguish between importing a module and running a module as a script.
> When Python runs a module as a script, it sets the module's name to the string "__main__" (normally __name__ would contain the module's actual name). See more in defining a main function in Python. For packages, Python also looks for a __main__.py file to run (there's one in the zipfile package for example). This distinction between module versus script allows for some really nifty command-line tools.

`__all__` https://www.gauge.sh/blog/the-trouble-with-all https://github.com/gauge-sh/tach

> When a Python module or package is imported, __name__ is set to the module's name. Usually, this is the name of the Python file itself without the .py extension: `import configparser; configparser.__name__` https://docs.python.org/3/library/__main__.html
> __main__ is the name of the environment where top-level code is run. "Top-level code" is the first user-specified Python module that starts running. It's "top-level" because it imports all other modules that the program needs. Sometimes "top-level code" is called an entry point to the application. https://docs.python.org/3/library/__main__.html

* happened to me when I was trying to import pandas in a dir named `to-csv` https://stackoverflow.com/a/36250354

https://nedbatchelder.com/blog/202405/one_way_to_fix_python_circular_imports.html
https://pythontest.com/fix-circular-import-python-typing-protocol/
https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/
* https://news.ycombinator.com/item?id=34727287

lazy https://lwn.net/Articles/917280/
https://twitter.com/bbelderbos/status/1598663617506734080
lazy https://talkpython.fm/episodes/show/369/getting-lazy-with-python-imports-and-pep-690

* types https://realpython.com/absolute-vs-relative-python-imports
```python
# relative = dot notation to specify location
from ..pkg import func

# absolute = 
# circular = 
```

* _absolute_: import from `sys.path`
* _relative_: specify location of module being imported relative to module doing the importing https://realpython.com/absolute-vs-relative-python-imports/ https://stackoverflow.com/q/1918539/6813490 https://stackoverflow.com/questions/14132789/relative-imports-for-the-billionth-time
* explicit vs. implicit https://realpython.com/absolute-vs-relative-python-imports/#relative-imports
❓ when do we need `.` for modules in same dir? https://www.youtube.com/watch?v=rGQKHpjMn_M @ 7:30
* _circular_: https://www.pythoninsight.com/2018/04/how-import-works-differently-in-python-3-5/ https://realpython.com/courses/python-imports-101/ https://seddonym.me/2019/05/20/meet-import-linter/

---

* https://rednafi.github.io/reflections/how-not-to-run-a-script-in-python.html
* people know they suck https://lucumr.pocoo.org/2018/7/13/python/
* speed up imports https://rednafi.github.io/reflections/caching-connection-objects-in-python.html
* _tldr_: most advice about import and project structure are for libraries (vs. apps or executables) https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 16:30
* _multiline_: use parens
* import from module in same dir: `from .module import SomeClass`
* get names defined in module: `dir(sys.modules[__name__])` https://stackoverflow.com/a/991158 🗄 `algos`

---

https://tenthousandmeters.com/blog/python-behind-the-scenes-11-how-the-python-import-system-works/
* _sink_: https://realpython.com/python-modules-packages https://docs.python.org/3/tutorial/modules.html#packages

* https://www.youtube.com/watch?v=rGYbrIf-y58
cool project https://github.com/dandavison/optimistic-reload
https://github.com/benawad/destiny
* https://github.com/ankur-gupta/rain
* https://github.com/Mckinsey666/bullet/blob/master/bullet/client.py
🔗 https://github.com/zachvalenta/python-imports
* FastAPI: imports, app structure, ASGI, Stack Overflow https://stackoverflow.com/questions/tagged/fastapi?tab=votes&pagesize=50 https://developer.mongodb.com/how-to/FARM-Stack-FastAPI-React-MongoDB
* Python imports
```sh
├── dir
│   └── __init__.py
│   └── foo.py
│   └── bar.py
```
```python
# __init__.py https://github.com/Mckinsey666/bullet/blob/master/bullet/__init__.py
from .foo import obj_bar
from .bar import obj_bar

# application code https://github.com/Mckinsey666/bullet/blob/master/DOCUMENTATION.md#using-bullet-objects-
from dir import Bullet, Check, YesNo, Input
```

* https://nedbatchelder.com/text/test3/test3.html#21
* https://fastapi.tiangolo.com/tutorial/sql-databases/ https://testdriven.io/courses/tdd-fastapi/ https://testdriven.io/blog/moving-from-flask-to-fastapi/
* https://github.com/dinsaw/kines/blob/master/tests/test_metrics.py
* https://www.b-list.org/weblog/2020/feb/03/how-im-testing-2020/
* https://chrisyeh96.github.io/2017/08/08/definitive-guide-python-imports.html
* clean up create-python-app https://testandcode.com/80 https://testandcode.com/81
* the origin of digging into imports again --> works for pytest...
```sh
drwxr-xr-x     - adcbtb9 17 Dec 14:03 .
.rw-r--r--@   28 adcbtb9 17 Dec 14:03 ├── .gitignore
.rw-r--r--@   30 adcbtb9 17 Dec 13:55 ├── array.py
.rw-r--r--  1.3k adcbtb9 17 Dec 14:03 ├── Makefile
.rw-r--r--   187 adcbtb9 17 Dec 13:55 ├── requirements.txt
.rw-r--r--@   74 adcbtb9 17 Dec 13:55 └── test_array.py
```
```python
# array.py
def say_hi():
    return "hi"

# test_array.py
from array import say_hi

def test_say_hi():
    assert say_hi() == "hi"
```
```Makefile
test:
	pytest -v test_array.py
```

* ...not for coverage https://coverage.readthedocs.io/en/coverage-5.0/ coverage changes `sys.path` https://github.com/pytest-dev/pytest-cov
```Makefile
test:
	coverage run -m pytest -v test_array.py
```
```sh
ImportError while importing test module '/Users/adcbtb9/Desktop/death-by-imports/test_array.py'.
Hint: make sure your test modules/packages have valid Python names.

Traceback:
test_array.py:1: in <module>
    from array import say_hi
    ImportError: cannot import name 'say_hi' from 'array' (Python.framework/Versions/3.7/lib/python3.7/lib-dynload/array.cpython-37m-darwin.so)
```

* modules are only executed once, at import @ 2.11 0:25
* `__init__.py` executed when pkg imported 📍 useful to put module attr into higher namespace @ 2.12 1:15
* seems like there's only direction for pkg structure for distro (lib, exec) and not app (web, daemon) and not the-as-of-yet unnamed third category (scripts with tests?)
* execute module `python3 -m <mod>`@ 2.12 1:20
* _relative imports_: import mod from pkg w/out specifying the full module path, have to use syntax `from .mod import name`, not supposed to use @ 2.12 1:30
* `__all__`: list of attr to export when `from mod import *` is used @ 2.12 2:10
* _regular pkg_: pkg as defined before introduction of namespace pkg https://www.python.org/dev/peps/pep-0420/#terminology
* _namespace pkg_: don't use `__init__.py`, exist when dir on `PYTHONPATH` matches import and no normal pkg does, "across multiple directories" seems to mean "filepath to pkg" https://www.python.org/dev/peps/pep-0420/#abstract @ 2.12 2:20
* _executable directory_: has `__main__.py`

MODULES 📙 Van Rossum ch. 6
* _module_: file containing Python [tutorial 6.0] https://docs.python.org/3/glossary.html#term-module
* _impl_: can be written in Python or C (`re`, mathematical libs) https://realpython.com/python-modules-packages/#python-modules-overview
* _types_: user-defined, third-party, stdlib (`itertools`) https://realpython.com/python-modules-packages/#python-modules-overview
* _script_: module meant to be directly executed https://realpython.com/run-python-scripts/#scripts-vs-modules
* _import time_: when the interpreter loads module [Fluent Python 7.185] once per interpreter session https://realpython.com/python-modules-packages/#reloading-a-module on module load the entire module is executed, not only the object imported https://www.youtube.com/watch?v=44PvX0Yv368 @ 3:15

ATTRIBUTES
* `__file__`: location from which file is imported https://realpython.com/python-modules-packages/#the-module-search-path
* `__name__`: evaluates at runtime to either module name (if imported) or `__main__` (if run as script)
* `__main__.py`: module required to make pkg callable (think `pytest`) https://alex.dzyoba.com/blog/python-import/
* `__path__`: shows where pkg looks for submodules [Smallshire structure 2.2 @ 1:45]
* `__all__`: kinda like `exports` in Node; Cookbook 10.2 https://realpython.com/python-modules-packages/#importing-from-a-package
```python
def foo(): pass
def bar(): pass
__all__ = ['bar']  # only export 'bar'
```

PACKAGES
* _package_: collection of modules https://docs.python.org/3/tutorial/modules.html#packages
* module that can contain other modules https://docs.python.org/3/reference/import.html#packages
* project w/ `setup.py` (PEP 517) https://github.com/pipxproject/pipx/issues/279#issuecomment-555254281 setup.py https://news.ycombinator.com/item?id=38067822
* project w/ `pyproject.toml` (PEP 518) https://github.com/pipxproject/pipx/issues/279#issuecomment-555254281

module search path https://docs.python.org/3/tutorial/modules.html#the-module-search-path
* 1 - stdlib: `sys.path`, PYTHONHOME https://docs.python.org/3/using/cmdline.html#envvar-PYTHONHOME
* 2 - CWD
* 3 - PYTHONPATH: exact dir vary per installation
* 4 - site-packages

__types__

* _regular pkg_: pkg w/ `__init__.py`
* _namespace pkg_: pkg w/out `__init__.py`; since Python 3.3
* `__init__.py`: still recommended bc more explicit; useful for initialization logic

> When a package is imported, Python runs all of the code in the package’s `__init__.py` file, if such a file exists. All of the objects defined in the module or the package’s `__init__.py` file are made available to the importer.

> You can set up this `__init__.py` file in a way that enables you to import classes and methods from the package as a whole, instead of knowing the internal module structure and importing from `helloworld.helloworld` or `helloworld.helpers` https://realpython.com/python-application-layouts/#one-off-script

__get Python to find your pkg (here be dragons)__

* put your pkg in dir contained in `sys.path` [https://realpython.com/python-modules-packages/#the-module-search-path, Smallshire structure 3.1 @ 1:30] 
* ⚠️ edit `sys.path` at runtime https://realpython.com/python-modules-packages/#the-module-search-path 
* ⚠️ edit env var https://orbifold.xyz/pythonpath.html
* `context.py` file inside test suite https://docs.python-guide.org/writing/structure/#test-suite
* um, avoid it? https://alex.dzyoba.com/blog/python-import/ https://chrisyeh96.github.io/2017/08/08/definitive-guide-python-imports.html#case-4-importing-from-parent-directory 

## exec

📜 https://docs.python.org/3/using/cmdline.html

COMMAND LINE
```sh
python $MODULE  # exec module https://realpython.com/run-python-scripts
python -i $MODULE  # enter pdb after exec https://docs.python.org/3/using/cmdline.html#cmdoption-i
python -m $LIB  # exec lib as cmd https://www.pythonmorsels.com/cli-tools/#how-m-works
python -m $LIB $CMD  # exec lib cmd https://docs.python.org/3/using/cmdline.html#cmdoption-m
python -c "import $MOD; $MOD.$METHOD()"  # exec inline https://docs.python.org/3/using/cmdline.html#cmdoption-c
python -c "from home import foo; foo.bye()"  # exec module w/in dir
```

CALLABLE FROM TERMINAL
* standard
```sh
#!/usr/bin/env python3 https://docs.python.org/3/tutorial/appendix.html#executable-python-scripts
```
* third-party: symlink from bin to Python repo + shebang to local venv e.g. m2h https://github.com/zachvalenta/bin-mbp14
```sh
.gitignore  # ignore repos
huan  # bash script
news -> repos/news/main.py  # sym link to subrepo
```
```python
#!/Users/zach/Documents/denv/bin/repos/news/.venv/bin/python
```

---

https://pythonbytes.fm/episodes/show/367/a-new-cloud-computing-paradigm-at-python-bytes https://peps.python.org/pep-0723/

## namespaces

---

__people know that the import system sucks__
http://lucumr.pocoo.org/2018/7/13/python/
> The fact that most methods of invoking Python code from the command line break when that code is inside a package, and the two that do work are highly sensitive to the current working directory is all thoroughly confusing for a beginner. I personally believe it is one of the key factors leading to the perception that Python packages are complicated and hard to get right. http://python-notes.curiousefficiency.org/en/latest/python_concepts/import_traps.html Nick Coghlan (CPython dev)
> The problem is that where on your system you need to put a Python library module in order so that a Python main program (or other library) can see it and load it varies in only semi-predictable ways. By version, yes, but there’s also an obscure distinction between site-packages, dist-packages, and what for want of any better term I’ll call root-level modules (no subdirectory under the version directory) that different distributions and even different application packages seem to interpret in different and incompatible ways. The root of the problem seems to be that good practice is under-specified by the Python dev team. - http://esr.ibiblio.org/?p=8161 Eric Raymond

__namespaces__
* `import foo` binds module obj `foo` to name `foo` in current namespace [Smallshire 1 @ 5.7 0:20]
* `import f` binds module obj `foo` to name `f` in current namespace
* `import mod`: place module itself into caller's symbol table; doesn't place `mod` private symbol table into the caller i.e. need to use dot notation to drill down to symbol table `mod.obj1` https://realpython.com/python-modules-packages/#the-import-statement
* `from <mod> import <obj>`: place obj from module into caller's symbol table https://realpython.com/python-modules-packages/#the-import-statement

* https://realpython.com/python-namespaces-scope/
* https://learndjango.com/tutorials/django-best-practices-imports
* https://realpython.com/python-import/
* https://github.com/dabeaz-course/practical-python/blob/master/Notes/Contents.md
* _import module from same directory_: `from .views import TemplateView` https://djangoforbeginners.com/pages-app/
* _import obj from module in sibling directory_: pkg.mod.Obj https://djangoforbeginners.com/hello-world/

## project structure

🔍 email to Robert Heaton
🗄️
*️ `doc.md` dev
* `golang.md` project structure
* `plt.md` Rust

---

* `src/$NAME`: https://github.com/Zaloog/kanban-tui
* https://github.com/mikeckennedy/listmonk
* https://github.com/copyleftdev/x12-edi-tools
* https://github.com/gergelyk/para-cada
* https://www.youtube.com/watch?v=niMybnzmzqc
* https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/
* even Prolog uses src/test https://github.com/dnmfarrell/dict
* dupe https://github.com/simonw/files-to-prompt
* https://github.com/fpgmaas/cookiecutter-uv
* https://www.youtube.com/watch?v=dlCcnJdh4c4

https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/

https://nedbatchelder.com/blog/202402/one_way_to_package_python_code_right_now.html

* rm support for previous Python version https://adamj.eu/tech/2022/01/11/removing-python-3.6-support-from-my-packages
* _library_: archived package for others to consume as dependency https://docs.python-guide.org/shipping/packaging/ https://pythonwheels.com/
* _history_: https://stackoverflow.com/a/14753678/6813490 https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 7:40
* _project structure_: `src`: https://blog.ganssle.io/articles/2019/08/test-as-installed.html https://pythonbytes.fm/episodes/show/159/brian-s-pr-is-merged-the-src-will-flow https://github.com/taktluyver/flit/pull/260/commits https://bskinn.github.io/My-How-Why-Pyproject-Src/ https://github.com/takluyver/flit/pull/260 https://bskinn.github.io/My-How-Why-Pyproject-Src/ repetitive paths https://github.com/zachvalenta/site-content/commit/7e6b5f66ffd9f6b3b13b19669050289b26d8925b

* https://github.com/MatteoGuadrini/psp
* example repo, awful $proj_name/src/proj_name duped dir thing https://github.com/brohrer/pacemaker https://github.com/darrenburns/posting https://stackoverflow.com/questions/50090341/is-there-a-naming-convention-for-django-project-configuration-directory
* structure https://www.pythonpapers.com/p/how-to-publish-a-python-package-to
* https://www.pybitespodcast.com/1501156/12592983-110-dane-hillard-on-python-packaging-and-effective-developer-tooling
* lockfile https://pythonbytes.fm/episodes/show/395/pythont-compatible-packages

## scope

🗄 `language.md` overloading

---

* local, nonlocal https://realpython.com/inner-functions-what-are-they-good-for/#encapsulation
* _nested scope_: https://docs.python.org/3/glossary.html#term-nested-scope
🔗 https://blog.araj.me/til-nonlocal-statement-in-python/ https://realpython.com/python-namespaces-scope/ https://muhammadraza.me/2023/Python-Namespace/

unbound local, formal parameter https://www.fluentpython.com/lingo/#parameter https://docs.python.org/3/glossary.html#term-parameter

`locals()`, `globals()` https://arpitbhayani.me/blogs/function-overloading
> Calling the function locals() after defining a function we see that it returns a dictionary of all variables defined in the local namespace. The key of the dictionary is the name of the variable and value is the reference/value of that variable. When the runtime encounters another function with the same name it updates the entry in the local namespace and thus removes the possibility of two functions co-existing. Hence python does not support Function overloading. https://arpitbhayani.me/blogs/function-overloading

* _scope_: namespace; doesn't correspond to code blocks e.g. `if` doesn't introduce nested scope
* _local_: current function https://realpython.com/python-pass-by-reference/#passing-arguments-in-python
```python
def loc():
    foo = 'foo val'
    print(locals())  # {'foo': 'foo val'}
```
* _global_: module (func/class, imports, var); can cast name to global but not recommended (not thread safe) https://realpython.com/python-pass-by-reference/#replicating-pass-by-reference-with-python
* _variable shadowing_: prevent access to same name in higher scope [Smalleshire 5.5 @ 2:30]; use `global` to refer to globally scoped name in event of shadowing
```python
foo = 'foo val'  # global foo
def fail_to_set_foo():
    foo = 'new val'  # local foo

fail_to_set_foo()
foo  # global foo untouched
```

## semantics

---

start here https://lucumr.pocoo.org/2024/9/9/multiversion-python/
* _import_: https://docs.python.org/3/glossary.html#term-importing
* _import path_: https://docs.python.org/3/glossary.html#term-import-path
* _importer_: https://docs.python.org/3/glossary.html#term-importer
* _finder_: https://docs.python.org/3/glossary.html#term-importer
* _loader_: https://docs.python.org/3/glossary.html#term-importer
* _module_: https://blog.nicholdav.info/four-tips-structuring-research-python/
* _module spec_: https://docs.python.org/3/glossary.html#term-module-spec 
* _namespace_: https://docs.python.org/3/glossary.html#term-namespace
* _namespace package_: https://docs.python.org/3/glossary.html#term-namespace-package https://realpython.com/python-namespace-package/
* _path entry_: https://docs.python.org/3/glossary.html#term-path-entry
* _meta path finder_: https://docs.python.org/3/glossary.html#term-meta-path-finder
* _path based finder_: https://docs.python.org/3/glossary.html#term-path-based-finder
* _qualified name_: https://docs.python.org/3/glossary.html#term-qualified-name
* _import time_: https://www.fluentpython.com/lingo/#import_time

## underscores

https://dbader.org/blog/meaning-of-underscores-in-python
* https://github.com/darrenburns/ward/tree/master/ward
* _single_: placeholder for throwaway values from unpacking
* in REPL, refers to result of last operation
* _single leading_: won't be imported in `from <mod> import *` https://stackoverflow.com/a/8689983
* _single trailing_: break naming conflict
* _double leading_: name mangling i.e. measure to prevent accidental overrides
* _doubled_: dunder methods
