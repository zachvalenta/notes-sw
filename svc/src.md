# ⛩️

## 参考

🔍 https://softwareengineering.stackexchange.com

## 进步

* _23_: 📙 Evans domain-driven
* _19_: URL shortener, Gitlab for CI

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

🗄️ `infra.md` IaC

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

### Actions

🗄️ `git.md` Pages
📜 https://docs.github.com/en/actions
🔬 https://github.com/GothenburgBitFactory/taskwarrior/actions

SEMANTICS
* _workflow_: collection of jobs (test|deploy|add label to issue) defined in `.github/workflows`; triggered by event|chron|API
* _job_: collection of steps
* _step_: user-defined action (script) https://docs.github.com/en/actions/about-github-actions/understanding-github-actions
> Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another. For example, you can have a step that builds your application followed by a step that tests the application that was built.
* _runner_: container in which steps are run
> A runner is a server that runs your workflows when they're triggered. Each runner can run a single job at a time.
* _action_: GH-defined extension
> An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task. Use an action to help reduce the amount of repetitive code that you write in your workflow files. An action can pull your Git repository from GitHub, set up the correct toolchain for your build environment, or set up the authentication to your cloud provider.

EVENTS
* properties: id, type, payload, actor (user that triggers), repo (where event happens)
* `CreateEvent`: branch|tag created https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows
* `GollumEvent`: wiki page created|updated https://docs.github.com/en/rest/using-the-rest-api/github-event-types?apiVersion=2022-11-28#gollumevent
* `IssueCommentEvent`: comment on issue|PR
* `IssuesEvent`: opened, edited, closed, assigned, labeled
* `PullRequestEvent`: opened, edited, closed, review_requested
* `PushEvent`: commits pushed to branch

---

* use on AWS https://github.com/CloudSnorkel/cdk-github-runners
telemetry https://github.com/catchpoint/workflow-telemetry-action/issues/39 https://blog.smidt.dev/posts/0003/
can manipulate tags, create releases in repo using CLI https://cli.github.com/manual/gh_release

TOOLING
* _act_: run locally https://github.com/nektos/act
* _gama_: https://github.com/termkit/gama

* linking https://blog.github.com/2011-10-12-introducing-issue-mentions/
* draft PR https://github.blog/2019-02-14-introducing-draft-pull-requests/
* https://hynek.me/articles/python-github-actions/
* https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow
* https://github.com/sdispater/mixology/blob/master/.github/workflows/tests.yml
* https://github.com/github/super-linter
* https://www.youtube.com/watch?v=E1OunoCyuhY
* https://news.ycombinator.com/item?id=30060765
* https://towardsdatascience.com/ultimate-ci-pipeline-for-all-of-your-python-projects-27f9019ea71a
* python https://brntn.me/blog/open-source-python-ci/
* https://github.com/carderne/postmodern-python/blob/main/.github/workflows/pr.yml

### Gitlab

💻 https://gitlab.com/zachvalenta/pre-commit-test.git 
📜 https://docs.gitlab.com/ee/ci/yaml/ https://docs.gitlab.com/ https://docs.gitlab.com/runner/

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

### hooks

GIT HOOKS 📜 https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks https://githooks.com/
* BYO https://stefaniemolin.com/articles/devx/pre-commit/hook-creation-guide/
* https://rdrn.me/postmodern-python/
* actions: client-side (commit, merge) server (push)
* file-system location: `.git/hooks` 
* ignore failed hooks w/ `git commit --no-verify` http://omerkatz.com/blog/2013/2/15/git-hooks-part-1-the-basics

PRE-COMMIT https://pre-commit.com https://github.com/pre-commit/pre-commit/issues https://gitlab.com/zachvalenta/pre-commit-test https://learndjango.com/tutorials/pre-commit-django
* bypass for commit: `git commit -m "your message" --no-verify`
* bypass for push: `git push --no-verify`
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

# 🧩 PROGRAMS

🗄️ `api.md`
📚
* Beck tidy first? https://www.youtube.com/watch?v=QN-azRUAToc
* Dibernardo 500 lines or less http://aosabook.org/en/index.html
* Fowler refactoring https://www.amazon.com/dp/0134757599/ https://registerspill.thorstenball.com/p/skin-shedding-code https://www.youtube.com/watch?v=ZsPDz_BGbtE https://www.youtube.com/watch?v=CjCJ76oZXTE
> Also, as a general rule, you can at any given time get away with changing more than you think. Introducing change is like pulling off a bandage: the pain is a memory almost as soon as you feel it. http://paulgraham.com/popular.html
* Kernighan/Pike practice of programming
* Lopes exercises in programming style
* Martin clean code https://qntm.org/clean https://www.youtube.com/watch?v=wf68VDObVX0 https://www.youtube.com/watch?v=RkxVB1eNdCc
* McConnell code complete
* Ousterhout https://www.amazon.com/Philosophy-Software-Design-2nd/dp/173210221X against uncle bob https://www.youtube.com/watch?v=k0kTux_YNHw shallow vs. deep https://lobste.rs/s/qpzubc/don_t_refactor_like_uncle_bob_please https://benhoyt.com/writings/python-api-design/ https://minds.md/zakirullin/cognitive https://news.ycombinator.com/item?id=42489645 https://news.ycombinator.com/item?id=42512063 🗄️ `psychology.md`

---

🔗 https://news.ycombinator.com/item?id=35813496
🗄
* `golang.md` za / design
* `python.md` za / design
* `sociology.md` linguistics
* `system.md` programs / paradigms

https://buttondown.com/hillelwayne/archive/stroustrups-rule/
https://borretti.me/article/language-pragmatics

COMMUNITY
> But the choice of a main programming language is the most important signaling behavior that a technology company can engage in. Tell me that you program in Java, and I believe you to be either serious or boring. In Ruby, and you are interested in building things quickly. In Clojure, and I think you are smart but wonder if you ship. In Python, and I trust you implicitly. In PHP, and we sigh together. In C++ or C, and I nod humbly. In C#, and I smile and assume we have nothing in common. In Fortran, and I ask to see your security clearance. These languages contain entire civilizations. - Ford what is code?
* Java developers have high pain tolerances https://news.ycombinator.com/item?id=25124513
> The wrong people like it. The programmers I admire most are not, on the whole, captivated by Java. http://www.paulgraham.com/javacover.html
> Language users do not miss conveniences that they have never had access to in the first place. Those few bi-cultural citizens who function in both Chinese-character and alphabetic worlds are aware of the advantages conferred by the alphabet, but even these people soon get used to the differences, which slip below the level of consciousness, unremarked and unlamented...in virtually every informatic context, from library card catalogs to everyday user's manuals, the relatively cumbersome Chinese writing system exerts a low-level but constant drag force on productivity 📝 Moser invisible writing

HOWTO
* development speed vs. execution speed https://bitfieldconsulting.com/golang/rust-vs-go
> One especially good groove to span is the one between tools and things made with them. For example, programming languages and applications are usually written by different people, and this is responsible for a lot of the worst flaws in programming languages. I think every language should be designed simultaneously with a large application written in it, the way C was with Unix. http://paulgraham.com/marginal.html
> Part of the problem here is social. Language designers like to write fast compilers. That's how they measure their skill. They think of the profiler as an add-on, at best. But in practice a good profiler may do more to improve the speed of actual programs written in the language than a compiler that generates fast code. Here, again, language designers are somewhat out of touch with their users. They do a really good job of solving slightly the wrong problem. http://paulgraham.com/popular.html
* expressive
> Large organizations have different aims from hackers. They want languages that are (believed to be) suitable for use by large teams of mediocre programmers-- languages with features that, like the speed limiters in U-Haul trucks, prevent fools from doing too much damage. Hackers don't like a language that talks down to them. Hackers just want power. http://www.paulgraham.com/javacover.html
* _feature creep_: adding more features vs. making existing features better https://twitter.com/random_walker/status/1182635589604171776
* increases headcount, not total users https://news.ycombinator.com/item?id=34567237
> Second, C has a tendency to be conservative, changing and growing very slowly. This is a feature, and one that is often undervalued by developers. (In fact, I’d personally like to see a future revision that makes the C language specification smaller and simpler, rather than accumulate more features.) - https://nullprogram.com/blog/2018/11/21/

SYSTEMS PROGRAMMING
* https://news.ycombinator.com/item?id=42406893
* languages: C, C++, Rust
* Golang for containers https://github.com/sablierapp/sablier
* things people write with: dbms, web server, compiler, shell https://drewdevault.com/2021/05/30/Come-build-your-project.html
* fuzzy definition http://willcrichton.net/notes/systems-programming/ https://news.ycombinator.com/item?id=35092049
* memory management now in favor http://esr.ibiblio.org/?p=7804
* is easy :) https://news.ycombinator.com/item?id=34566918
* https://drewdevault.com/2021/03/19/A-new-systems-language.html

https://entropicthoughts.com/practices-of-reliable-software-design
extensible https://pycon-archive.python.org/2024/schedule/presentation/78/index.html
* application boundaries https://morizbuesing.com/blog/greppability-code-metric/
* Richard Gabriel https://www.jwz.org/doc/worse-is-better.html https://bitfieldconsulting.com/posts/not-real-developer
> Simplicity beats even strict correctness, in this view: it’s better to be simple (and handle the easy 90% of cases in a nice way) than to be totally correct (and handle the awkward edge cases, at the expense of making the code much more complex).

## CLI/TUI

🗄
* `denv.md` Make
* `linux.md` http://gnu.ist.utl.pt/prep/standards/html_node/Command_002dLine-Interfaces.html
> I will finally note that Ken Thompson has a history of designs that look like minimal solutions to near problems but turn out to have an amazing quality of openness to the future, the capability to be improved. Unix is like this, of course. It makes me very cautious about supposing that any of the obvious annoyances in Go that look like future-blockers to me (like, say, the lack of generics) actually are. Because for that to be true, I’d have to be smarter than Ken, which is not an easy thing to believe. http://esr.ibiblio.org/?p=7745
* `python.md` Click, functions
* `serde.md`

24.12.11
* positional for one|two obvious args
* keyword for options

---

https://jvns.ca/blog/2024/11/26/terminal-rules/ https://news.ycombinator.com/item?id=42401011
https://danluu.com/cli-complexity/

TUI
* https://news.ycombinator.com/item?id=40273177
* _curses_: UNIX https://docs.python.org/3/howto/curses.html https://github.com/cmus/cmus 
* ncurses
* https://news.ycombinator.com/item?id=37418424
* TUI for bash https://github.com/charmbracelet/gum
* design https://www.micahlerner.com/2021/07/14/unix-shell-programming-the-next-50-years.html 🗣 Dan Luu https://borretti.me/article/shells-are-two-things extensions https://github.com/dotenvx/dotenvx/pull/426

CLI IMPL LANGUAGE
> use Rust for CLI and Python for business logic? https://github.com/chubin/wttr.in
* tracking user info https://www.visidata.org/blog/2021/usage-graphs/
> build modern CLI applications without worrying about user accounts, data storage and encryption https://github.com/charmbracelet/charm#charm-kv
* fuzzy find https://github.com/denisidoro/navi
* C: ✅ fast ❌ development speed
* Nim: ✅ distribution ❌ maturity https://ssalewski.de/nimprogramming.html
* Python: ✅ exploratory ❌ distribution
* Go: ✅ distribution, fast startup https://news.ycombinator.com/item?id=23319684 ❌ stdlib lib lib not good
* Rust: ✅ speed, Clap library https://news.ycombinator.com/item?id=23320411 better for cross platform https://cuchi.me/posts/go-vs-rust ❌ language itself

OPTIONS 🔗 http://www.catb.org/~esr/writings/taoup/html/ch10s05.html
* _short option_: single dash prefix + single letter e.g. `-y`
* _option set_: n short options e.g. `-baz` = `-b`, `a`, `z`
* _long option_: double dash prefix + word e.g. `--foo-bar`
* options with a value are separated by their option by a space or an `=`
* `--`: ends option processing.

INPUT https://news.ycombinator.com/item?id=31293032
* https://nullprogram.com/blog/2020/08/01/
* _flag_: hyphen e.g. `cmd --from here --to there`
* letter (`-h`) word (`--help`) https://www.youtube.com/watch?v=FOQHGz__OLs
* _arg_: no hypen `cmd here there`; less clear than flags bc have to remember which is src and which is target https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46

## dependency injection (DI)

---

https://github.com/hynek/svcs/ https://svcs.hynek.me/en/stable/ https://www.youtube.com/watch?v=d1elMD9WgpA

loose coupling https://www.youtube.com/watch?v=uWTvMCra-_Y

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
* https://github.com/google/gin-config https://calmcode.io/course/gin/intro-to-gin
* in Python https://io.made.com/dependency-injection-with-type-signatures-in-python/ + https://moltenframework.com/v0.7.3/index.html + https://github.com/ekiro/haps + https://github.com/Dobiasd/enterprython/blob/master/why_you_want_formal_dependency_injection_in_python_too.md https://pythonbytes.fm/episodes/show/112/don-t-use-the-greater-than-sign-in-programming
* _dependency inversion_: is this a separate thing https://minds.md/zakirullin/cognitive
* _inversion of control(IoC)_: you're not in charge of app control flow, only hooking into it https://www.baeldung.com/running-setup-logic-on-startup-in-spring example of IoC https://seddonym.me/2019/08/03/ioc-techniques/ https://softwareengineering.stackexchange.com/questions/205681/why-is-inversion-of-control-named-that-way https://stackoverflow.com/questions/3058/what-is-inversion-of-control https://engineering.snagajob.com/dont-like-dependency-injection-898de93dc8d3 https://stackoverflow.com/a/2465052/6813490 https://stackoverflow.com/a/51117857/6813490 https://stackoverflow.com/a/140655/6813490 https://www.objc.io/issues/11-android/dependency-injection-in-java/ https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ ❓ pull in class deps all in one place [Conery 287]
> What is the glue that holds Django together? As a beginner entering, there really is no obvious central object to inspect, extend, or modify. https://www.reddit.com/r/Python/comments/olech/is_django_considered_pythonic_now/

## design patterns

🧠 https://chatgpt.com/c/672144f0-fbfc-8004-98c0-2209def70bc0
🔍 https://github.com/DovAmir/awesome-design-patterns
📚
* Conery ch. 11/12
* Mak https://www.manning.com/books/software-design-in-python

---

* Gang of Four: composition over inheritance https://en.wikipedia.org/wiki/Design_Patterns
> They warn that the implementation of a subclass can become so bound up with the implementation of its parent class that any change in the parent's implementation will force the subclass to change. Furthermore, they claim that a way to avoid this is to inherit only from abstract classes—but then, they point out that there is minimal code reuse...using inheritance is recommended mainly when adding to the functionality of existing components, reusing most of the old code and adding relatively small amounts of new code. https://buttondown.com/hillelwayne/archive/when-to-prefer-inheritance-to-composition/

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

## domain driven

📚
* ✅ Evans domain-driven design https://github.com/nickgerace/gfold/pull/149/files
* Percival https://www.amazon.com/gp/product/1492052205 https://www.youtube.com/watch?v=niMybnzmzqc [1:15]

* beware ideas coming from the Java world https://www.infoq.com/presentations/8-lines-code-refactoring/
> Ubiquitous language, domain, bounded context, aggregate, event storming are all about problem space. They are meant to help us learn the insights about the domain and extract the boundaries. DDD enables developers, domain experts and business people to communicate effectively using a single, unified language. Rather than focusing on these problem space aspects of DDD, we tend to emphasise particular folder structures, services, repositories, and other solution space techniques. https://minds.md/zakirullin/cognitive

## DSLs

---

📙 https://www.manning.com/books/building-user-friendly-dsls

* lose tooling of general purpose language https://news.ycombinator.com/item?id=22375721
* https://news.ycombinator.com/item?id=41938819
* https://registerspill.thorstenball.com/p/joy-and-curiosity-12
* https://news.ycombinator.com/item?id=41931507

ABSTRACTION
* https://jesseduffield.com/Beginners-Guide-To-Abstraction/
* howto https://tonsky.me/blog/dsl/
* against abstraction https://thorstenball.com/blog/2015/10/22/write-stupid-code/
* _law of leaky abstractions_: natch; if they wouldn't exist in the first place https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/

## paradigms

* use greppable names https://registerspill.thorstenball.com/p/use-data-that-looks-like-data
* write code that's easy to throw away
> Write code to be changed and/or deleted. This comes from someone who's worked in startups for the past 5 years. We often overestimate how long code =is supposed to live. We as programmers often exaggerate with our DRY and stuff, we do not want to repeat ourselves, we want to find another abstraction...we want to find some general that can help us abstract stuff away. My piece of advice is that, step back and consider for a moment that this code is not going to stay in, so maybe only try and find the abstraction layer once you really sure that this is how it's going to be. - Thorsten Ball https://developeronfire.com/podcast/episode-373-thorsten-ball-interpreters-compilers-and-writing https://news.ycombinator.com/item?id=41968409

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

## functional

📚
* Granin https://www.manning.com/books/functional-design-and-architecture
* ⭐️ Normand https://www.amazon.com/dp/1617296201 https://www.manning.com/books/grokking-simplicity
* Martin https://www.amazon.com/gp/product/0138176396

---

method chaining https://calmcode.io/course/method-chains/introduction
https://danluu.com/butler-lampson-1999/
https://us.pycon.org/2024/schedule/presentation/86/index.html
https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell
https://bytes.yingw787.com/posts/2018/11/07/data_driven_testing

FUNCTIONAL 📙 Conery https://github.com/hemanth/functional-programming-jargon
* _functional_: function that operates on other functions https://stackoverflow.com/a/94056
* as design: pure, uses higher-order
* _higher-order function_: takes func as arg or return func https://www.fluentpython.com/lingo/
* e.g. decorators, closures, lambdas
* _first-class function_: https://www.fluentpython.com/lingo/#first-class_function
* _y combinator_: https://www.youtube.com/watch?v=QuXJ3kXUCiU
* _curry_: break down larger function into smaller and chaining them together 📙 Conery [291,302]
> diff to closure? https://stackoverflow.com/questions/62499789/racket-closure-currying-where-is-the-difference#62500425 🗄 `python.md` partial https://www.youtube.com/watch?v=kZlOy1BY6lY

* _none_: https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/
* _pure_: no side effects
* _side effect_: IO, mutation
* _functor_: func that iterates over things that are iterable [Conery 307]
* _monad_: functor iterates, monad does logic [Conery 307]
* wraps control flow https://bytes.yingw787.com/posts/2019/12/06/monads/ https://samgrayson.me/2019-08-06-monads-as-a-programming-pattern/ https://lukeplant.me.uk/blog/posts/understanding-monads-via-python-list-comprehensions/ https://rbtcollins.wordpress.com/2018/08/26/monads-and-python/

https://github.com/dry-python/returns Land of Lisp epilogue https://docs.python.org/3/howto/functional.html https://kite.com/blog/python/functional-programming https://stackoverflow.com/q/1017621/6813490 https://treyhunner.com/2018/09/stop-writing-lambda-expressions/ https://blog.cleancoder.com/uncle-bob/2014/11/24/FPvsOO.html https://julien.danjou.info/python-and-functional-programming/ https://sumit-ghosh.com/articles/demystifying-decorators-python/ https://jrsinclair.com/articles/2019/what-i-wish-someone-had-explained-about-functional-programming/ https://codewords.recurse.com/issues/one/an-introduction-to-functional-programming http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html https://blog.cleancoder.com/uncle-bob/2017/07/11/PragmaticFunctionalProgramming.html

## object-oriented

📙 Bugayenko elegant obj https://www.elegantobjects.org/

https://hynek.me/talks/subclassing/
SOLID https://realpython.com/solid-principles-python/

OBJECTS
* _object_: vs. procedural 📙 Evans domain-driven [51]
* _object model_: how objs work in a language 📙 Ramalho [15]
* aka "data model" in Python
* BYO http://aosabook.org/en/500L/a-simple-object-model.html
* _class_: lang ft. that allows defining new types 📙 Ramalho https://www.fluentpython.com/lingo/#class
* _metaobject_: objs that form core of object model 📙 Ramalho [16]
* _attribute_: obj property i.e. field (data) or method (action) https://docs.python.org/dev/tutorial/classes.html
* _attribute reference_: access obj attr https://docs.python.org/dev/tutorial/classes.html#class-objects

INHERITANCE
* _inheritance_: subclass is an instance of parent class
> I use Django a lot and generally it's great. But I hate that you can't follow your code paths from start to finish on the surface. You have to know about how it works underneath. Meaning you can't just be a python + web server expert. You have to also be a Django expert. So I get non-Django experts reviewing code and they have no clue why things work or break. Just an opinion. Not saying this is objectively wrong. https://news.ycombinator.com/item?id=17728821

ZA
* _constant_: variable w/ hard-coded value
* _enumeration_: group of discrete constants https://realpython.com/python-enum/
* _member_: constant in enum

---

* _hierarchical_: 1 parent - 1 child
* _multi-level_: 1 grandparent - 1 parent - 1 child
* _multiple_: n parents - 1 child
* aka interfaces in Java, mixins in Python
* _polymorphism_: https://confuzeus.com/hub/django-web-framework/model-polymorphism/ https://news.ycombinator.com/item?id=27658706 re: duck typing https://www.fluentpython.com/lingo/#duck_typing
* _diamond problem_: https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem Python solves w/ MRO https://stackoverflow.com/a/44535084/6813490
* _Liskov_: every instance of a subclass (in this case, my extension of Thread) needs to remain a valid instance of the superclass
* _abstract class_: not instantiated; TwoDimensionalShape(Circle, Square, Triangle)
* _Law of Demeter_: don't reach through one object to get to another [Conery 278]

OPINIONS
* Golang https://blog.gypsydave5.com/posts/2024/4/12/go-is-an-object-oriented-programming-language/
* Smalltalk https://news.ycombinator.com/item?id=34137751 https://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html
* http://www.smashcompany.com/technology/object-oriented-programming-is-an-expensive-disaster-which-must-end
* creates confusion
> In 2003, Jane Street began a rewrite of its core trading systems in Java. The rewrite was eventually abandoned, in part because the resulting code was too difficult to read and reason about...we built up a nest of classes that left people scratching their heads when they wanted to understand just what piece of code was actually being invoked when a given method was called. https://queue.acm.org/detail.cfm?id=2038036
> The price is that the resulting code is bloated with protocols and full of duplication. This is not too high a price for big companies, because their software is probably going to be bloated and full of duplication anyway. http://www.paulgraham.com/noop.html

---

* quadratic complexity
* _composition_:
* CUPID https://dannorth.net/2022/02/10/cupid-for-joyful-coding/
* _delegation_: composition by another name https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/#delegation-in-oop
* https://www.thedigitalcatonline.com/blog/2020/08/17/delegation-composition-and-inheritance-in-object-oriented-programming/

* _information hiding_: obj as black box against which you can ask for stuff but you don't know how it's going on inside [Connolly database systems 25.3.1 814]
* _override_: replace method inherited from parent
* _history_: 1970s Smalltalk https://news.ycombinator.com/item?id=29890205 1990s Java https://twobithistory.org/2019/01/31/simula.html https://medium.com/javascript-scene/the-forgotten-history-of-oop-88d71b9b2d9f https://www.hillelwayne.com/post/alan-kay/ https://www.youtube.com/watch?v=QyJZzq0v7Z4

__static methods__
* _static_: belongs to class, not an individual instance
* something that won't change across instances 📍 example
* code organization https://stackoverflow.com/a/14085311/6813490
* bad for testing? https://stackoverflow.com/a/2671938/6813490

opinions
* tell, don't ask [Conery 276]
* unlearn OOP https://dpc.pw/the-faster-you-unlearn-oop-the-better-for-you-and-your-software
* Hickey https://www.youtube.com/watch?v=oytL881p-nQ

method chaining https://www.youtube.com/watch?v=BY34Fe-2xgk
* used in SQL query builders [2:45]
```python
class Player:
    def __init__(self, sh_per=0.40):
        self.points = 0
        self.fatigue = 0
        self.shooting_per = sh_per
    
    def shoot(self):
        self.points += 2.0 * self.shooting_per
        self.fatigue += 1
        return self

    def stats(self):
        print(f"pts {self.points} fatigue {self.fatigue}")
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
* _hook_: response to event e.g. db trigger
* aka event handler, callback 📙 Chacon [402] https://stackoverflow.com/a/11087727
* _webhook_: res/ack (vs. req/res); 3rd streams > 1st polls https://sendgrid.com/blog/whats-webhook
* route known as "receiver" https://adamj.eu/tech/2021/05/09/how-to-build-a-webhook-receiver-in-django/
* further considerations https://brandur.org/webhooks https://www.svix.com/blog/webhooks-are-harder-than-they-seem/

---

* more domain-driven https://www.youtube.com/watch?v=72V-5hrilv0
* _extract_: separate [Fowler https://refactoring.com/catalog/]
* _inline_: combine
> Inlining is the concept of replacing a function call in a program with the contents of the function itself, thus avoiding the call. https://golangweekly.com/issues/470

* CRD DDD 🗄 notebook 22.12.13
* DRY, single responsibility https://news.ycombinator.com/item?id=35151088

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

## frameworks

🗄 `python/core.md` functions > metaprogramming

> Web development is often broad, not deep - problems span many domains. https://docs.djangoproject.com/en/2.0/intro/whatsnext/
> A framework is a text where you fill in the blanks. The framework defines the grammar, you bring some of the words. https://blog.startifact.com/posts/framework-patterns.html

* components: HTTP, routes, ORM
* _Rails_: still the best
> It's productive, it's fast enough, it scales just fine, and perhaps most importantly there's a "right" way to do just about everything your web application will ever need to do: background jobs, websockets, read-only database replicas. https://news.ycombinator.com/item?id=42014906

---

Django vs. Rails https://news.ycombinator.com/item?id=42388340
https://github.com/CrocoFactory/sensei

BYO
* https://itsthejoker.github.io/spiderweb-the-tiny-web-framework/ https://www.destroyallsoftware.com/screencasts/catalog https://www.youtube.com/watch?v=7kwnjoAJ2HQ https://testdriven.io/courses/python-web-framework/ https://www.amazon.com/dp/1937785637 https://rubyonrails.org/doctrine/ https://github.com/itsthejoker/spiderweb/ https://github.com/iklobato/LightAPI https://news.ycombinator.com/item?id=41914544 https://dev.to/brunociccarino/how-i-wrote-express-go-in-19-hours-3ndh https://blog.dimitarandreev.com/posts/writing-an-http-router-for-aws-lambda-functions-from-scratch-with-go/

## checklist / scaffold

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

## internationalization (i18n)

* https://phrase.com/blog/posts/internationalization-i18n-go/
* examples: Odoo, https://github.com/jesseduffield/lazygit/tree/master/pkg/i18n
* _a11y_: accessibility https://en.wikipedia.org/wiki/Computer_accessibility
* _l10n_: language localization https://en.wikipedia.org/wiki/Language_localisation
* _Lokalise_: used at UM https://lokalise.com/automate-localization
