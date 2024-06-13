# ⛩️

## 参考

📚
* Buelta python architecture
* Dibernardo 500 lines or less http://aosabook.org/en/index.html
* ✅ Evans domain-driven design
* Fowler refactoring https://www.amazon.com/dp/0134757599/
* Martin clean code https://qntm.org/clean
* McConnell code complete
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming

## 进步

* _23_: 📙 Evans domain-driven
* _19_: URL shortener, Gitlab for CI

# 🛰️ API

🔍 https://github.com/public-apis/public-apis
📙 Masse api rulebook

PAGINATION
* _paginate_: return subset of records
* helps user and server both
* req `api/widgets?page=42` res can return header `x-total-count=<num>` https://slack.engineering/evolving-api-pagination-at-slack-1c1f644f8e12 https://www.reverb-api.com/docs#section-pagination

RATE LIMITING
* _rate limit_: increase cost of fetching resource
* why: defense against DDoS, general protection against overload
* how: increase latency, serve error code
* via web server https://news.ycombinator.com/item?id=23948720 https://www.nginx.com/blog/rate-limiting-nginx/
* via app (bucketing, GCRA) https://brandur.org/rate-limiting https://dev.to/astagi/rate-limiting-using-python-and-redis-58gk
```ruby
def rate_limit?(bucket)
  if !bucket.exists?
    bucket.set_value(RATE_BURST)  # 5000
    bucket.set_ttl(RATE_PERIOD)   # hour
  end

  if bucket.value > 0
    bucket.decrement
    true
  else
    false
  end
end
```

## approaches

📚
* Kleppmann ch. 3
* Masse api rulebook

REST
* hypermedia is REST https://htmx.org/essays/
* _REST_: architectural style, not protocol [Kleppmann 4.133] nowadays means JSON over HTTP i.e. there are few to-the-letter RESTful APIs https://news.ycombinator.com/item?id=15939552 backend supports n clients (web, mobile) https://wsvincent.com/rest-a-definition/ https://codewords.recurse.com/issues/five/what-restful-actually-means https://www.youtube.com/watch?v=pZYRC8IbCwk
* definition https://news.ycombinator.com/item?id=32141027
* _Fielding paper_: not specific to HTTP; guided tour; no reference implementation http://mickadoo.github.io/rest/2016/09/26/what-is-rest.html https://codewords.recurse.com/issues/five/what-restful-actually-means https://stackoverflow.com/a/983458/6813490 https://twobithistory.org/2020/06/28/rest.html https://news.ycombinator.com/item?id=24384048
* _HATEOAS_: navigate API via links btw endpoints https://htmx.org/docs/#introduction https://stackoverflow.com/questions/2239405/hateoas-absolute-or-relative-urls https://stackoverflow.com/questions/1139095/actual-examples-for-hateoas-rest-architecture https://www.django-rest-framework.org/topics/rest-hypermedia-hateoas/ https://htmx.org/essays/hateoas/
> RESTful API design consequently suffers the same problems as Active Record ORMs. The problem is most severe when fundamentalist RESTafarians get involved, as they advocate using hypertext-style links between API endpoints - HATEOAS ("Hypermedia As The Engine Of Application State"). Under HATEOAS, applications "browse" the API, moving from link to link to accomplish their goal. https://calpaterson.com/activerecord.html

JSON:API https://jsonapi.org
* req/res data fmt + more precise HTTP semantics https://changelog.com/podcast/189 46:30
* helps client not make unnecessary requests https://news.ycombinator.com/item?id=5654390
* the name is an annoying land grab https://news.ycombinator.com/item?id=5654375 
* other projects that aim for the same thing https://news.ycombinator.com/item?id=5653976
* ❓ diverges from OpenAPI https://phil.tech/api/2018/03/30/openapi-and-json-schema-divergence/
* _alternatives_: HAL https://jsonapi.org/faq/

SOAP
* tangled set of protocols

* API schema described using language called WSDL 📙 Kleppmann [4.133]
* tighter coupling btw client/server http://keithba.net/simplicity-and-utility-or-why-soap-lost
* typically uses XML 📙 Kleppmann [4.132]

RPC
* https://stackoverflow.blog/2022/11/28/when-to-use-grpc-vs-graphql/
* akin to intra-process communcation (more tightly coupled)
* apparently a bad idea 📙 Kleppmann [4.134]
* only used inside your own data center 📙 Kleppmann [4.136]
* argument for is no bikeshedding on HTTP semantics https://news.ycombinator.com/item?id=9597030
* https://etherealbits.com/2012/12/debunking-the-myths-of-rpc-rest/ https://www.smashingmagazine.com/2016/09/understanding-rest-and-rpc-for-http-apis/ https://apihandyman.io/do-you-really-know-why-you-prefer-rest-over-rpc/ https://stackoverflow.com/questions/15056878/rest-vs-json-rpc https://stackoverflow.com/a/26831221 https://github.com/fullstorydev/grpcurl https://realpython.com/python-microservices-grpc/ https://github.com/tomerfiliba-org/rpyc

GraphQL 📹 https://www.youtube.com/watch?v=QJhiMSUFgDM
* https://news.ycombinator.com/item?id=40521518
* https://stackoverflow.blog/2022/11/28/when-to-use-grpc-vs-graphql/
* spec + query language for API
* componenents: client (Apollo) server (Graphene)
* code generation https://hasura.io/
* _document_: request; what client sends to GraphQL server; can be sent over HTTP, sockets, SSH i.e. doesn’t depend on HTTP verbs
* operations: query (read) mutation (write)
* use case: avoid over-fetching, combine data from two services, better versioning 🗄 'design'
* design https://news.ycombinator.com/item?id=32366759
* better metrics?
> In a REST API, an API provider must assume that for any given API resource, every field is in use by every user because they have no insight at all into which ones they’re actually using. https://brandur.org/graphql#explicitness
* _sink_: https://retool.com/blog/a-beginners-guide-to-the-graphql-ecosystem/ https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/ https://www.howtographql.com/ https://graphql.org/learn/ https://pganalyze.com/blog/efficient-graphql-queries-in-ruby-on-rails-and-postgres https://brandur.org/api-paradigms https://brandur.org/graphql https://news.ycombinator.com/item?id=23758367 https://news.ycombinator.com/item?id=25432233 https://scattered-thoughts.net/writing/against-sql 

representing individual resources in URL
* PK (bad) 
* UUID (unwieldy) https://news.ycombinator.com/item?id=31715119
* short uuid (better https://0of1.com/blog/posts/django-staples/)
* _slug_: short repr for resource https://learndjango.com/tutorials/django-slug-tutorial

* _slug_: human readable addendum to URL resource id https://learndjango.com/tutorials/django-slug-tutorial
* typically hyphenated 🗄 `tfr.csv` https://github.com/un33k/python-slugify

* _slug_: to preserve URLs for external links, auto-generated slugs won't change when attr used for generation update [Osborn 1 9.57, 61]
```sh
https://stackoverflow.com/questions/427102/what-is-a-slug-in-django
```

misc
* just give folks everything and let them drill down vs. trying to predetermine what they need https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 38:00
* if API truly agnostic from frontend each page will end up making a bunch of calls instead of one call per page https://macwright.com/2020/05/10/spa-fatigue.html
* standards at national level https://increment.com/apis/introduction-apis-egovernment/
* _streaming_: server pushes to client https://2.python-requests.org/en/master/user/advanced/#streaming-requests
* _idempotent_: same req n times = no additional side effects after first req e.g. after initial req creates record, further requests won't create dupe https://stripe.com/blog/idempotency
* provide map of endpoints https://brandur.org/accessible-apis#programmatic-maps
* limit the number of req to get actionable info on resource https://www.dataengineeringpodcast.com/linode-object-storage-service-episode-125/ 25:00 JSON over REST and even higher level than that https://josephg.com/blog/api-for-changes/ https://josephg.com/blog/databases-have-failed-the-web/ https://josephg.com/blog/composing-databases/

## schema

* _schema_: typing 📙 Kleppmann [4.122-128]
* _spec_: doc explaining schema https://www.youtube.com/watch?v=1lo7idI7uq8
* generate spec from API and vice versa https://www.youtube.com/watch?v=1lo7idI7uq8 3:00

JSON SCHEMA https://json-schema.org/
* validate incoming requests via decorator https://apisyouwonthate.com/blog/json-api-openapi-and-json-schema-working-in-harmony https://stoplight.io/blog/openapi-json-schema/
```python
# decorator to validate req
def validate_request(schema: Dict[str, Any]) -> Callable:
    validator = fastjsonschema.compile(schema)
    def decorator(func: Callable) -> Callable:
        @wraps(func)
        async def wrapper(*args: Any, **kwargs: Any) -> Any:
            data = await request.get_json()
            try:
                validator(data)
            except fastjsonschema.JsonSchemaException:
                abort(400)
            else:
                return await func(*args, **kwargs)
        return wrapper
    return decorator

# add to endpoint
@app.route("/todo/", methods=["POST"])
@validate_request(
    {
        "type": "object",
        "properties": {
            "due": {"type": "string", "format": "date"},
            "task": {"type": "string"},
        },
        "required": ["due", "task"],
        "additionalProperties": False,
    }
)
def endpoint():
    return res
```

OPENAPI
* https://github.com/zaghaghi/openapi-tui
* howto https://www.youtube.com/watch?v=qcxio8C9Mh0
* _versions_: OpenAPI (v3) Swagger (v2)
* _schema_: description of API; formats differ between v2 and v3 https://docs.apistar.com/api-documentation/
* _parameters_: headers, query string, path https://swagger.io/docs/specification/describing-parameters/
* can generate schema from code https://news.ycombinator.com/item?id=14036628 https://github.com/axnsan12/drf-yasg
* can generate code from schema https://news.ycombinator.com/item?id=14036871
* most people write schemas and code by hand https://news.ycombinator.com/item?id=14037238
* faster to just write your API and docs in Markdown https://news.ycombinator.com/item?id=14036469
* ❓ GraphQL makes this easier? https://news.ycombinator.com/item?id=14037067
* _alternatives_: https://brandur.org/elegant-apis https://blog.heroku.com/json_schema_for_heroku_platform_api https://json-schema.org/
* _sink_: https://instagram-engineering.com/types-for-python-http-apis-an-instagram-story-d3c3a207fdb7 https://news.ycombinator.com/item?id=14035936 https://stackoverflow.com/questions/36634281/list-of-swagger-ui-alternatives https://www.youtube.com/results?search_query=openapi+pycon&page=&utm_source=opensearch https://github.com/kiwicom/schemathesis

API Star https://github.com/zachvalenta/flask-openapi
> my current approach to documentation is "other developers, use my Makefile"
* build docs for OpenAPI service
* _history_: began as a project to bring DRF browsable dev docs to Flask https://github.com/flask-api/flask-api/commit/b99c8d26e335cef696b931dde783ca80ca4ab798 then became a framework https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis and now is a toolkit to add OpenAPI stuff to any framework
* `apistar validate`: lint schema
* `apistar request`: can't get this working
* `apistar.yml`: path to schema, whether Swagger or OpenAPI
* ❓ able to build static or have to run server?
* ❓ run alongside prod?
* ❓ no hot reload https://github.com/encode/apistar/issues/637 from when it was a framework? https://github.com/encode/apistar/issues/40 https://github.com/encode/apistar/pull/57

## versioning

> Also, as a general rule, you can at any given time get away with changing more than you think. Introducing change is like pulling off a bandage: the pain is a memory almost as soon as you feel it. - http://paulgraham.com/popular.html

* _versioning_: how to communicate changes to avoid breaking functionality for clients
> if you don’t define breaking and non-breaking, everything is potentially breaking...for example, we could add a new field to a JSON response and usually this wouldn’t lead to a problem, but somehow somewhere one client used the number of fields in a JSON object to get the right data. We could also decide to send too much data, and suddenly one client can’t keep up anymore. - https://www.moesif.com/blog/technical/api-design/Best-Practices-for-Versioning-REST-and-GraphQL-APIs/

https://softwareengineeringdaily.com/2020/09/02/api-change-management-with-aidan-cunniffe/
https://mikehelmick.medium.com/django-rest-framework-better-api-versioning-with-semantic-versioning-d93908613dea
https://app.pluralsight.com/library/courses/designing-restful-web-apis/table-of-contents ❓ did the conery course go to his website
* https://increment.com/apis/web-api-versioning/

* _URL_: `/api/v2/bar` (downside: clients have to change)
* _query string_: `/api/bar?v=2` (upside: can have default version)
* _headers_: `X-Version: 2` or using the existing header `Accept: application/json; version=2`

* _impl agnostic_: decouple product release from API version (don't want new versions if no changes, silly to have hundreds of versions)
* _REST_: tell devs about change via new version
* _GraphQL_: tell devs about change via deprecating field -> seems like versioning by other means vs. not versioning at all (as the docs claim) https://graphql.org/learn/best-practices/ https://blog.hitchhq.com/graphql-3-reasons-not-to-use-it-7715f60cb934 https://www.graphile.org/postgraphile/

* _sink_: https://www.youtube.com/watch?v=dqDnB6jKzcE https://www.moesif.com/blog/technical/api-design/Best-Practices-for-Versioning-REST-and-GraphQL-APIs/ https://stackoverflow.com/questions/55877310/add-x-frame-options-header-to-all-flask-responses https://flask.palletsprojects.com/en/1.1.x/api/#flask.Flask.after_request https://pythonise.com/series/learning-flask/python-before-after-request https://stripe.com/blog/api-versioning https://news.ycombinator.com/item?id=21834628 https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api https://brandur.org/api-upgrades security https://nostarch.com/hacking-apis

# 🍥 DESIGN PATTERNS

🔍
* https://github.com/DovAmir/awesome-design-patterns
* https://softwareengineering.stackexchange.com/questions/tagged/design-patterns
📙 Conery ch. 11,12

* Gang of Four: composition over inheritance https://en.wikipedia.org/wiki/Design_Patterns
> They warn that the implementation of a subclass can become so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change. Furthermore, they claim that a way to avoid this is to inherit only from abstract classes—but then, they point out that there is minimal code reuse.
> Using inheritance is recommended mainly when adding to the functionality of existing components, reusing most of the old code and adding relatively small amounts of new code.

---

* fanout https://www.better-simple.com/django/2023/12/06/fanout-pattern-explained/
* the big ball of mud https://news.ycombinator.com/item?id=35481309
* _strangler_: you run the old code and new code live, in production, side-by-side, checking that the new code behaves exactly the same as the old code. Once you are confident it does, you retire the old code https://www.kosli.com/blog/how-to-strangle-old-code-using-python-decorators/

http://gameprogrammingpatterns.com/contents.html

> Some practices are the best when applied to a rewrite, but the worst when you’re still exploring. https://thorstenball.com/blog/2022/05/17/professional-programming-the-first-10-years/

https://developers.soundcloud.com/blog/end-of-the-strangler

data mapper
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

* _strangler fig_: https://developers.soundcloud.com/blog/end-of-the-strangler
* _builder_ https://github.com/kayak/pypika
* _proxy_ https://rednafi.github.io/digressions/python/2020/06/16/python-proxy-pattern.html

as red flag https://news.ycombinator.com/item?id=30675182

* _design patterns_: ❓ inherently OOP? [Conery 236]
* _adapter_: wrapper e.g. ORM class for Postgres, MySQL, et al. [Conery 249] https://bitfieldconsulting.com/golang/adapter
* _bridge_: allows you to update abstraction w/breaking impl i.e. yet another layer of abstraction [Conery 250]
* _decorator_: wrapper [Conery 254]
* _facade_: wrapper [Conery 255]
* _flyweight_: storage for other obj to use, cuts down on memory usage 📙 Conery [257] Evans [100]
* can use when shared obj is immutable, shared memory, when you really need to save space 📙 Evans [101]
* _factory_: 📙 Evans domain-driven [139]
* _constructor_: 📙 Evans domain-driven [141]
* _abstract factory_: dedicated class to construct `CustomerFactory().default()` [Conery 243]
* _singleton_: class that only allows single instance of itself; naive impl can go haywire in multithreaded env [Conery 248]
* _mediator_: obj passing msg btw two other obj [Conery 261]
* _observer_: obj that listens to events from another obj
* _strategy_: pass algo at runtime i.e. `charge(normal_price)` or `charge(half_off)`
* _visitor_: https://martinheinz.dev/blog/90

---

* _observer_: pub sub https://layerci.com/blog/postgres-is-the-answer http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/
* _sink_: https://github.com/kamranahmedse/design-patterns-for-humans https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745
* in python https://python-patterns.guide/ https://hynek.me/articles/python-subclassing-redux/

# 🎭 PARADIGMS

📚 Lopes exercises in programming style

---

> When in doubt, don't model it. Just get the code written, make forward progress. Don't let yourself get bogged down with the details of modeling a helper class that you're creating for documentation purposes. - http://steve-yegge.blogspot.com/2008/02/portrait-of-n00b.html

> This is what I’ve started telling people: Use mostly functions, try to make most of them pure. I think that can get people (even new devs) 80% of the benefits (testability, composability, loose coupling, and the ability to reason about code) of more complicated, prescriptive architectures (Hexagonal, Onion, Ports & Adapters, Clean, etc) with a minimal amount of ramp up. https://news.ycombinator.com/item?id=24915497

* _transform_: combine multiple functions into single [Fowler 14]
```python
# original
def do_this(thing):
def do_that(thing):

# transform
def do_this_and_that(thing):
    this(thing)
    that(thing)
```
* obj param [Fowler refactoring 40]
```python
# n params
def multi_args(foo_arg, bar_arg):
    do_foo(foo_arg)
    do_bar(foo_arg)

# obj param
def obj_args(obj):
    do_foo(obj.foo)
    do_bar(obj.bar)
```

---

https://www.youtube.com/watch?v=JlPMOszyjjo&t=1566s https://news.ycombinator.com/item?id=16617039
> seems like she's conflated style (straight ahead, code golf) with design (objects)

* __straight ahead (3)__: no abstractions, lots of nesting, no return statements
* __code golf (6)__: fewest # of lines, leverage stdlib
* __cookbook (4)__: break everything into functions
* (10): Java encapsulation hell
* (30): map reduce

 [changing your mind](https://news.ycombinator.com/item?id=19288954) hedge fund managers do it https://www.theobservereffect.org/marc.html

* _imperative_: detailed; how; e.g. machine code, assembly
* _declarative_: less detailed; what not how; e.g. SQL, HTML [Kleppmann 2.44] just say what you want i.e. SQL leaves it to DBMS to implement; better for parallelism bc doesn't specify order [Kleppmann 2.43] Prolog in Python https://fedoramagazine.org/exploring-the-world-of-declarative-programming/

📝 diff btw imperative and delcarative is [diff of abstraction](http://itsadeliverything.com/declarative-vs-imperative-gherkin-scenarios-for-cucumber) but that diff ends up being a diff of type

cf. [Designing Data Intensive Applications - chapter 2 - 'delcarative queries on the web']

* _procedural_: group code into functions; C, Basic
* __object-oriented__: procedural on steroids; Java, C++
* __scripting__: functions not attached to objects
* __logic__: formal mathematical logic; Prolog https://news.ycombinator.com/item?id=30091291

# 🟨 ZA

---

SEMANTICS
* _code path_: branch through codebase
* _cohesion_: put like with like 📙 Conery [270] Evans [109]
* _coupling_: "there should be low coupling btw modules and high cohesion within them" 📙 Evans [109]
* _encapsulation_: modularity via objects/method https://www.youtube.com/watch?v=QyJZzq0v7Z4 24:00
```python
foo = 'foo val'
def get_foo():
    return foo
```
* _information hiding_: e.g. factories https://en.wikipedia.org/wiki/Information_hiding 📙 Evans domain-driven [139]
* _modules_: impl for cohesion 📙 Conery [270] Evans [109]
* _single responsibility_: from SOLID https://en.wikipedia.org/wiki/Single-responsibility_principle 📙 Raymond unix Buelta architecture [5]
* _separation of concerns_: cohesion re: to app layers (UI, logic, db, auth, logs) and business functions (content mgmt, reporting, membership) 📙 Conery [271]

HOOKS
* _hook_: response to event
* aka event handler 📙 Chacon [402]
* e.g. trigger (db) lifecycle hook (Docker compose)
* callback https://stackoverflow.com/a/11087727
* _webhook_: res/ack (vs. req/res); 3rd streams > 1st polls https://sendgrid.com/blog/whats-webhook
* route known as "receiver" https://adamj.eu/tech/2021/05/09/how-to-build-a-webhook-receiver-in-django/
* further considerations https://brandur.org/webhooks

---

* more domain-driven https://www.youtube.com/watch?v=72V-5hrilv0
* _extract_: separate [Fowler https://refactoring.com/catalog/]
* _inline_: combine
> Inlining is the concept of replacing a function call in a program with the contents of the function itself, thus avoiding the call. https://golangweekly.com/issues/470

* CRD DDD 🗄 notebook 22.12.13
* DRY, single responsibility https://news.ycombinator.com/item?id=35151088

COMPATIBILITY https://thorben-janssen.com/update-database-schema-without-downtime/
* _backwards compatible_: new code can handle old data 📙 Kleppmann [112]
> is the old data really old?
> e.g. add attr, previous records don't have value for attr but have attr itself
> client/server can just massage data to handle null values
* aka open-closed principle (from SOLID) https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle
* _forward compatibility_: old code can handle new data; typically harder to do 📙 Kleppmann [112] typically old code doesn't touch new fields [129]
> how would this happen unless you logged in

https://news.ycombinator.com/item?id=33999191
* _fat model, skinny controller_: modularity around data access; != "all logic in model" http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/
* _Hungarian notation_: redundacy in identifier naming i.e. `CREATE TABLE tbl_book` instead of `CREATE TABLE book` https://www.sqlstyle.guide/#avoid
* _interface_: interface smuggling https://utcc.utoronto.ca/~cks/space/blog/programming/GoInterfaceSmuggling 🗄 `python` 'web'
* _introspection_: get info about an obj at runtime aka having a REPL https://realpython.com/primer-on-python-decorators/#simple-decorators aka 'reflection' https://changelog.com/gotime/133 also used as synonym for logging https://hacker-tools.github.io/machine-introspection/
* _modularity_: public interface, private impl https://www.youtube.com/watch?v=QyJZzq0v7Z4 @ 24:00
* _readability_: factors (familiarity, consistency) fetishization of one-liners (cf. Peter Norvig 'mine is shorter' from Crista Lopes talk on 'Exercises in Programming Style' @ 20:15)
> One of the core tenets behind the design of Python is creating readable code. The motivation behind this design is simple: The number one thing that Python programmers do is read code. [Hitchhiker's Guide 3.3]
> "A computer language is not just a way of getting a computer to perform operations...it is a novel formal medium for expressing ideas about methodology. Thus, programs must be written for people to read, and only incidentally for machines to execute." - Ford what is code? qt. SICP

URL shortener 🗄 `fd url-short`
* _URL shortener_: make links look more trustworthy
* providers: Bitly, TinyURL
* https://www.youtube.com/watch?v=rGQKHpjMn_M
* https://blog.codinghorror.com/url-shortening-hashes-in-practice/

## concurrency

📙 Butcher models https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks
🗄
* `golang.md` concurrency
* `infra.md` queues
* `linux.md` threads
* `python.md` concurrency

BIG PICTURE https://en.wikipedia.org/wiki/Concurrency_(computer_science)
* why: WebSockets https://channels.readthedocs.io/en/latest/
* why not: hard to reason about, just use a queue or a WebSockets server https://www.david-dahan.com/blog/10-reasons-i-stick-to-django

---

* _bricked_: cannot receive further commands https://news.ycombinator.com/item?id=36940626
* clock synchronization https://signalsandthreads.com/clock-synchronization/ https://www.exhypothesi.com/clocks-and-causality/ https://xeiaso.net/blog/nosleep
* _callback_: another func to call after func finishes execution 🗄 `application.md` webhook
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/59370383#59370383
* https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods/48530284#48530284
* imperative programming fundamentally about order, which makes concurrency hard https://softwareengineeringdaily.com/2020/05/28/distributed-systems-research-with-peter-alvaro/ 7:00
* concurrency is nearly always a bad idea https://www.arp242.net/go-easy.html
* [concurrency != parallelism](https://blog.golang.org/concurrency-is-not-parallelism)
* [multi-threading != parallelism](https://stackoverflow.com/a/806506/6813490) https://news.ycombinator.com/item?id=4495305
* https://news.ycombinator.com/item?id=23496994
* _sleeping barber problem_ http://kachayev.github.io/talks/kharkivpy%230/#/
* reactive in Python https://blog.oakbits.com/introduction-to-rxpy.html
* [the guy who wrote SQLAlchemy thinks async is kinda bs](https://news.ycombinator.com/item?id=18113889) + https://techspot.zzzeek.org/2015/02/15/asynchronous-python-and-databases/
* https://return.co.de/blog/articles/dont-drink-too-much-reactive-cool-aid/
* [asyncio problems](https://www.roguelynn.com/words/asyncio-we-did-it-wrong/)
* most (web) things are bound by network, not CPU https://talkpython.fm/episodes/show/225/can-subinterpreters-free-us-from-python-s-gil
* concurrency is a bad thing https://eli.thegreenplace.net/2018/go-hits-the-concurrency-nail-right-on-the-head/

## dep inject (DI)

https://www.youtube.com/watch?v=0yc2UANSDiw
* _dependency injection_: passing args [Conery 282]
* why?: loose coupling http://kc.my-junk.info/di-ioc-dip https://www.youtube.com/watch?v=sD94szvFqGw

https://testdriven.io/blog/python-dependency-injection
https://github.com/ZechCodes/Bevy
https://hakibenita.com/python-dependency-injection
https://romantomjak.com/posts/testing-python-code-that-makes-http-requests.html

---

* https://docs.pytest.org/en/latest/fixture.html#fixture
* in Python https://io.made.com/dependency-injection-with-type-signatures-in-python/ + https://moltenframework.com/v0.7.3/index.html + https://github.com/ekiro/haps + https://github.com/Dobiasd/enterprython/blob/master/why_you_want_formal_dependency_injection_in_python_too.md https://pythonbytes.fm/episodes/show/112/don-t-use-the-greater-than-sign-in-programming
* _inversion of control(IoC)_: you're not in charge of app control flow, only hooking into it https://www.baeldung.com/running-setup-logic-on-startup-in-spring example of IoC https://seddonym.me/2019/08/03/ioc-techniques/ https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way https://stackoverflow.com/questions/3058/what-is-inversion-of-control https://engineering.snagajob.com/dont-like-dependency-injection-898de93dc8d3 https://stackoverflow.com/a/2465052/6813490 https://stackoverflow.com/a/51117857/6813490 https://stackoverflow.com/a/140655/6813490 https://www.objc.io/issues/11-android/dependency-injection-in-java/ https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ ❓ pull in class deps all in one place [Conery 287]

> What is the glue that holds Django together? As a beginner entering, there really is no obvious central object to inspect, extend, or modify. https://www.reddit.com/r/Python/comments/olech/is_django_considered_pythonic_now/

## deployment

🗄
* `infra.md` config mgmt
* `linux.md` build systems
* `security.md` secrets mgmt
* `sql.md` migrations

https://blog.pecar.me/rds-blue-green
https://blog.pecar.me/gunicorn-restart
https://github.com/piku/piku

APPLICATION CONFIG
* env files: https://snarky.ca/use-toml-for-env-files/
* https://direnv.net/

DEPLOYMENT
* taxonomy: yolo (edit on server) FTP (edit on local, push to server) SCM (SSH to sever and pull repo, maybe use cron) CICD (triggered by repo hook https://dagger.io/) https://css-tricks.com/deployment/
* pipelines: fetch (clone from repo) build (install deps, compile) test (run unit tests) deploy (put artifact somewhere so CD can pick it up and run it)
* Jenkins https://itnext.io/jenkins-is-getting-old-2c98b3422f79 https://www.youtube.com/watch?v=WWcijE7ifcA
* BYO http://aosabook.org/en/500L/a-continuous-integration-system.html
* _deployment_: align higher env w/ lower env https://css-tricks.com/deployment/
* _staged deployment_: deploy to a few nodes at a time 📙 Kleppmann 4.112
* _blue-green deployment_: split traffic btw new and old; aka red-black https://fly.io/django-beats/smooth-database-changes-in-blue-green-deployments/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_198 https://news.ycombinator.com/item?id=39048317

RELEASE
* _release_: users get latest deployment
* have a `RELEASE.md` https://news.ycombinator.com/item?id=26902887
* have a runbook https://github.com/Microsoft/vscode/wiki/Development-Process#inside-an-iteration
* _canary release_: only subset of users get latest deployment https://medium.com/netflix-techblog/automated-canary-analysis-at-netflix-with-kayenta-3260bc7acc69 

FEATURE FLAGGING 🗄 `infra.md` analytics
* _feature flag_: toggle functionality; impl agnostic (env var, db, aaS) https://medium.com/@noahrobi/feature-toggles-give-you-superpowers-78fdeb7ab5e8
* https://github.com/flipt-io/flipt
* use cases: decouple deployment/release, canary release https://github.com/facebook/planout A/B testing https://findwork.dev/blog/django-b-testing-google-optimize https://www.evanmiller.org/
* lib: https://waffle.readthedocs.io/en/stable/
* service: paid (Launch Darkly, Split.io, Optimizely) on-prem (https://github.com/markphelps/flipt https://bullet-train.io/ https://github.com/Unleash/unleash)
* as tech debt https://www.youtube.com/watch?v=HhxNaPYpYiU https://github.blog/2021-04-27-ship-code-faster-safer-feature-flags/
* feature-flag-driven development
> Always start a feature with a feature flag and try to get something to production on day 1. even if it's only feature flagged to you. usual feature flag timeline: week 1 - developer and people interested in a feature week 3 - release or do beta with users
```python
class FeatureFlag(models.Model):
    name = models.CharField(max_length=80)
    enabled = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

## secrets

🗄
* `infra.md` config mgmt
* `shell.md` profiles

* _secret_: sensitive auth creds (db user/pass, AWS IAM roles) https://testdriven.io/blog/managing-secrets-with-vault-and-consul/#what-is-vault
* anything you can't version control
* don't use env var?! https://news.ycombinator.com/item?id=34055914
* scan Github https://github.com/eth0izzle/shhgit https://github.com/kootenpv/gittyleaks https://github.com/zricethezav/gitleaks
* _secrets mgmt_: instead of passing around over email, use a tool for SSoT / audit trail / encryption https://testdriven.io/blog/managing-secrets-with-vault-and-consul/#what-is-vault
* https://news.ycombinator.com/item?id=34083366

sops 📜 https://github.com/mozilla/sops
* = create encrypted secrets file for version control https://www.youtube.com/watch?v=AAUJjwdCx4I
* only values are encrypted
* workflow
```yaml
# config: `.sops.yaml` [1:50]
creation_rules:
    - path_regex: path/to/files # path to files that sops will encrypt
      kms/age: <public_key>     # public key to use
```
```sh
# open secrets file as human-readable to edit
sops my-secrets.yaml
# file encrypted viewed otherwise
bat my-secrets.yaml
```

---

https://github.com/Infisical/infisical
* https://github.com/tellerops/teller
> Teller is an open-source universal secret manager for developers that ensures the correct environment variables are set when starting an application. However, it's not a vault itself — it's a CLI tool that connects to a variety of sources, ranging from cloud secrets providers to third-party solutions like HashiCorp Vault to local environment files. Teller has additional functionality to scan for vault-kept secrets in your code, to redact secrets from logs, to detect drift between secrets providers and to sync between them. Given the sensitivity of accessing secrets, we can't emphasize enough the need to secure the supply chain for open-source dependencies, but we appreciate how easy the CLI is to use in local development environments, CI/CD pipelines and deployment automation.
* _KMS_: AWS service for storing encryption keys https://www.youtube.com/watch?v=eIvbUU8VH30

local dev and keeping secrets out of app/dotfiles
* app env: app uses `.env` + alias that when you nav to app dir cp `.env` from outside dotfiles
* shell env: source `.env.profile` from outside dotfiles
```sh
.env
.env.profile
├── dotfiles
│   └── .bash_profile
│   └── .zprofile
```

envs 🗄 `shell.md` env var
* don't use prod data outside of prod https://www.thoughtworks.com/radar/techniques/production-data-in-test-environments
* you don't need staging https://news.ycombinator.com/item?id=30899362
* _parity_: aka isomorphism 🗄 `testing.md` db
* db: not a silver bullet (Postgres in your Docker container will have some differences to db server you're connecting to in prod)
* codespaces https://www.thoughtworks.com/radar/tools?blipid=202203053 https://github.com/features/codespaces alternative https://www.daytona.io/ https://www.lastweekinaws.com/blog/the-real-reason-cloud-ide-adoption-is-lagging/

config in general
* _config_: everything that varies between deployment envs https://12factor.net/config 
* not to be confused with 'configuration mgmt' i.e. setting up consistent infra, although sometimes terms are mixed https://rednafi.github.io/digressions/python/2020/06/03/python-configs.html 🗄 `infra.md` Ansible
* can always just push your dev env to the cloud https://softwareengineeringdaily.com/2020/10/14/gitpod-cloud-development-environments-with-johannes-landgraf-and-sven-efftinge/
* _config class_: https://lincolnloop.com/blog/goodconf-python-configuration-library https://testdriven.io/blog/dynamic-secret-generation-with-vault-and-flask/ https://rednafi.github.io/digressions/python/2020/06/03/python-configs.html https://whalesalad.com/blog/doing-python-configuration-right [Grinberg chapter 7]
* _FTP on steroids_: spin up entire environment remotely then file watch/sync to mv local changes to remote https://slack.engineering/development-environments-at-slack/
* https://www.youtube.com/watch?v=omhJrT90lXU&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=39
* CLI https://smallstep.com/blog/command-line-secrets/
* store enums w/ versions https://martinfowler.com/articles/patterns-of-distributed-systems/versioned-value.html
* remote dev env https://www.gitpod.io/ https://www.youtube.com/watch?v=XcjqapXfrhk https://www.youtube.com/watch?v=llRLh8cM7QI 27:15 https://github.com/coder/coder

my current approach
* Makefile rule to sym link canonical env file into place from either `.env.dev` or `env.prod` [Osborn 14.106] export secrets from shell and document in README https://12factor.net/config downside is duplication btw files, this config class inheritance would pay off
```makefile
env-list:
	ls -al | grep '>'

env-dev:
	ln -sf .env.dev .env

env-prod:
	ln -sf .env.prod .env
```
* dummy approach to toggling database (in order to maintain test suite db setup)
* this emerged bc adding Postgres connection broke db setup for integration tests
* what you should probably do is overwrite the db connection in the test module itself
```python
if os.getenv("FLASK_ENV") == "production":
    db_uri = "postgresql://postgres:postgres@db:5432/postgres"
else
    db_path = os.path.join(basedir, os.getenv("DATABASE"))
    db_uri = "sqlite:///" + db_path
```

env file syntax
* _JSON_: work team, https://www.arp242.net/json-config.html generation and jsonnet https://leebriggs.co.uk/blog/2019/02/07/why-are-we-templating-yaml.html
* _YAML_: https://yaml.org/ file has to start with `---` (doesn't seem like people follow) linters https://github.com/adrienverge/yamllint processor https://github.com/mikefarah/yq generation https://github.com/jazzband/tablib
* _INI_: still used in Ansible https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#inventory-basics-formats-hosts-and-groups python's `ConfigParser` uses but maybe people don't like INI? 艘 gmail for 'Dmitrii' https://www.youtube.com/watch?v=HH9L9WFMfnE seems like people don't use .ini as extension https://github.com/rorymckinley/commcare-sandbox/tree/40cd03619641fd1ee94d5d544b03e0d1167e2b9f/ansible/inventories
* _altnernatives_: actual programming language (JS for Webpack, Python for setuptools) https://beepb00p.xyz/configs-suck.html#who_else
* _format problems_: reuse, templating languages = learning a new worse DSL https://beepb00p.xyz/configs-suck.html#cons https://www.arp242.net/yaml-config.html https://github.com/wincent/wincent/blob/master/fig/README.md https://leebriggs.co.uk/blog/2019/02/07/why-are-we-templating-yaml.html

* env var are strings
```python
# settings.py
TOGGLE = os.getenv("toggle", False)
# elsewhere
if settings.TOGGLE:
    pass
```
```conf
# eval to True
toggle=True
toggle=False

# eval to False
toggle=
```
