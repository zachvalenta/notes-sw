# ⛩️

## 参考

## 进步

* _24_: big rf, port site to Zola and rm old dirs for content/drafts
* _22_: rf fs, try Pelican, redesign
* _19_: water.css, Vue for BNY test runner
* _18_: JP (Vue for Dark Canary demo app)
* _17_: JP (Angular, CSS selectors for UI testing)
* _15_: struggle with positioning and assume I'll never be a developer

# 🪑 FRAMEWORKS

🗄️ `django.md` design
📙 https://www.manning.com/books/build-a-frontend-web-framework-from-scratch

## design

TAXONOMY https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/
* history: jQuery, Backbone, React, Next.js (built on top of React) https://blog.codepen.io/2024/11/11/chris-corner-our-eras-tour/
* templating, JSX https://news.ycombinator.com/item?id=42464310
* components https://github.com/wrabit/django-cotton
* Python https://github.com/widgetti/solara https://github.com/piercefreeman/mountaineer https://reflex.dev/ https://pybit.es/articles/fitness-tracker-app-with-python-reflex/
* _CRUD-and-forms_: Django https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/ 
* _vanilla_: https://github.com/bradtraversy/vanillawebprojects https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies
* _HTML-only_: htmx
* _jQuery-esque_: https://arp242.net/jquery.html Alpine https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/htmx-alpine/#building-interactive-interfaces-in-your-django-pages-with-alpinejs https://news.ycombinator.com/item?id=36697366 https://news.ycombinator.com/item?id=39580843 https://drewdevault.com/2013/08/19/You-dont-need-jQuery.html alpine with htmx https://www.youtube.com/watch?v=vLB7r8neQvE
* _React-esque_: Vue, Angular, Remix https://remix.run/
* _React-lite_: Mithril https://mithril.js.org https://news.ycombinator.com/item?id=24368689 Svelte https://svelte.dev/ https://news.ycombinator.com/item?id=24363261
* _full-stack_: Next, Redwood, sock-puppet, Remix https://macwright.com/2020/10/28/if-not-spas.html https://www.youtube.com/watch?v=hHWgGfZpk00
* _server side state_: do everything from the server w/ websockets https://macwright.com/2020/10/28/if-not-spas.html
> They [McMaster Carr] are server rendering all of their HTML...the server is very good at rendering HTML. https://www.youtube.com/watch?v=-Ln-8QM8KhQ
* _progressive enhancement_: content first, then sprinkle in some JS if the user-agent allows for it
* options: InstantPage (load pages before user even clicks) Turbolinks (fast nav w/out SPA) https://macwright.com/2020/10/28/if-not-spas.html 
* _wysiwyg_: https://news.ycombinator.com/item?id=27516212 https://github.com/facebook/lexical CodeMirror https://github.com/viebel/klipse

SPA tradeoffs
* https://htmx.org/essays/you-cant/
> Then there are the Node.js and Vue.js version upgrades, which feel like a relentless, never-ending battle. I swear, it's as if every single time I sit down to write a blog post, there's a new version of something absolutely critical to my site lurking in the shadows, waiting to pounce. With each upgrade comes the inevitable breaking changes, followed by the torturous debugging sessions that send me on a wild goose chase through the darkest, most obscure corners of Stack Overflow. And just when I think I've tamed the beast, another update appears, accompanied by a fresh set of dependency conflicts, deprecated methods, and newly introduced bugs that leave me questioning my very existence as a developer. Manual labor wasn't _that_ bad. Security upgrades are another beast entirely. Just when I think I've got everything under control, I load up GitHub to review and merge my latest pull request, but I'm beset instead by a dozen new CVE issues that dependabot is trying to patch via its own programmatic pull requests. Cue the panic, followed by the mad dash to patch and test the affected components. The other week I saw a guy drive up to my neighbor's house with a giant powerwashing setup and proceed to clean the entire exterior himself over the course of 4 hours. I could do that, too. https://zackproser.com/blog/maintaining-this-site-fucking-sucks
* no one cares about page reloads https://news.ycombinator.com/item?id=39471221
* JS framework vendor lock-in https://news.ycombinator.com/item?id=34613039
* history https://www.pzuraq.com/blog/four-eras-of-javascript-frameworks
* initial pageload, SEO, browser history management, analytics https://www.thoughtworks.com/radar/techniques?blipid=202203006
* decision fatigue https://reviewbunny.app/blog/dont-make-me-think-or-why-i-switched-to-rails-from-javascript-spas
* sacrifices maintenance for initial dev experience https://tinnedfruit.com/writing/create-your-own-dysfunctional-single-page-app.html
* good for interactivity https://tinnedfruit.com/writing/create-your-own-dysfunctional-single-page-app.html https://macwright.com/2020/05/10/spa-fatigue.html
> A chat application is a no-brainer. A dashboard of realtime data might not need to be a SPA, but would benefit from a reactive component that updates when the API is polled...I’d like to try and make it work offline. To do that, and do it well, you need a way to show the data in different ways even when you can’t call a server. This calls for javascript templating. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
* assumes prefer partial reload to page reload https://www.mattlayman.com/blog/2021/how-to-htmx-django
* user session is long-lived
> in theory subsequent actions might be faster once the page is loaded...but that assumes you make subsequent actions more often that initial actions. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
* doesn't use normal status codes https://remix.run/features
* error handling https://news.ycombinator.com/item?id=25507942
* makes everything more complex https://increment.com/frontend/when-frontend-means-full-stack/ https://github.blog/2018-09-06-removing-jquery-from-github-frontend/ https://news.ycombinator.com/item?id=29573607
> And one more thing: it’s possible to make fast, efficient CRUD apps the same way we made them in 2010. Fire up Django or Rails, stick the data in Postgres, put some thought into your forms and maybe add a tiny bit of javascript to enhance some input fields. Surely I must be missing something. Surely the billions of programming hours that have gone into all these new things aren’t in vain. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
> But the cultural tides are strong. Building a company on Django in 2020 seems like the equivalent of driving a PT Cruiser and blasting Faith Hill’s “Breathe” on a CD while your friends are listening to The Weeknd in their Teslas. Swimming against this current isn’t easy, and not in a trendy contrarian way. https://macwright.org/2020/05/10/spa-fatigue.html

ZA
* _PWA (progressive enhancement)_: layering functionality i.e. site works fine using HTML but adds CSS and JS if user agent supports https://technology.blog.gov.uk/2016/09/19/why-we-use-progressive-enhancement-to-build-gov-uk/ https://conroy.org/progressively-worse-apps
* page reloads are ok
> We ran Basecamp on a single server for the first year...most of the problems we feared weren't that big of a deal to customers. As long as you keep people in the loop, and are honest about the situation, they'll understand. - 📙 Getting Real [44]
taxonomy
* BYO https://nolanlawson.com/2023/12/02/lets-learn-how-modern-javascript-frameworks-work-by-building-one/ https://www.manning.com/books/build-a-frontend-web-framework-from-scratch
* https://github.com/redwoodjs/redwood https://news.ycombinator.com/item?id=34069527
* for Deno https://alephjs.org/
* Astro https://docs.astro.build/en/concepts/why-astro/ https://morizbuesing.com/blog/astro-from-next/
> It's hard to believe, but in 2022, the developer community continues to pump out interesting new frameworks for building web applications. Astro is a recent, open-source, multi-page application framework that renders HTML on the server and minimizes the amount of JavaScript sent over the wire. Astro seems particularly well-suited to content-oriented websites that pull from many different sources. We like the fact that although Astro encourages sending only HTML, it still supports — when appropriate — select active components written in the front-end JavaScript framework of your choice. It does this through its island architecture. Islands are regions of interactivity within a single page where the necessary JavaScript is downloaded only when needed. Astro is relatively new but seems to support a growing ecosystem of developers and code. It's one to watch as it develops. https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202210057

## htmx

> But as browsers proliferated and the Web grew from a document-delivery platform into a software-delivery platform, JavaScript became, arguably, the most widely deployed language runtime in the world. 📰 Ford what is code?
💻 https://github.com/zachvalenta/flask-htmx
📜
> https://pragprog.com/titles/mvhtmx/server-driven-web-apps-with-htmx/
* https://htmx.org/
* https://hypermedia.systems/book/contents/ https://www.amazon.com/REST-Practice-Hypermedia-Systems-Architecture/dp/0596805829
🗄
* `lang/python/flask/htmx-demo`
* `application.md`
* `html-css.md` Tailwind
* `system.md` API / approaches

---

 https://fluxsec.red/how-I-developed-a-markdown-blog-with-go-and-HTMX
* PETAL, Alpine, LiveView, Hotwire, htmx https://news.ycombinator.com/item?id=30325030 https://www.thoughtworks.com/radar/techniques?blipid=202203006 https://news.ycombinator.com/item?id=42711387
great core team https://news.ycombinator.com/item?id=42616476
if you try to do fancy stuff it will fight you https://news.ycombinator.com/item?id=42615472
https://htmx.org/essays/future/
https://calmcode.io/course/htmx/introduction
* people are using less Javascript https://blog.jetbrains.com/pycharm/2024/12/the-state-of-python/#trend-1-python-usage-with-other-languages-drops-as-general-adoption-grows
https://talkpython.fm/episodes/show/484/from-react-to-a-django-htmx-based-stack
https://github.com/maddalax/htmgo
https://news.ycombinator.com/item?id=41781457 https://chrisdone.com/posts/htmx-critique/
https://github.com/AnswerDotAI/fasthtml https://www.youtube.com/watch?v=4En57Zw6gU4

> It’s worth noting that AI tools are intimately familiar with Next.js and not so much with htmx, due to the lack of open-source training data. This is similar to the issue Rails faces. While not a dealbreaker, it did impact our development speed and the ease of finding solutions to problems. When we encountered issues, the wealth of resources available for React/Next.js made troubleshooting much faster. https://htmx.org/essays/why-gumroad-didnt-choose-htmx/

DESIGN
> Hotwire / htmx are about server-side rendering and making that work more smoothly with the client. eg fewer page navigations, more rapid update of the client, etc. But it's still, through and through, server render with server state. It works well as long as the server is always the source of truth. The things that it isn't good at, such as drag and drop or complex, multi-state forms on the client side, are basically because you temporarily have a split source of truth: the client is the source of truth with complex state. https://news.ycombinator.com/item?id=41733625
> The React/Next.js ecosystem is vast and mature, offering solutions to almost any problem we encountered. With htmx, we often found ourselves reinventing the wheel or compromising on functionality. This became particularly evident when we needed to integrate third-party services and libraries, which often had React bindings but no htmx equivalents...the complex, stateful nature of Helper’s interface made React and Next.js a better fit. https://htmx.org/essays/why-gumroad-didnt-choose-htmx/
* https://news.ycombinator.com/item?id=40847376
* https://testdriven.io/blog/fastapi-htmx/
* https://www.youtube.com/watch?v=kYV8K71pY64
* hypermedia https://quii.dev/HTMX_is_the_Future https://github.com/PyHAT-stack/awesome-python-htmx
* creator seems cool https://news.ycombinator.com/item?id=26769809 https://changelog.com/gotime/266
* vs. alpine, mithril https://news.ycombinator.com/item?id=32011439
* internals https://www.youtube.com/watch?v=javGxN-h9VQ
* htmz https://news.ycombinator.com/item?id=40709769
* https://drewdevault.com/2018/09/04/Conservative-web-development.html

DJANGO
> For my rewrite of the client, I’m going to skip the drama and just use htmx. Render Django templates server-side, include a single JS script, thrown in some HTML attributes, distinguish between full page requests vs. requests for a partial with updated data, and call it a day. No TypeScript, no Webpack, none of that nonsense. If I need special interactivity I can throw in some hyperscript. https://news.ycombinator.com/item?id=38517099
* https://www.youtube.com/watch?v=LwH4ifjt3Y4
* https://dev.to/kummerer94/django-and-htmx-i5c
* https://github.com/jacklinke/django-htmx-todo-list
* https://www.sharperinfo.com/post/htmx-django-bringing-the-new-school-to-the-old-school
* https://justdjango.com/blog/dynamic-forms-in-django-htmx https://github.com/guettli/django-htmx-fun

* https://leanrada.com/htmz/
* https://news.ycombinator.com/item?id=38952214
https://testdriven.io/courses/django-htmx/
https://github.com/bitswired/rustgpt
content negotiation https://news.ycombinator.com/item?id=38338033
https://htmx.org/essays/no-build-step/
replace your React https://htmx.org/essays/a-real-world-react-to-htmx-port/

* alternative: marko https://github.com/marko-js/marko
* vs. jQuery https://www.youtube.com/watch?v=VyCyDRcFHZc
* porting from React https://htmx.org/essays/a-real-world-react-to-htmx-port/
* dynamic search https://github.com/MattSegal/django-htmx-list-view
* https://testdriven.io/blog/flask-htmx-tailwind https://raw.githubusercontent.com/testdrivenio/flask-htmx-tailwind/master/todo.py
* tabs https://htmx.org/examples/tabs-hateoas/
* search https://htmx.org/examples/active-search/
* fade in https://htmx.org/examples/lazy-load/
* progress bar https://htmx.org/examples/progress-bar/
* download src https://testdriven.io/blog/flask-htmx-tailwind/#live-search-example

## React

---

📙 https://www.amazon.com/Road-learn-React-pragmatic-React-js/dp/172004399X/
https://roadmap.sh/react

* _Next_: framework https://www.joshwcomeau.com/blog/how-i-built-my-blog-v2/
* just a bit, Parcel https://mkaz.blog/code/add-react-to-existing-page
* solid.js https://typeofnan.dev/solid-js-feels-like-what-i-always-wanted-react-to-be/ https://github.com/solidjs/solid
* testing, Storybook, Ladle https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202210060
> As Storybook grew in popularity, it became more and more of a behemoth. If all you really care about is isolating and testing your React UI components, then Ladle is the alternative. Ladle supports most of the Storybook API (MDX files are not supported yet) and can be used as a drop-in replacement. It is lightweight and has better integration with Vite. It also provides simple and clean APIs that can be easily integrated with other testing frameworks.

## state

* `pushState()`: change browser history https://developer.mozilla.org/en-US/docs/Web/API/History/pushState
* used in SPAs (and McMaster Carr) to change history even when you're only rerendering part of the page https://www.youtube.com/watch?v=-Ln-8QM8KhQ

---

* HTML over websockets https://news.ycombinator.com/item?id=26265999
* Vuex, Pinia, Redux https://www.thoughtworks.com/radar/languages-and-frameworks/pinia
* _reactive_: update app to frequent state changes w/out reload
* _rendering - client-side_: initial req gets html/css/js, second req gets content as JSON and generates HTML https://www.openmymind.net/2012/5/30/Client-Side-vs-Server-Side-Rendering/
* _rendering - server-side_: initial req gets html/css/js + content https://www.openmymind.net/2012/5/30/Client-Side-vs-Server-Side-Rendering/ https://macwright.com/2020/05/10/spa-fatigue.html https://github.com/PyHAT-stack/awesome-python-htmx
* aka server-drive UI? https://www.thoughtworks.com/radar/techniques?blipid=202203029
* hydration https://fresh.deno.dev/ https://docs.astro.build/en/getting-started/

## Vue

📜 https://github.com/zachvalenta/vue-firebase

* wrappers: Nuxt, Quasar
* state of affairs circa 2021 https://news.ycombinator.com/item?id=28042766
* has own thing for HTTP https://github.com/pagekit/vue-resource
* Material design https://vuetifyjs.com/en/
* Python: write in Python https://stefanhoelzl.github.io/vue.py/ framework built on top https://github.com/elimintz/justpy Django https://tkainrad.dev/posts/use-vuejs-with-django/ template syntax conflicts w/ Flask https://www.youtube.com/watch?v=iwhuPxJ0dig https://testdriven.io/blog/developing-a-single-page-app-with-flask-and-vuejs/
* 450M CDN hits vs. 3M NPM downloads/month https://shoptalkshow.com/episodes/350/ @ 30 minute mark
* `mounted()`: hook to call on init https://stackoverflow.com/questions/45021907/vue-js-mounted before 2.0 was called `ready()` https://github.com/vuejs/vue/issues/2873 https://stackoverflow.com/a/40209796/6813490
* snippets
```js
// HIT API AND DISPLAY
data: {
    appName: 'foo',
    things: [],
},
api: function(){
    var url = "http://127.0.0.1:5000/api"
        fetch(url)
        .then(response => response.json())
        .then(json => {
            for (var i = 0; i <= json.results.length - 1 ; i++) {
                let thing = new Object();
                thing.name = json.results[i].name
                thing.desc = json.results[i].description
                this.things.push(thing)
            }
        })
}

<div id="listView">
    <ul> <li v-for="i in things"> name: {{i.name}} desc: {{i.desc}} </li> </ul>
</div>

// CLEAR INPUT FOR SEARCH https://stackoverflow.com/a/41519735
api: function(){
    this.query = ""  // clear input
    this.things = []  // clear data
    // call API again
}

// SETUP DEV TOOLS https://github.com/vuejs/vue-devtools/issues/190 https://vuejs.org/v2/guide/installation.html
<script type="text/javascript" src="https://unpkg.com/vue"></script> <!-- version I was using before -->
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script> <!-- from docs -->
<script type="text/javascript" src="vue.js"></script> <!-- dev version in single file -->
<script type="text/javascript" src="myMod.js"></script>

Vue.config.devtools = true;
var app = new Vue({
	el: '#root',
```

# 🥟 JAVASCRIPT

🛣️ https://roadmap.sh/nodejs
📙 Haverbeke eloquent javascript

---

STDLIB
* dashboard/D3 https://news.ycombinator.com/item?id=40378791
* site tour https://github.com/shipshapecode/shepherd
* datatable https://github.com/handsontable/handsontable https://appliku.com/post/django-rest-framework-and-datatable-example https://github.com/pivotal-energy-solutions/django-datatable-view https://news.ycombinator.com/item?id=30919257
* HTTP: Fetch, XHR/AJAX https://eloquentjavascript.net/18_http.html
* native: JS (Cordova/PhoneGap, Ionic, Capacitor) .NET (Xamarin) Golang (Lorca) Dart (Flutter https://news.ycombinator.com/item?id=41975047) Golang (https://github.com/wailsapp/wails https://github.com/cogentcore/core) Rust https://dioxuslabs.com/ https://www.bestinclassiosapp.com/ https://www.swiftjectivec.com/ React Native https://news.ycombinator.com/item?id=42690114
* typing: Typescript beat Elm/Flow
* Typescript, Civet https://news.ycombinator.com/item?id=41885940
* vizualization: https://www.chartjs.org/ https://testdriven.io/blog/django-charts/#prepare-and-serve-the-data https://github.com/airbnb/visx https://github.com/recharts/recharts -> https://openbb.co/open#social-media-metrics 🗄 `math.md` graphs
* WYSIWYG: https://quilljs.com/ https://github.com/Milkdown/milkdown
* tooling in other languages https://news.ycombinator.com/item?id=26872457
* rich text editor https://news.ycombinator.com/item?id=30299800
* heatmap https://cal-heatmap.com/
* keybindings https://github.com/jamiebuilds/tinykeys

SPECS
* _ECMAScript_: standards org (Bluetooth, USB); JS engines listen to them
* _ES1-3_: 1997-99
* _ES4_: abandoned due to disagreement
* _ES5_: 2009
* _ES6_: 2015

## lang

---

🔗 https://github.com/30-seconds/30-seconds-of-code

* lint https://github.com/biomejs/biome https://astral.sh/about
* _variables_: `var` don't use `let` like var but not in global scope `const` like it sounds
* object: collection of properties
* property: KV pair
* _array_: obj whose K is an int and whose V is a string; inherit from `Array.prototype` instead of `Object.prototype`
* _function statement/declaration_: `var test123 = function(){}`
* _function expression_: `var test123 = function(){}`; use this one bc avoids hoisting
* _arrow function_: same as function expression minus 'function', braces, ‘return'
* _IIFE (immediately invoked function expression)_: keeps variable names out of global scope
* this https://dev.to/ycmjason/let-me-explain-to-you-what-is-this-javascript-44ja
* `JSON.parse`: string to obj
* JS comes from Lisp https://brendaneich.com/tag/history/
* empty array https://stackoverflow.com/a/1232046/6813490 https://stackoverflow.com/a/47953762/6813490
* map (transform each el) reduce (n el to 1 el) filter (rm based on condition) https://wsvincent.com/functional-javascript-map-filter-reduce/
* _spread operator_: apply el of iterable as args to func call
* _sink_: https://javascript.info JavaScript 30 https://codeburst.io/the-2018-web-developer-roadmap-826b1b806e8d Eloquent JavaScript

* copy array
```javascript
const copied = array.slice();
```

* copy object
```javascript
let alice = {score: 5, name: 'Alice'};
let bob = Object.assign({}, player, {score: 3});
```

## packaging

MANAGERS
* _npm_: 
* _pnpm_: https://github.com/pnpm/pnpm https://pnpm.io/ https://www.youtube.com/watch?v=ZIKDJBrk56k
* _yarn_: https://yarnpkg.com/

REGISTRIES 🗄️ `python/pkg.md` publish > registry
* _jsr_: Deno https://www.youtube.com/watch?v=8IHhvkaVqVE [5:15]
* _npm_: https://www.npmjs.com/

ZA
* avoiding a build system https://jvns.ca/blog/2024/11/18/how-to-import-a-javascript-library/

---

* https://drewdevault.com/2021/11/16/Cash-for-leftpad.html
* _package_: anything w/ `package.json`

NPM
* `package.json`: dependency manifest
* `.npm`: cache https://docs.npmjs.com/files/folders
* `prune`: rm pkg in `node_modules` but not in `package.json`
* scopes: local (`./node_modules` of current pkg root; use for `require()`) global (`/usr/local` or wherever node is installed; use for CLI) https://stackoverflow.com/a/47284674

## runtimes

🗄️
* `linux.md` packaging
* `python/pkg.md` uv

RUNTIMES
* _bun_: ✅ runtime + tooling (bundle, transpile, pkg mgmt) https://bun.sh/
* impl: in Zig, using WebKit JavaScriptCore (instead Chromes V8 engine) https://news.ycombinator.com/item?id=31993556
* _Deno_: Node replacement https://softwareengineeringdaily.com/2020/09/28/deno-and-typescript-with-elio-rivero/
* _Node_: libuv (IO library) + V8 (JS engine) https://neovim.io/charter/
* don't install from OpenJS https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
* previous problem due to installing as root at Zipcode

VERSION MGMT
* _fnm_: https://github.com/Schniz/fnm
* _nodenv_: https://github.com/nodenv/nodenv
* rm version: find fs location `nodenv prefix <ver>` and then just rm dir https://github.com/nodenv/nodenv#uninstalling-node-versions
* shim = intercepts cmd and passes to specific version https://medium.com/@ujjawal.dixit/what-is-a-shim-72d9ac5d8620
* e.g. when you run `npm`, nodenv will find `npm` on `$PATH` in which Node version you're using and pass cmd to that binary use whatever
* workflow
```sh
version  # check current version
versions # list installed
install -l # available for install
install <ver> # install + rehash https://github.com/nodenv/nodenv#nodenv-rehash
whence $CMD # find version of cmd https://github.com/nodenv/nodenv#nodenv-whence
global/local <ver> # select https://stackoverflow.com/a/19518939
init # run `node` from shell https://github.com/nodenv/nodenv?tab=readme-ov-file#how-nodenv-hooks-into-your-shell
# UM thing
if command -v nodenv 1>/dev/null 2>&1; then
    eval "$(nodenv init --path)"
fi
```
* _nvm_: recommended by npm https://github.com/nvm-sh/nvm https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
* caveats: doesn't support fish, requires Command Line Tools https://github.com/creationix/nvm#important-notes
```sh
nvm current  # v22.13.1
nvm ls       # -> v22.13.1, default -> lts/* (-> v22.13.1), unstable -> N/A (default)
which node   # /Users/zvalenta/.config/nvm/versions/node/v22.13.1/bin/node
which npm    # /Users/zvalenta/.config/nvm/versions/node/v22.13.1/bin/npm
```
* _volta_: https://volta.sh/ https://www.thoughtworks.com/radar/tools?blipid=202203039

# 🟨 ZA

---

* _code splitting_: load separate bundles of js per page; typically need index bundle before you can start doing anything = 2 req/res minimum https://macwright.com/2020/05/10/spa-fatigue.html
>  The JS bundle alone is more than 7x the weight of the rendered page, can’t be called until the first HTTP request completes, and still has to make an API call. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
* _deep link_: opens to view inside native app
* _media player_: https://www.media-chrome.org/ https://player.style/
* _microfrontend_: micro service for frontend https://www.thoughtworks.com/radar/techniques/micro-frontends
* _minify_: https://glama.ai/blog/2024-08-29-reverse-engineering-minified-code-using-openai
* _polyfill_: replacement for Web API
* _sourcemap_: map from minified code to source for purpose of debugging
* _tree shaking_: remove dead code
* _WASM_: compilation target for browsers that supports non-JS languages https://words.steveklabnik.com/is-webassembly-the-return-of-java-applets-flash https://sqlite.org/wasm/doc/tip/about.md https://rsms.me/wasm-intro https://neugierig.org/software/blog/2024/04/rust-wasm-to-js.html https://antonz.org/go-1-24/
* _WebRTC_: browser-to-browser communication (for high-speed A/V) e.g. Facetime https://hpbn.co/webrtc/ https://pragprog.com/titles/ksrtc/programming-webrtc/
* _Webpack_: creates bundle (all libs in single file); preceded by Browserify, succeeded by Snowpack
* editors: Code Mirror, Monaco (what repl.it used before Code Mirror)

## browser

🗄
* `it.md` macos/app
* `security.md` privacy

STATE
> Speaking of data, there's a lot more data a website has to deal with that doesn't come from a database or an API. Which tab is active right now? Is this modal dialog open or closed? https://increment.com/frontend/when-frontend-means-full-stack/
* `window.localStorage` way to save state in browser https://www.w3schools.com/html/html5_webstorage.asp https://news.ycombinator.com/item?id=20855275
* _session_: only saved while tab open
* _cookie_: less than web storage (4k); sent to server on each request
* _web/DOM storage_: save data on per origin, available for different pages/tabs or even after restarting machine; isn't sent to server
* _IndexedDB_: in-browser obj db

BROWSERS
* set default: system preferences > general
* settings: zoom to 110, font fize large, downloads to desktop, switch search to DuckDuckGo, startup to open previous tabs
* extensions: Vimium, Mercury Reader, EditThisCookie, PocketTube
* clean pages: archive.vn, https://12ft.io/ https://github.com/wasi-master/13ft https://chromewebstore.google.com/detail/archive-page/gcaimhkfmliahedmeklebabdgagipbia?pli=1
* `python -m webbrowser pseudorandom.name` https://dev.to/dmahely/one-bash-command-to-start-the-day-2fni
* _Arc_: split panes https://en.wikipedia.org/wiki/Arc_(web_browser) https://www.youtube.com/watch?v=E9yZ0JusME4 https://news.ycombinator.com/item?id=36863925 https://news.ycombinator.com/item?id=41597250
* _awrit_: in terminal?!? https://github.com/chase/awrit
* _Brave_: switched to in 2022, way less storage hit (150M) than Chrome (1.2GB) 🗄️ `/Users/$USER/Library/Application Support`
* bad actors? https://news.ycombinator.com/item?id=18734999
* commands
```sh
CMD t  # restore tab
CMD r  # reload
CMD ALT i  # dev tools
CMD b  # bookmarks
```
* _Chrome_: what's the extension you're using to Youtube playlist org? https://sponsor.ajay.app/
* _Lynx_: 'reader mode' https://github.com/bensadeh/circumflex
* _Firefox_: https://wesbos.com/uses https://www.mozilla.org/en-US/firefox/developer/
* _Nyxt_: 🎯 https://news.ycombinator.com/item?id=42354691
* _Zen_: based on Firefox https://zen-browser.app/ can split panes within browser https://www.youtube.com/watch?v=VshptkoKfQo [6:30] https://x.com/mkennedy/status/1856416323447992381

---

browsers
* browser fingerprinting https://kevq.uk/how-browser-fingerprinting-works/ https://freedom-to-tinker.com/2018/06/29/against-privacy-defeatism-why-browsers-can-still-stop-fingerprinting/
* https://superuser.com/questions/1298062/chrome-clear-cookies-on-exit-feature-does-not-work can't use adblockers https://9to5google.com/2019/05/29/chrome-ad-blocking-enterprise-manifest-v3/ doesn't index old stuff https://www.tbray.org/ongoing/When/201x/2018/01/15/Google-is-losing-its-memory better memory https://blog.mozilla.org/firefox/firefox-uses-less-memory-chrome-edge-safari/ tree-style tabs https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/ also has Vimium https://addons.mozilla.org/en-US/firefox/addon/vimium-ff/ old version of Vimium for Firefox https://nullprogram.com/blog/2018/09/20/
* ad blocking https://www.jefftk.com/p/thoughts-on-ad-blocking https://news.ycombinator.com/item?id=27060898
* _Firefox_: https://www.mozilla.org/en-US/firefox/accounts/ http://ask-leo.com/why_isnt_my_browser_remembering_my_usernames_any_more.html https://marko.fyi/firefox/ https://www.troyhunt.com/were-baking-have-i-been-pwned-into-firefox-and-1password/ comes w/ VPN? https://premium.firefox.com/vpn/ 

* https://github.com/pyscript/pyscript https://realpython.com/pyscript-python-in-browser/
* Jest, https://github.com/capricorn86/happy-dom
* colors https://news.ycombinator.com/item?id=31107643
* text-based: lynx, browsh https://www.youtube.com/watch?v=sC9JH-Sr_2Q
* text-only mode: https://merabheja.com/12-text-only-browsers-for-browsing-in-slow-internet-connections/
* put script at end of body or in head using async https://stackoverflow.com/a/24070373
* extension for wayback machine https://news.ycombinator.com/item?id=27173185&utm_term=comment
* nyxt https://news.ycombinator.com/item?id=27219646
* _Web API_: document, window, Event, XMLHttpRequest, fetch https://www.vrk.dev/2019/07/11/why-is-modern-web-development-so-complicated-a-long-yet-hasty-explanation-part-1/

> Nowadays, if you say, "what is the web?", you must include specifications from at least IETF (e.g. HTTP), WHATWG (e.g. HTML), W3C (e.g. CSS) and Ecma (e.g. JavaScript); but actual browser behaviour (an extremely vague concept) must also be considered too, because it has a big impact on what the web is. https://news.ycombinator.com/item?id=24917780

* browser on remote box = you can have slow internet at home but use the faster connection in data center https://news.ycombinator.com/item?id=25129747
* be nice if they stopped developing https://drewdevault.com/2020/08/13/Web-browsers-need-to-stop.html
* `blur`: event fired when tabs switched https://blog.acolyer.org/2018/09/05/who-left-open-the-cookie-jar-a-comprehensive-evaluation-of-third-party-cookie-policies/
* _Chromium_: good for healthy standardization? https://dev.to/kenbellows/chromium-and-the-browser-monoculture-problem-420n
* _CLI_: googler/ddgr
* CSS bugs are a normal thing for browser vendors https://jvns.ca/blog/2020/08/10/some-more-css-comics/
* _debug_: save req res in dev tools, breakpoint (`debugger;`) inspect obj (`console.dir()`) stack trace (`console.trace()`)
* _DOM_: model of an HTML document as objects; interaction via Web APIs; standardized by W3C and WHATWG i.e. are not baked into the JavaScript language but rather reference to browser implementations
* _dev tools_: shortcuts https://developers.google.com/web/tools/chrome-devtools/shortcuts clear network panel https://www.youtube.com/watch?v=x4q86IjJFag https://apsdehal.in/blog/chrome-developer-tools-to-master
* _headless_: browser sans UI
* _JS engine_: V8 for Chrome, SpiderMonkey for Firefox
> ❓ aka web engine? browser engine? https://servo.org/ https://github.com/gosub-io/gosub-engine
* Blink, Servo https://news.ycombinator.com/item?id=42506569
* _layout engine_: parses XML/HTML into a DOM https://simonwillison.net/2024/Dec/21/clay-ui-library/
* scrolling https://news.ycombinator.com/item?id=23994619 https://dontfuckwithscroll.com/
* _service worker_: API to run background scripts; diff than AJAX bc allow for push notifications and sync from emanating from server https://whatisjasongoldstein.com/writing/service-workers-of-the-world-unite/
* `<script>`: now (inside `<head>` bc with async and defer can download script and parse HTML at the same time) then (at the end of <body> because browser stops parsing HTML while waiting for script to load) https://stackoverflow.com/a/24070373/6813490
* _WebGL_: 3D for the browser https://bits.coop/

## CSS

🗄️
* `education.md` design
* `viz.md` art
🔍 
* https://css-tricks.com/guides/
* https://cssreference.io/ 
* https://web.dev/learn/css/
📚
* Grant https://www.manning.com/books/css-in-depth-second-edition
* ⭐️ Dowden https://www.manning.com/books/tiny-css-projects
* Evans hell yes https://wizardzines.com/zines/css/
* Meyer https://www.amazon.com/CSS-Definitive-Guide-Layout-Presentation/dp/1098117611
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
* _halfmoon_: https://github.com/redimp/otterwiki
* _Magick_: sidenotes https://css.winterveil.net/
* _mpv_: 🎯 https://calmcode.io/shorts/mvp.css
* _pico_: 🎯 https://picocss.com
* _Pure_: 🎯 https://purecss.io/
* _Tailwind_: https://jvns.ca/blog/2018/11/01/tailwind--write-css-without-the-css/ for TUIs https://github.com/koaning/tuilwindcss https://calmcode.io/labs/tuilwind-css https://news.ycombinator.com/item?id=42799136
* _water_: ✅ https://github.com/kognise/water.css https://github.com/kognise/water.css/issues/160 

LAYOUT
* patterns https://github.com/phuoc-ng/csslayout https://web.dev/one-line-layouts/ https://gridbyexample.com/ https://every-layout.dev/
* responsive https://www.freecodecamp.org/news/responsive-web-design-how-to-make-a-website-look-good-on-phones-and-tablets/
* sticky https://btxx.org/posts/Please_Make_Your_Table_Headings_Sticky/
* adaptive (1 layout morphing to screensize) adaptative (n layouts for n screensizes) 🟧 Dowden
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
* preprocessors like SCSS without node/npm https://lukeplant.me.uk/blog/posts/django-sass-scss-without-nodejs-or-build-step/
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
* dropdown/collapsible https://news.ycombinator.com/item?id=29669812 🗄 `personal-site` nested https://www.youtube.com/watch?v=MA9WAHEEfGM
* link as button https://stackoverflow.com/q/2906582/6813490
* Youtube preview https://stackoverflow.com/a/18681824/6813490
* password protect a page https://github.com/robinmoisson/staticrypt
* understand `head` https://www.matuzo.at/blog/html-boilerplate/
* in email https://news.ycombinator.com/item?id=41007403

ARCHIVE
* _ArchiveBox_: https://archivebox.io/ https://news.ycombinator.com/item?id=41860909
* _monolith_: ✅ https://github.com/Y2Z/monolith 
* _SingleFile_: browser extension https://github.com/gildas-lormeau/SingleFile
* _Wayback Machine_: https://archive.org/
* _waybackpack_: every version of single page in Wayback Machine https://github.com/jsvine/waybackpack
* _wget_: https://stackoverflow.com/a/4769497 https://stackoverflow.com/a/10564190/6813490 https://news.ycombinator.com/item?id=16557439
* _you-get_: https://news.ycombinator.com/item?id=41962205

SEMANTICS
* _attribute_: metadata
* _canvas_: draw, make charts
* _EME (encrypted media extensions)_: DRM https://stackoverflow.com/questions/46212264/example-encrypted-media-extensions-encryption/46374671#46374671
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

## perf

📹 McMaster Carr https://www.youtube.com/watch?v=-Ln-8QM8KhQ @ 2:00
🗄️
* `application.md` HTTP
* `dbms.md` perf
* `python/stdlib.md` profiling
* `src.md` perf
* `telemetry.md` perf
* `test.md` integration

* _prefetch_: browser makes request when you hover over a link i.e. even before you click on it https://www.youtube.com/watch?v=-Ln-8QM8KhQ
* cache: "The browser stores URLs it fetches in a cache. At its simplest this looks like a big dictionary, from url to the contents of that url" https://www.jefftk.com/p/why-prefetch-is-broken https://developer.chrome.com/blog/http-cache-partitioning

---

* https://www.openmymind.net/2010/7/22/Website-Performance-Crossing-the-Ts-dotting-the-Is/
* https://hpbn.co/primer-on-web-performance/
* https://roadmap.sh/best-practices/frontend-performance
* https://developers.google.com/web/tools/chrome-devtools/network-performance/reference 
* https://1mb.club/
* https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-performance
* https://www.webpagetest.org/
* https://webhint.io
* https://developers.google.com/speed/pagespeed/insights/
