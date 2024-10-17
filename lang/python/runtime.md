# ⛩️

## 参考

## 进步

# 🟨️ ZA

---

auditing hooks https://stackoverflow.com/questions/63350394/how-to-set-up-and-use-python-audit-hooks https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP https://chatgpt.com/c/67094688-4dac-8004-88e8-4eadd79a1d0e

* free threaded https://github.com/astral-sh/uv/issues/7193
* GIL, JIT https://news.ycombinator.com/item?id=41677131

* `__pycache__`: holds bytecode in the form of `.pyc` https://stackoverflow.com/a/28365204/6813490 speeds up module loading https://docs.python.org/3/tutorial/modules.html#compiled-python-files suppress creation of with `export PYTHONDONTWRITEBYTECODE=1` more on bytecode https://blog.jse.li/posts/pyc/ https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md

## CPython

📙 Shaw cpyton internals
🗄 `language.md` compilers

---

ALTERNATIVES
* unique insofar as has to fit many use cases (web, CLI, security) https://talkpython.fm/episodes/show/265/why-is-python-slow 47:00
* things that need to be fast will be written in C https://talkpython.fm/episodes/show/265/why-is-python-slow 50:00
* _pypy_: JIT, supports Python 2 https://news.ycombinator.com/item?id=22928030 http://aosabook.org/en/pypy.html https://ao.gl/when-your-python-code-is-much-faster-with-pypy/ https://www.reddit.com/r/Python/comments/bv50uz/is_anyone_using_pypy_on_production/ https://realpython.com/pypy-faster-python/ https://avi.im/blag/2021/fast-sqlite-inserts/ 📙 Beazly 595
* pypy is dead https://news.ycombinator.com/item?id=33330706
* _numba_: just add annotation https://news.ycombinator.com/item?id=34148455 https://talkpython.fm/episodes/show/265/why-is-python-slow 37:00 https://news.ycombinator.com/item?id=30205848 📙 Beazly 595
* _pyjion_: https://talkpython.fm/episodes/show/340/time-to-jit-your-python-with-pyjion
* _Cython_: write Python, get perf of C++ 🗄 'executables'
* _others_: Jython (Java) Iron Python (.NET) call Go from Python https://opendatagroup.github.io/development/2019/06/13/go-ffi.html
* _HPy_: 💀 replacement C API for CPython, out of steam https://hpyproject.org/ https://github.com/hpyproject/hpy https://news.ycombinator.com/item?id=41755183
> Much faster on alternative implementations such as PyPy, GraalPy.
> Debug mode: in debug mode, you can easily identify common problems such as memory leaks, invalid lifetime of objects, invalid usage of APIs. Have you ever forgot a Py_INCREF or Py_DECREF? The HPy debug mode can be activated at runtime to detect these mistakes for you on universal binaries.
> Nicer API: the standard Python/C API shows its age. HPy is designed to overcome some of its limitations, be more consistent, produce better quality extensions and to make it harder to introduce bugs.
> Evolvability: As nicely summarized in PEP 620 the standard Python/C API exposes a lot of internal implementation details which makes it hard to evolve the C API. HPy doesn't have this problem because all internal implementation details are hidden.
* _SPy_: https://www.youtube.com/watch?v=hnQ0oJ_yXlw

STAGES https://www.youtube.com/watch?v=QU158nGABxI 25:30
* parse https://www.pythonpodcast.com/cpython-parser-replacement-episode-285/
* compile
* execute (interpreter loop)

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

## extensions

📙 Beazley ch. 15

* howto https://kenschutte.com/python-swap-ints/
* simplistic interpreter = C extensions = Python for datascience https://lucumr.pocoo.org/2018/7/13/python/
* can write extensions in Rust https://towardsdatascience.com/nine-rules-for-writing-python-extensions-in-rust-d35ea3a4ec29 https://github.com/RustPython/RustPython https://blog.jerrycodes.com/python-trends-in-2023/ https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/ https://github.com/fulcrum-so/ziggy-pydust https://pythonspeed.com/articles/intro-rust-python-extensions https://pythonspeed.com/articles/intro-rust-python-extensions/
* Rust https://rustpython.github.io/

## GIL

---

* recent perf improvements https://sumercip.com/posts/making-python-fitter-and-faster/
* GIL, JIT, free thread https://realpython.com/python313-free-threading-jit/ https://drew.silcock.dev/blog/everything-you-need-to-know-about-python-3-13/ https://blog.changs.co.uk/free-threaded-python-with-asyncio.html
* AST is slow https://www.gauge.sh/blog/python-extensions-should-be-lazy
* preprocessor https://pydong.org/posts/PythonsPreprocessor/
* https://snarky.ca/unravelling-attribute-access-in-python/
* https://snarky.ca/mvpy-minimum-viable-python/
