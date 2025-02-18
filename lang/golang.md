# ⛩️

## 参考

📚
* ⭐️ https://www.manning.com/books/learn-go-with-pocket-sized-projects
* Arundel https://bitfieldconsulting.com/books/love https://bitfieldconsulting.com/posts/best-go-books
* Butcher in practice
* Chang web
* Holmes https://www.manning.com/books/shipping-go
* ⭐️ Latour https://www.manning.com/books/learn-go-with-pocket-sized-projects
* Kennedy in action
* Kernighan go programming language

## 进步

https://fluxsec.red/how-I-developed-a-markdown-blog-with-go-and-HTMX
https://zackproser.com/blog/bubbletea-state-machine
https://bitfieldconsulting.com/posts/bit
https://bitfieldconsulting.com/posts/tdd-programming-confidence

https://www.youtube.com/watch?v=kNavnhzZHtk
https://www.willem.dev/articles/
https://rm4n0s.github.io/posts/2-go-devs-should-learn-odin/
building binary for your own archictecture (and fix frangipanni) https://github.com/jpbruinsslot/slack-term/issues/282

BASICS 📙 Ball
* BYO taskwarrior https://www.youtube.com/watch?v=yiFhQGJeRJk
* https://www.youtube.com/watch?v=un6ZyFkqFKo
* https://www.youtube.com/watch?v=8uiZC0l4Ajw
* https://go.dev/tour/list
* https://gist.github.com/prologic/5f6afe9c1b98016ca278f4d507e65510

* _20_: research packaging
* _19_: version mgmt (uninstall macOS pkg, reinstall `go` and `dep` w/ brew)
* _17_: PluralSight course w/ Roberto and Josh

# 📝 LANG

🗄️ `linux.md` concurrency
📚
* https://www.manning.com/books/go-by-example
* https://www.manning.com/books/go-in-practice-second-edition
📜
* https://github.com/uber-go/guide/blob/master/style.md
* https://golang.org/doc/effective_go.html
> Effective Go continues to be useful, but the reader should understand it is far from a complete guide.
> https://www.openmymind.net/The-Little-Go-Book/

* _embed_: good for distributed libs packaging the files they need vs. relying on the host OS fs https://www.youtube.com/watch?v=7EK06n485nk

---

https://www.openmymind.net/Things-I-Wish-Someone-Had-Told-Me-About-Go/
* generics https://www.dolthub.com/blog/2024-07-01-golang-generic-collections/ https://bitfieldconsulting.com/posts/generics https://bitfieldconsulting.com/posts/constraints
* lodash https://github.com/samber/lo
* enums https://www.zarl.dev/articles/enums
* loops https://go.dev/blog/loopvar-preview
* inheritance, interfaces https://www.dolthub.com/blog/2023-02-22-golangs-fake-inheritance/ https://preslav.me/2023/02/22/partially-implemented-interfaces-in-golang/ https://medium.com/@jankammerath/how-go-fixed-everything-that-was-wrong-with-programming-1b599a1055a8
* dates https://www.digitalocean.com/community/tutorials/how-to-use-dates-and-times-in-go
* _case_: uppercase (available on import) lower (unavailable on import)
* _error handling_: https://benhoyt.com/writings/go-intro/ https://dev.to/web3coach/how-to-handle-errors-in-go-5-rules-2bgf https://rauljordan.com/2020/07/06/why-go-error-handling-is-awesome.html https://github.com/kisielk/errcheck https://medium.com/@jankammerath/how-go-fixed-everything-that-was-wrong-with-programming-1b599a1055a8 https://github.com/kisielk/errcheck
* _types_: bool string int (+ specific types) no type hierarchy [Go in Action 1.1.3]

alias import
```golang
import (
    "rsc.io/quote"
    quoteV3 "rsc.io/quote/v3"
)
```

JSON 
* https://github.com/mailru/easyjson
* https://www.youtube.com/watch?v=Osm5SCw6gPU https://akrabat.com/converting-json-to-a-struct-in-go/ https://eli.thegreenplace.net/2020/representing-json-structures-in-go/ https://www.youtube.com/watch?v=52yMK6p_cAg 
* generate struct from JSON https://mholt.github.io/json-to-go/
* https://github.com/orsinium-labs/jsony
* default values https://github.com/creasty/defaults
```golang
type Book struct {
    Title string `json: "title"`
    Author string `json: "author"`
}
```

## collections

* container pkg: list, ring, heap https://therebelsource.com/blog/exploring-container-package-in-go-list-ring-and-heap/9zTBiMaaYg https://www.dolthub.com/blog/2023-12-01-why-are-go-heaps-confusing/
* _map_: map/dictionary 🗄 `algos.md` https://tour.golang.org/moretypes/22
* _struct_: user-defined type
```golang
// declare (type Book or type struct?)
type Book struct {
    Title string
    Author string
}
// init
book := Book{Title: "Go in Action", Author: "William Kennedy"}
```

* _slice_: resizable; doesn't store array data, but manipulating alters underlying array https://www.openmymind.net/The-Minimum-You-Need-To-Know-About-Arrays-And-Slices-In-Go/ https://github.com/elliotchance/pie
* bad https://build-your-own.org/blog/20241125_go_slice_surprise/ https://0x46.net/thoughts/2024/12/03/go-a-fractal-of-bad-design/
```go
[]bool{true, true, false}  // build array and slice on top all in one go w/ slice literal
// https://tour.golang.org/moretypes/10 --> same syntax as Python
// https://tour.golang.org/moretypes/11 --> length (slice) capacity (length of underlying array)
// https://tour.golang.org/moretypes/16 --> range to loop over slice and get index and value
```

* _array_: fixed size
```go
primes := [6]int{2, 3, 5, 7, 11, 13}
fmt.Println(primes[4]) // 11
mySlice := primes[1:4]
fmt.Println(mySlice) // [3 5 7]
```

## design

📙 Kernighan/Pike practice of programming https://www.amazon.com/Practice-Programming-Addison-Wesley-Professional-Computing/dp/020161586X
> I will finally note that Ken Thompson has a history of designs that look like minimal solutions to near problems but turn out to have an amazing quality of openness to the future, the capability to be improved. Unix is like this, of course. It makes me very cautious about supposing that any of the obvious annoyances in Go that look like future-blockers to me (like, say, the lack of generics) actually are. Because for that to be true, I’d have to be smarter than Ken, which is not an easy thing to believe. http://esr.ibiblio.org/?p=7745

FEATURES 📙 Jeffrey [3]
* concurrency
* more modern than C e.g. modules
* cross-compilation/cross-platform binaries (although trickier re: cgo) https://jvns.ca/til/cross-compiling-in-go-just-works/
* usage: CLI (charm) distributed systems (Docker, Kubernetes, Prometheus)

https://0x46.net/thoughts/2024/12/03/go-a-fractal-of-bad-design/
> And it's not necessarily very readable, at some point your brain just filters out all the boilerplate, sure, but if your brain just filters it out what's the point of typing it out? Just to possibly make a mistake in it?...a lot of the code we write in Go is written just because it has to be written and has nothing to do with what we are doing e.g. endless manual error handling. Using a linter just deals with the symptoms and doesn't solve the underlying problem. Languages should make making mistakes difficult.
> The absolute denial that generics are a useful feature comes to mind. I'm sure those people would also rather use arrays, slices and hash maps which aren't "generic" and require you to .(TypeAssert) the values you get out of them all the time. Want to create some data structures e.g. a heap? Good luck making a type safe library out of it! See, Go is a simple language so it can't have generics because that would make it no longer simple. It's the error prone code with no type safety which forces you to put type assertions all over the place or code mindlessly generated from unreadable templates that's simple!
> writing if err != nil every single time is tiring


---

https://mattjhall.co.uk/posts/go-is-well-designed-actually.html

> That sounds familiar to Go programmers, right? Go is almost brutally pragmatic. It’s not a beautiful language at all, at least on a surface level. Programming language theorists hate it! It may be fine in practice, they say, but it’ll never work in theory. Go is designed to be easy to parse, quick to compile, and simple to implement, just like Unix itself. It’s not aimed at programmers who want to express themselves in rich and byzantine hierarchies of type systems, or who need the compiler to catch all possible bugs. It’s just a plain, non-fancy language for getting useful programs written and running as quickly as possible. I appreciate that about it. https://bitfieldconsulting.com/posts/not-real-developer

https://drewdevault.com/2021/04/02/Go-is-a-great-language.html
* https://drewdevault.com/2018/10/08/Go-1.11.html
* governance https://changelog.com/gotime/333 https://www.youtube.com/watch?v=pLvZRnK2WRE
* https://commandcenter.blogspot.com/2024/01/what-we-got-right-what-we-got-wrong.html
* governance: controlled by Google https://news.ycombinator.com/item?id=27610108 https://drewdevault.com/2022/05/25/Google-has-been-DDoSing-sourcehut.html * https://sourcehut.org/blog/2023-01-09-gomodulemirror/
> If you must read the rest of this document to understand the behavior of your program, you are being too clever. https://go.dev/ref/mem
* is not easy https://www.arp242.net/go-easy.html
* https://golang.design/history/
* https://www.evanmiller.org/four-days-of-go.html
* https://www.fredrikholmqvist.com/posts/articles/brooks-wirth-go/
* releases every 6 months https://golang.org/project/
* https://blog.golang.org/open-source https://news.ycombinator.com/item?id=12889302 https://utcc.utoronto.ca/~cks/space/blog/programming/GoIsGooglesLanguage
* no exceptions
* user-defined inheritance https://www.capitalone.com/tech/software-engineering/go-is-boring/
* composition over inheritance (non-magical, good for maintenance) https://talks.golang.org/2012/splash.article https://python-patterns.guide/gang-of-four/composition-over-inheritance/
* cleanliness: won't compile if formatting guidelines not met, can't import packages that aren't used, can’t declare variables that aren’t used
* speed arbitrage (dev time faster than C, run time faster than dynamic)
* have to build API yourself https://www.arp242.net/go-easy.html https://drewdevault.com/2021/04/02/Go-is-a-great-language.html
> More concisely, I think of Go as an "internet programming language", distinct from the systems programming languages that inspired it. Its design shines especially in this context, but its value-add is less pronounced for other tasks in the systems programming domain - compilers, operating systems, etc https://drewdevault.com/2021/02/21/On-the-traits-of-good-replacements.html
* _pain points_: module system is weird limited to services and CLIs
> Where scripting languages got started as an effective way to write small programs and gradually scaled up, Rust and Go were positioned from the start as ways to reduce defect rates in really large projects. Like, Google’s search service and Facebook’s real-time-chat multiplexer. - http://esr.ibiblio.org/?p=7724
> The single best property of Go is that it is basically non-magical. With very few exceptions, a straight-line reading of Go code leaves no ambiguity about definitions, dependency relationships, or runtime behavior. This makes Go relatively easy to read, which in turn makes it relatively easy to maintain, which is the single highest virtue of industrial programming. - https://peter.bourgon.org/blog/2017/06/09/theory-of-modern-go.html
* Ken Thompson has been right
> I will finally note that Ken Thompson has a history of designs that look like minimal solutions to near problems but turn out to have an amazing quality of openness to the future, the capability to be improved. Unix is like this, of course. It makes me very cautious about supposing that any of the obvious annoyances in Go that look like future-blockers to me (like, say, the lack of generics) actually are. Because for that to be true, I’d have to be smarter than Ken, which is not an easy thing to believe. http://esr.ibiblio.org/?p=7745
* Ken Thompson has been wrong
> To be clear, I'm not saying that I or anyone else could have done better with the knowledge available in the 70s in terms of making a system that was practically useful at the time that would be elegant today. It's easy to look back and find issues with the benefit of hindsight. What I disagree with are comments from Unix mavens speaking today; comments like McIlroy's, which imply that we just forgot or don't understand the value of simplicity, or Ken Thompson saying that C is as safe a language as any and if we don't want bugs we should just write bug-free code. These kinds of comments imply that there's not much to learn from hindsight; in the 70s, we were building systems as effectively as anyone can today; five decades of collective experience, tens of millions of person-years, have taught us nothing; if we just go back to building systems like the original Unix mavens did, all will be well. I respectfully disagree. https://danluu.com/cli-complexity/#maven

## functions

* _naked returns_: return all; don't use for longer functions https://tour.golang.org/basics/7
capitalize function sig to export from package, type-id order in Golang/Python vs. C/Java https://blog.golang.org/gos-declaration-syntax

```go
// basic
func add(x int, y int) int {
    return x + y
}

// omit redundant type info
func add(x, y int) int {
    return x + y
}

// return n items
func swap(x, y string) (string, string) {
    return y, x
}

// naked return returns named values
func multi(num int) (x, y int) {
    x = num + 2  // this doesn't count as a short declaration bc x,y are params
    y = num * 2
    return
}
```

## variables

🔗 https://aardappel.github.io/lobster/C_style%20language%20Cheat%20Sheet%20for%20Lobster.html

* declare: `var x int` https://go.dev/tour/basics/8
* assign: `=` https://gist.github.com/prologic/5f6afe9c1b98016ca278f4d507e65510
* initialize: `var x int = 42` https://go.dev/tour/basics/9
* duck type: `x := 42`; only available within functions https://go.dev/tour/basics/10
```golang
func split(sum int) (x, y int) {
    // no duck typing syntax bc x/y are params and therefore already declared?
	x = sum * 4 / 9
	y = sum - x
	return
}
```
* _zero values_: aka default assignment, defaults; lead to bugs https://news.ycombinator.com/item?id=20266747 https://news.ycombinator.com/item?id=38436999
```golang
var myBool // false
var myString // ""
var myInt // 0
```

# 📦 PACKAGING

🧠 https://chatgpt.com/c/676abaf1-3560-8004-b613-0ac43a0afaa5

---

https://chatgpt.com/c/67327c2b-0a34-8004-9b0a-3c4d6c45dc92
📜 https://golang.org/ref/mod https://github.com/golang/go/wiki/Modules#table-of-contents
🔍 https://pkg.go.dev/
🔗 https://encore.dev/guide/go.mod

start here
* https://www.bytesizego.com/blog/history-of-dependency-management-go
* https://eli.thegreenplace.net/2020/you-dont-need-virtualenv-in-go/
> reinstall go to clean out previous pkgs?
* https://sourcehut.org/blog/2023-01-09-gomodulemirror/
* workspaces https://dev.to/gophers/what-are-go-workspaces-and-how-do-i-use-them-1643
* 📙 Jeffrey distributed [5]
* distribution https://www.kosli.com/blog/how-to-publish-your-golang-binaries-with-goreleaser/

workflow
* _add deps_: import dependency in your module's source and then try to execute your code in some way (build, test) and go will grab the deps https://blog.golang.org/using-go-modules can use `go download` but don't need to (cf. `go help mod download`); `go get -u ./...` https://engineering.kablamo.com.au/posts/2018/just-tell-me-how-to-use-go-modules
* _list deps_: `list -f '{{ .Imports }}'` (top-level) https://dave.cheney.net/2014/09/14/go-list-your-swiss-army-knife `list -m all` (top-level's subs) https://blog.golang.org/using-go-modules `mod download -json` https://stackoverflow.com/a/52082860/6813490 `go list -f '{{ .Deps }}'` (everything) https://dave.cheney.net/2014/09/14/go-list-your-swiss-army-knife https://www.reddit.com/r/golang/comments/bdtrti/best_way_to_visualize_library_dependencies_with/
* commands https://kadekillary.work/note/go/
```sh
# create module path
init

# rm unused
mod tidy
```

upgrade
* _psuedo-version_: untagged commit
* latest tagged: `go get <mod>`; defaults to `@latest` https://blog.golang.org/using-go-modules 'upgrading dependencies'
* list versions: `go list -m -versions <mod>`
* get specific version: `go get <mod>@<version>`
* versioning gotcha https://donatstudios.com/Go-v2-Modules https://qvault.io/2020/09/15/gos-major-version-handling-sucks-from-a-fanboy/

misc
* `get`: download and compile module; use global cache (`bin`, `pkg`) https://www.youtube.com/watch?v=71hgdExuCbg 3:50 ❓ dep hell avoided by per-project lockfile? https://dev.to/tbpalsulich/why-go-modules-are-faster-than-gopath-blj
* `install`: compile module; subset of `go get` https://stackoverflow.com/q/24878737 
* _distribution_: https://github.com/goreleaser/goreleaser
* find outdated deps https://github.com/psampaz/go-mod-outdated

design, legacy
* no central repo like PyPI or NPM https://nullprogram.com/blog/2020/01/21/ https://brandur.org/golang-packages 
* 📍 https://blog.golang.org/module-compatibility
* $GOPATH was weird https://news.ycombinator.com/item?id=17061713 
* road to modules: prelim module support in 1.11 and default from 1.13 https://blog.golang.org/using-go-modules https://blog.golang.org/versioning-proposal previous approaches included dep (from Go 1.9-1.10) and Glide https://brandur.org/golang-packages 

* projects move versions more slowly https://benjamincongdon.me/blog/2019/11/11/The-Value-in-Gos-Simplicity
* language seems somewhat Clojure like i.e. doesn't especially encourage using a ton of deps
> Note that while the go command makes adding a new dependency quick and easy, it is not without cost. Your module now literally depends on the new dependency in critical areas such as correctness, security, and proper licensing, just to name a few. - https://blog.golang.org/using-go-modules

* _vendoring_: 🗄 `system.md` https://engineering.kablamo.com.au/posts/2018/just-tell-me-how-to-use-go-modules https://www.youtube.com/watch?v=AIo0UBcvnPg
* _minimum version selection (MVS)_: get the lowest version that will satisfy needs i.e. if `go.mod` needs 1.2 Go won't download an available higher version https://ukiahsmith.com/blog/a-gentle-introduction-to-golang-modules/

* _semantic import versioning_: what would be a new major version of same package in semver becomes a new module https://research.swtch.com/vgo-import 'adding a dependency on a new major version'
> At the same time, allowing different major versions of a module (because they have different paths) gives module consumers the ability to upgrade to a new major version incrementally. In this example, we wanted to use quote. Concurrency from rsc/quote/v3 v3.1.0 but are not yet ready to migrate our uses of rsc.io/quote v1.5.2. The ability to migrate incrementally is especially important in a large program or codebase. - https://blog.golang.org/using-go-modules

## previous writeup

Ok, here are some preliminary thoughts after approx. 5 hours of reading about and tinkering with dependency management in Golang:

### GOPATH is not dead

* In the past all Go code lived at `$GOPATH`. Your project's source code, its dependencies, everything. Putting your code somewhere else was possible but irksome.
* Now you can put your _source_ code somewhere else.
* But: you still need `$GOPATH` to exist on your machine, in part because [that's where project dependencies are still downloaded to](https://dave.cheney.net/2018/07/14/taking-go-modules-for-a-spin). Your dependencies are per-project and I assume there's a way to inspect deps in `$GOPATH` to figure out which belong to which project, but it's less clear that Python virtual environments, either done with `venv` ("here's a folder in your project with all your deps") or Poetry (`poetry env info`).

### Python devs have it worse

If only because Golang is further along its trajectory of packaging solutions:

* initial attempt: Go had `go get` and `$GOPATH`, Python has `pip`, things work ok but there's room for improvement
* candidate solutions: Go had `dep` and Glide, Python has `venv` and Poetry and pipenv and pip-tools and dephell (forgetting anyone?)
* winner emerges: Go has modules now, but Python is still tbd as the above candidates continue to fight it out.

So, at least Golang devs are all speaking the same language when it comes to packaging.

### Golang is contra-consensus on packaging in general

* Gooooo slooooooow: Library development moves much more slowly, for the better (more stable packages?) but possibly for the worse as well (less new, shiny things?). Read more here: [link](https://benjamincongdon.me/blog/2019/11/11/The-Value-in-Gos-Simplicity).

* Anti-dependency dependency mgmt: The community seems somewhat akin to Clojure insofar as it doesn't especially encourage using a ton of dependencies. Python appears to be going to the other direction, to judge by the [dead batteries debate](https://pyfound.blogspot.com/2019/05/amber-brown-batteries-included-but.html). Other popular languages feel just as library-dependent than Python. But in the Golang documentation on their packaging tool, they include [an admonition to beware using packages](https://blog.golang.org/using-go-modules):
> Note that while the go command makes adding a new dependency quick and easy, it is not without cost. Your module now literally depends on the new dependency in critical areas such as correctness, security, and proper licensing, just to name a few.

## semantics

---

* _source file_: `.go` file https://golang.org/doc/code.html https://golang.org/ref/spec#Packages
* _package_: dir w/ n source files https://rakyll.org/style-packages/ https://golang.org/ref/spec#Packages
* _module_: n pkg + `go.mod` https://blog.golang.org/using-go-modules seems synonymous w/ 'repo' https://blog.golang.org/using-go-modules
* `go.sum`: lock file; check into version control https://blog.golang.org/using-go-modules
* `main`: `func main` (entry point, necessary to compile to bin) `package main` (holds `func main`) `main.go` (holds `func main`) https://www.callicoder.com/golang-packages/
* _import path_: namespace https://stackoverflow.com/q/46312734/6813490 https://blog.golang.org/using-go-modules
* _module path_: seems like same thing as 'import path' https://engineering.kablamo.com.au/posts/2018/just-tell-me-how-to-use-go-modules https://golang.org/ref/mod#tmp_2 required if you're outside $GOPATH https://blog.golang.org/using-go-modules
* _module cache_: where modules get downloaded to `$GOPATH/pkg/mod` https://stackoverflow.com/a/52082860 https://stackoverflow.com/a/52127364 ❓ seems like you can only blow away the entire module cache (`clean -modcache`) vs. the Poetry approach of deleting per project https://github.com/golang/go/issues/32976

## workspaces

## modules

---

GO.MOD
* human-readable list of deps
* check into version control https://blog.golang.org/using-go-modules
* only lists direct dependencies https://blog.golang.org/using-go-modules 'adding a dependency'
* necessary for module outside `$GOPATH/src`
* defaults to latest version of module if you don't specify https://blog.golang.org/using-go-modules 'adding a dependency'
* _directive_: keyword for each line e.g. `go` (version https://golang.org/ref/mod#tmp_11)
* `indirect`: subdependency https://blog.golang.org/using-go-modules won't be written to `go.mod` unless you perform an upgrade; what *seems* to be happening in the tutorial is that `golang.org/x/text` is a subdep and its parents (`rsc.io/quote`) doesn't specify its version so we just grab latest version which happens to be pseudo version, but when you run `go get golang.org/x/text` it grabs the latest tagged version (which actually should be less recent than the pseudo version, right? otherwise why wouldn't parent dep just specify the stable older version it wanted) and therefore because we're being more specific we have to write it to `go.mod`

https://go.dev/doc/modules/layout
> With Go 1.14 Go Modules are finally ready for production. Use Go Modules unless you have a specific reason not to use them and if you do then you don’t need to worry about $GOPATH and where you put your project. The basic go.mod file in the repo assumes your project is hosted on GitHub, but it's not a requirement. The module path can be anything though the first module path component should have a dot in its name (the current version of Go doesn't enforce it anymore, but if you are using slightly older versions don't be surprised if your builds fail without it). See Issues 37554 and 32819 if you want to know more about it. https://github.com/golang-standards/project-layout

## env var

```sh
$ echo $GOPATH  # if env var not set, default to output of go env GOPATH
$ go env GOPATH  # /Users/zvalenta/go
```

---

can you explain the following to me?
```sh
$ GOBIN
$ GOENV
$ GOROOT
$ GOPATH
```

* flags https://github.com/peterbourgon/ff
* _GO111MODULE_: off (modules outside $GOPATH) https://golang.org/doc/code.html on (modules w/in $GOPATH) https://www.youtube.com/watch?v=H_4eRD8aegk @ 2:54 🗄 `go111.log`
* _GOBIN_: location for `go install`; defaults to `$GOPATH/bin`; set w/ `go env -w GOBIN="$PWD"` https://golang.org/doc/code.html#Command
* _GOENV_: config location
* _GOROOT_: where Go is installed https://stackoverflow.com/a/30295306/6813490
* _GOPATH_: still used but only by the Go installation at large, not for package management https://ukiahsmith.com/blog/a-gentle-introduction-to-golang-modules/ previously pointed to central location (typically `~/go`) for all Go code (src, deps) holding 3 directories (`src`, `pkg`, `bin`) https://golang.org/doc/gopath_code.html

## installs

trying to find out if/where Go CLIs on my machine

```sh
$ find /usr/local/bin /usr/bin -type f -perm -u+x | grep -i go  # nada
```

## project structure

https://www.alexedwards.net/blog/how-to-manage-tool-dependencies-in-go-1.24-plus
> The standard way to do testing is to have a foo.go and foo_test.go file next to each other. https://www.arp242.net/jia-tan-go.html

```sh
├── dir
│   └── go.mod
│   └── foo.go
│   └── foo_test.go
```

STANDARDS
* big projects https://github.com/golang-standards/project-layout
* tooling https://github.com/Melkeydev/go-blueprint

PKG
* https://github.com/jesseduffield/lazygit/tree/master/pkg
* https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/

ZA
* `internal`: cannot be imported https://www.bytesizego.com/blog/golang-internal-package

---

* project structure for CLI and testing https://github.com/quii/learn-go-with-tests https://eli.thegreenplace.net/2022/file-driven-testing-in-go/ https://sourcegraph.com/notebooks/Tm90ZWJvb2s6MTM2Nw==
* https://lets-go.alexedwards.net/
* https://gist.github.com/candlerb/3cb11576b2d73800b58f3b548dc2ba4a

https://appliedgo.com/blog/go-project-layout

https://docs.go-blueprint.dev/

https://github.com/bbkane/shovel
https://go.dev/blog/gonew
https://golangweekly.com/link/146368/web
https://avivcarmi.com/finding-the-best-go-project-structure-part-1/
https://boyter.org/posts/how-to-start-go-project-2023/
https://github.com/create-go-app/cli
https://autostrada.dev/

https://github.com/mikestefanello/pagoda
https://autostrada.dev/

https://eli.thegreenplace.net/2019/simple-go-project-layout-with-modules/ https://github.com/golang-standards/project-layout/issues/117 https://github.com/golang/go/issues/45861
https://christine.website/blog/within-go-repo-layout-2020-09-07 https://github.com/golang-standards/project-layout https://commandercoriander.net/blog/2017/12/31/writing-go/ https://eli.thegreenplace.net/2019/simple-go-project-layout-with-modules/ https://bencane.com/stories/2020/07/06/how-i-structure-go-packages/#/3 simple https://github.com/healeycodes/conways-game-of-life  https://bencane.com/2020/12/29/how-to-structure-a-golang-cli-project/ https://adhoc.team/2021/03/29/simple-web-app-in-golang/

```sh
# MAIN
├── cmd/  #  python my_script.py
├── internal/  #  _internal 
├── pkg/  #  code that code also be used by other projects; 类似 Django app https://commandercoriander.net/blog/2017/12/31/writing-go/
├── vendor/  #  venv

# ANCILLARY
├── api/  #  Swagger
├── build/  #  Dockerfile, .gitlab-conf.yaml
├── config/  #  conf files I guess
├── init/  #  systemd
├── web/  #   js
```

* start here https://blog.ultirequiem.com/chigo#heading-starting-the-project
```sh
mkdir chigo
go mod init github.com/UltiRequiem/chigo
mkdir internal pkg cmd
touch pkg/root.go internal/root.go cmd/root.go
tree
├── cmd        # main
│   └── root.go
├── go.mod
├── internal   # business logic
│   └── root.go
└── pkg        # util
    └── root.go
```
```golang
// sketch of pkg

from "internal" import printFromStdin, printWithColors

help, fileArguments, files = parametersAndFlags()

if help {
   printHelp()
   exit()
}

if fileArguments {
   filesText = joinFiles(files)
   printWitColors(filesText)
   exit()
}

printFromStdin()
```
```golang
// take list of files and get text from them
package internal

import "os"

func JoinFiles(files []string) (string, error) {
    text := ""

    for _, file := range files {
        fileText, err := os.ReadFile(file)

        if err != nil {
            return "", err
        }

        text += string(fileText) + "\n"
    }

    return text, nil
}

```

## version mgmt

---

> homebrew conflict?

INSTALLATION
* ✅ use golang.org https://golang.org/doc/install#download
* uninstall: rm `~/go`, `/usr/local/go` https://golang.org/doc/install#uninstall
* use pkg manager https://quii.gitbook.io/learn-go-with-tests/go-fundamentals/install-go https://howistart.org/posts/go/1/ 
* pkg manager bundles tooling (compile, cover, doc)
> my version is Homebrew
* tooling location: `go env GOTOOLDIR` https://golang.org/doc/install#install 🗄 `go help environment`

VERSION MGMT
* ✅ just use version name https://go.dev/doc/manage-install
* version mgmt tool https://github.com/moovweb/gvm

# 📔 STDLIB

🔍
* https://threedots.tech/post/list-of-recommended-libraries/
* https://github.com/avelino/awesome-go

> https://matthewsanabria.dev/posts/start-with-the-go-standard-library/

* used in Python https://last9.io/blog/using-golang-package-in-python-using-gopy/
* datetime https://github.com/golang-module/carbon https://github.com/olebedev/when
* game engine https://ebiten.org/
* GUI https://github.com/fyne-io/fyne https://github.com/AllenDang/giu https://github.com/gizak/termui
* _datetime_: https://github.com/dromara/carbon
* _debug_: can use gdb but delve recommended https://golang.org/doc/gdb https://www.youtube.com/watch?v=r033vEzL6a4
* _env var_ https://endaphelan.me/guides/golang/a-no-nonsense-guide-to-environment-variables-in-go/ https://github.com/caarlos0/env https://github.com/joho/godotenv https://github.com/knadh/koanf to structs https://github.com/caarlos0/env
* _fake data_: https://github.com/brianvoe/gofakeit
* _feature flag_: https://github.com/thomaspoignant/go-feature-flag
* _file system_: https://github.com/spf13/afero
* _Excel_: https://github.com/360EntSecGroup-Skylar/excelize https://xuri.me/excelize/
* _filesystem_: https://github.com/spf13/afero
* _Git_: https://github.com/go-git/go-git
* _GraphQL_: https://gqlgen.com/ https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/
* _GUI_: https://gioui.org/ https://anvil-editor.net/
* _lint_: https://github.com/golangci/awesome-go-linters
* _logging_ https://github.com/bloom42/rz-go https://github.com/charmbracelet/log
* _Markdown_: https://github.com/yuin/goldmark
* _math_: https://github.com/montanaflynn/stats
* _profile_ https://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go https://blog.golang.org/profiling-go-programs https://marcan.st/2017/12/debugging-an-evil-go-runtime-bug https://artem.krylysov.com/blog/2017/03/13/profiling-and-optimizing-go-web-applications/ https://github.com/DataDog/go-profiler-notes/blob/main/guide/README.md https://notes.eatonphil.com/implementing-a-jq-clone-in-go.html https://eli.thegreenplace.net/2023/common-pitfalls-in-go-benchmarking/ https://www.willem.dev/articles/benchmarks-performance-testing/
* _refactoring_: http://blog.ralch.com/tutorial/golang-tools-refactoring/ http://www.gorefactor.org/
* _REPL_: https://github.com/cosmos72/gomacro https://stackoverflow.com/questions/8513609/does-go-provide-repl https://golangweekly.com/link/146377/web
* _search_ https://blevesearch.com/
* _security_ https://github.com/securego/gosec
* _serialization_: https://github.com/bytedance/sonic
* _testing_: https://github.com/stretchr/testify https://eli.thegreenplace.net/2020/faking-stdin-and-stdout-in-go/ https://www.youtube.com/channel/UC2GHqYE3fVJMncbrRd8AqcA/videos https://quii.gitbook.io/learn-go-with-tests/ mock db https://github.com/cockroachdb/copyist/ mocks https://github.com/stretchr/testify https://github.com/vektra/mockery https://github.com/jarcoal/httpmock https://www.youtube.com/watch?v=U-eO9_lNi7w https://github.com/gotestyourself/gotestsum visualize https://github.com/roblaszczak/vgt
* time https://github.com/mergestat/timediff
* _TOML_: https://github.com/pelletier/go-toml
* _YAML_: https://github.com/goccy/go-yaml

## web

* HTTP https://github.com/go-chi/chi
* https://pocketbase.io/ 
* https://echo.labstack.com/
* start here https://www.youtube.com/watch?v=F9H6vYelYyU
* https://github.com/mikestefanello/pagoda
* https://github.com/nikolaydubina/go-recipes
* https://github.com/livebud/bud
* https://www.allhandsontech.com/programming/golang/web-app-sqlite-go/
* URL shortener https://jrstupkadev.medium.com/golang-url-shortener-22ba6c970792 https://blog.pratimbhosale.com/building-a-url-shortener-using-go-and-sqlite#heading-project-setup

* basic
```golang
package main

import "net/http"

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		w.Write([]byte("Hello, Go"))
	})
	http.ListenAndServe(":8000", nil)
}
```
* OpenAPI https://github.com/danielgtaylor/huma
* https://github.com/carlmjohnson/requests
* https://news.ycombinator.com/item?id=39318867
* https://www.allhandsontech.com/programming/golang/web-app-sqlite-go/
* app config https://github.com/spf13/viper
* https://github.com/go-chi/chi
* vanilla https://eli.thegreenplace.net/2021/life-of-an-http-request-in-a-go-server/
* _db_: https://github.com/cvilsmeier/go-sqlite-bench `database/sql` (SQLAlchemy engine) gorm (SQLAlchemy ORM) https://eli.thegreenplace.net/2019/to-orm-or-not-to-orm/ https://www.calhoun.io/using-postgresql-with-go  https://github.com/go-reform/reform https://entgo.io/ https://github.com/upper/db in mem KV https://github.com/sdslabs/kiwi generate SQL https://github.com/Masterminds/squirrel CLI https://upper.io/v4/ query builder https://github.com/doug-martin/goqu https://pboyd.io/posts/5-ways-to-write-a-go-database-model/ ORM https://github.com/uptrace/bun
* _microservice_: https://github.com/micro/micro https://blog.m3o.com/2020/11/16/building-a-blog-with-micro.html
* frameworks: Buffalo, Gin, Echo; hot reload for Gin https://github.com/cosmtrek/air https://github.com/go-goyave/goyave https://github.com/cloudwego/hertz
* routing: https://benhoyt.com/writings/go-routing/
* servers: https://eli.thegreenplace.net/2021/rest-servers-in-go-part-1-standard-library/
* https://github.com/go-goyave/goyave
* https://www.honeybadger.io/blog/go-web-services/ https://www.youtube.com/channel/UC2GHqYE3fVJMncbrRd8AqcA/videos https://www.usegolang.com/sample/?__s=aqtioiz6aumf2qzwpp96 https://www.youtube.com/playlist/?__s=aqtioiz6aumf2qzwpp96&list=PLVEltXlEeWglOJ42pCxf22YVyxkzan3Xg https://www.usegolang.com/ https://www.youtube.com/playlist/?__s=aqtioiz6aumf2qzwpp96&list=PLVEltXlEeWglOJ42pCxf22YVyxkzan3Xg  https://github.com/go-resty/resty https://github.com/gojek/heimdall https://benhoyt.com/writings/go-routing/ https://github.com/projectdiscovery/httpx

# 🟨 ZA

CMDS
* _docs_: `doc <mod>` https://blog.golang.org/using-go-modules
* _run_: `run <path/to/file>`
* _binary_: create (`build`) create and mv to `$GOPATH/bin` (`install`) https://www.zombiezen.com/blog/2020/09/how-i-packaged-go-program-windows-linux/
* _rm_: `go clean` ❓ rm what?

---

* toolchain https://go.dev/doc/toolchain

* commands https://github.com/nikolaydubina/go-recipes
* _documentation_: https://blog.golang.org/go.dev https://blog.golang.org/pkg.go.dev-2020
* _gotchas_: http://devs.cloudimmunity.com/gotchas-and-common-mistakes-in-go-golang/
* _memory allocation_: https://blog.learngoprogramming.com/a-visual-guide-to-golang-memory-allocator-from-ground-up-e132258453ed https://notes.eatonphil.com/implementing-a-jq-clone-in-go.html
* _OO_: http://patshaughnessy.net/2015/9/25/what-do-perl-and-go-have-in-common
* _Python_: https://news.ycombinator.com/item?id=22304131
* _style_: https://github.com/golang/go/wiki/CodeReviewComments
* plugins https://eli.thegreenplace.net/2021/plugins-in-go/
