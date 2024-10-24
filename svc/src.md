# ⛩️

## 参考

🔍 https://softwareengineering.stackexchange.com
📚
* Buelta python architecture
* Dibernardo 500 lines or less http://aosabook.org/en/index.html
* ✅ Evans domain-driven design
* Fowler refactoring https://www.amazon.com/dp/0134757599/ https://registerspill.thorstenball.com/p/skin-shedding-code
* Martin clean code https://qntm.org/clean
* McConnell code complete
* Raymond unix programming https://www.arp242.net/the-art-of-unix-programming

## 进步

* _23_: 📙 Evans domain-driven
* _19_: URL shortener, Gitlab for CI

# 🛰️ API

🛣️ https://roadmap.sh/best-practices/api-security
🗄️ `databases.md` tooling / code generation
📙 Masse api rulebook
🔍 https://github.com/public-apis/public-apis https://rapidapi.com/hub

---

📚
* Kleppmann ch. 3
* Masse api rulebook
* https://roadmap.sh/api-design https://roadmap.sh/backend
* https://news.ycombinator.com/item?id=41432101

* styles https://www.youtube.com/watch?v=4vLxWqE94l4
* gateway https://www.youtube.com/watch?v=6ULyxuHKxg8
* protocols https://www.youtube.com/watch?v=zY2DMpCUfCg

ZA
* just give folks everything and let them drill down vs. trying to predetermine what they need https://simonwillison.net/2020/Nov/14/personal-data-warehouses/ 38:00
* if API truly agnostic from frontend each page will end up making a bunch of calls instead of one call per page https://macwright.com/2020/05/10/spa-fatigue.html
* standards at national level https://increment.com/apis/introduction-apis-egovernment/
* _streaming_: server pushes to client https://2.python-requests.org/en/master/user/advanced/#streaming-requests
* _idempotent_: same req n times = no additional side effects after first req e.g. after initial req creates record, further requests won't create dupe https://stripe.com/blog/idempotency
* provide map of endpoints https://brandur.org/accessible-apis#programmatic-maps
* limit the number of req to get actionable info on resource https://www.dataengineeringpodcast.com/linode-object-storage-service-episode-125/ 25:00 JSON over REST and even higher level than that https://josephg.com/blog/api-for-changes/ https://josephg.com/blog/databases-have-failed-the-web/ https://josephg.com/blog/composing-databases/

## approaches

* KISS: if data is static, use web server like Nginx, don't even need a backend https://blog.pecar.me/faster-api

### GraphQL

---

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

### JSON:API

📜  https://jsonapi.org

---

* req/res data fmt + more precise HTTP semantics https://changelog.com/podcast/189 46:30
* helps client not make unnecessary requests https://news.ycombinator.com/item?id=5654390
* the name is an annoying land grab https://news.ycombinator.com/item?id=5654375 
* other projects that aim for the same thing https://news.ycombinator.com/item?id=5653976
* ❓ diverges from OpenAPI https://phil.tech/api/2018/03/30/openapi-and-json-schema-divergence/
* _alternatives_: HAL https://jsonapi.org/faq/

### REST

* hypermedia is REST https://htmx.org/essays/
* _REST_: architectural style, not protocol [Kleppmann 4.133] nowadays means JSON over HTTP i.e. there are few to-the-letter RESTful APIs https://news.ycombinator.com/item?id=15939552 backend supports n clients (web, mobile) https://wsvincent.com/rest-a-definition/ https://codewords.recurse.com/issues/five/what-restful-actually-means https://www.youtube.com/watch?v=pZYRC8IbCwk
* definition https://news.ycombinator.com/item?id=32141027
* _Fielding paper_: not specific to HTTP; guided tour; no reference implementation http://mickadoo.github.io/rest/2016/09/26/what-is-rest.html https://codewords.recurse.com/issues/five/what-restful-actually-means https://stackoverflow.com/a/983458/6813490 https://twobithistory.org/2020/06/28/rest.html https://news.ycombinator.com/item?id=24384048
* _HATEOAS_: navigate API via links btw endpoints https://htmx.org/docs/#introduction https://stackoverflow.com/questions/2239405/hateoas-absolute-or-relative-urls https://stackoverflow.com/questions/1139095/actual-examples-for-hateoas-rest-architecture https://www.django-rest-framework.org/topics/rest-hypermedia-hateoas/ https://htmx.org/essays/hateoas/
> RESTful API design consequently suffers the same problems as Active Record ORMs. The problem is most severe when fundamentalist RESTafarians get involved, as they advocate using hypertext-style links between API endpoints - HATEOAS ("Hypermedia As The Engine Of Application State"). Under HATEOAS, applications "browse" the API, moving from link to link to accomplish their goal. https://calpaterson.com/activerecord.html

### RPC

---

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

## pagination

* _paginate_: return subset of records
* why: server (reduced load) client (more granular query)
* howto: req `api/widgets?page=42` res can return header `x-total-count=<num>` https://slack.engineering/evolving-api-pagination-at-slack-1c1f644f8e12 https://www.reverb-api.com/docs#section-pagination

## rate limiting

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

## schema

---

https://news.ycombinator.com/item?id=41939027

* _schema_: typing 📙 Kleppmann [4.122-128]
* _spec_: doc explaining schema https://www.youtube.com/watch?v=1lo7idI7uq8
* generate spec from API and vice versa https://www.youtube.com/watch?v=1lo7idI7uq8 3:00

### JSON Schema

📜 https://json-schema.org/

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

### OPEN API

---

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

## slugs

---

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

* _sink_: https://www.youtube.com/watch?v=dqDnB6jKzcE https://www.moesif.com/blog/technical/api-design/Best-Practices-for-Versioning-REST-and-GraphQL-APIs/ https://stackoverflow.com/questions/55877310/add-x-frame-options-header-to-all-flask-responses https://flask.palletsprojects.com/en/1.1.x/api/#flask.Flask.after_request https://pythonise.com/series/learning-flask/python-before-after-request https://stripe.com/blog/api-versioning https://news.ycombinator.com/item?id=21834628 https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api https://brandur.org/api-upgrades security https://nostarch.com/hacking-apis

# 🏗️ DEPLOYMENT

---

🗄
* `infra.md` config mgmt
* `linux.md` build systems
* `security.md` secrets mgmt
* `sql.md` migrations

https://blog.pecar.me/rds-blue-green
https://blog.pecar.me/gunicorn-restart
https://github.com/piku/piku

SEMANTICS
* _release_: users get latest deployment
* _canary release_: only subset of users get latest deployment https://medium.com/netflix-techblog/automated-canary-analysis-at-netflix-with-kayenta-3260bc7acc69 

## CICD

OPTIONS
* _Dagger_: created by the guy who created Docker, used Cuelang https://github.com/dagger/dagger https://news.ycombinator.com/item?id=30857012
* _Github Actions_: 🗄️ `git.md` Github / Actions

---

https://github.com/zillow/tycho

* validate configs https://github.com/kehoecj/validate-configs-action
* taxonomy: yolo (edit on server) FTP (edit on local, push to server) SCM (SSH to sever and pull repo, maybe use cron) CICD (triggered by repo hook https://dagger.io/) https://css-tricks.com/deployment/
* pipelines: fetch (clone from repo) build (install deps, compile) test (run unit tests) deploy (put artifact somewhere so CD can pick it up and run it)
* Jenkins https://itnext.io/jenkins-is-getting-old-2c98b3422f79 https://www.youtube.com/watch?v=WWcijE7ifcA
* BYO http://aosabook.org/en/500L/a-continuous-integration-system.html
* _deployment_: align higher env w/ lower env https://css-tricks.com/deployment/
* _staged deployment_: deploy to a few nodes at a time 📙 Kleppmann 4.112
* _blue-green deployment_: split traffic btw new and old; aka red-black https://fly.io/django-beats/smooth-database-changes-in-blue-green-deployments/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_198 https://news.ycombinator.com/item?id=39048317

https://gitlab.com/zachvalenta/pre-commit-test.git https://docs.gitlab.com/ee/ci/yaml/ https://docs.gitlab.com/ https://docs.gitlab.com/runner/
* _job_: declarative series of steps
* _stage_: grouping mechanism for jobs e.g. test, deploy
* _pipeline_: collection of stages; can force manual interaction https://docs.gitlab.com/ee/ci/pipelines/index.html#add-manual-interaction-to-your-pipeline to run without, toggle off in project (visibility and merge requests)
* conditionals https://docs.gitlab.com/ee/ci/yaml/#rulesif
* _artifact_: static files produced by pipeline e.g. coverage report from tests
* generate report: `pytest --junitxml=report.xml` https://docs.gitlab.com/ee/ci/unit_test_reports.html#python-example
```yaml
# basic
unit_tests:
  image: python:3.7
  script:
    - "pip install -r requirements.txt"
    - "ln -sf .env.dev .env"
    - "pytest -v app_test.py"

# ref env var set via GL instance
ax2: "${ax2}"
```

HOOKS 📜 https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks https://githooks.com/
* BYO https://stefaniemolin.com/articles/devx/pre-commit/hook-creation-guide/
* https://rdrn.me/postmodern-python/
* actions: client-side (commit, merge) server (push)
* file-system location: `.git/hooks` 
* ignore failed hooks w/ `git commit --no-verify` http://omerkatz.com/blog/2013/2/15/git-hooks-part-1-the-basics

PRE-COMMIT https://pre-commit.com https://github.com/pre-commit/pre-commit/issues https://gitlab.com/zachvalenta/pre-commit-test https://learndjango.com/tutorials/pre-commit-django
* set: `pre-commit install -t pre-commit; pre-commit install -t pre-push` (i.e. copy Python scripts in place of Git samples) https://pre-commit.com/#3-install-the-git-hook-scripts https://pre-commit.com/#pre-commit-install
* skip: `SKIP=<stage> git commit -m "foo"`
* uninstall: `pre-commit uninstall -t <action>`
* conf: `.pre-commit-config.yaml`
* run in parallel, can cause random failures, run in serial using `require_serial = true` https://pre-commit.com/#hooks-require_serial
* official hooks: black handles `trailing-whitespace` and `end-of-file-fixer` https://github.com/pre-commit/pre-commit-hooks/tree/master/pre_commit_hooks https://www.youtube.com/watch?v=BzC3ft8rm4c
* pylint is a pain https://github.com/pre-commit/pre-commit/issues/266#issuecomment-399682269 black https://github.com/pre-commit/pre-commit-hooks/issues/356 https://github.com/psf/black#version-control-integration pytest 

```yaml
---
- repo: local  #  https://pre-commit.com/#repository-local-hooks https://github.com/pre-commit/pre-commit/issues/1245
  hooks:
  - id: lint
    stages: [commit]
    name: run lint
    entry: make lint
    language: system
    types: [python]
  - id: test
    stages: [push]
    name: run test
    entry: make test
    language: system
    types: [python]
```

## denv

🗄 `linux.md` denv

CLOUD
* https://www.lastweekinaws.com/blog/the-real-reason-cloud-ide-adoption-is-lagging/
* switching locally: macOS spaces https://github.com/dandavison/wormhole
* _Coder_: https://github.com/coder/coder
* _Daytona_: https://www.daytona.io/
* _Github codespaces_: https://github.com/features/codespaces https://www.thoughtworks.com/radar/tools?blipid=202203053 https://cli.github.com/manual/gh_codespace
* _Gitpod_: https://www.gitpod.io/ https://www.youtube.com/watch?v=XcjqapXfrhk https://www.youtube.com/watch?v=llRLh8cM7QI 27:15
* _Zed_: https://zed.dev/releases/stable/0.145.1 https://www.youtube.com/watch?v=F9sQPpVVLeQ

---

* db: not a silver bullet (Postgres in your Docker container will have some differences to db server you're connecting to in prod)

## feature flag

---

https://news.ycombinator.com/item?id=41941493

🗄 `infra.md` analytics

* _feature flag_: toggle functionality; impl agnostic (env var, db, aaS) https://medium.com/@noahrobi/feature-toggles-give-you-superpowers-78fdeb7ab5e8
* use cases: decouple deployment/release, canary release https://github.com/facebook/planout A/B testing https://findwork.dev/blog/django-b-testing-google-optimize https://www.evanmiller.org/
* as tech debt https://www.youtube.com/watch?v=HhxNaPYpYiU https://github.blog/2021-04-27-ship-code-faster-safer-feature-flags/
* feature-flag-driven development
> Always start a feature with a feature flag and try to get something to production on day 1. even if it's only feature flagged to you. usual feature flag timeline: week 1 - developer and people interested in a feature week 3 - release or do beta with users
```python
class FeatureFlag(models.Model):
    name = models.CharField(max_length=80)
    enabled = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

TOOLING
* _flagsmith_: https://bullet-train.io/
* _flipt_: https://github.com/markphelps/flipt https://github.com/flipt-io/flipt
* _Launch Darkly_:
* _Optimizely_:
* _split_: https://www.split.io/
* _unleash_: https://github.com/Unleash/unleash
* _waffle_: https://waffle.readthedocs.io/en/stable/

## secrets

🗄
* `security.md` users/ passwords
* `shell.md` env var

OPTIONS
> https://news.ycombinator.com/item?id=40789353
* _BitWarden_: has their own vault?
* _dotenv_:
* _dotenvx_: https://dotenvx.com/blog/2024/06/24/dotenvx-next-generation-config-management.html
* _KMS_: AWS service for storing encryption keys https://www.youtube.com/watch?v=eIvbUU8VH30
* _sops_: https://github.com/mozilla/sops https://www.youtube.com/watch?v=AAUJjwdCx4I
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

https://archive.vn/zyWMC
* https://www.youtube.com/watch?v=G6Qbnitlwjk
> what's the python stdlib for this?
* env files: https://snarky.ca/use-toml-for-env-files/

https://github.com/brittonhayes/pillager
* _secret_: sensitive auth creds (db user/pass, AWS IAM roles) https://testdriven.io/blog/managing-secrets-with-vault-and-consul/#what-is-vault
* anything you can't version control
* don't use env var?! https://news.ycombinator.com/item?id=34055914
* scan Github https://github.com/eth0izzle/shhgit https://github.com/kootenpv/gittyleaks https://github.com/zricethezav/gitleaks
* _secrets mgmt_: instead of passing around over email, use a tool for SSoT / audit trail / encryption https://testdriven.io/blog/managing-secrets-with-vault-and-consul/#what-is-vault
* https://news.ycombinator.com/item?id=34083366

https://github.com/Infisical/infisical
* https://github.com/tellerops/teller
> Teller is an open-source universal secret manager for developers that ensures the correct environment variables are set when starting an application. However, it's not a vault itself — it's a CLI tool that connects to a variety of sources, ranging from cloud secrets providers to third-party solutions like HashiCorp Vault to local environment files. Teller has additional functionality to scan for vault-kept secrets in your code, to redact secrets from logs, to detect drift between secrets providers and to sync between them. Given the sensitivity of accessing secrets, we can't emphasize enough the need to secure the supply chain for open-source dependencies, but we appreciate how easy the CLI is to use in local development environments, CI/CD pipelines and deployment automation.

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

config in general
* _config_: everything that varies between deployment envs https://12factor.net/config 
* not to be confused with 'configuration mgmt' i.e. setting up consistent infra, although sometimes terms are mixed https://rednafi.github.io/digressions/python/2020/06/03/python-configs.html 🗄 `infra.md` Ansible
* can always just push your dev env to the cloud https://softwareengineeringdaily.com/2020/10/14/gitpod-cloud-development-environments-with-johannes-landgraf-and-sven-efftinge/
* _config class_: https://lincolnloop.com/blog/goodconf-python-configuration-library https://testdriven.io/blog/dynamic-secret-generation-with-vault-and-flask/ https://rednafi.github.io/digressions/python/2020/06/03/python-configs.html https://whalesalad.com/blog/doing-python-configuration-right [Grinberg chapter 7]
* _FTP on steroids_: spin up entire environment remotely then file watch/sync to mv local changes to remote https://slack.engineering/development-environments-at-slack/
* https://www.youtube.com/watch?v=omhJrT90lXU&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=39
* CLI https://smallstep.com/blog/command-line-secrets/
* store enums w/ versions https://martinfowler.com/articles/patterns-of-distributed-systems/versioned-value.html

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

# 🟨 ZA

---

SEMANTICS
* _code path_: branch through codebase
* _cohesion_: put like with like 📙 Conery [270] Evans [109] https://entropicthoughts.com/event-sourcing-and-microservices-unix-style
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

## checklist

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
* https://pocketbase.io/
* BYO Saas https://www.datasette.cloud/blog/2023/welcome/

* _files - static_: CSS, JS, fonts https://learndjango.com/tutorials/django-static-files
* _files - media_: uploaded by user https://docs.djangoproject.com/en/3.1/topics/files/#managing-files

## dependency injection (DI)

* https://github.com/uber-go/fx
* https://www.youtube.com/watch?v=uWTvMCra-_Y
* https://www.youtube.com/watch?v=0yc2UANSDiw
* _dependency injection_: passing args [Conery 282]
* why?: loose coupling http://kc.my-junk.info/di-ioc-dip https://www.youtube.com/watch?v=sD94szvFqGw
* https://blog.thea.codes/my-python-testing-style-guide/
* https://testdriven.io/blog/python-dependency-injection
* https://github.com/ZechCodes/Bevy
* https://hakibenita.com/python-dependency-injection
* https://romantomjak.com/posts/testing-python-code-that-makes-http-requests.html
* https://docs.pytest.org/en/latest/fixture.html#fixture
* in Python https://io.made.com/dependency-injection-with-type-signatures-in-python/ + https://moltenframework.com/v0.7.3/index.html + https://github.com/ekiro/haps + https://github.com/Dobiasd/enterprython/blob/master/why_you_want_formal_dependency_injection_in_python_too.md https://pythonbytes.fm/episodes/show/112/don-t-use-the-greater-than-sign-in-programming
* _inversion of control(IoC)_: you're not in charge of app control flow, only hooking into it https://www.baeldung.com/running-setup-logic-on-startup-in-spring example of IoC https://seddonym.me/2019/08/03/ioc-techniques/ https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way https://stackoverflow.com/questions/3058/what-is-inversion-of-control https://engineering.snagajob.com/dont-like-dependency-injection-898de93dc8d3 https://stackoverflow.com/a/2465052/6813490 https://stackoverflow.com/a/51117857/6813490 https://stackoverflow.com/a/140655/6813490 https://www.objc.io/issues/11-android/dependency-injection-in-java/ https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ ❓ pull in class deps all in one place [Conery 287]
> What is the glue that holds Django together? As a beginner entering, there really is no obvious central object to inspect, extend, or modify. https://www.reddit.com/r/Python/comments/olech/is_django_considered_pythonic_now/

## 🍥 design patterns

🔍
* https://github.com/DovAmir/awesome-design-patterns
* https://softwareengineering.stackexchange.com/questions/tagged/design-patterns
📙 Conery ch. 11,12

* Gang of Four: composition over inheritance https://en.wikipedia.org/wiki/Design_Patterns https://buttondown.com/hillelwayne/archive/when-to-prefer-inheritance-to-composition/
> They warn that the implementation of a subclass can become so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change. Furthermore, they claim that a way to avoid this is to inherit only from abstract classes—but then, they point out that there is minimal code reuse.
> Using inheritance is recommended mainly when adding to the functionality of existing components, reusing most of the old code and adding relatively small amounts of new code.

---

https://github.com/DovAmir/awesome-design-patterns
* fanout https://www.better-simple.com/django/2023/12/06/fanout-pattern-explained/
* the big ball of mud https://news.ycombinator.com/item?id=35481309
* _strangler fig_: you run the old code and new code live, in production, side-by-side, checking that the new code behaves exactly the same as the old code. Once you are confident it does, you retire the old code https://www.kosli.com/blog/how-to-strangle-old-code-using-python-decorators/ https://news.ycombinator.com/item?id=41423421

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

* entity component https://akkartik.name/post/programming-2024
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
* _template method_: https://startcodingnow.com/template-method-design-pattern
* _visitor_: https://martinheinz.dev/blog/90

---

* _observer_: pub sub https://layerci.com/blog/postgres-is-the-answer http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/
* _sink_: https://github.com/kamranahmedse/design-patterns-for-humans https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745
* in python https://python-patterns.guide/ https://hynek.me/articles/python-subclassing-redux/


## internationalization (i18n)

* https://phrase.com/blog/posts/internationalization-i18n-go/
* examples: Odoo, https://github.com/jesseduffield/lazygit/tree/master/pkg/i18n
* https://chatgpt.com/c/6717c3a0-0424-8004-9feb-90d6451666d7
* _a11y_: accessibility https://en.wikipedia.org/wiki/Computer_accessibility
* _l10n_: language localization https://en.wikipedia.org/wiki/Language_localisation
* _Lokalise_: used at UM https://lokalise.com/automate-localization

## 🎭 paradigms

📚 Lopes exercises in programming style

* use greppable names https://registerspill.thorstenball.com/p/use-data-that-looks-like-data
* write code that's easy to throw away
> Write code to be changed and/or deleted. This comes from someone who's worked in startups for the past 5 years. We often overestimate how long code =is supposed to live. We as programmers often exaggerate with our DRY and stuff, we do not want to repeat ourselves, we want to find another abstraction...we want to find some general that can help us abstract stuff away. My piece of advice is that, step back and consider for a moment that this code is not going to stay in, so maybe only try and find the abstraction layer once you really sure that this is how it's going to be. - Thorsten Ball https://developeronfire.com/podcast/episode-373-thorsten-ball-interpreters-compilers-and-writing

---

https://drewdevault.com/2019/04/29/Shut-up-and-get-back-to-work-style.html

* hoisting

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

## perf

---

https://roadmap.sh/best-practices/backend-performance

> The notes on benchmark performance graphs often read "higher is better" and performance improvements are even called "optimisations". But the truth is, at least as a user, once performance reaches a satisfactory level - enough for your own data analysis to complete in a reasonable about of time - there is no further benefit from increased speed. Instead of being called "performance optimisation" it should probably be called "performance satisfaction" as once it is satisfactory you have finished. Usability is different. The whole point of computers is as an aid to productivity so user-friendliness is actually the bit you want to optimise. Unlike speed, being easier to use is always better and there is very little limit to that. So it's "usability improvements" that should be called "optimisations" but perhaps the relevant ships on all of these terms have sailed. https://csvbase.com/blog/6
