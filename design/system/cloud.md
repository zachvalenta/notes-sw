# ⛩️

## 参考

🔍 https://softwarerecs.stackexchange.com
🗄️
* `aws.md`
* `system.md` factors

## 进步

* https://simonwillison.net/2025/May/17/django-simple-deploy/
* Docker / Kamal/ IaaS https://www.youtube.com/watch?v=fuZoxuBiL9o https://www.youtube.com/watch?v=F-9KWQByeU0 https://www.youtube.com/watch?v=7lkJmElHkSw https://www.youtube.com/watch?v=DmbBgXK8M5M

* _20_: Heroku (simple Django app)
* _18_: Cloud Foundry and AMQP/Spring for Dark Canary
* _17_: try out Terraform and AWS for Comcast interview

# 🧮 IaC

🗄️ `src.md` CICD

---

> In the bad old days, managing configuration on servers and networks was anarchy, but anarchy made of a lot of largely non-portable and incorrect shell scripts. Every company just cobbled together some bespoke tools...the problem is, you can build a machine with a shell script, but then what? If you make manual changes to the server, and then forget about them, there’s no automated way to revert them. And you can't easily roll out a single change to a big farm of heterogeneous machines, all with different operating systems and software versions, in a safe and repeatable way. - re: Puppet https://bitfieldconsulting.com/posts/not-real-developer

https://roadmap.sh/linux
* SQL https://news.ycombinator.com/item?id=28554089
* Ansible-like (Puppet, Chef, Salt)
* https://github.com/Fizzadar/pyinfra https://www.pythonpodcast.com/pyinfra-configuration-management-episode-270/
* http://scriptedconfiguration.org/ https://github.com/comtrya/comtrya https://www.youtube.com/watch?v=TNlDSG1iDW8
* _CloudFormation_: deployment
* _config mgmt_: provision server remotely

REMOTE EXECUTION 🗄️ `python/stdlib.md` process exec
* _Capistrano_: https://capistranorb.com/ https://kamal-deploy.org/ https://blog.codepen.io/2014/02/22/002-servers/ https://www.digitalocean.com/community/tutorials/how-to-use-capistrano-to-automate-deployments-getting-started
* _Fabric_: run script on server over SSH and get Python response obj back; apparently not meant for fully-fledged config mgmt https://stackoverflow.com/questions/39370364/when-to-use-fabric-or-ansible but can/could be used with Ansible (article doesn't explain why not just use Ansible and is undated) https://www.blog.pythonlibrary.org/2024/10/16/ssh-scripting-with-fabric-and-python/
* _Paramiko_: https://github.com/paramiko/paramiko https://github.com/zachvalenta/capp-edi
* _Ruroco_: https://github.com/beac0n/ruroco

## Ansible

🗄 `system.md` config
🧪 https://github.com/zachvalenta/ansible-hello-word-macos
📺
* https://www.youtube.com/playlist?list=PL2_OBreMn7FqZkvMYt6ATmgC0KAGGJNAN
* https://news.ycombinator.com/item?id=37331212
* https://www.ansiblefordevops.com/
* https://serversforhackers.com/s/ansible

* Mitogen: make Ansible fast https://mitogen.networkgenomics.com/ansible_detailed.html
* alternative https://news.ycombinator.com/item?id=40211655 https://pyinfra.com/

semantics
* _control_: controls execution
* needs Linux, Python https://docs.ansible.com/ansible/latest/dev_guide/developing_locally.html#modules-and-plugins-what-s-the-difference
* _worker_: SSH into remote and run plays for control node
* _target_: runs plays
* agentless i.e. don't need anything Ansible-related installed
* _Tower_: PaaS layer (perms, credentials, notifications, scheduling, API, reporting); makes secrets easy, just encrypt using Tower and then you can store encrypted secrets files in your repo and when playbooks in repo run by Tower it will use private key to decrypt (assume it figures out which pk to use via repo/project metadata referenced when encrypting)
* _inventory_: list of all remotes
* _play_: task (install app, start service)
* _playbook_: list of plays; linter https://github.com/ansible/ansible-lint `ansible-playbook -c local` run playbook in cwd and run against localhost ❓ `-i` in Ryan's Makefile
* _plugin_: extends Ansible, executes on control node https://docs.ansible.com/ansible/latest/dev_guide/developing_locally.html#modules-and-plugins-what-s-the-difference
* _module_: impl of play, executes on target node; e.g. `ansible -m setup`; BYO https://www.youtube.com/watch?v=nyXDR4RG4A8

todo
* go through https://github.com/KeyboardInterrupt/awesome-ansible
* _infra for testing_: why use Vagrant? possible to use Docker? can you follow his course just using localhost? https://www.youtube.com/watch?v=goclfp6a2IQ
* _with other tools_: why use Ansible with Terraform? https://www.youtube.com/watch?v=-gKTeT3BgHE https://www.hashicorp.com/resources/ansible-terraform-better-together https://github.com/adammck/terraform-inventory Fabric https://realpython.com/automating-django-deployments-with-fabric-and-ansible

inventory
* will use from cwd if present and otherwise fall back to
* fmt: can be INI or YAML https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#inventory-basics-formats-hosts-and-groups 
* create groups https://buildvirtual.net/creating-a-simple-ansible-playbook/

config
* _config_: tells you where inventory is
* _locations_: installed via pipx so just using config per project for now https://stackoverflow.com/q/21958727 https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg
* Pyhton interpreter https://docs.ansible.com/ansible/latest/reference_appendices/interpreter_discovery.html

plugins 
* docs https://docs.ansible.com/ansible/latest/plugins/plugins.html
* output https://www.youtube.com/watch?v=VfrSCz_5yjg https://github.com/dodevops/ansible-teamcity-callback https://www.jeffgeerling.com/blog/2018/use-ansibles-yaml-callback-plugin-better-cli-experience
* post https://stackoverflow.com/questions/30509058/post-json-to-api-via-ansible
* _conf_: in ansible.cfg? https://github.com/search?p=5&q=callback_whitelist+filename%3Aansible.cfg&type=Code https://termlen0.github.io/2019/11/16/observations/
```conf
# pass args
[ur_plugin]
team = foo_team
```
```py
# map args to Python module's namespace

# reference
```

```conf
[defaults]
inventory      = ~/Desktop/proj/inventory.yml
```

run locally
* local_action https://www.educba.com/ansible-local_action/
* from playbook, from shell https://www.shellhacks.com/ansible-localhost-run-playbook-locally-local-command/ https://www.middlewareinventory.com/blog/run-ansible-playbook-locally/
* all options, best practices https://gist.github.com/alces/caa3e7e5f46f9595f715f0f55eef65c1
* specify inventory from config https://www.rogerperkin.co.uk/network-automation/ansible/inventory-file/
```yml
localhost              ansible_connection=local
```
```sh
$ ansible -m ping all
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```

## Copilot

https://testdriven.io/blog/django-ecs-aws-copilot/

## Sake

https://github.com/alajmo/sake

## Terraform

🛣️ https://roadmap.sh/terraform
📙 https://www.manning.com/books/terraform-in-depth

SEMANTICS
> generates a dependency graph of resources, runs against provider, walks resource graph and ensures that resources are configured
* _provider_: AWS, Azure, et al.
* _resource_: provider's infra
* _variable_: your data
* _data_: provider data
* _output_: attributes provider gives back

ZA
* _pulumi_: Python alternative https://github.com/pulumi/pulumi https://leebriggs.co.uk/

---

Zoro https://spacelift.io/ https://terragrunt.gruntwork.io/
> An analysis of Redis' source code repository also shows that a sizable percentage of contributions to the DBMS comes from outside the company (e.g., Tencent, Alibaba). This "stolen valor" was the reason for the ire HashiCorp received when they changed Terraform's license in 2023. https://www.cs.cmu.edu/~pavlo/blog/2025/01/2024-databases-retrospective.html

* https://github.com/idoavrah/terraform-tui
* https://github.com/magodo/pipeform
* https://github.com/leg100/pug
* certification https://www.hashicorp.com/certification
* alternative https://opentofu.org/
* `tf -plan`
* CLI to query https://github.com/mazen160/tfquery
* security scan https://github.com/tfsec/tfsec
* get cost estimate https://www.infracost.io/
* use languages other than HCL https://www.terraform.io/cdktf https://www.thoughtworks.com/radar/tools?blipid=202203047
* test config https://github.com/open-policy-agent/conftest https://www.thoughtworks.com/radar/tools?blipid=202110014

* Terraform https://github.com/tfutils/tfenv https://github.com/warrensbox/terraform-switcher
* alternatives https://news.ycombinator.com/item?id=3405132
📜 [ur-list](https://github.com/shuaibiyy/awesome-terraform)

* _sink_: https://grahamlyons.com/article/a-zero-fricton-terraform-primer
* _install_: spring 2019 tried to use Homebrew but no luck (`tf-brew.log`), then seemed like I downloaded binary into project folder (`/Users/zach/Desktop/home/kaifa/SDLC/6_IaC/terraform`), then created symlink in `usb/bin` (using `sudo`!?!), which I presume is no longer there as a result of upgrading to Mojave (`installs/terraform/tf-path.log`), I still had the binary lying around inside `assets-digital/installs/terraform` but deleted it -> official docs and [some tutorials](https://grahamlyons.com/article/a-zero-fricton-terraform-primer) say to install binary, [others to use Homebrew](https://developers.cloudflare.com/terraform/getting-started/installing/) and Bellavance does mention using Chocolatey, I tried Homebrew

how to use IRL
> We have a strict policy where everything (creating, updating or deleting) should be done through Terraform and the AWS console should be used as a read-only dashboard...We have alerting setup for any action that is performed in our AWS accounts that was done through the console...we're looking to move to an automated environment such as Atlantis or Terraform Enterprise later this year. + how to keep everything in sync https://news.ycombinator.com/item?id=19360031

* _components_: runtime + config (`.tf`) + storage (`.tfstate`) + secrets (`.tfvars` w/ `-var-file=path`)
* _variables_: types (string, list, map) precedence (CLI > file > hard-coded)

directory structure
```sh
├── dir
│   └── my_conf.tf  # tf cmd will include any .tf files in $CWD unless `.ignore` extension
│   └── terraform.state  # locked when in use, need to store in repo
```

* keeps track of state via `.tfstate`, can also refresh from provider, looks at state then config and then says "right, what do I need to do to state to make it like the dependency graph I've generated from the config file?"
* generate config from existing AWS resources https://former2.com/

commands
* _terraform_: help
* _init_: install plug-in for provider into `.terraform` in `$CWD`
* _plan_: generate dependency graph for resources
* _apply_: `plan` + deploy
* _destroy_: preview w/ `plan -destroy`

config
* _variable_: data
* _provider_: AWS, Azure, et al.; BYO https://vincent.composieux.fr/article/create-a-provider-plugin-for-terraform/
* _resource_: EC2, S3, et al. + _provisioner_ (code block to do something to resource)
* _output_: pipe elsewhere

# 🚢 PaaS

https://www.contraption.co/a-mini-data-center/ https://hatchbox.io/

DESIGN
> Features: Automatic scaling, continuous deployment, and integration with development tools.
* simplicity
> With something like Heroku, you can have multiple VM's in staging and production, w/ a deployment pipeline that supports rollbacks, monitoring, alerting, autoscaling, all in a managed environment w/ a managed, highly available Postgres setup, with very little effort and 0 maintenance. This is what I've setup at my current startup. My last company was on K8's and I loved it - but this is nearly as good and requires literally no maintenance and far less expertise / setup. https://news.ycombinator.com/item?id=22493873 
* built on larger cloud providers e.g. Heroku dyno just VM running on top of EC2 instance https://stackoverflow.com/questions/21462439/what-exactly-is-a-single-heroku-web-dyno
* pricey if you're moving lots of data
* can serve lots of traffic for not so much e.g. 4M req/month for $700 https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around
* deployment analogous to `docker-compose.yml` https://www.mattlayman.com/blog/2019/web-development-environments/
```Procfile
web: ./manage.py runserver
worker: celery worker --app new_hot_thing:celeryapp --loglevel info
frontend: webpack --watch
```

## CF

misc
* _architecture_: DEA (Ruby) Diego (Go) https://docs.cloudfoundry.org/concepts/diego/dea-vs-diego.html
* _healthchecks_: https://stackoverflow.com/questions/39736774/health-check-in-cloud-foundry https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html
* _history_: 2009 (acquired by SpringSource, itself acquired by VMware in 2009) 2011 (public launch)
* `runtime.txt`: specify runtime for Python https://docs.cloudfoundry.org/buildpacks/python/index.html
* _task_: akin to cronjob https://docs.cloudfoundry.org/devguide/using-tasks.html

Pivotal
* _Cloud Foundry_: the software
* _Pivotal Cloud Foundry_: enterprise version
* _Pivotal Web Services_: hosted environment for PCF
* _Cloud Foundry Foundation_: drive adoption to prevent AWS from taking over 😀
* _droplet_: app + dependencies

terms
* _Apps Manager_: GUI
* _pool_: 类似 AWS region ➡️ `AP`
* _lane_: 类似 AWS availability zone ➡️ `AP-3b`
* _org_: account ➡️ `AP-3b FooTeam`
* _space_: namespace within pool/lane owned by org ➡️ `AP-3b FooTeam DEV`

services
* _binding_: service credentials [delivered automatically to app](https://docs.cloudfoundry.org/devguide/services/#application-binding)
* if service listed in `manifest.yml` and service does not exist in CF, app will push but won't start
* _VCAP SERVICES_: JSON of connected services https://banck.net/2014/12/deploying-a-django-application-to-cloud-foundry/

cmds
* login: `login -a <url>`
* switch endpoints: `api <url>`
* view apps in pool: `apps`
* env var for app: `env <app>`
* tail logs: `logs <app>`
* dump logs: `logs <app> --recent`

db setup
* create dedicated db svc
* create db cluster
* create db _in_ cluster
* bind svc to db
* `cf push` app that will need the db

instances
* [kill specific instance](https://stackoverflow.com/a/39241780/6813490)
* [get instance GUID](https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html#CF-INSTANCE-GUID)
* [route request to specific instance](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#surgical-routing)
* [start instances in order](https://stackoverflow.com/a/49417497/6813490)

__app boot__

start command https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html
* https://docs.cloudfoundry.org/buildpacks/prod-server.html
* the console will show you the complete start command on the 'settings' page
* args provided by CLI trump `maninfest.yml`

semantics
* _buildpack_: 
* _droplet_: 
* _Procfile_: Ruby version of `docker-compose.yml` https://github.com/DarthSim/overmind

request flow
> if service listed in `manifest.yml` but nonexistant in CF, app won't start
* app binds to route
* create buildpack (`.profile.d`) https://news.ycombinator.com/item?id=28468660
* create droplet
* hooks (`.profile`)
* start (`Procfile`)

__routes__

create route
* _automatic_: CF creates route based on app name/pool and maps route to application on `cf push`
* _custom_: use `manifest.yml` or CLI (`create-route`, `map-route`)
* `manifest.yml` can create routes, but it will not remove previously mapped routes
* can create random route using `cf push <app> --random-route`
* `map-route` runs `create-route` as first step of its own execution so in practice you really only need to use `map-route`; same thing for `delete-route` and `unmap-route`

* commands
```sh
# associate route w/ *space*
create-route <space> <domain> --hostname

# associate route w/ *app*
map-route <app> <domain> --hostname

# rm route and its associations
delete-route <domain> --hostname
```

gotchas
* Gorouter does not use a route until route is _mapped_ to an app; if route created but unmapped, [Gorouter serves 404](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html)
* you probably have more routes than are visible from Apps Manager; view using `cf routes`
* if you don't explicitly create a route and map it to your application, CF will make the route combining `app-name` and `domain` and `pool-info`
* routes must be unique, even across spaces
> The URL for your app must be unique from other apps hosted by Cloud Foundry - https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html
> Routes are globally unique. Developers in one space cannot create a route with the same URL as developers in another space, regardless of which orgs control these spaces. - https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#routes

request flow
* client ➡️ Gorouter ➡️ route service ➡️ app
* _Gorouter_: routes w/in pool to app instances via round-robin
* _route service_: handles rate limiting, caching; find app instance using `X-CF-Forwarded-Url` header

## fly.io

> you have account tied to personal Github https://github.com/settings/connections/applications/Iv1.6b93b0cce72780ec

* _Fly.io_: 🎯 https://www.youtube.com/watch?v=0eP98xkLj9w https://django-simple-deploy.readthedocs.io/en/latest/

---

ALTERNATIVES https://testdriven.io/blog/heroku-alternatives/
* _Coolify_: https://coolify.io/ https://mkennedy.codes/posts/opposite-of-cloud-native-is-stack-native/ https://github.com/trailbaseio/trailbase
* _Firebase_: https://tinyprojects.dev/projects/tiny_website
* _Knative_: https://knative.dev/docs/ https://mkennedy.codes/posts/opposite-of-cloud-native-is-stack-native/
* _Netlify_: https://www.netlify.com/
* _Render_: https://dashboard.render.com/
* metabase deploy failed bc free-tier instance didn't have enough memory https://dashboard.render.com/project/prj-ct4ro05umphs73e7nfjg
* _PythonAnywhere_: https://www.pythonanywhere.com/
* _Railway_: https://railway.app/ https://docs.railway.app/guides/gin
* _Sidekick_: 🎯 https://github.com/MightyMoud/sidekick https://news.ycombinator.com/item?id=41591018
* _sst_: 🎯 https://sst.dev/
* _Supabase_: https://supabase.com/ https://www.youtube.com/watch?v=wa9-d63velk https://news.ycombinator.com/item?id=43763225
* _Tau_: https://github.com/taubyte/tau
* _Vercel_: https://zackproser.com/blog/maintaining-this-site-no-longer-fucking-sucks

## oxide

https://oxide.computer/
https://simonwillison.net/2025/Jan/10/ai-predictions/
https://www.mattkeeter.com/about/
https://cba.mit.edu/

## platform.sh

* _Platform.sh_: https://platform.sh/ https://django-simple-deploy.readthedocs.io/en/latest/

## pico

https://pico.sh/

## railyway

> you have account tied to personal Github

https://railway.com/

## Python Anywhere

https://www.pythonanywhere.com/

## Val Town

https://www.val.town/
https://www.val.town/v/mikker/dailySlackRoundup
https://www.geoffreylitt.com/2025/04/12/how-i-made-a-useful-ai-assistant-with-one-sqlite-table-and-a-handful-of-cron-jobs
https://www.geoffreylitt.com/2023/12/17/seven-books-that-stuck-with-me-in-2023

# 🏡 SELF HOST

🗄️ `it.md` home lab

CONSIDERATIONS
* data locality restrictions re: geography https://signoz.io/ https://danluu.com/simple-architectures/
* ability to move to best price https://news.ycombinator.com/item?id=42269059

---

* https://news.ycombinator.com/item?id=34860655
* https://news.ycombinator.com/item?id=34867314
* https://www.jotaen.net/anA6o/self-hosting-guide-docker-haproxy-lets-encrypt/
* https://knhash.in/gentle-guide-to-self-hosting/
* https://news.ycombinator.com/item?id=27674726
* https://github.com/tiagoad/docker-homeserver
* https://world.hey.com/dhh/why-we-re-leaving-the-cloud-654b47e0
* https://world.hey.com/dhh/the-big-cloud-exit-faq-20274010 https://www.reddit.com/r/programming/comments/y7zz2u/dhh_why_we_are_leaving_the_cloud/
* https://world.hey.com/dhh/our-cloud-exit-savings-will-now-top-ten-million-over-five-years-c7d9b5bd
* https://thenewstack.io/why-companies-are-ditching-the-cloud-the-rise-of-cloud-repatriation/
* https://meta.stackexchange.com/questions/404231/we-re-finally-going-to-the-cloud

## Dokku

* _Dokku_: 🎯 https://github.com/dokku/dokku https://dokku.com/ https://github.com/ankane/blazer https://blazer.dokkuapp.com/

## Kamal

* _Kamal_: 🎯 https://kamal-deploy.org/ https://www.youtube.com/watch?v=7lkJmElHkSw
> Rare opening to join our excellent ops team. Help us run Basecamp, HEY, and the heritage suite of apps on our own hardware with Kamal, MySQL, ElasticSearch, Prometheus, Grafana, KVM, Chef. https://x.com/dhh/status/1848544864436162705

```txt
Service Model: Deployment tool facilitating application deployment across various environments.
Target Users: Developers and teams seeking to deploy containerized applications to multiple servers or cloud providers.
Features: Zero-downtime deployments, compatibility with bare-metal servers and cloud VMs, and management of containerized services.
```

## Piku

* _Piku_: 🎯 6k https://github.com/piku/piku

## Ubicloud

https://www.ubicloud.com/blog/debugging-hetzner-uncovering-failures-with-powerstat-sensors-and-dmidecode

# 🟨 ZA

## stack native

📙 https://talkpython.fm/books/python-in-production#read-online

TAXONOMY 🧠 https://chatgpt.com/c/673a5946-7948-8004-9a56-e3b60009dccd https://mkennedy.codes/posts/opposite-of-cloud-native-is-stack-native/
> hyperscale https://blog.jetbrains.com/pycharm/2024/12/the-state-of-python/#trend-6-most-python-web-apps-run-on-hyperscale-clouds
* _cloud-native_: dependent on cloud services
* _lift-and-shift_: on-prem but on a dumb cloud instance
> Did you have one huge server in the office? Well, now you get one huge server in AWS EC2 and copy your app to it. You’ll also pay extreme prices for that privilege.
* _stack-native_: on-prem but on a smart cloud instance
> Here’s the crazy part. All of our infrastructure is running on one medium-sized server in a US-based data center from Hetzner. We have a single 8 CPU / 16 GB RAM server that we partition up across 17 apps and databases using docker. Most of these apps are as simple or simpler than the stack-native diagram above. For this entire setup, including bandwidth, we pay $65/month. That’s $25/mo for the server and another $40 for bandwidth. I just finished doing some tentative load testing using the amazing Locust.io framework. At its peak, this setup running Nginx + Granian + Python + Pyramid + MongoDB would handle over 100M Python requests / month. For $25. In contrast, what would this setup cost in AWS? Well, the server is about $205 / month. The bandwidth out of that server is another $100/mo. If we put all our bandwidth through AWS (for example mp3s and videos through S3) the price jumps up by another whopping $921. This brings the total to $1,226/mo. The contrast is stark. If we chose cloud-native, we’d be tied into cloud-front, EKS, S3, EC2, etc. That’s the way you use the cloud, you noobie. Let’ the company cover the monthly costs. But stack-native can move. We can run it in Digital Ocean for a few years as we did. When a company like Hetzner opens a data center in the US with 1/6th pricing, we can take our setup and move. The hardest part of this is Let’s Encrypt and DNS. There is nearly zero lock-in.

## cost control

📙 Vandeput https://www.manning.com/books/demand-forecasting-best-practices

SVC
* _Budgets_: set alerts for spend/underusage https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html
* can also set alarms in CloudWatch 📹 Brown ccp [1:43:30]
* _Trusted Advisor_: inspect your env, give recs https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html https://us-east-1.console.aws.amazon.com/trustedadvisor

ZA
* why cloud: metered billing, flexibility, cost
* free tier available for n months for certain svc
* some svc default to large node size e.g. ElasticCache 📹 Brown ccp [1:33:00]
* sometimes get refunded for misspend 📹 Brown ccp [1:34:00]
* _metered billing_: pay for what you use (vs. fixed costs) 📹 Brown ccp [1:31:15]
* autoscaling is overrated
> You won't need it to spin instances up and down based on utilization. Unless your profit margins are as thin as Amazon's, what you need instead is abundant capacity headroom. Permanently. Then you can sleep well at night - unlike Amazon's oncall engineers. https://x.com/dvassallo/status/1154516910265884672

---

* https://world.hey.com/dhh/five-values-guiding-our-cloud-exit-638add47
* _benefits_: cost (sometimes) scalability (most times) geographic DR (nearly always)
* _consultants_: https://aws.amazon.com/iq/ https://www.gruntwork.io/
* _cost control_: https://aws.amazon.com/aws-cost-management/aws-cost-explorer/ https://www.lastweekinaws.com/ https://github.com/mlabouardy/komiser https://www.infracost.io/

BUY VS. BUILD
* the 1960s
> While today we run application software on top of a few common operating systems, this wasn’t the case until the 1990s. During the middle ages of computing on mainframe machines, 90% of all software sold was custom-built; only 10% was purchased off the shelf. This landscape deeply influenced how companies developed their technology. Some imagined that the future of software would involve industry-standardized hardware, OS, and programming languages, like the SABRE system for the airline industry (that’s still used today!). Most companies stuck to building their own completely isolated software, often reinventing the wheel. https://retool.com/blog/erp-for-engineers
* https://danluu.com/in-house/
* https://news.ycombinator.com/item?id=25399250
> Another area is with software we’ve had to build (instead of buy). When we started out, we strongly preferred buying software over building it because a team of only a few engineers can’t afford the time cost of building everything. That was the right choice at the time even though the “buy” option generally gives you tools that don’t work. In cases where vendors can’t be convinced to fix showstopping bugs that are critical blockers for us, it does make sense to build more of our own tools and maintain in-house expertise in more areas, in contradiction to the standard advice that a company should only choose to “build” in its core competency. Much of that complexity is complexity that we don’t want to take on, but in some product categories, even after fairly extensive research we haven’t found any vendor that seems likely to provide a product that works for us. To be fair to our vendors, the problem they’d need to solve to deliver a working solution to us is much more complex than the problem we need to solve since our vendors are taking on the complexity of solving a problem for every customer, whereas we only need to solve the problem for one customer, ourselves. https://danluu.com/simple-architectures/

* https://blog.duolingo.com/reducing-cloud-spending
* https://world.hey.com/dhh/our-cloud-exit-savings-will-now-top-ten-million-over-five-years-c7d9b5bd
* https://focus.finops.org/
> Cloud and SaaS billing data can be complex, inconsistent among providers and difficult to understand. The FinOps Open Cost and Usage Specification (FOCUS) aims to reduce this friction with a spec containing a set of terminologies (aligned with the FinOps framework), a schema and a minimum set of requirements for billing data. The spec is intended to support use cases common to a variety of FinOps practitioners. Although still in the early stages of development and adoption, it’s worth watching because, with growing industry adoption, FOCUS will make it easier for platforms and end users to get a holistic view of cloud spend across a long tail of cloud and SaaS providers. https://www.thoughtworks.com/radar/platforms/focus
* rightsizing https://softwareengineeringdaily.com/2021/01/12/kubecost-with-webb-brown/
* on-prem: need to integrate w/ legacy systems inside firewall, regulatory, cheaper, you can still make the consumption of your data center feel like a public cloud (CF, HPE)
* _capacity planning / demand forecasting_: https://blog.codepen.io/2017/03/21/122-capacity-planning/ https://increment.com/cloud/an-engineers-guide-to-cloud-capacity-planning/ https://www.youtube.com/watch?v=UC5xf8FbdJc https://www.youtube.com/watch?v=ov7xhNdrsDM https://www.manning.com/books/demand-forecasting-best-practices
* free tier https://www.lastweekinaws.com/blog/an-aws-free-tier-bill-shock-your-next-steps/
> Exercise: Pick an infrastructure service that your team operates and calculate how many hours/month you work to maintain the solution. https://cloudonaut.io/my-mental-model-of-aws/
* https://www.lastweekinaws.com/blog/the-new-frontier-of-cloud-economics-why-aws-costs-are-a-weighty-issue/
* https://www.lastweekinaws.com/blog/awss-deprecation-policy-is-like-a-platypus/
* https://www.lastweekinaws.com/blog/why_amazon_cant_end_the_release_tidal_wave/
* https://www.lastweekinaws.com/blog/the-feudal-lords-of-amazon/
* https://www.lastweekinaws.com/blog/the-new-frontier-of-cloud-economics-why-aws-costs-are-a-weighty-issue/
* AWS is more expensive https://calpaterson.com/amazon-premium.html https://bravenewgeek.com/multi-cloud-is-a-trap/
* switching https://news.ycombinator.com/item?id=30942698
* https://www.lastweekinaws.com/blog/the-new-frontier-of-cloud-economics-why-aws-costs-are-a-weighty-issue/
> But the thing is in most of the companies you don't have full control over the whole stack. Even if you have "full control" over the database, you don't have control over networking, firewall, OS, "security" patching, VMs, Docker, Kubernetes, Load balancers, vendors managing parts of the infra, internet provider, hosting provider ... Not even datacenter team may have control over all of it, but at least that's their job and their area of expertise.

## IaaS

🗄 `html-css.com`

TAXONOMY https://www.youtube.com/watch?v=NhDYbskXRgc [48:00]
> Simplified deployment of virtual servers, managed databases, and networking services.
> What is a server? Is it just, like, a big computer? Or is it actually special? There's a lot of industrial history wrapped up in that question, and the answer is often very context-specific. But there are some generalizations we can make about the history of the server: client-server computing originated mostly as an evolution of time-sharing computing using multiple terminals connected to a single computer. There was no expectation that terminals had a similar architecture to computers (and indeed they were usually vastly simpler machines), and that attitude carried over to client-server systems. The PC revolution instilled a WinTel monoculture in much of client-side computing by the mid-'90s, but it remained common into the '00s for servers to run entirely different operating systems and architectures. https://computer.rip/2024-08-31-ipmi.html
* _node_: physical or virtual to host something (web server, API)
* con: can't vertically scale https://www.youtube.com/watch?v=NhDYbskXRgc [1:09:30]
* _dedicated_: physical machine (Raspberry Pi, Rackspace) + single business https://news.ycombinator.com/item?id=22407098
* _virtual_: virtualize physical node + single business
* _shared_: virtualize physical node + n businesses
* BYO https://news.ycombinator.com/item?id=30676595
* _cloud_: virtualize n nodes + n businesses; offers metered billing, composable services https://www.youtube.com/watch?v=NhDYbskXRgc [55:45]
* OSS: OpenStack, CloudStack, VSphere
* _PaaS_: e.g. Heroku https://www.youtube.com/watch?v=NhDYbskXRgc [1:14:15]
* _IaaS_: e.g. AWS

---

* Cloudflare https://rutar.org/writing/how-to-build-a-personal-webpage-from-scratch/ https://rutar.org/writing/previewing-a-development-branch-on-cloudflare-pages/ https://news.ycombinator.com/item?id=34639212
* https://adamj.eu/colophon/
* Netlify https://uglyduck.ca/articles/
* https://dev.to/harri_etty/the-introduction-to-servers-i-wish-i-d-had-44jl
* _level 2 (resellers)_: Heroku, Netlify, Render https://render.com/ https://softwareengineeringdaily.com/2019/06/17/render-high-level-cloud-with-anurag-goel/ Serverless https://serverless.com/
* _alternatives_: Platform.sh https://news.ycombinator.com/item?id=22486031, Zeit/Vercel https://news.ycombinator.com/item?id=22933479 OpenShift (RHEL managed Kubernetes https://news.ycombinator.com/item?id=3003289) Cloud Run https://alexolivier.me/posts/deploy-container-stateless-cheap-google-cloud-run-serverless Dokku http://dokku.viewdocs.io/dokku/ Cap Rover https://news.ycombinator.com/item?id=23465087 https://fly.io/
* _Digital Ocean_: https://github.com/seven1m/do-install-button

## Tailscale

🗄️
* `aws.md` network > VPC
* `tcp-ip.md` VPN

https://blog.6nok.org/tailscale-is-pretty-useful/
* https://news.ycombinator.com/item?id=33986430
> I’m a huge Tailscale fan and was quite happy to see that they’re doing well. The fascinating bit for me in that article, though, was this: “AI firms have big networking problems because they must transfer immense amounts of data between many machines across multiple cloud providers. They also face plenty of access control, compliance, cryptography, identity, and privacy concerns, given the amount of personal data they process for clients and the reputational risk should something go awry. These characteristics make AI companies ‘an ideal use case’ for Tailscale.” That makes sense, of course, but I have to admit that even though I was aware that AI involves a lot of data, my mind didn’t make the leap to “they probably run into a lot of networking problems.” https://registerspill.thorstenball.com/p/joy-and-curiosity-23
