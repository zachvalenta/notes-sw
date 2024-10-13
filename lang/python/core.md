# ⛩️

## 参考

📜 https://docs.python.org/3
🗣
* https://chat.stackoverflow.com/rooms/6/python
* https://www.youtube.com/@mCoding
📚
* Beazley cookbook
* Ramalho fluent https://github.com/fluentpython/example-code-2e/tree/master/01-data-model
> how to work through book: notebook | REPL + repo doctest
* Van Rossum tutorial

## 进步

* _24_: split from `python.md`, typing (exhaustiveness check, type narrowing)
* _23_: hashable
* _19_: imports, obj assignment, first pass (lambdas, dataclasses, shallow vs. copy, closure, decorator)
* _18_: Hitchhiker's Guide, first pass (imports, unit testing)
* _17_: PSF install, PS beginner course

# 📍 CLEAN UP

* https://treyhunner.com/2022/03/variables-objects-and-pointers-in-python/
* https://realpython.com/python-lazy-evaluation/
* https://www.pythonmorsels.com/cli-tools/
* initialize vs. construct, __init__, __new__ https://www.fluentpython.com/lingo/#initializer https://www.fluentpython.com/lingo/#constructor
attributes
* https://realpython.com/python-array/
* _property_: you can control `__get__`/`__set__`/`__delete` (whereas you cannot on attributes) https://stackoverflow.com/q/7374748
> name, reference count https://www.thepythoncodingstack.com/p/whats-in-a-name-python-namespace-objects-names
* kinds of attr: value, type, refcount (reference counting https://codeconfessions.substack.com/p/cpython-reference-counting-internals https://docs.python.org/3/glossary.html#term-reference-count https://signalsandthreads.com/memory-management/) https://realpython.com/pointers-in-python/#objects-in-python https://pythonspeed.com/articles/python-object-memory/ https://realpython.com/python-pass-by-reference/#passing-arguments-in-python https://realpython.com/python-pass-by-reference/#understanding-assignment-in-python
* _borrowed reference_: https://docs.python.org/3/glossary.html#term-borrowed-reference
* check if attr present with try/catch, don't use hasattr() https://hynek.me/articles/hasattr/
* https://docs.python-guide.org/writing/gotchas/#mutable-default-arguments
* dict keys to list + more unpacking https://stackoverflow.com/questions/33161448/getting-only-element-from-a-single-element-list-in-python#33161467
```python
[*dict]

# combine dicts https://stackoverflow.com/a/67450966
{**bar, **bar}
```
* https://rednafi.com/python/dataclasses_and_methods/
* library design https://benhoyt.com/writings/python-api-design/
* dataclasses, typing https://kobzol.github.io/rust/python/2023/05/20/writing-python-like-its-rust.html
* classes https://realpython.com/python-classes/
* protocols https://godatadriven.com/blog/protocols-in-python-why-you-need-them/ https://www.youtube.com/watch?v=xvb5hGLoK0A https://peps.python.org/pep-0544/ https://www.amazon.com/Architecture-Patterns-Python-Domain-Driven-Microservices/dp/1492052205 https://unitedmasters.atlassian.net/wiki/spaces/PROGRAM/pages/2379939844/2023-04-13+U+Sprint https://codebeez.nl/blogs/type-hinting-in-modern-python-the-protocol-class/
* https://lukeplant.me.uk/blog/posts/pythons-disappointing-superpowers/
* dictview, lru_cache https://death.andgravity.com/caching-methods namedtuple, frozen dataclasses, fractions over floats https://www.textualize.io/blog/posts/7-things-about-terminals multiset https://www.youtube.com/watch?v=b-K1ujf8u_k&pp=ygUQcHl0aG9uIGZyb3plbnNldA%3D%3D
* https://snarky.ca/tag/syntactic-sugar/ https://realpython.com/python-del-statement/ https://www.wrighters.io/intro-to-python-match-statement/
* enums https://realpython.com/python-enum/ https://florian-dahlitz.de/blog/why-you-should-use-more-enums-in-python

# 🗂 CLASSES

🗄 `language.md` object-oriented
📚
* Beazley ch. 7
* Ramalho ch. 1, 5, 11-14, 16, 22-24
* Van Rossum ch. 9 https://docs.python.org/dev/tutorial/classes.html

---

https://www.youtube.com/watch?v=5vpdzRbfTIM

SEMANTICS
* _attributes_: value tied to obj and accessed via dot notation https://docs.python.org/3/glossary.html#term-attribute
* data + methods 📙 Ramalho [839]
* _method_: callable attribute 📙 Ramalho [839]
* _data_: readable/writable attributes
* read via: dot notation, `dir()` (K) `vars()` (K-V)

DATA https://stackoverflow.com/questions/2714573/instance-variables-vs-class-variables-in-python
* _instance variable_: 
* _class variable_: 

TYPES https://blog.ionelmc.ro/2015/02/09/understanding-python-metaclasses/
* _metaclass_: parent of classes https://www.fluentpython.com/lingo/#metaclass https://eli.thegreenplace.net/2012/04/16/python-object-creation-sequence https://docs.python.org/3/glossary.html#term-metaclass
* used in Django https://news.ycombinator.com/item?id=22346964
* _class_: instance of metaclass https://docs.python.org/3/glossary.html#term-class
* _instance_: instance of class
```python
class Meta(type):
    pass
class Cls(metaclass=Meta):
    pass
type(Cls)  # <class '__main__.Meta'>
```

SYNTAX
```python
# declaration
class Foo(object):  # Python 2
class Bar:          # Python 3

# construction
alice = Human("alice")

# access
alice.name
```

* OOP
```python
# eh
class SomeView(BaseView):
  _foo_service = None
  @property
  def foo_service(self):
    if not self._foo_service:
      self._foo_service = factory.get_foo_service()
    return self._foo_service

# better
class SomeView(BaseView):
  @functools.cached_property
  def foo_service(self):
    return self._foo_service = factory.get_foo_service()
```

## dataclass

https://www.youtube.com/watch?v=vBH6GRJ1REM
* vs. defined https://www.youtube.com/watch?v=1S2h11XronA
> the most useful purpose is adding a certain degree of formalization to a group of values that need to be passed around. https://www.revsys.com/tidbits/dataclasses-and-attrs-when-and-why/
* `__repr__` and `__eq__` for free https://realpython.com/python-data-classes/
* faster access than `namedtuple` but worse mem usage https://stackoverflow.com/a/51673969
* convert dict to dataclass https://github.com/konradhalas/dacite

## descriptor

* https://www.youtube.com/watch?v=mMbVs17Vmo4
* https://docs.python.org/3/library/inspect.html#inspect.ismethoddescriptor https://docs.python.org/3/library/inspect.html#inspect.isdatadescriptor https://docs.python.org/3/library/inspect.html#inspect.ismemberdescriptor
* https://www.fluentpython.com/lingo/#descriptor https://docs.python.org/3/glossary.html#term-descriptor
> Descriptors provide the underlying magic for most of Python’s class features, including @classmethod, @staticmethod, @property, and even the __slots__ specification. By defining a descriptor, you can capture the core instance operations (get, set, delete) at a very low level and completely customize what they do. This gives you great power, and is one of the most important tools employed by the writers of advanced libraries and frameworks. 📙 Beazley 265
> Any method is actually a descriptor. https://www.fluentpython.com/lingo/#bound_method
* uniform acccess principle https://www.fluentpython.com/lingo/
* _attribute_: https://www.fluentpython.com/lingo/#EAFP https://www.fluentpython.com/lingo/#attribute
> other stuff on attributes scattered throughout note
* managed instance, managed class https://www.fluentpython.com/lingo/#managed_instance
* managed attribute https://www.fluentpython.com/lingo/#managed_attribute
* managed class https://www.fluentpython.com/lingo/#managed_attribute
* getter/setter https://realpython.com/python-getter-setter/
* storage attribute https://www.fluentpython.com/lingo/#storage_attribute
* (non)overriding https://www.fluentpython.com/lingo/#overriding_descriptor
* impl https://docs.python.org/dev/reference/datamodel.html#implementing-descriptors
* https://realpython.com/python-descriptors/#why-use-python-descriptors
* http://nbviewer.jupyter.org/urls/gist.github.com/ChrisBeaumont/5758381/raw/descriptor_writeup.ipynb
* https://sadh.life/post/descriptors/
* even the pros don't knwo much about them https://nedbatchelder.com/blog/201306/explaining_descriptors.html
* class that defines `__get__`, `__set__`?
* `__get__` enables for true encapsulation vs. name mangling https://www.youtube.com/watch?v=0hrEaA3N3lk
* https://docs.python.org/3/howto/descriptor.html 
* https://nedbatchelder.com/blog/201306/explaining_descriptors.html
* _fully persistent data structure_: Git works like this, can branch, can time travel
* _partially persistent data structure_: same as fully persistent except can only modify the most recent copy

## dunder

📚
* lang ref ch. 3-4
* Kettler magic  https://news.ycombinator.com/item?id=17727437
* Van Rossum ch. 9

---

https://mathspp.com/blog/case-insensitive-string-class
https://www.pythonmorsels.com/every-dunder-method/

* `__getattr__`: https://docs.python.org/3/glossary.html#term-attribute 
* `__setattr__`: https://docs.python.org/3/glossary.html#term-attribute 
* `__getattribute__` https://news.ycombinator.com/item?id=3719179

https://martinheinz.dev/blog/87 more introspection https://martinheinz.dev/blog/82

* getitem, iter, and/or, bool, getstate/setstate, repr https://books.agiliq.com/projects/Journeyman-Python/en/latest/magic-methods.html
* _call_: make class instance callable e.g. `foo = Foo(); foo()` https://realpython.com/python-class-constructor/ https://realpython.com/python-multiple-constructors/ re: metaclasses https://eli.thegreenplace.net/2012/04/16/python-object-creation-sequence
* _dict_: stores obj writable attributes https://docs.python.org/3/library/stdtypes.html#object.__dict__
* called by `vars()` https://docs.python.org/3/library/functions.html#vars

LIFECYLE
* _new_: thing that actually creates obj instance https://betterprogramming.pub/5-pairs-of-magic-methods-in-python-you-should-know-f98f0e5356d6 https://realpython.com/python-class-constructor/
* _init_: initializes obj https://realpython.com/python-multiple-constructors/ https://realpython.com/python-class-constructor/
* use `cls()` when you want a wrapper in front of this in a class constructor https://stackoverflow.com/q/24799403
```python
class Foo:
    def __init__(self, thing):
        result = lookup(thing)
        self.foo = result

foo = Foo(thing="hey")

# misdirection
class Foo:
    def __init__(self, foo):
        self.foo = foo

    @classmethod
    def get(cls, thing):
        result = thing.lookup(thing)
        return cls(foo=result)

Foo.get(thing="hi")
```
COMPARE
* __eq__: 📙 Ramalho [84,415]
* __hash__: returns int 📙 Ramalho [84,415] https://docs.python.org/3/reference/datamodel.html#object.__hash__
* usage: compare obj https://www.youtube.com/watch?v=opijuVoq3Kk 5:50
> the same logic as a conditional but just putting a bow on it
* called by `hash()`
* used by dict, set https://www.youtube.com/watch?v=opijuVoq3Kk 0:35
* set to `None` when underlying data structure is mutable https://www.youtube.com/watch?v=opijuVoq3Kk 3:15
* defaults to None when `__hash__` unimpl but `__eq__` impl https://www.youtube.com/watch?v=opijuVoq3Kk 0:25
* howto
```python
def __hash__:
    # no idea what xor is doing here, thought its output was boolean https://www.youtube.com/watch?v=opijuVoq3Kk 4:15
    return hash(self.foo) ^ hash(self.bar)
    # 📍 https://stackoverflow.com/questions/2909106/whats-a-correct-and-good-way-to-implement-hash https://stackoverflow.com/questions/4005318/how-to-implement-a-good-hash-function-in-python
```

FILES
```python
class UrOpener(object):
  def __init__(self, filename):
    self.file = open(filename)

  # enter = called when enter context (i.e. `with` block starts)
  def __enter__(self):
    return self.file  

  # exit = called when exit context (i.e. `with` block ends)
  # idk what extra 3 args do
  def __exit__(self, a,b,c):
    self.file.close()

with open ('sample-file.txt') as file:
  contents = file.read()
  print(contents)

with UrOpener('sample-file.txt') as file:
  contents = file.read()
  print(contents)
```

BASICS
* _dunder_: methods called by the interpreter 📙 Ramalho [3]
> When an object is passed to the str built-in function, its __str__ method is called. https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/
* _Python data model_: dunder methods as a framework called by the interpreter 📙 Ramalho [3,8]
> dunno if I agree with this semantic 🗄️ obj
* why: ubiquitous names for standard operations across stdlib and user-defined classes [6]
* used for: attribute access, iteration, operator overloading [4]
* documentation: language reference ch. 3 (data model) https://docs.python.org/dev/reference/datamodel.html#specialnames language reference ch. 4 (mapping types) https://www.fluentpython.com/lingo/#special_method "magic method"/"dunder" not in the docs 📙 Kettler https://docs.python.org/dev/reference/datamodel.html#specialnames https://www.fluentpython.com/lingo/#special_method https://docs.python.org/3/glossary.html#term-magic-method https://docs.python.org/dev/reference/datamodel.html#specialnames 📙 Ramalho [4]
> They're also not as well documented as they need to be. All of the magic methods for Python appear in the same section in the Python docs, but they're scattered about and only loosely organized. There's hardly an example to be found in that section (and that may very well be by design, since they're all detailed in the language reference, along with boring syntax descriptions, etc). 📙 Kettler https://rszalski.github.io/magicmethods/

## inheritance

---

```python
issubclass(bool, int)

# https://github.com/cosmologicon/pywat#circular-types 
isinstance(object, type)      # True
isinstance(type, object)  # True
```

* _abstract base class (ABC)_: https://www.fluentpython.com/lingo/ https://docs.python.org/3/glossary.html#term-abstract-base-class
* _virtual subclass_: https://www.fluentpython.com/lingo/ https://www.fluentpython.com/lingo/#constructor

MIXINS
* _mixin_: multiple inheritance of abstract class https://stackoverflow.com/a/15605119 https://www.fluentpython.com/lingo/#mixin_class
* _interface_: https://docs.python.org/3/faq/design.html#how-do-you-specify-and-enforce-an-interface-spec-in-python https://realpython.com/python-interface/ https://glyph.twistedmatrix.com/2021/03/interfaces-and-protocols.html https://www.youtube.com/watch?v=DqFspy9pI9k
* _sink_: https://www.ianlewis.org/en/mixins-and-python https://stackoverflow.com/a/52469499/6813490 https://www.residentmar.io/2019/07/07/python-mixins.html https://stackoverflow.com/questions/533631/what-is-a-mixin-and-why-are-they-useful mixins tutorial https://easyaspython.com/mixins-for-fun-and-profit-cb9962760556 https://stackoverflow.com/a/547714/6813490

* _sink_: https://www.youtube.com/watch?v=YXiaWtc0cgE https://realpython.com/inheritance-composition-python/ https://realpython.com/oop-in-python-vs-java/
* _inner class_: encapsulate something only relevant to enclosing class, stem proliferation of small modules https://stackoverflow.com/questions/719705/what-is-the-purpose-of-pythons-inner-classes

* super: call method from parent
```python
class Mammal():
    def __init__(self, name):
        print('{} is a warm-blooded animal'.format(name))
#############################3
class Dog(Mammal):
    def __init__(self):
        super().__init__('a dog')
```

```python
class Alice():
    def crawl(self):
        print('crawling')

class Bob():
    def walk(self):
        print('walking')

class Candace(Alice, Bob):
    def run(self):
        print('running')

c = Candace()
c.run()
c.walk()
c.crawl()
```

## methods

---

* virtual method https://stackoverflow.com/questions/622132/what-are-virtual-methods
* the use of class methods https://stackoverflow.com/a/38276/6813490
* https://stackoverflow.com/questions/22616559/use-cases-for-property-vs-descriptor-vs-getattribute
* bound method https://www.fluentpython.com/lingo/#bound_method
* _accessor_: https://www.fluentpython.com/lingo/#accessor

* _single underscore_: hint (not enforcement) of private method [tutorial 9.6] i.e. no access modifiers
* _name mangling_: https://www.fluentpython.com/lingo/

```python
# https://monadical.com/posts/operator-overloading-in-python.html
class Clock:
   def __init__(self, time: str):
       self.hour, self.min = [int(i) for i in time.split(':')]

   def __repr__(self) -> str:
       min = '0' + str(self.min)
       return str(self.hour) + ':' + min[-2:]
```

METHODS
| type      | called on | arg          | variable access | use case                                          |
|-----------|-----------|--------------|-----------------|---------------------------------------------------|
| instance  | instance  | instance     | instance, class |                                                   |
| class     | class     | class        | class           | factory                                           |
| static    | class     | user-defined | --------------- | just plain func namespaced to class; Ramalho [371]|
* _self_: parameter to instance method whose arg is instance itself https://martinheinz.dev/blog/81
* _cls_: parameter to class method whose arg is class itself
* impl via descriptor https://www.youtube.com/watch?v=ANLjBsWHshc
* just a naming convention https://stackoverflow.com/a/475919
* debate http://neopythonic.blogspot.com/2008/10/why-explicit-self-has-to-stay.html https://stackoverflow.com/q/2709821
* _property_: 
* 📙 Ramalho [839]
* call method same way you used access property/attr i.e. dot notation
* way to refactor field into method https://www.machinelearningplus.com/python/python-property/ https://stackoverflow.com/q/6618002/6813490
* uniform acccess principle https://www.fluentpython.com/lingo/
```python
# phase 1 - .fullname becomes inconsistent if other attr updated bc only set on init
class Person():
    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname
        self.fullname = self.first + ' '+ self.last

# phase 2 - works but a breaking change bc .fullname is now .fullname()
class Person():
    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname

    def fullname(self)
        return self.first + ' ' + self.last

# phase 3 - invoke method with same syntax as accessing property
class Person():

    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname

    @property
    def fullname(self)
        return self.first + ' ' + self.last
```

# 🌊 CONTROL FLOW

🗄 `language.md`
📙 Van Rossum ch. 4 https://docs.python.org/3/tutorial/controlflow.html

## conditionals

BRANCHING
```python
def if_example():
    if True:
        print("i will print")
    if True: # unaffected by exec of previous if statements https://stackoverflow.com/a/53545252
        print("i will also print")

```

MULTILINE
```python
if (
    'spam' in email['sender'] or
    'spam' in email['subject'] or
    'spam' in email['metadata']
    ):
else:
```

TERNARY
* hides branching from coverage https://406.ch/writing/how-ruff-changed-my-python-programming-habits/#flake8-simplify
```python
this() if x else that()
return True if x else False
var = foo if condition else bar
```

---

dictionary dispatch https://martinheinz.dev/blog/90

## exceptions

📚 Beazley ch. 14, Van Rossum ch. 8 https://docs.python.org/3/tutorial/errors.html https://www.b-list.org/weblog/2023/dec/11/python-exceptions/

SEMANTICS
* _handler_: `try` block
* _handled_: try/catch
* _unhandled_: no handler found

TYPES
* `Attribute`: attr doesn't exist or cannot be set
* `Index`: trying to access non-existent index; slices handle these in a weak way (i.e. type conversion)
* `Key`: dict doesn't have key you asked for
* `Name`: identifier not defined
* `Syntax`: kw misspelled, bad indentation, missing closing syntax
* `Type`: give wrong type to function, try to do something you can't (mutate string)
* `Value`: func given correct type but still err ex. `int('5')` can convert string to int but not for all strings e.g. `int('five')`

USER-DEFINED
* why: way to dedupe logging
* simple impl
```python
class EarthquakError(Exception): 
    pass
raise EarthquakError("earthquake!")
```
* fancier impl
```python
class EarthquakError(Exception): 
    def __init__(self, place):
        self.place = place
    def __str__(self):
        return f"earthquake at {self.place}"
raise EarthquakError(place)
```

---

* warnings, subclasses https://lerner.co.il/2020/04/27/working-with-warnings-in-python/
* 📙 tutorial ch 8 stdlib ch 5
* approach: EAFP (forgivness > perm i.e. try-catch) better than LBYL (C-style if-else) https://docs.python.org/3/glossary.html#term-EAFP
* https://realpython.com/courses/python-exceptions-101/
* https://sobolevn.me/2019/02/python-exceptions-considered-an-antipattern
* https://news.ycombinator.com/item?id=19133948
* swallow msg: https://stackoverflow.com/a/52625133/6813490

## matching

```python
match result[0]:
    case "foo":
    case "bar":
    case "baz":
```

---

* https://www.youtube.com/watch?v=ASRqxDGutpA
* https://martinheinz.dev/blog/78
* switch statement on steroids https://benhoyt.com/writings/python-pattern-matching/ https://peps.python.org/pep-0634/
> An if...elif...elif...sequence is a substitute for the switch or case statements found in other languages. https://docs.python.org/3/tutorial/controlflow.html
* subject https://www.fluentpython.com/lingo/#subject
* _switch statement replacements_: bisect https://stackoverflow.com/a/61030734/6813490 https://www.youtube.com/watch?v=gllUwQnYVww https://github.com/ralsina/enum_switch https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://docs.python.org/3/faq/design.html#why-isn-t-there-a-switch-or-case-statement-in-python

## try/catch

---
* multiple exceptions https://realpython.com/python-catch-multiple-exceptions/
* https://github.com/guilatrova/tryceratops
* control flow: don't go nuts with it https://blog.cerebralab.com/Exceptions_as_control_flow
```python
# CONTROL FLOW
try:
    pass
except SpecificException as e:
    logger.exception(e)
    raise
else: 
    # only for the happy path
finally:
    # no matter what happens

# PASS TO CALLER https://stackoverflow.com/a/34622772
def raiser():
    try:
        do_something()
    except ValueError as err:
        logger.exception(err)
        raise  # https://stackoverflow.com/a/24065533

for el in li:
    raiser()
except Exception as err:
    logger.exception(err)
```

# 🤖 FUNCTIONS

📚
* Beazley ch. 7
* Ramalho ch. 7, 9-10

BUILT-IN 📜 https://docs.python.org/3/library/functions.html https://www.youtube.com/watch?v=7Qu_KXc7xSI https://www.mattlayman.com/blog/2024/layman-guide-python-built-in-functions/
* _all_: return True if iterable empty or all el true
* _dir_: list obj attr
* _next_: call `__next__`
* _type_: calls `obj.__class__`
* _vars_: list obj attr; calls `__dict__`

---

* multiple dispacth / multimethods https://martinheinz.dev/blog/50
* mixs usage of "parameter" and "argument" https://www.fluentpython.com/lingo/#parameter

* _argument_: https://docs.python.org/3/glossary.html#term-argument
* _pass_: implicit return of `None`
* _return_: implicit return of `None` if no other return defined
> A Python function will always have a return value. There is no notion of procedure or routine in Python. https://realpython.com/python-return-statement/#implicit-return-statements
* multimethod, generic function https://www.fluentpython.com/lingo
* callable object https://www.fluentpython.com/lingo/#function

## args

* functions maintain order of args passed sinced Python 3.6 https://treyhunner.com/2018/04/keyword-arguments-in-python/#Order_matters

FIXED
* _positional_: arg matched to param by sequence
* positinal-only `def bar(/, x)` https://www.youtube.com/watch?v=R8-oAqCgHag
* _keyword_: arg matched to param by name
* must follow positional
```python
foo("hey", "there")      # positional
foo(y="there", x="hey")  # keyword
```

VARIADIC
* _*args_: variable number of positional args
* kw-only after
```python
def foo(*args, kw):
def bar(x, *, kw):  # alternate syntax https://www.youtube.com/watch?v=R8-oAqCgHag https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/#Keyword-only_arguments_without_positional_arguments https://realpython.com/python-asterisk-and-slash-special-parameters/
```
* _**kwargs_: variable number of keyword args
* used in: OO https://stackoverflow.com/a/1415882 stdlib https://treyhunner.com/2018/04/keyword-arguments-in-python/#Where_you_see_keyword_arguments
* https://realpython.com/python-kwargs-and-args/#passing-multiple-arguments-to-a-function https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/#Asterisks_for_packing_arguments_given_to_function
```python
def foo(**kwargs):
    if "isrc" in kwargs.keys():
        print(kwargs["isrc"])
```

PREFIX OPERATOR
* _prefix operator_: used for packing/unpacking https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/ 📍 https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/#Asterisks_in_list_literals https://www.youtube.com/watch?v=R8-oAqCgHag https://bas.codes/posts/python-asterisks
* _packing_: caputure all positional/keyword args and put into list/dict
* _unpacking_: iterate over list/dict https://www.fluentpython.com/lingo/#tuple_unpacking
* _parallel assignment_: https://www.fluentpython.com/lingo/#parallel_assignment
```python
# packing on function declaration
def bar(**kwargs):
# unpacking on function invocation
myd = dict(magic=32, larry=33)
"{magic} {larry}".format(**myd)
```

DEFAULT
* must follow positional/keyword
* _early-bound_: evaluated at function definition https://rednafi.github.io/reflections/gotchas-of-early-bound-function-argument-defaults-in-python.html
* evaluated only once so use `None` over empty list https://news.ycombinator.com/item?id=29682785

## functional

---

* https://docs.python.org/3/howto/functional.html
* https://realpython.com/python-functional-programming/ 
* https://github.com/pytoolz/toolz
FUNCTOOLS https://florian-dahlitz.de/articles/introduction-to-pythons-functools-module https://pybit.es/articles/6-cool-things-you-can-do-with-the-functools-module/
* _partial_: create callable by wrapping another callable w/ default args http://pymotw.com/2/functools/
* closure for a function vs. just a value
> we created a new callable that will always pass the `file=sys.stderr` keyword argument to print, allowing us to simplify our code by not having to specify the keyword argument every time. https://towardsdatascience.com/functools-the-power-of-higher-order-functions-in-python-8e6e61c6e4e4 
```python
from functools import partial
import sys
print_stderr = partial(print, file=sys.stderr)
print_stderr("This goes to standard error output")
```
* _reduce_: sum over list comprehension https://stackoverflow.com/a/16632125 https://realpython.com/python-reduce-function/ https://martinheinz.dev/blog/93
```python
from functools import reduce
from operator import mul
nums = [1, 2, 3]
reduce(mul, nums)  # 6
```

## inner / closures

🗄 functools/partial

https://www.youtube.com/watch?v=jXugs4B3lwU
* _closure_: closes around value on stack to preserve in mem after stack finishes 
```python
def generate_power(number):
    def nth_power(power):
        return number ** power
    return nth_power

# use this example
# https://stackoverflow.com/a/141426/6813490 https://www.pythonmorsels.com/using-counter/
def counter():
    count = 0
    def count()
```

* _inner_: sans closure doesn't seem particularly useful re: encapsulation https://stackoverflow.com/a/4020443/6813490 https://realpython.com/inner-functions-what-are-they-good-for/#encapsulation
```python
def outer(num):
    def inner_increment(num):
        return num + 1
    return inner_increment(num)
```

## lambdas

https://www.youtube.com/watch?v=fZE6ZWde-Os
https://www.pythonmorsels.com/lambda-expressions/
https://lwn.net/Articles/964839/
* https://docs.python.org/3/glossary.html#term-lambda
* _anonymous_: don't assign a name https://treyhunner.com/2018/09/stop-writing-lambda-expressions/
* _constraints_: only for expression i.e. no iteration, conditions https://wsvincent.com/python-lambda-expressions/
* _sink_: https://zenhack.net/2016/12/25/why-python-is-not-my-favorite-language.html https://realpython.com/python-lambda/ https://philip-trauner.me/blog/post/python-quirks-lambdas

__use cases__

* avoid a throwaway function definition

```python
colors = ["Goldenrod", "Purple", "Salmon", "Turquoise", "Cyan"]

# bad
def normalize_case(string):
    return string.lower()

normalized_colors = map(normalize_case, colors)

# better --> keep in mind, use list comprehensions instead of either map or filter
list(map(lambda x:x.upper(), colors))
```

* `key` function

```python
"""
MAX
-> https://www.youtube.com/watch?v=EnSu9hHGq5o&__s=kznp9q3qiibqzd9qjf12 @ 12:15 https://mathspp.com/blog/max-is-broken
"""
tall_buildings = {'Empire State': 381, 'Sears Towers': 442, 'Burj Khalifa': 828}
max(tall_buildings.keys())  # 'Sears Towers'
max(tall_buildings.values())  # 828
max(tall_buildings.items(), key=lambda b: b[1])  # ('Burj Khalifa', 828)

"""
SORTED
-> https://treyhunner.com/2018/09/stop-writing-lambda-expressions/
"""

colors = ["Goldenrod", "Salmon", "purple", "turquoise", "cyan"]
sorted(colors, key=lambda s: s.lower())  # ['cyan', 'Goldenrod', 'purple', 'Salmon', 'turquoise']
sorted(colors, key=lambda c: (len(c), c.lower()))  # can also use tuple for combinatorial i.e. sort by length and then, if tie in length, use lexicographical (lowercased)
```

## metaprogramming

📜 https://docs.python.org/3/library/language.html
🗄 `language.md` design / metaprogramming
📚
* Beazley ch. 9
* Ramalho ch. 22-24

---

* https://dev.to/karishmashukla/a-practical-guide-to-metaprogramming-in-python-691
* Flask debugger, typing, metaprogramming vs monkey patching https://news.ycombinator.com/item?id=34611969
* _metaprogramming_: functions that manipulate existing code e.g. decorators, inspection 📙 Beazley 329
* also synonym for process (build tools, dep mgmt) https://missing.csail.mit.edu/2020/metaprogramming/
* in Ruby (Perrotta) https://news.ycombinator.com/item?id=24935242 

* _meta programming_: function that takes some other code, wraps it, and returns https://medium.com/@saurabhkukade_96600/meta-programming-in-python-7fb94c8c7152

DECORATORS
* _decorator_: factory + functionality https://www.fluentpython.com/lingo/#decorator https://jcarlosroldan.com/post/329/my-latest-tils-about-python
* https://www.fluentpython.com/lingo/#decorator https://docs.python.org/3/glossary.html#term-decorator https://www.bitecode.dev/p/xmas-decorations-part-3
* use cases
```python
# logging

# caching

# sanitization

# app config https://bytepawn.com/python-decorators-for-data-scientists.html

# execeptions https://dev.to/fcurella/refining-exceptions-with-context-decorators-31i5

# login https://realpython.com/primer-on-python-decorators/#a-few-real-world-examples

# pagination https://stackoverflow.com/questions/53638221/unable-to-handle-two-links-having-different-pagination-using-decorator
```
* https://bas.codes/posts/python-decorators
* https://suyogdahal.com.np/posts/how-decorator-crashed-my-flask-app/
* https://blog.luisrei.com/articles/flaskrest.html
* https://stackoverflow.com/questions/308999/what-does-functools-wraps-do
* https://samireland.com/writing/decorators/ https://rednafi.github.io/digressions/python/2020/05/13/python-decorators.html
* _decorator_: factory that takes func and adds functionality via inner function; introduced in 2.4 via PEP 318
* _basics_: https://realpython.com/primer-on-python-decorators/#a-few-real-world-examples https://www.youtube.com/watch?v=MjHpMCIvwsY
* _factory_: https://joeriksson.io/blog/Decorator-with-arguments/ https://realpython.com/inner-functions-what-are-they-good-for/#conclusion https://stackoverflow.com/a/28695034/6813490 https://www.learnpython.org/en/Decorators https://stackoverflow.com/questions/10957409/python-naming-conventions-in-decorators https://realpython.com/inner-functions-what-are-they-good-for/#conclusion https://zenhack.net/2016/12/25/why-python-is-not-my-favorite-language.html

* pre-2.4
```python
def my_decorator(func):
    def wrapper():
        print(f"my_decorator is wrapping {func}")
        func()
    return wrapper

def use_decorator():
    print("calling use_decorator")

use_decorator = my_decorator(use_decorator)
```

* syntactic sugar https://realpython.com/primer-on-python-decorators/#simple-decorators
```python
def my_decorator(func):
    def wrapper():
        print(f"my_decorator is wrapping {func}")
        func()
    return wrapper

@my_decorator
def use_decorator():
    print("calling use_decorator")
```

* decorator that can handle the decorated functions args
```python
def my_decorator(func):
    def wrapper(*args, **kwargs):  # wrapper takes function args just like my_decorator takes function itself
        print(f"my_decorator is wrapping {func}")
        func(*args, **kwargs)
    return wrapper

@my_decorator
def use_decorator(name):
    print(f"calling use_decorator with args {name}")
```

* decorator w/ introspection
```python
import functools

def my_decorator(func):
    @functools.wraps(func)
    def wrapper():
        print(f"my_decorator is wrapping {func}")
        func()
    return wrapper

@my_decorator
def use_decorator():
    print("calling use_decorator")
```

# 🕉 OBJECTS

📙 Ramalho ch. 6

* _object_: https://docs.python.org/3/glossary.html#term-object
* _object model_: everything inherits from `object` as of Python 2.2 https://www.youtube.com/watch?v=vvuYPUbwAO0 2:30 https://docs.python.org/3/reference/datamodel.html
* everything is an object, which means tons of allocations and therefore GC
> A massive number of memory allocations (malloc) and a significant amount of time spent on garbage collection. This is when ‘everything is an object’ really bites you. https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust

---

* _callable_: any obj that impl `__call__` e.g function, method, classes e.g. `MyClass()` https://eli.thegreenplace.net/2012/03/23/python-internals-how-callables-work https://www.fluentpython.com/lingo/#callable_object https://www.pythonmorsels.com/class-function-and-callable/ https://docs.python.org/3/glossary.html#term-callable
* _key function_: for callables https://docs.python.org/3/glossary.html#term-key-function
* _destructuors_: https://eli.thegreenplace.net/2009/06/12/safely-using-destructors-in-python

* immortal https://engineering.fb.com/2023/08/15/developer-tools/immortal-objects-for-python-instagram-meta/
* get class name from obj `foo.__class__.__name__`
> gets entire functionality from this attribute https://martinheinz.dev/blog/103
* comparison operators 🗄 `language.md` semantics
```python
# isinstance -> type
isinstance(False, bool)  # True

# `is` -> identity (same obj) 🗄 'assignment'
a = "hey"
b = a
a is b  # True
b is a  # True

# `==` -> equality (same val); SimpleNameSpace does this as well https://treyhunner.com/2019/03/python-deep-comparisons-and-code-readability/
x = [1,2,3]
y = [1,2,3]
id(x)  # 4567741704
id(y)  # 4567723016
x == y  # True
x is y  # False
```

---

* _None_: is a singleton https://www.fluentpython.com/lingo/#singleton

* _sink_: https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc 📙 tutorial chapter 9, Hitchhiker's Guide 3.1.7, https://zenhack.net/2016/12/25/why-python-is-not-my-favorite-language.html https://realpython.com/python3-object-oriented-programming/ https://www.youtube.com/watch?v=epKegvx_Jws https://realpython.com/python38-new-features/#more-precise-types https://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/ + https://www.hackerfactor.com/blog/index.php?/archives/825-8-Reasons-Python-Sucks.html https://www.youtube.com/watch?v=mUu_4k6a5-I object types https://medium.com/@meghamohan/mutable-and-immutable-side-of-python-c2145cf72747 https://apirobot.me/posts/lets-talk-about-data-structures-in-python https://kite.com/blog/python/python-dictionaries

obj
* PyObject is base obj class for CPython, impl as C struct https://realpython.com/pointers-in-python/#names-in-python
* _representation_: tldr always impl `__repr__` bc it will be used by both `str()` and `repr()`; longer answer is that if you do impl both `__repr__` is expected to be more detailed and (logging) `__str__` more readable (debugging) https://realpython.com/courses/pythonic-oop-string-conversion-__repr__-vs-__str__/ https://stackoverflow.com/a/2626364
* _temporary_: holds another name's value https://docs.python.org/2.4/lib/weakref-extension.html https://www.quora.com/What-is-temp-in-c-programming
```python
# everything is an obj (var, fun, class, modules)
isinstance(1, object)

# components: 
sys.getrefcount('abc')  # 43 (idky so many; bpython cache? vanilla Python interpreter displays different, lower number)
hey = 'abc'
sys.getrefcount('abc')  # 44
```

## garbage collection

> port to `language.md`

* weakref https://martinheinz.dev/blog/112
* _garbage_: memory occupied by obj no longer in use
* _garbage collection_: scheduled memory management
* _why?_ other wise you'd run out of memory; easier than manual, but can be slower
* can turn off for performance improvements https://talkpython.fm/episodes/show/265/why-is-python-slow 42:00
* how to fit a lot of data in memory https://pythonspeed.com/articles/data-doesnt-fit-in-memory/
* _sink_: https://docs.python.org/3/faq/design.html#how-does-python-manage-memory https://docs.python.org/3/faq/design.html#why-doesn-t-cpython-use-a-more-traditional-garbage-collection-scheme https://docs.python.org/3/faq/design.html#why-isn-t-all-memory-freed-when-cpython-exits https://docs.python.org/3/faq/design.html#why-isn-t-all-memory-freed-when-cpython-exits https://pythonspeed.com/articles/function-calls-prevent-garbage-collection/ https://dev.to/karishmashukla/how-python-uses-garbage-collection-for-efficient-memory-management-270h

* _when?_
```python
# unbind name from obj

x = 1000  # int obj created w/ value of 1000
x = 500  # creates new int obj, re-points `x` at new obj

# delete variable, class instance

y  = [2,3,5]
del y

# local var goes out of scope

def foo(param):
    bar = [1,2,3]  # will be gc'd
    return param
```

* `__del__()`: aka finalizer; method called when `del` called against obj/var; meant for cleaning up memory, not doing other code cleanup (use `with` instead) [4:00]

## memory

🗄
* `architecture.md` memory
* `language.md` memory

BASICS
* _object_: underlying value
* get size `sys.getsizeof(obj)`
* _name_: way to refer to obj
* aka object reference https://nedbatchelder.com/text/names.html
* _aliasing_: multiple names bind to same obj https://docs.python.org/dev/tutorial/classes.html#a-word-about-names-and-objects see shallow copy https://www.fluentpython.com/lingo/#deep_copy https://www.fluentpython.com/lingo/#alias https://www.fluentpython.com/lingo/#aliasing
> better explanation https://chatgpt.com/share/66e87aa9-bd44-8004-ad6b-79a7e73853d7
```python
def view_obj(obj):
    print(id(obj))

myo = 1
id(myo)        # 4300357872
view_obj(myo)  # 4300357872
```

---

* https://docs.python.org/3/glossary.html#term-__slots__
* https://pythonspeed.com/articles/json-memory-streaming/
* https://martinheinz.dev/blog/68
* https://realpython.com/python-memory-management/
* https://pythonspeed.com/memory/
* https://www.moderndescartes.com/essays/data_oriented_python/

* _assignment_: bind name to obj https://realpython.com/copying-python-objects/ https://eloquentjavascript.net/03_functions.html
```python
###
# WALRUS
# combine assignment w/ another operatation https://martinheinz.dev/blog/79
##

foo = 'foo val'  # w/out walrus, have to do next operation (print, whatever) in another statement
print(foo := 'foo val')  # can combine assignment w/ another statement

# makes for easier control flow https://realpython.com/python-pass-by-reference/#creating-conditional-multiple-return-functions
if (temp_var := foo_func()) is not None:
    another_func(temp_var)

###
# PACKING
# *return* n obj in single statement
###

def multiple_return():
    return 1, 2  # tuple

###
# UNPACKING
# *assign* n obj in single statement 📙 Beazley 1
###

t = multiple_return()  # tuple
for k, v in  # type depends on iterable

# can unpack iterable to single name
l_in_l = [1, [42, 13, 99]]
a, b = l_in_l
a  # 1
b  # [42, 13, 99]

# cannot unpack n el to single name
my_l = [42, 13, 99]
a, b = my_l
Traceback (most recent call last):
  File "<input>", line 1, in <module>
    a, b = my_l
ValueError: too many values to unpack (expected 2)

# used to replace hard-coded indices w/ asterisk/star operator https://mathspp.com/blog/pydonts/unpacking-with-starred-assignments https://mathspp.com/blog/pydonts/deep-unpacking
# splat operator https://stackoverflow.com/a/48451275
sys.argv[0], sys.argv[1:]
program_name, *arguments = sys.argv

# used to replace hard-coded indices
date = timestamp.split('/')
print(f'{date[2]}-{date[0]}-{date[1]}')
month, day, year = timestamp.split('/')
print(f'{year}-{month}-{day}')
```

* _reassigment_: rebind name to new obj https://realpython.com/python-pass-by-reference/#understanding-assignment-in-python
```python
# assignment evaluated right to left i.e. can swap (just another form of packing) https://docs.python.org/3/reference/expressions.html#evaluation-order
a, b = b, a
# can do for multiple https://stackoverflow.com/a/31111801
l = list('cat')
l[0:1], l[1:3] = l[1:3], l[0:1]

bl = 42
bl = 13  # new int obj created for 42 (as opposed to updating value of int obj already created for 13)
id(bl)  # 4304845696

bar = [0]
bar = [0, 1]  # diff obj

# versus performing operation on existing obj
foo = [0]
foo.append(1)  # same obj
```

* _interning_: 🗄 `language.md` https://realpython.com/pointers-in-python/#a-note-on-intern-objects-in-python -> don't understand his first example in this section
```python
# ✅ pre-created immutable obj are interned (ints 0-256)
hey = 13
hi = 13
hi is hey  # True

# ❌ non-pre-created immutable obj are not interned 
hey = 257
hi = 257
hi is hey  # False

# ✅ strings under 20 char and only containing char/int/underscores are interned
x = "hey"
y = "hey"
x is y  # True

# ❌ strings over 20 char or not containing char/int/underscores are not interned
x = "hey!"
y = "hey!"
x is y  # False

# 🎗 can force interning with sys.intern() https://docs.python.org/3/library/sys.html#sys.intern useful for speeding dict lookup bc interned obj will be compared using memory address, not value https://realpython.com/pointers-in-python/#a-note-on-intern-objects-in-python
import sys
x = sys.intern(x)
y = sys.intern(y)
x is y  # True

# ✅ mutable obj can be interned if names are transitively bound
hey = [1, 2, 3]
hi = [1, 2, 3]
hi is hey  # False
hello = hey
hello is hey  # True

# ⚠️ mutable obj updated for all bound names https://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/
foo = [1, 2, 3]
bar = foo
bar[0] = 42
foo  # [42, 2, 3]
```

## typing

🗄 `language.md` typing

* _exhaustiveness check_: check that functions handle newly-added attributes on their args https://news.ycombinator.com/item?id=25428583
* _type narrowing_: issue warning if src tries to operate on type that args cannot be passed on blocks's previous code https://hakibenita.com/python-mypy-exhaustive-checking

---

* _type annotation_: Python 3, PEP 484 https://blog.zulip.org/2016/10/13/static-types-in-python-oh-mypy/
```python
def greeting(name: str) -> str:
    return f"hello, {}"
```
* mypy can check both annotation and comments
* _type comments_: alternative to annotations for Python 2 https://realpython.com/lessons/type-comments/
```python
def my_func(arg):
    # type:(str) -> str
    return arg

my_variable = 42  # type: int

# not available in `__annotations__`
func.__annotations__
# {}
```

---

PYDANTIC
* throw err if typing mismatch https://hackernoon.com/pydantic-what-it-is-and-why-its-useful https://talkpython.fm/episodes/show/466/pydantic-performance-tips
* https://realpython.com/python-pydantic/
* https://fastapi.tiangolo.com/python-types/
* https://www.pythonpodcast.com/pydantic-data-validation-episode-263/
* https://github.com/shopnilsazal/validus
* https://blog.couchbase.com/validate-json-documents-in-python-using-pydantic/
* https://talkpython.fm/episodes/show/466/pydantic-performance-tips

> you probably know my skepticism towards Python typing. This stems from the syntax's complexity, the sluggishness of mypy, the overall cumbersome nature of its implementation and awkwardness of interactions with it...in a way in some areas we are creating the new Java. We became the people we originally displaced. Just that when we are not careful we are on a path to the world's worst Java. We put typing on a language that does not support it, our interpreter is slow, it has a GIL. We need to be careful not to forget that our roots are somewhere else. We should not collectively throw away the benefits we had. https://lucumr.pocoo.org/2023/12/1/the-python-that-was/

multiple returns https://realpython.com/python-type-hints-multiple-types/
https://realpython.com/python-type-self/
https://lukeplant.me.uk/blog/posts/the-different-uses-of-python-type-hints/

ANNOTATIONS
* _annotation_: https://docs.python.org/3/glossary.html#term-annotation
* _function annotation_: https://docs.python.org/3/glossary.html#term-function-annotation
* _variable annotation_: https://docs.python.org/3/glossary.html#term-variable-annotation

* _generic type_: https://docs.python.org/3/glossary.html#term-generic-type
* https://terokarvinen.com/2022/python-dotted-dictionary/
* https://realpython.com/python311-new-features/#improved-type-variables
* history https://www.fluentpython.com/lingo/#type
* https://realpython.com/python311-new-features/#improved-type-variables
* boxing https://www.moderndescartes.com/essays/data_oriented_python/ https://en.wikipedia.org/wiki/Object_type_(object-oriented_programming)#Boxing https://stackoverflow.com/questions/13055/what-is-boxing-and-unboxing-and-what-are-the-trade-offs
* _dummy version_: `isinstance`
* type hints introduced in PEP 484 https://www.python.org/dev/peps/pep-0484/
* mypy vs. pyright https://news.ycombinator.com/item?id=37914146 https://rdrn.me/postmodern-python/
* _libs_: mpypy (PSF) PyRight (Microsoft) https://github.com/Microsoft/pyright pyre (Facebook) https://pyre-check.org/ pyannotate (Dropbox i.e. Python 2) https://github.com/dropbox/pyannotate MonkeyType (Instagram i.e. Python 3 https://github.com/Instagram/MonkeyType https://www.pythonpodcast.com/monkeytype-with-carl-meyer-and-matt-page-episode-146/
* _sink_: https://talkpython.fm/episodes/show/151/gradual-typing-of-production-applications https://www.youtube.com/watch?v=mh9jQSxzv0c https://inventwithpython.com/blog/2019/11/24/type-hints-for-busy-python-programmers/ https://veekaybee.github.io/2019/07/08/python-type-hints/ https://blog.petrzemek.net/2019/02/22/even-feature-that-you-do-not-use-can-bite-you/


mypy https://mypy.readthedocs.io/en/stable/getting_started.html#installing-mypy
* _impl_: looks at AST, doesn't run src
* changes versions too frequently https://news.ycombinator.com/item?id=26814919
* trade-offs: write a bit more code but read a lot less; more code but simpler (vs. Java tower of abstractions in type graph); prevents drift btw method sig and impl (esp. after refactor); seems easier/better to use at the start of a project (although, gradual typing given as a main use case; tbh, idk)
* debugging, best practices https://calpaterson.com/mypy-hints.html
* _Any_: mypy catch-all type for anything it can't do type inference on https://calpaterson.com/mypy-hints.html
* _Optional_: can return None (or another value)
* `typing.cast`: tell mypy that you know better than it does https://calpaterson.com/mypy-hints.html
```python
def get_config_value(key: str): Optional[str]:
    # Either return the config value, or None if it's not present
```

# 🟨 ZA

UNDERSCORES https://dbader.org/blog/meaning-of-underscores-in-python
* https://github.com/darrenburns/ward/tree/master/ward
* _single_: placeholder for throwaway values from unpacking
* in REPL, refers to result of last operation
* _single leading_: won't be imported in `from <mod> import *` https://stackoverflow.com/a/8689983
* _single trailing_: break naming conflict
* _double leading_: name mangling i.e. measure to prevent accidental overrides
* _doubled_: dunder methods

---

* soft keywords https://mathspp.com/blog/til/pythons-soft-keywords

## ecosystem

📜 https://docs.python.org/3/faq/design.html

DESIGN
* history: origins in ABC https://www.fluentpython.com/lingo/#ABC
* readabillity: indentation for statement grouping via significant white space vs. semi-colons https://news.ycombinator.com/item?id=34936023
* simplicity: `python -m this` https://peps.python.org/pep-0020/ https://xkcd.com/353/
* pain points: binaries, import system, version management, packaging, browser, native (mobile, desktop), speed (not built for multi-core https://twitter.com/mitsuhiko/status/1091802711908106240)

USAGE 💡 second-best for everything
* teaching: Jupyter
* web: Django, Flask, FastAPI
* sys admin: Ansible, scripting
* ML: data science, pytorch
* security: network hacking, scraping
* microcontrollers
* industrial automation https://www.pythonpodcast.com/episode-114-industrial-automation-with-jonas-neubert/
* finance https://www.openbb.co/
* architecture https://talkpython.fm/episodes/show/342/python-in-architecture-as-in-actual-buildings
* GPU simulation https://news.ycombinator.com/item?id=40680737
* game engine https://github.com/kitao/pyxel https://github.com/Broderick-Westrope/tetrigo
* browser https://www.youtube.com/watch?v=Vh77_2-Z0vc

GOVERNANCE
* corporate: internal language team at Google https://news.ycombinator.com/item?id=40176338
* quasi-official: PyPA, PyCQA
* people: Donald Stuft (PyPA) Raymond Hettinger (core) Tim Peters (Zen of Python `import this`, Timsort) Armin Ronacher (Flask) Brett Cannon (core) Nick Coghlan (core) Eli Bendersky (Google, buddies w/ Coghlan) https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* core contributor https://mariatta.ca/posts/perks-of-python-core/
* _Steering Council_: https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* _PSF_: https://simonwillison.net/2024/Sep/18/board-of-the-python-software-foundation/

STDLIB
* new batteries in Rust https://baincapitalventures.com/insight/why-more-python-developers-are-using-rust-for-building-libraries/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* how libs get in https://github.com/hukkin/tomli/issues/141#issuecomment-997999824

PEPS https://peps.python.org/
* _0_: establish what a PEP is
* _8_: style guide
* _20_: Zen of Python
* _387_: no promise of backwards comptability https://news.ycombinator.com/item?id=26826158

## operators

🗄️ `language.md` semantics / operators
🔗 https://github.com/cosmologicon/pywat

PRECEDENCE
* https://www.thepythoncodingstack.com/p/python-operator-precedence-after-you-no-i-insist
* anything in parentheses executed first https://stackoverflow.com/a/10034611
* AND has higher precedence than OR

https://realpython.com/python-assert-statement/

RETURN
* _pass_: results in NOP https://wsvincent.com/python-pass-statement/
* returns neither True nor False

OPERATORS 🗄 `philosophy.md` logic `language.md` semantics
* _not_: opposite of operand
```python
not True   # false
not False  # true
```
* _and_: true if both input true else false
```python
# true
True and True
# false
False and False
True and False
False and True
```
* _or_: true if one of operands true
```python
# false
False or False
# true
True or False
False or True
True or True
```
* _xor_: true if only one of operands true
```python
# true
True ^ False
bool("") ^ bool("hey")
0 ^ 1  # 1 -> this what we mean by bitwise
# false
True ^ True
bool("") ^ bool("")
0 ^ 0  # 0
```

---

* https://martinheinz.dev/blog/54
* fuzzy comparison w/ dirty-equals https://martinheinz.dev/blog/96
* format specifier https://stackoverflow.com/a/50340297
* compared to algebra, variable values true/false (not numbers) and operations are logical (not addition, et al.) https://www.youtube.com/watch?v=gI-qXk7XojA 2:35
* _decision table_: extension of truth table? https://www.hillelwayne.com/post/decision-tables/
* aka function table https://reasonablypolymorphic.com/book/machine-diagrams#fn1
* _bitwise operation_: boolean logic on bits https://realpython.com/python-bitwise-operators/ vs. on boolean value https://stackoverflow.com/a/3845032 https://www.andreinc.net/2023/02/01/demystifying-bitwise-ops
* https://docs.python.org/3/library/stdtypes.html

OPERATORS
* _operator symbol_: e.g. `^` maps to `operator.xor` https://docs.python.org/3/library/operator.html#mapping-operators-to-functions
* bitwise operators: `^` (caret) `&` (ampersand) `|` (pipe) https://docs.python.org/3/reference/expressions.html#binary-bitwise-operations
* _logical_: `and` and `or` short-circuit https://docs.python.org/3/tutorial/datastructures.html#more-on-conditions https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not
* _comparison_: can be chained e.g. `a > b == c` https://docs.python.org/3/tutorial/datastructures.html#more-on-conditions

TRUE AND FALSE
* _truthy_: non-empty collections, num greater than zero
* obj are true https://www.fluentpython.com/lingo/#truthy
* _falsy_: empty collections, zero, None https://www.fluentpython.com/lingo/#falsy
```python
# toggle boolean https://stackoverflow.com/a/8381955 https://realpython.com/python-boolean/
x = True
x = not x

# syllogism https://blog.carlmjohnson.net/post/2020/python-square-of-opposition/
all(['hi', 'hey'])  # True
all(['hi', 'hey', ''])  # False
any(['hi', 'hey', ''])  # True
any([''])  # False
```

* _infix operator_: `*` 🗄 `language.md`

## scope

🗄 `language.md` overloading

---

* _nested scope_: https://docs.python.org/3/glossary.html#term-nested-scope
🔗 https://blog.araj.me/til-nonlocal-statement-in-python/ https://realpython.com/python-namespaces-scope/ https://muhammadraza.me/2023/Python-Namespace/

unbound local, formal parameter https://www.fluentpython.com/lingo/#parameter https://docs.python.org/3/glossary.html#term-parameter

`locals()`, `globals()` https://arpitbhayani.me/blogs/function-overloading
> Calling the function locals() after defining a function we see that it returns a dictionary of all variables defined in the local namespace. The key of the dictionary is the name of the variable and value is the reference/value of that variable. When the runtime encounters another function with the same name it updates the entry in the local namespace and thus removes the possibility of two functions co-existing. Hence python does not support Function overloading. https://arpitbhayani.me/blogs/function-overloading

* _scope_: namespace; doesn't correspond to code blocks e.g. `if` doesn't introduce nested scope
* _local_: current function https://realpython.com/python-pass-by-reference/#passing-arguments-in-python
```python
def loc():
    foo = 'foo val'
    print(locals())  # {'foo': 'foo val'}
```
* _global_: module (func/class, imports, var); can cast name to global but not recommended (not thread safe) https://realpython.com/python-pass-by-reference/#replicating-pass-by-reference-with-python
* _variable shadowing_: prevent access to same name in higher scope [Smalleshire 5.5 @ 2:30]; use `global` to refer to globally scoped name in event of shadowing
```python
foo = 'foo val'  # global foo
def fail_to_set_foo():
    foo = 'new val'  # local foo

fail_to_set_foo()
foo  # global foo untouched
```

## style

🗄️ `stdlib.md` lint/fmt
📜 https://peps.python.org/pep-0008/ https://github.com/google/styleguide/blob/gh-pages/pyguide.md

* string quotes: single|double both fine https://peps.python.org/pep-0008/#string-quotes black/ruff use double quotes https://github.com/astral-sh/ruff

---

* _line continuation_: "join consecutive lines if the last character of the line is a backslash" [HG 3.2.5 pg. 56] can use parens https://stackoverflow.com/a/53180/6813490
* PEP8 error codes https://pep8.readthedocs.io/en/release-1.7.x/intro.html#error-codes
* line length http://jakevdp.github.io/blog/2017/11/09/exploring-line-lengths-in-python-packages/
* https://nickjanetakis.com/blog/80-characters-per-line-is-a-standard-worth-sticking-to-even-today
* blank lines: 2 after imports, 2 before functions, 1 before methods https://www.python.org/dev/peps/pep-0008/#blank-lines
