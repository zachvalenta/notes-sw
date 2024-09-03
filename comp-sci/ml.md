# ⛩️

## 参考

🔍
* https://ai.stackexchange.com/
* https://datascience.stackexchange.com/
📚
* Anathaswamy https://www.amazon.com/gp/product/0593185749 https://www.thediff.co/archive/longreads-open-thread-90/
* Ferguson game of go
* Perrota programming ML https://www.amazon.com/Programming-Machine-Learning-Zero-Deep/dp/1680506609/ref=sr_1_1
* Trask grok deep learning https://github.com/iamtrask/Grokking-Deep-Learning

## 进步

* rule-based https://www.youtube.com/watch?v=CeukwyUdaz8
* supervised https://www.youtube.com/watch?v=j9kcEuGcC2Y
* CRISP-DM https://www.youtube.com/watch?v=dCa3JvmJbr0
* model selection https://www.youtube.com/watch?v=OH_R0Sl9neM

BYO
* https://www.youtube.com/watch?v=kCc8FmEb1nY
* https://news.ycombinator.com/item?id=41412256&utm_term=comment
* https://spreadsheets-are-all-you-need.ai/index.html
* https://iamjoshknox.com/2023/12/06/econeats-an-ai-dining-guide/
* https://www.saaspegasus.com/guides/django-websockets-chatgpt-channels-htmx
* https://github.com/langgenius/dify
* https://github.com/BerriAI/litellm

> https://langfuse.com/ https://www.thoughtworks.com/radar/platforms/langfuse
https://www.thoughtworks.com/radar/languages-and-frameworks/langchain

https://karpathy.ai/zero-to-hero.html
https://www.youtube.com/watch?v=fuMKrKlaku4
https://writings.stephenwolfram.com/2024/08/whats-really-going-on-in-machine-learning-some-minimal-models/

REPOS
https://www.freecodecamp.org/news/get-started-with-hugging-face/ https://pola.rs/posts/polars-hugging-face/ https://github.com/huggingface/transformers https://astral.sh/blog/uv-unified-python-packaging
https://huggingface.co/stabilityai/stable-diffusion-3-medium
https://realpython.com/huggingface-transformers/

RAG, vector https://news.ycombinator.com/item?id=41105130 https://en.wikipedia.org/wiki/Retrieval-augmented_generation https://retool.com/blog/retrieval-augmented-generation https://www.youtube.com/watch?v=Q75JgLEXMsM

https://www.amazon.com/gp/product/1098107969

* _24_: start using for dev (regex, stdlib)

# 🧪 TECHNIQUES

🔗 https://github.com/ritchie46/vanilla-machine-learning

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

## LLM

> He does not think of them as Artificial Intelligence. He thinks of them as Imitation Intelligence. They predict the next word in a sentence. When they get good at that, it's spooky what they can do. https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

> The marginal product of LLMs is when they are interacting with well-prepared, intricately cooperating humans at their peak, not when you pose them random queries for fun. https://marginalrevolution.com/marginalrevolution/2024/08/okie-dokie-solve-for-the-equilibrium.html https://x.com/hud_zah/status/1827057785995141558

---

* https://news.ycombinator.com/item?id=40416362
* https://explainextended.com/2023/12/31/happy-new-year-15/ https://news.ycombinator.com/item?id=40378499
* https://blog.miguelgrinberg.com/post/how-llms-work-explained-without-math
* how to teach https://news.ycombinator.com/item?id=38759877
* embeddings https://simonwillison.net/2023/Oct/23/embeddings/ https://blog.wilsonl.in/hackerverse/
* with notes https://github.com/reorproject/reor

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

## neural networks

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

VECTORS
* _scalar_: single value 📙 Trask [3.45] Bradshaw [62]
* _vector_: list 📙 Trask 3.31
* _matrix_: list of lists 📙 Trask 3.41 e.g. NumPy array, Pandas dataframe
* _elementwise operation_: perform same operation on two vectors of equal length 📙 Trask 3.31 i.e. zip

BASICS https://www.youtube.com/watch?v=aircAruvnKk https://karpathy.ai/zero-to-hero.html
* _neural network_: graph (network) that mimics the brain (neural) https://victorzhou.com/blog/intro-to-neural-networks/
* in NN, just a var holding boolean value https://www.youtube.com/watch?v=aircAruvnKk 2:55
* akin to logic gate https://victorzhou.com/blog/intro-to-neural-networks/
* as non-leaky abstraction https://blog.cerebralab.com/Neural_networks_as_non-leaky_mathematical_abstraction

TYPES
* _deep_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/how-deep-neural-networks-work
* _recurrent_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm https://victorzhou.com/blog/intro-to-rnns/
* _convolutional_: https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/how-convolutional-neural-networks-work https://victorzhou.com/blog/intro-to-cnns-part-1/ good for computer vision https://www.youtube.com/watch?v=aircAruvnKk 2:10

## regression

* _linear regression_: use set of numerical X values (e.g. study time, price of crude oil) to predict numerical Y values (e.g. test score, price of gasoline)
* BYO https://www.youtube.com/watch?v=VmbA0pi2cRQ https://www.youtube.com/watch?v=KsVBBJRb9TE
* in Pandas, SQL https://hakibenita.com/sql-for-data-analysis#linear-regression
* uses k-NN 📙 Bhargava 10.196 🗄 `algos.md`
* 名 relationship
> the common narrative that it's a fairly simple regression with size, where small startups are fast and large companies are slow, I don't think that's necessarily the case at all, where Facebook is a good example of a company that's remarkable at executing quickly from a technology point of view https://www.stitcher.com/podcast/mathew-passy/invest-like-the-best/e/71161348 25:00
* 动 plot relationship btw
> People have regressed spending by countries, states, and districts on outcome metrics for a long time, and they pretty much universally show that there is no relationship between spending and success as defined in traditional terms. https://freddiedeboer.substack.com/p/is-the-conventional-wisdom-on-educational
* _logistic regression_: use set of numerical X values (e.g. email attr) to predict categorical Y value (e.g. spam or no?) https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/

## stdlib

* _Tensorflow_: tensor (array) flow (operations) https://github.com/Hvass-Labs/TensorFlow-Tutorials
* _Keras_: less verbose Tensorflow (will eventually be packaged w/) https://victorzhou.com/blog/keras-neural-network-tutorial/
* _PyTorch_: superceded Tensorflow https://thegradient.pub/state-of-ml-frameworks-2019-pytorch-dominates-research-tensorflow-dominates-industry/ NumPy that can run in parallel on GPUs; tensor (array 类似 NumPy array) scalar (single value) vector (array) matrix (2d array) tensor (multi-dimensional array) https://aiweirdness.com/post/189170306297/how-to-begin-a-novel alternative https://github.com/geohot/tinygrad https://github.com/Lightning-AI/lightning
* _CUDA_: GPUs aaS
* _sci-kit learn_: https://jakevdp.github.io/PythonDataScienceHandbook/
* _Matplotlib_: Matlab for Python https://jakevdp.github.io/PythonDataScienceHandbook/
* _Numpy_: subset of scipy https://jakevdp.github.io/PythonDataScienceHandbook/ 📙 Trask 44
```python
# numpy.array.dot https://stackoverflow.com/a/35208273 📙 Trask 3.35
def dot(v1, v2):  # vectors
    return sum(x*y for x,y in zip(v1,v2))

dot([1,2,3], [4,5,6])
```

# 🛠️ TOOLING

🔗 https://a16z.com/100-gen-ai-apps-3/

* AI friend https://x.com/deedydas/status/1804550284552949771
* Devin https://news.ycombinator.com/item?id=40008109
* https://github.com/minimaxir/simpleaichat/blob/main/examples/notebooks/schema_ttrpg.ipynb
* hacks: offer to tip https://twitter.com/emollick/status/1730742277792813517 change date https://twitter.com/venturetwins/status/1710321733184667985 get instructions https://twitter.com/fabianstelzer/status/1709562237310878122
* use when coding https://realpython.com/chatgpt-coding-mentor-python/
* use when reading https://www.reddit.com/r/ChatGPT/comments/17p968u/leaving_chatgpt_voice_on_while_reading_a_book_is/?rdt=52836 https://marginalrevolution.com/marginalrevolution/2023/11/the-early-days.html
* https://twitter.com/patio11/status/1728018125398978659/photo/1
* run locally https://github.com/Mozilla-Ocho/llamafile
* training on literature https://news.ycombinator.com/item?id=25607809 https://news.ycombinator.com/item?id=24884789 
* _agent_: give it a dataset, it writes the paper https://www.oneusefulthing.org/p/almost-an-agent-what-gpts-can-do
* respond to social pressure https://twitter.com/AndrewCurran_/status/1720177766283505724
* run locally https://github.com/getumbrel/llama-gpt
* use to study math https://news.ycombinator.com/item?id=37963453
* pretty transparent https://twitter.com/zoink/status/1599281052115034113
* tooling https://github.com/eth-sri/lmql
* _constitution_: heuristic for LLM https://www.anthropic.com/index/claudes-constitution
* impact on software dev https://about.sourcegraph.com/blog/cheating-is-all-you-need https://github.com/jiggy-ai/pair https://news.ycombinator.com/item?id=35470915&utm_term=comment ChatGPT https://kadekillary.work/posts/1000x-eng/ https://news.ycombinator.com/item?id=35385019 https://news.ycombinator.com/item?id=35493631 https://news.ycombinator.com/item?id=35612494 https://news.ycombinator.com/item?id=35638552  https://www.phind.com/
* how it works https://www.jonstokes.com/p/chatgpt-explained-a-guide-for-normies
* LLM https://news.ycombinator.com/item?id=34726115 https://marginalrevolution.com/marginalrevolution/2023/11/the-single-best-introduction-to-llms.html
> Using AI-assisted code changes our work from writing code to proofreading code. https://buttondown.email/hillelwayne/archive/programming-ais-worry-me/
* howto use https://marginalrevolution.com/marginalrevolution/2023/02/how-should-you-talk-to-chatgpt-a-users-guide.html https://marginalrevolution.com/marginalrevolution/2023/03/what-is-the-single-best-way-of-improving-your-gpt-prompts.html https://simonwillison.net/2023/Aug/6/annotated-presentations/ https://realpython.com/practical-prompt-engineering/ https://news.ycombinator.com/item?id=41395921
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
* politics of LLMs https://twitter.com/DavidRozado/status/1606249231185981440 https://cactus.substack.com/p/openais-woke-catechism-part-1
* politics of LLM research https://twitter.com/RamaswmySridhar/status/1606031588789088256 https://twitter.com/pmarca/status/1611229226765783041 https://twitter.com/pmarca/status/1611237679496331265
* effect on trust https://marginalrevolution.com/marginalrevolution/2022/12/ben-thompson-interview-with-daniel-gross-and-nat-friedman.html
* Spielberg https://marginalrevolution.com/marginalrevolution/2022/12/rewatching-a-i-minor-spoilers.html
* alternatives https://twitter.com/goodside/status/1606611869661384706
* https://twitter.com/peterwildeford/status/1602521505279184897
* Christian alignment problem https://news.ycombinator.com/item?id=34185488 https://richardhanania.substack.com/p/can-a-paperclip-maximizer-overthrow
* ethics vs. alignment https://scottaaronson.blog/?p=7042 ethics as red herring https://blog.cerebralab.com/AI_alarmism_and_the_misinformed_position https://news.ycombinator.com/item?id=35146676
* success and failures https://marginalrevolution.com/marginalrevolution/2023/01/chatgpt-and-the-revenge-of-history.html

## chat

OPTIONS
* benchmark https://arena.lmsys.org/
* _ChatGPT_: need to ugrade macOS to get access to desktop app
* code: https://ollama.com/blog/python-javascript-libraries
* _Gemma_: https://ai.google.dev/gemma
* _Llama_: Meta https://en.wikipedia.org/wiki/Llama_(language_model)
* uncensored https://ollama.com/blog/llama-3-is-not-very-censored https://ollama.com/blog/run-llama2-uncensored-locally https://joshuacook.netlify.app/posts/2024-01-31_ollama-quickstart/
* _Mistral_: https://en.wikipedia.org/wiki/Mistral_AI

PROMPTS https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote
* _prompt injection_: getting model to do something its creators don't want
> Ask it to give options (it's more likely to give a better answer)
> It will rarely get the answer right. Ask it to "do better."

---

https://github.com/charmbracelet/mods
https://treyhunner.com/2024/07/chatgpt-and-claude-from-your-browser-url-bar/
building into projects https://news.ycombinator.com/item?id=40857589

LOCAL
https://github.com/ggozad/oterm
* https://llm.datasette.io/en/stable/
* https://github.com/khoj-ai/khoj
* https://github.com/darrenburns/elia
* https://github.com/sigoden/aichat
* https://github.com/simonmysun/ell
* https://datasette.io/tools/llm
* https://github.com/aandrew-me/tgpt
* llamafile https://news.ycombinator.com/item?id=40424519
* BYO https://jnnnthnn.com/how-to-build-your-own-perplexity-for-any-dataset

ZA
* structured output https://news.ycombinator.com/item?id=40713952
* https://notebooklm.google/
* Claude https://www.anthropic.com/ https://x.com/AnthropicAI/status/1803790681971859473
* https://news.ycombinator.com/item?id=40441945
* custom GPT https://talkpython.fm/episodes/show/456/building-gpt-actions-with-fastapi-and-pydantic
* customization prompt https://news.ycombinator.com/item?id=40474716
* telemetry https://github.com/dagworks-inc/burr?tab=readme-ov-file

## code assist

---

* legacy codebases https://bloop.ai/ https://www.driverai.com/

https://aider.chat/ https://news.ycombinator.com/item?id=41453237

https://github.com/guywaldman/magic-cli https://news.ycombinator.com/item?id=40980715

wilder, vimgpt https://www.youtube.com/watch?v=WeulqMMJgrs

https://simonwillison.net/2024/Jul/13/give-people-something-to-link-to/

> The crux of my raging hatred is not that I hate LLMs or the generative AI craze. I had my fun with Copilot before I decided that it was making me stupider - it's impressive, but not actually suitable for anything more than churning out boilerplate. Nothing wrong with that, but it did not end up being the crazy productivity booster that I thought it would be, because programming is designing and these tools aren't good enough (yet) to assist me with this seriously. https://ludic.mataroa.blog/blog/i-will-fucking-piledrive-you-if-you-mention-ai-again/

https://github.com/leapingio/leaping
https://visualstudiomagazine.com/articles/2024/01/25/copilot-research.aspx
https://www.youtube.com/watch?v=MzFr7iXsESs
https://www.youtube.com/watch?v=dkV01hBdhZE

> LLMs are good at explaining code. Give it code in a language you don't understand and it will explain it with 90% accuracy. https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

* code prompt: https://ollama.com/blog/how-to-prompt-code-llama https://ollama.com/blog/run-code-llama-locally Codestral https://ollama.com/blog/continue-code-assistant
* math: https://ollama.com/blog/wizardmath-examples
* Copilot
* Cody https://sourcegraph.com/ https://marketplace.visualstudio.com/items?itemName=sourcegraph.cody-ai
* https://stratechery.com/2024/gemini-1-5-and-googles-nature/
* https://news.ycombinator.com/item?id=37940572
* https://www.youtube.com/watch?v=MzFr7iXsESs
* https://simonwillison.net/2023/Dec/31/ai-in-2023/

## img

* Midjourney https://midlibrary.io/styles
* DALL-E
* Stable Diffusion
* https://news.ycombinator.com/item?id=40437641

## music

* Suno https://www.garbageday.email/p/suno-just-raised-lot-money

# 🟨️ ZA

* _OCR_: image to text https://en.wikipedia.org/wiki/Optical_character_recognition https://news.ycombinator.com/item?id=41048194

---

https://www.nbcnews.com/tech/internet/hunting-ai-bots-four-words-trick-rcna161318

https://softwareengineeringdaily.com/2024/05/14/llms-for-data-queries-with-sarah-nagy/

https://news.ycombinator.com/item?id=40271457

https://news.ycombinator.com/item?id=40184372&utm_term=comment
https://news.ycombinator.com/item?id=40224459
https://twitter.com/skirano/status/1785469853689639379

https://www.freecodecamp.org/learn/machine-learning-with-python/#tensorflow

* context window https://twitter.com/deedydas/status/1778621375592485076
> Google hasn’t said how Gemini 1.5 was made, but clearly the company has overcome the key limitation of traditional transformers: memory requirements increase quadratically with context length. One promising approach is Ring Attention with Blockwise Transformers, which breaks long contexts into pieces to be computed individually even as the various devices computing those pieces simultaneously communicate to make sense of the context as a whole; in this case memory requirements scale linearly with context length, and can be extended by simply adding more devices to the ring topology. https://stratechery.com/2024/gemini-1-5-and-googles-nature/
* https://news.ycombinator.com/item?id=39849393

https://zed.dev/blog/between-editors-and-ides

WAYS OF LEARNING https://danielmiessler.com/blog/machine-learning-new-statistics/
* event-based: no model + datum
* stat: fixed model + data
* transformers https://e2eml.school/transformers.html https://jalammar.github.io/illustrated-transformer/ https://news.ycombinator.com/item?id=37774676 https://news.ycombinator.com/item?id=39898221 https://news.ycombinator.com/item?id=41378806
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
* _VGA (visual question answering)_: answer open-ended question about image https://victorzhou.com/blog/easy-vqa/
* overlap btw stat and ML https://news.columbia.edu/news/top-10-ideas-statistics-ai
* multi-armed bandit, Gittins Index, upper confidence bound 📙 Christian chapter 2
* math: stat/probability, linear algebra https://nostarch.com/math-deep-learning

models
* _model_: machine impl algo (vs. human impl) https://github.com/minimaxir/automl-gs
* serialize https://onnx.ai/
* _gradient descent_: https://www.youtube.com/watch?v=IHZwWFHWa-w

TYPES
* _supervised_: labeled data during training, unlabeled during predication [Trask 2.11]
* _unsupervised_: unlabeled data during training and prediction [Trask 13]
* _reinforcement_: no labels but algo can tell if it's getting hotter or colder http://aiplaybook.a16z.com/docs/guides/dl-learning#user-content-reinforcementlearning
* _parametric_: modeler derives parameters [Trask 2.14, 2.18]
* _nonparametric_: model derives parameters [Trask 2.14, 2.18]

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

OVERRATED
* https://news.ycombinator.com/item?id=30764701
* stagnation https://softwareengineeringdaily.com/2021/06/04/machine-learning-the-great-stagnation-with-mark-saroufim/
* ML hasn't solved radiology https://news.ycombinator.com/item?id=27422610
* as oracle https://marginalrevolution.com/marginalrevolution/2022/06/are-we-entering-an-age-of-oracles.html
* you mostly just need SQL + regression http://aiplaybook.a16z.com/docs/guides/dl https://news.ycombinator.com/item?id=25775872 https://www.youtube.com/watch?v=qw5dBdTXLEs https://ai.google/research/pubs/pub43146 https://nullprogram.com/blog/2020/11/24/
* job market has collapse for data science, big data, ML https://news.ycombinator.com/item?id=24330326 https://news.ycombinator.com/item?id=25775740
* ML doesn't think, only answers, and therefore can be hacked
> In 2017, M.I.T.’s LabSix—a research group of undergraduate and graduate students—succeeded in altering the pixels of a photograph of a cat so that, although it looked like a cat to human eyes, Inception became 99.99-per-cent sure it had been given a photograph of guacamole. (There was, it calculated, a slim chance that the photograph showed broccoli, or mortar.) Inception, of course, can’t explain what features led it to conclude that a cat is a cat; as a result, there’s no easy way to predict how it might fail when presented with specially crafted or corrupted data. Such a system is likely to have unknown gaps in its accuracy that amount to vulnerabilities for a smart and determined attacker. - https://www.newyorker.com/tech/annals-of-technology/the-hidden-costs-of-automated-thinking
> Well, in the past, if a software engineer wanted to create a system to recognise something, they would write logical steps (‘rules’). To recognise a cat in a picture, you would write rules to find edges, fur, legs, eyes, pointed ears and so on, and bolt them all together and hope it worked. The trouble was that though this works in theory, in practice it’s rather like trying to make a mechanical horse - it’s theoretically possible, but the decree of complexity required is impractical. We can’t actually describe all of the logical steps we use to walk, or to recognise a cat. With machine learning, instead of writing rules, you give examples (lots of examples) to a statistical engine, and that engine generates a model that can tell the difference. You give it 100,000 pictures labelled ‘cat’ and 100,000 labelled ‘no cat’ and the machine works out the difference. ML replaces hand-written logical steps with automatically determined patterns in data, and works much better for a very broad class of question - https://www.ben-evans.com/benedictevans/2018/12/19/does-ai-make-strong-tech-companies-stronger
* need data specific to problem
> First, though you need a lot of data for machine learning, the data you use is very specific to the problem that you’re trying to solve. GE has lots of telemetry data from gas turbines, Google has lots of search data, and Amex has lots of credit card fraud data. You can’t use the turbine data as examples to spot fraudulent transactions, and you can’t use web searches to spot gas turbines that are about to fail. https://www.ben-evans.com/benedictevans/2018/12/19/does-ai-make-strong-tech-companies-stronger

## NLP

🗄
* `literature.md` distant reading
* `psychology.md` reading
* `system.md` search engine

BASICS
* _NLP_: linguistics + CS
* rule system (noun phrase can be followed by noun, article, etc.) to construct parse tree
* use cases: speech synthesis http://aiplaybook.a16z.com/docs/guides/nlp speech to text https://www.fullstackpython.com/blog/transcribe-recordings-speech-text-assemblyai.html
* libraries: nltk, spaCy
* _language detection_: https://github.com/pemistahl/lingua-go
* _sentiment analysis_: determine emotional content https://aeon.co/ideas/why-are-pop-songs-getting-sadder-than-they-used-to-be
* _word cloud_: https://dataanalysis.substack.com/p/generating-a-word-cloud-in-python?s=r
* clean up https://nostarch.com/NLPPython https://codewords.recurse.com/issues/seven/data-driven-literary-analysis https://www.fast.ai/2019/07/08/fastai-nlp/ https://speakerdeck.com/pycon2015/adam-palay-words-words-words-reading-shakespeare-with-python https://victorzhou.com/blog/better-profanity-detection-with-scikit-learn/
* word2vec, byte-pair encoding, LSTM https://arpit.substack.com/p/how-zomato-improved-its-search-using https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm 

SEMANTICS
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

## operationalizing

* gradient-boosted trees better for audit than neural nets
* https://roadmap.sh/mlops
* https://news.ycombinator.com/item?id=35438192
* https://applied-llms.org/
* https://news.ycombinator.com/item?id=38120493
* MLflow https://www.thoughtworks.com/radar/tools/mlflow metaflow https://www.thoughtworks.com/radar/tools?blipid=202203023
* can't debug like traditional programming [Ferguson 7] unexplainable? https://blog.cerebralab.com/Machine_learning_could_be_fundamentally_unexplainable
* aka ml ops https://news.ycombinator.com/item?id=20865012 https://testdriven.io/blog/machine-learning-reliability-engineering/
* web app integration https://github.com/xadrianzetx/fullstack.ai https://news.ycombinator.com/item?id=20865012 https://talkpython.fm/episodes/transcript/226/building-flask-apis-for-data-scientists https://testdriven.io/blog/fastapi-machine-learning/
* quants can't code, coders can't quant https://news.ycombinator.com/item?id=23941075
* 90% of the job is munging data, models are implemented by people w/ PhDs https://towardsdatascience.com/the-cold-start-problem-how-to-build-your-machine-learning-portfolio-6718b4ae83e9 https://spectrum.ieee.org/view-from-the-valley/artificial-intelligence/machine-learning/andrew-ng-xrays-the-ai-hype more on job market https://evjang.com/2022/04/25/rome.html
* https://www.youtube.com/watch?v=JLTYNPoK7nw https://www.youtube.com/watch?v=pvaIi0l1GME https://softwareengineeringdaily.com/2019/06/13/stripe-machine-learning-infrastructure-with-rob-story-and-kelley-rivoire/

## projects

* Iris dataset https://www.youtube.com/results?search_query=iris+dataset https://docs.pola.rs/user-guide/misc/visualization/#altair
* get familiar https://simonwillison.net/2024/Apr/17/ai-for-data-journalism/
* https://www.freecodecamp.org/news/customer-segmentation-python-machine-learning/
* https://archive.vn/073bS
* https://news.ycombinator.com/item?id=40877136
* train model on dickens, cowen
* https://www.freecodecamp.org/learn/machine-learning-with-python/machine-learning-with-python-projects/book-recommendation-engine-using-knn

## uses

---

* text to SQL https://github.com/vanna-ai/vanna
* chat with your docs https://github.com/Cinnamon/kotaemon
* to synthesize all comments on a product into a blurb https://blog.untrod.com/2024/04/llm-chatgpt-powered-django-admin-fields.html
* copyedit a novel https://blog.untrod.com/2023/06/copy-editing-a-novel-with-chatgpt.html
* audio prompt + voice cloning for answer https://blog.untrod.com/2023/11/robot-dad.html https://elevenlabs.io/
* vocals https://audimee.com/
* analyze research papers https://elicit.com/
* IFTTT https://news.ycombinator.com/item?id=41059821 https://en.wikipedia.org/wiki/IFTTT
* audio transcription https://news.ycombinator.com/item?id=41199567
* deep fakes https://github.com/hacksider/Deep-Live-Cam
