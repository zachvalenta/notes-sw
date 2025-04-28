# ⛩️

## 参考

🔍 https://github.com/stars/zachvalenta/lists/ai
🗄 `src.md` secrets https://gist.github.com/zachvalenta/d3b7cd172dd2d3d8ff7340bd458c6fe2

## 进步

* _25_: start agentic
* _24_: lots of work to research/taxonomize tooling, start with llm and aider

TOP OF MIND
* try Codex https://www.youtube.com/watch?v=FUq9qRwrDrI https://help.openai.com/en/articles/11096431-openai-codex-cli-getting-started
* use llm better https://simonwillison.net/2025/Apr/23/llm-fragment-symbex/
* copilot https://simonwillison.net/2024/Dec/18/free-tier-for-github-copilot/ https://www.youtube.com/watch?v=dutyOc_cAEU https://www.youtube.com/watch?v=hyhZKRAQdLs
* voice notes to self https://simonwillison.net/2025/Apr/23/diane/ https://whispermemos.com/
* https://news.ycombinator.com/item?id=43739456 https://github.com/The-Pocket/Tutorial-Codebase-Knowledge

# 🪚 IN USE

ALTERNATIVES
* niche: COBOL to Java https://bloop.ai/
* _plandex_: 🎯 multi-model https://plandex.ai/ https://github.com/plandex-ai/plandex
* _aichat_: https://github.com/sigoden/aichat context / RAG https://github.com/sigoden/aichat?tab=readme-ov-file#rag multimodel https://github.com/sigoden/aichat?tab=readme-ov-file#llm-arena ChatGPT API tiers https://github.com/sigoden/aichat/issues/924
* _ipychat_: https://github.com/vinayak-mehta/ipychat/ https://github.com/shobrook/wut
* _codebuff_: https://news.ycombinator.com/item?id=42078536
* _aider_: https://aider.chat/
* fs: `$HOME/.aider.conf.yml`
* analytics: `$HOME/.aider/analytics.json`
* workflows https://aider.chat/examples/2048-game.html https://aider.chat/examples/hello-world-flask.html https://aider.chat/docs/usage/tutorials.html
* modes https://aider.chat/docs/usage/modes.html
* repo map https://aider.chat/docs/repomap.html#using-a-repo-map-to-provide-context
* conventions https://aider.chat/docs/usage/conventions.html https://github.com/zachvalenta/dotfiles-mini23/tree/main/ai
* Git repo history https://aider.chat/docs/faq.html#how-do-i-include-the-git-history-in-the-context
* problems: lack of autocomplete to add files, slow startup, slow exit, analytics, input file scope https://aider.chat/docs/config/options.html#history-files https://github.com/Aider-AI/aider/issues/2684
```python
def keyboard_interrupt(self):
    self.io.tool_warning("\n\n^C again to exit")
```

## 🟫 Claude Code

📜 https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview

* Vim https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview#vim-mode
* multi-line: `OPTION ENTER`
* tips https://news.ycombinator.com/item?id=43735550 https://www.anthropic.com/engineering/claude-code-best-practices https://simonwillison.net/2025/Apr/19/claude-code-best-practices/ https://cookbook.openai.com/examples/gpt4-1_prompting_guide
* woodchipper https://simonwillison.net/2025/Mar/9/steve-yegge/
* can install w/ bun https://github.com/anthropics/claude-code/issues/124 https://github.com/zachvalenta/logs-mini23/commit/5780344c5900878bc15af666a63732405f9a4f06
```sh
bun install -g @anthropic-ai/claude-code
```

## ☸️ Codex

* impl: `sandbox-exec` https://simonwillison.net/2025/Apr/16/openai-codex/
* https://news.ycombinator.com/item?id=43708025

## ♎️ llm

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

* files-to-prompt https://simonwillison.net/2025/Mar/26/notes/ https://simonwillison.net/2025/Apr/14/llms-as-the-first-line-of-support/
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

llm plugins  # working with UV https://github.com/joshuadavidthomas/llm-uv-tool
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

# 🚃 CATEGORIES

## db

🗄️ `sql.md` schema > approaches
> Nothing is yet one is data-aware (only schema-aware), so the important thing is a good REPL + related db GUI/TUI features. You can just pipe in schema to tool

* schema-aware: DataGrip, DataSpell https://whodb.clidey.com/docs/
* natural language queries: https://github.com/sqlchat/sqlchat https://whodb.clidey.com/docs/usage-houdini/what-is-houdini
* un-aware: litecli

## CLI

💄 MODS
* Markdown output, system prompt https://github.com/charmbracelet/mods
* continue conversation https://github.com/charmbracelet/mods/issues/197
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

🟢 ELIA https://github.com/darrenburns/elia
* API key 🗄️ `src.md` secrets https://github.com/darrenburns/elia/issues/52 https://github.com/darrenburns/elia/issues/73
> open a PR to document this
* config fs: `$HOME/.config`
* design: slow startup
* themes https://github.com/darrenburns/elia/issues/72
* available models https://github.com/darrenburns/elia/blob/main/elia_chat/config.py
* export/import: JSON https://github.com/darrenburns/elia/pull/70 https://github.com/darrenburns/elia?tab=readme-ov-file#import-from-chatgpt
> ❌ no way to do this through the UI https://chatgpt.com/c/67106b06-8884-8004-ab78-84e5bce7dea9
> how does this work under the hood? https://github.com/darrenburns/elia?tab=readme-ov-file#wiping-the-database

PROSPECTIVE
* output first, gimme impl https://austinhenley.com/blog/mirrorlang.html
* _smartcat_: 🎯 conversations as Markdown https://github.com/efugier/smartcat
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

## extensions

EXTENSIONS https://fly.io/blog/vscode-ssh-wtf/
> I'd much, much prefer Aide to continue as a CLI tool or as a VSCode plugin. Every fork of VSCode ends up with IDE maintenance bugs that never get addressed and slowly the effort implodes as the bug surface becomes too wide. https://news.ycombinator.com/item?id=42063346
* _Avante_: ❌ Neovim https://github.com/yetone/avante.nvim https://news.ycombinator.com/item?id=41353835 https://www.youtube.com/watch?v=r-3o35-5hlg https://www.youtube.com/watch?v=4kzSV2xctjc https://www.youtube.com/watch?v=iyftGvVs86E
* _Cline_: 🎯 VSC extension https://github.com/cline/cline
* _Cody_: 🎯 https://sourcegraph.com/ https://marketplace.visualstudio.com/items?itemName=sourcegraph.cody-ai
* _Continue_: autocomplete https://ollama.com/blog/continue-code-assistant
* _Copilot_: 🎯 VSC-native, multi-model https://simonwillison.net/2024/Dec/18/free-tier-for-github-copilot/
* agent requires insiders build https://github.blog/news-insights/product-news/github-copilot-the-agent-awakens/ https://www.youtube.com/watch?v=zIejF3IGtWk
* _Sage_: 💀 https://github.com/Storia-AI/sage

## GUI

* _Chatbox_: desktop app https://chatboxai.app/en
* _chat-macOS_: spotlight, Homebrew https://github.com/huggingface/chat-macOS https://news.ycombinator.com/item?id=41927624
* _chorus_: 🎯 multimodel https://news.ycombinator.com/item?id=42543601
* _DDG_: ❌ `!ai` = slightly faster REPL but loses all org functionality
* _gpt4all_: 🎯 local https://github.com/nomic-ai/gpt4all
* _janAI_: local https://jan.ai/ https://msty.app/as/janai-alternative
* _khoj_: 🎯 https://github.com/khoj-ai/khoj
* _lmstudio_: 🎯 local https://lmstudio.ai/ https://msty.app/as/lmstudio-alternative
* _msty_: 🎯 aaS and local, parallel queries https://msty.app/
* _OpenWebUI_: https://github.com/open-webui/open-webui
* _SillyTavern_: 🎯 https://github.com/SillyTavern/SillyTavern
* _TypingMind_: web app https://www.typingmind.com/ https://news.ycombinator.com/item?id=41988306

## IDE (Cursor)

CURSOR https://www.cursor.com/ https://github.com/getcursor/cursor
* has Vim emulation
* people talk about Cursor and Windsurf synonymously https://ghuntley.com/oh-fuck/ https://www.youtube.com/watch?v=zIejF3IGtWk
* jerks? https://news.ycombinator.com/item?id=37888477
* closed source VS Code fork (Chromium?)
* pricing https://news.ycombinator.com/item?id=43755321

ALTERNATIVES
* _Github copilot_: compared to Cursor https://www.youtube.com/watch?v=V2tv6GZuV0A
* _Windsurf_: 🎯 https://blog.val.town/blog/fast-follow/
* _Codeium_: 🎯 supports Neovim and VSC, more filetypes than Copilot https://codeium.com/windsurf https://zackproser.com/blog/codeium-analysis-4-2024 https://zackproser.com/blog/codeium-review https://zackproser.com/blog/chatgpt-4-and-codeium-are-my-favorite-stack https://zackproser.com/blog/codeium-vs-chatgpt
* you've enabled Codeium extension auth on Github (for VS Code)
* _Jetbrains junie_: https://www.jetbrains.com/junie/
* _Tabby_: ❌ no traction, no mention of context awareness https://www.tabbyml.com/ https://news.ycombinator.com/item?id=42675725
* _Void_: ❌ unfinished https://voideditor.com/ https://news.ycombinator.com/item?id=41563958
* _Zed_: not quite there yet? https://zed.dev/docs/assistant/inline-assistant https://stevedylan.dev/posts/leaving-neovim-for-zed/#ai-stuff https://zed.dev/docs/assistant/assistant-panel 🗄️ `vim.md` Zed
