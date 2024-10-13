# ⛩️

## 参考

## 进步

DEPLOYMENT
* DNS tools to diff `zachvalenta.com` vs. `zjayv.com`
* learn Github actions
* specify `index.html` for GH Pages: `publish_dir` https://chatgpt.com/share/66f4a7c1-ea3c-8004-8327-46a9840bf1d5 https://github.com/shalzz/zola-deploy-action/blob/master/README.md#custom-domain symlink to `templates/index.html`? https://chevyray.dev/blog/how-this-site-is-made/#deploying https://stackoverflow.com/questions/42941170/how-to-set-up-github-pages-to-look-for-index-html-in-a-different-location https://stackoverflow.com/questions/25320356/can-i-have-my-github-pages-index-html-in-a-subfolder-of-the-repository or Cloudflare https://chevyray.dev/blog/how-this-site-is-made/ or Netlify https://www.netlify.com/blog/2021/12/20/how-to-add-custom-domains-to-netlify-sites/

NEXT https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* tags
* RSS
* search
* styling from https://chevyray.dev/blog/test-post/
* template inheritance
* SSoT for book notes
> complication: some things you don't want to publish e.g. Austen notes

* _24_: big rf, port site to Zola and rm old dirs for content/drafts
* _22_: rf fs, try Pelican, redesign
* _20_: MkDocs
* _19_: water.css
* _17_: CSS selectors for UI testing
* _15_: struggle with positioning and assume I'll never be a developer

# 📚 LANGUAGES

🗄 `js.md` browser

## CSS

🗄️
* `education.md` design
* `viz.md` art
🔍 
* https://css-tricks.com/guides/
* https://cssreference.io/ 
* https://web.dev/learn/css/
📚
* Evans hell yes https://wizardzines.com/zines/css/
* Meyer https://www.amazon.com/CSS-Definitive-Guide-Layout-Presentation/dp/1098117611
* https://macwright.com/2016/12/28/what-little-i-know-about-design.html
* https://cssfordesigners.com/articles/things-i-wish-id-known-about-css 

HOWTO
* hover animation https://bsago.me/blog
* inspect https://www.youtube.com/watch?v=Sp9ZfSvpf7A
* charts https://chartscss.org/ https://uglyduck.ca/flexbox-bar-graphs/
* dark mode https://tinyprojects.dev/ https://www.youtube.com/watch?v=jmepqJ5UbuM
* tylesheet: inline, `<style>` `<link rel="stylesheet" style="text/css" href="../CSS/file.css">` https://stackoverflow.com/a/43947639

FRAMEWORKS
* minimal https://github.com/dohliam/dropin-minimal-css https://news.ycombinator.com/item?id=35709494
* BEM http://getbem.com/
* animation https://roughnotation.com/ https://animejs.com/ https://github.com/greensock/GSAP https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/
* _blocks_: https://thesephist.github.io/blocks.css/
* _Bulma_: https://bulma.io/ 
* _Magick_: sidenotes https://css.winterveil.net/
* _Pure_: 🎯 https://purecss.io/
* _Tailwind_: https://jvns.ca/blog/2018/11/01/tailwind--write-css-without-the-css/
* _water_: ✅ https://github.com/kognise/water.css https://github.com/kognise/water.css/issues/160 

LAYOUT
* patterns https://github.com/phuoc-ng/csslayout https://web.dev/one-line-layouts/ https://gridbyexample.com/ https://every-layout.dev/
* responsive https://www.freecodecamp.org/news/responsive-web-design-how-to-make-a-website-look-good-on-phones-and-tablets/
* sticky https://btxx.org/posts/Please_Make_Your_Table_Headings_Sticky/
* _Flexbox_: 1 dimension
* _grid_: 2 dimensions https://css-tricks.com/snippets/css/complete-guide-grid/
* _static_: default
* _relative_: ability to be positioned relative to its own place (were it static) and for other other elements to be positioned relative to it
* _absolute_: positioned to nearest relative parent (or <html>), removed from flow of elements
* _fixed_: removed from flow of elements, positioned to viewport (which doesn’t change as page scrolls i.e. doesn’t change as move through the body)
* snippets
```css
text-align: center;  /* text - center in div https://stackoverflow.com/a/10853894/6813490 */
text-decoration: none;  /* link - rm underline */
list-style-type: none;  /* no style --> extra styling https://www.youtube.com/watch?v=2awepiNoaZI */
/* center horizontally https://github.com/iamshaunjp/css-grid-playlist/blob/lesson-2/index.html */
margin: 0 auto;
/* align el https://stackoverflow.com/a/8577183/6813490 */
input { display: inline-block; }
grid { display: grid; }
}
```

SELECTORS
* starts with: `[attr^="tocolor-"]` https://stackoverflow.com/a/5110337/6813490
* contains: `[attr*="tocolor-"]`
* multiple classes: `foo.bar` https://css-tricks.com/multiple-class-id-selectors/
* element type + class: `div.select2-container`
* element type + attr: `div[data-name='team_name’]`
* test in dev tools: `$$('<urSelectorHere>')`
* _selector_: syntax for describing set of elements
* _descendent_: nested anywhere inside parent; `div div.descendent`
* _child_: nested directly inside parent; `div > div.child`
* _pseudo-selector_: selector preceded w/ colon https://css-tricks.com/pseudo-class-selectors/ e.g. target https://css-tricks.com/a-whole-website-in-a-single-html-file/
* _pseudo-class_: select existing element based on state of DOM e.g. `:hover`
* _pseudo-element_: allow styling certain part of an element e.g. `:first-letter`
* _adjacent_: next to; `div + div.adjacent`

ZA
* history: https://www.w3.org/Style/CSS20/history.html https://eev.ee/blog/2020/02/01/old-css-new-css/ https://news.ycombinator.com/item?id=23915263
* _SASS_: features not in CSS; transpiles to CSS https://sass-lang.com/guide/
* diff btw SCSS and SASS https://stackoverflow.com/questions/5654447/whats-the-difference-between-scss-and-sass/
* _variable_: aka 'custom properties' https://developer.mozilla.org/en-US/docs/Web/CSS/--*
```css
:root { --base-color: #e0e0e0; }
.header { border: 1px solid var(--base-color); }
```

## HTML

📜 https://htmlreference.io/
🗄 
* `stdlib.com` UI / IO (rich)
* `stdlib.com` HTML

HOWTO
* real-time editor https://github.com/urin/vscode-web-visual-editor
* footnotes https://stackoverflow.com/a/29384216/6813490 
* dropdown/collapsible https://news.ycombinator.com/item?id=29669812 🗄 `personal-site` nested
* link as button https://stackoverflow.com/q/2906582/6813490
* Youtube preview https://stackoverflow.com/a/18681824/6813490
* password protect a page https://github.com/robinmoisson/staticrypt
* understand `head` https://www.matuzo.at/blog/html-boilerplate/
* in email https://news.ycombinator.com/item?id=41007403
* archive: archive single page https://github.com/Y2Z/monolith https://github.com/gildas-lormeau/SingleFile whole site w/ wget https://stackoverflow.com/a/4769497 https://stackoverflow.com/a/10564190/6813490 https://news.ycombinator.com/item?id=16557439 every version of single page in Wayback Machine https://github.com/jsvine/waybackpack

SEMANTICS
* _attribute_: metadata
* _canvas_: draw, make charts
* _EME (encrypted media extensions)_: DRM https://stackoverflow.com/questions/46212264/example-encrypted-media-extensions-encryption/46374671#46374671
* _PWA (progressive enhancement)_: layering functionality i.e. site works fine using HTML but adds CSS and JS if user agent supports https://technology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/
* _semantic web_: element describes content e.g. `<footer>` `<section>` https://twobithistory.org/2018/06/10/birth-of-the-web.html#fnref:11 https://twobithistory.org/2018/05/27/semantic-web.html https://news.ycombinator.com/item?id=30166788 https://news.ycombinator.com/item?id=41307011 https://csvbase.com/blog/13

FORMS
```html
<form method="post">
    <input type="text">
</form>
```
* using Markdown https://news.ycombinator.com/item?id=41407993
* `action`: URL to send data
* `enctype`: HTML parlance for media type for forms https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/enctype 🗄 `4-application.md`
* `method`: HTTP verb https://stackoverflow.com/questions/8395269-->
* `role`: accessibility thing https://stackoverflow.com/a/18664038/6813490
* `type`: text, file, submit; submit is only useful for input elements (button el default to submit anyway https://stackoverflow.com/a/10079197/6813490)

## Markdown

🔗 https://www.markdownguide.org/

FLAVORS
* _Djot_: https://djot.net/ https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* _CommonMark_: https://meta.stackexchange.com/q/348746
* _GFM_: https://github.com/github/markup/issues/498#issuecomment-158257453 
* _MyST_: https://github.com/executablebooks/MyST-Parser

PARSERS
* _MDX_: jsx in markdown (for tables, charting) by transpiling Markdown to JS via JS runtime (e.g. React) and then running in the browser https://github.com/mdx-js/mdx/ https://signalsandthreads.com/writing-technically/
* time suck https://www.joshwcomeau.com/blog/how-i-built-my-blog-v2/
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

* vs. RST https://buttondown.com/hillelwayne/archive/why-i-prefer-rst-to-markdown/
* use image (w/ Github renderer) https://github.com/catppuccin/python/blob/main/README.md

* links https://jordanelver.co.uk/blog/2021/03/13/til-about-markdown-reference-style-links/
* convert to HTML with Vim http://vimcasts.org/episodes/converting-markdown-to-structured-html-with-a-macro/
* Github https://docs.github.com/en/issues/tracking-your-work-with-issues/about-slash-commands
* RENDERME https://news.ycombinator.com/item?id=30336703
* metadata https://github.com/blacksmithgu/obsidian-dataview
* spec https://github.blog/2017-03-14-a-formal-spec-for-github-markdown/
* asciidoc vs. Markdown https://news.ycombinator.com/item?id=27744509
* href https://github.com/pemistahl/grex
* linting https://mkaz.blog/code/linting-markdown-syntax/
* Latex http://www.danielallington.net/2016/09/the-latex-fetish/ https://increment.com/open-source/the-lingua-franca-of-latex/ alternative https://sile-typesetter.org/ https://news.ycombinator.com/item?id=35242299 https://news.ycombinator.com/item?id=35250210 Typst https://www.youtube.com/watch?v=sWmlbMh3ol8 Overleaf, Markdown https://brainbaking.com/post/2021/02/writing-academic-papers-in-markdown/
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

# 📑 SITE

🗄️ `infra.com` hosting

## content

---

https://kaiwenwang.com/stack
just a normal dev blog https://www.jonashietala.se/blog/tags/neovim/
https://gwern.net/matt-levine
https://gwern.net/book-writing

collections https://buttondown.com/hillelwayne/archive/in-defense-of/

CONTENT
* blog
* book reviews
* music reviews
* idea glossary
* za: cv, phone screen, quotes
* about: gifs https://adamj.eu/contact/

* CV https://yorickpeterse.com/resume/
* https://www.felixstocker.com/blog/geheimnisvoll

PROJECTS
* book of lyrics for Luambo, Rochereau, Mulatu, Francis Bebey, Cesaria Evora, Amalia Rodrigues
* history of thought https://www.amazon.com/Ideas-History-Thought-Invention-Freud/dp/0060935642 https://www.amazon.com/Ideas-History-Thought-Invention-Freud/dp/0060935642 https://www.amazon.com/Brief-History-Thought-Philosophical-Learning/dp/0062074245 https://www.amazon.com/History-Knowledge-Past-Present-Future/dp/0345373162

DEV JOURNAL
* https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/

HOW I CODE
> changing stuff and seeing what happens https://orlybooks.com/
* profiling
* test
* docs
* API
* paradigms
* servers
* monitoring / metrics
* tracing
* analytics

FAVORITES
* favorite software writing: Paul Ford what is code https://registerspill.thorstenball.com/p/joy-and-curiosity-8 https://www.youtube.com/watch?v=5WLlLxU2EZE
* blogroll https://claytonerrington.com/

HOW THINGS WORK
* movies https://www.theringer.com/2024/8/21/24225522/the-arms-race-behind-where-movies-shoot https://www.theringer.com/2024/9/23/24252627/biggest-takeaways-netflix-data-dump-2024-streaming https://www.theringer.com/2024/9/25/24253629/how-to-make-your-own-tv-show-and-get-netflix-to-buy-it-mark-duplass-penelope-netflix https://www.theringer.com/2024/9/30/24258856/how-should-movie-and-tv-stars-be-paid
* sports betting https://archive.vn/rfPo4 https://www.theringer.com/2024/8/5/24213559/the-state-of-sports-gambling-with-todd-fuhrman https://archive.vn/lZw1l

## design

🔗 https://github.com/zachvalenta/web-design
🇬🇧 UK design system https://govukvue.org/
🗄
* `viz.md`
* `sw/lang/html-css/design`
📝
* https://www.refactoringui.com/
* https://anthonyhobday.com/sideprojects/saferules/
* https://macwright.com/2016/12/28/what-little-i-know-about-design.html
* https://jamesg.blog/2024/08/16/content-layout-design/

MINIMAL 🔗 https://news.ycombinator.com/item?id=36745314
* https://news.ycombinator.com/login?goto=news
* https://himitsustore.org/
* https://stevenvanbael.com/
* https://maxlangenkamp.me/posts/tech_not_inevitable
* https://www.oilshell.org/
* https://yossarian.net/

UNIQUE
* https://shreyans.org/
* blocks https://www.ntietz.com/ https://thisisimportant.net/
* https://borretti.me/
* https://robinrendle.com/
* https://kaiwenwang.com/stack
* https://abundance.institute/

ZA
* squares https://allaboutberlin.com/
* single page https://run.jotaen.net/ https://omakub.org/

## features

LAYOUT 🔗  https://github.com/arp242/hello-css/
- [x] TOC https://www.murilopereira.com/how-to-open-a-file-in-emacs https://www.oilshell.org/blog/2021/08/xargs.html dynamic https://danilafe.com/blog/blog_microfeatures/ https://lock.cmpxchg8b.com/
- [x] paragraph titles https://fabiensanglard.net/
* paragraphs https://shreyans.org/airbnb https://sriramk.com/group-chats-rule-the-world
* tags
* header/footer: https://www.erichgrunewald.com/ https://bastian.rieck.me/outreach/ https://borretti.me/article/languages-not-ecosystems
* sidebar: https://www.goatcounter.com/help/start https://litchipi.github.io/infosec/2023/01/24/git-code-audit-viewed-as-rust-programmer.html
* sidenote: https://goodwill.awardwinninghuman.com/ https://www.w3.org/Style/CSS20/history.html https://pomb.us/build-your-own-react/ https://bsago.me/posts/waltzing-with-wireshark https://www.micahlerner.com/2021/05/23/reflecting-on-2020.html https://github.com/mlerner/mlerner.github.io/blob/master/_plugins/sidenote.rbhttps://danilafe.com/blog/blog_microfeatures/

PICTURES https://robinrendle.com/essays/
* in post 🗄️ `grunewald post picture.png`
* next to posts https://www.jotaen.net/blog/
* on homepage https://spwhitton.name/ 🗄️ `nirvana`
* photo album https://www.jefftk.com/pictures/
* illustrations https://mazzo.li/posts/fast-pipes.html#fn1
* code syntax highlighting https://danilafe.com/blog/blog_microfeatures/

LINKS
* linkable header https://danilafe.com/blog/blog_microfeatures/
* preview https://linkpreview.xyz/
* link checker https://github.com/lycheeverse/lychee https://bernard.app/
* underline https://danilafe.com/blog/blog_microfeatures/
* highlight on hover https://man7.org/linux/man-pages/dir_by_project.html#man-pages--man7
* highlight on selection `::selection` https://css-tricks.com/overriding-the-default-text-selection-color-with-css/

SEARCH
* DDG https://vadosware.io/ https://ddg.patdryburgh.com/
* _lunr.js_: https://github.com/olivernn/lunr.js https://clearerthinkingpodcast.com/#episodes
* _Stork_: https://stork-search.net/ https://danilafe.com/search/
* _TinySearch_: https://github.com/tinysearch/tinysearch https://news.ycombinator.com/item?id=23474134

MAIN PAGE
* audio / voice note https://mally.stanford.edu/index.html https://news.ycombinator.com/item?id=41582539
* hand-written note http://worrydream.com/July2023/

SOCIAL
* newsletter: https://www.scattered-thoughts.net/ https://www.erichgrunewald.com/newsletter/ https://www.benkuhn.net/ https://www.ntietz.com/newsletter/ https://thisisimportant.net/topics/newsletter/
> Congratulations, you are now on the list. Look out for an email sometime in the indefinite future.
> You've been sent a verification email with a link that you need to click, because that's how this always works. Check your inbox for a message from me@computer.rip. If you still haven't received it after an appropriate seeming amount of time, cross your fingers and try again
> In the future, you will be permitted (but not encouraged) to unsubscribe using a link at the end of each message.
* webring https://en.wikipedia.org/wiki/IndieWeb https://xn--sr8hvo.ws/ https://www.jvt.me/
* webmentions https://indieweb.org/static_site
* comments: HN, MR https://github.com/umputun/remark42 https://lists.sr.ht/~skeeto https://chevyray.dev/ask/
> Folks wanted to talk about stuff where they already were, rather than centralizing that conversation on individual blogs. https://news.ycombinator.com/item?id=30853711
* RSS generation

## SSG

ZOLA 📜 https://github.com/getzola/zola
* features: hot reload, tags, TOC https://chevyray.dev/blog/creating-175-fonts/
* used by https://github.com/ChevyRay/chevyray.dev https://haskellbook.com/
* tags https://inputusername.github.io/zola-hook/
* themes https://www.getzola.org/themes/zola-easydocs-theme/ https://www.getzola.org/themes/dinkleberg/ https://www.getzola.org/themes/hook/ https://www.getzola.org/themes/zola-386/

FEATURES
* hot reload
* index of all pages https://otterwiki.com/-/index
* _metadata_: title/desc, date, tags https://www.janmeppe.com/blog/I-dont-like-my-blog-anymore/ linking https://github.com/erwald/blog/blob/master/_data/series.json https://danilafe.com/blog/blog_microfeatures/
* advanced metadata https://gwern.net/metadata/annotation/backlink/https%253A%252F%252Fpublicdomainreview.org%252Fessay%252Four-masterpiece-is-the-private-life-in-pursuit-of-the-real-chateaubriand%252F.html
* _template engine_: page structure e.g. Jinja, Tera https://www.getzola.org/documentation/getting-started/overview/#first-steps-with-zola
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

SSGs 🗄️ `algos.md` tree / treebuilders
* Emacs org mode
* just HTML https://fabiensanglard.net/html/index.html
* BYO https://www.youtube.com/watch?v=Ph7oJDR71Jc https://github.com/mitsuhiko/rstblog https://til.simonwillison.net/django/building-a-blog-in-django dynamic https://realpython.com/build-a-blog-from-scratch-django/ https://dev.to/chasefleming/building-a-go-static-site-generator-using-elem-go-3fhh https://github.com/jeffkaufman/webscripts https://github.com/PaulJuliusMartinez/jless/tree/website
* _Astro micro_: 🎯 https://drew.silcock.dev/about/ https://github.com/drewsilcock/silcock-dev https://astro.build/themes/details/astro-micro/ https://astro-nano-demo.vercel.app/ https://www.bytedrum.com/about/
* _aurora_: 🎯 https://github.com/capjamesg/aurora
* _Bearclaw_: https://github.com/donuts-are-good/bearclaw
* _Eleventy_: https://www.11ty.dev/ https://www.erichgrunewald.com/ https://news.ycombinator.com/item?id=31293971 https://angeliqueweger.com/
* _Lanyon_: server, same guy that did termgraph https://github.com/mkaz/lanyon
* _Hugo_: https://gitlab.com/gitlab-com/content-sites/handbook
* popular https://blog.golang.org/8years
* bad docs https://yawpitchroll.com/posts/hugo-probably-is-not-for-you/ https://twitter.com/danluu/status/1244024025019342851
* _Lektor_: Python https://www.getlektor.com/ https://lucumr.pocoo.org/2015/12/21/introducing-lektor/
* _Lume_: https://lume.land/
* _m2h_: exec + move html from `content` to `src` https://github.com/zachvalenta/markdown-2-html
* _Makesite_: 🎯 https://github.com/sunainapai/makesite
* _Markata_: Python https://github.com/WaylonWalker/markata
* _Metalsmith_: Javascript https://github.com/metalsmith/metalsmith
* _Nikola_: https://getnikola.com/ not a blog https://getnikola.com/creating-a-site-not-a-blog-with-nikola.html
* _Pelican_: 🎯 no TOC, blog-oriented https://pirsquared.org/blog/pelican-transition.html https://pirsquared.org/blog/pelican-tags-vs-categories.html https://chat.openai.com/c/25d8a905-4ff4-4905-b63f-126f60ec9c75
* _Shite_: Bash https://github.com/adityaathalye/shite

CMS
* _website builder_: optimized for non-dev e.g. Wix, SquareSpace https://news.ycombinator.com/item?id=41337356
* _CMS_: client-server, content creation via UI, requires some dev e.g. Wordpress https://kevq.uk/the-case-for-wordpress https://blot.im/how https://bearblog.dev/ https://tunalog.org/en-us/index.html
* _headless CMS_: SPA gets content via API https://softwareengineeringdaily.com/2020/04/30/jamstack-content-management-with-scott-gallant-jordan-patterson-and-nolan-phillips/
* Ghost: hosting, newsletters, Stripe, membership https://softwareengineeringdaily.com/2018/07/26/ghost-open-source-publishing-platform-with-john-onolan/
* Netlify, Wagtail, Django, Perch
