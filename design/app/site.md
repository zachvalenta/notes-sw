# ⛩️

## 参考

## 进步

https://harper.blog/colophon/
cool
* https://yomguithereal.github.io/ https://edwardtufte.github.io/tufte-css/
* WebGL https://alexharri.com/blog/webgl-gradients
* animejs https://fuma-nama.vercel.app/blog/svg-art

update linux fs to account for work machine

TO ADD
> where to put Manning book notes? how to keep track of what your reading? -> it has a repo in `projects` -> you can also use Manning notebooks to see where you've been highlighting
> figure out which Manning books you're going to use your credits on
* finish going through notebook
* https://realpython.com/courses/programming-sockets/
* GoT death calculator
* outliers
> 🎗️ https://github.com/zachvalenta/python-from-the-guts
> how to work through book: notebook | REPL + repo doctest
> This strategy revolves around writing a crate...for every section of every chapter...to reduce friction as much as possible, I opted to write (type) down my chapter notes as comments within the “section crates” themselves. This system allows me to co-locate my notes with my Rust code, and learn a bit extra about Cargo along the way. It also keeps me on the keyboard, either writing code or taking notes in the same files. https://nickgerace.dev/posts/how-i-read-the-rust-programming-language/

---

DEPLOYMENT 🗄 `dns.md` Zola deployment
* ✅ DNS tools to diff `zachvalenta.com` vs. `zjayv.com`
* learn Github actions
* specify `index.html` for GH Pages: `publish_dir` https://chatgpt.com/c/66f4a787-5a40-8004-bda8-c9c207ae0e88 https://github.com/shalzz/zola-deploy-action/blob/master/README.md#custom-domain symlink to `templates/index.html`? https://chevyray.dev/blog/how-this-site-is-made/#deploying https://stackoverflow.com/questions/42941170/how-to-set-up-github-pages-to-look-for-index-html-in-a-different-location https://stackoverflow.com/questions/25320356/can-i-have-my-github-pages-index-html-in-a-subfolder-of-the-repository or Cloudflare https://chevyray.dev/blog/how-this-site-is-made/ or Netlify https://www.netlify.com/blog/2021/12/20/how-to-add-custom-domains-to-netlify-sites/

MORE SSG https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* tags
* RSS
* search
* styling from https://chevyray.dev/blog/test-post/
* template inheritance
* SSoT for book notes
> complication: some things you don't want to publish e.g. Austen notes

* _19_: Markdown-to-HTML util https://github.com/zachvalenta/markdown-2-html https://github.com/zachvalenta/site-drafts https://github.com/zachvalenta/site-content
* _18_: add content https://github.com/zachvalenta/zachvalenta.github.io/commit/15f304a8de18b7fef8f9cac1a6e9b778e5526d22
* _15_: init https://github.com/zachvalenta/zachvalenta.github.io/tree/54e8edd39c3a46a5867a399c3f60582693860018 https://github.com/zachvalenta/zachvalenta.github.io/commit/9c92238b0e6a35bda7afe505c1c7b4c965af7e11

# 📰 CONTENT

📙 https://www.manning.com/books/writing-for-developers

---

> There's much to love about lanparty.house: the house, the engine room, the wiring, the cat doors, the cat bathroom. But what I enjoyed the most was the fact that this site belongs to a rare class of internet gems: a single page, full of information with nothing held back, neatly formatted, easy to digest. https://registerspill.thorstenball.com/p/joy-and-curiosity-16
🏔️ write like this guy https://ludic.mataroa.blog/blog/you-must-read-at-least-one-book-to-ride/ standing invitation https://avi.im/blag/about/ https://refactoringenglish.com/chapters/rules-for-software-tutorials/ https://www.openmymind.net/ https://lambdaclass.com/ https://gleam.run/ https://simonwillison.net/2025/May/5/prompting/
🏔️ Julia Evans https://www.youtube.com/@wizardzines/videos
> the zines has been her only job since 2019 https://github.com/zserge/zine https://zserge.com/posts/tab/

* addendum https://blog.plover.com/math/PM.html https://blog.plover.com/calendar/poor-richards-almanack.html
* factors: smart, wise, taste
* companies I want to work for https://www.wave.com/en/blog/world/
* https://simonwillison.net/2024/Dec/22/link-blog/ https://simonwillison.net/2025/Feb/4/build-a-link-blog/

HOW THINGS WORK
* movies https://www.theringer.com/2024/8/21/24225522/the-arms-race-behind-where-movies-shoot https://www.theringer.com/2024/9/23/24252627/biggest-takeaways-netflix-data-dump-2024-streaming https://www.theringer.com/2024/9/25/24253629/how-to-make-your-own-tv-show-and-get-netflix-to-buy-it-mark-duplass-penelope-netflix https://www.theringer.com/2024/9/30/24258856/how-should-movie-and-tv-stars-be-paid
https://kaiwenwang.com/stack
https://gwern.net/matt-levine https://www.felixstocker.com/blog/geheimnisvoll https://news.ycombinator.com/item?id=41975993
https://gwern.net/book-writing

JOB BOARDS
* Github has a job profile?
* why did Stack Overflow kill their job board? why did they bring it back with Indeed?
* why aren't there tentpoles in this space akin to Hackernews and Lobste.rs?
> get set up with RSS btw and use for Lobste.rs

OBSESSIVES
* https://git-how.com/
* https://blog.plover.com/misc/three-corners-4.html
* bob is honest https://robertheaton.com/chatgpt/ https://uk.linkedin.com/in/robertjheaton
* https://en.wikipedia.org/wiki/Rosetta_Reitz

ZA
* EDI and Stedi: papering over a bad spec for fun and profit https://news.ycombinator.com/item?id=41919907
> kinda like Typescript to JS, OCaml to JS
* dev journal https://www.peterbaumgartner.com/blog/wrapping-a-rust-crate-in-a-python-package/
* how to fake being a pythonista in 2024
> I wish there was a good place to learn “the other parts” of C++, the build systems, using static analyzers, testing, dependency management, etc. https://news.ycombinator.com/item?id=34229802

## projects

🗄️ `it.md` fs

MONOREPO
* reduces toil of copying CQ learnings across repos

MICRO
* facilitates sharing
* prevents pileup in global dep cache
* prevent cluttering single repo
* repo tag for grep: `nmb` | `sandbox`

## sitemap

```sh
├── dir
│   └── about  #  https://adamj.eu/contact/
│   └────── CV  # https://yorickpeterse.com/resume/ http://127.0.0.1:1111/cv
│   └────── phone screen  #  http://127.0.0.1:1111/phone-screen/
│   └────── quotes
│   └────── draw/skate/music
│   └── blog
│   └────── how things work
│   └────── idea glossary
│   └────── little thoughts
│   └────── software opinions
│   └────── TIL
│   └── notes on books  # https://daverupert.com/bookshelf/
│   └────── fiction
│   └────── non-fiction
│   └── personal
│   └────── photos
│   └────── updates
│   └── projects
│   └────── lyrics  # Babatunde, Luambo, Rochereau, Mulatu, Francis Bebey, Cesaria Evora, Amalia Rodrigues
│   └────── learn econ with python  # https://en.wikipedia.org/wiki/Paul_Romer
```

## syndication

🗄️ `sociology.com` RSS

* blog
* repo https://github.com/hynek/stamina
* Youtube https://www.youtube.com/watch?v=BxikFuvaT1Y

---

> You have to think of YouTube and other platforms as a mechanism for distribution, not a source of truth. If you're a creator it's essential to have your own place on the web were you can host and publish anything without fear that it will be taken down for any reason — even accidentally. As it becomes cheap to automate both creating takedown requests and processing requests, the volume of spam requests is going to skyrocket and it seems likely there will be more false positives. https://x.com/3blue1brown/status/1876291319955398799
* email/RSS https://travisjeffery.com/subscribe/
* bibtex citation https://www.milesmcbain.com/posts/zsa-moonlander-review/ https://distill.pub/2021/gnn-intro/
* “POSSE” (“post on your own site, syndicate elsewhere”) https://jvns.ca/blog/2024/11/09/new-microblog/ https://www.youtube.com/watch?v=WYqnxCFJoLE https://x.com/jeremyjkun/status/1798789885966602419 https://chrisholdgraf.com/blog/2024/bluesky
* no traffic from Google -> "whatever Google and Twitter are doing right now, unless your blog post lands on Hacker News front page, you basically get no more traffic anymore." https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek
* https://zackproser.com/blog/run-your-own-tech-blog
* https://zackproser.com/blog/2023-wins
* https://danluu.com/corp-eng-blogs/
* https://simonwillison.net/2024/Jul/13/give-people-something-to-link-to/

🏔️
* Warmerdam https://calmcode.io
* Willison

## animation / video

🗄️ `feedback.md` Marimo

* _Raylib_: https://github.com/raysan5/raylib https://github.com/danslocombe/wobbly_vid https://www.youtube.com/watch?v=EO02mP0mLYI
* _Manim_: 🎯 Visualize concepts like Pareto efficiency. https://www.youtube.com/watch?v=rbu7Zu5X1zI https://chriskw.xyz/2025/05/21/Fractal/
* _Plotly_/_Bokeh_: Time-series analysis of economic indicators.
* _Pygame_: Agent-based modeling for economic simulations (e.g., consumer markets) https://www.jtolio.com/2025/02/py3-pygame-miyoo-a30/
* _Matplotlib (FuncAnimation)_: Works well for things like step-by-step economic equilibrium shifts.
```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

def bubble_sort_steps(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                yield arr.copy()

def animate_bubble_sort():
    data = np.random.randint(1, 100, 20)
    fig, ax = plt.subplots()
    bar_rects = ax.bar(range(len(data)), data)
    def update(arr):
        for rect, val in zip(bar_rects, arr):
            rect.set_height(val)
        return bar_rects
    anim = FuncAnimation(fig, update, frames=bubble_sort_steps(data), interval=50, repeat=False)
    return anim
```

> 150K subs = $25-50k/year
> even this, despite looking great, is not good enough
mCoding https://www.youtube.com/watch?v=qZNJTh2NEiU
https://github.com/mCodingLLC/VideosSampleCode
https://github.com/ManimCommunity/manim/
Dreams of Code https://www.youtube.com/watch?v=A_3MP_V-kB4

# 🕸️ DESIGN

📚
* Stimac https://www.manning.com/books/design-for-developers
* Zeldman  https://cybercultural.com/p/web-design-1997/

https://youtube.com/watch?v=Jf0cjocP8Wk
scroll bar https://focusfurnace.com/scroll_buddy.html

## font / text

🗄️ typography

* https://neil.computer/
* https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
* Claude output pretty good
* FOIT/FOUT https://css-tricks.com/fighting-foit-and-fout-together/
* _line spacing_: 130% point size
* _line length_: 80 char https://practicaltypography.com/typography-in-ten-minutes.html http://www.designishistory.com/1920/jan-tschichold/
* https://practicaltypography.com/type-composition.html
* https://practicaltypography.com/text-formatting.html
* https://practicaltypography.com/page-layout.html
* https://typographyforlawyers.com/page-layout.html
* https://practicaltypography.com/sample-documents.html
* https://typographyforlawyers.com/sample-documents.html
* asterisk for highlight https://asteriskmag.com/issues/09/abundance-at-home

## layout

---

https://lambdaclass.com/
* https://lwn.net/Articles/997784/
* https://drewdevault.com/2019/03/04/sourcehut-design.html
🛠️ Sketch, Figma
🇬🇧 UK design system https://govukvue.org/
🗄
* `viz.md`
* `sw/lang/html-css/design`
📝
* https://www.refactoringui.com/
* https://anthonyhobday.com/sideprojects/saferules/
* https://macwright.com/2016/12/28/what-little-i-know-about-design.html
* https://jamesg.blog/2024/08/16/content-layout-design/
* squares https://allaboutberlin.com/
* single page https://run.jotaen.net/ https://omakub.org/

MAIN PAGE
* audio / voice note https://mally.stanford.edu/index.html https://news.ycombinator.com/item?id=41582539
* hand-written note http://worrydream.com/July2023/

LAYOUT 🔗  https://github.com/arp242/hello-css/
* https://drewdevault.com/2024/08/30/2024-08-30-Rust-in-Linux-revisited.html
- [x] paragraph titles https://fabiensanglard.net/
* paragraphs https://shreyans.org/airbnb https://sriramk.com/group-chats-rule-the-world
* tags
* header/footer: https://www.erichgrunewald.com/ https://bastian.rieck.me/outreach/ https://borretti.me/article/languages-not-ecosystems

## examples

🏔️ https://travisjeffery.com/
🔗 https://github.com/zachvalenta/web-design

https://spectrum.ieee.org/lely-dairy-robots
make this into a page https://webdesigninspiration.io/
great 404s https://news.ycombinator.com/item?id=43589119 https://www.ft.com/404

MINIMAL 🔗 https://news.ycombinator.com/item?id=36745314
* https://blog.yossarian.net/
* https://blog.jacobvosmaer.nl/0014-yocto/
* centered https://urchade.github.io/
* https://nat.org/
* https://vancouver.systems/
* https://news.ycombinator.com/login?goto=news
* https://himitsustore.org/
* https://stevenvanbael.com/
* https://maxlangenkamp.me/posts/tech_not_inevitable
* https://www.oilshell.org/
* https://yossarian.net/
* https://xnacly.me/
* https://www.netmeister.org/blog/nsauth-diversity.html
* https://www.shopify.com/ca/editions/winter2025
* https://www.mattkeeter.com/blog/2024-03-25-packing/

UNIQUE
* https://shreyans.org/
* https://shaaddsouza.com/
* blocks https://www.ntietz.com/ https://thisisimportant.net/
* https://borretti.me/
* https://robinrendle.com/
* https://kaiwenwang.com/stack
* https://abundance.institute/
* https://www.nicchan.me/
* https://www.sacred.computer/
* https://blog.glyphdrawing.club/why-is-there-a-small-house-in-ibm-s-code-page-437/

## dropdowns

* do this instead https://www.cs.cmu.edu/~pavlo/blog/2024/01/2023-databases-retrospective.html
* https://blog.danielh.cc/blog/sat

## ToC

* https://tomlinford.com/posts/robinhood-sharding-to-scale
* quarto https://github.com/emilyriederer/website https://www.emilyriederer.com/post/py-rgo-2025/ reports https://www.youtube.com/watch?v=Q3phTByW138
* https://www.goatcounter.com/help/start https://litchipi.github.io/infosec/2023/01/24/git-code-audit-viewed-as-rust-programmer.html    https://gendignoux.com/readlist/
> needs to be on the side, at least on non-mobile web https://www.paulox.net/2023/11/07/database-generated-columns-part-1-django-and-sqlite/
* https://www.murilopereira.com/how-to-open-a-file-in-emacs
* https://www.oilshell.org/blog/2021/08/xargs.html
* dynamic https://danilafe.com/blog/blog_microfeatures/ https://lock.cmpxchg8b.com/ https://daniel.lawrence.lu/blog/y2024m05d31/
* https://vadimkravcenko.com/shorts/habits-of-great-software-engineers/

## images

* text, image, text, image https://aresluna.org/the-hardest-working-font-in-manhattan/

---

* https://terriblesoftware.org/2025/04/07/making-ai-actually-work-on-your-team/
* avatar/identicons for null image products https://github.com/MuhammadSaim/goavatar
* https://pilledtexts.com/why-i-use-a-17-year-old-thinkpad/
* image, text https://neil.computer/notes/how-to-install-postgresql-in-a-custom-directory/ https://neil.computer/notes/chart-of-accounts-for-startups-and-saas-companies/
* draw your own Ben Thompson style https://tej.as/blog/how-to-grow-professional-relationships-tjs-model
* use them in articles to make things stick! https://eli.thegreenplace.net/2024/ml-in-go-with-a-python-sidecar/
* face on every page https://blog.plover.com/music/revolver.html https://drewdevault.com/
* https://www.cs.cmu.edu/~pavlo/
* https://levien.com/
* https://robinrendle.com/essays/
* in post 🗄️ `grunewald post picture.png`
* next to posts https://www.jotaen.net/blog/
* on homepage https://spwhitton.name/ 🗄️ `nirvana`
* photo album https://www.jefftk.com/pictures/
* illustrations https://mazzo.li/posts/fast-pipes.html#fn1
* code syntax highlighting https://danilafe.com/blog/blog_microfeatures/

## notes

SIDENOTE
* https://goodwill.awardwinninghuman.com/
* https://www.w3.org/Style/CSS20/history.html
* https://pomb.us/build-your-own-react/
* https://bsago.me/posts/waltzing-with-wireshark
* https://www.micahlerner.com/2021/05/23/reflecting-on-2020.html
* https://github.com/mlerner/mlerner.github.io/blob/master/_plugins/sidenote.rbhttps://danilafe.com/blog/blog_microfeatures/
* https://news.ycombinator.com/item?id=42244832

## links

* linkable header https://danilafe.com/blog/blog_microfeatures/
* preview https://linkpreview.xyz/ https://metacheck.appstate.co/
* link checker https://github.com/lycheeverse/lychee https://bernard.app/
* underline https://danilafe.com/blog/blog_microfeatures/
* highlight on hover https://man7.org/linux/man-pages/dir_by_project.html#man-pages--man7
* highlight on selection `::selection` https://css-tricks.com/overriding-the-default-text-selection-color-with-css/

## tables

https://grayduck.mn/articles/
https://lisamahapatra.com/
charts https://worksinprogress.co/issue/how-madrid-built-its-metro-cheaply/

# 🏡 HOSTING

🗄️ `src.md` CICD > Actions

---

https://www.openmymind.net/2010/10/26/An-Introduction-To-Hosting/
* _AWS_: https://brandur.org/aws-intrinsic-static S3 and Cloudfront https://www.benkuhn.net/about/ https://github.com/s3tools/s3cmd s3-website https://bedford.io/misc/about/
* _pico_: https://pico.sh/pgs
* _Netlify_: https://wsvincent.com/site-design/ https://adamwathan.me/uses/
* _AWS amplify_: https://aws.amazon.com/amplify/
* _Cloudflare pages_:
* _Github pages_: https://simonwillison.net/2025/Mar/18/actions-pages/
* _Netlify_: https://www.netlify.com/
* _Render_:
* _Surge_: https://surge.sh/
* _Vercel_: https://vercel.com/

## Amazon

https://www.getzola.org/documentation/deployment/aws-s3/

## Github Pages

https://claytonwramsey.com/

context: my personal site repo is https://github.com/zachvalenta/zachvalenta.github.io I'm trying to move to a different static site generator. I'm using this repo to test it out: https://github.com/zachvalenta/zjayv.github.io
> https://chatgpt.com/c/680eda63-ce0c-8004-8e45-5f65dc69ae6a
```txt
You already have a user site at
→ https://zachvalenta.github.io
(GitHub requires that repo to be named zachvalenta.github.io.)

You’re trying to also publish zjayv.github.io as another "user site" — but GitHub Pages only allows one user site per account.

zjayv.github.io will not automatically become a second root-level site (https://zjayv.github.io/).

GitHub will treat it as a project site, meaning URL will be:
→ https://zachvalenta.github.io/zjayv.github.io/
```

> try using Sourcehut instead

RULES https://www.getzola.org/documentation/deployment/github-pages/ https://github.com/shalzz/zola-deploy-action https://chatgpt.com/c/675a107f-ecac-8004-97eb-1fecff5fb9c0
* `index.html` in root of branches `master`|`main`|`gh-pages`
* specify branch `repo/settings/pages/branch`
* don't need to do anything with `GITHUB_TOKEN` if the job only needs to access the repo it is running in
* site named `<username>.github.io` must correspond to repo named `<username>.github.io`

WORKLOG
* commit `d5072df` + `settings/pages/branch` to `gh-pages` got the site deployed but the URL nested under my user name (`https://www.zachvalenta.com/zjayv.github.io/`), presumably bc a single user can only have a single `github.io` site?
* adding CNAME broke site bc you have to add CNAME config in registrar (in my case, Name Cheap) https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain
* zjay.github.io: CNAME still broken i.e. not serving actual site (but stock pages from Name Cheap?)
```sh
#!/usr/bin/env bash
# DNS
doggo liyasthomas.github.io --time
doggo zachvalenta.com --time
doggo zjayv.github.io --time
doggo zjayv.com --time

# HTTP: STATUS CODE PASS/FAIL
control_url="https://liyasthomas.github.io/"
control_status=$(curl -o /dev/null -s -w "%{http_code}" "$control_url")
control="$control_url,$control_status"
treatment_url="https://zjayv.github.io/"
treatment_status=$(curl -o /dev/null -s -w "%{http_code}" "$treatment_url")
treatment="$treatment_url,$treatment_status"
sites=($control $treatment)
for site in "${sites[@]}"; do
  if [[ "$(echo "$site" | cut -d ',' -f 2)" == "200" ]]; then
    bg="green"
    fg="$(pastel textcolor "$bg")"
    pastel paint "$fg" --on "$bg" "url: $(echo "$site" | cut -d ',' -f 1) status: $(echo "$site" | cut -d ',' -f 2)"
  else
    bg="red"
    fg="$(pastel textcolor "$bg")"
    pastel paint "$fg" --on "$bg" "url: $(echo "$site" | cut -d ',' -f 1) status: $(echo "$site" | cut -d ',' -f 2)"
  fi
done

# HTTP: DEBUG
# curl -I https://liyasthomas.github.io/
# curl -I https://zjayv.github.io/
```

---

WORKLOG
* zjay.github.io: unpublish
> 🎗️ try deploying on Vercel et al.
> this maybe wiped out all previous commits on the `gh-pages` branch?
* zjay.github.io: roll back to `d5072df`
* zjay.github.io: use as playground
* zjay.com: set up CNAME in Name Cheap
* zachvalenta.com: import Zola blog (DNS already set up)
* zjay.com: unpublish (do you need to take down DNS from Name Cheap?)

* attempt to specify build dir
```yaml
name: deploy to GH Pages
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: checkout repo
        uses: actions/checkout@v3
      - name: deploy to GH Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

DEPLOYING ZJAYV https://zjayv.github.io/ 🧠 https://chatgpt.com/c/66f4a787-5a40-8004-bda8-c9c207ae0e88
> start here https://www.getzola.org/documentation/deployment/github-pages/
```txt
things I've already tried

- publish_dir
- specify branch (settings > pages)
```
* workflows https://github.com/zachvalenta/zjayv.github.io/actions
> why do they have two different names?
* site that works https://liyasthomas.github.io/
* need cname? https://github.com/zachvalenta/zachvalenta.github.io/blob/master/CNAME https://github.com/zachvalenta/zachvalenta.github.io/blob/master/CNAME.txt
* docs https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
* more docs https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages

## sourcehut

https://www.getzola.org/documentation/deployment/sourcehut/

# 🦾 SSG

BYO https://fluxsec.red/how-I-developed-a-markdown-blog-with-go-and-HTMX

## alternatives

🗄️️ `algos.md` tree / treebuilders

* Emacs org mode
* BYO https://www.youtube.com/watch?v=Ph7oJDR71Jc https://github.com/mitsuhiko/rstblog https://til.simonwillison.net/django/building-a-blog-in-django dynamic https://realpython.com/build-a-blog-from-scratch-django/ https://dev.to/chasefleming/building-a-go-static-site-generator-using-elem-go-3fhh https://github.com/jeffkaufman/webscripts https://github.com/PaulJuliusMartinez/jless/tree/website or just HTML https://fabiensanglard.net/html/index.html
* _Astro micro_: 🎯 https://drew.silcock.dev/about/ https://github.com/drewsilcock/silcock-dev https://astro.build/themes/details/astro-micro/ https://astro-nano-demo.vercel.app/ https://www.bytedrum.com/about/ https://steveklabnik.com/writing/ten-years-of-ru---ewriting-my-website/
* _aurora_: 🎯 https://github.com/capjamesg/aurora
* _Bearclaw_: https://github.com/donuts-are-good/bearclaw
* _Django_: 🎯 https://simonwillison.net/about/#subscribe
* _Eleventy_: https://www.11ty.dev/ https://www.erichgrunewald.com/ https://news.ycombinator.com/item?id=31293971 https://angeliqueweger.com/
* _Lanyon_: server, same guy that did termgraph https://github.com/mkaz/lanyon
* _hakyll_: 🎯 Haskell https://jaspervdj.be/hakyll/ https://blog.moertel.com/ https://github.com/gwern/gwern.net https://gwern.net/design
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
* Netlify, Wagtail, Django, Perch https://wagtail.org/blog/how-the-wagtail-newsletter-package-came-to-be/

## features

* hot reload
* social/comments via Github https://zackproser.com/blog/autocomplete-is-not-all-you-need https://eradman.com/posts/sidecomment-web-stack.html
* browser `python -m http.server` https://www.pythonmorsels.com/cli-tools/
* sitemap https://otterwiki.com/-/index https://werc.cat-v.org/sitemap
* _metadata_: title/desc, date, tags https://www.janmeppe.com/blog/I-dont-like-my-blog-anymore/ linking https://github.com/erwald/blog/blob/master/_data/series.json https://danilafe.com/blog/blog_microfeatures/
* advanced metadata https://gwern.net/metadata/annotation/backlink/https%253A%252F%252Fpublicdomainreview.org%252Fessay%252Four-masterpiece-is-the-private-life-in-pursuit-of-the-real-chateaubriand%252F.html
* SQL https://news.ycombinator.com/item?id=42244987
* _template engine_: page structure e.g. Jinja, Tera https://www.getzola.org/documentation/getting-started/overview/#first-steps-with-zola https://www.gomponents.com/
* Templ https://www.youtube.com/watch?v=v9NC2P328sI
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

SEARCH
* DDG https://vadosware.io/ https://ddg.patdryburgh.com/
* _lunr.js_: 🎯 https://github.com/olivernn/lunr.js https://clearerthinkingpodcast.com/#episodes https://calmcode.io/shorts/lunr.py
* _Stork_: https://stork-search.net/ https://danilafe.com/search/
* _TinySearch_: https://github.com/tinysearch/tinysearch https://news.ycombinator.com/item?id=23474134

## ♾️ Hakyll

📜 https://jaspervdj.be/hakyll/

related at the end of article https://til.simonwillison.net/django/just-with-django https://bsky.app/profile/adamj.eu/post/3ld23bwbilk2y
https://gwern.net/about#importance-tags

> tags or tree? both? https://www.jonashietala.se/blog/tags/neovim/
structure https://rknight.me/

## ◻️ Hastie

https://github.com/mkaz/hastie
https://mkaz.github.io/hastie/

## 🪴 Quartz

📜 https://quartz.jzhao.xyz/

https://jzhao.xyz/posts/networked-thought https://x.com/_jzhao/status/1815280245764751465 https://jzhao.xyz/ examples https://patternlanguage.cc/ https://aarnphm.xyz/ search https://glossary.airbyte.com/ https://glossary.airbyte.com/ this guy showed up on Hacker News, no? https://www.ssp.sh/brain/data-engineering/ no URLs? https://git-how.com/

## 🔲 Zola

📜 https://github.com/getzola/zola https://www.getzola.org/

* places to update to add new section
```sh
├── content
│   └── new_section
│   └────── _index.md
│   └────── first_entry.md
├── templates
│   └────── _index.md  # add link
│   └────── new_section.md  # listview
│   └────── new_section_page.md  # template for individual entries
```

* features: hot reload, tags, TOC https://chevyray.dev/blog/creating-175-fonts/
* used by https://github.com/ChevyRay/chevyray.dev https://haskellbook.com/
* tags https://inputusername.github.io/zola-hook/
* themes https://www.getzola.org/themes/zola-easydocs-theme/ https://www.getzola.org/themes/dinkleberg/ https://www.getzola.org/themes/hook/ https://www.getzola.org/themes/zola-386/
