# ⛩️

## 参考

🗄️ `sql.md` code gen
📚
* Gross hypermedia systems https://www.amazon.com/gp/product/B0C9S88QV6
* Masse api rulebook
* security https://www.manning.com/books/secure-apis https://roadmap.sh/best-practices/api-security

## 进步

* monitoring https://news.ycombinator.com/item?id=42915435
* https://roadmap.sh/api-design https://pycon-archive.python.org/2024/schedule/presentation/25/index.html 🗄️ `src.md` https://conroy.org/writing-api-clients-in-go
* https://roadmap.sh/backend
*️ https://us.pycon.org/2024/schedule/presentation/5/index.html https://www.manning.com/books/secure-apis https://nostarch.com/hacking-apis
* https://news.ycombinator.com/item?id=41432101
* Kleppmann ch. 3
* styles https://www.youtube.com/watch?v=4vLxWqE94l4
* gateway https://www.youtube.com/watch?v=6ULyxuHKxg8
* protocols https://www.youtube.com/watch?v=zY2DMpCUfCg

* just give folks everything and let them drill down vs. trying to predetermine what they need https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 38:00
* if API truly agnostic from frontend each page will end up making a bunch of calls instead of one call per page https://macwright.com/2020/05/10/spa-fatigue.html
* _streaming_: server pushes to client https://2.python-requests.org/en/master/user/advanced/#streaming-requests
* _idempotent_: same req n times = no additional side effects after first req e.g. after initial req creates record, further requests won't create dupe https://stripe.com/blog/idempotency
* provide map of endpoints https://brandur.org/accessible-apis#programmatic-maps
* limit the number of req to get actionable info on resource https://www.dataengineeringpodcast.com/linode-object-storage-service-episode-125/ 25:00 JSON over REST and even higher level than that https://josephg.com/blog/api-for-changes/ https://josephg.com/blog/databases-have-failed-the-web/ https://josephg.com/blog/composing-databases/

DONE
* _19_: BNY take over testrunner
* _17_: JP the glory of PHP

# 🏮 DESIGN

📙 Laurent https://www.manning.com/books/the-design-of-web-apis-second-edition

* KISS: if data is static, use web server like Nginx, don't even need a backend https://blog.pecar.me/faster-api
* _Hyrums Law_: https://news.ycombinator.com/item?id=42201892

---

> In some sense, deprecated methods and parameters are relatively easy because it's relatively clear to see what's happened. It's when it's subtle changes in behavior.  Like, do you apply an integer constraint before or after a function that wraps the integer validation?...you decide to change it because you're like this is marginally more correct? https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python

## GraphQL

---

https://danluu.com/simple-architectures/
> Pros:
> Self-documentation of exact return type
> Code generation of exact return type leads to safer clients
> GraphiQL interactive explorer is a productivity win
> Our various apps (user app, support app, Wave agent app, etc.) can mostly share one API, reducing complexity
> Composable query language allows clients to fetch exactly the data they need in a single packet roundtrip without needing to build a large number of special-purpose endpoints
> Eliminates bikeshedding over what counts as a RESTful API
> Cons:
> GraphQL libraries weren’t great when we adopted GraphQL (the base Python library was a port of the Javascript one so not Pythonic, Graphene required a lot of boilerplate, and Apollo-Android produced very poorly optimized code)
> Default GQL encoding is redundant and we care a lot about limiting size because many of our customers have low bandwidth

https://softwareengineeringdaily.com/2024/10/16/the-end-of-graphql-matt-bessey/
📹 https://www.youtube.com/watch?v=QJhiMSUFgDM
* https://roadmap.sh/graphql
* https://www.youtube.com/watch?v=yWzKJPw_VzM
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

## REST

* hypermedia is REST https://htmx.org/essays/
* _REST_: architectural style, not protocol [Kleppmann 4.133] nowadays means JSON over HTTP i.e. there are few to-the-letter RESTful APIs https://news.ycombinator.com/item?id=15939552 backend supports n clients (web, mobile) https://wsvincent.com/rest-a-definition/ https://codewords.recurse.com/issues/five/what-restful-actually-means https://www.youtube.com/watch?v=pZYRC8IbCwk
* definition https://news.ycombinator.com/item?id=32141027
* _Fielding paper_: not specific to HTTP; guided tour; no reference implementation http://mickadoo.github.io/rest/2016/09/26/what-is-rest.html https://codewords.recurse.com/issues/five/what-restful-actually-means https://stackoverflow.com/a/983458/6813490 https://twobithistory.org/2020/06/28/rest.html https://news.ycombinator.com/item?id=24384048
* _HATEOAS_: navigate API via links btw endpoints https://htmx.org/docs/#introduction https://stackoverflow.com/questions/2239405/hateoas-absolute-or-relative-urls https://stackoverflow.com/questions/1139095/actual-examples-for-hateoas-rest-architecture https://www.django-rest-framework.org/topics/rest-hypermedia-hateoas/ https://htmx.org/essays/hateoas/
> RESTful API design consequently suffers the same problems as Active Record ORMs. The problem is most severe when fundamentalist RESTafarians get involved, as they advocate using hypertext-style links between API endpoints - HATEOAS ("Hypermedia As The Engine Of Application State"). Under HATEOAS, applications "browse" the API, moving from link to link to accomplish their goal. https://calpaterson.com/activerecord.html

## RPC

🗄️ `protocols.md` protobuf

---

* https://danluu.com/butler-lampson-1999/
* used more for internal services 📙 Jeffrey distributed [5]
* BYO https://github.com/travisjeffery/proglog
* https://stackoverflow.blog/2022/11/28/when-to-use-grpc-vs-graphql/
* https://www.youtube.com/watch?v=gnchfOojMk4
* https://www.youtube.com/watch?v=_4TPM6clQjM
* https://kmcd.dev/posts/grpc-the-good-parts/
* akin to intra-process communcation (more tightly coupled)
* apparently a bad idea 📙 Kleppmann [4.134]
* only used inside your own data center 📙 Kleppmann [4.136]
* argument for is no bikeshedding on HTTP semantics https://news.ycombinator.com/item?id=9597030
* https://etherealbits.com/2012/12/debunking-the-myths-of-rpc-rest/ https://www.smashingmagazine.com/2016/09/understanding-rest-and-rpc-for-http-apis/ https://apihandyman.io/do-you-really-know-why-you-prefer-rest-over-rpc/ https://stackoverflow.com/questions/15056878/rest-vs-json-rpc https://stackoverflow.com/a/26831221 https://github.com/fullstorydev/grpcurl https://realpython.com/python-microservices-grpc/ https://github.com/tomerfiliba-org/rpyc

SOAP
* tangled set of protocols
* API schema described using language called WSDL 📙 Kleppmann [4.133]
* tighter coupling btw client/server http://keithba.net/simplicity-and-utility-or-why-soap-lost
* typically uses XML 📙 Kleppmann [4.132]

# 📰 SCHEMA

🗄️ `sql.md` migrations

---

https://news.ycombinator.com/item?id=41939027

* _schema_: typing 📙 Kleppmann [4.122-128]
* _spec_: doc explaining schema https://www.youtube.com/watch?v=1lo7idI7uq8
* generate spec from API and vice versa https://www.youtube.com/watch?v=1lo7idI7uq8 3:00

## contract testing

📙 https://www.manning.com/books/contract-testing-in-action

> APIs are just the most common use case since they're explicit interfaces between separate systems.  The core idea is: "Component A and Component B have an agreement (contract) about how they'll interact. Let's verify both sides honor that agreement." The Pact library popularized contract testing for APIs, which is probably why there's that association. But the concept generalizes to any interface where you can formalize the expectations between producer and consumer.
* Pact https://www.thoughtworks.com/radar/tools?blipid=202110074
* https://colorsofcode.ghost.io/counting-sheeps-with-contracts-in-python/
* Jepsen https://news.ycombinator.com/item?id=38525968
* https://tratt.net/laurie/blog/2024/what_factors_explain_the_nature_of_software.html

## JSON:API

📜  https://jsonapi.org

---

> was there ever adoption of this? also, Klabnik/Katz involved? https://news.ycombinator.com/item?id=5653706 the name grab makes it hard to tell 🧠 https://chatgpt.com/c/673ca597-ed10-8004-83a3-0dc3251aad7b

* req/res data fmt + more precise HTTP semantics https://changelog.com/podcast/189 46:30
* helps client not make unnecessary requests https://news.ycombinator.com/item?id=5654390
* the name is an annoying land grab https://news.ycombinator.com/item?id=5654375 
* other projects that aim for the same thing https://news.ycombinator.com/item?id=5653976
* ❓ diverges from OpenAPI https://phil.tech/api/2018/03/30/openapi-and-json-schema-divergence/
* _alternatives_: HAL https://jsonapi.org/faq/

## JSON Schema

📜 https://json-schema.org/

CONTINUE HERE
https://json-schema.org/learn/getting-started-step-by-step
https://github.com/python-jsonschema/jsonschema
https://github.com/python-jsonschema/check-jsonschema

* _instance_: JSON doc being validated
* _schema_: doc containing description
```json
// INSTANCE
{
  "productId": 1,
  "productName": "A green door",
  "price": 12.50,
  "tags": [ "home", "green" ]
}
// SCHEMA
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",  // version of JSON Schema
  "$id": "https://example.com/product.schema.json",  // why would you need a URL 
  "title": "Product",
  "description": "A product in the catalog",
  "type": "object"
}

```

---

TOOLS https://json-schema.org/tools
* _fastjsonschema_: https://github.com/horejsek/python-fastjsonschema https://horejsek.github.io/python-fastjsonschema/
* _jschon_: https://github.com/marksparkza/jschon

USAGE
* validation in dbms https://github.com/supabase/pg_jsonschema
```sql
ALTER TABLE products ADD CONSTRAINT data_is_valid CHECK(
  validate_json_schema('{
    "type": "object", "properties": {
       "tags": {
          "type": "array", "items": { "type": "string" }
       }
    }
  }',  attributes)
);
INSERT INTO products (attributes) VALUES ('{}');  -- ok
INSERT INTO products (attributes) VALUES ('{ "tags":[] }');  -- ok
INSERT INTO products (attributes) VALUES ('{ "tags":["test"] }');  -- ok
INSERT INTO products (attributes) VALUES ('{ "tags":[2] }'); -- ERROR: new row for relation "products" violates check constraint "data_is_valid". Failing row contains ({"tags": [2]}).
```


---

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

## OPEN API

---

* https://www.stedi.com/docs/api-reference/index https://github.com/Stedi/openApi/blob/main/core.json
* code gen https://github.com/ogen-go/ogen
* https://github.com/marshmallow-code/apispec
* https://github.com/zaghaghi/openapi-tui
* code generation https://github.com/oapi-codegen/oapi-codegen
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

API STAR 📜 https://docs.apistar.com/ https://github.com/zachvalenta/flask-openapi
* build docs for OpenAPI service
* _history_: began as a project to bring DRF browsable dev docs to Flask https://github.com/flask-api/flask-api/commit/b99c8d26e335cef696b931dde783ca80ca4ab798 then became a framework https://pythonbytes.fm/episodes/show/21/python-has-a-new-star-framework-for-restful-apis and now is a toolkit to add OpenAPI stuff to any framework
* `apistar validate`: lint schema
* `apistar request`: can't get this working
* `apistar.yml`: path to schema, whether Swagger or OpenAPI
* ❓ able to build static or have to run server?
* ❓ run alongside prod?
* ❓ no hot reload https://github.com/encode/apistar/issues/637 from when it was a framework? https://github.com/encode/apistar/issues/40 https://github.com/encode/apistar/pull/57

# 🟨 ZA

* reverse engineering https://apiparrot.com/?utm_source=hackernewsletter https://news.ycombinator.com/item?id=41983409 https://news.ycombinator.com/item?id=42057903 https://news.ycombinator.com/item?id=42565821

## pagination

* _paginate_: return subset of records
* why: server (reduced load) client (more granular query)
* howto: req `api/widgets?page=42` res can return header `x-total-count=<num>` https://slack.engineering/evolving-api-pagination-at-slack-1c1f644f8e12 https://www.reverb-api.com/docs#section-pagination

## public

🗄️ `stat.md` datasets

https://github.com/public-apis/public-apis
https://rapidapi.com/hub
planes https://github.com/mrjackwills/adsbdb

## rate limiting

🗄️ `http.md` rate limiting

---

APPROACHES
* token bucket
* leaky bucket
* fixed window
* sliding window

```python
def should_retry(headers):
    """
    return true if we should wait before retrying based on rate limit headers
    >>> headers = {
    ...     'x-ratelimit-remaining': '0',
    ...     'x-ratelimit-reset': str(int(datetime.now().timestamp()) + 30)
    ... }
    >>> should_retry(headers)
    True
    """
    remaining = int(headers['x-ratelimit-remaining'])
    return remaining == 0
```

💻 scaffold client to provide backoff/retry/jitter https://github.com/zachvalenta/shishi
```txt
Jitter helps prevent "thundering herd" problems where many clients retry at exactly the same time
We only apply jitter to the exponential backoff case, not to explicit Retry-After timing
The jitter factor determines how much randomization - here ±20%
Using uniform distribution but you could also use truncated normal for different retry patterns
Want me to show you how this behaves with matplotlib to visualize the retry timing patterns?
```

* https://github.com/jsocol/django-ratelimit
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

## slugs

🗄️ `application.md` URLs

---

URL obfuscation https://chatgpt.com/c/6749cb63-5a28-8004-8ffa-cc1a50c7b8da

REPRESENTING INDIVIDUAL RESOURCES IN URL
https://news.ycombinator.com/item?id=41243992&utm_term=comment
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

## versioning

---

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

* _sink_: https://www.youtube.com/watch?v=dqDnB6jKzcE https://www.moesif.com/blog/technical/api-design/Best-Practices-for-Versioning-REST-and-GraphQL-APIs/ https://stackoverflow.com/questions/55877310/add-x-frame-options-header-to-all-flask-responses https://flask.palletsprojects.com/en/1.1.x/api/#flask.Flask.after_request https://pythonise.com/series/learning-flask/python-before-after-request https://stripe.com/blog/api-versioning https://news.ycombinator.com/item?id=21834628 https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api https://brandur.org/api-upgrades
