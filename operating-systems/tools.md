# ⛩️

## 参考

📚
* Barrett https://www.amazon.com/gp/product/1098113403 https://fabiensanglard.net/bash/
* Evans shell
* Shotts linux command line https://www.linuxcommand.org/tlcl.php
* Stutz cookbook

## 进步

* _24_: forced switch to eza, try difftastic
* _20_: broot
* _19_: try out eza, z, fish, tig, fzf, ranger, ripgrep

# 📄 FILE

* file/dir name linter https://github.com/loeffel-io/ls-lint https://ls-lint.org/

FILE/DIR DIFF 🗄️ `protocols.md` JSON
* 🎯 https://www.pythonmorsels.com/cli-tools/#filecmp
* _vimdiff_: `vim -d <file1> <file2>` https://stackoverflow.com/a/113328/6813490
* wraps Vim's diff mode for use in other tools, notably Git's mergetool https://vi.stackexchange.com/a/626 https://www.youtube.com/watch?v=kFVjoIish0E
* _diff_: https://danyspin97.org/blog/colorize-your-cli/
* BeyondCompare https://scootersoftware.com/ https://news.ycombinator.com/item?id=22850711
* _difftastic_: diff + syntax https://github.com/Wilfred/difftastic https://www.nathaniel.ai/myers-diff

FILE NAME EDITING
* file manager (nnn, ranger, et al.)
* vimv https://news.ycombinator.com/item?id=13890944 https://github.com/thameera/vimv
* visidata https://www.visidata.org/blog/2020/ten/
* `fne` (bulk, dry run, default for youtube-dl)

FILE WATCHERS
* watch sites https://github.com/vsoch/watchme/
* Golang impl https://github.com/cespare/reflex https://github.com/cortesi/modd
* exec code in response to fs change https://github.com/wtetsu/gaze https://github.com/watchexec/watchexec
* application code in Python https://github.com/gorakhargosh/watchdog
* _entr_: bad install https://github.com/eradman/entr https://jvns.ca/blog/2020/06/28/entr/ https://github.com/eradman/entr/issues/45 http://eradman.com/posts/repeatable-workspaces.html
* _fswatch_: bad install https://github.com/emcrisostomo/fswatch https://slack.engineering/development-environments-at-slack/
* _LiveReload_: https://pythonbytes.fm/episodes/show/406/whats-on-django-tv-tonight https://livereload.readthedocs.io/en/latest/index.html https://gist.github.com/mikeckennedy/4e1378477a6d174aa8d59921f8db89c3
* _watch_: built-in https://linux.die.net/man/1/watch https://nickjanetakis.com/blog/monitor-the-output-of-a-program-for-changes-using-the-watch-command
* _watchman_: shaky install https://facebook.github.io/watchman/ https://adamj.eu/tech/2021/01/20/efficient-reloading-in-djangos-runserver-with-watchman
* _hwatch_: https://github.com/blacknon/hwatch
* _viddy_: 🎯 https://github.com/sachaos/viddy

## find (fd)

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

## explorer

ALTERNATIVES
* file explorer = TUI for file system e.g. Finder (mv, rm, preview); aka file browser, file manager
* _bt_: https://github.com/LeperGnome/bt
* _fff_: 💀 https://github.com/dylanaraps/fff/issues/135 
* _lf_: https://github.com/gokcehan/lf https://www.youtube.com/c/BrodieRobertson/search?query=lf
* _mini_: 🎯 https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-files.md
* _nnn_: https://github.com/jarun/nnn
* _telescope_: 🎯 https://github.com/nvim-telescope/telescope.nvim https://www.youtube.com/watch?v=OhnLevLpGB4 https://www.youtube.com/watch?v=indguFY7wJ0
* _superfile_: ❌ no way to enter directory you've navigated to https://github.com/MHNightCat/superfile https://news.ycombinator.com/item?id=40323101
* _vifm_: https://github.com/vifm/vifm https://www.youtube.com/watch?v=RGOsE3UWqhI https://www.youtube.com/watch?v=6eyFXcyosu8
* _walk_: ❌ no way to enter directory you've navigated to https://github.com/antonmedv/walk
* _xlpr_: 🎯 https://github.com/sayanarijit/xplr https://news.ycombinator.com/item?id=33209020
* _yazi_: 🎯 PDF preview via poppler https://github.com/sxyazi/yazi

### broot

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

### browsr

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

## jump

> currently do via aliases + atuin

* `.bash_profile` aliases
* BYO https://news.ycombinator.com/item?id=22853119
* _autojump_: 🎯 mature https://github.com/wting/autojump
* _wd_: manually add https://github.com/mfaerevaag/wd
* _z_: https://github.com/rupa/z
* _zoxide_: ❌ tried out and init in zsh didn't work, requires fzf https://github.com/ajeetdsouza/zoxide

## list (eza)

FEATURES
* config e.g. way to avoid repetition of eza commands in `.zprofile`
* icons
* file dimming
* link related files
* highlight outliers (size, last accessed)
* conditional logic (if in `yin`, use `ll` instead of `l`)

OPTIONS
* _exa_: ✅ https://github.com/ogham/exa https://the.exa.website/
* _eza_: ✅ Makefile icon broken, absentee maintainers? https://github.com/eza-community/eza https://github.com/eza-community/eza/pull/554
* _logols_: 💀 https://github.com/Yash-Handa/logo-ls
* _lsd_: 🎯 https://github.com/lsd-rs/lsd
* _pls_: 🎯 https://github.com/pls-rs/pls

TREE
* eza
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
# ✏️ TEXT

## fuzzy find (fzf)

🗄 `vim.md` fuzzy find
📜 https://github.com/junegunn/fzf
> fzf is just a Unix filter https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/

USES https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff
* file preview/open aka picker https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-pick.md
> can replace broot
* autojump
> can replace aliases

---

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

## munge

🗄 `eng.md` munge

* _cut_: rm columns https://blog.balthazar-rouberol.com/text-processing-in-the-shell#cut https://kadekillary.work/posts/cli-4-ds/ https://github.com/theryangeary/choose https://github.com/ibraheemdev/modern-unix

### awk

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

### stream edit

---

🗄 `vim.md` argdo

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

ZA
* _tail_: `tail -n +42 $FILE` view file starting from 42 line https://askubuntu.com/a/410207
* _tr_: string edit e.g. case, add newline https://github.com/Idnan/bash-guide#k-tr https://shapeshed.com/unix-tr/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#tr
```sh
cat example.txt | tr 'a-z' 'A-Z'  # uppercase
cat example.txt | tr ' ' '\n'  # replace spaces with newlines
cat example.txt | tr '\n' ','  # concat n lines into single comma-delineated line
```
* _join_: SQL join on files https://kadekillary.work/posts/cli-4-ds/
* _paste_: merge sorted files https://kadekillary.work/posts/cli-4-ds/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#paste
```sh
# 📍 todo
```
* _shuf_: https://neowaylabs.github.io/programming/unix-shell-for-data-scientists/
* _sort_: sort lines https://github.com/Idnan/bash-guide#j-sort https://kadekillary.work/posts/cli-4-ds/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#sort
* `LC_COLLATE`: determine sort order https://unix.stackexchange.com/q/75341/331460
```sh
# 📍 todo
```
* _split_: split file into chunks https://kadekillary.work/posts/cli-4-ds/ https://tech.marksblogg.com/importing-data-from-s3-into-redshift.html
* _uniq_: rm dupes https://github.com/Idnan/bash-guide#l-uniq https://kadekillary.work/posts/cli-4-ds/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#uniq
```sh
# 📍 todo
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

🗄 `vim.md` utils

ZA
* _rga_: PDFs, Microsoft Office https://github.com/phiresky/ripgrep-all https://pdfgrep.org/
* _srgn_: 🎯 alternative to LSP https://github.com/alexpovel/srgn https://www.youtube.com/watch?v=TRJo2-P9AEY
* _symbex_: Python symbols https://github.com/simonw/symbex

RG 📜 https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md
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

# 🟨️ ZA

🐍 in Python https://github.com/bugen/pypipe
🔍
* https://www.commandlinefu.com
* https://explainshell.com/ https://github.com/akavel/up
🗄
* `applications.md` utils
* `db.md` utils
* `git.md` utils
* `linux.md` denv

---

CLEAN UP
* _ffmpeg_: video encoding, file format conversion https://www.youtube.com/watch?v=MPV7JXTWPWI https://ffmpeg.guide/ https://img.ly/blog/ultimate-guide-to-ffmpeg/ https://drewdevault.com/2022/10/12/In-praise-of-ffmpeg.html
* _imgcat_: render img in terminal https://news.ycombinator.com/item?id=23319272
* _tee_: view output https://www.youtube.com/watch?v=NsAUBict1Aw
* _try_: view files that command touches https://github.com/binpash/try
* weather: https://github.com/chubin/wttr.in https://github.com/fcambus/ansiweather https://pirateweather.net/
* Wikipedia https://github.com/yashsinghcodes/wik

CLIPBOARD
* manager https://github.com/Slackadays/Clipboard
* copy output: `<cmd> | pbcopy` https://github.com/Slackadays/Clipboard
* copy file: `pbcopy < ~/.ssh/id_rsa.pub`

CORE
* versions: Linux uses GNU, macOS uses BSD (get w/ `brew install coreutils`) 📙 Evans shell [4]
* _dd_: copy/rm data https://github.com/akavel/up
* _df_: free disk space
* _file_: info on encoding, if executable
* _free_: disk space? free memory? `df` memory https://apple.stackexchange.com/q/4286/328389 or `duf` https://github.com/ibraheemdev/modern-unix `top` on macOS
* _bc_: do math on stdin https://missing.csail.mit.edu/2020/data-wrangling/
* _head_: 类似 SQL `limit` e.g. `ls <query> | head -4` or `kaiff` (`ls | sort -f | head -1 | xargs open`) https://stackoverflow.com/a/14510257/6813490
* _which_: search for executables on $PATH https://github.com/Idnan/bash-guide#d-which full path https://nil.wallyjones.com/what-shell-am-i-using/
* _tar_: https://switowski.com/blog/favorite-mac-tools/
* _w_: who is logged in and what they're doing https://rachelbythebay.com/w/2018/03/26/w/

COREUTILS
* _coreutils_: ls, rm, cat, et al. https://en.wikipedia.org/wiki/List_of_GNU_Core_Utilities_commands https://github.com/Gandalf-/coreutils
* aka userland https://bitfieldconsulting.com/golang/scripting
* aka "modern UNIX" https://www.thoughtworks.com/radar/tools/modern-unix-commands
* Rust rewrite https://news.ycombinator.com/item?id=26396798 https://jvns.ca/blog/2022/04/12/a-list-of-new-ish--command-line-tools/ https://github.com/ibraheemdev/modern-Unix

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

TRASH
* https://github.com/nivekuil/rip https://hacker-tools.github.io/command-line/ https://github.com/umlx5h/gtrash https://news.ycombinator.com/item?id=41902864
* _recoverpy_: https://github.com/PabloLec/RecoverPy
* _rm_: send to `~/.Trash`; `i` prompt before each `R` answer yes to all prompts `rf` all recursively; alternatives
* _send2trash_: https://github.com/arsenetar/send2trash/issues https://github.com/arsenetar/send2trash/issues/56 

## jobs

🗄 `infra.md` task

NOHUP
* _nohup_: separates process and terminal https://unix.stackexchange.com/a/148698
* keeps process alive after terminal that started process is killed https://hacker-tools.github.io/remote-machines/
* appends to `nohup.out`
```sh
# keep alive https://github.com/Idnan/bash-guide#d-nohup
nohup <cmd>
# keep alive + run in background
nohup <cmd> &
```

CRON https://chatgpt.com/c/6728d6eb-b654-8004-acba-f5f0d6aa8055 https://www.youtube.com/watch?v=QZJ1drMQz1A
* used for: backups, rotate log files
* semantics: cron = daemon, crontab(le) = file
* alternatives: launchd = macOS version? https://en.wikipedia.org/wiki/Launchd anachron runs even if machine powered off (unlike chron) https://ports.macports.org/port/anacron/ https://github.com/dshearer/jobber
> It’s a simple text file with an ASCII table that will execute a command on schedule. 📙 Conery [422]
* flags: `-l` list `-e` edit
* fs: system `/etc/crontab` user `/tmp/crontab.$HASH`
* macOS perms workaround https://www.bejarano.io/fixing-cron-jobs-in-mojave/
* syntax https://crontab.guru/examples.html
* env: does not load same env (.bashrc, .zshrc) so you should use absolute paths, does not log the output anywhere by default https://missing.csail.mit.edu/2019/automation/
```sh
$SCHEDULE $USER /path/to/script.sh >> /tmp/out.log 2>&1
```
```yaml
tasks:
  - name: "Backup"
    command: "python3 backup.py"
    interval: "daily"
  - name: "Data Cleanup"
    command: "python3 cleanup.py"
    interval: "hourly"
  - name: "Generate Report"
    command: "python3 generate_report.py"
    interval: "weekly"
```
```python
import schedule
import time
import subprocess
import yaml
from datetime import datetime, timedelta

def load_tasks(file_path='tasks.yaml'):
    with open(file_path, 'r') as file:
        config = yaml.safe_load(file)
    return config['tasks']

def schedule_task(task):
    command = task['command']
    def job():
        print(f"Running: {task['name']} - {datetime.now()}")
        subprocess.run(command, shell=True)
    interval = task.get('interval', 'daily')
    if interval == "hourly":
        schedule.every().hour.do(job)
    elif interval == "daily":
        schedule.every().day.at("00:00").do(job)
    elif interval == "weekly":
        schedule.every().monday.at("00:00").do(job)
    else:
        minutes = int(interval)
        schedule.every(minutes).minutes.do(job)

def main():
    tasks = load_tasks()
    for task in tasks:
        schedule_task(task)
    while True:
        schedule.run_pending()
        time.sleep(300)

if __name__ == "__main__":
    main()
```
```python
# alt impl
import schedule
import time
def job1(): print("Job 1 executed")
schedule.every().hour.do(job1)             # Every hour
schedule.every().monday.at("13:15").do(job1)   # Every Monday at 1:15 PM
while True:
    schedule.run_pending()
    time.sleep(1)
```

---

* wait https://www.youtube.com/watch?v=AHAAA7zfT7Q
* _bg_: put job in background
* _fg_: put background job into foreground https://hacker-tools.github.io/shell/
* _&_: run in background
* _nq_: queuing commands https://github.com/leahneukirchen/nq
```sh
# build targets without occupying the terminal
$ nq make clean
$ nq make depends
$ nq make all
$ fq  # look at output without stopping the build
```

## monitoring

STATS
> why is air-capp slow? Google Drive? age (2020 machine)? 🗄️ `tcp-ip.md` network monitor
* iTerm: 15%
* VS Code: 10%

SYSTEM INFO
* can do in iTerm https://wompa.land/articles/iterm-status-bar
* free (UNIX) top (macos)
* _below_: 🎯 JSON https://github.com/facebookincubator/below
* _bottom_: 🎯 GUI https://github.com/ClementTsang/bottom
* _btop_: https://github.com/aristocratos/btop
* _glances_: 🎯 JSON https://nicolargo.github.io/glances/ https://tech.marksblogg.com/top-htop-glances.html
* _gotop_: 🎯 JSON export https://github.com/xxxserxxx/gotop/issues/50 https://asciinema.org/a/spxxHKMf3MBR8OfUYwsbZurXq
* _htop_: https://tech.marksblogg.com/top-htop-glances.html
* _procs_: ✅ modes (snapshot, watch) ❓ how to sum cpu/mem across PID by app name https://github.com/dalance/procs
* _tiptop_: installed on capp machine https://github.com/nschloe/tiptop
* _vtop_: ❌ sudo https://github.com/MrRio/vtop
* _ytop_: 💀 https://github.com/cjbassi/ytop
* _zenith_: 🎯 https://github.com/bvaisvil/zenith

SYSTEM ARCHITECTURE
* `python -m platform` https://www.pythonmorsels.com/cli-tools/#platform
* _cpufetch_: https://github.com/Dr-Noob/cpufetch
* _neofetch_: https://github.com/dylanaraps/neofetch
* pfetch: https://github.com/dylanaraps/pfetch

DISK USAGE
* _df_: view of mounts https://danyspin97.org/blog/colorize-your-cli/
* _duf_: 🎯 df rewrite, JSON https://github.com/muesli/duf
* _diskonaut_: treemap https://github.com/imsnif/diskonaut
* _du_: `du -sh $DIR` https://unix.stackexchange.com/a/185777
* _dust_: du replacement https://github.com/bootandy/dust
* _ncdu_: `$HOME/.config/ncdu/config` https://dev.yorhel.nl/ncdu/man

ZA
* _progress_: 🎯 estimate remaining time on coretuil execution https://sirupsen.com/progress

---

PORT SCAN / NETWORK MONITOR https://chatgpt.com/c/67252f81-b728-8004-974b-7a9a5c4dea2c
* control internet access for apps https://tripmode.ch/ https://www.obdev.at/products/littlesnitch/index.html
* port viewer https://github.com/allyring/pvw
* LAN port scanner https://github.com/RustScan/RustScan https://github.com/aceberg/WatchYourLAN
* port scanner https://github.com/mrjackwills/havn
* monitor, Slack notification on completion (or to Twilio) https://github.com/variadico/noti
* _bandwhich_: network https://github.com/imsnif/bandwhich
* _rustscan_: https://github.com/RustScan/RustScan

MORE PROCESSES
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
