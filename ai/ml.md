# ⛩️

## 参考

🗄️ `modeling.md` vector
🔍
* https://ai.stackexchange.com/
* https://datascience.stackexchange.com/
📚
* Ananthaswamy why machines learn
* Ferguson game of go
* ⭐️ Perrotta programming ML https://www.amazon.com/Little-Learner-Straight-Line-Learning/dp/026254637X
* ⭐️ Raschka build LLM from scratch https://www.manning.com/books/build-a-large-language-model-from-scratch
* Scardapane alices differentiable https://www.amazon.com/dp/B0D9QHS5NG
* Trask deep learning https://github.com/iamtrask/Grokking-Deep-Learning
* Wolfram https://bookoverflow.io/

## 进步

START HERE
* Clinton book + https://www.manning.com/books/llms-in-production
* https://www.youtube.com/@gptLearningHub/videos
* Raschka thirty questions and answers https://www.amazon.com/dp/1718503768
* 🧠 https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a
* https://jalammar.github.io/visual-interactive-guide-basics-neural-networks/
* RLHF https://x.com/liminal_bardo/status/1864063342081691649
* GPT from scratch https://bbycroft.net/llm https://news.ycombinator.com/item?id=38505211
* llama3 from scratch https://github.com/naklecha/llama3-from-scratch

FROM ELIZA TO LLM
* https://zserge.com/posts/ai-eliza/
* https://zserge.com/posts/ai-markov/
* https://zserge.com/posts/ai-nn/
* https://zserge.com/posts/ai-llm/

---

ARE THESE TRAINING? BUILDING FROM SCRATCH?
* https://eli.thegreenplace.net/2024/gomlx-ml-in-go-without-python/
* learn from Simon https://news.ycombinator.com/item?id=41624759 and Ilya https://tensorlabbet.com/
* https://medium.com/@msouza.os/llm-from-scratch-with-pytorch-9f21808c6319
* https://youtu.be/kCc8FmEb1nY
* https://github.com/pingcap/autoflow
* https://news.ycombinator.com/item?id=42256093

* _19_: Deep Learning and the Game of Go (Christmas gift?)

Here's the working taxonomy I have. Can you correct it?

```sh
├── core ideas
│   └── features
│   └── inference
│   └── labels
│   └── vectors
├── classical ML
│   └── KNN
│   └── linear regression
│   └── random forest
│   └── SVM
├── neural networks
│   └── transforms
│   └── tokens
│   └── embeddings
```

# ⭕️ CORE

## embeddings (repr ++)

🗄️ `modeling.md` vector
💡 calc relatedness of strings

* _embedding_: categorized repr of text/image/audio https://simonwillison.net/2023/Oct/23/embeddings

USAGE https://platform.openai.com/docs/guides/embeddings
* search (where results are ranked by relevance to a query string)
* clustering (where text strings are grouped by similarity)
* recommendations (where items with related text strings are recommended)
* anomaly detection (where outliers with little relatedness are identified)
* diversity measurement (where similarity distributions are analyzed)
* classification (where text strings are classified by their most similar label)

---

* https://calmcode.io/course/embeddings/introduction
* try it out https://github.com/taylorai/aiq
* https://www.youtube.com/watch?v=XPA213k8G_U
* https://www.youtube.com/watch?v=pfRA3Scz3Fw
* https://blog.wilsonl.in/hackerverse/
* https://www.youtube.com/watch?v=zzY64Qu8HHc
* https://news.ycombinator.com/item?id=41473518
* https://www.youtube.com/watch?v=hB7sGE0W8CI
* https://news.ycombinator.com/item?id=42013762

## features (input var)

* _feature_: metadata 📙 Bueno [25]

---

* https://www.hopsworks.ai/post/pandas2-and-polars-for-feature-engineering
* _feature extraction_: key attr e.g. semantic meaning, syntax, sentiment analysis https://zackproser.com/blog/introduction-to-embeddings
* _Naive Bayes_: priors + data; naive bc assume every feature has same weight [Bhargava 10.200]
* softmax https://victorzhou.com/blog/softmax/
* visualization in Jupyter https://kylekizirian.github.io/prims-algorithm.html

## inference (prediction)

* https://github.com/samuel-vitorino/lm.rs
* https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a
* https://www.youtube.com/watch?v=J_3jrS3FalY

## labels (output var)

🗄️ scikit

* https://calmcode.io/course/bad-labels/introduction
* https://calmcode.io/course/pigeon/introduction
* https://calmcode.io/datasets/clinc
* https://calmcode.io/labs/doubtlab
* https://labelerrors.com/
* https://www.manning.com/books/data-without-labels

TYPES
* _supervised_: labeled data during training, unlabeled during predication [Trask 2.11]
* _unsupervised_: unlabeled data during training and prediction [Trask 13]
* _reinforcement_: no labels but algo can tell if it's getting hotter or colder http://aiplaybook.a16z.com/docs/guides/dl-learning#user-content-reinforcementlearning
* _parameters_: https://www.youtube.com/watch?v=BbZ2m8mfwYU https://01-ai.github.io/blog.html?post=en/2024-09-05-A-Small-but-Mighty-LLM-for-Code.md
* _parametric_: modeler derives parameters [Trask 2.14, 2.18]
* _nonparametric_: model derives parameters [Trask 2.14, 2.18]

> The fundamental leap of machine learning is to change the problem from a logic problem to a statistics problem. Instead of trying to explain to a computer how you would recognise a picture of a cat, you give it a million pictures of ‘cat’ and let the computer work it out. By extension, the leap in LLMs is to do this with ‘intelligence’ - instead of trying to teach a computer how to think and reason, you give it a billion examples of human reasoning, as captured in text written by people, and let the computer work it out. As we’ve scaled these models we’ve found, so far, that the more examples the better the models work, which means that companies building LLMs want to vacuum up all the text that there is - the one web, yes, but also every patent ever filed, every law, every legal argument in every court case, every book or email or anything else that gives examples of ‘what people tend to say’. - Ben Evans 24.12

## vectors (repr)

---

* word2vec, byte-pair encoding, LSTM https://arpit.substack.com/p/how-zomato-improved-its-search-using https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm * _Word2Vec_: vector db https://www.youtube.com/watch?v=a8Oz6Mz8pk0

SEMANTICS
* _scalar_: single value 📙 Trask [3.45] Bradshaw [62]
* _vector_: list 📙 Trask 3.31
* _matrix_: list of lists 📙 Trask 3.41 e.g. NumPy array, Pandas dataframe
* _elementwise operation_: perform same operation on two vectors of equal length 📙 Trask 3.31 i.e. zip
* _dimensionality_: number of components in a vector https://zackproser.com/blog/introduction-to-dimensionality#what-is-dimensionality-

🧠 https://chatgpt.com/c/6733b490-8d1c-8004-aa20-c1c6722b0247

* _ChromaDB_: https://www.youtube.com/watch?v=QSW2L8dkaZk&list=PL58zEckBH8fA-R1ifTjTIjrdc3QKSk6hI&pp=iAQB
* _Pinecone_: https://zackproser.com/blog/i-am-joining-pinecone-io https://zackproser.com/blog/vector-databases-compared

---

> While embeddings fundamentally changed how we can represent and compare content, they didn't need an entirely new infrastructure category. What we label as "vector databases" are, in reality, search engines with vector capabilities. https://simonwillison.net/2024/Dec/28/jo-kristian-bergum/
* https://www.youtube.com/watch?v=OM1CHD89jqw
* for recommendation systems, NLP
* Milvus, Chroma, Weaviate, FAISS https://zackproser.com/blog/vector-databases-compared
* LanceDB https://www.youtube.com/watch?v=hB7sGE0W8CI
* https://news.ycombinator.com/item?id=41985176
* https://news.ycombinator.com/item?id=35550567 https://garybake.com/vector_databases.html Pinecone https://news.ycombinator.com/item?id=35826929 https://code.dblock.org/2023/06/16/getting-started-with-vector-dbs-in-python.html https://news.ycombinator.com/item?id=37747534 https://realpython.com/chromadb-vector-database/ https://github.com/asg017/sqlite-vec https://github.com/qdrant/qdrant https://www.youtube.com/watch?v=awIm3rQOBxE

# 🏛️ CLASSICAL

## 🛖 KNN

🗄 `math.md` regression

https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a

> It's useful in recommender situations but also with neural embeddings in general. It's an expensive thing to calculate so it is common to calculate approximate distances as a proxy https://calmcode.io/course/altair/introduction
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

## 📈 linear regression

---

* _linear regression_: use set of numerical X values (e.g. study time, price of crude oil) to predict numerical Y values (e.g. test score, price of gasoline)
* BYO https://www.youtube.com/watch?v=VmbA0pi2cRQ https://www.youtube.com/watch?v=KsVBBJRb9TE
* in Pandas, SQL https://hakibenita.com/sql-for-data-analysis#linear-regression
* uses k-NN 📙 Bhargava 10.196 🗄 `algos.md`
* 名 relationship
> the common narrative that it's a fairly simple regression with size, where small startups are fast and large companies are slow, I don't think that's necessarily the case at all, where Facebook is a good example of a company that's remarkable at executing quickly from a technology point of view https://www.stitcher.com/podcast/mathew-passy/invest-like-the-best/e/71161348 25:00
* 动 plot relationship btw
> People have regressed spending by countries, states, and districts on outcome metrics for a long time, and they pretty much universally show that there is no relationship between spending and success as defined in traditional terms. https://freddiedeboer.substack.com/p/is-the-conventional-wisdom-on-educational
* linear regression https://news.ycombinator.com/item?id=41111115
* _logistic regression_: use set of numerical X values (e.g. email attr) to predict categorical Y value (e.g. spam or no?) https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/

## 🌳 random forest

---

* https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/
* https://victorzhou.com/blog/intro-to-random-forests/
* https://mlu-explain.github.io/

## 🦾 SVM

> SVMs sit in the supervised learning family, specifically for classification and regression. They're part of the broader kernel methods taxonomy alongside kernel PCA, kernel ridge regression, etc.

# 🧠 NEURAL NETWORKS

🗄️ `graphs.md` https://www.manning.com/books/graph-neural-networks-in-action https://www.manning.com/books/math-and-architectures-of-deep-learning https://fleetwood.dev/posts/you-could-have-designed-SOTA-positional-encoding https://news.ycombinator.com/item?id=42468214
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

## transformers

---

> GPT stands for Generative Pre-trained Transformer 📙 Clinton obsolete gen AI
📙 Tunstall nlp with transformers https://www.amazon.com/dp/1098136799

* https://www.youtube.com/watch?v=KJtZARuO3JY
* https://www.manning.com/books/transformers-in-action
* https://www.amazon.com/gp/product/1098134184
* https://realpython.com/huggingface-transformers/

## tokens

* _token_: ~4 chars; ~1500 words = 2k tokens 📙 Clinton obsolete gen AI

---

https://llm.datasette.io/en/stable/related-tools.html

## CNNs

## RNNs

# 🛠️ STDLIB

* _Tensorflow_: tensor (array) flow (operations) https://github.com/Hvass-Labs/TensorFlow-Tutorials https://news.ycombinator.com/item?id=42133844
* _Keras_: less verbose Tensorflow (will eventually be packaged w/) https://victorzhou.com/blog/keras-neural-network-tutorial/ https://news.ycombinator.com/item?id=42133844
* _PyTorch_: superceded Tensorflow https://thegradient.pub/state-of-ml-frameworks-2019-pytorch-dominates-research-tensorflow-dominates-industry/ NumPy that can run in parallel on GPUs; tensor (array 类似 NumPy array) scalar (single value) vector (array) matrix (2d array) tensor (multi-dimensional array) https://aiweirdness.com/post/189170306297/how-to-begin-a-novel alternative https://github.com/geohot/tinygrad https://github.com/Lightning-AI/lightning
* _sci-kit learn_: https://jakevdp.github.io/PythonDataScienceHandbook/
* _Matplotlib_: eaten by Python https://realpython.com/podcasts/rpp/197/
* Matlab for Python https://jakevdp.github.io/PythonDataScienceHandbook/
* _MLX_: numpy for Apple silicon https://github.com/ml-explore/mlx

## jax

https://github.com/jax-ml/jax https://jax.readthedocs.io/en/latest/

https://calmcode.io/course/jax/introduction

```txt
Great question! JAX is indeed somewhat like NumPy, but it has some distinct and powerful features that make it a key tool in the modern machine learning (ML) and scientific computing ecosystem.

What is JAX?
JAX is a high-performance numerical computing library that combines:

NumPy-like API: It provides functions and data structures that mirror those in NumPy, so you can use it in a similar way for array computations.
Automatic Differentiation (Autograd): JAX can compute gradients of functions, which is essential for optimization tasks in ML.
Just-in-Time Compilation (JIT): JAX can compile your Python code to machine-specific optimized code using XLA (Accelerated Linear Algebra), significantly speeding up computations.
GPU/TPU Support: JAX seamlessly runs on CPUs, GPUs, and TPUs, making it ideal for high-performance applications.
How is it similar to NumPy?
JAX's jax.numpy module offers a NumPy-compatible API, so you can write code that feels familiar if you're used to NumPy.
You can perform element-wise operations, linear algebra, and other array manipulations just like you would in NumPy.
How does it differ from NumPy?
Accelerated Computing: JAX can leverage GPUs and TPUs, whereas NumPy is CPU-only.
Gradients: JAX has built-in support for automatic differentiation, enabling you to compute derivatives with ease (e.g., for ML or optimization).
JIT Compilation: Unlike NumPy, JAX can compile functions for significant speedups.
Pure Functional Programming Paradigm: JAX promotes immutability and pure functions, which differs from NumPy's in-place operations.
Where does JAX fit in the larger ecosystem?
ML and Deep Learning: JAX is widely used in cutting-edge ML research because it supports fast prototyping and efficient gradient-based optimization.
Scientific Computing: Researchers in physics, biology, and other domains use JAX for its combination of high performance and ease of use.
Frameworks Built on JAX:
Flax and Haiku: ML libraries that provide high-level abstractions for building neural networks.
Optax: For optimization algorithms.
Equinox: A lightweight framework for building neural networks in a PyTorch-like style.
Competitor to TensorFlow and PyTorch: While not a direct competitor in terms of ease of deployment for production, JAX is preferred for research due to its flexibility and simplicity.
In summary
JAX can be thought of as "NumPy on steroids" with GPU/TPU acceleration, automatic differentiation, and JIT compilation. It's an excellent tool for both high-performance scientific computing and machine learning research. If you're familiar with NumPy and looking to explore ML or computationally intensive tasks, JAX is a fantastic library to dive into.
```

## numpy

https://realpython.com/numpy-example/

* _Numpy_: subset of scipy https://jakevdp.github.io/PythonDataScienceHandbook/ 📙 Trask 44
```python
# numpy.array.dot https://stackoverflow.com/a/35208273 📙 Trask 3.35
def dot(v1, v2):  # vectors
    return sum(x*y for x,y in zip(v1,v2))

dot([1,2,3], [4,5,6])
```

## scikit

💡 good at classical

* _dummy_: https://calmcode.io/course/scikit-dummy/intro
* _learn_: https://calmcode.io/course/scikit-learn/introduction https://calmcode.io/course/human-learn/introduction https://github.com/koaning/human-learn/ https://calmcode.io/course/model-mining/introduction https://calmcode.io/course/partial_fit/introduction
* _lego_: https://github.com/koaning/scikit-lego https://calmcode.io/course/hiplot/introduction
* _save_: https://calmcode.io/course/scikit-save/introduction
* _prep_: https://calmcode.io/course/scikit-prep/introduction
* _metrics_: https://calmcode.io/course/scikit-metrics/introduction
* _meta_: https://calmcode.io/course/scikit-meta/introduction

## scipy

https://github.com/statsmodels/statsmodels

# 🟨️ ZA

## cleanup

---

> It’s worth noting that AI tools are intimately familiar with Next.js and not so much with htmx, due to the lack of open-source training data. This is similar to the issue Rails faces. While not a dealbreaker, it did impact our development speed and the ease of finding solutions to problems. When we encountered issues, the wealth of resources available for React/Next.js made troubleshooting much faster. https://htmx.org/essays/why-gumroad-didnt-choose-htmx/
* trained on hacked data, really good for coding https://simonwillison.net/2023/Dec/31/ai-in-2023/ https://til.simonwillison.net/clickhouse/github-public-history
https://en.wikipedia.org/wiki/Generative_artificial_intelligence
https://www.apricitas.io/archive https://github.com/zillow/luminaire https://github.com/zillow/fair-housing-guardrail
https://forklightning.substack.com/
https://treyhunner.com/2024/07/chatgpt-and-claude-from-your-browser-url-bar/
building into projects https://news.ycombinator.com/item?id=40857589

ZA
* scraping https://chatgpt.com/c/6723e31b-bf8c-8004-a801-41b1b4e52419
* structured output https://news.ycombinator.com/item?id=40713952
* https://news.ycombinator.com/item?id=40441945
* custom GPT https://talkpython.fm/episodes/show/456/building-gpt-actions-with-fastapi-and-pydantic
* customization prompt https://news.ycombinator.com/item?id=40474716
* telemetry https://github.com/dagworks-inc/burr

* AI friend https://x.com/deedydas/status/1804550284552949771
* Devin https://news.ycombinator.com/item?id=40008109
* https://github.com/minimaxir/simpleaichat/blob/main/examples/notebooks/schema_ttrpg.ipynb
* hacks: offer to tip https://twitter.com/emollick/status/1730742277792813517 change date https://twitter.com/venturetwins/status/1710321733184667985 get instructions https://twitter.com/fabianstelzer/status/1709562237310878122
* use when coding https://realpython.com/chatgpt-coding-mentor-python/
* use when reading https://www.reddit.com/r/ChatGPT/comments/17p968u/leaving_chatgpt_voice_on_while_reading_a_book_is/?rdt=52836 https://marginalrevolution.com/marginalrevolution/2023/11/the-early-days.html
* https://twitter.com/patio11/status/1728018125398978659/photo/1
* training on literature https://news.ycombinator.com/item?id=25607809 https://news.ycombinator.com/item?id=24884789 
* respond to social pressure https://twitter.com/AndrewCurran_/status/1720177766283505724
* use to study math https://news.ycombinator.com/item?id=37963453
* pretty transparent https://twitter.com/zoink/status/1599281052115034113
* tooling https://github.com/eth-sri/lmql
* impact on software dev https://about.sourcegraph.com/blog/cheating-is-all-you-need https://github.com/jiggy-ai/pair https://news.ycombinator.com/item?id=35470915&utm_term=comment ChatGPT https://kadekillary.work/posts/1000x-eng/ https://news.ycombinator.com/item?id=35385019 https://news.ycombinator.com/item?id=35493631 https://news.ycombinator.com/item?id=35612494 https://news.ycombinator.com/item?id=35638552  https://www.phind.com/
* how it works https://www.jonstokes.com/p/chatgpt-explained-a-guide-for-normies
* LLM https://news.ycombinator.com/item?id=34726115 https://marginalrevolution.com/marginalrevolution/2023/11/the-single-best-introduction-to-llms.html
> Using AI-assisted code changes our work from writing code to proofreading code. https://buttondown.email/hillelwayne/archive/programming-ais-worry-me/
* howto use https://marginalrevolution.com/marginalrevolution/2023/02/how-should-you-talk-to-chatgpt-a-users-guide.html https://marginalrevolution.com/marginalrevolution/2023/03/what-is-the-single-best-way-of-improving-your-gpt-prompts.html https://simonwillison.net/2023/Aug/6/annotated-presentations/ https://realpython.com/practical-prompt-engineering/ https://news.ycombinator.com/item?id=41395921 https://roadmap.sh/prompt-engineering
> Ask ChatGPT "What is Marxism?" for example, and you will get a passable answer, probably no better than what you would get by using Wikipedia or Google. Instead, make the question more specific: "Which were the important developments in French Marxism in the second half of the 19th century?" ChatGPT will do much better - and it's also the kind of question it's hard to use Google and Wikipedia to answer.
> ChatGPT will do better yet if you ask it sequential questions along an evolving line of inquiry. Ask it about the specific French Marxists it cites, what they did, and how they differed from their German counterparts.
> Another way to hone ChatGPT's capabilities is to ask it for responses in the voice of a third person. Ask, "What are the costs of inflation?" and you might get answers that aren't wrong exactly, but neither are they impressive. Instead, try this: "What are the costs of inflation? Please answer using the ideas of Milton Friedman." By mentioning Friedman, you have pointed it to a more intelligent corner of the ideas universe.
* hallucination https://twitter.com/dsmerdon/status/1618816703923912704
* Pynchon https://marginalrevolution.com/marginalrevolution/2023/01/signs-of-encroaching-gpt-dom.html
* music https://google-research.github.io/seanet/musiclm/examples/ https://twitter.com/bleedingedgeai/status/1619081383477137408
* impact on art https://www.drorpoleg.com/ai-and-the-long-tail/
* https://en.wikipedia.org/wiki/ChatGPT
* prompts https://writings.stephenwolfram.com/2023/01/wolframalpha-as-the-way-to-bring-computational-knowledge-superpowers-to-chatgpt/
* impl https://github.com/karpathy/nanoGPT https://hut.pm/nanogpt.html
* good at application vs. theory https://marginalrevolution.com/marginalrevolution/2023/01/the-differential-impact-of-gpt.html
* 2022 was crazy https://twitter.com/DrJimFan/status/1607746957753057280
https://stratechery.com/2023/ai-and-the-big-five/
> The story of 2022 was the emergence of AI, first with image generation models, including DALL-E, MidJourney, and the open source Stable Diffusion, and then ChatGPT, the first text-generation model to break through in a major way. It seems clear to me that this is a new epoch in technology.
> Stable Diffusion is remarkable not simply because it is open source, but also because the model is surprisingly small: when it was released it could already run on some consumer graphics cards; within a matter of weeks it had been optimized to the point where it could run on an iPhone.
> Google invented the transformer, the key technology undergirding the latest AI models. Google is rumored to have a conversation chat product that is far superior to ChatGPT. Google claims that its image generation capabilities are better than Dall-E or anyone else on the market. And yet, these claims are just that: claims, because there aren’t any actual products on the market.
* https://marginalrevolution.com/marginalrevolution/2022/12/one-look-at-our-future.html
* more ChatGPT https://marginalrevolution.com/marginalrevolution/2022/12/chatgpt-does-a-thomas-schelling-poem.html https://davidrozado.substack.com/p/the-political-orientation-of-the how to use https://twitter.com/omarsar0/status/1600149116369051649 https://substack.com/inbox/post/88017506 https://astralcodexten.substack.com/p/perhaps-it-is-a-bad-thing-that-the AI will corrupt the corpus of the internet https://news.ycombinator.com/item?id=33864276
* journaling to ChatGPT https://marginalrevolution.com/marginalrevolution/2022/12/chatting-with-yourself.html
* politics of LLMs https://twitter.com/DavidRozado/status/1606249231185981440 https://cactus.substack.com/p/openais-woke-catechism-part-1 https://x.com/DavidRozado/status/1850715219850678736 https://davidrozado.substack.com/p/an-analysis-of-ai-political-preferences
* politics of LLM research https://twitter.com/RamaswmySridhar/status/1606031588789088256 https://twitter.com/pmarca/status/1611229226765783041 https://twitter.com/pmarca/status/1611237679496331265
* effect on trust https://marginalrevolution.com/marginalrevolution/2022/12/ben-thompson-interview-with-daniel-gross-and-nat-friedman.html
* Spielberg https://marginalrevolution.com/marginalrevolution/2022/12/rewatching-a-i-minor-spoilers.html
* alternatives https://twitter.com/goodside/status/1606611869661384706
* https://twitter.com/peterwildeford/status/1602521505279184897
* Christian alignment problem https://news.ycombinator.com/item?id=34185488 https://richardhanania.substack.com/p/can-a-paperclip-maximizer-overthrow
* ethics vs. alignment https://scottaaronson.blog/?p=7042 ethics as red herring https://blog.cerebralab.com/AI_alarmism_and_the_misinformed_position https://news.ycombinator.com/item?id=35146676
* success and failures https://marginalrevolution.com/marginalrevolution/2023/01/chatgpt-and-the-revenge-of-history.html

> He does not think of them as Artificial Intelligence. He thinks of them as Imitation Intelligence. They predict the next word in a sentence. When they get good at that, it's spooky what they can do. https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

> The marginal product of LLMs is when they are interacting with well-prepared, intricately cooperating humans at their peak, not when you pose them random queries for fun. https://marginalrevolution.com/marginalrevolution/2024/08/okie-dokie-solve-for-the-equilibrium.html https://x.com/hud_zah/status/1827057785995141558

* chess https://arxiv.org/pdf/2402.04494 https://x.com/sytelus/status/1848160140278555049
* https://news.ycombinator.com/item?id=40416362
* https://explainextended.com/2023/12/31/happy-new-year-15/ https://news.ycombinator.com/item?id=40378499
* https://blog.miguelgrinberg.com/post/how-llms-work-explained-without-math

* legal https://pycon-archive.python.org/2024/schedule/presentation/7/index.html https://simonwillison.net/2024/Dec/5/amazon-bedrock-data-protection/ https://simonwillison.net/2024/Dec/5/pleias-llms/ https://marginalrevolution.com/marginalrevolution/2024/12/thomas-storrs-on-elastic-data-supply-from-my-email.html https://www.tosabout.com/
* contextual search 🗄️ `info.md` search https://jnnnthnn.com/how-to-build-your-own-perplexity-for-any-dataset https://www.perplexity.ai/
* price per token https://x.com/drorpoleg/status/1847686346078368006
* tokens, read whole thing
> The big challenge for traditional LLMs is that they are path-dependent; while they can consider the puzzle as a whole, as soon as they commit to a particular guess they are locked in, and doomed to failure. This is a fundamental weakness of what are known as “auto-regressive large language models”, which to date, is all of them. To grossly simplify, a large language model generates a token (usually a word, or part of a word) based on all of the tokens that preceded the token being generated; the specific token is the most statistically likely next possible token derived from the model’s training (this also gets complicated, as the “temperature” of the output determines what level of randomness goes into choosing from the best possible options; a low temperature chooses the most likely next token, while a higher temperature is more “creative”). The key thing to understand, though, is that this is a serial process: once a token is generated it influences what token is generated next. https://stratechery.com/2024/enterprise-philosophy-and-the-first-wave-of-ai/
> These new models are also available through Mistral's la Plateforme API, priced at $0.1/million tokens (input and output) for the 8B and $0.04/million tokens for the 3B. https://simonw.substack.com/p/video-scraping-using-google-gemini
* rule-based https://www.youtube.com/watch?v=CeukwyUdaz8
* supervised https://www.youtube.com/watch?v=j9kcEuGcC2Y
* CRISP-DM https://www.youtube.com/watch?v=dCa3JvmJbr0
* model selection https://www.youtube.com/watch?v=OH_R0Sl9neM

https://karpathy.ai/zero-to-hero.html
https://www.youtube.com/watch?v=fuMKrKlaku4
https://writings.stephenwolfram.com/2024/08/whats-really-going-on-in-machine-learning-some-minimal-models/

REPOS
https://www.freecodecamp.org/news/get-started-with-hugging-face/ https://pola.rs/posts/polars-hugging-face/ https://github.com/huggingface/transformers https://astral.sh/blog/uv-unified-python-packaging
https://huggingface.co/stabilityai/stable-diffusion-3-medium

https://www.nbcnews.com/tech/internet/hunting-ai-bots-four-words-trick-rcna161318

https://softwareengineeringdaily.com/2024/05/14/llms-for-data-queries-with-sarah-nagy/

https://news.ycombinator.com/item?id=40271457

https://news.ycombinator.com/item?id=40184372&utm_term=comment
https://news.ycombinator.com/item?id=40224459
https://twitter.com/skirano/status/1785469853689639379

https://www.freecodecamp.org/learn/machine-learning-with-python/#tensorflow

* context window https://twitter.com/deedydas/status/1778621375592485076
> the idea that a bigger context window might be more than, well, just more of the same, but instead a game changer for LLMs is very interesting https://registerspill.thorstenball.com/p/joy-and-curiosity-19 https://thelongcontext.com/
> Google hasn’t said how Gemini 1.5 was made, but clearly the company has overcome the key limitation of traditional transformers: memory requirements increase quadratically with context length. One promising approach is Ring Attention with Blockwise Transformers, which breaks long contexts into pieces to be computed individually even as the various devices computing those pieces simultaneously communicate to make sense of the context as a whole; in this case memory requirements scale linearly with context length, and can be extended by simply adding more devices to the ring topology. https://stratechery.com/2024/gemini-1-5-and-googles-nature/
* https://news.ycombinator.com/item?id=39849393

https://zed.dev/blog/between-editors-and-ides

WAYS OF LEARNING https://danielmiessler.com/blog/machine-learning-new-statistics/
* event-based: no model + datum
* stat: fixed model + data
* transformers https://e2eml.school/transformers.html https://jalammar.github.io/illustrated-transformer/ https://news.ycombinator.com/item?id=37774676 https://news.ycombinator.com/item?id=39898221 https://news.ycombinator.com/item?id=41378806 https://x.com/fchollet/status/1846263128801378616
* AI: fluid model + data [Ferguson 7] https://blog.cerebralab.com/Replacing_statistics_with_modern_predictive_models

rf
* https://tigyog.app/d/C-I1weB9CpTH/r/everyday-data-science
* Ferguson section 1
* https://sirupsen.com/napkin/neural-net
* https://news.ycombinator.com/item?id=39894302

za
* object detection: https://github.com/tryolabs/norfair
* TigerGraph https://github.com/benedekrozemberczki/tigerlily
* _TinyML_: ML on devices e.g. phones, IoT https://www.thoughtworks.com/radar/techniques?blipid=202203070
* _computer vision_: ability of computer to process visual input; aka image recognition http://aiplaybook.a16z.com/docs/guides/vision
* _OCR_: map picture to text [Bhargava 10.199] aka image recognition https://news.ycombinator.com/item?id=26207049
* _VQA (visual question answering)_: answer open-ended question about image https://victorzhou.com/blog/easy-vqa/
* overlap btw stat and ML https://news.columbia.edu/news/top-10-ideas-statistics-ai
* multi-armed bandit, Gittins Index, upper confidence bound 📙 Christian chapter 2
* math: stat/probability, linear algebra https://nostarch.com/math-deep-learning

models
* _model_: machine impl algo (vs. human impl) https://github.com/minimaxir/automl-gs
* serialize https://onnx.ai/
* _gradient descent_: https://www.youtube.com/watch?v=IHZwWFHWa-w

TYPES
* _AGI_: Hal9000
* aka strong 📙 Thiel 150
* https://www.richardhanania.com/p/ai-doomerism-as-science-fiction
* Bostrom https://www.cspicenter.com/p/why-the-singularity-might-never-come https://www.youtube.com/watch?v=fQ4rc7npiXQ
how to use https://realpython.com/generate-images-with-dalle-openai-api/
* PALM https://ai.googleblog.com/2022/04/pathways-language-model-palm-scaling-to.html https://news.ycombinator.com/item?id=30908941 https://blog.samaltman.com/dall-star-e-2 aka language models https://marginalrevolution.com/marginalrevolution/2022/04/monday-assorted-links-351.html https://stratechery.com/2022/dall-e-the-metaverse-and-zero-marginal-content https://twitter.com/nickcammarata/status/1511861061988892675 large language models https://www.nytimes.com/2022/04/15/magazine/ai-language.html https://astralcodexten.substack.com/p/mantic-monday-41822 https://www.assemblyai.com/blog/how-dall-e-2-actually-works/ https://github.com/lucidrains/DALLE2-pytorch pictures https://news.ycombinator.com/item?id=31967141 GPT-3 for code docs https://news.ycombinator.com/item?id=32036224 prompts https://deephaven.io/blog/2022/08/08/AI-generated-blog-thumbnails/ Midjourney https://alexanderwales.com/the-ai-art-apocalypse/ https://midjourney.gitbook.io/docs/ https://discord.com/channels/662267976984297473 https://news.ycombinator.com/item?id=41312225 Stable Diffusion https://news.ycombinator.com/item?id=32644176 https://diffusionbee.com/ Disco Diffusion https://github.com/jina-ai/discoart
* _AI_: superset of machine learning
* other subsets [Ferguson 6]
* used interchangely w/ deep learning [Ferguson 7]
* 1956: Dartmouth Summer Research Project, Geoffrey Hinton https://www.technologyreview.com/s/608911/is-ai-riding-a-one-trick-pony/ https://fermatslibrary.com/s/a-proposal-for-the-dartmouth-summer-research-project-on-artificial-intelligence
* 1960s: classical AI i.e. use normal coding techniques (control flow, data structure) http://aiplaybook.a16z.com/docs/guides/ai Eliza chatbot (me: "I like to code" Elize: "how do you feel about that?")
* 2010s: Google DeepMind, OpenAI, Future of Humanity Institute
* _ML_: superset of deep learning [Trask 2.10] https://pragprog.com/titles/pplearn/programming-machine-learning/ https://dafriedman97.github.io/mlbook/content/introduction.html https://course18.fast.ai/ml 🗄 techniques
* _deep learning_: subset of ML using neural networks [Trask 2.10] just stats and calculus https://news.ycombinator.com/item?id=24593529
* _cybernetic_: https://en.wikipedia.org/wiki/Johns_Hopkins_Beast

## meta

* output first, gimme impl https://austinhenley.com/blog/mirrorlang.html

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
```python
# https://realpython.com/podcasts/rpp/232/ https://blog.jetbrains.com/pycharm/2024/12/introduction-to-sentiment-analysis-in-python/
import nltk
from nltk.sentiment.vader import SentimentIntensityAnalyzer
nltk.download('vader_lexicon')
analyzer = SentimentIntensityAnalyzer()
sentence = "I love PyCharm! It's my favorite Python IDE."
sentiment_scores = analyzer.polarity_scores(sentence)
print(sentiment_scores)  # {'neg': 0.0, 'neu': 0.572, 'pos': 0.428, 'compound': 0.6696}

import spacy
import spacy.cli
from spacytextblob.spacytextblob import SpacyTextBlob
spacy.cli.download("en_core_web_sm")
nlp = spacy.load('en_core_web_sm')
nlp.add_pipe('spacytextblob')
doc = nlp("I love PyCharm! It's my favorite Python IDE.")
print('Polarity: ', doc._.polarity) # Polarity:  0.625
print('Subjectivity: ', doc._.subjectivity) # Subjectivity:  0.6
```
* _word cloud_: https://dataanalysis.substack.com/p/generating-a-word-cloud-in-python?s=r
* clean up https://nostarch.com/NLPPython https://codewords.recurse.com/issues/seven/data-driven-literary-analysis https://www.fast.ai/2019/07/08/fastai-nlp/ https://speakerdeck.com/pycon2015/adam-palay-words-words-words-reading-shakespeare-with-python https://victorzhou.com/blog/better-profanity-detection-with-scikit-learn/ https://calmcode.io/labs/scikit-partial
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
