# ⛩️

## 参考

> Good programmers worry about data structures. https://softwareengineering.stackexchange.com/q/163185
🔍 https://xlinux.nist.gov/dads/
📙 Conery ch. 7

## 进步

* taxonomy https://chatgpt.com/c/6706989f-02a4-8004-9933-bbe525f36b55 https://www.interviewcake.com/data-structures-reference https://roadmap.sh/datastructures-and-algorithms
* Python collections https://www.30secondsofcode.org/python/p/1 https://realpython.com/python-data-structures/
* mixing trees and tags https://borretti.me/article/the-design-space-of-wikis#pages
* goofiness https://calmcode.io/data-science-fiction
* Task Warrior vs. kanbai-tui

# 🌫️ ADT

```sh
├── Linear/
│   ├── List/
│   │   ├── ArrayList
│   │   ├── LinkedList
│   │   │   ├── SinglyLinkedList
│   │   │   ├── DoublyLinkedList
│   │   │   └── CircularLinkedList
│   │   └── SkipList
│   ├── Stack
│   └── Queue/
│       ├── SimpleQueue
│       ├── CircularQueue
│       └── PriorityQueue
├── Associative/
│   ├── Dictionary/
│   │   ├── HashMap
│   │   ├── TreeMap
│   │   └── OrderedDict
│   ├── Set/
│   │   ├── HashSet
│   │   └── SortedSet
│   └── Multimap
└── Non-linear/
    ├── Tree/
    │   ├── BinaryTree
    │   │   ├── BinarySearchTree
    │   │   ├── AVLTree
    │   │   └── RedBlackTree
    │   ├── BTree
    │   ├── Trie
    │   └── Heap/
    │       ├── MinHeap
    │       └── MaxHeap
    └── Graph/
        ├── DirectedGraph
        ├── UndirectedGraph
        └── WeightedGraph
```
```sh
├── linear
│   ├── list
│   ├── stack
│   ├── queue
│   └── deque
├── associative
│   ├── map
│   ├── dictionary
│   └── symbol_table
├── hierarchical
│   ├── tree
│   ├── heap
│   └── priority_queue
├── graph
│   ├── directed
│   ├── undirected
│   └── weighted
└── set
    ├── set
    ├── multiset
    └── disjoint_set
```

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

## heap

* _heap_: tree + heap property e.g. max (parent node >= child nodes) min (parent node >= child nodes) https://www.youtube.com/watch?v=dM_JHpfFITs
* used for priority queue 🗄 *FO https://en.wikipedia.org/wiki/Heap_(data_structure)
```
    9
   / \
  5   7
 /     \
4       6
```


## graph

📙 https://www.manning.com/books/graph-algorithms-for-data-science

---

🛠 https://github.com/networkx/networkx https://www.youtube.com/watch?v=x6KnkZKktRY https://us.pycon.org/2024/schedule/presentation/91/index.html https://pragprog.com/titles/dzcnapy/complex-network-analysis-in-python/ https://github.com/dominikbraun/graph/ https://news.ycombinator.com/item?id=38834780 https://www.hytradboi.com/2022/how-to-query-almost-everything https://calmcode.io/datasets/dependencies https://realpython.com/podcasts/rpp/212/
> clean these up https://pycon-archive.python.org/2024/schedule/presentation/52/index.html
* https://www.youtube.com/watch?v=PkFpFCqIdZ8
* https://www.youtube.com/watch?v=_mk78aQhWPM
* topological sort, dynamic programming https://blog.danielh.cc/blog/leetcode https://rednafi.com/go/topological_sort/
* https://calmcode.io/datasets/dependencies 🗄️ `linux.md` build systems
* https://www.hytradboi.com/2022/how-to-query-almost-everything
* https://www.kaseyklimes.com/notes/2019/10/16/an-augmented-mind-designing-a-personal-knowledge-base-with-notion
* _use cases_: good at relationships btw heterogenous data ("does Alice follow Bob?") w/out a million joins  📙 Kleppmann 2.49, 2.63 bad at aggregates or anything that deals w/ a few attr over many records; used for networks (IAM, knowledge mgmt, Git, recommendation engine) https://www.youtube.com/watch?v=h8cyPIEfxQY 14:30
* _OGM_: ORM for graphs https://www.youtube.com/watch?v=h8cyPIEfxQY 12:30

* _property graph_: vertex (id, dict of properties, and list of incoming/outgoing edges) edge (id, dict of properties, start/end vertices and descriptive label) 📙 Kleppmann 2.50
* _triple-store_: subject (vertex) predicate, object (value or another vertex) 📙 Kleppmann 2.55 used by Datomic (Datalog query language) 📙 ibid 2.50, 60, 63 https://github.com/instantdb/instant
* _RDF (resource description framework)_: triple store for semantic web 📙 Kleppmann 2.57 SPARQL query language 📙 ibid 59 https://twobithistory.org/2020/01/05/foaf.html
* _types_: https://stackoverflow.com/a/59532041/6813490
* visualization https://github.com/shahinrostami/chord https://github.com/plotly/falcon
* _sink_: https://github.com/brettkromkamp/contextualise https://www.youtube.com/watch?v=GekQqFZm7mA https://www.denizcemonduygu.com/philo/ http://aosabook.org/en/500L/dagoba-an-in-memory-graph-database.html https://pragprog.com/book/pwrdata/seven-databases-in-seven-weeks-second-edition

### semantics

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
* _knowledge graph_: https://news.ycombinator.com/item?id=27245696 https://www.manning.com/books/knowledge-graphs-applied
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

### category theory

🔗 https://en.wikipedia.org/wiki/Graph_theory
🗄️ `src.md` functional
📚
* Cheng joy of abstraction https://www.amazon.com/gp/product/1108477224

* _centrality_: see email to Cowen re: Jamie Brandon https://en.wikipedia.org/wiki/Centrality Gwern https://news.ycombinator.com/item?id=42134708 TC https://danluu.com/broken-builds/

---

```txt
Yes, there are interesting overlaps between category theory and software development, particularly in areas like functional programming, type theory, and abstract data structures. These connections stem from how category theory deals with abstract structures and mappings between them, which can be applied to the structure and behavior of software systems. Here are some key overlaps:

1. Functional Programming
Functor, Monads, and Applicatives: These are fundamental concepts in category theory that have direct implementations in functional programming languages, particularly in Haskell and Scala. A Functor in programming refers to a type that can be mapped over (like lists or trees). A Monad provides a way to chain computations, and this is central to handling side effects (like I/O, exceptions, or state) in purely functional languages.
Composition: Category theory emphasizes the concept of composing functions (arrows between objects), which is a core practice in functional programming. Functions are treated as first-class citizens and composed to form complex operations.
2. Type Systems and Abstraction
Types as Objects, Functions as Morphisms: In some ways, types in a programming language can be seen as objects in a category, and functions between types are morphisms (arrows) between objects. This provides a way to reason about type safety, refactoring, and code reuse.
Generic Programming: Category theory’s abstraction powers align well with polymorphism in type systems (such as generics in Java or templates in C++). Abstracting over data types allows code to work over a wide variety of inputs in a safe manner, similar to how category theory abstracts over structures.
3. Software Architecture
Modularity and Composition: Software systems are often built in a modular fashion, where smaller components are composed to form larger systems. In category theory, the idea of breaking systems into composable parts and studying their interactions is central. This mirrors software architectures like microservices, where small independent services are composed to form larger applications.
Duality: Many software structures exhibit dualities similar to those found in category theory. For example, a concept like reading from a data stream and writing to a data stream can be seen as dual operations. Category theory’s handling of dualities can provide deeper insight into how these operations relate.
4. DSLs (Domain-Specific Languages)
Category theory can influence the design of DSLs for software development. Algebraic data types (used to represent data structures) and the mathematical precision provided by category theory can help create clean, concise, and powerful languages tailored to specific problem domains.
5. Declarative Programming and Databases
SQL queries, for instance, can be related to monads and monoids in category theory. The ideas of combining queries and mapping data transformations bear similarity to functional programming practices rooted in category theory.
6. Proofs and Correctness
Category theory is often used in the formal verification of software. It provides a language for specifying and proving the properties of algorithms, software systems, and programming languages. This ties into dependently typed languages (like Agda or Coq), where software correctness can be proven as part of the program.
7. Monoidal Categories and Parallelism
Monoidal categories offer insights into how systems can be structured in a parallel or distributed fashion. These categories define how processes can be combined in parallel, providing a mathematical foundation for understanding concurrency in software systems.
```

https://news.ycombinator.com/item?id=42291141 https://docs.racket-lang.org/ctp/index.html

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

## linked list

---

* https://www.youtube.com/watch?v=odW9FU8jPRQ
* https://news.ycombinator.com/item?id=33473497
* https://docs.python.org/3/glossary.html#term-list
* https://nullprogram.com/blog/2024/07/31/
LINKED LIST https://realpython.com/linked-lists-python/ https://news.ycombinator.com/item?id=26620598
* singly or doubly linked https://lwn.net/Articles/827180/
* _memory_: discontiguous locations = sequential access [2.30]
* _O(1)_: write [Bhargava 2.28] delete [ibid]
* _O(n)_: read [Bhargava 2.28]
> seems like mutative operations only O(1) if items tracked and if everything not the first/last index is untracked then shouldn't it be O(n)? [Bhargava 2.30]
* _piece table_: append-only list used for editing text https://darrenburns.net/posts/piece-table/ https://news.ycombinator.com/item?id=36312488 https://cdacamar.github.io/data%20structures/algorithms/benchmarking/text%20editors/c++/editor-data-structures/
* diff than rope? https://github.com/cessen/ropey https://github.com/prompt-toolkit/pyvim https://web.eecs.utk.edu/~azh/blog/challengingprojects.html
* Myers diff https://github.com/aymanbagabas/go-udiff

## map

---

* Doggerland, Bering Land Bridge https://gizmodo.com/the-famous-bering-land-bridge-was-more-like-a-swamp-geologists-say-2000539043 https://en.wikipedia.org/wiki/Doggerland
* mind map https://en.wikipedia.org/wiki/Mind_map https://www.dendron.so/ https://github.com/vimwiki/vimwiki
* concept map https://en.wikipedia.org/wiki/Concept_map https://cmap.ihmc.us/docs/learn.php

* ADT: reference array via key https://calpaterson.com/how-a-sql-database-works.html
* impl: BST, red-black https://jvns.ca/blog/2017/09/09/data-structure--the-treap-/

https://tenthousandmeters.com/blog/python-behind-the-scenes-10-how-python-dictionaries-work/
* _operations_: lookup, insert, delete
* _O(1)_: Bhargava 5.90
* _hash aggregate_: aggregate keys e.g. A 1 B 2 A 4 -> A 5 B 2 https://veekaybee.github.io/2021/06/06/hashaggregate/

## queue

---

* queue https://www.youtube.com/watch?v=mDCi1lXd9hc
QUEUES
* _enqueue_: add to queue https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
* _dequeue_: rm from queue
* _head_: first item in the queue i.e. oldest item https://www.youtube.com/watch?v=RSY85SLXzwk 0:50

* _dequeue_: *FO; either; push to each pop from each https://stackoverflow.com/a/38812944/6813490 https://hamatti.org/posts/rotating-turn-order-with-deque/
```python
pass
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

## stack

* _stack_: LIFO; post-it https://stackabuse.com/stacks-and-queues-in-python/ https://realpython.com/how-to-implement-python-stack/ https://www.youtube.com/watch?v=I5lq6sCuABE
```python
stack = [42, 'abc']
stack.append('alice')  # push
stack.pop()  # pop
```

## tree

🔗 https://en.wikipedia.org/wiki/Tree_(data_structure)
🛠️ https://github.com/queelius/AlgoTree
> trees are easy to deal with and understand, but graphs are more "open" with what you can do https://news.ycombinator.com/item?id=27662089
🗄️
*️ `km.md` notes / tooling
*️ `lisp.md` s-expressions
* `science.md` metascience / categories https://en.wikipedia.org/wiki/Phylogenetic_tree

---

MORE TYPES
* https://news.ycombinator.com/item?id=42201936
* _BPS tree_: formed from binary space partitioning https://twobithistory.org/2019/11/06/doom-bsp.html
* _minimum spanning tree (MST)_: edges to connect every node in weight graph while minimizing edge weight 📙 Christian chapter 8
* _multitree_: https://github.com/climech/grit
* _treemap_: https://github.com/niyue/skillmap https://github.com/nikolaydubina/go-cover-treemap https://github.com/imsnif/diskonaut https://calmcode.io/labs/pytest-duration-insights
https://buttondown.com/hillelwayne/archive/maybe-software-engineers-could-learn-something/ https://en.wikipedia.org/wiki/Hypernymy_and_hyponymy

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

---

* _tree_: type of graph 📙 Bhargava 6.113
* _parent_: node w/ children
* _leaf_: node with no children https://www.youtube.com/watch?v=5cU1ILGy6dM [0:30]
* _height_: distance from root to given leaf measured in levels https://www.youtube.com/watch?v=Aagf3RyK3Lw [0:15] https://www.youtube.com/watch?v=dM_JHpfFITs [1:10]
* _subtree_: tree nested w/ root tree https://www.youtube.com/watch?v=5cU1ILGy6dM
* _completeness_: know how many elements in each layer except the last one https://realpython.com/python-heapq-module/#heaps-as-lists-in-the-python-heapq-module
* _treemap_ https://news.ycombinator.com/item?id=36868940 https://en.wikipedia.org/wiki/Treemapping

### tools

WALKERS
* BYO https://realpython.com/directory-tree-generator-python/
* _frangipanni_: https://github.com/birchb1024/frangipanni https://news.ycombinator.com/item?id=26622548
* no Homebrew https://github.com/birchb1024/frangipanni/issues/21
* previously just Darwin executable and put on $PATH, now just building myself https://github.com/birchb1024/frangipanni/issues/22 https://github.com/zachvalenta/logs-mini23/commit/d8ffc518739eecc16d02821f4e98d705be6715e1
* _snapdiff_: snapshot https://www.jotaen.net/iE3XC/snapdiff-compare-directory-trees-on-CLI/
* _walkdir_: https://github.com/BurntSushi/walkdir

BUILDERS 🗄️ `html-css.md` SSG `protocols.md` JSON `km.md` notes / tooling `info.md` viz / system
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

### binary

🛠 https://github.com/joowani/binarytree 

---

https://benjamincongdon.me/blog/2021/08/17/B-Trees-More-Than-I-Thought-Id-Want-to-Know/
https://planetscale.com/blog/btrees-and-database-indexes

* _b-tree_: two branches for each node https://stackoverflow.com/a/6380314 🗄 `db.md` indexing https://avi.im/blag/ https://build-your-own.org/ https://build-your-own.org/database/04_btree_code_1 https://planetscale.com/blog/btrees-and-database-indexes
```txt
Designed to store and retrieve comparable keys efficiently in a sorted order.
Traversal is determined by key comparisons (e.g., left for smaller, right for larger).
```
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
* _red-black tree_: BST that keeps itself balanced 📙 Bhargava 11.206
* used for SSTables 📙 Kleppmann 78
* _splay tree_: red-black + recently accessed are fast to lookup again 📙 Bhargava 11.206

### ordered

* Markdown, DOM, fs, AST, config mgmt, version control, NLP parse trees, task mgmt, window mgmt https://nikitabobko.github.io/AeroSpace/guide#tree

### trie

🗄️ `algos.md` matching > flashtext

* _trie (prefix tree)_: typically used to store words https://www.youtube.com/watch?v=7XmS8McW_1U https://medium.com/basecs/trying-to-understand-tries-3ec6bede0014 https://blog.cloudflare.com/pingora-saving-compute-1-percent-at-a-time/ https://news.ycombinator.com/item?id=41501496

```txt
Hierarchical Representation of Strings:
* Each level of the trie corresponds to a character in a string.
* A path from the root to a node represents a prefix of a string.

Efficient for Prefix Matching: Tries are optimized for retrieving words with shared prefixes, making operations like autocomplete or prefix-based search very efficient.
Space Usage: It can be space-efficient for strings with overlapping prefixes since common prefixes are stored only once. However, it may require more memory than other structures if the stored strings are diverse and do not share many prefixes.
Insertion and Search Time Complexity: O(L), where L is the length of the word being inserted or searched. This makes it faster than hash-based structures for prefix-related operations.

Nodes:
* Each node typically stores:
* A character (or part of the string).
* References to child nodes (often stored in a hash table or array).
* A flag indicating whether the node represents the end of a valid string.

Common Use Cases:
Autocomplete Systems: Quickly suggest words that start with a given prefix.
Spell Checking: Validate whether a word exists in a dictionary.
Search Engines: Optimize prefix searches for terms or keywords.
IP Routing: Used in networking to efficiently store and retrieve IP prefixes.
```

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end_of_word = True

    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end_of_word

    def starts_with(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True

trie = Trie()
trie.insert("cat")
trie.insert("car")
trie.insert("cap")
print(trie.search("cat"))        # True
print(trie.search("can"))        # False
print(trie.starts_with("ca"))    # True
print(trie.starts_with("bat"))   # False
```

# 🌪️ STRUCTURES

```sh
├── Linear/
│   ├── Array
│   ├── LinkedList/
│   │   ├── SinglyLinkedList
│   │   ├── DoublyLinkedList
│   │   └── CircularLinkedList
│   ├── Stack
│   ├── Queue
│   └── Deque
├── Hashing/
│   ├── HashTable
│   └── BloomFilter
├── Trees/
│   ├── GeneralTree
│   ├── BinaryTree
│   │   ├── BinarySearchTree
│   │   ├── AVLTree
│   │   ├── RedBlackTree
│   │   └── SplayTree
│   ├── BTree
│   ├── Trie
│   └── Heap
└── Graphs/
    ├── AdjacencyMatrix
    ├── AdjacencyList
    ├── EdgeList
    └── Variants/
        ├── DirectedGraph
        ├── UndirectedGraph
        ├── WeightedGraph
        └── CyclicGraph
```
```sh
├── arrays
│   ├── static
│   ├── dynamic
│   └── circular
├── linked_lists
│   ├── singly
│   ├── doubly
│   ├── circular
│   └── skip_list
├── hash_tables
│   ├── separate_chaining
│   ├── open_addressing
│   │   ├── linear_probing
│   │   ├── quadratic_probing
│   │   └── double_hashing
│   └── perfect_hashing
├── trees
│   ├── binary
│   │   ├── bst
│   │   └── expression_tree
│   ├── balanced
│   │   ├── avl
│   │   ├── red_black
│   │   └── splay
│   ├── multiway
│   │   ├── b_tree
│   │   └── b_plus_tree
│   └── trie
└── graphs
    ├── adjacency_matrix
    ├── adjacency_list
    └── edge_list
```

## array

---

* array https://www.youtube.com/watch?v=QJNwK2uJyGs
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

## bloom filter

https://avi.im/blag/2024/sqlite-past-present-future/

```txt
A Bloom filter is a probabilistic data structure that's implemented using multiple hash functions and a bit array.

PROBABILISTIC DATA STRUCTURES

Membership Testing
* Bloom Filter (allows false positives but no false negatives)
* Cuckoo Filter (allows deletion unlike Bloom)

Frequency Estimation
* Count-Min Sketch
* Count Sketch

Cardinality Estimation
* HyperLogLog

The core tradeoff: Bloom filters trade perfect accuracy for extremely space-efficient membership testing. You can test if an element is "definitely not in the set" or "probably in the set".

Common use cases:
* Cache filtering (is this URL definitely not cached?)
* Spell checkers (is this word definitely not in our dictionary?)
* Network routing (is this packet definitely not for this subnet?)

If you're dealing with any of these patterns - "check if X might be in large set Y to avoid expensive lookups" - a Bloom filter might help.
```

https://www.youtube.com/watch?v=qZNJTh2NEiU https://www.youtube.com/watch?v=V3pzxngeLqw
* _bloom filter_: like a hash table except takes up a lot less space and false positives are possible
* https://simonwillison.net/2024/Dec/24/jeremy-edberg/
* use case is to see whether item already part of a very large set e.g. whether a key exists in a database 📙 11.210-11
* https://vprusso.github.io/blog/2017/bloom-filters-and-pokemon/ 📙 Kleppmann 79 https://onatm.dev/2020/08/10/let-s-implement-a-bloom-filter/ http://aosabook.org/en/posa/working-with-big-data-in-bioinformatics.html https://luminousmen.com/post/building-a-bloom-filter

## hash table

🗄 `security.md` `python.md`

* _hash table_: hash function + array to put the results in [Bhargava 5.76-8, 5.90-2, 11.213]
* hashing https://blog.codinghorror.com/url-shortening-hashes-in-practice/
* aka map, dictionary, associative array https://docs.python.org/3/glossary.html#term-dictionary
* alternatives incl. BST, skip list https://stackoverflow.com/a/301822 📙 Skiena 12.1

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

# 🟨 ZA

## operations

https://github.com/jamiebuilds/itsy-bitsy-data-structures https://www.interviewcake.com/concept/python3/array
* _lookup_: read
* _insert_: add anywhere
* _delete_: rm anywhere
* _unshift_: add to start
* _push_: add to end
* _shift_: rm from start
* _pop_: rm from end

## probabilistic

🗄️ `stats.md` Bayes
📙 Pfeffer https://www.manning.com/books/practical-probabilistic-programming

---

* _probabilistic data structures_: CAP theorem but w/ accuracy, functionality, efficiency https://www.youtube.com/watch?v=VjFS-_H10bw 9:15
* _hyperlog_: https://will-keleher.com/about.html
* _hyperloglog_: distinct el in set https://www.youtube.com/watch?v=VjFS-_H10bw 10:00 https://redis.com/redis-best-practices/counting/hyperloglog/
* probabilistic https://www.youtube.com/watch?v=VjFS-_H10bw @ 15:00 https://pypi.org/project/datasketch/
