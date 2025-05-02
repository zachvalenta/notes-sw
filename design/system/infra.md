# ⛩️

## 参考

🔍 https://softwarerecs.stackexchange.com

## 进步

WORKFLOW ENGINE OR TASK QUEUE?
* https://news.ycombinator.com/item?id=34163888
* https://www.reddit.com/r/golang/comments/1as23yb/when_to_use_a_workflow_tool_temporal_vs_a_job/
* https://www.inngest.com/blog/how-durable-workflow-engines-work
* https://www.reddit.com/r/golang/comments/xa25ed/workflow_engine_vs_task_queue/
* https://www.youtube.com/watch?v=x4k1XEjNzYQ
* https://www.youtube.com/watch?v=x4k1XEjNzYQ

* _20_: gunicorn, uWSGI
* _19_: Gitlab for CI https://github.com/zachvalenta/nginx-wsgi

# 💾 CACHES

🗄
* `distributed.md` caching
* `http.md` caching

## diskcache / moke

https://calmcode.io/course/diskcache/introduction
https://github.com/deliro/moka-py

## memcached

https://read.engineerscodex.com/p/how-facebook-scaled-memcached
* _is?_: volatile cache https://news.ycombinator.com/item?id=23689549 aka application caching layer
* _how?_: distributed hash table i.e. n instances of app share 1 distributed instance of memcached
* _why?_: so you don't have to read from db
* _disadvantages_: doesn't track cache misses; meant for simple data, not tables or objects; not durable http://aosabook.org/en/nosql.html
* _sink_: https://realpython.com/python-memcache-efficient-caching/ https://github.com/thadeusb/flask-cache Django has OOB support for memcached https://docs.djangoproject.com/en/2.1/topics/cache/

## Redis

📙 https://www.openmymind.net/2012/1/23/The-Little-Redis-Book/

* vs. memcached https://blog.bytebytego.com/p/ep155-the-shopify-tech-stack
* client https://github.com/laixintao/iredis
* license craziness https://www.cs.cmu.edu/~pavlo/blog/2025/01/2024-databases-retrospective.html
> I'll be blunt: I don't care for Redis. It is slow, it has fake transactions, and its query syntax is a freakshow. Our experiments at CMU found Dragonfly to have much more impressive performance numbers (even with a single CPU core). In my database course, I use the Redis query language as an example of what not to do. Nevertheless, I am sympathetic to Redis Ltd.'s plight of being overrun by Amazon. However, the company is overestimating the barrier of entry to build a simplistic system like Redis; it is much lower than building a full-featured DBMS (e.g., Postgres), so there are several alternatives to the OG Redis. They are not in position of strength where such posturing will be tolerated by the community. https://www.cs.cmu.edu/~pavlo/blog/2025/01/2024-databases-retrospective.html

* scaling https://www.youtube.com/watch?v=uptpnVdwFM4
* open source alternative Valkey https://www.youtube.com/watch?v=npnagMgbruc
* another alternative https://news.ycombinator.com/item?id=43379262 reactive https://dicedb.io/
https://www.openmymind.net/Redis-Is-The-Most-Important-Tool-In-My-Toolbelt/
https://www.openmymind.net/2011/5/8/Practical-NoSQL-Solving-a-Real-Problem-w-Mongo-Red/
https://www.openmymind.net/Data-Modeling-In-Redis/
transactions https://www.openmymind.net/You-Cant-Rollback-Redis-Transaction/
> just use postgres https://martinheinz.dev/blog/105
* pipelines https://medium.com/@tonywangcn/27-6-of-the-top-10-million-sites-are-dead-6bc7805efa85
* https://www.youtube.com/watch?v=WQ61RL1GpEE
* https://www.youtube.com/watch?v=5TRFpFBccQM
* implementation http://aosabook.org/en/nosql.html
* https://github.com/dragonflydb/dragonfly
* test/mock https://github.com/cunla/fakeredis-py
* use Postgres as impl https://github.com/alash3al/redix
* governance https://news.ycombinator.com/item?id=23689549
* key expiration https://news.ycombinator.com/item?id=30099572
* alternative https://github.com/dragonflydb/dragonfly https://github.com/buraksezer/olric#installing
* embedded https://github.com/symisc/vedis https://news.ycombinator.com/item?id=19464144
> You can either set Redis up as a "data-structures" server or you set it up right as a cache. You can't do both. If you choose to use Redis as your cache, ensure that the cache instance is only serving as your cache. Your inter-system message bus should be on a different Redis with a different configuration. https://calpaterson.com/ttl-hell.html

# 🏗️ DEPLOYMENT

SEMANTICS
* _release_: users get latest deployment
* _canary release_: only subset of users get latest deployment https://medium.com/netflix-techblog/automated-canary-analysis-at-netflix-with-kayenta-3260bc7acc69 
* _version detection_: `$BASH_VERSION == "4.4"` https://github.com/oils-for-unix/oils/wiki/Feature-Detection-Is-Better-than-Version-Detection
* _feature detection_: "does the feature that I need exist?"

---

🗄
* `infra.md` config mgmt
* `linux.md` build systems
* `security.md` secrets mgmt
* `sql.md` migrations

https://news.ycombinator.com/item?id=41968026
https://blog.pecar.me/rds-blue-green
https://blog.pecar.me/gunicorn-restart

## CICD

OPTIONS
* _Dagger_: created by the guy who created Docker, used Cuelang https://github.com/dagger/dagger https://news.ycombinator.com/item?id=30857012
* _Github Actions_: 🗄️ `git.md` Github / Actions
> you get a cool deployments tab on the repo as well that shows what's processing

GITOPS
> The idea is to bring together the processes of deploying code and managing that code with version control (git being one of the more popular source control tools in use these days). Instead of keeping your code in a Git repository and then running some command or process to manually deploy changes from it, when you do GitOps you are automatically deploying whatever is at the head of that repo. So 'deployment', for you as a developer, means simply merging a pull request, and the automation does the rest. This means maintaining a single Git repository that contains all of your Kubernetes manifests, both for your own applications, along with any supporting services you need to install, such as prometheus for metrics, fluentd for logs, or cert-manager for managing TLS certificates. Because everything is in one place, it's easy to manage, and there's a single audit trail that shows who changed what, when, and why in the git commit history. Adding a new application to your clusters can be as simple as opening a PR to this central “configuration repo” containing the Kubernetes manifests or Helm charts for your new service. Once that PR is approved by your team and merged, a GitOps tool (like Flux or Argo) can automatically apply that change from within the cluster. https://bitfieldconsulting.com/blog/what-is-gitops

---

* build times https://entropicthoughts.com/build-failure-rate-from-build-times
https://github.com/kehoecj/validate-configs-action
https://github.com/zillow/tycho

* validate configs https://github.com/kehoecj/validate-configs-action
* taxonomy: yolo (edit on server) FTP (edit on local, push to server) SCM (SSH to sever and pull repo, maybe use cron) CICD (triggered by repo hook https://dagger.io/) https://css-tricks.com/deployment/
* pipelines: fetch (clone from repo) build (install deps, compile) test (run unit tests) deploy (put artifact somewhere so CD can pick it up and run it)
* Jenkins https://itnext.io/jenkins-is-getting-old-2c98b3422f79 https://www.youtube.com/watch?v=WWcijE7ifcA
* BYO http://aosabook.org/en/500L/a-continuous-integration-system.html
* _deployment_: align higher env w/ lower env https://css-tricks.com/deployment/
* _staged deployment_: deploy to a few nodes at a time 📙 Kleppmann 4.112
* _blue-green deployment_: split traffic btw new and old; aka red-black https://fly.io/django-beats/smooth-database-changes-in-blue-green-deployments/?utm_campaign=Django%2BNewsletter&utm_medium=email&utm_source=Django_Newsletter_198 https://news.ycombinator.com/item?id=39048317

## env var (12 factor)

* https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/
* security re: access keys https://www.youtube.com/watch?v=R69FnBT00ew
* 📙 Thomas pragmatic programmer [144]

## denv

🗄
* `containers.md`
* `django.md` denv
* `linux.md` denv

CLOUD
* why local https://nickgerace.dev/posts/theres-nothing-like-local-development/ https://news.ycombinator.com/item?id=42043130
* why cloud: CPU/mem intensive e.g. 2TB mem for computational biology https://realpython.com/podcasts/rpp/197/
> I don't understand the need for "cloud development environments" though. Isn't the point of containerized apps is to avoid the need for synchronizing dev envs amongst teams?...It's to ensure a consistent environment for all developers, with the resources required. E.g. they mention GPUs, for developers working with GPU-intensive workloads. You can ship all developers gaming laptops with 64GB RAM and proper GPUs, and have them fight the environment to get the correct libraries as you have in prod (even with containers that's not trivial), or you can ship them Macbook Airs and similar, and have them run consistent (the same) dev environments remotely (you can self-host gitpod, it's not only a cloud service, it's more the API/environment to get consistent remote dev enviornments). https://news.ycombinator.com/item?id=42042522
* 🎯 Omakub on a spot instance?
* _Coder_: https://github.com/coder/coder
* _CodeSandbox_: https://codesandbox.io/docs/sdk
* _Devpod_: 🎯 https://www.youtube.com/watch?v=ceDrFx2K3jE
* _Daytona_: https://www.daytona.io/
* _Github codespaces_: https://github.com/features/codespaces https://www.thoughtworks.com/radar/tools?blipid=202203053 https://cli.github.com/manual/gh_codespace
* _Github devcontainers_: https://code.visualstudio.com/docs/devcontainers/containers
* _Gitpod_: 🎯 runs on your own AWS env (per This Week in AWS) https://www.gitpod.io/ https://www.youtube.com/watch?v=XcjqapXfrhk https://www.youtube.com/watch?v=llRLh8cM7QI 27:15 https://news.ycombinator.com/item?id=42041917
* _Theia_: https://github.com/eclipse-theia/theia https://news.ycombinator.com/item?id=41563958
* _Zed_: https://zed.dev/releases/stable/0.145.1 https://www.youtube.com/watch?v=F9sQPpVVLeQ

---

* https://www.lastweekinaws.com/blog/the-real-reason-cloud-ide-adoption-is-lagging/
* dev containers https://github.com/michidk/vscli
* db: not a silver bullet (Postgres in your Docker container will have some differences to db server you're connecting to in prod)

## feature flag

---

https://simonwillison.net/2025/Feb/2/feature-flags/
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

## secrets (dotenvx)

🗄
* `security.md` users/ passwords
* `shell.md` env var
* `spec.md` config

WORKFLOWS
* env file: gitignore, 600 perms, read from script 🗄️ `ai.md` aider
```sh
# aider.env
export OPENAI_API_KEY=ur_key
# bz
OPENAI_KEY_PATH="$HOME/Documents/denv/bin/aider.env"
```
* export: rm from shell history 🗄️ `ai.md` llm
* 📍 to grok

---

🧠 https://chatgpt.com/c/673f8c16-e090-8004-bdc8-564bbfeb33d5
> env var, fs, manager https://news.ycombinator.com/item?id=40789353
> 💡 point config to file holding pw = you can version control config https://www.youtube.com/watch?v=2yplBzPCghA [7:30]

VAULTS
* _BitWarden_: has their own vault?
* _KMS_: AWS service for storing encryption keys https://www.youtube.com/watch?v=eIvbUU8VH30

CLIENTS
* how to share https://github.com/dotenvx/dotenvx/issues/267
* _whispr_: can fetch from vaults https://github.com/narenaryan/whispr
* _dotenv_: ✅ started using in 2019 with Flask https://github.com/theskumar/python-dotenv
* _dotenvx_: https://github.com/dotenvx/dotenvx https://dotenvx.com/blog/2024/06/24/dotenvx-next-generation-config-management.html
* check out extensions https://github.com/dotenvx/dotenvx/pull/426
* decrypt: pw into manager (BitWarden) https://github.com/dotenvx/dotenvx/issues/223
```sh
$ dotenvx encrypt
# ✔ encrypted .env, key added to .env.keys (DOTENV_PRIVATE_KEY)
# ℹ run [DOTENV_PRIVATE_KEY='loooooooong-sha256' dotenvx run -- yourcommand] to test decryption locally
```
```sh
#!/usr/bin/env bash
echo 'hey $ME'
```
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

# 🛤️ PROXY

🗄
* `application.md` caching
* `flask.md` context
* `infra.md` servers

TYPES
* _proxy_: layer between requester and responder
* _reverse proxy_: closer to servers
* often unecessary https://news.ycombinator.com/item?id=41642151 
* less of a need given a cloud environment where a load balancer is already built-in?
* https://pythonspeed.com/articles/gunicorn-in-docker/ https://www.artur-rodrigues.com/tech/2023/03/12/reverse-proxy-with-dynamic-backend-selection.html https://www.youtube.com/watch?v=RqfaTIWc3LQ https://www.youtube.com/watch?v=4NB0NDtOwIQ
* _forward proxy_: closer to users; way for users to access resources outside network https://www.linuxbabe.com/it-knowledge/differences-between-forward-proxy-and-reverse-proxy https://github.com/mkjt2/lockbox

---

* https://github.com/apernet/hysteria
* when things go wrong on Cloudflare https://news.ycombinator.com/item?id=30054739
📍 https://www.youtube.com/watch?v=-W9F__D3oY4
* _OpenResty_: Nginx + script some more logic in with Lua https://www.dataengineeringpodcast.com/linode-object-storage-service-episode-125/ 10:00
* _firewall_: impl rules for server in/egress (e.g. iptables)
* https://entropicthoughts.com/basic-firewall-configuration-iptables
* UFW https://github.com/peltho/tufw
* phoning home, open snitch https://news.ycombinator.com/item?id=33506576
* https://softwareengineeringdaily.com/2021/08/10/fly-io-geographic-app-deployment-with-kurt-mackey/
* _sink_: https://serversforhackers.com/t/proxies https://www.maxcdn.com/one/visual-glossary/proxy-caching/ reverse cache https://msdn.microsoft.com/en-us/library/windows/desktop/dd892097%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396 https://blog.envoyproxy.io/introduction-to-modern-network-load-balancing-and-proxying-a57f6ff80236

## CDN

> Oh, you want all your images to be cached at the edge so they're super snappy for everyone visiting your page, but you also want to bust your cache each time you publish a new version of your site? Fuck you! Figure it out and do it yourself. https://zackproser.com/blog/maintaining-this-site-fucking-sucks
> Caching reverse proxies that you self-host, like Varnish and Apache Traffic Server, can use non-standard PUSH and PURGE verbs that let you explicitly control the cache contents. If you can invalidate explicitly you can use strategies #2 and #3 [update-on-write]. If you have the file on hand, why not also populate your reverse proxy's cache? The nice thing overall about caching at the HTTP level is that it takes work off the applications server's plate. https://calpaterson.com/ttl-hell.html
* BYO https://github.com/leandromoreira/cdn-up-and-running https://news.ycombinator.com/item?id=41731720
* https://jvns.ca/blog/2016/04/29/cdns-arent-just-for-caching/
* https://css-tricks.com/adding-a-cdn-to-your-website/
* Google/Facebook CDNs are blocked in China https://www.freecodecamp.org/news/devblog-launch-your-developer-blog-own-domain/
* https://www.youtube.com/watch?v=6DXEPcXKQNY
* _sink_: https://arp242.net/cdn.html https://css-tricks.com/adding-a-cdn-to-your-website/ http://highscalability.com/blog/2011/2/28/a-practical-guide-to-varnish-why-varnish-matters.html Whitenoise vs. nginx https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/ https://pasztor.at/blog/building-your-own-cdn
* BYO https://dev.to/megajakob/how-to-build-your-own-cdn-io1 https://debugged.it/blog/building-your-own-cdn/
* _files - static_: CSS, JS, fonts https://learndjango.com/tutorials/django-static-files
* _files - media_: uploaded by user https://docs.djangoproject.com/en/3.1/topics/files/#managing-files

## load balancing

* https://sre.google/sre-book/table-of-contents/
* algos https://www.youtube.com/watch?v=dBmxNsS3BGE
* https://news.ycombinator.com/item?id=35588797
* https://www.youtube.com/watch?v=galcDRNd5Ow
* _ALB_: protocols (HTTP, gRPC) algo (round robin based on HTTP headers or session ID) https://aws.amazon.com/compare/the-difference-between-the-difference-between-application-network-and-gateway-load-balancing/
> You should probably use one even if you only have 1 instance. For $16/mo you get automatic TLS cert management, and that alone makes it worth it IMO. You just set it up once & forget about it. An ALB is probably what you’ll need, but NLB is good too. https://x.com/dvassallo/status/1154516910265884672
* _NLB_: protocols (TCP, UDP, TLS) algo (flow hash based on IP address)
* _GLB_: network
* load balancer vs. API gateway vs. ingress controller https://caddyserver.com/docs/
* _HAProxy_: just does load balancing (vs. Nginx, which also serves static assets) https://stackoverflow.com/a/21181066/6813490 conf (port, lb algo, server for forwarding)
* Nginx, Envoy https://dropbox.tech/infrastructure/how-we-migrated-dropbox-from-nginx-to-envoy https://news.ycombinator.com/item?id=32572153
* _algos_: least-busy (based on server pushing <foo> metric?) round-robin (subject to chance i.e. server n could unluckily keep getting the heavier requests) https://www.youtube.com/watch?v=-W9F__D3oY4 @ 18:00
* _hw_: Kemp, Barracuda, F5; run $1-20k bc need to handle GBps of traffic https://news.ycombinator.com/item?id=21095159&utm_term=comment 
* BYO: https://kasvith.github.io/posts/lets-create-a-simple-lb-go/ https://dev.to/bmf_san/implement-a-load-balancer-in-golang-8gj https://hackernoon.com/this-150-line-go-script-is-actually-a-full-on-load-balancer

# 🏁 QUEUES

🗄
*️ `architecture/system.md` distributed
* `eng.md` pipelines
📚
* Kleppmann ch. 11
* Narkhede ch. 11

TAXONOMY https://eranstiller.com/rabbitmq-vs-kafka-an-architects-dilemma-part-1
* _bus_: stores msgs
* _message queue_: bus + FIFO; aka stream processing https://stackoverflow.com/q/7793927 📙 Kleppmann [3]
* _job_: https://github.com/janbjorge/pgqueuer
* _task queue_: consumes task, exec, return result; aka batch processing 📙 Kleppmann [3]
* _workflow engine_: cron + track job history + easy to compose jobs

PATTERNS
* _point-to-point_: 1 pub, 1 sub
* _pub-sub_: 1 pub, n subs, immediate push
* _fanout exchange_: send msg to all bound queues
* _priority queue_: assign priority to msgs https://stackoverflow.com/a/32343878
* _deadletter queue_: stores undelivered msgs from other queues

PUB/SUB 📙 Narkhede ch. 1
* why: interprocess communcation
* alternative to point-to-point
* _publisher_: publish msg
* _broker_: destination for published msg
* _subscriber_: consumes msgs of class

---

* semantics 📻 Macey 4:50
* https://bloomberg.github.io/blazingmq/
https://www.openmymind.net/Grow-Up-Use-Queues/
poison https://www.openmymind.net/Queue-Despair-Ordering-And-Poison-Messages/

## cron

---

* cron / scheduling / daemon: https://github.com/zachvalenta/pypub https://github.com/maxhumber/hickory https://docs.python.org/3/library/sched.html https://github.com/dbader/schedule https://github.com/dbader/schedule https://schedule.readthedocs.io/en/stable/faq.html#how-to-continuously-run-the-scheduler-without-blocking-the-main-thread https://towardsdatascience.com/scheduling-all-kinds-of-recurring-jobs-with-python-b8784c74d5dc

CRON https://chatgpt.com/c/6728d6eb-b654-8004-acba-f5f0d6aa8055 https://www.youtube.com/watch?v=QZJ1drMQz1A
* used for: backups, rotate log files
* semantics: cron = daemon, crontab(le) = file
* alternatives: launchd = macOS version? https://en.wikipedia.org/wiki/Launchd anachron runs even if machine powered off (unlike chron) https://ports.macports.org/port/anacron/ https://github.com/dshearer/jobber
> It’s a simple text file with an ASCII table that will execute a command on schedule. 📙 Conery [422]
* flags: `-l` list `-e` edit
* fs: system `/etc/crontab` user `/tmp/crontab.$HASH`
* macOS perms workaround https://www.bejarano.io/fixing-cron-jobs-in-mojave/
* syntax https://crontab.guru/examples.html
* env: does not load same env (.bashrc, .zshrc) so you should use absolute paths, does not log the output anywhere by default https://missing.csail.mit.edu/2019/automation/
```sh
$SCHEDULE $USER /path/to/script.sh >> /tmp/out.log 2>&1
```
```yaml
tasks:
  - name: "Backup"
    command: "python3 backup.py"
    interval: "daily"
  - name: "Data Cleanup"
    command: "python3 cleanup.py"
    interval: "hourly"
  - name: "Generate Report"
    command: "python3 generate_report.py"
    interval: "weekly"
```
```python
import schedule
import time
import subprocess
import yaml
from datetime import datetime, timedelta

def load_tasks(file_path='tasks.yaml'):
    with open(file_path, 'r') as file:
        config = yaml.safe_load(file)
    return config['tasks']

def schedule_task(task):
    command = task['command']
    def job():
        print(f"Running: {task['name']} - {datetime.now()}")
        subprocess.run(command, shell=True)
    interval = task.get('interval', 'daily')
    if interval == "hourly":
        schedule.every().hour.do(job)
    elif interval == "daily":
        schedule.every().day.at("00:00").do(job)
    elif interval == "weekly":
        schedule.every().monday.at("00:00").do(job)
    else:
        minutes = int(interval)
        schedule.every(minutes).minutes.do(job)

def main():
    tasks = load_tasks()
    for task in tasks:
        schedule_task(task)
    while True:
        schedule.run_pending()
        time.sleep(300)

if __name__ == "__main__":
    main()
```
```python
# alt impl
import schedule
import time
def job1(): print("Job 1 executed")
schedule.every().hour.do(job1)             # Every hour
schedule.every().monday.at("13:15").do(job1)   # Every Monday at 1:15 PM
while True:
    schedule.run_pending()
    time.sleep(1)
```

## event (Kafka)

📚
* Narkhede guide
* https://www.manning.com/books/streaming-data-pipelines-with-kafka

---

ALTERNATIVES
* Redis streams https://news.ycombinator.com/item?id=43790420
* _AWS SQS_: https://cheesecakelabs.com/blog/asynchronous-task-queue-django-celery-aws-sqs
* _Nats_: Nats (non-durable) Jetstream (durable) https://faststream.airt.ai/latest/nats/#advantages-and-disadvantages https://nats-io.github.io/nats.py/
* lib + Kafka https://github.com/airtai/FastStream
```sh
# https://chatgpt.com/c/67f82c9e-e088-8004-b351-3d2ef30e212f https://claude.ai/chat/1caf57d7-7999-4ceb-ba45-846a91e0d4a5
brew install nats-io/nats-tools/nats-server  # on macOS
nats-server --js
pip install nats-py

brew install --cask stats      # optional: system monitor
```
* _Pulsar_: Kafka alternative https://www.youtube.com/watch?v=x4k1XEjNzYQ
* _Rabbit_: comes w/ own db https://stackoverflow.com/q/38444425
* vs. Kafka https://aws.amazon.com/msk/what-is-kafka/
* _ZeroMQ_: http://aosabook.org/en/zeromq.html https://zguide.zeromq.org/docs/chapter1/

TOOLING
* _kaskade_: TUI https://github.com/sauljabin/kaskade
* _kplay_: message inspection https://github.com/dhth/kplay
* _plumber_: CLI https://github.com/batchcorp/plumber

https://www.warpstream.com/ https://changelog.com/podcast/606#transcript + sponsors

🗄 `data/eng.md` streaming
📜 https://kafka.apache.org/documentation/
* https://www.manning.com/books/kafka-streams-in-action-second-edition
📹
* 101 https://www.youtube.com/playlist?list=PLa7VYi0yPIH0KbnJQcMv5N9iW8HkZHztH
* talk https://www.youtube.com/watch?v=Ltgt0ekso4c
* example https://www.youtube.com/channel/UCDankIVMXJEkhtjv5yLSN4g/videos

RUN
* Docker https://www.youtube.com/watch?v=qi7uR3ItaOY 4:00
* GUIs https://news.ycombinator.com/item?id=24099037 https://akhq.io/ https://github.com/sauljabin/kaskade
* alternative https://github.com/liftbridge-io/liftbridge https://buf.build/blog/bufstream-jepsen-report
* no more Zookeeper (impl yet?) https://news.ycombinator.com/item?id=23207377 https://www.confluent.io/blog/kafka-without-zookeeper-a-sneak-peek/
* _Confluent_: managed Kafka https://news.ycombinator.com/item?id=26644713
```sh
https://kadekillary.work/note/kafka/
```

SEMANTICS
* _topic_: group of msgs
* can have n consumers for 1 topic
* _producer_: write msg to topic
* _consumer_: read msg from topic
* read doesn't destroy msg (unlike MQ)
* can either stream or batch https://kafka.apache.org/intro.html
* _transactions_: https://www.warpstream.com/blog/kafka-transactions-explained-twice

USAGE
* as distributed commit log https://news.ycombinator.com/item?id=26644713 📙 Jeffrey distributed [6]
> same as audit log?

PROTOCOL https://kafka.apache.org/0100/protocol.html
* rides on top of TCP so you need client per language https://strimzi.io/blog/2019/07/19/http-bridge-intro/
* handshake https://pierrezemb.fr/posts/diving-into-kafka-protocol/
* _message set_: msgs grouped https://kafka.apache.org/documentation/#maximizingefficiency

za
* BYO https://github.com/travisjeffery/jocko https://www.openmymind.net/Building-A-Queue-Part-1/
* https://developer.confluent.io/what-is-apache-kafka/#intro-to-ak
* https://www.confluent.io/blog/author/martin-kleppmann/
* Avro (eventbus README)
* https://unitedmasters.atlassian.net/wiki/spaces/ENG/pages/322273452/Event+Bus+System

## msg (Rabbit)

* use something else
> RabbitMQ (for our purposes, Redis would probably work equally well as a task queue and just using Redis would reduce operational burden) https://danluu.com/simple-architectures/

---

* queue attributes: durability (keep in mem, write to disk, write to db bc broker can restart, fail) time-to-live (how long to keep in the queue?) security (what consumers have access?) batching (delivery immediately or wait until x messages before allowing consumers to take)
* msg attributes: id, user/groups id, creation time, reply to, subject https://www.rabbitmq.com/tutorials/amqp-concepts.html
* _MQTT_: https://news.ycombinator.com/item?id=41912787 https://github.com/EdJoPaTo/mqttui/
* _AMQP_: protocol for MQ; alternatives incl. JMS, MSMQ, STOMP (text vs. binary for AMQP); originated in 2003 at JP Morgan, worked w/ Red Hat to create Qpid; can set version in HTTP but not AMQP https://www.digitalocean.com/community/tutorials/an-advanced-message-queuing-protocol-amqp-walkthrough
> Unlike JMS, which defines an API and a set of behaviors that a messaging implementation must provide, AMQP is a wire-level protocol. A wire-level protocol is a description of the format of the data that is sent across the network as a stream of bytes. Consequently, any tool that can create and interpret messages that conform to this data format can interoperate with any other compliant tool irrespective of implementation language. - https://spring.io/understanding/AMQP
* _consumer ack_: queue only rm msgs when consumer acks https://www.rabbitmq.com/tutorials/amqp-concepts.html
* _consumer priority_: defaults to highest in Qpid https://qpid.apache.org/releases/qpid-broker-j-7.0.6/book/Java-Broker-Runtime-Consumers.html#Java-Broker-Runtime-Consumers-Prioirty Spring allows setting on the consumer side but JMS doesn't https://stackoverflow.com/q/53602831/6813490 https://docs.spring.io/spring-amqp/reference/htmlsingle/#consumer-priority but does allow message priority https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jms/core/JmsTemplate.html#setPriority-int-
* _back pressure_: pressure from data source to write new data when streaming system is already holding too much (e.g. bc consumer hasn't ingested) [Macey 39:00]
* _order_: round robin in RabbitMQ https://www.rabbitmq.com/consumer-priority.html

SEMANTICS
* _entity_: producer, consumer
* _broker(queue)_: app to send/rec/store msgs conforming to AMQP
* _exchange_: receives message, routes to queue
* _queue_: entity that holds msg for consumer
* _binding_: rule for routing from exchange to queue
* _entity_: collective name for queue, exchange, binding https://www.rabbitmq.com/tutorials/amqp-concepts.html
* used to offload long-running operations outside HTTP req-res cycle options (email, report generation, talking to third-party services) https://nickjanetakis.com/blog/4-use-cases-for-when-to-use-celery-in-a-flask-application
* don't need presently available connection (unlike API) https://www.netlify.com/blog/2017/03/02/to-message-bus-or-not-distributed-systems-design/
* use for all db operations?!? https://www.openmymind.net/Grow-Up-Use-Queues/
* https://news.ycombinator.com/item?id=22901856 Kleppmann 4.136

## task (Celery)

🔍 https://taskqueues.com/ 
🗄
* `django.md` libs > tasks
* `eng.md` pipelines
* `tools.md` jobs

* use something else https://danluu.com/simple-architectures/e
> Celery (which is overcomplicated for our use case and has been implicated in several outages e.g. due to backwards compatibility issues during version upgrades)
* monitoring https://github.com/healthchecks/healthchecks
> Healthchecks is a cron job monitoring service. It listens for HTTP requests and email messages ("pings") from your cron jobs and scheduled tasks ("checks"). When a ping does not arrive on time, Healthchecks sends out alerts.

---

CLEANUP
* https://www.dbos.dev/blog/why-workflows-should-be-postgres-rows
* https://judoscale.com/blog/choose-python-task-queue
* https://testdriven.io/courses/django-celery/ https://testdriven.io/blog/django-admin-celery/
* durable https://github.com/dbos-inc/dbos-transact-py
* https://github.com/cybertec-postgresql/pg_timetable
* chron jobs https://github.com/Nukesor/pueue
* BYO https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/
* https://github.com/bensheldon/good_job
* _Hatchet_: https://github.com/hatchet-dev/hatchet
* _Huey_: https://www.untangled.dev/2020/07/01/huey-minimal-task-queue-django https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#27:00 https://github.com/coleifer/huey https://www.youtube.com/watch?v=TV7jHHpvGvA

CELERY 📹 https://www.youtube.com/@NickJanetakis/search?query=celery
* https://adamj.eu/tech/2020/02/03/common-celery-issues-on-django-projects
* https://steve.dignam.xyz/2023/05/20/many-problems-with-celery/
* https://nickjanetakis.com/blog/4-use-cases-for-when-to-use-celery-in-a-flask-application
* https://us.pycon.org/2024/schedule/presentation/35/index.html
* Redis as db for Celery jobs https://ljvmiranda921.github.io/notebook/2019/11/08/flask-redis-celery-mcdo/
* https://www.youtube.com/watch?v=v7LOVlPq7ds
* _Flower_: monitor Celery https://github.com/mher/flower https://testdriven.io/blog/flower-nginx/
* https://www.agiliq.com/blog/2015/07/getting-started-with-celery-and-redis/
* https://djangostars.com/blog/the-python-celery-cookbook-small-tool-big-possibilities/
* https://testdriven.io/blog/asynchronous-tasks-with-falcon-and-celery/
* https://stackshare.io/sentry/how-sentry-receives-20-billion-events-per-month-while-preparing-to-handle-twice-that

REDIS QUEUE (RQ)
* https://testdriven.io/blog/asynchronous-tasks-with-flask-and-redis-queue/
* https://pyvideo.org/pygotham-2018/tracking-the-international-space-station-in-django-with-redis-queue-and-rq-scheduler.html
* https://testdriven.io/blog/sending-confirmation-emails-with-flask-rq-and-ses/#workflow
* https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/

## workflow engine (Airflow)

🗄 `eng.md` pipelines
📙 https://www.manning.com/books/data-pipelines-with-apache-airflow-second-edition

---

* calling LLMs https://github.com/astronomer/airflow-ai-sdk https://news.ycombinator.com/item?id=43544631
* _AWS Step Functions_: 
* _Airflow_: https://news.ycombinator.com/item?id=23349507 https://tech.marksblogg.com/install-and-configure-apache-airflow.html https://www.youtube.com/watch?v=7YCEydBUnjg
* aaS https://www.astronomer.io/managed-airflow-service/
* local https://www.youtube.com/watch?v=A1p5LQ0zzaQ
* _Dagster_: https://github.com/dagster-io/dagster https://www.pythonpodcast.com/dagster-data-orchestration-episode-279/ https://www.dagster.io/blog/dagster-airflow https://news.ycombinator.com/item?id=39217728 https://talkpython.fm/episodes/show/454/data-pipelines-with-dagster https://trino.io/blog/2022/08/24/data-pipelines-production-ready-great-expectations.html
* _Luigi_: https://github.com/spotify/luigi
* _Mage_: https://github.com/mage-ai/mage-ai https://www.youtube.com/watch?v=y5sWD1yWi70
* _n8n_: hosted, WSIYWG https://news.ycombinator.com/item?id=37274052

# 🤖 WEB SERVERS

🗄️
* `application.md` HTTP
* `stdlib.md` web / frameworks

LOCALITY
```txt
The web server's job is basically just:
* accept the http connection
* parse the request
* hand it to your application code
* take your response and send it back

That's typically milliseconds or less. But then your actual application code might:
* wait 100ms for a db query
* wait 200ms for an api call
* spend 50ms processing data
* wait 150ms for another api call

So the web server piece ends up being maybe 1-5% of your total response time. That's why shifting from Gunicorn to a faster server often doesn't move the needle much in real-world apps.
```

SEMANTICS
* req/res: OS takes req on port, hands req to web server, web server hands req to app server, app server hands req to application, res flow back up
* servers useful in Python bc GIL only allows one thread to execute at a time so server does pools other connections 📙 Butcher practice 1.3.3
* why use a server? in Python's case bc 
* _machine_: hw (or vm) https://sre.google/sre-book/production-environment/
* _server_: machine w/ server sw or sw itself https://sre.google/sre-book/production-environment/
* _web server_: deal w/ HTTP, handle static content and rate limiting https://www.quora.com/What-are-the-differences-between-nginx-and-gunicorn
* port 80
* BYO https://ruslanspivak.com/lsbaws-part1/ https://realpython.com/courses/programming-sockets/
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

URL FOR DEV SERVER
* _ngrok_
* _pico_: https://pico.sh/tuns https://news.ycombinator.com/item?id=40355744 
* _piko_: https://github.com/andydunstall/piko

ALTERNATIVES
* just use SQLite https://news.ycombinator.com/item?id=41963996
* _Apache_: on start, Apache runs as master process `root` and binds to port 80; pre-fork (master process spawns child proccesses under UID `apached` to wait for connections) https://stackoverflow.com/a/25894770/6813490
* _CGI_: process per req (vs. connection) cannot keep db connection over multiple
* _Granian_: https://github.com/emmett-framework/granian https://talkpython.fm/episodes/show/463/running-on-rust-granian-web-server https://mkennedy.codes/posts/we-must-replace-uwsgi-with-something-else-but-with-what/
* _hypercorn_: https://mkennedy.codes/posts/we-must-replace-uwsgi-with-something-else-but-with-what/
* _uvicorn_: https://mkennedy.codes/posts/we-must-replace-uwsgi-with-something-else-but-with-what/
* _redbean_: small https://justine.lol/redbean/index.html https://news.ycombinator.com/item?id=27431910 https://simonwillison.net/2025/Feb/6/sqlite-page-explorer/

💀 UWSGI
* in maintenance mode https://pythonbytes.fm/episodes/show/401/we-must-replace-uwsgi-with-something-else
* impl in C
* docs are a mess, scroll past 42 changelogs for the README, and commercial support in Italian https://github.com/unbit/uwsgi-docs#commercial-support
* run options https://blog.ionelmc.ro/2022/03/14/how-to-run-uwsgi/
* commands https://github.com/zachvalenta/flask-skeleton/commit/435517e5e1353eaa875d16e91ea96e47300b35dc
```python
from myproject import application
if __name__ == "__main__":
    application.run()
```
```sh
uwsgi --http :9090 --wsgi-file foobar.py # https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploy-it-on-http-port-9090
uwsgi --socket 0.0.0.0:8000 --protocol=http -w wsgi # https://github.com/zachvalenta/flask-uwsgi-scaffold https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uswgi-and-nginx-on-ubuntu-18-04
uwsgi --http :5002 --wsgi-file app.py --callable app # expects app obj to be named `application`, rename w/ `callable` https://riptutorial.com/flask/example/16286/using-uwsgi-to-run-a-flask-application # https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploying-flask
# https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#adding-concurrency-and-monitoring
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2 --stats 127.0.0.1:9191
```
* can also point to app obj via `uwsgi.py` or `uwsgi.ini` https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04 https://www.youtube.com/watch?v=lnFMKAIHRcA

---

> Parsing the request is just a matter of splitting the request string into lines. The first line contains the method, path and protocol separated by spaces. The following lines contain the headers, followed by an empty line. https://blog.sylver.dev/build-a-web-server-with-rust-and-tokio-part-0-a-simple-get-handler
* benchmark: https://httpd.apache.org/docs/2.4/programs/ab.html https://github.com/wg/wrk https://github.com/giltene/wrk2 https://github.com/rakyll/hey https://github.com/encode/starlette#performance https://falconframework.org/#sectionBenchmarks https://www.webpagetest.org/ https://www.golang.dk/articles/benchmarking-sqlite-performance-in-go
* BYO https://github.com/codecrafters-io/build-your-own-x#build-your-own-web-server https://news.ycombinator.com/item?id=41642151 https://doc.rust-lang.org/book/ch20-00-final-project-a-web-server.html
* mock server: https://smocker.dev/
* comment server: Disqus, isso https://avi.im/blag/about/ https://posativ.org/isso/docs/
* BYO https://defn.io/2018/02/25/web-app-from-scratch-01/ http://joaoventura.net/blog/2017/python-webserver/

## Caddy

📜 https://github.com/caddyserver/caddy

---

https://github.com/abiosoft/caddy-exec
https://caddyserver.com/docs/getting-started https://caddyserver.com/docs/quick-starts

* license https://news.ycombinator.com/item?id=24434709
* _design_: no dependencies (not even libc); modules impl in Go
* _config_: via file or API

https://tech.marksblogg.com/caddy-https-minio.html

* _install_: macOS (Homebrew) other UNIX https://nginx.org/en/linux_packages.html
* _functionality_: caching https://danielmiessler.com/blog/nginx-caching-tempfs/ https://serversforhackers.com/c/nginx-caching rate limiting https://lincolnloop.com/blog/rate-limiting-nginx/ TLS https://raymii.org/s/tutorials/Strong_SSL_Security_On_nginx.html https://botleg.com/stories/https-with-lets-encrypt-and-nginx/
* _monitoring_: https://github.com/lebinh/ngxtop https://www.scalyr.com/community/guides/how-to-monitor-nginx-the-essential-guide https://www.honeycomb.io/blog/tell-me-more-nginx/ https://news.ycombinator.com/item?id=23466506
* _processes_: master (read config, manages workers) workers (handles requests)
* _server block_: running more than one site on single host; 类似 Apache virtual host; done w/ `sites-enabled` `sites-available` `conf.d` (macOS only has `servers`) https://stackoverflow.com/a/41303948/6813490

cmds
* _start_: `nginx`
* _stop_: `-s quit` (will wait for workers serving req to finish)
* _reload conf_: `-s reload`

conf
* ❓ per-project config: server block? symlink?
* generate https://www.digitalocean.com/community/tools/nginx 
* security lint https://github.com/yandex/gixy 
* location (Linux `/etc/nginx/nginx.conf` macOS `/usr/local/etc/nginx/nginx.conf`) 
* language: Nginx's own thing despite looking like JSON https://carrot.is/coding/nginx_introduction

## Ferron

https://www.ferronweb.org/

## Granian

🗄️ `telemetry.md` latency

* supports both WSGI and native ASGI (most WSGI servers force sync)
* 2x faster for WSGI than competition
* built-in worker process lifecycle mgmt
* smaller codebase

---

```txt
Network bottlenecks in web apps typically show up as:

External API calls
* Third party services
* Microservices in your architecture
* Cloud services (S3, etc)

Database network latency
* Physical distance to DB server
* Connection pool exhaustion
* Network congestion between app and DB

Client-side latency
* Large response payloads
* Slow client networks
* Geographic distance to users
```
```python
import time
import httpx

def measure_call():
    start = time.perf_counter()
    response = httpx.get('https://api.example.com')
    end = time.perf_counter()
    return end - start
```
```txt
The key insight is that server performance (Granian/Gunicorn) only optimizes the time spent processing the request in your Python code. If your app spends 300ms waiting on external APIs and 5ms processing in Python, even a 2x faster server only saves 2.5ms.

The web server's job is basically just:
* Accept the HTTP connection
* Parse the request
* Hand it to your application code
* Take your response and send it back

That's typically milliseconds or less. But then your actual application code might:
* Wait 100ms for a DB query
* Wait 200ms for an API call
* Spend 50ms processing data
* Wait 150ms for another API call

So the web server piece ends up being maybe 1-5% of your total response time. That's why shifting from Gunicorn to a faster server often doesn't move the needle much in real-world apps. Where raw server performance does matter more:
* Extremely high-concurrency scenarios
* CPU-intensive apps with minimal I/O
* Serverless where cold start time matters
```
```txt
Why would the server matter more here? Given that being ms faster at the server is still beholden to whatever the CPU is doing.
```
```txt
Ah good catch - I was wrong there. You're right: if the app is CPU-bound, then the bottleneck is the actual computation time, not how fast the server hands off the request.

Let me correct my earlier statement. Server raw performance matters most in:
* High-concurrency with lots of small, fast requests
* Serverless where cold start time matters
* Apps doing request routing/proxying where the server's main job is just moving bytes around

The CPU-bound case actually supports the original point - the server choice becomes even less relevant when you have long-running CPU work since it's dwarfed by computation time.
```

## Gunicorn

📜 https://docs.gunicorn.org/en/stable/

> Gunicorn does one thing - it’s a WSGI HTTP server - and it does it well. Deploy it quickly and easily, and let the rest of your stack do what the rest of your stack does well, wherever that may be. https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/

* impl in Python

config
* some settings only available from file https://docs.gunicorn.org/en/latest/settings.html
* _Docker_: start 2 workers (avoid heartbeat time out and scheduler restarting container) conf file for heartbeat (use `/dev/shm`) https://pythonspeed.com/articles/gunicorn-in-docker/
* _precedence_: command line > file > defaults https://docs.gunicorn.org/en/stable/configure.html
* _daemon_: https://stackoverflow.com/a/30503078 https://stackoverflow.com/a/52824526 ❓ so far `--daemon` keeps it running even after terminal closes; thought that every process created from terminal/tty (what's the diff again?) is a subprocess of that terminal and thus stops when terminal closes; other options -> systemd https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-16-04 supervisord https://mattsegal.dev/simple-django-deployment.html https://stackoverflow.com/questions/24941791/starting-flask-server-in-background https://prakhar.me/articles/flask-on-nginx-and-gunicorn/ screen https://stackoverflow.com/a/2975657/6813490 https://www.digitalocean.com/community/questions/how-keep-my-app-running-after-close-putty-f82aab17-ca84-46a0-8a39-3e25f1dd2d45

* command line
```sh
# Flask
gunicorn app:app  # defaults to localhost on port 8000 
gunicorn -b 127.0.0.1:5999 app:app  # specify port
gunicorn -b 0.0.0.0:5999 app:app  # take req from outside os
gunicorn -b 0.0.0.0:5999 app:app --daemon  # run in background

# Django https://docs.djangoproject.com/en/3.0/howto/deployment/wsgi/gunicorn/
gunicorn project.wsgi  # locahost
gunicorn project.wsgi -c guni-conf.py  # run using config file
gunicorn -b 0.0.0.0:5999 project.wsgi  # take req from outside os
```
* file
```python
import os
from dotenv import load_dotenv, find_dotenv

load_dotenv(find_dotenv())
host = os.getenv("APP_HOST")
bind = f"{host}:8000"
accesslog = "-"
```

logging https://mattsegal.dev/django-gunicorn-nginx-logging.html
* _access log_: each req; write to stdout with `accesslog = "-"`
* _error log_: info on start up, shut down
* `caputure_output`: grab info emitted from Django logs and incl in gunicorn log output

design
* pre-fork
* _processes_: typically run different workers, each with their own process https://pythonspeed.com/articles/gunicorn-in-docker/
* works best w/ Nginx https://gunicorn.org/#deployment 
* does ASGI https://sanic.readthedocs.io/en/latest/sanic/deploying.html#running-via-gunicorn https://github.com/encode/starlette#performance

## Nginx

📜 https://nginx.org/en/docs/beginners_guide.html https://nginx.org/en/docs/ https://github.com/trimstray/nginx-admins-handbook

https://github.com/Canop/rhit
https://github.com/zachvalenta/nginx-wsgi https://serverfault.com/q/821284/415712 https://stackoverflow.com/a/25486871/6813490
https://blog.codeship.com/tuning-nginx/

non-Docker
* https://stackoverflow.com/a/54298517
* https://mattsegal.dev/nginx-django-reverse-proxy-config.html
* https://github.com/zachvalenta/nginx-wsgi
* https://www.patricksoftwareblog.com/how-to-configure-nginx-for-a-flask-web-application/
* https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx
* https://www.youtube.com/watch?v=hxngRDmHTM0

Docker
* compose file https://www.youtube.com/watch?v=hxngRDmHTM0 https://pawamoy.github.io/posts/docker-compose-django-postgres-nginx/#compose-add-a-container-for-nginx https://github.com/pawamoy/docker-nginx-postgres-django-example/blob/master/config/nginx/conf.d/local.conf https://github.com/wiamsuri/django-gunicorn-nginx-docker/blob/master/docker-compose.yml
* separate Dockerfile https://www.codementor.io/@samueljames/nginx-setting-up-a-simple-proxy-server-using-docker-and-python-django-f7hy4e6jv https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/#nginx
* https://github.com/productive-dev/minimal-reverse-proxy-demo/blob/master/docker-compose.yml
* https://github.com/bunkerity/bunkerized-nginx

* example
```conf
# https://gunicorn.org/#deployment 

# things set here: log fmt, mime types, access log location https://www.patricksoftwareblog.com/how-to-configure-nginx-for-a-flask-web-application/
http {

    # servers for Nginx to balance btw https://www.youtube.com/watch?v=BRPvjNQsqis https://www.youtube.com/watch?v=spbkCihFpQ8 https://www.nginx.com/resources/wiki/start/topics/examples/loadbalanceexample/ https://nginx.org/en/docs/http/ngx_http_upstream_module.html
    upstream name_for_upstream {
        server localhost:8777;
        server localhost:8778;
    }

    server {
        listen 80;  # set port for Nginx itself
        server_name example.org;
        access_log  /var/log/nginx/example.log;

        # location = URL mapping
        location / {
            # pass requests here (assuming app running on same box)
            proxy_pass http://127.0.0.1:8000;
            proxy_set_header Host $host;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
        # serving static files
        location /static/ {
            # read from disk instead of passing req to WSGI server https://mattsegal.dev/nginx-django-reverse-proxy-config.html
            root /home/myuser/myproject;
        }
    }
}
```

config misc
* generator https://www.digitalocean.com/community/tools/nginx 
* linting https://github.com/yandex/gixy 
* file locations (Linux `/etc/nginx/nginx.conf` macOS `/usr/local/etc/nginx/nginx.conf`)

config syntax https://stackoverflow.com/a/46918583
* https://jvns.ca/blog/2021/09/24/new-tool--an-nginx-playground/
* syntax is custom, kinda looks like JSON, comments via hash at start of line https://unix.stackexchange.com/a/302823
* _directive_: name (mapping to Nginx module) that takes n params
* _simple directive_: one liner
* _block directive_: n lines; events (how many processes) http (routing) https://www.patricksoftwareblog.com/how-to-configure-nginx-for-a-flask-web-application/ aka 'context'
* _main_: anything outside block scope https://www.patricksoftwareblog.com/how-to-configure-nginx-for-a-flask-web-application/

misc
* scripting w/ Lua https://news.ycombinator.com/item?id=10618622
* cache to memory https://danielmiessler.com/blog/nginx-caching-tempfs/
* _docroot_: where Nginx finds files; `/usr/local/Cellar/nginx/1.15.7/html`
* _processes_: master (read config, manages workers) workers (handles requests)
* _server block_: running more than one site on single host; 类似 Apache virtual host; done w/ `sites-enabled` `sites-available` `conf.d` (macOS only has `servers`) https://stackoverflow.com/a/41303948/6813490
* seems like no one uses the commercial version https://dropbox.tech/infrastructure/how-we-migrated-dropbox-from-nginx-to-envoy

functionality and utils
* caching https://danielmiessler.com/blog/nginx-caching-tempfs/ https://serversforhackers.com/c/nginx-caching
* rate limiting https://lincolnloop.com/blog/rate-limiting-nginx/ https://preparingforcodinginterview.wordpress.com/2019/10/19/rate-limiting-algorithm-algo/
* TLS https://raymii.org/s/tutorials/Strong_SSL_Security_On_nginx.html https://botleg.com/stories/https-with-lets-encrypt-and-nginx/
* monitoring https://github.com/lebinh/ngxtop https://www.scalyr.com/community/guides/how-to-monitor-nginx-the-essential-guide https://www.honeycomb.io/blog/tell-me-more-nginx/ https://news.ycombinator.com/item?id=23466506

cmds
* _start_: `nginx`; starts as root and then switches to whatever user you config https://blog.bejarano.io/how-to-write-great-container-images/
* _stop_: `-s quit` (will wait for workers serving req to finish)
* _reload conf_: `-s reload`

# 🟨 ZA

## mobile

* _Kivy_: https://github.com/kivy/kivy https://www.bitecode.dev/p/the-next-big-thing-in-python
* _Flutter_: Python version on the way? https://talkpython.fm/episodes/show/494/update-on-flet-python-flutter-uis
* built using Dart
* fork https://news.ycombinator.com/item?id=41975047

* Kotlin https://nostarch.com/kotlin-scratch https://nostarch.com/kotlin-scratch
* app stores are a pain https://news.ycombinator.com/item?id=33632468
* automate app submission https://github.com/fastlane/fastlane
* Android has bad dev experience https://news.ycombinator.com/item?id=41062292

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

## internationalization (i18n)

* https://phrase.com/blog/posts/internationalization-i18n-go/
* examples: Odoo, https://github.com/jesseduffield/lazygit/tree/master/pkg/i18n
* translate https://tech.marksblogg.com/language-translation-ai-python.html
* _a11y_: accessibility https://en.wikipedia.org/wiki/Computer_accessibility
* _l10n_: language localization https://en.wikipedia.org/wiki/Language_localisation
* _Lokalise_: used at UM https://lokalise.com/automate-localization

## search

* _Algolia_: record (JSON obj) field (attr on obj) clients https://github.com/algolia/algoliasearch-client-javascript https://github.com/algolia/algoliasearch-client-python
* _Elasticsearch_: use in Postgres https://github.com/zombodb/zombodb alternative https://github.com/valeriansaliou/sonic https://github.com/paradedb/paradedb
* _Lucene_: framework https://stackoverflow.com/questions/15704644/difference-between-solr-and-lucene
* _Meilisearch_: https://github.com/meilisearch/MeiliSearch https://news.ycombinator.com/item?id=22685831 https://github.com/valeriansaliou/sonic https://softwareengineeringdaily.com/2019/03/20/elasticsearch-at-scale-with-volkan-yazici/ https://github.com/typesense/typesense https://news.ycombinator.com/item?id=25414389 https://tech.marksblogg.com/meilisearch-full-text-search.html https://tech.marksblogg.com/meilisearch-full-text-search.html https://www.revsys.com/tidbits/how-to-add-blazing-fast-search-to-your-django-site-with-meilisearch/
* _RediSearch_: built on Redis https://oss.redislabs.com/redisearch/
* _Redka_: Redis fork using SQLite https://github.com/nalgeon/redka
* _SeekStorm_: https://github.com/SeekStorm/SeekStorm https://news.ycombinator.com/item?id=42295792
* _Solr_: built on Lucene https://blog.codepen.io/2016/05/24/091-solr/
* _Typesense_: https://github.com/typesense/typesense https://xkcd-search.typesense.org/ https://www.thoughtworks.com/radar/tools?blipid=202203031
* _whoosh_: project is dead https://github.com/gyllstromk/Flask-WhooshAlchemy/issues/69 https://stackoverflow.com/a/53338666/6813490 
* _Zinc_: https://github.com/zinclabs/zinc
