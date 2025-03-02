# ⛩️

## 参考

🗄 `telemetry.md` monitoring
📚
* Arpaci ch. 13-23, 26-33
* Bryant ch. 12
* Kerrisk lpi 2.7
* Galvin dinosaur ch. 3-5

## 进步

🧠 https://claude.ai/chat/e6817b69-107e-4fc9-9dd6-20c2fea814d7
* _concurrency_: design tasks that can be independently executed
* best for network-bound tasks e.g. callbacks, task queue
* aka async
* _parallelism_: execute tasks simultaneously
* best for CPU/IO-bound tasks
* aka multi-threading
* https://nullprogram.com/blog/2020/04/30/

* _2015_: https://stackoverflow.com/a/47824267 

# 🐍 PYTHON

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

* https://lwn.net/Articles/872869/

parallel https://towardsdatascience.com/parallelizing-python-code-3eb3c8e5f9cd
https://news.ycombinator.com/item?id=22901856
https://www.cloudcity.io/blog/2019/02/27/things-i-wish-they-told-me-about-multiprocessing-in-python/ https://github.com/sybrenjansen/mpire what does multiprocessing mean exactly? https://news.ycombinator.com/item?id=25220674
multiprocessing https://github.com/spotify/pedalboard
https://realpython.com/intro-to-python-threading/
* _sink_: 搜 Gmail 'maestro system design'
https://news.ycombinator.com/item?id=22396740
https://news.ycombinator.com/item?id=22514004
* http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html
* https://news.ycombinator.com/item?id=23243237
* `py-concurrency.pdf` https://www.youtube.com/watch?v=iG6fr81xHKA 'Flask for web dev' chapter 2
* enable isolation amid multitentancy (i.e. multiple users) https://blog.sentry.io/2018/11/14/how-to-build-saas-application
* https://stackoverflow.com/questions/1408171/thread-local-storage-in-python
* https://stackoverflow.com/questions/104983/what-is-thread-local-storage-in-python-and-why-do-i-need-it
* https://www.youtube.com/watch?v=OxzVApXKWYM
* https://medium.com/@anthonypjshaw/9440d28fa93d
* https://www.youtube.com/watch?v=MCs5OvhV9S4&t=4s
* https://www.youtube.com/watch?v=5dMOYf0b_20
* https://www.youtube.com/watch?v=w2nKIGhXPAM
* https://realpython.com/intro-to-python-threading/
* https://www.youtube.com/watch?v=bckD_GK80oY
* https://www.youtube.com/watch?v=9zinZmE3Ogk
* https://www.youtube.com/watch?v=MCs5OvhV9S4
* https://bytes.yingw787.com/posts/2019/01/12/concurrency_with_python_threads_and_locks/
* https://bytes.yingw787.com/posts/2019/01/11/concurrency_with_python_why/
* https://github.com/pyper-dev/pyper

# 🖖 CONCURRENCY

🗄
*️ `architecture/system.md` distributed
* `python/runtime.md` concurrency
📚
* Bobrov grokking https://www.manning.com/books/grokking-concurrency
* Butcher models https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks

SEMANTIC CONFUSION
> Concurrency is hard, unfortunately. https://news.ycombinator.com/item?id=42406919
* multiple computations happen at the same time https://wiki.python.org/moin/Concurrency
* execute multiple tasks through simultaneous execution or time-sharing https://en.wikipedia.org/wiki/Concurrency_(computer_science)
* https://news.ycombinator.com/item?id=42631614

---

📍 define 'asynchronous', 'concurrent', 'parallel' https://pythonbytes.fm/episodes/show/161/sloppy-python-can-mean-fast-answers
* https://realpython.com/python-concurrency/
https://wyounas.github.io/concurrency/2024/12/12/how-concurrency-works-a-visual-guide/
start here https://lucumr.pocoo.org/2024/11/18/threads-beat-async-await/ threads are evil https://www.sqlite.org/faq.html https://avi.im/blag/2024/s3-log/ https://assets.bitbashing.io/papers/concurrency-primer.pdf https://github.com/mrkline/concurrency-primer

https://anishathalye.com/testing-distributed-systems-for-linearizability/ https://github.com/anishathalye/porcupine

* [concurrency != parallelism](https://blog.golang.org/concurrency-is-not-parallelism)
* [multi-threading != parallelism](https://stackoverflow.com/a/806506/6813490) https://news.ycombinator.com/item?id=4495305
* [the guy who wrote SQLAlchemy thinks async is kinda bs](https://news.ycombinator.com/item?id=18113889) + https://techspot.zzzeek.org/2015/02/15/asynchronous-python-and-databases/

BIG PICTURE https://en.wikipedia.org/wiki/Concurrency_(computer_science)
* why: WebSockets https://channels.readthedocs.io/en/latest/

what is a rendering engine? https://github.com/volfpeter/htmy
https://jacko.io/async_intro.html
https://threedots.tech/post/go-test-parallelism/

* MVCC https://www.cs.cmu.edu/~pavlo/blog/2023/04/the-part-of-postgresql-we-hate-the-most.html
* async IO https://registerspill.thorstenball.com/p/joy-and-curiosity-7
* _bricked_: cannot receive further commands https://news.ycombinator.com/item?id=36940626
* clock synchronization https://signalsandthreads.com/clock-synchronization/ https://www.exhypothesi.com/clocks-and-causality/ https://xeiaso.net/blog/nosleep
* _callback_: another func to call after func finishes execution 🗄 `application.md` webhook
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/59370383#59370383 https://danluu.com/butler-lampson-1999/
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/48530284#48530284
* https://news.ycombinator.com/item?id=23496994
* _sleeping barber problem_ http://kachayev.github.io/talks/kharkivpy%230/#/
* reactive in Python https://blog.oakbits.com/introduction-to-rxpy.html
* https://return.co.de/blog/articles/dont-drink-too-much-reactive-cool-aid/

## async

🔗 https://github.com/rednafi/think-async

---

```txt
* Single-threaded, event loop based
* Tasks cooperatively yield control
* Excellent for I/O-bound tasks, especially with many connections
* No GIL issues since it's single-threaded
* Requires async/await syntax
* Lower overhead than threads
```
* leaky bucket https://github.com/mjpieters/aiolimiter
BYO https://lucasoshiro.github.io/software-en/2025-01-25-python_async_iterators/
https://www.youtube.com/watch?v=ftmdDlwMwwQ 
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
* https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#sync-vs-async-in-python-tools-benchmarks-and-asgiwsgi-explained https://www.youtube.com/watch?v=UgoY3ChdqUU
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

## design

* imperative programming fundamentally about order, which makes concurrency hard https://softwareengineeringdaily.com/2020/05/28/distributed-systems-research-with-peter-alvaro/ 7:00
* concurrency is nearly always a bad idea https://www.arp242.net/go-easy.html
* most (web) things are bound by network, not CPU https://talkpython.fm/episodes/show/225/can-subinterpreters-free-us-from-python-s-gil
* concurrency is a bad thing https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/

* why not: hard to reason about, just use a queue or a WebSockets server https://www.david-dahan.com/blog/10-reasons-i-stick-to-django https://danluu.com/concurrency-bugs/
* not worth it
> We’re currently using boring, synchronous, Python, which means that our server processes block while waiting for I/O, like network requests. We previously tried Eventlet, an async framework that would, in theory, let us get more efficiency out of Python, but ran into so many bugs that we decided the CPU and latency cost of waiting for events wasn’t worth the operational pain we had to take on to deal with Eventlet issues. The are other well-known async frameworks for Python, but users of those at scale often also report significant fallout from using those frameworks at scale. Using synchronous Python is expensive, in the sense that we pay for CPU that does nothing but wait during network requests, but since we’re only handling billions of requests a month (for now), the cost of this is low even when using a slow language, like Python, and paying retail public cloud prices. The cost of our engineering team completely dominates the cost of the systems we operate. https://danluu.com/simple-architectures/ 
> Rather than take on the complexity of making our monolith async we farm out long-running tasks (that we don’t want responses to block on) to a queue.
> Yes, goroutines and channels are great: a super-lightweight task abstraction that’s very cheap compared to traditional multithreading. On the other hand, Go only gives us the fundamental building blocks: it’s up to us to make sure we use them safely, avoiding data races or deadlocks. And that can be hard to do! Rust doesn’t have goroutines, but it does have async tasks, which are much like goroutines, only with the usual Rust safety guarantees. There are also some excellent third-party frameworks such as Tokio and Rayon that can just take a bunch of data and automatically figure out the most efficient way to crunch it in parallel. https://bitfieldconsulting.com/posts/rust-and-go

## event loops

event loops https://questions.wizardzines.com/event-loops.html
* _event loop_: wrapper around OS service that tells you about network traffic https://www.pythonpodcast.com/episode-40-ben-darnell-on-tornado/
* also used in aeronautics https://news.ycombinator.com/item?id=27115372
* just a for loop https://softwareengineering.stackexchange.com/q/214889/322090
BYO event loop https://www.youtube.com/watch?v=8I9Rc2Zaos4

# 🛤️ PARALLEL

> You must be this tall to write multi-thread code. https://bholley.net/blog/2015/must-be-this-tall-to-write-multi-threaded-code.html https://news.ycombinator.com/item?id=42407167

---

* https://calmcode.io/shorts/parallel
* https://calmcode.io/course/ray/introduction
* https://github.com/roblaszczak/vgt

## goroutines

---

* _goroutine_: thread but... https://github.com/uber-go/goleak
scheduled by Go runtime instead of OS
* 2KB vs. 1MB for OS thread [ibid @ 1:10]
* _channels_: communication between go routines [‘Go in Action’ 1.1.2]
```golang
# _defer_: execute after surrounding code block returns
func hey() {
	defer fmt.Println("world")
	fmt.Println("hello")
}

# _mutex_: only one goroutine can 
func hi() {
    mutex.Lock() 
    defer mutex.Unlock()
    x = x + 1
}
```
* https://threedots.tech/post/go-test-parallelism/
* vs. concurrency in other languages https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/
* http://www.doxsey.net/blog/go-concurrency-from-the-ground-up https://rcoh.me/posts/why-you-can-have-a-million-go-routines-but-only-1000-java-threads/ https://utcc.utoronto.ca/~cks/space/blog/programming/GoConcurrencyStillNotEasy https://divan.dev/posts/go_concurrency_visualize/

## GIL

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

* https://pythonspeed.com/articles/python-gil/
* https://pythonbytes.fm/episodes/show/23/can-you-grok-the-gil
* http://python-notes.curiousefficiency.org/en/latest/python3/multicore_python.html
* https://www.youtube.com/watch?v=7RlqbHCCVyc
* http://www.dabeaz.com/python/UnderstandingGIL.pdf
* https://simonwillison.net/2021/Sep/29/the-gil-and-its-effects-on-python-multithreading/
* https://docs.python.org/3/glossary.html#term-global-interpreter-lock
* changing would break C code https://old.reddit.com/r/Python/comments/sy369l/your_python_4_dream_list/

## multiprocessing

```txt
The GIL prevents multiple threads from executing Python bytecode simultaneously. So for CPU work, threads end up taking turns, not running in parallel. Multiprocessing sidesteps this by running separate Python interpreters, each with their own GIL.
```

https://www.youtube.com/watch?v=X7vBbelRXn0

## threading

```txt
* One Python process, multiple threads within it
* Shares memory space between threads
* Good for I/O-bound tasks (network calls, file operations)
* Limited by the Global Interpreter Lock (GIL) for CPU-bound tasks
* Built on OS-level threads
```

# 🧵 PROCESSES

* https://neugierig.org/software/blog/2024/05/threading-two-ways.html
* _segmentation fault_: process tries to use inaccessible memory https://corecursive.com/066-sqlite-with-richard-hipp/
* e.g. indexing array OOB, writing to memory address belonging to another process, dereferencing null pointer https://www.youtube.com/watch?v=XIhQYRNBAYs

---

visualize https://github.com/joknarf/pgtree

COMMUNCATION
* _signals_: restart `-HUP/-1` terminate (sent to process) `-TERM/-15` terminate/sigterm (sent to kernel) `kill -KILL/-9 <pid>`
* _intra-process communication (IPC)_: signals, writing to disk (for slow apps), file locking, pipes, message queues 📙 Kerrisk [37,877]

## basics

🔍 https://softwareengineering.stackexchange.com/questions/tagged/concurrency

TAXONOMY https://stackoverflow.com/a/47824267 https://pthorpe92.dev/programming/systems/threads-async-runtimes-part0/
* _thread_: instance of executing program
* incl: stack, heap, text (src) data (var)
* _process_: group of threads [LPI 2.7] https://www.youtube.com/watch?v=4rLW7zg21gI
* _job_: group of processes [LPI 2.13]

storage problems
* _split brain_: data inconsistencies https://en.wikipedia.org/wiki/Split-brain
* e.g. two application instances write to database and search index such that each reads their own value from index 📙 Kleppmann 491/453
* solutions is either serve inconsistencies or serve old results until system heals

single-threaded + multicast https://signalsandthreads.com/multicast-and-the-markets/

* _copy on write_: processes share memory until they need to write, at which point make copy of memory section and write to it (thereby avoiding a page fault) 🗄 `evans-linux.pdf` [3] https://brandur.org/ruby-memory https://github.com/kentonv/lanparty https://simonwillison.net/2025/Jan/31/save-memory-with-bytesio/
* _mutex_: OS version of a lock https://jvns.ca/blog/2016/01/23/sendfile-a-new-to-me-system-call/ https://lwn.net/Articles/827180/ https://mortoray.com/2019/02/20/how-does-a-mutex-work-what-does-it-cost/
* _serial_: execution inside single thread https://pre-commit.com/#hooks-require_serial
* _history_: end of Moore's Law (clock speed increases slowing) = more cores per machine = more parallelization [Kleppmann 6]
* _actor model_: concurrency w/in single process [Kleppmann 4.138] https://news.ycombinator.com/item?id=27505267
* polling/blocking https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html https://cs61.seas.harvard.edu/site/2018/Shell3/ https://en.wikipedia.org/wiki/Polling_(computer_science)

## background

🗄️ `infra.md` task

---


NOHUP
* _nohup_: separates process and terminal https://unix.stackexchange.com/a/148698
* keeps process alive after terminal that started process is killed https://hacker-tools.github.io/remote-machines/
* appends to `nohup.out`
```sh
# keep alive https://github.com/Idnan/bash-guide#d-nohup
nohup <cmd>
# keep alive + run in background
nohup <cmd> &
```

* wait https://www.youtube.com/watch?v=AHAAA7zfT7Q
* _bg_: put job in background
* _fg_: put background job into foreground https://hacker-tools.github.io/shell/
* _&_: run in background
* _nq_: queuing commands https://github.com/leahneukirchen/nq
```sh
# build targets without occupying the terminal
$ nq make clean
$ nq make depends
$ nq make all
$ fq  # look at output without stopping the build
```

memory
* _hard limit_: inherited from parent
* _soft limit_: can be set by user [LPI 2.7]
* _load average_: CPU capacity to deal w/ processes; view w/ `uptime`; 1.0 is perfect capacity but anything above 0.70 should be investigated bc otherwise won't have any headroom for increases https://scoutapm.com/blog/understanding-load-averages
* _OOM killer (out-of-memory)_: https://unix.stackexchange.com/q/153585/331460 https://serverfault.com/a/571326/415712 https://lwn.net/Articles/391222/

telemetry
* _commands_: `uptime`, `top`
* _debug_: strace, application logs 
* _PID_: process ID
* how to use https://will-keleher.com/posts/What-can-you-do-with-a-pid.html
* written to file https://stackoverflow.com/a/8296204/6813490
* lookup PID using process name https://stackoverflow.com/a/11547409/6813490
* _PPID_: parent process ID

## creation

* _location_: $CWD of their parent process [LPI 2.5]
* _initial process_: PID 1, called `init` (or `systemd` on RHEL) [LPI 2.7]
* _inheritance_: process created when parent calls `fork()`
* child inherits UID/GID and stack, heap, data [LPI 2.7]
* `execute()`: child gets their own stack, heap, data [LPI 2.7] 
* _termination_: process calls `exit()` or killed by a signal [LPI 2.7] if parent process killed transitively kill child process https://github.com/jacek-kurlit/pik
* each program executed by the shell starts a new process [LPI 2.13]
* `fork()`: called by existing process (parent) to create new process (child), which is a duplicate [LPI 2.7 31]
* inheritance: child process shares read-only access to parent's program data and gets copy of parent's get data, stack, heap [LPI 2.7 32]
* https://thorstenball.com/blog/2014/06/13/where-did-fork-go/
> Every process running on a Unix system started out as a call to fork(2) followed by a call to execve(2). Well, not every process, since the first process, the init process, the one that starts up the rest of the operating system, didn’t. But every process that came after. The idea is rather simple: fork(2) creates a new process and execve(2) turns the new process into the kind of process you want it to be.
> Let’s say you’re a shell and your user wants to start his productivity utility vimwonderhorse. Now, the first thing you’ve got to do is to start a new process. The reason for that is simple: when the user quits vimwonderhorse you should still be there and wait for the user’s input again. If you, as the shell, would have changed into vimwonderhorse and the user quit, well, then you would be gone, too. So you start a new process with fork(2).
* `execve()`: syscall to load new program, which destroys parental segments [LPI 2.7 32] user-space wrappers incl `execv`, `execle` https://en.wikipedia.org/wiki/Exec_(system_call)#Nomenclature
* _supervisord_: restart processes if they crash

## segments

📙 Kerrisk LPI [31]

* _text_: program source code in machine-code form; read-only so process can't modify [LPI 6.115]
* _data_: static variables (won't change so thread-safe) [LPI 6.116]
> less sure about this definition
* _stack_: 🗄 `architecture.md` memory
* _heap_: 🗄 `architecture.md` memory 📙 Evans linux [16]
* _memory allocator_: keep track of memory usage and get more when necessary from OS; malloc, calloc, et al. 📙 Evans linux [16] https://danluu.com/malloc-tutorial/ https://8dcc.github.io/programming/pool-allocator.html

## traits

TYPES
* _privileged_: any process started by root
* _single-threaded_: program in single thread, IO in separate threads e.g. JS [`go-in-practice.pdf` 1.3.4]
* _multi-threaded_: program in n threads
* _daemon_: long-running background process; no controlling terminal [LPI 34]

## problems

📙 Galvin chapters 5/7 Tanenbaum chapter 6
* _deadlock_: each thread thinks the other is using resource, causing each to not use resource and wait indefinitely for other thread to "stop" using resource https://martinheinz.dev/blog/101 https://medium.com/a-journey-with-go/go-how-are-deadlocks-triggered-2305504ac019
* _livelock_: hallway problem i.e. each thread constantly changing to resolve lock but making no progress
* _race condition_: sequence of events screws up correctness
* vs. data race https://stackoverflow.com/a/18049303 https://www.avanderlee.com/swift/race-condition-vs-data-race/ https://blog.regehr.org/archives/490
> knock knock / race condition / who's there? https://twitter.com/iamdevloper/status/399991896862638081
* _thread safety_: threads don't overwrite data from other threads
