# ⛩️

## 参考

🔍
* https://www.commandlinefu.com
* https://explainshell.com/ https://github.com/akavel/up
🗄
* `applications.md` utils
* `db.md` utils
* `git.md` utils
* `linux.md` denv
📚
* Barrett https://www.amazon.com/gp/product/1098113403 https://fabiensanglard.net/bash/
* Evans shell
* Shotts linux command line https://www.linuxcommand.org/tlcl.php
* Stutz cookbook

## 进步

CLEAN UP FASTER
* _tee_: view output https://www.youtube.com/watch?v=NsAUBict1Aw
```sh
# https://github.com/zachvalenta/capp-denv-bin
jq -r '.data.user.contributionsCollection.contributionCalendar.weeks[].contributionDays[] | "\(.date): \(.contributionCount)"' | tee /dev/tty
```
* _try_: view files that command touches https://github.com/binpash/try

CLEAN UP
* _ffmpeg_: video encoding, file format conversion https://www.youtube.com/watch?v=MPV7JXTWPWI https://ffmpeg.guide/ https://img.ly/blog/ultimate-guide-to-ffmpeg/ https://drewdevault.com/2022/10/12/In-praise-of-ffmpeg.html https://news.ycombinator.com/item?id=42695547
* used by: Neovim
* _imgcat_: render img in terminal https://news.ycombinator.com/item?id=23319272
* weather: https://github.com/chubin/wttr.in https://github.com/fcambus/ansiweather https://pirateweather.net/ https://git.sr.ht/~timharek/yr
* Wikipedia https://github.com/yashsinghcodes/wik

* _24_: forced switch to eza, try difftastic, monitoring (tqdm, dust, procs, havn), uniq, get television working as reasonable substitute for text search in VS Code
* _20_: broot
* _19_: try out eza, z, fish, tig, fzf, ranger, ripgrep

# 📄 FILE

* file/dir name linter https://github.com/loeffel-io/ls-lint https://ls-lint.org/

FILE NAME EDITING
* file manager (nnn, ranger, et al.)
* vimv https://news.ycombinator.com/item?id=13890944 https://github.com/thameera/vimv
* https://github.com/yaa110/nomino
* visidata https://www.visidata.org/blog/2020/ten/
* `fne` (bulk, dry run, default for youtube-dl)

## diff

🗄️
* `algos.md` edit distance
* `protocols.md` JSON

* tree walkers
```sh
# Are there any CLI/TUI tools to diff directories? I don't need to diff file contents, just whether the file is there or not. The directories are arbitrarily nested.

diff --brief --recursive dir1 dir2
rsync -av --dry-run --ignore-existing dir1/ dir2/

fd --type f . dir1 > dir1_files.txt
fd --type f . dir2 > dir2_files.txt
diff dir1_files.txt dir2_files.txt
```
* BeyondCompare https://scootersoftware.com/ https://news.ycombinator.com/item?id=22850711
* _filecmp_: https://www.pythonmorsels.com/cli-tools/#filecmp https://chatgpt.com/c/5abbb7b1-ab77-4340-9d0d-d77de0d5ebd6
```sh
$ python -m filecmp dir1 dir2
```
* _diff_: https://danyspin97.org/blog/colorize-your-cli/
* _difftastic_: diff + syntax https://github.com/Wilfred/difftastic https://www.nathaniel.ai/myers-diff
* _vimdiff_: `vim -d <file1> <file2>` https://stackoverflow.com/a/113328/6813490
* wraps Vim's diff mode for use in other tools, notably Git's mergetool https://vi.stackexchange.com/a/626 https://www.youtube.com/watch?v=kFVjoIish0E

## find (fd)

FIND 📜 https://man7.org/linux/man-pages/man1/find.1.html
```sh
find . -type f -exec chmod 644 {} +  # mv file perms
find . -name ".DS_Store" | wc -l  # list all filename
find . -name ".DS_Store" -exec rm {} +  # rm all filename
```

FD 📜 https://github.com/sharkdp/fd
```sh
-E <exclude>
-HI  # include hidden/.gitignore https://github.com/sharkdp/fd#fd-does-not-find-my-file
-d <depth>

wc -l <file>  # lines in file
ls | wc -l    # files in dir
# world count from all files in subdirectory (use scc for lines)
fd -t f | xargs bat | wc -w
find . -type f | xargs wc -w | tail -1  # https://stackoverflow.com/a/35559868
# world count from all files in specified subdirectory
fd . "dir1/" "dir2/" -t f | xargs bat | wc -w
fd . "sw/" "za/" -t f | xargs bat | wc -w  # 226693

# https://missing.csail.mit.edu/2020/shell-tools/
# Delete all files with .tmp extension
find . -name '*.tmp' -exec rm {} \;
# Find all PNG files and convert them to JPG
find . -name '*.png' -exec convert {} {}.jpg \;

# directory depth (~/Desktop/zvmac/materials/za) https://unix.stackexchange.com/a/369458/331460
$ find yuyan -type d | wc -l  # 15
$ find business -type d | wc -l  # 1
```

ALTERNATIVES
* https://github.com/kashav/fsql
* https://github.com/darrenldl/docfd
* fselect https://github.com/jhspetersson/fselect
```sh
# ordering
fselect path from /tmp order by size desc, name
# music
fselect duration, path from /home/user/music where genre = Rap and bitrate = 320 and mp3_year lt 2000  
fselect path, mime from /home/user where is_audio = 1
```

## fuzzy find

🗄️
* grep
* `algos.md` matching
* `vim.md` fuzzy find

### 🌸 fzf

📜 https://github.com/junegunn/fzf
🧠 https://chatgpt.com/c/674624fd-2084-8004-bbf4-5de92b06f1ca
> fzf is just a Unix filter https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/

USES https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff
* file preview/open aka picker https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-pick.md
> can replace broot
* autojump
> can replace aliases

---

* https://www.youtube.com/watch?v=mmqDYw9C30I
* used by dbcli https://github.com/amjith/fuzzyfinder
https://github.com/peco/peco
https://www.youtube.com/watch?v=MvLQor1Ck3M
* https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
> As well as filtering the list of matches, the fuzzy finder also sorts the results using a ranking algorithm 📙 Neil modern [3.2   6]

* https://jvns.ca/blog/2023/08/08/what-helps-people-get-comfortable-on-the-command-line-/
* https://news.ycombinator.com/item?id=35248098
* setup using vim, bat, rg, fzf https://www.youtube.com/watch?v=aLMepxvUj4s
> you should finish Vim config and plugin mgmt and Neovim before doing this
* find all files containing text w/ rg, fzf for filter, bat for preview matches https://stackoverflow.com/questions/61740910/how-do-i-fuzzy-find-all-files-containing-specific-text-using-ripgrep-and-fzf-and
* seems like more documentation on how to do this within Vim https://sidneyliebrand.medium.com/how-fzf-and-ripgrep-improved-my-workflow-61c7ca212861 https://www.youtube.com/watch?v=fP_ckZ30gbs https://www.youtube.com/watch?v=loNdGAnKEf8
```sh
# https://www.linuxuprising.com/2021/03/a-quick-introduction-to-fzf-interactive.html
fzf --preview 'bat --style=numbers --color=always --line-range :500 {}'
```
* config https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
* select git branches https://seb.jambor.dev/posts/improving-shell-workflows-with-fzf
* can be used to replace broot file preview https://www.youtube.com/watch?v=aLMepxvUj4s
* alternatives: https://github.com/mptre/pick https://github.com/facebook/PathPicker https://github.com/lotabout/skim
* uses `find` under the hood https://github.com/junegunn/fzf/issues/1625#issuecomment-507674106
* as broot alternative (cd to dir of file) https://github.com/junegunn/fzf/wiki/Examples#changing-directory https://mike.place/2017/fzf-fd/
```sh
# cdf - cd into the directory of the selected file, suggested by @harelba and @dimonomid:
cdf() {
   local file
   local dir
   file=$(fzf +m -q "$1") && dir=$(dirname "$file") && cd "$dir"
}
```
* https://seb.jambor.dev/posts/improving-shell-workflows-with-fzf/
* can use to cd w/ `alt c` although broot does better here https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
* can use for tab completion w/ `<cmd>**` https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/ cant figure out yet how to ignore hidden dir in music-usb https://github.com/junegunn/fzf.vim/issues/453#issuecomment-526791474
* ignore files https://github.com/junegunn/fzf/issues/1625#issuecomment-507674106
* _alternatives_: dmenu https://eli.thegreenplace.net/2018/command-line-autocomplete-for-go-documentation/
* `--preview` unable to use the preview command despite following installation instructions https://github.com/junegunn/fzf#using-homebrew-or-linuxbrew https://github.com/junegunn/fzf/issues/1743 📍 https://github.com/junegunn/fzf/issues/1743#issuecomment-593052202
* _keybindings_: Emacs; ctrl j/k to scroll https://github.com/junegunn/fzf/issues/1716#issuecomment-542756200 but just type a few more char https://github.com/junegunn/fzf/issues/1716#issuecomment-542784884 more scroll bindings https://github.com/junegunn/fzf.vim/issues/211#issuecomment-497943378 https://github.com/junegunn/fzf.vim/issues/358#issuecomment-296737223 https://github.com/junegunn/fzf/blob/master/CHANGELOG.md#0152
* _Vim_: 🗄 `fzf.log`

### 🔭 Telescope

📜 https://github.com/nvim-telescope/telescope.nvim

---

https://www.youtube.com/watch?v=OhnLevLpGB4
https://www.youtube.com/watch?v=indguFY7wJ0

https://github.com/nvim-telescope/telescope.nvim 🗄 `shell.md` explorer

```sh
# https://github.com/nvim-telescope/telescope.nvim/blob/master/lua/telescope/mappings.lua
# 📍 update mappings like this https://github.com/malob/nixpkgs/blob/bc3924254db722ce5d1e44389e0702ddf3398e60/configs/nvim/lua/malo/telescope-nvim.lua#L22

select_horizontal/vertical  # open in split
select_tab                  # open in tab
select_tab_drop             # open in new tab, only available on master https://github.com/nvim-telescope/telescope.nvim/issues/2799
```
* semantics: picker = function, sorter = algo for sorting results, previewer = preview pane
* `select_tab_drop` only on master https://github.com/nvim-telescope/telescope.nvim/issues/2799
* theme https://www.reddit.com/r/neovim/comments/xcsatv/how_can_i_configure_telescope_to_look_like_this/
* layout https://github.com/nvim-telescope/telescope.nvim/blob/master/lua/telescope/pickers/layout_strategies.lua
* open Telescope on start https://www.youtube.com/watch?v=qN6BuJpsFbQ https://neovim.io/doc/user/autocmd.html#autocmd-define https://www.reddit.com/r/neovim/comments/13b7kfq/how_execute_a_command_at_start_nvim/ https://www.reddit.com/r/neovim/comments/zco47a/open_neovim_into_folder_with_telescope_open_in/
* result window (breadcrumb filenames, no column/line number), `--follow` coupled to others options
* alternatives: https://github.com/wincent/command-t https://github.com/ctrlpvim/ctrlp.vim https://github.com/junegunn/fzf.vim OOB https://www.youtube.com/watch?v=XA2WjJbmmoM 06:45
* Vim native commands
```sh
:e path/to/file  # open
:b  # fuzzy find https://drewdevault.com/2020/12/12/Shell-literacy.html
:bp # open previous
:e . # list
:pwd # get CWD
:cd path/to/dir # set CWD; Vim adopts CWD from shell 📙 Neil practical [7.100]
# create file/dir https://vimtricks.com/p/creating-files-and-directories/
```

### 📺 Television

📜 https://github.com/alexpasmantier/television

CONFIG FILESYSTEM STRANGENESS
* originally [0.5.3] config (and logs) was `$HOME/Library/Application Support/com.television/config.toml`
* `$XDG_CONFIG_HOME` is empty = based on docs the config should be at `$HOME/.config/television/config.toml`
* I tried updating config and didn't register so I created `.config/television` and then config updates registered

THEME
* color theme didn't cover main pane https://github.com/alexpasmantier/television/issues/80
* false alarm by me https://github.com/alexpasmantier/television/issues/117

ZA
* ❌ actual search itself kinda bad e.g. can't find altair
* piping stdout to command https://github.com/alexpasmantier/television/issues/16#issuecomment-2558615942 https://github.com/zachvalenta/dotfiles-mini23/commit/7175670d734ca1362ecfd8204682d2dddb162847

---

> wish you could configure the preview pane to be bigger

CONFIG
* base: https://github.com/alexpasmantier/television/blob/main/.config/config.toml
grep https://github.com/darrenldl/docfd

## explorer

FEATURES
* nav via Vim
* nav via fuzzy find
* enter dir
* file operations
* file preview
* _file explorer_: nav
* _file manager_: explorer + operations https://github.com/mgunyho/tere

MAYBE
* _mini_: https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-files.md
* _nnn_: https://github.com/jarun/nnn
* _tere_: https://github.com/mgunyho/tere
* _xlpr_: https://github.com/sayanarijit/xplr https://news.ycombinator.com/item?id=33209020 batch file operations https://github.com/sayanarijit/map.xplr

NO
* BYO https://github.com/willmcgugan/terminal-tree
* _bt_: https://github.com/LeperGnome/bt
* _fff_: 💀 https://github.com/dylanaraps/fff/issues/135 
* _lf_: https://github.com/gokcehan/lf https://www.youtube.com/c/BrodieRobertson/search?query=lf
* _superfile_: can't enter dir https://github.com/MHNightCat/superfile `spf` as alias https://news.ycombinator.com/item?id=40323101
* _vifm_: https://github.com/vifm/vifm https://www.youtube.com/watch?v=RGOsE3UWqhI https://www.youtube.com/watch?v=6eyFXcyosu8
* _walk_: can't enter dir https://github.com/antonmedv/walk

### 🟦 broot

📜 https://dystroy.org/broot/ https://github.com/Canop/broot

THINGS I NEED TO DO
* file preview
* file open using $EDITOR

DESIGN
* ❓ file preview mode
* ✅ fast
* ❌ install problems
* ❌ config problems (iTerm re: `ALT`)

CONFIG https://dystroy.org/broot/conf_file/
* fs on personal `~/Library/Preferences/org.dystroy.broot`
* fs on work machines `~/.config/broot/conf.toml`
* default file now `conf.hjson` but can rm and use `conf.toml`
* broot will run exec on ALT ENTER
* mv focus to preview pane https://github.com/Canop/broot/issues/480 https://dystroy.org/broot/#preview-files

KEYBINDINGS
* preview file `alt p`
* close preview `alt q`
* quit `ctrl w`
* open file in default OS app `alt enter` https://github.com/Canop/broot/issues/86#issuecomment-573197384
* open file in $EDITOR `enter` https://dystroy.org/broot/tricks/#change-standard-file-opening

INSTALL
* shell function adds line to bash profile https://github.com/Canop/broot/issues/115
* Homebrew version might lag https://github.com/Canop/broot/issues/123
* reinstall: `broot --install`
* ❓ how to turn file preview on by default? https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
* set Vim as editor https://missing.csail.mit.edu/2020/editors/

### 🗄️ browsr

📜 https://github.com/juftin/browsr

DESIGN
* nice to have: file preview for binary (PDR, Excel)
* ✅ starts in file preview
> are you under-using broot in this respect?
* ❌ doesn't dynamically preview file
* ✅ cloud e.g. can use for Github repos, AWS S3 buckets, SFTP
* ❌ no file pick
* ❌ super slow to load
* ❌ bad keybindings: parent directory cmd goes to root instead of parent, no jless/VSC-esqe fold all option no Vim https://github.com/juftin/browsr/issues/15
* ❌ no search

### 🦆 yazi

📜 https://yazi-rs.github.io/
📹 https://www.youtube.com/watch?v=iKb3cHDD9hw

FILE OPS
* `SPACE`: select | unselect
* `x` cut (mark for mv)
* `p` paste
* `y` yank
> have to select multiple in order to yank
* `X` undo yank | cut
* `d` rm
* `o` open
> you can just enter a dir by quitting yazi in that dir!
> would like to config so that it works for both dropping to shell and file edit https://yazi-rs.github.io/docs/tips/#dropping-to-shell https://github.com/yazi-rs/plugins/tree/main/smart-enter.yazi https://yazi-rs.github.io/docs/tips/#smart-enter
* `a`: create file (dir end with `/`)
* `r`: mv

ZA
* scroll preview: `J|K`

CONFIG
```sh
├── .config/yazi
│   └── keymap.toml  # shell/yazi/keymap.toml
│   └── package.toml  # shell/yazi/plugins.toml
│   └── theme.toml  # shell/yazi/catppuccin.toml https://github.com/catppuccin/yazi
│   └── yazi.toml  # shell/yazi/config.toml
```
* `ya`: CLI to install plugins
* plugins https://yazi-rs.github.io/docs/cli/#package-manager
* dir icons https://github.com/sxyazi/yazi/issues/2148

---

TODO
* file operations https://www.youtube.com/watch?v=iKb3cHDD9hw
* PDF preview via poppler https://github.com/sxyazi/yazi

## jump (zoxide)

DESIGN
* pro `.bash_profile`: better for staples (e.g. `sw`), specify post-`cd` behavior
* pro jump: better for adhoc, ~25 fewer LOC in `.zprofile`, less time going through atuin
* BYO https://news.ycombinator.com/item?id=22853119

ZOXIDE 📜 https://github.com/ajeetdsouza/zoxide https://www.youtube.com/watch?v=mmqDYw9C30I
* storage: `/Users/zach/Library/Application Support/zoxide/db.zo`
* initial usage didn't work bc of user error on my part 🗄️ `os/denv.md` profiles
* if you really go all in you can just `alias cd = z` https://www.youtube.com/watch?v=aghxkpyRVDY
* 📍 integrates with yazi?
* ❌ no post-exit hook (to ls)

ALTERNATIVES
* _autojump_: 🎯 mature https://github.com/wting/autojump
* _shunpo_: https://github.com/egurapha/Shunpo
* _wd_: manually add https://github.com/mfaerevaag/wd
* _z_: https://github.com/rupa/z

## list

FEATURES
* config e.g. way to avoid repetition of eza commands in `.zprofile`
* `--total-size` overstates dir size 🗄️ `yin`
* icons
* file dimming
* link related files
* highlight outliers (size, last accessed)
* conditional logic (if in `yin`, use `ll` instead of `l`)

OPTIONS
* _exa_: 💀 kicked off Homebrew https://github.com/ogham/exa https://the.exa.website/
* _g_: 🎯 https://github.com/Equationzhao/g
* _logols_: 💀 https://github.com/Yash-Handa/logo-ls
* _lsd_: https://github.com/lsd-rs/lsd
* _pls_: 🎯 https://pls.cli.rs/ ability to group to solve repo cruft problem? https://pls.cli.rs/guides/paths/
> what I want: cruft, non-cruft, immediate files, dirs

TREE
* eza/exa
* _tre_: Rust https://github.com/dduan/tre
* _tree_: ignore multiple https://unix.stackexchange.com/a/47806/331460 https://superuser.com/questions/772567/how-to-get-tree-a-to-ignore-git-directories
```sh
# https://superuser.com/a/595699/728972
tree -if | grep <query>
```

---

| FEATURE                                 | TOOL    |
|-----------------------------------------|---------|
| icons                                   | eza     |
| file dim                                | eza     |
| file link related                       | ?       |
| highlight outlier (size, access date)   | ?       |

* `ls`: a (hidden files) l (perms) F (file type) S (size) t (sort on write timestamp); if there's a tenth character in the column `@` it’s something to do w/ ACL (access control list) on the file https://linux-audit.com/plus-sign-ls-output/
* exa will list `.gitignore` files with marker
```sh
.rw-r--r--@  459 zv_mac 14 Feb 12:02 -I accounts.md
.rw-r--r--@ 1.2k zv_mac 16 Feb 08:48 N- company.md
.rw-r--r--@ 4.8k zv_mac 16 Feb 08:49 N- eng.md
.rw-r--r--@ 2.5k zv_mac 16 Feb 07:57 N- onboarding.md
.rw-r--r--@ 9.4k zv_mac 16 Feb 09:28 N- payments.md
```
🎗 `exa` already handles a bunch of filetypes for you https://the.exa.website/features/colours
* `exa` w/ `.gitignore`: smart enough to ignore everything in `.gitignore` if it's in the root directory, but `exa --tree` won't, so you have to add `.DS_Store` et al. via `exa -I`   https://github.com/ogham/exa/issues/136 https://github.com/ogham/exa/issues/408
`fd`: doesn't need but could use exa if you wanted to https://github.com/sharkdp/fd/issues/222
`ls`: exa - color config https://the.exa.website/docs/colour-themes
`tree`: 1) use vivid https://github.com/sharkdp/vivid/issues/25 2) use exa's tree functionality https://the.exa.website/features/tree-view + exa color config https://the.exa.website/docs/colour-themes 
* tree can rm files as well https://codesolid.com/what-are-those-pyc-files-in-a-python-project/
```python
pyclean () {
        find . -type f -name "*.py[co]" -delete
        find . -type d -name "__pycache__" -delete
}
```

### 🪨 eza

---

* _eza_: ✅ Makefile icon broken, absentee maintainers? https://github.com/eza-community/eza https://github.com/eza-community/eza/pull/554
> 📍 do you not have this configged at all? also, theme support now?

### 🇲🇦 lla

📜 https://github.com/triyanox/lla

CMD
* size map `-S`
> doesn't work on large dirs (yin) or small (brand enablement)
* timeline `--timeline`
* git commit `-G`

CONFIG
```sh
├── $HOME/.config/lla
│   └── config.toml
│   └── themes
│   └──── catppuccin_mocha.toml
```
* previously broken build https://github.com/triyanox/lla/issues/47

---

TODO
* config
* plugins
* impl `.gitignore`

## watchers

* ⭐️ https://github.com/wtetsu/gaze
* watch sites https://github.com/vsoch/watchme/
* Golang impl https://github.com/cespare/reflex https://github.com/cortesi/modd
* exec code in response to fs change https://github.com/wtetsu/gaze https://github.com/watchexec/watchexec
* application code in Python https://github.com/gorakhargosh/watchdog
* _entr_: bad install https://calmcode.io/course/entr/introduction https://github.com/eradman/entr https://jvns.ca/blog/2020/06/28/entr/ https://github.com/eradman/entr/issues/45 http://eradman.com/posts/repeatable-workspaces.html
* _fswatch_: bad install https://github.com/emcrisostomo/fswatch https://slack.engineering/development-environments-at-slack/
* _LiveReload_: https://pythonbytes.fm/episodes/show/406/whats-on-django-tv-tonight https://livereload.readthedocs.io/en/latest/index.html https://gist.github.com/mikeckennedy/4e1378477a6d174aa8d59921f8db89c3
* _watch_: built-in https://calmcode.io/shorts/watch https://linux.die.net/man/1/watch https://nickjanetakis.com/blog/monitor-the-output-of-a-program-for-changes-using-the-watch-command
* _watchman_: shaky install https://facebook.github.io/watchman/ https://adamj.eu/tech/2021/01/20/efficient-reloading-in-djangos-runserver-with-watchman
* _hwatch_: https://github.com/blacknon/hwatch
* _viddy_: 🎯 https://github.com/sachaos/viddy

# 🔬 MONITORING

🗄️ `telemetry.md`

ARCHITECTURE
* `python -m platform` https://www.pythonmorsels.com/cli-tools/#platform
* _cpufetch_: https://github.com/Dr-Noob/cpufetch
* _neofetch_: https://github.com/dylanaraps/neofetch https://github.com/dylanaraps/pfetch

DASHBOARDS
* https://github.com/wtfutil/wtf
* https://github.com/Phantas0s/devdash
* https://github.com/gizak/termui

DATA
* _tar_: https://switowski.com/blog/favorite-mac-tools/
* _dd_: copy/rm data https://github.com/akavel/up
* _caligula_: dd alternative https://github.com/ifd3f/caligula

## disk (dust/df)

* _df_: ✅ view of mounts https://danyspin97.org/blog/colorize-your-cli/
* _du_: ✅
* _duf_: ✅ JSON https://github.com/muesli/duf
* _diskonaut_: treemap https://github.com/imsnif/diskonaut
* _du_: `du -sh $DIR` https://unix.stackexchange.com/a/185777
* _dusage_: https://github.com/mihaigalos/dusage
* _dust_: ✅ JSON https://github.com/bootandy/dust
```sh
├── Applications
├── Library
├── System
│   └── Volumes
│   └──── Data  # user files; symlinked to /Users/user/Documents?
│   └──── Preboot  # BIOS
│   └──── VM  # virtual memory swap files (manage memory usage)
│   └──── Update  # system updates
├── Users
│   └── Shared
│   └── ur-user
```
* _dysk_: 🎯 https://github.com/Canop/dysk
* _gdu_: catppuccin theme https://github.com/dundee/gdu https://github.com/catppuccin/catppuccin/discussions/1851
* _wiper_: https://github.com/ikebastuz/wiper
* _ncdu_: ✅ JSON `$HOME/.config/ncdu/config` https://dev.yorhel.nl/ncdu/man
> why diff versions (and much more deps) btw mini23 and air-capp? https://github.com/zachvalenta/logs-mini23/commit/e1945af0ccb30f5212feb8616ef10e6eca29e3ad https://github.com/zachvalenta/capp-denv-logs/commit/7ffaff08b1a9a63aa88b1e8eeef108b853341c98
> 📍 align config btw machines

## mem/CPU (ps/procs)

* features: JSON, aggregation per app
* alternatives: free (UNIX) top (macos), iTerm https://wompa.land/articles/iterm-status-bar
* _Activity Monitor_: macOS GUI
* _below_: 🎯 JSON https://github.com/facebookincubator/below no Homebrew https://github.com/facebookincubator/below/issues/8239
* _bottom_: 🎯 GUI https://github.com/ClementTsang/bottom
* _btop_: https://github.com/aristocratos/btop
* _dstat_: https://missing.csail.mit.edu/2019/machine-introspection/
* _glances_: ✅ JSON https://nicolargo.github.io/glances/ https://tech.marksblogg.com/top-htop-glances.html
* _gotop_: 🎯 JSON export https://github.com/xxxserxxx/gotop/issues/50 https://asciinema.org/a/spxxHKMf3MBR8OfUYwsbZurXq
* _htop_: https://tech.marksblogg.com/top-htop-glances.html
* _procs_: ✅ modes (snapshot, watch) ❓ how to sum cpu/mem across PID by app name https://github.com/dalance/procs
```sh
# how to reduce Chrome tab mem usage
procs iterm --sortd mem
procs --sortd mem | awk '{ print substr($0, 1, 100) }' | head -n 100 > $DENV_DIR/logs/sys-info/"$(date +'%y%m%d_%H%M%S').txt"
```
* _tiptop_: installed on capp machine https://github.com/nschloe/tiptop
* _vtop_: ❌ sudo https://github.com/MrRio/vtop
* _ytop_: 💀 https://github.com/cjbassi/ytop
* _zenith_: 🎯 https://github.com/bvaisvil/zenith

---

* see what's running `ps aux | grep crond` https://missing.csail.mit.edu/2019/automation/
* `lsof`: open files https://danielmiessler.com/study/lsof/ GUI https://github.com/sveinbjornt/Sloth
* _PID by port_: `lsof -i :<port>`
* _$CWD by PID_: `lsof -p <PID> | grep cwd` https://unix.stackexchange.com/a/94359/331460
* `pstree`: tree of processes
* pgrep https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
* `ps`: processes associated with current shell
* pgrep https://hacker-tools.github.io/shell/
* `ps -u`: associated with specific user
* `ps -e`: associated with all users
* `ps -f`: info on PPID
* `ps -ejH`: show trees

## ports (havn)

* _havn_: ✅ https://github.com/mrjackwills/havn
* _ss_: https://missing.csail.mit.edu/2019/machine-introspection/
> To figure out what network connections you have open, ss is the way to go. ss -t will show all open TCP connections. ss -tl will show all listening (i.e., server) ports on your system. -p will also include which process is using that connection, and -n will give you the raw port numbers.

---

https://simonwillison.net/2024/Dec/11/rob-cheung/

PORT SCAN / NETWORK MONITOR https://chatgpt.com/c/67252f81-b728-8004-974b-7a9a5c4dea2c 🗄️ `tcp-ip.md` network monitor
* control internet access for apps https://tripmode.ch/ https://www.obdev.at/products/littlesnitch/index.html
* port viewer https://github.com/allyring/pvw
* LAN port scanner nmap https://github.com/RustScan/RustScan https://github.com/aceberg/WatchYourLAN
* monitor, Slack notification on completion (or to Twilio) https://github.com/variadico/noti
* _bandwhich_: https://github.com/imsnif/bandwhich
* _rustscan_: https://github.com/RustScan/RustScan

## progress bars (tqdm)

❓ how does sqlite-utils do its countdown? https://github.com/zachvalenta/capp-datalab

LINUX
* _enlighten_: https://github.com/Rockhopper-Technologies/enlighten
* _progress_: estimate remaining time on coretuil execution https://sirupsen.com/progress
* _pv_: 🚧 couldn't get it to work with markitdown https://catonmat.net/unix-utilities-pipe-viewer Homebrew https://codeberg.org/a-j-wood/pv
```txt
The reason the progress bar in pv immediately goes to 100% is that pv doesn’t know the total size of the input when it is being piped directly. This often happens when pv processes a file in a streaming context without being able to assess its full size.

If the progress bar still immediately jumps to 100%, it's likely due to how markitdown interacts with the input stream. When a program reads from the standard input (stdin), it might consume the entire input immediately, bypassing pv's progress-tracking capability.

If the progress bar still jumps to 100% immediately, the issue might be related to how pv calculates and displays progress. When used in combination with certain tools, pv might not process the file linearly or as expected.
```
* color https://social.vivaldi.net/@ivarch/113659619955647945
```sh
gzip -c access.log > access.log.gz
$CMD $STDIN $STDOUT
pv $STDIN | $CMD $STDOUT

cat > copy.dat
$CMD $OPERATOR


cat bigfile.dat | pv > copy.dat
```

PYTHON
> how does pip do it? https://github.com/hynek/doc2dash
```python
if i % 100 == 0:
    progress = ((i + 1) / float(len(qd))) * 100.0
    print('%.2f%%' % progress)
```
* _alive_: https://github.com/rsalmei/alive-progress
* _rich_: 🎯 https://realpython.com/python-rich-package/ https://realpython.com/python-rich-package/#animating-activities-with-progress-bars
* _tqdm_: ✅ https://github.com/tqdm/tqdm https://calmcode.io/course/tqdm/files-and-descriptions
* can't figure out how to work with reading CSV in Polars
```python
# https://github.com/zachvalenta/capp-mpn-match
from tqdm import tqdm
for foo in tqdm(iterable, desc="reading something big"):
```

## psutil

📜 https://github.com/giampaolo/psutil https://matt.sh/netmatt#_what-if-we-replaced-90s-c-netstat-with-python

* overview
```txt
psutil is a cross-platform library for retrieving info about running processes and system utilization (CPU, memory, disks, network, sensors).
Key features:
* Process management: creation, termination, status
* System monitoring: CPU times, memory usage, disk I/O
* Sensor readings: battery, fans, temperature
* Network info: connections, interfaces, stats
Benefits over shell:
* More robust process identification
* Cross-platform
* Type safety
* Better error handling
```
* could use for `kcm` (need to fix the control flow there anyway)
```sh
import psutil

if "cmus" in (p.name() for p in psutil.process_iter()):
    [p for p in psutil.process_iter() if p.name() == "cmus"][0].kill()
else:
    Path.home().joinpath(".config/cmus/socket").unlink(missing_ok=True)
```

# ✏️ TEXT

---

* _fold_: https://blog.balthazar-rouberol.com/text-processing-in-the-shell#fold
* _fmt_: fmt stdout https://github.com/Idnan/bash-guide#f-fmt

## awk

📜 https://eradman.com/posts/awk-programming.html

SNIPPETS
```sh
# read first column from CSV
awk -F, '{print $1}' file.csv

# read column by name
awk -F, 'NR==1 {for (i=1; i<=NF; i++) if ($i == "NAME") col=i} NR > 1 {print $col}' example.csv

# trim line length, dynamic date
procs --sortd mem | awk '{ print substr($0, 1, 100) }' | head -n 100 > "procs_$(date +'%y%m%d_%H%M%S').txt"
```

ZA
* macOS version doesn't fully support multidimensional arrays

---

* _awk_: process columnar data https://missing.csail.mit.edu/2020/data-wrangling/ https://kadekillary.work/note/awk/ https://benhoyt.com/writings/goawk/ https://kadekillary.work/post/cli-4-ds/ https://neowaylabs.github.io/programming/unix-shell-for-data-scientists/ 📙 Kernighan https://github.com/thewhitetulip/awk-anti-textbook/ https://en.wikipedia.org/wiki/The_AWK_Programming_Language https://blog.jpalardy.com/posts/why-learn-awk/ https://gregable.com/2010/09/why-you-should-know-just-little-awk.html http://www.grymoire.com/Unix/Awk.html
* avoid by parsing stdout to JSON then using JSON query tool e.g jq https://github.com/kellyjonbrazil/jc https://www.thoughtworks.com/radar/tools?blipid=202203056
* versions: `awk- W version` (doesn't work on macOS) ; mawk (Ubuntu, Debian) gawk (other distro incl macOS)
* rm blank lines: `"NF"` https://stackoverflow.com/a/29549497
* sum: 🗄 `.bash_profile` agg
* get $PWD from path: `awk -F"/" '{print $NF}'` https://stackoverflow.com/a/17921589
* get last word in line https://stackoverflow.com/a/16617037
* sum series of numbers https://stackoverflow.com/a/28926450
```sh
# RM TRAILING N CHARS https://chatgpt.com/share/2575c4e4-94d8-4006-8cab-829142e787b2
echo 'eid,b_line,p_line,full_description,' | awk '{print substr($0, 1, length($0)-1)}'

# use awk 'control file' against input file
awk -f my_script.awk /etc/ntp.conf
# set delimiter
ifconfig foo | awk -F":" '/HWaddr/{print toupper($3 $4)}'
```
```aw
# BEGIN block (processed once) = clarify output, set delimiter ('file separator'), 
BEGIN { FS=":" ; print "username"}

{ print $1}# UNNAMED block = prints for each line 
mt ps | awk '{print $1}' # https://askubuntu.com/a/161803

# END block (processed once) = clarify output
END { print "TOTAL USERS: " NR}  # NR = num rows
```

## pager (bat)

🗄️ `git.md` tooling / pager
📜 https://github.com/sharkdp/bat

* `bat --config-dir`: `$HOME/.config/bat`
* `bat --config-file`: `$HOME/.config/bat/config`
```sh
├── .config/bat
│   └── config
│   └── themes  # catppuccin https://github.com/catppuccin/bat
```
* commands
```sh
# SPECIFY STDIN LANGUAGE
yaml2json .travis.yml | json_pp | bat -l json
# MULTIPLE
bat src/*.rs
# THEMES
bat --list-themes
```

---

* pretty pager that supports following https://github.com/noborus/ov

* _pager_: print file
* cat https://twobithistory.org/2018/11/12/cat.html
* bat https://github.com/sharkdp/bat
* less https://danyspin97.org/blog/colorize-your-cli/ https://github.com/noborus/ov
* https://github.com/sharkdp/bat#man https://danyspin97.org/blog/colorize-your-cli/ https://askubuntu.com/a/623996 🗄 `linux.md` man pages

* _create theme_: https://github.com/sharkdp/bat#adding-new-themes https://github.com/sharkdp/bat/blob/d65ae517dd868008ce72b37e30604e5480554571/.gitmodules
* _make default pager_: bp - `export MANPAGER=bat` https://askubuntu.com/a/679058
* doesn't deal w/ binary https://github.com/sharkdp/bat/issues/150 https://github.com/sharkdp/bat/issues/248
* [rm binary data from text file](https://unix.stackexchange.com/a/353420/331460) + [view binary data in text file](https://unix.stackexchange.com/a/353421/331460)
* can open multiple files 🗄 xargs
```sh
bat --line-range 227:236 $NOTES_DIR/sw/za/algos.md
```

## search (ripgrep)

🗄
* fuzzy find
* `vim.md` utils

ZA
* _rga_: PDFs, Microsoft Office https://github.com/phiresky/ripgrep-all https://pdfgrep.org/
* _srgn_: 🎯 alternative to LSP https://github.com/alexpovel/srgn https://www.youtube.com/watch?v=TRJo2-P9AEY
* _symbex_: Python symbols https://github.com/simonw/symbex

RG 📜 https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md
> 🚧 query `GIS` deson't return `science.md/geography/GIS` in domains repo; thought it was lack of config on `air-capp` but didn't solve
* `.rgignore`: to ignore a specific file
* `I`: don't output filename
* `N`: don't output line number
* `s`: case-sensitive 🗄 `.bash_profile` mq
* `l`: show filenames w/ matches 🗄 `.bash_profile` kba
* `U` multiline-mode, necessary for regex 🗄 `.bash_profile` mq
* conf: set fs in profile `RIPGREP_CONFIG_PATH` https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md#configuration-file
```sh
# SYNTAX
<query> <args> <dir>
# SEARCH HIDDEN FILES
--hidden
# FILES WITH MATCHES
<query> --files-with-matches
# SEE WHAT FILES WILL BE SEARCHED
<query> --files <dir>

###
# FILTER / GLOB https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md#manual-filtering-globs
# n.b. use single quotes on globs
# -uuu turn off automatic filtering https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md#automatic-filtering
###

# FILE TYPES
--type-list  # get file types
<query> -g '*.py'  # only file type
<query> -g '!*.toml'  # exclude file type

# GLOBBING
rg toil -g '*-tracking*'
rg bpython -g [Mm]akefile

# DIR
<query> -g 'src/*'  # only incl single dir
<query> -g 'src/*' ; <query> -g 'src/*' # only incl multiple dir
<query> -g '!jay/*'  # exclude dir
```

GREP 📙 Evans shell [5]
* flags: `i` (case insensitive) `n` (line numbers) `B/A` (context) `E` (regex/egrep) `F` (don't treat query as regex aka fgrep)
```sh
# syntax
$QUERY $PATH

# all files in directory
-r $QUERY *

# alias for colorize https://danyspin97.org/blog/colorize-your-cli/ https://github.com/arsham/blush
--color=auto

# multiple queries --> https://unix.stackexchange.com/a/37316
-E 'PROJECTS|venv' ~/.bash_profile
'^user' $PATH  # begins w/
```

## stream edit (sed)

---

🗄 `vim.md` argdo

https://github.com/SoptikHa2/desed
* _scooter_: https://github.com/thomasschafer/scooter
* _sed_: stream editor = filter/transform text
* _sd_: Rust rewrite https://github.com/chmln/sd
* rename symbol across files https://news.ycombinator.com/item?id=34071811
* rm newline `sed "s/\r$//" file.txt > out.txt`
* rm lines https://www.youtube.com/watch?v=Ix24Hh_SfO4
* 📍 use sed to replace 'board' w/ 'now' https://stackoverflow.com/a/4824742
* https://jvns.ca/blog/2018/05/11/batch-editing-files-with-ed/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#sed https://kadekillary.work/post/cli-4-ds/
* macOS version is BSD, which doesn't work with any further examples from article https://unix.stackexchange.com/a/13716/331460 https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux https://github.com/tanrax/maza-ad-blocking
* all but last line `sed \$d` https://stackoverflow.com/a/18127797/6813490
* syntax
```sh
sed $OPTIONS $COMMANDS $INPUT
sed '' BSD  # no cmd i.e. just send to stdout
```
* print range: `sed -n '1,5p' bsd.txt` (specific) `sed -n '1,5p' bsd.txt` (relative)

## string processing

🗄️ `data/analytics.md` miller, xsv
🔗 https://blog.balthazar-rouberol.com/text-processing-in-the-shell
💡 no editing in-place per Claude
```txt
No, standard Unix text processing tools like cat, join, and paste don't actually modify files in-place. They all output to stdout and can't directly modify their input files. That's why they're typically used with redirection (>) or in pipelines. Even sed -i (in-place edit) and perl -i actually work by creating a temporary file behind the scenes, though they hide this detail from the user. The fundamental issue is that Unix file operations can't simultaneously read from and write to the same file position. Any tool that appears to modify a file "in-place" is actually:

* creating a temporary file
* writing the modified content to it
* moving it over the original file

This is true for all the standard Unix text processing tools: sed, awk, cat, join, paste, cut, etc. The only true in-place modifications are at the byte level using tools like dd or through specific filesystem operations, but those aren't suitable for text processing tasks like what you're trying to do.
```

CHUNK
* _head/tail_: https://github.com/zachvalenta/interview-capp/blob/main/Makefile
```sh
$ tail -n +2 $FILE  # start from line 2
$ tail -n +42 $FILE  # start from line 42
```
* _split_: https://tech.marksblogg.com/importing-data-from-s3-into-redshift.html
```sh
split -l 100 $FILE
```

EDIT
* _echo_: create CSV header line
```sh
echo "manufacturer" > aaon.csv
```
* _cut_: 📍 rm columns https://blog.balthazar-rouberol.com/text-processing-in-the-shell#cut https://github.com/theryangeary/choose https://github.com/ibraheemdev/modern-unix
* _tr_: edit e.g. case, add newline https://shapeshed.com/unix-tr/ https://github.com/zachvalenta/interview-capp/blob/main/Makefile
```sh
$ cat example.txt | tr 'a-z' 'A-Z'  # uppercase
$ cat example.txt | tr ' ' '\n'  # replace spaces with newlines
$ cat example.txt | tr '\n' ','  # concat n lines into single comma-delineated line

# lowercase/snakecase CSV headers
{ 
  head -n1 foo.csv | tr '[:upper:]' '[:lower:]' | sed -E 's/[^a-z0-9,]+/_/g' ;
  tail -n +2 foo.csv;
} > tmp.csv
```

FILTER
* _look_: find words by prefix
* _uniq_: report/filter adjacent dupe lines i.e. need to use with `sort`
```sh
$ cat foo.txt

and one
and one
and two
and one
and two
and one, two, three

$ uniq foo.txt  # only filters line #2
$ sort foo.txt | uniq  # filters lines #2/4/5
$ sort foo.txt | uniq -c  # count occurences
$ sort foo.txt | uniq -d  # dupes to stdout
```

MERGE
* _cat_: combine sequentially
```sh
$ cat <(tail -n +2 aaon.csv) <(tail -n +2 baldor.csv)
```
* _join_: combine on join key
* 📍 understand how `-` works https://github.com/zachvalenta/capp-looker
```sh
$ join foo.txt bar.txt

1 apple red
2 banana yellow
3 cherry red
```
* _paste_: combine columns
```sh
$ paste -d, baz.txt qux.txt  # set delimiter
$ paste -d ','  # alt syntax

HY6O,HRHG
LL6N,5KQ7
57OZ,4LAS
```

ORDER
* _shuf_: not available on macOS but can replace with `sort -R`
* _sort_: LC_COLLATE: determine sort order https://unix.stackexchange.com/q/75341/331460
```sh
$ sort -n  # by numerical value
$ sort -R  # random; not always random for reason's I don't yet understand
```

# 🟨️ ZA

## coreutils

---

* _coreutils_: ls, rm, cat, et al. https://en.wikipedia.org/wiki/List_of_GNU_Core_Utilities_commands https://github.com/Gandalf-/coreutils
* aka userland https://bitfieldconsulting.com/golang/scripting
* Rust rewrites aka "modern UNIX" https://github.com/ibraheemdev/modern-unix https://github.com/ibraheemdev/modern-unix https://news.ycombinator.com/item?id=26396798 https://jvns.ca/blog/2022/04/12/a-list-of-new-ish--command-line-tools/ https://github.com/ibraheemdev/modern-Unix

CP
* dir: `cp -r <dir> <path/to>`
* dir but exclude `.git`_: `cmd --exclude=.git <source> <target>` https://stackoverflow.com/a/3672584
* dir contents: `cp -r <dir>/ <path/to>`

MAN PAGES
* _whereis_: search for executables and man page in system db https://github.com/Idnan/bash-guide#c-whereis
* _tldr_: cheatsheets https://github.com/tldr-pages/tldr/tree/master/pages https://github.com/dbrgn/tealdeer https://github.com/chubin/cheat.sh https://github.com/denisidoro/navi
* offline documentations https://devdocs.io/
> you can download plaintext of Python docs
* man (UNIX) vs. info (GNU) https://askubuntu.com/a/9332 man pages for systems calls as well (`sendfile`) [`evans-linux.pdf` 11]
* help: `man`, `info`, `whatis`, `man 2 <cmd>` (for system calls)
* man pages: following links (like at bottom of cmus manpage) https://unix.stackexchange.com/a/18161/331460 set pager `export MANPAGER=bat` https://askubuntu.com/a/679058

CORE
* versions: Linux uses GNU, macOS uses BSD (get w/ `brew install coreutils`) 📙 Evans shell [4]
* _file_: info on encoding, if executable
* _free_: disk space? free memory? `df` memory https://apple.stackexchange.com/q/4286/328389 or `duf` https://github.com/ibraheemdev/modern-unix `top` on macOS
* _bc_: do math on stdin https://missing.csail.mit.edu/2020/data-wrangling/
* _head_: 类似 SQL `limit` e.g. `ls <query> | head -4` or `kaiff` (`ls | sort -f | head -1 | xargs open`) https://stackoverflow.com/a/14510257/6813490
* _which_: search for executables on $PATH https://github.com/Idnan/bash-guide#d-which full path https://nil.wallyjones.com/what-shell-am-i-using/
*m_w_: who is logged in and what they're doing https://rachelbythebay.com/w/2018/03/26/w/

## clipboard

copy terminal output https://calmcode.io/course/cool-cli/yank

🗄️ Raycast

* manager https://github.com/Slackadays/Clipboard
* copy output: `<cmd> | pbcopy` https://github.com/Slackadays/Clipboard
* copy file: `pbcopy < ~/.ssh/id_rsa.pub`

## trash

🗄️ yazi

---

* https://github.com/nivekuil/rip https://hacker-tools.github.io/command-line/ https://github.com/umlx5h/gtrash https://news.ycombinator.com/item?id=41902864
* _gomi_: https://github.com/babarot/gomi
* _recoverpy_: https://github.com/PabloLec/RecoverPy
* _rm_: sends to `~/.Trash`; `i` prompt before each `R` answer yes to all prompts `rf` all recursively; alternatives
* _send2trash_: https://github.com/arsenetar/send2trash/issues https://github.com/arsenetar/send2trash/issues/56 
