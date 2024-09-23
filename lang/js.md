# ⛩️

## 参考

📙 Eloquent Javascript
🛣️ https://roadmap.sh/nodejs

## 进步

https://roadmap.sh/best-practices/frontend-performance

* _19_: Vue for Test Runner
* _18_: Vue for Dark Canary demo app
* _17_: Angular 1 for Case

# 🪑 FRAMEWORKS

## design

TAXONOMY https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/
* components https://github.com/wrabit/django-cotton
* Python https://github.com/widgetti/solara https://github.com/piercefreeman/mountaineer
* _CRUD-and-forms_: Django https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/ 
* _vanilla_: https://github.com/bradtraversy/vanillawebprojects https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies
* _HTML-only_: htmx
* _jQuery-esque_: https://arp242.net/jquery.html Alpine https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/htmx-alpine/#building-interactive-interfaces-in-your-django-pages-with-alpinejs https://news.ycombinator.com/item?id=36697366 https://news.ycombinator.com/item?id=39580843
* _React-esque_: Vue, Angular, Remix https://remix.run/
* _React-lite_: Mithril https://mithril.js.org https://news.ycombinator.com/item?id=24368689 Svelte https://svelte.dev/ https://news.ycombinator.com/item?id=24363261
* _full-stack_: Next, Redwood, sock-puppet https://macwright.com/2020/10/28/if-not-spas.html
* _server side state_: do everything from the server w/ websockets https://macwright.com/2020/10/28/if-not-spas.html
* _progressive enhancement_: content first, then sprinkle in some JS if the user-agent allows for it
* options: InstantPage (load pages before user even clicks) Turbolinks (fast nav w/out SPA) https://macwright.com/2020/10/28/if-not-spas.html 
* _wysiwyg_: https://news.ycombinator.com/item?id=27516212
* PETAL, Alpine, LiveView, Hotwire, htmx https://news.ycombinator.com/item?id=30325030 https://www.thoughtworks.com/radar/techniques?blipid=202203006

SPA tradeoffs
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
* page reloads are ok
> We ran Basecamp on a single server for the first year...most of the problems we feared weren't that big of a deal to customers. As long as you keep people in the loop, and are honest about the situation, they'll understand. - 📙 Getting Real [44]
taxonomy
* BYO https://nolanlawson.com/2023/12/02/lets-learn-how-modern-javascript-frameworks-work-by-building-one/
* https://github.com/redwoodjs/redwood https://news.ycombinator.com/item?id=34069527
* for Deno https://alephjs.org/
* Astro https://docs.astro.build/en/concepts/why-astro/ https://morizbuesing.com/blog/astro-from-next/
> It's hard to believe, but in 2022, the developer community continues to pump out interesting new frameworks for building web applications. Astro is a recent, open-source, multi-page application framework that renders HTML on the server and minimizes the amount of JavaScript sent over the wire. Astro seems particularly well-suited to content-oriented websites that pull from many different sources. We like the fact that although Astro encourages sending only HTML, it still supports — when appropriate — select active components written in the front-end JavaScript framework of your choice. It does this through its island architecture. Islands are regions of interactivity within a single page where the necessary JavaScript is downloaded only when needed. Astro is relatively new but seems to support a growing ecosystem of developers and code. It's one to watch as it develops. https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202210057

## htmx

📜
* https://htmx.org/
* https://hypermedia.systems/book/contents/
🗄
* `lang/python/flask/htmx-demo`
* `application.md`
* `html-css.md` Tailwind
* `system.md` API / approaches

---

https://github.com/AnswerDotAI/fasthtml

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

# 🟨 ZA

STATE
* HTML over websockets https://news.ycombinator.com/item?id=26265999
* Vuex, Pinia, Redux https://www.thoughtworks.com/radar/languages-and-frameworks/pinia
* _reactive_: update app to frequent state changes w/out reload
* _rendering - client-side_: initial req gets html/css/js, second req gets content as JSON and generates HTML https://www.openmymind.net/2012/5/30/Client-Side-vs-Server-Side-Rendering/
* _rendering - server-side_: initial req gets html/css/js + content https://www.openmymind.net/2012/5/30/Client-Side-vs-Server-Side-Rendering/ https://macwright.com/2020/05/10/spa-fatigue.html https://github.com/PyHAT-stack/awesome-python-htmx
* aka server-drive UI? https://www.thoughtworks.com/radar/techniques?blipid=202203029
* hydration https://fresh.deno.dev/ https://docs.astro.build/en/getting-started/

SEMANTICS
* _code splitting_: load separate bundles of js per page; typically need index bundle before you can start doing anything = 2 req/res minimum https://macwright.com/2020/05/10/spa-fatigue.html
>  The JS bundle alone is more than 7x the weight of the rendered page, can’t be called until the first HTTP request completes, and still has to make an API call. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
* _deep link_: opens to view inside native app
* _microfrontend_: micro service for frontend https://www.thoughtworks.com/radar/techniques/micro-frontends
* _minify_: https://glama.ai/blog/2024-08-29-reverse-engineering-minified-code-using-openai
* _polyfill_: replacement for Web API
* _sourcemap_: map from minified code to source for purpose of debugging
* _tree shaking_: remove dead code
* _WASM_: compilation target for browsers that supports non-JS languages https://words.steveklabnik.com/is-webassembly-the-return-of-java-applets-flash https://sqlite.org/wasm/doc/tip/about.md https://rsms.me/wasm-intro
* _WebRTC_: browser-to-browser communication (for high-speed A/V) https://hpbn.co/webrtc/
* _Webpack_: creates bundle (all libs in single file); preceded by Browserify, succeeded by Snowpack
* editors: Code Mirror, Monaco (what repl.it used before Code Mirror)

STDLIB
* dashboard/D3 https://news.ycombinator.com/item?id=40378791
* site tour https://github.com/shipshapecode/shepherd
* datatable https://github.com/handsontable/handsontable https://appliku.com/post/django-rest-framework-and-datatable-example https://github.com/pivotal-energy-solutions/django-datatable-view https://news.ycombinator.com/item?id=30919257
* HTTP: Fetch, XHR/AJAX https://eloquentjavascript.net/18_http.html
* native: JS (Cordova/PhoneGap, Ionic, React Native, Capacitor) .NET (Xamarin) Golang (Lorca) Dart (Flutter) Golang (Wails https://github.com/wailsapp/wails) Rust https://dioxuslabs.com/
* typing: Typescript beat Elm/Flow
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

## browser

🗄
* `it.md` macos/app
* `security.md` privacy

> But as browsers proliferated and the Web grew from a document-delivery platform into a software-delivery platform, JavaScript became, arguably, the most widely deployed language runtime in the world. 📰 Ford what is code?

STATE
> Speaking of data, there's a lot more data a website has to deal with that doesn't come from a database or an API. Which tab is active right now? Is this modal dialog open or closed? https://increment.com/frontend/when-frontend-means-full-stack/
* `window.localStorage` way to save state in browser https://www.w3schools.com/html/html5_webstorage.asp https://news.ycombinator.com/item?id=20855275
* _session_: only saved while tab open
* _cookie_: less than web storage (4k); sent to server on each request
* _web/DOM storage_: save data on per origin, available for different pages/tabs or even after restarting machine; isn't sent to server
* _IndexedDB_: in-browser obj db

---

* https://github.com/pyscript/pyscript https://realpython.com/pyscript-python-in-browser/
* Jest, https://github.com/capricorn86/happy-dom
* colors https://news.ycombinator.com/item?id=31107643
* text-based: lynx, browsh https://www.youtube.com/watch?v=sC9JH-Sr_2Q
* text-only mode: https://merabheja.com/12-text-only-browsers-for-browsing-in-slow-internet-connections/
* put script at end of body or in head using async https://stackoverflow.com/a/24070373
* archive whole site w/ wget https://stackoverflow.com/a/4769497 https://stackoverflow.com/a/10564190/6813490 https://news.ycombinator.com/item?id=16557439 every version of single page in Wayback Machine https://github.com/jsvine/waybackpack
* archive single page https://github.com/gildas-lormeau/SingleFile
* extensino for wayback machine https://news.ycombinator.com/item?id=27173185&utm_term=comment
* nyxt https://news.ycombinator.com/item?id=27219646
* _Web API_: document, window, Event, XMLHttpRequest, fetch https://www.vrk.dev/2019/07/11/why-is-modern-web-development-so-complicated-a-long-yet-hasty-explanation-part-1/
* prefetch https://www.jefftk.com/p/why-prefetch-is-broken

> Nowadays, if you say, "what is the web?", you must include specifications from at least IETF (e.g. HTTP), WHATWG (e.g. HTML), W3C (e.g. CSS) and Ecma (e.g. JavaScript); but actual browser behaviour (an extremely vague concept) must also be considered too, because it has a big impact on what the web is. https://news.ycombinator.com/item?id=24917780

* browser on remote box = you can have slow internet at home but use the faster connection in data center https://news.ycombinator.com/item?id=25129747
* be nice if they stopped developing https://drewdevault.com/2020/08/13/Web-browsers-need-to-stop.html
* code snippets in browser, CodeMirror https://github.com/viebel/klipse
* `blur`: event fired when tabs switched https://blog.acolyer.org/2018/09/05/who-left-open-the-cookie-jar-a-comprehensive-evaluation-of-third-party-cookie-policies/
* _Chromium_: good for healthy standardization? https://dev.to/kenbellows/chromium-and-the-browser-monoculture-problem-420n
* _CLI_: googler/ddgr
* CSS bugs are a normal thing for browser vendors https://jvns.ca/blog/2020/08/10/some-more-css-comics/
* _debug_: save req res in dev tools, breakpoint (`debugger;`) inspect obj (`console.dir()`) stack trace (`console.trace()`)
* _DOM_: model of an HTML document as objects; interaction via Web APIs; standardized by W3C and WHATWG i.e. are not baked into the JavaScript language but rather reference to browser implementations
* _dev tools_: shortcuts https://developers.google.com/web/tools/chrome-devtools/shortcuts clear network panel https://developers.google.com/web/tools/chrome-devtools/network-performance/reference https://www.youtube.com/watch?v=x4q86IjJFag https://apsdehal.in/blog/chrome-developer-tools-to-master
* _headless_: browser sans UI
* _JS engine_: V8 for Chrome, SpiderMonkey for Firefox
> ❓ aka web engine? browser engine? https://servo.org/
* _layout engine_: parses XML/HTML into a DOM
* scrolling https://news.ycombinator.com/item?id=23994619
* _service worker_: API to run background scripts; diff than AJAX bc allow for push notifications and sync from emanating from server https://whatisjasongoldstein.com/writing/service-workers-of-the-world-unite/
* `<script>`: now (inside `<head>` bc with async and defer can download script and parse HTML at the same time) then (at the end of <body> because browser stops parsing HTML while waiting for script to load) https://stackoverflow.com/a/24070373/6813490
* _SVG_: XML for drawing https://www.getmotion.io/blog/where-are-all-the-animated-svgs
* _WebGL_: 3D for the browser https://bits.coop/

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

## runtimes

* _bun_: ✅ runtime + tooling (bundle, transpile, pkg mgmt) https://bun.sh/
* impl: in Zig, using WebKit JavaScriptCore (instead Chromes V8 engine) https://news.ycombinator.com/item?id=31993556
* _Deno_: Node replacement https://softwareengineeringdaily.com/2020/09/28/deno-and-typescript-with-elio-rivero/
* _Node_: libuv (IO library) + V8 (JS engine) https://neovim.io/charter/
* don't install from OpenJS https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
* previous problem due to installing as root at Zipcode

## packaging

* _package_: anything w/ `package.json`
* _npm_: manager + registry https://www.npmjs.com/
* _yarn_: manager https://yarnpkg.com/
* `yarn install --ignore-engines` https://stackoverflow.com/a/45088032

NPM
* `package.json`: dependency manifest
* `.npm`: cache https://docs.npmjs.com/files/folders
* `prune`: rm pkg in `node_modules` but not in `package.json`
* scopes: local (`./node_modules` of current pkg root; use for `require()`) global (`/usr/local` or wherever node is installed; use for CLI) https://stackoverflow.com/a/47284674

## version mgmt

ALTERNATIVES
* _asdf_: https://github.com/asdf-vm/asdf
* _fnm_: https://github.com/Schniz/fnm
* _pkgx_: https://www.youtube.com/watch?v=S9oHESiZyr0
* _mise_: 🎯 https://github.com/jdx/mise
* _nvm_: https://github.com/creationix/nvm#important-notes
* _volta_: https://volta.sh/ https://www.thoughtworks.com/radar/tools?blipid=202203039

NODENV 📜 https://github.com/nodenv/nodenv
* rm version: find fs location `nodenv prefix <ver>` and then just rm dir https://github.com/nodenv/nodenv#uninstalling-node-versions
* _shim_: intercepts cmd and passes to specific version https://medium.com/@ujjawal.dixit/what-is-a-shim-72d9ac5d8620
* e.g. when you run `npm`, nodenv will find `npm` on `$PATH` in which Node version you're using and pass cmd to that binary use whatever
* workflow
```sh
# available for install
install -l

# install + rehash https://github.com/nodenv/nodenv#nodenv-rehash
install <ver>

# list installed
versions

# check current version
version
node --version

# find version of cmd https://github.com/nodenv/nodenv#nodenv-whence
whence $CMD

# select https://stackoverflow.com/a/19518939
global/local <ver>

# run `node` from shell https://github.com/nodenv/nodenv?tab=readme-ov-file#how-nodenv-hooks-into-your-shell
init
```
* UM thing
```sh
if command -v nodenv 1>/dev/null 2>&1; then
    eval "$(nodenv init --path)"
fi
```
