# ⛩️

## 参考

📜 https://docs.python.org/3
> `python -m pydoc` -> would love a version of this for the entire documenation 🧠 https://chatgpt.com/c/672a34e7-ca2c-8004-bef4-64829a580ab7
🗣
* https://chat.stackoverflow.com/rooms/6/python
* https://www.youtube.com/@mCoding
📚
* Beazley cookbook
* Ramalho fluent https://github.com/fluentpython/example-code-2e/tree/master/01-data-model
* Van Rossum tutorial

## 进步

* _24_: split from `python.md`, typing (exhaustiveness check, type narrowing)
* _23_: hashable
* _19_: imports, obj assignment, first pass (lambdas, dataclasses, shallow vs. copy, closure, decorator)
* _18_: Hitchhiker's Guide, first pass (imports, unit testing)
* _17_: PSF install, PS beginner course

# 🗂 CLASSES

🗄 `language.md` object-oriented
📚
* Beazley ch. 7
* Ramalho ch. 1, 5, 11-14, 16, 22-24
* Van Rossum ch. 9 https://docs.python.org/dev/tutorial/classes.html

---

* https://rednafi.com/python/dataclasses_and_methods/
* dataclasses, typing https://kobzol.github.io/rust/python/2023/05/20/writing-python-like-its-rust.html
* classes https://realpython.com/python-classes/
https://www.youtube.com/watch?v=5vpdzRbfTIM

SEMANTICS
* _attributes_: value tied to obj and accessed via dot notation https://docs.python.org/3/glossary.html#term-attribute
* data + methods 📙 Ramalho [839]
* kinds of attr: value, type, refcount (reference counting https://codeconfessions.substack.com/p/cpython-reference-counting-internals https://docs.python.org/3/glossary.html#term-reference-count https://signalsandthreads.com/memory-management/) https://realpython.com/pointers-in-python/#objects-in-python https://pythonspeed.com/articles/python-object-memory/ https://realpython.com/python-pass-by-reference/#passing-arguments-in-python https://realpython.com/python-pass-by-reference/#understanding-assignment-in-python
* check if attr present with try/catch, don't use hasattr() https://hynek.me/articles/hasattr/
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

📜 https://docs.python.org/3/library/dataclasses.html

BASICS
```python
from dataclasses import dataclass
@dataclass()
class Person:
    name: str  # typing mandatory
    hobbies: list
    age: int = 42  # default values have to go last
```

PARAMETERS https://docs.python.org/3/library/dataclasses.html#module-contents
> saves you impl + re-impl every time you update class
* no param
```python
# no param
('__eq__', <function Person.__eq__ at 0x1059974c0>),
('__init__', <function Person.__init__ at 0x1059971a0>),
('__repr__', <function Person.__repr__ at 0x105997420>)

@dataclass(kw_only=True)  # init only uses kwargs

@dataclass(frozen=True)   # immutable
('__hash__', <function Person.__hash__ at 0x1038a37e0>),
('__delattr__', <function Person.__delattr__ at 0x1038a3600>),
('__setattr__', <function Person.__setattr__ at 0x1038a3560>)

@dataclass(sort=True)     # sortable
('__ge__', <function Person.__ge__ at 0x10579f740>),
('__gt__', <function Person.__gt__ at 0x10579f6a0>),
('__le__', <function Person.__le__ at 0x10579f600>),
('__lt__', <function Person.__lt__ at 0x10579f560>),
```

---

ADVANTAGES COMPARED TO PLAIN CLASSES https://www.youtube.com/watch?v=vBH6GRJ1REM @ 5:30
* convert w/ `asdict`, `astuple`
* work around immutable https://www.youtube.com/watch?v=vBH6GRJ1REM [5:30]

* https://realpython.com/python-data-classes/
* https://jacobpadilla.com/articles/python-dataclass-internals
* alternative + serde https://github.com/python-attrs/attrs https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek https://hynek.me/articles/import-attrs/
* serde https://github.com/lidatong/dataclasses-json
* vs. defined https://www.youtube.com/watch?v=1S2h11XronA
> the most useful purpose is adding a certain degree of formalization to a group of values that need to be passed around. https://www.revsys.com/tidbits/dataclasses-and-attrs-when-and-why/
* `__repr__` and `__eq__` for free https://realpython.com/python-data-classes/
* faster access than `namedtuple` but worse mem usage https://stackoverflow.com/a/51673969
* convert dict to dataclass https://github.com/konradhalas/dacite

## dunder

📚
* lang ref ch. 3-4
* Kettler magic  https://news.ycombinator.com/item?id=17727437
* Van Rossum ch. 9

---

make immutable classes + port learning from dataclasses video https://www.youtube.com/watch?v=vBH6GRJ1REM [1:45]

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

## 🧑‍🧑‍🧒‍🧒 inheritance

🗄️ typing

---

```python
issubclass(bool, int)

# https://github.com/cosmologicon/pywat#circular-types 
isinstance(object, type)      # True
isinstance(type, object)  # True
```

* _abstract base class (ABC)_: https://www.fluentpython.com/lingo/ https://docs.python.org/3/glossary.html#term-abstract-base-class
* _virtual subclass_: https://www.fluentpython.com/lingo/ https://www.fluentpython.com/lingo/#constructor

### mixin

---

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

### protocol

---

* way to do interfaces
* https://chatgpt.com/c/671815e8-0f44-8004-abb5-be6b52fc8bd1
* https://godatadriven.com/blog/protocols-in-python-why-you-need-them/
* https://www.youtube.com/watch?v=xvb5hGLoK0A
* https://peps.python.org/pep-0544/
* https://www.amazon.com/Architecture-Patterns-Python-Domain-Driven-Microservices/dp/1492052205
* https://codebeez.nl/blogs/type-hinting-in-modern-python-the-protocol-class/
* https://pythontest.com/fix-circular-import-python-typing-protocol/

## methods

---

METHODS
| type      | called on | arg          | variable access | use case                                          |
|-----------|-----------|--------------|-----------------|---------------------------------------------------|
| instance  | instance  | instance     | instance, class |                                                   |
| class     | class     | class        | class           | factory                                           |
| static    | class     | user-defined | --------------- | just plain func namespaced to class; Ramalho [371]|

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

* _self_: parameter to instance method whose arg is instance itself https://martinheinz.dev/blog/81
* _cls_: parameter to class method whose arg is class itself
* impl via descriptor https://www.youtube.com/watch?v=ANLjBsWHshc
* just a naming convention https://stackoverflow.com/a/475919
* debate http://neopythonic.blogspot.com/2008/10/why-explicit-self-has-to-stay.html https://stackoverflow.com/q/2709821

## property

* _property_: https://realpython.com/python-property/
* aka managed attribute
> Programming languages such as Java and C++ encourage you to never expose your attributes to avoid this kind of problem. Instead, you should provide getter and setter methods, also known as accessors and mutators, respectively. These methods offer a way to change the internal implementation of your attributes without changing your public API.
> Properties represent an intermediate functionality between a plain attribute, or field, and a method. In other words, they allow you to create methods that behave like attributes. With properties, you can change how you compute the target attribute whenever you need to.

---

* _property_: you can control `__get__`/`__set__`/`__delete` (whereas you cannot on attributes) https://stackoverflow.com/q/7374748
* 📙 Ramalho [839]
* https://www.fluentpython.com/lingo/#managed_attribute

* call method same way you used access property/attr i.e. dot notation
* way to refactor field into method https://www.machinelearningplus.com/python/python-property/ https://stackoverflow.com/q/6618002/6813490
* uniform acccess principle https://www.fluentpython.com/lingo/
```python
# PHASE 1 - .fullname becomes inconsistent if other attr updated bc only set on init
class Person():
    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname
        self.fullname = self.first + ' '+ self.last

# PHASE 2 - works but a breaking change bc .fullname is now .fullname()
class Person():
    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname
    def fullname(self)
        return self.first + ' ' + self.last

# PHASE 3 - invoke method with same syntax as accessing property
class Person():
    def __init__(self, firstname, lastname):
        self.first = firstname
        self.last = lastname
    @property
    def fullname(self)
        return self.first + ' ' + self.last
```

# 🕉 OBJECTS

📙 Ramalho ch. 6

* _object_: https://docs.python.org/3/glossary.html#term-object
* _object model_: everything inherits from `object` as of Python 2.2 https://www.youtube.com/watch?v=vvuYPUbwAO0 2:30 https://docs.python.org/3/reference/datamodel.html
* everything is an object, which means tons of allocations and therefore GC
> A massive number of memory allocations (malloc) and a significant amount of time spent on garbage collection. This is when ‘everything is an object’ really bites you. https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust

---

* initialize vs. construct, __init__, __new__ https://www.fluentpython.com/lingo/#initializer https://www.fluentpython.com/lingo/#constructor
* https://realpython.com/python-lazy-evaluation/
* https://realpython.com/python-variables/
* https://treyhunner.com/2022/03/variables-objects-and-pointers-in-python/
* https://realpython.com/syntactic-sugar-python/
https://realpython.com/python313-new-features/#new-copyreplace-for-modifying-immutable-objects
https://github.com/google/pyglove
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

* `__del__()`: aka finalizer; method called when `del` called against obj/var; meant for cleaning up memory, not doing other code cleanup (use `with` instead) [4:00] https://realpython.com/python-del-statement/

## memory

🗄
* `architecture.md` memory
* `language.md` memory

BASICS
* _object_: underlying value
* get size `sys.getsizeof(obj)`
* _name_: way to refer to obj
* aka object reference https://nedbatchelder.com/text/names.html
* name, reference count https://www.thepythoncodingstack.com/p/whats-in-a-name-python-namespace-objects-names
* _borrowed reference_: https://docs.python.org/3/glossary.html#term-borrowed-reference
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

## assignment

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

## packing

* https://github.com/zachvalenta/capp-brand-enablement/
```python
def smart_join(dt, tt, did, tid):
    joined.select(joined.columns[0], joined.columns[-1], *joined.columns[1:-1])
```

```python
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



# dict keys to list + more unpacking https://stackoverflow.com/questions/33161448/getting-only-element-from-a-single-element-list-in-python#33161467
[*dict]
# combine dicts https://stackoverflow.com/a/67450966
{**bar, **bar}


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

## intern

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

## symbol table

---

https://llm.datasette.io/en/stable/related-tools.html

* _private_: all obj in module 
* _public_: obj in mod avaiable when import mod https://realpython.com/python-modules-packages/#the-import-statement https://docs.python.org/3/library/functions.html#locals
* `locals()`: local symbol table https://docs.python.org/3/library/functions.html#locals
* `globals()`: global symbol table
* `dir()`: locals() w/ out values https://stackoverflow.com/a/21961813 https://realpython.com/python-modules-packages/#the-dir-function

# 🎹 TYPING

🗄 `plt.md` typing

TYPE CHECKERS
* _Beartype_: https://github.com/beartype/beartype
* _MonkeyType_: Instagram i.e. Python 3 https://github.com/Instagram/MonkeyType https://www.pythonpodcast.com/monkeytype-with-carl-meyer-and-matt-page-episode-146/
* _mypy_: PSF
* _pyannotate_: Dropbox i.e. Python 2 https://github.com/dropbox/pyannotate
* _pyre_: Facebook https://pyre-check.org/
* _PyRight_: Microsoft https://github.com/Microsoft/pyright
* _typecheck_: 🎯 auto error handling for typed args https://calmcode.io/shorts/typeguard.py

ZA
> The foundations of Python’s static type system were defined in PEP 484 and introduced in Python 3.5. In November 2023, PEP 729 established the Typing Council and formalized the type system through a typing specification. https://realpython.com/python313-new-features/
* _exhaustiveness check_: check that functions handle newly-added attributes on their args https://news.ycombinator.com/item?id=25428583
* _type narrowing_: issue warning if src tries to operate on type that args cannot be passed on blocks's previous code https://hakibenita.com/python-mypy-exhaustive-checking

---

generate https://github.com/RightTyper/RightTyper
https://realpython.com/python313-new-features/#improvements-to-static-typing

ANNOTATIONS
* _annotation_: https://docs.python.org/3/glossary.html#term-annotation
* _function annotation_: https://docs.python.org/3/glossary.html#term-function-annotation
* _variable annotation_: https://docs.python.org/3/glossary.html#term-variable-annotation
* _generic type_: https://docs.python.org/3/glossary.html#term-generic-type
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

multiple returns https://realpython.com/python-type-hints-multiple-types/
https://realpython.com/python-type-self/
https://lukeplant.me.uk/blog/posts/the-different-uses-of-python-type-hints/

* https://terokarvinen.com/2022/python-dotted-dictionary/
* https://realpython.com/python311-new-features/#improved-type-variables
* history https://www.fluentpython.com/lingo/#type
* https://realpython.com/python311-new-features/#improved-type-variables
* boxing https://www.moderndescartes.com/essays/data_oriented_python/ https://en.wikipedia.org/wiki/Object_type_(object-oriented_programming)#Boxing https://stackoverflow.com/questions/13055/what-is-boxing-and-unboxing-and-what-are-the-trade-offs
* _dummy version_: `isinstance`
* type hints introduced in PEP 484 https://www.python.org/dev/peps/pep-0484/
* mypy vs. pyright https://news.ycombinator.com/item?id=37914146 https://rdrn.me/postmodern-python/
* _sink_: https://talkpython.fm/episodes/show/151/gradual-typing-of-production-applications https://www.youtube.com/watch?v=mh9jQSxzv0c https://inventwithpython.com/blog/2019/11/24/type-hints-for-busy-python-programmers/ https://veekaybee.github.io/2019/07/08/python-type-hints/ https://blog.petrzemek.net/2019/02/22/even-feature-that-you-do-not-use-can-bite-you/

## 🟦 mypy

📜 https://www.mypy-lang.org/

---

https://www.mypy-lang.org/
https://mypy.readthedocs.io/en/stable/getting_started.html#installing-mypy
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

## 🔺 pydantic

📜 https://docs.pydantic.dev/latest/ https://pydantic.dev/
🗄
* `eng.md` clean
* `python/stdlib.md` serde

---

can use as validation before handing over to sqlite3 https://github.com/Zaloog/kanban-tui/blob/main/src/kanban_tui/database.py

DESIGN
* https://chatgpt.com/c/67115402-236c-8004-b283-04e97eb8c541
* https://chatgpt.com/c/6711674f-be44-8004-be07-0236079e05c6

* throw err if typing mismatch https://hackernoon.com/pydantic-what-it-is-and-why-its-useful https://talkpython.fm/episodes/show/466/pydantic-performance-tips
* https://realpython.com/python-pydantic/
* https://fastapi.tiangolo.com/python-types/
* https://www.pythonpodcast.com/pydantic-data-validation-episode-263/
* https://github.com/shopnilsazal/validus
* https://blog.couchbase.com/validate-json-documents-in-python-using-pydantic/
* https://talkpython.fm/episodes/show/466/pydantic-performance-tips

ALTERNATIVES
* BYO https://realpython.com/primer-on-python-decorators/#more-real-world-examples https://blog.drewolson.org/declarative-validation
* _cerberus_: https://github.com/pyeve/cerberus https://hector.dev/2020/12/29/validating-data-in-python-with-cerberus.html
