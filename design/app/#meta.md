# ⛩️

## 参考

📚
* ✅ Beck tidy first
* Mak https://www.manning.com/books/software-design-in-python
* Martin clean code
* ✅ Ousterhout philosophy of sofware design
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming 🗄️ Kernighan unix a history

# 🟨 ZA

* _coupling_: one change necessitates another
* _cohesion_: like w/ like 📙 Conery [270] Evans [109] https://entropicthoughts.com/event-sourcing-and-microservices-unix-style
> there should be low coupling btw modules and high cohesion within them 📙 Evans [109]
> Shovel all the manure into one pile. 📙 Beck tidy first [89]

---

* long boolean expressions https://www.pythonmorsels.com/refactoring-boolean-expressions/
* application boundaries, greppable https://morizbuesing.com/blog/greppability-code-metric/
* _separation of concerns_: HTML for content/semantics, CSS for style
* _code path_: branch through codebase
* _encapsulation_: modularity via objects/method https://www.youtube.com/watch?v=QyJZzq0v7Z4 24:00
```python
foo = 'foo val'
def get_foo():
    return foo
```
* _information hiding_: e.g. factories https://en.wikipedia.org/wiki/Information_hiding 📙 Evans domain-driven [139]
* _modules_: impl for cohesion 📙 Conery [270] Evans [109]
* _single responsibility_: from SOLID https://en.wikipedia.org/wiki/Single-responsibility_principle 📙 Raymond unix Buelta architecture [5]
* _separation of concerns_: cohesion re: to app layers (UI, logic, db, auth, logs) and business functions (content mgmt, reporting, membership) 📙 Conery [271]
* _fat model, skinny controller_: modularity around data access; != "all logic in model" http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/
* _Hungarian notation_: redundacy in identifier naming i.e. `CREATE TABLE tbl_book` instead of `CREATE TABLE book` https://www.sqlstyle.guide/#avoid
* _interface_: interface smuggling https://utcc.utoronto.ca/~cks/space/blog/programming/GoInterfaceSmuggling 🗄 `python` 'web'
* _introspection_: get info about an obj at runtime aka having a REPL https://realpython.com/primer-on-python-decorators/#simple-decorators aka 'reflection' https://changelog.com/gotime/133 also used as synonym for logging https://hacker-tools.github.io/machine-introspection/
* _modularity_: public interface, private impl https://www.youtube.com/watch?v=QyJZzq0v7Z4 @ 24:00
* _readability_: factors (familiarity, consistency) fetishization of one-liners (cf. Peter Norvig 'mine is shorter' from Crista Lopes talk on 'Exercises in Programming Style' @ 20:15)
> One of the core tenets behind the design of Python is creating readable code. The motivation behind this design is simple: The number one thing that Python programmers do is read code. [Hitchhiker's Guide 3.3]
> "A computer language is not just a way of getting a computer to perform operations...it is a novel formal medium for expressing ideas about methodology. Thus, programs must be written for people to read, and only incidentally for machines to execute." - Ford what is code? qt. SICP

https://buttondown.com/hillelwayne/archive/stroustrups-rule/
https://borretti.me/article/language-pragmatics

## comments

* for: what's not obvious 📙 Beck tidy first [29]
* not for: repeating what the code says 📙 Beck tidy first [31]

---

* https://news.ycombinator.com/item?id=43576425

## functional

🗄️
* `graphs.md` category theory
* `lisp.md` Haskell
📚
* ⭐️ Normand grokking simplicity https://www.manning.com/books/grokking-simplicity
* https://pragprog.com/titles/d-qtmart/the-art-of-functional-programming/
* Martin functional design https://www.amazon.com/gp/product/0138176396
* Plachta grokking functional https://www.manning.com/books/grokking-functional-programming

---

https://danluu.com/butler-lampson-1999/
https://us.pycon.org/2024/schedule/presentation/86/index.html
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

OBJECTS
* _object_: vs. procedural 📙 Evans domain-driven [51]
* _object model_: how objs work in a language; aka data model in Python 📙 Ramalho [15] BYO http://aosabook.org/en/500L/a-simple-object-model.html
* _metaobject_: objs that form core of object model 📙 Ramalho [16]
* _attribute_: obj property i.e. field (data) or method (action) https://docs.python.org/dev/tutorial/classes.html
* _attribute reference_: access obj attr https://docs.python.org/dev/tutorial/classes.html#class-objects

CLASSES
* _class_: lang ft. that allows defining new types 📙 Ramalho https://www.fluentpython.com/lingo/#class
* _abstract class_: specifies what methods need impl in child classes not instantiated; TwoDimensionalShape(Circle, Square, Triangle)
* _concrete class_: implements abstract class
```python
from abc import ABC, abstractmethod
class Shape(ABC):
    @abstractmethod
    def area(self): 
        pass
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return 3.14 * self.radius ** 2
```

INHERITANCE
* _inheritance_: subclass is an instance of parent class
> I use Django a lot and generally it's great. But I hate that you can't follow your code paths from start to finish on the surface. You have to know about how it works underneath. Meaning you can't just be a python + web server expert. You have to also be a Django expert. So I get non-Django experts reviewing code and they have no clue why things work or break. Just an opinion. Not saying this is objectively wrong. https://news.ycombinator.com/item?id=17728821

ZA
* _constant_: variable w/ hard-coded value
* _enumeration_: group of discrete constants https://realpython.com/python-enum/
* _member_: constant in enum

---

https://hynek.me/talks/subclassing/
SOLID https://realpython.com/solid-principles-python/

* _hierarchical_: 1 parent - 1 child
* _multi-level_: 1 grandparent - 1 parent - 1 child
* _multiple_: n parents - 1 child
* aka interfaces in Java, mixins in Python
* _polymorphism_: https://confuzeus.com/hub/django-web-framework/model-polymorphism/ https://news.ycombinator.com/item?id=27658706 re: duck typing https://www.fluentpython.com/lingo/#duck_typing
* _diamond problem_: https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem Python solves w/ MRO https://stackoverflow.com/a/44535084/6813490
* _Liskov_: every instance of a subclass (in this case, my extension of Thread) needs to remain a valid instance of the superclass
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
* CUPID https://dannorth.net/2022/02/10/cupid-for-joyful-coding/

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

## method chaining

💻 https://github.com/zachvalenta/capp-edi 

---

* https://news.ycombinator.com/item?id=43751076
> Minimizes the need for patterns like Decorator and Strategy by leveraging pure functions and higher-order functions.
https://calmcode.io/course/method-chains/introduction
```python
@cli.command()
def new_item():
    # doc = DocBuilder().add_isa_gs_st().add_bct('new item').add_products('new item').add_ctt_to_iea()
    # doc.write(SCENARIO_DIR / 'new-item.edi')
    doc = DocBuilder()
    doc.add_isa_gs_st()
    doc.add_bct('new item')
    doc.add_products('new item')
    doc.add_ctt_to_iea()
    doc.write(SCENARIO_DIR / 'new-item.edi')
```

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

## refactoring

📙 Fowler refactoring
> you can probably rm the PDF you have of this

---

> Analysis of the curl codebase: “It means that every line in the product source code tree have by now been edited on average 3.5 times.” https://registerspill.thorstenball.com/p/joy-and-curiosity-28

* _extract_: separate [Fowler https://refactoring.com/catalog/] 📙 Beck tidy first [75,83,85]
* _inline_: combine
> Inlining is the concept of replacing a function call in a program with the contents of the function itself, thus avoiding the call. https://golangweekly.com/issues/470
* DRY, single responsibility https://news.ycombinator.com/item?id=35151088
* _transform_: combine multiple functions into single [Fowler 14]
```python
# original
def do_this(thing):
def do_that(thing):

# transform
def do_this_and_that(thing):
    this(thing)
    that(thing)
```
* obj param [Fowler refactoring 40]
```python
# n params
def multi_args(foo_arg, bar_arg):
    do_foo(foo_arg)
    do_bar(foo_arg)

# obj param
def obj_args(obj):
    do_foo(obj.foo)
    do_bar(obj.bar)
```

## style

📙 Lopes exercises in programming style

---

https://seeinglogic.com/posts/visual-readability-patterns/

https://www.youtube.com/watch?v=JlPMOszyjjo&t=1566s https://news.ycombinator.com/item?id=16617039
> seems like she's conflated style (straight ahead, code golf) with design (objects)

* __straight ahead (3)__: no abstractions, lots of nesting, no return statements
* __code golf (6)__: fewest # of lines, leverage stdlib
* __cookbook (4)__: break everything into functions
* (10): Java encapsulation hell
* (30): map reduce

 [changing your mind](https://news.ycombinator.com/item?id=19288954) hedge fund managers do it https://www.theobservereffect.org/marc.html

* _imperative_: detailed; how; e.g. machine code, assembly
* _declarative_: less detailed; what not how; e.g. SQL, HTML [Kleppmann 2.44] just say what you want i.e. SQL leaves it to DBMS to implement; better for parallelism bc doesn't specify order [Kleppmann 2.43] Prolog in Python https://fedoramagazine.org/exploring-the-world-of-declarative-programming/

📝 diff btw imperative and delcarative is [diff of abstraction](http://itsadeliverything.com/declarative-vs-imperative-gherkin-scenarios-for-cucumber) but that diff ends up being a diff of type

cf. [Designing Data Intensive Applications - chapter 2 - 'delcarative queries on the web']

* _procedural_: group code into functions; C, Basic
* __object-oriented__: procedural on steroids; Java, C++
* __scripting__: functions not attached to objects
* __logic__: formal mathematical logic; Prolog https://news.ycombinator.com/item?id=30091291

## things I believe

Reabability is table stakes.

Simplicity takes time:

> A complex system that works is invariably found to have evolved from a simple system that worked. A complex system designed from scratch never works and cannot be patched up to make it work. You have to start over with a working simple system. https://news.ycombinator.com/item?id=42668065

Doctest: If someone can't start a REPL and run what's in your doctest, the code in question is failing.

Docstrings: If someone can't read a docstring and grok context, the code in question is failing.

Commit messages are held to the same standard as docstrings. If a PR to the main branch doesn't provide context, it will be declined.

Good integration tests are more important than unit test coverage.

Use small, composeable functions to create deep modules. 📙 Ousterhout philosophy of sofware design

[Centralize control flow.](https://matklad.github.io/2023/11/15/push-ifs-up-and-fors-down.html)

Semantics: naming things is hard. We'll refactor until we get it right. Bad semantics metastasize confusion and will not be tolerated.

> Get the nouns and verbs just right. Great names are the essence of great code, they capture what a thing is or does, and provide a crisp, intuitive mental model. They show that you understand the domain. Take time to find the perfect name, to find nouns and verbs that work together, so that the whole is greater than the sum of its parts. - [Tigerbeetle](https://github.com/tigerbeetle/tigerbeetle/blob/main/docs/TIGER_STYLE.md)

WHY PYTHON?
* It's the second-best language for many, many things.
* It's good for sketching:
> A programming language is for thinking of programs, not for expressing programs you've already thought of. It should be a pencil, not a pen. 📙 Paul Graham hackers and painters, page 22
* It's got a great ecosystem:
> The true measure of a language isn’t how it uses semicolons; it’s the standard library of each language. - [Paul Ford](https://www.bloomberg.com/graphics/2015-paul-ford-what-is-code/)
> I think a lot of the advances that happen in programming languages in the next fifty years will have to do with library functions. I think future programming languages will have libraries that are as carefully designed as the core language. Programming language design will not be about whether to make your language strongly or weakly typed, or object oriented, or functional, or whatever, but about how to design great libraries. The kind of language designers who like to think about how to design type systems may shudder at this. It's almost like writing applications! Too bad. Languages are for programmers, and libraries are what programmers need. - [Paul Graham](http://paulgraham.com/popular.html)

PYTHON LIBRARIES
* testing: pytest
* HTTP: httpx
* file paths: Pathlib
* CLI: Click
* output: rich
* dataframes: Polars
* numerical: jax
* classical ML: scikit
* stats/econ: scipy
* NLP: spacy
* algebra: sympy

* Prefer to use single quotes.
* Don't use typing unless it's crucial to the problem at hand i.e. we're fixing some code that is currently failing due to an issue that stronger typing would solve.
