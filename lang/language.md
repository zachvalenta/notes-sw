# ⛩️

## 参考

## 进步

https://borretti.me/article/language-pragmatics

DONE
* _19-present_: Python, SQL
* _18_: Python, Spring Boot, Django/DRM
* _17_: PHP, SQL
* _16_: JavaScript, Java

# 📐 DESIGN

🔗 https://news.ycombinator.com/item?id=35813496
🗄
* `golang.md` za / design
* `python.md` za / design
* `sociology.md` linguistics
* `system.md` programs / paradigms

ABSTRACTION
* https://jesseduffield.com/Beginners-Guide-To-Abstraction/
* howto https://tonsky.me/blog/dsl/
* against abstraction https://thorstenball.com/blog/2015/10/22/write-stupid-code/
* _law of leaky abstractions_: natch; if they wouldn't exist in the first place https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/
* _DSL_: lose tooling of general purpose language https://news.ycombinator.com/item?id=22375721

COMMUNITY
> But the choice of a main programming language is the most important signaling behavior that a technology company can engage in. Tell me that you program in Java, and I believe you to be either serious or boring. In Ruby, and you are interested in building things quickly. In Clojure, and I think you are smart but wonder if you ship. In Python, and I trust you implicitly. In PHP, and we sigh together. In C++ or C, and I nod humbly. In C#, and I smile and assume we have nothing in common. In Fortran, and I ask to see your security clearance. These languages contain entire civilizations. - Ford what is code?
* Java developers have high pain tolerances https://news.ycombinator.com/item?id=25124513
> The wrong people like it. The programmers I admire most are not, on the whole, captivated by Java. http://www.paulgraham.com/javacover.html
> Language users do not miss conveniences that they have never had access to in the first place. Those few bi-cultural citizens who function in both Chinese-character and alphabetic worlds are aware of the advantages conferred by the alphabet, but even these people soon get used to the differences, which slip below the level of consciousness, unremarked and unlamented...in virtually every informatic context, from library card catalogs to everyday user's manuals, the relatively cumbersome Chinese writing system exerts a low-level but constant drag force on productivity 📝 Moser invisible writing
* stdlib https://borretti.me/article/languages-not-ecosystems
> 99.5% of programming consists of gluing together calls to library functions. All popular languages are equally good at this. So one can easily spend one's whole career operating in the intersection of popular programming languages. http://paulgraham.com/weird.html
> The true measure of a language isn’t how it uses semicolons; it’s the standard library of each language. - Ford what is code?
> I think a lot of the advances that happen in programming languages in the next fifty years will have to do with library functions. I think future programming languages will have libraries that are as carefully designed as the core language. Programming language design will not be about whether to make your language strongly or weakly typed, or object oriented, or functional, or whatever, but about how to design great libraries. The kind of language designers who like to think about how to design type systems may shudder at this. It's almost like writing applications! Too bad. Languages are for programmers, and libraries are what programmers need. - http://paulgraham.com/popular.html
> The open source JS ecosystem, though, has soooooo many folks working on it that you can almost always find something you need. Certainly compared to something like Java, which has a couple "800 pound gorilla" projects, but then it falls off pretty quickly. https://news.ycombinator.com/item?id=31996232

HOWTO
* development speed vs. execution speed https://bitfieldconsulting.com/golang/rust-vs-go
> One especially good groove to span is the one between tools and things made with them. For example, programming languages and applications are usually written by different people, and this is responsible for a lot of the worst flaws in programming languages. I think every language should be designed simultaneously with a large application written in it, the way C was with Unix. http://paulgraham.com/marginal.html
> Part of the problem here is social. Language designers like to write fast compilers. That's how they measure their skill. They think of the profiler as an add-on, at best. But in practice a good profiler may do more to improve the speed of actual programs written in the language than a compiler that generates fast code. Here, again, language designers are somewhat out of touch with their users. They do a really good job of solving slightly the wrong problem. http://paulgraham.com/popular.html
* expressive
> Large organizations have different aims from hackers. They want languages that are (believed to be) suitable for use by large teams of mediocre programmers-- languages with features that, like the speed limiters in U-Haul trucks, prevent fools from doing too much damage. Hackers don't like a language that talks down to them. Hackers just want power. http://www.paulgraham.com/javacover.html
* ability to experiment
> A programming language is for thinking of programs, not for expressing programs you've already thought of. It should be a pencil, not a pen. 📙 Graham hackers painters [22]
> Have you ever noticed that when you sit down to write something, half the ideas that end up in it are ones you thought of while writing? The same thing happens with software. Working to implement one idea gives you more ideas. 📙 Graham hackers painters [68]
* _feature creep_: adding more features vs. making existing features better https://twitter.com/random_walker/status/1182635589604171776
* increases headcount, not total users https://news.ycombinator.com/item?id=34567237
> Second, C has a tendency to be conservative, changing and growing very slowly. This is a feature, and one that is often undervalued by developers. (In fact, I’d personally like to see a future revision that makes the C language specification smaller and simpler, rather than accumulate more features.) - https://nullprogram.com/blog/2018/11/21/


SYSTEMS PROGRAMMING
* languages: C, C++, Rust
* things people write with: dbms, web server, compiler, shell https://drewdevault.com/2021/05/30/Come-build-your-project.html https://drewdevault.com/2021/02/21/On-the-traits-of-good-replacements.html
* fuzzy definition http://willcrichton.net/notes/systems-programming/ https://news.ycombinator.com/item?id=35092049
* memory management now in favor http://esr.ibiblio.org/?p=7804
* is easy :) https://news.ycombinator.com/item?id=34566918

## functional

---

https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell
https://bytes.yingw787.com/posts/2018/11/07/data_driven_testing

FUNCTIONAL 📙 Conery https://github.com/hemanth/functional-programming-jargon
* _functional_: function that operates on other functions https://stackoverflow.com/a/94056
* as design: pure, uses higher-order
* _higher-order function_: takes func as arg or return func https://www.fluentpython.com/lingo/
* e.g. decorators, closures, lambdas
* _first-class function_: https://www.fluentpython.com/lingo/#first-class_function
* _y combinator_: https://www.youtube.com/watch?v=QuXJ3kXUCiU
* _curry_: break down larger function into smaller and chaining them together 📙 Conery [291,302]
> diff to closure? https://stackoverflow.com/questions/62499789/racket-closure-currying-where-is-the-difference#62500425 🗄 `python.md` partial https://www.youtube.com/watch?v=kZlOy1BY6lY

* _none_: https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/
* _pure_: no side effects
* _side effect_: IO, mutation
* _functor_: func that iterates over things that are iterable [Conery 307]
* _monad_: functor iterates, monad does logic [Conery 307]
* wraps control flow https://bytes.yingw787.com/posts/2019/12/06/monads/ https://samgrayson.me/2019-08-06-monads-as-a-programming-pattern/ https://lukeplant.me.uk/blog/posts/understanding-monads-via-python-list-comprehensions/ https://rbtcollins.wordpress.com/2018/08/26/monads-and-python/

https://github.com/dry-python/returns Land of Lisp epilogue https://docs.python.org/3/howto/functional.html https://kite.com/blog/python/functional-programming https://stackoverflow.com/q/1017621/6813490 https://treyhunner.com/2018/09/stop-writing-lambda-expressions/ https://blog.cleancoder.com/uncle-bob/2014/11/24/FPvsOO.html https://julien.danjou.info/python-and-functional-programming/ https://sumit-ghosh.com/articles/demystifying-decorators-python/ https://jrsinclair.com/articles/2019/what-i-wish-someone-had-explained-about-functional-programming/ https://codewords.recurse.com/issues/one/an-introduction-to-functional-programming http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html https://blog.cleancoder.com/uncle-bob/2017/07/11/PragmaticFunctionalProgramming.html

## object-oriented

📙 Bugayenko elegant obj https://www.elegantobjects.org/

SOLID https://realpython.com/solid-principles-python/

OBJECTS
* _object_: vs. procedural 📙 Evans domain-driven [51]
* _object model_: how objs work in a language 📙 Ramalho [15]
* aka "data model" in Python
* BYO http://aosabook.org/en/500L/a-simple-object-model.html
* _class_: lang ft. that allows defining new types 📙 Ramalho https://www.fluentpython.com/lingo/#class
* _metaobject_: objs that form core of object model 📙 Ramalho [16]
* _attribute_: obj property i.e. field (data) or method (action) https://docs.python.org/dev/tutorial/classes.html
* _attribute reference_: access obj attr https://docs.python.org/dev/tutorial/classes.html#class-objects

INHERITANCE
* _inheritance_: subclass is an instance of parent class
> I use Django a lot and generally it's great. But I hate that you can't follow your code paths from start to finish on the surface. You have to know about how it works underneath. Meaning you can't just be a python + web server expert. You have to also be a Django expert. So I get non-Django experts reviewing code and they have no clue why things work or break. Just an opinion. Not saying this is objectively wrong. https://news.ycombinator.com/item?id=17728821

ZA
* _constant_: variable w/ hard-coded value
* _enumeration_: group of discrete constants https://realpython.com/python-enum/
* _member_: constant in enum

---

* _hierarchical_: 1 parent - 1 child
* _multi-level_: 1 grandparent - 1 parent - 1 child
* _multiple_: n parents - 1 child
* aka interfaces in Java, mixins in Python
* _polymorphism_: https://confuzeus.com/hub/django-web-framework/model-polymorphism/ https://news.ycombinator.com/item?id=27658706 re: duck typing https://www.fluentpython.com/lingo/#duck_typing
* _diamond problem_: https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem Python solves w/ MRO https://stackoverflow.com/a/44535084/6813490
* _Liskov_: every instance of a subclass (in this case, my extension of Thread) needs to remain a valid instance of the superclass
* _abstract class_: not instantiated; TwoDimensionalShape(Circle, Square, Triangle)
* _Law of Demeter_: don't reach through one object to get to another [Conery 278]

OPINIONS
* Golang https://blog.gypsydave5.com/posts/2024/4/12/go-is-an-object-oriented-programming-language/
* Smalltalk https://news.ycombinator.com/item?id=34137751 https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html
* http://www.smashcompany.com/technology/object-oriented-programming-is-an-expensive-disaster-which-must-end
* creates confusion
> In 2003, Jane Street began a rewrite of its core trading systems in Java. The rewrite was eventually abandoned, in part because the resulting code was too difficult to read and reason about...we built up a nest of classes that left people scratching their heads when they wanted to understand just what piece of code was actually being invoked when a given method was called. https://queue.acm.org/detail.cfm?id=2038036
> The price is that the resulting code is bloated with protocols and full of duplication. This is not too high a price for big companies, because their software is probably going to be bloated and full of duplication anyway. http://www.paulgraham.com/noop.html

---

* quadratic complexity
* _composition_:
* CUPID https://dannorth.net/2022/02/10/cupid-for-joyful-coding/
* _delegation_: composition by another name https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/#delegation-in-oop
* https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/

* _information hiding_: obj as black box against which you can ask for stuff but you don't know how it's going on inside [Connolly database systems 25.3.1 814]
* _override_: replace method inherited from parent
* _history_: 1970s Smalltalk https://news.ycombinator.com/item?id=29890205 1990s Java https://twobithistory.org/2019/01/31/simula.html https://medium.com/javascript-scene/the-forgotten-history-of-oop-88d71b9b2d9f https://www.hillelwayne.com/post/alan-kay/ https://www.youtube.com/watch?v=QyJZzq0v7Z4

__static methods__
* _static_: belongs to class, not an individual instance
* something that won't change across instances 📍 example
* code organization https://stackoverflow.com/a/14085311/6813490
* bad for testing? https://stackoverflow.com/a/2671938/6813490

opinions
* tell, don't ask [Conery 276]
* unlearn OOP https://dpc.pw/the-faster-you-unlearn-oop-the-better-for-you-and-your-software
* Hickey https://www.youtube.com/watch?v=oytL881p-nQ

method chaining https://www.youtube.com/watch?v=BY34Fe-2xgk
* used in SQL query builders [2:45]
```python
class Player:
    def __init__(self, sh_per=0.40):
        self.points = 0
        self.fatigue = 0
        self.shooting_per = sh_per
    
    def shoot(self):
        self.points += 2.0 * self.shooting_per
        self.fatigue += 1
        return self

    def stats(self):
        print(f"pts {self.points} fatigue {self.fatigue}")
```

## typing

🔗 https://en.wikipedia.org/wiki/Type_system
🗄
* `algos.md` data structures
* `python.md` typing

SEMANTICS
* _nominative typing_: obj type explicitly declared https://en.wikipedia.org/wiki/Nominal_type_system
* _duck typing_: obj is type if it has properties/methods of that type (vs. nominative) https://docs.python.org/3/glossary.html#term-duck-typing
* _type inference_: figure out type based on context https://calpaterson.com/mypy-hints.html
> aka implicit? https://go.dev/tour/basics/10

---

> types add value and they add cost https://lucumr.pocoo.org/2023/12/1/the-python-that-was/
https://langdev.stackexchange.com/questions/2692/how-should-i-read-type-system-notation
https://news.ycombinator.com/item?id=36775644

* history https://www.youtube.com/watch?v=Tml94je2edk
* Liskov (from SOLID) https://en.wikipedia.org/wiki/Liskov_substitution_principle
* Flask debugger, typing, metaprogramming vs monkey patching https://news.ycombinator.com/item?id=34611969
* _null_: https://2ality.com/2013/10/typeof-null.html
    
GENERICS
* _generics_: prevent type errors in Collections (bc Collections can contain any obj type e.g. str, int, et al.)
* e.g. reverse array of any type
* in Python https://stackoverflow.com/questions/6725868/generics-templates-in-python https://mypy.readthedocs.io/en/stable/generics.html https://www.youtube.com/watch?v=LcfxUU1A-RQ
* https://news.ycombinator.com/item?id=29705134
* https://news.ycombinator.com/item?id=29702607
* https://drewdevault.com/2019/02/18/Generics-arent-ready-for-Go.html
* https://go.dev/blog/why-generics https://go.dev/blog/generics-next-step

https://gist.github.com/non/ec48b0a7343db8291b92
https://www.fluentpython.com/lingo/#fail_fast
* Kotlin as toolable https://news.ycombinator.com/item?id=33331123
 https://thelittletyper.com/
https://www.destroyallsoftware.com/compendium/types?share_key=baf6b67369843fa2

* gradual typing: type hints/annotations in code checked by static analysis tooling, not compiler
* _definitions_: strong/weak less rigorously defined than static/dynamic [Smallshire 1 @ 5.4]
* _sink_: https://danluu.com/empirical-pl/ https://www.cs.uaf.edu/users/chappell/public_html/class/2018_spr/cs331/docs/types_primer.html https://eli.thegreenplace.net/2006/11/25/a-taxonomy-of-typing-systems vocab https://cdsmith.wordpress.com/2011/01/09/an-old-article-i-wrote/ https://danluu.com/empirical-pl/

|   	    | static   	| dynamic   	    |
|---	    |---	    |---	            |
| strong   	| C++      	| Python, Ruby   	|
| weak  	|   	    | JS, Perl   	    |

* _static_: specify type in code (resolved during compilation)
* _dynamic_: don't specify type in code (resolved during runtime) ❓ 'dynamic' synonym for duck typing?
* _weak_: will perform type conversion (e.g. JS) 
* _strong_: won't perform type conversion `42 + 'hi'` throws `TypeError` (only time this happens in Python is `if` statements)

__opinions__

* implicit https://news.ycombinator.com/item?id=26671136 https://go.dev/tour/basics/10
https://news.ycombinator.com/item?id=24839697

> Type checking catches bugs that unit testing does not, often much faster and with less code overhead than unit testing requires. It has surprised me how much of my unit tests were de facto implementing a type system halfheartedly as opposed to testing behavior of those types. - https://threadreaderapp.com/thread/1141836825838800896.html more on typing as a analog to unit tests https://www.jorgemanrubia.com/2019/06/22/on-ruby-and-type-checkers/

> Research has shown that Franklin's remark about giving up liberty to purchase safety is actually about type systems. - https://twitter.com/MarijnJH/status/570833749065265152

turns into metadata addiction

> And Haskell, OCaml and their ilk are part of a 45-year-old static-typing movement within academia to try to force people to model everything. Programmers hate that. These languages will never, ever enjoy any substantial commercial success, for the exact same reason the Semantic Web is a failure. You can't force people to provide metadata for everything they do. They'll hate you. The type system is 'wrong' whenever it cannot match the intended computational model. Every time want to use multiple inheritance or mixins in Java's type system, Java is 'wrong', because it can't do what you want. You have to take the most natural design and corrupt it to fit Java's view of the world. I think the general answer to this is: when in doubt, don't model it. Just get the code written, make forward progress. Don't let yourself get bogged down with the details of modeling a helper class that you're creating for documentation purposes. http://steve-yegge.blogspot.com/2008/02/portrait-of-n00b.html

# 📚 LANGUAGES

> an algorithm management system 📰 Ford what is code?
> We can see that Brooks' 1986 claim that we've basically captured all the productivity gains high-level languages can provide isn't too different from an assembly language programmer saying the same thing in 1955, thinking that assembly is as good as any language can be. https://danluu.com/essential-complexity/#summary

HISTORY https://increment.com/programming-languages/language-history/
* _1957_: Fortran (IBM); still the best for math https://news.ycombinator.com/item?id=14498904 Python better? https://cerfacs.fr/coop/fortran-vs-python role in Python https://labs.quansight.org/blog/building-scipy-with-flang
* _1958_: Lisp (MIT)
* _1959_: Cobol; process transactions
* _1963_: BASIC https://en.wikipedia.org/wiki/BASIC https://en.wikipedia.org/wiki/Pick_operating_system
* _1972_: C (Bell Labs) Smalltalk (Xerox Parc) 
* _1985_: C++ (Bell Labs)
* _1990_: Python
* _1993_: Lua
* _1995_: Java (Sun) JS (Netscape) Ruby (Matz) https://twobithistory.org/2017/11/19/the-ruby-story.html
* _1996_: OCaml https://ocaml.org/ https://crmarsh.com/intro-to-ocaml/ https://crmarsh.com/ocaml-dev-environment/
> part of ML family tree, related to F# https://en.wikipedia.org/wiki/ML_(programming_language)
* _2015_: Rust
* _2016_: Zig

🇧🇷 LUA https://www.lua.org/start.html 🔍 https://github.com/LewisJEllis/awesome-lua https://nvchad.com/docs/quickstart/learn-lua
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

🔤 R
* language for stats https://walker-data.com/census-r/index.html
* _CRAN_: where you download R itself and also (?) R packages https://cran.r-project.org/
* _packrat_: pkg manager https://rstudio.github.io/packrat/
* _RStudio_: IDE
* _tidyverse_: https://www.tidyverse.org/index.html
* clean https://github.com/sfirke/janitor https://tidyr.tidyverse.org https://tidyr.tidyverse.org/articles/tidy-data.html
* functional https://purrr.tidyverse.org/
* string pattern match https://stringr.tidyverse.org/
* plot https://ggplot2.tidyverse.org/ grammar of graphics https://plotnine.org/
* dataframes https://tibble.tidyverse.org/

🦀 RUST https://rftgu.rs/ https://www.youtube.com/playlist?list=PLhoH5vyxr6Qqn3E9tm5bwUCQrkDzAIhav https://google.github.io/comprehensive-rust/ https://www.youtube.com/@codetothemoon https://roadmap.sh/rust https://www.ntietz.com/projects/
* vs. Golang https://registerspill.thorstenball.com/p/glad-i-did-it-in-go
> This blog post, Rewriting Rust, was very interesting. “I swear, it took more effort to learn pinning in rust than it took me to learn the entire Go programming language.” Some day (in the far future) I might write more about my feelings on Rust, but while reading this post I kept waiting for the paragraph in which they say what they would remove from the language. That paragraph never came and I think that’s one of the biggest sources of friction between me and Rust. https://registerspill.thorstenball.com/p/joy-and-curiosity-9
* incomplete bc no BDFL https://news.ycombinator.com/item?id=41656463 https://doc.rust-lang.org/unstable-book/the-unstable-book.html
> Maybe this is by design. Good languages are stable languages. It might be time to think of rust as a fully baked language - warts and all. Python 2.7 for life. https://josephg.com/blog/rewriting-rust/
* release, editions https://blog.rust-lang.org/2014/10/30/Stability.html https://doc.rust-lang.org/edition-guide/editions/
* desktop framework https://github.com/tauri-apps/tauri https://blog.gitbutler.com/open-source-pledge-2024/
* Neovim https://www.youtube.com/watch?v=mh_EJhH49Ms
* example project https://github.com/nate-sys/tuime https://github.com/swsnr/mdcat
* books https://news.ycombinator.com/item?id=34556318 https://github.com/plabayo/learn-rust-101/blob/main/README.md
* CLI https://www.amazon.com/gp/product/1098109430/ref=ox_sc_act_title_1?smid=ATVPDKIKX0DER&psc=1
* web https://tech.marksblogg.com/poem-rust-web-framework.html https://tech.marksblogg.com/actix-rust-web-framework.html https://tech.marksblogg.com/rocket-rust-web-framework.html https://www.shuttle.rs/blog/2023/09/27/rust-vs-go-comparison
* TUI https://github.com/gyscos/Cursive https://github.com/fdehau/tui-rs https://github.com/ratatui-org/ratatui https://github.com/lusingander/stu
* vs. Golang https://news.ycombinator.com/item?id=31205072
* doesn't have a spec https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html
* big learning curve https://news.ycombinator.com/item?id=30627667
> Despite my infamous distaste for Rust, long-time readers will know that where I have distaste for Rust, I have passionate scorn for C++. I’m quite glad to see Rust taking it on, and I hope very much that it succeeds in this respect. https://drewdevault.com/2021/02/21/On-the-traits-of-good-replacements.html
* syntax https://lucumr.pocoo.org/2015/5/27/rust-for-pythonistas/ https://fasterthanli.me/blog/2020/a-half-hour-to-learn-rust/
* used for: CPU intensive, not API https://news.ycombinator.com/item?id=25798008
* governance problems https://news.ycombinator.com/item?id=28513130
* what people love: packaging, DX https://stackoverflow.blog/2020/06/05/why-the-developers-who-use-rust-love-it-so-much parallelization https://news.ycombinator.com/item?id=26443768 CLI (jless) https://news.ycombinator.com/item?id=30273940 correctness
> [invariant violation] At point A, there's some assumption, and way over there at point B, that assumption is violated... Type systems prevent some invariant violations. Because that works, there are ongoing attempts to extend type systems to prevent still more invariant violations. That creates another layer of confusing abstraction. Some invariants are not well represented as types, and trying makes for a bad fit. What you're really trying to do is to substitute manual specification of attributes for global analysis. The Rust borrow checker is an invariant enforcer. It explicitly does automatic global analysis, and reports explicitly that what's going on at point B is inconsistent with what point A needs. This is real progress in programming language design, and is Rust's main contribution. https://news.ycombinator.com/item?id=29996240

↯ ZIG
* overview https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202203010 https://kristoff.it/blog/maintain-it-with-zig/
* tutorial https://gist.github.com/ityonemo/769532c2017ed9143f3571e5ac104e50
* BYO ls https://stackoverflow.com/questions/13554150/implementing-the-ls-al-command-in-c
* getting popular https://macwright.com/2020/08/01/recently.html
* https://news.ycombinator.com/item?id=29702607
* seems way easier than Rust https://scattered-thoughts.net/writing/assorted-thoughts-on-zig-and-rust/ https://kevinlynagh.com/rust-zig/
* smart users https://github.com/jamii
* current state of affairs https://news.ycombinator.com/item?id=36149462
* use as compiler https://jakstys.lt/2022/how-uber-uses-zig/ https://mitchellh.com/writing/zig-comptime-tagged-union-subset
* as a teaching language https://news.ycombinator.com/item?id=32752383

ZA
* _APL_: https://mathspp.com/blog/what-learning-apl-taught-me-about-python
* _C++_: https://ccc.codes/ https://github.com/green7ea/cpp-compilation http://esr.ibiblio.org/?p=7724 people hate C++ https://news.ycombinator.com/item?id=33436268 https://borretti.me/article/simplicity-and-survival https://news.ycombinator.com/item?id=34588340 https://news.ycombinator.com/item?id=34643530
* _Elixir_: well-liked, good at concurrency/distributed, OTP (stdlib) BEAM (VM), functional https://stackoverflow.com/questions/32807981/what-exactly-is-erlang-otp https://news.ycombinator.com/item?id=34936023 https://robconery.com/video/how-elixirs-concurrency-changed-me-as-a-programmer/ https://news.ycombinator.com/item?id=28482580 https://news.ycombinator.com/item?id=34934620 main reason to use is Phoneix, and the main reason to use that is LiveView https://joyyo.app/elixir-for-humans-who-know-python https://news.ycombinator.com/item?id=37787805 https://aosabook.org/en/v1/riak.html
* with Alpine https://news.ycombinator.com/item?id=34365515
* _Haskell_: https://learnyouahaskell.com/ https://haskellbook.com/ https://news.ycombinator.com/item?id=40702146
* _Julia_: theoretically great (e.g. can inspect assembly) but practically immature and academic https://increment.com/programming-languages/goldilocks-language-history-of-julia/  https://www.evanmiller.org/why-im-betting-on-julia.html https://danluu.com/julialang/ https://viralinstruction.com/posts/badjulia/
* _Pascal_: https://news.ycombinator.com/item?id=34939231 https://en.wikipedia.org/wiki/Pascal_(programming_language)
* _PHP_: Laravel great for solo devs and big in Europe https://news.ycombinator.com/item?id=30259097 https://stitcher.io/blog/php-in-2019 https://news.ycombinator.com/item?id=34411018
* _Prolog_: https://rogersm.net/posts/developing-a-go-bot-embedding-ichiban-prolog/
* _Nim_: https://nim-lang.org/ https://github.com/Pebaz/nimporter

## assembly

🔗 https://github.com/hackclub/some-assembly-required
📚
* Petzold code (24)
* Nisan nand2tetris (4, 6)

* https://shikaan.github.io/assembly/x86/guide/2024/09/08/x86-64-introduction-hello.html
* ARM https://www.youtube.com/watch?v=gfmRrPjnEw4
* compiler explorer https://godbolt.org/
* _assembly_: shorthand for whatever binary the CPU understands 📙 `evans-linux.pdf` 1
* _learning_: 📍 finish second chapter of Manga Microprocessors 🗄 Duntemann https://news.ycombinator.com/item?id=7143585 Latacora CTF https://news.ycombinator.com/item?id=7145479 🗄 Bryant https://news.ycombinator.com/item?id=7143866 microcontrollers https://news.ycombinator.com/item?id=7147009
https://wizardzines.com/comics/assembly/
* most assembly scoped to particular machine architecture; assembly used to be what OS were written in until Unix [LPI 1.1]
* macOS https://news.ycombinator.com/item?id=7144020
* _HLA (high-level assembly)_: just a Randall Hyde thing https://news.ycombinator.com/item?id=7143409
* https://news.ycombinator.com/item?id=26311722

## C lang

📹 https://www.youtube.com/c/JacobSorber/videos
📚
* Matthews dive https://diveintosystems.org/
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming
🔍
* courses http://www.buildyourownlisp.com https://gribblelab.org/teaching/CBootCamp/ https://www.enlightenment.org/docs/c/start
* more books http://fabiensanglard.net/c/index.php

STDLIB
* things people don't like and replacements https://news.ycombinator.com/item?id=25125034
* _libc_: POSIX spec for os stdlib; used by higher-levels languages for everything from networking to memory management https://wizardzines.com/comics/libc/
* _glibc_: most common impl of libc https://stackoverflow.com/a/11373143
* _musl_: used by Alpine https://www.musl-libc.org/ https://news.ycombinator.com/item?id=23819500 https://www.etalabs.net/compare_libcs.html cleaner? https://drewdevault.com/2020/09/25/A-story-of-two-libcs.html

DESIGN
> C has a tendency to be conservative, changing and growing very slowly. https://nullprogram.com/blog/2018/11/21/
> The C language is old and boring. It is a well-known and well-understood language. https://sqlite.org/whyc.html
> When programming in C you do not stand on a path, but a plane of decision, and C dares you to decide what to do. http://www.buildyourownlisp.com/chapter1_introduction
* portable
> Libraries written in C are callable from any programming language. https://sqlite.org/whyc.html
> The Linux kernel is written in C. The software that connects your printer to your computer could be in C. The Web servers that serve up your Web pages are often written in C. It’s also a good language for writing other languages - Python, PHP, and Perl are written in C, as are many others. C is a language you use for building systems; it has the same role in computing that Latin did among Renaissance academics. - Ford what is code?
* example code: Redis, SQlite https://news.ycombinator.com/item?id=30753428

HISTORY
* _1972_: created https://www.bell-labs.com/usr/dmr/www/chist.html
* _1978_: K&R spec
* _1980_: prominence http://esr.ibiblio.org/?p=7711
* _1989_: c89
* _90s-present_: used for firmware and kernels but new stuff now in other languages http://esr.ibiblio.org/?p=7711
* c99, c11, c17 https://drewdevault.com/2020/11/01/What-is-Gemini-anyway.html https://news.ycombinator.com/item?id=24361469

PROJECTS
* Python extension https://realpython.com/build-python-c-extension-module/
* BYO db https://cstack.github.io/db_tutorial/
* cmus https://github.com/cmus
* BYO virtual machine https://justinmeiners.github.io/lc3-vm/
* BYO text editor https://viewsourcecode.org/snaptoken/kilo/01.setup.html https://github.com/codecrafters-io/build-your-own-x#build-your-own-text-editor

----

* start here https://realpython.com/c-for-python-programmers/
> Make builds output files from input files. It was originally designed for C programs, which utilize both code and header files which are built into object files. These object files are then compiled to binary. This is a multi-step build that requires some orchestration. That’s what Make is all about. 📙 Conery [406]

misc
* design: https://saagarjha.com/blog/2020/05/10/why-we-at-famous-company-switched-to-hyped-technology/ https://eev.ee/blog/2016/12/01/lets-stop-copying-c/ https://nullprogram.com/tags/c/
* sysroot, undefined behavior (UB) https://news.ycombinator.com/item?id=30488979
* _gdb_: debugger https://www.gnu.org/software/gdb/ https://github.com/cs01/gdbgui can be used on more than C https://golang.org/doc/gdb influential in debugger design https://www.npmjs.com/package/trepanjs https://rubygems.org/gems/trepanning https://github.com/snare/voltron
* Postgres codebase is supposed to be a good guide https://news.ycombinator.com/item?id=20556336
* `#define`: constants https://www.youtube.com/watch?v=hsmGp3cp_50 0:50

under the hood
* _ABI_: https://en.wikipedia.org/wiki/Application_binary_interface https://news.ycombinator.com/item?id=24140848 https://gankra.github.io/blah/c-isnt-a-language/
* _abstract machine_: C's version of a virtual machine https://words.steveklabnik.com/should-you-learn-c-to-learn-how-the-computer-works
* _bitfield_: https://danluu.com/algorithms-interviews/
* _compilation_: https://jvns.ca/blog/2019/10/28/sqlite-is-really-easy-to-compile/
* _garbage collection_: (kinda) possible https://stackoverflow.com/a/5009966/6813490
* _undefined behavior_: when an error happens but it's not thrown i.e. `TypeError` in Python might be mean the compiler just chugging along in C https://blog.regehr.org/archives/213 https://news.ycombinator.com/item?id=24363573
* call Python from C http://eradman.com/posts/extending-c-python.html

## Java

* abstraction run wild https://news.ycombinator.com/item?id=8420314
* Flask for Java https://javalin.io/
* version mgmt: sdkman https://www.youtube.com/watch?v=rouaKVAH3iM
* 🎗 emailed self books on Maven and Spring Boot
* HTTP client https://github.com/square/okhttp
* dev env https://news.ycombinator.com/item?id=30841581
* relearn https://maxmautner.com/2019/09/12/java-primer-for-python-developers.html
* Scala https://news.ycombinator.com/item?id=28479697
* concurrency: https://return.co.de/blog/articles/programming-languages/
* exceptions: Object > Throwable > Error, Exception; checked (compile time) vs. unchecked (runtime)
* governance https://headcrashing.wordpress.com/2019/05/03/negotiations-failed-how-oracle-killed-java-ee/ https://docs.google.com/document/d/1nFGazvrCvHMZJgFstlbzoHjpAVwv5DEdnaBr_5pKuHo/preview
* GUI: AWT -> FX -> Swing
* imports: can't alias imports, so if you have 2 classes w/ same name, pick one and instead of importing, refer to using fully-qualified name https://stackoverflow.com/a/35686734/6813490
* primitives: everything that's not an object
* _JNDI_: API to lookup on fs or db
* naming: `DefaultJmsListenerContainerFactoryConfigurer` https://spring.io/guides/gs/messaging-jms/
* testing: beware of EasyMock and PowerMock https://return.co.de/blog/articles/java-development-fast/
* run from shell
```sh
# ❗️ "Class JavaLaunchHelper is implemented in both" is [Java on Mac bug](https://stackoverflow.com/a/43003231/6813490)
# from $CWD https://stackoverflow.com/a/3692235/6813490
javac Hello.java
java -cp . Hello

# from package root i.e. `.com` https://stackoverflow.com/a/3081700/6813490
java -cp . com.zachvalenta.Main
```

PACKAGES
* package naming convention to create globally unique namespace
* full class name includes the package name
* technically no correlation btw package name and file structure but IDE will complain, which is why we get comically deep directory nesting
* _classpath_: Java's answer to $PATH i.e. where it looks for `.class` files https://stackoverflow.com/a/2396513/6813490

HIBERNATE
* _DTO/DAO_ https://stackoverflow.com/a/35079306/6813490
* _JPA_: spec for ORM https://stackoverflow.com/a/11881732/6813490
* _ORM_: Hibernate (impl of JPA) JDBC (connect, query w/ SQL) https://www.jooq.org
* pull from db and map onto the `@Entitiy` class
* `validate`: validates that entities compatible against db (checks presence of tables, columns, id generators) https://stackoverflow.com/a/44479455/6813490
* [default value for column](https://www.daveperrett.com/articles/2007/12/05/default-values-with-hibernate-annotations/)
* `none`: do nothing; same effect as elision from `app.props`
* `validate`: [validate entities against DDL](https://stackoverflow.com/q/43965089/6813490)
* `create`: run DDL based on entities when app boots
* `create-drop`: " " + then rm on shutdown
* `update`: update schema according to entities (but won't rm columns)
❗️ `update` not for PROD https://stackoverflow.com/a/221422/6813490 + https://stackoverflow.com/a/21113195/6813490 + https://stackoverflow.com/a/42147995/6813490
* create table
```java
@Entity
@Table(name = "ZV_TEST_TABLE")
public class ZVTestTable {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private long id;
    private String foocol;
    private String barcol;
}
```

JVM
* _Java_: language + JDK
* _JDK_: JRE + compiler; `/usr/libexec/java_home`
* _JRE_: JVM + libs (Collections, IO)
* _JVM_: src to bytecode, env to run byte; handles IO, threading; [written in C](https://stackoverflow.com/a/1220931)
* _classloader_: pull `.class` files into JVM
* workaround for JVM cold start https://medium.com/teads-engineering/jvm-and-cache-warm-up-strategy-for-high-traffic-services-4b5016f8b565
* keeps getting faster https://stackoverflow.blog/2020/07/30/java-at-25-features-that-made-an-impact-and-a-look-to-the-future

MAVEN
* better than Gradle: https://return.co.de/blog/articles/java-development-fast/ https://blog.philipphauer.de/moving-back-from-gradle-to-maven/ but Gradle uses Groovy instead of XML, back in the day there was Ant
* _bill of materials_: define parent POM, all lower transitive dependencies (child dependencies [test, web, Jackson] and their children) will all be compatible) https://www.thoughtworks.com/radar/techniques?blipid=202110076
* build: `package`
* fix all your problems: `clean install`
* skip tests: `-DskipTests=true`
* rebuild w/out deps update: `-o`
* `target`: where compiled code goes
* _plugin_: kinda like a class
* _goal_: kinda like a method on a class
* _phase_: series of goals strung together e.g. `mvn package` runs all goals up to and incl. `package`; `install` (installs to local `~/.m2`) `deploy` same as install except pushes to internal repo

SPRING
* _Spring_: next gen EE
* _Spring Boot_ : Spring (MVC) + OOB config
* _wiring_: use IDE to make Maven project, parent POM to `spring-boot-starter-parent` https://www.youtube.com/watch?v=bDtZvYAT5Sc
* _aspect-oriented_: afaik encapsulation by another name; separate logging from business logic 📙 Ramalho 16
* _bean_: obj
* _boot_: init Spring context (looks around for `@Components`), starts Tomcat, runs app https://www.baeldung.com/running-setup-logic-on-startup-in-spring
* _container_: manage beans i.e. create, config, connect, garbage collection
* _dependencies_: https://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#appendix-dependency-versions
* _history_: 2002 Rod Johnson publishes framework, turns into SpringSource 2003 Dell acquires VMWare 2009 VMWare acquires SpringSource 20013 Dell and GE form Pivotal
* `@Bean`: init obj and keep track of it https://stackoverflow.com/a/34174782/6813490
* `@Configuration`: seems similar to `@Bean`
* `@Autowire`: use obj already init elsewhere (or from some 3rd-party lib)
* `@Entity`: tells JPA to map class to table https://stackoverflow.com/a/29333628/6813490
* `@Value`: pull in V from `.properties` into class

## Lisp

LANGUAGE
* little syntax https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html
* mutual interop w/ Java https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html

ZA
* written in Lisp: ITA, Emacs
* embedded in Python https://news.ycombinator.com/item?id=33600941

---

📙 SICP https://wizardforcel.gitbooks.io/sicp-in-python/content/ https://mitpress.mit.edu/sites/default/files/sicp/index.html https://www.youtube.com/playlist?list=PLE18841CABEA24090 http://www.sicpdistilled.com/ https://xuanji.appspot.com/isicp/ https://corecursive.com/039-hal-abelson-sicp/ https://news.ycombinator.com/item?id=24428907 https://thorstenball.com/blog/2016/11/30/why-i-wrote-a-book-about-interpreters/ https://news.ycombinator.com/item?id=30016323

ZA
* declarative? 📙 Karwin [2]
* _history_: self-perpetuating failure https://news.ycombinator.com/item?id=13143282 Lisp was more awesome in a world w/out Java, Python?
* https://twobithistory.org/2018/10/14/lisp.html
* https://beautifulracket.com/appendix/why-racket-why-lisp.html
* http://jakob.space/blog/thoughts-on-lisps.html
* http://www.paulgraham.com/rootsoflisp.html
* https://treenotation.org/
* https://www.youtube.com/watch?v=1r5GkhoN-Zc
* https://github.com/syncsynchalt/axiomatic-lisp
* https://news.ycombinator.com/item?id=33600941
* https://news.ycombinator.com/item?id=40335608
* https://www.fosskers.ca/en/blog/rounds-of-lisp

LISPS
* _Clojure_: https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html https://tonsky.me/blog/utils/ Joy of Clojure better than Clojure for the Brave and True? http://ahungry.com/blog/2018-12-26-Clojure-is-Capable.html https://news.ycombinator.com/item?id=20844978 check out this book, Dan Luu recommended https://twitter.com/ctford/status/1345798531119009792
* https://github.com/damn/core
* _Common Lisp_: less Lisp-y, really fast compiler https://notes.eatonphil.com/starting-a-minimal-common-lisp-project.html https://ebzzry.io/en/script-lisp/ http://stevelosh.com/blog/2018/08/a-road-to-common-lisp/ http://paulgraham.com/popular.html https://news.ycombinator.com/item?id=32723784 https://borretti.me/article/simplicity-and-survival
* _Fennel_: Lisp built on Lua https://fennel-lang.org/ https://www.mattroelle.com/fennel-the-practical-lisp https://github.com/pluffie/neoproj
* _Racket_: based off Scheme, async database https://notes.eatonphil.com/walking-through-a-basic-racket-web-service.html https://news.ycombinator.com/item?id=7823337 https://news.ycombinator.com/item?id=19952714 https://news.ycombinator.com/item?id=23132621 https://news.ycombinator.com/item?id=8206038 https://news.ycombinator.com/item?id=13881535 https://news.ycombinator.com/item?id=32723784
* _Scheme_: lotta different Scheme compilers and Scheme programs are not compatible across different compilers bc the language spec is so minimal (50 pages compared to 650 for Java) https://hardmath123.github.io/perchance-to-scheme.html 

LANGUAGE https://tryclojure.org/
* https://stackoverflow.com/questions/47482349/what-characterizes-a-lisp-dialect
* s-expressions https://news.ycombinator.com/item?id=5654398 https://notes.eatonphil.com/compiler-basics-lisp-to-assembly.html
* no loops https://www.lvguowei.me/post/sicp-goodness-looping/
* prefix notation: operator comes first https://www.braveclojure.com/getting-started/

# 📥 MEMORY

🔍 https://softwareengineering.stackexchange.com/questions/tagged/memory
🗄
* `architecture.md` memory
* `python.md` memory

> port from `python.md`

memory management https://stackoverflow.com/a/3434252
* _unmanaged code_: language w/ no memory management e.g. C, C++; sometimes used to mean "compiles directly to machine code" by people who do not understand that C has an abstract machine
* _managed code_: language w/ memory management (Java); dynamic languages not typically described as such, more of a marketing term for enterprise languages
* _garbage_: 
* _garbage collection_: scheduled memory management; yes (Python, Java) no (Rust 'borrow checker') no-unless-you-hack-real-hard (C, C++)
* _memory leak_: https://www.glean.com/blog/how-we-analyzed-and-fixed-a-golang-memory-leak
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

# 🟨 ZA

OVERLOADING
* _function overloading_: same method name, different sig (i.e. diff params)
* some people don't like https://news.ycombinator.com/item?id=22347007
* can do in Python via variadic args https://news.ycombinator.com/item?id=22346418 https://news.ycombinator.com/item?id=22347918
> Function overloading is a common programming pattern which seems to be reserved to statically-typed, compiled languages. https://martinheinz.dev/blog/50
* can do in Python via multiple dispath / multimethods https://martinheinz.dev/blog/50
* can do in Python via `__call__`, virtual namespace, decorators https://arpitbhayani.me/blogs/function-overloading
* _operator overloading_: operator works differently based on args https://en.wikipedia.org/wiki/Operator_overloading
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

HOISTING
* variable/func declaration moved to top of containing scope during compilation and therefore you can reference at LOC higher the declaration LOC https://chatgpt.com/c/6709656d-5ea4-8004-90c0-46226937e4aa
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
* _static analysis_: run rules against non-running code; aka code quality (CQ); autofmt (black, prettier) lint (flake8) security (https://github.com/returntocorp/semgrep) Sylver https://blog.sylver.dev/building-a-json-validator-with-sylver-part13-writing-a-json-parser-in-49-lines-of-code https://blog.sylver.dev/build-a-custom-python-linter-in-5-minutes
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

## compilers

🔗 https://en.wikipedia.org/wiki/Execution_(computing)
🔍 https://softwareengineering.stackexchange.com/questions/tagged/compiler
🗄️ `algos.md` data structures / tree
📚
* Ball interpreter https://vgel.me/posts/c500/
* Nystrom crafting https://craftinginterpreters.com
* Eloquent Javascript
* https://keleshev.com/compiling-to-assembly-from-scratch/

SEMANTICS
* _compiler_: src code -> machine code https://www.youtube.com/watch?v=QdnxjYj1pS0
* _transpile_: convert from one HLA to another http://coconut-lang.org/
* in JS world, to previous ECMAScript spec for older browser e.g. Babel https://www.vrk.dev/2019/07/11/why-is-modern-web-development-so-complicated-a-long-yet-hasty-explanation-part-1/
* _hot reload_: change program while it runs http://www.jakubkonka.com/2022/03/16/hcs-zig.html
* _inline cache_: https://en.wikipedia.org/wiki/Inline_caching https://bernsteinbear.com/blog/inline-caches-in-skybison/

| impl    | target  | link                                   |
|---------|---------|----------------------------------------|
| C       | C       | https://github.com/DoctorWkt/acwj      |

---

BNF https://realpython.com/python-bnf-notation/
BYO JSON parser https://news.ycombinator.com/item?id=38150833

* JIT https://tonybaloney.github.io/posts/python-gets-a-jit.html
* Bryant (5)
* Nisan nand2tetris (4, 6-11)

types of code 📙 Bryant computer systems (3)
* _machine code_: binary; handled by compiler's backend https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/ via `objdump` 📙 Erickson hacking [21]
* _instuction set_: pattern of bits/int/char that map to cmd https://en.wikipedia.org/wiki/Machine_code#Instruction_set https://steveklabnik.com/writing/is-webassembly-the-return-of-java-applets-flash
* _intermediate representation (IR)_: final step before machine code; handled by compiler's front end https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/
* _instruction_: individual line of machine code https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/
* _bytecode_: step after src but before IR? uses hex? https://www.youtube.com/watch?v=QU158nGABxI 23:55 🗄 `python.md` interpreter https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md injection https://stackoverflow.com/questions/3470949/what-is-java-bytecode-injection https://github.com/yiblet/inquest  https://docs.python.org/3/glossary.html#term-bytecode

* Conery ch. 10
* bytecode, control flow graphs (CFG) https://bernsteinbear.com/blog/discovering-basic-blocks/

types of compilation
* _just-in-time (JIT)_: https://eli.thegreenplace.net/2013/11/05/how-to-jit-an-introduction
* _ahead-of-time (AOT)_: https://news.ycombinator.com/item?id=22346540
* _adaptive_: quickening https://realpython.com/python311-new-features/#faster-code-execution https://github.com/brandtbucher/specialist

compilers
* _cc_: original compiler https://simonwillison.net/2022/Jan/30/a-cgo-free-port-of-sqlite/
* _gcc_: 
* _Clang_: 
* _LLVM_: https://aosabook.org/en/v1/llvm.html

compilation
* _compilers_: gcc, Clang, cl (MS) LLVM (from source to IR, then optimize IR http://aosabook.org/en/llvm.html)
* _output_: machine code ['Go in Practice' 18]
* _CLI options_: `Wall` warn all `-o` choose own name instead of a.out `std` spec
```sh
gcc foo.c -Wall -o my_program m -std='c99'
./my_program
```
* `.a`: lib whose code is embedded into your library
* `.so`: lib whose code is referenced by your library https://stackoverflow.com/a/9809250
* _header file_: imports

* _bootstrapping_: wrote core of compiler in another language and then use that core to build the rest of the compiler in the source language i.e. self-compilation https://softwareengineering.stackexchange.com/a/76640 https://stackoverflow.com/a/18126181
* _executable_: runtime + binary compatible with user os architecture
* for user's machine vs. your server https://testandcode.com/52 @ 29:00
* aka freeze in Python land https://docs.python-guide.org/shipping/freezing/

don't have good topic name for this yet
* _parser_: generates AST from src https://drewdevault.com/2018/12/28/Anatomy-of-a-shell.html https://astral.sh/blog/ruff-v0.4.0
* _AST_: src as tree https://sadh.life/post/ast/
* translate AST from c to Golang src https://simonwillison.net/2022/Jan/30/a-cgo-free-port-of-sqlite/
```python
def area_of_circle(radius):
    pi = 3.14
    return pi * radius * radius

area_of_circle(5)

                 (program)
                /         \
  (area_of_circle r)      (main)
  /           |             |
define    calculate        run area_of_circle
  pi        area             with r = 5
           /   |
     multiply  (pi, r, r)
```
* _grammar_: rules for language's AST https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework#parsing-the-code
* FFI parser https://scottlocklin.wordpress.com/2021/04/01/obvious-and-possible-software-innovations-nobody-does/
* FFI, JNI https://news.ycombinator.com/item?id=31353740
* _compilation target_: compilation fmt e.g. another lang (JS https://www.youtube.com/watch?v=3LWgbjVWLug 3:00) or binary (WASM) https://steveklabnik.com/writing/is-webassembly-the-return-of-java-applets-flash

times https://stackoverflow.com/q/846103
* _compile time_: compile code; err on static err (syntax, typing)
* _run time_: exec code; err on dynamic err (zero division, run out of mem)
* _import time_: exec code; leads to suble errors
> In Java, import foo means "I depend on the `foo` module; please have the virtual machine link me to it when I run." In Python, import `foo` means "look for `foo.py` in the path, execute it, store local variables in a module object, and assign that module to the `foo` variable in my scope." The difference is that the Python version can run essentially arbitrary code, including importing other modules which then import other modules in turn. https://www.benkuhn.net/importtime/

* linker https://news.ycombinator.com/item?id=27444647 https://gankra.github.io/blah/swift-abi/ 📙 Bryant (7)
https://web.eecs.utk.edu/~azh/blog/teenytinycompiler1.html

🗣 people to ask for help https://github.com/yiblet https://notes.eatonphil.com/starting-a-minimal-common-lisp-project.html
🔗 https://news.ycombinator.com/item?id=24066570
🔗 start here https://www.destroyallsoftware.com/screencasts/catalog
* hosted language: language using 3rd-party compiler (as Clojure uses JVM)
https://keleshev.com/compiling-to-assembly-from-scratch/ https://news.ycombinator.com/item?id=24609774

translators https://en.wikipedia.org/wiki/Symbol_table https://stackoverflow.com/a/3434252
* _assembler_: transform assembly to something less abstract, sometimes machine code and sometimes something a few levels up https://stackoverflow.com/questions/3434202/what-is-the-difference-between-native-code-machine-code-and-assembly-code/3434252#comment25665803_3434252
* _interpreter_: 
* _compiler_: transform high-level language to IR; 'self-hosting' is written in language it's compiling https://robertheaton.com/2017/10/24/what-is-a-self-hosting-compiler/

instructions
> where do virtual machines fit in this taxonomy? https://www.capitalone.com/tech/software-engineering/go-is-boring/
* _symbol table_: map of idenifiers (aka symbol) to type and scope https://en.wikipedia.org/wiki/Symbol_table#Example https://eli.thegreenplace.net/2010/09/18/python-internals-symbol-tables-part-1 https://drewdevault.com/2021/03/19/A-new-systems-language.html

implementations https://github.com/marcpaq/b1fipl
* make a Lisp https://news.ycombinator.com/item?id=21670442
* _JS_: https://github.com/jamiebuilds/the-super-tiny-compiler
* _Ruby_: Ruby Under a Microscope https://codon.com/compilers-for-free from Python https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/
* _Python_: https://bernsteinbear.com/blog/bytecode-interpreters/ https://ruslanspivak.com/lsbasi-part1/ http://www.aosabook.org/en/500L/a-python-interpreter-written-in-python.html http://www.thedigitalcatonline.com/blog/2017/05/09/a-game-of-tokens-write-an-interpreter-in-python-with-tdd-part-1/ https://github.com/danistefanovic/build-your-own-x#build-your-own-programming-language http://aosabook.org/en/500L/a-python-interpreter-written-in-python.html https://codewords.recurse.com/issues/seven/dragon-taming-with-tailbiter-a-bytecode-compiler http://www.trevorblackwell.com/#faq https://blog.miguelgrinberg.com/post/building-a-toy-programming-language-in-python https://mathspp.com/blog/building-a-python-compiler-and-interpreter
* _general_: https://www.youtube.com/watch?v=wSdV1M7n4gQ&t=157s + https://increment.com/programming-languages/crash-course-in-compilers/ + https://blog.wesleyac.com/posts/language-todos + https://blog.felixangell.com/compilers-brief-and-brisk + https://medium.com/basecs
* _Jit_ https://www.youtube.com/watch?v=2BB39q6cqPQ https://eli.thegreenplace.net/2013/11/05/how-to-jit-an-introduction
* _Ball_: src not in repo https://www.reddit.com/r/golang/comments/5eiiw6/writing_an_interpreter_in_go_now_available/ user impl https://github.com/mmyoji/go-monkey https://github.com/skatsuta/monkey-interpreter https://github.com/ELD/monkey-lang-go https://github.com/dnutiu/monkeyInterpreter
* _SQL_: http://aosabook.org/en/sqlalchemy.html

clean up
* mojo https://www.fast.ai/posts/2023-05-03-mojo-launch.html
* _compiled_: src type checked, then run
* _reference implementation_: primary implementation of language (CPython) as compared to other alternate implementations (PyPy, Jython)
* need to have same errors
> We crashed Oracle, including commercial versions of Oracle. We crashed DB2. Anything we could get our hands on, we tried it and we managed to crash it, but the point was that we wanted to make sure that SQLite got the same answers for all of these queries, or equivalent answers, because a lot of these queries, they’re indeterminate and the rows might come out in a different order because you [crosstalk 00:25:10] order by clause, so we wanted to make sure that all the database engines got equivalent answers. Mostly, we wanted to make sure that SQLite was getting the same answers everybody else is. https://corecursive.com/066-sqlite-with-richard-hipp/
* syntax trees https://eli.thegreenplace.net/2009/02/16/abstract-vs-concrete-syntax-trees https://www.pythonpodcast.com/episode-113-jedi-code-completion-with-david-halter/
* _interpreted_: src code run straight away
* _JIT_: normal interpreter but will compile hot paths https://carolchen.me/blog/jits-impls/
* _output_: assembly (for GCC) https://cs.stackexchange.com/questions/14749/why-do-compilers-produce-assembly-code
* writing language compiler in that language https://stackoverflow.com/questions/18247888/how-can-a-c-compiler-be-written-in-c
* _grammar_: syntax for programming language https://blog.robertelder.org/computer-science-for-engineers/
* https://github.com/aalhour/awesome-compilers http://steve-yegge.blogspot.com/2007/06/rich-programmer-food.html https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript https://medium.com/basecs https://ruslanspivak.com/lsbasi-part1/ https://nicoleorchard.com/blog/compilers https://github.com/jamiebuilds/the-super-tiny-compiler/blob/master/README.md http://aosabook.org/en/500L/static-analysis.html https://increment.com/programming-languages/crash-course-in-compilers/ https://corecursive.com/037-thorsten-ball-compilers/ https://news.ycombinator.com/item?id=22731505 https://www.pythoninsight.com/2018/09/python-basics-bytecode 

STEPS
* 📙 Conery 216
* _assemble_: convert from HLA to assembly
* _disassemble_: show assembly for HLA https://realpython.com/python311-new-features/#faster-code-execution https://florian-dahlitz.de/blog/disassemble-your-python-code 
```python
import dis
dis.dis(fn)
```
* _lex_: tokenize [Conery 218] https://www.aaronraff.dev/blog/how-to-write-a-lexer-in-go
* why it's split from parse https://news.ycombinator.com/item?id=35798829
* _lexical analysis_: https://docs.python.org/3/reference/lexical_analysis.html
* _parse_: 
* _semantic analysis_: 
* _optimization_: most of diff btw compilers is here [Conery 216] https://signalsandthreads.com/compiler-optimization/
* _code generation_: 
* _token_: atomic unit of significance
```python
tokens = {
    "variable": "foo",
    "operator": "=",
    "number": 10
}
```

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
* _branching factor_: degree of nesting in control flow 📙 Kleppmann 81 https://fivethirtyeight.com/features/what-if-trump-loses-and-wont-leave/
* _cyclomatic complexity_: number of linear paths through a problem i.e. how many if-else https://github.com/PyCQA/mccabe
> diff btw branching factor and cyclomatic complexity?

## functions

* _caller_: calls
* _callee_: is called https://nullprogram.com/blog/2019/06/30/

---

SEMANTICS https://realpython.com/python-pass-by-reference/#defining-pass-by-reference
* _function_: returns single obj https://www.youtube.com/watch?v=EnSu9hHGq5o 14:30
* _subroutine_: synonym for function https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/
* aka callable https://towardsdatascience.com/functools-the-power-of-higher-order-functions-in-python-8e6e61c6e4e4
> That process of going character by character can be wrapped up into a routine - also called a function, a method, a subroutine, or component. (Little in computing has a single, reliable name, which means everyone is always arguing over semantics.) - Ford what is code?

* _parameter_: spec for arg (number, order, type) https://www.fluentpython.com/lingo/#parameter
* _argument_: value passed to function https://www.fluentpython.com/lingo/#argument

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

## semantics

📜 https://docs.python.org/3/reference/index.html

UNITS
* _expression_: value + operator https://realpython.com/python-walrus-operator/#hello-walrus
* an eval to single value e.g. `y + 13` (number) `price > 0` (bool) 📙 Sweigart automate [14]
* _statement_: 动 an action e.g. function call (`logger.debug(ex)`) assignment (`x = 42`) https://beautifulracket.com/appendix/why-racket-why-lisp.html
* compositions of n expressions 📙 Haverbeke [ch.2]
* _block_: 名 group of statements

OPERATORS 📙 Nisan nand2tetris ch. 1-2
* _operand_: value used by operator
* _operator_: perform action
* _assignment_: =
* _conditional/ternary_: ?
* _logical/boolean_: and, or, not
* _equality_: ==, != 🗄 `python.md`
* SQL uses `=`
* _identity_: is 🗄 `python.md`
* _comparison_: >, < 📙 Bradshaw [55]
* _membership_: in

NAMES
* _identifier_: user defined name; aka 'symbol' https://en.wikipedia.org/wiki/Symbol_table#Example
* _keyword_: reserved and in use; getting shorter https://news.ycombinator.com/item?id=22474850 https://danluu.com/cli-complexity/
* _reserved_: not in use

VARIABLES
* _declare_: put var into namespace
* _initialize_: give var initial value
* _assign_: give var subsequent values; `TypeError: 'tuple' object does not support item assignment` supports the definition I've gleaned

ARITHMATIC
* _increment_: `++`
* _infix_: multiplication `*` exponentiation `**` https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/ 🗄 `python.md`
* += https://stackoverflow.com/a/7456548
