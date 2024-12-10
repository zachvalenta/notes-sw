# ⛩️

## 参考

🔍 https://www.youtube.com/@JacobSorber/playlists
📚 https://fabiensanglard.net/c/index.php
* algos https://www.amazon.com/gp/product/1718503229
* https://www.manning.com/books/modern-c-third-edition
* Kernighan https://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628
* Matthews dive https://diveintosystems.org/
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming

## 进步

* start here https://realpython.com/c-for-python-programmers/ https://chatgpt.com/c/673363d3-885c-8004-b7fe-083b927e6999
> Make builds output files from input files. It was originally designed for C programs, which utilize both code and header files which are built into object files. These object files are then compiled to binary. This is a multi-step build that requires some orchestration. That’s what Make is all about. 📙 Conery [406]

---

* modules https://chatgpt.com/c/67336227-2d40-8004-8789-e8fc768f60a5 📙 Jeffrey [3]
* courses http://www.buildyourownlisp.com https://gribblelab.org/teaching/CBootCamp/ https://www.enlightenment.org/docs/c/start
* design: https://saagarjha.com/blog/2020/05/10/why-we-at-famous-company-switched-to-hyped-technology/ https://eev.ee/blog/2016/12/01/lets-stop-copying-c/ https://nullprogram.com/tags/c/
* sysroot, undefined behavior (UB) https://news.ycombinator.com/item?id=30488979
* _gdb_: debugger https://www.gnu.org/software/gdb/ https://github.com/cs01/gdbgui can be used on more than C https://golang.org/doc/gdb influential in debugger design https://www.npmjs.com/package/trepanjs https://rubygems.org/gems/trepanning https://github.com/snare/voltron https://news.ycombinator.com/item?id=42146338 https://begriffs.com/posts/2022-07-17-debugging-gdb-ddd.html
* Postgres codebase is supposed to be a good guide https://news.ycombinator.com/item?id=20556336
* `#define`: constants https://www.youtube.com/watch?v=hsmGp3cp_50 0:50

PROJECTS
* Python extension https://realpython.com/build-python-c-extension-module/
* BYO db https://cstack.github.io/db_tutorial/
* cmus https://github.com/cmus
* BYO virtual machine https://justinmeiners.github.io/lc3-vm/
* BYO text editor https://viewsourcecode.org/snaptoken/kilo/01.setup.html https://github.com/codecrafters-io/build-your-own-x#build-your-own-text-editor

# 📝 LANG

## design

> C has a tendency to be conservative, changing and growing very slowly. https://nullprogram.com/blog/2018/11/21/
> The C language is old and boring. It is a well-known and well-understood language. https://sqlite.org/whyc.html
> When programming in C you do not stand on a path, but a plane of decision, and C dares you to decide what to do. http://www.buildyourownlisp.com/chapter1_introduction
* portable
> Libraries written in C are callable from any programming language. https://sqlite.org/whyc.html
> The Linux kernel is written in C. The software that connects your printer to your computer could be in C. The Web servers that serve up your Web pages are often written in C. It’s also a good language for writing other languages - Python, PHP, and Perl are written in C, as are many others. C is a language you use for building systems; it has the same role in computing that Latin did among Renaissance academics. - Ford what is code?
* example code: Redis, SQlite https://news.ycombinator.com/item?id=30753428
* https://drewdevault.com/2017/03/15/How-I-learned-to-stop-worrying-and-love-C.html
* https://drewdevault.com/2017/01/30/Lessons-to-learn-from-C.html

## stdlib

* _libc_: POSIX spec for os stdlib; used by higher-levels languages for everything from networking to memory management https://wizardzines.com/comics/libc/ https://drewdevault.com/2020/09/25/A-story-of-two-libcs.html
* _glibc_: most common impl of libc https://stackoverflow.com/a/11373143
* _musl_: used by Alpine https://www.musl-libc.org/ https://news.ycombinator.com/item?id=23819500 https://www.etalabs.net/compare_libcs.html cleaner? https://drewdevault.com/2020/09/25/A-story-of-two-libcs.html
# 🦑 RELATIVES

## 🧱 assembly

🔗 https://github.com/hackclub/some-assembly-required
📚
* Petzold code 24
* Nisan nand2tetris 4, 6

* _assembly_: shorthand for whatever binary the CPU understands 📙 `evans-linux.pdf` 1
* _HLA (high-level assembly)_: just a Randall Hyde thing https://news.ycombinator.com/item?id=7143409
* _intrinsics_: function that corresponds to paricular assembly instructions https://danluu.com/assembly-intrinsics/

---

* https://shikaan.github.io/assembly/x86/guide/2024/09/08/x86-64-introduction-hello.html
* ARM https://www.youtube.com/watch?v=gfmRrPjnEw4
* compiler explorer https://godbolt.org/
* _learning_: 📍 finish second chapter of Manga Microprocessors 🗄 Duntemann https://news.ycombinator.com/item?id=7143585 Latacora CTF https://news.ycombinator.com/item?id=7145479 🗄 Bryant https://news.ycombinator.com/item?id=7143866 microcontrollers https://news.ycombinator.com/item?id=7147009
https://wizardzines.com/comics/assembly/
* most assembly scoped to particular machine architecture; assembly used to be what OS were written in until Unix [LPI 1.1]
* macOS https://news.ycombinator.com/item?id=7144020
* https://news.ycombinator.com/item?id=26311722

## ➕ C++

* https://news.ycombinator.com/item?id=42231489
* https://ccc.codes/
* https://github.com/green7ea/cpp-compilation
* http://esr.ibiblio.org/?p=7724
* people hate C++ https://news.ycombinator.com/item?id=33436268
* https://borretti.me/article/simplicity-and-survival
* https://news.ycombinator.com/item?id=34588340
* https://news.ycombinator.com/item?id=34643530

## ⚡️ Zig

https://ziglang.org/

USE FOR BUILDS
* https://jakstys.lt/2022/how-uber-uses-zig/
* https://mitchellh.com/writing/zig-comptime-tagged-union-subset
* https://goreleaser.com/ https://goreleaser.com/customization/rust-builds/ https://goreleaser.com/customization/zig-builds/

PROJECTS
* https://github.com/Arnau478/hevi

* https://www.youtube.com/watch?v=ug-KuDlMTYw
* compared to Rust https://www.youtube.com/watch?v=Vxq6Qc-uAmE
* overview https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202203010 https://kristoff.it/blog/maintain-it-with-zig/
* tutorial https://gist.github.com/ityonemo/769532c2017ed9143f3571e5ac104e50
* BYO ls https://stackoverflow.com/questions/13554150/implementing-the-ls-al-command-in-c
* getting popular https://macwright.com/2020/08/01/recently.html
* https://news.ycombinator.com/item?id=29702607
* seems way easier than Rust https://scattered-thoughts.net/writing/assorted-thoughts-on-zig-and-rust/ https://kevinlynagh.com/rust-zig/
* smart users https://github.com/jamii
* current state of affairs https://news.ycombinator.com/item?id=36149462
* as a teaching language https://news.ycombinator.com/item?id=32752383

# 🦀 RUST

🗄️ `python/runtime.md` CPython > PyO3
📚
> start with Rustlings course https://bitfieldconsulting.com/posts/rust-and-go https://github.com/rust-lang/rustlings https://bitfieldconsulting.com/books/rust-tools
* https://bitfieldconsulting.com/books/rust-tools
* https://bitfieldconsulting.com/posts/best-rust-books
* https://www.manning.com/books/rust-servers-services-and-apps
* internals https://www.amazon.com/dp/B0D7FQB3DH

CODEBASES TO LEARN FROM
* plugin interface https://github.com/triyanox/lla
* tests with the source code https://github.com/b1rger/carl
* https://github.com/lusingander/serie
* not so hard to read after all https://github.com/raphlinus/font-rs/blob/master/src/accumulate.rs

PROJECT STRUCTURE
* basic TUI https://github.com/lusingander/btox
* src https://github.com/raphlinus/font-rs https://github.com/dotenvx/dotenvx
* lib/$PROJ_NAME https://github.com/nickgerace/gfold https://nickgerace.dev/posts/how-i-read-the-rust-programming-language/
* https://github.com/b1rger/carl

STDLIB
* cq/LSP https://github.com/rust-lang/rust-clippy https://github.com/Canop/bacon
* render Markdown in terminal https://github.com/Canop/termimad
* _db_: https://github.com/launchbadge/sqlx
* _GUI_ https://raphlinus.github.io/rust/gui/2022/07/15/next-dozen-guis.html
* _TUI_: https://github.com/ratatui-org/ratatui https://github.com/mrjackwills/oxker cursive https://github.com/gyscos/cursive https://github.com/Builditluc/wiki-tui https://github.com/fdehau/tui-rs https://github.com/lusingander/stu
* _web_: https://news.ycombinator.com/item?id=41914544 https://www.leptos.dev/ https://dioxuslabs.com/ https://loco.rs/
* _tauri_: crossplatform (mobile, desktop, web) https://github.com/tauri-apps/tauri https://blog.gitbutler.com/open-source-pledge-2024/ https://github.com/mrjackwills/obliqoro

COMMUNITY
* good graphic design taste https://rustlab.it/

---

https://gopodcast.dev/episodes/046-lets-talk-about-rust-with-john-arundel
community https://nickgerace.dev/posts/announcing-gfold3/
https://simonwillison.net/tags/rust/
https://chrisdone.com/posts/rust/
https://drewdevault.com/2024/08/30/2024-08-30-Rust-in-Linux-revisited.html
https://drewdevault.com/2022/10/03/Does-Rust-belong-in-Linux.html
https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html
https://rftgu.rs/ https://www.youtube.com/playlist?list=PLhoH5vyxr6Qqn3E9tm5bwUCQrkDzAIhav https://google.github.io/comprehensive-rust/ https://www.youtube.com/@codetothemoon https://roadmap.sh/rust https://www.ntietz.com/projects/
* incomplete bc no BDFL https://news.ycombinator.com/item?id=41656463 https://doc.rust-lang.org/unstable-book/the-unstable-book.html
> Maybe this is by design. Good languages are stable languages. It might be time to think of rust as a fully baked language - warts and all. Python 2.7 for life. https://josephg.com/blog/rewriting-rust/
* release, editions https://blog.rust-lang.org/2014/10/30/Stability.html https://doc.rust-lang.org/edition-guide/editions/
* Neovim https://www.youtube.com/watch?v=mh_EJhH49Ms
* example project https://github.com/nate-sys/tuime https://github.com/swsnr/mdcat
* books https://news.ycombinator.com/item?id=34556318 https://github.com/plabayo/learn-rust-101/blob/main/README.md
* CLI https://www.amazon.com/gp/product/1098109430/ref=ox_sc_act_title_1?smid=ATVPDKIKX0DER&psc=1
* web https://tech.marksblogg.com/poem-rust-web-framework.html https://tech.marksblogg.com/actix-rust-web-framework.html https://tech.marksblogg.com/rocket-rust-web-framework.html https://www.shuttle.rs/blog/2023/09/27/rust-vs-go-comparison
* vs. Golang https://news.ycombinator.com/item?id=31205072
* used for: CPU intensive, not API https://news.ycombinator.com/item?id=25798008
* governance problems https://news.ycombinator.com/item?id=28513130
* what people love: packaging, DX https://stackoverflow.blog/2020/06/05/why-the-developers-who-use-rust-love-it-so-much parallelization https://news.ycombinator.com/item?id=26443768 CLI (jless) https://news.ycombinator.com/item?id=30273940 correctness
* lifetimes, safety profiles in C++ https://en.wikipedia.org/wiki/Erlang_(programming_language) https://news.ycombinator.com/item?id=42302673

## borrow checker

🗄️ `plt.md` memory

https://bitfieldconsulting.com/posts/rust-and-go

> Rust is a language for controlling elevators...we can't prevent all bugs, but we can at least use a programming language that eliminates some major categories of bugs, such as buffer overflows, data races, and "use after free" issues. So from the very beginning, Rust's focus has been on building reliable software, automating many of the safety checks that good programmers do anyway, and helping to catch mistakes before they reach production.
> It reclaims memory automatically, but without having to pause the program. It can do this by keeping track of all the references to a particular piece of data that exist. When no part of the program can refer to the data any more, Rust knows that bit of memory can be safely recycled straight away.
> Well, I have good news - if you’re already used to pointers in Go, then references in Rust work basically the same way, only safer. If you create a mutable reference to a variable, it works just like a Go pointer: you can pass it to a function, or store it somewhere.
> But, unlike in Go, as long as that mutable reference exists, it has exclusive access to the data: no one else can modify it, or even read it. In Go terms, it’s like having an automatic mutex lock. And when a function doesn’t need to modify the data, it can instead borrow a shared reference, which is read-only, and lots of them can exist at once.
> Rust also keeps track of the original data: when it goes out of scope, any references to it are no longer valid. So the compiler can detect many kinds of dangling pointer bugs where you try to use a reference to a value that doesn’t exist any more. That results in undefined behaviour, which is a nice way of saying that something horrible will happen, and part of Rust’s value proposition is “no undefined behaviour—ever”.
> In Rust, then, we have to figure out a way to write our programs so that references to data are always valid, and only one mutable reference ever exists at a time. That takes some getting used to (Rust programmers call it “fighting the borrow checker”), but the resulting programs are more reliable, and more likely to be correct.
> For example, all Go programmers are familiar with data races, where two or more goroutines try to access some shared data at the same time, with unpredictable results: at best, the program will crash, and at worst, it will continue with corrupted or invalid data.
> In Rust, a program like this won’t compile! The ownership and reference rules mean that two mutable references to the same thing can’t exist simultaneously. You just have to solve the problem a different way.

## Cargo

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup self uninstall

cargo build
cargo run
cargo test
cargo doc
cargo publish
```

PACKAGING / VERSION MGMT 🧠 https://chatgpt.com/c/673544c8-978c-8004-bc38-c7c4d2efdba1 📙 https://doc.rust-lang.org/cargo/index.html
> Cargo makes no distinction between managing dependencies for CLI tools and libraries. Every Rust project can be both a CLI and a library without extra configuration.
* no REPL!?! `evcxr_repl` as alternative
* local install: `$PROJ/.cargo`
* global install: `~/.cargo/bin`
* `rust-toolchain.toml`: spec version for project
* `Cargo.toml`: deps + metadata
```sh
# DUMP
cargo install --list | rg -o "^\S*\S" > crates.txt
xargs cargo install --locked < crates.txt # install from dump

# UPDATE https://nickgerace.dev/posts/how-to-manage-rust-tools-and-applications/
cargo install --locked cargo-update
cargo install-update -a
```
* `--locked`: use lock file i.e. reproducible but no updates
> have my experience using the tool or application to match that of the upstream developer's experience...using the dependencies they tested with https://nickgerace.dev/posts/how-to-manage-rust-tools-and-applications/
* _crate_: pkg
* _rustup_: version mgmt

---

https://github.com/lusingander/cargo-selector

## design

* rewrite: Django templates https://github.com/LilyFoote/django-rusty-templates
* building postgres extensions https://github.com/pgcentralfoundation/pgrx
> Go is perfectly suited for plain, ordinary, everyday software: command-line tools, business processes, database applications, web services. It’s fairly easy to write Go programs; they build fast, and they run very fast. For probably 80% of the software we write, Go gets the job done just fine. Rust, on the other hand, neatly fills the gaps where Go isn’t an ideal choice: kernels, firmware, embedded devices, real-time systems. It gives you all the keys to the hardware, and to ultimate performance. Its relentless focus on memory safety and program correctness make Rust the obvious choice for safety-critical applications: industrial, medical, aerospace. https://bitfieldconsulting.com/posts/rust-and-go

---

* too complicated, learn Golang instead https://registerspill.thorstenball.com/p/glad-i-did-it-in-go https://registerspill.thorstenball.com/p/rust-prism
> This blog post, Rewriting Rust, was very interesting. “I swear, it took more effort to learn pinning in rust than it took me to learn the entire Go programming language.” Some day (in the far future) I might write more about my feelings on Rust, but while reading this post I kept waiting for the paragraph in which they say what they would remove from the language. That paragraph never came and I think that’s one of the biggest sources of friction between me and Rust. https://registerspill.thorstenball.com/p/joy-and-curiosity-9
* using in other languages https://news.ycombinator.com/item?id=41941451
* for the big kids https://www.lambdafunctions.com/articles/racing-sed-with-rust https://github.com/rayon-rs/rayon
* error handling https://bitfieldconsulting.com/posts/rust-errors-option-result

* doesn't have a spec https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html
* big learning curve https://news.ycombinator.com/item?id=30627667
> Despite my infamous distaste for Rust, long-time readers will know that where I have distaste for Rust, I have passionate scorn for C++. I’m quite glad to see Rust taking it on, and I hope very much that it succeeds in this respect. https://drewdevault.com/2021/02/21/On-the-traits-of-good-replacements.html
* syntax https://lucumr.pocoo.org/2015/5/27/rust-for-pythonistas/ https://fasterthanli.me/blog/2020/a-half-hour-to-learn-rust/

# 🟨 ZA

HISTORY https://news.ycombinator.com/item?id=24361469
* rose to prominence in the 1980s, now used for firmware and kernels but new stuff now in other languages http://esr.ibiblio.org/?p=7711
* _c89_: aka ANSI C https://fabiensanglard.net/c/index.php
* _c99_: not supported everywhere https://fabiensanglard.net/c/index.php
* _c11_: ? https://drewdevault.com/2020/11/01/What-is-Gemini-anyway.html
* _c23_:
* _1972_: created https://www.bell-labs.com/usr/dmr/www/chist.html
* _1978_: K&R spec

## internals

---

* _undefined behavior_: when an error happens but it's not thrown i.e. `TypeError` in Python might be mean the compiler just chugging along in C https://blog.regehr.org/archives/213 https://news.ycombinator.com/item?id=24363573
> Rust also keeps track of the original data: when it goes out of scope, any references to it are no longer valid. So the compiler can detect many kinds of dangling pointer bugs where you try to use a reference to a value that doesn’t exist any more. That results in undefined behaviour, which is a nice way of saying that something horrible will happen, and part of Rust’s value proposition is “no undefined behaviour—ever”. https://bitfieldconsulting.com/posts/rust-and-go

* call Python from C http://eradman.com/posts/extending-c-python.html
* _ABI_: https://en.wikipedia.org/wiki/Application_binary_interface https://news.ycombinator.com/item?id=24140848 https://gankra.github.io/blah/c-isnt-a-language/ https://hpyproject.org/ https://news.ycombinator.com/item?id=41992899
* _abstract machine_: C's version of a virtual machine https://words.steveklabnik.com/should-you-learn-c-to-learn-how-the-computer-works
* _bitfield_: https://danluu.com/algorithms-interviews/
* _compilation_: https://jvns.ca/blog/2019/10/28/sqlite-is-really-easy-to-compile/
* _garbage collection_: (kinda) possible https://stackoverflow.com/a/5009966/6813490
