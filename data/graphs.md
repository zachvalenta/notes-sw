# ⛩️

## 参考

🗄 `doc.md` viz
📙 https://www.manning.com/books/graph-algorithms-for-data-science

## 进步

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

# 🌳 TREES

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

## semantics

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

## binary

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


## ordered

* Markdown, DOM, fs, AST, config mgmt, version control, NLP parse trees, task mgmt, window mgmt https://nikitabobko.github.io/AeroSpace/guide#tree

## trie

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

## tools

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

# 🟨 ZA

## category theory / graph theory

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

## dbms

---

* _PGQ_: property graph queries https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
> SQL now supports defining read-only queries on graphs. This allows an application to declare a property graph structure over existing tables. It is left up to the DBMS to decide whether to create an auxiliary data structure (e.g., adjacency matrix) for the property graph or just keep track of the meta-data. You can then write graph traversal queries in SQL using the MATCH keyword. The syntax builds on existing languages (e.g., Neo4j's Cypher, Oracle’s PGQL, and TigerGraph’s GSQL), and shares aspects of the emerging GQL standard. As of January 2024, the only DBMS that I am aware of that supports SQL/PGQ features is Oracle. There is an experimental branch of DuckDB that also supports SQL/PGQ.
> SQL/PGQ is a big deal. However, I do not foresee it being an immediate deathblow for graph DBMSs, as there are already several ways to translate graph-oriented queries to SQL. Some DBMSs, including SQL Server and Oracle, provide built-in SQL extensions that make storing and querying graph data easier. Amazon Neptune is a graph-oriented veneer on top of their Aurora MySQL offering. Apache AGE provides an OpenCypher interface on top of PostgreSQL. I expect other major OLAP systems (e.g., Snowflake, Redshift, BigQuery) will support SQL/PGQ in the near future.
> Adding SQL/PGQ in a DBMS is not as simple as adding support for the new syntax. There are several engineering considerations to ensure graph queries perform well. For example, graph queries perform multi-way joins to traverse the graph. But a problem arises when the intermediate results for these joins are larger than the base tables. A DBMS must use a worst-case optimal join (WCOJ) algorithm to execute such joins more efficiently than the usual hash join used when joining two tables. Another important technique is to use factorization to avoid materializing redundant intermediate results during joins. This type of compression helps the DBMS avoid blowing out its memory with the same join record over and over again.

* Tiger Graph, Dgraph https://softwareengineeringdaily.com/2021/01/19/dgraph-native-graphql-database-with-manish-jain/ Memgraph, Terminus db, embedded https://github.com/CodyKochmann/graphdb https://github.com/dpapathanasiou/simple-graph cache for dgraph https://github.com/dgraph-io/ristretto

* _Neo4J_ https://media.pragprog.com/titles/pwrdata/neo4j.pdf https://calmcode.io/course/neo4j/introduction

https://danluu.com/yegge-predictions/
DBMS
* embedded w/ Datalog https://news.ycombinator.com/item?id=33518320 https://github.com/cozodb/cozo
* Mongo offers as well https://www.mongodb.com/databases/mongodb-graph-database
* SQLite, Postgres https://news.ycombinator.com/item?id=35386948
* _Age_: Postgres extension https://github.com/apache/age
* _EdgeDB_: graph-relational = no impedance mismatch but still relational https://news.ycombinator.com/item?id=30290225
* written in Python on top of Postgres https://talkpython.fm/episodes/show/355/edgedb-building-a-database-in-python
* _Janus_: distributed, OSS https://github.com/JanusGraph/janusgraph
* _SQLite_: https://www.hytradboi.com/2022/simple-graph-sqlite-as-probably-the-only-graph-database-youll-ever-need
* _Tao_: distributed https://news.ycombinator.com/item?id=29045443 https://www.micahlerner.com/2021/10/13/tao-facebooks-distributed-data-store-for-the-social-graph.html
* _network database_: similar to graph https://stackoverflow.com/a/52325525 📙 Takahashi [2.39]
* anything that would have ever been network is now SQL https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37 📙 Kleppmann [2.36]

QUERY LANGUAGES
* _Cypher_: declarative
* _GQL_: emerging standard https://stackoverflow.com/q/13824962 https://www.youtube.com/watch?v=h8cyPIEfxQY 11:30
* _Gremlin_: wrapper over Neo4J Java API

## semantics

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
