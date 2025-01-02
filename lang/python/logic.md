# ⛩️

## 参考

📙 Wayne logic for programmers
🗄
* `philosophy.md` logic
* `plt.md` control flow

## 进步

# 🌊 CONTROL FLOW

📜 Van Rossum ch. 4 https://docs.python.org/3/tutorial/controlflow.html

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

* https://www.wrighters.io/intro-to-python-match-statement/
* https://blog.changs.co.uk/customising-pattern-matching-behaviour.html
* https://realpython.com/structural-pattern-matching/
* https://www.youtube.com/watch?v=ASRqxDGutpA
* https://martinheinz.dev/blog/78
* switch statement on steroids https://benhoyt.com/writings/python-pattern-matching/ https://peps.python.org/pep-0634/
> An if...elif...elif...sequence is a substitute for the switch or case statements found in other languages. https://docs.python.org/3/tutorial/controlflow.html
* subject https://www.fluentpython.com/lingo/#subject
* _switch statement replacements_: bisect https://stackoverflow.com/a/61030734/6813490 https://www.youtube.com/watch?v=gllUwQnYVww https://github.com/ralsina/enum_switch https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://pythonbytes.fm/episodes/show/135/macos-deprecates-python-2-will-stop-shipping-it-eventually https://docs.python.org/3/faq/design.html#why-isn-t-there-a-switch-or-case-statement-in-python

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
* _eval_: take string and evaluate as if expression from language
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

* https://docs.python-guide.org/writing/gotchas/#mutable-default-arguments

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

* _inner_:
* considered harmful
> Although writing your helper functions as inner functions achieves the desired result, you’ll probably be better served by extracting them as top-level functions. In this case, you could use a leading underscore (_) in the name of the function to indicate that it’s private to the current module or class. https://realpython.com/inner-functions-what-are-they-good-for/#encapsulation

---

https://realpython.com/python-closure/

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

---

https://calmcode.io/course/lambda/introduction
* https://blog.appsignal.com/2024/10/16/how-to-use-lambda-functions-in-python.html
https://www.youtube.com/watch?v=fZE6ZWde-Os
https://www.pythonmorsels.com/lambda-expressions/
https://lwn.net/Articles/964839/
* https://docs.python.org/3/glossary.html#term-lambda
* _anonymous_: don't assign a name https://treyhunner.com/2018/09/stop-writing-lambda-expressions/
* _constraints_: only for expression i.e. no iteration, conditions https://wsvincent.com/python-lambda-expressions/
* _sink_: https://zenhack.net/2016/12/25/why-python-is-not-my-favorite-language.html https://realpython.com/python-lambda/ https://philip-trauner.me/blog/post/python-quirks-lambdas https://pybit.es/articles/a-practical-example-of-the-pipeline-pattern-in-python/

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

# 🪷 METAPROGRAMMING

🗄
* `django.md` design
* `plt.md` typing
*️ `src.md` dependency injection
📚
* Beazley ch. 9
* Ramalho ch. 22-24
* Perrotta metaprogramming ruby https://news.ycombinator.com/item?id=24935242
> might be worthwhile to buy the first edition

---

🧠 https://chatgpt.com/c/6720e992-860c-8004-a2dd-2cc826753ecf https://claude.ai/chat/0783b7f1-cde6-4e22-b4d3-83199e90fc71
* https://dev.to/karishmashukla/a-practical-guide-to-metaprogramming-in-python-691
* Flask debugger, typing, metaprogramming vs monkey patching https://news.ycombinator.com/item?id=34611969
* _metaprogramming_: functions that manipulate existing code e.g. decorators, inspection 📙 Beazley 329
* function that takes some other code, wraps it, and returns https://medium.com/@saurabhkukade_96600/meta-programming-in-python-7fb94c8c7152
* also synonym for process (build tools, dep mgmt) https://missing.csail.mit.edu/2020/metaprogramming/

## other uses

* inspection
```python
import inspect

def example_function():
    pass

print(inspect.getsource(example_function))
# Output: # def example_function(): pass
```
* _monkey patch_: modify/extend modules/classes at runtime, used for fixing bugs without altering original src
```python
import datetime

def fixed_now():
    return datetime.datetime(2000, 1, 1)

# Monkey patching datetime.now()
datetime.datetime.now = fixed_now
print(datetime.datetime.now())  # Output: 2000-01-01 00:00:00

```

* dynamic attribute generation
```python
class DynamicAttributes:
    def __getattr__(self, name):
        return f"{name} attribute not found!"

    def __setattr__(self, name, value):
        print(f"Setting {name} to {value}")
        super().__setattr__(name, value)

obj = DynamicAttributes()
print(obj.some_attribute)  # Output: some_attribute attribute not found!
obj.new_attr = 42  # Output: Setting new_attr to 42
```

* you can replace or inject new behavior into functions or methods dynamically.
```python
def original_function():
    print("Original function")

def new_function():
    print("New function")

original_function = new_function  # Replacing original function
original_function()  # Output: New function
```

* create a new class dynamically
```python
NewClass = type('NewClass', (object,), {'attr': 42, 'method': lambda self: 'Hello'})
obj = NewClass()
print(obj.attr)      # Output: 42
print(obj.method())  # Output: Hello
```

## decorators

---

https://us.pycon.org/2024/schedule/presentation/85/index.html
* perf https://treyhunner.com/2024/06/a-beautiful-python-monstrosity/
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

## descriptor

---

* https://www.youtube.com/watch?v=mMbVs17Vmo4
* https://docs.python.org/3/library/inspect.html#inspect.ismethoddescriptor https://docs.python.org/3/library/inspect.html#inspect.isdatadescriptor https://docs.python.org/3/library/inspect.html#inspect.ismemberdescriptor
* https://www.fluentpython.com/lingo/#descriptor https://docs.python.org/3/glossary.html#term-descriptor
> Descriptors provide the underlying magic for most of Python’s class features, including @classmethod, @staticmethod, @property, and even the __slots__ specification. By defining a descriptor, you can capture the core instance operations (get, set, delete) at a very low level and completely customize what they do. This gives you great power, and is one of the most important tools employed by the writers of advanced libraries and frameworks. 📙 Beazley 265
> Any method is actually a descriptor. https://www.fluentpython.com/lingo/#bound_method
* uniform acccess principle https://www.fluentpython.com/lingo/
* _attribute_: https://www.fluentpython.com/lingo/#EAFP https://www.fluentpython.com/lingo/#attribute
> other stuff on attributes scattered throughout note
* managed instance, managed class https://www.fluentpython.com/lingo/#managed_instance
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
