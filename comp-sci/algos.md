# ⛩️

## 参考

> Until you start dealing with millions of people on a network or you need to blur or sharpen a million photos quickly, you can just use the work of other people. When it gets real, break out the comp sci. 🗄 `ford-code.pdf`
🔍
* https://github.com/TheAlgorithms/Python
* https://xlinux.nist.gov/dads/
📚
* ✅ Bhargava grokking algorithms
* ✅ Christian algorithms to live by
* Dasgupta algorithms
* La Rocca advanced https://www.manning.com/books/advanced-algorithms-and-data-structures
* Khamis optimization https://www.manning.com/books/optimization-algorithms
* MacCormick nine algorithms
* Skiena manual https://www.algorist.com/ https://fabiensanglard.net/algorithms_and_datastructures/index.php
* ⭐️ Tuckfield https://nostarch.com/Dive-Into-Algorithms
* ⭐️ Wengrow ds/algos https://pragprog.com/titles/jwpython/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-1/ https://pragprog.com/titles/jwpython2/a-common-sense-guide-to-data-structures-and-algorithms-in-python-volume-2/

## 进步

https://neetcode.io/

taxonomy https://livebook.manning.com/book/advanced-algorithms-and-data-structures
🛣️ https://roadmap.sh/datastructures-and-algorithms https://roadmap.sh/computer-science https://roadmap.sh/python

LeetCode https://www.youtube.com/@NeetCodeIO/videos

* _algorithm_: solution (Dijkstra) to specific problem (lightest path through unweighted graph)
* sometimes the name of the problem (set covering)

> do you have the PDF? https://news.ycombinator.com/item?id=41967900

streams? SICP https://blog.moertel.com/posts/2013-05-26-python-lazy-merge.html

fizz buzz
fibonacci
> look up the ten algorithms you have to know, rosetta code, project euler

minimax https://claytonwramsey.com/blog/sixty-four-elo/

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
> With just two banks, you only need one connection. Add a third, and now you have three connections in a triangle. With four, it’s six connections. Life gets very complicated very fast, in what technologists would recognize as an N-squared relationship. [Patrick notes: Many readers have passed geometry at some point and know this  is the number of edges of an N-sided polygon plus the number of diagonals you could draw, which is (of course) N * (N - 1) / 2. In CS, we say “Eh, for sufficiently large N, that’s basically N^2.”]  https://www.complexsystemspodcast.com/episodes/money-movement-erik-torenberg/
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

# 💘 MATCHING

🗄️
* `ml.md` entity recognition
* `tools.md` fuzzy find, file > diff

```sh
Text Similarity Algorithms
├── Edit Distance Based
│   ├── Levenshtein (fuzzywuzzy default)
│   │   └── Faster C implementation (python-Levenshtein)
├── Sequence Based
│   └── SequenceMatcher (difflib)
│       └── Uses Ratcliff/Obershelp algorithm
└── Other Approaches
    ├── Phonetic (Soundex, Metaphone)
    ├── Token Based (cosine similarity, Jaccard)
    └── Context Based (word2vec, etc)
```

SEMANTICS
* _substring_: common contiguous char 📙 Bhargava [179,182]
```markdown
y _bcd_ af 
x _bcd_ edf
```
* _subsequence_: discontiguous char; used for autocorrect 📙 Bhargava [184]
```markdown
y _bcd_ a _f_
x _bcd_ ed _f_
```
* _substring_: char in order and continuous e.g. for `hello there` valid substrings are `hello` and `llo th` https://stackoverflow.com/a/49688118/6813490
* _subsequence_: char in order but not necessarily continuous e.g. for `hello there` a valid subsequences is `hll th` (note missing `e`)
> these moved in from different file, don't know which set of definitions valid

BYO fuzzy finder https://github.com/amjith/fuzzyfinder
```python
import re
def fuzzyfinder(input, collection, accessor=lambda x: x, sort_results=True, ignore_case=True):
    suggestions = []
    input = str(input) if not isinstance(input, str) else input
    pat = ".*?".join(map(re.escape, input))
    pat = "(?=({0}))".format(pat)  # lookahead regex to manage overlapping matches
    regex = re.compile(pat, re.IGNORECASE if ignore_case else 0)
    for item in collection:
        r = list(regex.finditer(accessor(item)))
        if r:
            best = min(r, key=lambda x: len(x.group(1)))  # find shortest match
            suggestions.append((len(best.group(1)), best.start(), accessor(item), item))

    if sort_results:
        return (z[-1] for z in sorted(suggestions))
    else:
        return (z[-1] for z in sorted(suggestions, key=lambda x: x[:2]))
```

## difflib

* simple
```python
def fuzzy_search(items, query, threshold=0.6):
    from difflib import SequenceMatcher
    return [
        item for item in items 
        if SequenceMatcher(None, query, item.lower().replace(' ', '')).ratio() >= threshold
    ]
```

* higher score for membership
```python
def fuzzy_search(items, query, threshold=0.75):
    '''
    >>> brands = ['Bakers Pride', 'Bakers Aid', 'Banner Corp', 'Baumer LLC']
    >>> fuzzy_search(brands, 'baker')
    ['Bakers Pride', 'Bakers Aid']
    >>> fuzzy_search(brands, 'bakerpride')
    ['Bakers Pride']
    '''
    from difflib import SequenceMatcher
    matches = []
    for item in items:
        item_lower = item.lower()
        if query in item_lower:
            matches.append((1.0, item))
            continue
        ratios = [
            SequenceMatcher(None, query, item_lower).ratio(),
            SequenceMatcher(None, query, item_lower.replace(' ', '')).ratio(),
        ]
        best_ratio = max(ratios)
        if best_ratio >= threshold:
            matches.append((best_ratio, item))
    return [item for _, item in sorted(matches, reverse=True)]
```

## mask

* _mask_: boolean array for filtering
* synonym for filter e.g. mask in|out
```python
# res is our mask i.e. filters out non-matching brands
query = 'smith'
brands = ['A. O. Smith', 'Bakers Pride', 'ABB']
mask = [query in brand.lower() for brand in brands]
matches = [brand for brand, match in zip(brands, mask) if match]
```

## flashtext

🗄️ `graphs.md` trees > trie

```txt
* Category: Keyword extraction and exact pattern matching.
* Purpose: Efficiently finds and replaces keywords in a text using a Trie-based approach. Unlike regex, it avoids redundant searches and works faster for large keyword sets.
* Use Cases:
* Search: Extract keywords or highlight them within a document.
* Natural Language Processing: Extract entities from text.
* Log Analysis: Quickly find specific terms in logs.
* Nature: Optimized for high-speed keyword matching, especially for large dictionaries. Its time complexity is closer to O(n) where n is the length of the text.
```

https://calmcode.io/shorts/flashtext.py
https://github.com/vi3k6i5/flashtext/
https://arxiv.org/abs/1711.00046

```python
class FlashText:
    def __init__(self, case_sensitive=True):
        self.case_sensitive = case_sensitive
        self.keyword_trie = {}
        self.keyword_end = "_end"  # Special marker for end of a keyword

    def add_keyword(self, keyword):
        """Add a keyword to the Trie."""
        if not self.case_sensitive:
            keyword = keyword.lower()
        current_dict = self.keyword_trie
        for char in keyword:
            current_dict = current_dict.setdefault(char, {})
        current_dict[self.keyword_end] = keyword

    def extract_keywords(self, text):
        """Extract keywords from the input text."""
        if not self.case_sensitive:
            text = text.lower()
        keywords_found = []
        current_dict = self.keyword_trie
        text_length = len(text)
        i = 0
        while i < text_length:
            current_char = text[i]
            if current_char in current_dict:
                temp_dict = current_dict
                j = i
                keyword_match = None
                while j < text_length and text[j] in temp_dict:
                    temp_dict = temp_dict[text[j]]
                    if self.keyword_end in temp_dict:
                        keyword_match = temp_dict[self.keyword_end]
                    j += 1
                if keyword_match:
                    keywords_found.append(keyword_match)
                    i = j - 1  # Skip the matched keyword
            i += 1
        return keywords_found

    def replace_keywords(self, text, replacement_dict):
        """Replace keywords in the text with their corresponding replacements."""
        if not self.case_sensitive:
            text = text.lower()
        result = []
        current_dict = self.keyword_trie
        text_length = len(text)
        i = 0
        while i < text_length:
            current_char = text[i]
            if current_char in current_dict:
                temp_dict = current_dict
                j = i
                keyword_match = None
                while j < text_length and text[j] in temp_dict:
                    temp_dict = temp_dict[text[j]]
                    if self.keyword_end in temp_dict:
                        keyword_match = temp_dict[self.keyword_end]
                    j += 1
                if keyword_match:
                    replacement = replacement_dict.get(keyword_match, keyword_match)
                    result.append(replacement)
                    i = j - 1  # Skip the matched keyword
                else:
                    result.append(text[i])
            else:
                result.append(text[i])
            i += 1
        return ''.join(result)

flash_text = FlashText(case_sensitive=False)
flash_text.add_keyword("cat")
flash_text.add_keyword("caterpillar")
text = "The caterpillar is a cat."
keywords = flash_text.extract_keywords(text)
print("Extracted Keywords:", keywords)  # Output: ['caterpillar', 'cat']
replacements = { "cat": "feline", "caterpillar": "larva" }
replaced_text = flash_text.replace_keywords(text, replacements)
print("Replaced Text:", replaced_text)  # Output: "The larva is a feline."
```

## Levenshtein distance

```txt
* Category: String similarity and approximate matching.
* Purpose: Measures the minimum number of single-character edits (insertions, deletions, substitutions) required to transform one string into another.
* Use Cases:
* Search: Used in fuzzy search or approximate string matching to find matches that are similar but not exact (e.g., autocorrect, typo correction).
* Natural Language Processing: Comparing words, phrases, or text similarity.
* Data Cleaning: Finding and reconciling near-duplicate entries.
* Nature: Computationally intensive for large datasets due to its O(n * m) complexity for strings of length n and m.
```
```txt
1. Dynamic Programming Algorithm:
Levenshtein distance uses a dynamic programming approach to calculate the minimum number of single-character edits (insertions, deletions, or substitutions) required to change one string into another.
It builds a 2D matrix where each cell represents the cost of transforming a substring of one string into a substring of another.
2. String Similarity Algorithm:
It is used to quantify the difference (or similarity) between two strings, making it part of the broader category of string matching or string similarity algorithms.
3. Metric Space Algorithm:
Levenshtein distance satisfies the properties of a metric: non-negativity, symmetry, and the triangle inequality, making it a distance metric for strings.
```

* https://blog.paperspace.com/implementing-levenshtein-distance-word-autocomplete-autocorrect/
* https://www.youtube.com/watch?v=kTS2b6pGElE
* https://towardsdatascience.com/text-similarity-w-levenshtein-distance-in-python-2f7478986e75
* https://xnacly.me/posts/2024/making-sql-keyword-suggestions-work/
* BK-tree https://github.com/benhoyt/pybktree
* _edlib_: https://github.com/hbollon/go-edlib 

## thefuzz

📜 https://github.com/seatgeek/thefuzz https://github.com/seatgeek/fuzzywuzzy

* https://github.com/zachvalenta/capp-matchme
```python
"""
I have two data sources, both CSVs. They both have a single column. One is pretty short (700 LOC). The other is fairly long (~1M LOC).
"""
import csv
from thefuzz import fuzz
from tqdm import tqdm
import polars as pl
short_csv_path = "maxi.csv"
long_csv_path = "mpns.csv"
similarity_threshold = 85
short_data = pl.read_csv(short_csv_path).to_dicts()
long_data = pl.read_csv(long_csv_path).to_dicts()
short_column = list(short_data[0].keys())[0]
long_column = list(long_data[0].keys())[0]
results = []
for short_row in tqdm(short_data, desc="Processing short CSV"):
    short_value = short_row[short_column]
    best_match = None
    best_similarity = 0
    for long_row in long_data:
        long_value = long_row[long_column]
        similarity = fuzz.ratio(short_value, long_value)
        if similarity > best_similarity:
            best_similarity = similarity
            best_match = long_value
    if best_similarity >= similarity_threshold:
        results.append({
            "short_value": short_value,
            "long_match": best_match,
            "similarity": best_similarity,
        })
```

# 🥇 RANKING

## bm25

> Best for ranking documents by relevance to a query.

* full text https://emschwartz.me/understanding-the-bm25-full-text-search-algorithm/
* used by Lucene/Solr/Elasticsearch, SQLite, Postgres https://news.ycombinator.com/item?id=43237911
* impl: https://github.com/jankovicsandras/bm25opt https://news.ycombinator.com/item?id=42790902
* alternative: Okapi BM25F
> Spent the last week looking into search - embeddings, BM25, how LLMs fit into the picture, and so on - and then, surprise, this popped up on HackerNews: FastGraphRAG. I haven’t even looked at the project itself yet, because this comment tripped me up: "Hypothetical answer generation from a query using an LLM, and then using that hypothetical answer to query for embeddings works really well." They use an LLM to generate hypothetical answers to a query and then use those answers to find relevant documents by comparing them in vector space. Don't know how else to put it, so pardonnez mon langage, but that's fucking nuts. https://registerspill.thorstenball.com/p/joy-and-curiosity-16

```txt
 Okapi BM25F
How it works:
A variant of BM25 that considers different fields (e.g., title, headers, body content) with different weights.
Boosts relevance of terms in high-priority fields like titles.
Application: Used in document retrieval systems to handle structured documents.
```

## PageRank

BYO https://news.ycombinator.com/item?id=44039744

> Best for ranking nodes (e.g., web pages) by global importance in a graph.

that weights on number of incoming links (and their popularity)

* https://0x65.dev/blog/2019-12-06/building-a-search-engine-from-scratch.html

```txt
Links as Votes: A link from one page to another is treated as a "vote" of confidence in the destination page. The idea is that if many pages link to a given page, it is likely more important or relevant.

Popularity of Links Matters: Not all links are equal. A link from a highly-ranked (popular) page is worth more than a link from a less popular page. This ensures that not just the quantity, but also the quality of links is factored in.

Recursive Nature: The importance of a page is influenced by the importance of the pages linking to it, and their importance is in turn influenced by the pages linking to them. This creates a recursive feedback loop.

Damping Factor: The algorithm includes a damping factor, typically around 0.85, which accounts for the probability that a user will randomly jump to another page (e.g., by typing a URL directly) rather than following links. This prevents the PageRank values from being entirely link-dependent and ensures the model reflects real-world behavior better.
```

```python
from collections import defaultdict
def pagerank(graph, damping_factor=0.85, iterations=100):
    # Initialize PageRank values to 1/N
    nodes = list(graph.keys())
    N = len(nodes)
    ranks = {node: 1 / N for node in nodes}
    
    for _ in range(iterations):
        new_ranks = defaultdict(float)
        for node in nodes:
            # Distribute current rank to outbound links
            outbound_links = graph[node]
            if outbound_links:
                shared_rank = ranks[node] / len(outbound_links)
                for outbound in outbound_links:
                    new_ranks[outbound] += shared_rank
            # Handle dangling nodes (no outbound links)
            else:
                for other_node in nodes:
                    new_ranks[other_node] += ranks[node] / N
        # Apply the damping factor
        for node in nodes:
            new_ranks[node] = (1 - damping_factor) / N + damping_factor * new_ranks[node]
        ranks = new_ranks
    return ranks

example_graph = {
    "A": ["B", "C"],
    "B": ["C", "D"],
    "C": ["A"],
    "D": ["C"],
    "E": ["A", "D"],
}

result = pagerank(example_graph)
print("PageRank results:")
for page, rank in sorted(result.items(), key=lambda x: x[1], reverse=True):
    print(f"{page}: {rank:.4f}")
```
```python
import numpy as np

def pagerank_numpy(graph, damping_factor=0.85, tol=1e-6):
    # Step 1: Create the adjacency matrix
    nodes = list(graph.keys())
    N = len(nodes)
    node_idx = {node: i for i, node in enumerate(nodes)}  # Map node to index
    adjacency_matrix = np.zeros((N, N))
    
    for node, outbound_links in graph.items():
        if outbound_links:
            for link in outbound_links:
                adjacency_matrix[node_idx[link], node_idx[node]] = 1 / len(outbound_links)
        else:  # Handle dangling nodes
            adjacency_matrix[:, node_idx[node]] = 1 / N
    
    # Step 2: Create the Google matrix
    M = damping_factor * adjacency_matrix + (1 - damping_factor) / N * np.ones((N, N))
    
    # Step 3: Initialize the rank vector
    R = np.ones(N) / N  # Start with equal rank for all nodes
    
    # Step 4: Power iteration to compute PageRank
    delta = 1
    while delta > tol:
        R_new = M @ R  # Matrix-vector multiplication
        delta = np.linalg.norm(R_new - R, ord=1)  # Convergence check (L1 norm)
        R = R_new
    
    # Map back to node names
    return {nodes[i]: rank for i, rank in enumerate(R)}

# Example graph (adjacency list format)
example_graph = {
    "A": ["B", "C"],
    "B": ["C", "D"],
    "C": ["A"],
    "D": ["C"],
    "E": ["A", "D"],
}
# Run the PageRank algorithm
result = pagerank_numpy(example_graph)
# Print the results
print("PageRank results:")
for page, rank in sorted(result.items(), key=lambda x: x[1], reverse=True):
    print(f"{page}: {rank:.4f}")

```

SYMPY IMPL
```python
from sympy import symbols, Eq, Function, Sum, pretty, latex
from sympy.abc import i, j, d

PR = Function("PR")  # PageRank function
M = symbols("M")  # Transition matrix
v = symbols("v")  # Personalization vector
R = symbols("R")  # Rank vector
N = symbols("N", positive=True, integer=True)  # Number of nodes
L = Function("L")(j)  # Links to node
C = Function("C")(j)  # Outbound links count
# PageRank equation
eq = Eq(PR(i), (1 - d) / N + d * Sum(PR(j) / C, (j, 1, N)))

print("Plain text:")
print(eq)
print("\nPretty printed (Unicode):")
print(pretty(eq))
print("\nLaTeX representation:")
print(latex(eq))
```

## TF-IDF

> Best for evaluating the importance of terms in a corpus or performing basic relevance scoring.
> Document classification

* https://jamesg.blog/2024/08/17/tf-idf-python/
* https://simonwillison.net/2020/Dec/19/dogsheep-beta/

```txt
What are alternatives to PageRank that *do* directly measure content relevance, whether through keyword matching or other means?
```

# 🔍 SEARCH

🗄
* `math.md` linear algebra
* `system.md` search 

https://github.com/tsenart/kth
* _search space_: set of possible solutions to the problem constraints https://en.wikipedia.org/wiki/Feasible_region

ZA
* _simple_: 🗄 `/algos`

---

https://avi.im/blag/2024/galloping-search/
* _Aho-Corasick_: trie https://en.wikipedia.org/wiki/Aho%E2%80%93Corasick_algorithm https://www.lambdafunctions.com/articles/racing-sed-with-rust https://github.com/BurntSushi/aho-corasick
* index https://jamesg.blog/2024/07/16/build-a-search-index/
* semantic https://news.ycombinator.com/item?id=41088273 https://github.com/arunsupe/semantic-grep https://blog.elicit.com/semantic-search/
* shazam https://github.com/cgzirim/seek-tune https://news.ycombinator.com/item?id=41127726
* https://www.alexmolas.com/2024/02/05/a-search-engine-in-80-lines.html
* _A*_: https://www.redblobgames.com/pathfinding/a-star/introduction.html 
* _Bellman-Ford_: Dijkstra for negative-weighted [7.130]
* _Dijkstra_: 🗄 `/algos` https://medium.com/basecs/finding-the-shortest-path-with-a-little-help-from-dijkstra-613149fbdc8e https://en.wikipedia.org/wiki/Dynamic_programming#Dijkstra's_algorithm_for_the_shortest_path_problem
* _optimal stopping_: related to dynamic programming, Bellman 📙 Christian chapter 1 https://en.wikipedia.org/wiki/Optimal_stopping
* _traveling salesperson(TSP)_: Bhargava 8.157 https://medium.com/basecs/the-trials-and-tribulations-of-the-traveling-salesman-56048d6709d seems like genetic algorithms are popular for this https://www.youtube.com/watch?v=9zfeTw-uFCw https://towardsdatascience.com/evolution-of-a-salesman-a-complete-genetic-algorithm-tutorial-for-python-6fe5d2b3ca35 https://www.quantamagazine.org/computer-scientists-break-traveling-salesperson-record-20201008/ https://news.ycombinator.com/item?id=24761105 https://joseprupi.github.io/misc/2023/08/19/playing_with_genetic_algorithms_in_python.html 📙 Christian chapter 8 https://www.math.uwaterloo.ca/tsp/korea/index.html

## binary

----

* _binary_: 🗄 `/algos`; using BST (❌ log O of n average case and O of n worst case, sequential access ✅ faster mutative operations) [Bhargava 11.205]

## bfs/dfs

----

* _breadth-first (bfs)_: 🗄 `/algos` https://healeycodes.com/practical-intro-to-graphs/
* _depth-first (dfs)_:
> Doing great work is a depth-first search whose root node is the desire to. So "If at first you don't succeed, try, try again" isn't quite right. It should be: If at first you don't succeed, either try again, or backtrack and then try again. http://paulgraham.com/greatwork.html
* _dfs_: https://medium.com/basecs/deep-dive-through-a-graph-dfs-traversal-8177df5d0f13 

## engine

----

🗄 `za/search-engine` (port data to query sandbox)

* BYO https://news.ycombinator.com/item?id=39293050 https://www.alexmolas.com/2024/02/05/a-search-engine-in-80-lines.html
* _robots.txt_: file that tells crawlers what files to ignore https://adamj.eu/tech/2020/02/10/robots-tx https://pythonbytes.fm/episodes/show/376/every-dunder-method-in-a-python-lockbox https://x.com/didaoh/status/1814341975195492378 https://news.ycombinator.com/item?id=41960003 you can just ignore it e.g. Perplexity
* don't crawl https://unitedmasters.xyz/robots.txt https://searchfacts.com/robots-txt-allow-disallow-all/
```txt
User-agent: *
Disallow: /
```
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

# ⚔️ STRATEGIES

🔗 https://en.wikipedia.org/wiki/Approximation_algorithm#Algorithm_design_techniques

---

* decision tree 📙 MacCormick chapter 6 https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/ https://victorzhou.com/blog/information-gain/ https://mlu-explain.github.io/
* gini impurity https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/ https://victorzhou.com/blog/gini-impurity/
* _genetic_: select best candidates from random population https://danielmiessler.com/blog/genetic-algorithms-could-be-more-significant-than-machine-learning/  evolutionary https://www.drorpoleg.com/books-to-read-in-2023-part-2/ there's also something called 'genetic programming' whose relationship to genetic algorithms is unclear https://stackoverflow.com/a/3821746 https://aerique.blogspot.com/2011/01/baby-steps-into-genetic-programming.html Bayesian optimization https://news.ycombinator.com/item?id=43605731
* _divide and conquer (D&C)_: winnow to atomic case using recursion
* most (but not all) recursive algos use D&C e.g. quicksort https://stackoverflow.com/a/53796319
* _partition_: split list into two smaller sub-lists 🗄 `linux.md` split
* _pivot_: el used to partition
* _MapReduce_: map (apply func to each item in el) reduce (combine els) [Bhargava 11.209-10] parallel doesn't mean new runtime is old_runtime/cores bc have to load balance btw core and merge results [ibid 11.208] https://en.wikipedia.org/wiki/Parallel_algorithm 🗄 `language.md` concurrency

GOOD ENOUGH
* _hill-climbing_: local maxima https://diff.substack.com/p/big-tech-sees-like-a-state 📙 Christian 195
* _approximation_: aim for good enough when optimal solution too expensive/NP [Bhargava 8.147] take local maximum https://en.wikipedia.org/wiki/Approximation_algorithm

## brute force

* _brute force_: enumerate all possible solutions

## dynamic programming

* _dynamic programming (DP)_: maximize X given constraint on Y or calculate optimum involves large numbers 📙 Bhargava 9.163, 178 https://www.youtube.com/watch?v=gK8KmTDtX8E
* only works for independent problems 📙 Bhargava 9.177
* used for Towers of Hanoi, Dikstra, longest substring/sequence, Fibonacci https://www.youtube.com/playlist?list=PLZHQObOWTQDMRtm8h9bG9P06WINNoBnCR
* must have optimal substructure and overlapping sub-problems https://en.wikipedia.org/wiki/Dynamic_programming#Computer_programming
* clean up https://ngoldbaum.github.io/posts/dynamic-programming/ https://skerritt.blog/dynamic-programming/#why-is-dynamic-programming-called-dynamic-programmin https://trekhleb.dev/blog/2018/dynamic-programming-vs-divide-and-conquer/

## greedy

* _greedy_: recursively choose local optimum e.g. counting change, lightest edge in MST; might not lead to global optimum but that can be ok w/ NP [Bhargava 8.144-5] https://www.interviewcake.com/concept/python3/greedy

## linear programming

https://calmcode.io/course/cvxpy-one/the-stigler-diet
https://en.wikipedia.org/wiki/Linear_programming
* _linear programming_: maximize target given constraints 📙 Bhargava 11.218 https://www.jeremykun.com/2017/09/24/linear-programming-and-healthy-diets-part-2/

# 🦋 TYPES

---

* _anagram_: https://news.ycombinator.com/item?id=35824173
* _collison detection_: https://leanrada.com/notes/sweep-and-prune/
* _codec_: algo for video file compression https://github.com/leandromoreira/digital_video_introduction#how-does-a-video-codec-work https://news.ycombinator.com/item?id=25328622  https://github.com/ablwr/my-recurse-center-syllabus
* _Fibonacci_: 🗄 `classic-compsci.pdf` https://docs.python.org/3/tutorial/modules.html https://www.youtube.com/watch?v=anrOzOapJ2E @ 34:00 https://realpython.com/fibonacci-sequence-python/
* _Fisher-Jenks_: https://pbpython.com/natural-breaks.html
* _hyper log_: count unique items in large set 📙 Bhargava 11.213
* _Morris counter_: https://arpitbhayani.me/blogs/morris-counter
* _Prim's algorithm:_ find MST
* _PubGrub_: for dependency resolution (SAT) https://github.com/sdispater/mixology https://github.com/dart-lang/pub/blob/master/doc/solver.md SAT solver, theorem prover https://news.ycombinator.com/item?id=35626783
* _simulated annealing_: https://matthewstrom.com/writing/how-to-pick-the-least-wrong-colors/
* _Towers of Hanoi_: 🗄 `classic-compsci.pdf` https://en.wikipedia.org/wiki/Dynamic_programming#Tower_of_Hanoi_puzzle

## knapsack problem

https://en.wikipedia.org/wiki/knapsack_problem

* given container w/ weight capacity (knapsack) and items w/ weights and values, calculate most valuable combination of items that could fit into container 📙 Bhargava 8.144, 9.162
* an example of combinatorics (part of stats? calculus? both? https://www.khanacademy.org/math/precalculus)
* ❓ version of set covering or different animal entirely?
* ❓ howto: last column serves as optimal solution until cell at last row and column, at which you compare previous optimal against...power set of all other other items? 📙 Bhargava 9.168  https://www.youtube.com/watch?v=YRBON9sIZ2Y https://aiven.io/blog/solving-the-knapsack-problem-in-postgresql

## PRNG

🗄️ `analytics.md` Polars > IO
🔗 https://en.wikipedia.org/wiki/Linear_congruential_generator

OVERVIEW
> Using the seed, PRNG applies a mathematical function to generate a number. It then uses this number as input for the next step, repeating the process.
> Given the same seed, the PRNG will always produce the same sequence of numbers. This is useful for debugging or testing.
> Eventually, PRNGs repeat their sequences due to finite precision, but a good PRNG has a very long period before repeating.
> Linear Congruential Generators (LCG): Simple algorithms like X_{n+1} = (aX_n + c) mod m.
> Mersenne Twister: A popular PRNG with a long period and high-quality randomness.
> Xoroshiro128+: A newer, fast PRNG with good statistical properties.

```python
class SimplePRNG:
    def __init__(self, seed):
        self.state = seed  # Initialize the generator with a seed

    def next(self):
        # Parameters for the LCG
        a = 1664525  # Multiplier
        c = 1013904223  # Increment
        m = 2**32  # Modulus
        self.state = (a * self.state + c) % m
        return self.state

prng = SimplePRNG(seed=42)
for _ in range(5):
    print(prng.next())
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

---

semantic https://simonwillison.net/2025/Feb/11/llm-sort/

TYPES
* natural: e.g. `2.txt` before `10.txt` https://github.com/triyanox/lla
```python
# lexicographic
sorted(['40', '15', '100'])  # ['100', '15', '40']
# numeric
sorted(['40', '15', '100'], key=int)  # ['15', '40', '100']
# natural
["a1", "a10", "a2"]  # ["a1", "a2", "a10"]
```

QUICKSORT https://en.wikipedia.org/wiki/Quicksort https://github.com/orlp/pdqsort
* strat: D&C via partition 📙 Bhargava 4.65 https://stackoverflow.com/q/164163
* time: O(n log n); iterate input multiple times but smaller input each time; parallel versions can be O(n) 📙 Bhargava 11.208 https://softwareengineering.stackexchange.com/a/297161
* space: O(n)

* https://gwern.net/resorter
* _bubble_: https://realpython.com/sorting-algorithms-python/
* _heap_: https://favtutor.com/blogs/heap-in-python
* _insertion_: https://realpython.com/sorting-algorithms-python/
* _merge_: used for SSTables [Kleppmann 76] https://realpython.com/sorting-algorithms-python/
* _natural_: put like w/ like re: ints, strings https://github.com/SethMMorton/natsort
* _selection_: 🗄 `algos`
* _Timsort_: https://realpython.com/sorting-algorithms-python/
* _topological_: [Bhargava 6.112] https://calmcode.io/shorts/toposort.py

# 🟨 ZA

* _undo/redo_: https://news.ycombinator.com/item?id=43458738
* _y combinator_: https://news.ycombinator.com/item?id=27673177
* cellular automaton, Conway's game of life https://en.wikipedia.org/wiki/Cellular_automaton https://robertheaton.com/2018/07/20/project-2-game-of-life/
* _byte offset_: distance from initial byte to target; used to lookup char in file [Kleppmann 72]
* _intelligent music production_: using algos to mix? https://www.amazon.com/gp/product/B0815BWLXV
* randomness https://classic.qz.com/perfect-company-2/1172282/this-company-built-one-of-the-worlds-most-efficient-warehouses-by-embracing-chaos/

---

* _audio warping_: https://stackoverflow.com/q/9953219/6813490
* geography https://github.com/jftuga/geodist
* shoelace problem 📙 Thomas pragmatic programmer [219]

## recursion

🗄️ `algos.md` recursion
📙 Sweigart https://nostarch.com/recursive-book-recursion

SEMANTICS
* _base case_: function doesn't call itself
* _recursive case_: function calls itself
* _partial execution_: state of function when another function called from within it 📙 Bhargava [44]

```python
def countdown(arg):
    return None if arg == 0 else countdown(arg - 1)
"""
countdown(1) ⬇️:
* first frame goes on stack
* first frame blocks on else, calls countdown(0)
* second frame countdown(0) goes on stack
* second frame comes off stack
* first frame stops blocking on else, comes off stack
"""
```

* for retry 🗄️ `distributed.md` retry
```python
class Foo:
    def _cache():
        """ one-off fetch """
        pass

    def get(retry=True):
        try:
            return read_csv(path/to/cached)
        except FileNotFoundError:
            if retry:
                Foo._cache()
                return Foo.get(retry=False)
            raise
```

---

https://calmcode.io/course/recursion/introduction
* _tail_: can prevent stack overflows but depends on compiler to provide optimization https://stackoverflow.com/a/37010/6813490
* tail call optimization https://blog.jonas.foo/posts/python-tail-call-optimization/

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
