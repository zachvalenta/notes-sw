# ⛩️

## 参考

📜 
* Neovim https://neovim.io/doc/user/usr_01.html https://github.com/neovim/neovim
* Vim https://vimhelp.org/usr_toc.txt.html https://www.vim.org/docs.php
🔍
* https://vi.stackexchange.com/
* https://stackoverflow.com/questions/tagged/vim
* notation 📙 Neil practical [xx]
📚
* Neil modern
* Neil practical vim
* Robbins learning vim

## 进步

sketch out what you still remember of your previous config and then restart https://www.youtube.com/@teej_dv/videos

* markdown https://www.youtube.com/watch?v=1Lmyh0YRH-w
* config https://github.com/jdhao/nvim-config
https://www.youtube.com/watch?v=6pAG3BHurdM
https://www.youtube.com/watch?v=VljhZ0e9zGE
https://www.youtube.com/watch?v=Qf9gfx7gWEY
https://www.youtube.com/watch?v=bb3UqIzd7L0
https://github.com/folke/snacks.nvim https://www.youtube.com/watch?v=rc3LMw4QCec

* VS Code plugins: indentation rainbow, bookmarks, project manager https://switowski.com/blog/plugins-for-python-in-vscode/
https://www.youtube.com/watch?v=VljhZ0e9zGE
https://www.youtube.com/watch?v=oo_I5lAmdi0
https://news.ycombinator.com/item?id=41637286
note-taking in Markdown https://www.youtube.com/watch?v=DgKI4hZ4EEI
basic setup https://www.youtube.com/watch?v=VljhZ0e9zGE
https://www.youtube.com/watch?v=zHTeCSVAFNY
https://stevedylan.dev/posts/leaving-neovim-for-zed/
* Codi

* _24_: try Zed
* _23_: try mv to Neovim, stuck on global search and LSP 📙 Neil practical (6-7, 9) 📙 Neil modern (2-3, 6-7) + visual block mode, buffers/windows/sessions/workspaces, config, vim-plug, Telescope (basics, workspaces, select_tab_drop), augroups for Markdown syntax highlighting for color scheme https://github.com/zachvalenta/dotfiles-air22/blob/main/vim/user/markdown_fmt.lua, plugins (highlight cursorword and scope, autoclose pairs, treesitter, aerial, barbar)
* _22_: built-in pkg mgmt
* _20_: VS Code (Markdown extensions break, pinned to 1.41 since 20.12.17)
* _19_: VS Code + vim emulation 📙 Neil practical vim 1.1-3, 2.7-9, 3.13-15, 4.20-22, 5.27-28, 8.47-53, 9.56-57, 10.60-62
* _18_: IntelliJ, PyCharm
* _17_: Eclipse
* _15_: Sublime

---

LSP
* https://www.youtube.com/watch?v=puWgHa7k3SY
* https://www.youtube.com/watch?v=Ku-m7eEbWas
* https://www.youtube.com/watch?v=C9X5VF9ASac
* https://www.youtube.com/watch?v=190HoB0pVro

FUZZY SEARCH HEADER GLOBALLY (CMD T) https://vi.stackexchange.com/q/42870/35177
* ❌ src `lsp.lua` breaks aerial (`no symbols`)
* ❌ Telescope: `lsp_workspace_symbols` err `no client attached` if no buffer open
* ❌ lsp-zero: imports not resolved
* ❌ lsp-zero - keybindings: `K` no info `gd/gD` no response `gi` unsupported
> The common convention here is to setup these keybindings only when you have a language server active in the current file. https://github.com/VonHeikemen/lsp-zero.nvim/blob/v3.x/doc/md/lsp.md#creating-new-keybindings
* Neovim LSP: `:lua =vim.lsp.get_clients()` throws err https://neovim.io/doc/user/lsp.html
- [ ] different language servers
- [ ] lsp-zero: reread docs
- [ ] primeagen config https://github.com/VonHeikemen/lsp-zero.nvim/blob/v3.x/doc/md/configuration-templates.md#primes-config
- [ ] Telescope config
- [ ] lsp-zero config

FEATURE PARITY - DOMAIN NOTES
> move to mini23 and figure out later bc despite meh vsc theme neovim also has meh theme + broken functionality (sidebar, LSP for Markdown navigation)
* ✅ workspace: Telescope
* ✅ fuzzy search file (CMD p): Telescope
* ✅ grep all files (CMD CTRL f): Telescope
* ✅ switch btw buffers (CMD $NUM): barbar
* ❌ fuzzy search header globally (CMD t): Telescope
* fuzzy search header w/in file (CMD r): Telescope
* reopen previous buffer (CMD SHIFT t): barbar
* ⏳ Markdown color scheme
* ❌ minimap
* ❌ sidebar

FUZZY SEARCH HEADER W/IN FILE (`CMD R`)
* Telescope https://github.com/crispgm/telescope-heading.nvim
* https://www.reddit.com/r/neovim/comments/pdiflv/search_workspace_symbols/
* https://github.com/SmiteshP/nvim-navbuddy

TELESCOPE
* search history, code intel, wrap text in preview, limit results in buffers by using rg instead of fd https://github.com/nvim-telescope/telescope.nvim/issues/2044 https://www.youtube.com/watch?v=OhnLevLpGB4 https://github.com/LunarVim/Neovim-from-scratch  https://www.youtube.com/watch?v=indguFY7wJ0
* `buffers` (goto open buffer) `current_buffer_fuzzy_find` (search w/in current buffer) `colorscheme` (switch colorsheme) `oldfiles` (previously opened) `command_history` (previously run Vim cmd) https://github.com/bhalash/dotfiles/blob/cc67fc358744832ef0a04552b853113d158a9a53/vim/plugin/30.telescope.lua#L29
> I keep inadvertently exiting bc I'm used to pressing escape multiple times

ZA
* which-key
* tree
* dashboard: both have catppuccin integrations https://github.com/goolord/alpha-nvim https://github.com/nvimdev/dashboard-nvim https://github.com/mhinz/vim-startify https://www.youtube.com/watch?v=9IcXJvoPHCY https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-starter.md
* Markdown https://github.com/lukas-reineke/headlines.nvim https://arnaudr.io/2020/08/17/modify-vim-syntax-files-for-your-taste/ https://github.com/preservim/vim-markdown https://vimtricks.com/p/vertical-alignment/ https://www.youtube.com/watch?v=XdDUGAePASA http://vimcasts.org/episodes/aligning-text-with-tabular-vim/ exec code blocks https://news.ycombinator.com/item?id=41954254#41979534 https://github.com/gpanders/vim-medieval
* databases https://github.com/tpope/vim-dadbod https://github.com/tpope/vim-dadbod https://github.com/kndndrj/nvim-dbee
* replace vimv https://github.com/stevearc/oil.nvim
* `H/M/L`

# 🦚 ALTERNATIVES

* https://news.ycombinator.com/item?id=42447012
* _dte_: https://github.com/craigbarnes/dte
* _kibi_: https://github.com/ilai-deutel/kibi

## design

> port in from Zed
* document outline: VSC has a long-standing bug where Markdown outlines get wiped and then only rerender on further editing
> which makes file pin useless
* LSP
* plugin mgmt
* modal https://marketplace.visualstudio.com/items?itemName=wmaurer.vscode-jumpy
* _soft wrap_: wrap real line to look like multiple lines https://www.youtube.com/watch?v=5WLlLxU2EZE [10:45]
* syntax highlighting: VSC can't highlight TOML
* terminal integration

HISTORY
* stone age: no screen = teletype
* 1969: ed https://begriffs.com/posts/2019-07-19-history-use-vim.html
* 1976: vi, Emacs
* 1991: Vim https://twobithistory.org/2018/08/05/where-vim-came-from.html https://begriffs.com/posts/2019-07-19-history-use-vim.html
* 2006: Vim 7.0
* 2013: Vim 8.0 📙 PV [5.27]
* 2015: Neovim
* 2020s: Zed, Helix https://helix-editor.com/ Helix matcher https://github.com/alexpasmantier/television https://news.ycombinator.com/item?id=33147270 https://www.youtube.com/watch?v=tGYvUXYN-c0 Kakoune https://www.youtube.com/watch?v=5WLlLxU2EZE https://www.youtube.com/watch?v=5WLlLxU2EZE Amp https://amp.rs/
> select + action and space mode makes me think helix is worth learning https://www.youtube.com/watch?v=xHebvTGOdH8 https://www.youtube.com/watch?v=5WLlLxU2EZE
> https://anvil-editor.net/ http://acme.cat-v.org/ https://news.ycombinator.com/item?id=41923018

## Emacs

🗄️ `doc.md` notes > tooling > Org Mode

* AI client https://github.com/karthink/gptel
* https://entropicthoughts.com/why-you-should-buy-into-the-emacs-platform
* https://www.youtube.com/@SystemCrafters/videos
* https://lwn.net/Articles/832429/
* https://two-wrongs.com/why-you-should-buy-into-the-emacs-platform
* https://two-wrongs.com/on-escape-meta-alt-control-shift-emacs.html
* https://github.com/hlissner/doom-emacs https://news.ycombinator.com/item?id=34967802
* https://www.murilopereira.com/a-rabbit-hole-full-of-lisp/
* https://www.murilopereira.com/whats-good-about-staying-inside-emacs/
* https://www.murilopereira.com/emacs-from-catching-up-to-getting-ahead/
* https://www.murilopereira.com/the-values-of-emacs-the-neovim-revolution-and-the-vscode-gorilla/
* https://www.thediff.co/archive/building-for-power-users/

## Jetbrains

* _find action (god command)_: CMD SHIFT a
* _problems_: sometimes doesn't display *any* directories properly and you need to close IDE and blow away `.idea` dir and restart IDE, ignore dir in search is flaky
* _keymap schemes_: macOS (what the keymap reference PDF shows) OS-agnostic (what you'd be used to if you use other JetBrains IDEs)
* _sink_: https://github.com/JetBrains/awesome-pycharm https://www.youtube.com/playlist?list=PLQ176FUIyIUZ1mwB-uImQE-gmkwzjNLjP
* _settings - global_ | CMD ,
* _settings - project_ | CMD ;
* _editor font_: preferences > editor > font
* _default dir to open projects_: appearance > system settings
* _editor config_: `code style`
* [change file association](https://intellij-support.jetbrains.com/hc/en-us/community/posts/206237949-Change-file-association-manually)
* [turn off spell check](https://stackoverflow.com/a/2298724/6813490)
* visual guide for line length: `preferences > code style`
* ignore PEP8 error code in Pycharm: `preferences > inspections > Python > PEP8 > 'ignore errors` > add 'E5' (for line length)
* [show current file being edited in project window](https://stackoverflow.com/a/36738303/6813490)
* spaces instead of tabs: `editor > code style > Python` uncheck `use tab character` --> then do 'reformat code' in file to go from [tabs to spaces](https://stackoverflow.com/a/11816221/6813490)
* ['speed search'](https://www.jetbrains.com/help/phpstorm/speed-search-in-the-tool-windows.html) i.e. fuzzy search once inside project window
* exclude file (from inspections, code completion): [project structure](https://www.jetbrains.com/help/pycharm/excluding-files-from-projects.html)
* need `localhost` in `etc/hosts` to use console https://stackoverflow.com/a/41345334/6813490
* config interpreter to venv: `pref > project > interpreter > venv/bin/python_interpreter` ['Django Fundamentals']
* settings: `~/Library/Preferences/<PyCharmEdition>`
* launcher script: open dir/file from CLI; 'Tools | Create Command-Line Launcher'
* [can be discrepancy btw PyCharm and terminal](https://stackoverflow.com/q/31348711/6813490) about whether your imports are done correctly; potential resolution [here](https://stackoverflow.com/a/21241988/6813490)

editor
* _line_: CMD l (`main menu > navigate`)
* _tab - by number_: CMD # (GoToTabs plugin)
* _tab - scroll ('select next tab')_ : `CMD ALT arrow`
* _method - search_: ALT m https://stackoverflow.com/a/3992371/6813490
* _method - next/previous_: CMD SHIFT arrow
* _un/fold - single_: CMD +/-
* _un/fold -  all_: CMD SHIFT +/-

project
* _project - close_: CMD SHIFT w
* _project - open_: CMD SHIFT o
* _project - open recent_: CMD ALT o
* _pane - split_: CMD ALT s https://vimtricks.com/p/close-all-other-splits/ https://vimtricks.com/p/open-file-in-a-split/ https://vimtricks.com/p/open-vim-and-split-files/ https://vimtricks.com/p/navigating-splits/
* _pane - switch ('splitter')_: CMD ALT j/k
* _function - declaration_: CMD b
* _function - usage_: CMD u
* _search - class_: CMD n
* _search - text ('find in path')_: CMD SHIFT f

windows
* show current editor file in sidebar via 'Autoscroll from source' in project window settings
* _windows + recent files_ | CMD e
* _editor_: ESC (when in other windows)
* _project_: ALT 1
* _shell - Bash_: ALT 2
* _shell - Python_: ALT 3 (close w/ ALT w)
* _find_: ALT 4
* _structure_: ALT 8
* _todo_: ALT 9

edit
* _code completion_: SHIFT RETURN
* _quick fix_: ALT RETURN
* _comment_: CMD /
* _line - cut_:  CMD x
* _line - move_ | CMD arrows
* _refactor_ | CMD SHIFT r
* _select - next occurence_: 📍
* _select - all occurences_: 📍
* _undo/redo_ | CMD z / CMD SHIFT z

## VS Code

🔗 UI https://code.visualstudio.com/docs/getstarted/userinterface

* shift right: `>`
* comment out: `CMD /`
* walled garden https://news.ycombinator.com/item?id=41907350
* switch dir, switch project in IDE https://github.com/dandavison/wormhole
* open at file and LOC: `code -g data/eng.md:419`

THINGS I'M NOTICING ABOUT VSC
* ❌ weird overlay when using checkboxes
* ❌ strange way of getting on `$PATH` -> command pallete > search 'shell command'
* ❌ constantly wipes out the outliner and requires Vim action to prompt redraw
* ❌ symbol search doesn't work after git pull of new files | movement of headers
> sometimes not at all, even after you've just opened file and navigated to header
> this is getting worse in my notes; maybe some perf/data integrity thing with more headers
* ❌ Vim plugin fails on big CSV files
* ❌ no tab groups https://github.com/microsoft/vscode/issues/100335
* ❌ can't update font
* when you uninstall an extension you need to close and reopen VSC for that extesion to be removed from `$HOME/.vscode/extensions`
* autocomplete works for any word in the workspace
* prompt to clear editor history is annoying https://github.com/microsoft/vscode/pull/156421

WORKSPACES 📜 https://code.visualstudio.com/docs/editor/multi-root-workspaces 
* _workspace_: dir(s) in scope for search https://stackoverflow.com/a/50185038
* create: file > 'save workspace as'
* add to: file > 'add folder to workspace'
* open: select `.workspace` file in project root
* switch: 'open recent' from cmd pallete
* `<dir>.code-workspace`: not sure how this works; doesn't seem to tell VS Code "here are paths to dir inside workspace"
```json
// BEFORE
{
	"folders": [
        { "path": "./notes" },
        { "path": "./personal/contacts" },
        { "path": "./personal/calendar/logs/yearly" },
        { "path": "personal/calendar/logs" },
        { "path": "notes/domains" }
    ]
}
// AFTER
{
	"folders": [
        { "path": "notes/domains" },
        { "path": "personal/logs" },
        { "path": "personal/people" }
    ]
}
```

MARKDOWN
* _Markdown Shortcuts_: activity https://github.com/mdickin/vscode-markdown-shortcuts/issues/57 double underscore for bold https://github.com/mdickin/vscode-markdown-shortcuts/issues/49 bold depends on highlighting word first https://github.com/mdickin/vscode-markdown-shortcuts/issues/58
* _Markdown All in One_: bold/italic `cmd b/i` check `alt c`; perf https://github.com/yzhang-gh/vscode-markdown/issues/578 can't config bold https://github.com/yzhang-gh/vscode-markdown/issues/325
* bullet points: think this was provided by previous version of VS Code itself, still works using carriage return (vs. Vim's operator)
* emphasis
```json
// Markdown All in One
"markdown.extension.italic.indicator": "_",
// Markdown Shortcuts
"markdownShortcuts.bold.marker": "__",
```

---

* not OSS https://news.ycombinator.com/item?id=34078225
* type of highlighting https://stackoverflow.com/questions/39775406/how-to-turn-off-matching-highlighting-in-vs-code/45640244#45640244 
* outline view: sort by postition, follow cursor
* explorer font/zoom: `window.zoomLevel: <num>` https://stackoverflow.com/a/36041997

downsides
* update perils https://github.com/microsoft/vscode/issues/142451
* search randomly breaks
* versions (1.41 broke Markdown extensions, seems unsustainable to run older)
* outline view too verbose
* still bloated (console, terminal, version control)
* GUI
* MS product https://news.ycombinator.com/item?id=28812486

misc
* upsides: completion, Vim emulation, less memory usage and better community than Sublime w/ less bloat than PyCharm, same editor for notes and code, merge requests, Markdown formatting (outline for inline code w/ 1.41 is nice), respect gitignore on file search
* views: command pallete, editor, sidebar
* remote development: think this requires src on remote itself vs. Pycharm (which afaik you edit locally and autodeploys to remote on save and runs interpreter there) https://code.visualstudio.com/docs/remote/remote-overview have to repoint `python.venvPath` (settings.json) and `git.path` (ssh settings)
* on path `ln -s /Applications/Visual\ Studio\ Code.app/Contents/Resources/app/bin/code /usr/local/bin/vsc`

EXTENSIONS
* fs location: `$HOME/.vscode/extensions`
* previous breaks from Markdown extensions https://github.com/mdickin/vscode-markdown-shortcuts/issues/60 https://github.com/mdickin/vscode-markdown-shortcuts/issues/59 https://github.com/yzhang-gh/vscode-markdown/issues/578
* freeze: `alias vscfr="ls ~/.vscode/extensions/ > $DOTFILES_DIR/vsc-pkg.txt"`
* rollback version https://stackoverflow.com/questions/42626065/vs-code-rollback-extension-install-specific-extension-version
* Makefile: ecosystem could use one just for goto https://github.com/microsoft/vscode/issues/47098 outline support https://github.com/microsoft/vscode/issues/81069 there's another extension that tries to run Makefile targets, mine just provides goto symbol and outline support (with prereqs) https://marketplace.visualstudio.com/items?itemName=technosophos.vscode-make&ssr=false
* Markdown: auto-close, bold/italic (independent of cursor location in word)

config
* _file locations_: config home `~/Library/Application Support/Code/User/` conf `settings.json` keys `keybindings.json` snippets `/snippets` https://stackoverflow.com/a/45910856
* exclude dir from search `search.exclude` https://stackoverflow.com/a/33418660/6813490
* file explorer outline follow cursor, sort by position, levels of nesting https://github.com/Microsoft/vscode/issues/54941 https://github.com/Microsoft/vscode/issues/58095
* relative line number for Vim https://github.com/VSCodeVim/Vim/issues/423
* clickable URLs https://github.com/Microsoft/vscode/issues/68333
* Markdown: autoclose for backticks and quotes https://github.com/Microsoft/vscode/issues/38352 bold w/ double underscore https://github.com/mdickin/vscode-markdown-shortcuts/issues/57 https://github.com/mdickin/vscode-markdown-shortcuts/issues/58
* open tabs to far right https://stackoverflow.com/a/46865080
* open links w/ keybinding https://github.com/microsoft/vscode/issues/68333
```json
{
    "key": "cmd+alt+enter",
    "command": "editor.action.openLink"
}
```
* finding Python envs https://github.com/microsoft/vscode-python/issues/8372 stuck on recently used w/ Poetry https://github.com/microsoft/vscode-python/issues/9826
* _code completion and virtual environment_:  does it really work? or just using globally installed pkg? https://realpython.com/python-development-visual-studio-code/ manually set https://code.visualstudio.com/docs/getstarted/settings#_settings-file-locations https://code.visualstudio.com/docs/python/environments#_manually-specify-an-interpreter https://stackoverflow.com/questions/40377654/how-to-create-and-init-vscode-in-vscode

reinstall
* rm old using App Cleaner
* install
* disable plugins you only use occasionally
* outline view: follow cursor, sort by position
* color theme
* symlink to `dotfiles`
```sh
# path/to/Code/User
ln -sf "/Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/settings.json" "/Users/zach/Library/Application Support/Code/User/settings.json"
ln -sf "/Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/keybindings.json" "/Users/zach/Library/Application Support/Code/User/keybindings.json"

# path/to/Code/User/snippets
ln -sf "/Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/markdown.json" "/Users/zach/Library/Application Support/Code/User/snippets/markdown.json"
# python https://github.com/zachvalenta/dotfiles-capp/commit/7114f4f25ef73b22a38386aad90006781b386f20
```

install specific version
* uninstall using App Cleaner
* grab specific version
* unzip and move to `/Applications`
* open then quickly close so you can ⤵️ https://github.com/microsoft/vscode/issues/87215
* symlink from `settings.json`, `keybindings.json`, and snippets https://stackoverflow.com/a/49347158/6813490
* uninstall didn't seem to affect `~/.vscode/extensions`, fresh install just picked them up, enabled by default
* 1.41: broke Markdown extensions
* 1.46: pinned tabs https://code.visualstudio.com/updates/v1_46#_pin-tabs more flexible layouts https://code.visualstudio.com/updates/v1_46#_flexible-layout

keybindings
* tab: previous `gT` next `gt` (w/ Vim extension) https://stackoverflow.com/a/51407314
* goto symbol https://code.visualstudio.com/updates/v1_44#_workbench
* _clear file history_: command pallete + `clear editor history`
* _command palette (god command)_: `cmd shift p`
* _extensions_: `cmd shift x`
* _file explorer_: `cmd shift e`
* _function - declaration/definition_: cmd palette -> 'definition'
* _function - usage/reference_: cmd palette -> 'reference'
* Markdown preview: `cmd shift v`
* _outline view_: rm imports/vars/classes and leave only functions https://github.com/microsoft/vscode/issues/84380 https://github.com/zfeher/dotfiles/blob/66f3c1cb0d7a502adb5d4ee6d90493af3fab6c49/vscode/User/settings.json
* _pane - split_: `CMD \`
* _pane - switch ('splitter')_: `CMD ALT <arrow>`
* _search workspace_: `CMD SHIFT f` if you accidentally pull this off the activity bar [the leftmost section] you can drag back on https://stackoverflow.com/a/50065112/6813490
* _sidebar - show_: `cmd b`
* _tab - by number_: `{ "key": "cmd+1", "command": "workbench.action.openEditorAtIndex1" }`
* _tab - close others_: `cmd alt t`
* _un/fold_: cmd palette

## Zed

📜 https://zed.dev/
🗄️ `ml.md` code assist > IDE

VIM
* https://zed.dev/blog/zed-decoded-vim
* use Vim normal mode to drive Zed itself https://stevedylan.dev/posts/leaving-neovim-for-zed/#vim-mode--keybindings
> I’ll likely get into this further into the post, but the way you can structure keybindings for Vim mode in Zed is fantastic. The structure allows for your typical VScode style config, but with the ability to scope a keybinding to a Vim mode is such a huge win for Neovim users. For instance, I can cheat my way into using a leader key when in normal mode and get things like space d to see diagnostics, or space t to open a full window terminal. It’s a pattern many Vim users will appreciate and I wish there was more docs for it as I’ve had to figure some of it out myself. https://stevedylan.dev/posts/leaving-neovim-for-zed/#vim-mode

DESIGN
* cross-platform https://zed.dev/releases/stable/0.143.6
* fast input 🗄️ `models.md` Claude
* just works™️: no Neomvim config hell, Python pkg mgmt with Poetry https://stevedylan.dev/posts/leaving-neovim-for-zed/
* ❌ makes itself default editor (broot)
* ❌ workspaces https://github.com/zed-industries/zed/discussions/17278 https://github.com/zed-industries/zed/discussions/7194 https://github.com/zed-industries/zed/issues/9459 but you can open multiple repos from CLI `zed domains sw`
* document outline available now but doesn't nest enough + shows code snippets as headers in Markdown https://github.com/zed-industries/zed/discussions/13421 https://zed.dev/releases/stable/0.141.2

---

visual component semantics https://github.com/zed-industries/zed/discussions/9763

FEATURES - BASICS
* search https://zed.dev/releases/stable/0.152.3
* themes https://zed.dev/blog/user-themes-now-in-preview

📍 FEATURES - EXPLORE
* feedback: notebooks, REPL https://zed.dev/releases/stable/0.146.3
* remote dev 🗄️ `src.md` denv > cloud
* collab https://zed.dev/docs/collaboration
* project mgmt https://stevedylan.dev/posts/leaving-neovim-for-zed/#plugin-replacements https://zed.dev/docs/channels
* remote dev https://zed.dev/releases/stable/0.145.1

AI 🗄️ `ml.md` code assist
* https://zed.dev/releases/stable/0.147.2
* https://zed.dev/releases/stable/0.149.3
* https://zed.dev/blog/replhttps://zed.dev/blog/zed-ai

DESIGN
* https://zed.dev/blog/between-editors-and-ides
* https://zed.dev/blog/we-have-to-start-over 
* https://registerspill.thorstenball.com/p/from-vim-to-zed
* https://jackevans.bearblog.dev/trying-out-zed/

# ⭕️️ CORE

PLUGINS
* pairs - edit: https://github.com/tpope/vim-surround https://stackoverflow.com/a/50687836 https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-surround.md
* pairs - autoclose: https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-pairs.md https://github.com/tpope/vim-unimpaired https://github.com/windwp/nvim-autopairs

---

VISUAL MODE
* _visual_: select text first, then operate 📙 Neil practical [40]
* sub-modes: character `v` block `CTRL v` line `V`
* block: for columns https://www.youtube.com/watch?v=prnrwpOEsmo 22:20

* https://github.com/iggredible/Learn-Vim/blob/master/ch11_visual_mode.md
* https://www.getrevue.co/profile/vim_tricks/issues/edit-multiple-lines-at-once-1221503 📙 Neil practical 8.52
* http://vimcasts.org/episodes/selecting-columns-with-visual-block-mode/
* `V` (linewise) `v` (characterwise) indent (viz + `< / >`) surround (highlight + `S` + char https://stackoverflow.com/a/50687836/6813490)
* `o` restart selection https://vimtricks.substack.com/p/vimtrick-editing-visual-selections

MODES
* _normal_: motions
* _insert_: actually writing
* _command line_: anything preceded by `:` 📙 Neil practical [5.27]
* _operator-pending_: 📍 📙 Neil practical [2.12]
* _visual_: 📍

SEMANTICS https://github.com/iggredible/Learn-Vim/blob/master/ch04_vim_grammar.md
* _syntax_: operator + count + motion; order can change e.g. `3dd` for delete 3 lines [VT 2.6]
* _change_: anything from any mode that modifies text in document [PV 2.8]
* _macro_: save series of commands as single cmd https://hacker-tools.github.io/editors/ https://www.youtube.com/watch?v=K4PoBfz3WLA https://www.youtube.com/watch?v=futay9NjOac 📙 Neil practical ch. 11 https://github.com/iggredible/Learn-Vim/blob/master/ch09_macros.md https://stackoverflow.com/questions/8745514/concept-of-index-in-vim
> need macro to `zt` on nav motions
* _word_: char, num, underscore [Neil pv 8.119]
* _WORD_: word but incl. delimiters [Neil pv 8.119]

SNIPPETS
* https://www.youtube.com/watch?v=Co4S_uJYb1o
* https://vimtricks.com/p/automated-file-templates/
* https://www.youtube.com/watch?v=PJiOYNMOQ8M&lc=UgguwtLM8AsVcXgCoAEC
* https://www.youtube.com/watch?v=XA2WjJbmmoM 38:20
* https://www.semicolonandsons.com/episode/IDE-like-refactors-snippets-tests-hover-docs-commenting-and-git 2:15
* _ultisnips_: https://github.com/SirVer/ultisnips http://vimcasts.org/episodes/meet-ultisnips/

SUBSTITUTE 📙 Neil practical ch. 14
```sh
# basic
:%s/this/that

# things you have to escape
:%s/\'/\"  # quotes
:%s/\ /\-  # white space
```
* live preview http://vimcasts.org/episodes/neovim-eyecandy/
* project wide http://vimcasts.org/episodes/project-wide-find-and-replace/
* all lines: `:%` [PV 5.28]
* last line: `:$`
* https://vimtricks.com/p/tag/replace/ https://vimtricks.substack.com/p/vimtrick-count-occurrences
* https://news.ycombinator.com/item?id=26285372
* current line_: `.` e.g. `:.s/\ /-/g` replace all spaces on line with hyphen https://stackoverflow.com/a/46181576/6813490
* https://github.com/osyo-manga/vim-over

* block cursor, line cursor (for insert mode) https://www.youtube.com/watch?v=FcQjTXLrVUU
* open URL under cursor https://vimtricks.com/p/open-url-under-cursor/
* highlight lines https://vimtricks.com/p/highlight-specific-lines/
* run cmd on every line https://vimtricks.com/p/operate-on-every-line/
* once you're in insert mode, stay there until you finish full edit so it's repeatable https://vimtricks.com/p/insert-mode-edit-mappings/
* comments https://vimtricks.com/p/commenting-code/ https://github.com/preservim/nerdcommenter https://github.com/tpope/vim-commentary https://www.semicolonandsons.com/episode/IDE-like-refactors-snippets-tests-hover-docs-commenting-and-git 4:00 https://www.youtube.com/watch?v=aH50njzReXQ
* hidden char https://vimtricks.com/p/display-hidden-characters/
* mouse support `set mouse+=a`
* export visual as html https://stefanoborini.com/export-vim-text-with-colors-to-html/
* datetime: https://vimtricks.substack.com/p/insert-the-current-date-or-time
* design: available everywhere and modal (melodies not chords) [Neil pv xx] but Vimscript is meh and destructive tasks are easy
> The most important idea in Vim is that Vim’s interface itself is a programming language. Keystrokes (with mnemonic names) are commands, and these commands compose. https://missing.csail.mit.edu/2020/editors/
* new line: treated differently than other text editors https://stackoverflow.com/questions/15639511/vim-show-newline-at-the-end-of-file
* spell check: `:set spell/nospell` https://vimtricks.substack.com/p/vimtrick-spell-checking-in-vim http://vimcasts.org/episodes/archive/ https://www.youtube.com/watch?v=44pNDuRO77g
* remote editing https://vimtricks.substack.com/p/vimtrick-edit-files-remotely
* whitespace: flag https://realpython.com/vim-and-python-a-match-made-in-heaven/#flagging-unnecessary-whitespace trim https://vimtricks.substack.com/p/vimtrick-trim-trailing-whitespace tabs, spaces http://vimcasts.org/episodes/archive/
* text wrap http://vimcasts.org/episodes/archive/ format line length https://www.youtube.com/watch?v=a3yhIOelUCY
* show newline, invisible char http://vimcasts.org/episodes/show-invisibles/
* lists: quickfixlist, arglist https://vimtricks.substack.com/p/vimtrick-copy-from-quickfix-to-the 📙 Neil modern ch. 4 https://vimtricks.substack.com/p/vimtricks-help-powerup

## command mode

📚
* Neil modern ch. 5
* Neil practical ch. 5

OPEN FILE AT
* search query: `alias com="vim +/commits $MAT_DIR/sw/db/shujuku/hiring/profile.md"`
* last line: `vim '+normal G$' $PER_DIR/tracking/24/"$fname";`

---

* completion https://alpha2phi.medium.com/neovim-for-beginners-built-in-completion-8bbbb0f16c9c
* can run terminal emulator inside buffer http://vimcasts.org/episodes/neovim-terminal/ https://www.youtube.com/watch?v=ehD382bPuPA https://rutar.org/writing/from-vim-and-tmux-to-neovim/ 📙 Neil modern [5.130] http://vimcasts.org/episodes/neovim-terminal/ http://vimcasts.org/episodes/neovim-terminal-mappings/ https://github.com/akinsho/toggleterm.nvim

ARGDO
* bufdo, tabdo, location list, quickfix list 📙 Neil practical chapter 17 https://github.com/iggredible/Learn-Vim/blob/master/ch21_multiple_file_operations.md
* https://www.youtube.com/watch?v=futay9NjOac
* http://vimcasts.org/episodes/using-argdo-to-change-multiple-files/
* https://www.semicolonandsons.com/episode/Vim's-Versatile-CLI https://www.semicolonandsons.com/episode/Advanced-Vim-Workflows

* scroll cmd history: `: + arrow`
* search: `:<start_of_cmd> + arrow` https://vim.fandom.com/wiki/Using_command-line_history
* open stdin: `cmd | vim -` e.g. `\ls | vim -` for file editing https://vim.fandom.com/wiki/Bulk_rename_files_with_Vim

* http://vimcasts.org/episodes/refining-search-patterns-with-the-command-line-window/

* execute over a range of lines, aka ex cmds [PV 5.intro]
* enter: `:` or `/` [PV 5.intro]
* exit: `esc`
* view history https://vimtricks.substack.com/p/vimtrick-view-your-history-from-command
* quit and discard: `:q!`
* https://vimtricks.com/p/operate-across-files-by-name/

* _substitute_: `:%s/<old>/<new>` [PV 5.58] repeat https://vimtricks.substack.com/p/vimtrick-repeat-the-last-substitution across files https://vimtricks.substack.com/p/vimtrick-replace-across-files
* _global_: `:%s/<old>/<new>/g` [PV 5.58]
can also use to delete lines https://vimtricks.substack.com/p/vimtrick-remove-lines-matching-pattern

## motions

---

> clean up normal mode header first

* https://news.ycombinator.com/item?id=33136190

char
* _find by_: `t` (incl) `f` (ex); `;` (next) `,` (previous); for current line, cap for backwards
* _matching_: `%`
* _left/right_: `h/l`
* _left/right - insert_: `i/a` ('append')

file
* _start/end_: `gg/G`
* _goto_: `<num>G`
* _up/down_: `k/j`
* _start/end_: `0/$`
* _start/end - non-blank_: `^/g_`
* _start/end - insert_: `I/A`

* current line - nudge: `ctrl e/y` https://vimtricks.substack.com/p/vimtrick-nudge-current-line-up-or
* page - half: `CTRL d/u`
* page - whole: `CTRL b/f`

word
* _forward to start_: `w`
* _forward to end_: `e` ('append')
* _back to start_: `b`
* _back to end_: `ge`

## normal mode

JUMPS https://github.com/folke/flash.nvim https://github.com/phaazon/hop.nvim https://github.com/ggandor/leap.nvim sneak https://www.youtube.com/watch?v=HkY3LoQqKVA https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-jump2d.md
* _jump_: mv btw buffers; can think of as long-range motions 📙 Neil practical [9.135-6]
* separate per window 📙 Neil practical [9.136]
* `gf`: jump to filename 📙 Neil practical [9.136,139]
> seems like more trouble than its worth compared to ctags
* _jumplist_: list of recent jumps (move btw files, long-range motions) 📙 Neil practical [9.56]
* `CTRL i/o`: forward/back 📙 Neil practical [9.136]
* `:jumps`: list

---

* `gj/k`: mv visual line
* `j/k`: mv real line
* run on every line https://www.getrevue.co/profile/vim_tricks/issues/operate-on-every-line-1181574
* `g_` mv to last normal char in line (vs. new line) https://stackoverflow.com/a/105734
* _case_: lower `gu` upper `gU` https://vimtricks.com/p/change-character-case/

📙 Neil practical 2.12
🔗 `:h motion.txt`

rf
* region selection https://vimtricks.substack.com/p/vimtrick-region-expanding
🎗 all motion are either inclusive or exclusive [`:h exclusive`]

* `]m`: next method https://vimtricks.substack.com/p/vimtrick-jump-to-next-method
* `H/M/L`: mv to new cursor line at top/mid/btm of viewport 📙 Neil practical [9.136]
* `$NUM G`: goto line 📙 Neil practical [9.136]
```sh
:num  # goto line
```
* _motion_: mv w/in buffer 📙 Neil practical [113,9.135]
* vs. jumps as long-range motions 📙 Neil practical [9.136]

---

* wrap: `gw`  https://vimtricks.substack.com/p/vimtrick-tidy-paragraphs
https://github.com/easymotion/vim-easymotion

 📍 operate until https://vimtricks.substack.com/p/vimtrick-operate-until-pattern

## operators

* _operator_: verb
* _text object_: pattern (paren pair, HTML tags) 📙 Neil practical [8.128] https://www.youtube.com/watch?v=FuYQ7M73bC0

---

* _swap_: http://vimcasts.org/episodes/swapping-two-regions-of-text-with-exchange-vim/ https://github.com/tommcdo/vim-exchange swapfile https://www.youtube.com/watch?v=_PoI0zSCLJE
* _bubble_: http://vimcasts.org/episodes/bubbling-text/ https://www.youtube.com/watch?v=gNyNm5DsQ88
* _case_: `u` (lower) `U` (cap) -> think this is different than 'undo' bc need to select something first
* _change_: `c` (cut + insert mode) `cc` (line) `C` (to line end)
* _delete (cut)_ : `d` (operator pending)  `dd` (line) `D` (line end) `s` (char under cursor + insert)
* _dot_: `.` [PV 1.2] rewards repeatable changes [PV 2.9]
* _indent_: https://vimtricks.substack.com/p/vimtrick-indenting-code
* _open_: `O` (at current) `o` (below current VT 6.1)
* _put (paste)_: `P` (before) `p` (after); will swap if pasting over text highlighted in visual mode [PV 10.62] `CTRL r <register>` (put from register while inside insert mode) [PV 3.15]
* _redo_: `CTRL r`
* _replace_: `r` (char) `R` (word)
* _yank (copy)_: `y` (+ motion) `yy`/`Y` (line) https://vimtricks.com/p/copy-from-above-or-below/ http://vimcasts.org/episodes/neovim-eyecandy/
yank by line number without moving https://vimtricks.com/p/copying-and-pasting-lines/

## registers

UNDO https://github.com/iggredible/Learn-Vim/blob/master/ch10_undo.md
* https://news.ycombinator.com/item?id=40928893
* VSCodeVim strangeness for undo bc using an embedded NeoVim? 📙 Neil modern [135]
* `undofile`: persist undo history btw sessions 📙 Neil modern [6.99]
* `u`: undo single change
* `CTRL r`: redo single change
* `U`: undo all changes on line
* `CTRL u`: stay in insert mode https://vimtricks.com/p/undo-from-insert-mode/
* time travel: https://github.com/mbbill/undotree https://github.com/sjl/gundo.vim https://vimtricks.com/p/vimtrick-time-travel-in-vim/
```sh
:earlier 3   # undo the last 3 changes
:earlier 5m  # go back to the state of the file 5 minutes ago
:later 2     # after undoing something, redo the next 2 changes
:later 1h    # travel forward through the change history 1 hour
```
* infinite https://news.ycombinator.com/item?id=18901621 
```vimrc
set undofile
set undodir=~/.vim/undodir
```

SEMANTICS https://github.com/iggredible/Learn-Vim/blob/master/ch08_registers.md
* _register_: container that holds text [Neil pv 10.62]
* _system register_: used by os; aka clipboard 📙 Neil practical [10.62] http://vimcasts.org/episodes/accessing-the-system-clipboard-from-vim/
* `"+` (`*` on macOS) https://realpython.com/vim-and-python-a-match-made-in-heaven/#system-clipboard http://vimcasts.org/episodes/using-vims-paste-mode-with-the-system-paste-command/
* avoid overwrite https://www.youtube.com/watch?v=JU8g1-j2jd8
* _unnamed register_: not addressable by char/num https://vimtricks.com/p/pasting-multiple-times/
* _undolist_: list of changes? https://vi.stackexchange.com/a/26309
* `,/;`: travel back/forward https://vimtricks.substack.com/p/vimtrick-jump-between-changes
* _changelist_: cursor location at the time of edit? 📙 Neil [9.137] http://vimcasts.org/episodes/using-the-changelist-and-jumplist/
* `+/-`: travel back/forward https://vi.stackexchange.com/a/26309

---

http://vimcasts.org/episodes/pasting-from-visual-mode/

* list registers `:reg`
* address register `"<reg>`

actions https://vimtricks.com/p/pasting-multiple-times/
* yank: copies text to both unnamed register and 0 register
* paste: copies text pasted over into unnamed register but doesn't touch 0 register

When I copy text with y, Vim puts it in the unnamed register and the 0 register. Both those registers contain the same thing.
When I paste over with p, Vim puts what I pasted over into the unnamed register but the 0 register still contains my original yanked text.
That means that if I paste with p, I’ll get the last thing I pasted over but if I paste with "0p, then I’ll paste with the last yanked text. Which is exactly what we want!

https://vimtricks.com/p/improving-usage-of-registers/
* _VS Code Vim_: using default register across windows https://github.com/VSCodeVim/Vim/issues/4197
* _put (paste)_: `P` (before) `p` (after); will swap if pasting over text highlighted in visual mode [PV 10.62] `CTRL r <register>` (put from register while inside insert mode) [PV 3.15]
* 📝 there are a few registers whose values (current file, last searched text) are read-only [PV 10.62]
* can paste from system register into Vim as well https://vimtricks.substack.com/p/vimtrick-the-clipboard-register
* https://vimtricks.substack.com/p/vimtricks-command-mode-paste
* https://vimtricks.com/p/pasting-multiple-times/
* https://vimtricks.substack.com/p/vimtricks-avoid-paste-formatting
* https://vimtricks.com/p/go-to-next-match-and-select/
* [PV 10.61]

# 🔳 ORG

🐘 BARBAR https://github.com/romgrk/barbar.nvim
* tabline aka bufferline https://github.com/mengelbrecht/lightline-bufferline https://github.com/akinsho/bufferline.nvim
* catppuccin integration
* pin https://github.com/romgrk/barbar.nvim/issues/539 https://github.com/romgrk/barbar.nvim/issues/175
* tab width https://github.com/romgrk/barbar.nvim/issues/515
* separator https://github.com/romgrk/barbar.nvim/issues/457
* alternatives https://github.com/nanozuki/tabby.nvim https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-tabline.md

## buffers

🗄️ `shell.md` file explorer, fuzzy find, multiplex
📙 Neil modern ch. 3 practical ch. 6-7

BUFFERS https://github.com/romgrk/barbar.nvim/issues/279
* _file_: on disk 📙 Neil practical [6.84]
* _buffer_: file contents in memory, waiting to be written back to disk 📙 Neil practical [6.84]
* `:edit $PATH`: open 📙 Neil practical [7.101] modern [3.23]
* update name 📙 Neil modern [6.103]
* `:wall`: save all 📙 Neil practical [6.90]
* hidden http://vimcasts.org/episodes/working-with-buffers/
* _bufferlist_: open buffers 📙 Neil practical [6.84]
* using airline https://jdhao.github.io/2018/09/29/Switching_buffers_quickly_Neovim/
* similar to how other editors/browsers do tabs http://vimcasts.org/episodes/how-to-use-tabs/ [0:45]
* _argument list_: buffer group to run batch cmd against 📙 Neil practical [6.86,89] https://vimtricks.substack.com/p/vimtrick-open-all-files-in-a-directory 
* _minimap_: sidebar showing compressed version of buffer
* lib to generate https://github.com/wfxr/code-minimap
* requires another library https://github.com/wfxr/minimap.vim
* doesn't render correctly https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-map.md
* _outliner_: display buffers ctags in order of definition
* _tree_: display project fs; nvim-tree (catppuccin integration) https://github.com/nvim-tree/nvim-tree.lua https://www.youtube.com/watch?v=SpexCBrZ1pQ https://github.com/preservim/nerdtree https://github.com/nvim-neo-tree/neo-tree.nvim fern (catppuccin integration) https://www.youtube.com/watch?v=YpzIhRoZ-tk https://www.youtube.com/watch?v=oFc2kr734rs https://www.youtube.com/watch?v=dL2J0TtdCRk NerdTree https://github.com/scrooloose/nerdtree netrw https://www.youtube.com/watch?v=nDGhjk4Eqbc https://vimtricks.substack.com/p/vimtrick-filesystem-exploration http://vimcasts.org/episodes/the-file-explorer/ https://www.youtube.com/watch?v=XA2WjJbmmoM 34:30
* _winbar_: fs breadcrumbs;
* catppuccin integration https://github.com/utilyre/barbecue.nvim https://github.com/Bekaboo/dropbar.nvim

## tabs / sessions

* _tab group_: collection of windows 📙 Neil practical [6.95] http://vimcasts.org/episodes/working-with-tabs/ http://vimcasts.org/episodes/how-to-use-tabs/
> this is something that I didn't fully realize that I wanted from VS Code
* `tabedit` workflow https://vimtricks.com/p/quickly-access-project-notes/
* use to encapsulate diff types of files e.g. business logic vs. immediate files https://www.youtube.com/watch?v=hbs7tuwpgZA 5:00
* no way to name, tab gets name from `MyTabLabel` https://github.com/neovim/neovim/issues/19272 https://neovim.io/doc/user/tabpage.html
```sh
:tabs      # list buffers open in all tabs
:tabonly   # close all other tabs
:tabclose  # close https://stackoverflow.com/questions/32714834/how-to-close-a-tab-in-vim
:tabmove   # https://www.youtube.com/watch?v=ZlyiNuxlkJY 2:45
```
* _tabline_: display for tab
* _session_: tab group + state https://github.com/iggredible/Learn-Vim/blob/master/ch20_views_sessions_viminfo.md https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-sessions.md
* cmd https://jvns.ca/blog/2017/09/10/vim-sessions/
```sh
# SAVE
:mksession ~/.vim/sessions/foo.vim
# RESTORE
:source ~/.vim/sessions/foo.vim
vim -S ~/.vim/sessions/foo.vim
```
* harpoon for file marking + sessions https://github.com/ThePrimeagen/harpoon https://www.youtube.com/watch?v=Qnos8aApa9g https://willcodefor.beer/posts/keyvim
* records bufferlist, tab group 📙 Neil modern [6.98]
* state also recorded in `viminfo` and `shada-file` (Neovim) 📙 Neil modern [6.98]
* restore https://github.com/rmagatti/auto-session
* porcelain https://github.com/tpope/vim-obsession

## windows

* _viewport_: what's in view 📙 Neil practical [6.92] https://developer.mozilla.org/en-US/docs/Web/CSS/Viewport_concepts https://vimtricks.com/p/navigating-around-the-screen/
* `zt/z/b`: mv cursor line to top/mid/btm of viewport https://vimtricks.substack.com/p/vimtrick-reposition-the-current-line
* keep cursor vertically centered https://vim.fandom.com/wiki/Keep_your_cursor_centered_vertically_on_the_screen https://stackoverflow.com/a/2281755
* _window/split_: viewport onto buffer 📙 Neil practical [6.92] http://vimcasts.org/episodes/working-with-windows/
* create: horizontal `:split`/`CTRL-w s` vertical `:vsplit`/`CTRL-w v` 📙 Neil practical [6.92]
* balance: `CTRL W` https://vimtricks.substack.com/p/vimtrick-equalize-your-splits
* nav 📙 Neil practical [6.93]
* mv https://vimtricks.substack.com/p/vimtrick-moving-splits https://vimtricks.substack.com/p/vimtrick-change-split-orientation
* resize, close [6.94]
* create w/ file `:sp $FILE` [6.93]
* create to specific line https://vimtricks.substack.com/p/vimtrick-split-to-a-line
* maximize current split https://vimtricks.com/p/maximize-the-current-split/

## workspaces

* people don't seem to grok why this is useful https://www.reddit.com/r/vim/comments/97113u/simpleworkspacesvim_vs_codelike_workspace_support/ https://www.reddit.com/r/neovim/comments/10g76tf/open_multiple_directories_like_vs_code_workspace/
> Workspaces are the major thing keeping me in VSCode https://www.reddit.com/r/neovim/comments/11r8npx/hello_first_post_here_any_alternatives_to_vscodes/
* could just have diff projects in diff tab groups but would lose search across (domain/book notes, logs/ren)
* _Telescope_: ✅
* grep: patched Telescope to use ripgrep's ability to follow symlinks in workspace dir https://github.com/nvim-telescope/telescope.nvim/pull/2795
* files: create workspace dir, symlink to dirs, `find_files follow=true` https://github.com/nvim-telescope/telescope.nvim/blob/18774ec7929c8a8003a91e9e1f69f6c32258bbfe/lua/telescope/builtin/init.lua#L80 https://www.reddit.com/r/neovim/comments/10g76tf/open_multiple_directories_like_vs_code_workspace/
* _SimpleWorkspaces_: ✅ https://github.com/andreyorst/SimpleWorkspaces.vim
* `projections`: ✅ https://github.com/GnikDroy/projections.nvim
* `project.nvim`: dir picker? https://github.com/ahmedkhalf/project.nvim https://www.reddit.com/r/neovim/comments/10g76tf/comment/j51605k/
* `whaler.nvim`: dir picker? https://github.com/SalOrak/whaler.nvim
* `workspaces.nvim`: misnomer https://www.reddit.com/r/neovim/comments/10g76tf/open_multiple_directories_like_vs_code_workspace/
* `telescope-project`: allows jump btw dir, doesn't allow putting dirs into single workspace https://github.com/nvim-telescope/telescope-project.nvim

# 🛠️ UTILS

🗄️ `os/tools.md` search

* can wrap CLIs in Lua to run within Neovim https://www.youtube.com/watch?v=rerTvidyz-0

## code intel

---

* error lens https://switowski.com/blog/plugins-for-python-in-vscode/
* https://github.com/facebookincubator/bowler
* use `inspect` and vim to look at source (vs. IDE goto source) https://www.youtube.com/watch?v=hZ0dRTYy5NA

GIT 🗄️ `git.md` tooling
* _gitgutter_: https://github.com/airblade/vim-gitgutter
* _gitsigns_: catppuccin integration https://github.com/lewis6991/gitsigns.nvim
* _gitlens_: https://switowski.com/blog/plugins-for-python-in-vscode/

FOLDING
* _ufo_: https://github.com/kevinhwang91/nvim-ufo
* https://realpython.com/vim-and-python-a-match-made-in-heaven/#code-folding http://vimcasts.org/episodes/archive/
* https://github.com/iggredible/Learn-Vim/blob/master/ch17_fold.md

Python indentation https://vimtricks.substack.com/p/vimtrick-column-highlighting 
Python terminal, debugger https://github.com/AstroNvim/AstroNvim https://zackproser.com/blog/codeium-analysis-4-2024

LINTING 📙 Neil practical ch. 20
* null-ls https://www.youtube.com/watch?v=ybUE4D80XSk
* functions: autocorrect, spellcheck, thesaurus, dictionary, grammar
* https://www.youtube.com/watch?v=3TX3kV3TICU
* https://github.com/preservim/vim-lexical
* https://github.com/preservim/vim-litecorrect
* https://github.com/preservim/vim-wordy
* grammar https://www.youtube.com/watch?v=tIvdLeeW6pM https://github.com/caderek/gramma
* https://github.com/languagetool-org/languagetool
* linting https://github.com/errata-ai/vale
```vimrc
# https://www.moolenaar.net/habits.html
:abbr Lunix Linux
:abbr accross across
:abbr hte the
```

### highlight

MISC PLUGINS
* _aerial_: ✅ outliner https://github.com/stevearc/aerial.nvim (catppuccin theme, Telescope integration)
* treesitter alone doesn't support markdown? https://www.reddit.com/r/neovim/comments/qzp4as/aerialnvim_outline_window_now_supports_treesitter/
* submit PR to allow config of Markdown symbols https://github.com/stevearc/aerial.nvim/issues/327
* alternatives: requires LSP https://github.com/simrat39/symbols-outline.nvim tagbar https://github.com/preservim/tagbar https://jdhao.github.io/2018/09/28/nvim_tagbar_install_use/ Markdown https://github.com/taoso/tagbar-markdown
* _tree-sitter_: ✅ build syntax tree for file in order to provide highlighting https://github.com/nvim-treesitter/nvim-treesitter https://www.youtube.com/watch?v=puWgHa7k3SY 5:00 https://news.ycombinator.com/item?id=26225298
* alternative to using regex to understand language features https://www.youtube.com/watch?v=Ku-m7eEbWas
* install: you'll get a install error from vim-plug, open neovim again and it should download language parsers
* can use for code folding https://www.youtube.com/watch?v=Ku-m7eEbWas 4:30
* https://news.ycombinator.com/item?id=27292237
* text objects in treesitter https://www.youtube.com/watch?v=CEMPq_r8UYQ
* https://github.com/nvim-treesitter/nvim-treesitter-context

HIGHLIGHT PLUGINS
* ✅ cursorword https://github.com/RRethy/vim-illuminate https://github.com/itchyny/vim-cursorword https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-cursorword.md
* ✅ scope https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-indentscope.md
* todos https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-hipatterns.md

### LSP

🗄️ `plt.md` LSP

* people hate this https://www.youtube.com/watch?v=G1_Y5hLTfgw [2:00,7:30] https://www.youtube.com/watch?v=IRd2zwF527M
* how this works in Neovim: `nvim-lspconfig` configs nvim client, `vim.lsp` as framework for tooling to connect to language servers, tool for language server mgmt (mason) https://www.youtube.com/watch?v=3a1PCir_aHs
* _lsp-zero_: ✅ wrapper around `nvim-lspconfig`, `nvim-cmp`, and `mason` https://github.com/VonHeikemen/lsp-zero.nvim https://www.youtube.com/watch?v=3a1PCir_aHs 2:15
* keybindings: things that don't work so far are `gd` but maybe this is because poetry build broken https://github.com/VonHeikemen/lsp-zero.nvim?tab=readme-ov-file#keybindings
* install: for some reason pyright needs `npm`, installed with `nodenv` and then ran `nodenv init` (need to restart terminal) https://github.com/VonHeikemen/lsp-zero.nvim/issues/91#issuecomment-1364608056
* _mason_: ✅ mgmt for language servers, DAP, linters, formatters https://github.com/williamboman/mason.nvim
* alternative https://github.com/neoclide/coc.nvim https://www.youtube.com/watch?v=OXEVhnY621M https://news.ycombinator.com/item?id=33210247
* _nvim-cmp_: ✅ code completion, catppuccin https://github.com/hrsh7th/nvim-cmp

📍 todo LSP plugins
* _ALE_: real-time linting via LSP https://github.com/dense-analysis/ale
* use individual linters behind the scenes e.g. jslint for project X and eshint for project Y 📙 Neil modern [118]
* _DAP_: debugger https://www.youtube.com/watch?v=RziPWdTzSV8 https://github.com/puremourning/vimspector
* _trouble_: diagnostics https://github.com/folke/trouble.nvim
* _vim-test_: run test under cursor https://www.youtube.com/watch?v=7VP7TdItuEs https://www.semicolonandsons.com/episode/IDE-like-refactors-snippets-tests-hover-docs-commenting-and-git 1:40 alternative https://github.com/nvim-neotest/neotest
* _vim-projectionist_: decouple way you organize buffers from fs 📙 Neil modern [30,113-124] https://github.com/tpope/vim-projectionist https://subvisual.com/blog/posts/133-super-powered-vim-part-i-projections/ using in Neovim https://stackoverflow.com/questions/76493146/configure-vim-projectionist-in-neovim-with-lua
* switch btw src and test https://www.semicolonandsons.com/episode/IDE-like-refactors-snippets-tests-hover-docs-commenting-and-git 1:15

AUTOCOMPLETE 📙 Neil practical ch. 19
* https://github.com/ycm-core/YouCompleteMe
* https://stackoverflow.com/questions/7138039/vim-autocomplete-for-python
* find virtualenv https://realpython.com/vim-and-python-a-match-made-in-heaven/#virtualenv-support 
* https://www.semicolonandsons.com/episode/vim-autocomplete-overview 
* https://vimtricks.com/p/autocomplete-word-for-word/
* text expansion / abbreviations https://vimtricks.substack.com/p/vimtrick-type-less-with-abbreviations http://vimcasts.org/episodes/enhanced-abbreviations-with-abolish/
* copilot https://www.youtube.com/watch?v=7k0KZsheLP4

## search

🗄 `shell.md` filter, nav
📚
* Neil modern ch. 3
* Neil practical ch. 18

OPEN FILE AT
* _mark_: bookmark w/in file https://vimtricks.com/p/bookmark-frequent-locations/ 📙 Neil practical [8.131,9.141]
* either local to buffer or global across Vim https://www.youtube.com/watch?v=Qnos8aApa9g 7:45
* Harpoon = marks per project https://www.youtube.com/watch?v=Qnos8aApa9g 11:15
* section: `vim +/'## profile'`
* tag https://www.youtube.com/watch?v=pt36X1OJRG4 2:20
* line number https://www.youtube.com/watch?v=pt36X1OJRG4 2:45 https://stackoverflow.com/q/39232615/6813490 https://www.cyberciti.biz/faq/linux-unix-command-open-file-linenumber-function/ last line: `alias qu='vim "+normal G$" ~/Desktop/music-queue.md'` https://edunham.net/2015/01/29/vim_open_file_with_cursor_at_the_end.html https://www.youtube.com/watch?v=kAAGEx8deM8
* string https://www.youtube.com/watch?v=pt36X1OJRG4 3:15

---

* http://vimcasts.org/episodes/operating-on-search-matches-using-gn/
* subvert http://vimcasts.org/episodes/smart-search-with-subvert/ http://vimcasts.org/episodes/supercharged-substitution-with-subvert/
❓ Vim emulation seems to default to smart-case like ripgrep but Vim itself no
https://vimtricks.com/p/navigating-around-the-screen/

search 📙 Neil practical ch. 13
* https://vimtricks.substack.com/p/vimtrick-search-project-for-current
* previous search: `/` `ctrl p` https://vi.stackexchange.com/a/10340
* _start_: `/` [PV 10.51]
* _n/p_: `n`/`N`
* _under cursor - n/p_: `*`/`#`
* _smartcase_: only case sensitive if query contains caps; ignore with `\query\C` https://stackoverflow.com/a/2287449
* clear highlight https://vimtricks.com/p/clear-search-highlight/

## viz

🗄 `km.md` notes

HIGHLIGHT GROUPS
* syntax files: fs location `$VIMRUNTIME/syntax` https://neovim.io/doc/user/syntax.html
* Markdown syntax https://github.com/neovim/neovim/blob/master/runtime/syntax/markdown.vim https://vim.fandom.com/wiki/Creating_your_own_syntax_files
* _highlight group_: per-language group (e.g. keywords in Python, headers in Markdown) https://alvinalexander.com/linux/vi-vim-editor-color-scheme-syntax/
* `:help highlight-groups` `:highlight`
* `:Inspect`: view highlight group under cursor in Neovim
* `:so $VIMRUNTIME/syntax/hitest.vim`: view all highlight groups for theme https://jordanelver.co.uk/blog/2015/05/27/working-with-vim-colorschemes/
* user-defined can be cleared by colorscheme https://jdhao.github.io/2020/09/22/highlight_groups_cleared_in_nvim/

MARKDOWN SYNTAX HIGHLIGHTING
> could you copy old Noctis theme and get it to work for newer VSC version?
* ❓ can you do this another way instead of augroups https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-colors.md
* need to use augroup https://www.reddit.com/r/vim/comments/dgbvw4/how_can_i_have_italic_keywords_etc_in_neovim_like/ https://kewbi.sh/blog/posts/230807/
* thought I needed a font that supports italics (Hack) but Fira worked https://www.reddit.com/r/neovim/comments/zan566/font_in_italics_is_displayed_wrong/
* iTerm supports italics https://weibeld.net/terminals-and-shells/italics.html https://alex.pearwin.com/2014/05/italics-in-iterm2-vim-tmux/ https://sookocheff.com/post/vim/italics/
* `:echo $TERM` -> `xterm-256color` (in Neovim, from iTerm, during Git commit)
* `markdownBlockquote` marker maps to `Comment` but not text itself https://github.com/neovim/neovim/blob/master/runtime/syntax/markdown.vim https://www.reddit.com/r/neovim/comments/ydsx60/bold_and_italics_not_working_with_markdown_on/
* thought it was catppuccin's fault https://github.com/catppuccin/nvim/issues/620
- [ ] bold headers https://arnaudr.io/2020/08/17/modify-vim-syntax-files-for-your-taste/ https://neovim.io/doc/user/syntax.html#%3Asyn-files
- [ ] syntax highlighting https://vimtricks.com/p/highlight-syntax-inside-markdown/ https://kewbi.sh/blog/posts/230807/ https://kewbi.sh/blog/posts/200913/
```vimrc
let g:markdown_fenced_languages = ['html', 'python', 'ruby', 'vim']
```
- [ ] list: separate colors for angle bracket https://neovim.io/doc/user/usr_27.html#usr_27.txt https://regex101.com/r/8EPiOR/1 https://stackoverflow.com/questions/19193251/regex-to-get-the-words-after-matching-string https://stackoverflow.com/questions/13542950/support-of-k-in-regex https://regexone.com/lesson/wildcards_dot?
- [ ] comment: separate colors for asterisk

ZA
* highlight TODO/FIXME/NOTE https://switowski.com/blog/plugins-for-python-in-vscode/
* devicons ✅ https://github.com/nvim-tree/nvim-web-devicons https://github.com/alexpasmantier/rust-devicons
* highlight current line: Rigel https://github.com/junegunn/limelight.vim
* dim other code blocks https://github.com/folke/twilight.nvim Markdown preview https://github.com/junegunn/goyo.vim https://www.youtube.com/watch?v=zbguTldYkCw
* _line number mode_: relative or absolute https://vimtricks.substack.com/p/vimtrick-toggle-line-number-mode
* _statusline_: display Vim mode, Git branch; lualine https://github.com/nvim-lualine/lualine.nvim alternatives https://github.com/itchyny/lightline.vim https://github.com/vim-airline/vim-airline https://github.com/nvimdev/galaxyline.nvim https://github.com/powerline/powerline BYO https://jdhao.github.io/2019/11/03/vim_custom_statusline https://kadekillary.work/posts/statusline-vim/ https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-statusline.md
> does Lualine work with Rigel?

# 🟨 ZA

> open help in new tab `:tab help $TOPIC` https://www.youtube.com/watch?v=ZlyiNuxlkJY 1:45
* installation: M1 macs come with Vim installed; `vim --version` https://www.vim.org/download.php

HELP https://neovim.io/doc/user/usr_02.html#help-summary
* https://vimtricks.substack.com/p/vimtricks-help-powerup
* full screen https://vi.stackexchange.com/questions/358/how-to-full-screen-browse-vim-help
* use Telescope https://www.youtube.com/watch?v=prnrwpOEsmo 20:00
* notifications https://github.com/vigoux/notifier.nvim https://github.com/folke/noice.nvim https://github.com/j-hui/fidget.nvim

NEOVIM
* vs. VS Code: can run in terminal, more customizable, modal https://www.reddit.com/r/neovim/comments/15c7al9/why_turn_neovim_into_vscode/
* installation: Homebrew (requires macOS > 10.14) 📙 Neil modern [5]
* design: run tasks async, Lua for scripting https://github.com/nvim-lua/plenary.nvim can also use Python to script https://mkaz.blog/code/neovim-plugin-python
> Bram's comparison is Vi, Neovim teams' comparison is VS Code. https://news.ycombinator.com/item?id=31936725

## config

📚
* Neil modern ch. 7
* Neil practical appendix
🔗
* https://github.com/romainl/idiomatic-vimrc
* https://github.com/tpope/vim-sensible
* https://github.com/nvim-lua/kickstart.nvim/blob/master/init.lua

Neovim just too fragile? https://www.youtube.com/watch?v=G1_Y5hLTfgw
> Every now and then I would update a plugin in Neovim and everything would break, and I would have to spend time fixing it instead of getting work done. This resulted in slimming down my config more and more, but there was still so much that went into making all the basics work. I stuck with it because it was still better than using VSCode, which I did try for a two week sprint to see if it could be any better. It was also key to a terminal based workflow that other editors couldn’t really match. The sentiment started to shift again not too long ago as I started working in some really large code bases, and boy Neovim was struggling. I would have random hang ups, frozen screens, stuff that just drove me nuts when productivity was king. I tried switching to other terminal emulators too such as Alacritty and Wezterm but it didn’t help much. https://stevedylan.dev/posts/leaving-neovim-for-zed/

NEOVIM SETUPS
* DIY https://www.youtube.com/watch?v=x__SZUuLOxw https://www.youtube.com/playlist?list=PLsz00TDipIffreIaUNk64KxTIkQaGguqn https://www.youtube.com/watch?v=6pAG3BHurdM
* _Astro_: 🎯 12k stars; strong maintainer https://github.com/mehalter https://github.com/AstroNvim/AstroNvim https://zackproser.com/blog/astronvim-overview
* _LazyVim_: 15k stars https://www.lazyvim.org/
* _Lunar_: 17.5k stars; more open issues, heavy setup (req: npm, cargo, rg) https://www.lunarvim.org/
* _NVChad_: 🎯 23.5 stars https://nvchad.com/
* PYthon setup https://www.youtube.com/watch?v=4BnVeOUeZxc
* still have to do the hard part yourself?
> Once the binaries are installed, you will have to configure them to properly work with LSP, conform.nvim, nvim-lint, nvim-dap etc. It depends on what you installed. NvChad does not provide any language configuration aside from lua. https://nvchad.com/docs/config/lsp/

NEOVIM
* files: `init.lua`, `init.vim` 📙 Neil modern [6] https://neovim.io/doc/user/starting.html#init.vim
* debug: `:checkhealth` http://vimcasts.org/episodes/neovim-checkhealth/
* fs
```sh
#~/.config/nvim https://neovim.io/doc/user/starting.html#standard-path
├── init.lua
├── lua/$DIR/  # https://github.com/mrnugget/vimconfig https://www.youtube.com/watch?v=hY5-Q6NxQgY
│   └── keymap.lua
│   └── option.lua
```
* Vimscript -> Lua  https://www.youtube.com/watch?v=hY5-Q6NxQgY 7:15 https://www.youtube.com/watch?v=prnrwpOEsmo
```lua
--- CMDS
vim.cmd[[colorscheme tokyonight]]  -- colorscheme tokyonight

-- VARIABLES
vim g.foo = 'im globally available' -- let g:foo = 'im globally available'

-- OPTIONS
vim.opt.shiftwidth = 2 -- set shiftwidth=2

-- KEYMAPS
vim.api.nvim_set_keymap() -- :noremap
```

OPTIONS 🔍 `:help options`
* defaults https://neovim.io/doc/user/vim_diff.html#nvim-defaults
* set: vimrc `set $OPT` exec `:set $OPT`
* view non-default settings: `:set`
* view source of setting: `:verbose set <value>`
* view available settings: `:options`
* `hidden`: allow switch to diff buffer before write https://vimtricks.com/p/what-is-set-hidden/
* `nocompatible`: disable Vi compatability; default since Vim 8 https://vi.stackexchange.com/q/25149
* `syntax enable`: on by default in neovim https://www.reddit.com/r/neovim/comments/nhwkbs/comment/gyyl1zl/

PATHS
* _VIMRUNTIME_: Vim system files
* `:echo $VIMRUNTIME` (mbp14 `/usr/local/share/vim/vim82` air22 `$HOMEBREW/neovim/$VERSION/share/nvim/runtime`) https://vim.fandom.com/wiki/Understanding_VIMRUNTIME
* _runtimepath (rtp)_: user config https://neovim.io/doc/user/syntax.html#mysyntaxfile
* `:echo %rpt` https://neovim.io/doc/user/options.html https://stackoverflow.com/q/14248335
* `autoload`: scripts; src before anything else, can use in .vimrc https://stackoverflow.com/a/59609961
* `ftplugin`: conf per filetype https://stackoverflow.com/a/59609961 https://vimtricks.com/p/per-file-type-configs/

VIMRC
* `~/.vimrc`: user vimrc
* user backup: `~/.vim/vimrc` 💻 `vim --version`
* base vimrc: `$VIMRUNTIME/defaults.vim` 💻 `vim --version`
* src user w/ no config: `vim -u NONE`, `nvim --clean` 📙 Neil practical [xxiv] https://vi.stackexchange.com/a/11127
* src alternate location: `vim -u $FILEPATH`, set `MYVIMRC` https://stackoverflow.com/a/4618219 https://stackoverflow.com/a/4618301 📙 Neil practical [xxiv]
* src from CWD: https://vimtricks.com/p/local-vimrc-files/
```sh
# .vim/
├── init              # https://tuckerchapman.com/posts/vimrc_organization/
│   └── func.vimrc    # custom func
│   └── leader.vimrc  # leader cmd
│   └── opt.vimrc     # core options
│   └── plug.vimrc    # load plugins, set plugin settings
```
```vimrc
source $HOME/.vim/init/plug.vimrc
source $HOME/.vim/init/core.vimrc
source $HOME/.vim/init/func.vimrc
source $HOME/.vim/init/leader.vimrc
```

MAPPINGS
* reminders https://github.com/folke/which-key.nvim
* `:noremap`: non-recursive i.e. mapping will just use the cmd you defined https://vi.stackexchange.com/a/282
* `:map`: recursive i.e. mapping will use already existing mappings if available
* don't use TAB 📙 Neil practical [9.137]
* _leader key_: namespace user-defined cmd 📙 Neil practical [8.122] https://stackoverflow.com/a/23503958
* can set multiple https://tuckerchapman.com/posts/how-to-use-the-vim-leader-key/
* print: `:echo mapleader` (`E121` = mapped to `\`) https://vi.stackexchange.com/a/282
* `timeoutlen`: time to type cmd after hitting leader key https://tuckerchapman.com/posts/how-to-use-the-vim-leader-key/
* to `SPACE` https://www.youtube.com/watch?v=435-amtVYJ8 5:30
* to `,` https://news.ycombinator.com/item?id=24287951 📙 Neil modern [xiv] practical [8.122]

ZA
* perf: `nv --startuptime out.log` https://www.youtube.com/watch?v=28FmViFye2I
* define variable: `let $SCOPE:$NAME = $MAPPING` e.g. `let g:foo = 'im globally available` https://vi.stackexchange.com/a/282 https://www.youtube.com/watch?v=prnrwpOEsmo 13:45
* variables: `$VISUAL` (for Git), `$VIM_CONFIG`, `$VIM_DATA` 📙 Neil modern [6-7]
* clipboard 📙 Neil modern [8] https://neovim.io/doc/user/provider.html#provider-clipboard
* Python support 📙 Neil modern [8] https://neovim.io/doc/user/provider.html#provider-python https://github.com/LunarVim/Neovim-from-scratch
* _modeline_: config for individual file 📙 Neil practical [xxv]
* _autocommand_: hook 📙 Neil practical [306] modern [105]
* have to wrap in `vim.cmd` in Lua https://www.youtube.com/watch?v=prnrwpOEsmo 25:45
```sh
# on Bufread, set scrolloff
:autocmd BufRead /Users/zach/Desktop/zvmac/notes/sw/za/industry.md set scrolloff=999
# set file type https://www.youtube.com/watch?v=hrbV5WGxxdY
:autocmd BufRead .*aliases set ft=sh
```
* _augroup_: group of autocommands 📙 Neil practical ch. 11-14
```sh
augroup foo
  autocmd!  # rm all autocmds for the event and file pattern from the default autocmd-group and sets new autocmd for this event/pattern
augroup END
```

---

* http://vimcasts.org/episodes/creating-repeatable-mappings-with-repeat-vim/
* http://vimcasts.org/episodes/creating-mappings-that-accept-a-count/
* help https://www.youtube.com/watch?v=BdoizYjJHis
* search https://vimtricks.substack.com/p/vimtrick-search-your-mappings

## plugins

📙 Neil modern ch. 2
🗄 `shell.md` userland
🔍
* https://vimawesome.com/
* https://github.com/rockerBOO/awesome-neovim

MGMT 📙 Neil modern ch. 2
* _vim-plug_: ✅ concise syntax https://github.com/junegunn/vim-plug
* plugin dir: Vim `~/.vim/plugged` Neovim `.local/share/nvim/plugged`
* install plugins: `:PlugInstall`
* uninstall plugins: remove from plugin file, `:PlugClean`
* using w/ `init.lua` https://stackoverflow.com/a/74344959
* installation
```sh
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```
* fs
```sh
$HOME/.config/nvim
├── init.lua
├── lua/zv
│   └── catppuccin.lua
│   └── keymap.lua
```
* _lazy.nvim_: verbose syntax, good UI https://github.com/folke/lazy.nvim https://www.youtube.com/watch?v=28FmViFye2I https://www.youtube.com/watch?v=6mxWayq-s9I
* succeeded packer https://github.com/wbthomason/packer.nvim
* _minpac_: built-in for Vim 8/Neovim https://github.com/k-takata/minpac https://danielmiessler.com/p/vim-configuration-update-2019-version
* gets `runtimepath` for free but less features than full pkg managers 📙 Neil modern [18,21]
> I'm actually under the impression that most popular third party package managers are actually a good deal more feature-rich than the new built-in one. I think the new built-in package manager is actually more useful when looked at as a more modern backend for the third party ones to use going forward rather than a full replacement. https://www.reddit.com/r/vim/comments/6x64oh/comment/dmdfgq8/
* _built-in_: just `git clone` to file location https://vimtricks.substack.com/p/vimtrick-plugin-installation
* reads from: manually config (`:packadd plugin-name`) default (`~/.vim/pack/*/start`)
```sh
├── $HOME/.vim/pack
│   └── color
│   └──── start
│   └────── pkg1
│   └────── pkg2
│   └── git
│   └──── start
│   └────── pkg3
│   └────── pkg4
```
* _pathogen_: ❌ Tim Pope says to just use built-in

SEMANTICS
* _script_: file extending Vim functionality 📙 Neil modern [11]
* howto source 📙 Neil modern [12]
* _package_: dir containing plugin(s) 📙 Neil modern [11]
* placed in `$VIM_CONFIG/pack` 📙 Neil modern [13]
* _plugin_: Vimscript pkg loaded when Vim starts
* some come pre-installed e.g. netrw 📙 Neil practical [7.104]
* install: add to `runtimepath` 📙 Neil modern [12]
* can impl using other languages e.g. Python https://www.youtube.com/watch?v=vMAeYp8mX_M
* scope: global, filetype (aka `ftplugin` https://www.swamphogg.com/2015/vim-setup/ https://thoughtbot.com/upcase/videos/intro-to-dotfiles)
