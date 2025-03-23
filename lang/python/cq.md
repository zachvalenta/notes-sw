# ⛩️

## 参考

⭐️ https://github.com/stars/zachvalenta/lists/code-quality

## 进步

* _24_: ward
* _21_: doctest basics
* _19_: pytest

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

* impl https://nedbatchelder.com/blog/202411/coveragepy_originally.html
* alternative https://www.youtube.com/watch?v=X9aXWeLC_C0 https://github.com/plasma-umass/slipcover
* design: `sys.settrace` https://nedbatchelder.com/blog/202406/coverage_at_a_crossroads.html
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

RUNNING
```sh
python -m doctest -v my_mod.py
```
```python
doctest.testmod(ur_mod)
```

---

TRYING TO GET GOOD STDOUT
```python
def foo(a, b):
    """
    >>> foo(2, 3)
    5
    """
    return a + b

if __name__ == '__main__':
    import doctest
    print(f'\nDOCTEST SUMMARY: {doctest.testmod(verbose=True)}')
```
```txt
test: func_name
expect: 26.77
actual: 26.77
result: ✅ pass
```

https://hamatti.org/posts/document-intended-usage-through-tests-with-doctest/
* https://rdrn.me/postmodern-python/
* `ELLIPSIS` 📙 Ramalho [7]
* _doctest_: docstring + test https://www.fluentpython.com/lingo/#doctest
> [key feature] they look like transcripts of interactive Python console sessions, so you can easily try out the demonstrations yourself 📙 Ramalho [xviii]
* as TDD-as-design tool bc favors small functions that require minimal setup
* keep docstring aligned to src

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

📙 Okken https://www.amazon.com/gp/product/1680508601
📜 https://docs.pytest.org/en/latest/contents.html#toc

PLUGINS
* plugin metadata https://github.com/pytest-dev/pytest-metadata
* randomize execution order https://github.com/pytest-dev/pytest-randomly 
* port ward output to pytest https://github.com/darrenburns/ward/blob/master/ward/_terminal.py https://docs.pytest.org/en/7.1.x/how-to/writing_plugins.html#writing-your-own-plugin https://github.com/nicoddemus/pytest-rich/tree/main
* failure https://mathspp.com/blog/til/pytest-selection-arguments-for-failing-tests
* Markdown output https://testandcode.com/episodes/markdown-reports-pytest-md-pytest-md-report
* dump https://github.com/gaogaotiantian/coredumpy
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
* https://github.com/dbfixtures/pytest-postgresql
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

---

nox vs. tox https://www.youtube.com/watch?v=ImBvrDvK-1U
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

# 🟨 ZA

SECURITY
* _safety_: https://calmcode.io/shorts/safety.py
* _bandit_: https://github.com/PyCQA/bandit https://github.com/fetter-io/fetter-rs
* https://pyup.io/ (uses same vulnerability db as pipenv)
* _pysa_ https://github.com/facebook/pyre-check https://news.ycombinator.com/item?id=24083432
* https://github.com/DataDog/guarddog

## docstring

GETTING HELP
```python
ur_method??  # ipython magic
help(ur_module)
help(ur_func.__doc__)
```

STANDARDS
* I use JetBrains but there's also Google and numpy https://stackoverflow.com/a/40596167
* auto-generate tooling doesn't support JetBrains? https://github.com/NilsJPWerner/autoDocstring?tab=readme-ov-file#docstring-formats
```python
"""
This line is for an overview

:param arg1: desc of arg1
:return: desc of return

>>> doctest_here()
"""
```

SEMANTICS
* _doctring_: triple quoted string as first line of class/function https://www.fluentpython.com/lingo/#docstring
* 🎯 check for missing https://github.com/econchick/interrogate
* _TQS_: ignored if not a docstring, preferred over multi-line comment https://stackoverflow.com/a/7696966 https://docs.python.org/3/glossary.html#term-triple-quoted-string
* parsed by doc libraries e.g. pdoc

GENERATE DOCUMENTATION FROM
* _mkdocstrings_: https://mkdocstrings.github.io/
* _pdoc_: thing that pdoc3 forked from https://github.com/mitmproxy/pdoc
* _pdoc3_: https://pdoc3.github.io/pdoc/ some controversy https://github.com/pdoc3/pdoc/issues/64 https://github.com/pdoc3/pdoc/issues/87 even worse than first blush, apparently he is a fascist https://news.ycombinator.com/item?id=20800157
* _pdocs_: https://github.com/timothycrosley/pdocs/issues/3
* _portray_: built on pdoc3 https://github.com/timothycrosley/portray/
* _pydoc_: https://docs.python.org/3/library/pydoc.html https://stackoverflow.com/a/13043765/6813490 
* _pycco_: pretty but don't see use case https://pycco-docs.github.io/pycco/ https://realpython.com/generating-code-documentation-with-pycco/
* _Sphinx_: `sphinx-apidoc` 缺点 RST, not geared towards APIs https://realpython.com/courses/documenting-python-projects-sphinx-read-the-docs/ can now use Markdown https://www.youtube.com/watch?v=YclYtM56qjo&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=38

## lint / fmt (ruff)

🗄️ `core.md` style

RUFF 📜 https://github.com/astral-sh/ruff
* doesn't surface rules behind their formatting https://github.com/astral-sh/ruff/issues/15024
* meant to replace black, isort
```sh
check  # view lint err
check --fix  # fix lint err
format --diff  # view formatting err; be nice if associated rule was listed as well https://github.com/astral-sh/ruff/issues/15024
format  # fix formatting err
```

CONFIG
```toml
line-length = 125
[format]
quote-style = "single"
```
* prevent format
```python
# fmt: off
def foo()
# fmt: on
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

## logging (loguru)

🗄 `telemetry` logging

LOGURU 📜 https://github.com/Delgan/loguru
* log to stdout and file
```python
logger.remove()
logger.add(sys.stdout)
logger.add("validation.log")
```
* config stdout https://github.com/zachvalenta/capp-edi
```python
logger.remove()
logger.add(
    sys.stderr,
    colorize=True,
    format="<green>{level: <2}</green> | <cyan>{function: <12}</cyan>:<yellow>{line: <2}</yellow> | {message}"
)
```

ALTERNATIVES
* _eliot_: https://github.com/itamarst/eliot 
* _structlog_: https://github.com/hynek/structlog
* _tamga_: Tailwind https://github.com/dogukanurker/tamga

---

https://calmcode.io/course/logging/introduction
* hstdlib https://docs.python.org/3/howto/logging.html https://docs.python.org/3/howto/logging-cookbook.html GUI https://github.com/busimus/cutelog

* flush https://stackoverflow.com/a/51362214
https://rednafi.com/python/no_hijack_root_logger/
icecream for print debugging https://github.com/gruns/icecream
* people don't use format/f-strings in logging
* https://monadical.com/posts/ins-and-outs-of-logging-in-python-part-one.html
* logs sent by default to `sys.stdout` i.e. they're buffered https://stackoverflow.com/a/51362214/6813490 https://realpython.com/python-flush-print-output/
* pretty stdout https://github.com/onelivesleft/PrettyErrors
* can unbuffer w/ `PYTHONUNBUFFERED=1` https://docs.python.org/3/using/cmdline.html?highlight=pythonunbuffered#envvar-PYTHONUNBUFFERED
* Docker won't show logs from Flask dev server in real-time unless logs set to unbuffered although I don't know why https://github.com/sclorg/s2i-python-container/issues/157 https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
* add logs without updating source https://github.com/yiblet/inquest

## stats

* Python2 https://chatgpt.com/c/6717c005-9560-8004-8240-a612fd00792e
* stats: https://github.com/boyter/scc https://github.com/XAMPPRocky/tokei https://github.com/k1LoW/octocov
* dead code: https://github.com/jendrikseipp/vulture https://github.com/sobolevn/flake8-eradicate
> does ruff do this?

## style

🗄️ `stdlib.md` lint/fmt
📜 https://peps.python.org/pep-0008/ https://github.com/google/styleguide/blob/gh-pages/pyguide.md

* string quotes: single|double both fine https://peps.python.org/pep-0008/#string-quotes black/ruff use double quotes https://github.com/astral-sh/ruff

---

* _line continuation_: "join consecutive lines if the last character of the line is a backslash" [HG 3.2.5 pg. 56] can use parens https://stackoverflow.com/a/53180/6813490
* PEP8 error codes https://pep8.readthedocs.io/en/release-1.7.x/intro.html#error-codes
* line length http://jakevdp.github.io/blog/2017/11/09/exploring-line-lengths-in-python-packages/
* https://nickjanetakis.com/blog/80-characters-per-line-is-a-standard-worth-sticking-to-even-today
* blank lines: 2 after imports, 2 before functions, 1 before methods https://www.python.org/dev/peps/pep-0008/#blank-lines
