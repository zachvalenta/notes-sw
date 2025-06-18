# ⛩️

## 参考

🔗 https://en.wikipedia.org/wiki/Domain-driven_design
📚
* ✅ Evans domain-driven design https://github.com/nickgerace/gfold/pull/149/files
* Percival https://www.amazon.com/gp/product/1492052205 https://www.youtube.com/watch?v=niMybnzmzqc [1:15]

## 进步

* _25_: mv to own note from `design-patterns.md` https://github.com/zachvalenta/capp-dataload
* _23_: Evans
* _22_: United Masters
* _19_: first time I can remember thinking about fat models skinny controllers
* _18_: Werner's serializers

https://blog.bytebytego.com/p/domain-driven-design-ddd-demystified
Django > design
building an exchange https://www.youtube.com/watch?v=b1e4t2k2KJY

> DDD is about capturing the business domain—its rules, entities, and processes—in a way that makes sense to the business, not just the database.

DDD sits within the spectrum of:
* Simpler: CRUD applications, Active Record pattern
* Similar: Hexagonal Architecture, Clean Architecture, Onion Architecture
* More complex: Event Sourcing, CQRS

> restore Evans in bookcase
> then clean this up
> then start from ## basics and distribute Evans where necessary
learn django-ddd
feed in other django repo + docs and do the whole goddamn thing

CRD's DEFINITION 🗄 notebook 22.12.13
* repository: mapper to db
* service: domain
* transport: HTTP | RPC | GraphQL

https://en.wikipedia.org/wiki/Domain-driven_design

tactical vs. strategic https://claude.ai/chat/50e0f262-0f86-43e0-8fc3-f33f80dcee83
entity / aggregate / repository / data mapper/ CQRS / Active Record / event sourcing https://claude.ai/chat/38b933dd-801a-4827-8794-7126b445f943
strategy pattern vs. repository https://claude.ai/chat/65dda4b1-ff8b-44fd-be95-ec754cc78086

https://grok.com/chat/a45bf890-a7d9-4a60-81f2-647f65f639e1
https://grok.com/chat/32d7a8a4-4449-4413-a9c2-64b40cd37ad8

CQRS: Command/query separation
Unit of Work: Transaction management

## my own version of you

> bot: Domain modules usually organize related entities and value objects by business concept, while services operate at different layers with different purposes
> me: but I thought the whole point of DDD was to allow a single domain to cross multiple tables. seems like services are just a layer up, but not fundamentally different. in the same way you might (in non-DDD) have a function do something small, a class do something bigger, and module do something bigger yet.

Here's my current conception of it, my own modified version of DDD:

* models: define actual tables (bc we live in reality and eventually all of this junk ends up in a table)
* repository: CRUD for modules
* domain: business rules in their purest form
* services: apply domain to repository
* tasks: actually do work i.e. use services to perform processes that normal people think of as "the business"

> You're right that there's a hierarchy of abstraction here. Let me clarify the relationship: Domain modules and services aren't fundamentally different - they're both part of organizing your business logic, just at different granularities.  The practical structure often looks like: https://claude.ai/chat/14d39177-3900-438e-94f5-07a6994b5458
> Domain entities/value objects: Model individual business objects (Customer, Order)
> Domain modules: Group related domain objects (Customer module, Order module)
> Services: Coordinate across domain objects/modules to implement use cases
> DDD's key contribution is decoupling your business concepts from your data storage. A single domain concept (like "Customer") might cross multiple tables (customer_profiles, customer_preferences, customer_addresses), and that's exactly what DDD helps with.

> Services in the application layer (often called "application services" in DDD) orchestrate use cases. They’re the verbs of your system—things like "calculate a price," "process a disconnection," or "validate a part."

> In DDD, the domain layer defines the core business logic and entities, while the application layer (often containing services) orchestrates use cases and coordinates domain objects. A single service in the application layer might interact with multiple domain entities or aggregates

but I thought the whole point of DDD was to allow a single domain to cross multiple tables. not in the words of DDD practicioners, but IRL come on that's what it is. which I respect, it's totally useful (it's why I'm trying to use it now!).

# 🗺️ STRATEGIC (domain)

> Ubiquitous language, domain, bounded context, aggregate, event storming are all about problem space. They are meant to help us learn the insights about the domain and extract the boundaries. DDD enables developers, domain experts and business people to communicate effectively using a single, unified language. Rather than focusing on these problem space aspects of DDD, we tend to emphasise particular folder structures, services, repositories, and other solution space techniques. https://minds.md/zakirullin/cognitive

## bounded context

---

💻️ https://github.com/zachvalenta/ddd-bounded-context

Same term ("Order"), different meanings in each context.
* Order Management Context: An "Order" contains items, prices, shipping info
* Inventory Context: An "Order" is just a reservation of stock
* Customer Support Context: An "Order" includes communication history

Why not just have an order and they each context uses whatever info they need?

The problem with having a single "Order" that all contexts use:
* Complexity explosion - The Order model would need to satisfy all teams' requirements, creating a bloated entity with many unrelated attributes
* Coupling - A change for one team affects all teams
* Cognitive load - Developers would need to understand the entire model, not just their relevant portion
* Conflicting requirements - What if Inventory needs to track Order status differently than Customer Support?

A Real Example
Consider how "Order completion" differs by context:

Order Management: Complete when payment processed
Inventory: Complete when items shipped
Customer Support: Complete when return period ends

These aren't just different views - they're fundamentally different business concepts with the same name.

## context mapping

## ubiquitous language

> everyone involved in a project speaks the same language
> used consistently across conversations, code, documentation, and user interfaces
> Instead of developers using "User" and business experts saying "Client," the team agrees to use "Customer" everywhere to describe the same concept.

## DSLs

📙 Boersma https://www.manning.com/books/building-user-friendly-dsls

---

* lose tooling of general purpose language https://news.ycombinator.com/item?id=22375721
* https://news.ycombinator.com/item?id=41938819
* https://registerspill.thorstenball.com/p/joy-and-curiosity-12
* https://news.ycombinator.com/item?id=41931507

ABSTRACTION
* https://jesseduffield.com/Beginners-Guide-To-Abstraction/
* howto https://tonsky.me/blog/dsl/
* against abstraction https://thorstenball.com/blog/2015/10/22/write-stupid-code/
* _law of leaky abstractions_: natch; if they wouldn't exist in the first place https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/

## rule encapsulation

* _invariant_: business rule 📙 Beck tidy first [61]

---

* https://grok.com/chat/8513a2e6-8c8a-42f3-883b-05668fe08054
* modular https://github.com/gauge-sh/tach https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/ https://github.com/gauge-sh/tach/issues/665 https://www.gauge.sh/
> A Python tool to enforce a modular, decoupled package architecture. tach allows you to define boundaries and control dependencies between your Python packages. Each package can define its public interface. If a package tries to import from another package that is not listed as a dependency, tach will report an error. If a package tries to import from another package and does not use its public interface, with strict: true set, tach will report an error. Zero runtime impact. https://pythonbytes.fm/episodes/show/384/force-push-lightly
* https://claude.ai/chat/61e85fd7-a33f-43e7-989f-7295de72845b
* https://claude.ai/chat/525e681b-a645-4eb9-a56f-1b51cf5fbccf
* existing rules `ECLIPSE_DISCONTINUED` https://github.com/cappusa/product-workflow/commit/711be5d67fc9f2ee9b30670971ea4dbe9a72f6a2

# 🛠️ TACTICAL

## obj

---

* _entity_: the table, the *thing*
> The entity has a lifecycle (e.g., created, updated, discontinued) tied to this identity.
* _value obj_: the details

* _entity_: defined by ID
* _value obj_: defined by state
* used for the details i.e. date, time, money, address
* _aggregate_: group of entities and value obj w/ single entity as root
* acts as interface for applying invariants

https://claude.ai/chat/53ccf574-253a-4b55-ac3f-69cb877cd63e
https://grok.com/chat/64f25eb3-92b5-4c0a-af17-374039ed8c27

## services

---

* _domain_: invariants
* _application_: domain + tasks
* _infra_: email, logging, other boring stuff

DOMAIN
* business logic
* Example: A TransferService that handles money transfers between two Account Entities, ensuring rules like balance checks are enforced.
* Lives in the Domain Layer and is purely focused on the domain model.

APPLICATION
* Coordinate application-level tasks, such as handling user requests, interacting with the UI, or orchestrating calls to Domain Services and Repositories.
* Example: An OrderApplicationService that processes an order by calling a Domain Service and saving the result via a Repository.
* Lives in the Application Layer.

INFRASTRUCTURE
* Handle technical concerns, like sending emails, logging, or interacting with external systems.
* Example: An EmailService that sends order confirmation emails.
* Lives in the Infrastructure Layer.

---

Domain Services: Stateless operations that don’t fit neatly into entities or value objects. Example: A "TaxCalculator" service applying tax rules across orders.
Lifecycle Patterns:

## data mapper

* https://www.sqlalchemy.org/
* https://github.com/tommyboytech/t3/pull/11906
* https://en.wikipedia.org/wiki/Data_mapper_pattern#Python
* https://www.youtube.com/watch?v=oaiwS5KFHEs
* https://www.openmymind.net/2011/11/18/I-Just-Dont-Like-Object-Mappers/
* https://www.js-data.io/docs/data-mapper-pattern
* https://www.codeproject.com/articles/821803/data-mapper-pattern
* https://codingwithscott.com/how-to-implement-the-data-mapper-design-pattern-in-c/
* https://designpatternsphp.readthedocs.io/en/latest/Structural/DataMapper/README.html
* https://martinfowler.com/eaaCatalog/dataMapper.html

## repo

---

* _Hexagonal Architecture_: Uses ports/adapters instead of repositories
Factories: Encapsulate complex object creation. Example: A "PolicyFactory" creating a configured insurance policy.
Repositories: Manage collections of aggregates, abstracting persistence. Example: An "OrderRepository" retrieving or saving Orders from a database.

REPOSITORY
* CRUD module 📙 Evan [151] https://grok.com/chat/68e4076a-a644-4201-9bdb-1861d5e324a2 https://claude.ai/chat/d6a4943d-f1af-4a80-b3f9-42825bf0c41d
repository pattern would abstract data access behind a consistent interface
├── Repository: data access abstraction 🗄️ `sql.md` schema / approaches
├── Factory
├── Aggregate
└── Entity

# 🏗️ IMPL

## in Django

---

* repo structure and services https://grok.com/chat/4b933c4f-67e4-43bb-b363-f64faaf33992
* Django admin https://claude.ai/chat/6cb37b84-901f-4b18-bf0f-7ba7684ddf2f
* is Django really DDD?  https://www.cosmicpython.com/book/appendix_django.html https://grok.com/chat/95d5f5bc-e490-4a0f-b8e8-a8b6eafcf884
> circle back and ensure bounded context
* 💻 https://github.com/zachvalenta/django-DDD https://grok.com/chat/95d5f5bc-e490-4a0f-b8e8-a8b6eafcf884
> I think the move is to 1) clean up the `development` dir in `kern` 2) put the concerns about Django to an LLM and get opinions based on the current approach in `kern`
* Evans https://github.com/zachvalenta/bookcase-sjk/blob/master/notes/non-fiction/dev/svc/2003%20evans%20-%20domain%20driven%20design.md
> sketch things you need to understand more from these LLMS
* https://claude.ai/chat/61e85fd7-a33f-43e7-989f-7295de72845b -> https://claude.ai/chat/53ccf574-253a-4b55-ac3f-69cb877cd63e
* https://chatgpt.com/c/67e15081-a4f8-8004-86ab-9db58ca5b111 https://claude.ai/chat/812e936c-e2d0-4bfd-a403-8dfacf7a57a0
* https://claude.ai/chat/92bdb3e8-c87f-484c-8821-fbb7b2d4800f
* https://grok.com/chat/33a41760-ce83-4dc0-af25-1c7219736aed
* https://www.cosmicpython.com/book/appendix_django.html#_steps_along_the_way
* Percival, Django as Active Record https://news.ycombinator.com/item?id=43501989 Architecture Patterns for Python https://neil.computer/notes/teaching-how-to-code-is-broken/
* https://forum.djangoproject.com/t/where-to-put-business-logic-in-django/282 https://www.cosmicpython.com/book/appendix_django.html#_steps_along_the_way
* hating Django https://lucumr.pocoo.org/2025/2/20/ugly-code/
* in python https://www.pythonpodcast.com/episodepage/domain-driven-design-episode-219

* existing impl? https://claude.ai/chat/92bdb3e8-c87f-484c-8821-fbb7b2d4800f https://claude.ai/chat/812e936c-e2d0-4bfd-a403-8dfacf7a57a0
> what's that Python project that prevents circular dependencies, among other things?
> Let's say you have a custom piece of logic that touches models A, B, C, and D. Where do you put it? The idea is to let your domain live separately from your data model & API layer. https://github.com/HackSoftware/Django-Styleguide
* https://www.youtube.com/watch?v=72V-5hrilv0
* https://news.ycombinator.com/item?id=33999191

## Evans

---

incorporate Thomas notes

SEMANTICS
* _domain_: business logic https://www.youtube.com/watch?v=dlCcnJdh4c4 [1:15]
* _domain model_: data model [xvii]
* just data modeling? [84]
* holds business logic [71]
* the domain is the thing = the db is what matters = data eng! [70]
* the hard part of software [xxi]
* extends through all parts of project, to all team members [4]
* dependent on writing culture [16]
* could be non-OO e.g. Prolog [119]
* _ubiquitous language_: attention to semantics [xviii,25] https://tools.ietf.org/html/rfc2119
* have to 1) have documents that use the langauge 2) involve them in project activities [39]
* the hard part is sticking to it [26]
> It takes fastidiousness to write code that doesn't just do the right thing but also says the right thing. [40]
* a form of linguistic determinism [27]
> Translation muddles model concepts. [24]
* entire thing premised on having a dictionary [31]
* diagrams aren't helpful without semantics [35]
* _layered architecture_: UI, transport, service, repo/domain, db [68,70] 🗄 notebook 22.12.13
* vs. hexagonal, onion, microkernel https://blog.europython.eu/kraken-technologies-how-we-organize-our-very-large-pythonmonolith/
* or, transport, logic, messaging [107]
* separation of concerns [69]
* infrastructure = not db, but sending msgs? [73]
* _entity obj_: e.g. person, account
* e.g. transactions [92]
* has identity, diff states [81,91]
* _value obj_: e.g. enum
* e.g. values of transactions [92]
* attr [81]
* _aggregate_: entity + other associated obj [126] e.g. car is aggregate and wheel, tires, engine are associated obj [127]
* _service_: verb vs. noun [104]
* _factory_: creates other obj [138]
* _specification_: business logic [223,282]

STYLE
* anondyne: "talk to domain experts" [14] encapsulate [19]
* bizarre use of bolding [61]
* bizarre use of capitalization [62]
* diagrams gone wrong [65]
* poor writer [73,82]
* unclear writer [91] e.g. the main topic of section he defines 10 paragraphs in [126,138]
* semantics that are not in the index [147,151]
* dated e.g. 4GL https://en.wikipedia.org/wiki/Fourth-generation_programming_language [77,78]

ZA
> Hard to tell whether this book Norman-esque / curse of knowledge or reputational alá Finegan's Wake. The biggest impact I've seen it have is ubiquitous language.
* _CQRS_: diff svc for read/write https://martinfowler.com/bliki/CQRS.html https://ownyourbits.com/2018/05/02/understanding-disk-usage-in-linux/
* _pub sub_: 📙 Thomas pragmatic programmer [158]
* _event sourcing_: pub sub but more https://chriskiehl.com/article/event-sourcing-is-hard 📙 Thomas pragmatic programmer [160] https://everydaysuperpowers.dev/articles/what-is-event-sourcing-and-why-you-should-care/ Elixir https://pragprog.com/titles/khpes/real-world-event-sourcing/
> architectural pattern where state changes in your application are represented as a sequence of immutable events, rather than being persisted directly in the database as the current state https://django-news.com/issues/283 https://everydaysuperpowers.dev/articles/event-sourcing-reactivity-without-the-react-overhead/
* aka event-driven? Components communicate through events. Publishers emit events without knowledge of subscribers.
* same probelm as Norman, ideas have won?
* background: agile [xxii] object-oriented [xxvi,51,87] Java oriented (back cover blurb) [74,111]
* event storming https://www.lucidchart.com/blog/ddd-event-storming https://www.youtube.com/results?search_query=event+storming
* ch. 7-9: examples
* https://www.packtpub.com/product/domain-driven-design-with-golang/9781804613450
* https://everydaysuperpowers.dev/articles/what-is-event-sourcing-and-why-you-should-care/
> Event sourcing is an architectural pattern for software development that has two components: To change the state of the application, you save the data associated with that change in an append-only log. The current state of an item is derived by querying the log for related events and building the state from those events.
> However, these two components are the core of event sourcing. I’ve seen people include eventual consistency, CQRS, and event streaming in their definitions of event sourcing, but these are optional additions to the pattern.
* _domain-driven design_: ❓ seems to boil down to "do things sensibly" (cf. 'bounded context') Evans 'Domain-Driven Design' Folwer 'Patterns of Entreprise Architecture' https://www.pythonpodcast.com/domain-driven-design-episode-219/
> Let’s for a moment talk about what all microservices have in common. Eric Evans, the father of Domain Driven Design, defines them as the following: "[services] that can consume and produce messages."

## Percival
