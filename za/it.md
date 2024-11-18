# ⛩️

## 参考

🗄 `km.md` file mgmt

## 进步

* swap mac mini? external storage for mac much slower than internal until thunderbolt 5 comes out https://www.youtube.com/watch?v=I3Jg9pInnag [11:30] https://www.jeffgeerling.com/blog/2024/m4-mac-minis-efficiency-incredible
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
> songs of the month: Ramones swallow my pride
* dance: francis harris, jamie xx, danilov, techno
> za (chemical brothers et al.)
* electronic: drone
* far: Aster Aweke
* jazz: christian scott, alice coltrane, bill frisell, ahmad jamal
* rock: singles, dylan, band, dinosaur jr, dr john to psych, ritter to pop, neil young 75-2002, wilco, punk (minutemen, buzzcocks, cramps, ramones)
> loud soft loud out of punk + import meat puppets
* za/blues: hendrix
* za/gospel: hank jones

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

# 🗂 FILE MGMT

MOVIES
* Handbrake https://superuser.com/a/12779/728972 https://unix.stackexchange.com/questions/224277/is-it-better-to-use-cat-dd-pv-or-another-procedure-to-copy-a-cd-dvd and `libdvdcss` (made by people behind VLC, has Homebrew install) https://www.howtogeek.com/102886/how-to-decrypt-dvds-with-hardbrake-so-you-can-rip-them/ which allows Handbrake to decrypt and then transcode (i.e. take DRM fmt and output OSS codec)

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
```

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

PYDUB
* https://github.com/jiaaro/pydub https://realpython.com/playing-and-recording-sound-python/
```python
from pydub import AudioSegment
song = AudioSegment.from_mp3("song.mp3")
first_10_seconds = song[:10000]
repeated = first_10_seconds * 2
repeated.export("mashup.mp3", format="mp3")
```

### cmus

https://github.com/hajimehoshi/oto
* install: homebrew
* alternatives: https://github.com/clangen/musikcube https://github.com/tramhao/termusic https://github.com/issadarkthing/gomu BYO https://www.reddit.com/r/rust/comments/ipjijo/how_to_make_a_tui_music_player/
> write your own https://x.com/_darrenburns/status/1803836046213357792/photo/1
* _pymus_: cmus replacement https://github.com/darrenburns/posting https://realpython.com/python-guitar-synthesizer/ https://rapidapi.com/collection/lyrics-apis https://aosabook.org/en/v1/audacity.html https://github.com/james4ever0/vignore
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

* is there a dataset for lyrics 🗄️ project idea for lyrics for Babatunde et. al.
* https://github.com/azuline/rose
* music brainz, picard, discogs https://community.metabrainz.org/
* https://tedium.co/2016/09/20/allmusic-database-historic-importance/?utm_source=substack&utm_medium=email
* seems like a pain https://bitheap.org/dnuos/ http://oidua.suxbad.com/ https://www.theverge.com/2019/5/29/18531476/music-industry-song-royalties-metadata-credit-problems http://richardmavis.info/tagging-files https://dustri.org/b/horrible-edge-cases-to-consider-when-dealing-with-music.html
* tools: http://beets.io/ + Meta ('Benjamin Jaeger' 🗄 `Applications/Meta`) https://github.com/beetbox/mediafile https://musicbrainz.org/

### youtube-dl

📜 https://github.com/yt-dlp/yt-dlp 🗄 `python-3.10-youtube-ffmpeg.md`

* conf: `${XDG_CONFIG_HOME}/yt-dlp/config` https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file#configuration
* quotes issue https://apple.stackexchange.com/questions/254014/zsh-no-matches-found
* alternative https://github.com/yt-dlp/yt-dlp https://github.com/soimort/you-get https://news.ycombinator.com/item?id=24904676
* makes Hombrew responsible for ingesting latest version https://github.com/ytdl-org/youtube-dl/issues/20553 
* if 403 run `--rm-cache-dir` https://github.com/ytdl-org/youtube-dl/issues/23638
* _alternatives_: https://github.com/Miserlou/SoundScrape https://git hub.com/Marethyu12/gotube https://github.com/topics/youtube-downloader

## media server

HOME MEDIA SERVERS
* Spotify client https://github.com/Rigellute/spotify-tui https://github.com/hrkfdn/ncspot
* BYO https://www.youtube.com/watch?v=jf_5FaVFnrU
* _Emby_: https://www.youtube.com/watch?v=lgY97D5nCek
* _Jellyfin_: https://www.youtube.com/watch?v=lgY97D5nCek
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
* https://nicolasbouliane.com/projects/home-server
* aka home server https://www.youtube.com/watch?v=yFuTAKq_j3Q
* options (Plex, cmus remote) https://www.youtube.com/results?search_query=cmus+remote&page=&utm_source=opensearch https://www.youtube.com/watch?v=UJw9YU_SBzo https://blog.dave.tf/post/building-nas-1/ https://www.youtube.com/results?search_query=build+a+nas https://www.youtube.com/results?search_query=buy+a+nas https://kevq.uk/my-home-server-2-months-on/
* https://selfhostedsource.tech/category/self-hosted/audio-streaming
> all this work just to stream music doesn't make sense, just keep rolling w/ backups and your $60 thumb drive
* https://news.ycombinator.com/item?id=30118273

## photos

---

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

# 💻 HARDWARE

🔍 models https://support.apple.com/en-us/HT201300

---

MICE
* mouse: magic mouse, keychron m3 https://www.keychron.com/products/keychron-m3-wireless-mouse https://www.nytimes.com/wirecutter/reviews/best-wireless-mouse/
* cooling pad for mbp2014 https://www.amazon.com/gp/product/B00NNMB3KS
* keep Teams active :) https://news.ycombinator.com/item?id=34273107

KVM
> could just use Thunderbolt dock https://www.nytimes.com/wirecutter/reviews/best-thunderbolt-dock/ https://wesbos.com/uses
> https://www.nytimes.com/wirecutter/blog/kvm-switch-to-declutter-desk/
* _KVM switch_: switch keyboard/video/mouse between computers https://www.pcmag.com/how-to/how-to-control-multiple-computers-with-one-keyboard-and-mouse https://www.pcmag.com/picks/best-kvm-switches
> not sure how this would work with audio
* wiring https://www.youtube.com/watch?v=S9YhQ8e9Q0o https://news.ycombinator.com/item?id=34275847
* usb-c/VGA for mbp2022 to monitor https://www.amazon.com/Thunderbolt-Compatible-MacBook-Samsung-Pixelbook/dp/B082R5W86P
* usb-3/usb-c for kvm to mbp2022
```txt
   monitor
    /   \
   |     |
box1     box2
   |     |
    \   /
     KVM
      |
  peripherals
```

USB https://en.wikipedia.org/wiki/USB
* _USB_: protocol
* spec is a mess apparently https://news.ycombinator.com/item?id=25724014 https://tidbits.com/2021/12/03/usbefuddled-untangling-the-rats-nest-of-usb-c-standards-and-cables/
* _connector_: hardware for connection e.g. USB-A, micro USB, USB-C
* USB-C https://www.sweetwater.com/insync/what-thunderbolt-3-usb-c-mean-to-musicians/
* _Thunderbolt_: https://www.pcmag.com/news/thunderbolt-3-vs-usb-c-whats-the-difference
* works w/ USB-C https://www.youtube.com/watch?v=H4Z67HfHkN4 6:00

## iPad

🔗 versions https://en.wikipedia.org/wiki/IPad#iPad
🗄️
* `audio.md` garageband
* `draw.md` digital
* `golf.md` analysis

FACTORS https://www.youtube.com/watch?v=2RqaNTPjzQ8
* size: mini is too small
* storage: at least 256GB
* mem: 8GB https://www.youtube.com/watch?v=988Jua0fMms [1:00]

---

| IPAD   | STATUS  | USED  | NEW | DISPLAY | STORAGE | PENCIL |
|--------|---------|-------|-----|---------|---------|--------|
| mini   | buy     | 120   | 500 | 8       |  64     | ?      |
| reg    | caution | 170   | 350 | 11      |  64     | ?      |
| air    | buy     | ---   | --- | 11      |  --     | ?      |
| pro    | neutral | ---   | --- | --      |  --     | ?      |

ROUGH PLAN
* buy used mini for golf ($150)
* buy used reg for procreate ($170 + pencil $80)

USE CASES
> procreate/garageband storage needs
> any special reqs for recording guitar?
* procreate https://www.creativebloq.com/buying-guides/best-ipad-for-procreate
* golf https://apps.apple.com/us/app/onform-video-analysis-app/id1490334045 https://apps.apple.com/us/app/swing-profile-golf-analyzer/id1039981052 https://apps.apple.com/us/app/v1-golf-golf-swing-analyzer/id349715369
* skate
* garageband
* travel https://github.com/rand-net/khan-dl

https://buyersguide.macrumors.com/#iPad-Air
https://www.amazon.com/dp/B09G9FPHY6 
https://www.ebay.com/itm/144379058448?itmmeta=01HYK52QFWFVWA6GQWZJ4QHAPJ
https://www.ebay.com/sch/i.html?_dkr=1&iconV2Request=true&_blrs=recall_filtering&_ssn=guaranteecellular&store_cat=0&store_name=guaranteecellular&_oac=1&_nkw=mini

PENCIL
* can just buy on amazon https://www.youtube.com/watch?v=MQnejB-SLWw [5:15]
* https://www.amazon.com/Apple-Pencil-1st-Generation-Adapter/dp/B0BJLG69QR
* https://support.apple.com/en-us/108937
* https://en.wikipedia.org/wiki/Apple_Pencil
* https://www.lifewire.com/apple-pencil-compatibility-with-ipad-5189841

* reg: $425 11" (with pencil) 64GB
* air: $725 11" 128GB; $800 13"

## machines

MINI23
```sh
zach@zachs-mac-mini.lan
OS: macOS 13.4 22F66 arm64
Host: Mac14,3
Kernel: 22.5.0
Packages: 187 (brew)
Shell: zsh 5.9
Resolution: 1920x1080
DE: Aqua
WM: Quartz Compositor
WM Theme: Blue (Dark)
Terminal: iTerm2
Terminal Font: FiraMonoNerdFontComplete-Regular 14
CPU: Apple M2
GPU: Apple M2
Memory: 1267MiB / 8192MiB
```

MBP14 🗄 `python-3.10-youtube-ffmpeg.md`
* left behind: Ableton, Human Japanese
* no room to update to Big Sur = no Homebrew support = no Brave/Chrome updates & broken exa, sqlite3, difftastic, neovim
* MacBook Pro (Retina, 13-inch, Mid 2014)
```sh
processor: 2.6 GHz Intel Core i5
Number of Processors:	1
Total Number of Cores:	2
memory: 8 GB 1600 MHz DDR3
graphics/GPU: Intel Iris 1536 MB
serial number: C02P2GD4G3QH
Hardware UUID:	8297AD35-7359-5F1C-B99F-B8C71A0B4D2B

neofetch

                    'c.          zach@zachs-mbp.lan
                 ,xNMM.          ------------------
               .OMMMMo           OS: macOS Mojave 10.14.6 18G103 x86_64
               OMMM0,            Uptime: 5 days, 9 hours, 22 mins
     .;loddo:' loolloddol;.      Resolution: 1920x1080@2x
   cKMMMMMMMMMMNWMMMMMMMMMM0:    CPU: Intel i5-4278U (4) @ 2.60GHz
 .KMMMMMMMMMMMMMMMMMMMMMMMWd.    Memory: 5001MiB / 8192MiB
 XMMMMMMMMMMMMMMMMMMMMMMMX.      CPU Usage: 11%
;MMMMMMMMMMMMMMMMMMMMMMMM:       Disk (/): 105G / 113G (95%)
:MMMMMMMMMMMMMMMMMMMMMMMM:       Local IP: 192.168.86.33
.MMMMMMMMMMMMMMMMMMMMMMMMX.      Public IP: 76.124.80.235
 kMMMMMMMMMMMMMMMMMMMMMMMMWd.    Packages: 187 (brew)
 .XMMMMMMMMMMMMMMMMMMMMMMMMMMk   Shell: bash 3.2.57
  .XMMMMMMMMMMMMMMMMMMMMMMMMK.   Terminal: iTerm2
    kMMMMMMMMMMMMMMMMMMMMMMd     Terminal Font: FiraMonoNerdFontComplete-Regular 15
     ;KMMMMMMMWXXWMMMMMMMk.
```

COMPATIBILITY https://en.wikipedia.org/wiki/MacOS_version_history#Releases
* current version: v10.14 (Mojave)
* v11 (Big Sur) works for mbp2014 https://support.apple.com/en-us/HT211238
* v12 (Monterey) doesn't work for mbp2014 https://support.apple.com/en-us/HT212551
* can run Mojave (10.14) on anything 2012 and higher https://www.techjunkie.com/macos-mojave-system-requirements/
* probably can't run 11 on 2012 Macs https://www.youtube.com/watch?v=8jM1brvJhzg 10:20
* Apple prevents downloads of older OS versions if you're on Mojave; on other versions, to have access to previous OS you need to have them previously installed and available from the App Store's 'Previously Purchased' tab or find someone who does https://www.macworld.co.uk/how-to/mac-software/download-old-os-x-3629363/#toc-3629363-1

❌ BIG SUR UPGRADE
* said it need 12gb
* had 18gb
* installed 12gb
* said it needed another 28gb
* I'm out 12gb

✅ MOJAVE UPGRADE
* 10.10 to 10.14 bc Sublime and Homebrew started to break and the answer threads looked grim
* caused when I tried to install Vim and it ended up breaking some core libs
* Sublime error -
```sh
# Sublime error https://stackoverflow.com/a/26044247/6813490
plugin_host has exited unexpectedly, plugin functionality wont be available until Sublime Text has been restarted
# Homebrew error https://github.com/Homebrew/homebrew-core/issues/5799
dyld: Library not loaded: /usr/local/opt/readline/lib/libreadline.7.dylib
Referenced from: /usr/local/bin/awk
Reason: image not found
#  Bash/Neofetch error
$ neofetch
dyld: Library not loaded: /usr/local/opt/readline/lib/libreadline.7.dylib
  Referenced from: /usr/local/bin/awk
  Reason: image not found
/usr/local/bin/neofetch: line 4160: 11158 Trace/BPT trap: 5       awk -F'<|>' '/string/ {print $3}' "/System/Library/CoreServices/SystemVersion.plist"
```

## manufacturers

https://drewdevault.com/2020/02/18/Fucking-laptops.html

CONSIDERATIONS
* ✅ Mac: familiarity, hardware
* ❌ Windows: pyenv is second-class citizen, WSL just something else to debug, unused to keybindings
* ❌ Linux: no Ableton, hardware, apps, bluetooth https://github.com/darkhz/bluetuith but if you do... https://www.youtube.com/@optimumtech/videos
> be like having American Express

🍎 APPLE
* cleaning dust https://quanticdev.com/articles/cleaning-macbook-after-16800-hours-of-use/
* https://cfenollosa.com/blog/the-m1-macbook-air-one-year-later.html
* can't upgrade battery or drives since 2015 https://www.youtube.com/watch?v=Q1u2tA9dgCQ
* used: vendors will list year of OS vs. machine production year, ignore photos (might not even be of the same machine), processor (make sure exact type is listed, that they're quoting base speed, beware if year unlisted) https://www.youtube.com/watch?v=JF1EsYfxwhM
* use 'sold items' to gauge prices https://www.youtube.com/watch?v=b-ltpMVA7BI 6:10
* 2011 unibody: avoid these https://www.youtube.com/watch?v=8jM1brvJhzg 11:45
* 2012 Pro unibody (last pre-retina, easy to add hard drive) https://www.youtube.com/watch?v=8jM1brvJhzg 
* 2015 Pro https://www.youtube.com/watch?v=8jM1brvJhzg 3:20

🐧 LINUX https://www.thinkpenguin.com/ https://news.ycombinator.com/item?id=34180508
* not ready https://cfenollosa.com/blog/fed-up-with-the-mac-i-spent-six-months-with-a-linux-laptop-the-grass-is-not-greener-on-the-other-side.html
* script install https://blog.jessfraz.com/post/windows-for-linux-nerds/
* lack of support for Ableton, might not have audio interface drivers https://news.ycombinator.com/item?id=20745072
* _Chromebook_: Linux beta https://uglyduck.ca/chromebook-web-development/
* _Dell_: https://cfenollosa.com/blog/fed-up-with-the-mac-i-spent-six-months-with-a-linux-laptop-the-grass-is-not-greener-on-the-other-side.html break all the time https://news.ycombinator.com/item?id=32632720
* _Framework_: https://frame.work/ broken https://news.ycombinator.com/item?id=33322143 https://news.ycombinator.com/item?id=28606962 https://news.ycombinator.com/item?id=27926425 better now? https://frame.work/products/laptop13-diy-intel-ultra-1 https://omakub.org/
* _System76_: more expensive than Apple https://system76.com/ https://news.ycombinator.com/item?id=34599094 https://news.ycombinator.com/item?id=34599094 https://zackproser.com/blog/why-I-buy-system-76-computers
* _Thinkpad_: https://news.ycombinator.com/item?id=30241960 x200 https://drewdevault.com/2021/05/14/Pinebook-Pro-review.html beware machines after 2012, X60 can only deal w/ 32-bit os, X200/X220/X230 are popular https://www.youtube.com/watch?v=mxA9Gyyu6Rg 9:45 12:40 13:15
* Linux laptops https://news.ycombinator.com/item?id=35355494

🪟 WINDOWS
* https://news.ycombinator.com/item?id=25534258
* https://news.ycombinator.com/item?id=22852878
* not MS cares about serving existing customers w/ whatever os it can, not Windows itself https://stratechery.com/2021/intel-problems/
* _remote control_: SSH for Windows
* `-whatif` show results if the command had actually executed!
* _grep_: `dir | find “query”` (quotes required)
* to open a file, just enter full name
* `ls -r`: `dir/s`
* `ls -a`: `Get-ChildItem –Hidden`
* _touch_: `New-Item c:\Users\F618838\Desktop\restOfPath\newFileName.txt -type file`
* copy output to clipboard: `<cmd> | clip`

## monitors

🔗 https://www.apple.com/mac-mini/specs/
🗜️ dimensions https://chatgpt.com/c/6737a255-6780-8004-8741-77accad98212

FACTORS 🗄️ machines
* aspect ratio
* scaling
* size
* refresh rate

---

COLORATION
* dark mode: set from terminal https://stefan.sofa-rockers.org/2018/10/23/macos-dark-mode-terminal-vim/
* Flux https://justgetflux.com/ https://news.ycombinator.com/item?id=30626803
* NightShift https://shifty.natethompson.io/en/

* https://registerspill.thorstenball.com/p/joy-and-curiosity-13 https://daniel.lawrence.lu/blog/y2023m12d15/
* https://news.ycombinator.com/item?id=41987359
* https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development#is-4k-worth-it-even-with-abnormal-vision
* config on macOS https://news.ycombinator.com/item?id=34487066
* 1080p vs. 4k for readability https://news.ycombinator.com/item?id=23551983 
* _OLED_: most accurate, best for viewing from non-direct angle https://www.tomsguide.com/us/what-is-oled,news-25120.html

ASPECT RATIO
* https://www.jeffgeerling.com/blog/2020/making-terminal-window-right-aspect-ratio-streaming-or-recording
* Apple retina standard, 3:2 aspect ratio https://news.ycombinator.com/item?id=40385371 https://news.ycombinator.com/item?id=40399662
* 16:9

MODELS
* _Asus pa278cgv_: https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/ https://www.nytimes.com/wirecutter/reviews/best-monitors/
* _BenQ RD320UA_: 🎯 $600 https://www.youtube.com/watch?v=784pFXYBqsg https://www.youtube.com/watch?v=rp1fEKGkG2M
* _Dell S2318HN_: ✅ $175, 23", 1080p
* _Dell S2722QC_: $225, 27", 4k https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding https://www.amazon.com/dp/B09DTDRJWP/
* _Dell U2515H_: $250 https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development#is-4k-worth-it-even-with-abnormal-vision
* _Dell U2723QE_: $600 https://www.nytimes.com/wirecutter/reviews/best-monitors/
* _Dell U3223QE_: $600, 32", 4k, KVM switch https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/
* _Spectrum black_: 🎯 $750 https://www.dough.tech/pages/monitors

## phone

🗄️ `km.md` music

GOOGLE FI
* apparently you cant have multiple numbers https://support.google.com/fi/answer/7322914?hl=en
* no customer support
> I tried to call your customer support number about this, the customer support chatbot said something about "standing by for your click"; was a text message supposed to be sent to my phone?. No message was sent and therefore couldn't even talk to a chatbot.

ANDROID
* main: keep, files by google, chrome, calls
* social: whatsapp, messages, gmail, slack, zoom, wechat, contacts, signal
> music mgmt via Android File Transfer on macOS
* music: perfect ear, liveBPM, Koala Sampler https://www.youtube.com/watch?v=Wwq5ChHiGGk musicolet, playtube, music folder player https://play.google.com/store/apps/details?id=de.zorillasoft.musicfolderplayer&hl=en_US&gl=US Youtube alternative https://github.com/TeamNewPipe/NewPipe Meta (audio metadata) 搜 'Meta on MacOS 10.10'
* transport: maps, lyft, uber, airbnb, stasher
* language: word reference, easy voice, vlc, libby, overdrive, translate, pleco
* chess/golf: drive, camera, video frame player, chess clock, chess, lichess
* util: clock, interval timer, youtube, play tube, latch, monzo, labcoat, google home, google authenticate
* files: Podcast Addict https://github.com/zhanghai/MaterialFiles

---

* retro case for iPhone https://www.printables.com/model/919133-iphone-retro-case
* https://drewdevault.com/2019/12/18/PinePhone-review.html 
* https://drewdevault.com/2017/11/24/Phone-maintenance.html
* alternatives to Google Play https://news.ycombinator.com/item?id=41770193
* iPhone 1TB storage https://news.ycombinator.com/item?id=41631130
* iPhone keyboard https://www.clicks.tech/
* dumb https://news.ycombinator.com/item?id=34415704
* Pine64, Librem, Power, RISC-V ISA https://news.ycombinator.com/item?id=26396582 https://news.ycombinator.com/item?id=30760883
* on not having a phone https://www.alvarez.io/posts/living-like-its99/
* terminal https://holzschu.github.io/a-Shell_iOS/ https://libterm.app/
* _Google Wifi_: nothing dependent on phone, only need email
* _router debug_: turn off and unplug for 5 mins (w/out unplug it doesnn't seem to ever really turn off) get password https://github.com/rauchg/wifi-password

* _requirements_: ❌ two numbers (biz, personal) ✅ overseas ❌ portability from messenger app ❌ OSS
* _Android_: https://kevq.uk/why-im-ditching-android https://www.hexaquo.at/posts/2019/06/29/Freeing+my+phone+from+Google https://eggonomy.com/blogs/news/how-fragmented-is-android normal setting for Messages is 'group MMS', safe mode https://support.google.com/pixelphone/answer/2852139?hl=en bad customer support  https://news.ycombinator.com/item?id=21815260
* _Apple_: ❓ works on Google Fi (incl overseas)?
* _OSS_: https://www.pine64.org/ https://postmarketos.org/ https://www.techrepublic.com/article/librem-5-review-the-linux-based-smartphone-is-not-close-to-consumer-ready
* _dumbphone_: https://news.ycombinator.com/item?id=19423434

apps
* chess: chess.com, lichess
* 交通: lyft, uber, meterUP, google maps
* lang: pleco, translate, audio recording, perfect ear, functional ear trainer, guitar tune
* util: labcoat, monzo, clock, interval timer
* reading: vlc, overdrive, libby, files
* 人脉: wechat, gmail, whatsapp, phone, youtube, msg, signal
* bottom row: chrome, musicolet
* music: koala, smart chord, live bpm, perfect ear, pro guitar tuner, guitar tuna, Vanced https://news.ycombinator.com/item?id=30205848 NewPipe https://newpipe.net/

__WhatsApp__ 🗓 summer 2018

🔍 艘 'restore chat history following official Change Number guide'

* _premise_: uncoupled to cell number, able to export data
* _irl_: cannot switch number and device simultaneously and preserve chat history, dearth of documentation, WhatsApp customer service will absolutely not help you in any way

[export chat history is broken](https://faq.whatsapp.com/en/android/23756533/) -> this will not necessarily export what you're seeing on your phone, but whatever backup the phone can access i.e. even if you're backup says it was made yesterday, you're account might be reading from something that doesn't include earlier *or* more recent chats. fun right?

* https://stackpointer.io/security/decrypt-whatsapp-crypt8-database-messages/419/
* https://stackpointer.io/security/decrypt-whatsapp-crypt12-database-messages/559/
* https://faq.whatsapp.com/en/android/28000018/?category=5245246
* https://faq.whatsapp.com/en/android/20887921#restore
* https://stackpointer.io/security/decrypt-whatsapp-crypt8-database-messages/419/
* https://stackpointer.io/security/decrypt-whatsapp-crypt12-database-messages/559/

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
* menu bar: iTerm, VS Code, Brave; Bitbar https://switowski.com/blog/favorite-mac-tools/
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
* alternatives https://news.ycombinator.com/item?id=34071191 https://news.ycombinator.com/item?id=34149340 https://news.ycombinator.com/item?id=34150016
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

PKGS
> when to install command line tools?
> does Git come with macOS? Homebrew?
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
* prevent computer from sleeping automatically

DOCK
* rm extas
* turn off 'show recent'
* turn on auto show/hide
* pins (terminal, editor, browser)

KEYBOARD
* key repeat repeat https://apple.stackexchange.com/questions/10467/how-to-increase-keyboard-key-repeat-rate-on-os-x
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

# 🟨️ ZA

## cameras

* series https://deannadikeman.com/leaving-and-waving
* kids https://www.youtube.com/watch?v=lTyRiO08xi8 https://www.amazon.com/Toddler-Digital-Instant-Childrens-Birthday/dp/B0CSW8719G
* fancy https://www.youtube.com/watch?v=Z--EFPp5Yds https://daniel.lawrence.lu/blog/y2024m05d31/
* iPhone: 🎯 camera https://www.youtube.com/watch?v=jjpylH_We_o video https://www.youtube.com/watch?v=M7paNi4UVDc
* early film https://www.youtube.com/watch?v=O0YcfiSR-wg
* how cameras work https://news.ycombinator.com/item?id=25357315
* multiple camera angles https://www.jeffgeerling.com/blog/2020/recording-multiple-camera-angles-full-size-simultaneously-on-mac
* DSLR camera https://www.youtube.com/watch?v=vQXmPlBskrk

## screencast

* howto https://www.youtube.com/watch?v=AzVn5H0ZNVM https://www.youtube.com/watch?v=K5GeaoJCsoI
* livestream https://til.simonwillison.net/youtube/livestreaming
* https://www.jeffgeerling.com/blog/2018/how-i-record-my-own-conference-presentations
* OBS https://obsproject.com/ https://news.ycombinator.com/item?id=22748247 https://www.youtube.com/watch?v=QCpuTSFVohQ
* ScreenFlow, Camtasia (Khan)
* screenshare tool https://www.useloom.com/ https://www.youtube.com/playlist?list=PL4cUxeGkcC9hKBg2mU8Hat4-NedlubC3C https://github.com/wulkano/kap
* https://news.ycombinator.com/item?id=41968863

GEAR https://wesbos.com/uses
* boom stand, mic https://www.youtube.com/watch?v=U1VjQ1NKpjg
* camera app https://www.youtube.com/watch?v=nqvHPYIuUBQ
* audio interface
* laptop with dedicated graphics card
* lighting https://www.youtube.com/watch?v=nqvHPYIuUBQ https://www.youtube.com/watch?v=-6VVf5DGqBU https://www.youtube.com/watch?v=jsmVL7SDp5Y https://www.youtube.com/watch?v=q-vZycP3dMI

ZA
* sync audio to video https://github.com/Rudrabha/Wav2Lip
* lighting https://www.jeffgeerling.com/blog/2020/i-replaced-my-office-lights-get-better-video
* overlay https://www.jeffgeerling.com/blog/2019/display-webcam-content-overlaid-on-your-presentation-on-mac
* effects https://www.youtube.com/watch?v=Fr4ahylCjsw https://www.youtube.com/watch?v=izukmcD8_Kw 2:15
* motion smoothing https://www.vulture.com/2019/07/motion-smoothing-is-ruining-cinema.html
