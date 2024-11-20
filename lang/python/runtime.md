# ⛩️

## 参考

📙 Shaw python internals https://www.amazon.com/dp/1775093344

## 进步

# 🧫 CONCURRENCY

📙 Beazley ch. 12
🗄
* `linux.md` processes
* `plt.md` concurrency

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

> start with Armin article in `linux.md`
📍 define 'asynchronous', 'concurrent', 'parallel' https://pythonbytes.fm/episodes/show/161/sloppy-python-can-mean-fast-answers
* 📺 https://training.talkpython.fm/courses/explore_async_python/async-in-python-with-threading-and-multiprocessing

* bad concurrency compared to other languages?
> Python (which was the right initial choice because of our founding CTO’s technical background, but its concurrency support, performance, and extensive dynamism make us question whether it’s the right choice for a large-scale backend codebase). None of these was a major mistake, and for some (e.g. Python) the downsides are minimal enough that it’s cheaper for us to continue to pay the increased maintenance burden than to invest in migrating to something theoretically better, but if we were starting a similar codebase from scratch today we’d think hard about whether they were the right choice. https://danluu.com/simple-architectures/

* start here https://pycon-archive.python.org/2024/schedule/presentation/151/index.html 
BYO event loop https://www.youtube.com/watch?v=8I9Rc2Zaos4
https://www.amazon.com/gp/product/1492055026
start here https://www.youtube.com/watch?v=ftmdDlwMwwQ https://www.youtube.com/watch?v=X7vBbelRXn0
coroutine https://docs.python.org/3/glossary.html#term-coroutine-function
https://martinheinz.dev/blog/97
https://higherorderco.com/
https://roadmap.sh/python
https://hakibenita.com/django-concurrency
https://news.ycombinator.com/item?id=41001951

* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#overcoming-gil-with-subinterpreters-and-immutability
* JIT https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#building-a-jit-compiler-for-cpython

SEMANTICS https://python.hamel.dev/concurrency/
* thread
* process
* _coroutine_ https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/ https://www.fluentpython.com/extra/classic-coroutines/ prime https://www.fluentpython.com/lingo https://www.fluentpython.com/lingo/#coroutine https://docs.python.org/3/glossary.html#term-coroutine-function https://docs.python.org/3/glossary.html#term-coroutine https://news.ycombinator.com/item?id=40097681&utm_term=comment

https://realpython.com/python-concurrency/
https://realpython.com/intro-to-python-threading/

https://www.youtube.com/watch?v=Wvh5C3NbQtA

* https://blog.wilsonl.in/hackerverse/
* https://news.ycombinator.com/item?id=39812969
* https://pythonspeed.com/articles/cpu-thread-pool-size
* https://www.photondesigner.com/articles/instant-messenger
* https://pythonspeed.com/articles/gpu-vs-cpu/
* https://tonybaloney.github.io/posts/sub-interpreter-web-workers.html
* thead pools https://pythonspeed.com/articles/two-thread-pools/
* https://pythonspeed.com/articles/optimizing-dithering/
* https://news.ycombinator.com/item?id=37505553
* semaphore https://death.andgravity.com/limit-concurrency
https://news.ycombinator.com/item?id=35073136
* https://news.ycombinator.com/item?id=34483294
* https://news.ycombinator.com/item?id=33547323
* https://nullprogram.com/blog/2020/07/30/
* https://superfastpython.com/multiprocessing-race-condition-python/
* https://superfastpython.com/parallel-nested-for-loops-in-python/
* liveness https://www.fluentpython.com/lingo/#liveness https://en.wikipedia.org/wiki/Safety_and_liveness_properties
* parallelism https://github.com/taichi-dev/taichi
* threading https://news.ycombinator.com/item?id=22514004
* https://superfastpython.com/threading-in-python/
* functools.partial for actual parallelization?
* parallelism https://pythonspeed.com/articles/concurrency-control/

event loops https://questions.wizardzines.com/event-loops.html
* _event loop_: wrapper around OS service that tells you about network traffic https://www.pythonpodcast.com/episode-40-ben-darnell-on-tornado/
* also used in aeronautics https://news.ycombinator.com/item?id=27115372
* just a for loop https://softwareengineering.stackexchange.com/q/214889/322090

* https://lwn.net/Articles/872869/
* _GIL_: https://pythonspeed.com/articles/python-gil/ https://pythonbytes.fm/episodes/show/23/can-you-grok-the-gil http://python-notes.curiousefficiency.org/en/latest/python3/multicore_python.html https://www.youtube.com/watch?v=7RlqbHCCVyc http://www.dabeaz.com/python/UnderstandingGIL.pdf https://simonwillison.net/2021/Sep/29/the-gil-and-its-effects-on-python-multithreading/ https://docs.python.org/3/glossary.html#term-global-interpreter-lock
changing would break C code https://old.reddit.com/r/Python/comments/sy369l/your_python_4_dream_list/
parallel https://towardsdatascience.com/parallelizing-python-code-3eb3c8e5f9cd
https://news.ycombinator.com/item?id=22901856
https://www.cloudcity.io/blog/2019/02/27/things-i-wish-they-told-me-about-multiprocessing-in-python/ https://github.com/sybrenjansen/mpire what does multiprocessing mean exactly? https://news.ycombinator.com/item?id=25220674
multiprocessing https://github.com/spotify/pedalboard
https://realpython.com/intro-to-python-threading/
https://realpython.com/python-concurrency/
* _sink_: 搜 Gmail 'maestro system design'
https://news.ycombinator.com/item?id=22396740
https://news.ycombinator.com/item?id=22514004
* http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html
* https://news.ycombinator.com/item?id=23243237
* `py-concurrency.pdf` https://www.youtube.com/watch?v=iG6fr81xHKA 'Flask for web dev' chapter 2
* enable isolation amid multi-tentancy (i.e. multiple users) https://blog.sentry.io/2018/11/14/how-to-build-saas-application
* https://stackoverflow.com/questions/1408171/thread-local-storage-in-python
* https://stackoverflow.com/questions/104983/what-is-thread-local-storage-in-python-and-why-do-i-need-it
* https://www.youtube.com/watch?v=OxzVApXKWYM
* https://medium.com/@anthonypjshaw/9440d28fa93d
* https://www.youtube.com/watch?v=MCs5OvhV9S4&t=4s
* https://www.youtube.com/watch?v=5dMOYf0b_20
* https://www.youtube.com/watch?v=w2nKIGhXPAM
* https://realpython.com/python-concurrency/
* https://realpython.com/intro-to-python-threading/
* https://www.youtube.com/watch?v=bckD_GK80oY
* https://www.youtube.com/watch?v=9zinZmE3Ogk
* https://www.youtube.com/watch?v=MCs5OvhV9S4
* https://bytes.yingw787.com/posts/2019/01/12/concurrency_with_python_threads_and_locks/
* https://bytes.yingw787.com/posts/2019/01/11/concurrency_with_python_why/

## async

🔗 https://github.com/rednafi/think-async

---

* _asyncio_: stdlib async lib; came in w/ 3.4 https://www.roguelynn.com/archives/
* _Twisted/Tornado_: Python 2 era event loops, used in Scrapy http://masnun.rocks/2016/11/17/exploring-asyncio-uvloop-sanic-motor/ Tornado is also an app framework https://www.pythonpodcast.com/twisted-with-moshe-zadka-episode-170/ https://glyph.twistedmatrix.com/2019/06/kernel-python.html http://aosabook.org/en/twisted.html
* _uvloop_: faster replacement for asyncio; impl using Cython and libuv (C lib for async)
* _gevent_: something to do w/ greenlet http://www.gevent.org/ http://flask.pocoo.org/docs/1.0/design/#thread-locals used by Grinberg in Flask sockets https://blog.miguelgrinberg.com/post/easy-websockets-with-flask-and-gevent
* _thread locals_: exists for duration of thread, seems globally available to your src but are actually copied for each thread https://stackoverflow.com/a/11984017 ❓ why are they typically a bad idea? http://flask.pocoo.org/docs/1.0/design/#thread-locals

* [asyncio problems](https://www.roguelynn.com/words/asyncio-we-did-it-wrong/)
* https://lucumr.pocoo.org/2020/1/1/async-pressure/
* https://realpython.com/python-async-features/
* https://whatisjasongoldstein.com/writing/im-too-stupid-for-asyncio/
* https://www.youtube.com/watch?v=olT7ejlv0uE
* https://talkpython.fm/episodes/show/389/18-awesome-asyncio-packages-in-python https://github.com/agronholm/anyio
* https://testdriven.io/blog/building-a-concurrent-web-scraper-with-python-and-selenium/
* https://stackabuse.com/overview-of-async-io-in-python-3-7/
* https://pyvideo.org/pygotham-2018/how-i-learned-to-stop-worrying-and-love-atomic-banking-blunders-and-concurrency-challenges.html
* https://realpython.com/quizzes/python-concurrency/
* https://realpython.com/courses/python-3-concurrency-asyncio-module/
* https://www.erichgrunewald.com/posts/gradually-migrating-python-code-to-asyncio/
* https://tonybaloney.github.io/posts/async-test-patterns-for-pytest-and-unittest.html
* task groups https://realpython.com/python311-new-features/#nicer-syntax-for-asynchronous-tasks
* https://superfastpython.com/python-asyncio/
* https://snarky.ca/unravelling-async-and-await/
* https://nullprogram.com/blog/2020/05/24/
* https://www.encode.io/articles/python-async-frameworks-beyond-developer-tribalism
* https://pythonbytes.fm/episodes/show/184/too-many-ways-to-wait-with-await
* REPL `python -m asyncio` https://www.pythonmorsels.com/cli-tools/#asyncio
* https://superfastpython.com/asyncio-event-loop-separate-thread/
* https://calpaterson.com/async-python-is-not-faster.html
* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#sync-vs-async-in-python-tools-benchmarks-and-asgiwsgi-explained
* https://realpython.com/python-async-iterators/
* https://sobolevn.me/2020/06/how-async-should-have-been
* requests have async plugin now https://github.com/encode/requests-async
* https://charlesleifer.com/blog/asyncio/
* https://realpython.com/python-async-features/
* https://jacobpadilla.com/articles/recreating-asyncio https://news.ycombinator.com/item?id=40281139
* https://superfastpython.com/asyncio-coroutine-methods/
* async https://textual.textualize.io/blog/2023/03/15/no-async-async-with-python/
* https://www.bitecode.dev/p/asyncio-twisted-tornado-gevent-walk
* _async iterator_: https://docs.python.org/3/glossary.html#term-asynchronous-iterator
* _async generator_: https://docs.python.org/3/glossary.html#term-asynchronous-generator
* _async iteratable_: https://docs.python.org/3/glossary.html#term-asynchronous-iterable
* _async generator iterator_: https://docs.python.org/3/glossary.html#term-asynchronous-generator-iterator
* _awaitable_: https://docs.python.org/3/glossary.html#term-awaitable
* _callback_: https://docs.python.org/3/glossary.html#term-callback
* _context variable_: https://docs.python.org/3/glossary.html#term-context-variable

## threading

## multithreading

# 🐍 CPYTHON

📙 Shaw cpyton internals
🗄 `language.md` compilers

---

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

### alternatives

---

* unique insofar as has to fit many use cases (web, CLI, security) https://talkpython.fm/episodes/show/265/why-is-python-slow 47:00
* things that need to be fast will be written in C https://talkpython.fm/episodes/show/265/why-is-python-slow 50:00
* _pypy_: JIT, supports Python 2 https://news.ycombinator.com/item?id=22928030 http://aosabook.org/en/pypy.html https://ao.gl/when-your-python-code-is-much-faster-with-pypy/ https://www.reddit.com/r/Python/comments/bv50uz/is_anyone_using_pypy_on_production/ https://realpython.com/pypy-faster-python/ https://avi.im/blag/2021/fast-sqlite-inserts/ 📙 Beazly 595
* pypy is dead https://news.ycombinator.com/item?id=33330706
* _numba_: just add annotation https://news.ycombinator.com/item?id=34148455 https://talkpython.fm/episodes/show/265/why-is-python-slow 37:00 https://news.ycombinator.com/item?id=30205848 📙 Beazly 595
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

### GIL

---

start here https://pycon-archive.python.org/2024/schedule/presentation/72/index.html

FREE-THREADING
* https://codspeed.io/blog/state-of-python-3-13-performance-free-threading
* https://pycon-archive.python.org/2024/schedule/presentation/128/index.html
* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#unlocking-the-parallel-universe-subinterpreters-and-free-threading-in-python-313
* https://til.simonwillison.net/python/trying-free-threaded-python
* https://blog.changs.co.uk/free-threaded-python-with-asyncio.html=

https://softwareengineeringdaily.com/2024/10/29/the-big-changes-in-python-3-13-with-lukasz-langa/
* experimental features https://realpython.com/podcasts/rpp/223/

https://realpython.com/python313-new-features/
> You don't need to worry about allocating memory before initializing a data structure, and you don’t need to remember to free the memory when you’re done working with it.
> Another programming problem that Python helps you with is making sure that your code is thread-safe. Simply put, for code to be thread-safe, it needs to ensure that two different threads of execution don’t update the same part of memory at the same time. Python’s solution to this is a bit heavy-handed. It uses a global interpreter lock (GIL) to ensure that only one thread accesses the memory at a time. For most operations, a thread must first acquire the GIL. Because this lock is global—there’s only one GIL—most Python programs are effectively single-threaded, even when they’re running on modern hardware with several CPUs available. Many libraries that are written in C, including NumPy, are able to bypass the GIL by handling thread safety on their own. Such code can often take advantage of computers with multiple cores.
> The most recent attempt, initialized by Sam Gross, is by far the most promising. In fact, you can set up a special free-threaded version of Python 3.13 that doesn’t have a global interpreter lock.

https://realpython.com/python-bindings-overview/
> Python bindings allow you to call functions and pass data from Python to C or C++
> Marshalling is what the Python bindings are doing when they prepare data to move it from Python to C or vice versa. Python bindings need to do marshalling because Python and C store data in different ways. C stores data in the most compact form in memory possible. If you use an uint8_t, then it will only use 8 bits of memory total. In Python, on the other hand, everything is an object. This means that each integer uses several bytes in memory. How many will depend on which version of Python you’re running, your operating system, and other factors. This means that your Python bindings will need to convert a C integer to a Python integer for each integer passed across the boundary. https://en.wikipedia.org/wiki/Marshalling_(computer_science)

* Python 3.13 lays the foundation for Python to get faster before other languages get readable or reach stdlib parity
> Like, internally, I mean, I shouldn't admit it, but I'm also a Python core developer, but I'm just not very active because I have enough of my own stuff going on nowadays.  But internally, the 3.13 is kind of called like a secret 4.0, which everybody who has to do with C-APIs have noticed because, like, unlike the releases before, like 3.12, 3.11, it took quite a while for the ecosystem to catch up with all the changes to the C-API because there's been a lot of changes. I mean, the Py REPL is great. Pablo has made a big push for better error messages, which is also nice. And they continue to get better. Yeah, that's great. This is like the things that are truly user-facing, but things that I don't really care about that much. I mean, I use IPython, so I will probably keep using it still. I just hope that maybe PDB will get better now that we have a better REPL because my favorite debugger, PDBPP, has been broken for two releases. I'm not really excited about anything from 3.12 and 3.13. I'm just excited for what those releases are going to give us in the future. https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek

thread-safe https://realpython.com/python-thread-lock/
* free threaded https://github.com/astral-sh/uv/issues/7193 https://changelog.com/podcast/611
> I want to give a quick shout out to a pytest plugin called pytest-Free Threaded from Anthony Shaw and friends. And this one basically lets you run your tests in the free threaded Python mode and run them with parallelism and stuff like that. https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek

* https://realpython.com/courses/understanding-global-interpreter-lock-gil/
* recent perf improvements https://sumercip.com/posts/making-python-fitter-and-faster/
* adaptive https://github.com/brandtbucher/specialist
* AST is slow https://www.gauge.sh/blog/python-extensions-should-be-lazy
* preprocessor https://pydong.org/posts/PythonsPreprocessor/
* https://snarky.ca/unravelling-attribute-access-in-python/
* https://snarky.ca/mvpy-minimum-viable-python/
* https://news.ycombinator.com/item?id=42051197

### JIT

---

> A just-in-time, or JIT, compiler provides a kind of middle ground, where the interpreter may choose to compile some code while a program is running in order to speed it up. In Python 3.13, there’s a new, experimental JIT compiler. The fact that it’s experimental means that it’s present in Python’s source code, but it’s not enabled by default. Python’s JIT compiler is based on an algorithm called copy-and-patch. The interpreter will look for patterns in your code that match pre-compiled templates and fill in the machine code with specific information like memory addresses of variables. https://realpython.com/python313-new-features/
* _perf_: https://pycon-archive.python.org/2024/schedule/presentation/69/index.html
* https://news.ycombinator.com/item?id=41677131
* https://realpython.com/python313-free-threading-jit/
* https://drew.silcock.dev/blog/everything-you-need-to-know-about-python-3-13/

# 🟨️ ZA

auditing hooks https://stackoverflow.com/questions/63350394/how-to-set-up-and-use-python-audit-hooks https://docs.python.org/3/using/cmdline.html#envvar-PYTHONSTARTUP https://chatgpt.com/c/67094688-4dac-8004-88e8-4eadd79a1d0e

* `__pycache__`: holds bytecode in the form of `.pyc` https://stackoverflow.com/a/28365204/6813490 speeds up module loading https://docs.python.org/3/tutorial/modules.html#compiled-python-files suppress creation of with `export PYTHONDONTWRITEBYTECODE=1` more on bytecode https://blog.jse.li/posts/pyc/ https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md `python -m compileall` https://www.pythonmorsels.com/cli-tools/

* tabs vs. spaces https://www.pythonmorsels.com/cli-tools/#tabnanny

## extensions

📙 Beazley ch. 15

* howto https://kenschutte.com/python-swap-ints/
* simplistic interpreter = C extensions = Python for datascience https://lucumr.pocoo.org/2018/7/13/python/
* can write extensions in Rust https://towardsdatascience.com/nine-rules-for-writing-python-extensions-in-rust-d35ea3a4ec29 https://github.com/RustPython/RustPython https://blog.jerrycodes.com/python-trends-in-2023/ https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/ https://github.com/fulcrum-so/ziggy-pydust https://pythonspeed.com/articles/intro-rust-python-extensions https://pythonspeed.com/articles/intro-rust-python-extensions/
* Rust https://rustpython.github.io/
* using other language in Python e.g. Julia https://www.peterbaumgartner.com/blog/incorporating-julia-into-python-programs/

### PyO3

📜 https://github.com/pyo3/pyo3

```python
#[pyfunction]
fn single_name_to_first_last_names() -> &PyAny {}
```
* https://www.youtube.com/watch?v=UilujdubqVU
> PyO3 is a Rust crate that allows you to write Python modules in Rust. It handles type conversion between Python and Rust, making it easy to call Rust functions from Python. You can use PyO3 to wrap Rust logic (including ORM operations) and expose it as a Python module.
> Maturin simplifies the process of compiling Rust code into Python-compatible packages. This tool builds Rust libraries as Python packages (wheels) that can be installed and imported like any other Python module.

CAN BE SLOWER THAN PYTHON https://pythonspeed.com/articles/faster-text-processing/
* overhead from obj conversion e.g strings (Rust uses UTF, CPython doesn't)
* Python APIs quite optimized, CPython's C can beat Rust e.g. CPython string repr differs based on contents, can use optimized impl specifically for ASCII

---

* https://us.pycon.org/2024/schedule/presentation/113/index.html
* https://pycon-archive.python.org/2024/schedule/presentation/113/index.html
* https://pythonspeed.com/articles/python-extension-performance/
* https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
