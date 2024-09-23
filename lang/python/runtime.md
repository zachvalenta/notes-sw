# ⛩️

## 参考

## 进步

* _24_: split from `python.md`
* _19_: lib (pipx, Poetry, pyinstaller)

# 📺 FEEDBACK

📙 Van Rossum ch. 2, 14
🗄
* `databases.md` tooling
* `education.md` design

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

## 🐛 debugger

📚
* Beazley ch. 14
* Seitz grey hat ch. 2

---

INTERNALS / DESIGN https://www.youtube.com/watch?v=QU158nGABxI https://www.youtube.com/watch?v=3UbVs18SBzo https://www.youtube.com/watch?v=COa-JHYuW3M
* `sys.settrace` registers callback on interpreter for function call, LOC executed, func return value, exceptions raised [3:45]
```python
def simple_tracer(frame, event):  # 4:30
```
* trickier with multithreading [10:00]
* BYO w/ bdb [11:45]
* BYO https://www.timdbg.com/posts/writing-a-debugger-from-scratch-part-5/
* https://werat.dev/blog/what-a-good-debugger-can-do/

### alternatives

---

IPYTHON
* https://switowski.com/blog/ipython-debugging/
* https://adamj.eu/tech/2021/02/21/improve-your-django-experience-with-ipython/
```python
from IPython import embed; embed()
```

ALTERNATIVES
* https://www.youtube.com/watch?v=3UbVs18SBzo
> tmux send-keys https://news.ycombinator.com/item?id=37172711 https://www.reddit.com/r/zellij/comments/13zqggd/sending_keys_to_another_terminal/ https://www.youtube.com/results?search_query=send-keys+tmux
* _pudb_: 🎯 https://github.com/inducer/pudb https://realpython.com/python-packages/#pudb-for-visual-debugging
* _ipdb_: 🎯 https://stackoverflow.com/a/15976544/6813490 https://adamj.eu/tech/2021/02/21/improve-your-django-experience-with-ipython/
* _bdb_: level down from pdb https://stackoverflow.com/a/10302538/6813490
* _gdb_: deep bad things https://wiki.python.org/moin/DebuggingWithGdb
* `print()`: if you don't know how to use a debugger https://twitter.com/raymondh/status/1266668437020897280 https://github.com/gruns/icecream https://github.com/cool-RR/PySnooper
> It takes less time to decide where to put print statements than to single-step to the critical section of code https://news.ycombinator.com/item?id=26928696
* _pdb++_: 🎯 https://github.com/pdbpp/pdbpp
* main reason to use seem to be syntax highlighting and tab completion https://github.com/pdbpp/pdbpp#what-is-it
* pytest workaround https://github.com/pdbpp/pdbpp/issues/392 https://github.com/zachvalenta/algos/blob/master/Makefile#L43
* overrides pdb breakpoint https://github.com/pdbpp/pdbpp/issues/281
* `track`: (requires pypy)
* `display`: (couldn't figure out how this worked first time around)
* _nvim-dap_: 🎯 https://github.com/mfussenegger/nvim-dap https://www.youtube.com/watch?v=4BnVeOUeZxc
* _rewind_: 🎯 https://www.youtube.com/watch?v=ex9draKAP3c

### pdb

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

## 📔 notebook

🗄 `km.md` notes

ALTERNATIVES
* VS Code https://news.ycombinator.com/item?id=40899242
* Zed https://zed.dev/blog/repl

---

* https://blog.jetbrains.com/pycharm/2024/09/7-ways-to-use-jupyter-notebooks-inside-pycharm/

ALTERNATIVES
* org mode https://dualpower.supply/
* https://github.com/Bycelium/PyFlow
* in Vim https://www.maxwellrules.com/misc/nvim_jupyter.html
* Elixir livebook https://livebook.dev/
* Typescript Srcbook https://news.ycombinator.com/item?id=41291700
* https://zeppelin.apache.org/
* https://github.com/ottomatica/docable-notebooks
* aaS https://www.youtube.com/watch?v=EVSJxMnXoJk
* https://www.hytradboi.com/2022/percival-a-reactive-language-for-exploratory-data-analysis-and-visualization
* TUI https://mastodon.top/@davidbrochart/111926774648199625

### design

---

* https://news.ycombinator.com/item?id=41580166
* https://www.reddit.com/r/Python/comments/6hwa22/what_is_the_point_of_jupyter/ https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.html
* notebooks as articles https://news.ycombinator.com/item?id=27367948 as books https://executablebooks.org/en/latest/ https://jupyterbook.org/en/stable/intro.html
* reproducibility https://jvns.ca/blog/2017/11/12/binder--an-awesome-tool-for-hosting-jupyter-notebooks/ https://news.ycombinator.com/item?id=24943962
* design https://news.ycombinator.com/item?id=25538454 https://www.fast.ai/2019/12/02/nbdev/ http://willcrichton.net/notes/programming-in-the-debugger https://ljvmiranda921.github.io/notebook/2020/03/06/jupyter-notebooks-in-2020/ Somers https://www.theatlantic.com/science/archive/2018/04/the-scientific-paper-is-obsolete/556676/ https://github.com/naklecha/llama3-from-scratch https://news.ycombinator.com/item?id=41045834
* https://www.singlestore.com/blog/how-we-made-notebooks-load-10-times-faster/

### Jupyter

📜 https://jupyter.readthedocs.io/en/latest/index.html https://realpython.com/jupyter-notebook-introduction/

FEATURES
* run SQL https://github.com/ploomber/jupysql https://www.youtube.com/watch?v=xuASJwVBhvc
* testing https://github.com/ploomber/nbsnapshot https://www.youtube.com/watch?v=8wpBd-jfUTU
* Markdown https://github.com/mwouts/jupytext
* TOC https://jupyterlab.readthedocs.io/en/stable/user/toc.html https://jupyterbook.org/en/stable/intro.html https://github.com/fluentpython/example-code-2e/blob/master/01-data-model/data-model.ipynb

INSTALL
* Conda recommended https://jupyter.readthedocs.io/en/latest/install.html#id3
* pip works fine https://jupyter.readthedocs.io/en/latest/install.html#alternative-for-experienced-python-users-installing-jupyter-with-pip
* poetry worked as well http://jupyterlab.io/install.html

ZA
* `.ipynb_checkpoints`: most recent state of `<file>.ipynb` https://stackoverflow.com/a/46422176/6813490 ignore in version control https://stackoverflow.com/a/39997938/6813490
* libraries https://github.com/twosigma/beakerx

COMPONENTS
* _iPython_: REPL + syntax highlighting, access to Bash cmd, Jupyter kernel
* _IPython Notebook_: IPython + persistence, web browser, visualizations (chart, Markdown); predecessor to contemporary Jupyter
* _Jupyter_: IPython Notebook + kernels for other languages (R, F#, Java)
* _kernel_: runtime
* _Jupyter Lab_: pretty UI, less features https://stackoverflow.com/a/52392304 https://satyrn.app/

### Marimo

📻 https://github.com/marimo-team/marimo

* no ToC
* design https://marimo.io/blog/lessons-learned https://pythonbytes.fm/episodes/show/393/dare-enter-the-bash-dungeon
* commands
```bash
poetry init -n
poetry add marimo
poetry run python marimo tutorial intro
```

## 👾 REPL

🗄 `vim.md` Zed

FEATURES
* block-level history https://treyhunner.com/2024/05/my-favorite-python-3-dot-13-feature/
* paste https://treyhunner.com/2024/05/my-favorite-python-3-dot-13-feature/
* autocomplete
* syntax highlighting
* obj explorer
* readline https://docs.python.org/3/tutorial/interactive.html#alternatives-to-the-interactive-interpreter

---

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
* pyclbr https://www.pythonmorsels.com/cli-tools/
* 🗄️ `stdlib.md` IO

STACK TRACES 🗄️ stdlib/profiling
* stackprinter https://martinheinz.dev/blog/96
* hide https://www.bitecode.dev/p/why-and-how-to-hide-the-python-stack
* fmt https://martinheinz.dev/blog/96
* traceback https://martinheinz.dev/blog/66 https://docs.python.org/3/library/inspect.html#inspect.istraceback
* https://docs.python.org/3/library/inspect.html#the-interpreter-stack
* history https://stackoverflow.com/a/4289945

### iPython

📜
* https://github.com/ipython/ipython
* `ipython.py`
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
│   └──── history.sqlite  # command history
│   └──── ipython_config.py  # generature with `ipython profile create` 
│   └──── startup  # modules executed prior to startup?
│   └────── 00-first.py
│   └────── 00-last.py
```

DESIGN
* bad: no docstrong in autocomplete for `PYTHONSTARTUP` function
* good: numbered prompts, pretty traceback, magic cmd, auto indent, autocomplete

ALTERNATIVES
* built-in https://realpython.com/python313-repl/
* _bpython_:
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

### inspect

📜 https://docs.python.org/3/library/inspect.html https://www.youtube.com/watch?v=NIyljVEcJKw

---

* rich vs. iypthon's `obj?` https://ipython.readthedocs.io/en/stable/interactive/tutorial.html#exploring-your-objects
* wat https://github.com/igrek51/wat
```python
getsource(obj)  # view src code https://stackoverflow.com/a/1562795
getfile(obj)  # filepath where obj defined
obj.__class__.__mro__  # view inheriance hierarchy
```

### startup

📜 https://docs.python.org/3/tutorial/appendix.html#the-interactive-startup-file 🗄️ imports

PYTHONSTARTUP
* `PYTHONSTARTUP`: module executed and loaded on REPL startup, module in same namespace as interactive cmds i.e. all module symbols available for use https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP
* set in shell: `export PYTHONSTARTUP='$DOT_DIR/python/python_startup.py'`
* using per project: https://github.com/zachvalenta/algo-sandbox/blob/master/Makefile#L28

FUNCTIONALITY
* view module help: `pretty(help(__name__))`
* list user-defined modules https://github.com/zachvalenta/algo-sandbox/commit/3ab6b3d8b4bcbf1ad7548c14f62958e5f88c75e1 https://chatgpt.com/share/19cfacb1-05ac-4339-a6c8-a8aa4bac6a80

---

* sink https://arpitbhayani.me/blogs/python-prompts https://github.com/bpython/bpython/blob/ae4a502a443e024bd82ed1a7b88adf8be2068a2c/doc/sphinx/source/django.rst https://github.com/bpython/bpython/search?q=PYTHONSTARTUP&unscoped_q=PYTHONSTARTUP https://stackoverflow.com/a/14244310 https://stackoverflow.com/a/34774703
* reload: `from importlib import reload; reload (mod)` https://realpython.com/run-python-scripts/#using-importlib-and-imp normal reimport doesn't work https://realpython.com/run-python-scripts/#taking-advantage-of-import lib https://github.com/hoh/reloadr https://github.com/breuleux/jurigged https://switowski.com/blog/ipython-autoreload/
* reload src: point is to avoid continual exit/rerun https://news.ycombinator.com/item?id=23793054 https://mikelevins.github.io/posts/2020-12-18-repl-driven/
* history: save https://stackoverflow.com/a/33880964 readline error manifests in garbled cmd history (have only seen when setting breakpoint in Flask) https://stackoverflow.com/a/3486617

ZA
* 📍 load module: `$REPL -i $MODULE` https://stackoverflow.com/a/14244342 https://stackoverflow.com/a/56844640
* silence version info: `python -q`
* reload https://news.ycombinator.com/item?id=34865421
* BYO using `code.InteractiveConsole()` https://bernsteinbear.com/blog/simple-python-repl/ https://news.ycombinator.com/item?id=34865421
* CTRL arrows on macOS https://mathspp.com/blog/til/ctrl-left-and-ctrl-right-not-working-in-the-python-repl-on-macos

# 🤖 INTERPRETER

---

GIL, JIT https://news.ycombinator.com/item?id=41677131

auditing hooks https://stackoverflow.com/questions/63350394/how-to-set-up-and-use-python-audit-hooks https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP https://chatgpt.com/c/67094688-4dac-8004-88e8-4eadd79a1d0e

* free threaded https://github.com/astral-sh/uv/issues/7193
* `__pycache__`: holds bytecode in the form of `.pyc` https://stackoverflow.com/a/28365204/6813490 speeds up module loading https://docs.python.org/3/tutorial/modules.html#compiled-python-files suppress creation of with `export PYTHONDONTWRITEBYTECODE=1` more on bytecode https://blog.jse.li/posts/pyc/ https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md

VERSIONS https://docs.python.org/3/whatsnew/index.html https://nedbatchelder.com/text/which-py.html https://www.nicholashairs.com/posts/major-changes-between-python-versions/
* major https://en.wikipedia.org/wiki/History_of_Python#Table_of_versions
* minor/patch https://blog.python.org/
* switch to latest minor version after subsequent patch release https://www.b-list.org/weblog/2022/nov/08/python-311-gotcha/ https://pythonspeed.com/articles/upgrade-python-3.11/
* _89_: initial
* _00_: Python2
* _08_: Python3 https://nedbatchelder.com/blog/201803/whats_in_which_python_3436.html
* can't test Python2 code using Python3 if you're using parts of stdlib that have been deprecated between releases (urllib2, xrange)
* Tauthon to backport Python3 features to Python2 https://www.pythonpodcast.com/tauthon-python-2-fork-episode-265/
* 2to3 https://news.ycombinator.com/item?id=24461157
* _18_: 3.7
* _19_: 3.8 https://realpython.com/courses/cool-new-features-python-38/
* _20_: Python 2 EoL
* _3.11_: specializing adaptive interpreter https://peps.python.org/pep-0659/
* _3.13_: JIT https://tonybaloney.github.io/posts/python-gets-a-jit.html

* using other language in Python e.g. Julia https://www.peterbaumgartner.com/blog/incorporating-julia-into-python-programs/

## CPython

📙 Shaw cpyton internals
🗄 `language.md` compilers

---

GIL, JIT, free thread https://realpython.com/python313-free-threading-jit/ https://drew.silcock.dev/blog/everything-you-need-to-know-about-python-3-13/ https://blog.changs.co.uk/free-threaded-python-with-asyncio.html
AST is slow https://www.gauge.sh/blog/python-extensions-should-be-lazy
preprocessor https://pydong.org/posts/PythonsPreprocessor/
https://snarky.ca/unravelling-attribute-access-in-python/
https://snarky.ca/mvpy-minimum-viable-python/

ALTERNATIVES
* unique insofar as has to fit many use cases (web, CLI, security) https://talkpython.fm/episodes/show/265/why-is-python-slow 47:00
* things that need to be fast will be written in C https://talkpython.fm/episodes/show/265/why-is-python-slow 50:00
* _pypy_: JIT, supports Python 2 https://news.ycombinator.com/item?id=22928030 http://aosabook.org/en/pypy.html https://ao.gl/when-your-python-code-is-much-faster-with-pypy/ https://www.reddit.com/r/Python/comments/bv50uz/is_anyone_using_pypy_on_production/ https://realpython.com/pypy-faster-python/ https://avi.im/blag/2021/fast-sqlite-inserts/ 📙 Beazly 595
* pypy is dead https://news.ycombinator.com/item?id=33330706
* _numba_: just add annotation https://news.ycombinator.com/item?id=34148455 https://talkpython.fm/episodes/show/265/why-is-python-slow 37:00 https://news.ycombinator.com/item?id=30205848 📙 Beazly 595
* _pyjion_: https://talkpython.fm/episodes/show/340/time-to-jit-your-python-with-pyjion
* _Cython_: write Python, get perf of C++ 🗄 'executables'
* _others_: Jython (Java) Iron Python (.NET) call Go from Python https://opendatagroup.github.io/development/2019/06/13/go-ffi.html

STAGES https://www.youtube.com/watch?v=QU158nGABxI 25:30
* parse https://www.pythonpodcast.com/cpython-parser-replacement-episode-285/
* compile
* execute (interpreter loop)

AST
* https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* https://github.com/PyO3/pyo3 https://www.youtube.com/watch?v=UilujdubqVU
* https://ward.readthedocs.io/en/latest/guide/writing_tests.html#using-assert-statements
* https://www.youtube.com/watch?v=OjPT15y2EpE
* inspect https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework
* https://www.mattlayman.com/blog/2018/decipher-python-ast/
* https://talkpython.fm/episodes/show/152/understanding-and-using-python-s-ast
* get data structure from string `ast.literal_eval(ds_as_str)` https://stackoverflow.com/a/17768535

C EXTENSIONS 📙 Beazley ch. 15
* howto https://kenschutte.com/python-swap-ints/
* simplistic interpreter = C extensions = Python for datascience https://lucumr.pocoo.org/2018/7/13/python/
* can write extensions in Rust https://towardsdatascience.com/nine-rules-for-writing-python-extensions-in-rust-d35ea3a4ec29 https://github.com/RustPython/RustPython https://blog.jerrycodes.com/python-trends-in-2023/ https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/ https://github.com/fulcrum-so/ziggy-pydust https://pythonspeed.com/articles/intro-rust-python-extensions https://pythonspeed.com/articles/intro-rust-python-extensions/

* Rust https://rustpython.github.io/
* actually compiled https://realpython.com/build-a-blog-from-scratch-django/
* foreign functions https://arturdryomov.dev/posts/python-foreign-functions-and-steam/
* production build won't run asserts https://docs.python.org/3/using/configure.html#python-debug-build
* _Cinder_ https://news.ycombinator.com/item?id=36621027

https://github.com/brandtbucher/specialist
Shannon plan, PEP 659, adaptive interpreter https://realpython.com/python311-new-features/#faster-code-execution

misc
* _contributing_: https://medium.com/@Captain_Joannah/so-you-want-to-contribute-to-cpython-gather-here-5a2694148ca4 http://emilyemorehouse.com/blog/015-my-path-to-becoming-a-python-core-developer/ http://lukasz.langa.pl/cv/ https://paper.dropbox.com/doc/Contributing-to-CPython--AuND60K_lABiNS7PHp0KZ9hoAg-JlgnduI6kw9MJIaGPpN9G
* _portable_: https://www.scylladb.com/2019/02/14/the-complex-path-for-a-simple-portable-python-interpreter-or-snakes-on-a-data-plane/
* _optimization_: minimize function calls and obj attr lookup https://gregoryszorc.com/blog/2019/01/10/what-i've-learned-about-optimizing-python/
* why Python doesn't have `main()` https://news.ycombinator.com/item?id=23904313
* _sink_: https://realpython.com/cpython-source-code-guide https://hackernoon.com/has-the-python-gil-been-slain-9440d28fa93d https://realpython.com/run-python-scripts/#whats-the-python-interpreter https://snarky.ca/what-is-the-core-of-the-python-programming-language

* going faster https://talkpython.fm/episodes/show/339/making-python-faster-with-guido-and-mark
* https://www.freecodecamp.org/news/hacking-together-a-simple-graphical-python-debugger-efe7e6b1f9a8/ https://github.com/puremourning/vimspector
https://tenthousandmeters.com/blog/python-behind-the-scenes-6-how-python-object-system-works/
CPython 🗄 `cpython-internals.pdf` https://talkpython.fm/episodes/show/240/a-guided-tour-of-the-cpython-source-code https://github.com/python/cpython https://news.ycombinator.com/item?id=34570315
* has no formal spec https://www.pythonpodcast.com/cpython-formal-specification-episode-288/
* _Python_: language spec; very much tied to CPython e.g. metaclasses https://news.ycombinator.com/item?id=23698846
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

## concurrency

📙 Beazley ch. 12
🗄
* `linux.md` processes
* `src.md` concurrency

BIG PICTURE
* Python as a language spec supports multiple threads
* CPython cannot execute threads in parallel https://stackoverflow.com/a/3086582
* Python is good at concurrency (IO intensive e.g. networking) https://news.ycombinator.com/item?id=22907891
* Python is bad at parallelism (CPU intensive e.g. search) http://esr.ibiblio.org/?p=8161

LIBRARIES https://testdriven.io/blog/concurrency-parallelism-asyncio/
* `multithreading`: actually parallel bc spawns own process i.e. heavier
* `asyncio`: single process; pre-emptive multi-tasking (OS interrupts itself); lighter than threads
* `threading`: single process; cooperative multi-tasking (code tells OS when to interrupt)

---

BYO event loop https://www.youtube.com/watch?v=8I9Rc2Zaos4
https://www.amazon.com/gp/product/1492055026
start here https://www.youtube.com/watch?v=ftmdDlwMwwQ https://www.youtube.com/watch?v=X7vBbelRXn0
coroutine https://docs.python.org/3/glossary.html#term-coroutine-function
https://superfastpython.com/asyncio-event-loop-separate-thread/
https://calpaterson.com/async-python-is-not-faster.html
https://martinheinz.dev/blog/97
https://higherorderco.com/
https://www.amazon.com/gp/product/1492055026
https://roadmap.sh/python
https://hakibenita.com/django-concurrency
https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#sync-vs-async-in-python-tools-benchmarks-and-asgiwsgi-explained
https://news.ycombinator.com/item?id=41001951
https://realpython.com/python-async-iterators/
https://sobolevn.me/2020/06/how-async-should-have-been

* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#overcoming-gil-with-subinterpreters-and-immutability
* JIT https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#building-a-jit-compiler-for-cpython
* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#unlocking-the-parallel-universe-subinterpreters-and-free-threading-in-python-313

SEMANTICS https://python.hamel.dev/concurrency/
* thread
* process
* _coroutine_ https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/ https://www.fluentpython.com/extra/classic-coroutines/ prime https://www.fluentpython.com/lingo https://www.fluentpython.com/lingo/#coroutine https://docs.python.org/3/glossary.html#term-coroutine-function https://docs.python.org/3/glossary.html#term-coroutine https://news.ycombinator.com/item?id=40097681&utm_term=comment

https://realpython.com/python-concurrency/
https://realpython.com/python-async-features/
https://realpython.com/intro-to-python-threading/
https://jacobpadilla.com/articles/recreating-asyncio https://news.ycombinator.com/item?id=40281139
https://www.youtube.com/watch?v=Wvh5C3NbQtA

* https://blog.wilsonl.in/hackerverse/
* https://news.ycombinator.com/item?id=39812969
* https://pythonspeed.com/articles/cpu-thread-pool-size
* https://www.photondesigner.com/articles/instant-messenger
* https://pythonspeed.com/articles/gpu-vs-cpu/
* https://charlesleifer.com/blog/asyncio/
* https://tonybaloney.github.io/posts/sub-interpreter-web-workers.html
* thead pools https://pythonspeed.com/articles/two-thread-pools/
* https://pythonspeed.com/articles/optimizing-dithering/
* https://news.ycombinator.com/item?id=37505553
* https://www.bitecode.dev/p/asyncio-twisted-tornado-gevent-walk
* semaphore https://death.andgravity.com/limit-concurrency
* async https://textual.textualize.io/blog/2023/03/15/no-async-async-with-python/
https://news.ycombinator.com/item?id=35073136
* https://superfastpython.com/asyncio-coroutine-methods/
* _async iterator_: https://docs.python.org/3/glossary.html#term-asynchronous-iterator
* _async generator_: https://docs.python.org/3/glossary.html#term-asynchronous-generator
* _async iteratable_: https://docs.python.org/3/glossary.html#term-asynchronous-iterable
* _async generator iterator_: https://docs.python.org/3/glossary.html#term-asynchronous-generator-iterator
* _awaitable_: https://docs.python.org/3/glossary.html#term-awaitable
* _callback_: https://docs.python.org/3/glossary.html#term-callback
* _context variable_: https://docs.python.org/3/glossary.html#term-context-variable
* https://news.ycombinator.com/item?id=34483294
* https://news.ycombinator.com/item?id=33547323
* https://nullprogram.com/blog/2020/07/30/
* https://superfastpython.com/multiprocessing-race-condition-python/
* https://superfastpython.com/parallel-nested-for-loops-in-python/
* https://superfastpython.com/python-asyncio/
* liveness https://www.fluentpython.com/lingo/#liveness https://en.wikipedia.org/wiki/Safety_and_liveness_properties
* task groups https://realpython.com/python311-new-features/#nicer-syntax-for-asynchronous-tasks
* parallelism https://github.com/taichi-dev/taichi
* threading https://news.ycombinator.com/item?id=22514004
* https://www.erichgrunewald.com/posts/gradually-migrating-python-code-to-asyncio/
* https://superfastpython.com/threading-in-python/
* functools.partial for actual parallelization?
* https://www.amazon.com/dp/1937785653
* https://github.com/rednafi/think-async
* https://talkpython.fm/episodes/show/389/18-awesome-asyncio-packages-in-python https://github.com/agronholm/anyio
* parallelism https://pythonspeed.com/articles/concurrency-control/

event loops https://questions.wizardzines.com/event-loops.html
* _event loop_: wrapper around OS service that tells you about network traffic https://www.pythonpodcast.com/episode-40-ben-darnell-on-tornado/
* also used in aeronautics https://news.ycombinator.com/item?id=27115372
* just a for loop https://softwareengineering.stackexchange.com/q/214889/322090

* https://lwn.net/Articles/872869/
* _GIL_: https://pythonspeed.com/articles/python-gil/ https://pythonbytes.fm/episodes/show/23/can-you-grok-the-gil http://python-notes.curiousefficiency.org/en/latest/python3/multicore_python.html https://www.youtube.com/watch?v=7RlqbHCCVyc http://www.dabeaz.com/python/UnderstandingGIL.pdf https://simonwillison.net/2021/Sep/29/the-gil-and-its-effects-on-python-multithreading/ https://docs.python.org/3/glossary.html#term-global-interpreter-lock
changing would break C code https://old.reddit.com/r/Python/comments/sy369l/your_python_4_dream_list/
parallel https://towardsdatascience.com/parallelizing-python-code-3eb3c8e5f9cd
async https://www.youtube.com/watch?v=olT7ejlv0uE&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=43
https://snarky.ca/unravelling-async-and-await/
https://www.encode.io/articles/python-async-frameworks-beyond-developer-tribalism
https://pythonbytes.fm/episodes/show/184/too-many-ways-to-wait-with-await
https://nullprogram.com/blog/2020/05/24/
https://whatisjasongoldstein.com/writing/im-too-stupid-for-asyncio/
https://news.ycombinator.com/item?id=22901856
📍 define 'asynchronous', 'concurrent', 'parallel' https://pythonbytes.fm/episodes/show/161/sloppy-python-can-mean-fast-answers
https://www.cloudcity.io/blog/2019/02/27/things-i-wish-they-told-me-about-multiprocessing-in-python/ https://github.com/sybrenjansen/mpire what does multiprocessing mean exactly? https://news.ycombinator.com/item?id=25220674
multiprocessing https://github.com/spotify/pedalboard
https://realpython.com/intro-to-python-threading/
https://realpython.com/python-concurrency/
* _sink_: 搜 Gmail 'maestro system design'
https://realpython.com/python-async-features/
https://news.ycombinator.com/item?id=22396740
https://lucumr.pocoo.org/2020/1/1/async-pressure/
https://news.ycombinator.com/item?id=22514004
* http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html
* https://news.ycombinator.com/item?id=23243237
* `py-concurrency.pdf` https://www.youtube.com/watch?v=iG6fr81xHKA 'Flask for web dev' chapter 2 https://testdriven.io/blog/building-a-concurrent-web-scraper-with-python-and-selenium/ https://stackabuse.com/overview-of-async-io-in-python-3-7/ https://pyvideo.org/pygotham-2018/how-i-learned-to-stop-worrying-and-love-atomic-banking-blunders-and-concurrency-challenges.html https://realpython.com/quizzes/python-concurrency/
* _asyncio_: stdlib async lib; came in w/ 3.4 https://www.roguelynn.com/archives/
* _uvloop_: faster replacement for asyncio; impl using Cython and libuv (C lib for async)
* _Twisted/Tornado_: Python 2 era event loops, used in Scrapy http://masnun.rocks/2016/11/17/exploring-asyncio-uvloop-sanic-motor/ Tornado is also an app framework https://www.pythonpodcast.com/twisted-with-moshe-zadka-episode-170/ https://glyph.twistedmatrix.com/2019/06/kernel-python.html http://aosabook.org/en/twisted.html
* _gevent_: something to do w/ greenlet http://www.gevent.org/ http://flask.pocoo.org/docs/1.0/design/#thread-locals used by Grinberg in Flask sockets https://blog.miguelgrinberg.com/post/easy-websockets-with-flask-and-gevent
* https://tonybaloney.github.io/posts/async-test-patterns-for-pytest-and-unittest.html
* _thread locals_: exists for duration of thread, seems globally available to your src but are actually copied for each thread https://stackoverflow.com/a/11984017 ❓ why are they typically a bad idea? http://flask.pocoo.org/docs/1.0/design/#thread-locals
* enable isolation amid multi-tentancy (i.e. multiple users) https://blog.sentry.io/2018/11/14/how-to-build-saas-application
* https://stackoverflow.com/questions/1408171/thread-local-storage-in-python
* https://stackoverflow.com/questions/104983/what-is-thread-local-storage-in-python-and-why-do-i-need-it
* 📺 https://training.talkpython.fm/courses/explore_async_python/async-in-python-with-threading-and-multiprocessing
* https://www.youtube.com/watch?v=OxzVApXKWYM
* https://medium.com/@anthonypjshaw/9440d28fa93d
* https://www.youtube.com/watch?v=MCs5OvhV9S4&t=4s
* https://www.youtube.com/watch?v=5dMOYf0b_20
* https://www.youtube.com/watch?v=w2nKIGhXPAM
* https://realpython.com/python-concurrency/
* https://realpython.com/intro-to-python-threading/
* https://www.youtube.com/watch?v=bckD_GK80oY
* https://realpython.com/courses/python-3-concurrency-asyncio-module/
* https://www.youtube.com/watch?v=9zinZmE3Ogk
* https://www.youtube.com/watch?v=MCs5OvhV9S4
* https://bytes.yingw787.com/posts/2019/01/12/concurrency_with_python_threads_and_locks/
* https://bytes.yingw787.com/posts/2019/01/11/concurrency_with_python_why/
* requests have async plugin now https://github.com/encode/requests-async

## exec

📜 https://docs.python.org/3/using/cmdline.html
📰 https://www.pythonmorsels.com/cli-tools/

COMMAND LINE
```sh
python $MODULE  # exec module https://realpython.com/run-python-scripts
python -i $MODULE  # enter pdb after exec https://docs.python.org/3/using/cmdline.html#cmdoption-i
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

## imports

📙 Beazley ch. 10
📜 https://docs.python.org/3/reference/import.html https://docs.python.org/3/library/imp.html

NAMING
* _classes_: camel case
* _modules_: start w/ letter or underscore
* _pkg_: all seem to use hyphens instead of underscores https://stackoverflow.com/a/36611371
* case is significant https://www.python.org/dev/peps/pep-0008/#descriptive-naming-styles

ZA
* pkgutil https://docs.python.org/3/library/pkgutil.html https://chatgpt.com/share/19cfacb1-05ac-4339-a6c8-a8aa4bac6a80

----

🎗️ start here for semantics https://lucumr.pocoo.org/2024/9/9/multiversion-python/

`__all__` https://www.gauge.sh/blog/the-trouble-with-all https://github.com/gauge-sh/tach

> When a Python module or package is imported, __name__ is set to the module's name. Usually, this is the name of the Python file itself without the .py extension: `import configparser; configparser.__name__` https://docs.python.org/3/library/__main__.html
> __main__ is the name of the environment where top-level code is run. "Top-level code" is the first user-specified Python module that starts running. It's "top-level" because it imports all other modules that the program needs. Sometimes "top-level code" is called an entry point to the application. https://docs.python.org/3/library/__main__.html

* happened to me when I was trying to import pandas in a dir named `to-csv` https://stackoverflow.com/a/36250354

https://nedbatchelder.com/blog/202405/one_way_to_fix_python_circular_imports.html
https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/
* https://news.ycombinator.com/item?id=34727287
* _import_: https://docs.python.org/3/glossary.html#term-importing
* _import path_: https://docs.python.org/3/glossary.html#term-import-path
* _importer_: https://docs.python.org/3/glossary.html#term-importer
* _finder_: https://docs.python.org/3/glossary.html#term-importer
* _loader_: https://docs.python.org/3/glossary.html#term-importer
* _module spec_: https://docs.python.org/3/glossary.html#term-module-spec 
* _namespace_: https://docs.python.org/3/glossary.html#term-namespace
* _namespace package_: https://docs.python.org/3/glossary.html#term-namespace-package https://realpython.com/python-namespace-package/
* _path entry_: https://docs.python.org/3/glossary.html#term-path-entry
* _meta path finder_: https://docs.python.org/3/glossary.html#term-meta-path-finder
* _path based finder_: https://docs.python.org/3/glossary.html#term-path-based-finder
* _qualified name_: https://docs.python.org/3/glossary.html#term-qualified-name
* _import time_: https://www.fluentpython.com/lingo/#import_time

modules https://blog.nicholdav.info/four-tips-structuring-research-python/
lazy https://lwn.net/Articles/917280/
https://twitter.com/bbelderbos/status/1598663617506734080
lazy https://talkpython.fm/episodes/show/369/getting-lazy-with-python-imports-and-pep-690

`py-repetitive-paths.md`

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

symbol table
* _private_: all obj in module 
* _public_: obj in mod avaiable when import mod https://realpython.com/python-modules-packages/#the-import-statement https://docs.python.org/3/library/functions.html#locals
* `locals()`: local symbol table https://docs.python.org/3/library/functions.html#locals
* `globals()`: global symbol table
* `dir()`: locals() w/ out values https://stackoverflow.com/a/21961813 https://realpython.com/python-modules-packages/#the-dir-function

---

https://tenthousandmeters.com/blog/python-behind-the-scenes-11-how-the-python-import-system-works/
* _sink_: https://realpython.com/python-modules-packages https://docs.python.org/3/tutorial/modules.html#packages

__people know that the import system sucks__

http://lucumr.pocoo.org/2018/7/13/python/

> The fact that most methods of invoking Python code from the command line break when that code is inside a package, and the two that do work are highly sensitive to the current working directory is all thoroughly confusing for a beginner. I personally believe it is one of the key factors leading to the perception that Python packages are complicated and hard to get right. http://python-notes.curiousefficiency.org/en/latest/python_concepts/import_traps.html Nick Coghlan (CPython dev)

> The problem is that where on your system you need to put a Python library module in order so that a Python main program (or other library) can see it and load it varies in only semi-predictable ways. By version, yes, but there’s also an obscure distinction between site-packages, dist-packages, and what for want of any better term I’ll call root-level modules (no subdirectory under the version directory) that different distributions and even different application packages seem to interpret in different and incompatible ways. The root of the problem seems to be that good practice is under-specified by the Python dev team. - http://esr.ibiblio.org/?p=8161 Eric Raymond

__namespaces__

* `import foo` binds module obj `foo` to name `foo` in current namespace [Smallshire 1 @ 5.7 0:20]
* `import f` binds module obj `foo` to name `f` in current namespace
* `import mod`: place module itself into caller's symbol table; doesn't place `mod` private symbol table into the caller i.e. need to use dot notation to drill down to symbol table `mod.obj1` https://realpython.com/python-modules-packages/#the-import-statement
* `from <mod> import <obj>`: place obj from module into caller's symbol table https://realpython.com/python-modules-packages/#the-import-statement

https://realpython.com/python-namespaces-scope/
https://learndjango.com/tutorials/django-best-practices-imports
https://realpython.com/python-import/
https://github.com/dabeaz-course/practical-python/blob/master/Notes/Contents.md
* _import module from same directory_: `from .views import TemplateView` https://djangoforbeginners.com/pages-app/
* _import obj from module in sibling directory_: pkg.mod.Obj https://djangoforbeginners.com/hello-world/

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
* install: Homebrew https://jacobian.org/2019/nov/11/python-environment-2020/ Linux https://mitelman.engineering/blog/python-best-practice/automating-python-best-practices-for-a-new-project/
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

# 📦 PACKAGING

🗄 `linux.md` packaging
🔍 https://stackoverflow.com/questions/tagged/python-packaging

SEMANTICS
* _packaging_: blanket term for distribution, dependency mgmt, and environment mgmt https://www.b-list.org/weblog/2020/jan/05/packaging
* as synonym for distribution https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 7:10 https://talkpython.fm/episodes/show/245/python-packaging-landscape-in-2020
* _package_: dir containing modules https://docs.python.org/3/glossary.html#term-package
* _distribution_: getting your exec/lib to users
* _dependencies_: using others exec/lib

---

compare to Golang and Rust https://crates.io/crates/basilk https://pypistats.org/packages/__all__

VENV
* _venv_: use `bin` to make https://stackoverflow.com/questions/45293436/how-to-specify-python-version-used-to-create-virtual-2
* _virtual environment_: Python installation + pkgs [tutorial 12.1, Grinberg 4]
* _Docker_: shouldn't just use whole container as env https://hynek.me/articles/python-app-deps-2018/
* _history_: `venv` and `virtualenv` are not the same  ️https://docs.python.org/3/installing/index.html https://chriswarrick.com/blog/2017/07/03/setting-up-a-python-development-environment/#tools-and-management https://stackoverflow.com/a/49967371/6813490

## executable

📜 https://peps.python.org/pep-0711/ https://news.ycombinator.com/item?id=35687895 https://github.com/mitsuhiko/rye/discussions/6

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

ALTERNATIVES
* https://github.com/cole-wilson/sailboat
* Beeware https://github.com/beeware/ https://www.youtube.com/watch?v=WjMDXDHBn1I
* _auto-py-to-exe_: https://pythonbytes.fm/episodes/show/160/your-json-shall-be-streamed
* _Bazel_: https://news.ycombinator.com/item?id=23338316 https://github.com/google/subpar
* _bbfreeze_: https://stackoverflow.com/a/29515965/6813490
* _Cython_: compiles to C extension and runs that https://tryexceptpass.org/article/package-python-as-executable/ http://shvbsle.in/computers-are-fast-but-you-dont-know-it-p1/
* _Nuitka_: https://tryexceptpass.org/article/package-python-as-executable/ https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/ https://snarky.ca/what-is-the-core-of-the-python-programming-language
* _PEX_: https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/
* _py2exe_: https://stackoverflow.com/a/5458807/6813490
* _Shiv_: https://pythonbytes.fm/episodes/show/114/what-should-be-in-the-python-standard-library https://jhermann.github.io/blog/python/deployment/2020/03/08/ship_libs_with_shiv.html https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/
* _XAR_: https://gregoryszorc.com/blog/2018/12/18/distributing-standalone-python-applications/

## library

📙 https://pypackages.com/
📜 https://docs.python.org/3/distributing/index.html
📊 stats https://pepy.tech/
🧀
* https://pypi.org/manage/account/
* https://test.pypi.org/

---

GET NAMESPACE FOR DATACLERK
* PSF https://packaging.python.org/en/latest/tutorials/packaging-projects/
* Real Python https://realpython.com/pypi-publish-python-package/
* Poetry
* Twine https://github.com/pypa/twine
> see termgraph
> do people use? https://talkpython.fm/episodes/transcript/208/packaging-making-the-most-of-pycon-and-more
> tool to replace `stup.py` upload https://talkpython.fm/episodes/transcript/64/inside-the-python-package-index

ZA
* editable installs `pip install -e` https://pgjones.dev/blog/packaging-without-setup-py-2020 https://talkpython.fm/episodes/transcript/208/packaging-making-the-most-of-pycon-and-more 🔍 Twine
* _distribution_: archived package (lib) or binary (executable) https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 6:00 distribution != release https://pydist.com/blog/distributions-vs-releases
* internal https://twitter.com/brianokken/status/1402631045107707908
* _how to_: create archive and put on PyPI https://pgjones.dev/blog/packaging-without-setup-py-2020 https://packaging.python.org/guides/tool-recommendations/#packaging-tool-recommendations don't delete a build from PyPI https://pydist.com/blog/never-delete-a-release https://dustingram.com/articles/2019/04/02/pypi-as-a-service/ https://snarky.ca/how-do-you-verify-pypi-can-be-trusted/ https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 14:30 https://www.youtube.com/watch?v=P3dY3uDmnkU https://www.python.org/dev/peps/pep-0518/ PyPI doesn't have good search mechanism https://github.com/pipxproject/pipx/issues/249#issuecomment-636019556 https://jwodder.github.io/kbits/posts/pypkg-mistakes/ https://news.ycombinator.com/item?id=26733423 fix bad release https://snarky.ca/what-to-do-when-you-botch-a-release-on-pypi/
* internal PyPI https://www.pythonpodcast.com/pulp-with-bihan-zhang-and-austin-macdonald-episode-168/
* example https://github.com/tfeldmann/simplematch
* _deprecation_: https://www.dampfkraft.com/code/how-to-deprecate-a-pypi-package.html https://blog.ovalerio.net/archives/1971 https://sirupsen.com/shitlists/
* _PyPI_: security https://github.com/gitpython-developers/GitPython
* alternative https://pyoven.org/
* find old versions https://pypi-browser.org/
* warnings, PYTHONWARNINGS https://www.reddit.com/r/learnpython/comments/a14ow5/psa_when_developing_set_pythonwarnings/ https://docs.python.org/3/using/cmdline.html#cmdoption-w https://www.youtube.com/watch?v=X0AjcpicNOM&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=35

### structure

---

* https://github.com/fpgmaas/cookiecutter-uv
* _publish_: Flit, Poetry, Twine https://www.youtube.com/watch?v=QX_Nhu1zhlg @ 16:00

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
* https://www.youtube.com/watch?v=niMybnzmzqc
* https://www.youtube.com/watch?v=dlCcnJdh4c4

### history / standards

📜 https://docs.python.org/3/installing/index.html

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
* `pyproject.toml`: spec for using something other than `setup.py`; used by Poetry, Flit https://realpython.com/courses/packaging-with-pyproject-toml/ https://lincolnloop.com/insights/using-pyprojecttoml-in-your-django-project/

FORMATS
* _wheel_: binary https://pythonspeed.com/articles/upgrade-python-3.11/
* _Wheel_: `.whl`; current fmt, built by pip https://testandcode.com/52 @ 16:00 https://www.youtube.com/watch?v=02aAZ8u3wEQ https://realpython.com/python-wheels/ https://pythonwheels.com/
> also a package? see termgraph
* _sdist_: `tar.gz`; ❓ does PyPI need this along with `.whl` and why? https://poetry.eustace.io
* _egg_: `.egg` https://packaging.python.org/discussions/wheel-vs-egg/ https://pythonwheels.com/

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
https://pythonspeed.com/articles/distributing-software/ https://pgjones.dev/blog/trusted-plublishing-2023/

🗄 `list-of-python-pkg-terminology.md`

* _sink_: http://andrewsforge.com/article/python-new-package-landscape/ http://aosabook.org/en/packaging.html  https://chriswarrick.com/blog/2018/07/17/pipenv-promises-a-lot-delivers-very-little/#id11 https://realpython.com/pipenv-guide/ https://www.reddit.com/r/Python/comments/aox5ah/moving_away_from_pipenv/ https://medium.com/@grassfedcode/five-myths-about-pipenv-698c5f198e4b https://medium.com/@DJetelina/pipenv-review-after-using-in-production-a05e7176f3f0 https://jacobian.org/2019/nov/11/python-environment-2020/ https://packaging.python.org/glossary/ https://manikos.github.io/a-tour-on-python-packaging#pip http://aosabook.org/en/packaging.html 

* _tldr_: dep mgmt and distro are intermingled cf. `setuptools`; even with things outside either cf. `setup.cfg` https://www.b-list.org/weblog/2020/jan/05/packaging/ ❓ should all apps also be packages from a 'this makes working with other Python constructs easier?' https://hynek.me/articles/python-app-deps-2018/

* `pyproject.toml` does both distro (replaces `setup.py`) and dep mgmt (`requirements.txt`, `Pipfile`, which is backend by the PyPA); tricky w/ Heroku https://jacobian.org/2019/nov/11/python-environment-2020/ https://snarky.ca/what-the-heck-is-pyproject-toml https://github.com/carlosperate/awesome-pyproject https://lincolnloop.com/insights/using-pyprojecttoml-in-your-django-project/ projects that use https://github.com/carlosperate/awesome-pyproject

## mgmt

🗄️ `linux.md` packaging / manager

ALTERNATIVES
* too many tools https://chriswarrick.com/blog/2023/01/15/how-to-improve-python-packaging/#tooling-proliferation-and-the-python-package-authority
* _hatch_: https://github.com/pypa/hatch
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

### pip

📜 https://pip.pypa.io/en/stable/

* cmd
```sh
install $PKG==$VERSION
install $PKG --user  # per user
list  # global
list --user  # per user
freeze > $FILE  # global
freeze --user > $FILE  # per user
```
* install from forked branch https://stackoverflow.com/questions/20101834/pip-install-from-git-repo-branch

---

* install from lockfile: `pip install -r requirements.txt`; run from inside activated virtualenv
* uninstall from requirements: `pip uninstall -r requirements.txt -y` https://stackoverflow.com/a/53032141
* require venv: `PIP_REQUIRE_VIRTUALENV=true` https://docs.python-guide.org/dev/pip-virtualenv/#requiring-an-active-virtual-environment-for-pip
* pinning w/ pip-tools https://lincolnloop.com/blog/python-dependency-locking-pip-tools
* pip-compile
* local PyPI https://testdriven.io/blog/private-pypi/
```sh
# https://github.com/pywharf/pywharf https://stefan.sofa-rockers.org/2019/04/18/python-packaging-gitlab-conda/ https://pythonbytes.fm/episodes/show/24/i-have-a-local-pypi-server-and-so-do-you https://pydist.com https://github.com/devpi/devpi
# create index
mkdir pypi-local

# populate index w/ pkg
pip3 download -r /Users/zach/Desktop/zvmac/materials/sw/lang/python/create-python-app/requirements.txt

# use index for new project
pip3 install --no-index --find-links=~/Desktop/pypi-local coverage
```
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

### pipx

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

### Poetry

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

* create env - new project: `init - n` creates `pyproject.toml`; deps dir (macOS: `~/Library/Caches/pypoetry` RHEL: `~/.cache/pypoetry/virtualenvs`) and lockfile (`poetry.lock`) not created until you actually install something
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

### uv

📜 https://docs.astral.sh/uv/ https://github.com/astral-sh/uv

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

* https://github.com/fpgmaas/cookiecutter-uv

> They leverage years and years of work that went into migrating the Python ecosystems from setup.py files to eggs and finally wheels. From not having a metadata standard to having one. From coupled to decoupled build systems. Much of what makes Rye so enjoyable were individuals that worked towards making redistributable and downloadable Python binaries a possibility. There was a lot of work that was put into building out an amazing ecosystem of Rust crates and Python libraries needed to make these tools work. All of that brought us to that point where we are today. https://lucumr.pocoo.org/2024/8/21/harvest-season/

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
