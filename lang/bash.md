# ⛩️

## 参考

📚
* Barrett https://www.amazon.com/gp/product/1098113403 https://fabiensanglard.net/bash/
* Shotts linux command line https://www.linuxcommand.org/tlcl.php
* Stutz cookbook
🔗
* https://github.com/dylanaraps/pure-bash-bible
* https://github.com/anordal/shellharden/blob/master/how_to_do_things_safely_in_bash.md https://jvns.ca/blog/2023/08/08/what-helps-people-get-comfortable-on-the-command-line-/
* https://leanpub.com/learnbashthehardway
* https://wizardzines.com/zines/bite-size-bash/
* https://mywiki.wooledge.org/BashGuide/Practices

## 进步

# 🟨 ZA

## args

* access
```sh
$@  # all e.g. for file in "{$files[@]}"
$#  # get by number
$_  # get previous arg https://www.youtube.com/watch?v=vt-IvdFP5ZA

# get positional
$ cmd arg1 arg2 # $0 = cmd, $1 = arg1, $2 = arg2, $@ = all args

# set default https://stackoverflow.com/a/33419280
function agg(){
    # e.g. `agg` -> YEAR = 23; `agg 21` -> YEAR = 21
    YEAR=${1:-23}
    rg foo "$YEAR"/??.dat
}
```

* checks
```sh
if [ $# -eq 0 ]  # none
if [ "$var" = "$var" ]  # equality
if [ -z "$var" ]  # empty string: -z (true if empty) -n (true if not empty) https://stackoverflow.com/a/18096739
if [[ "$var" =~ ^-?[0-9]+[.,]?[0-9]*$ ]]  # integer https://stackoverflow.com/a/28898213
```

## checks

```sh
# EMPTY / NON-EMPTY
if [ "$var" ]  # assert non-empty
if [ -z "$var" ]  # assert empty

# TYPE INFO https://www.youtube.com/watch?v=hrbV5WGxxdY
file $FILE

# ENV VAR SET
if [ -z "$OPENAI_API_KEY" ]; then
    echo "OPENAI_API_KEY not set. Set in aider.env."
    exit 1
fi

# CHECK FILE EXISTS
test -f "path/to/file" && echo "exists" || echo "does not exist"

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

## control flow

📜 https://ss64.com/bash/if.html

BOOLEAN OPERATORS
```sh
&&  # AND
```

---

```txt
So you have to use double braces ([[) if you use boolean operators like &&?

Not quite. The difference is more nuanced:

Single square brackets [ ]:
* Traditional POSIX shell syntax
* Requires spaces around operators
* Requires explicit -n or -z for string tests
* Boolean operators (&&, ||) work best outside the brackets

Double square brackets [[ ]]:

* Bash-specific extended test command
* More flexible string handling
* Allows && and || directly inside the brackets
* Provides some additional features like pattern matching

So you can use boolean operators with single brackets, but you need to do it differently:
```

```sh
A ; B # A then B (regardless of A exit code)
A || B # if not A then B
A & B # A and B simultaneously
```

ITERATION
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
> ternary https://run.jotaen.net/
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

## design

📙 https://aosabook.org/en/v1/bash.html

---

* inspired by Algol https://news.ycombinator.com/item?id=42020368 https://www.youtube.com/watch?v=olH-9b3VJfs https://shellhaters.org/talk
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

## execution

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

## snippets

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

---

* generate random string https://unix.stackexchange.com/a/230710/331460
* fallback value https://run.jotaen.net/

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
