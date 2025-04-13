# ⛩️

## 参考

🗄 `src.md` secrets
🔗
* https://github.com/stars/zachvalenta/lists/ai-clients
* https://gist.github.com/zachvalenta/d3b7cd172dd2d3d8ff7340bd458c6fe2

## 进步

* _24_: lots of work to research/taxonomize tooling, start with llm and aider

# 🚃 CATEGORIES

## CLI

PROSPECTIVE
* output first, gimme impl https://austinhenley.com/blog/mirrorlang.html
* _ch_: bash https://github.com/dnmfarrell/ch https://blog.dnmfarrell.com/post/chatgpt-at-the-terminal/
* _tenere_: no context, file output (all to one file?), create Homebrew install yet https://github.com/pythops/tenere https://github.com/pythops/tenere/issues/31

LOW ADOPTION | FEATURE POOR
> BYO examples
* _chatgpt-cli_: 🎯 Markdown https://github.com/kardolus/chatgpt-cli
* _ell_: 🎯 Bash https://github.com/simonmysun/ell
* _Magic CLI_: https://github.com/guywaldman/magic-cli
* _oterm_: for Ollama https://github.com/ggozad/oterm
* _tgpt_: no API keys required https://github.com/aandrew-me/tgpt
* _zsh codex_: https://github.com/tom-doerr/zsh_codex

## GUI

* _Chatbox_: desktop app https://chatboxai.app/en
* _chat-macOS_: spotlight, Homebrew https://github.com/huggingface/chat-macOS https://news.ycombinator.com/item?id=41927624
* _DDG_: ❌ `!ai` = slightly faster REPL but loses all org functionality
* _gpt4all_: 🎯 local https://github.com/nomic-ai/gpt4all
* _janAI_: local https://jan.ai/ https://msty.app/as/janai-alternative
* _khoj_: 🎯 https://github.com/khoj-ai/khoj
* _lmstudio_: 🎯 local https://lmstudio.ai/ https://msty.app/as/lmstudio-alternative
* _msty_: 🎯 aaS and local, parallel queries https://msty.app/
* _OpenWebUI_: https://github.com/open-webui/open-webui
* _SillyTavern_: 🎯 https://github.com/SillyTavern/SillyTavern
* _TypingMind_: web app https://www.typingmind.com/ https://news.ycombinator.com/item?id=41988306

## IDE

NATIVE 🗄️ `vim.md` Zed
* _Tabby_: ❌ no traction, no mention of context awareness https://www.tabbyml.com/ https://news.ycombinator.com/item?id=42675725
* _Void_: ❌ unfinished https://voideditor.com/ https://news.ycombinator.com/item?id=41563958

EXTENSIONS https://fly.io/blog/vscode-ssh-wtf/
> I'd much, much prefer Aide to continue as a CLI tool or as a VSCode plugin. Every fork of VSCode ends up with IDE maintenance bugs that never get addressed and slowly the effort implodes as the bug surface becomes too wide. https://news.ycombinator.com/item?id=42063346
* _Avante_: ❌ Neovim https://github.com/yetone/avante.nvim https://news.ycombinator.com/item?id=41353835 https://www.youtube.com/watch?v=r-3o35-5hlg https://www.youtube.com/watch?v=4kzSV2xctjc https://www.youtube.com/watch?v=iyftGvVs86E
* _Cline_: 🎯 VSC extension https://github.com/cline/cline
* _Cody_: 🎯 https://sourcegraph.com/ https://marketplace.visualstudio.com/items?itemName=sourcegraph.cody-ai
* _Continue_: autocomplete https://ollama.com/blog/continue-code-assistant
* _Copilot_: 🎯 VSC-native, multi-model https://simonwillison.net/2024/Dec/18/free-tier-for-github-copilot/ https://www.bloomberg.com/news/articles/2024-10-29/microsoft-s-github-unit-cuts-ai-deals-with-google-anthropic
* agent requires insiders build https://github.blog/news-insights/product-news/github-copilot-the-agent-awakens/ https://www.youtube.com/watch?v=zIejF3IGtWk
* _Sage_: 💀 https://github.com/Storia-AI/sage

# 🛸 IN USE

📙 Brosseau LLMs in production https://www.manning.com/books/llms-in-production
💡️ use AI to write docs and understand the entire architecture of the system https://www.driver.ai/

locality
> export current chats first | incorporate old chats into notes and gradually rm over time
> llm only add new chats? assume so.

## context

---

https://whodb.com/docs/
https://news.ycombinator.com/item?id=43573755
https://help.openai.com/en/articles/10303002-how-does-memory-use-past-conversations

## 🟠 aichat

📜 https://github.com/sigoden/aichat

* killer feature https://github.com/sigoden/aichat#local-server-capabilities
* https://github.com/sigoden/aichat/issues/924

## ⏳🐲 aider

📜 https://aider.chat/
🗄️ `task-mgmt.md` 2024 workflow

CONFIG
* fs: `$HOME/.aider.conf.yml`
* analytics: `$HOME/.aider/analytics.json`

ZA
* 🚧 upgrade to latest version and see if that fixes bug where aider asks if you want to create a file and then errs out bc it tries to read a file it didn't create
* workflows https://aider.chat/examples/2048-game.html https://aider.chat/examples/hello-world-flask.html https://aider.chat/docs/usage/tutorials.html
* modes https://aider.chat/docs/usage/modes.html

---

* is it just the wrong design? at least for exploratory work where you don't already know how things fit together
```txt
Only add the files that need to be edited for your task. Don’t add a bunch of extra files. If you add too many files, the LLM can get overwhelmed and confused (and it costs more tokens). Aider will automatically pull in content from related files so that it can understand the rest of your code base.

You’ll get the best results if you think about which files need to be edited. Add just those files to the chat. Aider will include relevant context from the rest of your repo.
```

* disable analytics
* _codebuff_: alternative https://news.ycombinator.com/item?id=42078536

CONTEXT
* repo map https://aider.chat/docs/repomap.html#using-a-repo-map-to-provide-context
* conventions https://aider.chat/docs/usage/conventions.html https://github.com/zachvalenta/dotfiles-mini23/tree/main/ai
* Git repo history https://aider.chat/docs/faq.html#how-do-i-include-the-git-history-in-the-context

CONS
* history/input files should be dynamic https://aider.chat/docs/config/options.html#history-files https://github.com/Aider-AI/aider/issues/2684
* slow startup
* prompts (to upgrade, to create git repo)
* `.aider.conf.yml` as a filename
* are they sending usage analytics?
```json
// .aider/analytics.json
{
    "uuid": "8e79949d-d9a5-4a7d-9fe0-5392518fcda5",
    "permanently_disable": null,
    "asked_opt_in": null
}
```
* just exit already and don't make me pay for it!
```sh
exit
Goodbye! If you need further assistance, feel free to return. Have a great day!
Tokens: 2.8k sent, 19 received. Cost: $0.0073 message, $0.02 session.
```
```python
def keyboard_interrupt(self):
    self.io.tool_warning("\n\n^C again to exit")
```

## Claude Code

https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview
https://simonwillison.net/2025/Mar/9/steve-yegge/

## ⚪️ Cursor

* has Vim emulation
* people talk about Cursor and Windsurf synonymously https://ghuntley.com/oh-fuck/ https://www.youtube.com/watch?v=zIejF3IGtWk
* Zed not quite there yet? https://zed.dev/docs/assistant/inline-assistant https://stevedylan.dev/posts/leaving-neovim-for-zed/#ai-stuff https://zed.dev/docs/assistant/assistant-panel

---

https://getstream.io/blog/cursor-ai-large-projects/ file to prompt + https://news.ycombinator.com/item?id=43478199 https://simonwillison.net/2025/Mar/26/notes/

you've enabled Codeium extension auth on Github (for VS Code)
https://news.ycombinator.com/item?id=43340662
try Cline VS Code extension

Jet Brains is 6 months behind the market https://www.jetbrains.com/junie/

Data Wrangler for Jet Brains https://www.jetbrains.com/dataspell/

does Data Grip have aider-like context window but for tables? https://www.jetbrains.com/datagrip/

https://www.youtube.com/watch?v=YWwS911iLhg

CURSOR https://www.cursor.com/ https://github.com/getcursor/cursor
* jerks? https://news.ycombinator.com/item?id=37888477
* closed source VS Code fork (Chromium?)
* compared to Copilot https://www.youtube.com/watch?v=V2tv6GZuV0A

* system prompt https://docs.cursor.com/context/rules-for-ai https://ghuntley.com/stdlib/
* code completion https://www.arguingwithalgorithms.com/posts/cursor-review.html

* _Windsurf_:
* _Codeium_: 🎯 supports Neovim and VSC, more filetypes than Copilot https://codeium.com/windsurf https://zackproser.com/blog/codeium-analysis-4-2024 https://zackproser.com/blog/codeium-review https://zackproser.com/blog/chatgpt-4-and-codeium-are-my-favorite-stack https://zackproser.com/blog/codeium-vs-chatgpt

## 🎙️ chorus

https://news.ycombinator.com/item?id=42543601

## 🟢 elia

📜 https://github.com/darrenburns/elia

* API key 🗄️ `src.md` secrets https://github.com/darrenburns/elia/issues/52 https://github.com/darrenburns/elia/issues/73
> open a PR to document this
* config fs: `$HOME/.config`
* design: slow startup
* themes https://github.com/darrenburns/elia/issues/72
* available models https://github.com/darrenburns/elia/blob/main/elia_chat/config.py
* export/import: JSON https://github.com/darrenburns/elia/pull/70 https://github.com/darrenburns/elia?tab=readme-ov-file#import-from-chatgpt
> ❌ no way to do this through the UI https://chatgpt.com/c/67106b06-8884-8004-ab78-84e5bce7dea9
> how does this work under the hood? https://github.com/darrenburns/elia?tab=readme-ov-file#wiping-the-database

## ipychat

https://github.com/vinayak-mehta/ipychat/
https://github.com/shobrook/wut

## ⏳♎️ llm

📜 https://llm.datasette.io

CONFIG
* XDG: `export LLM_USER_PATH="$XDG_CONFIG_HOME/llm"` https://llm.datasette.io/en/stable/setup.html#setting-a-custom-directory-location
```sh
llm keys
llm keys set openai
```

LOGS https://llm.datasette.io/en/stable/logging.html
```sh
logs -n 10  # view
$PROMPT -n  # dont log
logs -q $QUERY  # grep
logs -m $MODEL  # logs by model
```

---

https://simonwillison.net/2025/Apr/10/llm-fragments-go/
https://mathpn.com/posts/llm-docsmith/
https://simonwillison.net/2025/Apr/11/llm-fragments-rust/
https://github.com/dtnewman/zev
https://github.com/koaning/smartfunc https://simonwillison.net/2025/Apr/3/smartfunc/ https://www.youtube.com/watch?v=j9jh46R0ryY https://simonwillison.net/2025/Apr/7/long-context-llm/ https://github.com/simonw/llm-hacker-news/issues/1 https://simonwillison.net/2025/Apr/8/llm-hacker-news/
https://www.youtube.com/watch?v=VL2TmuDJXhE

```sh
llm logs path
llm -c  # continue existing conversation
llm logs -c  # logs from existing conversation

llm plugins
llm models
llm models default
llm models default $MODEL  # set
```

ZA
* design: faster write REPL, better search, org via SQL, compare responses from diff models
* working with local models [15:00]

TTS usage https://simonwillison.net/2024/Dec/19/q-and-qv-zsh-functions/ https://retool.com/blog/air-travel-software
https://www.youtube.com/watch?v=QUXQNi6jQ30 @ 20:30

> 🎗️ opportunity to use Datasette https://www.youtube.com/watch?v=QUXQNi6jQ30 [9:00]
LLM
* guide https://simonwillison.net/2024/Jun/17/cli-language-models/
* logs https://simonwillison.net/2024/Mar/22/claude-and-chatgpt-case-study/ https://llm.datasette.io/en/stable/logging.html
* models: https://github.com/simonw/llm-mistral https://github.com/simonw/llm-claude-3 https://simonw.substack.com/p/claude-35-haiku
* working with databases locally https://simonw.substack.com/p/ask-questions-of-sqlite-databases https://github.com/Sinaptik-AI/pandas-ai
* working with audio https://simonw.substack.com/p/video-scraping-using-google-gemini https://simonw.substack.com/p/run-prompts-against-images-audio

## 💄 mods

CONFIG
```sh
Wrote config file to: /Users/zvalenta/Library/Application Support/mods/mods.yml
# ❓ was this before I set $XDG_CONFIG_HOME?
```
```sh
$ mods --settings

├── $HOME/.config/mods
│   └── mods.yml
│   └── conversations
│   └──── mods.db
```

---

* _mods_: Markdown output, system prompt https://github.com/charmbracelet/mods continue conversation https://github.com/charmbracelet/mods/issues/197

## 😺 smartcat

📜 https://github.com/efugier/smartcat

* conversations as Markdown

# 🟨️ ZA

## features

FEATURES I WANT
* Vim
* file find
* grep
* dirs
* tags
* model interop
> Users want control over which model they're running and want to be able to swap them quickly or provide their own API keys as needed to avoid limits.

CODE ASSIST https://zackproser.com/blog/cursor-review
* project context (language, deps)
* at-mention specific files (aider)
* version control integration
* niche: COBOL to Java https://bloop.ai/
* speed
> If copy and pasting back and forth between ChatGPT.com is crawling, then Cursor's interface is sprinting. Being able to discuss the code, architecture, a single file, or to tell Cursor to use a file as inspiration when making other changes is my favorite feature of Cursor.

## interchange (MCP)

* https://github.com/jlowin/fastmcp
> Put simply, MCP is a way for LLMs to more easily integrate with external tools. MCP Servers: Providers like Sentry, Slack, JIRA, Gmail, etc. set up adapters around their APIs that follow the MCP Protocol. https://read.highgrowthengineer.com/p/mcps-simply-explained
https://github.com/github/github-mcp-server
Postgres https://news.ycombinator.com/item?id=43520953
https://simonwillison.net/2025/Mar/25/playwright-mcp/
schemas https://simonwillison.net/2025/Feb/28/llm-schemas/
https://github.com/crmne/ruby_llm
https://registerspill.thorstenball.com/p/joy-and-curiosity-30 https://github.com/punkpeye/awesome-mcp-servers
https://github.com/simonw/llm/releases/tag/0.23
https://www.youtube.com/watch?v=oX6IKXfcx78

MODEL CONTEXT PROTOCOL (MCP)
* protocol to allow clients (in this case, models) to use tools (e.g. here are the queries you can run against a database) https://www.youtube.com/watch?v=oX6IKXfcx78
* impl https://pypi.org/project/mcp/
* usage https://github.com/jasonjmcghee/claude-debugs-for-you
* _MCP (model context protocol)_: spec for comms btw hosted model and data to enable RAG https://news.ycombinator.com/item?id=42237424 https://glama.ai/blog/2024-11-25-model-context-protocol-quickstart
> Today, we're open-sourcing the Model Context Protocol (MCP), a new standard for connecting AI assistants to the systems where data lives, including content repositories, business tools, and development environments. Its aim is to help frontier models produce better, more relevant responses. https://www.anthropic.com/news/model-context-protocol
> But none of the examples seem to indicate what the protocol is, whether it's a RAG sort of thing, do I need to prompt, etc.
> From what I understand, "servers" are data sources that an LLM can query at will to answer questions, using this new protocol. They're connectors to external information that the LLM can process on the fly.
> The gist of it is: you have an llm application such as Claude desktop. You want to have it interact (read or write) with some system you have. MCP solves this.
> An attempt to create a standard protocol to plug tools to LLM app via the good ol' tools/function calling mechanism. It's not introducing new capabilities, just solving the NxM problem, hopefully leading to more tools being written.

```python
import openai
openai.api_key = "your_openai_api_key"
messages = [ {"role": "user", "content": "Explain how to use Markdown to create tables."} ]
response = openai.ChatCompletion.create( model="gpt-4", messages=messages)
content = response.choices[0].message['content']
with open("response.md", "w") as f:
    f.write(content)
```

* export from GPT: navigate to data controls > export data
```python
import json
with open("conversations.json", "r") as f:
    data = json.load(f)
for conversation in data["conversations"]:
    filename = f"{conversation['title'].replace(' ', '_')}.md"
    with open(filename, "w") as md_file:
        md_file.write(f"# {conversation['title']}\n\n")
        for message in conversation["mapping"].values():
            role = message["message"]["author"]["role"]
            content = message["message"]["content"]["parts"][0]
            md_file.write(f"**{role.capitalize()}**:\n{content}\n\n")
```

> OpenAI now supports structured output, allowing developers to supply a JSON Schema, pydantic or Zod object to constrain model responses. https://www.thoughtworks.com/radar/techniques/structured-output-from-llms

https://simonwillison.net/2025/Jan/24/anthropics-new-citations-api/
https://news.ycombinator.com/item?id=42753302

* GPT code completions API https://www.youtube.com/watch?v=g9tIm50VO4g
* GPT as standard https://simonwillison.net/2024/Dec/22/openai-openapi/
* API spec
> ch works with any compatible chat completion API that has the same interface as ChatGPT https://github.com/dnmfarrell/ch
> Projects such as LocalAI offer a REST API that imitates the OpenAI API but can be used to run other models, including models that can be installed on your own machine. These can be added using the same configuration mechanism. https://llm.datasette.io/en/stable/other-models.html#openai-compatible-models
* Claude JSON export https://simonwillison.net/2024/Oct/21/claude-artifacts/ https://simonwillison.net/2024/Dec/31/llms-in-2024/#prompt-driven-app-generation-is-a-commodity-already
* _Amazon bedrock_: API for all models https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html

---

FILE FMT
https://chatgpt.com/c/671bf6dc-3058-8004-8e67-fff34d61eb1a https://chatgpt.com/c/671ebbd6-c110-8004-a519-0f723970d64c
* streaming https://til.simonwillison.net/llms/streaming-llm-apis
* _JSON_: Superpower ChatGPT, Claude https://github.com/simonw/claude-to-sqlite https://simonw.substack.com/p/everything-i-built-with-claude-artifacts https://support.anthropic.com/en/articles/9450526-how-can-i-export-my-claude-ai-data
> you've more in Elia about JSON export
* _Markdown_: https://simonw.substack.com/p/video-scraping-using-google-gemini https://github.com/kardolus/chatgpt-cli?tab=readme-ov-file#markdown-rendering
> don't forget you should be able to parse JSON to Markdown as well
* _XML_: https://github.com/simonw/files-to-prompt

browser interaction https://news.ycombinator.com/item?id=42052432 https://news.ycombinator.com/item?id=42052432
> Claude from the browser https://news.ycombinator.com/item?id=42012412
