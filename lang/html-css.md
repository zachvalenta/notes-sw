# ⛩️

## 参考

🗄
* `infra.com` hosting
* `js.md` browser
* `python.md` HTML

## 进步

* consolidate Zola notes
* try Markdoc

---

fonts, css, images https://github.com/yorickpeterse/yorickpeterse.com/blob/main/source/fonts/icons.woff2

* _Zola_: 🎯 no assumptions regarding the structure of your site

ZOLA 📜 https://github.com/getzola/zola
* requirements: hot reload, 
* example https://github.com/ChevyRay/chevyray.dev
* themes https://www.getzola.org/themes/zola-easydocs-theme/ https://www.getzola.org/themes/dinkleberg/ https://www.getzola.org/themes/hook/ https://www.getzola.org/themes/zola-386/
* used by https://haskellbook.com/

* https://chevyray.dev/ask/ https://chat.openai.com/c/25d8a905-4ff4-4905-b63f-126f60ec9c75

* rf blog/design/features
> topics should go as drafts for site
* try Zola
* learn CSS for site redesign https://web.dev/learn/css/ https://wizardzines.com/zines/css/

* _24_: big rf
* _22_: rf fs, try Pelican, redesign
* _20_: MkDocs
* _19_: water.css
* _17_: CSS selectors for UI testing
* _15_: struggle with positioning and assume I'll never be a developer

# 🖼️ CSS

🔍 https://css-tricks.com/guides/ https://cssreference.io/ https://web.dev/learn/css/
📚
* Evans hell yes https://wizardzines.com/zines/css/
* Meyer https://www.amazon.com/CSS-Definitive-Guide-Layout-Presentation/dp/1098117611

> I don’t personally use Macs but I think everyone in B2C software needs to take lessons from Apple and the Mac community. They have proven, again and again, that people will pay a premium for products which are attractive. Often in B2C the first glimpse of the software makes the sale and everything after that is just justifying to the customer that their gut decision was the right one. https://www.kalzumeus.com/2009/03/07/how-to-successfully-compete-with-open-source-software/

HOWTO
* dark mode https://tinyprojects.dev/ https://www.youtube.com/watch?v=jmepqJ5UbuM
* link stylesheet `<link rel="stylesheet" style="text/css" href="../CSS/file.css">` https://stackoverflow.com/a/43947639
* charts https://chartscss.org/ https://uglyduck.ca/flexbox-bar-graphs/
* checklist https://drewdevault.com/new-server
* columns https://www.youtube.com/watch?v=hiIlFz8UN8Q
* dropdown https://uglyduck.ca/stripe-menu-css/
* tables https://uglyduck.ca/responsive-tables/

TAILWIND
* downsides: the sites all look the same, CDN not recommended, assumes you're using npx and postcss
* https://www.youtube.com/watch?v=21HuwjmuS7A
* https://builtwithtailwind.com/
* https://jvns.ca/blog/2018/11/01/tailwind--write-css-without-the-css/
* https://github.com/dohliam/dropin-minimal-css
* https://news.ycombinator.com/item?id=23270581
* alternatives: https://news.ycombinator.com/item?id=35709494 water.css https://watercss.netlify.com/ https://github.com/kognise/water.css/issues/160 Pure https://github.com/pure-css/pure/ https://newcss.net/ https://bulma.io/ https://simplecss.org/ https://css.winterveil.net/

---

https://cssfordesigners.com/articles/things-i-wish-id-known-about-css 
https://moderncss.dev/12-modern-css-one-line-upgrades/
* aria-current https://www.erichgrunewald.com/start-here/ https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-current
* aspect-ratio https://news.ycombinator.com/item?id=30280210&utm_term=comment
* blocks https://thesephist.github.io/blocks.css/
* _animation_: https://animejs.com/ https://fluca1978.github.io/2020/01/30/PostgreSQL_pgcatcheck.html https://www.youtube.com/watch?v=0-DY8J_skZ0 https://roughnotation.com/ https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://github.com/greensock/GSAP hover https://bsago.me/blog https://animejs.com/ https://sobolevn.me/2020/06/how-async-should-have-been https://github.com/jh3y/whirl/tree/dist

* _SASS_: features not in CSS; transpiles to CSS https://sass-lang.com/guide/

* _CSS-in-JS_: exactly what it sounds like; more composable, apparently https://frontarm.com/james-k-nelson/css-in-js-static-rendering/
* _debug_: https://github.com/lucagez/Debucsser https://www.youtube.com/watch?v=Sp9ZfSvpf7A
* _feature detection_: `@supports` https://www.youtube.com/watch?v=QG8Zv_doPOM 4:45
* _history_: https://www.w3.org/Style/CSS20/history.html https://eev.ee/blog/2020/02/01/old-css-new-css/ https://news.ycombinator.com/item?id=23915263
* _image_: trim off part to create polygon `clip-path` [6:00] masks [7:00] https://www.youtube.com/watch?v=QG8Zv_doPOM lazy loading https://victorzhou.com/blog/lazy-loading-images/
* _length values_: rem (calculated against root el) https://css-tricks.com/the-lengths-of-css/
* _methodologies_: BEM http://getbem.com/ Atomic https://acss.io/
* _testing_: https://about.gitlab.com/2019/03/13/quantifying-ux-validating-the-redesign-of-gitlabs-settings-pages/
* _usage_: linked stylesheet, `<style>`, inline

* _block_: takes 100% of available width by default

* snippets
```css
el {
    text-align: center;  /* text - center in div https://stackoverflow.com/a/10853894/6813490 */
    text-decoration: none;  /* link - rm underline */
    list-style-type: none;  /* no style --> extra styling https://www.youtube.com/watch?v=2awepiNoaZI */
}
```

VARIABLES
* aka 'custom properties' https://developer.mozilla.org/en-US/docs/Web/CSS/--*
* https://www.youtube.com/watch?v=lgaxU7CRmxU
* how to https://uglyduck.ca/css-variables/ https://www.youtube.com/playlist?list=PL4cUxeGkcC9ii5PB2UMyYH7QFZWfGnVgZ
```css
:root {
    --base-color: #e0e0e0;
}

.header {
    border: 1px solid var(--base-color);
}
```

## layout

---

📜 https://gridbyexample.com/ https://every-layout.dev/ https://css-tricks.com/guides/layout/ https://github.com/phuoc-ng/csslayout https://github.com/f-prime/Blunt https://web.dev/one-line-layouts/ https://news.ycombinator.com/item?id=24818485
> * Pure https://github.com/pure-css/pure/
https://chriscoyier.net/2022/12/21/things-css-could-still-use-heading-into-2023/

* _requirements_: full screen on mobile, centered on web cf. Dan Luu
```css
body {
    /* https://jrl.ninja/etc/1/ */
    max-width: 38rem;
    padding: 2rem;
    margin: auto;
}
```

* _flexible_: squish to fit
* _responsive_: stack https://css-tricks.com/snippets/css/css-grid-starter-layouts/ https://www.freecodecamp.org/news/responsive-web-design-how-to-make-a-website-look-good-on-phones-and-tablets/
* _Flexbox_: 1 dimension
* _grid_: 2 dimensions https://www.youtube.com/playlist?list=PL4cUxeGkcC9hH1tAjyUPZPjbj-7s200a4 https://github.com/iamshaunjp/css-grid-playlist https://css-tricks.com/snippets/css/complete-guide-grid/ https://testdriven.io/blog/css-grid/

display
* _static_: default
* _relative_: ability to be positioned relative to its own place (were it static) and for other other elements to be positioned relative to it
* _absolute_: positioned to nearest relative parent (or <html>), removed from flow of elements
* _fixed_: removed from flow of elements, positioned to viewport (which doesn’t change as page scrolls i.e. doesn’t change as move through the body)

* align=center https://github.blog/2020-04-09-github-protips-tips-tricks-hacks-and-secrets-from-lee-reilly/
* sticky https://btxx.org/posts/Please_Make_Your_Table_Headings_Sticky/

* snippets
```css
/* center horizontally https://github.com/iamshaunjp/css-grid-playlist/blob/lesson-2/index.html */
margin: 0 auto;

/* align el https://stackoverflow.com/a/8577183/6813490 */
input {
    display: inline-block;
}

grid {
    display: grid;
}
```

## selectors

semantics
* _selector_: syntax for describing set of elements
* _descendent_: nested anywhere inside parent; `div div.descendent`
* _child_: nested directly inside parent; `div > div.child`

pseudo
* _pseudo-selector_: selector preceded w/ colon https://css-tricks.com/pseudo-class-selectors/ e.g. target https://css-tricks.com/a-whole-website-in-a-single-html-file/
* _pseudo-class_: select existing element based on state of DOM e.g. `:hover`
* _pseudo-element_: allow styling certain part of an element e.g. `:first-letter`

howto
* test css selector in dev tools: `$$('<urSelectorHere>')`
* _adjacent_: next to; `div + div.adjacent`
* _starts with_: `[attr^="tocolor-"]` https://stackoverflow.com/a/5110337/6813490
* _contains_: `[attr*="tocolor-"]`
* _multiple classes_: `foo.bar` https://css-tricks.com/multiple-class-id-selectors/
* _element type + class_: `div.select2-container`
* _element type + attr_: `div[data-name='team_name’]`

## typography

📙 https://practicaltypography.com/

SEMANTICS
* _type_: font + layout
* _font_: set of textual glyphs
* just a `.tff` file https://practicaltypography.com/font-basics.html
* _glyph_: single shape https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html
* synonym for icon https://www.nerdfonts.com/
* packaged w/ font https://the.exa.website/features/icons
* _emphasis_: bold, italics

TOOLS
* https://github.com/googlefonts/fontations
* _fnt_: manager https://github.com/alexmyczko/fnt
* Pollen https://docs.racket-lang.org/pollen/ https://news.ycombinator.com/item?id=20029372
* TeX https://news.ycombinator.com/item?id=20027807 https://news.ycombinator.com/item?id=7823337 https://news.ycombinator.com/item?id=7822057 https://news.ycombinator.com/item?id=20027116
* BYO https://news.ycombinator.com/item?id=38421452

LAYOUT
* _line spacing_: 130% point size
* _line length_: 80 char https://practicaltypography.com/typography-in-ten-minutes.html http://www.designishistory.com/1920/jan-tschichold/
* sidenote: https://goodwill.awardwinninghuman.com/ https://www.w3.org/Style/CSS20/history.html https://pomb.us/build-your-own-react/ https://bsago.me/posts/waltzing-with-wireshark https://www.micahlerner.com/2021/05/23/reflecting-on-2020.html https://github.com/mlerner/mlerner.github.io/blob/master/_plugins/sidenote.rb
* https://practicaltypography.com/type-composition.html
* https://practicaltypography.com/text-formatting.html
* https://practicaltypography.com/page-layout.html
* https://typographyforlawyers.com/page-layout.html
* https://practicaltypography.com/sample-documents.html
* https://typographyforlawyers.com/sample-documents.html

FONTS IN USE
* Brave: Times (serif) Helvetica (sans) Courier (monospace)
* iTerm: Fira Mono regular (me) Monaco (default); Vim inherits https://stackoverflow.com/a/63647904
* site: https://rhodesmill.org/brandon/ https://fonts.google.com/specimen/Prociono https://www.theleagueofmoveabletype.com/prociono
* VS Code: Menlo
> tried Fira Sans but couldn't get Markdown tables to line up
> line length was much lower in VS Code, don't understand why this would change

FONTS https://www.nerdfonts.com/
* taxonomy http://www.designishistory.com/1450/type-classification/
* recs https://practicaltypography.com/font-recommendations.html https://practicaltypography.com/free-fonts.html
* _Alegreya_: https://cotonoha.io/en.html
* _Berkley mono_: Capp https://berkeleygraphics.com/typefaces/
* _Clarendon_: used for newspaper in the 19th century https://www.typotheque.com/articles/brief_history_of_webfonts
* _Comic Mono_: https://dtinth.github.io/comic-mono-font/
* _Computer Modern_: Donald Knuth https://czep.net/about/
* _Concourse_: popular w/ software people https://practicaltypography.com/concourse.html https://wsvincent.com/site-design/ https://danielmiessler.com/colophon/
* _Departure Mono_: https://news.ycombinator.com/item?id=41379985
* _Editor_: https://www.worksinprogress.co/issue/why-didnt-suicides-rise-during-covid/
* _Fira Code_: ligature crazy spin-off of Fira Mono https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html
* _Fira Mono_: ✅ monospaced https://practicaltypography.com/courier-alternatives.html
* _Hack_: ✅ https://github.com/source-foundry/Hack 
* _Litera_: https://quarchive.com/getting-started
* _London TFL_: https://github.com/petykowski/London-Underground-Dot-Matrix-Typeface
* _Recursive_: warm https://github.com/arrowtype/recursive/
* _Routed gothic_: https://webonastick.com/fonts/routed-gothic/
* _Signifier_: https://klim.co.nz/retail-fonts/signifier/

DESIGN
* it goes deep https://news.ycombinator.com/item?id=24631681
* differentiate btw 0 and O https://news.ycombinator.com/item?id=27066965
* color https://news.ycombinator.com/item?id=24303042
* _point size_: 20 pixels for web
* _weight_: width https://en.wikipedia.org/wiki/Font#Weight
* _book weight_: regular https://news.ycombinator.com/item?id=30400828
* _monospace_: equal space btw char http://www.ii.com/vim-unicode-digraphs/ https://news.ycombinator.com/item?id=33498799
* doesn't support italics https://www.reddit.com/r/neovim/comments/zan566/comment/iymtd9p/
* for software dev bc alignment https://stackoverflow.com/a/218639
* _ligature_: combine n characters into 1 e.g. `!=`
* _proportional_: diff space btw char
* for prose https://stackoverflow.com/a/218749
* aka variable https://www.recursive.design/

SYSTEM VS. WEB
* _system font_: stored locally https://practicaltypography.com/system-fonts.html 📍 https://news.ycombinator.com/item?id=31543054
* aka desktop font https://meta.stackexchange.com/questions/364048/we-are-switching-to-system-fonts-on-may-10-2021
* macOS install: double click on font file, click installer (fs location `$HOME/Library/Fonts`)
* manage w/ Font Book
* use font editor https://github.com/fontforge/fontforge
* _OpenType_: fmt for desktop font https://en.wikipedia.org/wiki/OpenType https://github.com/arrowtype/recursive/
> ❓ what prevents people from grabbing font files from browser/repos?
* webpages use to rely on desktop fonts https://www.typotheque.com/articles/brief_history_of_webfonts
> There was, however, a catch: while images could be loaded to webpages from remote servers, fonts could be loaded only from the client's computer...font foundries were reluctant to expose their products to piracy, so font licenses generally prevented webpage owners from using the fonts online.
* _web font_: hosted online
* e.g. Google Fonts, Adobe TypeKit https://fonts.google.com/
* user can set font from browser to override site https://news.ycombinator.com/item?id=27068036 https://news.ycombinator.com/item?id=27065041
* perf https://iainbean.com/posts/2021/5-steps-to-faster-web-fonts/
* _font-face_: w/out this you have to rely on system font https://css-tricks.com/snippets/css/using-font-face-in-css/
```css
/* https://stackoverflow.com/a/3245187 */
@font-face {
    font-family: fira-mono;
    src: url("fira-mono.otf") format("opentype");
}
@font-face {
    font-family: fira-mono-bold;
    src: url("fira-mono-bold.otf") format("opentype");
}
body {
  font-family: fira-mono, fallback;
}

<style>
    @font-face {
    font-family: "elevate-display-font";
    font-weight: 500;
    font-style: normal;
    src: url("https://maddo.xxx/assets/fonts/heldane-500-normal-latin.woff2")
        format("woff2"),
        url("https://maddo.xxx/assets/fonts/heldane-500-normal-latin.woff")
        format("woff");
    unicode-range: U+0-7F, U+A0, U+200A, U+2014, U+2018, U+2019, U+201C,
        U+201D, U+2022, U+2026;
    }
</style>
```

FILE FMT https://practicaltypography.com/triplicate.html
* _OTF_: macOS
* can use on web, convert to WOFF https://stackoverflow.com/a/3245187
* _TTF_: Windows
* for web https://stackoverflow.com/a/24990647
* _WOFF_: websites https://practicaltypography.com/concourse.html
* load faster https://css-tricks.com/snippets/css/using-font-face-in-css/#aa-woff-woff2
* created so that people could sell fonts i.e has way to embed license info https://developer.mozilla.org/en-US/docs/Web/Guide/WOFF
> The WOFF format was initially created as a reaction to OTF and TTF, in part, because these formats could easily (and illegally) be copied.

# 📑 SITES

## blog

> There are a surprising number of things that are underserved by other writers online (who would have thought!) https://entropicthoughts.com/two-wrongs-is-now-entropic-thoughts

* book of lyrics for Luambo, Rochereau, Mulatu, Francis Bebey, Cesaria Evora, Amalia Rodrigues
* history of thought https://www.amazon.com/Ideas-History-Thought-Invention-Freud/dp/0060935642 https://www.amazon.com/Ideas-History-Thought-Invention-Freud/dp/0060935642 https://www.amazon.com/Brief-History-Thought-Philosophical-Learning/dp/0062074245 https://www.amazon.com/History-Knowledge-Past-Present-Future/dp/0345373162

DEV JOURNAL
* https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/

HOW I CODE
* profiling
* test
* docs
* API
* paradigms
* servers
* monitoring / metrics
* tracing
* analytics

HOW THINGS WORK
* where movies shoot https://www.theringer.com/2024/8/21/24225522/the-arms-race-behind-where-movies-shoot
* sports betting https://archive.vn/rfPo4 https://www.theringer.com/2024/8/5/24213559/the-state-of-sports-gambling-with-todd-fuhrman https://archive.vn/lZw1l

## design

---

📙 https://www.refactoringui.com/

https://govukvue.org/

COLOR
* https://anthonyhobday.com/sideprojects/saferules/
* variables, currentColor, preprocessor https://css-tricks.com/nerds-guide-color-web/
* _HSL_: https://designsystem.digital.gov/design-tokens/color/overview/
* _hex_: https://css-tricks.com/nerds-guide-color-web/
* _named_: https://css-tricks.com/nerds-guide-color-web/

INSPIRATION 🗄️ `sw/lang/html-css/design` https://shreyans.org/ 
* https://www.ntietz.com/
* https://allaboutberlin.com/
* https://jamesg.blog/2024/08/16/content-layout-design/
* https://lock.cmpxchg8b.com/watch.html
* https://borretti.me/
* https://maxlangenkamp.me/
* https://anthonyhobday.com/sideprojects/saferules/
* https://github.com/asnewman/asnewman.github.io
* https://news.ycombinator.com/item?id=36745314
* https://yossarian.net/
* https://vitalik.eth.limo/general/2023/11/27/techno_optimism.html
* https://spwhitton.name/
* https://sriramk.com/building-unmeasurable-things/

## features

* _comment engine_: https://github.com/umputun/remark42 or just use a repo https://lists.sr.ht/~skeeto
* _link checker_: https://bernard.app/
* _TOC_: https://www.murilopereira.com/how-to-open-a-file-in-emacs

---

webring https://en.wikipedia.org/wiki/IndieWeb https://xn--sr8hvo.ws/ https://www.jvt.me/
webmentions https://indieweb.org/static_site

blogroll https://claytonerrington.com/

https://yorickpeterse.com/resume/

https://linkpreview.xyz/

pictures https://mazzo.li/posts/fast-pipes.html#fn1

https://news.ycombinator.com/item?id=39511714
https://danilafe.com/blog/blog_microfeatures/
https://kylascanlon.com/
who i am https://www.youtube.com/watch?v=5WLlLxU2EZE

CONTENT
* main
* blog
* book reviews
* music reviews
* idea glossary
* za: cv, phone screen, quotes

MAIN PAGE
- [ ] audio https://mally.stanford.edu/index.html
- [ ] hand-written note http://worrydream.com/July2023/

POSTS
- [ ] header/footer: https://www.erichgrunewald.com/ https://bastian.rieck.me/outreach/ https://fabiensanglard.net/
- [ ] toc: https://adtax.paulromer.net/ https://www.goatcounter.com/help/start
- [ ] sidebar: https://www.arp242.net/ https://github.com/arp242/arp242.net gifs https://adamj.eu/contact/ sticky https://litchipi.github.io/infosec/2023/01/24/git-code-audit-viewed-as-rust-programmer.html
- [ ] layout https://macwright.com/2016/12/28/what-little-i-know-about-design.html https://borretti.me/article/languages-not-ecosystems https://github.com/arp242/hello-css/
- [ ] footnotes: https://stackoverflow.com/a/29384216/6813490 https://twobithistory.org/2018/08/18/ada-lovelace-note-g.html

STYLING
- [ ] highlight on hover: https://man7.org/linux/man-pages/dir_by_project.html#man-pages--man7 
- [ ] highlight on selection: `::selection` https://css-tricks.com/overriding-the-default-text-selection-color-with-css/
- [ ] images: https://fabiensanglard.net/sf2_health_bar/index.html David Byrne book 🗄 `aesthetics.md` history

USABILITY
- [ ] perf https://developers.google.com/speed/pagespeed/insights/ https://webhint.io https://www.webpagetest.org/ https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-performance https://github.com/theodo/falco https://1mb.club/
- [ ] analytics: `robots.txt` https://will-keleher.com/about.html
- [ ] comments: HN, MR https://www.jefftk.com/p/designing-low-upkeep-software Discord, Github https://github.com/jameslittle230/stork/discussions
> Folks wanted to talk about stuff where they already were, rather than centralizing that conversation on individual blogs. https://news.ycombinator.com/item?id=30853711
- [ ] email: https://www.benkuhn.net/ https://lchsk.com/ Buttondown https://www.erichgrunewald.com/start-here/ https://news.ycombinator.com/item?id=34906476 https://computer.rip/2024-07-13-the-contemporary-carphone.html
> I sincerely apologize for the hCaptcha but some dumb credential stuffer has been shoveling emails into this form. Then people hit the spam report button on the confirmation emails and my gateway provider gets upset with me for harming their IP reputation. This is why we can't have nice things.
> You've been sent a verification email with a link that you need to click, because that's how this always works. Check your inbox for a message from me@computer.rip. If you still haven't received it after an appropriate seeming amount of time, cross your fingers and try again, or maybe this thing broke and you should let me know at me@computer.rip.
> Hello, and welcome to the elite circle of subscribers to *Computers Are Bad*. For reasons you can probably imagine, I have to confirm that you actually intend to subscribe to this list and are not yet another victim of low-level identity theft at the Harbor Freight checkout counter. To confirm your subscription, use this link:
> In the future, you will be permitted (but not encouraged) to unsubscribe using a link at the end of each message. In the rare case that you experience lingering doubts, fears, or anxieties, you will find that this mailbox *is* monitored for replies.
> Congratulations, you are now on the list. Look out for an email sometime in the indefinite future.
- [ ] search
- [ ] RSS: https://github.com/jeffkaufman/webscripts/blob/e7261e894cee12df6b1f0a90d426764a802691dd/reverserss.py#L20
- [ ] tags

## HTML

🗄 `stdlib.com` UI / IO (rich)
📜 https://htmlreference.io/

---

* _PWA (progressive enhancement)_: https://technology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/ https://www.youtube.com/playlist?list=PL4cUxeGkcC9gTxqJBcDmoi5Q2pzDusSL7
* _semantic web_: element describes content e.g. `<footer>` `<section>` https://twobithistory.org/2018/06/10/birth-of-the-web.html#fnref:11 https://twobithistory.org/2018/05/27/semantic-web.html https://news.ycombinator.com/item?id=30166788 https://news.ycombinator.com/item?id=41307011
* _UI_: elements https://codepen.io/topics/ is hard https://overreacted.io/the-elements-of-ui-engineering/
* _validation_: `<input maxlength= "15" type="url" regex="<regex>" required>` must be of type url, must input something and match regex, limit 15 chars
* _W3C_: https://24ways.org/2018/researching-a-property-in-the-css-specifications/

* _attribute_: metadata
* _canvas_: draw, make charts
* auto reload: `<meta http-equiv="refresh" content="3">`
* head: https://www.matuzo.at/blog/html-boilerplate/

howto
* link - use button https://stackoverflow.com/a/2906586/6813490
* link - preload: `<link rel="preload">` = "go fetch this heavy resource before you (browser) get busy rendering"; perf thing
* image - Youtube preview thumbnail: https://stackoverflow.com/a/18681824/6813490
* dropdown/collapsible https://news.ycombinator.com/item?id=29669812 🗄 `personal-site` nested

FORMS
```html
<form method="post">
    <input type="text">
</form>
```
* using Markdown https://news.ycombinator.com/item?id=41407993
* dates https://uglyduck.ca/basic-form-styling/
* `action`: URL to send data
* `enctype`: HTML parlance for media type for forms https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/enctype 🗄 `4-application.md`
* `method`: HTTP verb https://stackoverflow.com/questions/8395269-->
* `role`: accessibility thing https://stackoverflow.com/a/18664038/6813490
* `type`: text, file, submit; submit is only useful for input elements (button el default to submit anyway https://stackoverflow.com/a/10079197/6813490)
* encrypt/password protect HTML https://github.com/robinmoisson/staticrypt
* EME encrypted media extensions https://stackoverflow.com/questions/46212264/example-encrypted-media-extensions-encryption/46374671#46374671
* email is hard https://news.ycombinator.com/item?id=41007403

## Markdown

🔗 https://www.markdownguide.org/

FLAVORS
* _CommonMark_: https://meta.stackexchange.com/q/348746
* _GFM_: https://github.com/github/markup/issues/498#issuecomment-158257453 
* _MyST_: https://github.com/executablebooks/MyST-Parser

PARSERS
* _MDX_: jsx in markdown (for tables, charting) by transpiling Markdown to JS via JS runtime (e.g. React) and then running in the browser https://github.com/mdx-js/mdx/ https://signalsandthreads.com/writing-technically/
* _markdown-it-py_: https://github.com/executablebooks/markdown-it-py https://pythonbytes.fm/episodes/show/320/the-bug-is-in-the-javascript
* _commonmark_: https://github.com/readthedocs/commonmark.py https://github.com/Textualize/rich/pull/2439/files
* _goldmark_: https://github.com/yuin/goldmark
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown

RENDER
* mdcat https://github.com/swsnr/mdcat
* rich https://rich.readthedocs.io/en/latest/markdown.html
* https://github.com/Textualize/frogmouth
* glow https://github.com/charmbracelet/bubbletea

EDITOR
* https://simplemde.com/ https://tunalog.org/en-us/index.html

---

* use image (w/ Github renderer) https://github.com/catppuccin/python/blob/main/README.md
* current approach https://github.com/zachvalenta/markdown-2-html
```log
.rwxr-xr-x@ 2.0k zach 21 Dec 17:19 -- jb*
lrwxr-xr-x    69 zach  7 Oct  2019 -- m2h -> /Users/zach/Desktop/zvmac/materials/sw/lang/html-css/m2h/converter.py
```

* links https://jordanelver.co.uk/blog/2021/03/13/til-about-markdown-reference-style-links/
* convert to HTML with Vim http://vimcasts.org/episodes/converting-markdown-to-structured-html-with-a-macro/
* Github https://docs.github.com/en/issues/tracking-your-work-with-issues/about-slash-commands
* RENDERME https://news.ycombinator.com/item?id=30336703
* metadata https://github.com/blacksmithgu/obsidian-dataview
* spec https://github.blog/2017-03-14-a-formal-spec-for-github-markdown/
* asciidoc vs. Markdown https://news.ycombinator.com/item?id=27744509
* href https://github.com/pemistahl/grex
* linting https://mkaz.blog/code/linting-markdown-syntax/
* Latex http://www.danielallington.net/2016/09/the-latex-fetish/ https://increment.com/open-source/the-lingua-franca-of-latex/ alternative https://sile-typesetter.org/ https://news.ycombinator.com/item?id=35242299 https://news.ycombinator.com/item?id=35250210 Typst https://www.youtube.com/watch?v=sWmlbMh3ol8
* formal spec https://githubengineering.com/a-formal-spec-for-github-markdown/
* code syntax support https://github.com/github/linguist/blob/master/lib/linguist/languages.yml
* Pandoc has their own version of Markdown? https://yihui.name/en/2018/09/target-blank/
* Markdown to PowerPoint https://yhatt.github.io/marp https://www.youtube.com/watch?v=CkIweDviGH8
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown
* [dropdowns!](https://raw.githubusercontent.com/30-seconds/30-seconds-of-code/master/README.md)
* [diff](https://stackoverflow.com/a/40883538)
* table fmt: Jira, Markdown/RST, Latex https://jsvine.github.io/intro-to-visidata/basics/saving-sheets/
* Markdown for Google Docs https://www.theverge.com/2022/3/29/23002138/google-docs-markdown-support-formatting-update

conversion to HTML
* https://github.com/susam/texme
* Markdown to HTML w/ Python CLI https://python-markdown.github.io/cli/ `python -m markdown 1997-graham-hackers-painters.md > pg.html` -> doesn't handle quotes, output is vanilla would need to figure way to add CSS
* _mistune_: https://github.com/lepture/mistune
* _markdown_: `python -m markdown rn.md > rn.html` https://python-markdown.github.io/cli/ used in MkDocs https://github.com/mkdocs/mkdocs/blob/master/requirements/project.txt
* _markdown2_: https://github.com/trentm/python-markdown2 supports (maybe) ghfm https://github.com/mkdocs/mkdocs/issues/263#issuecomment-65362418
```sh
python -m markdown2 --extras fenced-code-blocks my-debug-checklist.md > debug.html
```

add styles
* `water.css` w/ Beatiful Soup in script https://stackoverflow.com/a/19123463/6813490 
* more advanced https://github.com/cburmeister/cburmeister.github.io/blob/master/Makefile pandoc https://serverless.pub/lambda-utility-layers/ https://github.com/kickstartcoding/cheatsheets

## static site (SSG)

FEATURES
> https://twitter.com/danluu/status/1244051446313574402 https://meridian.mercury.com/dwarkesh-patel
* template engine: Jinja, Tera https://www.getzola.org/documentation/getting-started/overview/#first-steps-with-zola
* search: Stork https://stork-search.net/ TinySearch https://github.com/tinysearch/tinysearch https://news.ycombinator.com/item?id=23474134 DDG https://vadosware.io/ https://ddg.patdryburgh.com/ lunr.js https://github.com/olivernn/lunr.js https://brainbaking.com/search/?q=database example https://clearerthinkingpodcast.com/#episodes
* RSS generation
* tags: https://github.com/erwald/blog/blob/master/_data/series.json https://www.erichgrunewald.com/posts/the-kingdom-of-tamego/ https://github.com/jeffkaufman/webscripts/blob/e1c8a399536bb92e3f09886eea9fb925e710c981/intros.json https://www.jefftk.com/news/money
* _metadata_: title/desc, date, tags https://www.janmeppe.com/blog/I-dont-like-my-blog-anymore/
* _HTML preprocessor_: turn Markdown in HTML e.g. Nunjucks https://css-tricks.com/killer-features-of-nunjucks/ https://github.com/erwald/blog
```sh
# https://fvsch.com/static-site-generators
├── content
│   ├── 2018-09-07-cool-blog-post.txt
│   └── 2018-10-01-other-blog-post.txt
└── output
    ├── cool-blog-post.html
    ├── index.html
    ├── other-blog-post.html
    └── rss.xml
```

SSGs
* BYO https://www.youtube.com/watch?v=Ph7oJDR71Jc https://github.com/mitsuhiko/rstblog https://til.simonwillison.net/django/building-a-blog-in-django dynamic https://realpython.com/build-a-blog-from-scratch-django/ https://dev.to/chasefleming/building-a-go-static-site-generator-using-elem-go-3fhh
* me: run m2h, move all html from content to src, open any html files from src with modified Git status
* https://fabiensanglard.net/html/index.html
* _Astro micro_: 🎯 https://drew.silcock.dev/about/ https://github.com/drewsilcock/silcock-dev https://astro.build/themes/details/astro-micro/ https://astro-nano-demo.vercel.app/ https://www.bytedrum.com/about/
* _aurora_: 🎯 https://github.com/capjamesg/aurora
* _Bearclaw_: https://github.com/donuts-are-good/bearclaw
* _Eleventy_: https://www.11ty.dev/ https://www.erichgrunewald.com/ https://news.ycombinator.com/item?id=31293971 https://angeliqueweger.com/
* _Lanyon_: server, same guy that did termgraph https://github.com/mkaz/lanyon
* _Hugo_: https://www.peterbaumgartner.com popular https://blog.golang.org/8years bad docs https://yawpitchroll.com/posts/hugo-probably-is-not-for-you/ https://twitter.com/danluu/status/1244024025019342851
* _Lektor_: Python https://www.getlektor.com/ https://lucumr.pocoo.org/2015/12/21/introducing-lektor/
* _Lume_: https://lume.land/
* _Makesite_: 🎯 https://github.com/sunainapai/makesite
* _Markata_: Python https://github.com/WaylonWalker/markata
* _Markdoc_: 🎯 https://markdoc.dev/ https://steinkamp.us/posts/2022-11-10-what-i-learned-at-stripe
* _Metalsmith_: Javascript https://github.com/metalsmith/metalsmith
* _Nikola_: https://getnikola.com/ not a blog https://getnikola.com/creating-a-site-not-a-blog-with-nikola.html
* _Pelican_: 🎯 no TOC, blog-oriented https://pirsquared.org/blog/pelican-transition.html https://pirsquared.org/blog/pelican-tags-vs-categories.html
* _Shite_: Bash https://github.com/adityaathalye/shite

CMS
* _website builder_: optimized for non-dev e.g. Wix, SquareSpace https://news.ycombinator.com/item?id=41337356
* _CMS_: client-server, content creation via UI, requires some dev e.g. Wordpress https://kevq.uk/the-case-for-wordpress https://blot.im/how https://bearblog.dev/ https://tunalog.org/en-us/index.html
* _headless CMS_: SPA gets content via API https://softwareengineeringdaily.com/2020/04/30/jamstack-content-management-with-scott-gallant-jordan-patterson-and-nolan-phillips/
* Ghost: hosting, newsletters, Stripe, membership https://softwareengineeringdaily.com/2018/07/26/ghost-open-source-publishing-platform-with-john-onolan/
* Netlify, Wagtail, Django, Perch
