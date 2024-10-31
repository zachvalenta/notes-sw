# ⛩️

## 参考

## 进步

* _24_: shell (oh-my-posh, atuin, readline vi mode)
* _23_: terminal (research Zellij)
* _22_: terminal (Fira Mono for iTerm) shell (try starship, try/fail vi mode for readline)
* _21_: shell (exposure to readline, fzf for bash history https://hacker-tools.github.io/lectures/)

# 🐚 SHELL

SEMANTICS https://unixsheikh.com/articles/the-terminal-the-console-and-the-shell-what-are-they.html
* _shell_: cmd interpreter https://stackoverflow.com/a/44388115 📙 Conery [378]
* origins in VT-100 terminal https://josephg.com/blog/databases-have-failed-the-web/
* _command line_: IO for shell
* _line editor_: editing for command line https://en.wikipedia.org/wiki/Line_editor
* ++ autocomplete, history substitution https://danyspin97.org/blog/colorize-your-cli/
> Some versions of the Python interpreter support editing of the current input line and history substitution, similar to facilities found in the Korn shell and the GNU Bash shell. This is implemented using the GNU Readline library, which supports various styles of editing. https://docs.python.org/3/tutorial/interactive.html

ALTERNATIVES https://github.com/oilshell/oil/wiki/Alternative-Shells
* typical to write a scripting language to go along with your shell https://news.ycombinator.com/item?id=24079001
* BYO https://www.destroyallsoftware.com/screencasts/catalog https://github.com/elves/elvish
* POSIX compatability https://www.youtube.com/watch?v=Yva_nTXzTTw https://drewdevault.com/2018/02/05/Introduction-to-POSIX-shell.html https://drewdevault.com/2017/11/13/Portability-matters.html
* _elvish_: https://news.ycombinator.com/item?id=18778681 https://news.ycombinator.com/item?id=41401463
* _nushell_: structured data https://www.nushell.sh/ https://www.youtube.com/watch?v=uJsZATwQ3R8
* _oil_: https://github.com/oilshell/oil
* _Powershell_: supports some Bash commands but no arguments https://yehudakatz.com/2019/04/24/powershell-lets-get-started
* good at working with structured text like CSV https://news.ycombinator.com/item?id=28306401
* multiple versions https://www.youtube.com/watch?v=--c3yNP-hL0 7:30
* _WSL_: run Linux programs on Windows https://www.youtube.com/watch?v=idW-an99TAM https://blog.jessfraz.com/post/windows-for-linux-nerds/
* version 2 much faster, using with Neovim https://www.youtube.com/watch?v=--c3yNP-hL0
* _xonsh_: need to rewrite profile https://xon.sh/xonshrc.html https://xon.sh/bash_to_xsh.html bad w/ virtualenvs https://xon.sh/python_virtual_environments.html https://news.ycombinator.com/item?id=30302955 https://github.com/hauntsaninja/pyp https://github.com/donnemartin/gitsome

---

* zsh tutorial https://www.youtube.com/watch?v=bTLYiNvRIVI
* get current shell: `echo $SHELL` https://stackoverflow.com/a/3327022/6813490
* switch shell: `<shell>` https://fishshell.com/docs/current/tutorial.html#tut_getting_started
* return to default shell: `exit`
* https://drewdevault.com/2020/12/12/Shell-literacy.html

SEMANTICS
* https://drewdevault.com/2018/12/28/Anatomy-of-a-shell.html
* _subshell_: ? https://github.com/Canop/broot/issues/115#issuecomment-573183294
* _teletype (TTY)_: https://www.linusakesson.net/programming/tty/ https://bas.codes/posts/python-asterisks https://the.exa.website/introduction https://en.wikipedia.org/wiki/Tty_(Unix) https://en.wikipedia.org/wiki/Tty_(Unix) https://the.exa.website/introduction https://jvns.ca/blog/2022/08/30/a-way-to-categorize-debugging-skills/ https://news.ycombinator.com/item?id=34146212 https://en.wikipedia.org/wiki/Teleprinter
* https://bestasciitable.com/

## bash

📚
* Barrett https://www.amazon.com/gp/product/1098113403 https://fabiensanglard.net/bash/
* Shotts linux command line https://www.linuxcommand.org/tlcl.php
* Stutz cookbook
🔗
* https://github.com/dylanaraps/pure-bash-bible
* https://aosabook.org/en/v1/bash.html
* http://aosabook.org/en/bash.html
* https://github.com/anordal/shellharden/blob/master/how_to_do_things_safely_in_bash.md https://jvns.ca/blog/2023/08/08/what-helps-people-get-comfortable-on-the-command-line-/
* https://leanpub.com/learnbashthehardway
* https://wizardzines.com/zines/bite-size-bash/
* https://mywiki.wooledge.org/BashGuide/Practices

DESIGN
* use other languages (like Golang) https://blog.kowalczyk.info/article/4b1f9201181340099b698246857ea98d/using-go-instead-of-bash-for-scripts.html
* downsides: not great for scripting other than universality (which is great); crappy syntax, hard to test, limited data structures https://medium.com/capital-one-developers/bashing-the-bash-replacing-shell-scripts-with-python-d8d201bc0989 doesn't do autosuggestion, syntax highlighting https://danyspin97.org/blog/colorize-your-cli/
> The opposite of "it's like riding a bike" is "it's like programming in bash". A phrase which means that no matter how many times you do something, you will have to re-learn it every single time. https://twitter.com/JakeWharton/status/1334177665356587008
* mischief https://news.ycombinator.com/item?id=18902830
* `reset`: bail out when things go crazy [Linux Cookbook 2.3.5]
* template https://news.ycombinator.com/item?id=25428621
* linting: https://github.com/koalaman/shellcheck https://github.com/anordal/shellharden https://www.youtube.com/watch?v=28Ygo05cLmo
* testing https://github.com/sstephenson/bats https://github.com/amoffat/sh https://blog.esciencecenter.nl/testing-shell-commands-from-python-2a2ec87ebf71 https://github.com/bach-sh/bach 📙 Evans domain-driven [57] https://news.ycombinator.com/item?id=23268911
* Python from command line https://github.com/hauntsaninja/pyp https://github.com/python-mario/mario 
* pkg mgmt https://github.com/bpkg/bpkg 
* Bash as C# https://github.com/niieani/bash-oo-framework
* Python as declarative Bash https://github.com/tfeldmann/organize 

### args

```sh
# DEFAULT https://stackoverflow.com/a/33419280
function agg(){
# e.g. `agg` -> YEAR = 23; `agg 21` -> YEAR = 21
    YEAR=${1:-23}
    rg foo "$YEAR"/??.dat
}

# get previous arg https://www.youtube.com/watch?v=vt-IvdFP5ZA
$_

# positional
$ cmd arg1 arg2 # $0 = cmd, $1 = arg1, $2 = arg2, $@ = all args

$#  # number
$@  # all e.g. for file in "{$files[@]}"

# none
if [ $# -eq 0 ]; then

# equality
if [ "$var" = "$var" ]; then

# empty string: -z (true if empty) -n (true if not empty) https://stackoverflow.com/a/18096739
if [ -z "$var" ]; then

# integer https://stackoverflow.com/a/28898213
if [[ "$var" =~ ^-?[0-9]+[.,]?[0-9]*$ ]]
```

### control flow

📜 https://ss64.com/bash/if.html

* iteration
```sh
my_array=(item1 item2 item3)

# FOR
for FILE in *; do echo $FILE; done  # files in dir https://www.digitalocean.com/community/tutorials/workflow-loop-through-files-in-a-directory
for var in "$@"  # all args
for var in "${arr[@]}"  # all arr el
do
    git add "$var"
done

# WHILE
while [ -z "$ur_var" ]; do
    thing
done

# UNTIL
until [ -z "$ur_var" ]; do
    thing
done
```

* conditional
> ternaryhttps://run.jotaen.net/
```sh
# IF
if [ -z "$ur_var" ]; then
    echo "hey"
else
    echo "hi"
fi

# IF ELSE
if [ -z "$ur_var" ]; then
    echo "hey"
else
    echo "hi"
fi

# IF ELIF ELSE
if [ ]; then
    echo "hey"
elif [ ]
then
    echo "hi"
else
    echo "hello"
fi
```

* boolean operators
```sh
A && B # if A then B
A ; B # A then B (regardless of A exit code)
A || B # if not A then B
A & B # A and B simultaneously
```

### snippets

* modes
```sh
# DEBUG https://github.com/Idnan/bash-guide#4-debugging https://wizardzines.com/comics/bash-debugging/
#!/usr/bin/env bash - x

# STRICT http://redsymbol.net/articles/unofficial-bash-strict-mode/ https://www.youtube.com/watch?v=kEJzqMfxZVI
set -euo pipefail
IFS=$'\n\t'
```

```sh
# NEW LINE
echo -e "foo bar \n"
echo -en "\n"
```

* checks
```sh
# GET TYPE INFO https://www.youtube.com/watch?v=hrbV5WGxxdY
file $FILE

# CHECK FILE EXISTS
test -f ~/.netrc && echo "~/.netrc already exists"

# CHECK FILE DOESN'T EXIST https://stackoverflow.com/a/638980
if [ ! -f /tmp/foo.txt ]; then  # test can also be written as braces e.g. [ ! -f /tmp/foo.txt ]
    echo "File not found!"
fi

# CHECK PORT IN USE https://stackoverflow.com/a/50108745
bash -c 'while !</dev/tcp/db/5432; do sleep 1; done; npm start'

# CHECK CMD EXISTS
if ! type -f fswatch >/dev/null ; then
  echo "fswatch not installed: install with `brew install fswatch`" >&2
  exit 2
fi
```

---

* generate random string https://unix.stackexchange.com/a/230710/331460
* fallback value https://run.jotaen.net/

### variables

STRINGS
* remove char from front of string https://unix.stackexchange.com/a/194938
* remove char from end of string https://unix.stackexchange.com/a/399397
* store command in string and then run https://stackoverflow.com/a/2355242/6813490
```sh
alice="hi, alice"
echo "${alice}"  # contents
echo "${#alice}" # length

# slice https://unix.stackexchange.com/a/47372
alice="alice"
nickName="$(echo "$alice" | cut -c3-)"
echo "$nickName"
```

---

* parameters 🗄 `.bash_profile/tu` https://stackoverflow.com/questions/6212219/passing-parameters-to-a-bash-function
> this function probably removed 22.12
* `export`: propagates variable to child processes [LPI 34] https://unix.stackexchange.com/a/209581/331460
* _$PWD_: output for `pwd`
* _$EDITOR_: how os knows what to use to open text files https://github.com/dylanaraps/fff/issues/30#issuecomment-451484118 https://unix.stackexchange.com/a/251055/331460
* braces https://www.youtube.com/watch?v=FzBdcKkvUg8
* https://jvns.ca/blog/2017/03/26/bash-quirks/ https://zwischenzugs.com/2018/01/06/ten-things-i-wish-id-known-about-bash/ https://www.hackerrank.com/domains/shell/bash
* [store command in string and then run](https://stackoverflow.com/a/2355242/6813490)
* [plus command substitution](http://www.compciv.org/topics/bash/variables-and-substitution/)

```sh
# assign
# AFAIK can't have spaces between var, equal operator, and value
str="alice"
arr=("one" "two" "three")

# ref
echo "$alice"

# expand/concatenate
echo "hi, ${alice}. look at these random numbers: ${randomNum}"
```

📝 use quotes around variables (if contains spaces, is empty &c. everything will break 😑)
📝 always quote your variables

https://stackoverflow.com/a/673940/6813490

## fish

📜 https://fishshell.com/

* design: pgcli inspired by fish https://news.ycombinator.com/item?id=23957325 https://news.ycombinator.com/item?id=15912028
* install: brew; uninstall https://fishshell.com/docs/current/faq.html#faq-uninstalling
* plugins https://github.com/jorgebucaran/fisher
* prompt https://github.com/IlanCosman/tide
* aliases
> aliases (which are called abbreviations) are actually expanded after typing, so the full command appears in your history. You can also edit the full command before running it https://news.ycombinator.com/item?id=27992073
* ✅ autocomplete https://news.ycombinator.com/item?id=27992073 https://www.benkuhn.net/autocomplete/ https://ianthehenry.com/posts/sd-my-script-directory/ https://news.ycombinator.com/item?id=18777113 
* accept autosuggestion: `CTRL f` https://stackoverflow.com/a/58382167/6813490
* ❌ have to rewrite profile https://news.ycombinator.com/item?id=15913251 https://superuser.com/questions/446925/re-use-profile-for-fish
* ❌ `!!` doesn't run last cmd https://news.ycombinator.com/item?id=15943070 https://bsago.me/tech-notes https://bsago.me/tech-notes/a-replacement-for-!!-in-fish
* ❌ Vi mode but apparently doesn't work well https://stackoverflow.com/questions/28444740/how-to-use-vi-mode-in-fish-shell https://news.ycombinator.com/item?id=18778048
* ❌ scripting language not portable https://news.ycombinator.com/item?id=18778681 https://news.ycombinator.com/item?id=15911216 https://rutar.org/writing/vim-session-management-an-introduction-to-fish/
* can't run bash scripts = just switch back to bash https://news.ycombinator.com/item?id=18777141 https://jvns.ca/blog/2017/04/23/the-fish-shell-is-awesome/

## history (atuin)

ATUIN 📜 https://github.com/atuinsh/atuin https://docs.atuin.sh/
* cmd
```sh
CTRL r  # change search context (global, host, session, directory) https://www.youtube.com/watch?v=WB7qojkkVVU [7:45]
CTRL o  # inspect cmd
CTRL d  # rm cmd
```
* design: import will give everything a timestamp from moment of import https://www.youtube.com/watch?v=WB7qojkkVVU [4:40]
* creates own `.bash_profile` and `.bashrc`
```sh
. "$HOME/.atuin/bin/env"
[[ -f ~/.bash-preexec.sh ]] && source ~/.bash-preexec.sh
eval "$(atuin init bash)"
```

ALTERNATIVES
* _history-sync_: zsh plugin https://martinheinz.dev/blog/110
* _hishtory_: https://github.com/ddworken/hishtory
* _marker_: uses tldr https://github.com/pindexis/marker
* _mcfly_: cmd suggestions https://github.com/cantino/mcfly
* _tsukae_: 🎯 view most commonly used commands https://github.com/irevenko/tsukae
* _zsh-histdb_: https://github.com/larkery/zsh-histdb https://www.jefftk.com/p/logging-shell-history-in-zsh

CMD
* `history 0`: view full history https://unix.stackexchange.com/a/657934

ZA
* files: `.bash_history`, `.zsh_history` https://catonmat.net/the-definitive-guide-to-bash-command-line-history
> unsure mechanism to determine which cmd end up here, all entries from mini23 are not there
* search, rm entries https://catonmat.net/the-definitive-guide-to-bash-command-line-history
* dedupe, fmt https://martinheinz.dev/blog/110
* in bash https://www.jefftk.com/p/logging-shell-history-in-zsh
* comment for easier search https://news.ycombinator.com/item?id=41031837

---

replace atuin for scrolling commands https://www.youtube.com/watch?v=uOnL4fEnldA [10:45]

* search: `ctrl r`
* scroll all items that match query: `ctrl r` (again)
* cancel search: `ctrl c`
* scroll previous: `ctrl p`
* scroll next: `ctrl n`
> same when you're in search mode
* event designator: `history | rg cd` then go to event w/ `!<event_num>`
> it can be helpful to stick something like `#useful` or `# description` on the end of a command you expect to need again https://news.ycombinator.com/item?id=13888269

## line editor (readline)

* _readline_: line editor https://news.ycombinator.com/item?id=33785631
* impl https://github.com/chzyer/readline
* view keybindings: `bind -P` https://catonmat.net/bash-vi-editing-mode-cheat-sheet
* exec previous cmd: `!!` https://bsago.me/tech-notes/a-replacement-for-!!-in-fish

MODES
* set mode: `set -o <emacs/vi>`
* _vi_: doesn't support text obj e.g. `cw` works but `ciw` doesn't https://vi.stackexchange.com/a/9876 https://catonmat.net/bash-vi-editing-mode-cheat-sheet
* scroll history: `j/k`

---

* everything is a mess https://jvns.ca/blog/2024/07/08/readline/
> for TUI, some use Vim (Tig `CTRL d` to scroll vs. visidata)
* https://twobithistory.org/2019/08/22/readline.html
* https://thoughtbot.com/upcase/videos/readline
* config https://missing.csail.mit.edu/2020/editors/
* problem #1: would allow single motion and then go into insert mode
* problem #2: scroll history; can use emacs commands in vi mode as workaround https://stackoverflow.com/q/42951222
> both of these worked at first

bindings
* readline https://stackoverflow.com/questions/35046794/where-can-i-view-all-my-custom-keybindings-in-bash
* https://bsago.me/tech-notes/insert-text-with-fish-keybindings
* https://stackoverflow.com/questions/10870468/whats-the-usage-of-bind-in-bash
* https://www.computerhope.com/unix/bash/bind.htm

EMACS MODE https://catonmat.net/bash-emacs-editing-mode-cheat-sheet
* scroll history: `CTRL n/p`
* _repeat previous command_: `!!`
* _goto - word - forward_: alt b
* _goto - word - forward_: alt f
* _goto - line - end_: ctrl e
* _goto - line - start_: ctrl a
* _rm - word - back_: ctrl w
* _rm - word - forward_: alt d
* _rm to - line - end_: ctrl k
* _rm to - line - start_: ctrl u

completion
* _tab completion_: aka autocomplete, expansion https://python-poetry.org/docs/ https://www.freecodecamp.org/news/fzf-a-command-line-fuzzy-finder-missing-demo-a7de312403ff/
* https://iridakos.com/tutorials/2018/03/01/bash-programmable-completion-tutorial.html
* uses `complete` https://tuzz.tech/blog/how-bash-completion-works
```sh
$ complete -W "red green blue yellow purple pink orange" color
$ color <TAB><TAB>
# blue    green   orange  pink    purple  red     yellow
$ color p<TAB><TAB>
# pink    purple
```
* `ctrl e` tab complete from bash history
```sh
# tig.log
> Bash completion has been installed to: /usr/local/etc/bash_completion.d
```

## prompt (oh-my-posh)

FEATURES
* Python version
* venv https://github.com/b-ryan/powerline-shell/issues/507
* transient: only display prompt for current cmd https://www.youtube.com/watch?v=9U8LCjuQzdc [0:50]
* Git branch: can do in pure bash https://www.youtube.com/watch?v=wku-1nJR_oA https://github.com/zachvalenta/dotfiles/commit/cc4117a72c7b1d80f0ec58021530727435a2e4af https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh https://stackoverflow.com/questions/31252573/get-current-directory-without-full-path-in-fish-shell

OPTIONS
* _ohmyposh_: ✅ https://github.com/jandedobbeleer/oh-my-posh https://ohmyposh.dev/
* themes: multiverse-neon, capr4n, powerlevel10k_lean, tokyonight_storm, tonybaloney, takuya, M365Princess, catppuccin https://github.com/maxstollmayer/catppuccin.omp
> configured in `.zshenv`
* _powerlevel10k_: unsupported https://github.com/romkatv/powerlevel10k
* _powerline_: Vim and zsh https://github.com/powerline/powerline https://pypi.org/project/powerline-status/ https://github.com/wesbos/Cobalt2-iterm
* _powerline-shell_: ✅ powerline but works on bash and zsh (w/out ohmyzsh) https://github.com/b-ryan/powerline-shell
* conf: `~/.config/powerline-shell/config.json`
```json
{
    "segments": [
      "cwd",
      "git",
      "ssh",
      "virtual_env"
    ],
    "mode": "flat"
}
```
* requires powerline for fonts? https://powerline.readthedocs.io/en/latest/installation/osx.html
* no Poetry support https://github.com/b-ryan/powerline-shell/issues/507
* https://github.com/b-ryan/powerline-shell#generic-segments
* _pure_: https://github.com/sindresorhus/pure
* _starship_: https://starship.rs/
* downside: slower than powerline-shell, unattractive Git status
* upside: support for pyenv, Poetry https://starship.rs/config/#package-version
* install `brew install starship` or `sh -c "$(curl -fsSL https://starship.rs/install.sh)"`
* update `sh -c "$(curl -fsSL https://starship.rs/install.sh)"`
* uninstall `sh -c 'rm "$(command -v 'starship')"'`
* venv https://github.com/starship/starship/issues/1529
* won't get Python version if you're using an alias https://github.com/starship/starship/issues/632
## zsh

📜 https://zsh.sourceforge.io/

> ✅ autocomplete, default on macOS
* _zsh_: bash superset
* `.zprofile`: `.bash_profile` https://apple.stackexchange.com/q/388622
* `.zshrc`: put `PS1` here https://unix.stackexchange.com/q/71253
* silence warning not to use bash `export BASH_SILENCE_DEPRECATION_WARNING=1` https://elisabethirgens.github.io/notes/2020/02/bye-bash/
* comes installed on macOS https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH https://nil.wallyjones.com/what-shell-am-i-using/
* frameworks: ohmyzsh, pretzo https://hacker-tools.github.io/command-line/
* plugins https://www.zapzsh.org/
* autocomplete https://github.com/zsh-users/zsh-autosuggestions
* scripting language not portable https://news.ycombinator.com/item?id=18778681
* trailing percent sign thing https://unix.stackexchange.com/a/167600
* startup speed https://news.ycombinator.com/item?id=33580350

# 🖥️ TERMINAL

🗄️ `IT.md` window systems

SEMANTICS https://unixsheikh.com/articles/the-terminal-the-console-and-the-shell-what-are-they.html
* _terminal emulator_: shell GUI https://poor.dev/blog/terminal-anatomy/
* i.e. command line + viewport (previous cmd, output)
* get current terminal `echo $TERM_PROGRAM` https://github.com/dylanaraps/neofetch/wiki/Terminal-and-Terminal-Font-detection
* handles font, colors https://hacker-tools.github.io/command-line/ https://wizardzines.com/comics/terminals/
* color support https://github.com/apparebit/prettypretty
* "emulator" bc original terminals were hw connected to mainframe https://news.ycombinator.com/item?id=23320090
* _multiplexer_: window manager + session mgmt for terminal 📙 Hogan [x]
* multiplexers w/out sessions e.g. dvtm
* sessions w/out window mgmt e.g. abduco https://www.youtube.com/watch?v=GbZFwpmr230 0:45

## alternatives

https://chatgpt.com/c/671abdee-ccec-8004-958e-6dd5bf9f6ed9

* _Alacritty_: 🎯 YAML config, fastest, cross-platform, no global hotkey but Hammerspoon/Karabiner workaround https://github.com/alacritty/alacritty/issues/3313 https://github.com/alacritty/alacritty/issues/862 https://alacritty.org/index.html
* doesnt work on mac? https://www.youtube.com/watch?v=3wq0RFYAvNo [2:20]
* _gotty_: term as web app https://github.com/yudai/gotty
* _ghostty_: 🎯 private beta, written in Zig, coming out in 2025 https://mitchellh.com/writing/ghostty-is-coming https://mitchellh.com/ghostty https://www.youtube.com/watch?v=7Jon_cAK_to
* _Hyper_: ❌ Electron https://hyper.is/
* _kitty_: 🎯 https://sw.kovidgoyal.net/kitty/
* great integrations https://sw.kovidgoyal.net/kitty/integrations/ https://github.com/chase/awrit https://github.com/mpv-player/mpv/commit/874e28f4a41a916bb567a882063dd2589e9234e1
* opinionated maintainer https://news.ycombinator.com/item?id=41223934 https://kovidgoyal.net/ https://kovidgoyal.net/
* doesnt work on mac? https://www.youtube.com/watch?v=3wq0RFYAvNo [2:20]
* _sshx_: real-time collaboration https://github.com/ekzhang/sshx
* _Tabby_: ❌ Electron https://news.ycombinator.com/item?id=35111397 https://github.com/Eugeny/tabby?tab=readme-ov-file#what-tabby-is-and-isnt
* _Warp_: ❌ https://www.warp.dev/
* good community? https://news.ycombinator.com/item?id=30926360
* you need to login?!? https://app.warp.dev/login/
* trying to move gen AI to shell https://www.warp.dev/ai
* trying to move docs into a walled garden https://www.warp.dev/warp-drive
* autocomplete is cool, esp. Git branches https://www.warp.dev/modern-terminal
* terminal block is interesting https://www.warp.dev/modern-terminal
* launch configurations 类似 iterm profiles
* _Wezterm_: 🎯 no global hotkey, Lua config for macros https://github.com/wez/wezterm https://github.com/wez/wezterm/issues/1751 https://www.youtube.com/watch?v=TTgQV21X0SQ
* keybindings for built-in multiplex are bad https://wezfurlong.org/wezterm/features.html#available-features

---

https://www.youtube.com/watch?v=WxzYtdIcHnQ

## color

🗄 `viz.md` color

ICON/FONT/COLOR INTERPLAY
* eza/exa use different icons (setup screenshots on air22)
> can you byo your icons in eza?
* iterm version on mini22 can't display icon for music files correctly with both exa&eza but mini23 can
> I thought this was something that couldn't be patched in iTerm?

---

https://danyspin97.org/blog/colorize-your-cli/
color themes https://realpython.com/courses/custom-vs-code-color-themes/

https://news.ycombinator.com/item?id=41727971 https://jvns.ca/blog/2024/10/01/terminal-colours/

> The default terminal app is limited to 256 colors. We recommend installing a newer terminal such as iterm2, Kitty, or WezTerm. https://textual.textualize.io/getting_started/#macos

* _HSL_: https://designsystem.digital.gov/design-tokens/color/overview/
* _hex_: https://css-tricks.com/nerds-guide-color-web/
* _named_: https://css-tricks.com/nerds-guide-color-web/

* config https://github.com/guedesfelipe/pls-cli
* https://www.youtube.com/watch?v=RGlj4dcdWgM [5:30]
* colorize https://danyspin97.org/blog/colorize-your-cli/ solarized https://news.ycombinator.com/item?id=33400822
* color output: `tput` https://stackoverflow.com/a/20983251/6813490
* 256 color codes https://github.com/trapd00r/LS_COLORS https://github.com/search?q=exa_colors&type=Code https://www.howtogeek.com/307899/how-to-change-the-colors-of-directories-and-files-in-the-ls-command/
* solarized https://news.ycombinator.com/item?id=33400822
* `LS_COLORS`: var that controls output of ls, tree https://github.com/sharkdp/vivid https://github.com/chriskempson/base16-shell
> broot doesn't support LS_COLORS which isn't available on all systems and is limited to 16 system dependent colors. https://dystroy.org/broot/conf_file/
* no color https://news.ycombinator.com/item?id=30483417
* color https://news.ycombinator.com/item?id=33407620 https://fishshell.com/
* vivid https://github.com/sharkdp/vivid https://github.com/zachvalenta/dotfiles-capp/commit/fe6fe34ff3aaafcaa1e52de4257663b334622b9f
* use vivid with exa_colors https://github.com/mimame/.dotfiles/blob/b097b3dba50dc4ed7ff26886678392aa6926bed7/zsh/.zshrc#L152

## features

* compute: iTerm uses ~15% CPU on air-capp, Alacritty is supposed to be good https://chatgpt.com/c/671149f9-6ff4-8004-a834-78d1cbfdd46b

---

https://wezfurlong.org/wezterm/features.html

> UX also isn't something that can really be competed on for a terminal app as the UX is typically dictated by the shell, tool, tmux, etc. https://news.ycombinator.com/item?id=35125295

https://anarc.at/blog/2018-04-12-terminal-emulators-1/ https://news.ycombinator.com/item?id=35125442

* silence `last login` msg: add `.hushlogin` to $HOME
* Unicode support: emojis, prompts https://darrenburns.net/posts/emoji-in-the-terminal/
* tabs/profiles

VIZ
* background color/image
* transparency
* themes e.g. gruvbox https://www.youtube.com/watch?v=h509rn2xIyU
* image rendering https://github.com/lusingander/serie?tab=readme-ov-file#supported-terminals https://iterm2.com/documentation-images.html https://sw.kovidgoyal.net/kitty/graphics-protocol/

HOTKEY
* = keypress handled by listening program even if another program is active
* killer feature https://news.ycombinator.com/item?id=17924264 https://news.ycombinator.com/item?id=22853277
* used by: iTerm, Google Drive for Desktop
> would be great to remap `CMD SPACE` bc I never use Spotlight + less strain on left thumb
* _AutoHotKey_: https://www.hillelwayne.com/post/ahk/ https://www.autohotkey.com/ 
* _Alfred_ https://www.alfredapp.com/ https://wesbos.com/uses
* _BetterTouchTool_: https://switowski.com/blog/favorite-mac-tools/
* _Hammerspoon_: Keyboard Maestro https://news.ycombinator.com/item?id=34070951 install https://github.com/dandavison/wormhole
* _Karabiner_: https://missing.csail.mit.edu/2019/os-customization/ https://news.ycombinator.com/item?id=30876934
* _Raycast_: https://www.raycast.com/ https://wesbos.com/uses https://www.youtube.com/watch?v=lhJwEckGi4U https://www.youtube.com/watch?v=Bslp82vTQaM

## 🍎 iTerm

📜 https://iterm2.com/documentation.html

---

https://news.ycombinator.com/item?id=35126280
* can edit tab title
* conf: `$HOME/.config/iterm2/AppSupport -> /Users/zach/Library/Application Support/iTerm2`
* allow file access: security > full disk access
* getting help https://gitlab.com/gnachman/iterm2/-/issues/7517
* fullscreen: `CMD ENTER`
* fullscreen pane: `SHIFT CMD ENTER` https://stackoverflow.com/questions/13243933/iterm2-how-to-expand-split-pane-temporarily
* locate cursor: `CMD /`
* config status bar: profile > session > configure status bar
* hotkey: keys > hotkey > show/hide all windows (`ALT SPACE`)
* select tab by number: keys > nav > tab https://stackoverflow.com/a/59303000
* restore tabs https://superuser.com/a/755924
* handle using ALT: preferences > profiles > keys > left option as esc+ https://stackoverflow.com/a/345949
* font: load to Font Book, then update per profile
* create config file: general > preferences > load from folder https://stackoverflow.com/a/25122646 (`com.googlecode.iterm2.plist`)
* scripting https://cgamesplay.com/post/2020/11/25/iterm-plugins/ https://github.com/kamranahmedse/itomate
* can't do icons for music files https://gitlab.com/gnachman/iterm2/-/issues/7570
> workaround #1: check file extension every time you run ls e.g. `fd -d 1 -e md`
> workaround #2: every time you go to music dir, source alternate profile that will overwrite `l` with no icons
* _pane_: command line + profile
* create: keys > keybindings > split w/ default; preferences > keys > add
* nav: keys > nav > shortcut to chooose split pane > CMD number
* goto: preferences > keys > navigation shortcuts > switch to split panes
* _profile_: config for pane
* _arrangement_: group of windows
* alternative to tmux, Vim sessions https://medium.com/@jessesrsmith/five-tips-for-iterm-91db83cf4d4e
* open: window > restore window arrangement
* save default: `CMD SHIFT s`
* use default: arrangements > set default, general > startup
* open default: general > startup > default window arrangement
* startup: send text at start `imgcat /Users/zach/Desktop/zvmac/personal/photos/2020/water.png`
* how to open custom arrangement in new window w/ keyboard shortcut? https://gitlab.com/gnachman/iterm2/issues/5739 https://github.com/gnachman/iTerm2 https://stackoverflow.com/questions/tagged/iterm2 https://stackoverflow.com/a/29464585/6813490 https://apple.stackexchange.com/a/25084
> I would like to open an arrangement in a new window after starting up iTerm. I already have configured iTerm to open a specific arrangements of profiles (start `cmus`, cd into my `code` directory, etc.) on startup.

## multiplex

🗄️ `vim.md` buffers
📙 notebook [82]

WORKFLOW
* why: can name workspaces and bc screen mgmt (quick resize of panes) is what it's meant to do https://www.youtube.com/watch?v=zH3CH6zXTew
> Vim tab groups don't allow named tab groups  https://www.youtube.com/watch?v=hbs7tuwpgZA [5:00]
* why: better than iTerm for quick switch for diff workspaces https://www.youtube.com/watch?v=hbs7tuwpgZA [7:50]
* why not Vim: splits are for looking at a bunch of code at once https://www.youtube.com/watch?v=ST_DZ6yIiXY
* why not Vim: cannot name tabs
* howto: one session per project e.g. baseline (desktop/cmus/yin), data eng, algos, sk8list https://www.youtube.com/watch?v=hbs7tuwpgZA [1:45]

* _pane_: terminal window + process
* _tab_: group of panes
* _layout_: tab + start cmd
* _session_: https://www.youtube.com/watch?v=bdumjiHabhQ 5:00

ALTERNATIVES
* _cy_: https://github.com/cfoust/cy
* _screen_: https://www.gnu.org/software/screen/
* _shpool_: https://github.com/shell-pool/shpool

### 🟩 tmux

📜 https://github.com/tmux/tmux
📙 Hogan https://github.com/git-pull/tao-of-tmux https://willvaughn.org/articles/the-tmux-manual-review/

* video courses https://thoughtbot.com/upcase/tmux https://www.youtube.com/watch?v=GH3kpsbbERo
> https://www.youtube.com/watch?v=sSOfr2MtRU8 https://www.youtube.com/watch?v=DzNmUNvnB04
* https://stevedylan.dev/posts/a-terminal-based-workflow/#neovim-plugins
* install: Homebrew
* floating pane https://www.youtube.com/watch?v=JFipv1_ycqU
* stacked panes: closest option is hiding panes https://unix.stackexchange.com/questions/145857/how-do-you-hide-a-tmux-pane
* workspaces via named sessions https://www.youtube.com/watch?v=niuOc02Rvrc&t=482s
* pkg mgmt https://github.com/tmux-plugins/tpm
* status bar restore https://stackoverflow.com/questions/22407819/my-tmux-status-bar-has-disappeared
* color theme https://github.com/nordtheme/tmux
* status bar https://github.com/git-pull/tao-of-tmux/blob/master/manuscript/09-status-bar.md
* config: more ergonomic binding for prefix https://thoughtbot.com/upcase/videos/tmux-introduction https://thoughtbot.com/upcase/videos/tmux-configuration pane count https://www.youtube.com/watch?v=FTklH6z0LWA
* env var https://news.ycombinator.com/item?id=35021587
* _pane_: terminal window + split https://thoughtbot.com/upcase/videos/tmux-introduction
* 类似 Vim split (and you could also have a window be a single pane of a Vim instance within which you use Vim splits) https://www.youtube.com/watch?v=hbs7tuwpgZA 3:58 https://thoughtbot.com/upcase/videos/tmux-vim-integration
* nav btw Vim and tmux splits https://github.com/christoomey/vim-tmux-navigator
* _window_: a tab (in Zellij terms)
* _session_: window(s) + state https://www.youtube.com/watch?v=hbs7tuwpgZA 3:30
* cmd https://thoughtbot.com/upcase/videos/tmux-introduction
```sh
tmux/exit  # start/stop
CTRL b  # prefix
?  # list cmd
prefix %  # split
prefix o  # toggle split
prefix arrow  # toggle split by direction
new-session -s $NAME  # create session; tmux-resurrect https://www.youtube.com/watch?v=hbs7tuwpgZA [9:50] https://github.com/tmux-plugins/tmux-continuum
ls  # list sessions
a $NUM / attach -t $NAME  # attach to session https://thoughtbot.com/upcase/videos/tmux-navigation
```

### 🧩 Zellij

📜 https://zellij.dev/documentation/

* shell: doesn't use login, work around using `.zshenv` https://github.com/zellij-org/zellij/issues/1434#issuecomment-2185020449
* copy/paste: doesn't work with iTerm but Alacritty doesn't have native global hotkey https://zellij.dev/documentation/faq#copy--paste-isnt-working-how-can-i-fix-this

---

https://github.com/nickolaj-jepsen/fnug

@ show status bar when opening with user-defined layout

https://zellij.dev/screencasts/
https://www.youtube.com/watch?v=lmcrVRM9V4k

* plugins: https://github.com/zellij-org/awesome-zellij https://github.com/imsnif/monocle https://github.com/dj95/zjstatus/ Harpoon to nav tabs https://zellij.dev/documentation/plugin-examples Strider https://www.youtube.com/watch?v=BjfMWqy1hnw 9:45 https://www.youtube.com/watch?v=lmcrVRM9V4k 16:45 Catpppuccin https://github.com/catppuccin/zellij
* why: stacked panes, named tabs/workspaces, tmux seems like a steeper learning curve
* workaround for keybinding conflicts w/ Vim https://www.youtube.com/watch?v=Cd8P4hBC8i8 2:45
* _normal mode_: workaround for not having to constantly switch back to this https://www.youtube.com/watch?v=Cd8P4hBC8i8 2:00
* _copy mode_: get a Neovim session to munge STDOUT (e.g. tailing logs) https://www.youtube.com/watch?v=BjfMWqy1hnw 5:45
* _pane_: terminal window + process
* stacked panes looks great https://www.youtube.com/watch?v=gtjPeTCkm-8 2:15
* floating panes for ad hoc work https://www.youtube.com/watch?v=gtjPeTCkm-8 2:45 https://www.youtube.com/watch?v=BjfMWqy1hnw 7:45
* resize https://www.youtube.com/watch?v=BjfMWqy1hnw 2:15 https://www.youtube.com/watch?v=BjfMWqy1hnw 4:40
* break into separate tabs, mv btw tabs https://zellij.dev/news/session-manager-protobuffs/ https://www.youtube.com/watch?v=HaJoRgBlRc8
* full screen https://www.youtube.com/watch?v=BjfMWqy1hnw 5:40
* _tab_: group of panes
* named tabs useful for work https://www.youtube.com/watch?v=gtjPeTCkm-8 3:30
* _layout_: tab + state https://www.youtube.com/watch?v=lmcrVRM9V4k 17:15
```sh
# worked from cli
zellij --layout path/to/layout
# didn't work from conf
layout_dir "~/.config/zellij"
```
* really like version control https://www.youtube.com/watch?v=gtjPeTCkm-8 4:15
* open with cmd https://www.youtube.com/watch?v=lmcrVRM9V4k 17:15
* sync = run same cmd in all panes https://www.youtube.com/watch?v=lmcrVRM9V4k 18:00
* potential layouts: home (domains/bookcase, cmus, yin, shell) Ramalho (home w/ Python and book note opened and shell opened to REPL) personal site (repo, Neovim, file watcher) bread data (pf, vd, gobang, bread schema notes) t3 data (Mongo shell, REPL, t3 schema notes) t3 local (Neovim, broot repo)
> maybe for all these, have a floating pane for wf
* _session_: tab(s) + state https://www.youtube.com/watch?v=gtjPeTCkm-8 4:00
* 类似 tabs but for stuff you don't need going all the time https://www.youtube.com/watch?v=gtjPeTCkm-8 3:45
* mgmt https://zellij.dev/news/session-manager-protobuffs/
* resurrect https://zellij.dev/news/session-resurrection-ui-components/

# 🟨 ZA

## window systems

🗄️ `interfaces.md` terminal

WINDOW MANAGERS
* _aerospace_: 🎯 https://github.com/nikitabobko/AeroSpace https://nikitabobko.github.io/AeroSpace/guide https://www.youtube.com/watch?v=-FoWClVHG5g
* _hyprland_: https://www.youtube.com/watch?v=2CP_9-jCV6A config hell https://www.youtube.com/watch?v=T__INNgTW1M
* _yabai_: 🎯 https://github.com/koekeishiya/yabai https://daniel.lawrence.lu/blog/y2023m12d15/

SEMANTICS
* _window system_: server that displays graphics https://en.wikipedia.org/wiki/Windowing_system
* protocols: x11 https://unix.stackexchange.com/q/517 Wayland, pipewire https://www.youtube.com/watch?v=jFxwPJpUwl0 https://github.com/sharkdp/pastel#get-a-list-of-all-x11--css-color-names https://en.wikipedia.org/wiki/Wayland_(display_server_protocol) https://www.youtube.com/watch?v=lpowigSQthg https://en.wikipedia.org/wiki/X_Window_System
* _window manager_: control windows displayed by window system https://en.wikipedia.org/wiki/Window_manager https://news.ycombinator.com/item?id=34591661 https://news.ycombinator.com/item?id=36880235 https://www.youtube.com/watch?v=xWIDvnNFl5I
* _tiling window manager_: keyboard-driven arrangement of and switching btw windows
> https://www.youtube.com/watch?v=bdumjiHabhQ on i3 convinced me that this was potentially worthwhile just to not have to scroll for VS Code (and break dependency on iTerm auto hotkey)
* _desktop environment_: mouse-driven GUI riding on top of window system https://askubuntu.com/a/20435
* _display server_: ❓ e.g. Quartz Compositor (aka WindowServer) https://en.wikipedia.org/wiki/Quartz_Compositor https://unix.stackexchange.com/a/1016

DESKTOP ENV
* rainmeter https://modkavartini.github.io/catppuccin/ https://www.rainmeter.net/
* _GNOME_: https://blog.edfloreshz.dev/articles/linux/system76/rust-based-desktop-environment/
* _Material Shell_: https://news.ycombinator.com/item?id=24491091
* _Cinnamon_: https://news.ycombinator.com/item?id=24491091

---

WINDOW MANAGERS
* window manager https://news.ycombinator.com/item?id=34591661
* for Windows https://news.ycombinator.com/item?id=33168263
* for macOS https://magnet.crowdcafe.com/ https://news.ycombinator.com/item?id=22852157 https://faun.pub/yabai-macos-tile-window-manager-833ce1be396a?gi=132df1bca0e1 https://github.com/koekeishiya/yabai https://news.ycombinator.com/item?id=36368990
* AlwaysOnTop https://www.youtube.com/watch?v=6IxRlaTWsoQ
* _alt-tab_: https://alt-tab-macos.netlify.app/
* _Amethyst_: macOS https://github.com/ianyh/Amethyst https://www.reddit.com/r/xmonad/comments/3j4tnt/is_it_possible_to_use_xmonad_on_os_x/ https://switowski.com/blog/favorite-mac-tools/
* _dwm_: https://dwm.suckless.org/
* _i3_: tiling + hotkeys https://www.youtube.com/watch?v=bdumjiHabhQ 3:30 https://www.youtube.com/watch?v=bdumjiHabhQ 1:30
* _Magnet_: https://switowski.com/blog/favorite-mac-tools/
* _PaperWM_: https://jvns.ca/blog/2020/01/05/paperwm/
* _Slate_: unmaintained https://github.com/jigish/slate
* _Sway_: https://swaywm.org/
* _Rectangle_: macOS https://rectangleapp.com/ https://switowski.com/blog/favorite-mac-tools/ https://github.com/rxhanson/Rectangle
* _X.org_: https://www.x.org/wiki/
* _XQuartz_: port of X.org for macOS https://www.xquartz.org/
* _xmonad_: x11, no macOS https://news.ycombinator.com/item?id=30402358 https://xmonad.org/
> I've mellowed as I've aged, but still fondly remember the thrill of the XMonad tiling window manager on multiple monitors — in particular, its responsiveness. With a few fast keyboard shortcuts, I could throw windows between monitors, arrange windows side-by-side, and immediately move focus to exactly the window I had in mind. XMonad also supports "virtual desktops", which I used to organize windows by task. For example, when working on a web app I'd put a terminal window, Emacs window, two web browsers (one for my app, the other for looking up documentation) all on the same virtual desktop. Then, when I wanted to do something else, I could switch to an empty virtual desktop, effectively saving my previous one "away for later". https://kevinlynagh.com/newsletter/2020_04_keyboards_rethinking_desktops/
