# ⛩️

## 参考

🔍 https://distrosea.com/
📚
* Galvin dinosaur 18-20
* Kerrisk 1

## 进步

# 🍎 MACOS

🗄 `linux.md` denv
🔍
* https://apple.stackexchange.com/
* https://git.herrbischoff.com/awesome-macos-command-line/about/

ZA
* `caffeinate` https://weiyen.net/articles/useful-macos-cmd-line-utilities
* speech recognition https://github.com/sveinbjornt/hear `say` https://weiyen.net/articles/useful-macos-cmd-line-utilities
* `.localized`: i18n e.g. show `/Library` as `/Biblioteca` https://discussions.apple.com/thread/252040
* `scutil`: macOS tool to set hostname, etc.
* disk format: disk utility > select outermost > erase > ExFAT https://www.youtube.com/watch?v=Rq0_PQa8Irs https://www.youtube.com/watch?v=rMkGdnUwvXE
* force quit: `cmd alt esc` or use Activity Monitor (had to kill Docker once this way)
* CLI: https://github.com/rgcr/m-cli settings https://missing.csail.mit.edu/2019/os-customization/
* screen capture https://switowski.com/blog/favorite-mac-tools/

## apps

INVENTORY 🗄 `/Applications`
* full list of applications: `about this mac > system report > sw > applications` --> 32-bit apps may not be compatible with macOS 10.14
* menu bar: iTerm, VS Code, Brave; Bitbar https://switowski.com/blog/favorite-mac-tools/ https://github.com/FelixKratz/SketchyBar https://www.youtube.com/watch?v=8W06wMNZmo8
* dev: iTerm, VS Code, GitUp
* audio: cmus, Sound Source
> have to enable keyboard volume through the app itself
> new install instructions https://rogueamoeba.com/support/knowledgebase/?showArticle=ACE-StepByStep&product=SoundSource
* video: VLC, Handbrake, Quicktime
* macOS: Preview, Pages, Photos
* music: Ableton, Spitfire Audio
* util: Android File Transfer, Airdroid https://www.youtube.com/watch?v=D6gE-W9oUz0 AppCleaner, DriveDX, Disk Drill, Monodraw, Flux, Battery Health 2 https://www.youtube.com/watch?v=UGOJmN3Lc2U 4:30
* za: Human Japanese

🔍 FINDER
* preferences: sidebar items (desktop, documents, hard disks, external disks)
* set default window size: hold CMD when resizing window, then hold ALT and right click Finder in Dock to relaunch https://apple.stackexchange.com/a/192959 
* rm default app for opening file https://apple.stackexchange.com/questions/47512/how-to-remove-the-default-application-for-opening-a-file
* show file extensions: Finder preferences > advanced
* suppress creation of `DS_Store` seems like a pain https://stackoverflow.com/questions/18015978/how-to-stop-creating-ds-store-on-mac 
* show hidden files: `SHIFT CMD .`

GOOGLE DRIVE FOR DESKTOP
* search: `CMD ALT g` (global hotkey)

---

keypress sim https://github.com/cjerrington/wakey
system register https://github.com/TermiT/Flycut

* Gmail: have to opt into keyboard shortcuts
* Youtube_: shortcuts `?` skip to % `<num>` list all video titles in playst `youtube-dl --get-filename https://www.youtube.com/playlist?list=PLIiejGE6XOgm_iInCjfVc2Rd0ghl5zJAV > sampling.txt`

Firevim https://github.com/glacambre/firenvim

VIMIUM
> sites where Vimium search doesn't work: Github, Stedi
* alternatives https://news.ycombinator.com/item?id=34071191 https://news.ycombinator.com/item?id=34149340 https://news.ycombinator.com/item?id=34150016 https://news.ycombinator.com/item?id=42396336
* help: `?`
* omnibar: `o`
* tab - search: `T`
* tab - scroll: `J/K`
* nav history: `H/L`
* reload: `r`
* goto input: `gi`
* page - scroll: `j/k`
* page - page: `u/d`
* page - goto: `g/G`
* page - search: `/`
* restore tab: `X`

SPOTLIGHT
> Raycast also an app launcher https://omakub.org/
* access: `CMD SPACE`
* folders to search: apps, calculator, definition, documents, folder, music, pdf documents, system preferences
* NLP = can no longer turn off web search https://forums.macrumors.com/threads/spotlight-how-to-remove-web-search-from-results.2271616/
* alternatives https://news.ycombinator.com/item?id=22849208 Alfred https://switowski.com/blog/favorite-mac-tools/

PREVIEW
* alternative https://getpolarized.io/
* ToC: CMD ALT 3
* hightlight: CTRL CMD h
* higlights: CMD ALT 4
* full screen: CMD SHIFT f
* _views_: cmd <num>
* _goto page_: cmd alt g
* _toggle search_: tab
* _magnify_: ~
* merge: open first PDF, go to last page, `edit > insert > page from file`, use next PDF https://support.apple.com/en-us/HT202945)
* can't close single file when have multiple open https://discussions.apple.com/thread/8135180
* https://news.ycombinator.com/item?id=26681337

VLC 📜 https://wiki.videolan.org/Mac_OS_X/ https://www.maketecheasier.com/mastering-vlc-via-the-command-line-linux/
* _alternatives_: https://iina.io/ https://mpv.io/
* _config_: ❓ is VLC using i.e why isn't long jump 300 seconds (vs 60 seconds) `~/Library/Preferences/org.videolan.vlc/vlcrc` https://superuser.com/a/599305/728972
* _versions_: 3.0.11 (rewind would then play forward but no output audio; macOS version at time 10.14.6) removed and downloaded 3.0.8 and fixed
* help: `--help`
* version: `--version`
* file: `vlc <file>`
* _play/pause_: `SPACE`
* _full screen_: cmd f
* _playback speed up/down_: `CMD =/-`
* _playlist_: cmd alt p
* _jump_: to time (cmd j, then h:m:s) very short () short () mid () long (cmd shift arrow) https://askubuntu.com/a/618391

## bindings

basics (as you were learning keychron v8)
* switch app: `CMD TAB`
* iterm hotkey: `ALT SPACE`
* start/end of line: `CMD ARROW`
* start/end of word: `ALT ARROW`
* select start/end of word: `SHIFT ALT ARROW`

EMOJI
* picker: `CTRL CMD SPACE`
* alternate picker https://matthewpalmer.net/rocket/ https://wesbos.com/uses
* disable suggestions: `sudo defaults write /Library/Preferences/FeatureFlags/Domain/UIKit.plist emoji_enhancements -dict-add Enabled -bool NO` https://www.reddit.com/r/MacOS/comments/16wzdk9/is_there_a_way_to_turn_off_the_new_emoji

SYSTEM
* screenshot - whole: CMD SHIFT 3
* screenshot - portion: CMD SHIFT 4
* window - hide: CMD h

SYMBOLS
* keyboard viewer https://setapp.com/how-to/type-math-symbols-on-mac
* _copyright_: `alt g`
* _trademark_: `alt 2`
* _delta (∆)_: alt j
* _degree(°)_: alt shift 8
* _infinity_: alt 5
* _accent_: alt e
* _enye_: alt n
* _sigma_: alt w

---

* _movie_: CMD SHIFT 5
* _Spanish question mark_: SHIFT ALT ?
* _Spanish exclamation mark_: ALT 1
* [map of macOS key symbols to names](https://www.danrodney.com/mac/)
* _page up/down_ | FN arrows
* _home/end_ | CMD arrows
* _open file_: CMD down arrow
* [function keys](https://support.apple.com/en-us/HT207240): F1 F2 et al.
* [track down large files for cleanup](https://www.youtube.com/watch?v=agtsRgCeAVg)
* _adjust system font size_: system pref - displays - scaled - slider
* _set maximize app_: keyboard - app shortcuts - title shortcut to 'Zoom'

__SQLite extension and `DYLD_LIBRARY_PATH`__

https://forum.djangoproject.com/t/jsonfield-for-sqlite-on-macos-cannot-set-dyld-library-path/3878 https://code.djangoproject.com/ticket/31882#ticket 🗄 `brew/sqlite-dyld.log`

Trying to use `JSONField` with SQLite on macOS [Mojave 10.14]. 
I followed the instructions [here](https://code.djangoproject.com/wiki/JSON1Extension) for how to enable SQLite's `JSON1` extension but was unable to set `DYLD_LIBRARY_PATH` as an environmental variable.
```sh
# attempt to export
$ export DYLD_FALLBACK_LIBRARY_PATH=path/to/dir
# no stdout
$ env | rg DYLD
```
Based on Stack Overflow, inability to set this env var is the result of a [macOS security policy](https://stackoverflow.com/search?q=DYLD_LIBRARY_PATH+macos).
Should the [docs for JSONField using SQLite](https://code.djangoproject.com/wiki/JSON1Extension) be updated? Is there a commonly used workaround to this problem in the Django community?

## command line tools

* _XCode_: IDE for macOS dev
* _Command Line Tools_: compilers from XCode
* _OSX-GCC installer_: don't install this alongside Command Line Tools https://docs.python-guide.org/starting/install3/osx/
```sh
# install https://apple.stackexchange.com/a/324598
xcode-select --install

# switch
sudo xcode-select --switch /Library/Developer/CommandLineTools

# switch back
sudo xcode-select --reset

# view SDK
xcrun --show-sdk-path

# get fs
xcode-select -p  # /Library/Developer/CommandLineTools

# reintsall
sudo rm -rf $(xcode-select -print-path) # Enter root password. No output is normal.
sudo rm -rf /Library/Developer/CommandLineTools # Enter root password.
sudo xcode-select --reset
xcode-select --install

# update
Warning: A newer Command Line Tools release is available.
Update them from Software Update in System Preferences or run:
  softwareupdate --all --install --force
```

## provision

🗄️ `linux.md` denv
🔗 https://www.roguelynn.com/words/m1-dev-setup/
> make a runbook for this https://news.ycombinator.com/item?id=43791941

PKGS
* questions: Git (bundled with macOS?), install coreutils separately, alternative to installing command line tools from Apple?
* set `XDG_CONFIG_HOME`
* pyenv/pipx, bun, rust
* neovim
* Homebrew last 🗄️ `linux.md` Homebrew > constraints

## rosetta

* _Rosetta_: gets Intel apps to work on M1 https://news.ycombinator.com/item?id=30799686 https://news.ycombinator.com/item?id=31696447
> Rosetta 2 is an “emulator” or a translator for software built for Intel-based processors to run on Apple’s Silicon/M1 processors. While many apps for macOS have transitioned to running on M1 machines, there are still a lot of non-user-facing (a.k.a developer-facing) software and tools that do not play nicely. For instance, for Python, there are many packages with C-extensions whose binaries are not yet built for the M1, causing a lot of headaches (I’m looking at you, grpcio, tensorflow, librosa). Then there’s Docker, which will run fine on Apple Silicon, but can cause frustration when trying to build & deploy to a non-M1 environment. Enter: Rosetta 2. https://www.roguelynn.com/words/m1-dev-setup/
> You may find it a lot easier to have two copies of iTerm.app (or Terminal.app), one that runs with Rosetta, and one that does not. Having both makes it easy to visually separate which environment you’re working in, as you can now customize the look and theme of each terminal app.
* installed on mini23 for Android File Transfer
* iTerm/Terminal > get info > open using Rosetta
```sh
# print architecture
arch
uname -p

# print hardware
uname -m

arch  # i386 w/ Rosetta
arch  # arm64 w/out Rosetta
```

## settings

* CLI https://saurabhs.org/advanced-macos-commands
* in Ventura https://arstechnica.com/gadgets/2022/10/macos-13-ventura-the-ars-technica-review/6/
* desktop: right click to enlarge icons, font
* `operation not permitted` / access: security > privacy > full disk access https://gitlab.com/gnachman/iterm2/-/wikis/fulldiskaccess https://apple.stackexchange.com/a/341723
* turn off stacks https://www.tekrevue.com/tip/desktop-files-missing-mojave-stacks/

BATTERY
* used to be known as 'energy saver'
* turn display off after 30 mins
* prevent computer from sleeping automatically https://github.com/stigoleg/keep-alive

DOCK
* rm extas
* turn off 'show recent'
* turn on auto show/hide
* pins (terminal, editor, browser)

KEYBOARD
* key repeat https://apple.stackexchange.com/questions/10467/how-to-increase-keyboard-key-repeat-rate-on-os-x
* rampping to CMD key in Vim https://github.com/bugb/dotfiles/blob/main/.config/nvim/core/options.lua https://stackoverflow.com/questions/40990454/how-to-map-mac-command-key-in-vim https://github.com/neovim/neovim/issues/22748 http://vimcasts.org/episodes/neovim-terminal-mappings/
* remap escape to caps locks: keyboard > modifier keys https://news.ycombinator.com/item?id=24287951 https://vim.fandom.com/wiki/Avoid_the_escape_key
* remap escape to `jk`
```conf
# https://www.youtube.com/watch?v=9FECnDJShMk
:inoremap kj <Esc> 
:cnoremap kj <Esc>
# https://sanctum.geek.nz/arabesque/vim-anti-patterns/
inoremap jj <Esc>
```
> need to do for each keyboard i.e. built-in, external
* show desktop: keyboard > shortcuts > mission control 
* Chinese: input sources > simplified/pinyin, shortcuts > input sources > select next source in input menu
* enable keyboard repeat/hold: `defaults write -g ApplePressAndHoldEnabled -bool false` (restart apps after setting) https://kingluddite.com/st2/using-vintage-mode-in-sublime-text-the-skinny disabled for 18n https://laceysnr.com/fixing-broken-key-repeat-with-sublime/ https://stackoverflow.com/a/44010683/6813490
```sh
$ defaults write ApplePressAndHoldEnabled -bool f
$ defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```

---

* silence beep: iTerm (profiles > terminal > notifications > silence bell) http://codingshower.com/how-to-disable-mac-os-annoying-beep-alert-bell-sound-in-terminal-and-iterm2/ global https://apple.stackexchange.com/questions/384025/why-is-my-macbook-pro-beeping-when-performing-a-keyboard-shortcut VS Code https://stackoverflow.com/a/62581536

# 🟨 ZA

## alternatives

* _alpine_: https://drewdevault.com/2023/07/25/Alpine-does-not-make-news.html https://drewdevault.com/2021/05/06/Praise-for-Alpine-Linux.html
* _asahi_: linux for Mac https://asahilinux.org/ https://www.youtube.com/watch?v=PHFhyqYav5M
* _arch_: manjaro https://www.youtube.com/watch?v=Dg2Lek-xN70
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

## history

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
