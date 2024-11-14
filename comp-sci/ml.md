# ⛩️

## 参考

🔍
* https://ai.stackexchange.com/
* https://datascience.stackexchange.com/
📚
* Anathaswamy https://www.amazon.com/gp/product/0593185749 https://www.thediff.co/archive/longreads-open-thread-90/
* Ferguson game of go
* Perrota programming ML https://www.amazon.com/Programming-Machine-Learning-Zero-Deep/dp/1680506609/ref=sr_1_1
* Trask deep learning https://github.com/iamtrask/Grokking-Deep-Learning

## 进步

* cleanup
* boundaries: operationalizing, projects, NLP, stdlib

* _24_: usage (regex, stdlib, EDI) tooling (clients)
> using a lot, much progress -> had this in notes from before! https://realpython.com/chatgpt-coding-mentor-python/ 
* _23_: few random queries

# 🤖 CLIENTS

---

Can you give a taxonomy of $FOO in the form of a tree, like this?
```sh
├── root
│   └── nodes
│   └──── leaves
```

> sort these

NON-CLI/TUI
* DDG offers bang (`ai`), slightly faster REPL but loses all org functionality
* emacs https://github.com/karthink/gptel
* https://chatboxai.app/en

CLI/TUI
* _aichat_: 🎯 multichat https://github.com/sigoden/aichat/issues/924 https://github.com/sigoden/aichat 
* _ch_: 🎯 https://github.com/dnmfarrell/ch https://blog.dnmfarrell.com/post/chatgpt-at-the-terminal/
* _chat-macOS_: https://github.com/huggingface/chat-macOS https://news.ycombinator.com/item?id=41927624
* _chatgpt-cli_: 🎯 Markdown https://github.com/kardolus/chatgpt-cli
* _ell_: Bash https://github.com/simonmysun/ell
* _gpt4all_: local https://github.com/nomic-ai/gpt4all
* _lmstudio_: https://lmstudio.ai/
* _jan_: 🎯 https://github.com/janhq/jan
* _khoj_: 🎯 https://github.com/khoj-ai/khoj
* _llm_: 🎯 https://llm.datasette.io/en/stable/ https://datasette.io/tools/llm https://simonw.substack.com/p/video-scraping-using-google-gemini plugins for models https://github.com/simonw/llm-mistral https://github.com/simonw/llm-claude-3 https://simonw.substack.com/p/run-prompts-against-images-audio https://simonw.substack.com/p/claude-35-haiku
* _msty_: https://msty.app/
* _mods_: 🎯 Markdown output https://github.com/charmbracelet/mods
* continue conversation https://github.com/charmbracelet/mods/issues/197
* _oterm_: for Ollama https://github.com/ggozad/oterm
* _tenere_: 🎯 file output, no Homebrew install yet https://github.com/pythops/tenere https://github.com/pythops/tenere/issues/31
* _tgpt_: no API keys required https://github.com/aandrew-me/tgpt

---

## code assist

FEATURES https://zackproser.com/blog/cursor-review
* autocomplete vs. natural language
> If copy and pasting back and forth between ChatGPT.com is crawling, then Cursor's interface is sprinting. Being able to discuss the code, architecture, a single file, or to tell Cursor to use a file as inspiration when making other changes is my favorite feature of Cursor.
* model interop
> Users want control over which model they're running and want to be able to swap them quickly or provide their own API keys as needed to avoid limits.
* at-mention specific files (Aider) vs. just saying what you want done

OPTIONS 🗄️ `vim.md` zed
> retry Claude for Zed integration
* impl https://news.ycombinator.com/item?id=42078536
* _Aide_: IDE https://news.ycombinator.com/item?id=42063346
* _aider_: CLI https://aider.chat/
* _Avante_: Neovim https://github.com/yetone/avante.nvim https://news.ycombinator.com/item?id=41353835 https://www.youtube.com/watch?v=r-3o35-5hlg https://www.youtube.com/watch?v=4kzSV2xctjc https://www.youtube.com/watch?v=iyftGvVs86E
* _Cline_: https://github.com/cline/cline
* _Codeium_: https://zackproser.com/blog/codeium-analysis-4-2024 https://zackproser.com/blog/codeium-review https://zackproser.com/blog/chatgpt-4-and-codeium-are-my-favorite-stack https://zackproser.com/blog/codeium-vs-chatgpt
* _Copilot_: multi-model https://www.bloomberg.com/news/articles/2024-10-29/microsoft-s-github-unit-cuts-ai-deals-with-google-anthropic
* _Cursor_: closed source, Chromium https://www.cursor.com/
* https://news.ycombinator.com/item?id=37888477 https://github.com/getcursor/cursor https://stevedylan.dev/posts/leaving-neovim-for-zed/#vim-mode https://news.ycombinator.com/item?id=41979203 https://news.ycombinator.com/item?id=41988211 https://news.ycombinator.com/item?id=41987367
* _TypingMind_: https://news.ycombinator.com/item?id=41988306
* _Void_: https://voideditor.com/ https://news.ycombinator.com/item?id=41563958

PROJECTS
* gfold https://github.com/nickgerace/gfold/issues/261
* basilk: alphabetic sort projects, JSON output
* lazygit (option to not add dir to recently_visited) https://github.com/search?q=repo%3Ajesseduffield%2Flazygit%20recentrepos&type=code

---

https://til.simonwillison.net/clickhouse/github-public-history
https://www.thediff.co/archive/offshoring-and-ai-agents/

* https://news.ycombinator.com/item?id=41732634
> It’s worth noting that AI tools are intimately familiar with Next.js and not so much with htmx, due to the lack of open-source training data. This is similar to the issue Rails faces. While not a dealbreaker, it did impact our development speed and the ease of finding solutions to problems. When we encountered issues, the wealth of resources available for React/Next.js made troubleshooting much faster. https://htmx.org/essays/why-gumroad-didnt-choose-htmx/

https://news.ycombinator.com/item?id=41563958

* legacy codebases https://bloop.ai/ https://www.driverai.com/

https://aider.chat/ https://news.ycombinator.com/item?id=41453237
https://news.ycombinator.com/item?id=41929174&utm_term=comment

https://github.com/guywaldman/magic-cli https://news.ycombinator.com/item?id=40980715

wilder, vimgpt https://www.youtube.com/watch?v=WeulqMMJgrs

https://simonwillison.net/2024/Jul/13/give-people-something-to-link-to/

> The crux of my raging hatred is not that I hate LLMs or the generative AI craze. I had my fun with Copilot before I decided that it was making me stupider - it's impressive, but not actually suitable for anything more than churning out boilerplate. Nothing wrong with that, but it did not end up being the crazy productivity booster that I thought it would be, because programming is designing and these tools aren't good enough (yet) to assist me with this seriously. https://ludic.mataroa.blog/blog/i-will-fucking-piledrive-you-if-you-mention-ai-again/

https://github.com/leapingio/leaping
https://visualstudiomagazine.com/articles/2024/01/25/copilot-research.aspx
https://www.youtube.com/watch?v=MzFr7iXsESs
https://www.youtube.com/watch?v=dkV01hBdhZE

> LLMs are good at explaining code. Give it code in a language you don't understand and it will explain it with 90% accuracy. https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

* math: https://ollama.com/blog/wizardmath-examples
* Copilot
* Cody https://sourcegraph.com/ https://marketplace.visualstudio.com/items?itemName=sourcegraph.cody-ai
* https://stratechery.com/2024/gemini-1-5-and-googles-nature/
* https://news.ycombinator.com/item?id=37940572
* https://www.youtube.com/watch?v=MzFr7iXsESs
* https://simonwillison.net/2023/Dec/31/ai-in-2023/

## elia

ELIA 📜 https://github.com/darrenburns/elia
* config fs: `$HOME/.config`
* design: slow startup
* themes https://github.com/darrenburns/elia/issues/72
* available models https://github.com/darrenburns/elia/blob/main/elia_chat/config.py
* export/import: JSON https://github.com/darrenburns/elia/pull/70 https://github.com/darrenburns/elia?tab=readme-ov-file#import-from-chatgpt
> ❌ no way to do this through the UI https://chatgpt.com/c/67106b06-8884-8004-ab78-84e5bce7dea9
> how does this work under the hood? https://github.com/darrenburns/elia?tab=readme-ov-file#wiping-the-database

---

ELIA API KEY
> open a PR to document this
* https://github.com/darrenburns/elia/issues/52
* https://github.com/darrenburns/elia/issues/73
* 🗄️ `src.md` secrets
```txt
Say you have a CLI program that needs a secret (e.g. an API key). The secret needs to be exposed as a Linux environment variable. You don't want to store the secret in your .bash_profile because:
* you have your environment variables version controlled
* the secret would be exposed to all other programs running on your machine
```

## features

browser interaction https://news.ycombinator.com/item?id=42052432 https://news.ycombinator.com/item?id=42052432
> Claude from the browser https://news.ycombinator.com/item?id=42012412

> get API tier, try mods, export current conversations https://chatgpt.com/c/671bf6dc-3058-8004-8e67-fff34d61eb1a do you really need to export current? just incorporate into your notes and delete, leaving anything outstanding. your notes is the final downstream for everything (excluding code, music, etc.), hence LLMs are upstream. the goal with this is to 1) reduce friction re: queries 2) better...system message / prompts / RAG 3) history / stats 4) tags

FEATURES
* folders: ❓ does anyone offer? https://chatgpt.com/c/67108642-c0cc-8004-b985-28773a5764fb
* search: ❓ does anyone offer?
* export: 🗄️ Elia

FILE FMT https://chatgpt.com/c/671bf6dc-3058-8004-8e67-fff34d61eb1a https://chatgpt.com/c/671ebbd6-c110-8004-a519-0f723970d64c
* streaming https://til.simonwillison.net/llms/streaming-llm-apis
* JSON: Superpower ChatGPT, Claude https://github.com/simonw/claude-to-sqlite https://simonw.substack.com/p/everything-i-built-with-claude-artifacts https://support.anthropic.com/en/articles/9450526-how-can-i-export-my-claude-ai-data
> you've more in Elia about JSON export
* Markdown: https://simonw.substack.com/p/video-scraping-using-google-gemini
> don't forget you should be able to parse JSON to Markdown as well
* XML: https://github.com/simonw/files-to-prompt

# 🧠 MODELS

🗄️ `modeling.md` vector
📙 build LLM from scratch https://www.manning.com/books/build-a-large-language-model-from-scratch
🔍 https://a16z.com/100-gen-ai-apps-3/
🛠️ benchmark https://arena.lmsys.org/

## aaS

YES
* _ChatGPT_:  native client (global hotkey conflicts with iterm but you get search https://openai.com/chatgpt/mac/)
* web client: search added 241031 (intra-doc but slow, none by title), no tags/org/page up, dark mode is bad for seeing prompt
* _Mistral_: less polished but fast + search https://chat.mistral.ai/chat
* _Perplexity_: search/org https://www.perplexity.ai/

NO
* _Claude_: web client has search + fast input / good UI
* allegedly the best but GPT legacy model beat it and the other time I tried it admitted to fabricating data https://x.com/emollick/status/1849168452914938082 https://simonwillison.net/2024/Oct/21/claude-artifacts/ https://darioamodei.com/
> If Claude 3.5 Sonnet, the current champ of commercial LLMs for coding at this moment, failed to meet your needs in that last refactor request - you could try the exact same prompt with ChatGPT 4o in one click. https://zackproser.com/blog/cursor-review
* _Gemini_: no search/tags/org, looks low-effort https://simonw.substack.com/p/video-scraping-using-google-gemini
* _Grok_: seems tied to Twitter https://grok.x.ai/ 

---

* features: moderation, tuning to domain
* Mixtral
* Haiku

## OSS

* _Centaur_: https://x.com/marcel_binz/status/1850806691958313160
* _Gemma_: https://ai.google.dev/gemma
* _Llama_: Meta https://en.wikipedia.org/wiki/Llama_(language_model) uncensored https://ollama.com/blog/llama-3-is-not-very-censored https://ollama.com/blog/run-llama2-uncensored-locally https://joshuacook.netlify.app/posts/2024-01-31_ollama-quickstart/
* _ollama_: ⭐️ https://ollama.com/
* can run any model e.g. Qwen but might need a computer with more CPU/GPU https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can
> Ollama lets us customize an LLM through a Modelfile, which includes things like setting model parameters, system prompts etc. If we fine-tuned a model [2], it can also be loaded into Ollama by specifying our own GGUF file. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* _Qwen_: https://simonw.substack.com/p/qwen25-coder-32b-is-an-llm-that-can

---

* run locally https://github.com/getumbrel/llama-gpt
* run locally https://github.com/Mozilla-Ocho/llamafile
* running locally, llamafile https://news.ycombinator.com/item?id=40424519
* code prompt: https://ollama.com/blog/how-to-prompt-code-llama https://ollama.com/blog/run-code-llama-locally Codestral https://ollama.com/blog/continue-code-assistant

## operationalizing

🛣️ https://roadmap.sh/mlops
📙 https://www.manning.com/books/llms-in-production

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

## RAG

📚
* https://www.amazon.com/gp/product/1098150961
* build LLM apps https://www.manning.com/books/build-llm-applications-from-scratch

> Retrieval augmented generation (RAG) is an architecture that provides the most relevant and contextually-important proprietary, private or dynamic data to your Generative AI application's large language model (LLM) when it is performing tasks to enhance its accuracy and performance. https://www.pinecone.io/learn/retrieval-augmented-generation/
* howto: Python in a sidecar and then your server in another language (that lacks Python's ML stdlib) talks to that https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/

---

* BYO https://www.youtube.com/@zackproser/videos https://aws.amazon.com/bedrock/
* _RAG_: document-based interactions https://github.com/sigoden/aichat#rag-chat-with-your-documents TTS https://changelog.com/practicalai/288 https://zackproser.com/blog/how-are-embeddings-models-trained-for-rag https://www.manning.com/books/a-simple-guide-to-retrieval-augmented-generation knowledge graph https://www.manning.com/books/knowledge-graph-enhanced-rag
* when you need more than either aaS or OSS
> If such a customized LLM is a suitable solution for your project, consider just running Ollama or Llamafile and using their REST APIs to communicate with the model. If you need higher degrees of customization, read on. https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* BYO https://us.pycon.org/2024/schedule/presentation/103/index.html https://github.com/Quansight/ragna
> We’re going to build a RAG server in Go. This is an HTTP server that provides two operations to users: Add a document to the knowledge base. Ask an LLM a question about this knowledge base. https://go.dev/blog/llmpowered
> You talked a lot about this distinction between LLM benchmarks and evaluating LLM applications. Could you talk a little bit about the differences? Maybe there are software engineers in the audience, that maybe they’re used to writing unit tests and integration tests for their software. Now as a consumer, as you said, they’re integrating some LLM functionality, or maybe a chain of reasoning with LLMs into their software. From a practical standpoint, what are the new types of things that they might need to consider that are different maybe from the way that they’ve unit-tested in the past, or written tests in the past, now that they’re working with these LLM workflows? https://changelog.com/practicalai/284#transcript
> Generative AI models struggle when you ask them about facts not covered in their training data. Retrieval Augmented Generation—or RAG—enhances an LLM’s available data by adding context from an external knowledge base, so it can answer accurately about proprietary content, recent information, and even live conversations. https://www.manning.com/books/a-simple-guide-to-retrieval-augmented-generation
> Claude's extensive context window has also transformed their approach to handling large codebases. When the 200K context window was released, Hedley notes they "ripped out the entire RAG and just put it in the context window instead and it went from 60 percent accuracy to 98. It was quicker, cheaper, better, everything." This combination of automation, speed, and accuracy has fundamentally changed how Headstart approaches software development. https://www.anthropic.com/customers/headstart
* https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
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
* papers to podcasts https://www.fwdaudio.com/ https://x.com/barbell_fi
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

* _langchain_: https://zackproser.com/blog/office-oracle-overview
> We mentioned some of the emerging criticisms about LangChain in the previous Radar. Since then, we’ve become even more wary of it. While the framework offers a powerful set of features for building applications with large language models (LLMs), we’ve found it to be hard to use and overcomplicated. LangChain gained early popularity and attention in the space, which turned it into a default for many developers. However, as LangChain is trying to evolve and keep up with the fast pace of change, it has become harder and harder to navigate those changes of concepts and patterns as a developer. We’ve also found the API design to be inconsistent and verbose. As such, it often obscures what is actually going on under the hood, making it hard for developers to understand and control how LLMs and the various patterns around them actually work. We’re moving LangChain to the Hold ring to reflect this. In many of our use cases, we’ve found that an implementation with minimum use of specialized frameworks is sufficient. Depending on your use case, you may also want to consider other frameworks such as Semantic Kernel, Haystack or LiteLLM.  https://www.thoughtworks.com/radar/languages-and-frameworks/langchain

# 🏗️ USAGE

---

ZA
* text to SQL https://github.com/vanna-ai/vanna
* to synthesize all comments on a product into a blurb https://blog.untrod.com/2024/04/llm-chatgpt-powered-django-admin-fields.html
* copyedit a novel https://blog.untrod.com/2023/06/copy-editing-a-novel-with-chatgpt.html
* detection https://deepmind.google/technologies/synthid/?utm_source=www.superpowerdaily.com&utm_medium=newsletter&utm_campaign=new-claude-ai-can-take-over-your-computer

https://platform.openai.com/docs/overview https://cookbook.openai.com/

## audio

TYPES https://elevenlabs.io/
* dubbing
* voice clone
* _TTS_: https://notebooklm.google/ https://news.ycombinator.com/item?id=41964980 multistage https://simonw.substack.com/p/verdad-tracking-misinformation-in
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

## img

* image to video https://www.vidifyapp.com/
* _OCR_: image to text e.g. PDF to plaintext https://en.wikipedia.org/wiki/Optical_character_recognition https://news.ycombinator.com/item?id=41048194 https://getomni.ai/ocr-demo https://news.ycombinator.com/item?id=41971614 https://github.com/Nutlope/llama-ocr

---

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

## cleanup

GREAT ANSWERS
* computer eng https://chatgpt.com/c/671121b1-633c-8004-88ee-bcc142ac24f5
* Python packaging history https://chatgpt.com/c/67111dbc-0964-8004-9e50-41fa41875da8

---

https://www.apricitas.io/archive https://github.com/zillow/luminaire https://github.com/zillow/fair-housing-guardrail
https://forklightning.substack.com/
https://treyhunner.com/2024/07/chatgpt-and-claude-from-your-browser-url-bar/
building into projects https://news.ycombinator.com/item?id=40857589

ZA
* structured output https://news.ycombinator.com/item?id=40713952
* Claude https://www.anthropic.com/ https://x.com/AnthropicAI/status/1803790681971859473
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
* _agent_: give it a dataset, it writes the paper https://www.oneusefulthing.org/p/almost-an-agent-what-gpts-can-do
* respond to social pressure https://twitter.com/AndrewCurran_/status/1720177766283505724
* use to study math https://news.ycombinator.com/item?id=37963453
* pretty transparent https://twitter.com/zoink/status/1599281052115034113
* tooling https://github.com/eth-sri/lmql
* _constitution_: heuristic for LLM https://www.anthropic.com/index/claudes-constitution
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

* legal https://pycon-archive.python.org/2024/schedule/presentation/7/index.html
* contextual search 🗄️ `info.md` search https://jnnnthnn.com/how-to-build-your-own-perplexity-for-any-dataset https://www.perplexity.ai/
* BYO https://medium.com/@msouza.os/llm-from-scratch-with-pytorch-9f21808c6319 https://youtu.be/kCc8FmEb1nY
* learn from Simon https://news.ycombinator.com/item?id=41624759 and Ilya https://tensorlabbet.com/
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
* _VGA (visual question answering)_: answer open-ended question about image https://victorzhou.com/blog/easy-vqa/
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

SCIKIT
* https://calmcode.io/labs/scikit-partial

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
* clean up https://nostarch.com/NLPPython https://codewords.recurse.com/issues/seven/data-driven-literary-analysis https://www.fast.ai/2019/07/08/fastai-nlp/ https://speakerdeck.com/pycon2015/adam-palay-words-words-words-reading-shakespeare-with-python https://victorzhou.com/blog/better-profanity-detection-with-scikit-learn/
* word2vec, byte-pair encoding, LSTM https://arpit.substack.com/p/how-zomato-improved-its-search-using https://www.freecodecamp.org/learn/machine-learning-with-python/how-neural-networks-work/recurrent-neural-networks-rnn-and-long-short-term-memory-lstm 
* https://github.com/rspeer/wordfreq

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

## prompts

📙 https://www.manning.com/books/prompt-engineering-in-practice
🗄️
* `psychology.md` interviewing
* `work.md` industry > Stack Overflow

* discrete pieces
* ask it to ask clarifying questions to help it make better decisions
* use a framework
> analyze this report by first summarizing key points, then evaluating the data, and finally suggesting improvements
* when working with documents, ask it to extract the relevant quotes
* ask to give options
* ask it to do better
```txt
Can you analyze a book for me: $BOOK
By first summarizing key points in a succinct and logical way i.e. I care most about the claims made by the author and how they are logically supported (or not).
And then summarizing criticism of the book (positive or negative) in a similar manner.
```

---

https://katherinemichel.github.io/portfolio/pycon-us-2024-recap.html#simon-willison-keynote

SEMANTICS
* _prompt engineering_: asking specific questions https://marginalrevolution.com/marginalrevolution/2023/05/how-to-use-gpt-4-plus-web-browsing.html https://www.youtube.com/watch?v=hB7sGE0W8CI
* _prompt injection_: getting model to do something its creators don't want
* _system message_: hidden instruction that defines the behavior/goals/tone of the model; aka system prompt https://chatgpt.com/c/67106e28-a6e0-8004-9ef0-dd2f3b1eb48b
* BYO your own characters https://news.ycombinator.com/item?id=42107113
> "You are a helpful assistant named Elia."

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
