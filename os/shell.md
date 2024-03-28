# 开

## 参考

📚
* Barrett https://www.amazon.com/gp/product/1098113403
* Evans shell
* Shotts linux command line https://www.linuxcommand.org/tlcl.php
* Stutz cookbook

## now

## next

---

* https://github.com/denisidoro/navi
* https://fabiensanglard.net/bash/
* readline history https://github.com/atuinsh/atuin https://www.youtube.com/watch?v=WB7qojkkVVU
> key features: UI, queries

# done

* _23_: big rf, Conery unix chapter, research Zellij
* _22_: Fira Mono for iTerm font/icons, try starship, try/fail vi mode for readline, organize utils
* _21_: line editor, fzf for bash history https://hacker-tools.github.io/lectures/
* _20_: broot
* _19_: exa, symlink dotfiles, try out utils (z, fish, tig, fzf, ranger, ripgrep)
* _18_: scripts (`fne`, `qing`, `ding`, `qiu`, `jb`)

# 🔨 BASH

🔗
* https://github.com/dylanaraps/pure-bash-bible
* http://aosabook.org/en/bash.html
* https://github.com/anordal/shellharden/blob/master/how_to_do_things_safely_in_bash.md https://jvns.ca/blog/2023/08/08/what-helps-people-get-comfortable-on-the-command-line-/
* https://leanpub.com/learnbashthehardway
* https://wizardzines.com/zines/bite-size-bash/
* https://mywiki.wooledge.org/BashGuide/Practices

GLOBBING
* _glob_: pattern for matching groups of files 📙 Neil practical [6.88]
* filename completion (vs. regex i.e. search text https://www.linuxjournal.com/content/globbing-and-regex-so-similar-so-different) [LPI 25] 
* aka wildcards
* `*`: anything 
* `?`: single char 
* `[]`: range; case-sensitive `cp [a-f]*.png` `rm 02[3-7].mp3`

DESIGN
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

DATES
* https://github.com/jarun/pdd
* backup w/ timestamp: `touch "$(date +%Y%m%d_%H%M%S).bak"` https://unix.stackexchange.com/a/96383/331460
* _touch_: make new file or update timestamp
* create dir with current date
```sh
today="$(date +'%Y-%m')"
hour_min="$(date +'%H-%M-%S')"
\cd $HOME/Documents
dir="my-dir-$today-$hour_min"
mkdir "$dir"
```
```sh
# https://news.ycombinator.com/item?id=31575076
function tz(){
    cal -3
    echo
    echo -n "Local:       "
    date --rfc-3339=s
    echo -n "UTC:         "
    date -u --rfc-3339=s
    echo -n "New York     "
    TZ='America/New_York' date --rfc-3339=s
    echo -n "London:      "
    TZ='Europe/London' date --rfc-3339=s
    echo -n "New Zealand: "
    TZ='Pacific/Auckland' date --rfc-3339=s
}
```

SNIPPETS
```sh
# new line
echo -e "foo bar \n"
echo -en "\n"

# get file type info https://www.youtube.com/watch?v=hrbV5WGxxdY
file $FILE

# debug mode https://github.com/Idnan/bash-guide#4-debugging https://wizardzines.com/comics/bash-debugging/
#!/usr/bin/env bash - x

# strict mode http://redsymbol.net/articles/unofficial-bash-strict-mode/ https://www.youtube.com/watch?v=kEJzqMfxZVI
set -euo pipefail
IFS=$'\n\t'

# generate random string https://unix.stackexchange.com/a/230710/331460
```

## args

```sh
# DEFAULT https://stackoverflow.com/a/33419280
# e.g. `agg` -> YEAR = 23; `agg 21` -> YEAR = 21
function agg(){
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

## control flow

📜 https://ss64.com/bash/if.html

```sh
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

```sh
###
# ITERATION
###

my_array=(item1 item2 item3)

# for
for FILE in *; do echo $FILE; done  # files in dir https://www.digitalocean.com/community/tutorials/workflow-loop-through-files-in-a-directory
for var in "$@"  # all args
for var in "${arr[@]}"  # all arr el
do
    git add "$var"
done

# while
while [ -z "$ur_var" ]; do
    thing
done

# until
until [ -z "$ur_var" ]; do
    thing
done

###
# CONDITIONALS
###

# if
if [ -z "$ur_var" ]; then
    echo "hey"
else
    echo "hi"
fi

# if else
if [ -z "$ur_var" ]; then
    echo "hey"
else
    echo "hi"
fi

# if elif else
if [ ]; then
    echo "hey"
elif [ ]
then
    echo "hi"
else
    echo "hello"
fi

###
# BOOLEAN OPERATORS
###

A && B # if A then B
A ; B # A then B (regardless of A exit code)
A || B # if not A then B
A & B # A and B simultaneously
```

## dotfiles

🗄 `linux.md` denv

* write script to do symlinks https://news.ycombinator.com/item?id=34304694
* prefer programs that store config as text
* keep under version control and symlink into place with script https://hacker-tools.github.io/dotfiles/ advanced mgmt https://github.com/twpayne/chezmoi https://news.ycombinator.com/item?id=32632533
> There are two basic approaches: version your entire home directory or symbolically link your dotfiles into place from a stand-alone repository. The first approach is straightforward but has a number of issues that make it a poor choice. https://nullprogram.com/blog/2012/06/23/
* install script https://www.youtube.com/watch?v=hXU54axdjJc https://alexpearce.me/2016/02/managing-dotfiles-with-stow/
* mgmt: GNU Stow https://www.youtube.com/watch?v=90xMTKml9O0 https://github.com/bbkane/fling
* mbp14
```sh
# /Users/zach
.bash_profile -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.bash_profile
.bashrc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.bashrc
.gitconfig -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.gitconfig
.mlrrc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.mlrrc
.pdbrc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/python/.pdbrc
.pdbrc.py -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/python/.pdbrc.py
.psqlrc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/db/.psqlrc
.sqliterc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/db/.sqliterc
.tmux.conf -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/tmux.conf
.vimrc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.vimrc
.visidatarc -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/db/.visidatarc
.zprofile -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/.zprofile
.sh -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/git-prompt.sh

# /Users/zach/.config
http-prompt/config.py -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/http-prompt-config.py
iterm2/AppSupport -> /Users/zach/Library/Application Support/iTerm2
litecli/config -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/db/litecli.conf
neofetch/config.conf -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/neofetch.conf
pgcli/config -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/db/pgcli.conf
powerline-shell/config.json -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/powerline-shell.json
starship.toml -> /Users/zach/Desktop/zvmac/materials/sw/os/za/dotfiles/starship.toml
```
* air22
```sh
# /Users/zach
.gitconfig -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/.gitconfig
.vimrc -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/.vimrc
.zprofile -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/.zprofile
.zshrc -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/.zshrc

# /Users/zach/.config
broot/conf.toml -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/broot-conf.toml
nvim/init.vim -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/init.vim
nvim/lua/zv  # Neovim conf: user, plugins
powerline-shell/config.json -> /Users/zach/Documents/zvroot/materials/stem/dev/os/denv/dotfiles/powerline-shell.json
```

## execution

EXEC
* specify interpreter from shell e.g. `python $SCRIPT` 📙 Conery [390]
* file extensions don't matter to program execution https://askubuntu.com/a/764126
* _shebang line_: specific interpreter from script `./ $SCRIPT` 📙 Conery [391]
```sh
# BASH
#!/usr/bin/env bash

# Python https://realpython.com/python-shebang/
#!/usr/bin/env python3  # $PATH
#!/usr/bin/python3.6    # absolute path
```
* _source_: load/export variable/script to current shell's env 📙 Conery [401]
* `source` = `.` https://stackoverflow.com/a/16619261

WHERE TO PUT SHELL SCRIPTS
* `/usr/local/bin` [Linux Cookbook A.3.4]
* `~/bin`
* `fooDir` --> `~/bin`

EXIT CODES
* _0_: success 
* _1_: err 
* _2_: "misuse of shell built-ins" (e.g. "no such file" err) https://askubuntu.com/a/892605 
* _?_: var for last cmd's exit code e.g. `echo "hi"; echo $?  #0` https://askubuntu.com/a/892607
* _127_: you use a command in your script that the shell doesn't know about
* _130_: termination via CTRL c
* _137_: script faile (128) and then received sig kill (9) from OOM killer https://stackoverflow.com/a/1041309
* cleanup on exit https://github.com/Idnan/bash-guide#exit-traps
* are less clear than you think https://news.ycombinator.com/item?id=24267155
* get exit code of last command: `$?` https://www.freecodecamp.org/news/docker-exec-how-to-run-a-command-inside-a-docker-image-or-container/
* `exit`: close shell
* `return`: exit script
* _sink_: http://www.tldp.org/LDP/abs/html/exitcodes.html https://en.wikipedia.org/wiki/Exit_status#Shell_and_scripts https://bencane.com/2014/09/02/understanding-exit-codes-and-how-to-use-them-in-bash-scripts/
```sh
~/Desktop/zvmac/materials/sw/algos/algos (master *)$ rg austen  # no results
~/Desktop/zvmac/materials/sw/algos/algos (master *)$ echo "$?"  # 1
```

---

https://github.com/sachaos/viddy
* file operators: exists `-e` is a regular file not dir `-f` https://ss64.com/bash/syntax-file-operators.html

* _eval_: use str as cmd https://www.youtube.com/watch?v=0A4Kjr8ThJA 1:45
```sh
x="date"
echo $x  # date
eval $x  # Tue Feb 22 18:33:49 EST 2022

# use to set multiple exports at once
eval "$(brew shellenv)"
```

* sudo https://bsago.me/tech-notes/sudo-with-aliases-in-fish
* keep script from consuming too many resources: `nice myscript`
* add location: `./myscript` doesn't need to be on $PATH
* as a cmd: `myscript` (script need shebang and perm to exec)
* using bash: `bash myscript` (doesn't need shebang or perm to exec, can debug this way using `bash -x myscript`)
```sh
$ foo
-bash: zv/bin/foo: Permission denied
$ l
-rw-r--r-- foo # no perm

$ bash foo
hi zjv # can still exec w/ `bash`
```

```sh
# 📍 'Automate' appendix B

# as .py
`python script.py`
# with shebang
`./script.py`  # apparently this only works if file is executable, where `bash script.sh` always works
```

📍 re: `suan` https://stackoverflow.com/questions/874452/change-the-current-directory-from-a-bash-script

* __call script directly__: `<script>`
* __dot command__: . `<script>`
* __dot + forward slash__: . `<script>`
* __sh command__: sh `<script>` 
* __bash command__: bash `<script>`

[source vs. execute](https://superuser.com/a/795838)

* put on $PATH
* make executable `chmod u+x script.sh`
* if bash, remove `.sh` (`script.sh` ➡️ `script`) and call (`script`)
* if python, keep `.py` and call (`script.py`)

📝 get tab completion from terminal if put on $PATH

__dot command__: `. fooScript.sh`

```sh
# diff btw `source` and `./` 
# ➡️ https://stackoverflow.com/a/9640736/6813490

# use `exit`
🈚️ ☞☞☞ ./git-hooks/test_zv.sh

# use `return`
🈚️ ☞☞☞ source git-hooks/test_zv.sh
```

❓ diff btw this and all the other ways 😄
❓ why does Python script require `./script.py`

```sh
code
<script>
. <script>
./ <script>
sh <script> 
bash <script>
```

## IO

OPERATORS
> https://unix.stackexchange.com/a/170573
* `1`: stdout
* `2`: stderr
* `&`: stdout + stderr
* `>`: overwrite
* `>>`: append
* `<`: use file as input
* e.g. `sqlite3 local.db < schema.sql`
* _pipe (|)_: directs stdout to stdin
```sh
# stdout           | takes stdin
echo "training 20" | termgraph
```

---

redirects

* _xargs_: construct list of args for cmd (bc some cmds only take args, not stdin) https://thorstenball.com/blog/2012/10/24/command-line-ride/ https://www.oilshell.org/blog/2021/08/xargs.html
> can also just input `./myscript.py < somefile.txt` (semantics for operator names) https://stackoverflow.com/a/11853307
```sh
LOGS_DIR/20 $ fd tracking | tail -n 3 | xargs bat  # open 3 most recent tracking files
ls | sort -f | head -1 | xargs open  # kaiff - open first file in directory; used to open Youtube talks downloaded as pods
fd tracking | xargs rg music  # from logs/20 -> get tracking info for music
```

* _fold_: https://blog.balthazar-rouberol.com/text-processing-in-the-shell#fold
* _fmt_: fmt stdout https://github.com/Idnan/bash-guide#f-fmt

* stdout, stderr
```sh
# stderr to file
cmd &> file.log

# capture cmd output
OUTPUT="$(ls -1)"
echo "${OUTPUT}"

# redirect stderr to stdout
2>&1  # `&` marks `1` as a file descriptor vs. a file name https://stackoverflow.com/a/818284

# redirect stderr to null
cat weight.dat | asciigraph -h 10 -c "weight" -cc red 2>/dev/null
```

## profiles

ALIASES
* _alias_: evaluated when shell loads profile
* view: `type <alias>` https://www.youtube.com/watch?v=aLMepxvUj4s 4:15
* use unaliased: `\cd` https://stackoverflow.com/a/11056541

ENV VAR 🗄 `infra.md` config mgmt `security.md` secrets mgmt
```sh
export FOO="val"      # set
DEBUG=true npm start  # set tmp to run cmd
echo $FOO             # read
env                   # list all
unset $FOO            # unset
```
* _envsubst_: sub env var into fmt strings https://nickjanetakis.com/blog/using-envsubst-to-merge-environment-variables-into-config-files
```sh
foo.sh  # echo $LOGNAME 
./foo.sh           # stdout: $LOGNAME
envsubst < foo.sh  # stdout: zach
```
* clean up: 🗄 `broot.log` https://unix.stackexchange.com/a/106606/331460 https://github.com/thoughtbot/til/blob/master/bash/bash_profile_vs_bashrc.md
* _direnv_: load env var based on dir https://jamey.thesharps.us/2019/05/29/per-project-postgres/ https://github.com/direnv/direnv

PATH
* https://terminaltrove.com/pathos/
* `$PATH`: list of directories that the shell should search when looking for programs corresponding to commands entered by the user [LPI 2.7]
* change precedence: https://apple.stackexchange.com/a/49961
* _default_: `/bin`, `usr/bin`
* _global_: `/etc/paths`
* _user_: `.bash_profile`

---

* https://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/
* macOS execution order: `.bash_profile`, `.bash_login`, `.profile`

SOURCING
* zsh automatically sources `.zprofile` and `.zshrc`
* bash automatically sources `.bash_profile`
* silence warning not to use bash `export BASH_SILENCE_DEPRECATION_WARNING=1` https://elisabethirgens.github.io/notes/2020/02/bye-bash/
* bash on zsh MacOS iTerm: profiles > command: (`bash`, `source ~/.bash_profile`)

SHELL TYPES
* _interactive_: normal
* _non-interactive_: process spawned when script run 📙 LPI 2.2 https://unix.stackexchange.com/questions/43385/what-do-you-mean-by-interactive-shell/43389#43389 
* _login_: reads profiles and env var 
* _non-login_: cron jobs https://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell/46856#46856 https://www.quora.com/What-are-the-differences-between-a-login-shell-and-a-non-login-shell/answer/Rod-Nussbaumer-1?srid=ebCJ

---

* _system_: `/etc/profile` `/etc/bashrc` https://bencane.com/2013/09/16/understanding-a-little-more-about-etcprofile-and-etcbashrc/
* _login_: `~/.bash_profile` 
* _non-login_: `~/.bashrc` https://unix.stackexchange.com/a/3469/331460 https://en.wikipedia.org/wiki/Run_commands
* _rc file_: startup script 📙 Conery [382]

```sh
# view single function def from `.bash_profile`
declare -f <name>

# view all function def
declare -f

# view all function names (regex = line starts with lower case characters)
declare -f | grep '^[a-z]'
```

## standards

🔗 http://gnu.ist.utl.pt/prep/standards/html_node/Command_002dLine-Interfaces.html

INPUT https://news.ycombinator.com/item?id=31293032
* https://nullprogram.com/blog/2020/08/01/
* _flag_: hyphen e.g. `cmd --from here --to there`
* letter (`-h`) word (`--help`) https://www.youtube.com/watch?v=FOQHGz__OLs
* _arg_: no hypen `cmd here there`; less clear than flags bc have to remember which is src and which is target https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46

ZA
> all executables should have the `execute` bits set i.e. `chmod a+x foo-bar`; git tracks the executable bit, and sets it during checkout
* _shebang line_: how os knows how to run your program
* fmt: `#!/usr/bin/env INTERPRETER` e.g. `#!/usr/bin/env python`
> The program `/usr/bin/env` locates the environment using the `PATH` variable like any other command. This lets us control which interpreter gets chosen in a given environment by manipulating `PATH` e.g. using a python virtualenv instead of the system python.

NAMING
* scripts: lowercase + snakecase e.g. `foo`, `foo-bar`, `foo-bar-baz`
* no file extension bc reimpl = rename in every place of usage, update doc links
* everything but env var is lowercase https://stackoverflow.com/a/673940

OPTIONS 🔗 http://www.catb.org/~esr/writings/taoup/html/ch10s05.html
* _short option_: single dash prefix + single letter e.g. `-y`
* _option set_: n short options e.g. `-baz` = `-b`, `a`, `z`
* _long option_: double dash prefix + word e.g. `--foo-bar`
* options with a value are separated by their option by a space or an `=`
* `--`: ends option processing.

LOCATION
* `tools/PROJECT/YOUR-TOOL` for project related tools
* `bin/YOUR-TOOL` for things that are useful to have accessible at all times

## variables

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

# 📺 INTERFACES

🔗 https://unixsheikh.com/articles/the-terminal-the-console-and-the-shell-what-are-they.html

EXEC
* _shell_: cmd interpreter https://stackoverflow.com/a/44388115 📙 Conery [378]
* origins in VT-100 terminal https://josephg.com/blog/databases-have-failed-the-web/

IO
* _command line_: IO for shell
* _line editor_: editing for command line https://en.wikipedia.org/wiki/Line_editor
* ++ autocomplete, history substitution https://danyspin97.org/blog/colorize-your-cli/
> Some versions of the Python interpreter support editing of the current input line and history substitution, similar to facilities found in the Korn shell and the GNU Bash shell. This is implemented using the GNU Readline library, which supports various styles of editing. https://docs.python.org/3/tutorial/interactive.html

UI
* _terminal emulator_: shell GUI https://poor.dev/blog/terminal-anatomy/
* i.e. command line + viewport (previous cmd, output)
* get current terminal `echo $TERM_PROGRAM` https://github.com/dylanaraps/neofetch/wiki/Terminal-and-Terminal-Font-detection
* handles font, colors https://hacker-tools.github.io/command-line/ https://wizardzines.com/comics/terminals/
* "emulator" bc original terminals were hw connected to mainframe https://news.ycombinator.com/item?id=23320090
* _multiplexer_: window manager + session mgmt for terminal 📙 Hogan [x]
* multiplexers w/out sessions e.g. dvtm
* sessions w/out window mgmt e.g. abduco https://www.youtube.com/watch?v=GbZFwpmr230 0:45

---

* _session_: https://www.youtube.com/watch?v=bdumjiHabhQ 5:00
* _subshell_: ? https://github.com/Canop/broot/issues/115#issuecomment-573183294
* _teletype (TTY)_: https://bas.codes/posts/python-asterisks https://the.exa.website/introduction https://en.wikipedia.org/wiki/Tty_(Unix) https://en.wikipedia.org/wiki/Tty_(Unix) https://the.exa.website/introduction https://jvns.ca/blog/2022/08/30/a-way-to-categorize-debugging-skills/ https://news.ycombinator.com/item?id=34146212 https://en.wikipedia.org/wiki/Teleprinter
* https://bestasciitable.com/

## line editor (readline)

* _readline_: line editor https://news.ycombinator.com/item?id=33785631
* impl https://github.com/chzyer/readline
* view keybindings: `bind -P` https://catonmat.net/bash-vi-editing-mode-cheat-sheet
* set mode: `set -o <emacs/vi>`
* exec previous cmd: `!!` https://bsago.me/tech-notes/a-replacement-for-!!-in-fish

* _vi_: doesn't support text obj e.g. `cw` works but `ciw` doesn't https://vi.stackexchange.com/a/9876 https://catonmat.net/bash-vi-editing-mode-cheat-sheet
* scroll history: `j/k`

---

* history https://github.com/ddworken/hishtory https://github.com/pindexis/marker https://www.jefftk.com/p/logging-shell-history-in-zsh https://jvns.ca/blog/2023/08/08/what-helps-people-get-comfortable-on-the-command-line-/
* autocomplete https://fig.io/

to read before you take another swing at using vi mode
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

## multiplex (Zellij)

📙 notebook [82,84]

ZELLIJ 📜 https://zellij.dev/documentation/
> quick resize of panes = Zellij might be better than using Vim splits
* plugins: Harpoon to nav tabs https://zellij.dev/documentation/plugin-examples Strider https://www.youtube.com/watch?v=BjfMWqy1hnw 9:45 https://www.youtube.com/watch?v=lmcrVRM9V4k 16:45 Catpppuccin https://github.com/catppuccin/zellij
* workaround for keybinding conflicts w/ Vim https://www.youtube.com/watch?v=Cd8P4hBC8i8 2:45
* scrollback https://zellij.dev/screencasts/
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
* really like version control https://www.youtube.com/watch?v=gtjPeTCkm-8 4:15
* open with cmd https://www.youtube.com/watch?v=lmcrVRM9V4k 17:15
* sync = run same cmd in all panes https://www.youtube.com/watch?v=lmcrVRM9V4k 18:00
* potential layouts: home (domains/bookcase, cmus, yin, shell) Ramalho (home w/ Python and book note opened and shell opened to REPL) personal site (repo, Neovim, file watcher) bread data (pf, vd, gobang, bread schema notes) t3 data (Mongo shell, REPL, t3 schema notes) t3 local (Neovim, broot repo)
> maybe for all these, have a floating pane for wf
* _session_: tab(s) + state https://www.youtube.com/watch?v=gtjPeTCkm-8 4:00
* 类似 tabs but for stuff you don't need going all the time https://www.youtube.com/watch?v=gtjPeTCkm-8 3:45
* mgmt https://zellij.dev/news/session-manager-protobuffs/
* resurrect https://zellij.dev/news/session-resurrection-ui-components/

TMUX 📜 https://github.com/tmux/tmux 📙 Hogan https://thoughtbot.com/upcase/tmux https://github.com/git-pull/tao-of-tmux
* install: Homebrew
* _pane_: terminal window + split https://thoughtbot.com/upcase/videos/tmux-introduction
* 类似 Vim split (and you could also have a window be a single pane of a Vim instance within which you use Vim splits) https://www.youtube.com/watch?v=hbs7tuwpgZA 3:58 https://thoughtbot.com/upcase/videos/tmux-vim-integration
* _window_: a tab (in Zellij terms)
* _session_: window(s) + state https://www.youtube.com/watch?v=hbs7tuwpgZA 3:30

ZA
* feature overlap re: editors/terminals: tabs (Vim, iTerm), sessions (Vim), replicated plugins (Harpoon, fuzzy find)
* history: screen https://www.gnu.org/software/screen/ -> tmux -> zellij

---

VIM
> pro of using zellij to control Vim via panes is you have access to zellij panes resizing but don't think zellij can handle having the Vim workspace in context for Harpoon e.g. I don't want to open a new pane and try fuzzy finding and only having the files in context that Strider knows about https://www.youtube.com/watch?v=lmcrVRM9V4k 16:30
* https://rutar.org/writing/from-vim-and-tmux-to-neovim/
* https://github.com/christoomey/vim-tmux-navigator
* https://www.youtube.com/watch?v=gnupOrSEikQ
* https://vimtricks.com/p/quickly-access-project-notes/
* https://www.youtube.com/results?search_query=vim+sessions+vs.+tmux https://www.youtube.com/watch?v=ST_DZ6yIiXY

WHY
* _why switch from iTerm?_ named sessions https://www.youtube.com/watch?v=hbs7tuwpgZA 7:50 temp full screen of panes [ibid 6:35]
* _workflow_: session per Git project https://www.youtube.com/watch?v=hbs7tuwpgZA https://thoughtbot.com/upcase/videos/tmux-introduction one pane for Vim and another for running tests
* copy, paste https://thoughtbot.com/upcase/videos/tmux-navigation

PLUGINS
* _tpm_: pkg mgmt https://github.com/tmux-plugins/tpm
* color theme https://github.com/nordtheme/tmux
* status bar https://github.com/git-pull/tao-of-tmux/blob/master/manuscript/09-status-bar.md
* https://github.com/tmux-plugins/tmux-resurrect
* https://github.com/tmux-plugins/tmux-continuum
* https://www.youtube.com/watch?v=DzNmUNvnB04
* https://www.youtube.com/shorts/PL1EoKjy4iM

* send keys https://news.ycombinator.com/item?id=37172711
* Zellij https://news.ycombinator.com/item?id=26902430 https://news.ycombinator.com/item?id=32444564 https://www.youtube.com/watch?v=mnp9LCUdtJw
* one session per project e.g. t3, data eng, baseline (desktop/cmus/yin) https://www.youtube.com/watch?v=hbs7tuwpgZA 1:45
* guided tour https://www.youtube.com/watch?v=sSOfr2MtRU8 @ 5:00
* persist sessions through restart https://github.com/tmux-plugins/tmux-resurrect https://www.youtube.com/watch?v=sMbuGf2g7gc
* n windows w/in single session of terminal emulator https://linuxize.com/post/getting-started-with-tmux/
* switch btw sessions w/ fzf https://news.ycombinator.com/item?id=22857615
* config, pane count https://www.youtube.com/watch?v=FTklH6z0LWA
* https://willvaughn.org/articles/the-tmux-manual-review/
* https://news.ycombinator.com/item?id=35021587
* _config_: more ergonomic binding for prefix https://thoughtbot.com/upcase/videos/tmux-introduction https://thoughtbot.com/upcase/videos/tmux-configuration
* _normal navigation cmds (page up, et al.)_: prefix [ then q to exit
* _leader_: synonym for hotkey?

cmd
* _start_: `tmux`
* _stop_: `exit`
* _prefix to all cmd_: `ctrl b`
* _list all cmd_: `?`

pane https://thoughtbot.com/upcase/videos/tmux-introduction
* _horizontal split_: prefix %
* _vertical split_: prefix "
* _toggle splits_: prefix o
* _switch splits by direction_: prefix arrow

session
* _create named_: `tmux new-session -s <name>`
* _save_: tmux-resurrect (apparently you'd otherwise lose on shutdown) https://www.youtube.com/watch?v=hbs7tuwpgZA 9:50
* _detach_: run in background; `prefix d` or `tmux detach-session` https://thoughtbot.com/upcase/videos/tmux-introduction
* _list_: `tmux ls`
* _attach_: bring to foreground; `tmux a <num>` or `tmux attach -t <name>`; can use `choose-tree` as well https://thoughtbot.com/upcase/videos/tmux-navigation

## shell (zsh)

ZSH 📜 https://zsh.sourceforge.io/
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

FISH 📜 https://fishshell.com/
* design: pgcli inspired by fish https://news.ycombinator.com/item?id=23957325 https://news.ycombinator.com/item?id=15912028
* install: brew; uninstall https://fishshell.com/docs/current/faq.html#faq-uninstalling
* plugins https://github.com/jorgebucaran/fisher
* prompt https://github.com/IlanCosman/tide
* aliases
> aliases (which are called abbreviations) are actually expanded after typing, so the full command appears in your history. You can also edit the full command before running it https://news.ycombinator.com/item?id=27992073
* ✅ autocomplete https://news.ycombinator.com/item?id=27992073 https://www.benkuhn.net/autocomplete/ https://ianthehenry.com/posts/sd-my-script-directory/ https://news.ycombinator.com/item?id=18777113 
* accept autosuggestion: `CTRL f` https://stackoverflow.com/a/58382167/6813490
* ❌ have to rewrite profile https://news.ycombinator.com/item?id=15913251 https://superuser.com/questions/446925/re-use-profile-for-fish
* ❌ `!!` doesn't run last cmd https://news.ycombinator.com/item?id=15943070 https://bsago.me/tech-notes
* ❌ Vi mode but apparently doesn't work well https://stackoverflow.com/questions/28444740/how-to-use-vi-mode-in-fish-shell https://news.ycombinator.com/item?id=18778048
* ❌ scripting language not portable https://news.ycombinator.com/item?id=18778681 https://news.ycombinator.com/item?id=15911216 https://rutar.org/writing/vim-session-management-an-introduction-to-fish/
* can't run bash scripts = just switch back to bash https://news.ycombinator.com/item?id=18777141 https://jvns.ca/blog/2017/04/23/the-fish-shell-is-awesome/

ALTERNATIVES https://github.com/oilshell/oil/wiki/Alternative-Shells
* BYO https://www.destroyallsoftware.com/screencasts/catalog
* _crush_ https://news.ycombinator.com/item?id=24079001
* _elvish_ https://news.ycombinator.com/item?id=18778681
* _nushell_: https://www.nushell.sh/
* _oil_: https://news.ycombinator.com/item?id=24079001
* _Powershell_: supports some Bash commands but no arguments https://yehudakatz.com/2019/04/24/powershell-lets-get-started
* good at working with structured text like CSV https://news.ycombinator.com/item?id=28306401
* multiple versions https://www.youtube.com/watch?v=--c3yNP-hL0 7:30
* _WSL_: run Linux programs on Windows https://www.youtube.com/watch?v=idW-an99TAM https://blog.jessfraz.com/post/windows-for-linux-nerds/
* version 2 much faster, using with Neovim https://www.youtube.com/watch?v=--c3yNP-hL0
* _xonsh_: need to rewrite profile https://xon.sh/xonshrc.html https://xon.sh/bash_to_xsh.html bad w/ virtualenvs https://xon.sh/python_virtual_environments.html https://news.ycombinator.com/item?id=30302955 https://github.com/hauntsaninja/pyp

---

* zsh tutorial https://www.youtube.com/watch?v=bTLYiNvRIVI
* what happens when... https://www.warp.dev/blog/what-happens-when-you-open-a-terminal-and-enter-ls
* TUI for bash https://github.com/charmbracelet/gum
* design https://www.micahlerner.com/2021/07/14/unix-shell-programming-the-next-50-years.html 🗣 Dan Luu https://borretti.me/article/shells-are-two-things
* get current shell: `echo $SHELL` https://stackoverflow.com/a/3327022/6813490
* switch shell: `<shell>` https://fishshell.com/docs/current/tutorial.html#tut_getting_started
* return to default shell: `exit`

## terminal (iTerm)

FEATURES https://anarc.at/blog/2018-04-12-terminal-emulators-1/
* Unicode support: emojis, prompts https://darrenburns.net/posts/emoji-in-the-terminal/
* tabs/profiles
* viz: background color/image, transparency, themes e.g. gruvbox https://www.youtube.com/watch?v=h509rn2xIyU
* _hotkey_: keypress handled by listening program even if another program is active
* the killer feature https://news.ycombinator.com/item?id=17924264 https://news.ycombinator.com/item?id=22853277
* options: AutoHotKey https://www.hillelwayne.com/post/ahk/ https://www.autohotkey.com/ Hammerspoon, Keyboard Maestro https://news.ycombinator.com/item?id=34070951 Karabiner https://missing.csail.mit.edu/2019/os-customization/ https://news.ycombinator.com/item?id=30876934 Alfred https://www.alfredapp.com/ snap https://rectangleapp.com/

PROMPT
* things I want: Git branch, Python version, venv
* Git: https://www.youtube.com/watch?v=wku-1nJR_oA https://github.com/zachvalenta/dotfiles/commit/cc4117a72c7b1d80f0ec58021530727435a2e4af https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh https://stackoverflow.com/questions/31252573/get-current-directory-without-full-path-in-fish-shell
* _pure_: zsh only https://github.com/sindresorhus/pure
* _powerlevel10k_: https://github.com/romkatv/powerlevel10k
* _powerline_: statusline and prompt for Vim and used by zsh https://github.com/powerline/powerline
* can install via pip https://pypi.org/project/powerline-status/ https://github.com/wesbos/Cobalt2-iterm
* _starship_: https://starship.rs/
* downside: slower than powerline-shell, Git status looks worse
* upside: support for pyenv, Poetry https://starship.rs/config/#package-version
* install `brew install starship` or `sh -c "$(curl -fsSL https://starship.rs/install.sh)"`
* update `sh -c "$(curl -fsSL https://starship.rs/install.sh)"`
* uninstall `sh -c 'rm "$(command -v 'starship')"'`
* venv https://github.com/starship/starship/issues/1529
* won't get Python version if you're using an alias https://github.com/starship/starship/issues/632
* _powerline-shell_: powerline but works on bash and zsh (w/out ohmyzsh) https://github.com/b-ryan/powerline-shell
* conf: `~/.config/powerline-shell/config.json`
* requires powerline for fonts? https://powerline.readthedocs.io/en/latest/installation/osx.html
* no Poetry support https://github.com/b-ryan/powerline-shell/issues/507
* https://github.com/b-ryan/powerline-shell#generic-segments

ITERM 📜 https://iterm2.com/documentation.html
https://news.ycombinator.com/item?id=35126280
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

ALTERNATIVES
> UX also isn't something that can really be competed on for a terminal app as the UX is typically dictated by the shell, tool, tmux, etc. https://news.ycombinator.com/item?id=35125295
* _Hyper_: Electron https://hyper.is/
* _kitty_: can preview images in broot https://sw.kovidgoyal.net/kitty/
* _sshx_: ✅ real-time collaboration https://github.com/ekzhang/sshx
* _Tabby_: memory hog https://news.ycombinator.com/item?id=35111397
* _Warp_: launch configurations 类似 iterm profiles, need to login w/ Github https://news.ycombinator.com/item?id=30926360
* _Wezterm_: immature https://wezfurlong.org/wezterm/index.html

## windows

🔗 https://en.wikipedia.org/wiki/Windowing_system

SEMANTICS
* _window system_: server that displays graphics
* protocols: x11 https://unix.stackexchange.com/q/517 Wayland, pipewire https://www.youtube.com/watch?v=jFxwPJpUwl0 https://github.com/sharkdp/pastel#get-a-list-of-all-x11--css-color-names https://en.wikipedia.org/wiki/Wayland_(display_server_protocol) https://en.wikipedia.org/wiki/X_Window_System
* _window manager_: control windows displayed by window system https://en.wikipedia.org/wiki/Window_manager https://news.ycombinator.com/item?id=34591661 https://news.ycombinator.com/item?id=36880235
* _tiling window manager_: keyboard-driven arrangement of and switching btw windows
> https://www.youtube.com/watch?v=bdumjiHabhQ on i3 convinced me that this was potentially worthwhile just to not have to scroll for VS Code (and break dependency on iTerm auto hotkey)
* _desktop environment_: mouse-driven GUI riding on top of window system https://askubuntu.com/a/20435
* _display server_: ❓ e.g. Quartz Compositor (aka WindowServer) https://en.wikipedia.org/wiki/Quartz_Compositor https://unix.stackexchange.com/a/1016

DESKTOP ENV
* _GNOME_: https://blog.edfloreshz.dev/articles/linux/system76/rust-based-desktop-environment/
* _Material Shell_: https://news.ycombinator.com/item?id=24491091
* _Cinnamon_: https://news.ycombinator.com/item?id=24491091

---

WINDOW MANAGERS
* window manager https://news.ycombinator.com/item?id=34591661
* for Windows https://news.ycombinator.com/item?id=33168263
* for macOS https://magnet.crowdcafe.com/ https://news.ycombinator.com/item?id=22852157 https://faun.pub/yabai-macos-tile-window-manager-833ce1be396a?gi=132df1bca0e1 https://github.com/koekeishiya/yabai https://news.ycombinator.com/item?id=36368990
* AlwaysOnTop https://www.youtube.com/watch?v=6IxRlaTWsoQ
* _Amethyst_: macOS https://github.com/ianyh/Amethyst https://www.reddit.com/r/xmonad/comments/3j4tnt/is_it_possible_to_use_xmonad_on_os_x/
* _dwm_: https://dwm.suckless.org/
* _i3_: tiling + hotkeys https://www.youtube.com/watch?v=bdumjiHabhQ 3:30 https://www.youtube.com/watch?v=bdumjiHabhQ 1:30
* _PaperWM_: https://jvns.ca/blog/2020/01/05/paperwm/
* _Slate_: unmaintained https://github.com/jigish/slate
* _Sway_: https://swaywm.org/
* _X.org_: https://www.x.org/wiki/
* _XQuartz_: port of X.org for macOS https://www.xquartz.org/
* _xmonad_: x11, no macOS https://news.ycombinator.com/item?id=30402358 https://xmonad.org/
> I've mellowed as I've aged, but still fondly remember the thrill of the XMonad tiling window manager on multiple monitors — in particular, its responsiveness. With a few fast keyboard shortcuts, I could throw windows between monitors, arrange windows side-by-side, and immediately move focus to exactly the window I had in mind. XMonad also supports "virtual desktops", which I used to organize windows by task. For example, when working on a web app I'd put a terminal window, Emacs window, two web browsers (one for my app, the other for looking up documentation) all on the same virtual desktop. Then, when I wanted to do something else, I could switch to an empty virtual desktop, effectively saving my previous one "away for later". https://kevinlynagh.com/newsletter/2020_04_keyboards_rethinking_desktops/

# 🏞 USERLAND

🐍 in Python https://github.com/bugen/pypipe
🔍
* https://www.commandlinefu.com
* https://explainshell.com/ https://github.com/akavel/up
🗄
* `applications.md` utils
* `db.md` utils
* `git.md` utils
* `linux.md` denv

CORE
* versions: Linux uses GNU, macOS uses BSD (get w/ `brew install coreutils`) 📙 Evans shell [4]
* _dd_: copy/rm data https://github.com/akavel/up
* _df_: free disk space
* _file_: info on encoding, if executable
* _free_: disk space? free memory? `df` memory https://apple.stackexchange.com/q/4286/328389 or `duf` https://github.com/ibraheemdev/modern-unix `top` on macOS
* _bc_: do math on stdin https://missing.csail.mit.edu/2020/data-wrangling/
* _head_: 类似 SQL `limit` e.g. `ls <query> | head -4` or `kaiff` (`ls | sort -f | head -1 | xargs open`) https://stackoverflow.com/a/14510257/6813490
* _whereis_: search for executables in system db https://github.com/Idnan/bash-guide#c-whereis
* _which_: search for executables on path https://github.com/Idnan/bash-guide#d-which full path https://nil.wallyjones.com/what-shell-am-i-using/
* _rm_: send to `~/.Trash`; `i` prompt before each `R` answer yes to all prompts `rf` all recursively; alternatives https://github.com/nivekuil/rip https://github.com/arsenetar/send2trash/issues https://github.com/arsenetar/send2trash/issues/56 https://hacker-tools.github.io/command-line/
* _w_: who is logged in and what they're doing https://rachelbythebay.com/w/2018/03/26/w/
* _watch_: https://github.com/sachaos/viddy

MODERN
* _asciicinema_: terminal recording https://darrenburns.net/posts/tools/ https://github.com/nbedos/termtosvg https://github.com/cytopia/ffscreencast https://github.com/charmbracelet/vhs
> vhs as alternative https://github.com/charmbracelet/vhs/ https://github.com/TypicalAM/goread
* _ffmpeg_: video encoding, file format conversion https://www.youtube.com/watch?v=MPV7JXTWPWI https://ffmpeg.guide/ https://img.ly/blog/ultimate-guide-to-ffmpeg/
* _imgcat_: render img in terminal https://news.ycombinator.com/item?id=23319272
* get file duration https://www.youtube.com/watch?v=s6DXMf_yj64
* _gotty_: term as web app https://github.com/yudai/gotty
* _neofetch_: system info
* _pdfgrep_: https://pdfgrep.org/ alternative
* _scc_: code stats https://github.com/XAMPPRocky/tokei
* _tee_: view output https://www.youtube.com/watch?v=NsAUBict1Aw
* _tldr_: cheatsheets https://github.com/tldr-pages/tldr/tree/master/pages https://github.com/dbrgn/tealdeer https://github.com/chubin/cheat.sh
* _tsukae_: view most commonly used commands https://github.com/irevenko/tsukae
* _try_: view files that command touches https://github.com/binpash/try
* weather: https://github.com/chubin/wttr.in https://github.com/fcambus/ansiweather https://pirateweather.net/
* Wikipedia https://github.com/yashsinghcodes/wik

AUTOJUMP
* _autojump_: jump to recently visited dir https://missing.csail.mit.edu/2020/shell-tools/
* what I use: lots of alias in `.bash_profile`
* options: https://github.com/rupa/z https://github.com/wting/autojump https://github.com/clvv/fasd https://github.com/ajeetdsouza/zoxide https://github.com/mfaerevaag/wd
* BYO https://news.ycombinator.com/item?id=22853119

COREUTILS
* _coreutils_: ls, rm, cat, et al. https://en.wikipedia.org/wiki/List_of_GNU_Core_Utilities_commands
* aka userland https://bitfieldconsulting.com/golang/scripting
* aka "modern UNIX" https://www.thoughtworks.com/radar/tools/modern-unix-commands
* Rust rewrite https://news.ycombinator.com/item?id=26396798 https://jvns.ca/blog/2022/04/12/a-list-of-new-ish--command-line-tools/ https://github.com/ibraheemdev/modern-Unix

CLI IMPL LANGUAGE 🗄 `information.md` serialization `python.md` CLI
> use Rust for CLI and Python for business logic? https://github.com/chubin/wttr.in
* tracking user info https://www.visidata.org/blog/2021/usage-graphs/
> build modern CLI applications without worrying about user accounts, data storage and encryption https://github.com/charmbracelet/charm#charm-kv
* fuzzy find https://github.com/denisidoro/navi
* C: ✅ fast ❌ development speed
* Nim: ✅ distribution ❌ maturity https://ssalewski.de/nimprogramming.html
* Python: ✅ exploratory ❌ distribution
* Go: ✅ distribution, fast startup https://news.ycombinator.com/item?id=23319684 ❌ stdlib lib lib not good
* Rust: ✅ speed, Clap library https://news.ycombinator.com/item?id=23320411 better for cross platform https://cuchi.me/posts/go-vs-rust ❌ language itself

CP
* dir: `cp -r <dir> <path/to>`
* dir but exclude `.git`_: `cmd --exclude=.git <source> <target>` https://stackoverflow.com/a/3672584
* dir contents: `cp -r <dir>/ <path/to>`

DASHBOARDS 🗄 `python.md` TUI
* https://github.com/wtfutil/wtf
* https://github.com/Phantas0s/devdash
* https://github.com/gizak/termui

HISTORY https://catonmat.net/the-definitive-guide-to-bash-command-line-history
* search: `ctrl r`
* scroll all items that match query: `ctrl r` (again)
* cancel search: `ctrl c`
* scroll previous: `ctrl p`
* scroll next: `ctrl n`
> same when you're in search mode
* event designator: `history | rg cd` then go to event w/ `!<event_num>`
> it can be helpful to stick something like `#useful` or `# description` on the end of a command you expect to need again https://news.ycombinator.com/item?id=13888269
* https://github.com/cantino/mcfly

MONITORING
* directory size: du, ncdu https://github.com/bootandy/dust `du -sh -- * | sort -r` https://unix.stackexchange.com/a/185777 https://github.com/muesli/duf https://github.com/imsnif/diskonaut
* disk space: view of mounts; `df -h`; colorize https://danyspin97.org/blog/colorize-your-cli/
* memory: free (UNIX) top (macos) gotop https://github.com/xxxserxxx/gotop/issues/50 ytop https://github.com/cjbassi/ytop htop https://tech.marksblogg.com/top-htop-glances.html below https://github.com/facebookincubator/below https://github.com/bvaisvil/zenith
* network: https://github.com/imsnif/bandwhich

SNIPPETS
* live log view `tail -f foo.log`

* copy output to clipboard : `<cmd> | pbcopy` https://github.com/Slackadays/Clipboard
* copy file to clipboard: `pbcopy < ~/.ssh/id_rsa.pub`

TUI
* https://news.ycombinator.com/item?id=40273177
* _curses_: UNIX https://docs.python.org/3/howto/curses.html https://github.com/cmus/cmus 
* _ncurses_: Linux https://github.com/jesseduffield/lazydocker https://github.com/NerdyPepper/dijo

## file

FILE/DIR DIFF
* _vimdiff_: `vim -d <file1> <file2>` https://stackoverflow.com/a/113328/6813490
* wraps Vim's diff mode for use in other tools, notably Git's mergetool https://vi.stackexchange.com/a/626 https://www.youtube.com/watch?v=kFVjoIish0E
* _diff_: https://danyspin97.org/blog/colorize-your-cli/ diffing trees https://github.com/trailofbits/graphtage
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
* _entr_: https://github.com/eradman/entr https://jvns.ca/blog/2020/06/28/entr/ https://github.com/eradman/entr/issues/45 http://eradman.com/posts/repeatable-workspaces.html
* _fswatch_: https://github.com/emcrisostomo/fswatch https://slack.engineering/development-environments-at-slack/
* _watch_: https://www.youtube.com/watch?v=bB2TmCfJiX8
* _watchman_: https://facebook.github.io/watchman/ https://adamj.eu/tech/2021/01/20/efficient-reloading-in-djangos-runserver-with-watchman
* _hwatch_: https://github.com/blacknon/hwatch

### explorer (broot)

📜 https://dystroy.org/broot/ https://github.com/Canop/broot

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

FILE EXPLORERS
* _file explorer_: TUI for file system e.g. Finder (mv, rm, preview)
* aka file browser, file manager
* _fff_: https://github.com/dylanaraps/fff/issues/135 
* _lf_: https://www.youtube.com/c/BrodieRobertson/search?query=lf
* _mini_: 🎯 https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-files.md
* _nnn_: https://github.com/jarun/nnn
* _telescope_: 🎯 https://github.com/nvim-telescope/telescope.nvim https://www.youtube.com/watch?v=OhnLevLpGB4 https://www.youtube.com/watch?v=indguFY7wJ0
* _superfile_: 🎯 https://github.com/MHNightCat/superfile https://news.ycombinator.com/item?id=40323101
* _vifm_: https://github.com/vifm/vifm https://www.youtube.com/watch?v=RGOsE3UWqhI https://www.youtube.com/watch?v=6eyFXcyosu8
* _walk_: https://github.com/antonmedv/walk
* _xlpr_: https://github.com/sayanarijit/xplr https://news.ycombinator.com/item?id=33209020

### find (fd)

📜 https://github.com/sharkdp/fd

* snippets
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

alternatives
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

### list (exa)

📜 https://github.com/ogham/exa https://the.exa.website/
> replaced? https://github.com/eza-community/eza https://github.com/lsd-rs/lsd

exa
* conf https://the.exa.website/docs/environment-variables
* no Git in grid view https://github.com/ogham/exa/issues/927
* grid-details aka long grid https://the.exa.website/features/long-view#long-grid
* long view without metadata https://the.exa.website/features/grid-view
* icons from nerd font https://the.exa.website/features/icons
> only work with more recent version of exa i.e. not available on mbp14

ls
* colorize https://danyspin97.org/blog/colorize-your-cli/ solarized https://news.ycombinator.com/item?id=33400822
* https://github.com/Yash-Handa/logo-ls
* list number of dir/files in $CWD/subs: `tree | tail -1`
> so tree gives some output stats that exa's tree mode doesn't?

---

* `ls`: a (hidden files) l (perms) F (file type) S (size) t (sort on write timestamp); if there's a tenth character in the column `@` it’s something to do w/ ACL (access control list) on the file https://linux-audit.com/plus-sign-ls-output/
* _tree_: ignore multiple https://unix.stackexchange.com/a/47806/331460 https://superuser.com/questions/772567/how-to-get-tree-a-to-ignore-git-directories
```sh
# https://superuser.com/a/595699/728972
tree -if | grep <query>
```
* exa will list `.gitignore` files with marker
```sh
.rw-r--r--@  459 zv_mac 14 Feb 12:02 -I accounts.md
.rw-r--r--@ 1.2k zv_mac 16 Feb 08:48 N- company.md
.rw-r--r--@ 4.8k zv_mac 16 Feb 08:49 N- eng.md
.rw-r--r--@ 2.5k zv_mac 16 Feb 07:57 N- onboarding.md
.rw-r--r--@ 9.4k zv_mac 16 Feb 09:28 N- payments.md
```
* solarized https://news.ycombinator.com/item?id=33400822
* `LS_COLORS`: var that controls output of ls, tree https://github.com/sharkdp/vivid https://github.com/chriskempson/base16-shell
* no color https://news.ycombinator.com/item?id=30483417
* color https://news.ycombinator.com/item?id=33407620 https://fishshell.com/
* vivid https://github.com/sharkdp/vivid
use vivid with exa_colors https://github.com/mimame/.dotfiles/blob/b097b3dba50dc4ed7ff26886678392aa6926bed7/zsh/.zshrc#L152
🎗 `exa` already handles a bunch of filetypes for you https://the.exa.website/features/colours
* `exa` w/ `.gitignore`: smart enough to ignore everything in `.gitignore` if it's in the root directory, but `exa --tree` won't, so you have to add `.DS_Store` et al. via `exa -I`   https://github.com/ogham/exa/issues/136 https://github.com/ogham/exa/issues/408
256 color codes https://github.com/trapd00r/LS_COLORS https://github.com/search?q=exa_colors&type=Code https://www.howtogeek.com/307899/how-to-change-the-colors-of-directories-and-files-in-the-ls-command/

rf your bash profile https://github.com/search?q=exa_colors&type=Code
* color symlinks (or just use default purple)
* show .gitignored env files
* background - white: `export LS_COLORS="*.py=38;5;114;47"`
* foreground - pink: `38;5;213`
* foreground - coral: `38;5;114`

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

color output: `tput` https://stackoverflow.com/a/20983251/6813490

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

## jobs (cron)

🗄 `distributed.md` TQ

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

---

* use postgres https://github.com/cybertec-postgresql/pg_timetable
* https://www.youtube.com/watch?v=AHAAA7zfT7Q
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

* https://www.twilio.com/blog/2017/04/wedding-at-scale-how-i-used-twilio-python-and-google-to-automate-my-wedding.html
* https://github.com/SkullTech/drymail
* https://github.com/caronc/apprise
* https://github.com/fonoster/fonos
* https://hacker-tools.github.io/automation/
* Python https://github.com/agronholm/apscheduler
* _anacron_: runs certain time after system start i.e. better for personal machine; 1 time/day
* _launchd_: macOS equivalent https://blog.bejarano.io/fixing-cron-jobs-in-mojave.html
* _batch_: runs when server load drops below specific level
* _Autosys_: tool for coordinating cron jobs; first heard about this 2017.11
* _monitoring_: https://github.com/healthchecks/healthchecks

* _cron_: expects specific time i.e. better for server
* `/etc/crontab` for system
* `~/crontab` for user
>  It’s a simple text file with an ASCII table that will execute a command on schedule. 📙 Conery [422]
* `crontab -e`: edit crontab 📙 Conery [422]
* `crontab -l`: see active entries

* syntax https://www.youtube.com/watch?v=QZJ1drMQz1A&t=895s https://crontab.guru/
```sh
# 1-min(0-59) 2-hour 3-day(month) 4-month 5-day(week)
5 * * * *  # 5th minute of every hour, every day of month, every month, every day of week
```

## munge (awk, sed)

🗄 `sql.md` munge

COLUMNAR
* _cut_: rm columns https://blog.balthazar-rouberol.com/text-processing-in-the-shell#cut https://kadekillary.work/posts/cli-4-ds/ https://github.com/theryangeary/choose https://github.com/ibraheemdev/modern-unix
```sh
# todo
```
* _awk_: process columnar data https://kadekillary.work/note/awk/ https://benhoyt.com/writings/goawk/ https://kadekillary.work/post/cli-4-ds/ https://neowaylabs.github.io/programming/unix-shell-for-data-scientists/ 📙 Kernighan https://github.com/thewhitetulip/awk-anti-textbook/ https://en.wikipedia.org/wiki/The_AWK_Programming_Language https://blog.jpalardy.com/posts/why-learn-awk/ https://gregable.com/2010/09/why-you-should-know-just-little-awk.html http://www.grymoire.com/Unix/Awk.html
* avoid by parsing stdout to JSON then using JSON query tool e.g jq https://github.com/kellyjonbrazil/jc https://www.thoughtworks.com/radar/tools?blipid=202203056
* versions: `awk- W version` (doesn't work on macOS) ; mawk (Ubuntu, Debian) gawk (other distro incl macOS)
* rm blank lines: `"NF"` https://stackoverflow.com/a/29549497
* sum: 🗄 `.bash_profile` agg
* get $PWD from path: `awk -F"/" '{print $NF}'` https://stackoverflow.com/a/17921589
* get last word in line https://stackoverflow.com/a/16617037
* sum series of numbers https://stackoverflow.com/a/28926450
```sh
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

STREAM EDITING 🗄 `vim.md` argdo
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
* _tr_: string edit e.g. case, add newline https://github.com/Idnan/bash-guide#k-tr https://shapeshed.com/unix-tr/ https://blog.balthazar-rouberol.com/text-processing-in-the-shell#tr
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

📜 https://github.com/sharkdp/bat

```sh
# CONFIG
bat --config-dir
bat --config-file
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

## text search (ripgrep)

🗄 `vim.md` code completion

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
