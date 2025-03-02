# ⛩️

## 参考

📜 https://man7.org/linux/man-pages/index.html
🔍
* https://serverfault.com/
* https://unix.stackexchange.com/
📚
* Evans linux
* Evans za
* Kerrisk lpi https://nostarch.com/linux-memory-manager
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

# 🗃️ FILES

📙 Galvin dinosaur 11-13 https://news.ycombinator.com/item?id=38512248

FILES https://danluu.com/deconstruct-files/ https://danluu.com/file-consistency/ https://danluu.com/filesystem-errors/
* _file_: sequence of bytes https://netflixtechblog.com/building-netflixs-distributed-tracing-infrastructure-bb856c319304
* or a name in a hierachy, or a file descriptor https://blog.sunfishcode.online/is-everything-is-a-file/?utm_source=pocket_saves
* _file handle_: https://stackoverflow.com/a/3385261/6813490 https://danluu.com/file-consistency/
* _file path_: absolute (from root) relative (to CWD)
* _inode_: file ID; ‘index node’ https://wizardzines.com/comics/inodes/
* _node_: ❓ file, pipe, other stuff c.f. `os.mkdnod()`
* _socket_: type of file that enables communications https://www.youtube.com/watch?v=Lbfe3-v7yE0 figure out how it works with Postgres
* _link_: how file is known by file system i.e. possible to have a file unlinked from file system and therefore cannot be opened by other programs https://pymotw.com/2/tempfile/
* rm broken https://github.com/sahib/rmlint
* they buffer https://news.ycombinator.com/item?id=42275033

ZA
* alternative file systems https://news.ycombinator.com/item?id=43283498
* notifications e.g. inotify, kqueue https://github.com/fsnotify/fsnotify
* file name sorting, `chr()`, `LC_COLLATE` https://rhodesmill.org/brandon/slides/2021-06-colombia-remote/
* trailing slash in path https://tookmund.com/2022/04/importance-of-the-trailing-slash

---

* https://www.youtube.com/watch?v=HbgzrKJvDRw
* file metadata vs. xattrs https://the.exa.website/features/xattrs
* https://news.ycombinator.com/item?id=29164727
https://www.youtube.com/watch?v=Ftg8fjY_YWU 3:40
https://www.youtube.com/watch?v=dDwXnB6XeiA
https://fasterthanli.me/series/reading-files-the-hard-way
* the kids don't even know what directories are https://www.theverge.com/22684730/students-file-folder-directory-structure-education-gen-z

## descriptors

* _file descriptor_: reference to file created when os opens file so that your program can do stuff w/out touching underlying file directly
* akin to Vim buffer
* useful for passing between processes https://jeffknupp.com/blog/2016/03/07/python-with-context-managers/ 
* _0_: stdin
* _1_: stdout
* _2_: stderr
* _&_: both stdout and stderr https://askubuntu.com/a/350216
* also way to mark file descriptor e.g. `2>&1` = "redirect file descriptor 2(stdout) to file descriptor 1" (without `&1` the redirect would assume a file named `1`)  https://askubuntu.com/a/350216 https://stackoverflow.com/a/818284

## fs

🗄️ `telemetry.md` logging

```sh
├── /
│   └── etc  # config
│   └──── resolv.conf  # DNS
```

---

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
* _virtual file system_: https://github.com/jedevc https://stackoverflow.com/questions/2910229/what-is-a-virtual-file-system-or-a-file-system-in-userspace https://github.com/rianhunter/dbxfs  https://github.com/azuline/rose
* _NFS (network file system)_: access files over network as if they were on local storage; uses ONC protocol https://en.wikipedia.org/wiki/Network_File_System https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols
* _timestamps_: access (file opened) modify (contents of file edited) change (inode modified i.e. permissions) https://unix.stackexchange.com/a/132661/240456
* _file corruption_: see if things are weird `cat -v` fix w/ `dos2unix`
* _alternate data stream_: hidden data embedded in file; similar to extended attributes in EXT https://www.youtube.com/watch?v=rF4sIxDIhEk
* _Autopsy_: forensics tool for Windows * forensics https://news.ycombinator.com/item?id=26271735

FUSE https://en.wikipedia.org/wiki/Filesystem_in_Userspace
* way to mount Google Drive / Dropbox / iCloud to local filesytem
* behind this as well https://github.com/azuline/rose
* howto https://gwolf.org/2024/10/started-a-guide-to-writing-fuse-filesystems-in-python.html

## globbing

* _glob_: pattern for matching groups of files 📙 Neil practical [6.88]
* filename completion (vs. regex i.e. search text https://www.linuxjournal.com/content/globbing-and-regex-so-similar-so-different) [LPI 25] 
* aka wildcards
* `*`: anything 
* `?`: single char 
* `[]`: range; case-sensitive `cp [a-f]*.png` `rm 02[3-7].mp3`

## links

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

* `/var`: for [variable data files](https://unix.stackexchange.com/a/264345)
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

## sockets

https://blog.sinjakli.co.uk/2025/01/01/ruby-3-4-highlights/

* re: `kcm`
```txt
Unix domain sockets are like pipes but for processes to communicate on the same machine. They show up as files in the filesystem.
When a process crashes instead of cleaning up properly, it can leave its socket file behind. Other processes then see this "stale" file and think the service is still running, refusing to start.
Common pattern:

Process A creates socket file
Process A crashes
Socket file remains
Process B sees socket, assumes A is running
Process B exits
```

# 🌊 FLOW

SUBSTITUTION
* _command substition_: capture the output of a command in a single variable
```sh
control_status=$(curl -o /dev/null -s -w "%{http_code}" "$control_url")
```
* _process substition_: use command stdout as if it were a file via tmp file/stream
```sh
$ paste <(tail -n +2 aaon.csv) <(tail -n +2 baldor.csv)
```

## IO

* grab stdout when you only get it after program closes https://github.com/alexpasmantier/television/issues/16#issuecomment-2558615942
```sh
alias ds='bash -c "tv | while read -r line; do code -g \"\$line\"; done"'
```
* _stdout_: `1`
* _stderr_: `2`
* _stdout + stderr_: `&`

---

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

## operators

REDIRECT
* _redirect_: connect cmd and file
* _output redirect_: `>`
* _append redirect_: `>>`
* _input redirect_: `<` e.g. ``
```sh
# $CMD $WHERE_TO_OUTPUT + "use schema.sql as input"
sqlite3 local.db < schema.sql
```

---

PIPES
* _pipe_: connects cmds
* _pipe_: vmsplice https://qsantos.fr/2024/08/25/linux-pipes-are-slow/
🐍 in Python https://github.com/bugen/pypipe
* _pipe (|)_: directs stdout to stdin
```sh
# stdout           | takes stdin
echo "training 20" | termgraph
```

LOGICAL OPERATORS
&& AND (run second command only if first succeeds)
|| OR (run second command only if first fails)
! NOT

SEQUENCE OPERATORS
; sequential execution (run commands in sequence regardless of success)
& background execution (run command in background)

GROUPING OPERATORS
( ) subshell grouping
{ } command grouping

## xargs

---

* _xargs_: construct list of args for cmd (bc some cmds only take args, not stdin) https://thorstenball.com/blog/2012/10/24/command-line-ride/ https://www.oilshell.org/blog/2021/08/xargs.html
> can also just input `./myscript.py < somefile.txt` (semantics for operator names) https://stackoverflow.com/a/11853307
```sh
LOGS_DIR/20 $ fd tracking | tail -n 3 | xargs bat  # open 3 most recent tracking files
ls | sort -f | head -1 | xargs open  # kaiff - open first file in directory; used to open Youtube talks downloaded as pods
fd tracking | xargs rg music  # from logs/20 -> get tracking info for music
```
```sh
echo "in.txt" | grep "txt"  # in.txt
echo "in.txt" |  xargs cat  # foo bar baz
```

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
* https://news.ycombinator.com/item?id=42200099
* https://uglyduck.ca/my-pi-desktop/
* https://news.ycombinator.com/item?id=24965614
* https://www.canakit.com/raspberry-pi-4-8gb.html
* https://www.jeffgeerling.com/project/raspberry-pi-dramble
* https://www.jeffgeerling.com/blog/2020/i-replaced-my-macbook-pro-raspberry-pi-4-8gb-day
* desktop https://www.raspberrypi.org/products/raspberry-pi-4-desktop-kit/

daemons
* _systemd_: spec for service start https://opensource.com/article/20/4/systemd https://news.ycombinator.com/item?id=42036305 https://unixdigest.com/articles/the-real-motivation-behind-systemd.html https://github.com/isd-project/isd https://github.com/rgwood/systemctl-tui
> To configure services, you pretty much have to interact with systemd these days, for better or for worse. Most services on your system will have a systemd service file that defines a systemd unit. These files define what command to run when that services is started, how to stop it, where to log things, etc. They’re usually not too bad to read, and you can find most of them in /usr/lib/systemd/system/. You can also define your own in /etc/systemd/system. https://missing.csail.mit.edu/2019/machine-introspection/
* _systemctl_: control service
> Once you have a systemd service in mind, you use the systemctl command to interact with it. systemctl enable UNIT will set the service to start on boot (disable removes it again), and start, stop, and restart will do what you expect. If something goes wrong, systemd will let you know, and you can use journalctl -u UNIT to see the application’s log. You can also use systemctl status to see how all your system services are doing. If your boot feels slow, it’s probably due to a couple of slow services, and you can use systemd-analyze (try it with blame) to figure out which ones. https://missing.csail.mit.edu/2019/machine-introspection/
* https://github.com/torfsen/python-systemd-tutorial
* https://systemd-by-example.com/
* can conf service to start on boot, restart if crashes https://www.reddit.com/r/Ubuntu/comments/7j5qgj/gunicorn_daemon_vs_gunicornservice_on_ubuntu_1604/
* preceded by Upstart https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04 https://christine.website/talks/systemd-the-good-parts-2021-05-16 https://unixsheikh.com/articles/systemd-isnt-safe-to-run-anywhere.html

BOOT
* https://www.youtube.com/watch?v=XpFsMB6FoOs
* _bootloader_: loads os e.g. GRUB
* _BIOS_: first step when powering on i.e. before bootloader
* https://utcc.utoronto.ca/~cks/space/blog/linux/LinuxBootOverview?
* https://news.ycombinator.com/item?id=35229045

## date/time

🗄️ `application.md` NTP

FORMATS
* kitchen: "3:04 PM"
* MM/DD/YYYY: "12/12/2024"
* YYYY-MM-DD: "2024-12-12"
* DD.MM.YYYY: "12.12.2024"
* _Unix_: seconds since January 1, 1970
* _ANSIC_: "Mon Jan _2 15:04:05 2006"
```sh
gum log --time ansic  # Thu Dec 12 09:54:57 2024  foo
```
* _RFC822_: "02 Jan 06 15:04 MST"
```sh
gum log --time rfc822  # 12 Dec 24 09:54 EST
```
* _RFC3339_: "2006-01-02T15:04:05Z07:00"
* _ISO8601_: "2006-01-02T15:04:05-07:00"

---

https://github.com/cdown/tzupdate
https://github.com/merschformann/gotz

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

## kernel

🗄 `languages.md` 'C'

🔍 https://livegrep.com/search/linux

📦 https://git.kernel.org/

* Rust https://news.ycombinator.com/item?id=42318644
* Rust, QEMU https://news.ycombinator.com/item?id=42253814
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

SYSTEM CALLS (SYSCALL)
* https://neugierig.org/software/blog/2024/09/retrowin32-syscalls.html
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

LOCATION
* `tools/PROJECT/YOUR-TOOL` for project related tools
* `bin/YOUR-TOOL` for things that are useful to have accessible at all times

ZA
> all executables should have the `execute` bits set i.e. `chmod a+x foo-bar`; git tracks the executable bit, and sets it during checkout
* _shebang line_: how os knows how to run your program
* fmt: `#!/usr/bin/env INTERPRETER` e.g. `#!/usr/bin/env python`
> The program `/usr/bin/env` locates the environment using the `PATH` variable like any other command. This lets us control which interpreter gets chosen in a given environment by manipulating `PATH` e.g. using a python virtualenv instead of the system python.

NAMING
* scripts: lowercase + snakecase e.g. `foo`, `foo-bar`, `foo-bar-baz`
* no file extension bc reimpl = rename in every place of usage, update doc links
* everything but env var is lowercase https://stackoverflow.com/a/673940

## perms + user/group

🗄️ `containers.md`

PERMS 📙 Evans linux https://chatgpt.com/c/672cbc33-dabc-8004-bbac-7c5050f53879 🗄️ `tools.md` find
* categories: `u` (user/owner) `g` (group) `o` (other) `a` (all)
* mv granular: `chmod` + group + `r|w|x` e.g. `u=rw` (user gains rw) `+x` (all gain x) `o-w` (other loses w)
* mv wholesale: `chmod $OCTAL`
* test: rw-only for owner `sudo -u nobody cat $FILE_WITH_PERMS_THAT_NOBODY_SHOULDNT_BE_ABLE_TO_READ`
* get as octal: `stat -f "%A" $FILE`
* default: `666` (file) `777` (dir)
* clean up DS files `fd -HI DS`
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
