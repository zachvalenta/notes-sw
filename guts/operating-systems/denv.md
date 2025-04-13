# ⛩️

## 参考

🗄
* `it.md` fs, provision
*️ `linux.md` files
* `src.md` denv

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
* _ninja_: https://github.com/ninja-build/ninja https://jvns.ca/blog/2020/10/26/ninja--a-simple-way-to-do-builds/ https://news.ycombinator.com/item?id=42268310 https://github.com/chagui/ninjavis
* _Nx_: monorepos https://github.com/nrwl/nx
* _Pants_: https://github.com/pantsbuild/pants https://rdrn.me/postmodern-python/
* _redo_: https://github.com/apenwarr/redo https://fzakaria.com/2020/06/08/my-love-letter-to-redo.html

TASK RUNNERS
* in editor https://zed.dev/docs/tasks
* _makedown_: Markdown https://github.com/tzador/makedown
* _mise_: 🎯 https://github.com/jdx/mise https://github.com/shuru-project/shuru
* _pypyr_: https://pypyr.io/
* _run_: https://run.jotaen.net/ https://github.com/jotaen/run.sh
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

🚧 terminal output for help text too dark on macOS https://github.com/casey/just/issues/1294

DESIGN
* no named args https://github.com/casey/just/blob/master/README.md#recipe-parameters
> although you lost readline autocomplete with Makefile named args
* can use Bash vs. Make's own language
> When my just recipes get too large, I turn them into an external file stored in a scripts folder, and I call them from a just recipe. This can be scripts/bootstrap.sh or scripts/bootstrap.py, depending on which language the recipe is written in. https://github.com/jefftriplett/scripts-to-rule-them-all
* make vs gmake = more portable? https://github.com/jefftriplett/scripts-to-rule-them-all

HOWTO
```makefile
@_default:
    just --list

# format and overwrite justfile
@fmt:
    just --fmt --unstable
```
* make it work with bat https://hynek.me/til/bat-justfile/
* aliases https://just.systems/man/en/aliases.html?highlight=alias
* fmt https://just.systems/man/en/formatting-and-dumping-justfiles.html https://github.com/jefftriplett/scripts-to-rule-them-all/blob/main/justfile
* submodules https://just.systems/man/en/modules1190.html

---

https://github.com/simonw/sqlite-utils
* _just_: 🎯 https://github.com/casey/just https://news.ycombinator.com/item?id=34317359 https://news.ycombinator.com/item?id=34073529 https://github.com/pls-rs/pls/blob/main/justfile https://github.com/pls-rs/pls/blob/main/docs/justfile https://github.com/pythops/tenere
https://luke.hsiao.dev/blog/housing-documentation/
* https://news.ycombinator.com/item?id=42351101

## make

📙 Meckleberg gnu make

* args
```Makefile
hey:
	echo "$(arg)"
```
```sh
make hey arg="there"
```
* default args
```Makefile
brand ?= Reznor
filter:
	poetry run python pipelines.py filter-on-brand $(brand)
```

---

```make
poetry run vd $(f) -b -o $(dir $(f))$(notdir $(basename $(f))).db  # https://github.com/zachvalenta/query-sandbox
```
* do Makefiles need to be executable?
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

# args
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

# 📦 PACKAGING

🗄
*️ `python/pkg.md`
* `src.md` deployment

---

attestations https://blog.pypi.org/posts/2024-11-14-pypi-now-supports-digital-attestations/
Golang https://til.simonwillison.net/go/installing-tools https://jerrynsh.com/3-easy-ways-to-add-version-flag-in-go/

💡 pkg manager = network, disk, standards, resolution https://talkpython.fm/episodes/transcript/476/unified-python-packaging-with-uv

SEMANTICS
* _app_: runs on your box
* _executable_: runs on someone else's box
* _library_: used in someone else's app/executable/library
* less e.g. jQuery
* _framework_: lib + default methods called
* more e.g. React

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

## binaries

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

## dependencies

---

https://lucumr.pocoo.org/2025/1/24/build-it-yourself/
* https://github.com/adamperkowski/nvrs
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

### semver

* _patch (~)_: only patches; `~1.3.7` = anything up to `1.4.0`
* _minor (^)_: only minors; `^1.3.7` = anything up to `2.0.0`
* _compatible release(~=)_: minor|patch ok but no major; `~= 1.4.1` = anything not `2.0`

---

https://stackoverflow.com/a/22345808
> what fmt is this? https://zed.dev/releases/stable/0.149.3
* https://mitchellh.com/writing/ghostty-is-coming
* definitions fuzzy e.g. what does "major" actually mean e.g. breaking change? for what percentage of users? https://gist.github.com/jashkenas/cbd2b088e20279ae2c8e https://snarky.ca/why-i-dont-like-semver/
* Golang brings into the realm of module/packges namespace (and therefore imports), meaning a version that is backwards incomptable must have a new namespace https://research.swtch.com/vgo-import https://news.ycombinator.com/item?id=16431299 🗄 `golang.md` 'semantic import versioning'
* contradictory interpretations? https://poetry.eustace.io/docs/basic-usage/#version-constraints https://docs.npmjs.com/about-semantic-versioning#using-semantic-versioning-to-specify-update-types-your-package-can-accept https://poetry.eustace.io/docs/versions/ https://research.swtch.com/deps

## 🍺 Homebrew

📜 https://docs.brew.sh/Manpage

SEMANTICS
* _bottle_: pre-compiled i.e. you don't need to download and build, just download i.e. faster
* _keg-only_: for Homebrew internal use https://chatgpt.com/c/673a0019-ccf0-8004-a613-6469c1eae461
* _services_: integrates w/ MacOS launchctl to start program on OS boot
* _cask_: install macOS apps (`.dmg`) e.g. Inkscape

FS
* Homebrew itself `/usr/local/Homebrew`
* installs `/usr/local/Cellar` 
* binaries `/opt/Homebrew/bin`

ALTERNATIVES https://github.com/cli/cli?tab=readme-ov-file#installation
* _macports_:
* _spack_: https://spack.io/
* _webi_: https://github.com/webinstall/webi-installers

---

* rewrite in Rust https://news.ycombinator.com/item?id=43765011
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

* if you opt out of autoupdate, Brew won't find the most recent version of packages
```sh
# A new release of gh is available: 2.57.0 → 2.64.0. To upgrade, run: brew upgrade gh.
$ brew upgrade gh
Warning: gh 2.57.0 already installed

# fix: unset this variable and then restart the shell
export HOMEBREW_NO_AUTO_UPDATE=1

```
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

* _core_: requires more legwork from maintainer https://github.com/pythops/tenere/issues/31 https://chatgpt.com/c/671502a5-99d0-8004-a57c-98b0962fdfc9 https://github.com/nickgerace/gfold https://github.com/neilotoole/sq
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

* _pacseek_: for Arch Linux https://github.com/moson-mo/pacseek
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

## 🧬 Nix

---

https://news.ycombinator.com/item?id=42666851
https://www.youtube.com/watch?v=cDZyeEtt8kY
https://github.com/mitchellh/nixos-config

GOVERNANCE 🗄️ `work.md` industry > work
* founder forced out by wokes https://www.reddit.com/r/NixOS/comments/1dqxhvk/comment/law6rek/ https://news.ycombinator.com/item?id=40199153 https://save-nix-together.org/
* founder himself a pain https://mastodon.delroth.net/@delroth/112310645064859357

ALTERNATIVES 🗄️ `python/pkg.md` uv `frontend.md` javascript > runtimes
* _asdf_: https://github.com/asdf-vm/asdf
* _pkgx_: from the creator of Homebrew https://www.youtube.com/watch?v=S9oHESiZyr0 https://dotenvx.com/docs/install#other https://www.youtube.com/watch?v=S9oHESiZyr0
* _mise_: 🎯 https://github.com/jdx/mise https://www.thoughtworks.com/radar/tools/mise

* https://github.com/sxyazi/yazi
* as an alternative to Docker https://mtlynch.io/notes/simple-go-web-service-nixos/
* https://entropicthoughts.com/using-nix-to-try-tools
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

# 🟨 ZA

## dotfiles

🗄️ `linux.md` locations

---

MGMT
* _fling_: https://github.com/bbkane/fling 
* _stow_: https://www.youtube.com/watch?v=90xMTKml9O0
* _Nix home manager_: https://nixos.wiki/wiki/Home_Manager https://www.youtube.com/watch?v=U6reJVR3FfA

* https://drewdevault.com/2019/12/30/dotfiles.html
* write script to do symlinks https://news.ycombinator.com/item?id=34304694
* prefer programs that store config as text
* keep under version control and symlink into place with script https://hacker-tools.github.io/dotfiles/ advanced mgmt https://github.com/twpayne/chezmoi https://news.ycombinator.com/item?id=32632533 https://github.com/atuinsh/atuin
> There are two basic approaches: version your entire home directory or symbolically link your dotfiles into place from a stand-alone repository. The first approach is straightforward but has a number of issues that make it a poor choice. https://nullprogram.com/blog/2012/06/23/
* install script https://www.youtube.com/watch?v=hXU54axdjJc https://alexpearce.me/2016/02/managing-dotfiles-with-stow/
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

* `set`/`setenv`
* https://github.com/zed-industries/zed/blob/main/docs/src/environment.md
* 🗄 `broot.log` https://unix.stackexchange.com/a/106606/331460 https://github.com/thoughtbot/til/blob/master/bash/bash_profile_vs_bashrc.md
* _envsubst_: sub env var into fmt strings https://nickjanetakis.com/blog/using-envsubst-to-merge-environment-variables-into-config-files
```sh
foo.sh  # echo $LOGNAME 
./foo.sh           # stdout: $LOGNAME
envsubst < foo.sh  # stdout: zach
```
* https://github.com/ankddev/envfetch

## path

TOOLS
* _has_: check tool (python, java) on PATH https://github.com/kdabir/has
* _justpath_: edit https://github.com/epogrebnyak/justpath
* _pathos_: edit https://terminaltrove.com/pathos/

---

* add dir to path https://jvns.ca/blog/2025/02/13/how-to-add-a-directory-to-your-path/
* https://wizardzines.com/comics/path-tips/ https://simonw.substack.com/p/video-scraping-using-google-gemini
* https://blog.izissise.net/posts/env-path/
* `$PATH`: list of directories that the shell should search when looking for programs corresponding to commands entered by the user [LPI 2.7]
* change precedence: https://apple.stackexchange.com/a/49961
* _default_: `/bin`, `usr/bin`
* _global_: `/etc/paths`
* _user_: `.bash_profile`

## profiles

```sh
├── $HOME
│   └── .zprofile
│   └── .zshenv
│   └── .zshrc
```

ZSH
* _zshrc_: src for interactive shells
* this isn't in `$HOME` by default i.e. I had `.zshrc` in my dotfiles that wasn't being sourced for months
* I tried to put `$LLM_USER_PATH` in `.zshrc` but wouldn't take until I put in `.zprofile`

---

📍 https://github.com/zachvalenta/dotfiles-mini23/commit/8be5846e05a964dd5f7f1de716271268331dde09

ZSH https://unix.stackexchange.com/a/71258
* _zshenv_: src for all shells
* Contains exported variables that should be available to other programs e.g. $PATH $PAGER are often set in .zshenv.
* _zprofile_: src for login shells, src before `.zshrc`

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

## XDG

📜 https://specifications.freedesktop.org/basedir-spec/latest/

ENV VAR
* `XDG_DATA_HOME`: `~/.local/share`
* libs to implement https://github.com/simonw/llm/issues/7 https://github.com/uncenter/user_dirs https://github.com/nickgerace/gfold
* macOS defaults
```python
# https://github.com/tox-dev/platformdirs
from platformdirs import *

# /Users/zach/Library/Application Support
# mini23: basilk, television (moved to XDG), harlequin, iTerm, kanban-tui, lazygit, moneyterm, broot, pipx, poetry, smassh, taskwarrior-tui, zoxide
user_config_dir()
user_data_dir()

site_data_dir()  # /Library/Application Support
user_cache_dir()  # /Users/zach/Library/Caches
user_log_dir()  # /Users/zach/Library/Logs
user_documents_dir()  # /Users/zach/Documents
user_downloads_dir()  # /Users/zach/Downloads
user_pictures_dir()  # /Users/zach/Pictures
user_videos_dir()  # /Users/zach/Movies
user_music_dir()  # /Users/zach/Music
user_desktop_dir()  # /Users/zach/Desktop
user_runtime_dir()  # /Users/zach/Library/Caches/TemporaryItems
```

---

XDG
* https://0x46.net/thoughts/2019/02/01/dotfile-madness/
* https://specifications.freedesktop.org/basedir-spec/latest/
* https://github.com/tox-dev/platformdirs
* https://github.com/Zaloog/kanban-tui
* `XDG_CONFIG_HOME`: typically `$HOME/.config` https://github.com/lusingander/serie/issues/25 https://github.com/kraanzu/dooit/issues/195
> On macOS, `$XDG_CONFIG_HOME` maps to `$HOME/.config`. Another popular path for config files is `/Users/USER/Library/Application\ Support`. Does this file path have a env var name in the way that $XDG_CONFIG_HOME does?
* you have to manually specify?
> If you want to change the config directory: macOS `export XDG_CONFIG_HOME="$HOME/.config` https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md
