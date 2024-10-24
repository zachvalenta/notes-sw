# ⛩️

## 参考

🛣️ https://roadmap.sh/datastructures-and-algorithms https://roadmap.sh/computer-science
📚
* ✅ Bhargava grokking algorithms
* Christian algorithms to live by
* Dasgupta algorithms
* MacCormick computed
* MacCormick nine algorithms
* Skiena manual https://www.algorist.com/ https://fabiensanglard.net/algorithms_and_datastructures/index.php
* Wengrow ds/algos https://pragprog.com/titles/jwpython/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-1/ https://pragprog.com/titles/jwpython2/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-2/

## 进步

https://chatgpt.com/share/67069a06-24cc-8004-9a88-108d568d211a
* extract data structures
* combine algos and ML

+ category theory

---

streams? SICP https://blog.moertel.com/posts/2013-05-26-python-lazy-merge.html

fizz buzz
fibonacci
> look up the ten algorithms you have to know, rosetta code, project euler

RANKING https://bearblog.dev/discover/
```txt
This page is ranked according to the following algorithm: score = log10(U) + (S / D * 86,400)

U = Upvotes of a post
S = Seconds since Jan 1st, 2020
D = Days modifier (currently at 14)

D values is used to modify the effect of time on the score. The higher D, the more time gravity influences post score.
```

https://roadmap.sh/datastructures-and-algorithms https://roadmap.sh/python
https://www.softwaredesign.ing/blog/ai-is-the-reason-interviews-are-harder-now
https://realpython.com/python-hash-table/
* do with books https://www.fast.ai/
* regex 🗄 vimrc, regex-test.md https://chat.openai.com/share/c31be3fc-ad04-4bea-bf65-1401d3d91f09 https://learnbyexample.gitbooks.io/vim-reference/content/Regular_Expressions.html https://neovim.io/doc/user/usr_03.html
* https://mathspp.com/blog/5-ways-to-flatten-a-list-of-lists
* hash tables re: maps, ADTs https://stackabuse.com/hash-tables-in-python/ https://blog.codingconfessions.com/p/cpython-set-implementation
* counter https://blog.ovalerio.net/archives/2924
* rf
* Monte Carlo
* trends https://news.ycombinator.com/item?id=35886900

za
* https://www.pythonmorsels.com/deduplicate-lists/
* https://www.youtube.com/watch?v=Peq4GCPNC5c
* Wengrow https://www.amazon.com/gp/product/1680507222
* https://malisper.me/an-algorithm-for-passing-programming-interviews/ 
* Conery chapters
* https://news.ycombinator.com/item?id=36096305

review data structures
* Python collections https://www.30secondsofcode.org/python/p/1 https://realpython.com/python-data-structures/
* array https://www.youtube.com/watch?v=QJNwK2uJyGs
* linked list https://www.youtube.com/watch?v=odW9FU8jPRQ https://news.ycombinator.com/item?id=33473497 https://docs.python.org/3/glossary.html#term-list https://nullprogram.com/blog/2024/07/31/
* stack https://www.youtube.com/watch?v=I5lq6sCuABE
* queue https://www.youtube.com/watch?v=mDCi1lXd9hc
* probabilistic https://www.youtube.com/watch?v=VjFS-_H10bw @ 15:00 https://pypi.org/project/datasketch/

INTERVIEWS
* reverse array in place w/ space compexity O(n) 🗄 `python.md` copy
* recurring character https://crunchskills.com/most-common-interview-question-at-google
* previous interviews 🗄 `ms; rg def`
```python
start = 0
end = -1
terminus = len(qd) // 2
for _ in range(terminus):
    qd[start], qd[end] = qd[end], qd[start]
    start += 1
    end -= 1
return qd
```
```python
###
# PROBLEM STATEMENT
###
# Write a function that given a dictionary of key-values of stage-names to
# configurations (in this problem, stage names to integer timeout values) 
# and a stage name, will return the configuration value.

# EXAMPLE DATA
# typing: K (key) V (str/int)
configs = {
    "dev" : 3,
    "staging" : "prod",
    "UAT": 7,
    # "prod" : "default",
    "prod" : "staging",
    "default" : 42,
}

# ✅ step 1: handle K w/ int V
# ✅ step 2: handle K w/ str V i.e. transitive lookups
# step 3: handle non-existant K

def get_config_value(configs, env):
    count = 0
    """
    configs: data_src
    env: env
    >>> int
    """
    def get_config_value_inner(configs, env):
        if type(configs[env]) is int:
            return configs[env]
        else:
            if counter(count) == upper_limit:
                pass
                # bail out
            else:
                return get_config_value_inner(configs, configs[env])


# test case 1 - naive lookup
print(get_config_value(configs, "dev"))
print(get_config_value(configs, "UAT"))
print(get_config_value(configs, "default"))

# test case 2 - transitive lookup
print(get_config_value(configs, "staging"))
print(get_config_value(configs, "prod"))

# test case 3 - n transitive lookups
```
* `interview-cake` 
* https://www.hackerrank.com/interview/interview-preparation-kit
* 10 from Rosetta Code https://rosettacode.org/wiki/Category:Programming_Tasks https://www.freecodecamp.org/learn/rosetta-code/
* 10 from Euler https://projecteuler.net/archives https://www.freecodecamp.org/learn/project-euler/
* https://interviewing.io/
* TripleByte

* personalization engine https://news.ycombinator.com/item?id=30778100
* code formatter https://yorickpeterse.com/articles/how-to-write-a-code-formatter/

* _21_: 📙 Trask chapters 1-3
* _20_: 📙 Bhargava grokking
* _19_: regex basics
* _18_: restart Bhargava
* _17_: start Bhargava, Castro and Roberto get everyone to buy the O'Reilly ML book
* _16_: Hacker Rank for Zip Code

# 🛣️ ALGORITHMS

🔍
* https://github.com/TheAlgorithms/Python
* https://softwareengineering.stackexchange.com/
* https://xlinux.nist.gov/dads/
> Until you start dealing with millions of people on a network or you need to blur or sharpen a million photos quickly, you can just use the work of other people. When it gets real, break out the comp sci. 🗄 `ford-code.pdf`

* _algorithm_: solution (Dijkstra) to specific problem (lightest path through unweighted graph)
* sometimes the name of the problem (set covering)

## classics

SET COVERING
* given target set and a collection of source sets, find the smallest sub-collection of target sets whose union equals the target set
* howto (brute): go through power set, either O(2^n) or O(n!) 📙 Bhargava 8.147, 8.152, 9.162
```python

```
* howto (approximation): iterate source sets and take whichever has the most from the target set that hasn't been taken already, O(n^2) 📙 Bhargava 8.152
```python

```

KNAPSACK PROBLEM https://en.wikipedia.org/wiki/Knapsack_problem
* given container w/ weight capacity (knapsack) and items w/ weights and values, calculate most valuable combination of items that could fit into container 📙 Bhargava 8.144, 9.162
* an example of combinatorics (part of stats? calculus? both? https://www.khanacademy.org/math/precalculus)
* ❓ version of set covering or different animal entirely?
* ❓ howto: last column serves as optimal solution until cell at last row and column, at which you compare previous optimal against...power set of all other other items? 📙 Bhargava 9.168  https://www.youtube.com/watch?v=YRBON9sIZ2Y https://aiven.io/blog/solving-the-knapsack-problem-in-postgresql

AUTOCORRECT
* _Levenshtein distance_: https://blog.paperspace.com/implementing-levenshtein-distance-word-autocomplete-autocorrect/ https://github.com/hbollon/go-edlib https://github.com/seatgeek/fuzzywuzzy https://www.youtube.com/watch?v=kTS2b6pGElE 🗄 `system.md` search https://towardsdatascience.com/text-similarity-w-levenshtein-distance-in-python-2f7478986e75 🗄 difftastic
* people use DP?
* _substring_: common contiguous char [Bhargava 9.179, 182]
```markdown
y _bcd_ af 
x _bcd_ edf
```
* _subsequence_: discontiguous char; used for autocorrect [Bhargava 9.184]
```markdown
y _bcd_ a _f_
x _bcd_ ed _f_
```
* _substring_: char in order and continuous e.g. for `hello there` valid substrings are `hello` and `llo th` https://stackoverflow.com/a/49688118/6813490
* _subsequence_: char in order but not necessarily continuous e.g. for `hello there` a valid subsequences is `hll th` (note missing `e`)
> these moved in from different file, don't know which set of definitions valid

ZA
* _anagram_: https://news.ycombinator.com/item?id=35824173
* _collison detection_: https://leanrada.com/notes/sweep-and-prune/
* _codec_: algo for video file compression https://github.com/leandromoreira/digital_video_introduction#how-does-a-video-codec-work https://news.ycombinator.com/item?id=25328622  https://github.com/ablwr/my-recurse-center-syllabus
* _Fibonacci_: 🗄 `classic-compsci.pdf` https://docs.python.org/3/tutorial/modules.html https://www.youtube.com/watch?v=anrOzOapJ2E @ 34:00 https://realpython.com/fibonacci-sequence-python/
* _Fisher-Jenks_: https://pbpython.com/natural-breaks.html
* _Huffman coding_: algo used to generate prefix code https://news.ycombinator.com/item?id=22474850
* _hyper log_: count unique items in large set 📙 Bhargava 11.213
* _Morris counter_: https://arpitbhayani.me/blogs/morris-counter
* _Prim's algorithm:_ find MST
* _PubGrub_: for dependency resolution (SAT) https://github.com/sdispater/mixology https://github.com/dart-lang/pub/blob/master/doc/solver.md SAT solver, theorem prover https://news.ycombinator.com/item?id=35626783
* _simulated annealing_: https://matthewstrom.com/writing/how-to-pick-the-least-wrong-colors/
* _Towers of Hanoi_: 🗄 `classic-compsci.pdf` https://en.wikipedia.org/wiki/Dynamic_programming#Tower_of_Hanoi_puzzle

## search

🗄 `math.md` linear algebra

* _search space_: set of possible solutions to the problem constraints https://en.wikipedia.org/wiki/Feasible_region
* _simple_: 🗄 `/algos`
* _binary_: 🗄 `/algos`; using BST (❌ log O of n average case and O of n worst case, sequential access ✅ faster mutative operations) [Bhargava 11.205]
* _breadth-first (bfs)_: 🗄 `/algos` https://healeycodes.com/practical-intro-to-graphs/
* _depth-first (dfs)_:
> Doing great work is a depth-first search whose root node is the desire to. So "If at first you don't succeed, try, try again" isn't quite right. It should be: If at first you don't succeed, either try again, or backtrack and then try again. http://paulgraham.com/greatwork.html

---

* index https://jamesg.blog/2024/07/16/build-a-search-index/
* semantic https://news.ycombinator.com/item?id=41088273 https://github.com/arunsupe/semantic-grep https://blog.elicit.com/semantic-search/
* shazam https://github.com/cgzirim/seek-tune https://news.ycombinator.com/item?id=41127726
* https://www.alexmolas.com/2024/02/05/a-search-engine-in-80-lines.html
* _A*_: https://www.redblobgames.com/pathfinding/a-star/introduction.html 
* _Bellman-Ford_: Dijkstra for negative-weighted [7.130]
* _dfs_: https://medium.com/basecs/deep-dive-through-a-graph-dfs-traversal-8177df5d0f13 
* _Dijkstra_: 🗄 `/algos` https://medium.com/basecs/finding-the-shortest-path-with-a-little-help-from-dijkstra-613149fbdc8e https://en.wikipedia.org/wiki/Dynamic_programming#Dijkstra's_algorithm_for_the_shortest_path_problem
* _optimal stopping_: related to dynamic programming, Bellman 📙 Christian chapter 1 https://en.wikipedia.org/wiki/Optimal_stopping
* _traveling salesperson(TSP)_: Bhargava 8.157 https://medium.com/basecs/the-trials-and-tribulations-of-the-traveling-salesman-56048d6709d seems like genetic algorithms are popular for this https://www.youtube.com/watch?v=9zfeTw-uFCw https://towardsdatascience.com/evolution-of-a-salesman-a-complete-genetic-algorithm-tutorial-for-python-6fe5d2b3ca35 https://www.quantamagazine.org/computer-scientists-break-traveling-salesperson-record-20201008/ https://news.ycombinator.com/item?id=24761105 https://joseprupi.github.io/misc/2023/08/19/playing_with_genetic_algorithms_in_python.html 📙 Christian chapter 8

ENGINE 🗄 `za/search-engine` (port data to query sandbox)
* BYO https://news.ycombinator.com/item?id=39293050 https://www.alexmolas.com/2024/02/05/a-search-engine-in-80-lines.html
* _robots.txt_: file that tells crawlers what files to ignore https://adamj.eu/tech/2020/02/10/robots-tx https://pythonbytes.fm/episodes/show/376/every-dunder-method-in-a-python-lockbox https://x.com/didaoh/status/1814341975195492378
* don't crawl https://unitedmasters.xyz/robots.txt https://searchfacts.com/robots-txt-allow-disallow-all/
```txt
User-agent: *
Disallow: /
```
* _PageRank_: ranking algo that weights on number of incoming links (and their popularity)
* _TF-IDF_: ranking  https://jamesg.blog/2024/08/17/tf-idf-python/
* _instant answer_: display text from top result in overall results https://drewdevault.com/2020/11/17/Better-than-DuckDuckGo.html
* _indexer_: writes/updates keys https://drewdevault.com/2020/11/17/Better-than-DuckDuckGo.html
* _full text search (FTS)_: search all text https://en.wikipedia.org/wiki/Full-text_search 📙 Karwin ch 17
* via db (Postgres) or specialized server (elasticsearch) https://news.ycombinator.com/item?id=27973497
* BYO https://artem.krylysov.com/blog/2020/07/28/lets-build-a-full-text-search-engine/ https://bart.degoe.de/building-a-full-text-search-engine-150-lines-of-code/ https://github.com/codecrafters-io/build-your-own-x#build-your-own-search-engine
* _meta search_: search metadata https://calpaterson.com/metadata.html
* _index_: subset of terms http://jsomers.net/blog/allusion
* Google has appox 60B documents indexed https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html
* usage in scholarship https://news.ycombinator.com/item?id=30407460
```txt
apple  - pg 3, 42
banana - pg 27, 113
```
* _inverted index_: map w/ K as topic and V as pages (whether book or web) 📙 MacCormick 12, Bhargava 11.207 🗄 `db.md` indexing ❓ different than index?
* _concordance_: all terms + snippet/full text from page https://www.opensourceshakespeare.org/concordance/
```txt
Wilt thou ever be a foul-mouthed and calumnious knave
Virtue itself scopes not calumnious strokes.
Theres none stands under more calumnious tongues
```
* _query_: what you're searching for
* _page_: where you're looking; aka document https://0x65.dev/blog/2019-12-05/a-new-search-engine.html
* _match_: page containing query 📙 MacCormick 11
* _lexical match_: exact e.g. query 'eggplant' only matches 'eggplant'https://github.blog/2018-09-18-towards-natural-language-semantic-code-search/ 
>  It was merely capable of answering queries that were an exact match to the queries we had in our query logs. Yes, that meant we didn’t have a "real" search-engine, but a glorified cache. https://0x65.dev/blog/2019-12-05/a-new-search-engine.html
* _semantic match_: smart e.g. query 'eggplant' matches 'eggplant' and 'aubergine' https://0x65.dev/blog/2019-12-05/a-new-search-engine.html
* anchor text from link tags a good way to get around document noise https://0x65.dev/blog/2019-12-05/a-new-search-engine.html#fn2
> Anchor text, curated by humans, serves as a mini summary of the content of a page. By building an inverted index based on it rather than the entire content, one can achieve a significantly smaller and more importantly, less noisy index.
```txt
# noisy documents
# query:	eggplant dishes

* document:	Popular Youtuber eggplant dishes out a severe attack against the whole music industry
* document:	I am not a fan of eggplant, but here are some zucchini dishes...
* document:	Did you know that eggplant dishes cannot be refrigerated?
```
* _relevance_: order matches 📙 MacCormick 11
* algos https://simonwillison.net/2020/Dec/19/dogsheep-beta/ 🗄 `algos.md` Levenshtein
* aka ranking, content match https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html
* _query logs_: map of query to URL clicked e.g. query 'boxing' URL 'espn.com/boxing' https://0x65.dev/blog/2019-12-05/a-new-search-engine.html
> Ranking is where it gets controversial. When you rank, you pick winners and losers. https://news.ycombinator.com/item?id=20286953
> The big problem with all the off-the-shelf search solutions (RDBMS full-text search, ES, Algolia) is that search ranking is a complicated and subtle problem, and frequently depends on signals that are not in the document itself. Google's big insight is that how other people talk about a website is more important than how the website talks about itself, and its ranking algorithm weights accordingly. https://news.ycombinator.com/item?id=27978505
* user feedback plays a part
> we would need real users to measure changes in search relevance in order to be competitive https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html
* https://news.ycombinator.com/item?id=28558884 https://news.ycombinator.com/item?id=33051393
```text
# page 1
# the dog stood at the mat
# 1   2   3     4  5   6

# page 2
# the cat sat   at the mat
# 1   2   3     4  5   6

* the: 1, 2
* dog: 1
* stood: 1
* at: 1, 2
* mat: 1, 2
* cat: 2
* sat: 2
```
* _phrase query_: match on entire phrase vs. single words e.g. page must have 'Jesus Christ' and not just 'Jesus' and 'Christ"  📙 MacCormick 14
* _word location_: location of word on page
* enables phrase query 📙 MacCormick 15
* _near query_: match on entire phrase within given proximity e.g. 'Jesus Christ' where 'Jesus' within n words of 'Christ' 📙 MacCormick 17
* enables ranking 📙 MacCormick 18
```text
# e.g. query "cat sat" returns 2-2, 2-3

* the: 1-1, 1-5, 2-1, 2-5
* dog: 1-2
* stood: 1-3
* at: 1-4, 2-4
* mat: 1-6, 2-6
* cat: 2-2
* sat: 2-3
```

## sort

🔗 https://xkcd.com/1185/
🗄 `python.md` sort
📙
* Christian ch. 3
* Conery ch. 8

quicksort https://en.wikipedia.org/wiki/Quicksort https://github.com/orlp/pdqsort
* strat: D&C via partition 📙 Bhargava 4.65 https://stackoverflow.com/q/164163
* time: O(n log n); iterate input multiple times but smaller input each time; parallel versions can be O(n) 📙 Bhargava 11.208 https://softwareengineering.stackexchange.com/a/297161
* space: O(n)

---

* _bubble_: https://realpython.com/sorting-algorithms-python/
* _heap_: https://favtutor.com/blogs/heap-in-python
* _insertion_: https://realpython.com/sorting-algorithms-python/
* _merge_: used for SSTables [Kleppmann 76] https://realpython.com/sorting-algorithms-python/
* _natural_: put like w/ like re: ints, strings https://github.com/SethMMorton/natsort
* _selection_: 🗄 `algos`
* _Timsort_: https://realpython.com/sorting-algorithms-python/
* _topological_: [Bhargava 6.112]

## strategies

🔗 https://en.wikipedia.org/wiki/Approximation_algorithm#Algorithm_design_techniques

---

* _dynamic programming (DP)_: maximize X given constraint on Y or calculate optimum involves large numbers 📙 Bhargava 9.163, 178 https://www.youtube.com/watch?v=gK8KmTDtX8E
* only works for independent problems 📙 Bhargava 9.177
* used for Towers of Hanoi, Dikstra, longest substring/sequence, Fibonacci
* must have optimal substructure and overlapping sub-problems https://en.wikipedia.org/wiki/Dynamic_programming#Computer_programming
* clean up https://ngoldbaum.github.io/posts/dynamic-programming/ https://skerritt.blog/dynamic-programming/#why-is-dynamic-programming-called-dynamic-programmin https://trekhleb.dev/blog/2018/dynamic-programming-vs-divide-and-conquer/

* _divide and conquer (D&C)_: winnow to atomic case using recursion
* most (but not all) recursive algos use D&C e.g. quicksort https://stackoverflow.com/a/53796319

* _brute force_: enumerate all possible solutions
* _partition_: split list into two smaller sub-lists 🗄 `linux.md` split
* _pivot_: el used to partition
* _MapReduce_: map (apply func to each item in el) reduce (combine els) [Bhargava 11.209-10] parallel doesn't mean new runtime is old_runtime/cores bc have to load balance btw core and merge results [ibid 11.208] https://en.wikipedia.org/wiki/Parallel_algorithm 🗄 `language.md` concurrency
* _hill-climbing_: local maxima https://diff.substack.com/p/big-tech-sees-like-a-state 📙 Christian 195

* decision tree 📙 MacCormick chapter 6 https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/ https://victorzhou.com/blog/information-gain/ https://mlu-explain.github.io/
* random forest https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/ https://victorzhou.com/blog/intro-to-random-forests/ https://mlu-explain.github.io/
* gini impurity https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/ https://victorzhou.com/blog/gini-impurity/

yet to use personally
* _approximation_: aim for good enough when optimal solution too expensive/NP [Bhargava 8.147] take local maximum https://en.wikipedia.org/wiki/Approximation_algorithm
* _genetic_: select best candidates from random population https://danielmiessler.com/blog/genetic-algorithms-could-be-more-significant-than-machine-learning/  evolutionary https://www.drorpoleg.com/books-to-read-in-2023-part-2/ there's also something called 'genetic programming' whose relationship to genetic algorithms is unclear https://stackoverflow.com/a/3821746
* _greedy_: recursively choose local optimum e.g. counting change, lightest edge in MST; might not lead to global optimum but that can be ok w/ NP [Bhargava 8.144-5] https://www.interviewcake.com/concept/python3/greedy
* _linear programming_: maximize target given constraints 📙 Bhargava 11.218

# 🧮 COMPLEXITY

🔗 https://en.wikipedia.org/wiki/Computational_complexity https://en.wikipedia.org/wiki/Computational_complexity_theory

Big O
* worst-case asymptotic time complexity
* measured using base-2 logarithms 📙 Bhargava 1.7, 1.15 https://www.interviewcake.com/article/big-o-notation-time-and-space-complexity
* _asymptotic_: concerned w/ rate of growth vs. walltime 📙 Bhargava 1.12
* walltime affected by hw, compiler, input, what else is running on box

---

Conery ch. 6
> how to know when to consider average time vs. worst-case? 📙 Bhargava 11.205
* _hardware lottery_: what algos win depend on what hardware is available https://arxiv.org/abs/2009.06489
* Conery chapter 2
* https://www.youtube.com/watch?v=YX40hbAHx3s
* https://medium.com/age-of-awareness/a-brief-history-of-systems-science-chaos-and-complexity-d9198b1a198d
* https://www.kanopy.com/product/lo-and-behold-reveries-connected-world-0
* _entanglement_: everything is super complex now https://aeon.co/essays/is-technology-making-the-world-indecipherable everything has always been super complex https://www.edge.org/response-detail/26191
* https://how.complexsystems.fail/

* _time complexity_: growth rate re: number of executions https://www.interviewcake.com/article/python3/big-o-notation-time-and-space-complexity
* in Python https://wiki.python.org/moin/TimeComplexity
* multiple time complexities resolve to dominant complexity e.g. quicksort is O(n log n) https://softwareengineering.stackexchange.com/q/258509
* _space complexity_: growth rate re: memory usage https://www.interviewcake.com/article/python3/big-o-notation-time-and-space-complexity

## constants

* matter less than runtime esp. as input becomes arbitrarily large e.g. O(1) will dust O(n) if n is 1M even if O(1) is actually O(1 + 42) [4.72, IC]
* but still matter sometimes e.g quicksort is faster than merge sort [Bhargava 4.72] does yield some perf improvement https://danluu.com/algorithms-interviews/ e.g. improvement to constant that makes script 4 hours faster doesn't change Big O but does save you 4 hours https://www.interviewcake.com/article/python3/big-o-notation-time-and-space-complexity
```python
# DROP CONSTANTS
def all_plus_one(items):  # O(1 + n) = O(n)
    print(items[0])
    for item in items:
        print(item)

def half(items):  # O(n/2) = O(n)
    current_index = 0
    middle_index = len(items) / 2
    while start_index < middle_index:
        print(items[current_index])
        current_index += 1

def twice(items):  # O(2n) = O(n)
    for item in items:
        print(item)

    for item in items:
        print(item)

# DROP LESS SIGNIFICANT TERMS
def linear_and_quadratic():  # O(n + n^2) = O(n^2)
    for item in items:  # O(n)
        print(item)

    for i in items:  # O(n^2)
        for j in items:
            print(i, j)
```

## NP

🗄 `computation.md`
📙 MacCormick computed

* _NP_: non-deterministic polynomial time i.e. might get different solution each time (unlike most algos) and solutions will be in polynomial time
* used for decision problems
* how to solve https://news.ycombinator.com/item?id=28845593
* _decision problem_: problem w/ yes or no answer
* _NP-hard_: problems that are pretty goddamn hard
* _NP-complete_: not possible to solve quickly w/out approximation e.g. set covering [Bhargava 8.157, 159] 🗄 `system.md` SAT https://blog.robertelder.org/computer-science-for-engineers/ https://github.com/konstin/sudoku-in-python-packaging
* _N = NP_: 不明觉厉 https://stackoverflow.com/a/1857342/6813490

## runtimes

⏲️ https://www.pythonmorsels.com/time-complexities/
🗄️ `math.md` logarithms
🔗 https://stackoverflow.com/a/11611770

```yaml
# replace this with a generated graphs per runtime ++ graph for all together
/*** ===================================================================== ***\
 *           a         b    O(N^2)                      d                    *
 *     O(N!) a        b                O(N log N)    d                    c  *
 *           a      b                            d                 c         *
 *          a      b                          d             c        O(N)    *
 *          a    b                         d         c                       *
 *          a  b                       d      c                              *
 *         a  b                     d  c                                     *
 *         ab                   c                          O(1)              *
 *  e    e    e    e    ec   d    e    e    e    e    e     e    e    e      *
 *      ba        c      d                                                   *
 *    ba   c        d                       f    f    f    f    f    f    f  *
 ** cadf    f d    f    f    f    f    f       O(log N)                     **
\*** ===================================================================== ***/
```

✅ O(1)
* time: constant
* ops/100: 1
* map (if 1 K to V)
```python
def get_db_port():
    return DB_PORT
```

✅ O(log n)
* time: log
* ops/100: 6-ish 📙 Bhargava 1.15
* binary search, balanced BST 📙 Bhargava 11.205 📍 Python bisect https://www.fluentpython.com/extra/ordered-sequences-with-bisect/
```python
def binary(query, sorted_list):
    low_index = 0
    high_index = len(sorted_list) - 1
    while low_index <= high_index:
        mid = (high_index + low_index) // 2
        if sorted_list[mid] == query:  # assert midpoint
            return f"found {query}"
        elif sorted_list[mid] > query:  # rm high side
            high_index = mid - 1
        else:  # rm low side
            low_index = mid + 1
```

✅ O(n)
* time: linear
* ops/100: 100
* map (if n K to V)
```python
def get_db_port():
    return DB_PORT  # ❓ how does this work? wouldn't a successful lookup also then need to iterate?
```

✅ O(n log n)
* time: polynomial
* ops/100: 
* sorts
```python

```

✅ O(n^2)
* time: quadratic
* ops/100: 100k 
* traversing 2D array e.g. selection sort (❓ bubble, insertion)
* quadratic complexity 🗄 branching factor, power set https://www.natemeyvis.com/writing/on-quadratic-complexity/
```python
def selection_sort(unsorted_list):
    unsorted_list_len = len(unsorted_list)
    sorted_list = []
    for _ in range(unsorted_list_len):
        high = find_high_val(unsorted_list)
        sorted_list.append(high)
        unsorted_list.remove(high)
    return sorted_list
```

❌ O(2^n) 🗄 `math.md` power set
* time: exponential https://www.natemeyvis.com/writing/on-quadratic-complexity/
* set covering problem, knapsack problem
```python
def set_covering(states_needed, stations):
    states_covered = set()
    stations_chosen = list()
    while states_covered != states_needed:
        station_w_most_uncovered_states = None
        states_from_station_w_most = set()
        for station, states in stations.items():
            uncovered_from_current_station = states - states_covered
            if len(uncovered_from_current_station) > len(states_from_station_w_most):
                station_w_most_uncovered_states = station
                states_from_station_w_most = uncovered_from_current_station
        states_covered.update(states_from_station_w_most)
        stations_chosen.append(station_w_most_uncovered_states)
    return stations_chosen
```

✅ O(n!)
* time: factorial
* ops/100: more than billions
* traveling salesman
```python

```

# 🏺 DATA STRUCTURES

> Good programmers worry about data structures. https://softwareengineering.stackexchange.com/q/163185
🔗 https://www.interviewcake.com/data-structures-reference
📙 Conery ch. 7
🗄
* `dbms.md` non-relational
* `dbms.md` internals / datastructures
* `eng.md` store / schemas
* `education.md` design / information design
* `languages.md` typing
* `science.md` metascience / categories
* `sql.md` modeling

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

## graph

📙 Kun ch. 6 https://en.wikipedia.org/wiki/Graph_theory
🛠 https://github.com/networkx/networkx https://pragprog.com/titles/dzcnapy/complex-network-analysis-in-python/ https://github.com/dominikbraun/graph/ https://news.ycombinator.com/item?id=38834780 https://www.hytradboi.com/2022/how-to-query-almost-everything d2 https://chatgpt.com/c/671043db-1354-8004-a127-6b4152994963 https://calmcode.io/datasets/dependencies
> clean these up
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

## tree

🔗
* https://en.wikipedia.org/wiki/Tree_(data_structure)
* HDF5 https://en.wikipedia.org/wiki/Hierarchical_Data_Format https://github.com/rhuygen/hdf5_ui
🗄️
*️ `km.md` notes / tooling
*️ `language.md` compiler
*️ `protocols.md` file fmt
* `science.md` metascience / categories

TREE BUILDERS 🗄️ `html-css.md` SSG `protocols.md` JSON `km.md` notes / tooling `info.md` viz / system
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

TYPES
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

# 🟨 ZA

* _y combinator_: https://news.ycombinator.com/item?id=27673177
* cellular automaton, Conway's game of life https://en.wikipedia.org/wiki/Cellular_automaton https://robertheaton.com/2018/07/20/project-2-game-of-life/
* _byte offset_: distance from initial byte to target; used to lookup char in file [Kleppmann 72]
* _intelligent music production_: using algos to mix? https://www.amazon.com/gp/product/B0815BWLXV
* randomness https://classic.qz.com/perfect-company-2/1172282/this-company-built-one-of-the-worlds-most-efficient-warehouses-by-embracing-chaos/
* _Naive Bayes_: priors + data; naive bc assume every feature has same weight [Bhargava 10.200]
* softmax https://victorzhou.com/blog/softmax/
* visualization in Jupyter https://kylekizirian.github.io/prims-algorithm.html

---

* _audio warping_: https://stackoverflow.com/q/9953219/6813490
* geography https://github.com/jftuga/geodist

## recursion

* _base case_: case in which the function doesn't call itself
* _recursive case_: case in which function calls itself
* _partial execution_: state of function when another function called from within it (until the other function completes its own execution) [3.44]
* _perf_: can be slow bc chewing up stack space [Code Complete 17.2, Bhargava 3.40]
* _tail_: can prevent stack overflows but depends on compiler to provide optimization https://stackoverflow.com/a/37010/6813490
* tail call optimization https://blog.jonas.foo/posts/python-tail-call-optimization/

```python
def countdown(arg):
    if arg == 0:
        return None
    else:
        countdown(arg - 1)

countdown(1)

""
first frame goes on stack
first frame blocks on else, calls `countdown(0)`
second frame `countdown(0)` goes on stack
second frame comes off stack
first frame stops blocking on else, comes off stack
"""
```

## regex

📜 https://regexone.com
🛠
* https://regex101.com
* https://github.com/royreznik/rexi
* https://github.com/pemistahl/grex

METACHARACTERS
> capitalize for opposite
* `.`: wildcard i.e. any single char except new line https://regexone.com/lesson/wildcards_dot
* `\s`: white space (space, tab, new line)
* `\t`: tab only
* `\d`: any num 0-9; equivalent to `[0-9]`
* `\w`: any letter or num, incl. `_`; equivalent to `[a-zA-Z0-9]`
 
RECIPES
```sh
# starts with
^$WORD
# multiple words
rg -IN "train|muz" 23/ | termgraph
```

SEMANTICS
* _regex_: pattern to match sequence of characters
* flavors: PCRE2 (Perl) https://github.com/rust-lang/regex/issues/127
* BYO regex engine https://kean.blog/post/lets-build-regex
* _regular_: based on something called 'regular languages' https://stackoverflow.com/a/975495

---

https://drewdevault.com/2017/08/13/When-not-to-use-a-regex.html
https://news.ycombinator.com/item?id=39763750
* https://github.com/learnbyexample/py_regular_expressions/tree/master/interactive_exercises
* impl https://perl.plover.com/Regex/article.html

* why doesn't this work?
```sh
/U/z/D/z/m/z/p/m/b/method $ l | rg 1*.mp3

```
* _flags_: Python and JavaScript have https://docs.python.org/3/library/re.html#re.compile
* _multiline_: https://www.youtube.com/watch?v=ASa7jjRCLNI https://stackoverflow.com/a/587620/6813490
* _standards_: Vim vs. PCRE https://stackoverflow.com/questions/3864467/whats-the-difference-between-vim-regex-and-normal-regex
* _sink_: 🗄 `algos/python-regex.pdf` https://regexone.com/

__quantifiers__

* `\d`  == 1 digit
* `\d?` == 0 || == 1 https://regex101.com/r/XsAyxb/1 + https://regex101.com/r/C4Rg6L/1
* `\d*` >= 0
* `\d+` >= 1
* `[aeious]{2,}` >= 2
* `[aeiou]{2}` == 2 vowels
* `[aeious]{2, 5}` >= 3 && <= 5
 
__special characters__

```sh
# [] char set = match single https://regex101.com/r/EulQ8w/1
[aeiouAEIOU]
Ba  # match on 'a'

# - range
[0-9]  # match single char in range
123  # separate match for each of 1, 2, and 3
```

* `()` group https://regex101.com/r/SF2Mpd/4
* `\` escape
* `\b` boundary (`\bcat\b` 'black cat' `\bcat` 'catfish' `cat\b` 'tomcat')
* `{<num>}` repeat https://regex101.com/r/xYhGg4/1
* `|` or

* `^` exclude (when inside character set)
* `^` anchor to start (when outside character set)
* `$` anchor to end https://regex101.com/r/SF2Mpd/1
