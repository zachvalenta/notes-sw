# ⛩️

## 参考

🗄️ `built.md` homes / studio
🔗 https://www.reddit.com/r/MechanicalKeyboards/
📙 https://shifthappens.site/#story-of-a-photo

## 进步

* _24_: models (Apple refurbished, nuphy air 75, keychron k8, keychron v8) program (v8 cmd keys to center)

https://getreuer.info/posts/keyboards/tour/index.html
https://blog.zsa.io/zsa-keyboard-first-month/

PROBLEMS WITH CURRENT BOARDS
* v8: no tilde/backtick
* air75: too scrunched, no opt on right side

CURRENT THOUGHTS
* used ZSA are too expensive, better to buy new
* buy Corne

# 📐 LAYOUTS

🔗 https://www.keyboard.university/100-courses/keyboard-sizes-layouts-gdeby

ERGO https://www.youtube.com/watch?v=pK41Mr4Kdd0 [1:45] https://www.youtube.com/watch?v=rnnNNLaFZ9Y
* thumb under palm e.g. CMD
* leaving home row e.g. BACKSPACE
* spacebar a waste of space
* ESC too far away

FACTORS
* diagonal (QWERTY)
* ortholinear (grid) https://www.youtube.com/watch?v=pK41Mr4Kdd0 [4:00]
* column stagger (straight + pinky stagger) https://www.youtube.com/watch?v=grg-_DNqoNo [1:15]
* thumb cluster https://www.youtube.com/watch?v=grg-_DNqoNo [2:30]
* tenting

TYPES
* BYO https://www.youtube.com/watch?v=RtYJYFMWjNM https://news.ycombinator.com/item?id=41972550
* _Alice_: ergo
* _Neo_: for German + English https://dariogoetz.github.io/noted-layout/
* _TKL_: 87 keys; aka 80% https://www.keychron.com/blogs/archived/keyboard-buying-guide
* _100%_: 104 keys

LETTERING
* _Colemak_: https://colemak.com/ https://people.zsa.io/andreas-tacke/
* _Dvorak_: 
* _QWERTY_: Anglosphere + western Europe https://en.wikipedia.org/wiki/QWERTY
* _QWERTZ_: https://en.wikipedia.org/wiki/QWERTZ
* _Workman_: 

## programmable

🗄️ `interfaces.md` terminals > features

PROGRAMS
* _kanata_: https://github.com/jtroo/kanata
* _Launcher_: ✅ https://launcher.keychron.com/ 🗄️ `dot/shell/keychron-v8.json`
* _Oryx_ built off of QMK https://blog.zsa.io/whack-a-key/ https://www.youtube.com/watch?v=FcFYv_dHIiQ
* can access QMK directly https://blog.zsa.io/oryx-custom-qmk-features/
* _QMK_: firmware; C impl https://www.youtube.com/watch?v=D05B6NXV504
* code > configurator https://www.youtube.com/watch?v=AA8fw2MbpYg
* _VIA_: https://www.caniusevia.com/ https://www.youtube.com/watch?v=CLiZ5rAEx3A
* "authorize your device" doesn't work for Nuphy
* "authorize your device" only works for Keychron in Chrome
* got basic homerow mods to work but conflicted with vim https://www.youtube.com/watch?v=CLiZ5rAEx3A
> one thing with initial stab [D,S] is that the timing is too fast and conflicts with Vim
```txt
MT(MOD_LGUI,KC_F)
MT(MOD_RGUI,KC_L)
```
* _ZMK_: https://www.youtube.com/watch?v=riqmW3UHqPY https://github.com/eigatech/zmk-config https://www.youtube.com/watch?v=pK41Mr4Kdd0 [9:00] https://www.youtube.com/watch?v=wTMcH7u-vu0

ZSA KEYS https://configure.zsa.io/voyager/layouts/ https://configure.zsa.io/moonlander/layouts/default/latest/2/
> you'd presume most of ZSA is Vim users
* 📍 example https://www.youtube.com/watch?v=6blfyl2Q0ag [12:00]
* z = CTRL
* quote = CMD
* 📍 double tap (aka tapdancing) in lieu of CMD + key https://www.youtube.com/watch?v=6blfyl2Q0ag [10:30,11:50]
> maybe better to start out keeping the CMD workflow
> can tune the time btw tapping to get around ambiguation
* 📍 thumb cluster meant to be used by index figure (for Vim escape?)
* Colemak backspace = QWERTY caps
* _hyper_: ALT CMD CONTROL SHIFT = global hotekey
* _meh_: ALT CONTROL SHIFT = global hotekey
* _layer_: SHIFT + customization
* _macro_: sequential https://www.youtube.com/watch?v=JydEeUEw8d8 [1:00]
* _combo_: 类似 Vim https://blog.zsa.io/2212-combos/ conflicts https://www.youtube.com/watch?v=5vYhPitiU2I

---

> 🎗️ learn how to use programmable so you can avoid RSI
> https://www.youtube.com/results?search_query=macos+to+zsa+keyboard
> current RSI threats: thumbs on CMD
> I think for generalist usage they can be adapted to pretty easily, but as a developer, the lack of dedicated keys for [, ] and ' is an insurmountable obstacle for me. Those keys are in my opinion perfectly placed on regular keyboards and no amount of layering, tap dancing or anything else will ever come close. https://news.ycombinator.com/item?id=37391934
* QMK|VIA https://www.youtube.com/watch?v=CLiZ5rAEx3A https://www.youtube.com/watch?v=nCUJK9zDXpI https://www.youtube.com/watch?v=CLiZ5rAEx3A https://www.keychron.com/blogs/news/why-qmk-via-is-one-of-the-most-essential-features-for-a-custom-keyboard https://www.youtube.com/watch?v=EWiOIVnrmMs
* home row mods https://www.youtube.com/watch?v=sLWQ4Gx88h4 https://www.youtube.com/watch?v=CLiZ5rAEx3A https://github.com/dreamsofcode-io/home-row-mods https://www.youtube.com/watch?v=pK41Mr4Kdd0 [6:30]

## mapping

ZA
* space bar: thumb paddle (outer)
* CMD: thumb paddle (inner)
* ✅ arrows: layer + Vim

L SIDE
* ✅ tilde/backtick
* tilde
* TAB
* ESC
* SHIFT
* CTRL

R side
* ✅ hyphen
* ❌ equals
* ❌ brackets
* ✅ colon
* ✅ quote
* ✅ period / comma / angle bracket
* ✅ slash / question
* ENTER
* SHIFT

---

* https://www.youtube.com/watch?v=IKKsREAlkoE @ 3:35
* https://www.youtube.com/watch?v=WfIfxaXC_Q4
* https://www.youtube.com/watch?v=KTWzwXg9Ra8
* no wasted inside buttons https://www.youtube.com/watch?v=KlyMuZIEOOw [4:00]
* keys the voyager has
> I need at least [ ] ; ' \ , . to be separate physical keys (because they are also letters/essential punctuation in other languages), and ideally arrows too, and more thumb buttons than just 2 (ideally ctrl/win/alt/altGr and backspace/delete/space/enter). Also quite important for gaming to have modifiers and the usual keys (spacebar, tab, etc) easily available without layers, tap hold or tapdance.

# ⌨️ MODELS

🏪
> prebuilt cheaper in time and money https://www.youtube.com/watch?v=N_mZEbJmKYg
* https://keeb-finder.com/
* https://mechanicalkeyboards.com/
* https://novelkeys.com/
* https://www.boardsource.xyz

KEYCHRON
* ✅ case https://www.keychron.com/products/keychron-keyboard-carrying-case
* _c1_: $75 https://www.keychron.com/products/keychron-c1-pro-qmk-via-wired-mechanical-keyboard?variant=40615797391449
* _k1_: stockout https://www.reddit.com/r/NuPhy/comments/1brdzgy/will_there_ever_be_low_profile_tkl_80_layout/
* _k8_: ✅ $110; switches (Gateron g pro brown) https://www.keychron.com/products/keychron-k8-pro-qmk-via-wireless-mechanical-keyboard?variant=39755425349721 https://www.amazon.com/Keychron-Wireless-Mechanical-Hot-Swappable-Programmable/dp/B0B97JZV99
* _v3_: $110: TKL, normal profile https://www.nytimes.com/wirecutter/reviews/our-favorite-mechanical-keyboards/ https://www.amazon.com/dp/B0CW5B5KL8

NUPHY
* _halo75_: less scrunched layout than air75? https://www.amazon.com/nuphy-Mechancial-Kyeboard-Swappable-Bluetooth/dp/B0D5Q891F1
* _air75 v2_: ✅ $125 https://nuphy.com/products/air75-v2
* 75% is too scrunched for me, tons of typos
* low profile (2.3mm)
* slow shipping (but next time you can just buy from Amazon?)
* _gem 80_: $150; TKL, normal profile https://nuphy.com/collections/keyboards/products/gem80

ZA
* _Apple wired_: ✅ $60; 100%, low profile (2.3mm) https://www.amazon.com/dp/B07K7V1FWC
* _Logitech mx mini_: https://www.logitech.com/en-us/products/keyboards/mx-keys-mini.920-010475.html
* _Varmilo mac_: https://varmilo.com/products/mac?variant=45350805405915 keycaps https://varmilo.com/products/shurikey-gear-keycaps-sets-167-keys?pr_prod_strat=jac&pr_rec_id=c6579d995&pr_rec_pid=7642777518299&pr_ref_pid=8195613425883&pr_seq=uniform

## BYO

🔍 serviced https://www.keyboardconcierge.com https://get-switched.com/ https://www.avikeebs.com/
> https://www.youtube.com/watch?v=PDguuYMG0IQ

COMPONENTS https://www.youtube.com/watch?v=7UXsD7nSfDY @ 4:45
* controller https://nicekeyboards.com/nice-nano/ [2:55]
* _PCB_: plastic + copper paths to allow current flow [3:05]
* program layout of PCB with ergogen https://github.com/ergogen/ergogen [4:30]
* _switch_: connects metal to PCB [3:20]

MODELS
* https://www.youtube.com/watch?v=h_ex-oMVOrI
* _Boardsource corne_: 🎯 https://www.youtube.com/watch?v=wTMcH7u-vu0 https://www.youtube.com/watch?v=j41G25VORmI https://www.boardsource.xyz/products/Corne https://www.youtube.com/watch?v=riqmW3UHqPY
* find someone to do soldering https://www.youtube.com/watch?v=vzDTdLaAzXc
* case https://www.youtube.com/watch?v=gMTfkPxcoEk
* layout https://www.youtube.com/watch?v=uy7_lswgb6A
* _Chocofi_: Voyager-esque https://www.youtube.com/watch?v=pK41Mr4Kdd0 [12:00]
* _Keebio iris_: 🎯 ZSA voyager replacement https://keeb.io/ https://keeb.io/products/iris-ce-keyboard https://keeb.io/products/iris-keyboard-pre-built https://www.youtube.com/watch?v=pK41Mr4Kdd0 [4:25] https://www.youtube.com/watch?v=wTMcH7u-vu0
* _Lily_: 🎯 https://www.youtube.com/watch?v=l5kAx08Iom4 https://typeractive.xyz/pages/build/lily58_mx

---

* where to source parts https://www.youtube.com/watch?v=co1rJaErdrI
* small boards https://www.youtube.com/watch?v=XwgoZcRi4ek
* home office https://www.youtube.com/watch?v=Lt6R6kNjVNU
* takes forever https://www.youtube.com/watch?v=9P74eCU19d0 https://www.youtube.com/watch?v=3n28JNSizvo https://www.youtube.com/watch?v=cnZEcnlyGyg
* space bar https://www.youtube.com/watch?v=VLnH61NCi9Y https://www.youtube.com/watch?v=QKQMPF15mgE

HOWTO
* https://www.youtube.com/watch?v=FJgvi7WShxY
* https://www.youtube.com/watch?v=7UXsD7nSfDY

## ergo

MAYBE
* _Dygma defy_: 🎯 $370; featureful, bad taste https://dygma.com/pages/defy https://www.youtube.com/watch?v=R9YTQn1ik9I
* _Glove80_: $400 low-profile, expensive, ugly https://www.moergo.com/collections/glove80-keyboards https://www.youtube.com/watch?v=QLb3ewK8R2Y

NO TILDE/BACKTICK
* _Keychron q8_: $210  https://www.keychron.com/products/keychron-q8-alice-layout-qmk-custom-mechanical-keyboard?variant=40077527122009
* _Keychron v8_: ❌ $90 Gateron jupiter brown https://www.keychron.com/products/keychron-v8-max-alice-layout-qmk-custom-mechanical-keyboard
* _Keychron k11_: $115; low profile https://www.keychron.com/products/keychron-k11-pro-alice-layout-qmk-via-wireless-custom-mechanical-keyboard programmable but only through Keychron (vs. QMK/VIA) https://www.youtube.com/watch?v=zqRBxioJIRI [5:00]

DOESN'T SOLVE RSI 
* _Akko alice_: $130 cmd key not symmetric https://en.akkogear.com/product/acr-pro-alice-plus-mechanical-keyboard/
* _Kinensis freestyle_: ❌ cheap, no hot swap https://www.amazon.com/Kinesis-Freestyle2-Ergonomic-Keyboard-Separation/dp/B009ZNBJK8
* _Matias ergo_: https://matias.ca/ergopro/programmable/

TOO SMALL|STRANGE
* _Bastard charybdis_: https://bastardkb.com/charybdis/ https://www.youtube.com/watch?v=riqmW3UHqPY
* _Splitkb elora_: https://splitkb.com/products/elora?variant=47357022699867 https://www.youtube.com/watch?v=grg-_DNqoNo
* _TOMEM_: https://github.com/GEIGEIGEIST/TOTEM https://www.youtube.com/watch?v=riqmW3UHqPY

## 🪐 ZSA

💡 voyager (portable) moonlander (key count + zip kit)
> buy used in case thumb cluster doesn't work? https://www.milesmcbain.com/posts/zsa-moonlander-review/ https://www.reddit.com/r/ergodox/comments/o8a7py/a_review_of_the_moonlander_after_60_days_and_a/ ++ Corne/Gergo keyboards

MODELS https://configure.zsa.io/voyager/layouts/
* _Ergodox_: 2015 https://ergodox-ez.com/ layout 52 keys, thumb cluster is too busy https://www.youtube.com/watch?v=KlyMuZIEOOw [2:10] https://www.youtube.com/watch?v=wpuwhqy5cgg https://configure.zsa.io/voyager/layouts/
* _Moonlander_: 2020 https://www.zsa.io/moonlander 72 keys https://www.youtube.com/watch?v=5AqXjVrnI2E zip kit = too many keys period? https://www.youtube.com/watch?v=BK_ezYCgIpY https://www.zsa.io/moonlander/zip-kit  https://www.youtube.com/watch?v=SVCFSe6NozU more keys on R side for ENTER/shift; tenting doesn't work bc poor build quality https://www.youtube.com/watch?v=y3lnLcb-nPo https://www.youtube.com/watch?v=SVCFSe6NozU https://www.youtube.com/watch?v=l-qkKIpHu9A [21:00]
* _Voyager_: 2023 https://www.zsa.io/voyager https://www.reddit.com/r/zsaVoyager/ https://www.youtube.com/watch?v=sLWQ4Gx88h4 [2:00]
> better angle for thumb cluster
> probably makes more sense to buy as ZSA themselves uses their own stuff and figured out how to improve the Moonlander + Moonlander already came with zip kit to reduce number of keys
* 52 keys not enough? https://configure.zsa.io/voyager/layouts/
* pinky keys should be big buttons https://www.youtube.com/watch?v=KlyMuZIEOOw [3:30]
* portable, tbd on choc switches tripod mount https://www.zsa.io/voyager/tripod-mount https://www.youtube.com/watch?v=rY2D4G4krRQ
* more tenting https://www.youtube.com/watch?v=II3Wm5P6fOU 3d printing for greater tenting https://www.zsa.io/voyager/printables https://chatgpt.com/c/673357a3-c144-8004-b9c4-7ace2f0cd9c3

COMPANY https://www.reddit.com/r/ergodox/
* graphic design
* culture of writing
* how it's made https://www.youtube.com/watch?v=7TvKziKKa98
* attention to detail e.g. pinky nib

---

https://people.zsa.io/andreas-tacke/
https://people.zsa.io/melissa-lopez/
https://people.zsa.io/anna-e-so/
https://people.zsa.io/stephen-perera/
https://people.zsa.io/pulin-agrawal/
https://people.zsa.io/emma-anderson/

# 🟨 ZA

STORAGE
> just use boxes for now
* shelves https://www.reddit.com/r/MechanicalKeyboards/comments/7vz7lr/what_is_everyones_keyboard_storage_situation_like/?rdt=58394 https://www.ikea.com/us/en/p/alex-drawer-unit-on-casters-white-80485423/
* https://www.reddit.com/r/MechanicalKeyboards/comments/6jm453/help_for_those_that_have_multiple_keyboards_how/ https://imgur.com/a/keyboard-storage-Ym4An https://www.amazon.com/dp/B01K07MZPK/ref=cm_sw_r_cp_apip_fyUmiTPzneJiH

## features

MY SETUP
* layout: TKL
* connection: wired
* no: lights, rotary knob

FEATURES
* connection: usb-c is faster https://www.keychron.com/blogs/news/solid-wireless-connection-type-c-connection
* lights
* rotary knob: typically used for volume, page up/down https://www.reddit.com/r/MechanicalKeyboards/comments/12nfiqg/what_are_you_using_the_knob_for/?rdt=47962

ZA
* _group buy_: group pre-order https://www.keyboard.university/100-courses/group-buy-335xl https://kbdfans.com/collections/group-buy

---

* plate, PCB https://www.amazon.com/Keychron-Wireless-Mechanical-Hot-Swappable-Programmable/dp/B0B97JZV99
* tray for desk https://www.amazon.com/VIVO-Computer-Keyboard-Platform-MOUNT-KB05E/dp/B07HFDJCSL
* can you use Windows keyboards for macOS? https://www.durgod.com/product/s230-dracula/
* layers https://news.ycombinator.com/item?id=34069927
* wrist rest https://news.ycombinator.com/item?id=34276226
* Linux vs. Macos https://www.youtube.com/watch?v=GKoz7mm2tNI
* chicklet https://www.youtube.com/watch?v=8jM1brvJhzg 5:20 butterfly started with 2015 12' Macbook https://www.theverge.com/2020/5/4/21246223/macbook-keyboard-butterfly-magic-pro-apple-design https://support.apple.com/keyboard-service-program-for-mac-notebooks returned to normal scissor keyboard (aka 'magic') with 2020 16' Macbook Pro https://www.wsj.com/articles/apple-updates-ipad-macbook-air-with-new-keyboard-11584538891
* remapping https://missing.csail.mit.edu/2019/os-customization/
* stenography for transcription https://www.openstenoproject.org/plover/

## keycaps

🏪
* Etsy
* https://novelkeys.com/collections/keycaps
* https://pacificparadiseprints.shop/ https://www.youtube.com/@PacificParadisePrints

* compatability: need to consider the switch type, keycap profile, stabilizer
* size
> Keycap sizes are described in terms of a "u. width. For example, 1u is the size of each of the number and alphabet keys on a keyboard. A 2u key, like Backspace, is twice the size of those 1u keys...compact keyboards often have a 1.75u right Shift key in place of the standard 2.75u right Shift key as well as 1u modifiers in the bottom row. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* color https://blog.zsa.io/how-to-dye-keycaps/
* _legend_: character on key; double-shot (more expensive) dye-sub (PBT only, non-transparent)
* _profile_: height * shape https://thekeeblog.com/overview-of-different-keycap-profiles/
* less options for low profile https://www.youtube.com/watch?v=BWQFUPm6XE0
* _PBT_: more durable
* _ABS_: less durable

## switches

🏪
* https://milktooth.com/products/switches
* https://switches.mx/

SOUNDS https://www.youtube.com/watch?v=xtadlynfAZ8 https://pacificparadiseprints.shop https://www.youtube.com/@kineticlabskb/videos
> need shocks for real quiet https://www.youtube.com/watch?v=UIeyhGTwxGA
* _clicky_: high pitched; Gateron blue
* _creamy_: ✅ quiet, more resistance; Gateron brown|milky yellow https://www.youtube.com/watch?v=EzKB-__6IW0 [13:00]
* _thocky_: clacky, less resistance; Gateron red

SEMANTICS
* _actuation_: lighter typists prefer red/blue, heavier prefer greens and blacks
* O rings https://www.youtube.com/watch?v=mvLyaSl3mmw
* _linear_: no bump on actuation
* _tactile_: bump on actuation e.g. MX Brown
* _clicky_: tactile + clicky sound
* _hot-swappable_: don't need to solder in new switch

TYPES
* _ALPS_: vintage https://matias.ca/switches/click/
> ALPS switches have been considered by enthusiasts to be one of the rarest type key switches. They are not as popular as mechanical switches, membrane switches, and even Topre switches. In fact, they can only be seen in vintage keyboards that were produced before the rise of membrane keyboards in the 1990s. https://keyboardsexpert.com/what-are-alps-switches/
* _mechanical_: 
* _membrane_: 
* _Topre_: https://duarteocarmo.com/blog/happy-hacking-keyboard-review https://gizmodo.com/this-is-the-perfect-keyboard-1845258727 HHKB https://www.youtube.com/watch?v=EzKB-__6IW0 [3:50]
> Switch makers also make low-profile switches, which aren’t as tall and have less travel. You can also find other, completely different types of switches, such as Topre, buckling spring, and Alps clones. None of these switch types are compatible with the wide pool of keycaps designed for MX stems, but they all have their own unique appeal. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/

---

MX vs. choc
> However, in general, Choc switches will be a little bit quieter than their MX-style contemporaries because of some simple acoustic principles. Choc switches allow for smaller enclosures that give sound waves less space to bounce and echo. Choc keycaps also tend to be more flat instead of hollow with lots of space inside them like MX-style keycaps, which further cuts down on possible echo. https://www.zsa.io/voyager/our-keyswitches
* choc harder to remove https://www.youtube.com/watch?v=6blfyl2Q0ag [1:30]

* _throw_: travel distance https://www.zsa.io/voyager/our-keyswitches
* _force rating_
> On the whole, Choc switches have higher force ratings than MX-style switches, but they still feel much lighter because of their shorter travel distance — you end up applying this force for a much shorter time. https://www.zsa.io/voyager/our-keyswitches

* mechanical keyboard: cherry mx browns https://www.keychron.com/ clear is quietest, blue is clicky, brown is chunky https://news.ycombinator.com/item?id=27221191 https://www.imore.com/best-mechanical-keyboards-mac customer service https://www.reddit.com/r/NuPhy/comments/ztbr5n/apologies_for_the_shipment_delay_and_adjustment/
* mixing https://www.youtube.com/watch?v=YEj-wnhNSIk
* linear switches don't feel clicky https://www.youtube.com/watch?v=xtadlynfAZ8
> One other small detail to keep an eye out for is north or south-facing switches. North-facing switches have the LED cutout facing toward the top of the keyboard - they're better at illuminating shine-through legends, but aren't compatible with common Cherry-profile keycaps. South-facing switches have the LED cutout facing toward the front of the keyboard, and they are compatible with Cherry-profile keycaps. Some keyboards have both north  and south-facing switches, so make sure to double-check before buying a new set of keycaps. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* it goes deep https://www.theremingoat.com/ https://keyboardsexpert.com/what-is-a-frankenswitch-keyboard-switch/
> If you don't already have a preference, we recommend Brown switches made by Gateron, Kailh, or Cherry because they're popular, readily available tactile switches that are good for most tasks and quiet enough for most offices...Clicky switches—like Blues and Kailh Box Whites—provide fun, typewriter-esque feedback. But they’re not ideal if you work or game in a shared space because they're very noisy...Optical switches use a laser to determine when you actuate a key. Manufacturers claim they work faster than mechanical switches, but in our experience, a light linear option like the common Red switch or the gaming-focused Cherry MX Speed Silver is plenty fast. https://www.nytimes.com/wirecutter/blog/how-to-shop-for-a-mechanical-keyboard/
* tester https://drop.com/buy/kbdfans-all-in-one-72-switch-tester?defaultSelectionIds=973206#signupv2 https://kineticlabs.com/switches/kinetic/keyboard-switch-sample-packs
* for low profile https://www.howtogeek.com/339502/low-profile-switches-are-coming-to-shrink-your-mechanical-keyboards/
* creamy https://kineticlabs.com/switches/hmx/hmx-latte-switches

## typing

ZA
* WPM calculation https://www.speedtypingonline.com/typing-equations https://github.com/AnirudhG07/typeinc?ref=terminaltrove#3-grading-and-typeinc-score-
> seems like I'm ~85wpm as of 24.11 on Keychron k8
* features: export, individual keys
* Oryx training https://www.youtube.com/watch?v=e6krxDENYOM
* _keycastr_: keystroke visualizer https://github.com/keycastr/keycastr https://switowski.com/blog/favorite-mac-tools/

TEST
* _gtypist_: https://archive.vn/9PAGP https://www.youtube.com/watch?v=A_3MP_V-kB4
* _keybr_: web, lightweight https://www.keybr.com/
* _monkeytype_: zach_v https://monkeytype.com/ https://www.youtube.com/watch?v=EzKB-__6IW0 [2:23]
* _smassh_: 🐍 https://github.com/kraanzu/smassh
* _ttyper_: local, no Homebrew install, no saved results https://github.com/max-niederman/ttyper
* _typingclub_: web https://www.typingclub.com/sportal/
* _typelit_: web + literature https://www.typelit.io/
* _typioca_: local https://github.com/bloznelis/typioca
* _typeinc_: 🎯 local + save results https://github.com/AnirudhG07/typeinc errors https://github.com/AnirudhG07/Typeinc/issues/3 https://github.com/AnirudhG07/Typeinc/issues/4

IMPORTANCE https://steve-yegge.blogspot.com/2008/09/programmings-dirtiest-little-secret.html
> And as for this non-college bullshit I got two words for that: learn to fuckin' type.
> Practice like this: Fast, Slow, Medium. Fast, Slow, Medium. Over and over...You want your fingers to know what it feels like to be correct. Doesn't matter if it takes you 30 seconds per note. Just get it right.
> For starters, non-typists are almost invisible. They don't leave a footprint in our online community...design involves communicating with other people, and design involves a persistent record of the decision tree.
