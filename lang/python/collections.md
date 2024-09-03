# ⛩️

## 参考

⏲️ https://www.pythonmorsels.com/time-complexities/
📜 https://docs.python.org/3/library/stdtypes.html
💻 https://github.com/python/cpython/tree/main/Include
📚
* Beazley ch. 1
* Van Rossum ch. 5

## 进步

* _24_: split from `python.md`
* _22_: iteration (iterators, generators), big rf
* _19_: first pass (tuple unpacking, iteration, shallow vs. copy)
* _17_: PSF install, PS beginner course

# 🎡 ITERATION

---

https://www.youtube.com/watch?v=Xd760PcgfPg
https://www.youtube.com/watch?v=YC-12-0sXR8
https://martinheinz.dev/blog/103
https://github.com/brohrer/pacemaker

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

## comprehensions

* aka listcomp https://www.fluentpython.com/lingo/#listcomp
* are eager https://www.fluentpython.com/lingo/#list_comprehension
* https://martinheinz.dev/blog/80
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

## iterables

---

https://realpython.com/python-iterators-iterables/ https://www.youtube.com/watch?v=DcCt0dA6q1Q

ITERABLE
* _iterable_: impl `__iter__` where `__iter__` returns iterator https://www.youtube.com/watch?v=EnSu9hHGq5o 23:45
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
* _iterator_: obj that iterates https://www.fluentpython.com/lingo/#iterator https://docs.python.org/3/glossary.html#term-iterator https://bitfieldconsulting.com/golang/iterators
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

## itertools

---

* https://mathspp.com/blog/module-itertools-overview?featured_on=pythonbytes
* module for doing stuff with iterables
* https://www.youtube.com/watch?v=1p7xa_BHYDs
* https://mathspp.com/blog/module-itertools-overview
* more-itertools https://martinheinz.dev/blog/96
* https://github.com/erikrose/more-itertools/ https://www.pythoncheatsheet.org/#itertools-Module https://realpython.com/python-itertools/ https://jeffknupp.com/blog/2018/12/13/how-to-do-just-about-anything-with-python-lists/ https://towardsdatascience.com/tour-of-python-itertools-2af84db18a5e https://florian-dahlitz.de/blog/introduction-to-itertools https://www.blog.pythonlibrary.org/2021/12/07/a-tour-of-pythons-itertools-library/ https://martinheinz.dev/blog/52
```python
# COMBINATIONS AND PERMUTATIONS https://www.youtube.com/watch?v=jUM_Dpt6yu0 https://www.youtube.com/watch?v=jUM_Dpt6yu0
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

RANGE
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

## generators

https://docs.python.org/3/tutorial/classes.html#iterators
https://www.youtube.com/watch?v=tmeksb2fras
https://docs.python.org/3/library/inspect.html#inspect.isgenerator
https://docs.python.org/3/library/inspect.html#current-state-of-generators-coroutines-and-asynchronous-generators

* _generator_: https://realpython.com/introduction-to-python-generators/ 🗄 `language.md` functions
* https://www.fluentpython.com/lingo/#generator https://docs.python.org/3/glossary.html#index-19 https://tushar.lol/post/recursive-generators/
* https://martinheinz.dev/blog/88
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
* 📍 https://medium.com/canopy-tax/sammys-generators-in-python-57e43386b89e https://jeffknupp.com/blog/2013/04/07/improve-your-python-yield-and-generators-explained/

# 🎰 OPERATIONS

## copy

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

## lodash

LODASH-ESQUE LIBRARIES
* https://github.com/mahmoud/boltons https://martinheinz.dev/blog/96
* https://github.com/dgilland/pydash
* https://github.com/dgilland/fnc
* https://github.com/seperman/deepdiff

## slice

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

## sort

📜 https://docs.python.org/3/howto/sorting.html https://realpython.com/python-sort

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

# 🦜 TYPES

SEMANTICS
* _collection_: data structures in which items can be accessed individually https://www.fluentpython.com/lingo/#collection
* _container_: holds ref to other objs e.g. list, tuple, dict https://www.fluentpython.com/lingo/#container
* _flat sequence_: physically stores the values of its items, and not references to other objects e.g. str, bytes, array https://www.fluentpython.com/lingo/#flat_sequence
* _binary sequence_: sequence + byte e.g. byte, bytearray, memoryview https://www.fluentpython.com/lingo/#binary_sequence https://docs.python.org/3/glossary.html#term-bytes-like-object
* `bytearray`: used for HTTP response, passing files around

MUTABLE
* can be altered i.e. updated values still use same obj/ID https://docs.python.org/3/glossary.html#term-mutable
* vs. updated values using new obj/ID https://docs.python.org/3/glossary.html#term-immutable
```python
# MUTABLE
foo = list()
id(foo)  # 4339427648
foo.append("hey")
id(foo)  # 4339427648

# IMMUTABLE
bar = "hi"
bar[0] = "b"  # TypeError: 'str' object does not support item assignment
id(bar)  # 4440141744
bar = "hey"
id(bar)  # 4458076080
```

---

https://www.b-list.org/weblog/2023/dec/24/python-container-types/

* _sequence_: https://www.fluentpython.com/lingo/#sequence https://docs.python.org/3/glossary.html#term-sequence
* _trailing commas_: for last el in collection https://docs.python.org/3/faq/design.html#why-does-python-allow-commas-at-the-end-of-lists-and-tuples https://www.python.org/dev/peps/pep-0008/#when-to-use-trailing-commas

| CLASS   | TYPE    | MUTABLE | HASHABLE       | SUBSCRIPTABLE |  NOTES              |
|---------|---------|---------|----------------|---------------|---------------------|
| list    | seq     | yes     | no             | byes          | for iteration       |
| tuple   | seq     | no      | if el hashable | yes           | list + immutable    |
| string  | seq     | no      | yes            | yes           | tuple + for text    |
| dict    | mapping | yes     | no             | yes           | place for ur stuff  |
| set     | set     | yes     | no             | no            | for set operations  |

SUBSCRIPTABLE
* read by key or index (indexing)
* impl via `__getitem__` https://stackoverflow.com/a/216980
```python
myd = dict(magic=32, larry=33)
myd["magic"]
```
```python
from enum import Enum

class Color(Enum):
    GREEN = "green"

Color.GREEN[0]  # TypeError: 'Color' object is not subscriptable
```

HASHABLE
* hash value never changes (`__hash__`) and can be compared to other objects (`__eq__`) https://docs.python.org/3/glossary.html#term-hashable
* https://stackoverflow.com/questions/1957396/why-dict-objects-are-unhashable-in-python
* https://realpython.com/python-hash-table/
* impl `__eq__` and `__hash__` (immutable) https://www.fluentpython.com/lingo/#hashable 📍📙 Ramalho [84,415]
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

## dict

---

https://treyhunner.com/2021/11/how-to-sort-a-dictionary-in-python/
https://www.youtube.com/watch?v=oUt1feRoyvI
* _mapping_: https://docs.python.org/3/glossary.html#term-mapping
https://realpython.com/python-mappings/
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

## list

https://treyhunner.com/2021/11/how-to-flatten-a-list-in-python/
https://www.youtube.com/watch?v=rdlQzhP71pQ
https://realpython.com/python-list/
https://codeconfessions.substack.com/p/why-do-python-lists-multiply-oddly
* bisect https://www.fluentpython.com/extra/ordered-sequences-with-bisect/ https://martinheinz.dev/blog/106 

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

## set

```python
# CREATE
ur_set = set()  # have to use parens for empty bc braces creates empty dictionary https://docs.python.org/3/tutorial/datastructures.html#sets
ur_set = {1, 1, 2, 3}  # literal
ur_set = set(['foo', 'foo', 'baz', 'foo'])  # constructor

# UPDATE: no way to read sans mutation bc sets are unordered don't support indexing https://stackoverflow.com/q/59825
my_set.add(el)  # push - single
my_set.pop()  # shift
my_set.update(iterable)  # push - n

# DELETE
ur_set.remove('foo_el')

# OPERATIONS 📍 pick SSoT between here and 🗄 `math.md` and 🗄 `sql.md` operations / set
fruit =  {"avocado", "banana", "tomato"}
veg = {"beet", "carrot", "tomato"}
# difference: el unique to first set 📙 Bhargava [150]
fruit - veg  # avocado, banana
# intersection: el shared 📙 Beaulieu [1000]
fruit & veg  # tomato
# symmetric difference: el not shared https://www.idiotinside.com/2017/08/19/set-theory-and-python-tips-tricks/
fruit ^ veg  # avocado, banana, beet, carrot
# union: el across sets sans dupes 📙 Beaulieu [99]
fruit | veg   # avocado, banana, tomato, beet, carrot

# SUB/SUPER
{42, 7}.issubset({13, 7, 42})  # true
{1,2,3}.issuperset({1,2})      # true
```

## string

📙 Beazley ch. 1

---

* https://www.youtube.com/watch?v=EimoZHDcQMA
* textwrap https://martinheinz.dev/blog/108
* f-strings https://martinheinz.dev/blog/103 https://martinheinz.dev/blog/70
* fuzzy comparison: difflib, thefuzz https://martinheinz.dev/blog/96 https://florian-dahlitz.de/articles/create-your-own-diff-tool-using-python

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
* _raw string_: treats backslash as literal, which is why they're seen in Django URLs, `re` https://docs.python.org/3/reference/lexical_analysis.html?highlight=string%20literal#string-and-bytes-literals https://realpython.com/python-raw-strings/ https://martinheinz.dev/blog/103
* _StringIO_: access string as if it were a file (for modules that are used to working with files) https://stackoverflow.com/a/7996541
encoding 🗄 `math.md` encoding https://docs.python.org/3/glossary.html#term-list
* _impl_: `PyBytesObject` (Python 3) `PyStringOjbect` (Python 2) https://www.laurentluce.com/posts/python-string-objects-implementation/ https://docs.python.org/3/whatsnew/2.6.html?highlight=pystringobject#pep-3112-byte-literals https://github.com/python/cpython/blob/45876a90e2663f12b90c2090ec3e48bd97841aae/Objects/bytesobject.c
* _unicode_: UTF8 seems like it was an unmitigated disaster https://news.ycombinator.com/item?id=21536468 https://pymongo.readthedocs.io/en/stable/tutorial.html file names stored as byte strings on OS, as Unicode in Python, PP 20:00 https://www.pythonpodcast.com/beets-with-adrian-sampson-episode-152/ @ 20:00 https://realpython.com/python-encodings-guide/ https://stackoverflow.com/a/2081655/6813490 https://www.b-list.org/weblog/2018/nov/26/case/ http://esr.ibiblio.org/?p=8161 http://python-notes.curiousefficiency.org/en/latest/python3/text_file_processing.html https://news.ycombinator.com/item?id=22931240 https://realpython.com/courses/python-unicode/
* _text encoding_: https://docs.python.org/3/glossary.html#term-text-encoding

## tuple

---

https://martinheinz.dev/blog/103
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
