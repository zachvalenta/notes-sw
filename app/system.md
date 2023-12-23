# 开

## 参考

🗄 `infra.md`
📅 conferences https://www.micahlerner.com/2021/08/14/systems-conferences-2021.html https://www.micahlerner.com/2021/12/30/conferences-2022.html
📹 https://www.youtube.com/channel/UCDankIVMXJEkhtjv5yLSN4g/videos
🔍
* https://roadmap.sh/backend
* https://softwarerecs.stackexchange.com
* https://softwareengineering.stackexchange.com
📚
* Bueno mature optimization http://book.mixu.net/distsys/index.html
* Jeffrey distributed services
* Kleppmann data-intensive
* Google SRE https://sre.google/sre-book/table-of-contents/

## now

## next

---

* https://en.wikipedia.org/wiki/The_Association
* db per user https://news.ycombinator.com/item?id=38171322
state machine, audit https://blog.lawrencejones.dev/state-machines/ https://www.youtube.com/watch?v=YSUxLRlTzZ4
cellular https://news.ycombinator.com/item?id=37274871
 https://news.ycombinator.com/item?id=36208420 https://github.com/karanpratapsingh/system-design https://davidvujic.blogspot.com/2023/08/kafka-messaging-with-python-and-polylith.html

WORLD'S DUMBEST COMPLETE SAAS
* Vincent books 🗄 `django.md`
* https://saasitive.com/
> scaffold (deployment, monitoring), accounts (individual, teams), auth (registration, login/logout, pw update, account removal), subscriptions
* https://news.ycombinator.com/item?id=34530052
* https://news.ycombinator.com/item?id=34483294
* https://pocketbase.io/ 
* BYO Saas https://www.datasette.cloud/blog/2023/welcome/

## done

* _23_: 📙 Evans domain-driven
* _20_: gunicorn, uWSGI
* _19_: https://github.com/zachvalenta/nginx-wsgi URL shortener, Gitlab for CI
* _18_: AMQP/Spring thing for Dark Canary
* _17_: Google SRE book first 20 chapters

---

https://www.youtube.com/watch?v=rIt0uj8TaKg

incentives https://news.ycombinator.com/item?id=36380711&utm_term=comment

🗄 notebook 23.01.11

CRD DDD 🗄 notebook 22.12.13
* transport: HTTP, RPC, GraphQL
* service: business logic
* repo: mapper to db
* db

* do with the Golang microservices book https://news.ycombinator.com/item?id=34572263

> Microservices, while often sold as solving a technical problem, usually actually solve for a human problem in scaling up an organization. There's two technical problems that microservices purport to solve: modularization (separation of concerns, hiding implementation, document interface and all that good stuff) and scalability (being able to increase the amount of compute, memory and IO to the specific modules that need it). The first problem, modules, can be solved at the language level. Modules can do that job, and that's the point of this blog post. The second problem, scalability, is harder to solve at the language level in most languages outside those designed to be run in a distributed environment. But most people need it a lot less than they think. Normally the database is your bottleneck and if you keep your application server stateless, you can just run lots of them; the database can eventually be a bottleneck, but you can scale up databases a lot. The real reason that microservices may make sense is because they keep people honest around module boundaries. They make it much harder to retain access to persistent in-memory state, harder to navigate object graphs to take dependencies on things they shouldn't, harder to create PRs with complex changes on either side of a module boundary without a conversation about designing for change and future proofing. Code ownership by teams is something you need as an organization scales, if only to reduce the amount of context switching that developers need to do if treated as fully fungible; owning a service is more defensible than owning a module, since the team will own release schedules and quality gating. I'm not so positive on every microservice maintaining its own copy of state, potentially with its own separate data store. I think that usually adds more ongoing complexity in synchronization than it saves by isolating schemas. A better rule is for one service to own writes for a table, and other services can only read that table, and maybe even then not all columns or all non-owned tables. Problems with state synchronization are one of the most common failure modes in distributed applications, where queues get backed up, retries of "bad" events cause blockages and so on. https://news.ycombinator.com/item?id=34231020

* https://news.ycombinator.com/item?id=34612919
* https://www.youtube.com/@AsliEngineering/videos
* things you need in an app https://www.amazon.com/Become-Awesome-Software-Architect-Foundation/dp/1697271065
* Heroku clone https://www.youtube.com/watch?v=zhJLVFR3pE8
* Netflix clone https://www.youtube.com/watch?v=gbyYXgiSgdM
* Facebook clone https://www.youtube.com/watch?v=xSUm6iMtREA
* PagerDuty clone https://www.youtube.com/watch?v=4xuBT3BbsYU alerts https://github.com/keephq/keep

* Jeffrey distributed systems ++ rf
> ++ `infra.md` telemetry
* course on microservices https://www.youtube.com/watch?v=hmkF77F9TLw https://www.youtube.com/watch?v=NVvIpqmf_Xc
* https://brooker.co.za/blog/
* https://runninginproduction.com/podcast/

STREAMING / BLOCKING 🗄 `computation.md` serialization
* blocking
* https://ossinsight.io/blog/why-we-choose-tidb-to-support-ossinsight/
* async https://www.b-list.org/weblog/2022/aug/16/async https://www.youtube.com/watch?v=bw1qeMoFBmw https://www.youtube.com/watch?v=0z74b3c63GA
* batch: TQ, Airflow
> port from `db.md`
* streaming: Kafka https://www.youtube.com/watch?v=qi7uR3ItaOY 🗄 site/drafts/ddd.md
* https://simonwillison.net/2021/Jul/1/pagnis/ https://news.ycombinator.com/item?id=38167423
* forum software in 500 lines or less https://news.ycombinator.com/item?id=33153152
> what is the relationship bte Kafka and faust? https://www.youtube.com/watch?v=Ik1PBbCWcTc
> is flink streaming or batch? https://github.com/apache/flink
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
* _stream processing_: one at a time 📙 Kleppmann ch. 10 🗄 `system.md` Kafka
* libraries: https://github.com/robinhood/faust https://github.com/apache/flink
* sources: clickstream, IoT sensors, time series
* lower memory consumption
> Once the block has finished executing, the Ruby interpreter is able to garbage collect the data for both the raw line and processed message, since it can see that the program won’t reference them again. This means that the Ruby interpreter can reuse the piece of memory in which they were stored.
```ruby
stats = {}
File.open("samplelog.txt").each_line do |l|
  message = parse_raw_log_line(l)
  stats = add_message_to_stats(message, stats)
end
```

https://news.ycombinator.com/item?id=32319147
https://www.youtube.com/channel/UCDankIVMXJEkhtjv5yLSN4g/videos

rf
> Solutions architect - Associate
* db https://news.ycombinator.com/item?id=34434025
* soft delete https://news.ycombinator.com/item?id=32156009 https://brandur.org/soft-deletion https://brandur.org/fragments/deleted-record-insert
* https://www.youtube.com/watch?v=Y-Gl4HEyeUQ
* https://www.youtube.com/watch?v=a2rcgzludDU
* https://jameslittle.me/blog/2020/about-the-guestbook/
* https://benhoyt.com/writings/io-is-no-longer-the-bottleneck/
* https://news.ycombinator.com/item?id=29727707
* https://www.natemeyvis.com/software-design/ https://www.natemeyvis.com/an-argument-from-jimmy-koppel/
* https://simonwillison.net/2022/Feb/9/single-dependency-stacks/
* https://www.semicolonandsons.com/series/learn-system-design-for-web
* https://sirupsen.com/napkin/problem-2
* https://mattsegal.dev/django-prod-architectures.html
* https://github.com/sirupsen/napkin-math https://sirupsen.com/napkin/problem-7
* https://anthonynsimon.com/blog/one-man-saas-architecture/
* https://sirupsen.com/napkin/problem-1
* deploy Django w/ Google Cloud Run https://news.ycombinator.com/item?id=24705668
* https://maheshba.bitbucket.io/blog/2021/10/19/42Things.html
* https://calpaterson.com/bank-python.html
* interviewing https://www.youtube.com/playlist?list=PLrtCHHeadkHptUb0gduz9pxLgvtKWznKj
* rf monitoring re: `link.md` 'speed'
* Kleppmann 1.5 (db, cache, search, MQ)
> ❓ where are you with Kleppmann notes? thought that everything from section 1 has been put into notes, why is there a section for him under 'architecture'?
* https://12factor.net/
* https://increment.com/software-architecture/
* taxonomize https://mattsegal.dev/django-prod-architectures.html
* http://aosabook.org/en/distsys.html
* https://github.com/zachvalenta/nginx-wsgi - general refactor for 1) Poetry 2) Caddy
* https://robertheaton.com/2020/04/06/systems-design-for-advanced-beginners/
* rf 'next'
* architecture - https://www.cosmicpython.com/book/preface.html
* Kleppmann chapter 1 notes @ 14 -> `math.md` distributions
* servers - Nginx - https://github.com/zachvalenta/nginx-wsgi https://serverfault.com/q/821284/415712 https://stackoverflow.com/a/25486871/6813490
* servers - Nginx - tune https://blog.codeship.com/tuning-nginx/
* servers - BYO https://defn.io/2018/02/25/web-app-from-scratch-01/ http://joaoventura.net/blog/2017/python-webserver/
* interviewing - system design - https://github.com/donnemartin/system-design-primer https://github.com/madd86/awesome-system-design https://www.youtube.com/watch?v=VYuToviSx5Q
* https://news.ycombinator.com/item?id=26300191
* https://man.sr.ht/ops/ https://bible-api.com/ https://github.com/seven1m/bible_api https://robertheaton.com/2020/04/06/systems-design-for-advanced-beginners/
* security https://www.freecodecamp.org/learn/information-security/information-security-projects/stock-price-checker
* caching https://mattsegal.dev/simple-django-deployment.html
* infra https://mattsegal.dev/simple-django-deployment.html
* https://saasitive.com/

# API

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

JSON Schema https://json-schema.org/
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

OpenAPI
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

# ARCHITECTURE

🔍 https://github.com/DovAmir/awesome-design-patterns
📙 Brooks design of design https://news.ycombinator.com/item?id=33410375

## approaches

🗄
* `db.md` migrations, scaling
* `language.md` design
* `science.md` complexity

SEMANTICS 🗄 distributed/semantics
* _architecture_: the stuff that's hard to change
* will change with each order of magnitude i.e. from 1.5k users to 10k 📙 Kleppmann [17,22]
* _node_: process https://leanpub.com/systemdesignmanual/read_sample
* _service_: 1/n nodes providing API https://leanpub.com/systemdesignmanual/read_sample
* _elastic_: scales automatically with load 📙 Kleppmann [17]

BAKED DATA
* _baked data_: data embedded as static asset https://simonwillison.net/2020/Dec/13/datasette-io/ https://news.ycombinator.com/item?id=28015980 https://postlight.com/insights/big-data-small-effort
* bc full stack SQL doesn't work https://news.ycombinator.com/item?id=26822884 https://simonwillison.net/2021/Jul/28/baked-data/
* aka flat data https://news.ycombinator.com/item?id=27197950
* sql.js https://github.com/sql-js/sql.js/ https://selectstarsql.com/frontmatter.html#technicals https://jvns.ca/blog/2019/09/30/notes-on-building-sql-exercises/ https://news.ycombinator.com/item?id=27016630
* query SQLite over HTTP https://github.com/psanford/sqlite3vfshttp
* with pyodide https://news.ycombinator.com/item?id=31261777 https://adtax.paulromer.net/

STATIC SITES, JAMSTACK
* _static site_: content not generated on the fly i.e. no db/server interaction https://wsvincent.com/static-vs-dynamic-a-question-of-layers/
* generators https://github.com/ehouse/kackle https://www.youtube.com/watch?v=ShBD5v6YoNw
* _JAMstack_: static site + APIs
* = dynamism via APIs instead of db https://wsvincent.com/what-is-a-static-site-generator/
* advantages: speed (everything on CDN) security (no db) ++ good for SEO? https://immutablewebapps.org
* 📍 clean up --> https://alexdanco.com/2019/10/26/everything-is-amazing-but-nothing-is-ours/ apparently good for SEO as well Netlify, Gridsome https://redwoodjs.com/ deployment on Zeit, Netlify https://softwareengineeringdaily.com/2020/04/30/jamstack-content-management-with-scott-gallant-jordan-patterson-and-nolan-phillips/ 15:00 https://hacks.mozilla.org/2020/10/mdn-web-docs-evolves-lowdown-on-the-upcoming-new-platform  what it means for backend dev https://www.youtube.com/watch?v=Z2JK7SS82wE https://www.youtube.com/watch?v=grSxHfGoaeg https://scotch.io/@sw-yx/python-the-jamstack

MONOLITH/DB/CDN
> It is well-known that the majority of the cost of software is not in its initial development, but in its ongoing maintenance [Kleppmann 24] Vinsel, Innovation Delusion
> Scaling for many web applications is typically bottlenecked by the database, not the web workers. - https://pythonspeed.com/articles/dont-need-kubernetes/ https://stribny.name/blog/2020/07/scaling-relational-sql-databases
> Build a monolith with copious amounts of telemetry. Use a RDBMS. Use a CDN. Let your telemetry guide you on how to scale, cache, or split your workloads. Don't hire people who want to boil the ocean. https://news.ycombinator.com/item?id=25037628
* just use one big db https://news.ycombinator.com/item?id=31084147
* _vertical scaling_: get faster drives for db
> I am always puzzled about this "autoscale" thing on a cloud. If your task can be represented as something like calculate sum of some ginormous array then sure. Split array in parts and launch thousand instances each working on it's own slice and then combine. In way more common situation you have a service hitting database and doing something with it. Sure you can spin a thousand instances of said service. But they will all be hitting the same database. - https://news.ycombinator.com/item?id=21741870
* _horizontal scaling_: shard https://www.youtube.com/watch?v=7v-wrJjcg4k until recently you waited as long as you could on this 📙 Kleppmann 1.18
> horizontal-scaling is often based on the partitioning of the data i.e. each node contains only part of the data, in vertical-scaling the data resides on a single node and scaling is done through multi-core i.e. spreading the load between the CPU and RAM resources of that machine. With horizontal-scaling it is often easier to scale dynamically by adding more machines into the existing pool - Vertical-scaling is often limited to the capacity of a single machine, scaling beyond that capacity often involves downtime and comes with an upper limit. - https://stackoverflow.com/a/11715598/6813490

SERVERLESS
* _types_: from FaaS (https://github.com/beer-garden/beer-garden) to cloud SQL (BigQuery) to messaging (SQS, Twilio) to ITTT (Zapier) https://softwareengineeringdaily.com/2019/01/10/zeit-serverless-cloud-with-guillermo-rauch/
* _downsides_: local dev https://twitter.com/dvassallo/status/1154516910265884672 speed and cost https://news.ycombinator.com/item?id=21046547 https://einaregilsson.com/serverless-15-percent-slower-and-eight-times-more-expensive/
* _events_: API, timer, msg
* _start_: cold (download code, start container, bootstrap runtime, run code) warm (run code)
* in Python https://github.com/Miserlou/Zappa
* testing https://buddy.works/tutorials/integration-testing-for-aws-lambda-in-go-with-docker-compose

NO CODE
* _retool_: https://retool.com/ https://www.youtube.com/watch?v=4xuBT3BbsYU https://www.youtube.com/watch?v=ChTGbmR2NeM
* wrap and connect APIs https://softwareengineeringdaily.com/2019/12/19/no-code-with-shawn-wang/ aka workflow automation https://github.com/n8n-io/n8n https://news.ycombinator.com/item?id=24648960
* _automatisch_: Zapier alternative https://github.com/automatisch/automatisch https://tedium.co/2023/03/04/self-hosted-saas-app-alternatives/
* _Zapier_ https://softwareengineeringdaily.com/2020/02/27/makerpad-low-code-tools-with-ben-tossell/ https://softwareengineeringdaily.com/2020/02/26/parabola-no-code-data-workflows-with-alex-yaseen/
* Honey Comb https://news.ycombinator.com/item?id=23633110 https://www.alexhudson.com/2020/01/13/the-no-code-delusion/ https://www.makerpad.co/ WebFlow https://news.ycombinator.com/item?id=27421408
* https://news.ycombinator.com/item?id=28984955

WEB APP CHECKLIST
* env: config, Docker, ❌ auth
* CQ: testing, hooks
* data: seed, repl, ❌ migrations, serialization, ORM
* UI: styling, pagination, search
🏡 intermediate - ✅ migrations, auth, env (✅ config, ✅ Docker)
🥕 basic - CRUD (✅ ORM, ✅ serialization, seed) UI (styling, search, pagination) CQ (✅ testing, hooks)

MICROSERVICES
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

options https://drewdevault.com/2020/09/20/The-potential-of-federation.html
* _centralized_: you own all the servers
* _peer to peer (p2p)_: you only own your serverr
* _federation_: servers work together but not p2p https://lwn.net/Articles/687294/ https://github.com/mastodon/mastodon

taxonomy
* _monolith_: single service, single data store https://news.ycombinator.com/item?id=24505467
* _SOA (service oriented)_: n services, n data stores
* _DOA (data oriented)_: n services, single data store https://blog.eyas.sh/2020/03/data-oriented-architecture/ https://changelog.com/podcast/522

---

* layered architecture https://blog.europython.eu/kraken-technologies-how-we-organize-our-very-large-pythonmonolith/
* event-driven https://encore.dev/blog/event-driven-architecture
* beware theologians https://news.ycombinator.com/item?id=26492798
* _patterns_: MVC, hexagonal https://blog.carlmjohnson.net/post/2020/go-cli-how-to-and-advice/ https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749
* _resiliency_: perform job through failure https://leanpub.com/systemdesignmanual/read_sample
* Lisp, database inside codebase https://news.ycombinator.com/item?id=26160186 https://feifan.blog/posts/the-database-inside-your-codebase
* _kill switch_: force upgrade mobile app https://simonwillison.net/2021/Jul/1/pagnis/
* _bounded context_: don't let a word mean two different things in the same part of the system ex. 'account' inside primary system vs. 'account' during Paypal integration; again, duh
* _circuit breaker_: error handling https://github.com/Netflix/Hystrix/wiki/How-it-Works https://www.gremlin.com/chaos-monkey/ https://pypi.org/project/circuitbreaker/ https://sirupsen.com/napkin/problem-11-circuit-breakers
* e.g. downstream call fails, return empty list instead of 404 and poll downstream, have limits on resources devoted to downstream
* avoid fault in one part of a system taking down the system
* _coupling_: one change necessitates another
* _horizontal scaling_: aka shared-nothing architecture [Kleppmann 17]
* _multi-tenant_: Edge, Sentry, Parse https://www.youtube.com/watch?v=W1fkGyIcePA&t=1044s https://www.pythonpodcast.com/datacoral-serverless-technology-episode-214/ 15:00-19:00 https://www.youtube.com/watch?v=OfPE7yj1trw https://www.viget.com/articles/multi-tenancy-in-django
* _service mesh_: https://servicemesh.io/ https://news.ycombinator.com/item?id=17415421 https://www.digitalocean.com/community/tutorials/an-introduction-to-service-meshes sidecar, eBPF https://www.thoughtworks.com/radar/techniques?blipid=202203060 Istio
* data mesh https://news.ycombinator.com/item?id=30721198 https://www.thoughtworks.com/radar/techniques?blipid=201911051
* _SSoT_: single source of truth
* _SPoF_: single point of failure
* _fault domain_: components sharing SPoF https://lethain.com/fault-domains/
* _sink_: https://martinfowler.com/architecture/ https://engineering.videoblocks.com/web-architecture-101-a3224e126947

Kleppmann
* _reliability_: works even if hw/sw failure [6]
* _scalability_: able to deal w/ growth (data, traffic, complexity)
* _maintainability_: other devs able to work on system
> it is well know that the majority of the cost of software is not in its intial development, but its ongoing maintenance [Kleppmann 18] https://www.jefftk.com/p/designing-low-upkeep-software
* _db on 1 machine_: requires planned downtime [8]
* _db on n machines_: can do rolling upgrade [8]
* _n db_:
* _things that can go wrong_: runaway process (consuming too much memory) [8] unresponsive downstream service [9] operator error [9]
* _how to prevent things going wrong_: testing https://danluu.com/why-benchmark/ easy rollback, monitoring
* _fan out_: num of req to other services to handle one incoming req [11]
📍 need to review SQL of Twitter example
* _evolvability_: ability to change different parts of system independently [Kleppmann 4.128]

KISS
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
* Hickey simple made easy https://news.ycombinator.com/item?id=38433358 https://www.youtube.com/watch?v=LKtk3HCgTa8 data is not easy https://grishaev.me/en/ddd-lie
* https://www.benkuhn.net/progessays/
* one dev's edge cases are another's entire project 📙 Kleppmann 491

* _extract_: separate [Fowler https://refactoring.com/catalog/]
* _inline_: combine
> Inlining is the concept of replacing a function call in a program with the contents of the function itself, thus avoiding the call. https://golangweekly.com/issues/470
* _bikeshedding_: aka yak shaving https://jsonapi.org/ http://bikeshed.org/ https://drewdevault.com/2020/08/17/Engineers-solve-problems.html

depends on use case
> Some applications where you would consider ditching Django to shave off some latency are: a stock trading marketplace; an global online advertisement serving network; a low level infrastructure control API - https://mattsegal.dev/is-django-too-slow.html
>  Forget that all these things exist: Microservices, Lambda, API Gateway, Containers, Kubernetes, Docker. Anything whose main value proposition is about “ability to scale” will likely trade off your "ability to be agile & survive". That’s rarely a good trade off. Start with a t3.nano EC2 instance, and do all your testing & staging on it. It only costs $3.80/mo. Then before you launch, use something bigger for prod, maybe an m5.large (2 vCPU & 8 GB mem). It’s $70/mo and can easily serve 1 million page views per day. - https://twitter.com/dvassallo/status/1154516910265884672

Getting Real
> don't waste time on problems you don't have yet - page 42
> We ran Basecamp on a single server for the first year...most of the problems we feared weren't that big of a deal to customers. As long as you keep people in the loop, and are honest about the situation, they'll understand. - page 44
> The bigger problem isn't scaling, it's getting to the point where you have to scale. - page 45

* listen to Knuth -> fast code matters less than you think https://www.youtube.com/watch?v=PhUb7y9WZGs
> We should forget about small efficiencies, say about 97% of the time; premature optimization is the root of all evil. - Donald Knuth
* write code that's easy to throw away
> Write code to be changed and/or deleted. This comes from someone who's worked in startups for the past 5 years. We often overestimate how long code =is supposed to live. We as programmers often exaggerate with our DRY and stuff, we do not want to repeat ourselves, we want to find another abstraction...we want to find some general that can help us abstract stuff away. My piece of advice is that, step back and consider for a moment that this code is not going to stay in, so maybe only try and find the abstraction layer once you really sure that this is how it's going to be. - Thorsten Ball https://developeronfire.com/podcast/episode-373-thorsten-ball-interpreters-compilers-and-writing
> To be attractive to hackers, a language must be good for writing the kinds of programs they want to write. And that means, perhaps surprisingly, that it has to be good for writing throwaway programs. - http://paulgraham.com/popular.html
* don't cargo cult 'best practices'
> Sophisticated design principles can make your code faster, more flexible, more modular, and all of the other positive adjectives that people use to describe high-quality software. But they also make it more complex. `AbstractSyntaxRenderers` and `DoubleBackflipDatabaseTransmogrophiers` do make some programs clearer and easier to understand, especially large ones. But they can also be the equivalent of using a metrics-oriented, fully agile, stakeholder-prioritized development flow for working on a jigsaw puzzle with your dad. Sure you’re following best practices, but you probably didn’t need to, and now your dad thinks you’re a Scientologist. - https://robertheaton.com/2018/12/02/programming-project-5-snake/
* wait for shared concerns to emerge -> repeat yourself until you find the right abstraction https://programmingisterrible.com/post/176657481103/repeat-yourself-do-more-than-one-thing-and
> There seemed to be a tendency to extract tiny packages first instead of waiting for a shared concern to emerge from the code and only then extracting a package. https://commandercoriander.net/blog/2017/12/31/writing-go/
> The problem with always using an abstraction is that you’re preemptively guessing which parts of the codebase need to change together. “Don’t Repeat Yourself” will lead to a rigid, tightly coupled mess of code. Repeating yourself is the best way to discover which abstractions, if any, you actually need.

## caching

📙 Christian chapter 4
🗄
* proxy
* `http.md` caching

semantics
* _cache_: tmp storage for read; e.g. browser (SQLite) network (CDN) db (connection pool); can cache to either memory or disk https://danielmiessler.com/blog/nginx-caching-tempfs/
* _buffer_: tmp storage for write
> Python's standard out is buffered (meaning that it collects some of the data "written" to standard out before it writes it to the terminal). Calling sys.stdout.flush() forces it to "flush" the buffer, meaning that it will write everything in the buffer to the terminal, even if normally it would wait before doing so. https://stackoverflow.com/questions/10019456/usage-of-sys-stdout-flush-method
* flush buffer https://stackoverflow.com/questions/3167494/how-often-does-python-flush-to-a-file https://stackoverflow.com/questions/29712445/what-is-the-use-of-buffering-in-pythons-built-in-open-function

* e.g. Python writerow
* _flush_: write buffer to disk https://stackoverflow.com/a/15042890
* _memoization_: cache at function level https://stackoverflow.com/a/6469470 https://news.ycombinator.com/item?id=31434078
* _cold_: infrequently used data
* _hot_: frequently used data
* _cache hit_: can pull from cache
> A cache hit is hopefully much more than twice as fast as a cache miss. https://calpaterson.com/ttl-hell.html
* _cache miss_: have to go to db
> It's important never to require a cache hit - even as a soft requirement. Evictions can happen at inconvenient times - such as when some other part of the system is under load - and there mustn't be any negative consequences to a cache miss. https://calpaterson.com/ttl-hell.html

eviction, expiry
* _eviction_: rm item based on usage e.g. LRU
* _expiration_: rm item based on TTL https://calpaterson.com/ttl-hell.html
> Data can be evicted before it has expired. And it often will be: most caches don't consider the TTL when looking for stuff to evict.
> Caching by TTL gives up correctness to gain speed.
* _LFU_: 
* random: 
* _LRU_: ensures cache full/hot as possible; used by application caches https://calpaterson.com/ttl-hell.html
```python
# There's nothing wrong with the above code but it only allows for strategy #1: never invalidate https://calpaterson.com/ttl-hell.html
from functools import lru_cache
@lru_cache(maxsize=1000)
def get_slow_thing_v1(thing_id):
    thing = get_slow_thing_from_a_database_layer(thing_id)
    return thing
```
* _update-on-write_: update cache item on db write
> Sometimes you want to cache something that will change. For example, your application's User object: username, email address, postal address, etc. This data is bound to change over time but is also accessed extremely frequently, often on every request or as part of every operation. The best approach here is to update the cache whenever you update the data in your persistent store.

misc
* _cache stampede_: user req for item not in cache, code begins to generate, during generation other reqs for same item, code begins n generations, server falls over; avoid by putting flag in cache to say "hey, I'm working on creating this item"
* _thrashing_: when computation continuously interrupted by context switch of cache items from one program to another resulting in no computation being done
* _namespace_: add timestamp key (210526) to item key (user-bob) https://calpaterson.com/ttl-hell.html

ideas https://calpaterson.com/ttl-hell.html
> Using a cache often changes the implicit complexity class of the system - downwards, and towards constant time.
> There's a snobbery about application level caches. It's more respectable to rewrite the program in a "systems programming language" (read: fast, compiled, for the serious) than to apply Memcache liberally to your PHP app (read: a "band-aid", apache2, used only by jokers).
> One particularly naughty thing to do is to store web sessions only in the cache. A cache miss then becomes an involuntary logout for the hapless user who has done nothing wrong and transgressed no one. Instead, use strategy #2 above and store the web-sessions in your database, using your cache just as a speedup.
> One tip: it's best to start by looking to invalidate. To paraphrase someone: "ask not of what you can cache - ask of what you can invalidate". If you can't invalidate something reliably, it's unlikely that you can cache it in the first place.

---

* https://softwareengineeringdaily.com/2023/08/08/database-caching-with-ben-hagan/
* TTL https://news.ycombinator.com/item?id=26620730 https://calpaterson.com/ttl-hell.html
* _cache invalidation_: https://news.ycombinator.com/item?id=26686770 https://blog.cerebralab.com/The_second_hardest_thing_in_programming_-_Part_1
* Cloudflare do image compression per browser (e.g. webp for Chrome) https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#44:00
https://healeycodes.com/webdev/python/beginners/tutorial/2019/07/07/introduction-to-caching-with-python.html

in Python
* BYO https://dbader.org/blog/python-memoization use a decorator https://github.com/realpython/python-guide/blob/1d5905d5d7e25ebf11cda50d3d93ac636c87a993/docs/writing/structure.rst#decorators
* built-in LRU cache https://datawhatnow.com/things-you-are-probably-not-using-in-python-3-but-should/
* https://adamj.eu/tech/2021/01/21/simple-in-memory-caching-of-django-models-with-cachetools/

in general

> A good example of a piece of functionality that is better handled with decoration is memoization or caching: you want to store the results of an expensive function in a table and use them directly instead of recomputing them when they have already been computed. This is clearly not part of the function logic. [Hitchhiker's Guide 3.1.6]

*  https://www.openmymind.net/Caching-Your-Worst-Best-Friend/
* https://bhavaniravi.com/blog/caching-in-python 
* https://ieftimov.com/post/when-why-least-frequently-used-cache-implementation-golang/ 
* http://danluu.com/2choices-eviction/
* https://www.digitalocean.com/community/tutorials/web-caching-basics-terminology-http-headers-and-caching-strategies

Redis
* implementation http://aosabook.org/en/nosql.html
* test/mock https://github.com/cunla/fakeredis-py
* use Postgres as impl https://github.com/alash3al/redix
* governance https://news.ycombinator.com/item?id=23689549
* key expiration https://news.ycombinator.com/item?id=30099572
* alternative https://github.com/dragonflydb/dragonfly https://github.com/buraksezer/olric#installing
> You can either set Redis up as a "data-structures" server or you set it up right as a cache. You can't do both. If you choose to use Redis as your cache, ensure that the cache instance is only serving as your cache. Your inter-system message bus should be on a different Redis with a different configuration. https://calpaterson.com/ttl-hell.html

memcached
* _is?_: volatile cache https://news.ycombinator.com/item?id=23689549 aka application caching layer
* _how?_: distributed hash table i.e. n instances of app share 1 distributed instance of memcached
* _why?_: so you don't have to read from db
* _disadvantages_: doesn't track cache misses; meant for simple data, not tables or objects; not durable http://aosabook.org/en/nosql.html
* _sink_: https://realpython.com/python-memcache-efficient-caching/ https://github.com/thadeusb/flask-cache Django has OOB support for memcached https://docs.djangoproject.com/en/2.1/topics/cache/

## concurrency

📙 Butcher models https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks
🗄
* `golang.md` concurrency
* `linux.md` threads
* `python.md` concurrency

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

## diagrams

🗄
* `aesthetics.md` design
* `math.md` graphs

TYPES
* _concept map_: https://cmap.ihmc.us/docs/learn.php
* _DAG_: https://arthursonzogni.com/Diagon/#GraphDAG
* _ERD_: syntax https://eli.thegreenplace.net/2019/to-orm-or-not-to-orm/ 📙 Karwin [7] 🗄 `sql.md` utils
* _flow_: https://news.ycombinator.com/item?id=26303784
* _infrastructure_: https://github.com/mingrammer/diagrams 
* _mind map_: https://github.com/nadrad/h-m-m https://markmap.js.org/ https://news.ycombinator.com/item?id=24132631 https://news.ycombinator.com/item?id=27614912 https://strlen.com/treesheets/ https://news.ycombinator.com/item?id=34184993 https://blog.dornea.nu/2015/09/17/organizing-and-visualizing-knowledge/ https://www.dendron.so/
* _state_: https://github.com/statecharts/statecharts.github.io/issues/44 https://en.wikipedia.org/wiki/State_diagram
* _tree/map_: https://github.com/niyue/skillmap
* _sequence_: msg passing https://sequencediagram.org https://gist.github.com/zachvalenta/2aeac1f945c5848c79087b2481cb187a https://arthursonzogni.com/Diagon/#Sequence
* https://jessems.com/posts/2023-07-22-the-unreasonable-effectiveness-of-sequence-diagrams-in-mermaidjs
* _UML_: aka class diagram https://www.amazon.com/UML-Distilled-Standard-Modeling-Language/dp/0321193687
* alternative syntax 📙 Evans domain-driven [42]
* can be used for ERD in Mongo https://stackoverflow.com/q/11323841 https://stackoverflow.com/q/6010408

| provider   | types             |   notes                                                                         |
|------------|-------------------|---------------------------------------------------------------------------------|
| D2         | ERD, sequence     | https://play.d2lang.com/                                                        |
| DrawSQL    | ERD               | https://drawsql.app/me-195/diagrams/testing123                                  |

PROVIDERS 🔍 https://xosh.org/text-to-diagram/
* ascii to SVG https://github.com/ivanceras/svgbob http://asciiflow.com/
* _DrawSQL_: ERD
* _Excalidraw_: https://excalidraw.com/ https://gist.github.com/zachvalenta/f4c2226b991b69d129fe7d1d40119f43
* _GraphViz_: https://sketchviz.com/graphviz-examples https://github.com/BurntSushi/erd
* _Mermaid_: editor https://mermaid.live/ no current Hombrew version https://github.com/mermaid-js/mermaid-cli https://github.com/mermaid-js/mermaid-cli/issues/25
* mermaid https://news.ycombinator.com/item?id=34906378
* _Monodraw_: https://monodraw.helftone.com/
* _PlantUML_: UML `.puml`

## proxies

🗄
* `flask.md` context
* `infra.md` servers

SERVERS
* req/res: OS takes req on port, hands req to web server, web server hands req to app server, app server hands req to application, res flow back up
* servers useful in Python bc GIL only allows one thread to execute at a time so server does pools other connections 📙 Butcher practice 1.3.3
* why use a server? in Python's case bc 
* _machine_: hw (or vm) https://sre.google/sre-book/production-environment/
* _server_: machine w/ server sw or sw itself https://sre.google/sre-book/production-environment/
* _web server_: deal w/ HTTP, handle static content and rate limiting https://www.quora.com/What-are-the-differences-between-nginx-and-gunicorn
* port 80
* BYO https://ruslanspivak.com/lsbaws-part1/
* _app server_: translate HTTP into obj for web framework
* can also be pressed into service as combo app/web server https://stackoverflow.com/a/38982989 https://www.nginx.com/resources/glossary/application-server-vs-web-server/
* port 8080

CONNECTIONS
* _threads_: single (one thread per connection; WSGI, PHP) multi (📍 http://aosabook.org/en/nginx.html https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#adding-concurrency-and-monitoring)
* _idle_: different languages require diff amount of memory e.g. Golang allocates buffer in preparation for data to be read (whereas C++ does not) https://blog.phusion.nl/2018/09/18/migrating-passenger-from-cxx-to-go/
* _multiple_: connections from many clients to single server
* _parallel_: multiple connections from single client to a server; HTTP spec recommends max of 2; workaround is multiple servers deal with different resources
* _persistent_: Keep-Alive, WebSocket
* _pipeline_: send a bunch of requests before waiting for response

TYPES
* _proxy_: layer between requester and responder
* _reverse proxy_: closer to servers; less of a need given a cloud environment where a load balancer is already built-in https://pythonspeed.com/articles/gunicorn-in-docker/ https://testdriven.io/blog/django-docker-traefik/ https://www.artur-rodrigues.com/tech/2023/03/12/reverse-proxy-with-dynamic-backend-selection.html
* _forward proxy_: closer to users; way for users to access resources outside network https://www.linuxbabe.com/it-knowledge/differences-between-forward-proxy-and-reverse-proxy
* _sidecar proxy_: https://caddyserver.com/docs/

CDN
> Caching reverse proxies that you self-host, like Varnish and Apache Traffic Server, can use non-standard PUSH and PURGE verbs that let you explicitly control the cache contents. If you can invalidate explicitly you can use strategies #2 and #3 [update-on-write]. If you have the file on hand, why not also populate your reverse proxy's cache? The nice thing overall about caching at the HTTP level is that it takes work off the applications server's plate. https://calpaterson.com/ttl-hell.html
* BYO https://github.com/leandromoreira/cdn-up-and-running
* https://jvns.ca/blog/2016/04/29/cdns-arent-just-for-caching/
* https://css-tricks.com/adding-a-cdn-to-your-website/
* Google/Facebook CDNs are blocked in China https://www.freecodecamp.org/news/devblog-launch-your-developer-blog-own-domain/
* https://www.youtube.com/watch?v=6DXEPcXKQNY
* _sink_: https://arp242.net/cdn.html https://css-tricks.com/adding-a-cdn-to-your-website/ http://highscalability.com/blog/2011/2/28/a-practical-guide-to-varnish-why-varnish-matters.html Whitenoise vs. nginx https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/ https://pasztor.at/blog/building-your-own-cdn
* BYO https://dev.to/megajakob/how-to-build-your-own-cdn-io1 https://debugged.it/blog/building-your-own-cdn/

---

* when things go wrong on Cloudflare https://news.ycombinator.com/item?id=30054739
📍 https://www.youtube.com/watch?v=-W9F__D3oY4
* _OpenResty_: Nginx + script some more logic in with Lua https://www.dataengineeringpodcast.com/linode-object-storage-service-episode-125/ 10:00
* _firewall_: impl rules for server in/egress (e.g. iptables)
* phoning home, open snitch https://news.ycombinator.com/item?id=33506576
* https://softwareengineeringdaily.com/2021/08/10/fly-io-geographic-app-deployment-with-kurt-mackey/
* _sink_: https://serversforhackers.com/t/proxies https://www.maxcdn.com/one/visual-glossary/proxy-caching/ reverse cache https://msdn.microsoft.com/en-us/library/windows/desktop/dd892097%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396 https://blog.envoyproxy.io/introduction-to-modern-network-load-balancing-and-proxying-a57f6ff80236

load balancing
* https://news.ycombinator.com/item?id=35588797
* https://www.youtube.com/watch?v=galcDRNd5Ow
* load balancer vs. API gateway vs. ingress controller https://caddyserver.com/docs/
* _HAProxy_: just does load balancing (vs. Nginx, which also serves static assets) https://stackoverflow.com/a/21181066/6813490 conf (port, lb algo, server for forwarding)
* Nginx, Envoy https://dropbox.tech/infrastructure/how-we-migrated-dropbox-from-nginx-to-envoy https://news.ycombinator.com/item?id=32572153
* _algos_: least-busy (based on server pushing <foo> metric?) round-robin (subject to chance i.e. server n could unluckily keep getting the heavier requests) https://www.youtube.com/watch?v=-W9F__D3oY4 @ 18:00
* _hw_: Kemp, Barracuda, F5; run $1-20k bc need to handle GBps of traffic https://news.ycombinator.com/item?id=21095159&utm_term=comment 
* BYO: https://kasvith.github.io/posts/lets-create-a-simple-lb-go/ https://dev.to/bmf_san/implement-a-load-balancer-in-golang-8gj

# DISTRIBUTED

🗄
* `db.md` plumbing
* `infra.md` queues
📚
* Arpaci ch. 48-50
* Galvin dinosaur chapter 17
* Jeffrey distributed
* Kleppmann data intensive
* Takada fun/profit

* _distributed system_: no shared memory, no shared clock https://news.ycombinator.com/item?id=26089683
* needs coordination across network/cores 📙 Jeffrey distributed [4]
* hard https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
> You need whole new categories of instrumentation and logging to getting understanding that isn’t quite as good as what you’d get from the logs of a monolithic application. https://pythonspeed.com/articles/dont-need-kubernetes/
* why: availability, durability, flexibility, locality https://news.ycombinator.com/item?id=29006223
> What happens when that database fails? Are you OK losing some data, or do you want the data to be synchronously replicated off the machine and be available somewhere else after failure? Distribution isn't only about scale, it's also about availability.
> What happens when that database loses some data? Do you want an up-to-the second backup, or point-in-time recovery? Or are you OK restoring last night's backup? Distribution isn't only about scale, it's also about durability.
> What happens when you need to run an expensive business process ad-hoc? Do you want it to be easy to scale out reads, or to export that data to an analytics system? Or are you OK building something else to handle that case? Distribution isn't only about scale, it's also about flexibility.
> What happens when you want to serve customers in one market, and make sure that their data stays local for regulatory compliance reasons or latency? Are you OK with having separate databases? Distribution isn't only about scale, it's also about locality.
* mesh, service weaver https://serviceweaver.dev/blog/quick_intro.html

za
* _Jepsen analysis_: standard safety in distributed/transactional systems https://news.ycombinator.com/item?id=8385970 https://news.ycombinator.com/item?id=26645654 https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html
* _GFS (Google File System)_: https://www.micahlerner.com/2020/03/22/understanding-googles-file-system.html

CAP theorem 🗄 `algos.md` probabilistic data structures
* https://www.youtube.com/watch?v=_RbsFXWRZ10 https://softwareengineeringdaily.com/2023/07/25/cap-theorem/
* _CAP theorem_: tradeoffs if network partition
* _consistency_: ACID
* _availability_: res for req
* _partition tolerance_: works offline 📙 Conery 336
* C: refuse to incoming reads/writes
* A, P: (db remains available but other cluster members becoming inconsistent)
* choose consistency 📙 `evans-linux.pdf` 2

## consensus

📙 Kleppmann ch. 8-9

* _leader election_: Raft algorithm https://www.micahlerner.com/2020/05/08/understanding-raft-consensus.html Paxos https://news.ycombinator.com/item?id=24906225

Raft https://raft.github.io/
* start here https://pyvideo.org/pygotham-2017/an-introduction-to-the-raft-distributed-consensus-algorithm.html https://news.ycombinator.com/item?id=31416812 https://notes.eatonphil.com/distributed-postgres.html https://news.ycombinator.com/item?id=35246228
* BYO https://eli.thegreenplace.net/2020/implementing-raft-part-1-elections/ https://github.com/streed/simpleRaft https://github.com/bbbilibili/raft-1----python https://github.com/erewok/raft-py https://github.com/xwhan/Raft-python
* https://www.micahlerner.com/2020/05/08/understanding-raft-consensus.html https://www.micahlerner.com/2020/05/09/understanding-raft-consensus-part-2.html
* https://www.confluent.io/blog/why-replace-zookeeper-with-kafka-raft-the-log-of-all-logs/

---

* https://lethain.com/distributed-systems-vocabulary/
* _distributed locks_: https://hazelcast.com/blog/long-live-distributed-locks/
* _Lamport timestamp_: https://towardsdatascience.com/understanding-lamport-timestamps-with-pythons-multiprocessing-library-12a6427881c6
* _Lamport clock_: https://martinfowler.com/articles/patterns-of-distributed-systems/lamport-clock.html
* _Byzantine generals problem_: achieve consensus when some actors are unreliable https://en.wikipedia.org/wiki/Byzantine_fault
* _Reed-Solomon_: way to protect messages against damage or partial arrival https://news.ycombinator.com/item?id=27491219
* _conflict resolution_: operational transform (funnel changes through central server, this is what Google Docs uses, a bunch of algorithms have been applied and found to fail; pretty subtle problem) CRDT (maintain each user's data in format that clients can resolve themselves) https://softwareengineeringdaily.com/2017/12/08/decentralized-objects-with-martin-kleppman/ https://www.inkandswitch.com/local-first.html https://github.com/xi-editor/xi-editor/issues/1187#issuecomment-491473599
* _semaphore_: synchronization primative, 类似 mutex/lock https://greenteapress.com/wp/semaphores/ https://danluu.com/programming-books/ https://en.wikipedia.org/wiki/Semaphore_(programming) https://sqlfordevs.com/transaction-locking-prevent-race-condition
* on having more than one primary 📙 Bradshaw [243]
* locks for task, Shedlock https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=202203061
* https://robertovitillo.com/what-every-developer-should-know-about-database-consistency/ https://news.ycombinator.com/item?id=28425379
* _eventual consistency_: when db gets write operation, responds w/ ack and then does write when it gets time, meaning one node could receive write, ack, write it, and then need time to propagate write to other nodes, which means during that time the system would be in a state of inconsistency; benefit is that distributed system means you can put lots of processing power behind your db so the walltime of inconsistent states should be very short; aka 'AP system' 📙 Conery 337-8
> https://www.youtube.com/watch?v=rpqsSkTIdAw
> eventually consistent = eventually corrupt https://www.youtube.com/watch?v=h8cyPIEfxQY 7:45
* https://nchammas.com/writing/database-access-patterns
* _new SQL_: relational semantics + non-relational scaling
* more resistant to CAP theory resistant SQL i.e. seems to shard more finely so that in network partition some very high % of cluster can remain available i.e. trade-off still there just minimized to the point that most users won't notice https://www.prisma.io/blog/comparison-of-database-models-1iz9u29nwn37
* dbms: Cockroach https://www.openmymind.net/Migrating-To-CockroachDB/ Spanner, Rethink https://brandur.org/cloud-databases distributed https://github.com/erikgrinaker/toydb https://github.com/rqlite/rqlite https://github.com/maxpert/marmot

## data

📙 Kleppmann ch. 5-6
🗄
* `db.md` backup, Mongo
* `sql.md` migrations

https://github.com/zknill/sqledge
* cutover
> There's an ongoing sync job as well, so writes that land on the old database are pushed to the new one, so low risk of data loss.

REPLICATION
* _replication_: same data on diff nodes 📙 Kleppmann [199] https://news.ycombinator.com/item?id=37066284
* secondaries only accept writes from primary 📙 Bradshaw [236]
* very slow if synchronous https://lethain.com/distributed-systems-vocabulary/
* _lag_: when secondaries fall behind primary 📙 Bradshaw [235]
* will refuse read requests to avoid serving stale data
* _RAID_: form of replication https://www.kalzumeus.com/2010/04/20/building-highly-reliable-websites-for-small-companies/ https://news.ycombinator.com/item?id=28405695 use ZFS/Zed https://drewdevault.com/2020/04/22/How-to-store-data-forever.html
* backup https://github.com/benbjohnson/litestream https://github.com/maxpert/marmot https://news.ycombinator.com/item?id=30883015 SQLite for edge computing https://news.ycombinator.com/item?id=33081159
* using Redis https://andrewbrookins.com/python/scaling-django-with-postgres-read-replicas/
* Cassandra https://stackoverflow.com/questions/17348558/does-an-update-become-an-implied-insert
* always use write db vs. read replica to avoid creating 2 records
* http://eradman.com/posts/pubsub-pgoutput.html
* https://news.ycombinator.com/item?id=31341392

PARTITION
* _partition_: diff data on diff nodes 📙 Kleppmann 199
* why: horizontal scaling, put more frequently accessed data on better hardware or more geographically proximate 📙 Bradshaw [289]
* aka sharding https://news.ycombinator.com/item?id=28776786 📙 Bradshaw [289] Kleppmann [199]
* avoid by scaling vertically as long as you can 📙 Conery imposter 343 https://news.ycombinator.com/item?id=28430852
* howto https://github.blog/2021-09-27-partitioning-githubs-relational-databases-scale/ 📙 Conery imposter 343
* https://stackoverflow.com/questions/20771435/database-sharding-vs-partitioning https://medium.com/@jeeyoungk/how-sharding-works-b4dec46b3f6 https://news.ycombinator.com/item?id=28425379
* _shard_: node in cluster 📙 Bradshaw [290]

---

* https://news.ycombinator.com/item?id=30767393

blockchain
> Blockchains are special computers that anyone can access but no one owns. https://twitter.com/cdixon/status/1442201642338643969
* https://cdixon.org/2018/02/18/why-decentralization-matters
* ethereum https://github.com/smartcontracts/eth2-book
* networking https://softwareengineeringdaily.com/2021/08/03/hedera-hashgraph-with-leemon-baird/
* sharding https://vitalik.ca/general/2021/04/07/sharding.html
* https://marginalrevolution.com/marginalrevolution/2021/09/roughgarden-on-blockchains.html
> We already store data. In a database. It works well. https://news.ycombinator.com/item?id=22296659
* token https://www.drorpoleg.com/the-crypto-future-of-work/
> Tokens play a vital role in the crypto world. They can serve as “tickets” to access events, as “coupons” to receive goods and services, as “shares” to receive rights to cash flow from a business, and as “votes” that govern an organization or project.
* _blockchain_: db distributed over p2p network w/ each node holding entire db https://danielmiessler.com/study/blockchain/
* _smart contract_: app using blockchain
* _oracle_: data ingestion onto chain
* BYO https://news.ycombinator.com/item?id=27594943 https://norswap.com/blockchain-how/
* use by criminals https://news.ycombinator.com/item?id=27313895
* history: https://danromero.org/crypto-reading/
* design: size of chain makes fraud difficult bc would have tamper with block, then re-write proceeding blocks on all nodes
* why does Patrick McKenzie not like them? https://medium.com/@cdixon/why-decentralization-matters-5e3f79f7638e http://adilmoujahid.com/posts/2018/03/intro-blockchain-bitcoin-python/ https://litepaper.com/ https://a16zcrypto.com/ https://blog.smartdec.net/you-do-not-need-blockchain-eight-popular-use-cases-and-why-they-do-not-work-f2ecc6cc2129 https://www.wired.com/story/how-blockchain-can-wrest-the-internet-from-corporations/ https://www.wired.com/story/theres-no-good-reason-to-trust-blockchain-technology/ https://unwttng.com/what-is-a-blockchain https://hackernoon.com/learn-blockchains-by-building-one-117428612f46 https://medium.com/crypto-currently/lets-build-the-tiniest-blockchain-e70965a248b https://a16z.com/2018/02/10/crypto-readings-resources/ https://www.freecodecamp.org/news/the-authoritative-guide-to-blockchain-development-855ab65b58bc/ https://www.manning.com/books/grokking-bitcoin 

## service discovery

🗄 consensus

---

📍
* https://www.youtube.com/watch?v=S7bsPbJvBzU
* try out Consul locally https://learn.hashicorp.com/tutorials/consul/get-started-install?in=consul/getting-started

* _service discovery_: registry of available services https://www.youtube.com/watch?v=Vv4HpLfqAz4 9:45
* aka configuration store https://github.com/zalando/patroni
* e.g. Zookeeper, etcd, Consul https://stackoverflow.com/a/48652680
* vs. static config of available services https://www.youtube.com/watch?v=Vv4HpLfqAz4 10:00
* like DNS https://www.youtube.com/watch?v=Vv4HpLfqAz4 1:35

ZOOKEEPER https://www.youtube.com/watch?v=Vv4HpLfqAz4
* high level: distributed KV store [8:35]
* impl: tree/hierarchical data model 类似 file system [8:50]
* features: service discovery + leader election https://www.youtube.com/watch?v=AS5a91DOmks 0:45
* used by: Kafka (previously) FoundationDB (itself a distributed KV store) https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html
* _znode_: node in tree [9:20]
* _node_: server in Zookeeper cluster [9:30]

## transactions

🗄 `system.md`
📙
* Bradshaw ch. 8
* Kleppmann ch. 7

📍 rf re: 'dbms taxnomy'

* _serializability_: ordered transactions https://www.micahlerner.com/2021/06/12/foundationdb-a-distributed-unbundled-transactional-key-value-store.html

---

https://sqlfordevs.com/transaction-locking-prevent-race-condition

transactions & isolation levels 📙 Beaulieu 12
* https://retool.com/blog/isolation-levels-and-locking-in-relational-databases/ https://jahfer.com/posts/innodb-locks/ https://www.postgresql.org/docs/9.5/transaction-iso.html
* _transaction_: unit of work https://unixsheikh.com/articles/sqlite-the-only-database-you-will-ever-need-in-most-cases.html https://sqlite.org/transactional.html https://news.ycombinator.com/item?id=33934694
* _commit_: save change; happens in two phases http://dbmsmusings.blogspot.com/2019/01/its-time-to-move-on-from-two-phase.html
* _serializable_: transactions only execute concurrently if end result is same as them executing sequentially
* repeatable read: 
* DDL changes can be transactional as well https://news.ycombinator.com/item?id=28077797

ACID 📙 Kleppmann 7, section 2 🗄 `django.md` design https://lethain.com/distributed-systems-vocabulary/
* https://www.youtube.com/watch?v=yaQ5YMWkxq4
* _atomic_: transaction succeeds/fails as an entire unit https://brandur.org/postgres-atomicity
* NoSQL kinda does http://aosabook.org/en/nosql.html
> Most NoSQL systems pick performance over full ACID guarantees, but do provide guarantees at the key level: two operations on the same key will be serialized, avoiding serious corruption to key-value pairs. For many applications, this decision will not pose noticeable correctness issues, and will allow quick operations to execute with more regularity. It does, however, leave more considerations for application design and correctness in the hands of the developer.
* _consistent_: transaction changes db from one valid state to another 
* eventual consistency 📝 Vogel https://dl.acm.org/doi/10.1145/1435417.1435432
* semantics https://lethain.com/distributed-systems-vocabulary/
* _isolated_: protection from dirty read
* no transaction affects another happening at the same time 📙 Conery 335
* _durable_: successful transaction will survive hardware fault e.g. server restart 📙 Kleppmann 226
* nothing can change transaction except another update 📙 Conery 335
* uses `fsync` http://aosabook.org/en/nosql.html https://sirupsen.com/napkin/problem-10-mysql-transactions-per-second

locking
* _lock_: db disallows other processes to access object (table, row, etc.)
* 'held' by transaction https://jahfer.com/posts/innodb-locks/
* handle at app level by throwing error or retry https://lincolnloop.com/blog/distributed-locking-django/
* _latch_: lightweight lock 📙 Kleppmann 82
* _dirty read_: read uncommitted data
* e.g. transaction 1 updates a row, transaction 2 reads the updated row before transaction 1 commits the update, transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed https://retool.com/blog/whats-an-acid-compliant-database/

# PROGRAMS

📚
* Buelta python architecture
* Dibernardo 500 lines or less http://aosabook.org/en/index.html
* ✅ Evans domain-driven design
* Fowler refactoring
* Martin clean code https://qntm.org/clean
* McConnell code complete
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming

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

## paradigms

📚 exercises in programming style

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

## patterns

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

# ZA

SEMANTICS
* _comment engine_: https://github.com/umputun/remark42 or just use a repo https://lists.sr.ht/~skeeto
* _devops_: align incentives of dev (functionality) and ops (stability); make sysadmin scale
* _files - static_: CSS, JS, fonts https://learndjango.com/tutorials/django-static-files
* _files - media_: uploaded by user https://docs.djangoproject.com/en/3.1/topics/files/#managing-files
* _mirroring_: http://www.postfix.org/mirror.html
* _platform engineering_: devops but w/ the word 'engineering' at the end https://softwareengineeringdaily.com/2020/02/13/setting-the-stage-for-platform-engineering/
* https://sre.google/sre-book/table-of-contents/ definition of production readiness https://www.thoughtworks.com/radar/techniques?blipid=202203026

MONEY
* rightsizing https://softwareengineeringdaily.com/2021/01/12/kubecost-with-webb-brown/
* on-prem: need to integrate w/ legacy systems inside firewall, regulatory, cheaper, you can still make the consumption of your data center feel like a public cloud (CF, HPE)
* _capacity planning_: https://blog.codepen.io/2017/03/21/122-capacity-planning/ https://increment.com/cloud/an-engineers-guide-to-cloud-capacity-planning/

URL shortener 🗄 `fd url-short`
* _URL shortener_: make links look more trustworthy
* providers: Bitly, TinyURL
* https://www.youtube.com/watch?v=rGQKHpjMn_M
* https://blog.codinghorror.com/url-shortening-hashes-in-practice/

## deployment

🗄
* `infra.md` telemetry
* `linux.md` build systems
* `security.md` secrets mgmt
* `sql.md` migrations

APPLICATION CONFIG
* env files: https://snarky.ca/use-toml-for-env-files/

DEPLOYMENT
* _deployment_: align higher env w/ lower env https://css-tricks.com/deployment/
* _staged deployment_: deploy to a few nodes at a time 📙 Kleppmann 4.112
* _blue-green deployment_: split traffic btw new and old; aka red-black https://fly.io/django-beats/smooth-database-changes-in-blue-green-deployments/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_198

RELEASE
* _release_: users get latest deployment
* have a `RELEASE.md` https://news.ycombinator.com/item?id=26902887
* have a runbook https://github.com/Microsoft/vscode/wiki/Development-Process#inside-an-iteration
* _canary release_: only subset of users get latest deployment https://medium.com/netflix-techblog/automated-canary-analysis-at-netflix-with-kayenta-3260bc7acc69 

IMPL https://css-tricks.com/deployment/
* _yolo_: edit on server
* _FTP_: edit on local, push to server
* _SCM_: SSH to sever and pull repo, maybe use cron
* _CICD_: repo hook triggers CICD https://dagger.io/

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

## mobile

* app stores are a pain https://news.ycombinator.com/item?id=33632468
* automate app submission https://github.com/fastlane/fastlane

Apple ID
* tied to user/device
* so if user/device tries to create a new account, use Apple ID to lookup their previous receipt
* i.e. they can't free trial multiple times
* on app start, hit endpoint to verify receipt(s) tied to Apple ID, so user with previous receipt can't just create new account and be given a fresh slate
> Google version of this is that you have a single email for Google Play store, so even if you use diff email(s) per app, purchases on GP still tied to that single email

two apple envs
* prod
* development

each with a URL for
* dummy charges
* real charges
