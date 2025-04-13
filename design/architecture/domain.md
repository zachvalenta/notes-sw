# ⛩️

## 参考

🔗 https://en.wikipedia.org/wiki/Domain-driven_design
📚
* ✅ Evans domain-driven design https://github.com/nickgerace/gfold/pull/149/files
* Percival https://www.amazon.com/gp/product/1492052205 https://www.youtube.com/watch?v=niMybnzmzqc [1:15]

## 进步

* _25_: own note
* _23_: Evans
* _22_: United Masters

# 🕋 DOMAIN DRIVEN (DDD)

> restore Evans in bookcase
> then clean this up
> then start from ## basics and distribute Evans where necessary

ZA
* CRD DDD 🗄 notebook 22.12.13
* beware ideas coming from the Java world https://www.infoq.com/presentations/8-lines-code-refactoring/
> Ubiquitous language, domain, bounded context, aggregate, event storming are all about problem space. They are meant to help us learn the insights about the domain and extract the boundaries. DDD enables developers, domain experts and business people to communicate effectively using a single, unified language. Rather than focusing on these problem space aspects of DDD, we tend to emphasise particular folder structures, services, repositories, and other solution space techniques. https://minds.md/zakirullin/cognitive

SEMANTICS
* _separation of concerns_: HTML for content/semantics, CSS for style
* _code path_: branch through codebase
* _cohesion_: put like with like 📙 Conery [270] Evans [109] https://entropicthoughts.com/event-sourcing-and-microservices-unix-style
* _coupling_: "there should be low coupling btw modules and high cohesion within them" 📙 Evans [109] https://www.youtube.com/watch?v=MM9VQp-k0JQ
* one change necessitates another
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

HOWTO
* development speed vs. execution speed https://bitfieldconsulting.com/golang/rust-vs-go
> One especially good groove to span is the one between tools and things made with them. For example, programming languages and applications are usually written by different people, and this is responsible for a lot of the worst flaws in programming languages. I think every language should be designed simultaneously with a large application written in it, the way C was with Unix. http://paulgraham.com/marginal.html
> Part of the problem here is social. Language designers like to write fast compilers. That's how they measure their skill. They think of the profiler as an add-on, at best. But in practice a good profiler may do more to improve the speed of actual programs written in the language than a compiler that generates fast code. Here, again, language designers are somewhat out of touch with their users. They do a really good job of solving slightly the wrong problem. http://paulgraham.com/popular.html
* expressive
> Large organizations have different aims from hackers. They want languages that are (believed to be) suitable for use by large teams of mediocre programmers-- languages with features that, like the speed limiters in U-Haul trucks, prevent fools from doing too much damage. Hackers don't like a language that talks down to them. Hackers just want power. http://www.paulgraham.com/javacover.html
* _feature creep_: adding more features vs. making existing features better https://twitter.com/random_walker/status/1182635589604171776
* increases headcount, not total users https://news.ycombinator.com/item?id=34567237
> Second, C has a tendency to be conservative, changing and growing very slowly. This is a feature, and one that is often undervalued by developers. (In fact, I’d personally like to see a future revision that makes the C language specification smaller and simpler, rather than accumulate more features.) - https://nullprogram.com/blog/2018/11/21/

https://entropicthoughts.com/practices-of-reliable-software-design
extensible https://pycon-archive.python.org/2024/schedule/presentation/78/index.html
* application boundaries https://morizbuesing.com/blog/greppability-code-metric/
* Richard Gabriel https://www.jwz.org/doc/worse-is-better.html https://bitfieldconsulting.com/posts/not-real-developer
> Simplicity beats even strict correctness, in this view: it’s better to be simple (and handle the easy 90% of cases in a nice way) than to be totally correct (and handle the awkward edge cases, at the expense of making the code much more complex).

## basics

tactical vs. strategic https://claude.ai/chat/50e0f262-0f86-43e0-8fc3-f33f80dcee83
entity / aggregate / repository / data mapper/ CQRS / Active Record / event sourcing https://claude.ai/chat/38b933dd-801a-4827-8794-7126b445f943
strategy pattern vs. repository https://claude.ai/chat/65dda4b1-ff8b-44fd-be95-ec754cc78086

---

REPOSITORY
* CRUD module 📙 Evan [151]
repository pattern would abstract data access behind a consistent interface
├── Repository: data access abstraction 🗄️ `sql.md` schema / approaches
├── Factory
├── Aggregate
└── Entity

## in Django

---

* 💻 https://github.com/zachvalenta/django-DDD https://grok.com/chat/95d5f5bc-e490-4a0f-b8e8-a8b6eafcf884
> I think the move is to 1) clean up the `development` dir in `kern` 2) put the concerns about Django to an LLM and get opinions based on the current approach in `kern`
* Evans https://github.com/zachvalenta/bookcase-sjk/blob/master/notes/non-fiction/dev/svc/2003%20evans%20-%20domain%20driven%20design.md
> sketch things you need to understand more from these LLMS
* https://claude.ai/chat/61e85fd7-a33f-43e7-989f-7295de72845b -> https://claude.ai/chat/53ccf574-253a-4b55-ac3f-69cb877cd63e
* https://chatgpt.com/c/67e15081-a4f8-8004-86ab-9db58ca5b111 https://claude.ai/chat/812e936c-e2d0-4bfd-a403-8dfacf7a57a0
* https://claude.ai/chat/92bdb3e8-c87f-484c-8821-fbb7b2d4800f
* https://grok.com/chat/8513a2e6-8c8a-42f3-883b-05668fe08054 https://grok.com/chat/33a41760-ce83-4dc0-af25-1c7219736aed
* https://www.cosmicpython.com/book/appendix_django.html#_steps_along_the_way
* Percival, Django as Active Record https://news.ycombinator.com/item?id=43501989 Architecture Patterns for Python https://neil.computer/notes/teaching-how-to-code-is-broken/
* https://forum.djangoproject.com/t/where-to-put-business-logic-in-django/282 https://www.cosmicpython.com/book/appendix_django.html#_steps_along_the_way
* hating Django https://lucumr.pocoo.org/2025/2/20/ugly-code/
* in python https://www.pythonpodcast.com/episodepage/domain-driven-design-episode-219

* existing impl? https://claude.ai/chat/92bdb3e8-c87f-484c-8821-fbb7b2d4800f https://claude.ai/chat/812e936c-e2d0-4bfd-a403-8dfacf7a57a0
> what's that Python project that prevents circular dependencies, among other things?
> Let's say you have a custom piece of logic that touches models A, B, C, and D. Where do you put it? The idea is to let your domain live separately from your data model & API layer. https://github.com/HackSoftware/Django-Styleguide
* https://www.youtube.com/watch?v=72V-5hrilv0
* https://news.ycombinator.com/item?id=33999191

## Evans

---

incorporate Thomas notes

SEMANTICS
* _domain_: business logic https://www.youtube.com/watch?v=dlCcnJdh4c4 [1:15]
* _domain model_: data model [xvii]
* just data modeling? [84]
* holds business logic [71]
* the domain is the thing = the db is what matters = data eng! [70]
* the hard part of software [xxi]
* extends through all parts of project, to all team members [4]
* dependent on writing culture [16]
* could be non-OO e.g. Prolog [119]
* _ubiquitous language_: attention to semantics [xviii,25] https://tools.ietf.org/html/rfc2119
* have to 1) have documents that use the langauge 2) involve them in project activities [39]
* the hard part is sticking to it [26]
> It takes fastidiousness to write code that doesn't just do the right thing but also says the right thing. [40]
* a form of linguistic determinism [27]
> Translation muddles model concepts. [24]
* entire thing premised on having a dictionary [31]
* diagrams aren't helpful without semantics [35]
* _layered architecture_: UI, transport, service, repo/domain, db [68,70] 🗄 notebook 22.12.13
* vs. hexagonal, onion, microkernel https://blog.europython.eu/kraken-technologies-how-we-organize-our-very-large-pythonmonolith/
* or, transport, logic, messaging [107]
* separation of concerns [69]
* infrastructure = not db, but sending msgs? [73]
* _entity obj_: e.g. person, account
* e.g. transactions [92]
* has identity, diff states [81,91]
* _value obj_: e.g. enum
* e.g. values of transactions [92]
* attr [81]
* _aggregate_: entity + other associated obj [126] e.g. car is aggregate and wheel, tires, engine are associated obj [127]
* _service_: verb vs. noun [104]
* _factory_: creates other obj [138]
* _specification_: business logic [223,282]

STYLE
* anondyne: "talk to domain experts" [14] encapsulate [19]
* bizarre use of bolding [61]
* bizarre use of capitalization [62]
* diagrams gone wrong [65]
* poor writer [73,82]
* unclear writer [91] e.g. the main topic of section he defines 10 paragraphs in [126,138]
* semantics that are not in the index [147,151]
* dated e.g. 4GL https://en.wikipedia.org/wiki/Fourth-generation_programming_language [77,78]

ZA
> Hard to tell whether this book Norman-esque / curse of knowledge or reputational alá Finegan's Wake. The biggest impact I've seen it have is ubiquitous language.
* _CQRS_: diff svc for read/write https://martinfowler.com/bliki/CQRS.html https://ownyourbits.com/2018/05/02/understanding-disk-usage-in-linux/
* _pub sub_: 📙 Thomas pragmatic programmer [158]
* _event sourcing_: pub sub but more https://chriskiehl.com/article/event-sourcing-is-hard 📙 Thomas pragmatic programmer [160]
* aka event-driven? Components communicate through events. Publishers emit events without knowledge of subscribers.
* same probelm as Norman, ideas have won?
* background: agile [xxii] object-oriented [xxvi,51,87] Java oriented (back cover blurb) [74,111]
* event storming https://www.lucidchart.com/blog/ddd-event-storming https://www.youtube.com/results?search_query=event+storming
* ch. 7-9: examples
* https://www.packtpub.com/product/domain-driven-design-with-golang/9781804613450
* https://everydaysuperpowers.dev/articles/what-is-event-sourcing-and-why-you-should-care/
> Event sourcing is an architectural pattern for software development that has two components: To change the state of the application, you save the data associated with that change in an append-only log. The current state of an item is derived by querying the log for related events and building the state from those events.
> However, these two components are the core of event sourcing. I’ve seen people include eventual consistency, CQRS, and event streaming in their definitions of event sourcing, but these are optional additions to the pattern.
* _domain-driven design_: ❓ seems to boil down to "do things sensibly" (cf. 'bounded context') Evans 'Domain-Driven Design' Folwer 'Patterns of Entreprise Architecture' https://www.pythonpodcast.com/domain-driven-design-episode-219/
> Let’s for a moment talk about what all microservices have in common. Eric Evans, the father of Domain Driven Design, defines them as the following: "[services] that can consume and produce messages."

## Percival

# 💡 IDEAS

## DSLs

📙 Boersma https://www.manning.com/books/building-user-friendly-dsls

---

* lose tooling of general purpose language https://news.ycombinator.com/item?id=22375721
* https://news.ycombinator.com/item?id=41938819
* https://registerspill.thorstenball.com/p/joy-and-curiosity-12
* https://news.ycombinator.com/item?id=41931507

ABSTRACTION
* https://jesseduffield.com/Beginners-Guide-To-Abstraction/
* howto https://tonsky.me/blog/dsl/
* against abstraction https://thorstenball.com/blog/2015/10/22/write-stupid-code/
* _law of leaky abstractions_: natch; if they wouldn't exist in the first place https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/

## bounded context

---

💻️ https://github.com/zachvalenta/DDD

Same term ("Order"), different meanings in each context.
* Order Management Context: An "Order" contains items, prices, shipping info
* Inventory Context: An "Order" is just a reservation of stock
* Customer Support Context: An "Order" includes communication history

Why not just have an order and they each context uses whatever info they need?

The problem with having a single "Order" that all contexts use:
* Complexity explosion - The Order model would need to satisfy all teams' requirements, creating a bloated entity with many unrelated attributes
* Coupling - A change for one team affects all teams
* Cognitive load - Developers would need to understand the entire model, not just their relevant portion
* Conflicting requirements - What if Inventory needs to track Order status differently than Customer Support?

A Real Example
Consider how "Order completion" differs by context:

Order Management: Complete when payment processed
Inventory: Complete when items shipped
Customer Support: Complete when return period ends

These aren't just different views - they're fundamentally different business concepts with the same name.

## data mapper

* https://www.sqlalchemy.org/
* https://github.com/tommyboytech/t3/pull/11906
* https://en.wikipedia.org/wiki/Data_mapper_pattern#Python
* https://www.youtube.com/watch?v=oaiwS5KFHEs
* https://www.openmymind.net/2011/11/18/I-Just-Dont-Like-Object-Mappers/
* https://www.js-data.io/docs/data-mapper-pattern
* https://www.codeproject.com/articles/821803/data-mapper-pattern
* https://codingwithscott.com/how-to-implement-the-data-mapper-design-pattern-in-c/
* https://designpatternsphp.readthedocs.io/en/latest/Structural/DataMapper/README.html
* https://martinfowler.com/eaaCatalog/dataMapper.html

## rule encapsulation

* modular https://github.com/gauge-sh/tach https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/ https://github.com/gauge-sh/tach/issues/665
> A Python tool to enforce a modular, decoupled package architecture. tach allows you to define boundaries and control dependencies between your Python packages. Each package can define its public interface. If a package tries to import from another package that is not listed as a dependency, tach will report an error. If a package tries to import from another package and does not use its public interface, with strict: true set, tach will report an error. Zero runtime impact. https://pythonbytes.fm/episodes/show/384/force-push-lightly
* https://claude.ai/chat/61e85fd7-a33f-43e7-989f-7295de72845b
* https://claude.ai/chat/525e681b-a645-4eb9-a56f-1b51cf5fbccf
* existing rules `ECLIPSE_DISCONTINUED` https://github.com/cappusa/product-workflow/commit/711be5d67fc9f2ee9b30670971ea4dbe9a72f6a2

## value objects

https://claude.ai/chat/53ccf574-253a-4b55-ac3f-69cb877cd63e

# 🗼 MODERN

---

CQRS: Command/query separation
Unit of Work: Transaction management

A key insight is that many patterns solve similar problems in different contexts. For example, both Strategy and Command encapsulate behavior, but Command adds undo/logging capabilities. Similarly, both Decorator and Chain of Responsibility compose behavior, but Chain focuses on request handling while Decorator is more general.

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

## method chaining

💻 https://github.com/zachvalenta/capp-edi 

---

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
