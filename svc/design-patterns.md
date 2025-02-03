# ⛩️

## 参考

📚
* Beck tidy first?
* Conery ch. 11/12
* Dibernardo 500 lines http://aosabook.org/en/index.html
* Fowler refactoring 🎗️ PDF
* GoF design patterns
* Mak https://www.manning.com/books/software-design-in-python
* Martin clean code
* Nystrom http://gameprogrammingpatterns.com/contents.html
* Ousterhout philosophy of sofware design

## 进步

* https://neetcode.io/courses/lessons/8-design-patterns
* https://www.youtube.com/watch?v=tAuRQs_d9F8

* _25_: factory
* _24_: builder for EDI at Capp
* _23_: 📙 Evans domain-driven

* fanout https://www.better-simple.com/django/2023/12/06/fanout-pattern-explained/
* the big ball of mud https://news.ycombinator.com/item?id=35481309
* _strangler fig_: you run the old code and new code live, in production, side-by-side, checking that the new code behaves exactly the same as the old code. Once you are confident it does, you retire the old code https://www.kosli.com/blog/how-to-strangle-old-code-using-python-decorators/ https://news.ycombinator.com/item?id=41423421

> Some practices are the best when applied to a rewrite, but the worst when you’re still exploring. https://thorstenball.com/blog/2022/05/17/professional-programming-the-first-10-years/

https://developers.soundcloud.com/blog/end-of-the-strangler

* _strangler fig_: https://developers.soundcloud.com/blog/end-of-the-strangler
* _builder_ https://github.com/kayak/pypika
* _proxy_ https://rednafi.github.io/digressions/python/2020/06/16/python-proxy-pattern.html

as red flag https://news.ycombinator.com/item?id=30675182

* entity component https://akkartik.name/post/programming-2024
* _design patterns_: ❓ inherently OOP? [Conery 236]
* _adapter_: wrapper e.g. ORM class for Postgres, MySQL, et al. [Conery 249] https://bitfieldconsulting.com/golang/adapter
* _bridge_: allows you to update abstraction w/breaking impl i.e. yet another layer of abstraction [Conery 250]
* _decorator_: wrapper [Conery 254]
* _facade_: wrapper [Conery 255]
* _flyweight_: storage for other obj to use, cuts down on memory usage 📙 Conery [257] Evans [100]
* can use when shared obj is immutable, shared memory, when you really need to save space 📙 Evans [101]
* _mediator_: obj passing msg btw two other obj [Conery 261]
* _observer_: obj that listens to events from another obj
* _strategy_: pass algo at runtime i.e. `charge(normal_price)` or `charge(half_off)`
* _template method_: https://startcodingnow.com/template-method-design-pattern
* _visitor_: https://martinheinz.dev/blog/90

* _sink_: https://github.com/kamranahmedse/design-patterns-for-humans https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745
* in python https://python-patterns.guide/ https://hynek.me/articles/python-subclassing-redux/

# 🏭 CREATIONAL

ABSTRACT FACTORY
* families of related objects
* Provides an interface for creating families of related or dependent objects without specifying their concrete classes
* Example: UI toolkit that can create buttons, checkboxes, etc., for different platforms

PROTOTYPE
* cloning existing objects
* Creates new objects by copying an existing object (cloning)
* Example: Creating new documents by duplicating a template document

## ✅ factory

💻 https://github.com/zachvalenta/capp-edi

TYPES
* _factory_: don't have to know product impl 📙 Evans domain-driven [139] GoF [107]
```python
DocBuilder().add_products('new item')
class ProductFactory:
    def create_segments(self, scenario_type, product_index=0):
        scenarios = {
            'new item': self._new_item,
            'pricing': self._pricing,
            'lead time': self._lead_time
        }
        return scenarios.get(scenario_type)
    def _new_item(self, index):
        return [
            f"LIN*{index}*VP*{product['id']}~",
            f"G53*003~",
        ] 
    def _pricing(self, index):
        return [
            f"LIN*{index}*VP*{product['id']}~",
            f"G53*001~",
        ]
```
```python
@dataclass
class Burger:
    bun: str | None = None
    protein: str | None = None
    cheese: str | None = None
    toppings: list[str] | None = None
    sauce: str | None = None
class BurgerFactory:
    @staticmethod
    def custom(**kwargs):
        return Burger(**kwargs)
    @staticmethod
    def kahuna():
        return Burger(
            bun = 'Hawaiian',
            protein = 'beef',
            cheese = 'cheddar',
            toppings = ['onions', 'pineapple'],
            sauce = 'teriyaki',
        )
```

SEMANTICS
* _factory_: creator 📙 GoF [108]
* _product_: thing being created

---

TYPES
* _constructor_: 📙 Evans domain-driven [141]
* _abstract factory_: dedicated class to construct `CustomerFactory().default()` [Conery 243]

## ✅ builder

💻 https://github.com/zachvalenta/capp-edi

```python
class DocBuilder:
    def __init__(self):
        self.segments = []
        self.control_number = 'VG9M'

def add_isa_gs_st(self):
    self.segments.extend([f"ST*832*{self.control_number}~"])
    return self

def add_ctt_to_iea(self):
    self.segments.extend(["GE*1*1~", "IEA*1*000000001~"])
    return self

DocBuilder().add_isa_gs_st().add_ctt_to_iea()
```

## singleton

---

> dependency injection generally better?

* single instance
* class that only allows single instance of itself
* naive impl can go haywire in multithreaded env [Conery 248]

Singleton: Ensures a class has only one instance and provides a global point of access to it.
Example: A configuration manager that should have a single instance.

Problem it solves: Ensures only one instance of a class is created and provides a global point of access to it.
Use cases:
Managing database connections.
Configuration objects or environment settings.
Logging systems where multiple instances are redundant.
Caution: Can introduce global state and tight coupling, so use it sparingly.

# 🦠 STRUCTURAL

FACADE (simplified interface)
* Provides a simplified interface to a larger body of code or subsystem.
* Example: A home theater facade that controls various subsystems (TV, speakers, streaming service).

BRIDGE
* Bridge (separate abstraction from implementation)
* Bridge: Decouples an abstraction from its implementation so that the two can vary independently.
* Example: A device abstraction (TV/Radio) with a concrete implementation of different remote controls.

COMPOSITE
* Composite (tree structures of objects)
* Composite: Composes objects into tree structures to represent part-whole hierarchies.
* Example: File system directories and files where directories can hold files and other directories.

FLYWEIGHT
Flyweight (sharing for efficiency)
Flyweight: Reduces memory usage by sharing data between similar objects.
Example: Sharing font objects to avoid creating multiple identical instances.

PROXY
Proxy (controlled access)
Proxy: Provides a surrogate or placeholder to control access to another object.
Example: Proxy server for security, logging, or caching.

## adapter

Adapter (interface compatibility)

Adapter: Converts the interface of a class into another interface that clients expect.
Example: Adapter to make a legacy API compatible with new code.

## 📍 decorator

---

> pull in your timing function

Decorator (dynamic additional responsibilities)
Decorator: Dynamically adds behavior to an object without altering its structure.
Example: Adding features to a base coffee object (milk, sugar, caramel).

Problem it solves: Adds behavior to individual objects dynamically without changing the underlying class.
Use cases:
Adding logging, caching, or validation logic to functions or objects.
Extending UI elements with additional features (e.g., tooltips, borders).
Implementing middleware in HTTP frameworks (like Express or Flask).

# 🔍 BEHAVIORAL

Chain of Responsibility (request handling pipeline)
Command (requests as objects)
Mediator (loose coupling via coordinator)
Memento (capture/restore state)
State (behavior tied to state)
Template Method (skeleton algorithm)
Visitor (operations on elements)

## observer

Observer (one-to-many dependencies)
* _observer_: pub sub https://layerci.com/blog/postgres-is-the-answer http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/

> Reactive Programming: Handles event-driven programming, which may replace Observer patterns in modern reactive frameworks.

Problem it solves: Establishes a one-to-many relationship, allowing multiple objects (observers) to react to changes in a subject.
Use cases:
Event listeners (like user interface updates in real-time).
Publish-subscribe models (e.g., React components or webhooks).
Data synchronization between models and views in the MVC architecture.

## iterator

Iterator (sequential access)

## 📍 strategy

🗄️ `business.md` pricing
💻 https://github.com/zachvalenta/capp-brand-enablement

```txt
This is metaprogramming using Python's attribute lookup system. The repository pattern would abstract data access behind a consistent interface. This code dynamically selects IO methods based on the format parameter, which is closer to the Strategy pattern, but implemented through Python's reflection capabilities.

Core mechanics:
getattr() returns bound methods for different formats
String interpolation creates method names
Uniform method naming convention in polars enables this
```

Strategy (interchangeable algorithms)

Problem it solves: Enables swapping algorithms or behaviors dynamically at runtime.
Use cases:
Different sorting algorithms based on data size (e.g., quicksort vs. mergesort).
Multiple authentication strategies (e.g., OAuth, API key, password-based).
Managing discounts or pricing rules dynamically in an e-commerce system.

# 🗼 MODERN

---

Event-Driven Architecture: Loose coupling at system level
CQRS: Command/query separation
Unit of Work: Transaction management

A key insight is that many patterns solve similar problems in different contexts. For example, both Strategy and Command encapsulate behavior, but Command adds undo/logging capabilities. Similarly, both Decorator and Chain of Responsibility compose behavior, but Chain focuses on request handling while Decorator is more general.

## composition

WHY PREFERRED OVER INHERITANCE
* parent changes can require child update
```python
class Burger:
    def __init__(self, size='regular'):  # add size
        self.size = size
class BurgerFactory(Burger):
    def __init__(self):
        super().__init__()  # now child init needs to add as well
```
* you have to know about parent's implementation

---

* _composition_:
* Gang of Four: composition over inheritance https://en.wikipedia.org/wiki/Design_Patterns
> They warn that the implementation of a subclass can become so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change. Furthermore, they claim that a way to avoid this is to inherit only from abstract classes—but then, they point out that there is minimal code reuse...using inheritance is recommended mainly when adding to the functionality of existing components, reusing most of the old code and adding relatively small amounts of new code. https://buttondown.com/hillelwayne/archive/when-to-prefer-inheritance-to-composition/
* _delegation_: composition by another name https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/#delegation-in-oop
* https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/

## data mapper

📙 Fowler enterprise patterns

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

## dependency injection (DI)

🗄️ `python/logic.md` metaprogramming

---

Dependency Injection: Inversion of control
> Can sometimes replace patterns like Singleton and Factory by handling object lifecycles and dependencies.

https://www.openmymind.net/Dependency-Injection-In-Go/
* https://github.com/hynek/svcs/ https://svcs.hynek.me/en/stable/ https://www.youtube.com/watch?v=d1elMD9WgpA
* loose coupling https://www.youtube.com/watch?v=uWTvMCra-_Y
* https://github.com/uber-go/fx
* https://www.youtube.com/watch?v=uWTvMCra-_Y
* https://www.youtube.com/watch?v=0yc2UANSDiw
* _dependency injection_: passing args [Conery 282]
* why?: loose coupling http://kc.my-junk.info/di-ioc-dip https://www.youtube.com/watch?v=sD94szvFqGw
* https://blog.thea.codes/my-python-testing-style-guide/
* https://testdriven.io/blog/python-dependency-injection
* https://github.com/ZechCodes/Bevy
* https://hakibenita.com/python-dependency-injection
* https://romantomjak.com/posts/testing-python-code-that-makes-http-requests.html
* https://docs.pytest.org/en/latest/fixture.html#fixture
* https://github.com/google/gin-config https://calmcode.io/course/gin/intro-to-gin
* in Python https://io.made.com/dependency-injection-with-type-signatures-in-python/ + https://moltenframework.com/v0.7.3/index.html + https://github.com/ekiro/haps + https://github.com/Dobiasd/enterprython/blob/master/why_you_want_formal_dependency_injection_in_python_too.md https://pythonbytes.fm/episodes/show/112/don-t-use-the-greater-than-sign-in-programming
* _dependency inversion_: is this a separate thing https://minds.md/zakirullin/cognitive
* _inversion of control(IoC)_: you're not in charge of app control flow, only hooking into it https://www.baeldung.com/running-setup-logic-on-startup-in-spring example of IoC https://seddonym.me/2019/08/03/ioc-techniques/ https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way https://stackoverflow.com/questions/3058/what-is-inversion-of-control https://engineering.snagajob.com/dont-like-dependency-injection-898de93dc8d3 https://stackoverflow.com/a/2465052/6813490 https://stackoverflow.com/a/51117857/6813490 https://stackoverflow.com/a/140655/6813490 https://www.objc.io/issues/11-android/dependency-injection-in-java/ https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ ❓ pull in class deps all in one place [Conery 287]
> What is the glue that holds Django together? As a beginner entering, there really is no obvious central object to inspect, extend, or modify. https://www.reddit.com/r/Python/comments/olech/is_django_considered_pythonic_now/

## domain driven

📚
* ✅ Evans domain-driven design https://github.com/nickgerace/gfold/pull/149/files
* Percival https://www.amazon.com/gp/product/1492052205 https://www.youtube.com/watch?v=niMybnzmzqc [1:15]

├── Repository: data access abstraction 🗄️ `sql.md` schema / approaches
> 📍 you have same def for strategy pattern
├── Factory
├── Aggregate
└── Entity

* _separation of concerns_: HTML for content/semantics, CSS for style
> Let's say you have a custom piece of logic that touches models A, B, C, and D. Where do you put it? The idea is to let your domain live separately from your data model & API layer. https://github.com/HackSoftware/Django-Styleguide
* CRD DDD 🗄 notebook 22.12.13
* more domain-driven https://www.youtube.com/watch?v=72V-5hrilv0
* beware ideas coming from the Java world https://www.infoq.com/presentations/8-lines-code-refactoring/
> Ubiquitous language, domain, bounded context, aggregate, event storming are all about problem space. They are meant to help us learn the insights about the domain and extract the boundaries. DDD enables developers, domain experts and business people to communicate effectively using a single, unified language. Rather than focusing on these problem space aspects of DDD, we tend to emphasise particular folder structures, services, repositories, and other solution space techniques. https://minds.md/zakirullin/cognitive

## functional

🗄️
* `graphs.md` category theory
* `lisp.md` Haskell
📚
* ⭐️ Normand grokking simplicity https://www.manning.com/books/grokking-simplicity
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
* Hickey https://www.youtube.com/watch?v=oytL881p-nQ

## plugins

https://pluggy.readthedocs.io/en/stable/
https://docs.datasette.io/en/stable/plugins.html

```txt
Hollywood Principle: "Don't call us, we'll call you." The main application defines hook specifications, and plugins register themselves without the core application needing to know them in advance.

1. Observer: While not a strict observer pattern, Pluggy enables callbacks where plugins can react to hook calls, similar to event listeners
2. Strategy: Plugins act as replaceable strategies that modify or extend behavior at runtime.
3. Dependency Injection: The hook system allows late binding of behavior via plugins, which is a form of dependency injection (DI) but at an architectural rather than class level
4. Microkernel: aka Hexagonal/Ports & Adapters; applications using Pluggy can be structured as a minimal core (microkernel) with plugins extending functionality.

pytest uses Pluggy for its extensive plugin system.
tox and other tools use Pluggy for defining hooks that external tools can implement.
```

## reactive

RxPY: Full reactive streams, good for complex event flows, but heavy dependency
Asyncio: Built-in, lightweight, but more manual stream management
Callbacks: Simple but can lead to callback hell
Observers: Clean pattern but requires more boilerplate

```python
import asyncio
from typing import AsyncIterator

async def data_stream() -> AsyncIterator[int]:
    """Generate a stream of data.
    
    >>> async def print_stream():
    ...     async for item in data_stream():
    ...         print(item)
    ...         if item >= 3: break
    >>> asyncio.run(print_stream())
    1
    2
    3
    """
    count = 1
    while True:
        yield count
        count += 1
        await asyncio.sleep(0.1)

async def process_stream():
    async for item in data_stream():
        # React to each item
        result = item * 2
        print(f"Processed: {result}")
        if item >= 5:
            break

if __name__ == "__main__":
    asyncio.run(process_stream())
```

# 🟨 ZA

## cleanup

SEMANTICS
* _code path_: branch through codebase
* _cohesion_: put like with like 📙 Conery [270] Evans [109] https://entropicthoughts.com/event-sourcing-and-microservices-unix-style
* _coupling_: "there should be low coupling btw modules and high cohesion within them" 📙 Evans [109]
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

HOOKS
* _hook_: response to event e.g. db trigger
* aka event handler, callback 📙 Chacon [402] https://stackoverflow.com/a/11087727
* _webhook_: res/ack (vs. req/res); 3rd streams > 1st polls https://sendgrid.com/blog/whats-webhook
* route known as "receiver" https://adamj.eu/tech/2021/05/09/how-to-build-a-webhook-receiver-in-django/
* further considerations https://brandur.org/webhooks https://www.svix.com/blog/webhooks-are-harder-than-they-seem/

https://news.ycombinator.com/item?id=33999191
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

## paradigms

* use greppable names https://registerspill.thorstenball.com/p/use-data-that-looks-like-data
* write code that's easy to throw away
> Write code to be changed and/or deleted. This comes from someone who's worked in startups for the past 5 years. We often overestimate how long code =is supposed to live. We as programmers often exaggerate with our DRY and stuff, we do not want to repeat ourselves, we want to find another abstraction...we want to find some general that can help us abstract stuff away. My piece of advice is that, step back and consider for a moment that this code is not going to stay in, so maybe only try and find the abstraction layer once you really sure that this is how it's going to be. - Thorsten Ball https://developeronfire.com/podcast/episode-373-thorsten-ball-interpreters-compilers-and-writing https://news.ycombinator.com/item?id=41968409

---

https://drewdevault.com/2019/04/29/Shut-up-and-get-back-to-work-style.html

* hoisting

> This is what I’ve started telling people: Use mostly functions, try to make most of them pure. I think that can get people (even new devs) 80% of the benefits (testability, composability, loose coupling, and the ability to reason about code) of more complicated, prescriptive architectures (Hexagonal, Onion, Ports & Adapters, Clean, etc) with a minimal amount of ramp up. https://news.ycombinator.com/item?id=24915497

## refactoring

* _extract_: separate [Fowler https://refactoring.com/catalog/]
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
