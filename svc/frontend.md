# ⛩️

## 参考

## 进步

ZOLA DEPLOYMENT
> blog auth? what is really the point of your site? 🗄️ `tmp.md`
* DNS tools to diff `zachvalenta.com` vs. `zjayv.com`
* learn Github actions
* specify `index.html` for GH Pages: `publish_dir` https://chatgpt.com/share/66f4a7c1-ea3c-8004-8327-46a9840bf1d5 https://github.com/shalzz/zola-deploy-action/blob/master/README.md#custom-domain symlink to `templates/index.html`? https://chevyray.dev/blog/how-this-site-is-made/#deploying https://stackoverflow.com/questions/42941170/how-to-set-up-github-pages-to-look-for-index-html-in-a-different-location https://stackoverflow.com/questions/25320356/can-i-have-my-github-pages-index-html-in-a-subfolder-of-the-repository or Cloudflare https://chevyray.dev/blog/how-this-site-is-made/ or Netlify https://www.netlify.com/blog/2021/12/20/how-to-add-custom-domains-to-netlify-sites/

MORE SSG https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* tags
* RSS
* search
* styling from https://chevyray.dev/blog/test-post/
* template inheritance
* SSoT for book notes
> complication: some things you don't want to publish e.g. Austen notes

* _24_: big rf, port site to Zola and rm old dirs for content/drafts
* _22_: rf fs, try Pelican, redesign
* _19_: water.css, Vue for BNY test runner
* _18_: JP (Vue for Dark Canary demo app)
* _17_: JP (Angular, CSS selectors for UI testing)
* _15_: struggle with positioning and assume I'll never be a developer

# 🪑 FRAMEWORKS

## design

TAXONOMY https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/
* components https://github.com/wrabit/django-cotton
* Python https://github.com/widgetti/solara https://github.com/piercefreeman/mountaineer
* _CRUD-and-forms_: Django https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/ 
* _vanilla_: https://github.com/bradtraversy/vanillawebprojects https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.semicolonandsons.com/episode/The-Hidden-Costs-of-Software-Dependencies
* _HTML-only_: htmx
* _jQuery-esque_: https://arp242.net/jquery.html Alpine https://www.saaspegasus.com/guides/modern-javascript-for-django-developers/htmx-alpine/#building-interactive-interfaces-in-your-django-pages-with-alpinejs https://news.ycombinator.com/item?id=36697366 https://news.ycombinator.com/item?id=39580843 https://drewdevault.com/2013/08/19/You-dont-need-jQuery.html
* _React-esque_: Vue, Angular, Remix https://remix.run/
* _React-lite_: Mithril https://mithril.js.org https://news.ycombinator.com/item?id=24368689 Svelte https://svelte.dev/ https://news.ycombinator.com/item?id=24363261
* _full-stack_: Next, Redwood, sock-puppet, Remix https://macwright.com/2020/10/28/if-not-spas.html https://www.youtube.com/watch?v=hHWgGfZpk00
* _server side state_: do everything from the server w/ websockets https://macwright.com/2020/10/28/if-not-spas.html
> They [McMaster Carr] are server rendering all of their HTML...the server is very good at rendering HTML. https://www.youtube.com/watch?v=-Ln-8QM8KhQ
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
> https://pragprog.com/titles/mvhtmx/server-driven-web-apps-with-htmx/
* https://htmx.org/
* https://hypermedia.systems/book/contents/
🗄
* `lang/python/flask/htmx-demo`
* `application.md`
* `html-css.md` Tailwind
* `system.md` API / approaches

---

https://github.com/maddalax/htmgo
https://news.ycombinator.com/item?id=41781457 https://chrisdone.com/posts/htmx-critique/
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
* used in SPAs (and McMaster Carr) to change history even when you're only rerendering part of the page https://chatgpt.com/c/67167486-b528-8004-b44c-89de54e2fded https://www.youtube.com/watch?v=-Ln-8QM8KhQ

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

📙 Eloquent Javascript
🛣️ https://roadmap.sh/nodejs

---

STDLIB
* dashboard/D3 https://news.ycombinator.com/item?id=40378791
* site tour https://github.com/shipshapecode/shepherd
* datatable https://github.com/handsontable/handsontable https://appliku.com/post/django-rest-framework-and-datatable-example https://github.com/pivotal-energy-solutions/django-datatable-view https://news.ycombinator.com/item?id=30919257
* HTTP: Fetch, XHR/AJAX https://eloquentjavascript.net/18_http.html
* native: JS (Cordova/PhoneGap, Ionic, React Native, Capacitor) .NET (Xamarin) Golang (Lorca) Dart (Flutter) Golang (Wails https://github.com/wailsapp/wails) Rust https://dioxuslabs.com/
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
* https://drewdevault.com/2021/11/16/Cash-for-leftpad.html
* _jsr_: Deno registry https://www.youtube.com/watch?v=8IHhvkaVqVE [5:15]
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
* _WASM_: compilation target for browsers that supports non-JS languages https://words.steveklabnik.com/is-webassembly-the-return-of-java-applets-flash https://sqlite.org/wasm/doc/tip/about.md https://rsms.me/wasm-intro
* _WebRTC_: browser-to-browser communication (for high-speed A/V) e.g. Facetime https://hpbn.co/webrtc/ https://pragprog.com/titles/ksrtc/programming-webrtc/
* _Webpack_: creates bundle (all libs in single file); preceded by Browserify, succeeded by Snowpack
* editors: Code Mirror, Monaco (what repl.it used before Code Mirror)

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
* extension for wayback machine https://news.ycombinator.com/item?id=27173185&utm_term=comment
* nyxt https://news.ycombinator.com/item?id=27219646
* _Web API_: document, window, Event, XMLHttpRequest, fetch https://www.vrk.dev/2019/07/11/why-is-modern-web-development-so-complicated-a-long-yet-hasty-explanation-part-1/

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
* _dev tools_: shortcuts https://developers.google.com/web/tools/chrome-devtools/shortcuts clear network panel https://www.youtube.com/watch?v=x4q86IjJFag https://apsdehal.in/blog/chrome-developer-tools-to-master
* _headless_: browser sans UI
* _JS engine_: V8 for Chrome, SpiderMonkey for Firefox
> ❓ aka web engine? browser engine? https://servo.org/ https://github.com/gosub-io/gosub-engine
* _layout engine_: parses XML/HTML into a DOM
* scrolling https://news.ycombinator.com/item?id=23994619
* _service worker_: API to run background scripts; diff than AJAX bc allow for push notifications and sync from emanating from server https://whatisjasongoldstein.com/writing/service-workers-of-the-world-unite/
* `<script>`: now (inside `<head>` bc with async and defer can download script and parse HTML at the same time) then (at the end of <body> because browser stops parsing HTML while waiting for script to load) https://stackoverflow.com/a/24070373/6813490
* _SVG_: XML for drawing https://www.getmotion.io/blog/where-are-all-the-animated-svgs
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
* _Tailwind_: https://jvns.ca/blog/2018/11/01/tailwind--write-css-without-the-css/ for TUIs https://github.com/koaning/tuilwindcss https://calmcode.io/labs/tuilwind-css
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

ARCHIVE
* _ArchiveBox_: https://archivebox.io/ https://news.ycombinator.com/item?id=41860909
* _monolith_: ✅ https://github.com/Y2Z/monolith 
* _SingleFile_: browser extension https://github.com/gildas-lormeau/SingleFile
* _Wayback Machine_: https://archive.org/
* _waybackpack_: every version of single page in Wayback Machine https://github.com/jsvine/waybackpack
* _wget_: https://stackoverflow.com/a/4769497 https://stackoverflow.com/a/10564190/6813490 https://news.ycombinator.com/item?id=16557439

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
* cache: "The browser stores URLs it fetches in a cache. At its simplest this looks like a big dictionary, from url to the contents of that url" https://www.jefftk.com/p/why-prefetch-is-broken

---

* https://roadmap.sh/best-practices/frontend-performance
* https://developers.google.com/web/tools/chrome-devtools/network-performance/reference 
* https://hpbn.co/primer-on-web-performance/
* https://1mb.club/
* https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-performance
* https://www.webpagetest.org/
* https://webhint.io
* https://developers.google.com/speed/pagespeed/insights/
* human perception https://hpbn.co/primer-on-web-performance/#speed-performance-and-human-perception

## SSG

🗄️ `infra.com` hosting

ZOLA 📜 https://github.com/getzola/zola
* features: hot reload, tags, TOC https://chevyray.dev/blog/creating-175-fonts/
* used by https://github.com/ChevyRay/chevyray.dev https://haskellbook.com/
* tags https://inputusername.github.io/zola-hook/
* themes https://www.getzola.org/themes/zola-easydocs-theme/ https://www.getzola.org/themes/dinkleberg/ https://www.getzola.org/themes/hook/ https://www.getzola.org/themes/zola-386/

FEATURES
* hot reload
* sitemap https://otterwiki.com/-/index https://werc.cat-v.org/sitemap
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

SEARCH
* DDG https://vadosware.io/ https://ddg.patdryburgh.com/
* _lunr.js_: https://github.com/olivernn/lunr.js https://clearerthinkingpodcast.com/#episodes
* _Stork_: https://stork-search.net/ https://danilafe.com/search/
* _TinySearch_: https://github.com/tinysearch/tinysearch https://news.ycombinator.com/item?id=23474134

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

SSGs 🗄️ `algos.md` tree / treebuilders
* Emacs org mode
* BYO https://www.youtube.com/watch?v=Ph7oJDR71Jc https://github.com/mitsuhiko/rstblog https://til.simonwillison.net/django/building-a-blog-in-django dynamic https://realpython.com/build-a-blog-from-scratch-django/ https://dev.to/chasefleming/building-a-go-static-site-generator-using-elem-go-3fhh https://github.com/jeffkaufman/webscripts https://github.com/PaulJuliusMartinez/jless/tree/website or just HTML https://fabiensanglard.net/html/index.html
* _Astro micro_: 🎯 https://drew.silcock.dev/about/ https://github.com/drewsilcock/silcock-dev https://astro.build/themes/details/astro-micro/ https://astro-nano-demo.vercel.app/ https://www.bytedrum.com/about/ https://steveklabnik.com/writing/ten-years-of-ru---ewriting-my-website/
* _aurora_: 🎯 https://github.com/capjamesg/aurora
* _Bearclaw_: https://github.com/donuts-are-good/bearclaw
* _Django_: 🎯 https://simonwillison.net/about/#subscribe
* _Eleventy_: https://www.11ty.dev/ https://www.erichgrunewald.com/ https://news.ycombinator.com/item?id=31293971 https://angeliqueweger.com/
* _Lanyon_: server, same guy that did termgraph https://github.com/mkaz/lanyon
* _hakyll_: Haskell https://jaspervdj.be/hakyll/ https://blog.moertel.com/
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
