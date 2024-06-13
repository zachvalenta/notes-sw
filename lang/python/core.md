# ⛩️

## 参考

📜 https://docs.python.org/3
🗣
* https://chat.stackoverflow.com/rooms/6/python
* https://www.youtube.com/@mCoding
📚
* Beazley cookbook
* Ramalho fluent
* Van Rossum tutorial

## 进步

* _23_: hashable
* _22_: iteration (iterators, generators), big rf
* _19_: executables, imports, obj assignment, first pass (lambdas, tuple unpacking, iteration, dataclasses, shallow vs. copy, closure, decorator)
* _18_: Hitchhiker's Guide, first pass (imports, unit testing)
* _17_: PSF install, PS beginner course

---

* 📙 Ramalho @ 2.20 -> hashable -> hash tables 🗄 `algos.md` hash tables re: maps, ADTs https://realpython.com/solid-principles-python/ https://github.com/dabeaz-course/python-mastery https://mkaz.blog/working-with-python/
* https://realpython.com/python-lazy-evaluation/
* https://realpython.com/python-pydantic/
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
* difflib https://florian-dahlitz.de/articles/create-your-own-diff-tool-using-python
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
* Van Rossum ch. 9 https://docs.python.org/dev/tutorial/classes.html

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

DATACLASS
> the most useful purpose is adding a certain degree of formalization to a group of values that need to be passed around. https://www.revsys.com/tidbits/dataclasses-and-attrs-when-and-why/
* `__repr__` and `__eq__` for free https://realpython.com/python-data-classes/
* faster access than `namedtuple` but worse mem usage https://stackoverflow.com/a/51673969
* convert dict to dataclass https://github.com/konradhalas/dacite

## attributes

---

```python
# https://monadical.com/posts/operator-overloading-in-python.html
class Clock:
   def __init__(self, time: str):
       self.hour, self.min = [int(i) for i in time.split(':')]

   def __repr__(self) -> str:
       min = '0' + str(self.min)
       return str(self.hour) + ':' + min[-2:]
```

SEMANTICS
* _attributes_: value tied to obj and accessed via dot notation https://docs.python.org/3/glossary.html#term-attribute
* data + methods 📙 Ramalho [839]
* _method_: callable attribute 📙 Ramalho [839]
* _data_: readable/writable attributes
* read via: dot notation, `dir()` (K) `vars()` (K-V)

DATA https://stackoverflow.com/questions/2714573/instance-variables-vs-class-variables-in-python
* _instance variable_: 
* _class variable_: 

METHODS
| type      | called on | arg          | variable access | use case                                          |
|-----------|-----------|--------------|-----------------|---------------------------------------------------|
| instance  | instance  | instance     | instance, class |                                                   |
| class     | class     | class        | class           | factory                                           |
| static    | class     | user-defined | --------------- | just plain func namespaced to class; Ramalho [371]|
* _self_: parameter to instance method whose arg is instance itself
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


---

* the use of class methods https://stackoverflow.com/a/38276/6813490
> c.f. dunder / __init__
* https://stackoverflow.com/questions/22616559/use-cases-for-property-vs-descriptor-vs-getattribute
* `__getattr__`: https://docs.python.org/3/glossary.html#term-attribute 
* `__setattr__`: https://docs.python.org/3/glossary.html#term-attribute 
* `__getattribute__` https://news.ycombinator.com/item?id=3719179

* bound method https://www.fluentpython.com/lingo/#bound_method
* _accessor_: https://www.fluentpython.com/lingo/#accessor

## descriptor

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
* `__get__` enables for true encapsulation vs. name mangling
* https://docs.python.org/3/howto/descriptor.html 
* https://nedbatchelder.com/blog/201306/explaining_descriptors.html
* _fully persistent data structure_: Git works like this, can branch, can time travel
* _partially persistent data structure_: same as fully persistent except can only modify the most recent copy

## dunder

📚
* lang ref ch. 3-4
* Ramalho ch. 1
* Van Rossum ch. 9

METHODS 📙 Kettler magic https://news.ycombinator.com/item?id=17727437
* lifecycle: `__new__`, `__init__`, `__hash__`, `__eq__`
* __dict__: stores obj writable attributes https://docs.python.org/3/library/stdtypes.html#object.__dict__
* called by `vars()` https://docs.python.org/3/library/functions.html#vars
* __new__: thing that actually creates obj instance https://betterprogramming.pub/5-pairs-of-magic-methods-in-python-you-should-know-f98f0e5356d6 https://realpython.com/python-class-constructor/
* __init__: initializes obj https://realpython.com/python-multiple-constructors/ https://realpython.com/python-class-constructor/
* use `cls()` when you want a wrapper in front of this in a class constructor https://stackoverflow.com/q/24799403
```python
# straightforward
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
* __hash__: returns int 📙 Ramalho [84,415] https://docs.python.org/3/reference/datamodel.html#object.__hash__
* use case: comparing obj https://www.youtube.com/watch?v=opijuVoq3Kk 5:50
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
* __eq__: 📙 Ramalho [84,415]
* __call__: make class instance callable e.g. `foo = Foo(); foo()` https://realpython.com/python-class-constructor/ https://realpython.com/python-multiple-constructors/ re: metaclasses https://eli.thegreenplace.net/2012/04/16/python-object-creation-sequence

BASICS
* _dunder_: methods called by the interpreter 📙 Ramalho [3]
> When an object is passed to the str built-in function, its __str__ method is called. https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/
* aka magic method, special method 📙 Ramalho [4] https://www.fluentpython.com/lingo/#special_method https://docs.python.org/3/glossary.html#term-magic-method https://docs.python.org/dev/reference/datamodel.html#specialnames
> why isn't "magic method" or "dunder" in the docs? 📙 Kettler https://docs.python.org/dev/reference/datamodel.html#specialnames
* usage: Django queryset https://books.agiliq.com/projects/Journeyman-Python/en/latest/magic-methods.html
* documentation: language reference ch. 3 (data model) https://docs.python.org/dev/reference/datamodel.html#specialnames language reference ch. 4 (mapping types) https://www.fluentpython.com/lingo/#special_method
> They're also not as well documented as they need to be. All of the magic methods for Python appear in the same section in the Python docs, but they're scattered about and only loosely organized. There's hardly an example to be found in that section (and that may very well be by design, since they're all detailed in the language reference, along with boring syntax descriptions, etc). https://rszalski.github.io/magicmethods/

---

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
* _interface_: https://docs.python.org/3/faq/design.html#how-do-you-specify-and-enforce-an-interface-spec-in-python https://realpython.com/python-interface/ https://glyph.twistedmatrix.com/2021/03/interfaces-and-protocols.html
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
* view source https://stackoverflow.com/a/1562795
```python
from inspect import getsource
print(getsource(ur_func))
```

AST
* inspect https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework
* https://www.mattlayman.com/blog/2018/decipher-python-ast/
* https://talkpython.fm/episodes/show/152/understanding-and-using-python-s-ast
* get data structure from string `ast.literal_eval(ds_as_str)` https://stackoverflow.com/a/17768535

DECORATORS
* _decorator_: factory + functionality https://www.fluentpython.com/lingo/#decorator
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

# 🧮 COLLECTIONS

📜 https://docs.python.org/3/library/stdtypes.html
📚
* Beazley ch. 1
* Van Rossum ch. 5

CHARACTERISTICS
* _hashable_: hash value never changes (`__hash__`) and can be compared to other objects (`__eq__`) https://docs.python.org/3/glossary.html#term-hashable
```python
https://stackoverflow.com/questions/1957396/why-dict-objects-are-unhashable-in-python
https://realpython.com/python-hash-table/
```
* _immutable_: obj w/ fixed value https://docs.python.org/3/glossary.html#term-immutable
* mutable objs can alter values but keep same ID https://docs.python.org/3/glossary.html#term-mutable
```python
# mutable bc diff values same ID
foo = list()
id(foo)  # 4339427648
foo.append("hey")
id(foo)  # 4339427648
```
* _subscriptable_: 
```python

```

> first section of dictionary header
OVERVIEW
* use case: container
* characteristics
```python
myd = dict(magic=32, larry=33)

# UNHASHABLE

# MUTABLE

# SUBSCRIPTABLE
myd["magic"]
```

---

https://www.pythonmorsels.com/time-complexities/

| CLASS   | TYPE    | MUTABLE | HASHABLE       | SUBSCRIPTABLE |  NOTES              |
|---------|---------|---------|----------------|---------------|---------------------|
| list    | seq     | yes     | no             | byes          | for iteration       |
| tuple   | seq     | no      | if el hashable | yes           | list + immutable    |
| string  | seq     | no      | yes            | yes           | tuple + for text    |
| dict    | mapping | yes     | no             | yes           | place for ur stuff  |
| set     | set     | yes     | no             | no            | for set operations  |

CHARACTERISTICS
* _subscriptable_: read by index or key aka indexing
* impl via `__getitem__` https://stackoverflow.com/a/216980
```python
from enum import Enum

class Color(Enum):
    GREEN = "green"

Color.GREEN[0]  # TypeError: 'Color' object is not subscriptable
```
* _mutable_: can be altered i.e. diff values same obj ID https://docs.python.org/3/glossary.html#term-mutable
```python
foo = list()
id(foo)  # 4339427648
foo.append("hey")
id(foo)  # 4339427648
```
* _immutable_: cannot be altered i.e. updates = new obj https://docs.python.org/3/glossary.html#term-immutable
```python
bar = "hi"
bar[0] = "b"  # TypeError: 'str' object does not support item assignment
id(bar)  # 4440141744
bar = "hey"
id(bar)  # 4458076080
```
* _hashable_: impl `__eq__` and `__hash__` (immutable) https://www.fluentpython.com/lingo/#hashable 📍📙 Ramalho [84,415]
* if `a == b` + also `hash(a) and hash(b)`
```python
from enum import Enum
class Color(Enum):
    GREEN = 1
    BLUE = 2
# hashable
hash(Color.BLUE) == hash(Color.BLUE)  # True
Color.BLUE == Color.BLUE              # True
# not hashable
[2] == [2]                            # True
hash([2]) == hash([2])                # TypeError: unhashable type: 'list'
```
* all immutable are hashable but not vice versa https://realpython.com/lessons/immutable-vs-hashable/
* hashable: immutable + immutable collections w/ hashable el (tuples, frozenset) https://www.fluentpython.com/lingo/#hashable https://docs.python.org/3/glossary.html#term-hashable
* unhashable: mutable collections https://docs.python.org/3/glossary.html#term-hashable
```python
# unhashable collections still need hashable el e.g. set https://www.youtube.com/watch?v=opijuVoq3Kk 1:10
{[1,2,3], [42,13,7]}  # TypeError: unhashable type: 'list'
{"hey", "hi"}         # ok
```

SEMANTICS
* _collection_: https://www.fluentpython.com/lingo/#collection
* _sequence_: https://www.fluentpython.com/lingo/#sequence https://docs.python.org/3/glossary.html#term-sequence
* _flat sequence_: https://www.fluentpython.com/lingo/#flat_sequence
* _binary sequence_: https://www.fluentpython.com/lingo/#binary_sequence
* _mapping_: https://docs.python.org/3/glossary.html#term-mapping
* _byte array_: used for HTTP response, passing files around
* _bytes-like object_: https://www.fluentpython.com/lingo/#bytes-like_object https://docs.python.org/3/glossary.html#term-bytes-like-object

## operations

🛠
* lodash https://github.com/dgilland/pydash https://github.com/dgilland/fnc
* diff https://github.com/seperman/deepdiff

COPY
* _idiom_: use factory function i.e. `list()` `dict()` instead of specific impl (`l[:]`, `l.copy()`) https://realpython.com/copying-python-objects/
* _shallow copy_: copied collection refers to obj from original i.e. cannot modify independently if obj are mutable [Smalleshire 1 6.5 @ 3:00]
* https://www.fluentpython.com/lingo/#shallow_copy
* see aliasing https://www.fluentpython.com/lingo/#deep_copy
```python
l = [42, 'abc', [1,2,3]]
n = list(l) 

n == l  # True bc holds same val
n is l  # False bc diff obj 

# shallow = mutable el will update for all collections that reference them
n[2][0] = 100
l  # [42, 'abc', [100, 2, 3]]
n  # [42, 'abc', [100, 2, 3]]

# immutable el are just replaced w/ new obj
n[0] = 0
l  # [42, 'abc', [100, 2, 3]]
n  # [0, 'abc', [100, 2, 3]]
```
* _deep copy_: copy actual values i.e. can modify independently https://www.fluentpython.com/lingo/#deep_copy
```python
from copy import deepcopy
l = [42, 'abc', [1,2,3]]
n = deepcopy(l) 
n[2][0] = 100
l  # [42, 'abc', [100, 2, 3]]
n  # [42, 'abc', [1, 2, 3]]
```

SLICE
* _slice_: subset of sequence type https://www.fluentpython.com/lingo/#slicing
* out-of-place https://stackoverflow.com/a/5131563
```python
# syntax https://stackoverflow.com/a/509295
[start : stop : step/direction]

# start/stop
'alice'[1:]  # 'lice' -> start is inclusive
'alice'[:3]  # 'ali' -> stop is exclusive
'alice'[:-2]  # 'ali' -> stop by negative index

# step
'alice'[::1]  # 'alice' 
'alice'[::2]  # 'aie'  -> inclusive

# direction
'alice'[::-1]  # 'ecila' 
'alice'[::-2]  # 'eia'  -> can combine w/ step

# slice obj https://stackoverflow.com/a/24713353 https://stackoverflow.com/a/10573523
my_s = slice(1,3)
'alice'[my_s]  # 'li'

# doesn't throw IndexError https://wsvincent.com/python-wat-slice-out-of-range/
[42, 13, 7][:100]  # returns entire collection
[42, 13, 7][100:]  # returns empty string
```

SORT 📜 https://docs.python.org/3/howto/sorting.html https://realpython.com/python-sort
```python
# out-of-place
# works for any iterable https://realpython.com/python-sort/#sorting-numbers
sorted(tup)

# in-place
# method on lists
# uses Timsort sorts by first el e.g. `[(5, 1100), (6, 200)]`
qd.sort()
```

---

* `__lt__`: define sort order for obj https://docs.python.org/3/howto/sorting.html#odd-and-ends
* `key`: func to apply to each el https://docs.python.org/3/howto/sorting.html#key-functions
```python
"""
basic
"""

sorted('This test string'.split(''))  # ['This', 'string', 'test']
sorted('This test string'.split(), key=str.lower)  # ['string', 'test', 'This'] -> ❓ unclear about syntax re: str.lower vs. str.lower() 

"""
1 attr
"""

from collections import namedtuple
Musician = namedtuple('Musician', 'name instrument genre')
mick = Musician(name='mick', instrument='vocals', genre='rock')
nas = Musician(name='nas', instrument='vocals', genre='rap')
stevie = Musician(name='stevie', instrument='piano', genre='r-n-b')
timbo = Musician(name='timbo', instrument='production', genre='rap')
musicians = [mick, nas, stevie, timbo]

sorted(musicians, key=lambda muz: muz.instrument)  # stevie and timbo to front

"""
n attr
"""

from operator import attrgetter
sorted(musicians, key=attrgetter('instrument', 'genre'))  # nas in front of mick
```

## iteration

📙 Beazley ch. 4
🔗
* https://www.bitecode.dev/p/a-taste-of-iteration-in-python
* https://stackoverflow.com/questions/2776829/difference-between-pythons-generators-and-iterators
* https://stackoverflow.com/questions/231767/what-does-the-yield-keyword-do/231855
* Batchelder https://www.youtube.com/watch?v=EnSu9hHGq5o
* Hunner 2016 https://treyhunner.com/2016/12/python-iterator-protocol-how-for-loops-work/
* Hunner 2017 https://www.youtube.com/watch?v=V2PkkMS2Ack
* Hunner 2018 https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/
* Hunner 2019 https://treyhunner.com/2019/06/loop-better-a-deeper-look-at-iteration-in-python/

ITERABLES https://realpython.com/python-iterators-iterables/
* _iterable_: 1) impl `__iter__` 2) where `__iter__` returns iterator https://www.youtube.com/watch?v=EnSu9hHGq5o 23:45
* https://www.fluentpython.com/lingo/#iterable https://docs.python.org/3/glossary.html#term-iterable
* anything you can for loop i.e. obj that can return members sequentially e.g. collections, files https://treyhunner.com/2019/06/loop-better-a-deeper-look-at-iteration-in-python/
```python
# ❌ TypeError: 'TodoList' object is not iterable
class TodoList():
    def __init__(self, items):
        self.items = items

todos = TodoList(["buy groceries", "pickup kids"])
for todo in todos:
    print(todo)

# ❌ TypeError: iter() returned non-iterator of type 'list'
class TodoList():
    def __init__(self, items):
        self.items = items
    def __iter__(self):
        return self.items

# ✅ iterable
class TodoList():
    def __init__(self, items):
        self.items = items
    def __iter__(self):
        return iter(self.items)  # ✅ iterator
```

ITERATORS
* _iterator_: obj that does the iterating https://www.fluentpython.com/lingo/#iterator https://docs.python.org/3/glossary.html#term-iterator https://bitfieldconsulting.com/golang/iterators
```python
# iterable
myl = [3, 42, 7]
# get iterator
myi = iter(myl)
# get next item (calls __next__)
next(myi)  # 3
```
* itself an iterable (impl `__iter__`) and its iterator is itself (`__next__`) https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python
```python
class Count:
    def __init__(self, start=0):
        self.num = start
    def __iter__(self):
        return self
    def __next__(self):
        num = self.num
        self.num += 1
        return num

# for loop impl: 1) call __iter__ 2) call __next__ until handle StopIteration https://github.com/python/cpython/blob/ac0c6e128cb6553585af096c851c488b53a6c952/Lib/test/test_enumerate.py#L109
for n in Count():
    print(n)  # 0 1 2...
```

GENERATORS
* _generator_: https://realpython.com/introduction-to-python-generators/ 🗄 `language.md` functions
* https://www.fluentpython.com/lingo/#generator https://docs.python.org/3/glossary.html#index-19 https://tushar.lol/post/recursive-generators/
* iterator using `yield` https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/
* _generator iterator_: https://docs.python.org/3/glossary.html#term-generator-iterator
* _generator expression_: syntactic sugar for generator function https://www.youtube.com/watch?v=EnSu9hHGq5o 24:45 https://docs.python.org/3/glossary.html#index-20
* can only iterate once bc values not stored in memory https://stackoverflow.com/a/231855
```python
gen = (x for x in range(3))
for el in gen:
    print(el)  # 0 1 2
for el in gen:
    print(el)  # nothing
```
* holds single value in memory at a time (vs. lists, which hold all el in memory at once)
* useful when you just want to iterate https://realpython.com/python-coding-interview-tips/#save-memory-with-generators
* lazy vs. eager https://treyhunner.com/2016/11/check-whether-all-items-match-a-condition-in-python/ https://www.fluentpython.com/lingo/#lazy
* type of continuation https://www.hhyu.org/posts/generator_and_continuation/
* with multiprocessing http://www.antoncohen.com/2016/10/python-generators-with-multiple-threads.html
* 📍 https://medium.com/canopy-tax/sammys-generators-in-python-57e43386b89e https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/  https://martinheinz.dev/blog/88

ITERTOOLS
* module for doing stuff with iterables
* https://github.com/erikrose/more-itertools/ https://www.pythoncheatsheet.org/#itertools-Module https://realpython.com/python-itertools/ https://jeffknupp.com/blog/2018/12/13/how-to-do-just-about-anything-with-python-lists/ https://towardsdatascience.com/tour-of-python-itertools-2af84db18a5e https://florian-dahlitz.de/blog/introduction-to-itertools https://www.blog.pythonlibrary.org/2021/12/07/a-tour-of-pythons-itertools-library/ https://martinheinz.dev/blog/52
```python
# COMBINATIONS AND PERMUTATIONS https://www.youtube.com/watch?v=jUM_Dpt6yu0
list(itertools.combinations(['alice', 'bob', 'candace'], r=2))  # [('alice', 'bob'), ('alice', 'candace'), ('bob', 'candace')]
list(itertools.permutations(['alice', 'bob', 'candace'], r=2))  # [('alice', 'bob'), ('bob', 'alice')...]

# ITERATE COLLECTIONS CONSECUTIVELY HTTPS://SOURCERY.AI/BLOG/EFFECTIVE-COLLECTION-HANDLING/
for foo in itertools.chain(this_one_first, then_this_one):
    do_something(foo)

# SUM LIST OF NUMBERS
from functools import reduce
from operator import add
round(reduce(add, [5.15, 4.2, 10.7]), 2)
```

COMPREHENSIONS
* aka listcomp https://www.fluentpython.com/lingo/#listcomp
* are eager https://www.fluentpython.com/lingo/#list_comprehension
* for-loop replacement https://sourcery.ai/blog/effective-collection-handling/
* takes iterable, performs operation on each el and adds to collection (list, dict, set)
```python
# syntax
x * 42             # 3 operate
for x in iterable  # 1 iterate
if x % 2 == 0      # 2 condition

# list
my_list = [
    x * 2
    for x in my_iterable
    if x % 2 == 0
]

# set comprehension to dedupe https://github.com/dedupeio/dedupe
my_set = { i for i in [42, 13, 7, 7, 7] }

# dictionary
my_dict = {
    i : string.ascii_letters[i]
    for i in range(3)
}

list_of_dict = [
    dict(id=i, letter=zimu[i])
    for i in range(3)]
```

INDEXES
* https://docs.python.org/3/tutorial/datastructures.html#looping-techniques
* https://treyhunner.com/2016/04/how-to-loop-with-indexes-in-python/
```python
# sequence
for val in seq:
for ind, val in enumerate(seq):  # aka elementwise operation
for artist, album in zip(artists, album):

# mapping https://realpython.com/iterate-through-dictionary-python
for k, v in cidian.items():
```

* `range()`
```python
# start inclusive, end exlusive
range(<start>, <stop>, <step>)

# single arg refers to 'stop'
range(1)  # iterates for zeroeth el
for _ in range(1):
    print('hey')
# hey

# two args refer to 'start' and 'stop'
for _ in range(2, 7):
    print('hey')
# hey
# hey
# hey
# hey
# hey

# three args refer to 'start', 'stop', 'step'
for _ in range(2, 7, 2):
    print('hey')
# hey
# hey
# hey

# if start is higher than stop, simple returns range obj that will iterate 0 times
for i in range(5,1):
    print(i)  # nothing happens
>>>
```

## dict

* _diciontary_: map hashable K to mutable V https://docs.python.org/3/glossary.html#term-dictionary
```python
# hashed K
{"aloha": "hi"}
# unhashed K = # TypeError: unhashable type: 'list'
{[1,2,3]: "hi"}
```

---

* iterate according to wall time https://github.com/brohrer/pacemaker
* dispatch https://martinheinz.dev/blog/90
* K can be int https://stackoverflow.com/questions/44814719/can-both-the-values-and-keys-of-a-dictionary-be-integers
* impl w/ hash table https://akshayr.me/blog/articles/python-dictionaries https://www.pythoninsight.com/2018/08/python-basics-dict-lookup/ https://habr.com/en/post/458518/ https://docs.python.org/3/faq/design.html#how-are-dictionaries-implemented-in-cpython

ORDEREDDICT
* ordered by insertion since 3.6 https://stackoverflow.com/a/39980744 https://just-taking-a-ride.com/inside_python_dict/chapter1.html
* doesn't work w/ keyword arguments https://stackoverflow.com/a/41866972
* need to add keys one at a time vs. constructor

```python
###
# INIT
###

literal = {'username': 'a-xia', 'followers': 987}
constructor = dict(username='a-xia', followers=987)

# can feed (unpack?) pairs into constructor
c = Counter(['alice', 'bob', 'candace', 'candace'])
c.most_common()  # [('candace', 2), ('alice', 1), ('bob', 1)]
dict(c.most_common())  # {'candace': 2, 'alice': 1, 'bob': 1}

###
# READ
###

# view obj  https://docs.python.org/3/library/stdtypes.html#dictionary-view-objects https://www.fluentpython.com/lingo/
# dictionary view https://docs.python.org/3/glossary.html#term-dictionary-view
.keys()   # K
.values() # V
.items()  # list of KV

```

recipes
* _check if empty_: cast to bool https://stackoverflow.com/a/54179636/6813490
* _check in key present_: `<key> in <dict>`
* _get all keys_: cast to list `list({'name': 'alice'})` https://docs.python.org/3/tutorial/datastructures.html#dictionaries
* _merge_: `{**dict1, **dict2}` https://realpython.com/iterate-through-dictionary-python/#using-the-dictionary-unpacking-operator https://treyhunner.com/2016/02/how-to-merge-dictionaries-in-python/
* _pretty print_: `print(json.dumps(item, indent=4, sort_keys=True))` only works when keys are primitives https://stackoverflow.com/a/47007417
* _sort_: `sorted(ur_dict.items(), key=lambda x: x[1])` (sorts by V) https://jeffknupp.com/blog/2018/12/13/how-to-do-just-about-anything-with-python-lists/

* read
```python
cidian['username']
cidian.get('username', 'could not find user name')  # fallback if attr not found
```

* default https://realpython.com/python-defaultdict/
* mutate
```python

# add key
my_dict['new_key'] = 'associated value'

# return existing key or set new (default)
my_dict = {'alice': 1234, 'bob': 5678}
my_dict.setdefault('alice', 'this val would be used if alice was not already a key')
my_dict  # {'alice': 1234, 'bob': 5678}
c = my_dict.setdefault('candace', 42)  # returns 42

# set default for all
my_dict = default_dict(list)
my_dict['alice'] = 1234
my_dict['bob'] = 5678
my_dict['candace']
# defaultdict(<class 'list'>, {'alice': 1234, 'bob': 5678, 'candace': []})

# overwrite key
user['name'] = 'alice'
user.update({'tweets': 42})

# rm key https://stackoverflow.com/a/11277439/6813490
del my_dict['key']  # KeyError if nonexistant
my_dict.pop('key')  # KeyError if nonexistant
k = my_dict.pop('key', None)  # no KeyError if nonexistant
k, v = cidian.popitem()  # pop off kv of last el
```

## set

* set operations 📍 pick SSoT between here and 🗄 `math.md` and 🗄 `sql.md` operations / set
```python
fruit =  {"avocado", "banana", "tomato"}
veg = {"beet", "carrot", "tomato"}

# _difference_: el unique to first set 📙 Bhargava [150]
fruit - veg  # avocado, banana
# _intersection_: el shared 📙 Beaulieu [1000]
fruit & veg  # tomato
# _symmetric difference_: el not shared https://www.idiotinside.com/2017/08/19/set-theory-and-python-tips-tricks/
fruit ^ veg  # avocado, banana, beet, carrot
# _union_: el across sets sans dupes 📙 Beaulieu [99]
fruit | veg   # avocado, banana, tomato, beet, carrot

{42, 7}.issubset({13, 7, 42})  # true
{1,2,3}.issuperset({1,2})      # true
```

* CRUD
```python
# CREATE
ur_set = set()  # have to use parens for empty bc braces creates empty dictionary https://docs.python.org/3/tutorial/datastructures.html#sets
ur_set = {1, 1, 2, 3}  # literal
ur_set = set(['foo', 'foo', 'baz', 'foo'])  # constructor

# UPDATE
# no way to read sans mutation bc sets are unordered don't support indexing https://stackoverflow.com/q/59825
my_set.add(el)  # push - single
my_set.pop()  # shift
my_set.update(iterable)  # push - n

# DELETE
ur_set.remove('foo_el')
```

## sequence

### list

https://realpython.com/python-list/
https://codeconfessions.substack.com/p/why-do-python-lists-multiply-oddly

```python
###
# READ
###

qd[0]   # read at index from start
qd[-2]  # read at index from end; n.b. not slice syntax
if qd:  # check if empty
qd.count(item)  # number of occurences

###
# UPDATE
###

qd.insert(ind, el)      # add at index
qd.extend(listToAdd)    # spread iterable
qd1 + qd2
qd2 = [42, *qd]
qd.insert(0, el)        # unshift
qd.append(el)           # push

del qd[2]  # rm at index
qd.remove('foo_el')  # rm by content
qd.pop(0)  # shift
qd.pop()  # pop

qd.reverse()  # in place
qd[index] = newItem  # overwrite at index
qd + qd  # concatenate

###
# INIT
###

l = [2]  # constructor - int, iterable as single el
list({1,2,3})  # constructor - spread over iterable
l = list ()  # empty (`list[]` is invalid)

###
# FMT
###

" ".join(str(x) for x in L)  # to string
print(*ur_list, sep="\n")  # https://stackoverflow.com/a/22695369
print(json.dumps(item, indent=4, sort_keys=True))  # https://stackoverflow.com/a/55179673/6813490
"""
{
    "first": 123,
    "second": 456,
    "third": {
        "1": 1,
        "2": 2
    }
}
"""
```
* 📍 https://docs.python.org/3/tutorial/stdlib2.html#tools-for-working-with-lists flatten https://realpython.com/python-flatten-list/
* specialized array storage: array (typed) bytes (immutable, single byte i.e. 0-256) bytearray (byte but mutable) https://dbader.org/blog/python-arrays
* impl as dynamic array https://docs.python.org/3/faq/design.html#how-are-lists-implemented-in-cpython
* finding stuff
```python
# membership = "is it there?"
1 in [1, 2, 3]
'a' in 'abc'

# location = "where is it?"
qd.index(el)  # only returns first match
if my_str.find(query) >= 0:  # # https://docs.python.org/3/library/stdtypes.html#str.find
    return my_str.find(query)
else:
    return QueryNotFoundException()
```

### string

📙 Beazley ch. 1

* munge
```python
# PARTS
"NYC:London".split(":")         # into chunks; default delimiter is space
"NYC:London".partition(":")     # into halves; requires delimiter
list("this test string")        # split by char
"".join(l)                      # join by delimiter

# RM
"foo ".strip()                  # rm newline, trailing/leading whitespace
"aaabc".strip("a")              # rm from start
"baaac".replace("a", "")        # swap from anywhere
```

* Python: strip to rm from/end, replace to rm all occurences https://stackoverflow.com/a/40950987/6813490

* contains `"hey" in "heya"`
* compare semver numbers
```python
from distutils.version import StrictVersion
StrictVersion("1.11") > StrictVersion("1.12.6")
```
formatting 📙 Van Rossum ch. 7 https://realpython.com/python-format-mini-language/
* _f-string_: only works on 3.6 and up https://old.reddit.com/r/learnpython/comments/hjegkc/why_do_people_use_format_method_when_f_string/ there's also Template strings, apparently safer that f-strings https://realpython.com/python-string-formatting/ convert to f-string https://github.com/ikamensh/flynt
```python
# HISTORY https://pyformat.info/
f"hey, {'zjv'.upper()}"  # newest
'{} {}'.format('one', 'two')  # newer
'%s %s' % ('one', 'two')  # old

###
# MULTILINE / CONCATENATION
###

# adjacent literals and f-strings concatenate automatically https://stackoverflow.com/a/54950733
me = 'z' 'j' 'v'

# combine w/ multiline (no commas else it's a tuple)
return (
    f"foo: {foo} bar: {bar}"
    f"baz: {baz} qux: {quz}"
)
my_var = (
    "long string oooooooooooooooooooooooone"
    "lone string twoooooooooooooooooooooooo"
)

# use join() bc other approaches create tmp obj (addition +, augmented assignment +=)
"".join(["alice", "and", "bob"])  # bobandalice
" ".join(["alice", "and", "bob"])  # bob and alice
```
* parsing quotes https://pymotw.com/2/shlex/
* char values: `import string; string.string.ascii_letters` https://realpython.com/python-coding-interview-tips/#access-common-string-groups-with-string-constants
* _raw string_: treats backslash as literal, which is why they're seen in Django URLs, `re` https://docs.python.org/3/reference/lexical_analysis.html?highlight=string%20literal#string-and-bytes-literals https://realpython.com/python-raw-strings/
* _StringIO_: access string as if it were a file (for modules that are used to working with files) https://stackoverflow.com/a/7996541
encoding 🗄 `math.md` encoding https://docs.python.org/3/glossary.html#term-list
* _impl_: `PyBytesObject` (Python 3) `PyStringOjbect` (Python 2) https://www.laurentluce.com/posts/python-string-objects-implementation/ https://docs.python.org/3/whatsnew/2.6.html?highlight=pystringobject#pep-3112-byte-literals https://github.com/python/cpython/blob/45876a90e2663f12b90c2090ec3e48bd97841aae/Objects/bytesobject.c
* _unicode_: UTF8 seems like it was an unmitigated disaster https://news.ycombinator.com/item?id=21536468 https://pymongo.readthedocs.io/en/stable/tutorial.html file names stored as byte strings on OS, as Unicode in Python, PP 20:00 https://www.pythonpodcast.com/beets-with-adrian-sampson-episode-152/ @ 20:00 https://realpython.com/python-encodings-guide/ https://stackoverflow.com/a/2081655/6813490 https://www.b-list.org/weblog/2018/nov/26/case/ http://esr.ibiblio.org/?p=8161 http://python-notes.curiousefficiency.org/en/latest/python3/text_file_processing.html https://news.ycombinator.com/item?id=22931240 https://realpython.com/courses/python-unicode/
* _text encoding_: https://docs.python.org/3/glossary.html#term-text-encoding

### tuple

---

https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences https://realpython.com/python-tuple/

```python
###
# INIT
###
tup = ()  # zero el
tup = ('a',)  # single el (sans trailing comma Python understands parens to be those of mathematical precedence control) https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences
tup = 'a', 42, [1, 2, 3] # n el - parens recommended but not strictly necessary

###
# NAMED TUPLE
###
from collections import namedtuple
Musician = namedtuple('Musician', 'name instrument')  # first arg is type, second is attrs
stevie = Musician(name='stevie', instrument='piano')
stevie.instrument = "guitar"  # AttributeError

###
# SimpleNameSpace
# set attr on init, repr for free, comparison by attr instead of id() https://stackoverflow.com/a/37161391
# ❓ given that SimpleNameSpace is writable, why do docs recommend using named tuple instead? if you need a more complete container, why not tell people to use a class (like the comments on Stack Overflow)? https://docs.python.org/3/library/types.html?highlight=simplenamespace#types.SimpleNamespace
###
from types import SimpleNameSpace
stevie = SimpleNamespace(name="stevie", instrument="piano")
stevie.instrument  # 'piano'
stevie.instrument = "guitar"
stevie.instrument  # 'guitar'
```

# 🤖 FUNCTIONS

📙 Beazley ch. 7
🗄 obj/assignment

* _argument_: https://docs.python.org/3/glossary.html#term-argument
* _pass_: implicit return of `None`
* _return_: implicit return of `None` if no other return defined
> A Python function will always have a return value. There is no notion of procedure or routine in Python. https://realpython.com/python-return-statement/#implicit-return-statements
* multimethod, generic function https://www.fluentpython.com/lingo
* callable object https://www.fluentpython.com/lingo/#function

BUILT-IN 📜 https://docs.python.org/3/library/functions.html
* _all()_: return True if iterable empty or all el true
* _dir()_: list obj attr
* _next()_: call `__next__`
* _vars()_: list obj attr + values via `__dict__`

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

TOOLS
* https://github.com/pytoolz/toolz
* howto https://docs.python.org/3/howto/functional.html https://realpython.com/python-functional-programming/ 

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
* _reduce_: sum over list comprehension https://stackoverflow.com/a/16632125 https://realpython.com/python-reduce-function/
```python
from functools import reduce
from operator import mul
nums = [1, 2, 3]
reduce(mul, nums)  # 6
```

## inner / closures

🗄 functools/partial

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

# 🕉 OBJECTS

📜 https://docs.python.org/3/tutorial/classes.html

* _object_: https://docs.python.org/3/glossary.html#term-object
* _object model_: everything inherits from `object` as of Python 2.2 https://www.youtube.com/watch?v=vvuYPUbwAO0 2:30

---

* immortal https://engineering.fb.com/2023/08/15/developer-tools/immortal-objects-for-python-instagram-meta/
* get class name from obj `foo.__class__.__name__`
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

* _get class_: `type()` or `obj.__class__`
* _single underscore_: hint (not enforcement) of private method [tutorial 9.6] i.e. no access modifiers

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

## garbage collection

> port to `language.md`

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
# combine assignment w/ another operatation
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
* mypy vs. pyright https://news.ycombinator.com/item?id=37914146
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

DESIGN https://docs.python.org/3/faq/design.html
* history: origins in ABC https://www.fluentpython.com/lingo/
* readabillity: indentation for statement grouping https://xkcd.com/353/
* aesthetic: `python -m this` https://peps.python.org/pep-0020/ significant white space vs. semi-colons https://news.ycombinator.com/item?id=34936023
* used for: teaching, web dev, sys admin, ML, security, scraping, microcontrollers, industrial automation https://www.pythonpodcast.com/episode-114-industrial-automation-with-jonas-neubert/ finance https://www.openbb.co/ architecture https://talkpython.fm/episodes/show/342/python-in-architecture-as-in-actual-buildings
* used at: Instagram, Dropbox, Reddit, Pinterest
* pain points: binaries, import system, version management, packaging, browser, native (mobile, desktop), speed (not built for multi-core https://twitter.com/mitsuhiko/status/1091802711908106240)
* soft keywords https://mathspp.com/blog/til/pythons-soft-keywords

DOCUMENTATION
* _user-defined_: as opposed to CPython devs https://www.fluentpython.com/lingo/
* mixs usage of "parameter" and "argument" https://www.fluentpython.com/lingo/#parameter

GOVERNANCE
* internal language team at Google https://news.ycombinator.com/item?id=40176338
* quasi-official (PyPA, PyCQA)
* Donald Stuft (PyPA) Raymond Hettinger (core) Tim Peters (Zen of Python `import this`, Timsort) Armin Ronacher (Flask) Brett Cannon (core) Nick Coghlan (core) Eli Bendersky (Google, buddies w/ Coghlan) https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* _Steering Council_: https://mail.python.org/pipermail/python-committers/2019-February/006520.html
* _PEP_: RFCs for Python
* 0 (establish what a PEP is) 8 (style guide) 20 (Zen of Python) https://talkpython.fm/episodes/show/153/how-python-evolves https://peps.python.org/
* how libs get into the stdlib https://github.com/hukkin/tomli/issues/141#issuecomment-997999824

UNDERSCORES https://dbader.org/blog/meaning-of-underscores-in-python
* _single_: placeholder for throwaway values from unpacking
* in REPL, refers to result of last operation
* _single leading_: won't be imported in `from <mod> import *` https://stackoverflow.com/a/8689983
* _single trailing_: break naming conflict
* _double leading_: naming mangling i.e. measure to prevent accidental overrides
* _doubled_: dunder methods

---

* `stderr.flush()`
> Python's standard out is buffered (meaning that it collects some of the data "written" to standard out before it writes it to the terminal). Calling sys.stdout.flush() forces it to "flush" the buffer, meaning that it will write everything in the buffer to the terminal, even if normally it would wait before doing so.
* multiple dispath / multimethods https://martinheinz.dev/blog/50
* _name mangling_: https://www.fluentpython.com/lingo/

* using other language in Python e.g. Julia https://www.peterbaumgartner.com/blog/incorporating-julia-into-python-programs/
* 2to3 https://news.ycombinator.com/item?id=24461157
* _callable_: any obj that impl `__call__` e.g function, method, classes e.g. `MyClass()` https://eli.thegreenplace.net/2012/03/23/python-internals-how-callables-work https://www.fluentpython.com/lingo/#callable_object https://www.pythonmorsels.com/class-function-and-callable/ https://docs.python.org/3/glossary.html#term-callable
* _key function_: for callables https://docs.python.org/3/glossary.html#term-key-function
* _destructuors_: https://eli.thegreenplace.net/2009/06/12/safely-using-destructors-in-python
* `eval()`: take string and evaluate as if expression from language
* _line continuation_: "join consecutive lines if the last character of the line is a backslash" [HG 3.2.5 pg. 56] can use parens https://stackoverflow.com/a/53180/6813490
* `print()`: implicitly adds `\n` under the hood; workaround is `print('hello zv', end="")`
* `__pycache__`: holds bytecode in the form of `.pyc` https://stackoverflow.com/a/28365204/6813490 speeds up module loading https://docs.python.org/3/tutorial/modules.html#compiled-python-files suppress creation of with `export PYTHONDONTWRITEBYTECODE=1` more on bytecode https://blog.jse.li/posts/pyc/ https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md
* _Python2_: can't test Python2 code using Python3 if you're using parts of stdlib that have been deprecated between releases (urllib2, xrange); Tauthon to backport Python3 features https://www.pythonpodcast.com/tauthon-python-2-fork-episode-265/
* _style_: style guides https://www.python.org/dev/peps/pep-0008/ https://github.com/google/styleguide/blob/gh-pages/pyguide.md PEP8 error codes https://pep8.readthedocs.io/en/release-1.7.x/intro.html#error-codes line length http://jakevdp.github.io/blog/2017/11/09/exploring-line-lengths-in-python-packages/ https://nickjanetakis.com/blog/80-characters-per-line-is-a-standard-worth-sticking-to-even-today blank lines (2 after imports, 2 before functions, 1 before methods) https://www.python.org/dev/peps/pep-0008/#blank-lines
* _trailing commas_: for last el in collection https://docs.python.org/3/faq/design.html#why-does-python-allow-commas-at-the-end-of-lists-and-tuples https://www.python.org/dev/peps/pep-0008/#when-to-use-trailing-commas

## control flow

🗄 `language.md`
📙 Van Rossum ch. 4

CONDITIONALS
```python
# `if` unaffected by execution of previous if statements https://stackoverflow.com/a/53545252
def if_example():
    if True:
        print("i will print")
    if True:
        print("i will also print")

# MULTILINE
if (
    'spam' in email['sender'] or
    'spam' in email['subject'] or
    'spam' in email['metadata']
    ):
else:

# TERNARY
this() if x else that()
return True if x else False
var = foo if condition else bar
```

EXCEPTIONS 📚 Beazley ch. 14, Van Rossum ch. 8 https://docs.python.org/3/tutorial/errors.html https://www.b-list.org/weblog/2023/dec/11/python-exceptions/
* _handler_: `try` block
* _unhandled_: no handler found
* `Attribute`: attr doesn't exist or cannot be set
* `Index`: trying to access non-existent index; slices handle these in a weak way (i.e. type conversion)
* `Key`: dict doesn't have key you asked for
* `Name`: identifier not defined
* `Syntax`: kw misspelled, bad indentation, missing closing syntax
* `Type`: give wrong type to function, try to do something you can't (mutate string)
* `Value`: func given correct type but still err ex. `int('5')` can convert string to int but not for all strings e.g. `int('five')`
* user-defined: way to dedupe logging
```python
# SIMPLE IMPL
class EarthquakError(Exception): 
    pass

if not stable_plate:
    raise EarthquakError("earthquake!")
```
```python
# fancy IMPL
class EarthquakError(Exception): 
    def __init__(self, place):
        self.place = place
    def __str__(self):
        return f"uh oh {self.place} has earthquakes"

def move_to(place):
    raise EarthquakError(place)

def get_better_life():
    try:
        move_to(place="california")
    except EarthquakError as e:
        print(e)
```

---

* multiple exceptions https://realpython.com/python-catch-multiple-exceptions/
* match https://www.fluentpython.com/lingo/#subject
* _switch statement replacements_: bisect https://stackoverflow.com/a/61030734/6813490 https://www.youtube.com/watch?v=gllUwQnYVww https://github.com/ralsina/enum_switch https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://docs.python.org/3/faq/design.html#why-isn-t-there-a-switch-or-case-statement-in-python
* _pass_: results in NOP https://wsvincent.com/python-pass-statement/
* returns neither True nor False

https://github.com/guilatrova/tryceratops
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

* _approach_: EAFP (forgivness > perm i.e. try-catch) better than LBYL (C-style if-else) https://docs.python.org/3/glossary.html#term-eafp
* _sink_: 📙 tutorial ch 8 stdlib ch 5 https://realpython.com/courses/python-exceptions-101/ https://sobolevn.me/2019/02/python-exceptions-considered-an-antipattern https://news.ycombinator.com/item?id=19133948

* _swallow msg_: https://stackoverflow.com/a/52625133/6813490
* _warnings_: https://www.reddit.com/r/learnpython/comments/a14ow5/psa_when_developing_set_pythonwarnings/ https://lerner.co.il/2020/04/27/working-with-warnings-in-python/

## math

🗄 `computation.md` theory/numeral systems
🔗 https://github.com/cosmologicon/pywat
📚
* Beazley ch. 3
* Nisan 1-2

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

precedence
* anything in parentheses executed first https://stackoverflow.com/a/10034611
* AND has higher precedence than OR

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

* rounding
```sh
# rounding works as expected
python -c 'print(round(0.0273, 3))'   # 0.027
python -c 'print(round(0.0273, 2))'   # 0.03

# division rounds down when there is a remainder
python -c 'print(14 / 5)'             # 2
python -c 'print(5 / 10)'             # 0

# workaround
python -c 'print(float(15) / float(365))'  # 0.041095890411
```

* _infix operator_: `*` 🗄 `language.md`

FLOATING POINT ARITHMETIC 📙 Van Rossum ch. 15
* comparing floats: `math.isclose(0.1 + 0.2, 0.3)` https://davidamos.dev/the-right-way-to-compare-floats-in-python/
> You can specify the relative tolerance with the rel_tol keyword argument of math.isclose() which defaults to 1e-9. In other words, if abs(a - b) is less than 1e-9 * max(abs(a), abs(b)), then a and b are considered "close" to each other. This guarantees that a and b are equal to about nine decimal places.
* rounding https://stackoverflow.com/a/43661374
```python
# rm decimal
int(1.9)  # 1

# round to closest
round(1.9)  # 2
round(1.94, 1)  # 1.9

# round down
math.floor(1.9)  # 1

# round up
math.ceil(1.1)  # 2
```

* use `localcontext` when dealing w/ decimals https://orbifold.xyz/numbers.html

```python
###
# INTS & FLOATS https://davidamos.dev/the-right-way-to-compare-floats-in-python/ 📙 Van Rossum ch. 15
###

# increment operators https://stackoverflow.com/a/15376520

# + -> calls __add__()
num = 0
num + 1
num  # 0
# += -> calls __iadd__(), can't use in return statement
num = 0
num += 1
num  # 1

def inc(num):
    return num + 1 # ✅
    return num += 1  # ❌

###################################################

# main types
# integers are objects https://pythonspeed.com/articles/python-integers-memory/
int()  # can be as big as your memory can deal with https://realpython.com/python-data-types/#integers
float()

# can also represent binary and complex
0b10  # 2  https://realpython.com/python-data-types/#integers
42+7j  # <class 'complex'> https://realpython.com/python-data-types/#complex-numbers [Saha 1.6]

# conversions -> can't convert float string to int [Saha 1.8]
float('1')  # 1.0
int('1')  # 1
float('1.0')  # 1.0
int('1.0')  # ValueError

# validate floats
1.0.is_integer()  # True
1.3.is_integer()  # False

# integers turn to floats if division https://orbifold.xyz/numbers.html
4/3

# avoid floats with floor division operator [Saha 1.2]
4//3

# variables holding integers btw -5 and 256 are just references to existing obj in Python integer cache https://wsvincent.com/python-wat-integer-cache/ https://arpitbhayani.me/blogs/python-caches-integers
a = 8
b = 8
id(a)  # 4304845536
id(b)  # 4304845536

# negative infinity https://www.interviewcake.com/article/python/big-o-notation-time-and-space-complexity
float("-inf")

# square root via exponent operator [Saha 1.3]
8 ** (1/3)
```
