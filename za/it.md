# ⛩️

## 参考

🗄 `km.md` file mgmt

## 进步

* replace previous (huge) email export with personal only https://www.google.com/search?hl=en&q=gmail%20export%20only%20subset https://webapps.stackexchange.com/a/67379

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
| `ExFatMain`   | desk     | 24.09 | mini23     |               |
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

> 📍 clean up DS files `fd -HI DS`
* rm mckinney book
* 23 taxes
* golf
* photos: nirvana
* parking tickets

MUSIC
* francis harris
* christian scott
* jamie xx
* beatles
* everything from sui generis
* alice coltrane
* bill frisell
* Aster Aweke
* bob seger
* mark kozelek

### air-capp ➡️ mini23

* dance/dark: nicolaas jaar, roisin murphy, pantha du prince
* electronic: we-as-is
* rock/80s: war on drugs, the police
* rock/indie: camera obscura
* rock/shoegaze: cocteau twins
* rnb: al green (belle)
* punk/60s
* rm police from rock/singles

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

* _storage cleanup_: https://www.macworld.com/article/2030221/macs/our-favorite-mac-cleanup-tips.html https://macpaw.com/cleanmymac https://macpaw.com/gemini https://daisydiskapp.com/ https://macpaw.com/cleanmymac newer macOS versions have 'Reduce Clutter' tool https://github.com/docker/for-mac/issues/2297
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
* `git.md` submodules
* `linux.md` denv

```sh
# /Users/zach/Documents
├── denv
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
│   └──── bookcase   # 📦
│   └──── domains    # 📦
│   └──── sw         # 📦
│   └── 🏡 PERSONAL
│   └──── logs       # 📦
│   └──── people     # 📦
│   └──── photos
│   └──── tracking   # 📦
```

## music

---

* get song duration https://www.youtube.com/watch?v=s6DXMf_yj64

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

* install: homebrew
* alternatives: https://github.com/clangen/musikcube https://github.com/tramhao/termusic https://github.com/issadarkthing/gomu BYO https://www.reddit.com/r/rust/comments/ipjijo/how_to_make_a_tui_music_player/
> write your own https://x.com/_darrenburns/status/1803836046213357792/photo/1
* _pymus_: cmus replacement https://github.com/darrenburns/posting https://realpython.com/python-guitar-synthesizer/ https://rapidapi.com/collection/lyrics-apis https://aosabook.org/en/v1/audacity.html
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

* ❌ _headunit_: wedded to vehicle, can't rely on this being around much longer https://www.youtube.com/watch?v=AEm2WbSwRIA https://www.amazon.com/KENWOOD-KDC-BT282U-Car-Stereo-Illumination/dp/B09GWC9QYZ models https://www.youtube.com/watch?v=P7pUT0gbZZQ speakers https://www.youtube.com/watch?v=ADFOAAN9SIA
* ❌ _home media server_: not oriented around file structure, streaming vs. on-device
* ✅ Android: enough storage with microSD, good app https://fi.google.com/about/phones/moto-g-5g microSDs fail frequently https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
> needs headphone jack and expandable memory e.g. Song xperia 10 IV https://www.androidcentral.com/best-android-phones-expandable-storage https://www.androidcentral.com/best-android-phone-headphone-jack
> I might not need an SD card bc current phone only has 32GB capacity and os/fs using 30GB, SD using 185GB. Music fs down to 150GB should fit me on to 

* cd ripping https://news.ycombinator.com/item?id=33499646

Spotify client https://github.com/Rigellute/spotify-tui https://github.com/hrkfdn/ncspot
https://github.com/hajimehoshi/oto

HOME MEDIA SERVERS
* _Emby_: https://www.youtube.com/watch?v=lgY97D5nCek
* _Jellyfin_: https://www.youtube.com/watch?v=lgY97D5nCek
* _Plex_: https://plexamp.com/
* _Navidrome_: https://github.com/navidrome/navidrome too expensive to run on cloud https://www.youtube.com/watch?v=RSIvuyLDuvk 2:15
* BYO https://www.youtube.com/watch?v=jf_5FaVFnrU

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
> could just use Thunderbolt dock https://www.nytimes.com/wirecutter/reviews/best-thunderbolt-dock/
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

| IPAD   | USED | NEW | DISPLAY | STORAGE | PENCIL |
|--------|------|-----|---------|---------|--------|
| mini   | 120  | 500 | 8       |  64     | ?      |
| reg    | 170  | 350 | 11      |  64     | ?      |
| air    | ---  | --- | 11      |  --     | ?      |
| pro    | ---  | --- | --      |  --     | ?      |

---

ROUGH PLAN
* buy used mini for golf ($150)
* buy used reg for procreate ($170 + pencil $80)

TABLET
* notes: Gitlab web IDE
* music production: GarageBand, Koala
* courses from Khan Academy https://github.com/rand-net/khan-dl

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

> procreate/garageband storage needs
> any special reqs for recording guitar?

* reg: $425 11" (with pencil) 64GB
* air: $725 11" 128GB; $800 13"

USE CASES
* procreate https://www.creativebloq.com/buying-guides/best-ipad-for-procreate
* golf https://apps.apple.com/us/app/onform-video-analysis-app/id1490334045 https://apps.apple.com/us/app/swing-profile-golf-analyzer/id1039981052 https://apps.apple.com/us/app/v1-golf-golf-swing-analyzer/id349715369
* skate
* garageband

## keyboards

🗄️ `built.md` homes / studio
📙 https://shifthappens.site/#story-of-a-photo

WHAT I WANT
* layout: TKL
> although halo75 looks less scrunched than layout for air75
* connection: wired
* no lights
* don't care about programmable or rotary knob

FEATURES
* connection: usb-c is faster https://www.keychron.com/blogs/news/solid-wireless-connection-type-c-connection
* layout: TKL https://www.keychron.com/blogs/archived/keyboard-buying-guide
* lights
* rotary knob: typically used for volume, page up/down https://www.reddit.com/r/MechanicalKeyboards/comments/12nfiqg/what_are_you_using_the_knob_for/?rdt=47962
* programmable: QMK|VIA https://www.youtube.com/watch?v=nCUJK9zDXpI https://www.youtube.com/watch?v=CLiZ5rAEx3A https://www.keychron.com/blogs/news/why-qmk-via-is-one-of-the-most-essential-features-for-a-custom-keyboard https://www.youtube.com/watch?v=EWiOIVnrmMs

MODELS
* shops https://novelkeys.com/
* split https://www.youtube.com/@calmcode-io/videos
* only low-profile from keychron either don't have brown switches or do have ISO https://www.keychron.com/collections/low-profile-keyboard-collection/products/keychron-k1-max-qmk-via-wireless-custom-mechanical-keyboard
* _Apple wired_: ✅ $60 layout (100) profile (low - 2.3mm) https://www.amazon.com/dp/B07K7V1FWC
* _Keychron c1_: 🎯 https://www.keychron.com/products/keychron-c1-pro-qmk-via-wired-mechanical-keyboard?variant=40615797391449
* _Keychron k1_: out of stock https://www.reddit.com/r/NuPhy/comments/1brdzgy/will_there_ever_be_low_profile_tkl_80_layout/
* _Keychron v3_: 🎯 $110 layout (80/TKL) profile (normal) https://www.nytimes.com/wirecutter/reviews/our-favorite-mechanical-keyboards/ https://www.amazon.com/dp/B0CW5B5KL8
* _Logitech mx mini_: https://www.logitech.com/en-us/products/keyboards/mx-keys-mini.920-010475.html
* _Nuphy air75 v2_: ✅ $125 layout (75) profile (low - 2.3mm) https://nuphy.com/products/air75-v2
* slow shipping (but next time you can just buy from Amazon?)
* layout too scrunched
* _Nuphy gem 80_: $150 layout (80/TKL) profile (normal) https://nuphy.com/collections/keyboards/products/gem80
* _Varmilo mac_: https://varmilo.com/products/mac?variant=45350805405915 keycaps https://varmilo.com/products/shurikey-gear-keycaps-sets-167-keys?pr_prod_strat=jac&pr_rec_id=c6579d995&pr_rec_pid=7642777518299&pr_ref_pid=8195613425883&pr_seq=uniform

KEYCAPS 🔍 https://novelkeys.com/collections/keycaps https://www.keychron.com/collections/all-keycaps
* size
> Keycap sizes are described in terms of a "u. width. For example, 1u is the size of each of the number and alphabet keys on a keyboard. A 2u key, like Backspace, is twice the size of those 1u keys...compact keyboards often have a 1.75u right Shift key in place of the standard 2.75u right Shift key as well as 1u modifiers in the bottom row. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* _legend_: character on key; double-shot (more expensive) dye-sub (PBT only, non-transparent)
* _profile_: height * shape https://thekeeblog.com/overview-of-different-keycap-profiles/
* less options for low profile https://www.youtube.com/watch?v=BWQFUPm6XE0
* _PBT_: more durable
* _ABS_: less durable

SWITCHES 🔍 https://milktooth.com/products/switches https://switches.mx/
> One other small detail to keep an eye out for is north or south-facing switches. North-facing switches have the LED cutout facing toward the top of the keyboard - they're better at illuminating shine-through legends, but aren't compatible with common Cherry-profile keycaps. South-facing switches have the LED cutout facing toward the front of the keyboard, and they are compatible with Cherry-profile keycaps. Some keyboards have both north  and south-facing switches, so make sure to double-check before buying a new set of keycaps. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* it goes deep https://www.theremingoat.com/ https://keyboardsexpert.com/what-is-a-frankenswitch-keyboard-switch/
> If you don't already have a preference, we recommend Brown switches made by Gateron, Kailh, or Cherry because they're popular, readily available tactile switches that are good for most tasks and quiet enough for most offices...Clicky switches—like Blues and Kailh Box Whites—provide fun, typewriter-esque feedback. But they’re not ideal if you work or game in a shared space because they're very noisy...Optical switches use a laser to determine when you actuate a key. Manufacturers claim they work faster than mechanical switches, but in our experience, a light linear option like the common Red switch or the gaming-focused Cherry MX Speed Silver is plenty fast. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* tester https://drop.com/buy/kbdfans-all-in-one-72-switch-tester?defaultSelectionIds=973206#signupv2 https://kineticlabs.com/switches/kinetic/keyboard-switch-sample-packs
* for low profile https://www.howtogeek.com/339502/low-profile-switches-are-coming-to-shrink-your-mechanical-keyboards/
* creamy https://kineticlabs.com/switches/hmx/hmx-latte-switches
* Topre: https://duarteocarmo.com/blog/happy-hacking-keyboard-review https://gizmodo.com/this-is-the-perfect-keyboard-1845258727
> ALPS switches have been considered by enthusiasts to be one of the rarest type key switches. They are not as popular as mechanical switches, membrane switches, and even Topre switches. In fact, they can only be seen in vintage keyboards that were produced before the rise of membrane keyboards in the 1990s.  https://keyboardsexpert.com/what-are-alps-switches/
> Switch makers also make low-profile switches, which aren’t as tall and have less travel. You can also find other, completely different types of switches, such as Topre, buckling spring, and Alps clones. None of these switch types are compatible with the wide pool of keycaps designed for MX stems, but they all have their own unique appeal. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* _linear_: smooth
* _tactile_: bump halfway through keypress
* _clicky_: tactile + click
* _hot-swappable_: don't need to solder in new switch

ZA
* tray for desk https://www.amazon.com/VIVO-Computer-Keyboard-Platform-MOUNT-KB05E/dp/B07HFDJCSL
* touch typing https://www.keybr.com/#!game https://github.com/kraanzu/smassh

---

* can you use Windows keyboards for macOS? https://www.durgod.com/product/s230-dracula/
* mechanical https://www.youtube.com/results?search_query=mechanical+keyboard+for+macos https://www.reddit.com/r/MechanicalKeyboards/comments/89fbk4/whats_all_the_hype_about_mechanical_keyboards_im/?rdt=56069
* mechanical keyboard: cherry mx browns https://www.keychron.com/ clear is quietest, blue is clicky, brown is chunky https://news.ycombinator.com/item?id=27221191 try this one https://www.imore.com/best-mechanical-keyboards-mac customer service https://www.reddit.com/r/NuPhy/comments/ztbr5n/apologies_for_the_shipment_delay_and_adjustment/
* layers https://news.ycombinator.com/item?id=34069927
* wrist rest https://news.ycombinator.com/item?id=34276226
* Linux vs. Macos https://www.youtube.com/watch?v=GKoz7mm2tNI
* chicklet https://www.youtube.com/watch?v=8jM1brvJhzg 5:20 butterfly started with 2015 12' Macbook https://www.theverge.com/2020/5/4/21246223/macbook-keyboard-butterfly-magic-pro-apple-design https://support.apple.com/keyboard-service-program-for-mac-notebooks returned to normal scissor keyboard (aka 'magic') with 2020 16' Macbook Pro https://www.wsj.com/articles/apple-updates-ipad-macbook-air-with-new-keyboard-11584538891
* remapping https://missing.csail.mit.edu/2019/os-customization/
* stenography for transcription https://www.openstenoproject.org/plover/

## machines

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

## manufacturers

CONSIDERATIONS
* ✅ Mac: familiarity, hardware
* ❌ Windows: pyenv is second-class citizen, WSL just something else to debug, unused to keybindings
* ❌ Linux: no Ableton, hardware, apps

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
* _System76_: https://system76.com/ https://news.ycombinator.com/item?id=34599094 https://news.ycombinator.com/item?id=34599094
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

---

* https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development#is-4k-worth-it-even-with-abnormal-vision
* config on macOS https://news.ycombinator.com/item?id=34487066
* 1080p vs. 4k for readability https://news.ycombinator.com/item?id=23551983 
* _OLED_: most accurate, best for viewing from non-direct angle https://www.tomsguide.com/us/what-is-oled,news-25120.html

MODELS
* _Asus pa278cgv_: https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/ https://www.nytimes.com/wirecutter/reviews/best-monitors/
* _BenQ_: $600 https://www.youtube.com/watch?v=784pFXYBqsg
* _Dell S2318HN_: ✅ $175, 23", 1080p
* _Dell S2722QC_: $225, 27", 4k https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding
* _Dell U2515H_: $250 https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development#is-4k-worth-it-even-with-abnormal-vision
* _Dell U2723QE_: $600 https://www.nytimes.com/wirecutter/reviews/best-monitors/
* _Dell U3223QE_: $600, 32", 4k, KVM switch https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/
* _Spectrum black_: $750 https://www.dough.tech/pages/monitors

## phone

🗄️ `km.md` music

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
* `.localized`: i18n e.g. show `/Library` as `/Biblioteca` https://discussions.apple.com/thread/252040
* `scutil`: macOS tool to set hostname, etc.
* disk format: disk utility > select outermost > erase > ExFAT https://www.youtube.com/watch?v=Rq0_PQa8Irs https://www.youtube.com/watch?v=rMkGdnUwvXE
* force quit: `cmd alt esc` or use Activity Monitor (had to kill Docker once this way)
* CLI: https://github.com/rgcr/m-cli settings https://missing.csail.mit.edu/2019/os-customization/

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

FINDER
* preferences: sidebar items (desktop, documents, hard disks, external disks)
* set default window size: hold CMD when resizing window, then hold ALT and right click Finder in Dock to relaunch https://apple.stackexchange.com/a/192959 
* rm default app for opening file https://apple.stackexchange.com/questions/47512/how-to-remove-the-default-application-for-opening-a-file
* show file extensions: Finder preferences > advanced
* suppress creation of `DS_Store` seems like a pain https://stackoverflow.com/questions/18015978/how-to-stop-creating-ds-store-on-mac 
* show hidden files: `SHIFT CMD .`

BRAVE
* restore tab: `CMD T`
* reload: `CMD r`
* dev tools: `CMD ALT i`
* bookmarks: `CMD B`

---

alternate browser https://zen-browser.app/ https://www.youtube.com/watch?v=VshptkoKfQo
keypress sim https://github.com/cjerrington/wakey
system register https://github.com/TermiT/Flycut

Chrome 🗄 `js.md` browser
* set default browser: system preferences > general
* settings: zoom to 110, font fize large, downloads to desktop, switch search to DuckDuckGo, startup to open previous tabs
* extensions: Vimium, Mercury Reader, EditThisCookie, PocketTube
* Gmail: have to opt into keyboard shortcuts
* Youtube_: shortcuts `?` skip to % `<num>` list all video titles in playst `youtube-dl --get-filename https://www.youtube.com/playlist?list=PLIiejGE6XOgm_iInCjfVc2Rd0ghl5zJAV > sampling.txt`
* _archive.vn_: https://chromewebstore.google.com/detail/archive-page/gcaimhkfmliahedmeklebabdgagipbia?pli=1

Firevim https://github.com/glacambre/firenvim

VIMIUM
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

COLORATION
* dark mode: set from terminal https://stefan.sofa-rockers.org/2018/10/23/macos-dark-mode-terminal-vim/
* Flux https://justgetflux.com/ https://news.ycombinator.com/item?id=30626803
* NightShift https://shifty.natethompson.io/en/

PREVIEW
* alternative https://getpolarized.io/
* ToC: CMD ALT 3
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

## dev

PROCESSOR
* _Rosetta_: gets Intel apps to work on M1 https://news.ycombinator.com/item?id=30799686 https://news.ycombinator.com/item?id=31696447
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

COMMAND LINE TOOLS
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

## keybindings

EMOJI
* https://matthewpalmer.net/rocket/
* picker: `CTRL CMD SPACE`
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

* _memory usage_: Activity Monitor
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

## versions

---

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

# 🟨 ZA

* keystroke visualizer https://github.com/keycastr/keycastr https://switowski.com/blog/favorite-mac-tools/
* screen capture https://switowski.com/blog/favorite-mac-tools/

## PDF

---

* grep https://github.com/darrenldl/docfd
* Sioyek https://news.ycombinator.com/item?id=34069804
* https://docs.racket-lang.org/quad/
* Markdown https://docs.racket-lang.org/quad/
* https://rtpg.co/2016/09/17/make-an-ebook.html
* _design_: https://news.ycombinator.com/item?id=24108950 https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/
* _annotation_: PDF Expert, Flexcil, https://news.ycombinator.com/item?id=23230218 https://github.com/xournalpp/xournalpp
* _archival_: https://github.com/danburzo/percollate https://github.com/pirate/ArchiveBox
* _readers - macOS_: PDF Expert (freemium version won't let you save) PDF Element ($90/year) Preview (search doesn't seem to work for most documents https://duckduckgo.com/?q=macos+preview+search+doesn%27t+work&atb=v161-1&ia=web text in sidebar doesn't correspond to hightlight, some hightlights produce no text in sidebar, can't enter emoji into notes, limited keyboard shortcuts) Nitro PDF
* _to plain text_: https://github.com/axa-group/Parsr https://github.com/jsvine/pdfplumber
* _from plain text_: http://richardmavis.info/using-web-technologies-to-print-a-book https://coreyburmeister.com/continuous-integration-and-deployment-for-my-resume/
* _from HTML_: https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.princexml.com/
* _split_: select subset and drag into Finder
https://github.com/jorisschellekens/borb
https://news.ycombinator.com/item?id=26691626
* _ereader_ https://johnfactotum.github.io/foliate/
[PDF is bad]()
* PDF reader w/ Vim bindings: Zathura http://jhshi.me/2016/03/09/zathura-pdf-viewer-for-vim-lovers/index.html#.Xg4gThdKh-U not available on macOS https://www.reddit.com/r/vim/comments/3prfd0/pdf_reader_with_vim_keybindings_for_mac_osx/
* https://github.com/burtonator/polar-bookshelf https://pwmt.org/projects/zathura/ https://goodreader.com/
* mobile: [Joplin](https://github.com/laurent22/joplin), IAWriter
* https://www.pdfa.org/a-technical-and-cultural-assessment-of-the-mueller-report-pdf/

## window systems

🔗 https://en.wikipedia.org/wiki/Windowing_system

SEMANTICS
* _window system_: server that displays graphics
* protocols: x11 https://unix.stackexchange.com/q/517 Wayland, pipewire https://www.youtube.com/watch?v=jFxwPJpUwl0 https://github.com/sharkdp/pastel#get-a-list-of-all-x11--css-color-names https://en.wikipedia.org/wiki/Wayland_(display_server_protocol) https://en.wikipedia.org/wiki/X_Window_System
* _window manager_: control windows displayed by window system https://en.wikipedia.org/wiki/Window_manager https://news.ycombinator.com/item?id=34591661 https://news.ycombinator.com/item?id=36880235 https://www.youtube.com/watch?v=xWIDvnNFl5I
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
