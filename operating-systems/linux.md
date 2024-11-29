# ⛩️

## 参考

📜 https://man7.org/linux/man-pages/index.html
🔍
* https://serverfault.com/
* https://unix.stackexchange.com/
📚
* Evans linux
* Evans za
* Kerrisk lpi
* Stutz cookbook

## 进步

clean up https://github.com/clarkema/x12pp
https://roadmap.sh/linux
BYO linux https://drewdevault.com/2024/05/24/2024-05-24-Bunnix.html

* _24_: combine Homebrew and other managers
* _23_: Conery unix chapter
* _22_: denv
* _19_: symlink dotfiles
* _18_: scripts (`fne`, `qing`, `ding`, `qiu`, `jb`)

# 🗃️ FILES

📙 Galvin dinosaur 11-13 https://news.ycombinator.com/item?id=38512248

FILES https://danluu.com/deconstruct-files/ https://danluu.com/file-consistency/ https://danluu.com/filesystem-errors/
* _file_: sequence of bytes https://netflixtechblog.com/building-netflixs-distributed-tracing-infrastructure-bb856c319304
* or a name in a hierachy, or a file descriptor https://blog.sunfishcode.online/is-everything-is-a-file/?utm_source=pocket_saves
* _file handle_: https://stackoverflow.com/a/3385261/6813490 https://danluu.com/file-consistency/
* _file path_: absolute (from root) relative (to CWD)
* _inode_: file ID; ‘index node’ https://wizardzines.com/comics/inodes/
* _node_: ❓ file, pipe, other stuff c.f. `os.mkdnod()`
* _socket_: type of file that enables communications https://www.youtube.com/watch?v=Lbfe3-v7yE0 figure out how it works with Postgres
* _link_: how file is known by file system i.e. possible to have a file unlinked from file system and therefore cannot be opened by other programs https://pymotw.com/2/tempfile/
* rm broken https://github.com/sahib/rmlint
* they buffer https://news.ycombinator.com/item?id=42275033

ZA
* notifications e.g. inotify, kqueue https://github.com/fsnotify/fsnotify
* file name sorting, `chr()`, `LC_COLLATE` https://rhodesmill.org/brandon/slides/2021-06-colombia-remote/
* trailing slash in path https://tookmund.com/2022/04/importance-of-the-trailing-slash

---

* https://www.youtube.com/watch?v=HbgzrKJvDRw
* file metadata vs. xattrs https://the.exa.website/features/xattrs
* https://news.ycombinator.com/item?id=29164727
https://www.youtube.com/watch?v=Ftg8fjY_YWU 3:40
https://www.youtube.com/watch?v=dDwXnB6XeiA
https://fasterthanli.me/series/reading-files-the-hard-way
* the kids don't even know what directories are https://www.theverge.com/22684730/students-file-folder-directory-structure-education-gen-z

## descriptors

* _file descriptor_: reference to file created when os opens file so that your program can do stuff w/out touching underlying file directly
* akin to Vim buffer
* useful for passing between processes https://jeffknupp.com/blog/2016/03/07/python-with-context-managers/ 
* _0_: stdin
* _1_: stdout
* _2_: stderr
* _&_: both stdout and stderr https://askubuntu.com/a/350216
* also way to mark file descriptor e.g. `2>&1` = "redirect file descriptor 2(stdout) to file descriptor 1" (without `&1` the redirect would assume a file named `1`)  https://askubuntu.com/a/350216 https://stackoverflow.com/a/818284

## fs

🗄️ `telemetry.md` logging

```sh
├── /
│   └── etc  # config
│   └──── resolv.conf  # DNS
```

---

* _file system_: map of file name to file contents
* abstraction of persistent storage hw [Think OS chapter 4 intro]
* way to represent data from hard disk to os
* doesn’t seem like os is responsible for creation of the file system [LPI 1.2.2]
* non-POSIX https://weinholt.se/articles/non-posix-filesystems/
* IPFS https://www.youtube.com/watch?v=5Uj6uR3fp-U https://stevedylan.dev/posts/how-to-run-your-own-ipfs-gateway/ https://macwright.com/2017/08/09/decentralize-ipfs.html https://austinvernon.eth.link/blog/ipfsbasics.html https://austinvernon.eth.link/blog/ipfscodeexample.html
* BYO https://blog.carlosgaldino.com/writing-a-file-system-from-scratch-in-rust.html
* _exFAT_: MS fs for external HD https://superuser.com/q/1292689
* _mount_: 名 (files accessible to OS) 动 (make file system accessible to OS) `df` disk free on mounts https://www.youtube.com/watch?v=gZUVaPPFBJY
* _design_: Linux (single hierarchical dir structure) vs. Windows (each disk has own dir structure) [LPI 27] most operating systems support several types of file systems
* _impl_: NTFS (Windows) EXT, FAT (Linux) HFS+ (Mac) [Think OS 4.2]
* new ones: https://lwn.net/Articles/824855/
* _journal_: ledger of action
* written to before action taken
* in event of power outage can just restart from the journal
* _file metadata_: name, type, size, location, timestamps (create, access, modify)
* _virtual file system_: https://github.com/jedevc https://stackoverflow.com/questions/2910229/what-is-a-virtual-file-system-or-a-file-system-in-userspace https://github.com/rianhunter/dbxfs  https://github.com/azuline/rose
* _NFS (network file system)_: access files over network as if they were on local storage; uses ONC protocol https://en.wikipedia.org/wiki/Network_File_System https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols
* _timestamps_: access (file opened) modify (contents of file edited) change (inode modified i.e. permissions) https://unix.stackexchange.com/a/132661/240456
* _file corruption_: see if things are weird `cat -v` fix w/ `dos2unix`
* _alternate data stream_: hidden data embedded in file; similar to extended attributes in EXT https://www.youtube.com/watch?v=rF4sIxDIhEk
* _Autopsy_: forensics tool for Windows * forensics https://news.ycombinator.com/item?id=26271735

FUSE https://en.wikipedia.org/wiki/Filesystem_in_Userspace
* way to mount Google Drive / Dropbox / iCloud to local filesytem
* behind this as well https://github.com/azuline/rose
* howto https://gwolf.org/2024/10/started-a-guide-to-writing-fuse-filesystems-in-python.html

## globbing

* _glob_: pattern for matching groups of files 📙 Neil practical [6.88]
* filename completion (vs. regex i.e. search text https://www.linuxjournal.com/content/globbing-and-regex-so-similar-so-different) [LPI 25] 
* aka wildcards
* `*`: anything 
* `?`: single char 
* `[]`: range; case-sensitive `cp [a-f]*.png` `rm 02[3-7].mp3`

## IO / pipes

SUBSTITUTION
* _command substition_: capture the output of a command in a single variable
```sh
control_status=$(curl -o /dev/null -s -w "%{http_code}" "$control_url")
```
* _process substition_: use command stdout as if it were a file via tmp file/stream
```sh
$ paste <(tail -n +2 aaon.csv) <(tail -n +2 baldor.csv)
```

OPERATORS
> https://unix.stackexchange.com/a/170573
* `1`: stdout
* `2`: stderr
* `&`: stdout + stderr
* `>`: overwrite
* `>>`: append
* `<`: use file as input e.g. `sqlite3 local.db < schema.sql`
```sh
# stdout           | takes stdin
echo "training 20" | termgraph
```

---

* _pipe_: vmsplice https://qsantos.fr/2024/08/25/linux-pipes-are-slow/
🐍 in Python https://github.com/bugen/pypipe
* _pipe (|)_: directs stdout to stdin

* _fold_: https://blog.balthazar-rouberol.com/text-processing-in-the-shell#fold
* _fmt_: fmt stdout https://github.com/Idnan/bash-guide#f-fmt

* stdout, stderr
```sh
# stderr to file
cmd &> file.log

# capture cmd output
OUTPUT="$(ls -1)"
echo "${OUTPUT}"

# redirect stderr to stdout
2>&1  # `&` marks `1` as a file descriptor vs. a file name https://stackoverflow.com/a/818284

# redirect stderr to null
cat weight.dat | asciigraph -h 10 -c "weight" -cc red 2>/dev/null
```

## links

* _symlink_: file pointing to source file
* find all 🗄 `.bash_profile` sym
* commands pass through to source file
* deleting soft link doesn’t affect source
* file w/ the name/path to another file in it 📙 `evans-linux.pdf` 4
* syntax: `ln -sf /path/to/source /path/to/link`
* `-f`: overwrite if file already exists at location
* _hard link_: file pointing to inode
* still works if original deleted (不明觉厉) https://hacker-tools.github.io/backups/
* doesn't take up file space https://www.lifewire.com/create-symbolic-links-ln-command-4059723

## locations

---

XDG
```python
# https://github.com/tox-dev/platformdirs
from platformdirs import *
user_config_dir()  # /Users/zach/Library/Application Support
user_data_dir()  # /Users/zach/Library/Application Support
site_data_dir()  # /Library/Application Support
user_cache_dir()  # /Users/zach/Library/Caches
user_log_dir()  # /Users/zach/Library/Logs
user_documents_dir()  # /Users/zach/Documents
user_downloads_dir()  # /Users/zach/Downloads
user_pictures_dir()  # /Users/zach/Pictures
user_videos_dir()  # /Users/zach/Movies
user_music_dir()  # /Users/zach/Music
user_desktop_dir()  # /Users/zach/Desktop
user_runtime_dir()  # /Users/zach/Library/Caches/TemporaryItems
```
* https://0x46.net/thoughts/2019/02/01/dotfile-madness/
* https://specifications.freedesktop.org/basedir-spec/latest/
* https://github.com/tox-dev/platformdirs
* https://github.com/Zaloog/kanban-tui
* `XDG_CONFIG_HOME`: typically `$HOME/.config` https://github.com/lusingander/serie/issues/25 https://github.com/kraanzu/dooit/issues/195
> On macOS, `$XDG_CONFIG_HOME` maps to `$HOME/.config`. Another popular path for config files is `/Users/USER/Library/Application\ Support`. Does this file path have a env var name in the way that $XDG_CONFIG_HOME does?
* you have to manually specify?
> If you want to change the config directory: macOS `export XDG_CONFIG_HOME="$HOME/.config` https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md

* `/var`: for [variable data files](https://unix.stackexchange.com/a/264345)
* `~/.config`: config for CLIs (http-prompt, wireshark)
* `/tmp`: can be either stored on disk or using tmpfs
* `/dev/shm`: alternative to `/tmp` https://superuser.com/a/45509 https://pythonspeed.com/articles/gunicorn-in-docker/
* `/dev/null`: special file for redirecting stuff you don't care about e.g. stderr `rm FILE 2> /dev/null` https://askubuntu.com/a/12099
* _tmpfs_: looks like storage but is actually memory https://docs.gunicorn.org/en/stable/faq.html#how-do-i-avoid-gunicorn-excessively-blocking-in-os-fchmod
* _FHS_: standard for where things should be located on Linux [‘Practical Guide to Linux Commands’ pg. 12] https://apple.stackexchange.com/a/119265/328389 https://www.youtube.com/watch?v=FSxab6etkzg
* _Mac_: `/private/tmp` = 类似 Linux var/tmp, kinda https://apple.stackexchange.com/a/131080 `/usr/local` Homebrew, git, go `/Library` (SDKs) `/System/Library/Frameworks` (binaries)
* _Linux_: `var`/`tmp` temp files `/etc` (settings files, third-party installs) [Clinton 'Linux in Action' 30] `/mnt` (additional volumes) [Sweigert Automate the Boring Stuff chapter 8]
* throw away stdout: `2>/dev/null` https://askubuntu.com/q/350208
* `/dev/null`: black hole `rm local.db 2> /dev/null; sqlite3 local.db < schema.sql`
📝 [`/dev/null`](https://askubuntu.com/a/12099) special file for dumping this sort of thing

# 🧵 PROCESSES

🗄
* `os/tools.md` monitoring
* `python/runtime.md` concurrency
* `src.md` concurrency
📙
* Arpaci ch. 13-23
* Kerrisk lpi 2.7
* Galvin dinosaur ch. 3-5

TAXONOMY https://stackoverflow.com/a/47824267 https://pthorpe92.dev/programming/systems/threads-async-runtimes-part0/
* _thread_: instance of executing program
* incl: stack, heap, text (src) data (var)
* _process_: group of threads [LPI 2.7] https://www.youtube.com/watch?v=4rLW7zg21gI
* _job_: group of processes [LPI 2.13]

ZA
* _segmentation fault_: process tries to use inaccessible memory https://corecursive.com/066-sqlite-with-richard-hipp/
* e.g. indexing array OOB, writing to memory address belonging to another process, dereferencing null pointer https://www.youtube.com/watch?v=XIhQYRNBAYs

---

visualize https://github.com/joknarf/pgtree

https://thorstenball.com/blog/2014/06/13/where-did-fork-go/
> Every process running on a Unix system started out as a call to fork(2) followed by a call to execve(2). Well, not every process, since the first process, the init process, the one that starts up the rest of the operating system, didn’t. But every process that came after. The idea is rather simple: fork(2) creates a new process and execve(2) turns the new process into the kind of process you want it to be.
> Let’s say you’re a shell and your user wants to start his productivity utility vimwonderhorse. Now, the first thing you’ve got to do is to start a new process. The reason for that is simple: when the user quits vimwonderhorse you should still be there and wait for the user’s input again. If you, as the shell, would have changed into vimwonderhorse and the user quit, well, then you would be gone, too. So you start a new process with fork(2).

types
* _privileged_: any process started by root
* _single-threaded_: program in single thread, IO in separate threads e.g. JS [`go-in-practice.pdf` 1.3.4]
* _multi-threaded_: program in n threads
* _daemon_: long-running background process; no controlling terminal [LPI 34]

segments [LPI 31]
* _text_: program source code in machine-code form; read-only so process can't modify [LPI 6.115]
* _data_: static variables (won't change so thread-safe) [LPI 6.116]
> less sure about this definition
* _stack_: 🗄 `architecture.md` memory
* _heap_: 🗄 `architecture.md` memory 📙 Evans linux [16]
* _memory allocator_: keep track of memory usage and get more when necessary from OS; malloc, calloc, et al. 📙 Evans linux [16] https://danluu.com/malloc-tutorial/

creation
* `fork()`: called by existing process (parent) to create new process (child), which is a duplicate [LPI 2.7 31]
* inheritance: child process shares read-only access to parent's program data and gets copy of parent's get data, stack, heap [LPI 2.7 32]
* `execve()`: syscall to load new program, which destroys parental segments [LPI 2.7 32] user-space wrappers incl `execv`, `execle` https://en.wikipedia.org/wiki/Exec_(system_call)#Nomenclature
* _supervisord_: restart processes if they crash

---

* each program executed by the shell starts a new process [LPI 2.13]
* _location_: $CWD of their parent process [LPI 2.5]
* _initial process_: PID 1, called `init` (or `systemd` on RHEL) [LPI 2.7]
* _inheritance_: process created when parent calls `fork()`
* child inherits UID/GID and stack, heap, data [LPI 2.7]
* `execute()`: child gets their own stack, heap, data [LPI 2.7] 
* _termination_: process calls `exit()` or killed by a signal [LPI 2.7] if parent process killed transitively kill child process https://github.com/jacek-kurlit/pik

communcation
* _signals_: restart `-HUP/-1` terminate (sent to process) `-TERM/-15` terminate/sigterm (sent to kernel) `kill -KILL/-9 <pid>`
* _intra-process communication (IPC)_: signals, writing to disk (for slow apps), file locking, pipes, message queues 📙 Kerrisk [37,877]

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

## concurrency

🗄
*️ `architecture/system.md` distributed
* `python/runtime.md` concurrency
📚
* Bobrov https://www.manning.com/books/grokking-concurrency
* Butcher models https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks

---

start here https://lucumr.pocoo.org/2024/11/18/threads-beat-async-await/ threads are evil https://www.sqlite.org/faq.html https://avi.im/blag/2024/s3-log/

> Yes, goroutines and channels are great: a super-lightweight task abstraction that’s very cheap compared to traditional multithreading. On the other hand, Go only gives us the fundamental building blocks: it’s up to us to make sure we use them safely, avoiding data races or deadlocks. And that can be hard to do! Rust doesn’t have goroutines, but it does have async tasks, which are much like goroutines, only with the usual Rust safety guarantees. There are also some excellent third-party frameworks such as Tokio and Rayon that can just take a bunch of data and automatically figure out the most efficient way to crunch it in parallel. https://bitfieldconsulting.com/posts/rust-and-go

https://anishathalye.com/testing-distributed-systems-for-linearizability/ https://github.com/anishathalye/porcupine

* [concurrency != parallelism](https://blog.golang.org/concurrency-is-not-parallelism)
* [multi-threading != parallelism](https://stackoverflow.com/a/806506/6813490) https://news.ycombinator.com/item?id=4495305
* [the guy who wrote SQLAlchemy thinks async is kinda bs](https://news.ycombinator.com/item?id=18113889) + https://techspot.zzzeek.org/2015/02/15/asynchronous-python-and-databases/

BIG PICTURE https://en.wikipedia.org/wiki/Concurrency_(computer_science)
* why: WebSockets https://channels.readthedocs.io/en/latest/
* why not: hard to reason about, just use a queue or a WebSockets server https://www.david-dahan.com/blog/10-reasons-i-stick-to-django https://danluu.com/concurrency-bugs/
* not worth it
> We’re currently using boring, synchronous, Python, which means that our server processes block while waiting for I/O, like network requests. We previously tried Eventlet, an async framework that would, in theory, let us get more efficiency out of Python, but ran into so many bugs that we decided the CPU and latency cost of waiting for events wasn’t worth the operational pain we had to take on to deal with Eventlet issues. The are other well-known async frameworks for Python, but users of those at scale often also report significant fallout from using those frameworks at scale. Using synchronous Python is expensive, in the sense that we pay for CPU that does nothing but wait during network requests, but since we’re only handling billions of requests a month (for now), the cost of this is low even when using a slow language, like Python, and paying retail public cloud prices. The cost of our engineering team completely dominates the cost of the systems we operate. https://danluu.com/simple-architectures/ 
> Rather than take on the complexity of making our monolith async we farm out long-running tasks (that we don’t want responses to block on) to a queue.

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
* imperative programming fundamentally about order, which makes concurrency hard https://softwareengineeringdaily.com/2020/05/28/distributed-systems-research-with-peter-alvaro/ 7:00
* concurrency is nearly always a bad idea https://www.arp242.net/go-easy.html
* https://news.ycombinator.com/item?id=23496994
* _sleeping barber problem_ http://kachayev.github.io/talks/kharkivpy%230/#/
* reactive in Python https://blog.oakbits.com/introduction-to-rxpy.html
* https://return.co.de/blog/articles/dont-drink-too-much-reactive-cool-aid/
* most (web) things are bound by network, not CPU https://talkpython.fm/episodes/show/225/can-subinterpreters-free-us-from-python-s-gil
* concurrency is a bad thing https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/

### golang

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

## threads

🔍 https://softwareengineering.stackexchange.com/questions/tagged/concurrency
📚
* Arpaci ch. 26-33
* Bryant ch. 12

---

https://neugierig.org/software/blog/2024/05/threading-two-ways.html

basics
* _concurrency_: design tasks that can be independently executed
* best for network-bound tasks e.g. callbacks, task queue
* aka async
* _parallelism_: execute tasks simultaneously
* best for CPU/IO-bound tasks
* aka multi-threading
* https://nullprogram.com/blog/2020/04/30/

problems 📙 Galvin chapters 5/7 Tanenbaum chapter 6
* _deadlock_: each thread thinks the other is using resource, causing each to not use resource and wait indefinitely for other thread to "stop" using resource https://martinheinz.dev/blog/101 https://medium.com/a-journey-with-go/go-how-are-deadlocks-triggered-2305504ac019
* _livelock_: hallway problem i.e. each thread constantly changing to resolve lock but making no progress
* _race condition_: sequence of events screws up correctness
* vs. data race https://stackoverflow.com/a/18049303 https://www.avanderlee.com/swift/race-condition-vs-data-race/ https://blog.regehr.org/archives/490
> knock knock / race condition / who's there? https://twitter.com/iamdevloper/status/399991896862638081
* _thread safety_: threads don't overwrite data from other threads

storage problems
* _split brain_: data inconsistencies https://en.wikipedia.org/wiki/Split-brain
* e.g. two application instances write to database and search index such that each reads their own value from index 📙 Kleppmann 491/453
* solutions is either serve inconsistencies or serve old results until system heals

single-threaded + multicast https://signalsandthreads.com/multicast-and-the-markets/

* _copy on write_: processes share memory until they need to write, at which point make copy of memory section and write to it (thereby avoiding a page fault) 🗄 `evans-linux.pdf` [3] https://brandur.org/ruby-memory https://github.com/kentonv/lanparty
* _mutex_: OS version of a lock https://jvns.ca/blog/2016/01/23/sendfile-a-new-to-me-system-call/ https://lwn.net/Articles/827180/ https://mortoray.com/2019/02/20/how-does-a-mutex-work-what-does-it-cost/
* _serial_: execution inside single thread https://pre-commit.com/#hooks-require_serial
* _history_: end of Moore's Law (clock speed increases slowing) = more cores per machine = more parallelization [Kleppmann 6]
* _actor model_: concurrency w/in single process [Kleppmann 4.138] https://news.ycombinator.com/item?id=27505267
* polling/blocking https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html https://cs61.seas.harvard.edu/site/2018/Shell3/ https://en.wikipedia.org/wiki/Polling_(computer_science)

## tracing

🗄
* processes
* `python.md` profiling
* `telemetry.md` tracing
📚
* Evans debug tools
* Evans perf
* Evans strace
* Evans tracing

VOCAB
* _monitor_: track errors; continuous
* _trace_: explore errors; ad hoc
* _profile_: measure perf (which LOC exec + exec time); ad hoc

TOOLS
* _beetrace_: 🐍 https://github.com/furkanonder/beetrace

---

flamegraph https://github.com/laixintao/flameshow

https://events.linuxfoundation.org/wp-content/uploads/2022/10/elena-zannoni-tracing-tutorial-LF-2021.pdf

* strace, ptrace https://nullprogram.com/blog/2018/06/23/
* magic trace https://github.com/janestreet/magic-trace
* ptrace https://medium.com/@lizrice/a-debugger-from-scratch-part-1-7f55417bc85f
* strace https://jvns.ca/blog/2021/04/03/what-problems-do-people-solve-with-strace/
* dtruss https://blog.safia.rocks/post/173241985600/unraveling-rm-what-happens-when-you-run-it

❌ normal debugging: know the language, look at src, print statements/debugger
✅ `strace` debugging: 'these are the system calls your program is making'
📝 don't run strace on production processes (or anything that needs to run at normal speed)

### bpf

EBPF https://www.brendangregg.com/
* https://blog.smidt.dev/posts/0003/
* _flamegraph_: visualization for CPU usage https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions https://flamegraph.com/ https://github.com/laixintao/flameshow
* https://www.youtube.com/watch?v=bGAVrtb_tFs
* https://coroot.com/blog/engineering/instrumenting-python-gil-with-ebpf/
* https://github.com/ZingerLittleBee/netop
* https://sazak.io/articles/an-applied-introduction-to-ebpf-with-go-2024-06-06
* https://news.ycombinator.com/item?id=27435081
* https://www.brendangregg.com/blog/2022-04-15/netflix-farewell-1.html
* https://ebpf.io/what-is-ebpf/ https://softwareengineeringdaily.com/2023/03/06/ebpf-with-thomas-graf/
* https://www.polarsignals.com/blog/posts/2023/10/04/profiling-python-and-ruby-with-ebpf
* https://about.gitlab.com/blog/2022/11/28/how-we-diagnosed-and-resolved-redis-latency-spikes/
* https://softwareengineeringdaily.com/2022/07/15/continuous-profiling-using-ebpf-with-frederic-branczyk/
* https://github.com/keyval-dev/odigos
* https://github.com/google/gops
* https://thume.ca/2023/12/02/tracing-methods/

# 🟨 ZA

---

* Unix timestamp https://news.ycombinator.com/item?id=33341652
* sysadmins https://xkcd.com/705/
> Somewhere there’s a database programmer surrounded by empty Mountain Dew bottles whose husband thinks she’s dead. And if these people stop, the world burns. Most people don’t even know what sysadmins do, but trust me, if they all took a lunch break at the same time they wouldn’t make it to the deli before you ran out of bullets protecting your canned goods from roving bands of mutants. http://www.stilldrinking.org/programming-sucks
* trash: https://github.com/andreafrancia/trash-cli recover deleted files https://sabotage-linux.github.io/blog/6/ alternative to rm https://github.com/alanzchen/rm-protection
* _tar_: work w/ compressed files https://terminaltrove.com/ouch/
* extract `-xf`
* compress w/ gzip `.tar.gz`
* aunpack/atoo https://hacker-tools.github.io/command-line/
* _line termination_: delimiter for end of line
* NL on *nix, CRLF on Windows https://stackoverflow.com/a/12747850/6813490
* sockets 📙 Bryant (11)

logging
* `syslog`: daemon that ingests logs and routes to log files
* `/var/log`: storage location
* viewer https://lnav.org/
* `journalctl`: view systemd and kernel logs https://hacker-tools.github.io/machine-introspection/

ports 🗄 `tcp-ip.md` packet
* _hosts file_: `/etc/hosts`; map of domains to IP addresses
* _privileged_: ports < 1024 are privileged and can only be bound to processes running as root
* _port knocking_: https://news.ycombinator.com/item?id=23187662
* _netstat_: check if port open https://askubuntu.com/a/224396 https://serverfault.com/a/309058 macOS has different flags https://www.lifewire.com/using-netstat-command-on-mac-4176069

Raspberry Pi
* use for Funkwhale
* https://news.ycombinator.com/item?id=42200099
* https://uglyduck.ca/my-pi-desktop/
* https://news.ycombinator.com/item?id=24965614
* https://www.canakit.com/raspberry-pi-4-8gb.html
* https://www.jeffgeerling.com/project/raspberry-pi-dramble
* https://www.jeffgeerling.com/blog/2020/i-replaced-my-macbook-pro-raspberry-pi-4-8gb-day
* desktop https://www.raspberrypi.org/products/raspberry-pi-4-desktop-kit/

daemons
* _systemd_: spec for service start https://opensource.com/article/20/4/systemd https://news.ycombinator.com/item?id=42036305
> To configure services, you pretty much have to interact with systemd these days, for better or for worse. Most services on your system will have a systemd service file that defines a systemd unit. These files define what command to run when that services is started, how to stop it, where to log things, etc. They’re usually not too bad to read, and you can find most of them in /usr/lib/systemd/system/. You can also define your own in /etc/systemd/system. https://missing.csail.mit.edu/2019/machine-introspection/
* _systemctl_: control service
> Once you have a systemd service in mind, you use the systemctl command to interact with it. systemctl enable UNIT will set the service to start on boot (disable removes it again), and start, stop, and restart will do what you expect. If something goes wrong, systemd will let you know, and you can use journalctl -u UNIT to see the application’s log. You can also use systemctl status to see how all your system services are doing. If your boot feels slow, it’s probably due to a couple of slow services, and you can use systemd-analyze (try it with blame) to figure out which ones. https://missing.csail.mit.edu/2019/machine-introspection/
* https://github.com/torfsen/python-systemd-tutorial
* https://systemd-by-example.com/
* can conf service to start on boot, restart if crashes https://www.reddit.com/r/Ubuntu/comments/7j5qgj/gunicorn_daemon_vs_gunicornservice_on_ubuntu_1604/
* preceded by Upstart https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04 https://christine.website/talks/systemd-the-good-parts-2021-05-16 https://unixsheikh.com/articles/systemd-isnt-safe-to-run-anywhere.html

BOOT
* https://www.youtube.com/watch?v=XpFsMB6FoOs
* _bootloader_: loads os e.g. GRUB
* _BIOS_: first step when powering on i.e. before bootloader
* https://utcc.utoronto.ca/~cks/space/blog/linux/LinuxBootOverview?
* https://news.ycombinator.com/item?id=35229045

## date/time

🗄️ `application.md` NTP

---

https://github.com/cdown/tzupdate

`date -u`
* backup w/ timestamp: `touch "$(date +%Y%m%d_%H%M%S).bak"` https://unix.stackexchange.com/a/96383/331460
* _touch_: make new file or update timestamp
* create dir with current date
```sh
today="$(date +'%Y-%m')"
hour_min="$(date +'%H-%M-%S')"
\cd $HOME/Documents
dir="my-dir-$today-$hour_min"
mkdir "$dir"
```
```sh
# https://news.ycombinator.com/item?id=31575076
function tz(){
    cal -3
    echo
    echo -n "Local:       "
    date --rfc-3339=s
    echo -n "UTC:         "
    date -u --rfc-3339=s
    echo -n "New York     "
    TZ='America/New_York' date --rfc-3339=s
    echo -n "London:      "
    TZ='Europe/London' date --rfc-3339=s
    echo -n "New Zealand: "
    TZ='Pacific/Auckland' date --rfc-3339=s
}
```

## exit codes

---

```sh
mkdir /some/protected/directory
if [ $? -ne 0 ]; then
    echo "Command failed"
    exit 1
fi
echo "Command succeeded"
```

* _0_: success 
* _1_: err 
* _2_: "misuse of shell built-ins" (e.g. "no such file" err) https://askubuntu.com/a/892605 
* _?_: var for last cmd's exit code e.g. `echo "hi"; echo $?  #0` https://askubuntu.com/a/892607
* _127_: you use a command in your script that the shell doesn't know about
* _130_: termination via CTRL c
* _137_: script fails (128) and then received sig kill (9) from OOM killer https://stackoverflow.com/a/1041309
* cleanup on exit https://github.com/Idnan/bash-guide#exit-traps
* are less clear than you think https://news.ycombinator.com/item?id=24267155
* get exit code of last command: `$?` https://www.freecodecamp.org/news/docker-exec-how-to-run-a-command-inside-a-docker-image-or-container/
* `exit`: close shell
* `return`: exit script
* _sink_: http://www.tldp.org/LDP/abs/html/exitcodes.html https://en.wikipedia.org/wiki/Exit_status#Shell_and_scripts https://bencane.com/2014/09/02/understanding-exit-codes-and-how-to-use-them-in-bash-scripts/
```sh
~/Desktop/zvmac/materials/sw/algos/algos (master *)$ rg austen  # no results
~/Desktop/zvmac/materials/sw/algos/algos (master *)$ echo "$?"  # 1
```

## kernel

🗄 `languages.md` 'C'

🔍 https://livegrep.com/search/linux

📦 https://git.kernel.org/

* Rust https://news.ycombinator.com/item?id=42318644
* Rust, QEMU https://news.ycombinator.com/item?id=42253814
* microkernel https://drewdevault.com/2022/06/13/helios.html
* _info_: `sysctl -n hw.ncpu` (number of cores) should be file `/etc/<distro>-release` (although of course not on macOS)
* _user space_: shell, user processes
* _kernel space_: stuff kernel controls
* _components_: https://makelinux.github.io/kernel/map/
* _things kernel does_: talks to cpu, mem, disk, network e.g. keyboard interrupt to figure out which key you type, knows you have HD and how to write to it, schedules procceses https://jvns.ca/blog/2013/10/02/day-3-what-does-the-linux-kernel-even-do/
* _RTOS_: lower latency constraints for scheduler  https://stratechery.com/2023/apple-vision/
* _driver_: kernel module for managing hardware device
* BYO https://s-matyukevich.github.io/raspberry-pi-os/
* kernel message logs https://zaiste.net/posts/shell-commands-rust/#rmesg
* _sink_: https://softwareengineeringdaily.com/2019/03/14/linux-kernel-development-with-shuah-khan/
* protection rings 📙 Conery [380]

SYSTEM CALLS (SYSCALL)
* https://neugierig.org/software/blog/2024/09/retrowin32-syscalls.html
* https://blog.cerebralab.com/If_I_were_to_select_the_worst_Linux_syscall
* API for kernel space e.g. create file, spawn process http://thevivekpandey.github.io/posts/2017-09-25-linux-system-calls.html
* actually pretty tricky, hence most common sys calls being wrapped by glibc
> Why does glibc do that? Why call clone(2) instead of fork(2)? And why does it wrap system calls in library functions? After digging around a bit I found out that making a system call is actually harder than just calling fork() somewhere in my code. I’d need to know the unique number of system call I was about to make, set up registers, call a special instruction (which varies on different machine architectures) to switch to kernel mode and then handle the results when I’m back in user space. By providing a wrapper around certain system calls glibc makes it a lot easier and portable for developers to use system calls. There is still the possibility to use syscall(2) to call system calls somewhat more directly. - https://thorstenball.com/blog/2014/06/13/where-did-fork-go/

## man pages

🗄️ `doc.md` repos

---

* Visidata handles this well
* run by Michael Kerrisk https://man7.org/tlpi/faq/index.html#many_errata https://www.kernel.org/doc/man-pages/
* why do they look so much worse in the terminal? https://man7.org/linux/man-pages/man1/bash.1.html 🗄 `shell.md` bat
* colorize https://danyspin97.org/blog/colorize-your-cli/
* with bat https://github.com/sharkdp/bat#man https://github.com/eth-p/bat-extras
* how to make one for your own program: https://github.com/bootandy/dust/issues/45 https://github.com/sharkdp/bat/blob/master/assets/manual/bat.1.in https://github.com/Canop/broot/blob/master/man/page `man bat -w` https://unix.stackexchange.com/a/6892/331460 http://www.tldp.org/HOWTO/Man-Page/

## scripts

🔗 http://gnu.ist.utl.pt/prep/standards/html_node/Command_002dLine-Interfaces.html

DESIGN 🗄 `protocols.md` serialization `python.md` UI

TUI
* https://news.ycombinator.com/item?id=40273177
* _curses_: UNIX https://docs.python.org/3/howto/curses.html https://github.com/cmus/cmus 
* ncurses
* https://news.ycombinator.com/item?id=37418424
* TUI for bash https://github.com/charmbracelet/gum
* design https://www.micahlerner.com/2021/07/14/unix-shell-programming-the-next-50-years.html 🗣 Dan Luu https://borretti.me/article/shells-are-two-things extensions https://github.com/dotenvx/dotenvx/pull/426

CLI IMPL LANGUAGE
> use Rust for CLI and Python for business logic? https://github.com/chubin/wttr.in
* tracking user info https://www.visidata.org/blog/2021/usage-graphs/
> build modern CLI applications without worrying about user accounts, data storage and encryption https://github.com/charmbracelet/charm#charm-kv
* fuzzy find https://github.com/denisidoro/navi
* C: ✅ fast ❌ development speed
* Nim: ✅ distribution ❌ maturity https://ssalewski.de/nimprogramming.html
* Python: ✅ exploratory ❌ distribution
* Go: ✅ distribution, fast startup https://news.ycombinator.com/item?id=23319684 ❌ stdlib lib lib not good
* Rust: ✅ speed, Clap library https://news.ycombinator.com/item?id=23320411 better for cross platform https://cuchi.me/posts/go-vs-rust ❌ language itself

EXEC
* specify interpreter from shell e.g. `python $SCRIPT` 📙 Conery [390]
* file extensions don't matter to program execution https://askubuntu.com/a/764126
* _shebang line_: specific interpreter from script `./ $SCRIPT` 📙 Conery [391]
```sh
# BASH
#!/usr/bin/env bash

# Python https://realpython.com/python-shebang/
#!/usr/bin/env python3  # $PATH
#!/usr/bin/python3.6    # absolute path
```
* _source_: load/export variable/script to current shell's env 📙 Conery [401]
* `source` = `.` https://stackoverflow.com/a/16619261

WHERE TO PUT SHELL SCRIPTS
* `/usr/local/bin` [Linux Cookbook A.3.4]
* `~/bin`
* `fooDir` --> `~/bin`

INPUT https://news.ycombinator.com/item?id=31293032
* https://nullprogram.com/blog/2020/08/01/
* _flag_: hyphen e.g. `cmd --from here --to there`
* letter (`-h`) word (`--help`) https://www.youtube.com/watch?v=FOQHGz__OLs
* _arg_: no hypen `cmd here there`; less clear than flags bc have to remember which is src and which is target https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46

ZA
> all executables should have the `execute` bits set i.e. `chmod a+x foo-bar`; git tracks the executable bit, and sets it during checkout
* _shebang line_: how os knows how to run your program
* fmt: `#!/usr/bin/env INTERPRETER` e.g. `#!/usr/bin/env python`
> The program `/usr/bin/env` locates the environment using the `PATH` variable like any other command. This lets us control which interpreter gets chosen in a given environment by manipulating `PATH` e.g. using a python virtualenv instead of the system python.

NAMING
* scripts: lowercase + snakecase e.g. `foo`, `foo-bar`, `foo-bar-baz`
* no file extension bc reimpl = rename in every place of usage, update doc links
* everything but env var is lowercase https://stackoverflow.com/a/673940

OPTIONS 🔗 http://www.catb.org/~esr/writings/taoup/html/ch10s05.html
* _short option_: single dash prefix + single letter e.g. `-y`
* _option set_: n short options e.g. `-baz` = `-b`, `a`, `z`
* _long option_: double dash prefix + word e.g. `--foo-bar`
* options with a value are separated by their option by a space or an `=`
* `--`: ends option processing.

LOCATION
* `tools/PROJECT/YOUR-TOOL` for project related tools
* `bin/YOUR-TOOL` for things that are useful to have accessible at all times

## perms + user/group

🗄️ `containers.md`

PERMS 📙 Evans linux https://chatgpt.com/c/672cbc33-dabc-8004-bbac-7c5050f53879 🗄️ `tools.md` find
* categories: `u` (user/owner) `g` (group) `o` (other) `a` (all)
* mv: `chmod` + group + `r|w|x` e.g. `u=rw` (user gains rw) `+x` (all gain x) `o-w` (other loses w)
* get as octal: `stat -f "%A" $FILE`
* default: `666` (file) `777` (dir)
* _umask_: set perms on new files via "mask" (subtraction) from default perms; can be set as user or distro level https://www.digitalocean.com/community/tutorials/linux-permissions-basics-and-how-to-use-umask-on-a-vps

---

https://eradman.com/posts/unix-group-membership.html

PERMS
* read/write/execute have slightly different meanings when applied to directories 📙 Kerrisk lpi [2.5]
* macoS extended attributes https://serverfault.com/questions/151997/what-does-the-symbol-mean-in-a-files-permission-settings https://stackoverflow.com/questions/4833052/how-do-i-remove-the-extended-attributes-on-a-file-in-mac-os-x

USER/GROUPS 🔗 https://jvns.ca/blog/2017/11/20/groups/ https://terminaltrove.com/ugm
* logged-in users: `w`
* many programs create username and perform operations as that user
* macOS root user disabled by default but admin users can enable
* all logged in users: `who`
* switch user: `su <user>`; for root `su -`
* create user: `adduser` 
* give user sudo privilege: `visudo` (I think just opens `/etc/sudoers`)
* groups for user: `groups <user>` (or just `groups` for yourself)
* `wheel`: users who can `sudo` https://en.wikipedia.org/wiki/Wheel_(computing) 📘
* `/etc/group`: lists group name, pass, GID, users in group [LPI 26]
* _GID_: group id
* _UID_: user id; `root` is 0
