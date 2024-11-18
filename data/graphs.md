# ⛩️

## 参考

🗄 `doc.md` viz
📙 https://www.manning.com/books/graph-algorithms-for-data-science

## 进步

---

🛠 https://github.com/networkx/networkx https://us.pycon.org/2024/schedule/presentation/91/index.html https://pragprog.com/titles/dzcnapy/complex-network-analysis-in-python/ https://github.com/dominikbraun/graph/ https://news.ycombinator.com/item?id=38834780 https://www.hytradboi.com/2022/how-to-query-almost-everything d2 https://chatgpt.com/c/671043db-1354-8004-a127-6b4152994963 https://calmcode.io/datasets/dependencies https://realpython.com/podcasts/rpp/212/
> clean these up https://pycon-archive.python.org/2024/schedule/presentation/52/index.html
* https://calmcode.io/datasets/dependencies 🗄️ `linux.md` build systems
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

# 🌳 TREES

🔗
* https://en.wikipedia.org/wiki/Tree_(data_structure)
* HDF5 https://en.wikipedia.org/wiki/Hierarchical_Data_Format https://github.com/rhuygen/hdf5_ui
🗄️
*️ `km.md` notes / tooling
*️ `language.md` compiler
*️ `protocols.md` file fmt
* `science.md` metascience / categories

SEMANTICS
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

* _s-expression_: nested list in which the elements are both data and src https://chatgpt.com/c/671f995f-e7e4-8004-9721-19cc903c3e98 akin to XML https://en.wikipedia.org/wiki/S-expression#Parsing https://news.ycombinator.com/item?id=31840852
* _treemap_: https://github.com/niyue/skillmap https://github.com/nikolaydubina/go-cover-treemap https://github.com/imsnif/diskonaut https://calmcode.io/labs/pytest-duration-insights
https://buttondown.com/hillelwayne/archive/maybe-software-engineers-could-learn-something/ https://en.wikipedia.org/wiki/Hypernymy_and_hyponymy

WALKING
* BYO https://realpython.com/directory-tree-generator-python/
* _frangipanni_: https://github.com/birchb1024/frangipanni https://news.ycombinator.com/item?id=26622548
* no Homebrew https://github.com/birchb1024/frangipanni/issues/21
* previously just Darwin executable and put on $PATH, now just building myself https://github.com/birchb1024/frangipanni/issues/22 https://github.com/zachvalenta/logs-mini23/commit/d8ffc518739eecc16d02821f4e98d705be6715e1
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

## builders

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

## types

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

# 🟨 ZA

## category theory / graph theory

🔗 https://en.wikipedia.org/wiki/Graph_theory
📚
* Cheng joy of abstraction https://www.amazon.com/gp/product/1108477224

* _centrality_: see email to Cowen re: Jamie Brandon https://en.wikipedia.org/wiki/Centrality Gwern https://news.ycombinator.com/item?id=42134708 TC https://danluu.com/broken-builds/

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

## dbms

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
