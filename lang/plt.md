# ⛩️

## 参考

🔗 https://en.wikipedia.org/wiki/Programming_language_theory
📚
* https://pragprog.com/titles/dzseven/seven-obscure-languages-in-seven-weeks/
* https://pragprog.com/titles/btlang/seven-languages-in-seven-weeks/
* https://pragprog.com/titles/7lang/seven-more-languages-in-seven-weeks/
* https://nostarch.com/strange-code

## 进步

* https://en.wikipedia.org/wiki/TempleOS
* BYO assembly https://zserge.com/posts/langs-asm/
* macros, AST https://news.ycombinator.com/item?id=42084603

* _22_: keeping track of Rust and Zig
* _19-present_: Python, SQL
* _18_: Python, Spring Boot, Django/DRM
* _17_: PHP, SQL
* _16_: JavaScript, Java

# 📚 LANGUAGES

FACTORS
* people like it: Ruby, Python, Rust, JS
* build import things with it: + Golang, Java, C++

* _Algol_: inspired Bash https://news.ycombinator.com/item?id=42020368 https://www.youtube.com/watch?v=olH-9b3VJfs https://shellhaters.org/talk
* _APL_: https://mathspp.com/blog/what-learning-apl-taught-me-about-python https://zserge.com/posts/langs-apl/
* _Basic_: https://zserge.com/posts/langs-basic/
* _C#_: .NET big in game dev https://news.ycombinator.com/item?id=41936001
* with Alpine https://news.ycombinator.com/item?id=34365515
* _Julia_: theoretically great (e.g. can inspect assembly) but practically immature and academic https://increment.com/programming-languages/goldilocks-language-history-of-julia/ https://www.evanmiller.org/why-im-betting-on-julia.html https://danluu.com/julialang/ https://viralinstruction.com/posts/badjulia/ https://www.manning.com/books/julia-as-a-second-language
* _Nim_: https://nim-lang.org/ https://github.com/Pebaz/nimporter small stdlib = Python will get fast before Nim gets big https://news.ycombinator.com/item?id=36958900 https://www.openmymind.net/Interfaces-In-Nim/
* _Pascal_: https://news.ycombinator.com/item?id=34939231 https://en.wikipedia.org/wiki/Pascal_(programming_language)
* _Perl_: https://buttondown.com/hillelwayne/archive/raku-a-language-for-gremlins/ https://buttondown.com/hillelwayne/archive/five-unusual-raku-features/ https://raku.org/ https://news.ycombinator.com/item?id=42307223
* _PHP_: Laravel great for solo devs and big in Europe https://news.ycombinator.com/item?id=30259097 https://stitcher.io/blog/php-in-2019 https://news.ycombinator.com/item?id=34411018
* _Prolog_: https://chatgpt.com/c/672d18fc-66cc-8004-94ba-23928fa2110c https://www.swi-prolog.org/ https://rogersm.net/posts/developing-a-go-bot-embedding-ichiban-prolog/ https://news.ycombinator.com/item?id=42004756 https://blog.dnmfarrell.com/ http://minikanren.org/
* _Ruby_:
> Somewhere, someone (bless them) linked to mousehole, a why the lucky stiff project. When I started programming in Ruby, _why was already gone and I only learned about him through the Slate article, but echos of him are still ringing through the Ruby world. This project is a sweet reminder. Just look at that README. “MouseHole can either intrude completely upon your browsing experience or you can keep it off in the outskirts, for whenever you’ve got a second to duck into that little crack in the wall” https://registerspill.thorstenball.com/p/joy-and-curiosity-16

## history

https://increment.com/programming-languages/language-history/

* _1957_: Fortran (IBM); still the best for math https://news.ycombinator.com/item?id=14498904 Python better? https://cerfacs.fr/coop/fortran-vs-python role in Python https://labs.quansight.org/blog/building-scipy-with-flang
* _1958_: Lisp (MIT)
* _1959_: Cobol; process transactions https://news.ycombinator.com/item?id=42513022
* _1963_: BASIC https://en.wikipedia.org/wiki/BASIC https://en.wikipedia.org/wiki/Pick_operating_system
* _1972_: C (Bell Labs) Smalltalk (Xerox Parc) 
* _1985_: C++ (Bell Labs)
* _1990_: Python
* _1993_: Lua
* _1995_: Java (Sun) JS (Netscape) Ruby (Matz) https://twobithistory.org/2017/11/19/the-ruby-story.html
* _1996_: OCaml
* _2015_: Rust
* _2016_: Zig
* _2020s_: Gleam, Odin https://odin-lang.org/ https://rm4n0s.github.io/posts/2-go-devs-should-learn-odin/ https://www.youtube.com/watch?v=0JeD48Ay8Ts Hazel https://hazel.org/ https://www.youtube.com/@codetothemoon/videos https://www.fast.ai/posts/2023-05-03-mojo-launch.html Lobster https://github.com/aardappel/lobster https://www.youtube.com/watch?v=uuPeBKdnBOI BYO https://www.scattered-thoughts.net/

## community

> But the choice of a main programming language is the most important signaling behavior that a technology company can engage in. Tell me that you program in Java, and I believe you to be either serious or boring. In Ruby, and you are interested in building things quickly. In Clojure, and I think you are smart but wonder if you ship. In Python, and I trust you implicitly. In PHP, and we sigh together. In C++ or C, and I nod humbly. In C#, and I smile and assume we have nothing in common. In Fortran, and I ask to see your security clearance. These languages contain entire civilizations. - Ford what is code?
* Java developers have high pain tolerances https://news.ycombinator.com/item?id=25124513
> The wrong people like it. The programmers I admire most are not, on the whole, captivated by Java. http://www.paulgraham.com/javacover.html
> Language users do not miss conveniences that they have never had access to in the first place. Those few bi-cultural citizens who function in both Chinese-character and alphabetic worlds are aware of the advantages conferred by the alphabet, but even these people soon get used to the differences, which slip below the level of consciousness, unremarked and unlamented...in virtually every informatic context, from library card catalogs to everyday user's manuals, the relatively cumbersome Chinese writing system exerts a low-level but constant drag force on productivity 📝 Moser invisible writing

## spec

https://drewdevault.com/2021/12/30/Language-design-considerations.html
https://www.paulgraham.com/arc.html
https://drewdevault.com/2021/08/11/Debugging-your-new-PL.html

## stdlib

---

> I wish there was a good place to learn “the other parts” of C++, the build systems, using static analyzers, testing, dependency management, etc. https://news.ycombinator.com/item?id=34229802
> an algorithm management system 📰 Ford what is code?
* builtin: hot reload, lint, fmt, http https://www.youtube.com/watch?v=8IHhvkaVqVE
* things people don't like and replacements https://news.ycombinator.com/item?id=25125034
* Fred Brooks very wrong about dev tooling https://twitter.com/danluu/status/1343898148863762435 https://varnish-cache.org/docs/6.2/phk/thatslow.html https://www.newyorker.com/magazine/2018/11/12/why-doctors-hate-their-computers https://www.hillelwayne.com/post/learning-a-language/ https://news.ycombinator.com/item?id=24123372 🗄️ Brooks Law
> We can see that Brooks' 1986 claim that we've basically captured all the productivity gains high-level languages can provide isn't too different from an assembly language programmer saying the same thing in 1955, thinking that assembly is as good as any language can be. https://danluu.com/essential-complexity/#summary

* stdlib https://borretti.me/article/languages-not-ecosystems
> Ruby missed the boat because Matz thinks developer happiness is purely about the language and they missed that it’s more and more about the tooling. https://registerspill.thorstenball.com/p/joy-and-curiosity-10
> 99.5% of programming consists of gluing together calls to library functions. All popular languages are equally good at this. So one can easily spend one's whole career operating in the intersection of popular programming languages. http://paulgraham.com/weird.html
> The true measure of a language isn’t how it uses semicolons; it’s the standard library of each language. - Ford what is code?
> I think a lot of the advances that happen in programming languages in the next fifty years will have to do with library functions. I think future programming languages will have libraries that are as carefully designed as the core language. Programming language design will not be about whether to make your language strongly or weakly typed, or object oriented, or functional, or whatever, but about how to design great libraries. The kind of language designers who like to think about how to design type systems may shudder at this. It's almost like writing applications! Too bad. Languages are for programmers, and libraries are what programmers need. - http://paulgraham.com/popular.html
> The open source JS ecosystem, though, has soooooo many folks working on it that you can almost always find something you need. Certainly compared to something like Java, which has a couple "800 pound gorilla" projects, but then it falls off pretty quickly. https://news.ycombinator.com/item?id=31996232

## systems programming

* https://news.ycombinator.com/item?id=42406893
* languages: C, C++, Rust
* Golang for containers https://github.com/sablierapp/sablier
* things people write with: dbms, web server, compiler, shell https://drewdevault.com/2021/05/30/Come-build-your-project.html
* fuzzy definition http://willcrichton.net/notes/systems-programming/ https://news.ycombinator.com/item?id=35092049
* memory management now in favor http://esr.ibiblio.org/?p=7804
* is easy :) https://news.ycombinator.com/item?id=34566918
* https://drewdevault.com/2021/03/19/A-new-systems-language.html

## 🇧🇷 Lua

USAGE
* scripting with Redis https://redis.io/docs/latest/develop/interact/programmability/eval-intro/ https://www.youtube.com/watch?v=7EK06n485nk [6:30]
* Neovim
* Hammerspoon
* extending C projects https://github.com/jmattaa/laser
* video games https://www.love2d.org/ https://www.youtube.com/watch?v=YntG_mSE0d3

ZA
* install: asdf for version mgmt, scared Homebrew will screw up Neovim install
> docs are bad https://www.lua.org/download.html

---

https://github.com/esbudylin/modest
https://news.ycombinator.com/item?id=42517102
https://www.lua.org/start.html 🔍 https://github.com/LewisJEllis/awesome-lua https://nvchad.com/docs/quickstart/learn-lua

* pkg mgmt https://luarocks.org/
* filepaths: use `.` separator, will handle forward/backslash on Linux, Windows https://www.youtube.com/watch?v=prnrwpOEsmo 9:45
* functions: can omit parens if passing string or table as a single arg https://www.youtube.com/watch?v=prnrwpOEsmo 10:15
* colons https://www.youtube.com/watch?v=prnrwpOEsmo 13:00
* syntax = Python + `end`
* small stdlib https://news.ycombinator.com/item?id=3535382
* libraries https://luarocks.org/
* for binaries https://news.ycombinator.com/item?id=10974870
* easy to embed https://news.ycombinator.com/item?id=3534746
* not backwards compatibile bc don't keep previous mistakes around https://news.ycombinator.com/item?id=3535382
* people like? https://news.ycombinator.com/item?id=40538540
* multiple compilers https://news.ycombinator.com/item?id=23686297

## 🔤 R

🗄️ `stat.md` Gelman

* preceded by SAS (data processing platform developed in the 1970s at North Carolina State and later commercialized)
* grammar of graphics https://github.com/Kanaries/graphic-walker
* vs. Prolog https://chatgpt.com/c/67336949-e2fc-8004-92cc-19f5e9e9f230
* language for stats https://walker-data.com/census-r/index.html https://gwern.net/resorter
* run inside Python
* _CRAN_: where you download R itself and also (?) R packages https://cran.r-project.org/
* _packrat_: pkg manager https://rstudio.github.io/packrat/
* _RStudio_: IDE
* _tidyverse_: https://www.tidyverse.org/index.html
* clean https://github.com/sfirke/janitor https://tidyr.tidyverse.org https://tidyr.tidyverse.org/articles/tidy-data.html
* functional https://purrr.tidyverse.org/
* string pattern match https://stringr.tidyverse.org/
* plot https://ggplot2.tidyverse.org/ https://calmcode.io/course/ggplot/introduction grammar of graphics https://plotnine.org/
* dataframes https://tibble.tidyverse.org/

## 💎 Ruby

📙 Perrotta metaprogramming ruby https://news.ycombinator.com/item?id=24935242

# 📥 MEMORY

---

🔍 https://softwareengineering.stackexchange.com/questions/tagged/memory
🗄
* `c.md` Rust > design
* `computation.md` memory
* `python/obj.md` memory

> port from `python.md`

memory management https://stackoverflow.com/a/3434252
* models https://news.ycombinator.com/item?id=42397737
* _leak_: run out of memory https://www.openmymind.net/Your-Buffer-Is-Leaking/
> What happens if you don't free memory? As your process uses more and more memory, it will eventually slow down, crash, or get killed silently. https://pythonspeed.com/articles/identifying-resource-leaks-with-pytest/
* _unmanaged code_: language w/ no memory management e.g. C, C++; sometimes used to mean "compiles directly to machine code" by people who do not understand that C has an abstract machine
* _managed code_: language w/ memory management (Java); dynamic languages not typically described as such, more of a marketing term for enterprise languages
* _garbage_: 
* _garbage collection_: scheduled memory management; yes (Python, Java) no (Rust 'borrow checker') no-unless-you-hack-real-hard (C, C++) https://news.ycombinator.com/item?id=41963259 https://danluu.com/butler-lampson-1999/ BYO https://jennyjams.net/blog/copygc/
* _memory leak_: https://www.glean.com/blog/how-we-analyzed-and-fixed-a-golang-memory-leak https://rtpg.co/2025/01/01/cowboy-coding-memory/
* reference counting, prefetching https://signalsandthreads.com/memory-management/)

interning
* _intern_: reuse i.e. only storing one version of obj
* prevent creation of obj with same value and type https://python-reference.readthedocs.io/en/latest/docs/functions/intern.html#remarks
* handled by compiler

## argument passing 

🗄 stack - in-place, out-of-place

https://mathspp.com/blog/pydonts/pass-by-value-reference-and-assignment
terms 🗄 pointers
* _pass by reference_: function operates on passed obj https://realpython.com/python-pass-by-reference/#defining-pass-by-reference
> seems to be used interchangeably w/ in-place https://realpython.com/python-pass-by-reference/#best-practice-use-dictionaries-and-lists
* _pass by value_: function operates on values of passed obj by copying to new obj https://www.interviewcake.com/question/python3/reverse-words https://neilalexander.dev/2021/08/29/go-pass-by-value.html
* _pass by assignment_: Python's approach; aka 'pass by object reference' https://realpython.com/python-pass-by-reference/#passing-arguments-in-python https://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/

pass by reference https://realpython.com/python-pass-by-reference/#using-pass-by-reference-constructs
* used to save memory when obj are large (data sci)
* used for counters
```c#
// C# allows actuall pass by reference
incrementer(ref int counter){
    counter++;
}
int counter = 0;
incrementer(ref counter);  // counter = 1
incrementer(ref counter);  // counter = 2
```
```python
# Python can give you interface of counter but not actually pass by reference i.e. still creates new obj https://realpython.com/python-pass-by-reference/#replicating-pass-by-reference-with-python
def incrementer(num):
    return num + 1

counter = 0
id(counter)  # 4304845280
counter = incrementer(counter)
id(counter)  # 4304845312
```

## pointers

🔗 https://en.wikipedia.org/wiki/Pointer_(computer_programming)

* a memory address https://nullprogram.com/blog/2019/06/30/
* _thin pointer_: takes up space of one unsigned int https://users.rust-lang.org/t/thin-pointers-fat-pointers-alignment-oh-my/50261
* _fat pointer_: takes up space of two unsigned ints, extra int stores length (e.g. Go slice) https://nullprogram.com/blog/2019/06/30/ https://stackoverflow.com/a/57754902

---

https://www.hytradboi.com/2025/05c72e39-c07e-41bc-ac40-85e8308f2917-programming-without-pointers
https://victoriametrics.com/blog/go-weak-pointer/
https://us.pycon.org/2024/schedule/presentation/80/index.html
https://pythonbytes.fm/episodes/show/375/pointing-at-countries

null https://www.youtube.com/watch?v=XIhQYRNBAYs

dereference https://stackoverflow.com/questions/4007268/what-exactly-is-meant-by-de-referencing-a-null-pointer https://stackoverflow.com/questions/14224831/meaning-of-referencing-and-dereferencing-in-c

obj storing a memory address https://nullprogram.com/blog/2019/06/30/ https://boredzo.org/pointers/#definition https://www.alexedwards.net/blog/a-gentle-introduction-to-pointers

pointer arithmetic https://nullprogram.com/blog/2019/06/30/

* https://golangweekly.com/link/147076/web
* https://www.youtube.com/watch?v=mqH21m0MsWk
* https://boredzo.org/pointers/ https://www.ralfj.de/blog/2020/12/14/provenance.html

* _pointer value_: value at memory address
* _reference_: synonym for memory address https://stackoverflow.com/a/36208432 or obj at mem address https://realpython.com/pointers-in-python/#names-in-python
* _dereference_: derive pointer value from pointer
* _reference_: derive pointer from pointer value
```go
// https://tour.golang.org/moretypes/1
hitchhiker := 42  // 42
p = &hitchhiker // 0x414020 - reference
*p // 42 -> dereference
```
* _strong reference_: https://docs.python.org/3/glossary.html#term-strong-reference
* references (weak, strong) https://www.fluentpython.com/extra/weak-references/ refcount, referent https://www.fluentpython.com/lingo/#weak_reference https://www.fluentpython.com/lingo/#refcount https://www.fluentpython.com/lingo/#referent
* used for saving memory https://stackoverflow.com/a/850850
* not even agreement on how difficult the topic is or, if it is difficult, why it's difficult (which probably means it is intrinsically difficult) https://stackoverflow.com/q/5727
* "FOO_LANGUAGE doesn't have pointers" = language doesn't expose memory allocation to end user? language doesn't intern? https://realpython.com/pointers-in-python/#understanding-variables
```python
# name: does intern
a = 13
b = a
a is b  # True
```
```c
// variable: doesn't intern i.e. value copied to new mem address
int x = 42;  // 0x7ffee4c114f8
int y = x;  // 0x7ffee4c114f4
```

## stacks

🗄️ `algos.md` recursion

* _stack frame_: instance of function execution
* vars, args, metadata (location in call stack, return address)
* _call stack_: all frames in state of execution 📙 Bhargava [42]
* aka traceback, stack trace https://realpython.com/python-debugging-pdb/#python-caller-id
* _stack overflow_: too many frames on stack and process runs out of memory https://developer.mozilla.org/en-US/docs/Glossary/Call_Stack

* _stack_: mem for stack frame var https://danielmiessler.com/study/difference-stack-heap-based-memory/
* auto deallocation on func completion
* faster to access than heap (at least in Java) https://www.baeldung.com/java-stack-heap https://blog.robertelder.org/computer-science-for-engineers/
* _heap_: memory used for manual de/allocation https://danielmiessler.com/study/difference-stack-heap-based-memory/
* _garbage collection_: deallocate mem in heap 📙 Conery [216]

PLACE 🗄 `algos.md` complexity
* _out-of-place_: mutates copy of data https://www.interviewcake.com/concept/python3/in-place
* _in-place_: mutates original data https://en.wikipedia.org/wiki/In-place_algorithm
* i.e. doesn't create additional obj for purpose of data manipulation, does it within stack frame
* generally a bad idea https://twitter.com/raymondh/status/1055478808793546752 https://stackoverflow.com/a/1637838 https://www.interviewcake.com/concept/python3/in-place
* aka 'destuctive'
* funny example from unit tests that requires you to swap elements https://www.interviewcake.com/question/python3/reverse-string-in-place

---

https://pythontutor.com/
call graph https://github.com/chanhx/crabviz

* ❓ relationship to space complexity https://www.interviewcake.com/concept/python3/in-place https://en.wikipedia.org/wiki/In-place_algorithm#Examples
```python
def in_place(qd):
    for ind, el in enumerate(qd):  # just mutates original
        qd[ind] *= el

def out_of_place(qd):
    new_qd = list()  # creates new obj for mutation
    for ind, el in enumerate(qd):
        new_qd[ind] *= el
```

# ⭕️ SEMANTICS

---

📜 https://docs.python.org/3/reference/index.html

NAMES
* _identifier_: user defined name; aka 'symbol' https://en.wikipedia.org/wiki/Symbol_table#Example
* _keyword_: reserved and in use; getting shorter https://news.ycombinator.com/item?id=22474850 https://danluu.com/cli-complexity/
* soft keywords https://mathspp.com/blog/til/pythons-soft-keywords
* _reserved_: not in use

VARIABLES
* _declare_: put var into namespace
* _initialize_: give var initial value
* _assign_: give var subsequent values; `TypeError: 'tuple' object does not support item assignment` supports the definition I've gleaned

ARITHMATIC
* _increment_: `++`
* _infix_: multiplication `*` exponentiation `**` https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/ 🗄 `python.md`
* += https://stackoverflow.com/a/7456548

## operators

* _assignment_: `=`
* _equality_: `==`|`!=`; SQL uses `=`
* _identity_: `is`
* _comparison_: `<`|`>`

---

📙 Nisan nand2tetris ch. 1-2 https://buttondown.com/hillelwayne/archive/a-list-of-ternary-operators/
* _operand_: value used by operator
* _operator_: perform action
* _conditional/ternary_: ?
* _logical/boolean_: and, or, not
* _membership_: in

## units

---

* _expression_: value + operator https://realpython.com/python-walrus-operator/#hello-walrus
* an eval to single value e.g. `y + 13` (number) `price > 0` (bool) 📙 Sweigart automate [14]
* _statement_: 动 an action e.g. function call (`logger.debug(ex)`) assignment (`x = 42`) https://beautifulracket.com/appendix/why-racket-why-lisp.html
* compositions of n expressions 📙 Haverbeke [ch.2]
* _block_: 名 group of statements

# 🔡 TYPING

🗄 `python/core.md` typing, metaprogramming
📙 Friedman little typer https://www.amazon.com/Little-Typer-MIT-Press/dp/0262536439
🔗 https://en.wikipedia.org/wiki/Type_system

## debate

PRO https://www.youtube.com/watch?v=YR5WdGrpoug https://news.ycombinator.com/item?id=42004756
> [invariant violation] At point A, there's some assumption, and way over there at point B, that assumption is violated... Type systems prevent some invariant violations. Because that works, there are ongoing attempts to extend type systems to prevent still more invariant violations. That creates another layer of confusing abstraction. Some invariants are not well represented as types, and trying makes for a bad fit. What you're really trying to do is to substitute manual specification of attributes for global analysis. The Rust borrow checker is an invariant enforcer. It explicitly does automatic global analysis, and reports explicitly that what's going on at point B is inconsistent with what point A needs. This is real progress in programming language design, and is Rust's main contribution. https://news.ycombinator.com/item?id=29996240
> Type checking catches bugs that unit testing does not, often much faster and with less code overhead than unit testing requires. It has surprised me how much of my unit tests were de facto implementing a type system halfheartedly as opposed to testing behavior of those types. - https://threadreaderapp.com/thread/1141836825838800896.html more on typing as a analog to unit tests https://www.jorgemanrubia.com/2019/06/22/on-ruby-and-type-checkers/
> Having used Kotlin on and off for the better part of a decade, the one thing I can say is that their editor support is unrivaled by any other language today. https://news.ycombinator.com/item?id=33331123

CON https://steveklabnik.com/writing/ten-years-of-ru---ewriting-my-website/ https://bryananthonio.com/blog/pydantic-custom-dictionary-types/
> Every dynamically-typed programming language attempts to expand until it has static types and compiles to machine code. https://news.ycombinator.com/item?id=24839697
> Types add value and they add cost https://lucumr.pocoo.org/2023/12/1/the-python-that-was/
> Research has shown that Franklin's remark about giving up liberty to purchase safety is actually about type systems. https://twitter.com/MarijnJH/status/570833749065265152
> And Haskell, OCaml and their ilk are part of a 45-year-old static-typing movement within academia to try to force people to model everything. Programmers hate that. These languages will never, ever enjoy any substantial commercial success, for the exact same reason the Semantic Web is a failure. You can't force people to provide metadata for everything they do. They'll hate you. The type system is 'wrong' whenever it cannot match the intended computational model. Every time want to use multiple inheritance or mixins in Java's type system, Java is 'wrong', because it can't do what you want. You have to take the most natural design and corrupt it to fit Java's view of the world. I think the general answer to this is: when in doubt, don't model it. Just get the code written, make forward progress. Don't let yourself get bogged down with the details of modeling a helper class that you're creating for documentation purposes. http://steve-yegge.blogspot.com/2008/02/portrait-of-n00b.html
> When in doubt, don't model it. Just get the code written, make forward progress. Don't let yourself get bogged down with the details of modeling a helper class that you're creating for documentation purposes. http://steve-yegge.blogspot.com/2008/02/portrait-of-n00b.html
> You probably know my skepticism towards Python typing...we are creating the new Java. We became the people we originally displaced. Just that when we are not careful we are on a path to the world's worst Java. We put typing on a language that does not support it, our interpreter is slow, it has a GIL. We need to be careful not to forget that our roots are somewhere else. We should not collectively throw away the benefits we had. https://lucumr.pocoo.org/2023/12/1/the-python-that-was/
> I'm worried that a de-facto move away from dynamic stuff in the Python ecosystem, possibly motivated by those who use Python only because they have to, and just want to make it more like the C# or Java they are comfortable with, could leave us with the very worst of all worlds. https://news.ycombinator.com/item?id=34615749
* a programming language is for sketching https://simonwillison.net/2024/Dec/15/preferring-throwaway-code-over-design-docs/ https://daniel.haxx.se/blog/2025/02/18/changing-every-line-three-times/
> A programming language is for thinking of programs, not for expressing programs you've already thought of. It should be a pencil, not a pen. 📙 Graham hackers painters [22]
> Have you ever noticed that when you sit down to write something, half the ideas that end up in it are ones you thought of while writing? The same thing happens with software. Working to implement one idea gives you more ideas. 📙 Graham hackers painters [68]

## generics

* https://www.dolthub.com/blog/2024-11-22-are-golang-generics-simple-or-incomplete-1/
* _generics_: prevent type errors in Collections (bc Collections can contain any obj type e.g. str, int, et al.)
* e.g. reverse array of any type
* in Python https://stackoverflow.com/questions/6725868/generics-templates-in-python https://mypy.readthedocs.io/en/stable/generics.html https://www.youtube.com/watch?v=LcfxUU1A-RQ
* https://news.ycombinator.com/item?id=29705134
* https://news.ycombinator.com/item?id=29702607
* https://drewdevault.com/2019/02/18/Generics-arent-ready-for-Go.html
* https://go.dev/blog/why-generics https://go.dev/blog/generics-next-step

## terminology

* _nominative typing_: obj type explicitly declared https://en.wikipedia.org/wiki/Nominal_type_system
* _duck typing_: obj is type if it has properties/methods of that type (vs. nominative) https://docs.python.org/3/glossary.html#term-duck-typing https://realpython.com/podcasts/rpp/196/
* _type inference_: figure out type based on context https://calpaterson.com/mypy-hints.html
> aka implicit? https://go.dev/tour/basics/10
* _reflection_: program's ability to examine type system of programming language + dynamically manipulate types/values at runtime https://drewdevault.com/2021/10/05/Reflection.html https://en.wikipedia.org/wiki/Reflective_programming
> Clojure provides easy access to the Java frameworks, with optional type hints and type inference, to ensure that calls to Java can avoid reflection. https://clojure.org/

---

https://danluu.com/butler-lampson-1999/

SEMANTICS https://www.destroyallsoftware.com/compendium/types?share_key=baf6b67369843fa2
* dynamic https://gist.github.com/non/ec48b0a7343db8291b92
* gradual typing: type hints/annotations in code checked by static analysis tooling, not compiler
* inference https://news.ycombinator.com/item?id=36775644 OCaml https://borretti.me/article/type-inference-was-a-mistake
> I don’t want to infer types from my code. I’d rather infer the code from the types. Types are the spec, they are small and low in expressiveness, code is big and has infinitely more degrees of freedom than types. The bug surface area is smaller with types. https://borretti.me/article/type-inference-was-a-mistake
* implicit https://news.ycombinator.com/item?id=26671136 https://go.dev/tour/basics/10
* _definitions_: strong/weak less rigorously defined than static/dynamic [Smallshire 1 @ 5.4]
* _sink_: https://danluu.com/empirical-pl/ https://www.cs.uaf.edu/users/chappell/public_html/class/2018_spr/cs331/docs/types_primer.html https://eli.thegreenplace.net/2006/11/25/a-taxonomy-of-typing-systems vocab https://cdsmith.wordpress.com/2011/01/09/an-old-article-i-wrote/ https://danluu.com/empirical-pl/ https://danluu.com/empirical-pl/
|   	    | static   	| dynamic   	    |
|---	    |---	    |---	            |
| strong   	| C++      	| Python, Ruby   	|
| weak  	|   	    | JS, Perl   	    |
* _static_: specify type in code (resolved during compilation)
* _dynamic_: don't specify type in code (resolved during runtime) ❓ 'dynamic' synonym for duck typing?
* _weak_: will perform type conversion (e.g. JS) 
* _strong_: won't perform type conversion `42 + 'hi'` throws `TypeError` (only time this happens in Python is `if` statements)
* history https://www.youtube.com/watch?v=Tml94je2edk
* Liskov (from SOLID) https://en.wikipedia.org/wiki/Liskov_substitution_principle
* metaprogramming and dynamic typing vs monkey patching https://news.ycombinator.com/item?id=34611969
* _null_: https://2ality.com/2013/10/typeof-null.html https://www.fluentpython.com/lingo/#fail_fast
* _dependent_: https://www.stephendiehl.com/posts/calculus_of_constructions_python/
    
# 🟨 ZA

HOISTING
* variable/func declaration moved to top of containing scope during compilation and therefore you can reference at LOC higher the declaration LOC
* more on the matter re: Javascript https://stackoverflow.com/a/336868/6813490
* also synonym for moving declaration to higher LOC https://adamj.eu/tech/2024/09/08/django-repeated-decorators/
```python
# NameError: name 'greet' is not defined
greet()
def greet():
    print('hi there')
```
```js
console.log(hey); // undefined
var hey = 'hi zjv'
console.log(hey); // hi zjv
```

ZA
* _embedded_: language runs in same process as another language i.e. you need to impl interpreter and stdlib for embedded lang within host lang runtime?
* Jython being built in Java means it's easy to embed bc it will run anywhere that has a JVM https://softwareengineering.stackexchange.com/a/403915
* Lua good at embedding bc small stdlib, used in game dev https://news.ycombinator.com/item?id=3534746 howto https://news.ycombinator.com/item?id=36107315
* _static analysis_: run rules against non-running code; aka code quality (CQ); autofmt (black, prettier) lint (flake8) security (https://github.com/returntocorp/semgrep) https://blog.sylver.dev/build-a-custom-python-linter-in-5-minutes
* _standard library (stdlib)_: algos, datetime, networking https://drewdevault.com/2021/03/19/A-new-systems-language.html
> The base state of programming is gluing together library calls. Since glue code can be written in any language, most programmers' language preferences are really library preferences. - Graham https://twitter.com/paulg/status/1373926244673323008
> The true measure of a language isn’t how it uses semicolons; it’s the standard library of each language. - Ford what is code

---

* math happens in the CPU, in language interpreters, and in libraries https://macwright.com/2020/02/14/math-keeps-changing.html
* Knuth 'Art of Computer Programming' are math books https://news.ycombinator.com/item?id=19976957 https://news.ycombinator.com/item?id=38443668
* _string interpolation_: combine string literal and placeholders https://en.wikipedia.org/wiki/String_interpolation
* probabilistic https://mrandri19.github.io/2022/01/12/a-PPL-in-70-lines-of-python.html
* visual https://news.ycombinator.com/item?id=27928772
* non-English languages: Italian https://news.ycombinator.com/item?id=24330089 https://en.wikipedia.org/wiki/Non-English-based_programming_languages atypical languages in general https://esoteric.codes/
* _sink_: https://blog.wesleyac.com/posts/language-todos https://opencredo.com/java-go-back/ https://news.ycombinator.com/item?id=14521894 http://peter.bourgon.org/blog/2017/06/09/theory-of-modern-go.html
* checklist https://news.ycombinator.com/item?id=21057335
* programming languages not in English
* _escape_: treat char in non-literal manner e.g. `\d` as a single digit in regex vs. the char `d` https://docs.python.org/3/reference/lexical_analysis.html?highlight=string%20literal#string-and-bytes-literals

learn a few languages well
> Based on internet comments and advice, I had the idea learning more languages would teach me how to be a good programmer so I worked through introductory books on Python and Ruby. As far as I can tell, this taught me basically nothing useful and I would have been much better off learning about a specific area (like algorithms or networking) than learning lots of languages. https://danluu.com/learning-to-program/

* _null_: indicates absence of value (n.b. obj ref cannot be said to 'equal' null) [Beaulieu 2.29] https://www.lucidchart.com/techblog/2015/08/31/the-worst-mistake-of-computer-science/
* _debuggers_ https://eli.thegreenplace.net/2011/01/23/how-debuggers-work-part-1 https://eli.thegreenplace.net/2011/01/27/how-debuggers-work-part-2-breakpoints https://eli.thegreenplace.net/2011/02/07/how-debuggers-work-part-3-debugging-information https://scattered-thoughts.net/writing/looking-for-debugger-2/
* keep a language small https://medium.com/@erights/the-tragedy-of-the-common-lisp-why-large-languages-explode-4e83096239b9

> “So much of art is discovery, and you can’t discover anything if you can’t see what you’re doing” - Victor, ‘Inventing on Principle'
* bring your own client (editor, browser, RSS) https://www.geoffreylitt.com/2021/03/05/bring-your-own-client.html

when you really love your favorite language 💜
> My favorite programming language is C. It’s fast, simple, and compiles very quickly. Unlike many other languages, it’s quite reasonable for an individual to have a comprehensive understanding of the entire language. C is my default choice unless something else is particularly better suited (Python, shell script, etc.). There’s also a special place in my heart for Emacs Lisp, a venerable goofball language that’s so much fun to discuss. https://nullprogram.com/about/

## control flow

CONDITIONALS
* case statemtent, goto, if/else (invented by McCarthy http://www.paulgraham.com/diff.html)
* _guard clause_: seems synonymous w/ 'conditional' https://en.wikipedia.org/wiki/Guard_%28computer_science%29 https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html
* don't nest https://pythonbytes.fm/episodes/show/131/python-3-has-issues-over-on-github

LOOPS
* batched vs. naive = if dealing with large number of iterations, do write operation every n iterations https://avi.im/blag/2021/fast-sqlite-inserts/
* types: for, while, do-while (same as `while` except executes at least once)
* `continue`: goto next iteration
* `break`: exit

ZA
* _branchless_: https://registerspill.thorstenball.com/p/joy-and-curiosity-14 https://lemire.me/blog/2019/10/15/mispredicted-branches-can-multiply-your-running-times/ https://lemire.me/blog/2019/10/16/benchmarking-is-hard-processors-learn-to-predict-branches/
* _branching factor_: degree of nesting in control flow 📙 Kleppmann 81 https://fivethirtyeight.com/features/what-if-trump-loses-and-wont-leave/
* _cyclomatic complexity_: number of linear paths through a problem i.e. how many if-else https://github.com/PyCQA/mccabe
> diff btw branching factor and cyclomatic complexity?

## functions

* _caller_: calls
* _callee_: is called https://nullprogram.com/blog/2019/06/30/

* _parameter_: spec for arg (number, order, type) https://www.fluentpython.com/lingo/#parameter
* _argument_: value passed to function https://www.fluentpython.com/lingo/#argument
> If `@dataclass` is used just as a simple decorator with no parameters https://docs.python.org/3/library/dataclasses.html#module-contents

---

SEMANTICS https://realpython.com/python-pass-by-reference/#defining-pass-by-reference
* _function_: returns single obj https://www.youtube.com/watch?v=EnSu9hHGq5o 14:30
* _subroutine_: synonym for function https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/
* aka callable https://towardsdatascience.com/functools-the-power-of-higher-order-functions-in-python-8e6e61c6e4e4
> That process of going character by character can be wrapped up into a routine - also called a function, a method, a subroutine, or component. (Little in computing has a single, reliable name, which means everyone is always arguing over semantics.) - Ford what is code?

* _return_: permanently return control of execution to the point where the function was called https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/
* _yield_: return but temporary i.e. function will

types
* _factory_: function that returns another function https://lukeplant.me.uk/blog/posts/test-factory-functions-in-django/
* e.g. constructor w/ some defaults https://realpython.com/factory-method-python/
* _generator_: returns stream of objs https://www.youtube.com/watch?v=EnSu9hHGq5o 14:30
* _first-class_: doesn't need to be attached to obj 
* _higher-order_: can be passed around, assigned to var, used as args to another function, returned from function, take other function as arg https://www.techbeamers.com/higher-order-functions-in-python/
* _lambda_: anonymous function; syntactic sugar for a normal function definition
* _eval()_: take string and evaluate as if expression from language

evaluation https://en.wikipedia.org/wiki/Evaluation_strategy
* _eager_: eval expression during assignment
* _lazy_: don't eval until necessary 🗄 `django.md` db
* _thunk_: way to do lazy evaluation https://en.wikipedia.org/wiki/Thunk

## overloading

* _function overloading_: same method name, different sig (i.e. diff params)
* Python doesn't support directly, easiest impl is variadic args
```python
def hey(*args):
    if args:
        print(*args)
    else:
        print("hi!")
```
* _operator overloading_: operator works differently based on args https://en.wikipedia.org/wiki/Operator_overloading

---

FUNCTION OVERLOADING
```python
# Python's functools module provides @singledispatch, which allows function overloading based on the type of the first argument.
from functools import singledispatch

@singledispatch
def process(value):
    print(f"Default: {value}")

@process.register(int)
def _(value):
    print(f"Processing an integer: {value}")

@process.register(str)
def _(value):
    print(f"Processing a string: {value}")

process(42)       # Processing an integer: 42
process("Hello")  # Processing a string: Hello
process([1, 2])   # Default: [1, 2]
```
* some people don't like https://news.ycombinator.com/item?id=22347007
* can do in Python via variadic args https://news.ycombinator.com/item?id=22346418 https://news.ycombinator.com/item?id=22347918
> Function overloading is a common programming pattern which seems to be reserved to statically-typed, compiled languages. https://martinheinz.dev/blog/50
* can do in Python via multiple dispath / multimethods https://martinheinz.dev/blog/50
* can do in Python via `__call__`, virtual namespace, decorators https://arpitbhayani.me/blogs/function-overloading

OPERATOR OVERLOADING
* handled by language data model
```python
print(1 + 2)
print("hey " + "there)
print("hey " * 3)
```
* handled by classes
> operators with special syntax (arithmetic operators, etc.) can be redefined for class instances https://docs.python.org/dev/tutorial/classes.html
```python
# https://monadical.com/posts/operator-overloading-in-python.html
class Clock:
   def __init__(self, time: str):
       self.hour, self.min = [int(i) for i in time.split(':')]

   def __repr__(self) -> str:
       min = '0' + str(self.min)
       return str(self.hour) + ':' + min[-2:]

   def __add__(self, other: Clock) -> Clock:
       hour, min = divmod(self.min + other.min, 60)
       hour = (hour + self.hour + other.hour) % 24
       return self.__class__(str(hour) + ':' + str(min))
```
