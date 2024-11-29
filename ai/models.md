# ⛩️

## 参考

🛣️ https://roadmap.sh/mlops
📚
* Huyen designing ml systems https://www.amazon.com/dp/1098107969
* https://www.amazon.com/Machine-Learning-System-Design-Interview/dp/1736049127
* https://www.amazon.com/Generative-AI-System-Design-Interview/dp/1736049143
* https://www.amazon.com/dp/1098149246

## 进步

# 🥗 MENU

🛠️ benchmark https://arena.lmsys.org/

## closed

* _Amazon nova_: https://news.ycombinator.com/item?id=42309121 https://news.ycombinator.com/item?id=42309121 https://simonwillison.net/2024/Dec/4/amazon-nova/
* _Anthropic claude_: 🎯 web client has search + fast input / good UI
* allegedly the best but GPT legacy model beat it and the other time I tried it admitted to fabricating data https://x.com/emollick/status/1849168452914938082 https://simonwillison.net/2024/Oct/21/claude-artifacts/ https://darioamodei.com/
* Haiku, Opus https://www.youtube.com/watch?v=QUXQNi6jQ30 [5:30]
> If Claude 3.5 Sonnet, the current champ of commercial LLMs for coding at this moment, failed to meet your needs in that last refactor request - you could try the exact same prompt with ChatGPT 4o in one click. https://zackproser.com/blog/cursor-review
* backed by Amazon https://news.ycombinator.com/item?id=42215126
* _Google Gemini_: no search/tags/org, looks low-effort https://simonw.substack.com/p/video-scraping-using-google-gemini
* _Mistral codestral_: less polished but fast + search https://chat.mistral.ai/chat
* _OpenAI chatgpt_: ✅ 22.11 GPT 23.03 GPT4 24.05 GPT4o 24.09 o1-preview 24.12 pro https://x.com/mckaywrigley/status/1865089975802646857 https://community.openai.com/t/chatgpt-recommends-the-use-of-the-open-ai-internal-library-ace-tools/852665 https://news.ycombinator.com/item?id=42330732
* _Perplexity api_: search/org https://www.perplexity.ai/
* Mixtral https://mistral.ai/news/mixtral-of-experts/
* _X grok_: seems tied to Twitter https://grok.x.ai/ 

---

* YiCoder: https://news.ycombinator.com/item?id=41453237
* features: moderation, tuning to domain
* Haiku
* Genie https://news.ycombinator.com/item?id=42317903

## open

🗄️ `hw.md` Apple 

HARDWARE https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can
> 🎗️ llamafile https://simonwillison.net/2024/Jun/17/cli-language-models/ https://simonwillison.net/2023/Nov/29/llamafile/ "this should be technically impossible" (having a single unmodified binary run across mac/Windows/linux) https://www.youtube.com/watch?v=QUXQNi6jQ30 [20:00] inference https://github.com/samuel-vitorino/lm.rs https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a
* mini23 uses 8B just w/ VS Code + browser + macOS core services
* Qwen req 32B
* Simon has 64B

MODELS https://simonwillison.net/2024/Jun/17/cli-language-models/
* _Codestral_: https://ollama.com/blog/continue-code-assistant
* _Centaur_: https://x.com/marcel_binz/status/1850806691958313160
* _Gemma_: https://ai.google.dev/gemma
* _jan_: 🎯 https://github.com/janhq/jan
* _Meta llama_: https://x.com/rowancheung/status/1865107700087980170 https://en.wikipedia.org/wiki/Llama_(language_model) uncensored https://ollama.com/blog/llama-3-is-not-very-censored https://ollama.com/blog/run-llama2-uncensored-locally https://joshuacook.netlify.app/posts/2024-01-31_ollama-quickstart/
* ccmake https://news.ycombinator.com/item?id=42274489
* _ollama_: ⭐️ https://ollama.com/
> customize through a Modelfile, incl model parameters, system prompts etc. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* multimodal, OCR https://ollama.com/blog/llama3.2-vision
* _Qwen_: https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can

---

* run locally https://github.com/getumbrel/llama-gpt
* run locally https://github.com/Mozilla-Ocho/llamafile
* running locally, llamafile https://news.ycombinator.com/item?id=40424519
* code prompt: https://ollama.com/blog/how-to-prompt-code-llama https://ollama.com/blog/run-code-llama-locally

# 🏗️ OPERATIONALIZE

* testing https://news.ycombinator.com/item?id=42317878 https://news.ycombinator.com/item?id=42330666
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

## agents

---

https://www.thediff.co/archive/offshoring-and-ai-agents/
https://github.com/ishan0102/vimGPT
* _agent_: give it a dataset, it writes the paper https://www.oneusefulthing.org/p/almost-an-agent-what-gpts-can-do
https://edwardbenson.com/2024/06/how-to-reason-about-agent-performance#user-content-fn-1
https://edwardbenson.com/2024/11/the-worlds-first-ai-street-hawker
https://edwardbenson.com/lollm
https://news.ycombinator.com/item?id=42299098
https://x.com/SullyOmarr/status/1864697992261062690/photo/1

## RAG

🗄️
* `doc.md` notes
* `algos.md` search > bm25
📚
* https://www.amazon.com/gp/product/1098150961
* build LLM apps https://www.manning.com/books/build-llm-applications-from-scratch

* BYO https://github.com/bhavnicksm/chonkie https://github.com/explosion/spacy-layout https://training.talkpython.fm/courses/getting-started-with-spacy https://github.com/DS4SD/docling https://x.com/_inesmontani
> I said earlier that building an LLM was still out of reach of hobbyists. That may be true for training from scratch, but fine-tuning one of those models is another matter entirely.  There’s now a fascinating ecosystem of people training their own models on top of these foundations, publishing those models, building fine-tuning datasets and sharing those too. The Hugging Face Open LLM Leaderboard is one place that tracks these. I can’t even attempt to count them, and any count would be out-of-date within a few hours. https://simonwillison.net/2023/Dec/31/ai-in-2023/ more on Hugging Face https://chatgpt.com/c/6750c201-f928-8004-b614-fb258458167a
* howto: Python in a sidecar and then your server in another language (that lacks Python's ML stdlib) talks to that https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/

---

START HERE 🗄️ `algos.md` neural networks
https://github.com/Shubhamsaboo/awesome-llm-apps https://www.theunwindai.com/p/build-a-personal-health-and-fitness-ai-agent-using-google-gemini
* https://www.youtube.com/watch?v=PJaqp5Kdwz0
* https://github.com/pingcap/autoflow https://github.com/stanfordnlp/dspy
* https://news.ycombinator.com/item?id=42174829
* https://haystack.deepset.ai/overview/quick-start https://www.youtube.com/watch?v=6aYclVrsqu0 https://www.youtube.com/watch?v=KYxlM0hh96o
* https://github.com/D-Star-AI/dsRAG/
* https://github.com/snexus/llm-search
* https://arcturus-labs.com/blog/2024/11/21/roaming-rag--make-_the-model_-find-the-answers/

* https://openai.com/12-days/
* _Guru_: https://www.getguru.com/
> Retrieval augmented generation (RAG) is an architecture that provides the most relevant and contextually-important proprietary, private or dynamic data to your Generative AI application's large language model (LLM) when it is performing tasks to enhance its accuracy and performance. https://www.pinecone.io/learn/retrieval-augmented-generation/
* BYO https://www.youtube.com/@zackproser/videos https://aws.amazon.com/bedrock/
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
* train on your own emails https://github.com/zycyc/LAMBDA
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

> https://langfuse.com/ https://www.thoughtworks.com/radar/platforms/langfuse

* _langchain_: https://zackproser.com/blog/office-oracle-overview https://www.amazon.com/dp/1835083463
> We mentioned some of the emerging criticisms about LangChain in the previous Radar. Since then, we’ve become even more wary of it. While the framework offers a powerful set of features for building applications with large language models (LLMs), we’ve found it to be hard to use and overcomplicated. LangChain gained early popularity and attention in the space, which turned it into a default for many developers. However, as LangChain is trying to evolve and keep up with the fast pace of change, it has become harder and harder to navigate those changes of concepts and patterns as a developer. We’ve also found the API design to be inconsistent and verbose. As such, it often obscures what is actually going on under the hood, making it hard for developers to understand and control how LLMs and the various patterns around them actually work. We’re moving LangChain to the Hold ring to reflect this. In many of our use cases, we’ve found that an implementation with minimum use of specialized frameworks is sufficient. Depending on your use case, you may also want to consider other frameworks such as Semantic Kernel, Haystack or LiteLLM.  https://www.thoughtworks.com/radar/languages-and-frameworks/langchain

## train

📙 Brosseau LLMs in production https://www.manning.com/books/llms-in-production
https://changelog.com/practicalai/295

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

TYPES https://elevenlabs.io/
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

## img

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
* Stable Diffusion
* https://news.ycombinator.com/item?id=40437641
* https://github.com/orhun/menyoki

## projects

* algos https://github.com/ritchie46/vanilla-machine-learning https://www.manning.com/books/optimization-algorithms
* Iris dataset https://www.youtube.com/results?search_query=iris+dataset https://docs.pola.rs/user-guide/misc/visualization/#altair
* get familiar https://simonwillison.net/2024/Apr/17/ai-for-data-journalism/
* https://www.freecodecamp.org/news/customer-segmentation-python-machine-learning/
* https://archive.vn/073bS
* https://news.ycombinator.com/item?id=40877136
* train model on dickens, cowen
* https://www.freecodecamp.org/learn/machine-learning-with-python/machine-learning-with-python-projects/book-recommendation-engine-using-knn

# 🟨️ ZA

## prompts

📙 https://www.manning.com/books/prompt-engineering-in-practice
🗄️
* `psychology.md` interviewing
* `work.md` industry > Stack Overflow

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

https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

SEMANTICS
* _prompt engineering_: asking specific questions https://marginalrevolution.com/marginalrevolution/2023/05/how-to-use-gpt-4-plus-web-browsing.html https://www.youtube.com/watch?v=hB7sGE0W8CI
* _prompt injection_: getting model to do something its creators don't want https://simonwillison.net/2023/Dec/31/ai-in-2023/
* _system message_: hidden instruction that defines the behavior/goals/tone of the model; aka system prompt https://chatgpt.com/c/67106e28-a6e0-8004-9ef0-dd2f3b1eb48b
* _chain of density_: broad to specific https://www.youtube.com/watch?v=9Ev208-Gc4c
* BYO your own characters https://news.ycombinator.com/item?id=42107113
> "You are a helpful assistant named Elia."
