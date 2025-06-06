# ⛩️

## 参考

## 进步

PDP1 for Eric Raymond book https://news.ycombinator.com/item?id=43002906

* _23_: mac mini
* _23_: macbook air
* _14_: macbook pro

# 📋 MANIFEST

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

## mbp14

🗄 `python-3.10-youtube-ffmpeg.md`

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

## mini23

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

#  🏭 MANUFACTURERS

https://drewdevault.com/2020/02/18/Fucking-laptops.html

CONSIDERATIONS
* ✅ Mac: familiarity, hardware
* ❌ Windows: WSL just something else to debug, unused to keybindings
* ❌ Linux: no Ableton, hardware, apps, bluetooth https://github.com/darkhz/bluetuith but if you do... https://www.youtube.com/@optimumtech/videos
> be like having American Express

## 🍎 Apple

MODELS 🗄️ `ml.md` OSS > hardware
```csv
model,base_price,cpu,gpu,mem,disk
air,1000,8,8,16,250
macbook,1600,10,10,16,500
imac,1300,8,8,16,250
mini,600,10,10,16,250
studio,2000,12,30,32,500
```

---

🔍 models https://support.apple.com/en-us/HT201300

* cleaning dust https://quanticdev.com/articles/cleaning-macbook-after-16800-hours-of-use/
* https://cfenollosa.com/blog/the-m1-macbook-air-one-year-later.html
* can't upgrade battery or drives since 2015 https://www.youtube.com/watch?v=Q1u2tA9dgCQ
* used: vendors will list year of OS vs. machine production year, ignore photos (might not even be of the same machine), processor (make sure exact type is listed, that they're quoting base speed, beware if year unlisted) https://www.youtube.com/watch?v=JF1EsYfxwhM
* use 'sold items' to gauge prices https://www.youtube.com/watch?v=b-ltpMVA7BI 6:10
* 2011 unibody: avoid these https://www.youtube.com/watch?v=8jM1brvJhzg 11:45
* 2012 Pro unibody (last pre-retina, easy to add hard drive) https://www.youtube.com/watch?v=8jM1brvJhzg 
* 2015 Pro https://www.youtube.com/watch?v=8jM1brvJhzg 3:20

## 🐧 Linux

can run ubuntu on Windows https://tech.marksblogg.com/satellogic-open-data-feed.html
https://www.thinkpenguin.com/ https://news.ycombinator.com/item?id=34180508

* not ready https://cfenollosa.com/blog/fed-up-with-the-mac-i-spent-six-months-with-a-linux-laptop-the-grass-is-not-greener-on-the-other-side.html
* script install https://blog.jessfraz.com/post/windows-for-linux-nerds/
* lack of support for Ableton, might not have audio interface drivers https://news.ycombinator.com/item?id=20745072
* _Chromebook_: Linux beta https://uglyduck.ca/chromebook-web-development/
* _Dell_: https://cfenollosa.com/blog/fed-up-with-the-mac-i-spent-six-months-with-a-linux-laptop-the-grass-is-not-greener-on-the-other-side.html break all the time https://news.ycombinator.com/item?id=32632720
* _Framework_: https://frame.work/ broken https://news.ycombinator.com/item?id=33322143 https://news.ycombinator.com/item?id=28606962 https://news.ycombinator.com/item?id=27926425 better now? https://frame.work/products/laptop13-diy-intel-ultra-1 https://omakub.org/ bad https://news.ycombinator.com/item?id=42163518 https://www.youtube.com/watch?v=tBS2PY2t9Mw
* _System76_: more expensive than Apple https://system76.com/ https://news.ycombinator.com/item?id=34599094 https://news.ycombinator.com/item?id=34599094 https://zackproser.com/blog/why-I-buy-system-76-computers
* _Thinkpad_: https://news.ycombinator.com/item?id=30241960 x200 https://drewdevault.com/2021/05/14/Pinebook-Pro-review.html beware machines after 2012, X60 can only deal w/ 32-bit os, X200/X220/X230 are popular https://www.youtube.com/watch?v=mxA9Gyyu6Rg 9:45 12:40 13:15
* Linux laptops https://news.ycombinator.com/item?id=35355494

## 🪟 Windows

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

# 🖥️ MONITORS

---

NEXT STEPS
* just port existing home setup
* measure work monitor
* figure out how to adjust to work monitor being so close (is that a bad thing?)

APPLE
* https://www.apple.com/mac-mini/specs/
* https://news.ycombinator.com/item?id=41987359
* https://news.ycombinator.com/item?id=34487066

I want to build a formula for computer monitor specs i.e. what factors matter and how to compute them to figure out what monitor you should buy. Factors I'm vaguely aware of:

* aspect ratio
* monitor size
* monitor resolution

Add any factors I'm missing, I don't know much on this topic.

DIMENSIONS & DISTANCE
```txt
Can you give me a rough formula for how far a computer monitor should be from your eyes (assuming average eyesight) given:

* aspect ratio
* monitor size
* monitor resolution
```
```python
# measurements in inches

screen_size = 23
ppi = 96

distance = (screen_size * ppi) / 60  # 60 = approximate pixels per degree of human vision for average eyesight at comfortable viewing
ppi = math.sqrt((horizontal_res ** 2) + (vertical_res ** 2)) / screen size
```

* https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development#is-4k-worth-it-even-with-abnormal-vision

## aspect ratio

💡 width to height expressed as a ratio

```python
def calculate_aspect_ratio(width: int, height: int) -> tuple[int, int]:
    """
    * calculate the simplified aspect ratio for given dimensions
    * uses gcd (greatest common divisor) to reduce the ratio
    >>> calculate_aspect_ratio(1920, 1080)
    (16, 9)
    """
    from math import gcd
    divisor = gcd(width, height)
    return (width // divisor, height // divisor)

def calc_dimension_from_ratio(target_width, target_height, ratio=None):
    """
    >>> calc_dimension_from_ratio(target_width=1280, ratio=(16, 9))
    (1280, 720)
    """
    width_ratio, height_ratio = ratio
    if target_width:
        return (target_width, int(target_width * (height_ratio / width_ratio)))
    else:
        return (int(target_height * (width_ratio / height_ratio)), target_height)
```

* _1:1_: square
* _3:2_: 35mm photos
* _4:3_: old TVs, monitors
* _16:9_: most modern screens, HD video

---

* https://www.jeffgeerling.com/blog/2020/making-terminal-window-right-aspect-ratio-streaming-or-recording
* Apple retina standard, 3:2 aspect ratio https://news.ycombinator.com/item?id=40385371 https://news.ycombinator.com/item?id=40399662

## coloration

* https://news.ycombinator.com/item?id=42796950
```txt
* Use diffuse light. This usually means multiple light sources bouncing and diffusing light off surfaces (ceilings, walls, etc) or diffusers.
* Minimize shadows. Shadows lead to contrast which can lead to eye strain. Use multiple, maybe directional, light sources to illuminate shadows.
* Minimize highlights. Windows without blinds let in lots of light which leads to contrast and can lead to eye strain. Curtains and blinds are great ways to diffuse light.
* Uniform color temperature. Try to make sure all your lights have the same color temperature. Small variations are okay but large color temperature variations lead to color contrast which also tends to be hard on eye strain.
* Select your color temperature based on needs and feeling. A lot of people prefer warmer color temperature lights and cool temperature lights are known to be more stressful for folks with anxiety-related conditions, but if your work requires accurate color representation, or you find yourself mentally trying to compensate for color temperature, then change the temperature to what you find most productive yet relaxing.
* Wall color. Remember that "white" light that reflects off colored surfaces will take on a hue similar to the reflected surfaces. Walls of different colors can cause challenges for uniform color temperature, and warm colored walls can take cold lights and turn them warm.
A side effect, of course, is that your room will become a lot more photogenic. It's no coincidence since photogenic rooms are often just easiest on the eye to look at.
"Golden Hour" is considered a great time for photogenic events, photographs, and videos. "Golden Hour" lighting tends to be diffuse, not too strong, and warm toned. Humans tend to really like this style of lighting and if you do too, you might want to recreate some of these properties in your office.
```
* dark mode: set from terminal https://stefan.sofa-rockers.org/2018/10/23/macos-dark-mode-terminal-vim/
* _Flux_: https://justgetflux.com/ https://news.ycombinator.com/item?id=30626803
* NightShift https://shifty.natethompson.io/en/

## frames

* _frame rate (FPS)_: how many frames CPU can produce per second
* 60 FPS is typical
* 6ms for single https://github.com/neurocyte/flow
* _refresh rate_: how quickly monitor can display FPS
* 60 Hz is typical

## pixels

https://www.nayuki.io/page/pixel-is-a-unit-of-length-and-area

💡 bigger screen = need higher resolution for higher PPI
```txt
if you have a 4k display and it's small, you'll have higher PPI and the images will be clearer
if you have a 4k display and it's big, you'll have lower PPI and the images will be less clear
```

* _scaling_: adjust size of UI elements without changing resolution
* ensures content remains readable esp. on high-resolution displays where default PPI can make elements too small
* _resolution_: total number of pixels
* _PPI_: density
* aka pixel density, pixel-to-screen size ratio
```python
import math
resolution = [1920, 1080]
diagonal_res = math.sqrt(resolution[0]**2 + resolution[1]**2)
ppi = diagonal_res / 23
```

```python
def calculate_ppi(width, height, diagonal_inches):
    """
    width (int): horizontal resolution (pixels)
    height (int): vertical resolution (pixels)
    diagonal_inches (float): screen diagonal size (in inches)
    """
    import math
    diagonal_pixels = math.sqrt(width**2 + height**2)
    ppi = diagonal_pixels / diagonal_inches
    if ppi >= 200:
        sharpness = "Excellent (Retina-level sharp for close work)"
    elif 160 <= ppi < 200:
        sharpness = "Very good (crisp and clear for desk work)"
    elif 100 <= ppi < 160:
        sharpness = "Good (suitable for general use, but not optimal for close work)"
    else:
        sharpness = "Low (visible pixels at close distances)"
    return {
        "width": width,
        "height": height,
        "diagonal_inches": diagonal_inches,
        "ppi": round(ppi, 2),
        "interpretation": sharpness
    }
```

---

* 1080p vs. 4k for readability https://news.ycombinator.com/item?id=23551983 

```txt
macOS "Retina" Scaling:
* Mac Retina displays (e.g., MacBook Pro 14" and 16") have high PPI (218+ PPI).
* By default, macOS renders UI at a virtual resolution that appears more like 2560×1600 (even though the physical resolution is higher).
* You get the appearance of a lower resolution but with sharper rendering.

Example:
4K resolution (3840 × 2160) at 200% scaling → UI looks like 1920 × 1080, but with twice as many pixels for every element → much sharper.

Windows Scaling:
* On Windows, you can set scaling to 100%, 125%, 150%, or more.
* This adjusts how big the text, icons, and windows appear.
* Without proper scaling, a 4K monitor at 100% scaling can make everything appear tiny.
```

## specs

---

FACTORS 🗄️ machines
* scaling

* https://registerspill.thorstenball.com/p/joy-and-curiosity-13 https://daniel.lawrence.lu/blog/y2023m12d15/
* _OLED_: most accurate, best for viewing from non-direct angle https://www.tomsguide.com/us/what-is-oled,news-25120.html

## models

* _BenQ RD320UA_: $650 https://www.youtube.com/watch?v=784pFXYBqsg https://www.youtube.com/watch?v=rp1fEKGkG2M
* _BenQ PD2706U_: https://www.amazon.com/dp/B0BS4R8YDJ/?tag=thewire06-20&linkCode=xm2&ascsubtag=F0401J8TNQFDX7TRVABATYDS716PY&th=1
* _BenQ PD2705U_: ✅ $400 same as PD2706U but no built-in KVM
* _Dell S2318HN_: ✅ $175 in 2017, 23", 1080p
* _Dell U2723QE_: $650 https://www.nytimes.com/wirecutter/reviews/best-monitors/
> The Dell UltraSharp U2723QE has a higher 4K resolution than our top pick, so text and images will look much sharper. It also has a new technology that doubles its contrast compared with that of standard IPS monitors, so its 2000:1 contrast ratio looks great when displaying movies, TV shows, and pictures. This monitor also looked great when used with Mac machines, which is something we can’t say for most lower-resolution 1440p monitors. So if you’re looking for a high-resolution 27-inch display, this is the best one we’ve tested.
* _Dell U3223QE_: $600, 32", 4k, KVM switch https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/
* _Spectrum black_: 🎯 $650 https://www.dough.tech/pages/monitors
> assume this is 27"

---

* _Asus pa278cgv_: https://www.nytimes.com/wirecutter/reviews/best-27-inch-monitor/ https://www.nytimes.com/wirecutter/reviews/best-monitors/
* _Dell S2721QS_: https://people.zsa.io/leon-si/
* _Dell S2722QC_: $225, 27", 4k https://www.rtings.com/monitor/reviews/best/by-usage/programming-and-coding https://www.amazon.com/dp/B09DTDRJWP/
* _Dell U2515H_: 🎯 $250 https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development
* _Dell U2518D_: 🎯 https://nickjanetakis.com/blog/how-to-pick-a-good-monitor-for-software-development

# 🟨️ ZA

USB https://en.wikipedia.org/wiki/USB
* _USB_: protocol
* spec is a mess apparently https://news.ycombinator.com/item?id=25724014 https://tidbits.com/2021/12/03/usbefuddled-untangling-the-rats-nest-of-usb-c-standards-and-cables/
* _connector_: hardware for connection e.g. USB-A, micro USB, USB-C
* USB-C https://www.sweetwater.com/insync/what-thunderbolt-3-usb-c-mean-to-musicians/
* _Thunderbolt_: https://www.pcmag.com/news/thunderbolt-3-vs-usb-c-whats-the-difference
* works w/ USB-C https://www.youtube.com/watch?v=H4Z67HfHkN4 6:00

## cameras

can just use an iPhone for youtube https://www.youtube.com/watch?v=UjxD6zn33t0

💡 Delco photo book https://jaapgrolleman.com/shanghai-before-the-foreigners/ https://loosejoints.biz/collections/current-titles/products/holy-island https://loosejoints.biz/collections/current-titles/products/robin-graubard-road-to-nowhere https://loosejoints.biz/collections/current-titles/products/office https://www.newyorker.com/culture/photo-booth/the-frightening-familiarity-of-late-nineties-office-photos https://news.ycombinator.com/item?id=41926849

* https://news.ycombinator.com/item?id=42273518
* series https://deannadikeman.com/leaving-and-waving
* kids https://www.youtube.com/watch?v=lTyRiO08xi8 https://www.amazon.com/Toddler-Digital-Instant-Childrens-Birthday/dp/B0CSW8719G
* fancy https://www.youtube.com/watch?v=Z--EFPp5Yds https://daniel.lawrence.lu/blog/y2024m05d31/
* iPhone: 🎯 camera https://www.youtube.com/watch?v=jjpylH_We_o video https://www.youtube.com/watch?v=M7paNi4UVDc
* early film https://www.youtube.com/watch?v=O0YcfiSR-wg
* how cameras work https://news.ycombinator.com/item?id=25357315
* multiple camera angles https://www.jeffgeerling.com/blog/2020/recording-multiple-camera-angles-full-size-simultaneously-on-mac
* DSLR camera https://www.youtube.com/watch?v=vQXmPlBskrk

## iPad

DRAW 🗄️ `draw.md` digital https://www.youtube.com/watch?v=2RqaNTPjzQ8 https://www.creativebloq.com/buying-guides/best-ipad-for-procreate
> pencil compatibility
* size: mini is too small
* storage: at least 256GB
* mem: 8GB https://www.youtube.com/watch?v=988Jua0fMms [1:00]

GOLF 🗄️ `golf.md` analysis
> 📍 https://apps.apple.com/us/app/onform-video-analysis-app/id1490334045 https://apps.apple.com/us/app/swing-profile-golf-analyzer/id1039981052 https://apps.apple.com/us/app/v1-golf-golf-swing-analyzer/id349715369
* size: mini good for stand but bad for viewing
* storage:
* mem:

MUSIC 🗄️ `audio.md` garageband
> need a keyboard?
> any special reqs for recording guitar?
* size: bigger = better
* storage:
* mem:

SKATE 🗄️ `skate.md`
* size: mini good for stand but bad for viewing
* storage:
* mem:

---

💻 https://github.com/zachvalenta/apple-models-data-analysis
> make new version for this

| IPAD   | STATUS  | USED  | NEW | DISPLAY | STORAGE | PENCIL |
|--------|---------|-------|-----|---------|---------|--------|
| mini   | buy     | 120   | 500 | 8       |  64     | ?      |
| reg    | caution | 170   | 350 | 11      |  64     | ?      |
| air    | buy     | ---   | --- | 11      |  --     | ?      |
| pro    | neutral | ---   | --- | --      |  --     | ?      |

MODELS
* buy old version? https://www.amazon.com/dp/B09G9FPHY6 🔗 versions https://en.wikipedia.org/wiki/IPad#iPad https://www.ebay.com/str/guaranteecellular
* buy used mini for golf ($150)?
* buy used reg for procreate ($170 + pencil $80)?

PENCIL
* can just buy on amazon https://www.youtube.com/watch?v=MQnejB-SLWw [5:15]
* https://www.amazon.com/Apple-Pencil-1st-Generation-Adapter/dp/B0BJLG69QR
* https://support.apple.com/en-us/108937
* https://en.wikipedia.org/wiki/Apple_Pencil
* https://www.lifewire.com/apple-pencil-compatibility-with-ipad-5189841

## KVM

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

## mice

* mouse: magic mouse, keychron m3 https://www.keychron.com/products/keychron-m3-wireless-mouse https://www.nytimes.com/wirecutter/reviews/best-wireless-mouse/
* cooling pad for mbp2014 https://www.amazon.com/gp/product/B00NNMB3KS
* keep Teams active :) https://news.ycombinator.com/item?id=34273107

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
* music: perfect ear, liveBPM, Koala Sampler https://www.youtube.com/watch?v=Wwq5ChHiGGk musicolet, playtube, Youtube alternative https://github.com/TeamNewPipe/NewPipe Meta (audio metadata) 搜 'Meta on MacOS 10.10'
> Music Folder Player was good but introduced video ads https://play.google.com/store/apps/details?id=de.zorillasoft.musicfolderplayer&hl=en_US&gl=US 
* transport: maps, lyft, uber, airbnb, stasher
* language: word reference, easy voice, vlc, libby, overdrive, translate, pleco
* chess/golf: drive, camera, video frame player, chess clock, chess, lichess
* util: clock, interval timer, youtube, play tube, latch, monzo, labcoat, google home, google authenticate
* files: Podcast Addict https://github.com/zhanghai/MaterialFiles

---

* iPhone https://www.youtube.com/watch?v=10iUIoVBRI8
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

## screencast

* `cmd shift 5` + select audio input
* howto https://www.youtube.com/watch?v=AzVn5H0ZNVM https://www.youtube.com/watch?v=K5GeaoJCsoI
* livestream https://til.simonwillison.net/youtube/livestreaming
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
