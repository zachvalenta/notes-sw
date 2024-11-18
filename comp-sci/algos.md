# ⛩️

## 参考

> Until you start dealing with millions of people on a network or you need to blur or sharpen a million photos quickly, you can just use the work of other people. When it gets real, break out the comp sci. 🗄 `ford-code.pdf`
🔍
* https://github.com/TheAlgorithms/Python
* https://xlinux.nist.gov/dads/
📚
* ✅ Bhargava grokking algorithms
* Christian algorithms to live by
* Dasgupta algorithms
* MacCormick computed
* MacCormick nine algorithms
* Skiena manual https://www.algorist.com/ https://fabiensanglard.net/algorithms_and_datastructures/index.php
* Wengrow ds/algos https://pragprog.com/titles/jwpython/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-1/ https://pragprog.com/titles/jwpython2/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-2/

## 进步

https://www.manning.com/books/optimization-algorithms
🛣️ https://roadmap.sh/datastructures-and-algorithms https://roadmap.sh/computer-science https://roadmap.sh/python

* _algorithm_: solution (Dijkstra) to specific problem (lightest path through unweighted graph)
* sometimes the name of the problem (set covering)

> do you have the PDF? https://news.ycombinator.com/item?id=41967900

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

# 🧠 NEURAL NETWORKS

🗄️ `graphs.md` https://www.manning.com/books/graph-neural-networks-in-action https://www.manning.com/books/math-and-architectures-of-deep-learning https://fleetwood.dev/posts/you-could-have-designed-SOTA-positional-encoding
BYO https://www.manning.com/books/design-a-machine-learning-system-design-from-scratch

FUNCTIONS
```python
def af(arg, weight):
    activation = arg * weight
    return activation
```
* _activation function (AF)_: arg * weight = activation 📙 Trask 9.162 https://stats.stackexchange.com/a/307295
* _weight_: importance of arg 📙 Trask 3.23, 3.27
* _activation_: return of AF https://stats.stackexchange.com/a/307295 https://www.youtube.com/watch?v=aircAruvnKk 3:25 📙 Trask 3.46
* _weighted sum_: multiply input by weights and sum; aka dot product 📙 Trask 3.30

PROPAGATION
* _datapoint_: arg to network as a whole (vs. weight) 📙 Trask 3.22
* _shape_: types of datapoints 📙 Trask 3.23
* _propagate_: pass datapoint to network 📙 Trask 3.22 e.g. pass n pixels for computer vision neural network
* _forward propagation_: datapoints go straight through network 📙 Trask 3.46
* _back propagation_: figuring out which weight from previous layer contributed to increased error at higher layer and updating it 📙 Trask 6.119 https://www.youtube.com/watch?v=Ilg3gGewQ5U
* _prediction_: return of neural network 📙 Trask 3.25

BASICS https://www.youtube.com/watch?v=aircAruvnKk https://karpathy.ai/zero-to-hero.html
* _neural network_: graph (network) that mimics the brain (neural) https://victorzhou.com/blog/intro-to-neural-networks/
* in NN, just a var holding boolean value https://www.youtube.com/watch?v=aircAruvnKk 2:55
* akin to logic gate https://victorzhou.com/blog/intro-to-neural-networks/
* as non-leaky abstraction https://blog.cerebralab.com/Neural_networks_as_non-leaky_mathematical_abstraction
* _LLM_: type of neural network, predict some likely output based on a given input https://www.seangoedecke.com/how-llms-work/

TYPES
* _deep_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/how-deep-neural-networks-work
* _recurrent_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm https://victorzhou.com/blog/intro-to-rnns/
* _convolutional_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/how-convolutional-neural-networks-work https://victorzhou.com/blog/intro-to-cnns-part-1/ good for computer vision https://www.youtube.com/watch?v=aircAruvnKk 2:10

## features

* _feature_: metadata 📙 Bueno [25]

---

* _feature extraction_: key attr e.g. semantic meaning, syntax, sentiment analysis https://zackproser.com/blog/introduction-to-embeddings
* _Naive Bayes_: priors + data; naive bc assume every feature has same weight [Bhargava 10.200]
* softmax https://victorzhou.com/blog/softmax/
* visualization in Jupyter https://kylekizirian.github.io/prims-algorithm.html

## labels

* https://calmcode.io/datasets/clinc
* https://calmcode.io/labs/doubtlab
* https://labelerrors.com/
* https://www.manning.com/books/data-without-labels

TYPES
* _supervised_: labeled data during training, unlabeled during predication [Trask 2.11]
* _unsupervised_: unlabeled data during training and prediction [Trask 13]
* _reinforcement_: no labels but algo can tell if it's getting hotter or colder http://aiplaybook.a16z.com/docs/guides/dl-learning#user-content-reinforcementlearning
* _parameters_: https://www.youtube.com/watch?v=BbZ2m8mfwYU
* _parametric_: modeler derives parameters [Trask 2.14, 2.18]
* _nonparametric_: model derives parameters [Trask 2.14, 2.18]

## stdlib

* _Tensorflow_: tensor (array) flow (operations) https://github.com/Hvass-Labs/TensorFlow-Tutorials https://news.ycombinator.com/item?id=42133844
* _Keras_: less verbose Tensorflow (will eventually be packaged w/) https://victorzhou.com/blog/keras-neural-network-tutorial/ https://news.ycombinator.com/item?id=42133844
* _PyTorch_: superceded Tensorflow https://thegradient.pub/state-of-ml-frameworks-2019-pytorch-dominates-research-tensorflow-dominates-industry/ NumPy that can run in parallel on GPUs; tensor (array 类似 NumPy array) scalar (single value) vector (array) matrix (2d array) tensor (multi-dimensional array) https://aiweirdness.com/post/189170306297/how-to-begin-a-novel alternative https://github.com/geohot/tinygrad https://github.com/Lightning-AI/lightning
* _CUDA_: GPUs aaS
* _sci-kit learn_: https://jakevdp.github.io/PythonDataScienceHandbook/
* _Matplotlib_: eaten by Python https://realpython.com/podcasts/rpp/197/
* Matlab for Python https://jakevdp.github.io/PythonDataScienceHandbook/
* _MLX_: numpy for Apple silicon https://github.com/ml-explore/mlx
* _Numpy_: subset of scipy https://jakevdp.github.io/PythonDataScienceHandbook/ 📙 Trask 44
```python
# numpy.array.dot https://stackoverflow.com/a/35208273 📙 Trask 3.35
def dot(v1, v2):  # vectors
    return sum(x*y for x,y in zip(v1,v2))

dot([1,2,3], [4,5,6])
```
## transformers

* https://www.manning.com/books/transformers-in-action
* https://www.amazon.com/gp/product/1098134184
* https://realpython.com/huggingface-transformers/

## vectors

* _scalar_: single value 📙 Trask [3.45] Bradshaw [62]
* _vector_: list 📙 Trask 3.31
* _matrix_: list of lists 📙 Trask 3.41 e.g. NumPy array, Pandas dataframe
* _elementwise operation_: perform same operation on two vectors of equal length 📙 Trask 3.31 i.e. zip
* _dimensionality_: number of components in a vector https://zackproser.com/blog/introduction-to-dimensionality#what-is-dimensionality-
* _embedding_: categorized repr of text/image/audio https://simonwillison.net/2023/Oct/23/embeddings/ https://blog.wilsonl.in/hackerverse/ https://www.youtube.com/watch?v=zzY64Qu8HHc https://news.ycombinator.com/item?id=41473518 https://www.youtube.com/watch?v=hB7sGE0W8CI https://news.ycombinator.com/item?id=42013762 try it out https://github.com/taylorai/aiq

# 🦋 TYPES

---

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

## autocorrect

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

## knapsack problem

https://en.wikipedia.org/wiki/knapsack_problem

* given container w/ weight capacity (knapsack) and items w/ weights and values, calculate most valuable combination of items that could fit into container 📙 Bhargava 8.144, 9.162
* an example of combinatorics (part of stats? calculus? both? https://www.khanacademy.org/math/precalculus)
* ❓ version of set covering or different animal entirely?
* ❓ howto: last column serves as optimal solution until cell at last row and column, at which you compare previous optimal against...power set of all other other items? 📙 Bhargava 9.168  https://www.youtube.com/watch?v=YRBON9sIZ2Y https://aiven.io/blog/solving-the-knapsack-problem-in-postgresql

## KNN

🗄 `math.md` regression

* _k-nearest neighbors_: taxonomize based on proximate elements i.e. those that have similar attributes
* form of supervised learning https://stats.stackexchange.com/a/56504
* used for recommendation system, regression, OCR 📙 Bhargava [186,195,196]
* recommendation systems https://github.com/gorse-io/gorse
* https://philippmuens.com/k-nearest-neighbors-from-scratch/
* https://www.freecodecamp.org/learn/machine-learning-with-python/machine-learning-with-python-projects/book-recommendation-engine-using-knn
* https://realpython.com/courses/knn-python/
* https://news.ycombinator.com/item?id=26328958
* https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/
* 📙 MacCormick chapter 6
* _k means_: group points into K clusters; unsupervised https://stats.stackexchange.com/a/56504

## Monte Carlo

🗄 `math.md` Markov chain

* _Monte Carlo tree search (MCTS)_: domain independent https://www.youtube.com/watch?v=Fbs4lnGLS8M @ 12:00
* tree: roots = next moves, branches = n order paths
* search: takes weights from neural net, traverse branches, report back
* _Monte Carlo_: 📙 Christian chapter 9 https://pbpython.com/monte-carlo.html https://news.ycombinator.com/item?id=27379310
* determine weights for MCTS
* weights = secret sauce https://github.com/leela-zero/leela-zero
* https://easylang.dev/apps/tutorial_mcarlo.html
* aka simulation 📙 Konnikova bluff Zuckerman simons
* https://sirupsen.com/napkin/problem-16-simulation 
* https://www.erichgrunewald.com/posts/simulations-of-diversity-hiring/
* https://conversationswithtyler.com/episodes/annie-duke/
* _minimax_: predecessor to MCTS https://www.youtube.com/watch?v=Fbs4lnGLS8M @ 1:15 used in chess 4:30 https://marginalrevolution.com/marginalrevolution/2021/05/maradona-plays-minimax.html

## NLP

📙 https://www.manning.com/books/natural-language-processing-in-action-second-edition
🛠️ https://spacy.io/ https://training.talkpython.fm/courses/build-an-audio-ai-app-with-python-and-assemblyai
🗄
* `literature.md` distant reading
* `psychology.md` reading
* `system.md` search engine

BASICS
* _Eliza_: https://web.njit.edu/~ronkowit/eliza.html
* _NLP_: linguistics + CS
* rule system (noun phrase can be followed by noun, article, etc.) to construct parse tree
* use cases: speech synthesis http://aiplaybook.a16z.com/docs/guides/nlp speech to text https://www.fullstackpython.com/blog/transcribe-recordings-speech-text-assemblyai.html
* libraries: nltk, spaCy
* _language detection_: https://github.com/pemistahl/lingua-go
* _sentiment analysis_: determine emotional content https://aeon.co/ideas/why-are-pop-songs-getting-sadder-than-they-used-to-be https://matthagy.github.io/rh_comment_categories/
* _word cloud_: https://dataanalysis.substack.com/p/generating-a-word-cloud-in-python?s=r
* clean up https://nostarch.com/NLPPython https://codewords.recurse.com/issues/seven/data-driven-literary-analysis https://www.fast.ai/2019/07/08/fastai-nlp/ https://speakerdeck.com/pycon2015/adam-palay-words-words-words-reading-shakespeare-with-python https://victorzhou.com/blog/better-profanity-detection-with-scikit-learn/ https://calmcode.io/labs/scikit-partial
* word2vec, byte-pair encoding, LSTM https://arpit.substack.com/p/how-zomato-improved-its-search-using https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm 
* https://github.com/rspeer/wordfreq

SEMANTICS
* phoneme recognition https://github.com/persephone-tools/persephone
* _tokenize_: break into words or subsets of words
* _span_: section of text https://rajpurkar.github.io/SQuAD-explorer/ https://0x65.dev/blog/2019-12-05/a-new-search-engine.html#fn1
* _stemming_: rm pre/suffix; can also mean to include related results from search engine e.g. search 'fish', get back results for 'fishy', 'fishing' https://news.ycombinator.com/item?id=24051229
* _parts of speech_: tokenization but for syntax
* _stopword removal_: strip out non-semantic words (articles, &c.)
* _n-gram_: items (word, phraes) collected from text https://en.wikipedia.org/wiki/N-gram
* used for finding most commonly occuring words https://news.ycombinator.com/item?id=24286844
* used for language detection https://github.com/pemistahl/lingua-go
* _disambiguation_: teach the machine context ('cool' indicates temperature and social prestige)
* _stylometry_: analyze writing style https://news.ycombinator.com/item?id=33755016
* _text classification_: https://www.youtube.com/watch?v=VtRLrQ3Ev-U
* _speech recognition_: https://www.youtube.com/watch?v=mYUyaKmvu6Y

## search

🗄 `math.md` linear algebra

* _search space_: set of possible solutions to the problem constraints https://en.wikipedia.org/wiki/Feasible_region
* _simple_: 🗄 `/algos`
* _binary_: 🗄 `/algos`; using BST (❌ log O of n average case and O of n worst case, sequential access ✅ faster mutative operations) [Bhargava 11.205]
* _breadth-first (bfs)_: 🗄 `/algos` https://healeycodes.com/practical-intro-to-graphs/
* _depth-first (dfs)_:
> Doing great work is a depth-first search whose root node is the desire to. So "If at first you don't succeed, try, try again" isn't quite right. It should be: If at first you don't succeed, either try again, or backtrack and then try again. http://paulgraham.com/greatwork.html
* _Aho-Corasick_: trie https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm https://www.lambdafunctions.com/articles/racing-sed-with-rust
* _bm25_: full text, used by Lucene and SQLite https://emschwartz.me/understanding-the-bm25-full-text-search-algorithm/

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
* _robots.txt_: file that tells crawlers what files to ignore https://adamj.eu/tech/2020/02/10/robots-tx https://pythonbytes.fm/episodes/show/376/every-dunder-method-in-a-python-lockbox https://x.com/didaoh/status/1814341975195492378 https://news.ycombinator.com/item?id=41960003 you can just ignore it e.g. Perplexity
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

## set covering

* given target set and a collection of source sets, find the smallest sub-collection of target sets whose union equals the target set
* howto (brute): go through power set, either O(2^n) or O(n!) 📙 Bhargava 8.147, 8.152, 9.162
```python

```
* howto (approximation): iterate source sets and take whichever has the most from the target set that hasn't been taken already, O(n^2) 📙 Bhargava 8.152
```python

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

* https://gwern.net/resorter
* _bubble_: https://realpython.com/sorting-algorithms-python/
* _heap_: https://favtutor.com/blogs/heap-in-python
* _insertion_: https://realpython.com/sorting-algorithms-python/
* _merge_: used for SSTables [Kleppmann 76] https://realpython.com/sorting-algorithms-python/
* _natural_: put like w/ like re: ints, strings https://github.com/SethMMorton/natsort
* _selection_: 🗄 `algos`
* _Timsort_: https://realpython.com/sorting-algorithms-python/
* _topological_: [Bhargava 6.112]

# 🟨 ZA

* _y combinator_: https://news.ycombinator.com/item?id=27673177
* cellular automaton, Conway's game of life https://en.wikipedia.org/wiki/Cellular_automaton https://robertheaton.com/2018/07/20/project-2-game-of-life/
* _byte offset_: distance from initial byte to target; used to lookup char in file [Kleppmann 72]
* _intelligent music production_: using algos to mix? https://www.amazon.com/gp/product/B0815BWLXV
* randomness https://classic.qz.com/perfect-company-2/1172282/this-company-built-one-of-the-worlds-most-efficient-warehouses-by-embracing-chaos/

---

* _audio warping_: https://stackoverflow.com/q/9953219/6813490
* geography https://github.com/jftuga/geodist

## recursion

📙 https://www.amazon.com/gp/product/1718502028

* _base case_: case in which the function doesn't call itself
* _recursive case_: case in which function calls itself
* _partial execution_: state of function when another function called from within it (until the other function completes its own execution) [3.44]
* perf: can be slow bc chewing up stack space [Code Complete 17.2, Bhargava 3.40]
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
* _linear programming_: maximize target given constraints 📙 Bhargava 11.218 https://www.jeremykun.com/2017/09/24/linear-programming-and-healthy-diets-part-2/
