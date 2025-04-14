# ⛩️

## 参考

📚
* Beck tidy first? https://www.oreilly.com/library/view/the-good-news/9781098170158/
* Mak https://www.manning.com/books/software-design-in-python
* Martin clean code
* Ousterhout philosophy of sofware design
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming 🗄️ Kernighan unix a history

# 🟨 ZA

## refactoring

📙 Fowler refactoring
> you can probably rm the PDF you have of this

---

> Analysis of the curl codebase: “It means that every line in the product source code tree have by now been edited on average 3.5 times.” https://registerspill.thorstenball.com/p/joy-and-curiosity-28

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

---

comments, vibe coding https://news.ycombinator.com/item?id=43576425
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
