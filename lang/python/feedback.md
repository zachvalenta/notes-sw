# ⛩️

## 参考

📙 Van Rossum ch. 2, 14
🗄
* `databases.md` tooling
* `education.md` design

## 进步

* https://davidvujic.blogspot.com/2025/04/feedback-loops-in-python.html
* can run Jupyter in the terminal!?! https://github.com/joouha/euporie https://zed.dev/docs/repl
> Marimo has the ability to run in WASM mode, which means that *everything* can run from the frontend
* https://www.answer.ai/posts/2024-12-13-nbsanity.html
* as dashboard https://news.ycombinator.com/item?id=43766200
* Jupyter in the browser https://github.com/jvns/pandas-cookbook
* rich live view, jupylab in the terminal, async, segments and triangles https://talkpython.fm/episodes/show/498/algorithms-for-high-performance-terminal-apps
```sh
# execute from shell
jupyter nbconvert --to notebook --execute --stdout nb.ipynb > /dev/null
```

```txt
Exactly! Your problem has several layers:
* IPython installed globally, raising virtualenv warnings
* Base PYTHONSTARTUP depends on rich/loguru, also installed globally
* When running in a project virtualenv, that startup can't access those global packages

You've basically hit the core tension between:
* Wanting a rich global REPL environment with helpful tools
* Wanting clean, isolated project environments

Options:
* Accept installing rich/loguru/ipython in every project
* Make the base startup more minimal, only using stdlib
* Create a "REPL utilities" package that you can install in projects that need it
* Skip virtualenv isolation just for REPL sessions
```
```python
# repl-utils/pyproject.toml
[project]
name = "repl-utils"
version = "0.1.0"
dependencies = [
    "rich",
    "loguru",
    "ipython"
]

[project.optional-dependencies]
dev = ["pytest"]
```
```python
# repl-utils/repl_utils/__init__.py
from pathlib import Path
import os
import sys
import json

from loguru import logger
from rich import pretty, traceback, print as rprint
from rich import inspect as ins

def setup_repl():
    """Configure REPL environment"""
    pretty.install()
    traceback.install(show_locals=False)
    
def ri(obj):
    """inspect obj with Rich and show methods"""
    return ins(obj, methods=True)

# ... rest of your current utilities ...
```
```python
# ~/.pythonrc.py
from repl_utils import setup_repl, ri, chuan, dump, qiu, vars, jk
setup_repl()
logger.info("loading base startup")
# Project startup loading logic...
```
```python
[tool.poetry.group.dev.dependencies]
repl-utils = {path = "/path/to/repl-utils"}
```

OPTIONS
* REPL
* repo + comments: based on REPL history
* notebook: when you want to share

* look into hosted
* pyodide https://news.ycombinator.com/item?id=31261777 https://adtax.paulromer.net/ https://duckdb.org/2024/10/02/pyodide.html 🗄️ `architecture.md` baked data, Datasette, WASM-based? https://simonwillison.net/2025/Feb/13/url-addressable-python/ https://trilogydata.dev/
* add to startup https://www.pythonmorsels.com/cli-tools/#pyclbr
* https://ericmjl.github.io/blog/2024/11/8/disposable-environments-for-ad-hoc-analyses/
* https://lukeplant.me.uk/blog/posts/repl-python-programming-and-debugging-with-ipython/

* _24_: iPython
* _21_: pdb

TAXONOMY https://en.wikipedia.org/wiki/Exploratory_programming
* _REPL_: interactive CLI to interpreter https://docs.python.org/3/glossary.html#term-interactive https://docs.python.org/3/tutorial/interpreter.html#interactive-mode
* Codi = REPL running async as you type https://github.com/metakirby5/codi.vim https://www.youtube.com/watch?v=tLQmGabfXHU
* Magma = highlight code blocks and exec in Jupyter https://github.com/dccsillag/magma-nvim
* Org Mode = exec code snippets
* _db CLI_: REPL to db 🗄️ `databases.md` CLI
* _object explorer_: REPL + autocomplete + print docstrings https://github.com/darrenburns/shira
* _debugger_: REPL + running program state
* _notebook_: REPL + presentation layer + persistent data
* _spreadsheet_: proprietary notebook https://www.youtube.com/watch?v=llgTl9BDuKw

# 🐛 DEBUG

🗄 `stdlib.md` profilng
📜 https://docs.python.org/3/library/debug.html
📚
* Beazley ch. 14
* Seitz grey hat ch. 2
* https://pragprog.com/titles/pbdp/debug-it/

INTERNALS / DESIGN https://www.youtube.com/watch?v=QU158nGABxI https://www.youtube.com/watch?v=COa-JHYuW3M
* `sys.settrace` registers callback on interpreter for function call, LOC executed, func return value, exceptions raised [3:45]
* perf https://www.youtube.com/watch?v=3UbVs18SBzo "Tian Gao: What makes a Python debugger possible and how can we make it 100x faster?"
```python
def simple_tracer(frame, event):  # 4:30
```
* trickier with multithreading [10:00]
* BYO w/ bdb [11:45] https://www.geoffreylitt.com/2024/12/22/making-programming-more-fun-with-an-ai-generated-debugger
* BYO https://www.timdbg.com/posts/writing-a-debugger-from-scratch-part-5/
* https://werat.dev/blog/what-a-good-debugger-can-do/
* https://wizardzines.com/zines/debugging-guide/
* https://peps.python.org/pep-0768/
* https://www.youtube.com/watch?v=fvRwG17XsaA
* internals https://www.hytradboi.com/2025/e4264872-f118-44cc-8d73-25f52f5efcdc-how-debuggers-work

## alternatives

---

debugpy https://www.bitecode.dev/p/whats-up-python-better-packaging https://github.com/microsoft/vscode-python-debugger/wiki/No%E2%80%90Config-Debugging
https://github.com/leapingio/leaping

IPYTHON
* https://switowski.com/blog/ipython-debugging/
* https://adamj.eu/tech/2021/02/21/improve-your-django-experience-with-ipython/
```python
from IPython import embed; embed()
```
* _ipdb_: https://stackoverflow.com/a/15976544/6813490 https://adamj.eu/tech/2021/02/21/improve-your-django-experience-with-ipython/

ALTERNATIVES
> pdb much better in 3.13 https://www.bitecode.dev/i/150706558/make-debugging-great-again
* `print()`: if you don't know how to use a debugger https://twitter.com/raymondh/status/1266668437020897280 https://github.com/gruns/icecream https://github.com/cool-RR/PySnooper
> It takes less time to decide where to put print statements than to single-step to the critical section of code https://news.ycombinator.com/item?id=26928696
* tmux send-keys https://news.ycombinator.com/item?id=37172711 https://www.reddit.com/r/zellij/comments/13zqggd/sending_keys_to_another_terminal/ https://www.youtube.com/results?search_query=send-keys+tmux
* _bdb_: ❌ level down from pdb https://stackoverflow.com/a/10302538/6813490
* _gdb_: ❌ deep bad things https://wiki.python.org/moin/DebuggingWithGdb
* _pdb++_: 🎯 1.5k dev has stopped and they might be in legal trouble https://github.com/pdbpp/pdbpp https://github.com/pdbpp/pdbpp/issues/529
* main reason to use seem to be syntax highlighting and tab completion https://github.com/pdbpp/pdbpp#what-is-it
* pytest workaround https://github.com/pdbpp/pdbpp/issues/392 https://github.com/zachvalenta/algos/blob/master/Makefile#L43
* overrides pdb breakpoint https://github.com/pdbpp/pdbpp/issues/281
* `track`: (requires pypy)
* `display`: (couldn't figure out how this worked first time around)
* _pytrace_: 150 https://github.com/gleb-sevruk/pycrunch-trace https://pytrace.com/
* _pyrewind_: 🧠 fork of CPython https://www.youtube.com/watch?v=ChoCe1OBhUc unreleased https://github.com/search?utf8=%E2%9C%93&q=pyrewind&type=repositories inspiration https://www.replay.io/
* _nvim-dap_: 5.5k https://github.com/mfussenegger/nvim-dap https://www.youtube.com/watch?v=4BnVeOUeZxc

## AST

---

* https://www.pythonmorsels.com/cli-tools/#analyzing-python-code
* https://lukeplant.me.uk/blog/posts/enforcing-conventions-in-django-projects-with-introspection/
* https://lukeplant.me.uk/blog/posts/tools-for-rewriting-python-code/
* https://lukeplant.me.uk/blog/posts/grep-python-syntax-using-ast-pyastgrep/
* https://ward.readthedocs.io/en/latest/guide/writing_tests.html#using-assert-statements
* https://www.youtube.com/watch?v=OjPT15y2EpE
* inspect https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework
* https://www.mattlayman.com/blog/2018/decipher-python-ast/
* https://talkpython.fm/episodes/show/152/understanding-and-using-python-s-ast
* get data structure from string `ast.literal_eval(ds_as_str)` https://stackoverflow.com/a/17768535
* https://lukeplant.me.uk/blog/posts/pyastgrep-and-custom-linting/

## inspect

💡 examine class contents, retrieve method src, extract/fmt func arg list, get traceback info

```python
# GET METHODS IMPL ON CLASS
from dataclasses import dataclass
from inspect import getmembers

@dataclass()
class Person:
    name: str
    age: int
    hobbies: list

getmembers(Person, inspect.isfunction)
```

---

EXPLORE THESE METHODS 📜 https://docs.python.org/3/library/inspect.html 
* getmodulename
* ismodule
* isbuiltin
* getdoc
* getcomments
* getfile
* getmodule
* getsourcefile
* getsource

https://www.youtube.com/watch?v=NIyljVEcJKw
* rich vs. iypthon's `obj?` https://ipython.readthedocs.io/en/stable/interactive/tutorial.html#exploring-your-objects
* wat https://github.com/igrek51/wat
```python
getsource(obj)  # view src code https://stackoverflow.com/a/1562795
getfile(obj)  # filepath where obj defined
obj.__class__.__mro__  # view inheriance hierarchy
```

## pdb

📜
* `help pdb`
* https://docs.python.org/3/library/pdb.html
* https://docs.python.org/3/library/debug.html https://www.debuggingbook.org/

CONTEXT
* `a`: func args
* `p <obj>`: print obj https://docs.python.org/3/library/pdb.html#pdbcommand-p 🗄 `.pdbrc`
* `i <obj>`: print obj attr 🗄 `.pdbrc`
* `loc`: print obj in scope 🗄 `.pdbrc`
* `pp <expresion>`: same but pprint https://hamatti.org/posts/improved-print-readability-with-pprint/
* `__return__`: view return val from function https://stackoverflow.com/a/18674516
* `whatis`: = `type()`
* `interact`: start REPL w/ local var in context
> how to exit REPL w/ out exit pdb? -> `!` run new code

CONTROL FLOW
* _step in_: `s` = enter func at current line
* _step over_: `n` = execute func at current line or exit current func
* _step out_: `r` = exec to end of current func
* `c`: continue exec to completion (or next breakpoint)
* `until <LOC>`: exit loop and jump to LOC https://docs.python.org/3/library/pdb.html?highlight=until#pdbcommand-until https://stackoverflow.com/a/61151333
* next iteration in loop: breakpoint inside loop + `c` https://stackoverflow.com/a/28414891

PAGING
* _list point (lp)_: LOC to list around
* != current LOC, != breakpoint
* ❓ lp follows current LOC as determined by control flow cmd?
* `l`: list n LOC from lp and then mv lp (hence `l .` to reset)
* `l .`: reset lp to current LOC https://stackoverflow.com/a/23064293
* doens't work on 2.7
* `ll`: list page at list point
* `w`: location in call stack
```python
# list src after navigation cmd
# = pdbpp 'sticky mode' https://github.com/pdbpp/pdbpp#sticky-mode
alias n n;;l
alias r r;;l
```

EXEC
```sh
# RUN FROM REPL
import pdb
import ur_script
script.div(6, 0)            # throws err
pdb.pm()                    # post-mortem mode

# RUN FROM SHELL
python3 -m pdb mymodule.py  # starts in pdb https://www.youtube.com/watch?v=P0pIW5tJrRM 2:50
python -i script.py         # interactive; `python --help` -> "inspect interactively after running script"
python -m pdb -c continue myscript.py  # https://stackoverflow.com/a/2438834/6813490
```

---

todo
* `h`
* `r`
* `u / d`
* `interact`

CONFIG
* use Rich for output https://github.com/cansarigol/pdbr
* `.pdbrc`: `$HOME` is default file location https://docs.python.org/3/library/pdb.html?highlight=pdbrc#debugger-commands
> should be sources if present in $CWD but so far only sourced if in $HOME https://docs.python.org/3/library/pdb.html?highlight=pdbrc#debugger-commands
* aliases https://docs.python.org/3.2/library/pdb.html#pdbcommand-alias
* comments https://nedbatchelder.com/blog/200704/my_pdbrc.html https://www.youtube.com/watch?v=_kCKBXtA2jQ
* command history buggy w/ readline incompatability https://stackoverflow.com/questions/6348034/python-pdb-command-history-not-working-on-windows

## pudb

📜 https://github.com/inducer/pudb

---

https://realpython.com/python-packages/#pudb-for-visual-debugging

# 📔 NOTEBOOK

💡 Romer econ textbook idea
🗄
* `analytics.md` BI, GUI
* `doc.md` notes

> Jupyter Notebooks are files that combine two content types: text/Markdown and executable Python code. https://www.pinecone.io/learn/retrieval-augmented-generation/

ALTERNATIVES
* VS Code https://news.ycombinator.com/item?id=40899242
* Zed https://zed.dev/blog/repl

---

* charting in Jupyter: https://github.com/plotly/plotly.py https://github.com/lux-org/lux

OBSERVABLE
* https://observablehq.com/
* https://observablehq.com/@simonw/datasette-downloads-per-day-with-observable-plot
* https://www.hytradboi.com/2025/5fc19c84-9ad9-49b5-9433-9f83b68a495b-hacking-observable-notebooks-from-within

* https://blog.jetbrains.com/pycharm/2024/09/7-ways-to-use-jupyter-notebooks-inside-pycharm/

ALTERNATIVES
* org mode https://dualpower.supply/
* https://github.com/Bycelium/PyFlow
* in Vim https://www.maxwellrules.com/misc/nvim_jupyter.html
* Elixir livebook https://livebook.dev/ https://github.com/livebook-dev/pythonx
* Typescript Srcbook https://news.ycombinator.com/item?id=41291700
* https://zeppelin.apache.org/
* https://github.com/ottomatica/docable-notebooks
* aaS https://www.youtube.com/watch?v=EVSJxMnXoJk
* https://www.hytradboi.com/2022/percival-a-reactive-language-for-exploratory-data-analysis-and-visualization
* TUI https://mastodon.top/@davidbrochart/111926774648199625

## design

---

* https://news.ycombinator.com/item?id=42451938
* as integration tests https://rakhim.exotext.com/jupyter-notebooks-as-e2e-tests
* https://pypi.org/project/nbformat/
* https://news.ycombinator.com/item?id=41580166
* https://www.reddit.com/r/Python/comments/6hwa22/what_is_the_point_of_jupyter/ https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.html
* notebooks as articles https://news.ycombinator.com/item?id=27367948 as books https://executablebooks.org/en/latest/ https://jupyterbook.org/en/stable/intro.html
* reproducibility https://jvns.ca/blog/2017/11/12/binder--an-awesome-tool-for-hosting-jupyter-notebooks/ https://news.ycombinator.com/item?id=24943962
* design https://news.ycombinator.com/item?id=25538454 https://www.fast.ai/2019/12/02/nbdev/ http://willcrichton.net/notes/programming-in-the-debugger https://ljvmiranda921.github.io/notebook/2020/03/06/jupyter-notebooks-in-2020/ Somers https://www.theatlantic.com/science/archive/2018/04/the-scientific-paper-is-obsolete/556676/ https://github.com/naklecha/llama3-from-scratch https://news.ycombinator.com/item?id=41045834
* https://www.singlestore.com/blog/how-we-made-notebooks-load-10-times-faster/
* widgets https://calmcode.io/course/ipywidgets/introduction

## hosted

https://deepnote.com/app/katkas-workspace/FaCT-721f3451-6e2e-4325-b2cc-0beeeb601c54?size_range=1000
https://deepnote.com/app/katkas-workspace/Vector-animations-with-Python-6642dc15-9d7d-40cc-8e5e-c4eb2238cbf2
https://github.com/zasper-io/zasper

## 🟧 Jupyter

📜 https://jupyter.readthedocs.io/en/latest/index.html https://realpython.com/jupyter-notebook-introduction/

HOWTO
```sh
# POETRY
poetry add jupyter
poetry run jupyter notebook

# PIP (GLOBAL TO USER)
python -m pip install --user jupyter
which jupyter  # /Users/zvalenta/.local/bin/jupyter
jupyter notebook

# VS Code extension
vsc path/to/.ipynb

# exec from shell
jupyter nbconvert --to notebook --execute --stdout nb.ipynb > /dev/null
```

FEATURES
* run SQL https://github.com/ploomber/jupysql https://www.youtube.com/watch?v=xuASJwVBhvc
* testing https://github.com/ploomber/nbsnapshot https://www.youtube.com/watch?v=8wpBd-jfUTU
* Markdown https://github.com/mwouts/jupytext
* TOC https://jupyterlab.readthedocs.io/en/stable/user/toc.html https://jupyterbook.org/en/stable/intro.html https://github.com/fluentpython/example-code-2e/blob/master/01-data-model/data-model.ipynb
* profiler https://github.com/robusta-dev/WhyProfiler

INSTALL
* Conda recommended https://jupyter.readthedocs.io/en/latest/install.html#id3
* pip works fine https://jupyter.readthedocs.io/en/latest/install.html#alternative-for-experienced-python-users-installing-jupyter-with-pip
* poetry worked as well http://jupyterlab.io/install.html

ZA
* diff https://github.com/jupyter/nbdime
* `.ipynb_checkpoints`: most recent state of `<file>.ipynb` https://stackoverflow.com/a/46422176/6813490 ignore in version control https://stackoverflow.com/a/39997938/6813490
* libraries https://github.com/twosigma/beakerx
* VS Code extension https://realpython.com/podcasts/rpp/197/

COMPONENTS
* _iPython_: REPL + syntax highlighting, access to Bash cmd, Jupyter kernel
* _IPython Notebook_: IPython + persistence, web browser, visualizations (chart, Markdown); predecessor to contemporary Jupyter
* _Jupyter_: IPython Notebook + kernels for other languages (R, F#, Java)
* _kernel_: runtime
* _Jupyter Lab_: pretty UI, less features https://stackoverflow.com/a/52392304 https://satyrn.app/ https://news.ycombinator.com/item?id=42572057

## 🟩 Marimo

🗄️ `feedback.md` Marimo
📻 https://marimo.io/ https://github.com/marimo-team/marimo

you can run in the browser!?! https://docs.marimo.io/cli/?h=wasm#marimo-export-html-wasm https://news.ycombinator.com/item?id=42700852 https://www.agentrecipes.com/prompt-chaining
share https://nbviewer.org/ https://ipython.org/documentation.html

SHARING
* hosted
* sidebar ToC

---

* https://talkpython.fm/episodes/show/501/marimo-reactive-notebooks-for-python
* WASM https://calmcode.io/course/marimo/webassembly
* design https://marimo.io/blog/python-not-json
https://calmcode.io/shorts/drawdata.py
lint https://calmcode.io/shorts/nbqa
https://calmcode.io/course/marimo/introduction

https://www.youtube.com/watch?v=ANIu4l9_FB8
* no ToC
* design https://marimo.io/blog/lessons-learned https://pythonbytes.fm/episodes/show/393/dare-enter-the-bash-dungeon https://realpython.com/podcasts/rpp/230/ https://realpython.com/podcasts/rpp/230/
* commands
```bash
poetry init -n
poetry add marimo
poetry run python marimo tutorial intro
```

# 👾 REPL

🗄 `vim.md` Zed

---

`list_all_user_defined_modules` https://github.com/zachvalenta/algo-sandbox

https://switowski.com/blog/ipython-debugging/

https://github.com/igrek51/wat
rich for repl https://rich.readthedocs.io/en/latest/introduction.html#ipython-extension https://rich.readthedocs.io/en/latest/introduction.html#rich-in-the-repl https://rich.readthedocs.io/en/latest/pretty.html#rich-repr-protocol
https://wesmckinney.com/book/ipython
https://github.com/gotcha/ipdb

* reload
* embed
* profiles https://ipython.readthedocs.io/en/stable/config/options/terminal.html#configtrait-BaseIPythonApplication.profile

ZA
* https://github.com/sloria/konch
* track state https://github.com/saurabh0719/constable
* `locals`, `globals`, `dir` https://stackoverflow.com/a/21961813/6813490
* inspect https://news.ycombinator.com/item?id=29947891 https://textual.textualize.io/blog/2023/07/27/using-rich-inspect-to-interrogate-python-objects/
* 🗄️ `stdlib.md` IO

STACK TRACES 🗄️ stdlib/profiling
* stackprinter https://martinheinz.dev/blog/96
* hide https://www.bitecode.dev/p/why-and-how-to-hide-the-python-stack
* fmt https://martinheinz.dev/blog/96
* traceback https://martinheinz.dev/blog/66 https://docs.python.org/3/library/inspect.html#inspect.istraceback
* https://docs.python.org/3/library/inspect.html#the-interpreter-stack
* history https://stackoverflow.com/a/4289945

## features

* global ipython that has it's own startup + can dynamically figure out what the project's deps are and import those as well
* block-level history https://treyhunner.com/2024/05/my-favorite-python-3-dot-13-feature/
* paste https://treyhunner.com/2024/05/my-favorite-python-3-dot-13-feature/
* autocomplete
* syntax highlighting
* obj explorer
* readline https://docs.python.org/3/tutorial/interactive.html#alternatives-to-the-interactive-interpreter
* multiline edit https://realpython.com/podcasts/rpp/223/

## 🟦 iPython

📜
* https://ipython.readthedocs.io/en/stable/
* https://ipython.org/
* https://github.com/ipython/ipython
* https://jakevdp.github.io/PythonDataScienceHandbook/01.00-ipython-beyond-normal-python.html
* https://realpython.com/ipython-interactive-python-shell/

CONFIG
* install: using pip into global pyenv interpreter https://github.com/zachvalenta/logs-capp/commit/4b6eca22fac0422406e5df5f0fb40dcc581d7341
* vi for readline https://gist.github.com/sstirlin/c3c207b1052b613ab9554b4ebdfc3f35
* color theme: rich in PYTHONSTARTUP + catppuccin/pygments https://github.com/catppuccin/python#ipython https://github.com/catppuccin/python/issues/22
* fs
```sh
├── .ipython
│   └── profile_default
│   └──── history.sqlite  # command history -> can scroll through with j|k in vi mode > normal mode
│   └──── ipython_config.py  # generated with `ipython profile create` 
│   └──── startup  # modules executed prior to startup?
│   └────── 00-first.py
│   └────── 99-last.py
```

DESIGN
* bad: no docstrong in autocomplete for `PYTHONSTARTUP` function
* good: numbered prompts, pretty traceback, magic cmd, auto indent, autocomplete

ALTERNATIVES
* built-in https://realpython.com/python313-repl/
* _bpython_: https://github.com/zachvalenta/algo-sandbox
* _pypython_:

---

* 📍 fix theme (try monokai)
separte startup files in addition to `PYTHON_STARTUP` https://ipython.readthedocs.io/en/stable/interactive/tutorial.html#startup-files

MAGIC
* alias https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-alias_magic

* why: 📍 Rich integration, ipdb, magic func https://realpython.com/ptpython-shell/#highlighting-code-syntax
* https://ipython.readthedocs.io/en/stable/config/options/terminal.html#configtrait-InteractiveShellApp.pylab
* command
```python
# run iPython and debug at site of error https://lukeplant.me.uk/blog/posts/repl-python-programming-and-debugging-with-ipython/ https://stackoverflow.com/a/21508070
from IPython import embed; embed()
# use already running iPython to debug at site of error
%debug
# pretty print obj
pp
# paste from system clipboard
%paste
```
* obj explore https://stackoverflow.com/q/41812447
* magic cmd https://jakevdp.github.io/PythonDataScienceHandbook/01.03-magic-commands.html
* edit https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-edit
* macro https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-macro
* debug https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-debug
* doc string https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-pdoc
* profile https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-prun time https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-time
* run file https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-run
* _line magic_: `%` operates on single line
* list https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-lsmagic
* _cell magic_: `%%` operates on n lines
* _automagic_: don't need prefex for line magic
* relationship to shell https://jakevdp.github.io/PythonDataScienceHandbook/01.05-ipython-and-shell-commands.html

## startup

📜 https://docs.python.org/3/tutorial/appendix.html#the-interactive-startup-file 🗄️ imports

PYTHONSTARTUP
* `PYTHONSTARTUP`: module executed and loaded on REPL startup, module in same namespace as interactive cmds i.e. all module symbols available for use https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP
* set in shell: `export PYTHONSTARTUP='$DOT_DIR/python/python_startup.py'`
* using per project: https://github.com/zachvalenta/algo-sandbox/blob/master/Makefile#L28

FUNCTIONALITY
* view module help: `pretty(help(__name__))`
> yet more powerful https://simonwillison.net/2025/Mar/3/pythons-help-function/
* list user-defined modules https://github.com/zachvalenta/algo-sandbox/commit/3ab6b3d8b4bcbf1ad7548c14f62958e5f88c75e1 https://chatgpt.com/share/19cfacb1-05ac-4339-a6c8-a8aa4bac6a80

---

* sink https://arpitbhayani.me/blogs/python-prompts https://github.com/bpython/bpython/blob/ae4a502a443e024bd82ed1a7b88adf8be2068a2c/doc/sphinx/source/django.rst https://github.com/bpython/bpython/search?q=PYTHONSTARTUP&unscoped_q=PYTHONSTARTUP https://stackoverflow.com/a/14244310 https://stackoverflow.com/a/34774703
* reload: `from importlib import reload; reload (mod)` https://realpython.com/run-python-scripts/#using-importlib-and-imp normal reimport doesn't work https://realpython.com/run-python-scripts/#taking-advantage-of-import lib https://github.com/hoh/reloadr https://github.com/breuleux/jurigged https://switowski.com/blog/ipython-autoreload/ https://github.com/reloadware/reloadium https://www.gauge.sh/blog/how-to-build-hot-module-replacement-in-python
* reload src: point is to avoid continual exit/rerun https://news.ycombinator.com/item?id=23793054 https://mikelevins.github.io/posts/2020-12-18-repl-driven/
* history: save https://stackoverflow.com/a/33880964 readline error manifests in garbled cmd history (have only seen when setting breakpoint in Flask) https://stackoverflow.com/a/3486617

ZA
* 📍 load module: `$REPL -i $MODULE` https://stackoverflow.com/a/14244342 https://stackoverflow.com/a/56844640
* silence version info: `python -q`
* reload https://news.ycombinator.com/item?id=34865421
* BYO using `code.InteractiveConsole()` https://bernsteinbear.com/blog/simple-python-repl/ https://news.ycombinator.com/item?id=34865421
* CTRL arrows on macOS https://mathspp.com/blog/til/ctrl-left-and-ctrl-right-not-working-in-the-python-repl-on-macos
