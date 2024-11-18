# ⛩️

## 参考

📜 https://man7.org/linux/man-pages/index.html
🔍
* https://serverfault.com/
* https://unix.stackexchange.com/
📚
* Evans linux
* Evans za
* Kerrisk lpi
* Stutz cookbook

## 进步

clean up https://github.com/clarkema/x12pp
https://roadmap.sh/linux
BYO linux https://drewdevault.com/2024/05/24/2024-05-24-Bunnix.html

* _24_: combine Homebrew and other managers
* _23_: Conery unix chapter
* _22_: denv
* _19_: symlink dotfiles
* _18_: scripts (`fne`, `qing`, `ding`, `qiu`, `jb`)

# 🏗️ BUILD SYSTEMS

🗄
* `svc/src.md` deployment
* `algos.md` graphs

BUILD SYSTEMS
* BYO http://aosabook.org/en/500L/contingent-a-fully-dynamic-build-system.html
* _Bazel_: Make for FANG https://eng.uber.com/go-monorepo-bazel/ https://github.com/bazelbuild/bazel https://testdriven.io/blog/bazel-builds/ https://www.youtube.com/watch?v=zaymCO1A1dM
* _cmake_: 不明觉厉 https://stackoverflow.com/a/25790020 http://aosabook.org/en/cmake.html
* _Meson_: https://mesonbuild.com/
* _ninja_: https://github.com/ninja-build/ninja https://jvns.ca/blog/2020/10/26/ninja--a-simple-way-to-do-builds/
* _Nx_: monorepos https://github.com/nrwl/nx
* _Pants_: https://github.com/pantsbuild/pants https://rdrn.me/postmodern-python/
* _redo_: https://github.com/apenwarr/redo https://fzakaria.com/2020/06/08/my-love-letter-to-redo.html

TASK RUNNERS
* _makedown_: Markdown https://github.com/tzador/makedown
* _mise_: 🎯 https://github.com/jdx/mise https://github.com/shuru-project/shuru
* _pypyr_: https://pypyr.io/
* _Task_: 🎯 https://github.com/go-task/task
* _Xc_: Markdown https://github.com/joerdav/xc https://news.ycombinator.com/item?id=34911216 https://news.ycombinator.com/item?id=34911216

---

📍 NEED TO TAXONOMIZE BTW TASK RUNNER AND BUILD SYSTEM https://chatgpt.com/c/672d26cf-0e5c-8004-8692-6333538088c0

https://pycon-archive.python.org/2024/schedule/presentation/112/index.html
> Binary extensions underlie much of the modern Python ecosystem, providing performance and access to a wealth of existing code. Packaging for these libraries is rapidly changing from thousands of lines of distutils and setuptools based hackery to build systems designed for binaries like scikit-build-core, meson-python, and maturin. NumPy, for example, went from around 13K to 2K lines of building related code by moving to Meson in NumPy 1.26.
> These build systems provide a much more integrated experience than was previously possible for compiled extensions. For example, CMake or Ninja are only required if the system doesn’t already provide an appropriate copy, which allows building with an external ninja/cmake on systems without binary wheels on PyPI like Pyodide, BSD, and Android. Modern editable installs are supported. Support for advanced features like ABI3 wheels or wheels that don’t call CPython is usually just a single configuration option.
> We will look at how easy it is now to set up a binary extension using CMake, Meson, or Maturin (Rust only). It can be done with only three files each containing only a handful of lines of code. Unlike the previous solutions, this covers cross-compilation,multithreaded builds, modern C++ standards, and other features that would each require custom code in a classic setup.py. Combined with cibuildwheel for building wheels and good support from modern binding tools like pybind11 and nanobind, the barrier for entry to reliable compiled extensions has dropped dramatically.
> We will also look at the challenges and solutions from some larger conversions to modern build systems, like NumPy’s and RAPIDS.ai.
> After this talk, you will know how to easily create compiled extensions to solve problems you encounter, and how to move existing projects to these modern build systems.

* _build system_: build executables (esp. for C, C++) https://signalsandthreads.com/build-systems/
* aka task runner, command runner https://github.com/casey/just https://en.wikipedia.org/wiki/List_of_build_automation_software https://github.com/go-task/task
* dependency graphs, build systems https://rhodesmill.org/brandon/slides/2021-06-colombia-remote/
* analyze dependency graph https://github.com/loov/goda
* faster deploys really save a lot of time https://github.blog/2022-12-08-experiment-the-hidden-costs-of-waiting-on-slow-build-times/

## just

---

* _just_: 🎯 https://github.com/casey/just https://news.ycombinator.com/item?id=34317359 https://news.ycombinator.com/item?id=34073529 https://github.com/pls-rs/pls/blob/main/justfile https://github.com/pls-rs/pls/blob/main/docs/justfile https://github.com/pythops/tenere
https://luke.hsiao.dev/blog/housing-documentation/

## make

📙 Meckleberg gnu make

---

* _make_: ✅ https://github.com/casey/just?tab=readme-ov-file#what-are-the-idiosyncrasies-of-make-that-just-avoids https://news.ycombinator.com/item?id=19900955 https://stackoverflow.com/a/3798664
* `all`, `clean`, `.PHONY`, `install` 📙 Conery [405]
> Make builds output files from input files. It was originally designed for C programs, which utilize both code and header files which are built into object files. These object files are then compiled to binary. This is a multi-step build that requires some orchestration. That’s what Make is all about. 📙 Conery [406]
* docs: `gnu-make.pdf` https://www.gnu.org/software/make/manual/make.html https://tech.davis-hansson.com/p/make/ http://gromnitsky.users.sourceforge.net/articles/notes-for-new-make-users/ https://www.openmymind.net/An-Awful-Introduction-To-Make/ https://makefiletutorial.com/ https://daniel.feldroy.com/posts/autodocumenting-makefiles
* call from another directory 🗄 music-prompt
* good for compilation https://www.youtube.com/watch?v=SdmYd5hJISM&lc=UgyBo0rkqGXZgLDmsRZ4AaABAg.9KU4gvKdDyN9KU9XbK1Cyl
* using shell script to handle more args https://www.youtube.com/watch?v=SdmYd5hJISM
* lot of blockers if you want it to work on Windows https://carolynvanslyck.com/blog/2021/01/mage-is-my-favorite-make/
* rules are run in separate shell https://stackoverflow.com/a/49621071
* control flow https://stackoverflow.com/a/14864888 https://stackoverflow.com/a/5553445 https://nullprogram.com/blog/2017/08/20/
* documentation at the level of the rule https://www.thapaliya.com/en/writings/well-documented-makefiles/ https://diamantidis.github.io/tips/2020/07/01/list-makefile-targets
* autocomplete https://stackoverflow.com/questions/4188324/bash-completion-of-makefile-target https://stackoverflow.com/questions/33760647/makefile-autocompletion-on-mac
* directories https://github.com/zachvalenta/query-sandbox
* _phony_: target that is name for a recipe vs. file name https://stackoverflow.com/a/3931814/6813490
* snippets
* escape dollar signs bc Make assumes you are referencing a Make variable otherwise (vs. shell variable or string literal) https://til.hashrocket.com/posts/k3kjqxtppx-escape-dollar-sign-on-makefiles
```sh
for i in *; do echo "i=$i"; done
```
```makefile
my-files:
	for i in *; do echo "i=$$i"; done
```

```makefile
#
# VARAIABLES 📙 Conery [410]
#

# reference env var https://stackoverflow.com/questions/28890634/how-to-get-a-shell-environment-variable-in-a-makefile
${var}

# args https://blog.mindlessness.life/2019/11/17/the-language-agnostic-all-purpose-incredible-makefile.html
env="dev"  # global
make deploy env=qa
deploy:
	echo $(env)

make bdd-dev,qa
bdd-%:
	poetry run behave --tags @${*}

#
# MISC
#

# syntax: whole thing called a rule (like CSS) http://gromnitsky.users.sourceforge.net/articles/notes-for-new-make-users/#4b6d995-adhere-to-the-common-terminology
target: prereq1 prereq2
    recipe

# points make to target (vs. file of same name) https://krzysztofzuraw.com/blog/2016/makefiles-in-python-projects.html
.PHONY

# combine rules https://stackoverflow.com/a/3519634
dummy: target1 target2

# ignore failure i.e. won't stop another recipe from running if it fails https://stackoverflow.com/a/53039783
ur-recipe:
    - rm $(file)

# hide cmd output https://stackoverflow.com/a/18105278
cmd:
    @poetry run pytest
```

# 🪐 DENV

🗄
* `it.md` fs, provision
* `src.md` denv

## dotfiles

🗄️ `it.md` fs

* `XDG_CONFIG_HOME`: typically `$HOME/.config` https://github.com/lusingander/serie/issues/25 https://github.com/kraanzu/dooit/issues/195
> On macOS, `$XDG_CONFIG_HOME` maps to $HOME/.config. Another popular path for config files is `/Users/USER/Library/Application\ Support`. Does this file path have a env var name in the way that $XDG_CONFIG_HOME does?
* you have to manually specify?
> If you want to change the config directory: macOS `export XDG_CONFIG_HOME="$HOME/.config` https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md

* write script to do symlinks https://news.ycombinator.com/item?id=34304694
* prefer programs that store config as text
* keep under version control and symlink into place with script https://hacker-tools.github.io/dotfiles/ advanced mgmt https://github.com/twpayne/chezmoi https://news.ycombinator.com/item?id=32632533 https://github.com/atuinsh/atuin
> There are two basic approaches: version your entire home directory or symbolically link your dotfiles into place from a stand-alone repository. The first approach is straightforward but has a number of issues that make it a poor choice. https://nullprogram.com/blog/2012/06/23/
* install script https://www.youtube.com/watch?v=hXU54axdjJc https://alexpearce.me/2016/02/managing-dotfiles-with-stow/
* mgmt: GNU Stow https://www.youtube.com/watch?v=90xMTKml9O0 https://github.com/bbkane/fling https://drewdevault.com/2019/12/30/dotfiles.html
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

## env var

🗄
* `security.md` users/ passwords
* `src.md` deployment / secrets

DIRENV 📜 https://github.com/direnv/direnv
* load env var based on dir
* alternative https://github.com/jdx/mise
* usage https://www.youtube.com/watch?v=udezempDBVQ
* use case https://jamey.thesharps.us/2019/05/29/per-project-postgres/

CMDS
```sh
export FOO="val"      # set
DEBUG=true npm start  # set tmp to run cmd
echo $FOO             # read
env                   # list all
unset $FOO            # unset
```

---

* https://github.com/zed-industries/zed/blob/main/docs/src/environment.md
* 🗄 `broot.log` https://unix.stackexchange.com/a/106606/331460 https://github.com/thoughtbot/til/blob/master/bash/bash_profile_vs_bashrc.md
* _envsubst_: sub env var into fmt strings https://nickjanetakis.com/blog/using-envsubst-to-merge-environment-variables-into-config-files
```sh
foo.sh  # echo $LOGNAME 
./foo.sh           # stdout: $LOGNAME
envsubst < foo.sh  # stdout: zach
```

## path

TOOLS
* _has_: check tool (python, java) on PATH https://github.com/kdabir/has
* _justpath_: edit https://github.com/epogrebnyak/justpath
* _pathos_: edit https://terminaltrove.com/pathos/

---

* https://wizardzines.com/comics/path-tips/ https://simonw.substack.com/p/video-scraping-using-google-gemini
* https://blog.izissise.net/posts/env-path/
* `$PATH`: list of directories that the shell should search when looking for programs corresponding to commands entered by the user [LPI 2.7]
* change precedence: https://apple.stackexchange.com/a/49961
* _default_: `/bin`, `usr/bin`
* _global_: `/etc/paths`
* _user_: `.bash_profile`

## profiles

---

ZSH https://unix.stackexchange.com/a/71258
* `.zshenv`: src for all shells
> often contains exported variables that should be available to other programs. For example, $PATH, $EDITOR, and $PAGER are often set in .zshenv. Also, you can set $ZDOTDIR in .zshenv to specify an alternative location for the rest of your zsh configuration.
* `.zprofile`: src for login shells, src before `.zshrc`
* `.zshrc`: src for interactive shells

ALIASES
* `alias`: list all
* _alias_: evaluated when shell loads profile
* view: `type <alias>` https://www.youtube.com/watch?v=aLMepxvUj4s 4:15
* use unaliased: `\cd` https://stackoverflow.com/a/11056541

SHELL TYPES https://github.com/nushell/nushell/issues/8169
* _interactive_: normal
* _non-interactive_: process spawned when script run 📙 LPI 2.2 https://unix.stackexchange.com/questions/43385/what-do-you-mean-by-interactive-shell/43389#43389 
* _login_: reads profiles and env var 
* _non-login_: cron jobs https://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell/46856#46856 https://www.quora.com/What-are-the-differences-between-a-login-shell-and-a-non-login-shell/answer/Rod-Nussbaumer-1?srid=ebCJ

---

* https://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/
* macOS execution order: `.bash_profile`, `.bash_login`, `.profile`

---

* bash automatically sources `.bash_profile`

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

# 📦 PACKAGING

🗄
* `system.md` deployment
*️ `python/runtime.md` packaging / mgmt

---

Rust
Golang https://til.simonwillison.net/go/installing-tools https://jerrynsh.com/3-easy-ways-to-add-version-flag-in-go/

💡 pkg manager = network, disk, standards, resolution https://talkpython.fm/episodes/transcript/476/unified-python-packaging-with-uv

MORE MACOS OPTIONS https://github.com/cli/cli?tab=readme-ov-file#installation
* _macports_:
* _spack_: https://spack.io/
* _webi_: https://github.com/webinstall/webi-installers

SEMANTICS
* _app_: runs on your box
* _executable_: runs on someone else's box
* _library_: used in someone else's app/executable/library
* less e.g. jQuery
* _framework_: lib + default methods called
* more e.g. React

BINARIES
* management: Artifactory, Nexus, Github Package Registry, Pulp https://pulpproject.org/ people also use these for language libraries and object stores as well https://devops.stackexchange.com/a/1900
* containerized runtimes e.g. flatpak, Steam https://ludocode.com/blog/flatpak-is-not-the-future https://news.ycombinator.com/item?id=30408161
```python
# upload
my_file = {"file": open(f"{file_name}", "rb")}
requests.put(artifactory_url, files=my_file, verify=False, auth=(user, pw))
# list archives in dir http://stackoverflow.com/a/55892053
requests.get(artifactory_url, verify=False, auth=(user, pw)).json()['children']
```
* _precompiled binary_: using what you've been given e.g. broot needs Rust as build dep, I don't have Rust, but I can still grab broot from Homebrew; downside is that in the app's build process, could be trying to run something sudo or trying to download one of its dependencies w/out verifying a checksum https://www.vitavonni.de/blog/201503/2015031201-the-sad-state-of-sysadmin-in-the-age-of-containers.html
* notarized binary: https://www.kencochrane.com/2020/08/01/build-and-sign-golang-binaries-for-macos-with-github-actions/
* _build from source_: can set compiler flags to optimize for your os (e.g. turn off debugging metrics so it runs faster) https://softwareengineering.stackexchange.com/a/167507 https://golang.org/doc/install#download

---

* https://drewdevault.com/2021/09/27/Let-distros-do-their-job.html
* https://drewdevault.com/2018/01/10/Learn-your-package-manager.html

* BYO package manager https://news.ycombinator.com/item?id=37220953
🔍 https://repology.org/ https://github.com/ziglang/zig/wiki/Install-Zig-from-a-Package-Manager
🙂 https://xkcd.com/2347/

* os has to trust pkgs to a degree https://lwn.net/Articles/770784/ https://news.ycombinator.com/item?id=23678409
* not a solved problem and no consensus on how it should be solved https://news.ycombinator.com/item?id=24140848
* BYO https://nullprogram.com/blog/2018/03/27/
* tracking stats https://lwn.net/Articles/826216/
* never update anything if you can avoid it https://blog.kronis.dev/articles/never-update-anything
* pkg mgmt https://news.ycombinator.com/item?id=34577844

## dependencies

🗄
* `golang.md` packaging
* `python.md` packaging

SEMVER https://stackoverflow.com/a/22345808
> what fmt is this? https://zed.dev/releases/stable/0.149.3
* https://mitchellh.com/writing/ghostty-is-coming
* _patch_: update all patches w/out changing minor e.g. `~1.3.7` gets everything up to `1.4.0`
* _minor_: update all patch + minor w/out changing major e.g. `^1.3.7` gets everything up to `2.0.0`
* definitions fuzzy e.g. what does "major" actually mean e.g. breaking change? for what percentage of users? https://gist.github.com/jashkenas/cbd2b088e20279ae2c8e https://snarky.ca/why-i-dont-like-semver/
* Golang brings into the realm of module/packges namespace (and therefore imports), meaning a version that is backwards incomptable must have a new namespace https://research.swtch.com/vgo-import https://news.ycombinator.com/item?id=16431299 🗄 `golang.md` 'semantic import versioning'
* contradictory interpretations? https://poetry.eustace.io/docs/basic-usage/#version-constraints https://docs.npmjs.com/about-semantic-versioning#using-semantic-versioning-to-specify-update-types-your-package-can-accept https://poetry.eustace.io/docs/versions/ https://research.swtch.com/deps

---

* https://calmcode.io/datasets/dependencies
* db of deps across org https://dmd.tanna.dev/

> years ago websites were made of files; now they are made of dependencies https://alexdanco.com/2019/10/26/everything-is-amazing-but-nothing-is-ours/

* vet https://github.com/irgolic/vet
* incl comment for each dep explaining need https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies 13:15
* update lockfile periodically https://news.ycombinator.com/item?id=30578276

* just pull unmaintained repos in your own lib https://lucumr.pocoo.org/2024/3/26/rust-cdo/
* dependabot for Python https://pyup.io/

> However. How can curl disappear? Curl is not just one of the most important dependencies, it's also one of the most resilient dependencies. When you or me install curl, we rarely install it from the official website. Curl is more likely to come from a mirror, vendored into a library we're using, there are a lot of forks in proprietary code bases etc. Curl is an unkillable dependency. Not only can the website go down, also the original developer could probably go away and someone would pick up the work, it's that useful. Let's contrast this for a second with the situation on npm...A few days ago the developer behind that library [colors] decided to release a new version of the library that no longer does what it advertised on the tin. Since it was a minor update quite a few people ended up with that version. They didn't however even know that they were depending on “that one package”, they probably pulled it in because something else in their dependency chain needed it. https://lucumr.pocoo.org/2022/1/10/dependency-risk-and-funding/

* _dependency resolution_: dep A and B both rely on pkg C, but they need different versions, what to do?
* _language dep ecosystem_: central pkg repo; each pkg w/ dependency manifest (`package.json`) lockfile (`poetry.lock`) and each version tagged according to semver https://blog.golang.org/versioning-proposal
* _determinism_: can pin version in human-readable file (`requirements.txt`) but then subject to library developers' interpretation of semver, whereas lockfile (`poetry.lock`) will give you exact build of dependency https://yarnpkg.com/blog/2017/05/31/determinism/ https://www.youtube.com/watch?v=wRHi8Ui5vWA
* _snapshot_: non-prod release https://stackoverflow.com/a/5901460/6813490
* _reproducible build_: attack vector in pkg distribution is discrepancy between src and artifact https://robertheaton.com/2018/11/17/reproducible-beliefs/ 🗄 `linux.md` Make
* _vendoring_: deps themselves under version control https://hacker-tools.github.io/package-management/ https://nullprogram.com/blog/2020/01/21/ protection against library disappearing, a bad push to master under the same version that you're using https://ukiahsmith.com/blog/a-gentle-introduction-to-golang-modules/
* _fat binary_: app has all dependencies packaged, to run successfully only needs a kernel (vs. anything in the user space)
* _pin_: get exact dependency versions https://pythonspeed.com/articles/reproducible-docker-builds-python/

problems
* failure modes: easy to impl what you need yourself, marginal improvement over built-in https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies 5:00 if deps abandoned can always fork and use your own forks [ibid 5:15]
* _compatability matrix_: which version goes with which other version https://docs.docker.com/compose/compose-file/#compose-and-docker-compatibility-matrix
* _diamond dependency_: species of transitive dependency problem https://www.youtube.com/watch?v=8ng4v1g5q7s
* bleeds over in reproduciblity crisis https://www.youtube.com/watch?v=8ng4v1g5q7s
* _dep hell_: choosing one dep leads you to choosing related dependencies based on that and increases coupling https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies 8:30
* _transitive_: dep A and B both depend on different versions of dep C
* _resolution_: figuring out subdepedencies for a dependency https://github.com/sdispater/mixology https://pyfound.blogspot.com/2020/03/new-pip-resolver-to-roll-out-this-year.html 
* _boolean satisfiability problem (SAT)_: dependency resolution, basically https://codingnest.com/modern-sat-solvers-fast-neat-underused-part-1-of-n/ NP complete https://en.wikipedia.org/wiki/Boolean_satisfiability_problem https://stackoverflow.com/a/9378268/6813490 used by Composer https://stackoverflow.com/q/37818396 https://news.ycombinator.com/item?id=14508546 https://jix.one/the-assembly-language-of-satisfiability/

## 🍺 Homebrew

📜 https://docs.brew.sh/Manpage

SEMANTICS
* _bottle_: pre-compiled i.e. you don't need to download and build, just download i.e. faster
* _key-only_: for Homebrew internal use https://chatgpt.com/c/673a0019-ccf0-8004-a613-6469c1eae461
* _services_: integrates w/ MacOS launchctl to start program on OS boot

FS
* Homebrew itself `/usr/local/Homebrew`
* installs `/usr/local/Cellar` 
* binaries `/opt/Homebrew/bin`

---

* Bundle, Brewfiles https://nickgerace.dev/posts/how-to-manage-rust-tools-and-applications/
* un/install Homebrew: requires Xcode command line tools https://github.com/homebrew/install#uninstall-homebrew
* GUI version https://news.ycombinator.com/item?id=37075730
* `pin` https://www.fernandomc.com/posts/brew-install-legacy-hugo-site-generator/
* switch to different installed version: `switch` https://github.com/thoughtbot/til/blob/master/homebrew/using_different_homebrew_formula_versions.md
> `link` does the same? https://stackoverflow.com/a/54175781
```sh
# INSTALL
install # curls URL, compares download against checksum
install -- prefix  # specific install location
uninstall -s # uninstall + rm from cache
upgrade # update; there's another cmd called `update` (akin to git fetch?)
export HOMEBREW_NO_AUTO_UPDATE=1  # toggle off auto-update
brew outdated | xargs brew upgrade  # updated all outdated

# INFO
commands  # list cmd
help $CMD  # help per cmd
doctor  # healthcheck
search  # search available pkg
leaves  # list installed (top-level) https://apple.stackexchange.com/a/279078
ls  # list installed (transitive) https://github.com/Homebrew/brew/issues/8257
info $PKG  # info on pkg
deps --tree --installed  # dependency graph https://apple.stackexchange.com/a/322371 https://github.com/martido/homebrew-graph
```

### constraints

* hard to find older pkg versions in Homebrew core https://github.com/Homebrew/homebrew-core https://www.fernandomc.com/posts/brew-install-legacy-hugo-site-generator/ https://flaviocopes.com/homebrew-install-older-version/
> brew cleanup works against this
* packages that need Rust might/will cause Rust download (to build?), if you try to install Rust later it will fail due to conflict https://chatgpt.com/c/673544c8-978c-8004-bc38-c7c4d2efdba1 https://github.com/zachvalenta/logs-mini23/commit/94d0bd7992c91018af6c1f783cb59eeec49209d4 installs deps just for building pkg https://github.com/Homebrew/brew/issues/634#issue-169347205
* deprecated repos unavailable
```sh
Warning: neofetch has been deprecated because it has an archived upstream repository! It will be disabled on 2025-05-04.
```
* `brew uses` doesn't work
```sh
$ brew uses --installed python # cairo, cmus, ffmpeg, glib, harfbuzz, libass, llvm, pango, rust, tesseract, yt-dlp
$ brew uses --installed rust # no stdout
```

---

when you catch a huge download like https://github.com/clarkema/x12pp can you interrupt install?

### registries

> vs Homebrew Core https://github.com/pythops/tenere/issues/31 https://chatgpt.com/c/671502a5-99d0-8004-a57c-98b0962fdfc9 https://github.com/nickgerace/gfold
* _formula_: Ruby class that manages install https://www.youtube.com/watch?v=fbyrLo6yx8M

TAPS
* _tap_: repo of formulae not maintained by Homebrew https://stackoverflow.com/a/37973017 🗄️ terrastruct
* examples taps https://github.com/GabAlpha/homebrew-tap https://github.com/Linus-Mussmaecher/homebrew-tap multiple https://github.com/lusingander/homebrew-tap
* howto https://chatgpt.com/c/671502a5-99d0-8004-a57c-98b0962fdfc9 https://github.com/Boeing/config-file-validator/issues/184 https://github.com/AmmarAbouZor/tui-journal/issues/457
* push release tag
* create tap repo `homebrew-$TAP_NAME`
* write formula https://github.com/GabAlpha/homebrew-tap/blob/main/Formula/basilk.rb
```ruby
class Basilk < Formula
    desc "A Terminal User Interface (TUI) to manage your tasks with minimal kanban logic"
    homepage "https://github.com/GabAlpha/basilk"
    on_macos do
      on_arm do
        url "https://github.com/GabAlpha/basilk/releases/download/0.2.0/basilk-aarch64-apple-darwin.tar.gz"
        sha256 "f073e37f93df22c1e35c576b9bbb10ce4b5e6d6364b28831e7be4cd47f8cb662"
      end
      on_intel do
        url "https://github.com/GabAlpha/basilk/releases/download/0.2.0/basilk-x86_64-apple-darwin.tar.gz"
        sha256 "1bb16be5c147e08413f6defd810602f3df6d69bba0f7a105396a9c2499a87b12"
      end
    end
    def install
      bin.install "basilk"
    end
  end
```

## managers

* _apk_: Alpine
* _apt_: used by Debian, Ubuntu, Mint
```sh
apt list -installed # list installed
-y  # yes to interactive prompts `export DEBIAN_FRONTEND=noninteractive``
apt-get -y update # update package listing so we know what packages exist
apt-get -y upgrade # grab security updates
RUN apt-get -y install <pkg> # install https://stackoverflow.com/a/50870967  sometimes have to update/upgrade or pkg won't be found
apt-get -y install --no-install-recommends <pkg> # don't install subdeps https://pythonspeed.com/articles/system-packages-docker/
apt-get clean; rm -rf /var/lib/apt/lists/* # clean up file cache https://pythonspeed.com/articles/system-packages-docker/
```
* _dpkg_: alternative to apt just installs pkg, not subdeps https://askubuntu.com/a/309121 list pkgs `dpkg-query -l`
* _lmod_: pkg + change env https://lmod.readthedocs.io/en/latest/ `module list` (what you have loaded) `module avail` (what you can load)
* _pixi_: uses conda-forge https://twitter.com/wuoulf/status/1691833538226610355 https://taras.glek.net/post/trying-pixi-modern-python-packaging/ https://github.com/prefix-dev/pixi https://talkpython.fm/episodes/show/439/pixi-a-fast-package-manager https://pythonbytes.fm/episodes/show/386/major-releases-abound
* _rpm_: pkg format and, confusingly, pkg manager for RHEL https://stackoverflow.com/a/8201051/6813490
* _Snap_: Ubuntu https://lwn.net/Articles/825005/
* _Tasksel_: Debian tool to install packages in bundled fashion e.g. LAMP stack
* _yum_: Red Hat (RHEL, Fedora)
* _Windows_: Chocolately, Nuget; uses Powershell under the hood
* _Whisky_: for running Windows apps on macOS https://github.com/Whisky-App/Whisky https://pketh.org/plantstudio.html

## 🧬 nix

---

ALTERNATIVES 🗄️ `python/pkg.md` uv `frontend.md` javascript > runtimes
* _asdf_: https://github.com/asdf-vm/asdf
* _pkgx_: from the creator of Homebrew https://www.youtube.com/watch?v=S9oHESiZyr0 https://dotenvx.com/docs/install#other https://www.youtube.com/watch?v=S9oHESiZyr0
* _mise_: 🎯 https://github.com/jdx/mise

* https://www.youtube.com/watch?v=5D3nUU1OVx8
* can script everything (install GUI apps, CLI apps, write dotfiles)
* nixpacks https://railway.app/
* _Nix_: 🎯 https://github.com/NixOS/nix
> The point of nix is just to create completely reproducible builds and package management, including support for multiple versions of packages side-by-size with no issues. It's sort of a next-generation package management system that tries to avoid most of the pitfalls that OS package managers have fumbled with up to this point. https://news.ycombinator.com/item?id=23251754
* https://www.youtube.com/watch?v=w_hqmmcufNc
* can use in place of Homebrew, provides one-off shell without having to install pkg https://www.youtube.com/watch?v=m4ST2dq10no
* isolate pkg by user/shell https://github.com/jetpack-io/devbox can do via flakes? https://www.youtube.com/watch?v=m4ST2dq10no
* use in tmp env (vs. full install) https://wickedchicken.github.io/post/macos-nix-setup/ like pipx https://pipx.pypa.io/stable/#inject-a-package
* NixOS is a whole other can of worms https://www.youtube.com/watch?v=m4ST2dq10no
* overview https://shopify.engineering/what-is-nix
* design https://news.ycombinator.com/item?id=34577844
* using w/ Docker https://pythonspeed.com/articles/reproducible-docker-builds-python/
* advanced usage https://bmcgee.ie/posts/2022/12/setting-up-my-new-laptop-nix-style/
* macOS: need nix-darwin https://wickedchicken.github.io/post/macos-nix-setup/ installs more isolated than Homebrew https://wickedchicken.github.io/post/macos-nix-setup/ https://www.reddit.com/r/Nix/comments/zdcteb/should_i_migrate_from_homebrew_to_nix/ https://news.ycombinator.com/item?id=29079096

# 🧵 PROCESSES

🗄
* `os/tools.md` monitoring
* `python/runtime.md` concurrency
* `src.md` concurrency
📙
* Arpaci ch. 13-23
* Kerrisk lpi 2.7
* Galvin dinosaur ch. 3-5

TAXONOMY https://stackoverflow.com/a/47824267 https://pthorpe92.dev/programming/systems/threads-async-runtimes-part0/
* _thread_: instance of executing program
* incl: stack, heap, text (src) data (var)
* _process_: group of threads [LPI 2.7] https://www.youtube.com/watch?v=4rLW7zg21gI
* _job_: group of processes [LPI 2.13]

ZA
* _segmentation fault_: process tries to use inaccessible memory https://corecursive.com/066-sqlite-with-richard-hipp/
* e.g. indexing array OOB, writing to memory address belonging to another process, dereferencing null pointer https://www.youtube.com/watch?v=XIhQYRNBAYs

---

visualize https://github.com/joknarf/pgtree

https://thorstenball.com/blog/2014/06/13/where-did-fork-go/
> Every process running on a Unix system started out as a call to fork(2) followed by a call to execve(2). Well, not every process, since the first process, the init process, the one that starts up the rest of the operating system, didn’t. But every process that came after. The idea is rather simple: fork(2) creates a new process and execve(2) turns the new process into the kind of process you want it to be.
> Let’s say you’re a shell and your user wants to start his productivity utility vimwonderhorse. Now, the first thing you’ve got to do is to start a new process. The reason for that is simple: when the user quits vimwonderhorse you should still be there and wait for the user’s input again. If you, as the shell, would have changed into vimwonderhorse and the user quit, well, then you would be gone, too. So you start a new process with fork(2).

types
* _privileged_: any process started by root
* _single-threaded_: program in single thread, IO in separate threads e.g. JS [`go-in-practice.pdf` 1.3.4]
* _multi-threaded_: program in n threads
* _daemon_: long-running background process; no controlling terminal [LPI 34]

segments [LPI 31]
* _text_: program source code in machine-code form; read-only so process can't modify [LPI 6.115]
* _data_: static variables (won't change so thread-safe) [LPI 6.116]
> less sure about this definition
* _stack_: 🗄 `architecture.md` memory
* _heap_: 🗄 `architecture.md` memory 📙 Evans linux [16]
* _memory allocator_: keep track of memory usage and get more when necessary from OS; malloc, calloc, et al. 📙 Evans linux [16] https://danluu.com/malloc-tutorial/

creation
* `fork()`: called by existing process (parent) to create new process (child), which is a duplicate [LPI 2.7 31]
* inheritance: child process shares read-only access to parent's program data and gets copy of parent's get data, stack, heap [LPI 2.7 32]
* `execve()`: syscall to load new program, which destroys parental segments [LPI 2.7 32] user-space wrappers incl `execv`, `execle` https://en.wikipedia.org/wiki/Exec_(system_call)#Nomenclature
* _supervisord_: restart processes if they crash

---

* each program executed by the shell starts a new process [LPI 2.13]
* _location_: $CWD of their parent process [LPI 2.5]
* _initial process_: PID 1, called `init` (or `systemd` on RHEL) [LPI 2.7]
* _inheritance_: process created when parent calls `fork()`
* child inherits UID/GID and stack, heap, data [LPI 2.7]
* `execute()`: child gets their own stack, heap, data [LPI 2.7] 
* _termination_: process calls `exit()` or killed by a signal [LPI 2.7] if parent process killed transitively kill child process https://github.com/jacek-kurlit/pik

communcation
* _signals_: restart `-HUP/-1` terminate (sent to process) `-TERM/-15` terminate/sigterm (sent to kernel) `kill -KILL/-9 <pid>`
* _intra-process communication (IPC)_: signals, writing to disk (for slow apps), file locking, pipes, message queues 📙 Kerrisk [37,877]

memory
* _hard limit_: inherited from parent
* _soft limit_: can be set by user [LPI 2.7]
* _load average_: CPU capacity to deal w/ processes; view w/ `uptime`; 1.0 is perfect capacity but anything above 0.70 should be investigated bc otherwise won't have any headroom for increases https://scoutapm.com/blog/understanding-load-averages
* _OOM killer (out-of-memory)_: https://unix.stackexchange.com/q/153585/331460 https://serverfault.com/a/571326/415712 https://lwn.net/Articles/391222/

telemetry
* _commands_: `uptime`, `top`
* _debug_: strace, application logs 
* _PID_: process ID
* how to use https://will-keleher.com/posts/What-can-you-do-with-a-pid.html
* written to file https://stackoverflow.com/a/8296204/6813490
* lookup PID using process name https://stackoverflow.com/a/11547409/6813490
* _PPID_: parent process ID

## concurrency

🗄
*️ `architecture/system.md` distributed
* `python/runtime.md` concurrency
📚
* Bobrov https://www.manning.com/books/grokking-concurrency
* Butcher models https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks

---

* [concurrency != parallelism](https://blog.golang.org/concurrency-is-not-parallelism)
* [multi-threading != parallelism](https://stackoverflow.com/a/806506/6813490) https://news.ycombinator.com/item?id=4495305
* [the guy who wrote SQLAlchemy thinks async is kinda bs](https://news.ycombinator.com/item?id=18113889) + https://techspot.zzzeek.org/2015/02/15/asynchronous-python-and-databases/

BIG PICTURE https://en.wikipedia.org/wiki/Concurrency_(computer_science)
* why: WebSockets https://channels.readthedocs.io/en/latest/
* why not: hard to reason about, just use a queue or a WebSockets server https://www.david-dahan.com/blog/10-reasons-i-stick-to-django https://danluu.com/concurrency-bugs/
* not worth it
> We’re currently using boring, synchronous, Python, which means that our server processes block while waiting for I/O, like network requests. We previously tried Eventlet, an async framework that would, in theory, let us get more efficiency out of Python, but ran into so many bugs that we decided the CPU and latency cost of waiting for events wasn’t worth the operational pain we had to take on to deal with Eventlet issues. The are other well-known async frameworks for Python, but users of those at scale often also report significant fallout from using those frameworks at scale. Using synchronous Python is expensive, in the sense that we pay for CPU that does nothing but wait during network requests, but since we’re only handling billions of requests a month (for now), the cost of this is low even when using a slow language, like Python, and paying retail public cloud prices. The cost of our engineering team completely dominates the cost of the systems we operate. https://danluu.com/simple-architectures/ 
> Rather than take on the complexity of making our monolith async we farm out long-running tasks (that we don’t want responses to block on) to a queue.

https://jacko.io/async_intro.html
https://threedots.tech/post/go-test-parallelism/

* MVCC https://www.cs.cmu.edu/~pavlo/blog/2023/04/the-part-of-postgresql-we-hate-the-most.html
* async IO https://registerspill.thorstenball.com/p/joy-and-curiosity-7
* _bricked_: cannot receive further commands https://news.ycombinator.com/item?id=36940626
* clock synchronization https://signalsandthreads.com/clock-synchronization/ https://www.exhypothesi.com/clocks-and-causality/ https://xeiaso.net/blog/nosleep
* _callback_: another func to call after func finishes execution 🗄 `application.md` webhook
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/59370383#59370383 https://danluu.com/butler-lampson-1999/
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/48530284#48530284
* imperative programming fundamentally about order, which makes concurrency hard https://softwareengineeringdaily.com/2020/05/28/distributed-systems-research-with-peter-alvaro/ 7:00
* concurrency is nearly always a bad idea https://www.arp242.net/go-easy.html
* https://news.ycombinator.com/item?id=23496994
* _sleeping barber problem_ http://kachayev.github.io/talks/kharkivpy%230/#/
* reactive in Python https://blog.oakbits.com/introduction-to-rxpy.html
* https://return.co.de/blog/articles/dont-drink-too-much-reactive-cool-aid/
* most (web) things are bound by network, not CPU https://talkpython.fm/episodes/show/225/can-subinterpreters-free-us-from-python-s-gil
* concurrency is a bad thing https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/

### golang

---

* _goroutine_: thread but... https://github.com/uber-go/goleak
scheduled by Go runtime instead of OS
* 2KB vs. 1MB for OS thread [ibid @ 1:10]
* _channels_: communication between go routines [‘Go in Action’ 1.1.2]
```golang
# _defer_: execute after surrounding code block returns
func hey() {
	defer fmt.Println("world")
	fmt.Println("hello")
}

# _mutex_: only one goroutine can 
func hi() {
    mutex.Lock() 
    defer mutex.Unlock()
    x = x + 1
}
```
* https://threedots.tech/post/go-test-parallelism/
* vs. concurrency in other languages https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/
* http://www.doxsey.net/blog/go-concurrency-from-the-ground-up https://rcoh.me/posts/why-you-can-have-a-million-go-routines-but-only-1000-java-threads/ https://utcc.utoronto.ca/~cks/space/blog/programming/GoConcurrencyStillNotEasy https://divan.dev/posts/go_concurrency_visualize/

## threads

🔍 https://softwareengineering.stackexchange.com/questions/tagged/concurrency
📚
* Arpaci ch. 26-33
* Bryant ch. 12

---

basics
* _concurrency_: design tasks that can be independently executed
* best for network-bound tasks e.g. callbacks, task queue
* aka async
* _parallelism_: execute tasks simultaneously
* best for CPU/IO-bound tasks
* aka multi-threading
* https://nullprogram.com/blog/2020/04/30/

problems 📙 Galvin chapters 5/7 Tanenbaum chapter 6
* _deadlock_: each thread thinks the other is using resource, causing each to not use resource and wait indefinitely for other thread to "stop" using resource https://martinheinz.dev/blog/101 https://medium.com/a-journey-with-go/go-how-are-deadlocks-triggered-2305504ac019
* _livelock_: hallway problem i.e. each thread constantly changing to resolve lock but making no progress
* _race condition_: sequence of events screws up correctness
* vs. data race https://stackoverflow.com/a/18049303 https://www.avanderlee.com/swift/race-condition-vs-data-race/ https://blog.regehr.org/archives/490
> knock knock / race condition / who's there? https://twitter.com/iamdevloper/status/399991896862638081
* _thread safety_: threads don't overwrite data from other threads

storage problems
* _split brain_: data inconsistencies https://en.wikipedia.org/wiki/Split-brain
* e.g. two application instances write to database and search index such that each reads their own value from index 📙 Kleppmann 491/453
* solutions is either serve inconsistencies or serve old results until system heals

single-threaded + multicast https://signalsandthreads.com/multicast-and-the-markets/

* _copy on write_: processes share memory until they need to write, at which point make copy of memory section and write to it (thereby avoiding a page fault) 🗄 `evans-linux.pdf` [3] https://brandur.org/ruby-memory https://github.com/kentonv/lanparty
* _mutex_: OS version of a lock https://jvns.ca/blog/2016/01/23/sendfile-a-new-to-me-system-call/ https://lwn.net/Articles/827180/ https://mortoray.com/2019/02/20/how-does-a-mutex-work-what-does-it-cost/
* _serial_: execution inside single thread https://pre-commit.com/#hooks-require_serial
* _history_: end of Moore's Law (clock speed increases slowing) = more cores per machine = more parallelization [Kleppmann 6]
* _actor model_: concurrency w/in single process [Kleppmann 4.138] https://news.ycombinator.com/item?id=27505267
* polling/blocking https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html https://cs61.seas.harvard.edu/site/2018/Shell3/ https://en.wikipedia.org/wiki/Polling_(computer_science)

## tracing

🗄
* processes
* `python.md` profiling
* `telemetry.md` tracing
📚
* Evans debug tools
* Evans perf
* Evans strace
* Evans tracing

VOCAB
* _monitor_: track errors; continuous
* _trace_: explore errors; ad hoc
* _profile_: measure perf (which LOC exec + exec time); ad hoc

TOOLS
* _beetrace_: 🐍 https://github.com/furkanonder/beetrace

---

flamegraph https://github.com/laixintao/flameshow

EBPF https://www.brendangregg.com/
* _flamegraph_: visualization for CPU usage https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions https://flamegraph.com/ https://github.com/laixintao/flameshow
* https://www.youtube.com/watch?v=bGAVrtb_tFs
* https://coroot.com/blog/engineering/instrumenting-python-gil-with-ebpf/
* https://github.com/ZingerLittleBee/netop
* https://sazak.io/articles/an-applied-introduction-to-ebpf-with-go-2024-06-06
* https://news.ycombinator.com/item?id=27435081
* https://www.brendangregg.com/blog/2022-04-15/netflix-farewell-1.html
* https://ebpf.io/what-is-ebpf/ https://softwareengineeringdaily.com/2023/03/06/ebpf-with-thomas-graf/
* https://www.polarsignals.com/blog/posts/2023/10/04/profiling-python-and-ruby-with-ebpf
* https://about.gitlab.com/blog/2022/11/28/how-we-diagnosed-and-resolved-redis-latency-spikes/
* https://softwareengineeringdaily.com/2022/07/15/continuous-profiling-using-ebpf-with-frederic-branczyk/
* https://github.com/keyval-dev/odigos
* https://github.com/google/gops
* https://thume.ca/2023/12/02/tracing-methods/

https://events.linuxfoundation.org/wp-content/uploads/2022/10/elena-zannoni-tracing-tutorial-LF-2021.pdf

* strace, ptrace https://nullprogram.com/blog/2018/06/23/
* magic trace https://github.com/janestreet/magic-trace
* ptrace https://medium.com/@lizrice/a-debugger-from-scratch-part-1-7f55417bc85f
* strace https://jvns.ca/blog/2021/04/03/what-problems-do-people-solve-with-strace/
* dtruss https://blog.safia.rocks/post/173241985600/unraveling-rm-what-happens-when-you-run-it

❌ normal debugging: know the language, look at src, print statements/debugger
✅ `strace` debugging: 'these are the system calls your program is making'
📝 don't run strace on production processes (or anything that needs to run at normal speed)

# 🟨 ZA

---

* Unix timestamp https://news.ycombinator.com/item?id=33341652
* sysadmins https://xkcd.com/705/
> Somewhere there’s a database programmer surrounded by empty Mountain Dew bottles whose husband thinks she’s dead. And if these people stop, the world burns. Most people don’t even know what sysadmins do, but trust me, if they all took a lunch break at the same time they wouldn’t make it to the deli before you ran out of bullets protecting your canned goods from roving bands of mutants. http://www.stilldrinking.org/programming-sucks
* trash: https://github.com/andreafrancia/trash-cli recover deleted files https://sabotage-linux.github.io/blog/6/ alternative to rm https://github.com/alanzchen/rm-protection
* _tar_: work w/ compressed files https://terminaltrove.com/ouch/
* extract `-xf`
* compress w/ gzip `.tar.gz`
* aunpack/atoo https://hacker-tools.github.io/command-line/
* _line termination_: delimiter for end of line
* NL on *nix, CRLF on Windows https://stackoverflow.com/a/12747850/6813490
* sockets 📙 Bryant (11)

logging
* `syslog`: daemon that ingests logs and routes to log files
* `/var/log`: storage location
* viewer https://lnav.org/
* `journalctl`: view systemd and kernel logs https://hacker-tools.github.io/machine-introspection/

ports 🗄 `tcp-ip.md` packet
* _hosts file_: `/etc/hosts`; map of domains to IP addresses
* _privileged_: ports < 1024 are privileged and can only be bound to processes running as root
* _port knocking_: https://news.ycombinator.com/item?id=23187662
* _netstat_: check if port open https://askubuntu.com/a/224396 https://serverfault.com/a/309058 macOS has different flags https://www.lifewire.com/using-netstat-command-on-mac-4176069

Raspberry Pi
* use for Funkwhale
* https://uglyduck.ca/my-pi-desktop/
* https://news.ycombinator.com/item?id=24965614
* https://www.canakit.com/raspberry-pi-4-8gb.html
* https://www.jeffgeerling.com/project/raspberry-pi-dramble
* https://www.jeffgeerling.com/blog/2020/i-replaced-my-macbook-pro-raspberry-pi-4-8gb-day
* desktop https://www.raspberrypi.org/products/raspberry-pi-4-desktop-kit/

daemons
* _systemd_: manage daemons https://opensource.com/article/20/4/systemd https://news.ycombinator.com/item?id=42036305
* https://github.com/torfsen/python-systemd-tutorial
* https://systemd-by-example.com/
* can conf service to start on boot, restart if crashes https://www.reddit.com/r/Ubuntu/comments/7j5qgj/gunicorn_daemon_vs_gunicornservice_on_ubuntu_1604/
* preceded by Upstart https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04 https://christine.website/talks/systemd-the-good-parts-2021-05-16 https://unixsheikh.com/articles/systemd-isnt-safe-to-run-anywhere.html
> To configure services, you pretty much have to interact with systemd these days, for better or for worse. Most services on your system will have a systemd service file that defines a systemd unit. These files define what command to run when that services is started, how to stop it, where to log things, etc. They’re usually not too bad to read, and you can find most of them in /usr/lib/systemd/system/. You can also define your own in /etc/systemd/system . Once you have a systemd service in mind, you use the systemctl command to interact with it. systemctl enable UNIT will set the service to start on boot (disable removes it again), and start, stop, and restart will do what you expect. If something goes wrong, systemd will let you know, and you can use journalctl -u UNIT to see the application’s log. You can also use systemctl status to see how all your system services are doing. If your boot feels slow, it’s probably due to a couple of slow services, and you can use systemd-analyze (try it with blame) to figure out which ones. https://hacker-tools.github.io/machine-introspection/

BOOT
* https://www.youtube.com/watch?v=XpFsMB6FoOs
* _bootloader_: loads os e.g. GRUB
* _BIOS_: first step when powering on i.e. before bootloader
* https://utcc.utoronto.ca/~cks/space/blog/linux/LinuxBootOverview?
* https://news.ycombinator.com/item?id=35229045

## date/time

🗄️ `application.md` NTP

---

`date -u`
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

## distros

📙
* Galvin dinosaur 18-20
* Kerrisk 1

* _alpine_: https://drewdevault.com/2023/07/25/Alpine-does-not-make-news.html https://drewdevault.com/2021/05/06/Praise-for-Alpine-Linux.html
* _asahi_: linux for Mac https://asahilinux.org/ https://www.youtube.com/watch?v=PHFhyqYav5M
* _arch_: 
* _CentOS_: https://taskwarrior.org/docs/workflow/
* _Fedora_: https://nickgerace.dev/posts/why-i-use-fedora/
* _mint_: https://drewdevault.com/2021/12/14/Linux-Mint-and-elementary-OS.html
* _omakub_: https://github.com/basecamp/omakub https://omakub.org/ https://www.youtube.com/watch?v=g2vcIRavtqY
* _Red Hat_: https://drewdevault.com/2023/07/25/Alpine-does-not-make-news.html
* _OpenBSD_: https://eradman.com/posts/openbsd-workstation.html https://unixsheikh.com/articles/openbsd-6.9-has-been-released-kudos-to-all-involved.html doesn't do bluetooth https://news.ycombinator.com/item?id=25949784 https://danielmiessler.com/blog/the-differences-between-bsd-and-system-v-unix/ https://dataswamp.org/~solene/2024-11-15-why-i-stopped-using-openbsd.html

---

* https://drewdevault.com/2017/05/05/Building-a-real-Linux-distro.html
* desktop https://drewdevault.com/2021/12/05/What-desktop-Linux-needs.html
* non-C operating systems e.g. SerenityOS https://news.ycombinator.com/item?id=30851955
* _DOS (disk os)_: os that came after punch cards and magnetic drums i.e. computers 1980s to mid 90s
* _Plan9_: os from Bell Labs after UNIX https://seh.dev/go-legacy/ https://drewdevault.com/2022/11/12/In-praise-of-Plan-9.html relationship to Golang https://registerspill.thorstenball.com/p/joy-and-curiosity-12
* [Rob Pike talk](https://www.youtube.com/watch?v=_2NI6t2r_Hs&t=1105s)
* The Open Group, an industry consortium (IBM Huawei DoD) controls UNIX name and compliance; no Linux distro qualifies [LPI 1, 1.3.3, 1.3.8]
* how to keep Linux distros consistent? The Linux Standard Base [LPI 1.3.8]
* _distros_: Ubuntu (default) Debian (tricky config) Red Hat (Enterprise, Fedora, CentOS and fork https://changelog.com/podcast/427) Kali (security) Arch, Mint (personal) Raspian (IoT) Alpine (lightweight) https://distrochooser.de/ https://news.ycombinator.com/item?id=23816007 https://news.ycombinator.com/item?id=16315087
* _Linux Foundation_: sponsors Linux, Cloud Foundry, Cloud Native Computing Foundation (which itself maintains Kubernetes) 
* _Unices_: enterprise (Unix, Solaris) open (BSD, Linux)
* _Nix_: https://news.ycombinator.com/item?id=31557430

history
* _1969_: Unix (Bell Labs; Ken Thompson)
* _1975_: Sixth Edition, first to be used widely outside AT&T [LPI 1.1]
* _1979_: Seventh Edition; awk, sed, tar, Bourne shell [LPI 1.1]
* _1979_: BSD (Ken Thompson); TCP/IP implementation, sockets API
* _1983_: Sun OS (based off BSD), followed up Solaris
* _1983_: System V proceeds from AT&T breakup
* _1984_: macOS; similar to FreeBSD https://wiki.freebsd.org/Myths http://www.paulgraham.com/mac.html
* _1985_: Stallman starts GNU and FSF, by early 90s has OS sans kernel
* _1993_: Novell acquires UNIX from AT&T
* _1994_: Linux 1.0 released
* _1995_: Debian; buster (current LTS) stretch, slim (previous) https://wiki.debian.org/DebianReleases#Production_Releases
* _2000_: RHEL
* _2004_: Ubuntu (Canonical is company behind it)
* _2011_: Elementary https://news.ycombinator.com/item?id=26658317

## file system

📙 Galvin dinosaur 11-13 https://news.ycombinator.com/item?id=38512248

FILE DESCRIPTORS
* _file descriptor_: reference to file created when os opens file so that your program can do stuff w/out touching underlying file directly
* akin to Vim buffer
* useful for passing between processes https://jeffknupp.com/blog/2016/03/07/python-with-context-managers/ 
* _0_: stdin
* _1_: stdout
* _2_: stderr
* _&_: both stdout and stderr https://askubuntu.com/a/350216
* also way to mark file descriptor e.g. `2>&1` = "redirect file descriptor 2(stdout) to file descriptor 1" (without `&1` the redirect would assume a file named `1`)  https://askubuntu.com/a/350216 https://stackoverflow.com/a/818284

LINKS
* _symlink_: file pointing to source file
* find all 🗄 `.bash_profile` sym
* commands pass through to source file
* deleting soft link doesn’t affect source
* file w/ the name/path to another file in it 📙 `evans-linux.pdf` 4
* syntax: `ln -sf /path/to/source /path/to/link`
* `-f`: overwrite if file already exists at location
* _hard link_: file pointing to inode
* still works if original deleted (不明觉厉) https://hacker-tools.github.io/backups/
* doesn't take up file space https://www.lifewire.com/create-symbolic-links-ln-command-4059723

FUSE https://en.wikipedia.org/wiki/Filesystem_in_Userspace
* way to mount Google Drive / Dropbox / iCloud to local filesytem
* behind this as well https://github.com/azuline/rose
* howto https://gwolf.org/2024/10/started-a-guide-to-writing-fuse-filesystems-in-python.html

ZA
* notifications e.g. inotify, kqueue https://github.com/fsnotify/fsnotify
* file name sorting, `chr()`, `LC_COLLATE` https://rhodesmill.org/brandon/slides/2021-06-colombia-remote/
* trailing slash in path https://tookmund.com/2022/04/importance-of-the-trailing-slash

---

FILES https://danluu.com/deconstruct-files/ https://danluu.com/file-consistency/ https://danluu.com/filesystem-errors/
* _file_: sequence of bytes https://netflixtechblog.com/building-netflixs-distributed-tracing-infrastructure-bb856c319304
* or a name in a hierachy, or a file descriptor https://blog.sunfishcode.online/is-everything-is-a-file/?utm_source=pocket_saves
* _file handle_: https://stackoverflow.com/a/3385261/6813490 https://danluu.com/file-consistency/
* _file path_: absolute (from root) relative (to CWD)
* _node_: ❓ file, pipe, other stuff c.f. `os.mkdnod()`
* _socket_: type of file that enables communications https://www.youtube.com/watch?v=Lbfe3-v7yE0 figure out how it works with Postgres
* _link_: how file is known by file system i.e. possible to have a file unlinked from file system and therefore cannot be opened by other programs https://pymotw.com/2/tempfile/
* rm broken https://github.com/sahib/rmlint
* _pipe_: vmsplice https://qsantos.fr/2024/08/25/linux-pipes-are-slow/

* https://www.youtube.com/watch?v=HbgzrKJvDRw
* file metadata vs. xattrs https://the.exa.website/features/xattrs

* https://news.ycombinator.com/item?id=29164727
https://www.youtube.com/watch?v=Ftg8fjY_YWU 3:40
https://www.youtube.com/watch?v=dDwXnB6XeiA
https://fasterthanli.me/series/reading-files-the-hard-way
* the kids don't even know what directories are https://www.theverge.com/22684730/students-file-folder-directory-structure-education-gen-z
* _XDG base directory specification_: put config files in `/config` https://0x46.net/thoughts/2019/02/01/dotfile-madness/
* _inode_: file ID; ‘index node’ https://wizardzines.com/comics/inodes/
* `/var`: for [variable data files](https://unix.stackexchange.com/a/264345)

LOCATIONS
* `~/.config`: config for CLIs (http-prompt, wireshark)
* `/tmp`: can be either stored on disk or using tmpfs
* `/dev/shm`: alternative to `/tmp` https://superuser.com/a/45509 https://pythonspeed.com/articles/gunicorn-in-docker/
* `/dev/null`: special file for redirecting stuff you don't care about e.g. stderr `rm FILE 2> /dev/null` https://askubuntu.com/a/12099
* _tmpfs_: looks like storage but is actually memory https://docs.gunicorn.org/en/stable/faq.html#how-do-i-avoid-gunicorn-excessively-blocking-in-os-fchmod
* _FHS_: standard for where things should be located on Linux [‘Practical Guide to Linux Commands’ pg. 12] https://apple.stackexchange.com/a/119265/328389 https://www.youtube.com/watch?v=FSxab6etkzg
* _Mac_: `/private/tmp` = 类似 Linux var/tmp, kinda https://apple.stackexchange.com/a/131080 `/usr/local` Homebrew, git, go `/Library` (SDKs) `/System/Library/Frameworks` (binaries)
* _Linux_: `var`/`tmp` temp files `/etc` (settings files, third-party installs) [Clinton 'Linux in Action' 30] `/mnt` (additional volumes) [Sweigert Automate the Boring Stuff chapter 8]
* throw away stdout: `2>/dev/null` https://askubuntu.com/q/350208
* `/dev/null`: black hole `rm local.db 2> /dev/null; sqlite3 local.db < schema.sql`
📝 [`/dev/null`](https://askubuntu.com/a/12099) special file for dumping this sort of thing

FILE SYSTEM
* _file system_: map of file name to file contents
* abstraction of persistent storage hw [Think OS chapter 4 intro]
* way to represent data from hard disk to os
* doesn’t seem like os is responsible for creation of the file system [LPI 1.2.2]
* non-POSIX https://weinholt.se/articles/non-posix-filesystems/
* IPFS https://www.youtube.com/watch?v=5Uj6uR3fp-U https://stevedylan.dev/posts/how-to-run-your-own-ipfs-gateway/ https://macwright.com/2017/08/09/decentralize-ipfs.html https://austinvernon.eth.link/blog/ipfsbasics.html https://austinvernon.eth.link/blog/ipfscodeexample.html
* BYO https://blog.carlosgaldino.com/writing-a-file-system-from-scratch-in-rust.html
* _exFAT_: MS fs for external HD https://superuser.com/q/1292689
* _mount_: 名 (files accessible to OS) 动 (make file system accessible to OS) `df` disk free on mounts https://www.youtube.com/watch?v=gZUVaPPFBJY
* _design_: Linux (single hierarchical dir structure) vs. Windows (each disk has own dir structure) [LPI 27] most operating systems support several types of file systems
* _impl_: NTFS (Windows) EXT, FAT (Linux) HFS+ (Mac) [Think OS 4.2]
* new ones: https://lwn.net/Articles/824855/
* _journal_: ledger of action
* written to before action taken
* in event of power outage can just restart from the journal
* _file metadata_: name, type, size, location, timestamps (create, access, modify)
* _virtual file system_: https://github.com/jedevc https://stackoverflow.com/questions/2910229/what-is-a-virtual-file-system-or-a-file-system-in-userspace https://github.com/rianhunter/dbxfs
* _NFS (network file system)_: access files over network as if they were on local storage; uses ONC protocol https://en.wikipedia.org/wiki/Network_File_System https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols
* _timestamps_: access (file opened) modify (contents of file edited) change (inode modified i.e. permissions) https://unix.stackexchange.com/a/132661/240456
* _file corruption_: see if things are weird `cat -v` fix w/ `dos2unix`
* _alternate data stream_: hidden data embedded in file; similar to extended attributes in EXT https://www.youtube.com/watch?v=rF4sIxDIhEk
* _Autopsy_: forensics tool for Windows * forensics https://news.ycombinator.com/item?id=26271735

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

## exit codes

---

```sh
mkdir /some/protected/directory
if [ $? -ne 0 ]; then
    echo "Command failed"
    exit 1
fi
echo "Command succeeded"
```

* _0_: success 
* _1_: err 
* _2_: "misuse of shell built-ins" (e.g. "no such file" err) https://askubuntu.com/a/892605 
* _?_: var for last cmd's exit code e.g. `echo "hi"; echo $?  #0` https://askubuntu.com/a/892607
* _127_: you use a command in your script that the shell doesn't know about
* _130_: termination via CTRL c
* _137_: script fails (128) and then received sig kill (9) from OOM killer https://stackoverflow.com/a/1041309
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

## globbing

* _glob_: pattern for matching groups of files 📙 Neil practical [6.88]
* filename completion (vs. regex i.e. search text https://www.linuxjournal.com/content/globbing-and-regex-so-similar-so-different) [LPI 25] 
* aka wildcards
* `*`: anything 
* `?`: single char 
* `[]`: range; case-sensitive `cp [a-f]*.png` `rm 02[3-7].mp3`
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

## kernel

🗄 `languages.md` 'C'

🔍 https://livegrep.com/search/linux

📦 https://git.kernel.org/

* microkernel https://drewdevault.com/2022/06/13/helios.html
* _info_: `sysctl -n hw.ncpu` (number of cores) should be file `/etc/<distro>-release` (although of course not on macOS)
* _user space_: shell, user processes
* _kernel space_: stuff kernel controls
* _components_: https://makelinux.github.io/kernel/map/
* _things kernel does_: talks to cpu, mem, disk, network e.g. keyboard interrupt to figure out which key you type, knows you have HD and how to write to it, schedules procceses https://jvns.ca/blog/2013/10/02/day-3-what-does-the-linux-kernel-even-do/
* _RTOS_: lower latency constraints for scheduler  https://stratechery.com/2023/apple-vision/
* _driver_: kernel module for managing hardware device
* BYO https://s-matyukevich.github.io/raspberry-pi-os/
* kernel message logs https://zaiste.net/posts/shell-commands-rust/#rmesg
* _sink_: https://softwareengineeringdaily.com/2019/03/14/linux-kernel-development-with-shuah-khan/
* protection rings 📙 Conery [380]

system calls
* aka syscall
* https://blog.cerebralab.com/If_I_were_to_select_the_worst_Linux_syscall
* API for kernel space e.g. create file, spawn process http://thevivekpandey.github.io/posts/2017-09-25-linux-system-calls.html
* actually pretty tricky, hence most common sys calls being wrapped by glibc
> Why does glibc do that? Why call clone(2) instead of fork(2)? And why does it wrap system calls in library functions? After digging around a bit I found out that making a system call is actually harder than just calling fork() somewhere in my code. I’d need to know the unique number of system call I was about to make, set up registers, call a special instruction (which varies on different machine architectures) to switch to kernel mode and then handle the results when I’m back in user space. By providing a wrapper around certain system calls glibc makes it a lot easier and portable for developers to use system calls. There is still the possibility to use syscall(2) to call system calls somewhat more directly. - https://thorstenball.com/blog/2014/06/13/where-did-fork-go/

## man pages

🗄️ `doc.md` repos

---

* Visidata handles this well
* run by Michael Kerrisk https://man7.org/tlpi/faq/index.html#many_errata https://www.kernel.org/doc/man-pages/
* why do they look so much worse in the terminal? https://man7.org/linux/man-pages/man1/bash.1.html 🗄 `shell.md` bat
* colorize https://danyspin97.org/blog/colorize-your-cli/
* with bat https://github.com/sharkdp/bat#man https://github.com/eth-p/bat-extras
* how to make one for your own program: https://github.com/bootandy/dust/issues/45 https://github.com/sharkdp/bat/blob/master/assets/manual/bat.1.in https://github.com/Canop/broot/blob/master/man/page `man bat -w` https://unix.stackexchange.com/a/6892/331460 http://www.tldp.org/HOWTO/Man-Page/

## scripts

🔗 http://gnu.ist.utl.pt/prep/standards/html_node/Command_002dLine-Interfaces.html

DESIGN 🗄 `protocols.md` serialization `python.md` UI

TUI
* https://news.ycombinator.com/item?id=40273177
* _curses_: UNIX https://docs.python.org/3/howto/curses.html https://github.com/cmus/cmus 
* ncurses
* https://news.ycombinator.com/item?id=37418424
* TUI for bash https://github.com/charmbracelet/gum
* design https://www.micahlerner.com/2021/07/14/unix-shell-programming-the-next-50-years.html 🗣 Dan Luu https://borretti.me/article/shells-are-two-things extensions https://github.com/dotenvx/dotenvx/pull/426

CLI IMPL LANGUAGE
> use Rust for CLI and Python for business logic? https://github.com/chubin/wttr.in
* tracking user info https://www.visidata.org/blog/2021/usage-graphs/
> build modern CLI applications without worrying about user accounts, data storage and encryption https://github.com/charmbracelet/charm#charm-kv
* fuzzy find https://github.com/denisidoro/navi
* C: ✅ fast ❌ development speed
* Nim: ✅ distribution ❌ maturity https://ssalewski.de/nimprogramming.html
* Python: ✅ exploratory ❌ distribution
* Go: ✅ distribution, fast startup https://news.ycombinator.com/item?id=23319684 ❌ stdlib lib lib not good
* Rust: ✅ speed, Clap library https://news.ycombinator.com/item?id=23320411 better for cross platform https://cuchi.me/posts/go-vs-rust ❌ language itself

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

## perms + user/group

🗄️ `containers.md`

PERMS 📙 Evans linux https://chatgpt.com/c/672cbc33-dabc-8004-bbac-7c5050f53879 🗄️ `tools.md` find
* categories: `u` (user/owner) `g` (group) `o` (other) `a` (all)
* mv: `chmod` + group + `r|w|x` e.g. `u=rw` (user gains rw) `+x` (all gain x) `o-w` (other loses w)
* get as octal: `stat -f "%A" $FILE`
* default: `666` (file) `777` (dir)
* _umask_: set perms on new files via "mask" (subtraction) from default perms; can be set as user or distro level https://www.digitalocean.com/community/tutorials/linux-permissions-basics-and-how-to-use-umask-on-a-vps

---

https://eradman.com/posts/unix-group-membership.html

PERMS
* read/write/execute have slightly different meanings when applied to directories 📙 Kerrisk lpi [2.5]
* macoS extended attributes https://serverfault.com/questions/151997/what-does-the-symbol-mean-in-a-files-permission-settings https://stackoverflow.com/questions/4833052/how-do-i-remove-the-extended-attributes-on-a-file-in-mac-os-x

USER/GROUPS 🔗 https://jvns.ca/blog/2017/11/20/groups/ https://terminaltrove.com/ugm
* logged-in users: `w`
* many programs create username and perform operations as that user
* macOS root user disabled by default but admin users can enable
* all logged in users: `who`
* switch user: `su <user>`; for root `su -`
* create user: `adduser` 
* give user sudo privilege: `visudo` (I think just opens `/etc/sudoers`)
* groups for user: `groups <user>` (or just `groups` for yourself)
* `wheel`: users who can `sudo` https://en.wikipedia.org/wiki/Wheel_(computing) 📘
* `/etc/group`: lists group name, pass, GID, users in group [LPI 26]
* _GID_: group id
* _UID_: user id; `root` is 0

## xargs

---

* _xargs_: construct list of args for cmd (bc some cmds only take args, not stdin) https://thorstenball.com/blog/2012/10/24/command-line-ride/ https://www.oilshell.org/blog/2021/08/xargs.html
> can also just input `./myscript.py < somefile.txt` (semantics for operator names) https://stackoverflow.com/a/11853307
```sh
LOGS_DIR/20 $ fd tracking | tail -n 3 | xargs bat  # open 3 most recent tracking files
ls | sort -f | head -1 | xargs open  # kaiff - open first file in directory; used to open Youtube talks downloaded as pods
fd tracking | xargs rg music  # from logs/20 -> get tracking info for music
```
