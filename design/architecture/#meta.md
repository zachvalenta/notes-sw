# ⛩️

## 参考

🗄️ `science.md` complexity
📚
* Buelta python architecture
* Dibernardo 500 lines http://aosabook.org/en/index.html
* Ford fundamentals of software architecture
* Ford/Sadalage evolutionary architectures https://www.youtube.com/watch?v=atwwf0qWpYg https://www.amazon.com/Software-Architecture-Metrics-Studies-Improve/dp/1098112237 https://www.amazon.com/gp/product/1492086894/ref=ox_sc_saved_image_10
* ✅ Jackson essence of software https://www.amazon.com/Essence-Software-Concepts-Matter-Design/dp/0691225389 https://www.hytradboi.com/2025/840b0b92-720e-4c0c-9760-19739d3832a5-back-to-modularity buddies with Jonathan Edwards https://alarmingdevelopment.org/ https://youtu.be/BdoWZPvfZSE https://www.geoffreylitt.com/
* Martin clean architecture

## 进步

* _19_: URL shortener

---

UNCLE BOB
* https://www.youtube.com/watch?v=qdcamTUcuAQ
* http://cleancoder.com/books
* https://x.com/unclebobmartin
* https://blog.cleancoder.com/
* https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure-ebook/dp/B075LRM681
* https://www.amazon.com/Functional-Design-Principles-Patterns-Practices-ebook/dp/B0CGHQKGYG

testing https://www.thediff.co/archive/antithesis-debugging-debugging/ https://antithesis.com/ https://www.thediff.co/archive/offshoring-and-ai-agents/ https://registerspill.thorstenball.com/p/joy-and-curiosity-19
Kleppmann https://www.davidreis.me/2024/designing-data-intensive-applications
https://www.davidreis.me/2024/what-happens-when-you-make-a-move-in-lichess https://news.ycombinator.com/item?id=41922928
https://drewdevault.com/2021/10/17/Reliability.html
https://drewdevault.com/2020/10/09/Four-principles-of-software-engineering.html
https://drewdevault.com/2020/11/06/Utility-vs-usability.html

* algos https://www.youtube.com/watch?v=xbgzl2maQUU
* phases https://buttondown.com/hillelwayne/archive/requirements-change-until-they-dont/

## 2025.04.12

APP
* 类似: construction
* what you do: coding
* what you worry about: frameworks, execution

ARCHITECTURE
* 类似: architecture
* what you do: designing
* what you worry about: correctness, perf

SYSTEM
* 类似: urban planning
* what you do: diagrams / conf
* what you worry about: distributed

# ⭕️ FACTORS

---

* use greppable names https://registerspill.thorstenball.com/p/use-data-that-looks-like-data
* write code that's easy to throw away
> Write code to be changed and/or deleted. This comes from someone who's worked in startups for the past 5 years. We often overestimate how long code =is supposed to live. We as programmers often exaggerate with our DRY and stuff, we do not want to repeat ourselves, we want to find another abstraction...we want to find some general that can help us abstract stuff away. My piece of advice is that, step back and consider for a moment that this code is not going to stay in, so maybe only try and find the abstraction layer once you really sure that this is how it's going to be. - Thorsten Ball https://developeronfire.com/podcast/episode-373-thorsten-ball-interpreters-compilers-and-writing https://news.ycombinator.com/item?id=41968409

https://drewdevault.com/2019/04/29/Shut-up-and-get-back-to-work-style.html

* hoisting

> This is what I’ve started telling people: Use mostly functions, try to make most of them pure. I think that can get people (even new devs) 80% of the benefits (testability, composability, loose coupling, and the ability to reason about code) of more complicated, prescriptive architectures (Hexagonal, Onion, Ports & Adapters, Clean, etc) with a minimal amount of ramp up. https://news.ycombinator.com/item?id=24915497

## clarity

🗄️
* blog / opinions.md
* `biology.md` memory

* Clarity trumps all other concerns. We're building informatio systems. 📻 DHH (STT) https://www.youtube.com/watch?v=9LfmrkyP81M
> I used to tolerate and expect complexity. Working on Go the past 10 years has changed my perspective, though. I now value simplicity above almost all else and tolerate complexity only when it's well isolated, well documented, well tested, and necessary to make things simpler overall at other layers for most people. - Brad Fitzpatrick (Go team member 2010-2020) https://golangweekly.com/issues/533
* Clarity matters even more when things are comlicated.
> And it's not only high performance hardware and software that's complex. Some domains are just really complicated. The tax code is 73k pages long. It's just not possible to reason effectively about something that complicated, and there are plenty of things that are that complicated. https://danluu.com/tests-v-reason/

---

* Richard Gabriel worse is better https://www.jwz.org/doc/worse-is-better.html https://bitfieldconsulting.com/posts/not-real-developer https://www.youtube.com/watch?v=lHZtq5IheBI
> Simplicity beats even strict correctness, in this view: it’s better to be simple (and handle the easy 90% of cases in a nice way) than to be totally correct (and handle the awkward edge cases, at the expense of making the code much more complex).

https://www.ntietz.com/blog/the-most-important-goal-in-designing-software-is-understandability/

KISS
* https://github.com/Olshansk/postgres_for_everything
* hidden control flow, PHP vs. Zig https://news.ycombinator.com/item?id=42203084

尝试
* complicated by not complex
* simple but not easy
* a straight line but many steps

## maintainable

* _maintainability_: other devs able to work on system
> it is well know that the majority of the cost of software is not in its intial development, but its ongoing maintenance 📙 Kleppmann [18] https://www.jefftk.com/p/designing-low-upkeep-software
* _evolvability_: ability to change different parts of system independently [Kleppmann 4.128]

---

SINGLE SERVER https://alexanderpetros.com/web-services
* Many web services experience traffic loads that can be handled by a single server
* Many web services have requirements that can be met with HTML and little to no JavaScript
* Many people believe, incorrectly, that (1) or (2) does not apply to their web service
* A web service that adheres to (1) and (2) is orders of magnitude cheaper to maintain than one which does not, and often provides a better user experience

SKETCHING
> In the intersection of the hardware and software industry, we just continuously run into [patterns like this]. A lot of things are defined by finding some process that works, scaling it up 10x and then it breaking in ways that you did not realize things could break. https://www.complexsystemspodcast.com/episodes/boom-busts-and-long-term-progress-with-byrne-hobart-2/

---

> "Bad engineering" in adhoc ways tends to mean new ideas are being explored. Sophisticated deployments, logistics, procedures, tends to mean you're optimizing or extending existing system. That's not to disparage the latter. making things work at scale is hard engineering. But when people praise the glory days, it may be a preference for working on new ideas in small projects. https://news.ycombinator.com/item?id=41278907

* boring technology https://simonwillison.net/2024/Jul/13/give-people-something-to-link-to/
* aka transitional architecture https://www.thoughtworks.com/radar/techniques?blipid=202203071
> But the cultural tides are strong. Building a company on Django in 2020 seems like the equivalent of driving a PT Cruiser and blasting Faith Hill’s “Breathe” on a CD while your friends are listening to The Weeknd in their Teslas. Swimming against this current isn’t easy, and not in a trendy contrarian way. https://macwright.com/2020/05/10/spa-fatigue.html
* https://martinfowler.com/bliki/Yagni.html https://www.jefftk.com/p/designing-low-upkeep-software
* https://thorstenball.com/blog/2020/09/15/the-context-in-which-we-build-software/
* https://news.ycombinator.com/item?id=26071906
* boring tech has well-understood failure modes https://news.ycombinator.com/item?id=23444594 https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/
* https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/
* https://josephg.com/blog/databases-have-failed-the-web/
* https://twitter.com/b0rk/status/1229860328139296768
* https://wizardzines.com/about/
* https://blog.cerebralab.com/Imaginary_Problems_Are_the_Root_of_Bad_Software https://blog.cerebralab.com/Stop_future_proofing_software
* https://blog.cerebralab.com/Bimodal_programming_%E2%80%93_why_design_patterns_fail
* https://www.benkuhn.net/progessays/
* one dev's edge cases are another's entire project 📙 Kleppmann 491
* listen to Knuth -> fast code matters less than you think https://www.youtube.com/watch?v=PhUb7y9WZGs
> We should forget about small efficiencies, say about 97% of the time; premature optimization is the root of all evil. - Donald Knuth
> To be attractive to hackers, a language must be good for writing the kinds of programs they want to write. And that means, perhaps surprisingly, that it has to be good for writing throwaway programs. - http://paulgraham.com/popular.html
* don't cargo cult 'best practices'
> Sophisticated design principles can make your code faster, more flexible, more modular, and all of the other positive adjectives that people use to describe high-quality software. But they also make it more complex. `AbstractSyntaxRenderers` and `DoubleBackflipDatabaseTransmogrophiers` do make some programs clearer and easier to understand, especially large ones. But they can also be the equivalent of using a metrics-oriented, fully agile, stakeholder-prioritized development flow for working on a jigsaw puzzle with your dad. Sure you’re following best practices, but you probably didn’t need to, and now your dad thinks you’re a Scientologist. - https://robertheaton.com/2018/12/02/programming-project-5-snake/
* wait for shared concerns to emerge -> repeat yourself until you find the right abstraction https://programmingisterrible.com/post/176657481103/repeat-yourself-do-more-than-one-thing-and
> There seemed to be a tendency to extract tiny packages first instead of waiting for a shared concern to emerge from the code and only then extracting a package. https://commandercoriander.net/blog/2017/12/31/writing-go/
> The problem with always using an abstraction is that you’re preemptively guessing which parts of the codebase need to change together. “Don’t Repeat Yourself” will lead to a rigid, tightly coupled mess of code. Repeating yourself is the best way to discover which abstractions, if any, you actually need.
> Beware of arguments related to programming speed. All things being equal, faster is better. But all things are never equal. Do you need the kind of speed that lets you get a website up and running quickly? Or the kind that allows you to rotate a few thousand polygons in 3D in real time? Do you need to convert 10,000 PDFs into text per hour? Or 10 million PDFs into text once? These are different problems. - Ford what is code?

# 💡 IDEAS

## composition

WHY PREFERRED OVER INHERITANCE
* parent changes can require child update
```python
class Burger:
    def __init__(self, size='regular'):  # add size
        self.size = size
class BurgerFactory(Burger):
    def __init__(self):
        super().__init__()  # now child init needs to add as well
```
* you have to know about parent's implementation

---

* _composition_:
* Gang of Four: composition over inheritance https://en.wikipedia.org/wiki/Design_Patterns
> They warn that the implementation of a subclass can become so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change. Furthermore, they claim that a way to avoid this is to inherit only from abstract classes—but then, they point out that there is minimal code reuse...using inheritance is recommended mainly when adding to the functionality of existing components, reusing most of the old code and adding relatively small amounts of new code. https://buttondown.com/hillelwayne/archive/when-to-prefer-inheritance-to-composition/
* _delegation_: composition by another name https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/#delegation-in-oop
* https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/

## coupling / cohesion

* https://www.youtube.com/watch?v=uWTvMCra-_Y
* https://everydaysuperpowers.dev/articles/preventing-painful-coupling/
* https://blog.bytebytego.com/p/coupling-and-cohesion-the-two-principles
* https://jerf.org/iri/post/2025/go_layered_design/
> how to brag about being a good architect https://jerf.org/iri/post/about/#blog

## dependency injection (DI)

🗄️ `python/logic.md` metaprogramming

---

Dependency Injection: Inversion of control
> Can sometimes replace patterns like Singleton and Factory by handling object lifecycles and dependencies.
> As a general rule of thumb, each layer uses the directly underlying layer to access and interact with the data. As an example, the commands package will not directly use the bug or repository package. It will request the data from the cache layer and go from there. Of course, the commands package will ultimately use types defined in the lower level package like Bug, but retrieving and changing the data has to go through the cache layer to ensure that bugs are properly deduplicated in memory. https://github.com/git-bug/git-bug

https://www.openmymind.net/Dependency-Injection-In-Go/
* https://github.com/hynek/svcs/ https://svcs.hynek.me/en/stable/ https://www.youtube.com/watch?v=d1elMD9WgpA
* https://github.com/uber-go/fx
* https://www.youtube.com/watch?v=uWTvMCra-_Y
* https://www.youtube.com/watch?v=0yc2UANSDiw
* _dependency injection_: passing args [Conery 282] https://en.wikipedia.org/wiki/Dependency_inversion_principle https://en.wikipedia.org/wiki/SOLID
* why?: loose coupling http://kc.my-junk.info/di-ioc-dip https://www.youtube.com/watch?v=sD94szvFqGw
* https://blog.thea.codes/my-python-testing-style-guide/
* https://testdriven.io/blog/python-dependency-injection
* https://github.com/ZechCodes/Bevy
* https://hakibenita.com/python-dependency-injection
* https://romantomjak.com/posts/testing-python-code-that-makes-http-requests.html
* https://docs.pytest.org/en/latest/fixture.html#fixture
* https://github.com/google/gin-config https://calmcode.io/course/gin/intro-to-gin
* in Python https://io.made.com/dependency-injection-with-type-signatures-in-python/ + https://moltenframework.com/v0.7.3/index.html + https://github.com/ekiro/haps + https://github.com/Dobiasd/enterprython/blob/master/why_you_want_formal_dependency_injection_in_python_too.md https://pythonbytes.fm/episodes/show/112/don-t-use-the-greater-than-sign-in-programming
* _dependency inversion_: is this a separate thing https://minds.md/zakirullin/cognitive

## IoC

---

* _inversion of control(IoC)_: you're not in charge of app control flow, only hooking into it https://www.baeldung.com/running-setup-logic-on-startup-in-spring example of IoC https://seddonym.me/2019/08/03/ioc-techniques/ https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way https://stackoverflow.com/questions/3058/what-is-inversion-of-control https://engineering.snagajob.com/dont-like-dependency-injection-898de93dc8d3 https://stackoverflow.com/a/2465052/6813490 https://stackoverflow.com/a/51117857/6813490 https://stackoverflow.com/a/140655/6813490 https://www.objc.io/issues/11-android/dependency-injection-in-java/ https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ ❓ pull in class deps all in one place [Conery 287]
> What is the glue that holds Django together? As a beginner entering, there really is no obvious central object to inspect, extend, or modify. https://www.reddit.com/r/Python/comments/olech/is_django_considered_pythonic_now/

Common IoC Implementations
* Dependency Injection (most common)
* Template Method pattern
* Strategy pattern
* Observer pattern
* Event-driven programming

## plugins

extensible https://pycon-archive.python.org/2024/schedule/presentation/78/index.html
https://pluggy.readthedocs.io/en/stable/
https://docs.datasette.io/en/stable/plugins.html

```txt
Hollywood Principle: "Don't call us, we'll call you." The main application defines hook specifications, and plugins register themselves without the core application needing to know them in advance.

1. Observer: While not a strict observer pattern, Pluggy enables callbacks where plugins can react to hook calls, similar to event listeners
2. Strategy: Plugins act as replaceable strategies that modify or extend behavior at runtime.
3. Dependency Injection: The hook system allows late binding of behavior via plugins, which is a form of dependency injection (DI) but at an architectural rather than class level
4. Microkernel: aka Hexagonal/Ports & Adapters; applications using Pluggy can be structured as a minimal core (microkernel) with plugins extending functionality.

pytest uses Pluggy for its extensive plugin system.
tox and other tools use Pluggy for defining hooks that external tools can implement.
```

## SOLID

---

https://blog.bytebytego.com/p/mastering-oop-fundamentals-with-solid
* _SOLID_: https://www.youtube.com/watch?v=ywDxJbULcdM
* beware theologians https://news.ycombinator.com/item?id=26492798
* _patterns_: MVC, hexagonal https://blog.carlmjohnson.net/post/2020/go-cli-how-to-and-advice/ https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749 https://www.youtube.com/watch?v=I5c7fBgvkNY

# ⠎ PATTERNS

* top 5 https://www.youtube.com/watch?v=f6zXyq4VPP8
* https://news.ycombinator.com/item?id=26300191
* https://github.com/DovAmir/awesome-design-patterns

WALKTHROUGHS
* https://www.youtube.com/channel/UCDankIVMXJEkhtjv5yLSN4g/videos
* https://www.youtube.com/playlist?list=PL8hP5HjAnJ3_mT7IHXjlbpYX_xiz4v_kP
* Heroku clone https://www.youtube.com/watch?v=zhJLVFR3pE8
* Netflix clone https://www.youtube.com/watch?v=gbyYXgiSgdM
* Facebook clone https://www.youtube.com/watch?v=xSUm6iMtREA
* PagerDuty clone https://www.youtube.com/watch?v=4xuBT3BbsYU alerts https://github.com/keephq/keep

## event-driven 

just the observer pattern on steroids

* bad for control flow?
> In event-driven programming, an application responds to external occurences, such as the arrival of a network packet or the press of a mouse button. 📙 Ousterhout [150]

= instead of service writing to DB, sends events to event store i.e. log of all states
> The event sourcing paradigm is used to design a system with determinism. This changes the philosophy of normal system designs. How does this work? Instead of recording the order states in the database, the event sourcing design persists the events that lead to the state changes in the event store. The event store is an append-only log. The events must be sequenced with incremental numbers to guarantee their ordering. The order states can be rebuilt from the events and maintained in OrderView. If the OrderView is down, we can always rely on the event store which is the source of truth to recover the order states. https://blog.bytebytego.com/p/ep166-what-is-event-sourcing

Domain Events: Objects capturing significant occurrences in the domain. Example: "OrderPlaced" event triggering inventory updates.
* CQRS-lite: Separate read/write paths without full event sourcing
* Django https://github.com/ambient-innovation/django-queuebie

* https://youtube.com/watch?v=VLUvfIm9wnQ
* https://news.ycombinator.com/item?id=40723302
* https://encore.dev/blog/event-driven-architecture
* https://news.ycombinator.com/item?id=40619521
* CQRS, service mesh, SOA, scaling (back pressure, throttling) https://roadmap.sh/backend
* event sourcing, sagas https://github.com/ThreeDotsLabs/watermill
> Think of it like an HTTP router but for messages https://threedots.tech/post/watermill-1-4/

## microservices

> Microservices only pay off when you have real scaling bottlenecks, large teams, or independently evolving domains. Before that? You’re paying the price without getting the benefit: duplicated infra, fragile local setups, and slow iteration. https://simonwillison.net/2025/May/8/oleg-pustovit/
> Microservices are a design pattern for organisations as opposed to technology. https://news.ycombinator.com/item?id=43927112

> Microservices, while often sold as solving a technical problem, usually actually solve for a human problem in scaling up an organization. There's two technical problems that microservices purport to solve: modularization (separation of concerns, hiding implementation, document interface and all that good stuff) and scalability (being able to increase the amount of compute, memory and IO to the specific modules that need it). The first problem, modules, can be solved at the language level. Modules can do that job, and that's the point of this blog post. The second problem, scalability, is harder to solve at the language level in most languages outside those designed to be run in a distributed environment. But most people need it a lot less than they think. Normally the database is your bottleneck and if you keep your application server stateless, you can just run lots of them; the database can eventually be a bottleneck, but you can scale up databases a lot. The real reason that microservices may make sense is because they keep people honest around module boundaries. They make it much harder to retain access to persistent in-memory state, harder to navigate object graphs to take dependencies on things they shouldn't, harder to create PRs with complex changes on either side of a module boundary without a conversation about designing for change and future proofing. Code ownership by teams is something you need as an organization scales, if only to reduce the amount of context switching that developers need to do if treated as fully fungible; owning a service is more defensible than owning a module, since the team will own release schedules and quality gating. I'm not so positive on every microservice maintaining its own copy of state, potentially with its own separate data store. I think that usually adds more ongoing complexity in synchronization than it saves by isolating schemas. A better rule is for one service to own writes for a table, and other services can only read that table, and maybe even then not all columns or all non-owned tables. Problems with state synchronization are one of the most common failure modes in distributed applications, where queues get backed up, retries of "bad" events cause blockages and so on. https://news.ycombinator.com/item?id=34231020

* https://github.com/micro/micro
* = distributed monolith, modularity https://news.ycombinator.com/item?id=31727453
* need more infra knowhow: 5 devs per service https://pythonspeed.com/articles/dont-need-kubernetes/
* https://world.hey.com/dhh/how-to-recover-from-microservices-ce3803cc
* _service layer_: Java-style abstraction https://www.b-list.org/weblog/2020/mar/16/no-service/
* make it a library instead http://catern.com/services.html
* business organization: https://news.ycombinator.com/item?id=23017388
> What microservices let you do is ship your org chart directly, and also map back from some functionality to an owning team. https://news.ycombinator.com/item?id=26247052
* _push_: if receiving svc goes down push svc has to stop
* _pull_: if push svc goes down receiving svc doesn't know (maybe the push svc just doesn't have any messages to push?) set batch size in polling svc (so it pulls when there's, say, 50 msgs vs. on each new msg)
* _sink_: https://www.feval.ca/posts/microservices/ Herman course https://www.zachvalenta.com/notes/2018-feval-microservices.html https://www.vinaysahni.com/best-practices-for-building-a-microservice-architecture https://www.dwmkerr.com/the-death-of-microservice-madness-in-2018/ https://nickjanetakis.com/blog/microservices-are-something-you-grow-into-not-begin-with https://nickjanetakis.com/blog/microservices-are-something-you-grow-into-not-begin-with https://robertnorthard.com/devops-days-well-architected-monoliths-are-okay/ https://segment.com/blog/goodbye-microservices/ https://blogs.dxc.technology/2018/05/08/everything-old-is-new-again-microservices/ https://changelog.com/podcast/312 https://news.ycombinator.com/item?id=22193383
* _benefits_: devs (specialization, experimentation) ergonomics (easier to grok)
* _drawbacks_: no joins (favor document db) outside single process (slower, flaky network) devs (easy code, complex infrastructure) hard to integration test https://aadrake.com/posts/2017-05-20-enough-with-the-microservices.html https://thoughtbot.com/blog/services-are-not-a-silver-bullet
* _communcation_: mq, pub-sub, RPC/REST https://testdriven.io/courses/microservices-with-docker-flask-and-react/part-one-microservices/
* microservices https://entropicthoughts.com/getting-used-to-microservices https://entropicthoughts.com/benefits-of-microservices

## monolith

* monolith + db https://danluu.com/simple-architectures/
> Wave is a $1.7B company with 70 engineers whose product is a CRUD app that adds and subtracts numbers. In keeping with this, our architecture is a standard CRUD app architecture, a Python monolith on top of Postgres. Starting with a simple architecture and solving problems in simple ways where possible has allowed us to scale to this size while engineers mostly focus on work that delivers value to users. Stackoverflow scaled up a monolith to good effect (2013 architecture / 2016 architecture), eventually getting acquired for $1.8B. If we look at traffic instead of market cap, Stackoverflow is among the top 100 highest traffic sites on the internet.
> Despite the unreasonable effectiveness of simple architectures, most press goes to complex architectures. For example, at a recent generalist tech conference, there were six talks on how to build or deal with side effects of complex, microservice-based, architectures and zero on how one might build out a simple monolith. There were more talks on quantum computing (one) than talks on monoliths (zero). Larger conferences are similar; a recent enterprise-oriented conference in SF had a double-digit number of talks on dealing with the complexity of a sophisticated architecture and zero on how to build a simple monolith. Something that was striking to me the last time I attended that conference is how many attendees who worked at enterprises with low-scale applications that could’ve been built with simple architectures had copied the latest and greatest sophisticated techniques that are popular on the conference circuit and HN.
> The cost of our engineering team completely dominates the cost of the systems we operate.
> A place where we can’t be as boring as we’d like is with our on-prem datacenters. When we were operating solely in Senegal and Côte d'Ivoire, we operated fully in the cloud, but as we expand into Uganda (and more countries in the future), we’re having to split our backend and deploy on-prem to comply with local data residency laws and regulations. That's not exactly a simple operation, but as anyone who's done the same thing with a complex service-oriented architecture knows, this operation is much simpler than it would've been if we had a complex service-oriented architecture.
* transistors
> With computing, there have been a couple different cases of scaling breakthroughs. One of them was the discovery of the vacuum tube, where you actually have a device that can do fairly simple logical operations such that you can implement it in a machine. Then we ran into this problem of, the vacuum tubes are mechanical, they do break, and so the bigger your machine, the more likely it is that it breaks; the more complicated your algorithm is, the more likely it is that something breaks down. So you have one of those dynamics where you're scaling your inputs a lot faster than you're scaling your outputs and you're doing things less and less efficiently over time. Then transistors do not actually have moving parts, so they don't have that particular problem – but they run into their own scaling obstacle. It's really fun to read about the early days of this: one of the books that I cite in Boom has an excerpt from, not Scientific American but a magazine of that type in the 50s, where it's speculating that perhaps in the future computers could be the size of a small house, and that's how much we could shrink them. But people ran into this problem with transistors, where the more of them that you connect – and you need all of them to be connected and working for that particular cluster of them to do anything useful – the more of them you connect, the more likely it is that you have one little issue somewhere that makes the whole thing not work. Then it turned out that there was a way around that too, which is that you don't actually plug together individual discrete devices, you actually etch the entire set of connections chemically, and now with many other things – but yeah, you etch it, a one shot [process] where you create one solid thing. That turned out to be a much more scalable architecture. https://www.complexsystemspodcast.com/episodes/boom-busts-and-long-term-progress-with-byrne-hobart-2/

---

* _bikeshedding_: aka yak shaving https://jsonapi.org/ http://bikeshed.org/ https://drewdevault.com/2020/08/17/Engineers-solve-problems.html
> Some applications where you would consider ditching Django to shave off some latency are: a stock trading marketplace; an global online advertisement serving network; a low level infrastructure control API - https://mattsegal.dev/is-django-too-slow.html
> Forget that all these things exist: Microservices, Lambda, API Gateway, Containers, Kubernetes...anything whose main value proposition is about "ability to scale" will likely trade off your "ability to be agile & survive". That’s rarely a good trade off. Start with a t3.nano EC2 instance, and do all your testing & staging on it. It only costs $3.80/mo. Then before you launch, use something bigger for prod, maybe an m5.large (2 vCPU & 8 GB mem). It’s $70/mo and can easily serve 1 million page views per day. https://twitter.com/dvassallo/status/1154516910265884672
> don't waste time on problems you don't have yet 📙 Getting Real [42]
> The bigger problem isn't scaling, it's getting to the point where you have to scale. 📙 Getting Real [42]
> It is well-known that the majority of the cost of software is not in its initial development, but in its ongoing maintenance [Kleppmann 24] Vinsel, Innovation Delusion
> Scaling for many web applications is typically bottlenecked by the database, not the web workers. - https://pythonspeed.com/articles/dont-need-kubernetes/ https://stribny.name/blog/2020/07/scaling-relational-sql-databases
> Build a monolith with copious amounts of telemetry. Use a RDBMS. Use a CDN. Let your telemetry guide you on how to scale, cache, or split your workloads. Don't hire people who want to boil the ocean. https://news.ycombinator.com/item?id=25037628
* just use one big db https://news.ycombinator.com/item?id=31084147
* _vertical scaling_: get faster drives for db
> I am always puzzled about this "autoscale" thing on a cloud. If your task can be represented as something like calculate sum of some ginormous array then sure. Split array in parts and launch thousand instances each working on it's own slice and then combine. In way more common situation you have a service hitting database and doing something with it. Sure you can spin a thousand instances of said service. But they will all be hitting the same database. - https://news.ycombinator.com/item?id=21741870
* _horizontal scaling_: shard https://www.youtube.com/watch?v=7v-wrJjcg4k until recently you waited as long as you could on this 📙 Kleppmann 1.18
> horizontal-scaling is often based on the partitioning of the data i.e. each node contains only part of the data, in vertical-scaling the data resides on a single node and scaling is done through multi-core i.e. spreading the load between the CPU and RAM resources of that machine. With horizontal-scaling it is often easier to scale dynamically by adding more machines into the existing pool - Vertical-scaling is often limited to the capacity of a single machine, scaling beyond that capacity often involves downtime and comes with an upper limit. - https://stackoverflow.com/a/11715598/6813490

## streaming

🗄️ `infra.md` queue / event (Kafka)
📙 Wang streaming systems https://www.manning.com/books/grokking-streaming-systems

---

```txt
Key points about streaming: It's typically not faster in terms of total processing time.

The main benefits are:
* lower peak memory usage (each chunk is processed and freed)
* = ability to handle files larger than RAM
* = earlier start to processing (can begin work before full file is read)

The streaming approach really shines when:
* you're memory-constrained
* you need to process data asap (like real-time dashboards)
* you're doing operations that can be parallelized across chunks
```

https://github.com/ebonnal/streamable
https://www.npmjs.com/package/x12-parser
https://www.youtube.com/watch?v=mDpS9J0-SQ4

* streaming architecture https://news.ycombinator.com/item?id=31421004
* streaming in Postgres https://github.com/sequinstream/sequin

https://www.youtube.com/watch?v=7AMRfNKwuYo

dashboard visualization https://github.com/finos/perspective

> A streaming SQL engine keeps queries’ results up to date without ever having to recalculate them, even as the underlying data changes. To explain this, imagine a simple query, such as SELECT count(*) FROM humans . A normal SQL engine (such as Postgres’s, MySQL’s) would need to go over all the different humans every time you ran that query- which could be quite costly and lengthy given our ever changing population count. With a streaming SQL engine, you would define that query once, and the engine would constantly keep the resulting count up to date as new humans were born and the old / sickly ones died off, without ever performing a recalculation of counting all humans in the world. https://news.ycombinator.com/item?id=37965319

STREAMING / BLOCKING 🗄 `computation.md` serialization
* https://www.scattered-thoughts.net/
* https://github.com/ynqa/sig
* blocking
* https://ossinsight.io/blog/why-we-choose-tidb-to-support-ossinsight/
* async https://www.b-list.org/weblog/2022/aug/16/async https://www.youtube.com/watch?v=bw1qeMoFBmw https://www.youtube.com/watch?v=0z74b3c63GA
* batch: TQ, Airflow
> port from `db.md`
* streaming: Kafka https://www.youtube.com/watch?v=qi7uR3ItaOY 🗄 site/drafts/ddd.md
* https://simonwillison.net/2021/Jul/1/pagnis/ https://news.ycombinator.com/item?id=38167423
* forum software in 500 lines or less https://news.ycombinator.com/item?id=33153152
> what is the relationship bte Kafka and faust? https://www.youtube.com/watch?v=Ik1PBbCWcTc
> is flink streaming or batch? https://github.com/apache/flink https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html
> what is windowing? https://www.scattered-thoughts.net/writing/against-sql
batch vs. streaming https://robertheaton.com/2020/02/08/pfab9-batch-vs-stream-processing/ 📙 Kleppmann section 3 🗄 `application.md` WebSocket
> 📍 batch to ETL, streaming to where?
* _batch_: more than one at a time 📍 Kleppmann chapter 9
* requires fewer trips to data source
* higher memory consumption
> Since the data in parsed_messages is essentially the same as that in raw_log but in a different form, parsed_messages probably takes up about the same amount of memory again as raw_log. We’re therefore using at least 20MB of memory to process a 10MB file.
```ruby
raw_log = File.read("samplelog.txt")
parsed_messages = parse_raw_log(raw_log)
message_stats = calculate_stats(parsed_messages)
```
* temporal data, virtual time https://www.hytradboi.com/2022/working-with-virtual-time-in-sql https://github.com/frankmcsherry/blog/blob/master/posts/2021-02-11.md
* _stream processing_: one at a time 📙 Kleppmann ch. 10 🗄 `system.md` Kafka
* libraries: https://github.com/robinhood/faust https://github.com/apache/flink
* sources: clickstream, IoT sensors, time series
* https://www.hytradboi.com/2022/a-faster-inner-dev-loop-for-stream-processing
* lower memory consumption
> Once the block has finished executing, the Ruby interpreter is able to garbage collect the data for both the raw line and processed message, since it can see that the program won’t reference them again. This means that the Ruby interpreter can reuse the piece of memory in which they were stored.
```ruby
stats = {}
File.open("samplelog.txt").each_line do |l|
  message = parse_raw_log_line(l)
  stats = add_message_to_stats(message, stats)
end
```

# 🟨 ZA

HICKEY / LISP / DATA-DRIVEN
* https://www.youtube.com/watch?v=oytL881p-nQ
* simple made easy https://news.ycombinator.com/item?id=38433358 https://www.youtube.com/watch?v=LKtk3HCgTa8
* data is not easy https://grishaev.me/en/ddd-lie https://news.ycombinator.com/item?id=41290189
* https://news.ycombinator.com/item?id=43300528
> What the author demonstrates here is a powerful principle that dates back to LISP's origins but remains revolutionary today: the collapse of artificial boundaries between program, data, and interface creates a more direct connection to the problem domain. This example elegantly shows how a few dozen lines of Clojure can replace an entire accounting application. The transactions live directly in the code, the categorization rules are simple pattern matchers, and the "interface" is just printed output of the transformed data. No SQL, no UI framework, no MVC architecture - yet it solves the actual problem perfectly.
> Over time I’ve come to see LISP less as the natural collapse of artificial boundaries but the artificial collapse of natural ones. Where and how data is stored is a real concern, but where and how the program is stored isn’t. Security boundaries around data and executable code are of paramount importance. Data storage concerns don’t benefit from being mixed with programming language concerns but from computer and storage architecture concerns (eg column stores).

## scaffold

💻 https://github.com/zachvalenta/ur-repo
https://github.com/rberenguel/motllo
https://mostlymaths.net/2024/11/test-driven-writing.html/

---

🛠️ https://github.com/zachvalenta/ur-repo https://github.com/zachvalenta/create-python-app
> turn this into a template repo? 🗄️ `git.md` Github > repos
🗄️
* `git.md` commmit
* `linux.md` man pages

```sh
├── meta
│   └── README.md  # symlink from root
│   └── pyproject.toml
│   └── settings  # https://stackoverflow.com/questions/50090341/is-there-a-naming-convention-for-django-project-configuration-directory https://stackoverflow.com/q/50090341
```

MESSY PROJECT ROOT = `$PROJ/meta` 🗄️ `python/pkg.md` project structure
* `README`
* `LICENSE`
* `Makefile`
* `.gitignore`
* `SECURITY.md`
* `CONTRIBUTING.md`

---

* copier, cookiecutter https://github.com/zillow/battenberg
* `kanban.md` https://github.com/frechdaggs/csvfloorsketcher
* https://karmanivero.us/blog/turning-the-crank-design-as-a-mechanical-process/
* https://karmanivero.us/toolkits/project-governance/design-as-code-a-frictionless-low-level-design-pipeline/
* comments https://drewdevault.com/2023/03/09/2023-03-09-Comment-or-no-comment.html

* UV
* healthcheck
* REPL
* make/task
* web server

* CICD
* admin

* auth
* dotenvx
* feature flag

* CDN
* load balancing
* cache

* Celery
* htmx

---

https://github.com/zachvalenta?tab=repositories&q=docker&type=&language=&sort=
* env: config, Docker, ❌ auth
* CQ: testing, hooks
* data: seed, repl, ❌ migrations, serialization, ORM
* UI: styling, pagination, search
🏡 intermediate - ✅ migrations, auth, env (✅ config, ✅ Docker)
🥕 basic - CRUD (✅ ORM, ✅ serialization, seed) UI (styling, search, pagination) CQ (✅ testing, hooks)

WORLD'S DUMBEST COMPLETE SAAS
> use as your repo to experiment
* Vincent books 🗄 `django.md`
* https://saasitive.com/
> scaffold (deployment, monitoring), accounts (individual, teams), auth (registration, login/logout, pw update, account removal), subscriptions
* https://news.ycombinator.com/item?id=34530052
* https://news.ycombinator.com/item?id=34483294
* https://pocketbase.io/ https://github.com/trailbaseio/trailbase https://news.ycombinator.com/item?id=42336207
* BYO Saas https://www.datasette.cloud/blog/2023/welcome/ https://simonwillison.net/2020/Jan/14/stanford-planning-datasette-cloud/ https://simonwillison.net/tags/datasette-cloud/?page=2
