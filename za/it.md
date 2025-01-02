# ⛩️

## 参考

🗄 `km.md` file mgmt

## 进步

* neofetch for air22
* trade-in mac mini? external storage for mac much slower than internal until thunderbolt 5 comes out https://www.youtube.com/watch?v=I3Jg9pInnag [11:30] https://www.jeffgeerling.com/blog/2024/m4-mac-minis-efficiency-incredible
* get the best albums in FLAC
* backups https://wesbos.com/uses HDD https://www.amazon.com/dp/B07VTWX8MN/
* replace previous (huge) email export with personal only https://www.google.com/search?hl=en&q=gmail%20export%20only%20subset https://webapps.stackexchange.com/a/67379
* macOS storage (just use external storage?) https://news.ycombinator.com/item?id=41986777

* _24_: port media/admin from Dropbox to mini23 and backup mini23
* _23_: mbp14 battery starts dying, buy mini23, port to mini23
* _22_: port from `linux.md`, buy air22
* _21_: macOS (failed upgrade to Big Sur) music (version control library)
* _19_: backups (Dropbox as placeholder until Tarsnap) macOS (upgrade to Mojave) 📙 `evans-random.pdf`
* _18_: phone (switch to new number, 'unknown number' problem, WhatsApp debacle)
* _17_: music (youtube-dl, `fne`)
* _16_: music (cmus)

# 🖲️ BACKUP

🗄 `eng.md` admin / backup

|  ITEM         | LOCATION | DATE  | CONTENTS   | TO            |
|---------------|----------|-------|------------|---------------|
| digits        | mini23   | 19.07 | pw         | safe, lockbox |
| calendar      | google   | 24.02 |            | mini23        |
| email         | google   | 22.02 |            | mini23        |
| mini23        | -        |       | fs         |               |
| air22         | -        | ----- | mini23     |               |
| `ExFatMain`   | desk     | 24.11 | mini23     |               |
| `WD1`         | safe     | 24.06 | mini23     |               |
| `WD2`         | lockbox  | 20.02 | mini23     |               |
| `music-usb`   | desk     | ----- | `yin`      |               |
| `music-usb-2` | desk     | 24.02 | `yin`      |               |

SEMANTICS
* _transfer_: mv data from A to B
* _sync_: scheduled transfer https://kevq.uk/building-my-home-server
* _backup_: adhoc transfer
* _dump_: "create a script that would allow me to recreate this database"
* _load_: "use script to create database"

---

https://github.com/paperless-ngx/paperless-ngx
https://yourdigitalrights.org/ https://news.ycombinator.com/item?id=34358622

potential new config
> same price as Dropbox but with incremental for local files
* $7.50 - Tarsnap for `zvmac` https://www.tiltedwindmillpress.com/product/tarsnap-mastery-online-backups-for-the-truly-paranoid/ https://www.kalzumeus.com/2014/04/03/fantasy-tarsnap/
* $3.00 - Google Drive for music
* $0.00 - personal drives

🎗 now that you're copying music files btw work machine and music-usb
* backup music-usb to exfat-main
> 22.02.10
* backup exfat-main non music files to new hard drive
* backup exfat-main music files to other drives and Dropbox
* now you can transfer work machine music files back
* this way if your work machine corrupts the files somehow you have physical and cloud backups of everything before that

recently updated
> 🎗 use music-lib for easier backups!
> do mac journal
* digits
* moved to ExFatMain: comedy, training

physical storage
* keys: office desk
* safe: HD, passport, personal
* lockbox: HD, personal

---

* drives https://news.ycombinator.com/item?id=42033931
* don't backup project deps e.g. `.node_modules` https://bsago.me/posts/lessons-learned-when-my-ssd-died
* regularize email export https://news.ycombinator.com/item?id=29978099
* https://hacker-tools.github.io/backups/
* https://unixsheikh.com/articles/how-i-store-my-files-and-why-you-should-not-rely-on-fancy-tools-for-backup.html
* export addresses from Amazon
* preventing file corruption https://duckduckgo.com/?q=how+do+hard+drives+get+corrupted&atb=v161-1&ia=web
* defrag?

BACKBLAZE https://wesbos.com/uses
📙 Shotts command line ch. 18
* ❓ versioned backups to prevent data corruption? https://hacker-tools.github.io/backups/
* 📍 extra consideration to code (dupe to Gitlab), digits, email https://hacker-tools.github.io/backups/ https://kevq.uk/i-nearly-lost-all-of-my-data/ 
* weird files on backup drives http://blog.hostilefork.com/trashes-fseventsd-and-spotlight-v100/

TIME MACHINE
* backup https://support.apple.com/en-us/HT201250
* restore https://support.apple.com/en-us/HT203981
* slow?
> There are only a few issues I can think of with Time Machine: first, it can slow things down on older, less powerful Macs. Five to ten years ago, it was common for my consulting clients to refuse to use Time Machine because they were tired of watching it slow down their machines. The other issue? Time Machine backups aren’t bootable — in other words, you can’t just select the backup drive during bootup and use it to bring a machine with a dead primary drive back to life. You can, however, boot from the Mac recovery partition and attempt to restore your machine with the backup. - https://blog.macsales.com/29785-backup-month-a-look-at-time-machine-carbon-copy-cloner-superduper
* deletion: should be automatically purged as they age and as the drive space dips; can do manually https://www.macworld.com/article/3260635/macs/how-to-delete-time-machine-snapshots-on-your-mac.html https://www.youtube.com/watch?v=GYXOuP6_PSQ
* list: `tmutil listlocalsnapshotdates` https://forums.macrumors.com/threads/how-to-delete-time-machine-local-backups-on-high-sierra.2073998/
* filepath: on my machine stored in `Volums/.com.apple.TimeMachine.localsnapshots` https://robservatory.com/disable-local-time-machine-backups-on-laptops/
* can always disable TM backups from System Preferences, which will start clearing out local backups

### mini23 ➡️ exfatmain

MUSIC
> just do everything
* slint nosferatu
* 17 moments of springs
* boris
* dru hill, alice coltrane sings
> songs of the month: Ramones swallow my pride, The Clean i wait around
* dance: francis harris, jamie xx, danilov, techno, Herbert this time
> za (chemical brothers et al.)
* electronic: drone
* far: Aster Aweke
* jazz: christian scott, alice coltrane, bill frisell, ahmad jamal
> loud soft loud out of punk + import meat puppets
* rock: singles, dylan, band, dinosaur jr, dr john to psych, ritter to pop, neil young 75-2002, wilco, fairport convention, punk (minutemen, buzzcocks, cramps, ramones, johnny thunders, elvis costello, sonic youth, death grips), Dehd desire, fugazi
> 🎗️ Capp 24.11.21-22: pere ubu, public image ltd + kendrick rich
* rock/80s-jangle: rm the soft boys, The Clean, Pale Saints
* za/blues: hendrix
* za/gospel: hank jones
* bruno mars

* mat/sw: system, ai, vincent django, hogan tmux
* Evans git, int/bit, containers, dns, bite size networking
> 📍 clean up DS files `fd -HI DS`
* 23 taxes
* golf
* photos: nirvana
* parking tickets

MAT
* sw: rm mckinney book, wayne logic for programmers, network, kent data and reality, evans containers and ints/floats, Bueno mature optimization
* math
* za
* science

### air-capp ➡️ mini23

* Alex Danilov

## reimage

SEMANTICS
* _image_: OS
* _bootable disk_: disk from which OS can boot https://pc.net/helpcenter/answers/startup_disk_vs_bootable_disk `install macOS Mojave` 🎗 in large safe 🗄 versions
* _startup disk_: disk from which OS actually does boot https://pc.net/helpcenter/answers/startup_disk_vs_bootable_disk
* _SD card_: non-volatile memory i.e. really fast storage
* _flash_: write OS image (to SD card) https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=24621 https://uglyduck.ca/linux-mint-macbook-air/

factory reset
* aka "Erase all contents and Settings"
> iOS where instead of going through this process it will just wipe everything and put a clean copy of macOS just like a fresh install just without the hassle of booting from drive etc. https://www.youtube.com/watch?v=rgHyvj_nWCU
* hardware: M1, T2 from 2017
* available from System Preferences
* _system partition_: os https://www.youtube.com/watch?v=O882iWxtZyo 2:50
* _data partition_: user files, settings
* after reset leave at Activate Mac screen otherwise will save your wifi to settings https://www.youtube.com/watch?v=O882iWxtZyo 3:15
* after Activate Mac, just reset to Setup Assistant

create image https://www.youtube.com/watch?v=rgHyvj_nWCU
* download OS version in App Store
* quit out of install
* format drive using Disk Utility to "Mac OS Extended Journaled"

test reimage
* create image
* add couple of apps/files
* reimage
* verify only apps/files from basic set up

---

* _storage cleanup_: https://www.macworld.com/article/2030221/macs/our-favorite-mac-cleanup-tips.html https://macpaw.com/cleanmymac https://macpaw.com/gemini https://daisydiskapp.com/ https://macpaw.com/cleanmymac macOS 'Reduce Clutter'
* file security https://hacker-tools.github.io/security/

prereqs
* [machine compatibility](https://support.apple.com/en-us/HT201475) 
* [space for install](https://blog.macsales.com/45780-get-ready-for-macos-mojave) 
* [run First Aid on startup drive](https://blog.macsales.com/45780-get-ready-for-macos-mojave)
* can't remove standard apps https://apple.stackexchange.com/a/65175/328389

bootable disk https://aaronchall.github.io/#sec-6-2 https://support.apple.com/en-us/HT201372
* disk should be at 16GB
* download OS but don't proceed with install
* grab OS from `Applications`
* https://www.youtube.com/watch?v=Y0NKkOOI9Ew

install from bootable disk
* adjust Energy Saver, plug in power source, `media/video/za` to phone, write down instructions
* insert bootable disk, power on holding `ALT`, folllow video
* troubleshoot https://support.apple.com/en-us/HT201475 + [potential issues](https://blog.macsales.com/45723-mac-installation-errors-you-may-encounter-and-how-to-fix-them)
* load user files

## sync

🗄️ `git.md` lazygit

CURRENT WORKFLOW
```yaml
# NOTES: SW, DOM
- /Users/zach/Documents/zv/notes/domains
- /Users/zach/Documents/zv/notes/sw

# CAPP: TM, HB, WLR
- /Users/zach/Documents/zv/capp/handbook
- /Users/zach/Documents/zv/capp/task-mgmt
- /Users/zach/Documents/zv/capp/worklogs

# ZA: BASILK, UR, MYB
- /Users/zach/Library/Application Support/basilk
- /Users/zach/Documents/zv/materials/sw/lang/html-css/myblog
- /Users/zach/Documents/zv/materials/sw/svc/ur-repo
```
* problem: slow workflow (git) + too many repos to sync (sw, dom, site, worklogs, task-mgmt, handbook)
* solution: lazygit multiple reops -> manually add all repos to lazygit `state.yaml` and then your sync workflow can be done with no cd-ing around + through lazygit's status pane you have a catalog of all the repos you need to sync

---

* is hard https://sirupsen.com/napkin/problem-14-using-checksums-to-verify
* https://news.ycombinator.com/item?id=26902422 https://github.com/rclone/rclone
* https://github.com/sahib/brig
* rclone https://news.ycombinator.com/item?id=22082585 http://www.cis.upenn.edu/~bcpierce/unison/ https://news.ycombinator.com/item?id=22791036
* Perkeep/Camlistore https://news.ycombinator.com/item?id=23676350
* Own Cloud, Amazon Glacier, BackBlaze, Arq https://github.com/kahun/awesome-sysadmin#backups https://github.com/rclone/rclone
* https://github.com/kimono-koans/httm
* _syncthing_: https://tonsky.me/blog/syncthing/
* _BackupPC_: https://backuppc.github.io/backuppc/
* _Dropbox_: https://superuser.com/q/351169/728972
* _Restic_: local https://github.com/restic/restic 
* _Borg_: https://www.borgbackup.org/ https://news.ycombinator.com/item?id=13694079 https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* _Backblaze_: Terraform provider https://news.ycombinator.com/item?id=26426489
* _rsync_: https://goteleport.com/blog/scp-familiar-simple-insecure-slow/ https://missing.csail.mit.edu/2019/remote-machines/ impl https://news.ycombinator.com/item?id=31958536 `rsync -rv --exclude=.git <dir> <path/to>` https://stackoverflow.com/a/3672584/6813490 https://michael.stapelberg.ch/posts/2022-07-02-rsync-how-does-it-work/
* progress bar https://github.com/laktak/rsyncy
```sh
# sync local to remote
rsync --rsync-path 'sudo -u app rsync' -arvR --exclude '.*' --exclude '*~' .  ${DEST_HOST}:/opt/t3  # start
fswatch --recursive --one-per-batch . | xargs -L1 -II rsync --rsync-path 'sudo -u app rsync' -arvR --exclude '.*' --exclude '*~' .  ${DEST_HOST}:/opt/t3 # on file change
```

# 🗂 HOMELAB

🗄️ `infra.md` self host

---

SKETCH
* ethernet
* DNS
* storage
* compute

* https://github.com/khuedoan/homelab
* containers, Plex https://www.youtube.com/watch?v=yFuTAKq_j3Q
* rack https://www.youtube.com/watch?v=akJ97oqmQlU
* https://nielscautaerts.xyz/we-have-cloud-at-home.html

## fs

🗄
* notebook [83,86]
* `doc.md` notes, task mgmt
* `git.md` submodules

CURRENT
> next time, denv inside zv
```sh
# /Users/zach/Documents
├── denv
│   └── bin
│   └──── news  # symlink
│   └─────── repos/news/main.py  # symlink src
│   └──── sysinfo
│   └──── vimv
│   └── dotfiles
│   └── fonts
│   └──── fira code
│   └──── fira mono
│   └── logs
├── telescope-workspace
├── zv
│   └── 🗄️ ADMIN
│   └──── healthcare
│   └──── real estate
│   └──── taxes
│   └── 💽 AV
│   └──── film
│   └──── lit
│   └──── yin
│   └── 🔍 MATERIALS
│   └──── art
│   └──── music
│   └──── sw
│   └──── za
│   └── 📝 NOTES
│   └──── bookcase   # 📦 bookcase-sjk.git
│   └──── domains    # 📦 notes-domains.git
│   └──── sw         # 📦 notes-sw.git
│   └── 🏡 PERSONAL
│   └──── logs       # 📦 logs.git
│   └──── people     # 📦 people.git
│   └──── photos
│   └──── tracking   # 📦 tracking.git
│   └── 🧪 PROJECTS  # used to have this in my notes `rg ZVPROJ $ZV_DIR/personal/people; rg ZVPROJ $ZV_DIR/notes`
│   └──── algos
│   └──── dataclerk
│   └──── jay-valenta
```

## media server

HOME MEDIA SERVERS
* Spotify client https://github.com/Rigellute/spotify-tui https://github.com/hrkfdn/ncspot
* BYO https://www.youtube.com/watch?v=jf_5FaVFnrU
* _Black Candy_: https://github.com/blackcandy-org/blackcandy
* _Emby_: https://www.youtube.com/watch?v=lgY97D5nCek
* _gonic_: https://news.ycombinator.com/item?id=42513171
* _Jellyfin_: https://www.youtube.com/watch?v=lgY97D5nCek client https://github.com/streamyfin/streamyfin
* _Komga_: PDFs https://komga.org/
* _Plex_: https://plexamp.com/
* mobile client https://github.com/jmshrv/finamp https://www.fintunes.app/
* _Navidrome_: https://github.com/navidrome/navidrome too expensive to run on cloud https://www.youtube.com/watch?v=RSIvuyLDuvk 2:15

---

https://drewdevault.com/2013/08/24/Music-syncing-on-Android.html

AUTOS
* ❌ _headunit_: wedded to vehicle, can't rely on this being around much longer https://www.youtube.com/watch?v=AEm2WbSwRIA https://www.amazon.com/KENWOOD-KDC-BT282U-Car-Stereo-Illumination/dp/B09GWC9QYZ models https://www.youtube.com/watch?v=P7pUT0gbZZQ speakers https://www.youtube.com/watch?v=ADFOAAN9SIA
* ❌ _home media server_: not oriented around file structure, streaming vs. on-device
* ✅ Android: enough storage with microSD, good app https://fi.google.com/about/phones/moto-g-5g microSDs fail frequently https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
> needs headphone jack and expandable memory e.g. Song xperia 10 IV https://www.androidcentral.com/best-android-phones-expandable-storage https://www.androidcentral.com/best-android-phone-headphone-jack
> I might not need an SD card bc current phone only has 32GB capacity and os/fs using 30GB, SD using 185GB. Music fs down to 150GB should fit me on to 

* cd ripping https://news.ycombinator.com/item?id=33499646

* fselect provides useful functionailty for music files 🗄 `shell.md` finder

SELF-HOSTED STREAMING
* _NAS (network attached storage)_: aka 'home media server' 🗄 `network-know-how.pdf`
* raspberry pi version https://www.youtube.com/watch?v=l30sADfDiM8
* https://www.youtube.com/watch?v=EYEPIDceoB0 [7:55]
* https://nicolasbouliane.com/projects/home-server
* aka home server https://www.youtube.com/watch?v=yFuTAKq_j3Q
* options (Plex, cmus remote) https://www.youtube.com/results?search_query=cmus+remote&page=&utm_source=opensearch https://www.youtube.com/watch?v=UJw9YU_SBzo https://blog.dave.tf/post/building-nas-1/ https://www.youtube.com/results?search_query=build+a+nas https://www.youtube.com/results?search_query=buy+a+nas https://kevq.uk/my-home-server-2-months-on/
* https://selfhostedsource.tech/category/self-hosted/audio-streaming
> all this work just to stream music doesn't make sense, just keep rolling w/ backups and your $60 thumb drive
* https://news.ycombinator.com/item?id=30118273

## movies

* Handbrake https://superuser.com/a/12779/728972 https://unix.stackexchange.com/questions/224277/is-it-better-to-use-cat-dd-pv-or-another-procedure-to-copy-a-cd-dvd and `libdvdcss` (made by people behind VLC, has Homebrew install) https://www.howtogeek.com/102886/how-to-decrypt-dvds-with-hardbrake-so-you-can-rip-them/ which allows Handbrake to decrypt and then transcode (i.e. take DRM fmt and output OSS codec)

## music

---

* get song duration https://www.youtube.com/watch?v=s6DXMf_yj64
* file fmt conversion https://news.ycombinator.com/item?id=42064988

TRACKING
* poc: `mlib` `os.walk()` https://unix.stackexchange.com/questions/90115/convert-output-of-tree-command-to-json-format/ regex to strip and kebab https://github.com/30-seconds/30-seconds-of-python#kebab https://www.robertchristgau.com/get_gl.php?g=A%2B store library song info as db
```sh
alias mlib="cd /Volumes/MUSIC-LIB && t > ~/Desktop/music-lib-$(date +"%Y%m%d").log"
```
```sh
fd 194[0-9] | wc -l
fd 194[0-9]
fd -t d 194[0-9]
```

### 🇯🇲 pydub

* https://github.com/jiaaro/pydub https://realpython.com/playing-and-recording-sound-python/
```python
from pydub import AudioSegment
song = AudioSegment.from_mp3("song.mp3")
first_10_seconds = song[:10000]
repeated = first_10_seconds * 2
repeated.export("mashup.mp3", format="mp3")
```
* CLI failed due to ffmpeg issues
```markdown
Can you write me a script called medit (music edit) using this lib (https://github.com/jiaaro/pydub) for a CLI to edit audio files?
Let's use Click for the CLI.
Here's the desired functionality:
* takes audio file
* creates a copy with the same file format as the original
* the copy version should be named by concat original name + `- medit` + file extension. For example, if the original is called `disco track.mp3`, the copy would be called `disco track - medit.mp3`.
* the copy will be edited by removing seconds of audio from either the start or end of the file or both
Here's example usage:
```sh
# copy version removes first 5 seconds of the song
medit --start 5 $AUDIO_FILE

# copy version removes first 7 seconds of the song
medit --end 7 $AUDIO_FILE

# copy version removes first 42 seconds and last 3 seconds of the song
medit --start 42 --end 3 $AUDIO_FILE

# either --start or --end must be used as parameter, so throw a warning if an audio file is passed without one
medit $AUDIO_FILE
```
```

### 🪲 cmus

* 2.12: progress bar (percentage counter doesn't work though) library view (played song highlights yellow)

---

* playlists 🗄️ `/Users/zach/Documents/zv/materials/music/za/music-library/lib.txt`
```sh
# not yet sure how to refresh; updating and reloading library and then re-running cmd doesn't do it
cat ~/.config/cmus/playlists/default > lib.txt
```

https://github.com/hajimehoshi/oto
* install: homebrew
* alternatives: https://github.com/clangen/musikcube https://github.com/tramhao/termusic https://github.com/issadarkthing/gomu BYO https://www.reddit.com/r/rust/comments/ipjijo/how_to_make_a_tui_music_player/
* file nav: opens to most recent dir, can cd to music dir and then if you need to return scroll command history
* playlists https://unix.stackexchange.com/q/593727 /Users/zach/Documents/zv/materials/music/za/music-library/playlists
```sh
:pl-create $NAME  # create
SPACE  # select playlist
y  # add song
D  # rm song
:pl-export /path/to/file.txt  # export
```
* _continue_: play next song after current finishes; `f` (browser view)

---

CMUS
* _command mode_: `:`
* mv dir: `:cd <path>`
> be nice if you could use fzf or env var ($MUSIC_DIR)
* listen to an album shuffled: add to playlist `y` toggle shuffle `s`
* listen to an artist shuffled: only works in first view?
queue
* mv down: `p`
* mv down: `P`
* prepend: `E`
* append: `e`
* rm: `D`
* rm all: `P`
* to shuffle through everything from artist, cfrs
> this doesn't work but one time when everything from artists was shuffling these were the settings
* Funkwhale https://news.ycombinator.com/item?id=25067701 https://news.ycombinator.com/item?id=25148623 https://news.ycombinator.com/item?id=25860094 Ampache https://www.youtube.com/watch?v=0dBcKNoJAso
* I wish there was history file
* _config_: `~/.config/cmus`
* _docs_: https://github.com/cmus/cmus/blob/master/Doc/cmus-tutorial.txt bad and won't get better because project not maintained https://github.com/cmus/cmus/issues/856
> There are more commands and features not covered here like loading and saving playlists, controlling cmus remotely with `cmus-remote`, etc.
* _features_: playlist from plain text
* _mark_: for bulk operations; `space`
nav
* _up/down_: Vim
* _top/bottom_: Vim
* _enter/leave_: `RETURN / DELETE`
* _search_: Vim
play
* _play/pause_: `c`
* _restart_: `x`
* _skip - back/forward_: `z/b`
* _skip - seconds - back/forward_: `:seek +/-<num>` 
* _repeat current_: `ctrl r`
* _continue_: `C`
* _shuffle_: `s`
* _play from_: `m`
* _toggle play from library or playlist_: `M`
views
* _library - clear_: `:clear`
* _playlist - add_: `y`
* _update_: `u`
config
* _add music_: `a` in browser view on dir to add https://github.com/cmus/cmus/issues/233#issuecomment-399426415
* _display - time remaining in song_: settings - 'show_remaining_time'
* _display - hidden files_: `i`

### metadata

TOOLS
* https://github.com/borewit/music-metadata
* _beets_: http://beets.io/ https://github.com/guerda/beets-statistics
* _rosé_: https://github.com/azuline/rose 🗄️ `linux.md` virtual file system

SOURCES
* _Discogs_: https://www.discogs.com/
* _Musicbrainz_: https://musicbrainz.org/

---

* lyrics 🗄️ project idea for lyrics for Babatunde et. al.
* music brainz, picard, discogs https://community.metabrainz.org/
* https://tedium.co/2016/09/20/allmusic-database-historic-importance/?utm_source=substack&utm_medium=email
* seems like a pain https://bitheap.org/dnuos/ http://oidua.suxbad.com/ https://www.theverge.com/2019/5/29/18531476/music-industry-song-royalties-metadata-credit-problems http://richardmavis.info/tagging-files https://dustri.org/b/horrible-edge-cases-to-consider-when-dealing-with-music.html
* tools: Meta ('Benjamin Jaeger' 🗄 `Applications/Meta`) https://github.com/beetbox/mediafile

### 🐍 pymus

---

* https://github.com/darrenburns/posting
* https://realpython.com/python-guitar-synthesizer/
* https://rapidapi.com/collection/lyrics-apis
* https://aosabook.org/en/v1/audacity.html
* https://github.com/james4ever0/vignore

### 🛰️ youtube-dl

📜 https://github.com/yt-dlp/yt-dlp 🗄 `python-3.10-youtube-ffmpeg.md`

* conf: `${XDG_CONFIG_HOME}/yt-dlp/config` https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file#configuration
* quotes issue https://apple.stackexchange.com/questions/254014/zsh-no-matches-found
* alternative https://github.com/yt-dlp/yt-dlp https://github.com/soimort/you-get https://news.ycombinator.com/item?id=24904676
* makes Hombrew responsible for ingesting latest version https://github.com/ytdl-org/youtube-dl/issues/20553 
* if 403 run `--rm-cache-dir` https://github.com/ytdl-org/youtube-dl/issues/23638
* _alternatives_: https://github.com/Miserlou/SoundScrape https://git hub.com/Marethyu12/gotube https://github.com/topics/youtube-downloader

## photos

---

* https://github.com/sedthh/pyxelate 
* https://immich.app/
* metadata https://stefaniemolin.com/articles/devx/pre-commit/exif-stripper/
* viewer https://github.com/karlch/vimiv-qt
* https://news.ycombinator.com/item?id=37670756
* https://www.jefftk.com/pictures/
* https://news.ycombinator.com/item?id=34716924 https://www.photoprism.app/
* https://github.com/immich-app/immich
* get metadata https://will-keleher.com/about.html https://jimpl.com/
* http://johnkerl.org/misc/jks.html
* https://news.ycombinator.com/item?id=33046281&utm_term=comment
* need mgmt for tagging
* checkout macOS storage mgmt, archived versions of iPhotos library: `Library.migratedphotolibrary/` `Library.photoslibrary/`
* pillow https://realpython.com/image-processing-with-the-python-pillow-library/
* photos: personal, site design
* https://news.ycombinator.com/item?id=26000113
* site: https://github.com/maxvoltar/photo-stream https://github.com/saimn/sigal
* mgmt: https://github.com/electerious/Lychee https://github.com/hooram/ownphotos https://github.com/photoprism/photoprism
