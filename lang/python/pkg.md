# ⛩️

## 参考

🗄 `linux.md` packaging
🔍 https://stackoverflow.com/questions/tagged/python-packaging

## 进步

* _24_: create own file
* _19_: lib (pipx, Poetry, pyinstaller)

# 📮 DISTRO

---

PYPI ALTERNATIVES
* internal https://www.pythonpodcast.com/pulp-with-bihan-zhang-and-austin-macdonald-episode-168/ https://twitter.com/brianokken/status/1402631045107707908
* external https://peps.python.org/pep-0759/ https://realpython.com/podcasts/rpp/227/

* _distribution_: archived package (lib) or binary (executable) https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 6:00 distribution != release https://pydist.com/blog/distributions-vs-releases
* _how to_: create archive and put on PyPI https://pgjones.dev/blog/packaging-without-setup-py-2020 https://packaging.python.org/guides/tool-recommendations/#packaging-tool-recommendations don't delete a build from PyPI https://pydist.com/blog/never-delete-a-release https://dustingram.com/articles/2019/04/02/pypi-as-a-service/ https://snarky.ca/how-do-you-verify-pypi-can-be-trusted/ https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 14:30 https://www.youtube.com/watch?v=P3dY3uDmnkU https://www.python.org/dev/peps/pep-0518/ PyPI doesn't have good search mechanism https://github.com/pipxproject/pipx/issues/249#issuecomment-636019556 https://jwodder.github.io/kbits/posts/pypkg-mistakes/ https://news.ycombinator.com/item?id=26733423 fix bad release https://snarky.ca/what-to-do-when-you-botch-a-release-on-pypi/
* example https://github.com/tfeldmann/simplematch
* _deprecation_: https://www.dampfkraft.com/code/how-to-deprecate-a-pypi-package.html https://blog.ovalerio.net/archives/1971 https://sirupsen.com/shitlists/
* _PyPI_: security https://github.com/gitpython-developers/GitPython
* browser https://github.com/wasi-master/pypi-command-line
* alternative https://pyoven.org/
* find old versions https://pypi-browser.org/
* warnings, PYTHONWARNINGS https://www.reddit.com/r/learnpython/comments/a14ow5/psa_when_developing_set_pythonwarnings/ https://docs.python.org/3/using/cmdline.html#cmdoption-w https://www.youtube.com/watch?v=X0AjcpicNOM&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=35

## executables

📜 https://peps.python.org/pep-0711/ https://news.ycombinator.com/item?id=35687895 https://github.com/mitsuhiko/rye/discussions/6

ALTERNATIVES
* `python -m zipapp` https://www.pythonmorsels.com/cli-tools/
* https://github.com/cole-wilson/sailboat
* Beeware https://github.com/beeware/ https://www.youtube.com/watch?v=WjMDXDHBn1I
* _auto-py-to-exe_: https://pythonbytes.fm/episodes/show/160/your-json-shall-be-streamed
* _Bazel_: https://news.ycombinator.com/item?id=23338316 https://github.com/google/subpar
* _bbfreeze_: https://stackoverflow.com/a/29515965/6813490
* _Cython_: compiles to C extension and runs that https://tryexceptpass.org/article/package-python-as-executable/ http://shvbsle.in/computers-are-fast-but-you-dont-know-it-p1/
* _Nuitka_: https://tryexceptpass.org/article/package-python-as-executable/ https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/ https://snarky.ca/what-is-the-core-of-the-python-programming-language
* _PEX_: https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/ https://news.ycombinator.com/item?id=42148220 https://github.com/pex-tool/pex
* _py2exe_: https://stackoverflow.com/a/5458807/6813490
* _Shiv_: https://pythonbytes.fm/episodes/show/114/what-should-be-in-the-python-standard-library https://jhermann.github.io/blog/python/deployment/2020/03/08/ship_libs_with_shiv.html https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/
* _XAR_: https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/

PYINSTALLER https://github.com/pyinstaller/pyinstaller https://realpython.com/pyinstaller-python/
* tldr: tars up src/interpreter, then upacks on user's computer and runs
* gets pkgs from your env
* i.e. pyinstaller needs to be installed into same env as the pkgs you want it to bundle
* i.e. can't have pyinstaller installed via pipx (which has it's own Python version) trying to bundle script that needs pkg that pipx doesn't know about
* i.e. pyinstaller is not pulling deps (either from script or lockfile) but rather finding them in your env
> PyInstaller reads a Python script written by you. It analyzes your code to discover every other module and library your script needs in order to execute. Then it collects copies of all those files - including the active Python interpreter! - and puts them with your script in a single folder, or optionally in a single executable file. https://pyinstaller.readthedocs.io/en/v4.9/operating-mode.html
* create binary: `pyinstaller -F <script.py>` https://pyinstaller.readthedocs.io/en/stable/usage.html#what-to-generate
```sh
├── dir
│   └── build  # for debugging https://realpython.com/pyinstaller-python/#build-folder
│   └── dist
│   └──── script_name  # what you give to user
```
* slow for CLIs than PyOxidizer
* supported 3rd party pkg https://github.com/pyinstaller/pyinstaller/wiki/Supported-Packages
* doesn't cross-compile https://stackoverflow.com/a/35878611/6813490
* works on M1 https://github.com/pyinstaller/pyinstaller/issues/5315
* playing nice with pyenv
```sh
$ pyinstaller main.py
OSError: Python library not found: Python, .Python, libpython3.8.dylib, libpython3.8m.dylib, Python3
* On Debian/Ubuntu, you need to install Python development packages:
* apt-get install python3-dev
* apt-get install python-dev
* If you are building Python by yourself, rebuild with `--enable-shared` (or, `--enable-framework` on macOS).
# https://stackoverflow.com/a/70795604 https://github.com/pyenv/pyenv/wiki#how-to-build-cpython-with-framework-support-on-os-x
$ env PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv install 3.5.0
```

PYOXIDIZER
* can now install Python as single executable as use that to run script!?! https://twitter.com/indygreg/status/1524041572173508608 https://gregoryszorc.com/blog/2022/05/10/announcing-the-pyoxy-python-runner/
* https://github.com/indygreg/PyOxidizer https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications
* 🚧 blocker w/ importing 3rd party packages https://github.com/indygreg/PyOxidizer/issues/69 https://tryexceptpass.org/article/package-python-as-executable/
* faster than PyInstaller for CLI https://pyoxidizer.readthedocs.io/en/latest/comparisons.html#pyinstaller https://pythonbytes.fm/episodes/show/138/will-pyoxidizer-weld-shut-one-of-python-s-major-gaps
* WIP https://news.ycombinator.com/item?id=23339970
* can produce binaries for all operating systems https://pythonbytes.fm/episodes/show/138/will-pyoxidizer-weld-shut-one-of-python-s-major-gaps
* https://www.pythonpodcast.com/pyoxidizer-python-package-creation-episode-282/

## publish

---

HOWTO 📙 https://pypackages.com/ 📜 https://docs.python.org/3/distributing/index.html https://www.manning.com/books/publishing-python-packages
* `MANIFEST.ini` https://chatgpt.com/c/67181d59-63f4-8004-ba67-ff251c9cb141
* fork https://github.com/zachvalenta/anytree https://github.com/zachvalenta/capp-prod-cat-alt
```toml
[tool.poetry.dependencies]
python = "^3.12"
anytree = {git = "https://github.com/zachvalenta/anytree.git"}
```
* PSF https://packaging.python.org/en/latest/tutorials/packaging-projects/
* Real Python https://realpython.com/pypi-publish-python-package/
* Poetry
* Twine https://github.com/pypa/twine
> see termgraph
> do people use? https://talkpython.fm/episodes/transcript/208/packaging-making-the-most-of-pycon-and-more
> tool to replace `stup.py` upload https://talkpython.fm/episodes/transcript/64/inside-the-python-package-index

### registries 🗄️ `frontend.md` packaging

* PyPI getting tied to Github https://news.ycombinator.com/item?id=42136375
* https://pythonbytes.fm/episodes/show/24/i-have-a-local-pypi-server-and-so-do-you
* stats https://pepy.tech/
* https://pypi.org/manage/account/
* https://test.pypi.org/
* compare to Golang and Rust https://crates.io/crates/basilk https://pypistats.org/packages/__all__ cargo https://github.com/ratatui/crates-tui
* local PyPI https://testdriven.io/blog/private-pypi/
```sh
# https://github.com/pywharf/pywharf https://stefan.sofa-rockers.org/2019/04/18/python-packaging-gitlab-conda/ https://pydist.com https://github.com/devpi/devpi
# create index
mkdir pypi-local

# populate index w/ pkg
pip3 download -r /Users/zach/Desktop/zvmac/materials/sw/lang/python/create-python-app/requirements.txt

# use index for new project
pip3 install --no-index --find-links=~/Desktop/pypi-local coverage
```

### Twine

---

* https://llm.datasette.io/en/stable/plugins/tutorial-model-plugin.html
* Flit, Poetry, Twine https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 16:00
* editable installs `pip install -e` https://pgjones.dev/blog/packaging-without-setup-py-2020 https://talkpython.fm/episodes/transcript/208/packaging-making-the-most-of-pycon-and-more https://llm.datasette.io/en/stable/plugins/tutorial-model-plugin.html

# 🧱 IMPORTS

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

----

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

* write an article on this and ask Brian Okken https://testandcode.com/52
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

# 📦 MGMT

🗄️ `linux.md` packaging / manager

## 24.12 workflow

```sh
├── pyenv
│   └── python
│   └──── pip
│   └──── pipx
```

I use pyenv to install Python itself. The whole can install multiple versions

## landscape

---

* https://www.b-list.org/weblog/2022/may/13/boring-python-dependencies/ https://www.b-list.org/weblog/2022/dec/19/boring-python-code-quality/

using Github URL like Golang https://github.com/seatgeek/thefuzz

https://pycon-archive.python.org/2024/schedule/presentation/61/index.html
> While other language ecosystems have a streamlined workflow that involves a single tool like Rust's Cargo and JavaScript's npm, maintaining Python projects has historically involved learning and using an ever-growing set of tools:
> packaging: distutils, setuptools, flit
> dependency management: pip, pip-tools, poetry
> Python management: pyenv, Homebrew, Windows store
> environments: virtualenv, tox, nox
> versioning: pbr, setuptools_scm, bump2version, versioneer
> builds: pip, build
> publishing: twine

ALTERNATIVES
* too many tools https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/#tooling-proliferation-and-the-python-package-authority dated https://www.amazon.com/dp/1098139585
* _hatch_: https://github.com/pypa/hatch https://github.com/juftin/browsr
* single contributor https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/
* good: no need for tox, separates deps by dev/test/link https://andrich.me/2023/08/switching-to-hatch/
* bad: no envs in project dir, no lockfile, no support for C extension modules, single contributor https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/
* _pdm_: smart people like https://github.com/pdm-project/pdm
* _pipenv_: Reitz problem https://github.com/pypa/pipenv/commit/9ba23242
* _piptools_: https://www.pythonpodcast.com/devops-in-python-episode-244/

---

https://dublog.net/blog/so-many-python-package-managers/

https://github.com/python-poetry/poetry/issues/8662

MORE ON ALTERNATIVES
* https://talkpython.fm/episodes/show/453/uv-the-next-evolution-in-python-packages
* https://chriswarrick.com/blog/2024/01/15/python-packaging-one-year-later/
* https://iahmed.me/post/python-air-gapped/
* https://talkpython.fm/episodes/show/436/an-unbiased-evaluation-of-environment-and-packaging-tools
* https://drivendata.co/blog/python-packaging-2023
* https://news.ycombinator.com/item?id=38196412
* https://www.b-list.org/weblog/2022/may/13/boring-python-dependencies/

## pip

📜 https://pip.pypa.io/en/stable/

* cmd
```sh
install $PKG==$VERSION
install $PKG --user  # per user

list  # global
list --user  # per user
show $PKG # pkg info

freeze > $FILE  # global
freeze --user > $FILE  # per user
```
* install from forked branch https://stackoverflow.com/questions/20101834/pip-install-from-git-repo-branch

---

```sh
python -m pip install -U --upgrade-strategy only-if-needed aider-chat  # https://aider.chat/docs/install/install.html

```
* freeze alternative https://github.com/bndr/pipreqs
* install from lockfile: `pip install -r requirements.txt`; run from inside activated virtualenv
* uninstall from requirements: `pip uninstall -r requirements.txt -y` https://stackoverflow.com/a/53032141
* require venv: `PIP_REQUIRE_VIRTUALENV=true` https://docs.python-guide.org/dev/pip-virtualenv/#requiring-an-active-virtual-environment-for-pip
* pinning w/ pip-tools https://lincolnloop.com/blog/python-dependency-locking-pip-tools
* pip-compile
```make
@echo "📦 DEPENDENCIES"
@echo
@echo "freeze:   	freeze dependencies into requirements.txt"
@echo "install:   	install dependencies from requirements.txt"
@echo "purge:   	remove any installed pkg *not* in requirements.txt"

freeze:
	pip freeze > requirements.txt

install:
	pip install -r requirements.txt

purge:
	@echo "🔍 - DISCOVERING UNSAVED PACKAGES\n"
	pip freeze > pkgs-to-rm.txt
	@echo
	@echo "📦 - UNINSTALL ALL PACKAGES\n"
	pip uninstall -y -r pkgs-to-rm.txt
	@echo
	@echo "♻️  - REINSTALL SAVED PACKAGES\n"
	pip install -r requirements.txt
	@echo
	@echo "🗑  - UNSAVED PACKAGES REMOVED\n"
	diff pkgs-to-rm.txt requirements.txt | grep '<'
	@echo
	rm pkgs-to-rm.txt
	@echo
```
* https://www.ianwootten.co.uk/2023/02/17/one-does-not-simply-pip-install/
* https://www.b-list.org/weblog/2023/dec/07/pip-install-safely/
* view dependency tree https://github.com/naiquevin/pipdeptree
* create: `python -m venv venv`; tied to fs location https://stackoverflow.com/q/32407365  📙 Van Rossum ch. 12
* `python3 -m venv venv; on; pip install -q --upgrade pip setuptools wheel; pip list` 🗄 `.bash_profile`
* activate: `source venv/bin/activate`; sets env var (`$VIRTUAL_ENV`) on activation
> When a virtual environment is active, the `VIRTUAL_ENV` environment variable is set to the path of the virtual environment. https://docs.python.org/3/library/venv.html#creating-virtual-environments
* cache venv in CI https://adamj.eu/tech/2023/11/02/github-actions-faster-python-virtual-environments/

* latest versions don't try to compile, will just get binary https://pythonspeed.com/articles/upgrade-pip
* checking for updates https://stackabuse.com/python-update-all-packages-with-pip-review/
* _upgrade_: `pip install --upgrade pip`
* _bundling_: comes w/ versions >= 2.7.9; don't install using os-managed Python https://pip.pypa.io/en/stable/installing/
* _view dependency tree_: https://github.com/naiquevin/pipdeptree https://github.com/zachvalenta/create-python-app/network/dependencies
* _virtual environment_: not installing into system or user-wise `site-packages` https://www.b-list.org/weblog/2020/jan/05/packaging/
* bash profile `venv` hack 🗄 `pip-venv-hack`
* _freeze_: `pip freeze > requirements.txt`
* _install from frozen_: `pip install -r requirements.txt`
* _fuzzy installs_: case insensitive (`flask-sqlalchemy` treated same as `Flask-SQLAlchemy` https://github.com/pallets/flask-sqlalchemy/) converts underscores to hyphen (`flask_whooshalchemy` same as `flask-whooshalchemy` https://github.com/gyllstromk/Flask-WhooshAlchemy https://www.youtube.com/watch?v=bAPcmGNsulc @ 0:55)
```diff
- /U/a/D/vue-firebase-master $ poetry add flask_whooshalchemy

Using version ^0.56 for flask_whooshalchemy
  - Installing blinker (1.4)
  - Installing whoosh (2.7.4)
  - Installing flask-whooshalchemy (0.56)

+ /U/a/D/vue-firebase-master $ poetry add flask-whooshalchemy

Using version ^0.56 for flask-whooshalchemy
  - Installing blinker (1.4)
  - Installing whoosh (2.7.4)
  - Installing flask-whooshalchemy (0.56)
```

* dependency resolver = hashed output like Poetry and pipenv? https://github.com/pypa/pip/issues/988
* `list` results matching PyPI https://github.com/pypa/pip/issues/7260
* _different versions_: can install different versions of dep e.g. `pip install flask-dance[sqla]` https://www.youtube.com/watch?v=MiHVTHzIgyE @ 1:15
* _bundled_: not part of stdlib but comes w/ Python install (since 3.4) via installer file (which means can update independently of Python version)
* `-editable`: meaning you can edit the source code of the pkg i.e. if you're developing a library and want to test out how it works without having to reinstall every time you update https://stackoverflow.com/a/35064498/6813490
* _invocation_: use `python -m pip` to ensure that you're using the version of `pip` bundled w/ the Python install https://stackoverflow.com/a/25749976/6813490
* _cache_: will check local before going to network https://pip.pypa.io/en/stable/reference/pip_install/#caching
* editable mode https://github.com/pallets/flask/blob/master/CONTRIBUTING.rst
* _conf_: `~/.config/pip/pip.conf` https://pip.pypa.io/en/stable/user_guide/#config-file
```conf
[global]
index-url = http://download.zope.org/ppix # CLI arg is `-i`
```
* https://pydist.com/blog/pip-install 

## pipx

📜 https://github.com/pypa/pipx

PKGS
```sh
pipx list --include-injected  # view injected pkg
pipx list --short  # view top-level pkg https://github.com/pipxproject/pipx/issues/390
```
* install into tmp env (like Nix) https://pipx.pypa.io/stable/#walkthrough-running-an-application-in-a-temporary-virtual-environment
* tmp/ephemeral: https://pipx.pypa.io/stable/#walkthrough-running-an-application-in-a-temporary-virtual-environment
```sh
pipx run pycowsay moo
```
* _inject_: add lib to CLI's env `pipx inject visidata psycopg2` https://jacobian.org/2019/nov/11/python-environment-2020/ https://pipx.pypa.io/stable/#inject-a-package 🗄 `html-css/drafts/dev/pipx-psycopg2.md`
```sh
pipx install visidata
pipx inject visidata psycopg2
```

INSTALLATION / FS
* install: Homebrew, pip https://pipx.pypa.io/stable/installation/ https://stackoverflow.com/a/70636663 https://packaging.python.org/en/latest/guides/installing-stand-alone-command-line-tools/
```sh
python3 -m pip install --user pipx
python3 -m pipx ensurepath
```
* config file: `~/Library/Application Support/pipx`
* venvs: `~/Library/Application Support/pipx/venvs`

GLOBAL DEPENDENCIES
* _global dependency_: something you'd use as a CLI (pipenv, AWS) https://jacobian.org/2018/feb/21/python-environment-2018/
* can always just use pip for user or even global install
* why: system Python no longer exposed https://news.ycombinator.com/item?id=29238700
* why not homebrew: when Python version upgrades it might lose track of the envs and you'll have to reinstall everything https://pythonbytes.fm/episodes/show/127/that-python-code-is-on-fire [14:00]
* how it works: `bin` symlinks to + script w/ shebang line scoped to local venv https://stackoverflow.com/a/30541898/6813490 https://pythonbytes.fm/episodes/show/123/time-to-right-the-py-wrongs

## Poetry

📜 https://python-poetry.org/docs/

FS
* config file: `~/Library/Application Support/pypoetry/config.toml`
* venvs: local (`$PROJ/.venv`) global (`~/Library/Caches/pypoetry/virtualenvs`)
> specify in VS Code https://stackoverflow.com/questions/59882884/vscode-doesnt-show-poetry-virtualenvs-in-select-interpreter-option https://code.visualstudio.com/docs/python/environments
```json
// https://github.com/zachvalenta/dotfiles-mini23/blob/main/vs-code/settings.json#L42
"python.defaultInterpreterPath": "path/to/.venv"
```

CMD
```sh
init -n        # create pyproject.toml
install        # install deps
add $PKG --group $GROUP  # dev https://python-poetry.org/docs/managing-dependencies/#adding-a-dependency-to-a-group
show --no-dev  # show prod deps
env info       # show Poetry env and where Poetry is installed (pipx)
remove -D      # remove dev dep
```

VS CODE SELECT INTERPRETER https://www.markhneedham.com/blog/2023/07/24/vscode-poetry-python-interpreter/
* open new, non-workspace window
* get path to venv `poetry env info --path | pbcopy`
* `select interpreter` > `enter interpreter path`
* can also use `"python.defaultInterpreterPath": "/Users/zach/Documents/zv/materials/sw/lang/python/mianshi/.venv"`?

UPDATE
* specific pkg https://github.com/orgs/python-poetry/discussions/3723
* all deps https://python-poetry.org/docs/basic-usage/#updating-dependencies-to-their-latest-versions
* Python version: `poetry env use $(which python)` https://stackoverflow.com/a/65589331
* manually specify Python version via `pyproject.toml` https://python-poetry.org/docs/basic-usage#setting-a-python-version https://stackoverflow.com/a/65589331

---

* create env - new project: `init - n` creates `pyproject.toml`; deps dir (macOS: `~/Library/Caches/pypoetry` RHEL: `~/.cache/pypoetry/virtualenvs`) and lockfile (`poetry.lock`; TOML) not created until you actually install something
* create env - existing project: `install` creates deps dir and installs deps using `poetry.lock` (if present) or `pyproject.toml` (if `poetry.lock` not present) https://poetry.eustace.io/docs/basic-usage/#installing-dependencies ❓ not being able to pick virtualenv name a problem https://hynek.me/articles/python-app-deps-2018/
* create env - existing project - prod: `install --no-dev` https://jacobian.org/2019/nov/11/python-environment-2020/
* rm env: `env remove 3.7`
> logic behind specifying version is that your project could support n versions, don't want to blanket rm all
> if no env associated w/ project dir output of `env info` will have `path` as `NA`
* activate env: `shell`
* _environment_: can put in project https://github.com/python-poetry/poetry/issues/1884
* _dependency resolution_: looks at `[tool.poetry.dependencies]` (which is just Python version) and finds dep version that works; presume for every pkg after the first has to do some voodoo to avoid transitive dep conflict
* _design_: distribution (`new <proj>` creates dir structure `init` asks for package name) inspired by Rust's Cargo https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 12:10
* `poetry.lock`: commit to version control https://poetry.eustace.io/docs/basic-usage/#commit-your-poetrylock-file-to-version-control merge conflics https://jokeyrhyme.github.io/2017/08/22/git-conflicts-and-lock-files.html https://www.peterbe.com/plog/how-to-resolve-a-git-conflict-in-poetry.lock
* `<proj>.egg-info`: doesn't need to be under version control https://stackoverflow.com/a/19377063/6813490
* w/ Django https://rasulkireev.com/managing-django-with-poetry
Poetry versions
* _installation_: docs say to use `curl` but `pipx` worked just fine for me https://jacobian.org/2019/nov/11/python-environment-2020/
* _update_: basic `self update` to beta `self update --preview`
* 1.0 backward compatible w/ 0.12 but not vice versa i.e. if you touch lock file w/ 1.0 then 0.12 won't be able to work with it
pkg versions
* update: `update <pkg>` https://python-poetry.org/docs/basic-usage/#updating-dependencies-to-their-latest-versions
```ini
[tool.poetry.dependencies]
python = "^3.6"
django = "^3.0.9"
# I updated to Django 3.1, poetry.lock changed but not pyproject.toml
# meaning pyproj will show minimum version but not necessarily actual version
```
format
* _import_: to go from `requirements.txt` is mostly manual https://jacobian.org/2019/nov/11/python-environment-2020/
* _export_: `export -f requirements.txt > req.txt` https://pythonspeed.com/articles/pipenv-docker/ only dev https://github.com/python-poetry/poetry/issues/1441 ignore https://github.com/python-poetry/poetry/issues/2010

> shell https://www.reddit.com/r/Python/comments/rjwr2d/moving_from_pipenv_to_poetry_or_pdm/
> using with pyenv https://jacobian.org/2019/nov/11/python-environment-2020/
| operation | dev        | prod          |
|-----------|----------- |---------------|
| init      | init -n    |               |
| install   | install    |               |
| add       | add -D     | add           |
| list      | show       | show --no-dev |
| dep dir   | env info   |               |
| rm        | remove -D  | remove        |
| run dep   |            | run <dep>     |

https://github.com/python-poetry/poetry/pull/7415
using inside docker https://ashishb.net/all/using-python-poetry-inside-docker/ https://codemageddon.me/post/poetry-docker/
* debug: `<cmd> -vvv`
* gotcha: project directory can't have same name as a dependency used by project https://github.com/python-poetry/poetry/issues/3438
* VS Code support https://github.com/microsoft/vscode-python/wiki/Support-poetry-virtual-environments
* can't show just top-level deps https://github.com/python-poetry/poetry/issues/1990
* `SolverProblemError` = conflict btw Python version in `[tool.poetry.dependencies]` and Python version required by dependency
```python
# run script using env
poetry run python script.py
# use dep as CLI
poetry run flask
```
* conf - list: `config --list`
* conf - file location: `~/Library/Application Support/pypoetry` https://python-poetry.org/docs/configuration/#configuration
* conf - set: `config virtualenvs.in-project true`
* venv - store as `.venv`: `config virtualenvs.in-project true` https://python-poetry.org/docs/configuration/#virtualenvsin-project
* venv - store as named: `~/Library/Caches/pypoetry/virtualenvs/`

* create env - new project: `venv` --- `poetry init -n`
* create env - existing project: `venv` + `pip install -r requirements.txt` --- `poetry install`
* create env - existing project - prod: ❌ --- `poetry install --no-dev`
* rm venv: `rm venv` ---  `env remove 3.7` 
* tree view: `make deps` --- `poetry show --tree`
* add dep - prod: `pip install <foo>` + `make freeze` --- `poetry add <pkg>`
* add dep - dev: ❌ --- `poetry add --dev <dep>`
* rm dep - prod: `pip uninstall <pkg>` + `make purge` --- `poetry remove <pkg>`
* rm dep - dev: ❌ --- `remove -D`
* add unsaved dep: `pip install <pkg>` --- ❌
* rm unsaved dep: `make purge` --- ❌
* view env: `ls` --- `poetry env info`
* list dep tree: `pipdeptree` --- poetry show --tree`
* can install a C compiler with pip https://news.ycombinator.com/item?id=31776873

## uv

📜 https://docs.astral.sh/uv/ https://github.com/astral-sh/uv
🗄️
* `linux.md` packaging
* `frontend.md` javascript > runtimes

VERSION MGMT
* via Python Build Standalone https://github.com/indygreg/python-build-standalone
* cross-platform https://astral.sh/blog/uv-unified-python-packaging
* inject https://github.com/astral-sh/uv/issues/7312 into shell scripts https://koaning.io/til/pyperclip/
* builds https://developers.home-assistant.io/blog/2024/04/03/build-images-with-uv/
* tmp/ephemeral
```sh
uvx posting
# won't work where install name diff than cmd name e.g. csvkit vs. in2csv https://github.com/wireservice/csvkit
```

DESIGN
* origins in Rye https://lucumr.pocoo.org/2024/2/15/rye-grows-with-uv/

---

https://blog.jetbrains.com/pycharm/2024/12/the-state-of-python/#trend-8-uv-takes-python-packaging-by-storm
https://treyhunner.com/2024/12/lazy-self-installing-python-scripts-with-uv/
build-standalone https://simonwillison.net/2024/Dec/3/python-build-standalone-astral/
scripts https://koaning.io/til/pyperclip/
build standalone https://gregoryszorc.com/blog/2024/12/03/transferring-python-build-standalone-stewardship-to-astral/
https://www.youtube.com/watch?v=8UuW8o4bHbw
https://www.youtube.com/watch?v=_FdjW47Au30
https://micro.webology.dev/2024/11/03/uv-does-everything.html https://pythonbytes.fm/episodes/show/409/weve-moved-to-hetzner-write-up
https://pythonbytes.fm/episodes/show/409/weve-moved-to-hetzner-write-up

> There was, over on Python Bytes, we covered this thing by Simon Willison, where he kind of summarized a Mastodon thread about UV and whether it being written in Rust is detrimental to the Python ecosystem or not and all of those things.  But I think it was there.  Your take was, look, fast is interesting.  But one of the really powerful things, I think, is here is a single binary that, if it's on your computer, you can do all things Python, right?  And right now, it's super, without UV, it's been really challenging, right?  Maybe I want to use pip-tools or I want to use pip to install something or all of those things are predicated on several steps.  Do you have Python?  Do you have a right version of Python?  Have you realized you've got to create a virtual environment because you don't have right access to where there's just, before you can get started, like, well, here's a whole set of conversations you need to have about not terribly complicated things, but things that people might not care about.  And now with UV, it's just UV, run.  And you can even put in the comment in the top, like, these are the three libraries I need to run.  And it'll just run.  Oh, so they don't break.  That's what I meant with the one binary, right?  Like, I think most of Python's bad reputation around packaging is that things just break.  Because Homebrew updated your Python or because you didn't activate your virtual length, accidentally installed something into your global thing.  Or you used pip install --user and now it's in all your virtual lengths and you don't know why.  And there's so much unpredictability around these things.  And now suddenly we have, like, this one thing that behaves in certain ways that people understand, that people expect it to behave.  As I said before, this is not necessarily the way I would like it to behave, but I understand why it's so important to just narrow the envelope of packaging of the behaviors that we expect and that we as a community endorse. https://talkpython.fm/episodes/transcript/481/python-opinions-and-zeitgeist-with-hynek

* https://github.com/fpgmaas/cookiecutter-uv


> read transcript https://talkpython.fm/episodes/transcript/476/unified-python-packaging-with-uv https://simonwillison.net/2024/Aug/20/uv-unified-python-packaging/

* controversial? https://pythonbytes.fm/episodes/show/403/a-machine-learning-algorithm-walks-into-a-bar
* https://bluesock.org/~willkg/blog/dev/switch_pyenv_to_uv.html
* https://simonwillison.net/2024/Sep/8/uv-under-discussion-on-mastodon/
* Docker https://mkennedy.codes/posts/python-docker-images-using-uv-s-new-python-features/?featured_on=pythonbytes
* https://news.ycombinator.com/item?id=41309072
* https://blog.glyph.im/2024/09/python-macos-framework-builds.html
* https://news.ycombinator.com/item?id=41302475
* project leadership https://github.com/astral-sh/rye/discussions/1342
* _uv_: early days, took over Rye, from creators of ruff https://rdrn.me/postmodern-python/
* https://astral.sh/blog/uv
* https://news.ycombinator.com/item?id=39387641
* https://lucumr.pocoo.org/2024/2/4/rye-a-vision/
* https://www.youtube.com/watch?v=_FdjW47Au30
* https://github.com/astral-sh/uv/releases/tag/0.4.0 
* Docker https://hynek.me/articles/docker-uv/
* still not there yet https://pythonbytes.fm/episodes/show/396/uv-ing-your-way-to-python
* https://talkpython.fm/episodes/show/476/unified-python-packaging-with-uv
* https://www.youtube.com/watch?v=zE-RigeEODM
* in Django https://blog.pecar.me/uv-with-django
* with Github Actions https://github.com/astral-sh/setup-uv https://pythonbytes.fm/episodes/show/405/oh-really
* https://www.bitecode.dev/p/uv-tricks

# 🟨️ ZA

## history / standards

> They leverage years and years of work that went into migrating the Python ecosystems from setup.py files to eggs and finally wheels. From not having a metadata standard to having one. From coupled to decoupled build systems. Much of what makes Rye so enjoyable were individuals that worked towards making redistributable and downloadable Python binaries a possibility. There was a lot of work that was put into building out an amazing ecosystem of Rust crates and Python libraries needed to make these tools work. All of that brought us to that point where we are today. https://lucumr.pocoo.org/2024/8/21/harvest-season/

PROGRESSION
* Python2 to Python3 https://www.pinecone.io/blog/pain-poetry-python/
* `setup.py`: https://github.com/freestream/pyedi
* _setuptools_: https://github.com/azoner/pyx12 not part of 3.12 https://chatgpt.com/c/6728df32-9ed8-8004-af28-b44b9bebb96c https://github.com/AnirudhG07/Typeinc/issues/3
* _egg_:
* _wheel_: https://llm.datasette.io/en/stable/plugins/tutorial-model-plugin.html
* _sdist_: https://llm.datasette.io/en/stable/plugins/tutorial-model-plugin.html

PEPS https://realpython.com/pypi-publish-python-package/#prepare-your-package-for-publication
* _PEP 427_: wheel packaging
* _PEP 440_: version number parsing
* _PEP 508_: specifying deps
* _PEP 517_: build backends
* _PEP 518_: specifying build systems
* _PEP 621_: specifying project metadata
* _PEP 639_: https://bsky.app/profile/hynek.me/post/3lc5n7g6kr22f https://pythonbytes.fm/episodes/show/411/tls-client-hello-guitar-solo
* _PEP 660_: editable installs
* _PEP 767_: read-only attributes https://peps.python.org/pep-0767/
* _PEP 735_: didn't Poetry already have this? https://pythonbytes.fm/episodes/show/406/whats-on-django-tv-tonight
* _PEP 751_: metadata https://lucumr.pocoo.org/2024/11/26/python-packaging-metadata/ https://discuss.python.org/t/pep-751-now-with-graphs/69721
* _PEP 777_: wheel backwards compatibility (to enable new functionality to be added to wheels) https://peps.python.org/pep-0777/

---

📍 great answer https://chatgpt.com/c/67111dbc-0964-8004-9e50-41fa41875da8

https://reinforcedknowledge.com/a-comprehensive-guide-to-python-project-management-and-packaging-concepts-illustrated-with-uv-part-i/

FORMATS
* _wheel_: binary https://pythonspeed.com/articles/upgrade-python-3.11/
* _Wheel_: `.whl`; current fmt, built by pip https://testandcode.com/52 @ 16:00 https://www.youtube.com/watch?v=02aAZ8u3wEQ https://realpython.com/python-wheels/ https://pythonwheels.com/
> also a package? see termgraph
* _sdist_: `tar.gz`; ❓ does PyPI need this along with `.whl` and why? https://poetry.eustace.io
* _egg_: `.egg` https://packaging.python.org/discussions/wheel-vs-egg/ https://pythonwheels.com/

📜 https://docs.python.org/3/installing/index.html

SEMANTICS
* _packaging_: blanket term for distribution, dependency mgmt, and environment mgmt https://www.b-list.org/weblog/2020/jan/05/packaging
* as synonym for distribution https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 7:10 https://talkpython.fm/episodes/show/245/python-packaging-landscape-in-2020
* _package_: dir containing modules https://docs.python.org/3/glossary.html#term-package
* _distribution_: getting your exec/lib to users
* _dependencies_: using others exec/lib

ZA
* large packages e.g. Tensorflow 12TB https://news.ycombinator.com/item?id=41633567
* _wheel_: prebuilt binary
> The reason for the exponential nature of that growth is simple: prebuilt binaries must be created for every combination of CPU architecture, OS, and sometimes also other things, like interpreter version. https://kristoff.it/blog/python-training-wheels/ https://news.ycombinator.com/item?id=41635441

DISTUTILS
* deprecated https://stackoverflow.com/a/77233866
* name of mailing list
> distutils is the original build and distribution system first added to the Python standard library in 1998. While direct use of distutils is being phased out, it still laid the foundation for the current packaging and distribution infrastructure, and it not only remains part of the standard library, but its name lives on in other ways (such as the name of the mailing list used to coordinate Python packaging standards development). https://docs.python.org/3/installing/index.html#key-terms

---

https://outlore.dev/blog/python-dev-2024/
https://burakku.com/blog/rye-test-and-python-tools/
https://chriswarrick.com/blog/2024/01/15/python-packaging-one-year-later/

* https://rdrn.me/postmodern-python/
* https://blog.glyph.im/2016/08/python-packaging.html
* https://dev.to/astrojuanlu/python-packaging-is-great-now-uv-is-all-you-need-4i2d
* https://www.bitecode.dev/p/whats-the-deal-with-setuptools-setuppy
* https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/
* https://snarky.ca/classifying-python-virtual-environment-workflows/ https://news.ycombinator.com/item?id=35131357
* https://pradyunsg.me/blog/2023/01/21/thoughts-on-python-packaging https://news.ycombinator.com/item?id=34467952
* https://aosabook.org/en/v1/packaging.html

PAST
* `setuptools`: uses `setup.py` to create distribution https://manikos.github.io/a-tour-on-python-packaging#mod_setuptools https://testandcode.com/52 @ 29:00 commonly thought of as distro tool but CLI (`easy_install`) was used for dep mtmt before `pip` https://dubroy.com/blog/so-you-want-to-install-a-python-package/ https://stackoverflow.com/questions/24727709/do-python-projects-need-a-manifest-in-and-what-should-be-in-it#24727824 for libraries https://github.com/pdm-project/pdm
* `setup.py`: specify what parts of library to expose to consumers for `distutils` https://www.pythoncheatsheet.org/#setup.py https://www.b-list.org/weblog/2020/feb/03/how-im-testing-2020/
* `setup.cfg`: hairer version of `setup.py` https://docs.python.org/3/distutils/configfile.html also used for app config https://github.com/pallets/flask/blob/master/setup.cfg

PRESENT
* _PEP 517_: API for build tools https://testandcode.com/52 @ 15:00
* _PEP 518_: https://testandcode.com/52 @ 14:00
* _pyproject.toml_: spec for using something other than `setup.py`; used by Poetry, Flit https://realpython.com/courses/packaging-with-pyproject-toml/ https://lincolnloop.com/insights/using-pyprojecttoml-in-your-django-project/ https://llm.datasette.io/en/stable/plugins/tutorial-model-plugin.html

* _PEP 517_: build backend https://github.com/pdm-project/pdm
* _PEP 582_: https://medium.com/@grassfedcode/goodbye-virtual-environments-b9f8115bc2b6 https://pythonbytes.fm/episodes/show/117/is-this-the-end-of-python-virtual-environments https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/
* _PEP 621_: how metadata should be represented in `pyproject.toml` https://github.com/pdm-project/pdm
* _location_: per project or all in `~`
* _sink_: using a Makefile https://github.com/sio/Makefile.venv https://realpython.com/python-virtual-environments-a-primer/

https://upcycled-code.com/blog/the-broken-version-breakdown/

pain points
* _transitive - resolution_: i.e. "is there (will there be if I bump this pkg) a transitive dep conflict?" https://docs.python-guide.org/starting/install3/osx/#pipenv-virtual-environments 
* _transitive - rm_: no porcelain to remove deps of deps https://github.com/invl/pip-autoremove ❓ does Poetry `remove` handle this?
* _split dev and prod_: https://github.com/algolia/algoliasearch-client-python/commit/33ff7a9ad39e5a0459795f171cf3424c815a7304  🗄 'Poetry'
* _figure out missing_: https://blog.piwheels.org/how-to-work-out-the-missing-dependencies-for-a-python-package/
* _uninstall unfrozen_: currently solving w/ Makefile `freeze` https://stackoverflow.com/q/13176968/6813490
* _no n versions of same pkg_: Ruby can do this https://pythonbytes.fm/episodes/show/127/that-python-code-is-on-fire @ 13:30

https://news.ycombinator.com/item?id=32258783
https://venthur.de/2021-06-26-python-packaging.html
https://pythonspeed.com/articles/distributing-software/ https://pgjones.dev/blog/trusted-plublishing-2023/ https://dev.to/ldrscke/trusted-publishing-it-has-never-been-easier-to-publish-your-python-packages-3dfn

🗄 `list-of-python-pkg-terminology.md`

* _sink_: http://andrewsforge.com/article/python-new-package-landscape/ http://aosabook.org/en/packaging.html  https://chriswarrick.com/blog/2018/07/17/pipenv-promises-a-lot-delivers-very-little/#id11 https://realpython.com/pipenv-guide/ https://www.reddit.com/r/Python/comments/aox5ah/moving_away_from_pipenv/ https://medium.com/@grassfedcode/five-myths-about-pipenv-698c5f198e4b https://medium.com/@DJetelina/pipenv-review-after-using-in-production-a05e7176f3f0 https://jacobian.org/2019/nov/11/python-environment-2020/ https://packaging.python.org/glossary/ https://manikos.github.io/a-tour-on-python-packaging#pip http://aosabook.org/en/packaging.html 

* _tldr_: dep mgmt and distro are intermingled cf. `setuptools`; even with things outside either cf. `setup.cfg` https://www.b-list.org/weblog/2020/jan/05/packaging/ ❓ should all apps also be packages from a 'this makes working with other Python constructs easier?' https://hynek.me/articles/python-app-deps-2018/

* `pyproject.toml` does both distro (replaces `setup.py`) and dep mgmt (`requirements.txt`, `Pipfile`, which is backend by the PyPA); tricky w/ Heroku https://jacobian.org/2019/nov/11/python-environment-2020/ https://snarky.ca/what-the-heck-is-pyproject-toml https://github.com/carlosperate/awesome-pyproject https://lincolnloop.com/insights/using-pyprojecttoml-in-your-django-project/ projects that use https://github.com/carlosperate/awesome-pyproject

## venv

* _venv_: use `bin` to make https://stackoverflow.com/questions/45293436/how-to-specify-python-version-used-to-create-virtual-2
* _virtual environment_: Python installation + pkgs [tutorial 12.1, Grinberg 4]
* _Docker_: shouldn't just use whole container as env https://hynek.me/articles/python-app-deps-2018/
* _history_: `venv` and `virtualenv` are not the same  ️https://docs.python.org/3/installing/index.html https://chriswarrick.com/blog/2017/07/03/setting-up-a-python-development-environment/#tools-and-management https://stackoverflow.com/a/49967371/6813490

## version mgmt (pyenv)

🗄 it / mpb 2014

PYENV 📜 https://github.com/pyenv/pyenv
* cmd
```sh
pyenv commands # list cmd
pyenv which python # list which version in use
pyenv versions # list installed versions
pyenv install -l # list versions available for install https://stackoverflow.com/a/58138512 upgrade pyenv to grab latest https://stackoverflow.com/a/43996315
pyenv local 3.9 # set local version (creates `.python-version` in $CWD)
pyenv global <ver> # set global version e.g. 3.9, system
pyenv which <library> # list library version https://realpython.com/intro-to-pyenv/#which
```
* how it works: wrapper that passes cmd to appropriate version http://akbaribrahim.com/managing-multiple-python-versions-with-pyenv/#how-pyenv-works https://rutar.org/writing/managing-python-versions-with-pyenv/
* Windows is a second-class citizen https://github.com/pyenv/pyenv#windows
* can use different interpreter (PyPy, Jython) https://realpython.com/intro-to-pyenv/
* install: Homebrew https://jacobian.org/2019/nov/11/python-environment-2020/ Linux https://mitelman.engineering/blog/python-best-practice/automating-python-best-practices-for-a-new-project/ https://drewdevault.com/2021/11/16/Python-stop-screwing-distros-over.html
* fs: `~/.pyenv/versions`
* setup
```sh
# create
pyenv virtualenv 3.8.5 project-3.8
# activate
. .pyenv/versions/project-3.8/bin/activate
# deps
pip install -r requirements.txt
```

---

```python
$ python -m site  # https://www.pythonmorsels.com/cli-tools/#site
$ python3.12 -m sysconfig | less  # https://www.pythonmorsels.com/cli-tools/#site

sys.path = [
    '/Users/zvalenta/Desktop',
    '/Users/zvalenta/.pyenv/versions/3.12.5/lib/python312.zip',
    '/Users/zvalenta/.pyenv/versions/3.12.5/lib/python3.12',
    '/Users/zvalenta/.pyenv/versions/3.12.5/lib/python3.12/lib-dynload',
    '/Users/zvalenta/.local/lib/python3.12/site-packages',
    '/Users/zvalenta/.pyenv/versions/3.12.5/lib/python3.12/site-packages',
]
USER_BASE: '/Users/zvalenta/.local' (exists)
USER_SITE: '/Users/zvalenta/.local/lib/python3.12/site-packages' (exists)
ENABLE_USER_SITE: True
```

Linux distros https://pythonspeed.com/articles/stop-using-python-3.8/

how to upgrade
> Luckily, Python 3 releases are fairly backwards compatible. So what you really want to do is: Upgrade to 3.9. Fix any bugs you find. Upgrade to 3.10, fix any bugs. Repeat until you hit Python 3.12, or perhaps even 3.13. https://pythonspeed.com/articles/stop-using-python-3.8/

NON-TRIVIAL
* new versions have syntax/features unsupported by other tools https://pythonspeed.com/articles/major-python-release/
* _PEP 394_: `python` should continue to point to OS version for comptability reasons https://github.com/sdispater/poetry/issues/536#issuecomment-507897724
* easy to shoot yourself in the foot https://xkcd.com/1987 but it's still your fault https://snarky.ca/deconstructing-xkcd-com-1987/
* too many versions on local https://www.hackerfactor.com/blog/index.php?/archives/825-8-Reasons-Python-Sucks.html
* Vincent https://talkpython.fm/episodes/show/190/teaching-django Guido https://twitter.com/brettsky/status/991172186911076352

OPTIONS
* ❌ system: pkg mgmt (yum) require own version https://realpython.com/intro-to-pyenv/#why-not-use-system-python
* ❌ macOS command line tools https://justinmayer.com/posts/homebrew-python-is-not-for-you/ https://docs.brew.sh/Homebrew-and-Python#python-3x
* ❌ PSF: no uninstaller https://chriswarrick.com/blog/2017/07/03/setting-up-a-python-development-environment/#macos https://docs.python.org/3/using/index.html 🗄 `psf-uninstall-problem.md`
* ❌ Homebrew: will update interpreter under your feet https://justinmayer.com/posts/homebrew-python-is-not-for-you/ https://realpython.com/intro-to-pyenv/#what-about-a-package-manager
* ❓ Anaconda
* ❓ nix; https://github.com/DavHau/mach-nix https://github.com/nix-community/poetry2nix
* ❓ asdf: https://justinmayer.com/posts/homebrew-python-is-not-for-you/
* ✅ pyenv

PYENV AT UNITED MASTERS
* macOS M1 issues https://news.ycombinator.com/item?id=26018722
* x86 brew to fix pyenv https://www.mejorcodigo.com/p/97778.html
```sh
if command -v pyenv 1>/dev/null 2>&1; then
    eval "$(pyenv init --path)"
fi
eval "$(brew shellenv)"
eval "$(pyenv init --path)"

# install brew x86_64
arch -x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# install brew arm64
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# alias Brew
alias brew86="arch -x86_64 /usr/local/Homebrew/bin/brew"
# install pyenv
brew86 install pyenv
# in case doesn't get linked add to the PATH brew86 dirs (consider to put it at the begining of your .zbashrc file)
export PATH=/usr/local/Homebrew/bin:/usr/local/Homebrew/sbin:$PATH
# install python through pyenv
pyenv install 3.8.5
# necessary?
$ brew86 install openssl readline sqlite3 xz zlib
```

VERSION INHERITANCE
> why are you not installing pipx via pyenv?
* Homebrew
* pipx: installed by Homebrew but can/will have different Python version as dependency
* Poetry: inherits from pipx
* project: inherits from Poetry (e.g. qing/send2trash)
```txt
get algos project working and align Python versions btw pyenv python and pipx python
* use pip to install poetry
* or use pip to install pipx
* read up https://stackoverflow.com/questions/68735503/how-does-pipx-know-which-python-version-to-use
```

ANACONDA
* just some random company https://chriswarrick.com/blog/2017/07/03/setting-up-a-python-development-environment/ https://paulromer.net/escaping-from-anaconda/
* replaced? https://github.com/mamba-org/mamba
* big in corporate envs bc built their own userland that handles python version + packaging https://news.ycombinator.com/item?id=39390246
* _conda_: pkg manager + Python version (400 MB)
* install via `miniconda`
* can install databases, non-Python pkg
* _anaconda_: all the pkgs (3 GB)
* install via `anaconda` https://stackoverflow.com/a/30057885/6813490
* ❓ mini/conda play nice w/ existing Python install? https://www.thisismetis.com/assets/files/Metis-Bootcamp-Curriculum-52f9979f4f638857bc185b0b788d6d832efb7f34d3b240e199dc6d3f2eef40ed.pdf
* https://mlpipes.com/changing-the-python-version-in-conda/ https://conda.io/docs/user-guide/install/index.html https://www.anaconda.com/blog/developer-blog/using-pip-in-a-conda-environment/ http://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/ http://www.sexchrlab.org/blog/2015/10/26/managing-multiple-python-environments-using-anaconda https://tdhopper.com/blog/my-python-environment-workflow-with-conda/ virtual env https://janakiev.com/til/jupyter-virtual-envs/
