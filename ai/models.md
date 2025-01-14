# ⛩️

## 参考

🛣️ https://roadmap.sh/mlops
📚
* Huyen designing ml systems https://www.amazon.com/dp/1098107969
* https://www.amazon.com/Machine-Learning-System-Design-Interview/dp/1736049127
* https://www.amazon.com/Generative-AI-System-Design-Interview/dp/1736049143
* https://www.amazon.com/dp/1098149246

## 进步

* _24_: ChatGPT (regex and Polars, then incorporate research) Claude (switch after GPT outage)
* _23_: few random queries

# 🥗 MENU

🛠️ benchmark https://arena.lmsys.org/
🔍 compare https://news.ycombinator.com/item?id=42348513 https://simonwillison.net/2024/Dec/16/webdev-arena/
🔑 https://gist.github.com/zachvalenta/d3b7cd172dd2d3d8ff7340bd458c6fe2

SLM
* _Gemini nano_: 
* _MS phi_:

ZA
* _BERT_: https://simonwillison.net/2024/Dec/31/alexis-gallagher/ https://github.com/urchade/GLiNER
* _DeepSeek_: https://thezvi.substack.com/p/deekseek-v3-the-six-million-dollar https://www.chinatalk.media/p/deepseeks-edge
* _X grok_: seems tied to Twitter https://grok.x.ai/ 

---

OPEN https://simonwillison.net/2024/Jun/17/cli-language-models/
* _Codestral_: https://ollama.com/blog/continue-code-assistant
* _Centaur_: https://x.com/marcel_binz/status/1850806691958313160
* _Gemma_: https://ai.google.dev/gemma
* _jan_: 🎯 https://github.com/janhq/jan
* _Qwen_: https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can

CLOSED
* _Amazon nova_: https://news.ycombinator.com/item?id=42309121 https://news.ycombinator.com/item?id=42309121 https://simonwillison.net/2024/Dec/4/amazon-nova/ https://simonwillison.net/2024/Dec/4/amazon-nova/
* backed by Amazon https://news.ycombinator.com/item?id=42215126
* _Mistral codestral_: less polished but fast + search https://chat.mistral.ai/chat
* Mixtral https://mistral.ai/news/mixtral-of-experts/
* YiCoder: https://news.ycombinator.com/item?id=41453237
* features: moderation, tuning to domain
* Haiku
* Genie https://news.ycombinator.com/item?id=42317903

## ☸️ ChatGPT

🔑 https://platform.openai.com/api-keys

MODELS
* legacy: 22.11 GPT 23.03 GPT4
* _4o_: 24.05
* _o1_: https://simonwillison.net/2024/Dec/7/prompts-js/ https://marginalrevolution.com/marginalrevolution/2024/12/dean-ball-speaks.html
* _o1 pro_: 24.12 (preview in 24.09) https://thezvi.substack.com/p/o1-turns-pro https://x.com/mckaywrigley/status/1865089975802646857 https://news.ycombinator.com/item?id=42330732

ZA
* 1-800-CHATGPT https://help.openai.com/en/articles/10193193-1-800-chatgpt-calling-and-messaging-chatgpt-with-your-phone
* internal libraries, `ace_tools` https://community.openai.com/t/chatgpt-recommends-the-use-of-the-open-ai-internal-library-ace-tools/852665
* native client: global hotkey conflicts with iterm https://openai.com/chatgpt/mac
* ❌ started having uptime issues 24.12

WEB CLIENT
* search added 241031 (intra-doc but slow, none by title)
* projects added 241214
* when you open a chat it's not reflected in the sidebar so if you want to rename or delete it you have to scroll sidebar and manually find it
* ❌ no page up/down, no home/end
* dark mode is bad for seeing prompt

## 🟫 Claude

🔑 https://console.anthropic.com
📜 https://docs.anthropic.com/en/home
🔢 https://docs.anthropic.com/en/release-notes/overview

WEB CLIENT
* fast input 🗄️ `vim.md` Zed
* good font
* code syntax highlighting
* retry
* mass delete
* controls (artifacts = output, content = attachments)
* org: search/stars
* outputs code in a sidebar to prevent tons of scrolling in the main chat
* interop with Google Docs
* ✅ yes page up/down, yes home/end
* ❌ conventions: user-level and per project
> doesn't listen, continues to gen typed Python
> conversations bleed, starts giving me Click CLIs when I haven't asked for them
* ❌ projects: can't add chat to project after the fact, can't view chats as part of projects
* ❌ can't follow URLs

MODELS
> built on AWS https://simonwillison.net/2024/Dec/5/claude-35-haiku-price-drops-by-20/
* _Sonnet_: best for code https://simonwillison.net/2025/Jan/13/codestral-2501/
* _Haiku_: fastest, better than GPT 3.5 https://www.youtube.com/watch?v=QUXQNi6jQ30 [5:30]
* _Opus_: writing

---

CONTEXT
* system prompt https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts
* developer console https://www.anthropic.com/news/evaluate-prompts
* projects https://www.anthropic.com/news/projects how to get good at projects https://x.com/patrick_oshag/status/1876455619516911720

* allegedly the best but GPT legacy model beat it and the other time I tried it admitted to fabricating data https://x.com/emollick/status/1849168452914938082 https://simonwillison.net/2024/Oct/21/claude-artifacts/ https://darioamodei.com/

## 🌉 Gemini

---

* https://thezvi.substack.com/p/the-second-gemini
* voice https://news.ycombinator.com/item?id=42397210
* no search/tags/org, looks low-effort
* https://simonw.substack.com/p/video-scraping-using-google-gemini

## hardware

🗄️ `hw.md` Apple 

https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can https://simonwillison.net/2024/Dec/9/llama-33-70b/ https://news.ycombinator.com/item?id=42539155&

> 🎗️ llamafile https://simonwillison.net/2024/Jun/17/cli-language-models/ https://simonwillison.net/2023/Nov/29/llamafile/ "this should be technically impossible" (having a single unmodified binary run across mac/Windows/linux) https://www.youtube.com/watch?v=QUXQNi6jQ30 [20:00]
* mini23 uses 8B just w/ VS Code + browser + macOS core services
* Qwen req 32B
* Simon has 64B

---

* run locally https://github.com/getumbrel/llama-gpt
* run locally https://github.com/Mozilla-Ocho/llamafile
* running locally, llamafile https://news.ycombinator.com/item?id=40424519
* code prompt: https://ollama.com/blog/how-to-prompt-code-llama https://ollama.com/blog/run-code-llama-locally

## 🦙 llama

* _Meta llama_: https://x.com/rowancheung/status/1865107700087980170 https://en.wikipedia.org/wiki/Llama_(language_model) uncensored https://ollama.com/blog/llama-3-is-not-very-censored https://ollama.com/blog/run-llama2-uncensored-locally https://joshuacook.netlify.app/posts/2024-01-31_ollama-quickstart/
* ccmake https://news.ycombinator.com/item?id=42274489
* _ollama_: ⭐️ https://ollama.com/
> customize through a Modelfile, incl model parameters, system prompts etc. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* multimodal, OCR https://ollama.com/blog/llama3.2-vision https://www.youtube.com/watch?v=wTukMgtkleA LanceDB https://talkpython.fm/episodes/show/488/multimodal-data-with-lancedb

## 📚 Perplexity

* _Perplexity api_: search/org https://www.perplexity.ai/

# 🏗️ OPERATIONALIZE

start here https://parlance-labs.com/education/ https://applied-llms.org/ https://www.agentrecipes.com/prompt-chaining

---

📙
* Clinton obsolete gen AI
* https://www.amazon.com/gp/product/1736049127
* https://www.amazon.com/dp/1736049143

* retrieval vs. generative https://cohere.com/
* testing https://news.ycombinator.com/item?id=42317878 https://news.ycombinator.com/item?id=42330666 https://github.com/BCG-X-Official/artkit https://www.youtube.com/watch?v=pGZo9gR5q_M https://gentrace.ai/ https://github.com/traceloop/openllmetry https://langfuse.com/ https://www.thoughtworks.com/radar/platforms/langfuse https://news.ycombinator.com/item?id=42441258 https://www.thoughtworks.com/radar/techniques/llm-as-a-judge

* gradient-boosted trees better for audit than neural nets
* https://roadmap.sh/mlops
* https://news.ycombinator.com/item?id=35438192
* https://applied-llms.org/
* https://news.ycombinator.com/item?id=38120493
* MLflow https://www.thoughtworks.com/radar/tools/mlflow metaflow https://www.thoughtworks.com/radar/tools?blipid=202203023
* can't debug like traditional programming [Ferguson 7]
* aka ml ops https://news.ycombinator.com/item?id=20865012 https://testdriven.io/blog/machine-learning-reliability-engineering/
* web app integration https://github.com/xadrianzetx/fullstack.ai https://news.ycombinator.com/item?id=20865012 https://talkpython.fm/episodes/transcript/226/building-flask-apis-for-data-scientists https://testdriven.io/blog/fastapi-machine-learning/
* quants can't code, coders can't quant https://news.ycombinator.com/item?id=23941075
* 90% of the job is munging data, models are implemented by people w/ PhDs https://towardsdatascience.com/the-cold-start-problem-how-to-build-your-machine-learning-portfolio-6718b4ae83e9 https://spectrum.ieee.org/view-from-the-valley/artificial-intelligence/machine-learning/andrew-ng-xrays-the-ai-hype more on job market https://evjang.com/2022/04/25/rome.html
* https://www.youtube.com/watch?v=JLTYNPoK7nw https://www.youtube.com/watch?v=pvaIi0l1GME https://softwareengineeringdaily.com/2019/06/13/stripe-machine-learning-infrastructure-with-rob-story-and-kelley-rivoire/
* this seems dumb but maybe I don't understand yet https://calmcode.io/course/deon/introduction

## agents

🔍 https://mychaelangelo.github.io/ai_agents_marketmap/

---

* defining https://www.anthropic.com/research/building-effective-agents
https://simonwillison.net/2025/Jan/11/agents/
https://www.thoughtworks.com/radar/techniques/function-calling-with-llms
> They discuss "agentic systems" as a parent term, then define a distinction between "workflows" - systems where multiple LLMs are orchestrated together using pre-defined patterns - and "agents", where the LLMs "dynamically direct their own processes and tool usage". https://simonwillison.net/2024/Dec/20/building-effective-agents/
* as judge https://registerspill.thorstenball.com/p/joy-and-curiosity-20
* LLM controlling your browser?
https://ai.pydantic.dev/
https://www.thediff.co/archive/offshoring-and-ai-agents/
https://github.com/ishan0102/vimGPT
* _agent_: give it a dataset, it writes the paper https://www.oneusefulthing.org/p/almost-an-agent-what-gpts-can-do
https://edwardbenson.com/2024/06/how-to-reason-about-agent-performance#user-content-fn-1
https://edwardbenson.com/2024/11/the-worlds-first-ai-street-hawker
https://edwardbenson.com/lollm
https://news.ycombinator.com/item?id=42299098
https://x.com/SullyOmarr/status/1864697992261062690/photo/1

## Hugging Face

> Transformers supports the majority of models available in Hugging Face’s Model Hub, and encompasses diverse tasks in natural language processing, computer vision, and audio processing...Because it’s built on top of PyTorch, TensorFlow, and JAX, [Hugging Face] `transformers` gives you the flexibility to use these frameworks to run and customize models at any stage. Using open-source models through Transformers has several advantages: Proprietary AI companies like OpenAI, Cohere, and Anthropic often charge you a token fee to use their models via an API. This means you pay for every token that goes in and out of the model, and your API costs can add up quickly. By deploying your own instance of a model with Transformers, you can significantly reduce your costs because you only pay for the infrastructure that hosts the model. https://realpython.com/huggingface-transformers/#exploring-hugging-face

ZERO-SHOT CLASSIFICATION
```python
model_name = "MoritzLaurer/deberta-v3-large-zeroshot-v2.0"
zs_text_classifier = pipeline(model=model_name)
candidate_labels = [
     "Billing Issues",
     "Technical Support",
     "Account Information",
     "General Inquiry",
]

hypothesis_template = "This text is about {}"

customer_text = "My account was charged twice for a single order."
zs_text_classifier(
    customer_text,
    candidate_labels,
    hypothesis_template=hypothesis_template,
    multi_label=True
)

"""
{'sequence': 'My account was charged twice for a single order.',
 'labels': ['Billing Issues',
            'General Inquiry',
            'Account Information',
            'Technical Support'],
 'scores': [0.98844587,
            0.01255007,
            0.00804191,
            0.00021988]}
"""
```
* image classification
```sh
python -m pip install Pillow
```
```python
image_classifier = pipeline(task="image-classification")
predictions = image_classifier(["llamas.png"])
predictions[0][0]  # {'label': 'llama', 'score': 0.9991388320922852}
predictions[0][1]  # {'label': 'Arabian camel, dromedary, Camelus dromedarius', 'score': 8.780974167166278e-05}
```


SENTIMENT ANALYSIS, TSS https://www.freecodecamp.org/news/get-started-with-hugging-face/
```sh
pip install transformers, tokenizers, datasets
```
```python
from transformers import pipeline

sentiment_analysis = pipeline("sentiment-analysis", model="distilbert-base-uncased-finetuned-sst-2-english")
input_text = [ "It’s a great app, my biggest problem is the card readers regularly do not connect. Which is very poor customer service for us because we have to manually enter our customers debit cards, which takes time. This slows down our efficiency." ]
result = sentiment_analysis(input_text)

transcriber = pipeline(task="automatic-speech-recognition", model="openai/whisper-small")
result = transcriber("https://huggingface.co/datasets/Narsil/asr_dummy/resolve/main/mlk.flac")
```

## keyword search

https://www.youtube.com/watch?v=d5i5Lc9X4Og
> 122 views 3 weeks after upload! what are people doing with their time!

> Keyword search is the traditional approach where the search engine looks for exact matches or close variants of the words in the query. For example, if you search "red car," it finds documents containing those exact words. It's fast and straightforward but can miss relevant results that use different terminology (like "crimson automobile").

## hybrid search

> Hybrid search combines both approaches to leverage their respective strengths. It typically uses keyword search for precise matches and high-confidence results, while incorporating semantic search to catch relevant results that wouldn't be found through exact word matching alone. For instance, an e-commerce site might use keyword search to find products with exact name matches, while using semantic search to suggest related items that might interest the user even if they don't contain the exact search terms.

> A practical example: If you search "how to treat a headache," a hybrid system would:
> Use keyword matching to find articles containing "headache" and "treat"
> Use semantic search to also find relevant content about "migraine remedies" or "pain relief techniques"
> Combine and rank these results based on both literal relevance and semantic meaning

## semantic search

BYO + RAG https://claude.ai/chat/ec4dbe09-e48a-466f-9e35-a7e430af0265

---

> Semantic search understands the meaning and intent behind queries rather than just matching words. It uses techniques like word embeddings and neural networks to understand context and relationships. For example, a semantic search for "red car" might also return results about "scarlet vehicles" or even "burgundy SUVs" because it understands these are conceptually related. It's particularly good at handling natural language queries and understanding synonyms, but can be more computationally intensive.

* https://koratkar.github.io/cwt-semantic-search/ https://x.com/whybyfire/status/1866239929732173846
> So semantic search is often a component of RAG, but RAG goes beyond just search. Here's an analogy: semantic search is like having a really smart librarian who understands what you're looking for and can find relevant books. RAG is like having that librarian plus a subject matter expert who can read those books, synthesize the information, and explain it to you in your own terms. https://claude.ai/chat/18bc4333-ff09-45f8-8610-0c325ce11ecf

https://chatgpt.com/c/675b9317-4bc4-8004-a0a5-b9d683ebd3d8 (now deleted)
> Semantic search is a search methodology that focuses on understanding the intent and contextual meaning of a query, rather than just matching keywords. It uses techniques like: Word embeddings to encode text meaning. Vector similarity to find relevant matches in a corpus. Contextual models, often based on transformers like BERT or Sentence-BERT, to retrieve results based on semantic relevance. Semantic search is focused on retrieval, aiming to return the most relevant documents, snippets, or knowledge units in response to a query.
> RAG is a hybrid system that combines two key stages: Retrieval: Uses semantic search or similar retrieval mechanisms to fetch relevant documents or knowledge pieces in response to a query. Generation: Uses a generative model (e.g., GPT or another transformer) to produce a response. The model conditions its output on both the query and the retrieved content.

https://news.ycombinator.com/item?id=42507116

## RAG

💡 core model enhanced by access to specific docs
🛠️ markitdown
🗄️
* `doc.md` notes
* `algos.md` search > bm25
📚
* Bratanic https://www.manning.com/books/knowledge-graph-enhanced-rag
* Farooq build LLM apps https://www.manning.com/books/build-llm-applications-from-scratch https://www.alldayta.com/#product-demo
* Kimothi https://www.manning.com/books/a-simple-guide-to-retrieval-augmented-generation

https://github.com/Cinnamon/kotaemon

HOWTO (LEARN BY BUILDING FOR DROR)
```txt
I'm still new to the space, so take with a grain of salt https://chatgpt.com/share/6756f806-27c4-8004-8768-b94f879a8b5e

* data prep: I have a good library in mind https://github.com/chonkie-ai/chonkie
* embeddings: would probably do with model aaS (GPT, Claude)
* vector db: I've been keeping tabs of the vector db ecosystem but that means ~20 links I haven't yet read and need to. Hopefully I can find either an embedded option or a good hosted service.
* training: assume we'd use transfer | reinforcement learning vs. getting into the weeds with adjusting the weights (finetuning, LoRA, PEFT) https://www.youtube.com/watch?v=55guW-DZVM0
```
* prompt
```txt
I want to build RAG for a book I'm writing so that I can learn more about the book (where is the structure weak? what connections *could* I make that I haven't already?). I want the RAG to act as some combination of an editor and a critic.
```
* completion
```txt
1. Data Preparation
Segment the Book: Split your manuscript into manageable chunks, such as chapters, sections, or paragraphs.
Create Metadata: Annotate each chunk with relevant metadata (e.g., chapter, themes, key ideas).
Embed Contextual Information: If you have earlier drafts, notes, or research material, include these as part of the corpus.
2. Knowledge Base Construction
Use embeddings to create a vectorized representation of each chunk, enabling semantic search. Libraries like OpenAI's embeddings, Hugging Face, or Sentence Transformers are excellent choices.
Organize a knowledge base (e.g., Pinecone, Weaviate, or FAISS) to allow fast and efficient retrieval.
3. RAG Architecture
Retrieval Component: Query your knowledge base for related chunks based on prompts.
Generation Component: Use a generative model fine-tuned on critique/editing tasks. Models like GPT-4 or fine-tuned open-source models can work well here.
4. Functionality
Structural Weakness Analysis: Prompt the system with questions like, “What parts of this argument lack support?” or “Where does the structure feel inconsistent?”
Connection Suggestions: Use prompts like, “What connections can be made between [Section A] and [Section B]?” or “Suggest thematic overlaps I’ve overlooked.”
Critique Generation: Ask for specific feedback, such as, “Critique the logical flow of this section” or “Analyze the character development in this chapter.”
5. Iterative Refinement
Analyze the outputs and iteratively refine the RAG system by adjusting the prompts, embeddings, or fine-tuning the model based on your unique style and goals.
```
* prompt
```txt
Is there an aider but for prose? What I'm looking for is something that has aider's map of everything you've written https://aider.chat/docs/repomap.html
+ text transform i.e. "take this paragraph and turn it into Proust"

https://www.hyperwriteai.com/aitools/text-style-transfer
```

---

https://github.com/hfhoffman1144/langchain_neo4j_rag_app https://realpython.com/build-llm-rag-chatbot-with-langchain/
⭐️ start here https://github.com/theam/rag-workshop-pydata-nyc-2024 https://www.youtube.com/watch?v=C4u1SjGiT_8 https://www.youtube.com/watch?v=XU2xhCHqILE

https://news.ycombinator.com/item?id=42360685
https://github.com/koaning
https://www.youtube.com/watch?v=kCCC-NlJgIA
https://simonwillison.net/2024/Dec/6/roaming-rag/
pipelines https://www.youtube.com/watch?v=YM3UrQd2wEA
* https://lincolnloop.com/insights/building-a-chat-backend-for-wikipedia-articles-in-django/
* BYO https://github.com/bhavnicksm/chonkie https://github.com/explosion/spacy-layout https://training.talkpython.fm/courses/getting-started-with-spacy https://github.com/DS4SD/docling https://x.com/_inesmontani
> I said earlier that building an LLM was still out of reach of hobbyists. That may be true for training from scratch, but fine-tuning one of those models is another matter entirely.  There’s now a fascinating ecosystem of people training their own models on top of these foundations, publishing those models, building fine-tuning datasets and sharing those too. The Hugging Face Open LLM Leaderboard is one place that tracks these. I can’t even attempt to count them, and any count would be out-of-date within a few hours. https://simonwillison.net/2023/Dec/31/ai-in-2023/ more on Hugging Face https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a
* howto: Python in a sidecar and then your server in another language (that lacks Python's ML stdlib) talks to that https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/

START HERE 🗄️ `algos.md` neural networks
https://github.com/Shubhamsaboo/awesome-llm-apps https://www.theunwindai.com/p/build-a-personal-health-and-fitness-ai-agent-using-google-gemini
* https://www.youtube.com/watch?v=PJaqp5Kdwz0
* https://github.com/pingcap/autoflow https://github.com/stanfordnlp/dspy
* https://news.ycombinator.com/item?id=42174829
* https://haystack.deepset.ai/overview/quick-start https://www.youtube.com/watch?v=6aYclVrsqu0 https://www.youtube.com/watch?v=KYxlM0hh96o
* https://github.com/D-Star-AI/dsRAG/
* https://github.com/snexus/llm-search
* https://arcturus-labs.com/blog/2024/11/21/roaming-rag--make-_the-model_-find-the-answers/

* https://www.thoughtworks.com/radar/techniques/fine-tuning-embedding-models
* https://openai.com/12-days/
* _Guru_: https://www.getguru.com/
> Retrieval augmented generation (RAG) is an architecture that provides the most relevant and contextually-important proprietary, private or dynamic data to your Generative AI application's large language model (LLM) when it is performing tasks to enhance its accuracy and performance. https://www.pinecone.io/learn/retrieval-augmented-generation/
* BYO https://www.youtube.com/@zackproser/videos https://aws.amazon.com/bedrock/ https://simonwillison.net/2024/Dec/6/llama-33/
* _RAG_: document-based interactions https://github.com/sigoden/aichat#rag-chat-with-your-documents TTS https://changelog.com/practicalai/288 https://zackproser.com/blog/how-are-embeddings-models-trained-for-rag https://www.manning.com/books/a-simple-guide-to-retrieval-augmented-generation knowledge graph https://www.manning.com/books/knowledge-graph-enhanced-rag
* when you need more than either aaS or OSS
> If such a customized LLM is a suitable solution for your project, consider just running Ollama or Llamafile and using their REST APIs to communicate with the model. If you need higher degrees of customization, read on. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* BYO https://us.pycon.org/2024/schedule/presentation/103/index.html https://github.com/Quansight/ragna
> We’re going to build a RAG server in Go. This is an HTTP server that provides two operations to users: Add a document to the knowledge base. Ask an LLM a question about this knowledge base. https://go.dev/blog/llmpowered
> You talked a lot about this distinction between LLM benchmarks and evaluating LLM applications. Could you talk a little bit about the differences? Maybe there are software engineers in the audience, that maybe they’re used to writing unit tests and integration tests for their software. Now as a consumer, as you said, they’re integrating some LLM functionality, or maybe a chain of reasoning with LLMs into their software. From a practical standpoint, what are the new types of things that they might need to consider that are different maybe from the way that they’ve unit-tested in the past, or written tests in the past, now that they’re working with these LLM workflows? https://changelog.com/practicalai/284#transcript
> Generative AI models struggle when you ask them about facts not covered in their training data. Retrieval Augmented Generation—or RAG—enhances an LLM’s available data by adding context from an external knowledge base, so it can answer accurately about proprietary content, recent information, and even live conversations. https://www.manning.com/books/a-simple-guide-to-retrieval-augmented-generation
> Claude's extensive context window has also transformed their approach to handling large codebases. When the 200K context window was released, Hedley notes they "ripped out the entire RAG and just put it in the context window instead and it went from 60 percent accuracy to 98. It was quicker, cheaper, better, everything." This combination of automation, speed, and accuracy has fundamentally changed how Headstart approaches software development. https://www.anthropic.com/customers/headstart
https://openai.com/index/introducing-canvas/
* https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
https://zackproser.com/blog/i-am-joining-pinecone-io
* RAG, vector https://news.ycombinator.com/item?id=41105130 https://en.wikipedia.org/wiki/Retrieval-augmented_generation https://retool.com/blog/retrieval-augmented-generation https://www.youtube.com/watch?v=Q75JgLEXMsM https://www.youtube.com/watch?v=PJaqp5Kdwz0
* how to teach https://news.ycombinator.com/item?id=38759877
* with notes https://github.com/reorproject/reor
https://www.amazon.com/gp/product/1098107969
* _NotebookLM_: https://notebooklm.google.com/ https://simonw.substack.com/p/video-scraping-using-google-gemini
* https://simonw.substack.com/p/video-scraping-using-google-gemini
* tokens https://github.com/simonw/ttok
* AWS Textract https://github.com/simonw/textract-cli
* chat with your docs https://github.com/Cinnamon/kotaemon
* ingest all your notes https://news.ycombinator.com/item?id=41732634
* analyze research papers https://elicit.com/
* PDF https://dev.to/jagroop2001/building-a-chat-with-pdfs-using-pinataopenai-and-streamlit-3jb7
* https://www.assemblyai.com/

BYO
* https://www.youtube.com/watch?v=kCc8FmEb1nY
* https://news.ycombinator.com/item?id=41412256&utm_term=comment
* https://spreadsheets-are-all-you-need.ai/index.html
* https://iamjoshknox.com/2023/12/06/econeats-an-ai-dining-guide/
* https://www.saaspegasus.com/guides/django-websockets-chatgpt-channels-htmx
* https://github.com/langgenius/dify
* https://github.com/BerriAI/litellm

* _langchain_: https://zackproser.com/blog/office-oracle-overview https://www.amazon.com/dp/1835083463
> We mentioned some of the emerging criticisms about LangChain in the previous Radar. Since then, we’ve become even more wary of it. While the framework offers a powerful set of features for building applications with large language models (LLMs), we’ve found it to be hard to use and overcomplicated. LangChain gained early popularity and attention in the space, which turned it into a default for many developers. However, as LangChain is trying to evolve and keep up with the fast pace of change, it has become harder and harder to navigate those changes of concepts and patterns as a developer. We’ve also found the API design to be inconsistent and verbose. As such, it often obscures what is actually going on under the hood, making it hard for developers to understand and control how LLMs and the various patterns around them actually work. We’re moving LangChain to the Hold ring to reflect this. In many of our use cases, we’ve found that an implementation with minimum use of specialized frameworks is sufficient. Depending on your use case, you may also want to consider other frameworks such as Semantic Kernel, Haystack or LiteLLM.  https://www.thoughtworks.com/radar/languages-and-frameworks/langchain

## train

📙
* Brosseau LLMs in production https://www.manning.com/books/llms-in-production
* Labonne https://github.com/PacktPublishing/LLM-Engineers-Handbook https://www.amazon.com/gp/product/1836200072
🧠 https://chatgpt.com/c/6756f73a-9d68-8004-9ef8-34d9744f767d

* _train_: further training pretrained model on specific domains using labeled data or prompts 📙 Clinton obsolete gen AI

---

* https://realpython.com/huggingface-transformers/#looking-under-the-hood-with-auto-classes
* https://realpython.com/huggingface-transformers/#setting-up-a-google-colab-notebook
* Fine-tuning (Full or Transfer Learning)
> Requires substantial compute and a large, high-quality dataset
* Parameter-Efficient Fine-Tuning (LoRA / PEFT)   
* Reinforcement Learning (RLHF or Task-Specific)

* train on your own emails https://github.com/zycyc/LAMBDA
data prep kit https://www.youtube.com/watch?v=tqRvmg2F_gI https://github.com/IBM/data-prep-kit
> assume we'd use transfer or reinforcement learning vs. getting into the weeds with adjusting the weights (finetuning, LoRA, PEFT)

https://changelog.com/practicalai/295

* inference scaling vs. model scaling https://simonwillison.net/2024/Dec/19/is-ai-progress-slowing-down/

# 🏗️ USAGE

🔍 https://a16z.com/100-gen-ai-apps-3/

---

usage aka modality e.g. GPT understanding images with GPT4 examples of multimodality i.e. text and images

ZA
* text to SQL https://github.com/vanna-ai/vanna
* to synthesize all comments on a product into a blurb https://blog.untrod.com/2024/04/llm-chatgpt-powered-django-admin-fields.html
* copyedit a novel https://blog.untrod.com/2023/06/copy-editing-a-novel-with-chatgpt.html
* detection https://deepmind.google/technologies/synthid/?utm_source=www.superpowerdaily.com&utm_medium=newsletter&utm_campaign=new-claude-ai-can-take-over-your-computer

https://platform.openai.com/docs/overview https://cookbook.openai.com/

## audio

🗄️ Hugging Face

GPT has a STT endpoint 📙 Clinton

TYPES https://elevenlabs.io/
* didn't work https://huggingface.co/spaces/openai/whisper
* dubbing
* voice clone https://www.tetragrammaton.com/content/richard-feynman
* _TTS_: https://notebooklm.google/ https://news.ycombinator.com/item?id=41964980 PDF to audio https://www.fwdaudio.com/ https://x.com/barbell_fi multistage https://simonw.substack.com/p/verdad-tracking-misinformation-in https://www.fwdaudio.com/
> Everyone is talking about the new hashtag#AI Notebook LM tool from Google that lets you create podcasts from articles and other sources. I decided to try it for myself, using one of my prior pieces, The Upside and Downside of AI, as the basis for the podcast. The result, which you can listen to in the article, is simply amazing. It doesn't just read the article - it has a discussion between two "people" about it that is very engaging. https://arnoldkling.substack.com/p/llm-links-b9d
> Meta recently introduced NotebookLlama, an "open" version of Google’s podcast-generating feature found in NotebookLM. Leveraging Meta's Llama models, NotebookLlama is capable of creating conversational, podcast-style digests of uploaded text files, such as PDFs of news articles or blog posts. This technology aims to replicate the interactive storytelling aspect of Google's viral tool, adding its own elements of dramatization and interruptions to make the content sound more dynamic. https://www.superpowerdaily.com/p/google-preps-jarvis-ai-agent-that-works-in-chrome
* _STT_: https://news.ycombinator.com/item?id=41941845

---

* TTS https://github.com/fishaudio/fish-speech https://til.simonwillison.net/ios/listen-to-page Hugging Face https://til.simonwillison.net/macos/whisper-cpp
* text to voice e.g. AWS Polly https://aws.amazon.com/blogs/aws/introducing-aws-b2b-data-interchange-simplified-connections-with-your-trading-partners/
* transcription https://news.ycombinator.com/item?id=41199567 https://www.theguardian.com/media/2014/jan/22/ten-tools-for-digital-and-citizen-journalists-on-the-go
* audio prompt + voice cloning for answer https://blog.untrod.com/2023/11/robot-dad.html https://elevenlabs.io/
* voice clone https://www.jeffgeerling.com/blog/2024/elecrow-responded-apologized-ai-voice-cloning
* speech to text https://github.com/kyutai-labs/moshi
* generative music https://www.garbageday.email/p/suno-just-raised-lot-money
* vocals https://audimee.com/
* Siri https://github.com/homebrewltd/ichigo
* mastering https://www.youtube.com/watch?v=wZRV2H4PK0Q
* tone https://x.com/ilanbigio/status/1861913173432946808

## forecasting

https://arxiv.org/pdf/2411.01582
> use to build stock market

## img

EXAMPLES
* https://www.mercatus.org/doge

* _TTV_: https://simonwillison.net/2024/Dec/9/sora/
* _TFI_: https://calmcode.io/shorts/pytesseract.py
* image to video https://www.vidifyapp.com/
* _OCR_: image to text e.g. PDF to plaintext https://en.wikipedia.org/wiki/Optical_character_recognition https://news.ycombinator.com/item?id=41048194 https://getomni.ai/ocr-demo https://news.ycombinator.com/item?id=41971614 https://github.com/Nutlope/llama-ocr

---

* video https://x.com/bilawalsidhu/status/1857816146688217099
* video scraping https://simonw.substack.com/p/video-scraping-using-google-gemini
* image recognition https://www.youtube.com/watch?v=XPA213k8G_U
* image to spreadsheet https://news.ycombinator.com/item?id=41059821 https://en.wikipedia.org/wiki/IFTTT
* deep fakes https://github.com/hacksider/Deep-Live-Cam
* image search https://tembo.io/blog/image-search
* https://github.com/GabAlpha/basilk https://perchance.org/ai-pixel-art-generator
* Midjourney https://midlibrary.io/styles
* DALL-E
* Stable Diffusion https://www.youtube.com/watch?v=kG9l41Dtuyo
* https://news.ycombinator.com/item?id=40437641
* https://github.com/orhun/menyoki

## projects

* algos https://github.com/ritchie46/vanilla-machine-learning https://www.manning.com/books/optimization-algorithms
* get familiar https://simonwillison.net/2024/Apr/17/ai-for-data-journalism/
* https://www.freecodecamp.org/news/customer-segmentation-python-machine-learning/
* https://archive.vn/073bS
* https://news.ycombinator.com/item?id=40877136
* train model on dickens, cowen
* https://www.freecodecamp.org/learn/machine-learning-with-python/machine-learning-with-python-projects/book-recommendation-engine-using-knn

# 🟨️ ZA

## prompts

🔗 https://www.promptingguide.ai/techniques/fewshot https://www.thoughtworks.com/radar/techniques/dynamic-few-shot-prompting
📙
* https://www.manning.com/books/prompt-engineering-in-practice
* https://www.manning.com/books/prompt-engineering-in-action
🗄️
* `psychology.md` interviewing
* `work.md` industry > Stack Overflow

SEMANTICS
* _prompt_: question
* _completion_: answer 📙 Clinton obsolete gen AI
* _prompt engineering_: asking specific questions https://marginalrevolution.com/marginalrevolution/2023/05/how-to-use-gpt-4-plus-web-browsing.html https://www.youtube.com/watch?v=hB7sGE0W8CI
* _prompt injection_: getting model to do something its creators don't want https://simonwillison.net/2023/Dec/31/ai-in-2023/
* _system message_: hidden instruction that defines the behavior/goals/tone of the model; aka system prompt https://chatgpt.com/c/67106e28-a6e0-8004-9ef0-dd2f3b1eb48b https://github.com/charmbracelet/mods#custom-roles
> "You are a helpful assistant named Elia."

STOCK
* taxonomy
```txt
Can you give a taxonomy of $FOO in the form of a tree, like this?
├── root
│   └── nodes
│   └──── leaves
```
* summary
```txt
Can you analyze a book for me: $BOOK
First, summarize key points in a succinct and logical way i.e. I care most about the claims made by the author and how they are logically supported (or not).
Next, summarize criticism of the book (positive or negative) in a similar manner.
Finally, extract relevant quotes, both indicative of the books arguments and anything that marks its writing style as specific e.g. an airport business book probably has little to mark it stylistically interesting, whereas Proust does.
```

STRATEGY
* use a framework e.g. "analyze this report by first summarizing key points, then evaluating the data, and finally suggesting improvements"
> isn't this just a user-defined system prompt? is there a separate word for that?
* discrete pieces
* ask it to ask clarifying questions to help it make better decisions
* ask to give options
* ask it to do better

---

https://simonwillison.net/2025/Jan/3/asking-them-to-write-better-code/

> Please back your claims up with specifics.

https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

* _chain of density_: broad to specific https://www.youtube.com/watch?v=9Ev208-Gc4c
* BYO your own characters https://news.ycombinator.com/item?id=42107113
