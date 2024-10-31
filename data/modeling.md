# ⛩️

## 参考

> All models are wrong, but some are useful - George Box 📙 Zuckerman simons [245]
> Good programmers worry about data structures. https://softwareengineering.stackexchange.com/q/163185
📚
* Alexopoulos semantic https://www.amazon.com/gp/product/1492054275
* Kent data/reality https://www.amazon.com/Data-Reality-Perspective-Perceiving-Information/dp/1935504215

## 进步

🔍 https://drawsql.app/templates
* enum > FK
* modeling payments https://news.ycombinator.com/item?id=36775098
* https://news.ycombinator.com/item?id=41146239&utm_term=comment

ACCESS PATTERNS
* _access pattern_: how you have to query based on schema https://calpaterson.com/non-relational-beartraps.html
* what you're prioritizing e.g. read/write vs. aggregations 📻 Macey 6:10
* _upsert_: insert or update 📙 Bradshaw [46]
* _get-or-create_: `get_or_create()` in Django, aka find_create_find

IMPORTANCE
> Data models are perhaps the most important part of developing software, because they have such a profound effect: not only on how the software is written, but also how we think about the problem that we are solving. 📙 Kleppmann [31]
> This is one reason it's so important to model your domain correctly: if, for example, you make something a property of A when it should be a property of B, the penalty is often that operations that formerly required checking all the As or all the Bs now require checking all the As and all the Bs. https://www.natemeyvis.com/writing/on-quadratic-complexity/
> Take data access patterns very seriously!...it's easy to turn something that should be logarithmic time into polynomial time https://calpaterson.com/activerecord.html

SEMANTICS
* _domain_: thing you're trying to model https://calpaterson.com/non-relational-beartraps.html
* _schema_: model of thing https://calpaterson.com/non-relational-beartraps.html
* general usage: table names + column name/type https://news.ycombinator.com/item?id=22723277
* Postgres usage: container for obj such as table or view https://news.ycombinator.com/item?id=22721914

# 🏺 DATA STRUCTURES

 Conery ch. 7
🗄
* `dbms.md` non-relational
* `dbms.md` internals / datastructures
* `eng.md` store / schemas
* `education.md` design / information design
* `languages.md` typing
* `science.md` metascience / categories
* `sql.md` modeling

https://chatgpt.com/share/67069a06-24cc-8004-9a88-108d568d211a https://www.interviewcake.com/data-structures-reference https://roadmap.sh/datastructures-and-algorithms
* extract data structures
* combine algos and ML
+ category theory

review data structures
* Python collections https://www.30secondsofcode.org/python/p/1 https://realpython.com/python-data-structures/
* array https://www.youtube.com/watch?v=QJNwK2uJyGs
* linked list https://www.youtube.com/watch?v=odW9FU8jPRQ https://news.ycombinator.com/item?id=33473497 https://docs.python.org/3/glossary.html#term-list https://nullprogram.com/blog/2024/07/31/
* stack https://www.youtube.com/watch?v=I5lq6sCuABE
* queue https://www.youtube.com/watch?v=mDCi1lXd9hc
* probabilistic https://www.youtube.com/watch?v=VjFS-_H10bw @ 15:00 https://pypi.org/project/datasketch/

OPERATIONS https://github.com/jamiebuilds/itsy-bitsy-data-structures https://www.interviewcake.com/concept/python3/array
* _lookup_: read
* _insert_: add anywhere
* _delete_: rm anywhere
* _unshift_: add to start
* _push_: add to end
* _shift_: rm from start
* _pop_: rm from end

ADT VS. DATA STRUCTURE
* _abstract data type (ADT)_: interface https://stackoverflow.com/a/1692961 https://en.wikipedia.org/wiki/Abstract_data_type#Examples
* _data structure_: impl https://en.wikipedia.org/wiki/Data_structure https://realpython.com/python-heapq-module/#what-are-heaps
* everything is an ADT e.g. arrays in C stored contiguously in mem but are still types i.e. objects https://stackoverflow.com/questions/50450578/how-are-arrays-implemented-in-c
> when students learn data structures they (1) learn how they work theoretically (2) use off-the-shelf data structures to solve problems and (3) sometimes implement these data structures from scratch. However, I don’t often see classes exploring the off-the-shelf implementations https://akshayr.me/blog/articles/python-dictionaries
* http://infolab.stanford.edu/~ullman/focs.html
* IC bottom up https://www.interviewcake.com/article/python3/data-structures-coding-interview @ RAM https://drewdevault.com/2016/05/28/Understanding-pointers.html
* stack https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-stacks 
* queue https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-queues
* linked list https://medium.com/outco/reversing-a-linked-list-easy-as-1-2-3-560fbffe2088 https://www.youtube.com/watch?v=FSsriWQ0qYE https://realpython.com/courses/working-linked-lists-python/
* array https://medium.com/@bsurajbh/implementing-arrays-with-python-7586206f0b13

PROBABILISTIC
* _probabilistic data structures_: CAP theorem but w/ accuracy, functionality, efficiency https://www.youtube.com/watch?v=VjFS-_H10bw 9:15
* _hyperlog_: https://will-keleher.com/about.html
* _hyperloglog_: distinct el in set https://www.youtube.com/watch?v=VjFS-_H10bw 10:00 https://redis.com/redis-best-practices/counting/hyperloglog/

LINKED LIST https://realpython.com/linked-lists-python/ https://news.ycombinator.com/item?id=26620598
* singly or doubly linked https://lwn.net/Articles/827180/
* _memory_: discontiguous locations = sequential access [2.30]
* _O(1)_: write [Bhargava 2.28] delete [ibid]
* _O(n)_: read [Bhargava 2.28]
> seems like mutative operations only O(1) if items tracked and if everything not the first/last index is untracked then shouldn't it be O(n)? [Bhargava 2.30]
* _piece table_: append-only list used for editing text https://darrenburns.net/posts/piece-table/ https://news.ycombinator.com/item?id=36312488 https://cdacamar.github.io/data%20structures/algorithms/benchmarking/text%20editors/c++/editor-data-structures/
* diff than rope? https://github.com/cessen/ropey https://github.com/prompt-toolkit/pyvim https://web.eecs.utk.edu/~azh/blog/challengingprojects.html
* Myers diff https://github.com/aymanbagabas/go-udiff

ZA
* _commit log_: append-only list of time-ordered records 📙 Jeffrey distributed [6]

## array

ADT/DS
* _ADT_: el in sequence w/ random access, supports all operations 📙 Bhargava 2.30 https://www.interviewcake.com/concept/python3/array
* _impl_: contiguous memory locations

complexity
* _O(1)_: lookup [Bhargava 2.28] push/pop [ibid 5.90]
* _O(n)_: insert (esp. unshift) delete [Bhargava 2.28] slice https://www.interviewcake.com/concept/python3/slice

types
* _one-dimensional (1d)_: `[42, 3, 7]`
* _n-dimensional (nd)_: `[[42, 3, 7], [4, 13]]`

za
* _static array_: manual memory
* _dynamic array_: memory managed; autoresize on backing store overflow (create new larger array, cp over existing); Java `ArrayList` Python `list`; same Big O as array except pushes that require resizing, which are O(n) https://www.interviewcake.com/concept/python3/dynamic-array
* _backing store_: free space in dynamic array https://danluu.com/algorithms-interviews/
* _array slice_: use array subset to form new array; example of out-of-place 🗄 `language.md` memory/stack; O(n) in both time and space https://www.interviewcake.com/concept/python3/slice

## category theory / graph theory

---

> Yes - the value of functional programming isn't that working in OCAML, or F#, or Haskell is 10x as productive as other languages. But that it can teach you worthwhile lessens about designing software that apply equally to imperative languages. Modelling the business domain, reasoning and managing side effects, avoiding common imperative bugs, these are all valuable skills to develop. https://news.ycombinator.com/item?id=40702146
* https://www.amazon.com/How-Bake-Pi-Exploration-Mathematics/dp/0465097677
https://chatgpt.com/c/670933eb-bfe0-8004-aca0-fb048ba5ede0
https://chatgpt.com/c/6709358b-4070-8004-8df9-cd6180a0e70b
https://www.reddit.com/r/math/comments/hqyynh/category_theory_for_programmers/
https://www.reddit.com/r/math/comments/140cbu6/why_are_computer_scientists_good_at_category/
https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/
https://www.reddit.com/r/haskell/comments/1evw5qo/ive_read_through_category_theory_for_programmers/
https://www.blurb.com/b/9621951-category-theory-for-programmers-new-edition-hardco
https://github.com/hmemcpy/milewski-ctfp-pdf
* _category theory_: subset of graph theory https://news.ycombinator.com/item?id=26011025 https://en.wikipedia.org/wiki/Category_theory
https://www.amazon.com/How-Bake-Pi-Exploration-Mathematics/dp/0465097677
* graph theory http://think-like-a-git.net/
* useful math for software: combinatorics, probability, linear algebra, graph theory, statistics https://buttondown.email/hillelwayne/archive/how-knowing-math-helps-you-write-better-software/
* relationship to algebra? https://chatgpt.com/c/671147cf-7ca8-8004-97e1-d49dafe49aaa https://news.ycombinator.com/item?id=41863500

## *FO

QUEUES
* _enqueue_: add to queue https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
* _dequeue_: rm from queue
* _head_: first item in the queue i.e. oldest item https://www.youtube.com/watch?v=RSY85SLXzwk 0:50

---

* _dequeue_: *FO; either; push to each pop from each https://stackoverflow.com/a/38812944/6813490 https://hamatti.org/posts/rotating-turn-order-with-deque/
```python
pass
```

* _stack_: LIFO; post-it https://stackabuse.com/stacks-and-queues-in-python/ https://realpython.com/how-to-implement-python-stack/
```python
stack = [42, 'abc']
stack.append('alice')  # push
stack.pop()  # pop
```

* _queue_: FIFO https://dbader.org/blog/queues-in-python 🔍 cf. 'rotate array'
* _priority queue_: impl w/ heap https://realpython.com/python-heapq-module/
> is_empty checks whether the queue is empty. add_element adds an element to the queue. pop_element pops the element with the highest priority.
```python
queue = [42, 'abc']  # slow bc list is dynamic array https://docs.python.org/3/tutorial/datastructures.html#using-lists-as-queues
queue.append('alice')  # push
queue.pop(0)  # shift

queue = deque([42, 'abc'])  # faster
queue.append('alice')  # push aka queue
queue.popleft()  # shift aka enque
```

## graph

📙 Kun ch. 6 https://en.wikipedia.org/wiki/Graph_theory
🛠 https://github.com/networkx/networkx https://us.pycon.org/2024/schedule/presentation/91/index.html https://pragprog.com/titles/dzcnapy/complex-network-analysis-in-python/ https://github.com/dominikbraun/graph/ https://news.ycombinator.com/item?id=38834780 https://www.hytradboi.com/2022/how-to-query-almost-everything d2 https://chatgpt.com/c/671043db-1354-8004-a127-6b4152994963 https://calmcode.io/datasets/dependencies https://realpython.com/podcasts/rpp/212/
> clean these up https://pycon-archive.python.org/2024/schedule/presentation/52/index.html
🗄
* `info.md` diagrams
* `linux.md` build systems

SEMANTICS
* _graph_: nodes + edges
* _node_: obj in graph
* aka vertex, point📙 Bhargava 6.99 
* _triplet_: https://github.com/getzep/graphiti
* _edge_: conection btw obj
* aka line, branch (in a tree)
* _root_: starting or topmost node in graph/tree
* _path_: series of edges from root to particular node
* _neighbors_: directly adjacent nodes 📙 Bhargava 6.99
* _undirected_: edges go both directions
* aka cyclic 📙 Bhargava 6.106
* _directed_: edge go one direction
* aka acyclic 📙 Bhargava 7.122
* _forced_: https://martinheinz.dev/blog/75
* _knowledge graph_: https://news.ycombinator.com/item?id=27245696
* category theory https://news.ycombinator.com/item?id=28953155 https://www.amazon.com/Joy-Abstraction-Exploration-Category-Theory/dp/1108477224
* doesn't add much value irl https://markusstrasser.org/p/bcd8bded-7136-4bb4-8f97-e8a3a7b6d926/
* graph of blogs https://astralcodexten.substack.com/p/links-for-april-644
* _DAG_: https://github.com/pyjanitor-devs/pyjanitor dependency graphs, build systems https://rhodesmill.org/brandon/slides/2021-06-colombia-remote/ https://en.wikipedia.org/wiki/Technology_tree
* _cycle_: https://endcrawl.com/credits-ordering/
```python
# UNWEIGHTED
friends['me'] = {}  # root
network['me']['jack'] = 'jack kredell'  # children
network['me']['will'] = 'will bartlett'
network['me']['jack']['neil'] = 'neil ellner'  # grandchildren

# WEIGHTED 📙 Bhargava 7.120
network['root'] = {}
network['root']['amber'] = 5
network['root']['jack'] = 2
network['root']['sean'] = 6
```

## map

---

* mind map https://en.wikipedia.org/wiki/Mind_map
* concept map https://en.wikipedia.org/wiki/Concept_map https://cmap.ihmc.us/docs/learn.php

hash tables
* https://realpython.com/python-hash-table/
https://docs.python.org/3/glossary.html#term-dictionary
https://stackoverflow.com/questions/2061222/what-is-the-true-difference-between-a-dictionary-and-a-hash-table
* https://www.youtube.com/watch?v=jalSiaIi8j4
* https://www.fluentpython.com/extra/internals-of-sets-and-dicts/
* https://courses.arpitbhayani.me/hash-table-internals/ https://realpython.com/python-hash-table/
* intersection of two lists https://jvns.ca/blog/2021/09/10/hashmaps-make-things-fast/
* https://calpaterson.com/how-a-sql-database-works.html 📙 Kleppmann 72
* https://news.ycombinator.com/item?id=24232752
* https://thepythoncorner.com/dev/hash-tables-understanding-dictionaries/
* https://www.youtube.com/watch?v=2Ti5yvumFTU
* https://github.com/jamiebuilds/itsy-bitsy-data-structures/blob/master/itsy-bitsy-data-structures.js
* https://www.youtube.com/watch?v=5cU1ILGy6dM
* http://paulmouzas.github.io/2014/12/31/implementing-a-hash-table.html

* ADT: reference array via key https://calpaterson.com/how-a-sql-database-works.html
* impl: BST, red-black https://jvns.ca/blog/2017/09/09/data-structure--the-treap-/

hash tables 🗄 `security.md` `python.md`
* _hash table_: hash function + array to put the results in [Bhargava 5.76-8, 5.90-2, 11.213]
* hashing https://blog.codinghorror.com/url-shortening-hashes-in-practice/
* aka map, dictionary, associative array https://docs.python.org/3/glossary.html#term-dictionary
* alternatives incl. BST, skip list https://stackoverflow.com/a/301822 📙 Skiena 12.1

bloom filter https://www.youtube.com/watch?v=qZNJTh2NEiU https://www.youtube.com/watch?v=V3pzxngeLqw
* _bloom filter_: like a hash table except takes up a lot less space and false positives are possible
* use case is to see whether item already part of a very large set e.g. whether a key exists in a database 📙 11.210-11
* https://vprusso.github.io/blog/2017/bloom-filters-and-pokemon/ 📙 Kleppmann 79 https://onatm.dev/2020/08/10/let-s-implement-a-bloom-filter/ http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html https://luminousmen.com/post/building-a-bloom-filter

https://tenthousandmeters.com/blog/python-behind-the-scenes-10-how-python-dictionaries-work/
* _operations_: lookup, insert, delete
* _O(1)_: Bhargava 5.90
* _hash aggregate_: aggregate keys e.g. A 1 B 2 A 4 -> A 5 B 2 https://veekaybee.github.io/2021/06/06/hashaggregate/

## 🌳 tree

🔗
* https://en.wikipedia.org/wiki/Tree_(data_structure)
* HDF5 https://en.wikipedia.org/wiki/Hierarchical_Data_Format https://github.com/rhuygen/hdf5_ui
🗄️
*️ `km.md` notes / tooling
*️ `language.md` compiler
*️ `protocols.md` file fmt
* `science.md` metascience / categories

---

* _s-expression_: nested list in which the elements are both data and src https://chatgpt.com/c/671f995f-e7e4-8004-9721-19cc903c3e98 akin to XML https://en.wikipedia.org/wiki/S-expression#Parsing https://news.ycombinator.com/item?id=31840852
* _treemap_: https://github.com/niyue/skillmap https://github.com/nikolaydubina/go-cover-treemap https://github.com/imsnif/diskonaut https://calmcode.io/labs/pytest-duration-insights
https://buttondown.com/hillelwayne/archive/maybe-software-engineers-could-learn-something/ https://en.wikipedia.org/wiki/Hypernymy_and_hyponymy

WALKING
* BYO https://realpython.com/directory-tree-generator-python/
* _frangipanni_: https://github.com/birchb1024/frangipanni
* doesn't work yet for m1 macOS https://github.com/birchb1024/frangipanni/issues/21
* install https://github.com/birchb1024/frangipanni/issues/22
* _snapdiff_: snapshot https://www.jotaen.net/iE3XC/snapdiff-compare-directory-trees-on-CLI/
* _walkdir_: https://github.com/BurntSushi/walkdir

🛠 https://github.com/joowani/binarytree https://github.com/queelius/AlgoTree
🔗 https://en.wikipedia.org/wiki/Phylogenetic_tree
> trees are easy to deal with and understand, but graphs are more "open" with what you can do https://news.ycombinator.com/item?id=27662089

SEMANTICS
* _tree_: type of graph 📙 Bhargava 6.113
* _parent_: node w/ children
* _leaf_: node with no children https://www.youtube.com/watch?v=5cU1ILGy6dM [0:30]
* _height_: distance from root to given leaf measured in levels https://www.youtube.com/watch?v=Aagf3RyK3Lw [0:15] https://www.youtube.com/watch?v=dM_JHpfFITs [1:10]
* _subtree_: tree nested w/ root tree https://www.youtube.com/watch?v=5cU1ILGy6dM
* _completeness_: know how many elements in each layer except the last one https://realpython.com/python-heapq-module/#heaps-as-lists-in-the-python-heapq-module
* _treemap_ https://news.ycombinator.com/item?id=36868940 https://en.wikipedia.org/wiki/Treemapping

### builders

🗄️
* `html-css.md` SSG
* `protocols.md` JSON
* `km.md` notes / tooling
* `info.md` viz / system

* features: dynamic creation via TUI, hot reload viz, tree merge, Vim traversal, symlink nodes
* BYO https://realpython.com/directory-tree-generator-python/
* _anytree_: ✅ https://github.com/c0fec0de/anytree
* repos https://github.com/zachvalenta/capp-prod-cat https://github.com/zachvalenta/capp-prod-cat-alt
* symlink node https://anytree.readthedocs.io/en/stable/api/anytree.node.html#anytree.node.symlinknode.SymlinkNode https://github.com/c0fec0de/anytree/pull/189 https://github.com/zachvalenta/anytree/blob/main/anytree/exporter/dictexporter.py 🗄️ `runtime.md` pip
* multi-dimensional https://anytree.readthedocs.io/en/stable/tricks/multidim.html https://en.wikipedia.org/wiki/MultiValue_database
* dict export https://anytree.readthedocs.io/en/stable/exporter/dictexporter.html
* json export https://anytree.readthedocs.io/en/stable/exporter/jsonexporter.html
* _basilk_: https://github.com/GabAlpha/basilk
* _d2_: grid diagram https://d2lang.com/tour/grid-diagrams
* _Haystack_: 🎯 tree follower https://news.ycombinator.com/item?id=41648564
* _hmm_: ✅ https://github.com/nadrad/h-m-m https://github.com/zachvalenta/capp-prod-cat-markmap
* _markmap_: ✅ Markdowm https://github.com/markmap/markmap
* _Leo_: 🎯 strange beast https://news.ycombinator.com/item?id=27615225 https://github.com/leo-editor/leo-editor
* _treebuilder_: 🎯 https://github.com/fdieulle/treebuilder

### semantics

* _node_: element of tree
* _root_: node w/out parent
* _parent_: node w/ children
* _leaf_: node with no children
```sh
├── actuator  # parent
│   └── damper
│   └──── fire safety  # leaf
```
* _child_: node directly below parent
* _grandchild_: node two levels below parent
* _grandparent_: node two levels above parent
```sh
├── actuator  # parent to damper, grandparent to fire safety
│   └── damper  # child to actuator, parent to fire safety
│   └──── fire safety  # child to damper, grandchild to actuator
```
* _height_: distance from root to given leaf measured in levels
* _subtree_: tree nested w/in root tree
* _traversal_: movement through the tree

### types

* _ordered_: Markdown, DOM, fs, AST, config mgmt, version control, NLP parse trees, task mgmt, window mgmt https://nikitabobko.github.io/AeroSpace/guide#tree https://chatgpt.com/c/67202b04-6aec-8004-92c2-1af3c5fce7de
* _b-tree_: two branches for each node https://stackoverflow.com/a/6380314 🗄 `db.md` indexing https://avi.im/blag/ https://build-your-own.org/ https://build-your-own.org/database/04_btree_code_1 https://planetscale.com/blog/btrees-and-database-indexes
* balanced = min height and max height differ by 1 (at most) https://www.youtube.com/watch?v=Aagf3RyK3Lw @ 0:50
```sh
  1
 / \
2   3
```
* _binary search tree (BST)_: left child only contains values less than parent and vice versa for right child 
* no random access but Big O average-case for search good as binary search + faster writes 📙 Bhargava 11.205
```sh
  2
 / \
1   3

     david
    /     \
adit       manning
          /       \
      maggie      mike
```
* _treap_: BST + each node has value + priority https://jvns.ca/blog/2017/09/09/data-structure--the-treap-/
* _heap_: tree + heap property e.g. max (parent node >= child nodes) min (parent node >= child nodes) https://www.youtube.com/watch?v=dM_JHpfFITs
* used for priority queue 🗄 *FO https://en.wikipedia.org/wiki/Heap_(data_structure)
```
    9
   / \
  5   7
 /     \
4       6
```
* _trie (prefix tree)_: typically used to store words https://www.youtube.com/watch?v=7XmS8McW_1U https://medium.com/basecs/trying-to-understand-tries-3ec6bede0014 https://blog.cloudflare.com/pingora-saving-compute-1-percent-at-a-time/ https://news.ycombinator.com/item?id=41501496
* _BPS tree_: formed from binary space partitioning https://twobithistory.org/2019/11/06/doom-bsp.html
* _minimum spanning tree (MST)_: edges to connect every node in weight graph while minimizing edge weight 📙 Christian chapter 8
* _red-black tree_: BST that keeps itself balanced 📙 Bhargava 11.206
* used for SSTables 📙 Kleppmann 78
* _multitree_: https://github.com/climech/grit
* _splay tree_: red-black + recently accessed are fast to lookup again 📙 Bhargava 11.206

# 🗺️ NON

🗄️ `algos.md` data structures
📙 Kleppmann ch. 2

> There are data stores that are also used as message queues (Redis), and there are message queues with database-like durability guarantees (Kafka), so the boundaries between the categories are becoming blurred 📙 Kleppmann [12]

* modeling from different angles https://www.openmymind.net/2011/7/5/Rethink-your-Data-Model/

---

* Datomic (Hickey), datalog/prolog https://news.ycombinator.com/item?id=21742222 https://kevinlynagh.com/newsletter/2022_04_on_datalog_application_databases/ https://news.ycombinator.com/item?id=31154039 https://news.ycombinator.com/item?id=35094017 https://news.ycombinator.com/item?id=35727967 https://clojure.org/news/2023/08/04/next-rich https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need https://news.ycombinator.com/item?id=41642969
* can be a problem is you need to change the PK https://calpaterson.com/non-relational-beartraps.html
> Changing the primary key of a table is a surprisingly common activity. In truth, it's pretty easy to pick something that initially looks like it will be unique but which later turns out to not be unique...Unfortunately, in many non-relational database systems the primary key is "special". For example, Dynamo-style systems will use the primary key to decide which of the partitions the record will go on.
* _polyglot persistence_: using multiple types of data stores 📙 Kleppmann 2.29 because choosing just one is no fun :) https://old.reddit.com/r/learnpython/comments/glbuog/whats_is_your_decision_process_between_csv_json/
* _block_: https://news.ycombinator.com/item?id=27200177
* immutable https://github.com/codenotary/immudb

## column

📙 Kleppmann chapter 3
🗄 `computation.md` encoding/CSV, Parquet

* _column store_: not row-oriented (like OLTP)
* can do in Sqlite? https://news.ycombinator.com/item?id=39207570&utm_term=comment
* 不明觉厉 https://news.ycombinator.com/item?id=36571110
* e.g. instead of looking for all `price` values by iterating over every sale record, just grab `price` column 📙 Kleppmann 96
* ❓ stores data differently on disk https://nchammas.com/writing/database-access-patterns
* in order to reconstruct a row, everything in row must be stored as nth in column 📙 Kleppmann 100
> Neither Parquet nor ORC files existed prior to 2012. These file formats were instrumental in making analytics fast on Hadoop. Prior to these formats, workloads were largely row-oriented. If you needed to transform TBs of data and could do so in a parallel fashion then Hadoop did a good job of that. MapReduce was a framework often used for this purpose. What columnar storage offered was a way to analyse TBs of data in seconds. This proved to be a more valuable proposition to more businesses. Data Scientists may only need a small amount of data to produce insights but they'll need to look over a data lake with potentially PBs of data to pick out what they need first. Columnar analytics is key for them to build the data fluency needed to know what to cherry-pick. https://tech.marksblogg.com/is-hadoop-dead.html
* _wide column store_: ❓

dbms https://en.wikipedia.org/wiki/List_of_column-oriented_DBMSes
* Cassandra https://stackoverflow.com/q/13010225 https://www.youtube.com/watch?v=J-cSy5MeMOA 📙 Kleppmann 99 https://news.ycombinator.com/item?id=28292369 https://simonwillison.net/2021/Aug/24/how-discord-stores-billions-of-messages/
* _Bigtable_: wide table = document store in SQL https://en.wikipedia.org/wiki/Wide-column_store
* _HBase_: Hadoop db

## document

---

📙 Kleppmann 2.28-42

> The thrust of it is that databases that are in the same genre as DynamoDB - which includes Cassandra and MongoDB - are fantastic if - and this is a load bearing if: You know exactly what your app needs to do, up-front. You know exactly what your access patterns will be, up-front. You have a known need to scale to really large sizes of data. You are okay giving up some level of consistency. This is because this sort of database is basically a giant distributed hash map. The only operations that work without needing to scan the entire database are lookups by partition key and scans that make use of a sort key. Whatever queries you need to make, you need to encode that knowledge in one of those indexes before you store it. You want to store users and look them up by either first name or last name? Well you best have a sort key that looks like `$FIRST_NAME $LAST_NAME>`. Your access patterns should be baked into how you store your data. If your access patterns change significantly, you might need to reprocess all of your data. https://mccue.dev/pages/8-16-24-just-use-postgres

document store
* _document_: JSON "obj"
* replaces row as paradigm 📙 Bradshaw [3]
* _schema_: structure of document https://docs.mongodb.com/realm/schemas/
* not fixed i.e. inconsistent intra-collection 📙 Bradshaw [3]
* _document reference_: UUID 📙 Kleppmann 3.38
* _field_: key
* _subdocument_: document key whose value is itself a document https://youtu.be/SM9gJv08dm0 1:20
* aka embedded 📙 Bradshaw [174]
* _collection_: group of documents

design
* 1-M w/in document itself
* M-M via document reference 📙 Kleppmann 3.38
* joins https://news.ycombinator.com/item?id=22834036
* good for 1-M or no relationships 📙 Kleppmann 2.49
* flexiblity: schema per doc aka schemaless/schema-on-read, obviates need for migrations 📙 Kleppmann 2.63, 4.111
* easier to scale/shard apparently, locality 📙 Kleppmann 2.32
* transactions only at level of single document https://docs.mongodb.com/v3.4/core/write-operations-atomicity/
* easy to have dupes 📙 Kleppmann 2.33
* hands off processing to application, so it's both slower in dev time and execution time 📙 Bradshaw [8]

DBMS
* BYO https://notes.eatonphil.com/documentdb.html
* _CouchDB_: good at replication https://www.dataengineeringpodcast.com/couchdb-document-database-episode-124/ 7:15 
* _Dante_: 🎯 embedded https://github.com/senko/dante
* _Lungo_: 🎯 embedded, Mongo compatible Golang impl https://github.com/256dpi/lungo
* _Mongo_: OSS alternative https://github.com/FerretDB/FerretDB https://pythonbytes.fm/episodes/show/318/gil-how-we-will-miss-you
* _Polo_: embedded https://github.com/vincentdchan/PoloDB
* _Postgres_: JSON
* _TinyDB_: 🎯 embedded https://github.com/msiemens/tinydb
* not atomic but potential workaround https://tinydb.readthedocs.io/en/latest/extensions.html#tinyrecord

HIERARCHICAL
* _hierarchical database_: document store + tree structure i.e. child only has one parent 📙 Takahashi [39] Beaulieu [2]
* too rigid for a data store https://stratechery.com/2016/oracles-cloudy-future/ https://twobithistory.org/2017/12/29/codd-relational-model.html
* e.g. file system, DNS https://www.postgresql.org/docs/12/tutorial-concepts.html 📙 Kleppmann 2.36-38
* used in Zookeeper https://www.youtube.com/watch?v=Vv4HpLfqAz4 8:50
* can be done in relational as well https://hoverbear.org/blog/postgresql-hierarchical-structures/
* _IMS_: https://twobithistory.org/2017/10/07/the-most-important-database.html

## graph

🗄 `algos.md` graph

* https://calmcode.io/datasets/dependencies
* _EdgeDB_: graph-relational = no impedance mismatch but still relational https://news.ycombinator.com/item?id=30290225
* written in Python on top of Postgres https://talkpython.fm/episodes/show/355/edgedb-building-a-database-in-python
* _network database_: similar to graph https://stackoverflow.com/a/52325525 📙 Takahashi [2.39]
* anything that would have ever been network is now SQL https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37 📙 Kleppmann [2.36]

DBMS
* embedded w/ Datalog https://news.ycombinator.com/item?id=33518320 https://github.com/cozodb/cozo
* Mongo offers as well https://www.mongodb.com/databases/mongodb-graph-database
* SQLite, Postgres https://news.ycombinator.com/item?id=35386948
* _Age_: Postgres extension https://github.com/apache/age
* _Janus_: distributed, OSS https://github.com/JanusGraph/janusgraph
* _SQLite_: https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need
* _Tao_: distributed https://news.ycombinator.com/item?id=29045443 https://www.micahlerner.com/2021/10/13/tao-facebooks-distributed-data-store-for-the-social-graph.html

QUERY LANGUAGES
* _Cypher_: declarative
* _GQL_: emerging standard https://stackoverflow.com/q/13824962 https://www.youtube.com/watch?v=h8cyPIEfxQY 11:30
* _Gremlin_: wrapper over Neo4J Java API

---

* https://www.hytradboi.com/2022/how-to-query-almost-everything
* https://www.kaseyklimes.com/notes/2019/10/16/an-augmented-mind-designing-a-personal-knowledge-base-with-notion
* _use cases_: good at relationships btw heterogenous data ("does Alice follow Bob?") w/out a million joins  📙 Kleppmann 2.49, 2.63 bad at aggregates or anything that deals w/ a few attr over many records; used for networks (IAM, knowledge mgmt, Git, recommendation engine) https://www.youtube.com/watch?v=h8cyPIEfxQY 14:30
* _dbms_: Tiger Graph, Dgraph https://softwareengineeringdaily.com/2021/01/19/dgraph-native-graphql-database-with-manish-jain/ Memgraph, Terminus db, Neo4J https://media.pragprog.com/titles/pwrdata/neo4j.pdf embedded https://github.com/CodyKochmann/graphdb https://github.com/dpapathanasiou/simple-graph cache for dgraph https://github.com/dgraph-io/ristretto
* _OGM_: ORM for graphs https://www.youtube.com/watch?v=h8cyPIEfxQY 12:30

* _property graph_: vertex (id, dict of properties, and list of incoming/outgoing edges) edge (id, dict of properties, start/end vertices and descriptive label) 📙 Kleppmann 2.50
* _triple-store_: subject (vertex) predicate, object (value or another vertex) 📙 Kleppmann 2.55 used by Datomic (Datalog query language) 📙 ibid 2.50, 60, 63 https://github.com/instantdb/instant
* _RDF (resource description framework)_: triple store for semantic web 📙 Kleppmann 2.57 SPARQL query language 📙 ibid 59 https://twobithistory.org/2020/01/05/foaf.html
* _types_: https://stackoverflow.com/a/59532041/6813490
* visualization https://github.com/shahinrostami/chord https://github.com/plotly/falcon
* _sink_: https://github.com/brettkromkamp/contextualise https://www.youtube.com/watch?v=GekQqFZm7mA https://www.denizcemonduygu.com/philo/ http://aosabook.org/en/500L/dagoba-an-in-memory-graph-database.html https://pragprog.com/book/pwrdata/seven-databases-in-seven-weeks-second-edition

## key

---

REDIS 📙 https://www.openmymind.net/2012/1/23/The-Little-Redis-Book/
> just use postgres https://martinheinz.dev/blog/105
* https://www.youtube.com/watch?v=WQ61RL1GpEE
* https://www.youtube.com/watch?v=5TRFpFBccQM
* implementation http://aosabook.org/en/nosql.html
* https://github.com/dragonflydb/dragonfly
* test/mock https://github.com/cunla/fakeredis-py
* use Postgres as impl https://github.com/alash3al/redix
* governance https://news.ycombinator.com/item?id=23689549
* key expiration https://news.ycombinator.com/item?id=30099572
* alternative https://github.com/dragonflydb/dragonfly https://github.com/buraksezer/olric#installing
* embedded https://github.com/symisc/vedis https://news.ycombinator.com/item?id=19464144
> You can either set Redis up as a "data-structures" server or you set it up right as a cache. You can't do both. If you choose to use Redis as your cache, ensure that the cache instance is only serving as your cache. Your inter-system message bus should be on a different Redis with a different configuration. https://calpaterson.com/ttl-hell.html

MEMCACHED
* _is?_: volatile cache https://news.ycombinator.com/item?id=23689549 aka application caching layer
* _how?_: distributed hash table i.e. n instances of app share 1 distributed instance of memcached
* _why?_: so you don't have to read from db
* _disadvantages_: doesn't track cache misses; meant for simple data, not tables or objects; not durable http://aosabook.org/en/nosql.html
* _sink_: https://realpython.com/python-memcache-efficient-caching/ https://github.com/thadeusb/flask-cache Django has OOB support for memcached https://docs.djangoproject.com/en/2.1/topics/cache/

* _KV store_: hash map + persistence 📙 Kleppmann [72]
* distributed KV store used for service discovery (etcd) ()
* used for metadata, counters
> ZippyDB serves a number of use cases, ranging from metadata for a distributed filesystem, counting events for both internal and external purposes, to product data that’s used for various app features https://engineering.fb.com/2021/08/06/core-data/zippydb/
* impl: hash index; faster not bc they don't have to go to disk but bc don't have to translate in-mem data structure to something that can be written to disk 📙 Kleppmann [89]
* typed values allow for in/decrement, push/pop from list
* used for caching db result set e.g. memcached 📙 Kleppmann [89] https://github.com/akrylysov/pogreb
* dbms: embedded https://github.com/patx/pickledb https://github.com/spacejam/sled https://github.com/charmbracelet/skate https://github.com/dgraph-io/badger disk for storage https://github.com/peterbourgon/diskv
* RocksDB, memcached used as storage for distributed KV https://github.com/bitleak/kvrocks https://engineering.fb.com/2021/08/06/core-data/zippydb/ https://www.micahlerner.com/2021/05/31/scaling-memcache-at-facebook.html
* BYO: https://aosabook.org/en/500L/dbdb-dog-bed-database.html https://notes.eatonphil.com/2023-05-25-raft.html Bitcask https://github.com/avinassh/py-caskdb
> In short, keys are stored in a hash table in RAM, k/v pairs are written to log files. Dead simple, but powerful enough. https://news.ycombinator.com/item?id=31306678

za
* _object store_: KV in which K is ID and V is blob (file, binary) 🗄 `infra.md` AWS/S3
* can only create/update, not append https://stackoverflow.com/a/47524241
* sink https://ceph.io/ceph-storage/ https://github.com/minio/minio https://stackoverflow.com/questions/56627446/docker-compose-how-to-use-minio-in-and-outside-of-the-docker-network https://alexwlchan.net/2020/08/s3-keys-are-not-file-paths
* _flat file_: meant for config, no way to represent relationships or handle concurrency (e.g. prevent dirty read); some structure via delimiters, new lines https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37

## time series

🗄
* `math.md` graphs / uplot
* `infra.md` analytics

todo
* Postgres https://tembo.io/blog/pg-timeseries
* https://www.youtube.com/watch?v=nT6UsVgJ0xw
* https://www.youtube.com/watch?v=Z6pghPlZ1vQ
* time-weighted average https://blog.timescale.com/blog/what-time-weighted-averages-are-and-why-you-should-care/?
* https://www.honeycomb.io/blog/time-series-database/
* https://news.ycombinator.com/item?id=28901063
* https://www.influxdata.com/blog/start-python-influxdb
* Homebrew analytics https://docs.brew.sh/Analytics

basics
* _time series_: KV in which K is time https://en.wikipedia.org/wiki/Time_series_database
* used for monitoring 🗄 `system.md` https://github.com/VictoriaMetrics/VictoriaMetrics
* _panel data_: timeseries for individuals https://en.wikipedia.org/wiki/Panel_data

libs
* _darts_: https://github.com/unit8co/darts/
* _kats_: https://github.com/facebookresearch/kats
* _sktime_: https://github.com/alan-turing-institute/sktime

dbms
* _Influx_: https://softwareengineeringdaily.com/2019/08/21/time-series-databases-with-rob-skillington/ https://softwareengineeringdaily.com/2021/08/19/influxdata-time-series-data-with-russ-savage/
* _Husky_: event store https://www.datadoghq.com/blog/engineering/husky-deep-dive/
* _Lin_: https://github.com/lindb/lindb
* _Timescale_: built on Postgres https://blog.timescale.com/blog/how-postgresql-aggregation-works-and-how-it-inspired-our-hyperfunctions-design-2/ https://softwareengineeringdaily.com/2021/06/28/timescale-time-series-databases-with-mike-freedman/
* _tstorage_: embedded https://github.com/nakabonne/tstorage BYO https://nakabonne.dev/posts/write-tsdb-from-scratch/ https://news.ycombinator.com/item?id=27730854
* _Whisper_: embedded db for Graphite https://github.com/graphite-project/whisper

## vector

* for recommendation systems, NLP
* _ChromaDB_: https://www.youtube.com/watch?v=QSW2L8dkaZk&list=PL58zEckBH8fA-R1ifTjTIjrdc3QKSk6hI&pp=iAQB

---

* LanceDB https://www.youtube.com/watch?v=hB7sGE0W8CI
* https://news.ycombinator.com/item?id=41985176
* https://news.ycombinator.com/item?id=35550567 https://garybake.com/vector_databases.html Pinecone https://news.ycombinator.com/item?id=35826929 https://code.dblock.org/2023/06/16/getting-started-with-vector-dbs-in-python.html https://news.ycombinator.com/item?id=37747534 https://realpython.com/chromadb-vector-database/ https://github.com/asg017/sqlite-vec https://github.com/qdrant/qdrant https://www.youtube.com/watch?v=awIm3rQOBxE

# 🕸️ RELATIONAL

RELATIONS
* _relationship_: what ties tables together https://twobithistory.org/2017/12/29/codd-relational-model.html
* _relational model_: Codd 📙 Kent data/reality [155] Beaulieu [5]
* relational algebra https://news.ycombinator.com/item?id=39753749
> when embedding would result in duplication of data but would not provide sufficient read performance advantages to outweigh the implications of the duplication.
> to represent more complex many-to-many relationships
> to model large hierarchical data sets
> In the database community it has been conventional wisdom for nearly half a century now (basically since the invention of the relational model) that in designing your database schema you should be careful to avoid any kind of redundancy. That's what database normalization theory is all about. https://www.cell-lang.net/relations.html
* _denormalization_: when speed more of a concern 📙 Conery imposter [320] Kleppmann [491] Manga [62]
* _denormalized query engine_: subset of data for search https://speakerdeck.com/simon/the-denormalized-query-engine-design-pattern https://simonwillison.net/2020/Dec/19/dogsheep-beta/
* _locality_: proximity of data relevant to an entity 📙 Kleppmann [32] 🗄 `db.md` document
* _embeded_: NoSQL https://www.mongodb.com/docs/manual/core/data-model-design/
> you have "contains" relationships between entities
> you have one-to-many relationships between entities, in these relationships the "many" or child documents always appear with or are viewed in the context of the "one" or parent documents.
> embedding provides better performance for read operations, as well as the ability to request and retrieve related data in a single database operation.

## 1-1

* = sole ownership
* impl: attr, separate table https://support.airtable.com/hc/en-us/articles/218734758#onetoone
* example: person-SSN, country-capital https://stackoverflow.com/a/15037461
* less common than you'd think https://www.b-list.org/weblog/2024/aug/27/highlander-problem/

## 1-M
* = ownership
```sql
CREATE TABLE team(
    team_id INTEGER PRIMARY KEY,
);

CREATE TABLE player(
    player_id INTEGER PRIMARY KEY,
    team_id INTEGER,
    FOREIGN KEY (team_id) REFERENCES team(team_id)
);
```

## M-M

* = collaboration
* aka join table, junction table https://stackoverflow.com/a/3419868
```sql
CREATE TABLE band(
    band_id INTEGER PRIMARY KEY,
);

CREATE TABLE musician(
    musician_id INTEGER PRIMARY KEY,
);

CREATE TABLE band_musician(
    bm_id INTEGER PRIMARY KEY,
    band INTEGER,
    musician INTEGER,
    FOREIGN KEY (band) REFERENCES band(band_id)
    FOREIGN KEY (musician) REFERENCES band(musician_id)
);
```

## normalization

* _normalization_: process of extracting entities from other entities https://en.wikipedia.org/wiki/Database_normalization#Normal_forms
* _form_: step in normalization
* avoids redundancy (no `author` in `book` bc you'd repeat Jane Austen for each novel)
* saves space (no dupes) 📙 Kleppmann [33]
* howto: one big mess and decompose from there, think of example queries
* _1NF_: 1 value for each attr
* aka atomic 📙 Takahashi [58] Winand [6]
```sql
-- pre-1NF: n values for each record
insert into danzi(item) values ('quesidilla, churro');

-- 1NF: 1 value for each record
insert into danzi(item) values ('quesidilla');
insert into danzi(item) values ('churro');
```
* _2NF_: non-PK must be related to PK 📙 Conery imposter 316 Takahashi 3.63 https://stackoverflow.com/a/724032
* symptom is redundancy (value repeats across records w/out reference to FK) and therefore anomaly (value could be mispelled) 📙 Karwin [289]
```sql
-- TITLE dependent on COURSE_ID but unrelated to SEMESTER_ID
CourseID | SemesterID | #Places  | Title        |
------------------------------------------------|
IT101    |   2009-1   | 100      | Programming  |
IT101    |   2009-2   | 100      | Programming  |
IT102    |   2009-1   | 200      | Databases    |
IT102    |   2010-1   | 150      | Databases    |
IT103    |   2009-2   | 120      | Web Design   |
```
* _3NF_: don't get difference from 2NF 📙 Conery imposter 318 Karwin 291
* the generally accepted level of normalization 📙 Winand 1.4
* https://stackoverflow.com/a/724013/6813490 https://www.mikealche.com/software-development/a-humble-guide-to-database-schema-design
```sql
-- todo
```
* _5NF (Boyce-Codd)_: when you're going too far 📙 Winand [5]

## ORM

---

* _ORM (object-relational mapper)_: obj as frontend to relational data store
* why: dbms portability, terseness, getting data into obj https://monadical.com/posts/why-use-orm.html https://news.ycombinator.com/item?id=37118633
* why not: SQL is more durable, more help on SO, easier for complicated relationships https://news.ycombinator.com/item?id=21961214 https://eli.thegreenplace.net/2019/to-orm-or-not-to-orm/ https://sirupsen.com/stop-relying-on-your-orm-and-learn-sql https://news.ycombinator.com/item?id=36497613
* write thin DSL over ORM vs. modifying default ORM methods https://rtpg.co/2016/09/12/orms-are-scary.html
* _data mapper_: https://en.wikipedia.org/wiki/SQLAlchemy https://www.openmymind.net/2011/11/18/I-Just-Dont-Like-Object-Mappers/
* _active record_: wrapper (row + DSL) https://www.martinfowler.com/eaaCatalog/activeRecord.html http://calpaterson.com/activerecord.html https://github.com/sdispater/orator
* ActiveRecord for Golang https://github.com/volatiletech/sqlboiler
* _N+1 problem_: https://roadmap.sh/backend https://macwright.org/2020/05/10/spa-fatigue.html https://stackoverflow.com/q/97197/6813490 https://www.sqlalchemy.org/features.html https://tech.yplanapp.com/2016/09/26/introducing-django-perf-rec/ https://www.youtube.com/watch?v=uCbFMZYQbxE https://github.com/jmcarp/nplusone https://news.ycombinator.com/item?id=26151302 https://fly.io/blog/introducing-litefs/ https://github.com/superfly/litefs
> The 1+N database anti-pattern is common: fetch some rows from the database then re-fetch specific rows to get all the items. An ORM can hide this away and make you not realize it is happening. https://suor.github.io/blog/2023/03/26/ban-1-plus-n-in-django/
* solved with eager loading https://news.learnenough.com/eager-loading
* _impedance mismatch_: difficulty of object-relational mapping [Kleppmann 1.33] multiple ways to aproach http://blogs.tedneward.com/post/the-vietnam-of-computer-science/
> In the database community it has been conventional wisdom for nearly half a century now (basically since the invention of the relational model) that in designing your database schema you should be careful to avoid any kind of redundancy. That's what database normalization theory is all about. For some unfathomable reason, the same kind of thinking is never (or almost never) applied to software construction, even though it would be as beneficial (possibly even more so) as it is for databases. So, before we countinue our discussion, it's a good idea to talk a bit about redundancy, and to explain what's so harmful about it. https://www.cell-lang.net/relations.html

# 🟨 ZA

## taxonomy of modeling

❗️ https://en.wikipedia.org/wiki/Information_science https://en.wikipedia.org/wiki/Ontology_(information_science)
🔗 https://en.wikipedia.org/wiki/Data_modeling
🧠 https://chatgpt.com/c/672d1eca-8194-8004-a7bb-ab67c03b2a58

https://en.wikipedia.org/wiki/Domain_model

```sh
# start here https://en.wikipedia.org/wiki/Three-schema_approach
├── Conceptual # https://en.wikipedia.org/wiki/Conceptual_schema
│   └── Entity-Relationship (ER) # https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model https://en.wikipedia.org/wiki/Relational_Model/Tasmania https://en.wikipedia.org/wiki/Information_model
│   └── Object-Oriented  # https://en.wikipedia.org/wiki/Object%E2%80%93role_modeling
│   └── Semantic Data # https://www.amazon.com/gp/product/1492054275 https://en.wikipedia.org/wiki/Semantic_data_model semantic web https://en.wikipedia.org/wiki/Semantic_technology https://en.wikipedia.org/wiki/Relational_Model/Tasmania
│       ├── Ontologies
│       ├── Taxonomies
│       ├── Conceptual Graphs # https://en.wikipedia.org/wiki/Conceptual_graph https://en.wikipedia.org/wiki/Concept_map
├── Logical # https://en.wikipedia.org/wiki/Logical_schema
│   └── Relational
│   └── Object-Relational # https://en.wikipedia.org/wiki/Object%E2%80%93relational_mapping
│   └── Hierarchical
│   └── Network
├── Physical  # https://en.wikipedia.org/wiki/Physical_schema
│   └── Database Schema Design
│   └── Indexing and Optimization
│   └── Partitioning and Replication
├── Dimensional
│   └── Star Schema
│   └── Snowflake Schema
│   └── Fact and Dimension Tables
├── Graph
│   └── Node and Edge
│   └── Property Graph
│   └── RDF (Resource Description Framework)
├── Temporal
│   └── Historical
│   └── Time-Series 
├── NoSQL
│   └── Key-Value Store
│   └── Document Store
│   └── Column-Family Store 
│   └── Graph Store
├── Object-Oriented Data
│   └── Classes and Inheritance
│   └── Encapsulation and Polymorphism
```
