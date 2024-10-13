# ⛩️

## 参考

🔍 https://softwarerecs.stackexchange.com

## 进步

https://www.youtube.com/watch?v=x4k1XEjNzYQ
workflow engine or task queue https://news.ycombinator.com/item?id=34163888 https://www.reddit.com/r/golang/comments/1as23yb/when_to_use_a_workflow_tool_temporal_vs_a_job/ https://www.inngest.com/blog/how-durable-workflow-engines-work https://www.reddit.com/r/golang/comments/xa25ed/workflow_engine_vs_task_queue/

* _20_: Heroku (simple Django app), gunicorn, uWSGI
* _19_: https://github.com/zachvalenta/nginx-wsgi
* _18_: Cloud Foundry and AMQP/Spring for Dark Canary
* _17_: try out Terraform and AWS for Comcast interview

# 🧮 IaC

---

https://roadmap.sh/linux
* SQL https://news.ycombinator.com/item?id=28554089
* Ansible-like (Puppet, Chef, Salt)
* https://github.com/Fizzadar/pyinfra https://www.pythonpodcast.com/pyinfra-configuration-management-episode-270/
* http://scriptedconfiguration.org/ https://github.com/comtrya/comtrya https://www.youtube.com/watch?v=TNlDSG1iDW8
* _CloudFormation_: deployment
* _config mgmt_: provision server remotely

REMOTE EXECUTION 🗄️ `python/stdlib.md` process exec
* _Fabric_: execute script on server; apparently not meant for fully-fledged config mgmt https://stackoverflow.com/questions/39370364/when-to-use-fabric-or-ansible but can/could be used with Ansible (article doesn't explain why not just use Ansible and is undated)
* _Paramiko_: https://github.com/paramiko/paramiko
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

## Terraform

🛣️ https://roadmap.sh/terraform

SEMANTICS
> generates a dependency graph of resources, runs against provider, walks resource graph and ensures that resources are configured
* _provider_: AWS, Azure, et al.
* _resource_: provider's infra
* _variable_: your data
* _data_: provider data
* _output_: attributes provider gives back

---

* https://github.com/leg100/pug
* certification https://www.hashicorp.com/certification
* alternative https://opentofu.org/
* https://github.com/idoavrah/terraform-tui
* `tf -plan`
* CLI to query https://github.com/mazen160/tfquery
* Python alternative https://www.pulumi.com/ https://leebriggs.co.uk/
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

# 🏁 QUEUES

🗄 `db.md` data eng/ETL
📚
* Kleppmann ch. 11
* Narkhede ch. 11

TAXONOMY https://eranstiller.com/rabbitmq-vs-kafka-an-architects-dilemma-part-1
* _bus_: stores msgs
* _message queue_: bus + FIFO; aka stream processing https://stackoverflow.com/q/7793927 📙 Kleppmann [3]
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

## event (Kafka)

🗄 `data/eng.md` streaming
📜 https://kafka.apache.org/documentation/
📙 Narkhede guide
📹
* 101 https://www.youtube.com/playlist?list=PLa7VYi0yPIH0KbnJQcMv5N9iW8HkZHztH
* talk https://www.youtube.com/watch?v=Ltgt0ekso4c
* example https://www.youtube.com/channel/UCDankIVMXJEkhtjv5yLSN4g/videos

RUN
* Docker https://www.youtube.com/watch?v=qi7uR3ItaOY 4:00
* GUIs https://news.ycombinator.com/item?id=24099037 https://akhq.io/ https://github.com/sauljabin/kaskade
* alternative https://github.com/liftbridge-io/liftbridge
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

USAGE
* as distributed commit log https://news.ycombinator.com/item?id=26644713 📙 Jeffrey distributed [6]
> same as audit log?

PROTOCOL https://kafka.apache.org/0100/protocol.html
* rides on top of TCP so you need client per language https://strimzi.io/blog/2019/07/19/http-bridge-intro/
* handshake https://pierrezemb.fr/posts/diving-into-kafka-protocol/
* _message set_: msgs grouped https://kafka.apache.org/documentation/#maximizingefficiency

ALTERNATIVES
* _AWS SQS_: https://cheesecakelabs.com/blog/asynchronous-task-queue-django-celery-aws-sqs
* _Pulsar_: Kafka alternative https://www.youtube.com/watch?v=x4k1XEjNzYQ
* _Rabbit_: comes w/ own db https://stackoverflow.com/q/38444425
* vs. Kafka https://aws.amazon.com/msk/what-is-kafka/
* _ZeroMQ_: http://aosabook.org/en/zeromq.html

za
* tooling https://github.com/batchcorp/plumber https://github.com/sauljabin/kaskade
* BYO https://github.com/travisjeffery/jocko
* https://developer.confluent.io/what-is-apache-kafka/#intro-to-ak
* https://www.confluent.io/blog/author/martin-kleppmann/
* Avro (eventbus README)
* https://unitedmasters.atlassian.net/wiki/spaces/ENG/pages/322273452/Event+Bus+System

## msg (Rabbit)

* queue attributes: durability (keep in mem, write to disk, write to db bc broker can restart, fail) time-to-live (how long to keep in the queue?) security (what consumers have access?) batching (delivery immediately or wait until x messages before allowing consumers to take)
* msg attributes: id, user/groups id, creation time, reply to, subject https://www.rabbitmq.com/tutorials/amqp-concepts.html
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

---

🛠 https://taskqueues.com/ aka worker https://news.ycombinator.com/item?id=34940920
🗄
* `eng.md` pipelines
* `shell.md` jobs

ZA
* chron jobs https://github.com/Nukesor/pueue
* Postgres https://github.com/procrastinate-org/procrastinate https://brandur.org/river https://github.com/riverqueue/river https://news.ycombinator.com/item?id=41284703
* BYO https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/
* _Django Q_: uses Django's own db to store tasks https://www.valentinog.com/blog/django-q https://django-simple-task.readthedocs.io
* _Hatchet_: https://github.com/hatchet-dev/hatchet
* _Huey_: https://www.untangled.dev/2020/07/01/huey-minimal-task-queue-django https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#27:00 https://github.com/coleifer/huey

CELERY 📹 https://www.youtube.com/@NickJanetakis/search?query=celery
* chron job
* https://steve.dignam.xyz/2023/05/20/many-problems-with-celery/
* Redis as db for Celery jobs https://ljvmiranda921.github.io/notebook/2019/11/08/flask-redis-celery-mcdo/
* https://www.youtube.com/watch?v=v7LOVlPq7ds
* _Flower_: monitor Celery https://github.com/mher/flower https://testdriven.io/blog/flower-nginx/
*  https://www.agiliq.com/blog/2015/07/getting-started-with-celery-and-redis/
*  https://djangostars.com/blog/the-python-celery-cookbook-small-tool-big-possibilities/
*  https://testdriven.io/blog/asynchronous-tasks-with-falcon-and-celery/
*  https://adamj.eu/tech/2020/02/03/common-celery-issues-on-django-projects
*  https://stackshare.io/sentry/how-sentry-receives-20-billion-events-per-month-while-preparing-to-handle-twice-that
*  https://nickjanetakis.com/blog/4-use-cases-for-when-to-use-celery-in-a-flask-application

REDIS QUEUE (RQ)
* https://testdriven.io/blog/asynchronous-tasks-with-flask-and-redis-queue/
* https://pyvideo.org/pygotham-2018/tracking-the-international-space-station-in-django-with-redis-queue-and-rq-scheduler.html
* https://testdriven.io/blog/sending-confirmation-emails-with-flask-rq-and-ses/#workflow
* https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/

## workflow engine (Airflow)

🗄 `eng.md` pipelines

---

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

> Parsing the request is just a matter of splitting the request string into lines. The first line contains the method, path and protocol separated by spaces. The following lines contain the headers, followed by an empty line. https://blog.sylver.dev/build-a-web-server-with-rust-and-tokio-part-0-a-simple-get-handler
* benchmark: https://httpd.apache.org/docs/2.4/programs/ab.html https://github.com/wg/wrk https://github.com/giltene/wrk2 https://github.com/rakyll/hey https://github.com/encode/starlette#performance https://falconframework.org/#sectionBenchmarks https://www.webpagetest.org/ https://www.golang.dk/articles/benchmarking-sqlite-performance-in-go
* BYO https://github.com/codecrafters-io/build-your-own-x#build-your-own-web-server https://news.ycombinator.com/item?id=41642151 https://doc.rust-lang.org/book/ch20-00-final-project-a-web-server.html
* mock server: https://smocker.dev/
* URL for dev server: ngrok https://news.ycombinator.com/item?id=40355744 https://github.com/andydunstall/piko
* comment server: Disqus, isso https://avi.im/blag/about/ https://posativ.org/isso/docs/
* _Apache_: on start, Apache runs as master process `root` and binds to port 80; pre-fork (master process spawns child proccesses under UID `apached` to wait for connections) https://stackoverflow.com/a/25894770/6813490
* _CGI_: process per req (vs. connection) cannot keep db connection over multiple
* _redbean_: small https://justine.lol/redbean/index.html https://news.ycombinator.com/item?id=27431910

💀 UWSGI
* in maintenance mode https://pythonbytes.fm/episodes/show/401/we-must-replace-uwsgi-with-something-else
* run options https://blog.ionelmc.ro/2022/03/14/how-to-run-uwsgi/
* docs are a mess, scroll past 42 changelogs for the README, and commercial support in Italian https://github.com/unbit/uwsgi-docs#commercial-support
* install
* commands https://github.com/zachvalenta/flask-skeleton/commit/435517e5e1353eaa875d16e91ea96e47300b35dc
```sh
# https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploy-it-on-http-port-9090
uwsgi --http :9090 --wsgi-file foobar.py

# https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uswgi-and-nginx-on-ubuntu-18-04
# https://github.com/zachvalenta/flask-uwsgi-scaffold
uwsgi --socket 0.0.0.0:8000 --protocol=http -w wsgi

# expects app obj to be named `application` https://riptutorial.com/flask/example/16286/using-uwsgi-to-run-a-flask-application
# rename w/ `callable` https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploying-flask
# https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploying-flask
uwsgi --http :5002 --wsgi-file app.py --callable app

# https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#adding-concurrency-and-monitoring
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2 --stats 127.0.0.1:9191
```
* can also point to app obj via `uwsgi.py` or `uwsgi.ini` https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-14-04 https://www.youtube.com/watch?v=lnFMKAIHRcA
```sh
uwsgi --socket 0.0.0.0:8000 --protocol=http -w wsgi --callable
```
```python
from myproject import application
if __name__ == "__main__":
    application.run()
```

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

## Granian

---
* https://github.com/emmett-framework/granian
* https://talkpython.fm/episodes/show/463/running-on-rust-granian-web-server

## Gunicorn

📜 https://docs.gunicorn.org/en/stable/

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

## Cloud Foundry

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
* _Procfile_: Ruby version of `docker-compose.yml`
* used by Heroku

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

## Heroku 

ALTERNATIVES https://testdriven.io/blog/heroku-alternatives/
* _AWS Beanstalk_:
* _Dokku_:
* _Fly.io_: https://www.youtube.com/watch?v=0eP98xkLj9w
* _Google App Engine_:
* _Kamal_: https://kamal-deploy.org/
* _Netlify_: 
* _Pikku_: https://github.com/piku/piku
* _Render_: 
* _Platform.sh_:
* _Sidekick_: 🎯 https://github.com/MightyMoud/sidekick https://news.ycombinator.com/item?id=41591018
* _Tau_: https://github.com/taubyte/tau
* _Vercel_: 

> With something like Heroku, you can have multiple VM's in staging and production, w/ a deployment pipeline that supports rollbacks, monitoring, alerting, autoscaling, all in a managed environment w/ a managed, highly available Postgres setup, with very little effort and 0 maintenance. This is what I've setup at my current startup. My last company was on K8's and I loved it -- but this is nearly as good and requires literally no maintenance and far less expertise / setup. - https://news.ycombinator.com/item?id=22493873 

relisten from 29:30 for limitations https://softwareengineeringdaily.com/2019/06/17/render-high-level-cloud-with-anurag-goel/
> my playbook: Heroku for experiments, Render for most work, AWS for work

cmd
* login: `login`
* create app: `create`
* push: `git push heroku master` [Vincent 📍]
* start: `ps:scale web=1` [Vincent 📍]
* open: `open`
* stop: `ps:scale web=0` https://stackoverflow.com/a/10231477/6813490

* https://www.accordbox.com/blog/deploy-django-project-heroku-using-docker/
* _pricing_: 2GB RAM is hundreds of dollars; they're owned by Salesforce now https://softwareengineeringdaily.com/2019/06/17/render-high-level-cloud-with-anurag-goel/ 29:15
* _dyno_: VM running on top of EC2 instance https://stackoverflow.com/questions/21462439/what-exactly-is-a-single-heroku-web-dyno
* _Git_: seems like when you're logged Heroku automatically becomes a Git remote [Vincent page 📍]
* _scale_: serves 2M req/month pretty easily https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around
* _virtual environments_: doesn't support Poetry yet https://github.com/heroku/heroku-buildpack-python/issues/796 need `requirements.txt` in root https://devcenter.heroku.com/articles/python-support#recognizing-a-python-app https://devcenter.heroku.com/articles/python-support#build-behavior
* _Python version_: `runtime.txt` https://devcenter.heroku.com/articles/python-runtimes#selecting-a-runtime

* analogous to `docker-compose.yml` https://www.mattlayman.com/blog/2019/web-development-environments/
```Procfile
web: ./manage.py runserver
worker: celery worker --app new_hot_thing:celeryapp --loglevel info
frontend: webpack --watch
```

## hosting

🗄 `html-css.com`

TAXONOMY https://www.youtube.com/watch?v=NhDYbskXRgc [48:00]
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

STATIC SITE
* _AWS_: https://brandur.org/aws-intrinsic-static S3 and Cloudfront https://www.benkuhn.net/about/ https://github.com/s3tools/s3cmd s3-website https://bedford.io/misc/about/
* _Firebase_: https://tinyprojects.dev/projects/tiny_website
* _Github_: source has to be public
* _Netlify_: https://wsvincent.com/site-design/ https://adamwathan.me/uses/

---

* self-hosting https://www.jotaen.net/anA6o/self-hosting-guide-docker-haproxy-lets-encrypt/ https://knhash.in/gentle-guide-to-self-hosting/
* hosting https://news.ycombinator.com/item?id=34860655 https://news.ycombinator.com/item?id=34867314
* Cloudflare https://rutar.org/writing/how-to-build-a-personal-webpage-from-scratch/ https://rutar.org/writing/previewing-a-development-branch-on-cloudflare-pages/ https://news.ycombinator.com/item?id=34639212
* https://adamj.eu/colophon/
* Netlify https://uglyduck.ca/articles/
* https://dev.to/harri_etty/the-introduction-to-servers-i-wish-i-d-had-44jl
* _level 2 (resellers)_: Heroku, Netlify, Render https://render.com/ https://softwareengineeringdaily.com/2019/06/17/render-high-level-cloud-with-anurag-goel/ Serverless https://serverless.com/
* _alternatives_: Platform.sh https://news.ycombinator.com/item?id=22486031, Zeit/Vercel https://news.ycombinator.com/item?id=22933479 OpenShift (RHEL managed Kubernetes https://news.ycombinator.com/item?id=3003289) Cloud Run https://alexolivier.me/posts/deploy-container-stateless-cheap-google-cloud-run-serverless Dokku http://dokku.viewdocs.io/dokku/ Cap Rover https://news.ycombinator.com/item?id=23465087 https://fly.io/
* _Digital Ocean_: https://github.com/seven1m/do-install-button

## GCP

* https://softwareengineeringdaily.com/2021/06/09/gcp-with-liz-fong-jones/

* _App Engine_: https://testdriven.io/blog/django-gae
* _RTDN_: notifcations from GP app https://developer.android.com/google/play/billing/rtdn-reference
* howto https://developer.android.com/google/play/billing/getting-ready#enable-rtdn
* _Cloud Pub/Sub_: MQ btw GCP apps https://cloud.google.com/pubsub/docs/publish-receive-messages-console https://console.cloud.google.com/cloudpubsub/topic/list https://console.cloud.google.com/cloudpubsub/subscription/list
* multiple topics for GP app: possible? https://stackoverflow.com/q/72688883 yes https://stackoverflow.com/a/52759477 https://stackoverflow.com/a/71740580 no https://stackoverflow.com/a/70986770
* https://stackoverflow.com/questions/6991135/what-does-it-mean-to-hydrate-an-object

IAM
* _principal_: user account, service account, group
* _role_: collection of perms
* _condition_: further constraint on role i.e. no write access if req lacks key
* _allow policy_: mapping of principal to role per resource https://cloud.google.com/iam/docs/policies
* _service account_: account for service (vs. user) https://cloud.google.com/iam/docs/service-accounts
* GCP also has service accounts for itself e.g. to publish RTDN https://stackoverflow.com/a/64184564

IAP Proxy https://www.youtube.com/watch?v=xM9-FSU5MoY
* type of access: public, authed users, authed employees [2:00]
* = identity service in front of site [3:30]
* uses Google (or Active Directory) as SSoT for identity [4:15]

za
* unreliable https://news.ycombinator.com/item?id=24169044
* bad customer supprt https://calpaterson.com/amazon-premium.html
* GCS = S3
* Cloud SQL = RDS
* Cloud Spanner = Aurora
* _BigQuery_: serverless db, good for GIS https://news.ycombinator.com/item?id=40052172
* _BigTable_: BigQuery but NoSQL https://cloud.google.com/free/docs/map-aws-google-cloud-platform

## mobile

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
