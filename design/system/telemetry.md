# ⛩️

## 参考

🗄️ `os/tools.md` monitoring
📚
* Bueno mature optimization https://carlos.bueno.org/optimization/
* Google SRE book https://sre.google/sre-book/table-of-contents/ https://danluu.com/google-sre-book/
> aka platform engineering https://www.manning.com/books/effective-platform-engineering
* ⭐️ Sweet experimentation https://www.manning.com/books/experimentation-for-engineers
* Wilkins https://www.manning.com/books/logs-and-telemetry

## 进步

🧠 https://claude.ai/chat/2f99faeb-79c6-4f49-8be8-b595a6ab1ff7
summaries https://github.com/dx-tooling/platform-problem-monitoring-core https://news.ycombinator.com/item?id=43575664

* _24_: big rf, ready to start implementing myself
* _23_: Datadog with CRD
* _17_: Google SRE book first 20 chapters

# 📊 METRICS

🗄️ `architecture.md` Ford fitness functions

---

https://simonwillison.net/2024/Dec/29/threads-ios-performance/
https://vadimkravcenko.com/shorts/habits-of-great-software-engineers/#the-art-of-approximation https://vadimkravcenko.com/technical-manager-guide/
https://sourcehut.org/blog/2020-07-03-how-we-monitor-our-services
* https://danluu.com/metrics-analytics/ https://www.kalzumeus.com/greatest-hits/ https://danluu.com/web-bloat https://thoughtbot.com/upcase/analytics-for-developers 

https://news.ycombinator.com/item?id=42203501

* Kleppmann chapter 1 notes @ 14 -> `math.md` distributions
bandwindth and CPU https://talkpython.fm/blog/posts/we-have-moved-to-hetzner/

https://www.roguelynn.com/words/tracing-fast-and-slow/
https://www.roguelynn.com/words/metrics-driven-development/
https://www.hytradboi.com/2025/52dd81d7-d720-4e53-8374-9e273c210348-lets-run-a-million-benchmarks

SEMANTICS https://www.datadoghq.com/ebook/monitoring-modern-infrastructure/
* _event_: change to system e.g. build, release, add/substract host/container, alert going off
* _metric_: value from system at a particlar point in time
* metrics: success rate, error rate


* https://www.webpagetest.org/
* _walltime_: time as humans generally perceive it [Mature Optimization Handbook]
* _bandwidth_: optimal bitrate (bits over network per second); measured in Gbps https://hpbn.co/primer-on-latency-and-bandwidth/
* _response time_: time btw client sending req and receiving res [Kleppmann 13-14] speed e.g. how fast does single req come back?; 100M dash
* _service time_: time to process client req i.e. compute [Kleppmann 14]

## bandwidth

> I will retell an anecdote because I love it so much: it's so hard to get a wire down the hole in a fashion that the wire survives, that rather than using wires to communicate with the drill bit that is 10 kilometers down, they use modems. The modem doesn't make acoustic sound over the wire or an electrical sound that approximates an acoustic sound at any point – no, they send an acoustic signal vibrating through the mud in the hole and then listen for that acoustic signal on the other end, and use a decoupler to turn that back into a waveform to get a very small number of bits per second of signal from the machine that is deep down the hole and which they are attempting not to break.  https://www.complexsystemspodcast.com/episodes/boom-busts-and-long-term-progress-with-byrne-hobart-2/

## ⭕️ factors

---

* https://news.ycombinator.com/item?id=23880071 https://simpleops.io/
* users online https://analytics.usa.gov/
* uptime https://news.ycombinator.com/item?id=25553445 depends on system component https://www.openmymind.net/Im-Not-Sold-On-High-Availability/

https://www.semicolonandsons.com/episode/error-tracking-and-monitoring
* exception reporting
* logging (production, retention, search)
* downtime alerting
* system monitoring
* financial reporting

* https://www.thediff.co/archive/the-data-business-at-three-resolutions/
* _chaos engineering_: trigger fault to see if it causes a failure https://github.com/powerfulseal/powerfulseal
* https://news.ycombinator.com/item?id=40573790
* https://www.ryancheley.com/2023/10/29/error-culture/

* https://en.wikipedia.org/wiki/Seven_basic_tools_of_quality

TAXONOMY
* user sessions https://news.ycombinator.com/item?id=40318542 https://jam.dev/ https://trackjs.com/
* tracing

* _dead man's switch_: cease operation in absence of human operator e.g. carts at airport [Conery 6; think his usage wrong]

## latency

📙 Enberg latency https://www.manning.com/books/latency
🗄️
* `tcp-ip.md` UDP
* `infra.md` Granian

SEMANTICS
* _latency_: time it takes for data to travel from one point to another; measured in ms
* causes: packet loss, routing
* _lag_: noticeable delay btw user action and system res
* can be due to latency but also low FPS (processor, RAM, monitor) https://mas-bandwidth.com/what-is-lag/

---

TIME
> time delay btw cause and observed effect 📙 Enberg
> number of seconds it takes for an operation to complete https://leanpub.com/systemdesignmanual/read_sample
> if your latency is 500ms https://jvns.ca/blog/2017/04/01/slow-down-your-internet-with-tc/
* https://github.com/apenwarr/blip

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

* latency throughput https://entropicthoughts.com/typing-fast-is-about-latency-not-throughput
* _throughput_: amount of work per unit of time e.g. RPS
> Amazon DynamoDB introduces warm throughput for tables and indexes - Ooh, you mean we can (finally) find out what the actual limits are for when a table will stop accepting reads or writes? Without having to fly to Seattle and make someone extremely uncomfortably by asking them from well within their personal space? For free?! Plus you can set that value higher for a one time fee? WHY ARE WE STILL TALKING? Take my money already! https://aws.amazon.com/about-aws/whats-new/2024/11/amazon-dynamodb-warm-throughput-ondemand-provisioned-tables/

📍 rf using Kleppmann, Data Networking Made Easy, sou (networking, system design)

* _latency_: time required to complete unit of work e.g. % of requests returns with X time e.g. 99% of requests return w/in 0.2 ms https://www.youtube.com/watch?v=FqR5vESuKe0 https://danluu.com/keyboard-latency/

https://networkengineering.stackexchange.com/questions/52232/whats-the-difference-between-latency-and-round-trip-time
* _latency_: time that req waiting to be handled; people use as a synonym for response time [Kleppmann 14]
* _latency_: https://robertovitillo.com/why-you-should-measure-tail-latencies/
* _tail latencies_: synonym for the higher percentiles of response times; hard to reduce bc easily affected by random stuff beyond your control [Kleppmann 15]

* _latency_: how long it takes the data to get to the place it needs to be computed https://www.moderndescartes.com/essays/data_oriented_python/ https://github.com/nakabonne/ali geography https://calpaterson.com/latency.html https://danluu.com/term-latency/

jitter https://gafferongames.com/post/fixing_the_internet_for_games/ https://www.youtube.com/watch?v=I_TtMk5z0O0
> variablility in latency https://networkengineering.stackexchange.com/a/22826
> out-of-sequence packets [Data Networking Made Easy 26]

## load parameters

* _load parameter_: metric; way to describe load on system [Kleppmann 11]
* _node_: CPU, mem, storage 
* _service_: req volume (RPS https://stackexchange.com/performance), simultaneously active users, error rate (5xx per M req), uptime (five nines https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/)
* _db_: queries per req (statsd) https://www.youtube.com/watch?v=-6Hk9rcgM94 ratio of reads to write, hit rate on cache [Kleppmann 11]

* _utilization_: % of time resource is busy
* _saturation_: amount of work resource cannot yet service i.e. how much stuff is queued up waiting
* _availability_: how often resource responds to request
* _p$NUM_: what percentage of requests below a certain latency https://www.youtube.com/watch?v=3JdQOExKtUY 1:55
```sh
# p99: 99% of req below 400MS
80%    90%    95%    98%    99%    99.9%  99.99% 100%
------|------|------|------|------|------|------|------
100    110    110    120    400    400    400    400
```
* _QPS (queries per second)_: https://www.youtube.com/watch?v=kEShMV4VfWE
* _RPS_: 

* _percentiles_: p50 (median) p90 (worst case); mean doesn't tell you how many nodes/users
* _skew_: uneven distibution re: load across worker processes [Kleppmann 20] what prevents run time of batch job being data divided by throughput

* _frecency_: frequency + recency https://missing.csail.mit.edu/2020/shell-tools/ https://github.com/rupa/z https://github.com/ajeetdsouza/zoxide/wiki/Algorithm#matching

* utilization, system metrics https://entropicthoughts.com/predicting-resource-usage-from-increased-traffic https://entropicthoughts.com/response-time-is-the-system-talking

## perf

🗄️ `databases.md` perf
📙 Gregg systems performance

---

https://slimsaas.com/blog/django-scaling-performance

DJANGO
* https://medium.com/django-unleashed/django-application-performance-optimization-a-checklist-63e2c6d69e4e
* https://loadforge.com/guides/the-ultimate-guide-to-django-performance-best-practices-for-scaling-and-optimization
* https://docs.djangoproject.com/en/5.1/topics/performance/
* https://blog.pecar.me/django-sqlite-benchmark
* https://blog.pecar.me/django-sqlite-dblock
* https://testdriven.io/blog/django-performance-optimization-tips/

ZA
* https://blog.pecar.me/sqlite-wal
* https://www.youtube.com/watch?v=gpbpVheR3gM
* https://blog.pecar.me/django-streaming-responses
* https://xnacly.me/posts/2024/optimizing-a-dependency/

## throughput

---

```txt
Warm throughput refers to the rate of processing or performance capacity of a system that is in a "warm" state, meaning it is already initialized, loaded, and ready to handle tasks. This contrasts with "cold throughput," where the system needs to initialize or load resources before becoming operational.

Key Aspects of Warm Throughput:
Pre-initialization: The system has already completed any one-time setup or loading processes.
Ready State: Resources such as caches, connections, and configurations are primed and active.
Performance Measurement: Warm throughput is typically measured when a system is operating under normal, steady-state conditions.
Optimization: Warm throughput is often higher than cold throughput due to reduced latency from skipping setup overhead.
Examples:
In a database, warm throughput refers to query performance when frequently accessed data is cached in memory versus the initial slower response when data is fetched from disk (cold throughput).
In serverless computing, warm throughput refers to the processing rate of already-initialized functions, as opposed to the delay caused by cold starts (e.g., loading the runtime environment for the first request).
In a network, warm throughput might measure the data transfer rate once a session is established, compared to the setup phase (e.g., TLS handshake).
```

https://leanpub.com/systemdesignmanual/read_sample
> throughput is the number of operations per second, where an operation is an application-specific unit of work.

throughput definitions
* https://sirupsen.com/napkin/problem-4
> a system that is designed to handle 100,000 requests per second, each 1 kB in size, looks very different from a system that is designed for three requests per minute, each 2 GB in size—even though the two systems have the same data throughput [Kleppmann 24]
* how long it takes the data to be computed https://www.moderndescartes.com/essays/data_oriented_python/
* amount e.g. RPS [Kleppmann 13, 20] https://calpaterson.com/async-python-is-not-faster.html
* actual bitrate https://networkengineering.stackexchange.com/a/57428
* how much you can get done 📙 Christian 124

warm throughput 🧠 https://chatgpt.com/c/673e0350-b5dc-8004-b222-e85277b89921
> sort this entire section out with GPT

# 🩻 MONITORING

---

https://claude.ai/chat/6bcfcae0-6294-47ef-a3bf-588a7f178c0e

PROVIDERS
* _Checkly_: https://bitfieldconsulting.com/blog/dips-and-wiggles https://www.checklyhq.com/
* _HyperDX_: 🎯 https://github.com/hyperdxio/hyperdx
> HyperDX is an open-source observability platform that unifies all three pillars of observability: logs, metrics and tracing. With it, you can correlate end-to-end and go from browser session replay to logs and traces in just a few clicks. The platform leverages ClickHouse as a central data store for all telemetry data, and it scales to aggregate log patterns and condense billions of events into distinctive clusters. Although you can choose from several observability platforms, we want to highlight HyperDX for its unified developer experience. https://www.thoughtworks.com/radar/platforms/hyperdx
* _Fluent Bit_: 🎯 https://www.manning.com/books/logs-and-telemetry https://fluentbit.io/
* _Logfire_: https://pydantic.dev/logfire https://pydantic.dev/articles/logfire-announcement
* _Jam_: error reporting https://jam.dev/ https://news.ycombinator.com/item?id=40318542 🗄️ `test.md` friction logs
* _Moderato_: 🎯 https://github.com/moderato-app/live-pprof
* _Netdata_: https://github.com/netdata/netdata
* _OpenObserve_: https://github.com/openobserve/openobserve https://news.ycombinator.com/item?id=41898910 https://sso.tax/
* _New Relic_: 
* _Rollbar_: https://pythonbytes.fm/episodes/show/24/i-have-a-local-pypi-server-and-so-do-you 
* _Sentry_: suspected commit behind break

PROVIDERS
* howto: server logs (GoAccess), CSS https://herman.bearblog.dev/how-bear-does-analytics-with-css/
* Django sessions
* _Amplitude_: https://satchel.com/web-analytics/
* _Braze_: 
* _Chartbeat_: publishing
> The most influential is Chartbeat, which shows you every article on your site, indicates the number of people on each article at any given second, and colors the dots representing those people to tell you how they found the article. Green dots mean they found you through a search engine. Purple dots mean they came from a social network, usually Facebook, Twitter, or Reddit. It’s pure pleasure to watch the display for an article you worked hard on fill with dots. https://www.vox.com/2020/1/28/21077888/why-were-polarized-media-book-ezra-news
* _Hotjar_: https://www.hotjar.com/
* _GoatCounter_: 🎯  Visidata uses https://www.goatcounter.com/ alternative https://github.com/ihucos/counter.dev https://news.ycombinator.com/item?id=26379569 https://simpleanalytics.com/ https://newcss.net/
* _Google Analytics_: https://satchel.com/web-analytics/ alternatives https://tedium.co/2023/03/04/self-hosted-saas-app-alternatives/
* Ackee https://github.com/electerious/Ackee
* BYO https://minimalanalytics.com/
* Countly https://thomashunter.name/posts/2018-12-28-migrating-from-google-analytics
* Fathom https://usefathom.com/
* Shynet https://github.com/milesmcc/shynet
* Simple https://simpleanalytics.io
* _Heap_: https://satchel.com/web-analytics/
* _Highlight_: https://news.ycombinator.com/item?id=34897645
* _LogRocket_: https://news.ycombinator.com/item?id=34897645
* _Minimalytics_: https://github.com/nafey/minimalytics
* _Mixpanel_: https://satchel.com/web-analytics/ https://news.ycombinator.com/item?id=40432213
* _Plausible_: https://plausible.io/calmcode.io https://plausible.io/privacy-focused-web-analytics https://www.erichgrunewald.com/posts/ravi-zacharias-solves-the-problem-of-evil/ https://plausible.io/blog/remove-google-analytics
* _Posthog_: https://github.com/posthog/posthog https://www.pythonpodcast.com/posthog-product-analytics-episode-266/
* _Spindl_: https://www.spindl.xyz/
* _trench_: https://github.com/FrigadeHQ/trench
* _Vince_: https://github.com/vinceanalytics/vince https://www.vinceanalytics.com/
* _Umami_: https://github.com/umami-software/umami

## Beszel

https://github.com/henrygd/beszel

## Datadog

📜 https://docs.datadoghq.com/
📙 https://www.datadoghq.com/ebook/monitoring-modern-infrastructure/

🔍 QUERY
```sh
# FUNCTION: have to add func name to logs
service:bread-internal upsert_artist_split 

# ARTIST ID + STRING https://app.datadoghq.com/logs?query=apNjkATwdFGD%20withdrawal
apNjkATwdFGD withdrawal

# SERVICE
service:bread-internal  # https://app.datadoghq.com/logs?query=service%3Abread-internal
service: t3.util.split_payments.batch_send_invites  # https://app.datadoghq.com/apm/traces?query=%40_top_level%3A1%20service%3At3.util.split_payments.batch_send_invites%20env%3Aprod&cols=core_service%2Ccore_resource_name%2Clog_duration%2Clog_http.method%2Clog_http.status_code&historicalData=true&messageDisplay=inline&query_translation_version=v0&sort=desc&spanType=service-entry&start=1695760955144&end=1695933755144&paused=false

# CONSUMER
*eventbus.consumers* *bread* service:bread_split_consumer 
service:bread_cashout_consumer

# RESOURCE
env:prod AND resource_name:"POST /api/v1/split-payments/payees/<payee_ref_fktype>/<payee_ref_fid>/invites/<invite_code>/accept"

# EVERYTHING IN SERVICE EXCEPT SINGLE RESOURCE
env:stage service:appserv-split-payments-api -resource_name:"GET /healthz" 
```

🤖 TRACING https://ddtrace.readthedocs.io/en/stable/
* manually trace
```python
import ddtrace.tracer
import util.tracing

DD_SERVICE_NAME = "services.my_svc"

@util.tracing.keep_trace
@ddtrace.tracer.wrap(service=DD_SERVICE_NAME)
```
* auto-instrument
```
#!/bin/bash
exec /usr/bin/env \
  DD_SERVICE=my_app \
  DD_ENV=$(python) \
  DD_VERSION=${DD_VERSION:=0.1} \
  DD_GEVENT_PATCH_ALL=true \
  DD_CALL_BASIC_CONFIG=true \
  DD_LOGS_INJECTION=true \
  ddtrace-run gunicorn -c gconfig.py $* gunicorn_run:app
```

SEMANTICS
* _trace_: code path
* group of spans
* _trace id_: GUID attached to all spans
* _span_: trace subcomponent
* _service_: user-defined namespace
* _resource_: endpoint, function
```
service:t3.services.split_payments resource_name:services.split_payments.service.accept_invite
```

📑 LOGGING
* only retained for 15 days
* has log ingestion svc that UM used to add context to traces
* `log.info` ingested https://github.com/tommyboytech/t3/pull/12912/files
* ingestion from Cloudwatch
* there has got to be a better way than Hungarian notation i.e. putting `SPX` in each log line
* _retention_: how long DD stores logs
* _indexed_: DD collects https://www.datadoghq.com/blog/logging-without-limits/
* _source_: where log is coming from, tells DD which log pipeline to use [62]
* _service_: user defined unit of work vs. infra e.g. servers responsible for backend vs. server A/B/et al. https://docs.datadoghq.com/getting_started/tagging/

GRAPHS
* _line_: single metric over time [22]
* _stacked area_: metric across multiple resources [27]
* _bar_: sparse metric [27]
* _toplist_: list of resouces + metric [38]
* _change graph_: metric + change over time [39]
* _host map_: snapshot of resource health [40]

SUMMARIES
* latency by service [35]
* max latency [36]
* prod hosts [36]
* RPS [37]
* host growth [38]

ZA
* alternatives: New Relic, https://github.com/hyperdxio/hyperdx
* work > resource > metric [22]
* _tagging_: grouping mechanism i.e. frontend, backend + by env [46]
* dashboard example [60]
* UI: log explorer, service catalog

## Grafana

* _Grafana_: visualize metrics https://www.youtube.com/watch?v=9TJx7QTrTyo [14:00]
* _Loki_: Prometheus for logs https://utcc.utoronto.ca/~cks/space/blog/sysadmin/GrafanaLokiStructuredMetadata
* https://www.reddit.com/r/devops/comments/sevtqs/whats_your_monitoring_stack/
* profiling https://github.com/grafana/pyroscope

ALTERNATIVES 🗄️ `os/tools.md` monitoring
> replace with Textual? TUIs out there?
* _chartbrew_: can chart SQL https://github.com/chartbrew/chartbrew


## 🪨 Graphite

📜 https://github.com/graphite-project/graphite-web

---

https://github.com/benhoyt/graphyte
https://www.youtube.com/results?search_query=graphite+metrics

* _statsd_: https://github.com/jsocol/pystatsd https://www.youtube.com/watch?v=-6Hk9rcgM94 https://www.datadoghq.com/blog/statsd/ https://docs.datadoghq.com/developers/dogstatsd/ https://www.digitalocean.com/community/tutorials/an-introduction-to-tracking-statistics-with-graphite-statsd-and-collectd https://www.youtube.com/watch?v=R4kMwckrUlg Graphite visualization tool for statsd https://www.digitalocean.com/community/tutorials/how-to-configure-statsd-to-collect-arbitrary-stats-for-graphite-on-ubuntu-14-04

## Honey Badger

https://www.honeybadger.io/blog/golang-frameworks/

## 🔥 Logfire

📜 https://github.com/pydantic/logfire
🗄️ `data/eng.md` query engines > DataFusion

---

https://www.bitecode.dev/p/samuel-colvin-on-logfire-mixing-python
https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python
> I suppose the two things that make it different from some of the stuff that's come before is Logfire is built on Open Telemetry...the rails of where the data is being transferred are on an open standard. And if you decide you didn't want to use the Logfire platform anymore, you can send that data to anything else that supports Open Telemetry. But unlike lots of other companies in our space, instead of using open telemetry as an excuse to abandon the SDK space and just say, use the horrible open telemetry SDK directly, we have the Logfire package, which tries to make that super nice and easy to use.
> So instead of having to use ClickOps...there are things you can do in Logfire that you cannot and never been able to do in like one of the big incumbents like Datadog because it's just SQL. And it's obviously much easier to learn for you, much easier for LLMs to write...that's the hardest bit, there is SQL you can write which is enormously heavy to compute. And so we have to be able to find ways to process that without taking down other customers. The definition of DOS is that like the effort required to DOS is significantly lower than the effort required to process it.

HOW TO START
* https://news.ycombinator.com/item?id=24006697
* have a health check page https://www.thoughtworks.com/radar/techniques/health-check-pages
* https://hodovi.ch/blog/monitoring-django-applications
* https://news.ycombinator.com/item?id=36469147&
* https://jvns.ca/blog/2022/07/09/monitoring-small-web-services/
* status page https://github.com/harsxv/tinystatus https://statusgator.com/
* ⭐️ https://github.com/ankorstore/yokai
* _get metrics_: point Uptime Robot at a URL https://www.youtube.com/watch?v=o9ekAeoBXDs Lighthouse https://forgeperf.org/ https://www.thoughtworks.com/radar/tools?blipid=1158
* _measure metrics_: https://news.ycombinator.com/item?id=23360794
* _sink_: https://serversforhackers.com/s/process-monitoring https://blog.appoptics.com/the-four-golden-signals-for-monitoring-distributed-systems/ https://infrequently.org/2018/09/the-developer-experience-bait-and-switch/ https://3perf.com/talks/web-perf-101/ https://medium.baqend.com/web-performance-made-simple-fc61d81d0c0e http://mediatemple.net/blog/tips/low-hanging-fruit-web-performance/ https://medium.com/observability/want-to-debug-latency-7aa48ecbe8f7 https://ferdychristant.com/amp-the-missing-controversy-3b424031047 https://medium.freecodecamp.org/a-beginners-guide-to-website-optimization-2185edca0b72 https://panic.com/blog/mystery-of-the-slow-downloads/ https://github.com/monitoror/monitoror

## OpenTelemetry

---

* https://allthingsopen.org/articles/what-is-opentelemetry-add-django-application
* https://youtube.com/watch?v=jC1icupHlMs
* https://youtube.com/watch?v=ag2ykPO805M
* https://www.lucavall.in/blog/opentelemetry-a-guide-to-observability-with-go
* https://www.jvt.me/posts/2024/11/17/cobra-otel-lessons/
* https://rdrn.me/observability/
* https://opentelemetry.io/ 
* https://github.blog/2021-05-26-why-and-how-github-is-adopting-opentelemetry/
* https://news.ycombinator.com/item?id=37559506
* https://andydote.co.uk/2023/09/19/tracing-is-better/
* https://news.ycombinator.com/item?id=41570163
* https://betterstack.com/community/guides/observability/opentelemetry-collector/

## Prometheus

📜 https://prometheus.io/ https://github.com/prometheus/prometheus

* what: metrics strore
* how: time-series db
> servers...response times, resource usage, traffic, statuses: modern infrastructure generates a heck of a lot of data, and it all has to go somewhere. These days, that somewhere is usually Prometheus, or something very much like it. The Prometheus server can collect (or 'scrape') data from a range of sources, and you can then use a standard query language (PromQL) to ask questions about it, or use it to generate graphs and dashboards using the popular Grafana tool.

---

* https://sourcehut.org/blog/2020-07-03-how-we-monitor-our-services/ https://github.com/yolossn/Prometheus-Basics https://softwareengineeringdaily.com/2020/07/09/chronosphere-scalable-metrics-database-with-rob-skillington/ https://tech.marksblogg.com/clickhouse-prometheus-grafana.html https://monzo.com/blog/2018/07/27/how-we-monitor-monzo/ https://www.youtube.com/watch?v=9TJx7QTrTyo [13:00]

## Side Eye

https://www.hytradboi.com/2025/0244a435-8f3d-4c26-9526-4445853476f1-side-eye-ask-your-programs-anything
https://side-eye.io/

## 🟧 Signoz

📜 https://github.com/SigNoz/signoz

* they really dont want you to self-host https://signoz.io/docs/install/docker/
> The easiest way to run SigNoz is to use SigNoz Cloud - no installation, maintenance, or scaling needed.

PRICING 🗄️ `business.md` pricing
* $200/month sub per org 
* usage: logs ($0.3/GB ingested) traces ($0.3/GB ingested) metrics ($0.1/M samples)
* rentention: 15 days

---

> marking them as viable for now just so you can see how OpenTelemetry spec works

* https://news.ycombinator.com/item?id=33049046

# 🔭 PROFILING

📙
* Beazley ch. 14
* Tornhill https://pragprog.com/titles/atcrime2/your-code-as-a-crime-scene-second-edition/
🗄
* `feedback.md` debug
* `linux.md` tracing
* `telemetry.md`

PG http://paulgraham.com/popular.html
> It might be a good idea to have an active profiler - to push performance data to the programmer instead of waiting for him to come asking for it.
> Part of the problem here is social. Language designers like to write fast compilers. That's how they measure their skill. They think of the profiler as an add-on, at best. But in practice a good profiler may do more to improve the speed of actual programs written in the language than a compiler that generates fast code. Here, again, language designers are somewhat out of touch with their users. They do a really good job of solving slightly the wrong problem.
> A good language, as everyone knows, should generate fast code. But in practice I don't think fast code comes primarily from things you do in the design of the language. As Knuth pointed out long ago, speed only matters in certain critical bottlenecks. And as many programmers have observed since, one is very often mistaken about where these bottlenecks are. So, in practice, the way to get fast code is to have a very good profiler, rather than by, say, making the language strongly typed. You don't need to know the type of every argument in every call in the program. You do need to be able to declare the types of arguments in the bottlenecks. And even more, you need to be able to find out where the bottlenecks are.

## benchmark

> There are lies, damned lies and benchmarks. https://github.com/pydantic/jiter https://news.ycombinator.com/item?id=42501532 https://news.ycombinator.com/item?id=43317592 https://news.ycombinator.com/item?id=43318130 https://blog.nelhage.com/post/cpython-tail-call/
🎗️ https://danluu.com/anon-benchmark/ https://danluu.com/why-benchmark/ https://jpcamara.com/2024/12/01/speeding-up-ruby.html https://benhoyt.com/writings/go-version-performance-2024/

* _millisecond (ms)_: 10^−3 (one-thousandth of a second)
* _microsecond (µs)_: 10^−6 (one-millionth of a second)
* _nanosecond (ns)_: 10^−9 (one-billionth of a second)

LINUX
* _time_: `/usr/bin/time -v` detailed output w/ memory stats https://github.com/egoist/dum https://news.ycombinator.com/item?id=30226742
```sh
cmd:
	@time ur makefile cmd
```
* _timedatectl_: nanoseconds
* _hyperfine_: https://github.com/sharkdp/hyperfine inode caching https://news.ycombinator.com/item?id=42179600

PYTHON
* https://github.com/airspeed-velocity/asv
* https://www.pythonmorsels.com/cli-tools/#timeit
* _fastero_: 🎯 timeit alternative https://github.com/wasi-master/fastero
* _time_: https://superfastpython.com/benchmark-execution-time * https://wsvincent.com/algorithms-binary-search/
* _timeit_: 🎯 https://www.pythonmorsels.com/cli-tools/ https://www.blog.pythonlibrary.org/2020/04/14/an-overview-of-profiling-tools-for-python/ https://realpython.com/python-f-strings/#comparing-performance-f-string-vs-traditional-tools
```python
# try this instead

# The "timeit" module lets you measure the execution
# time of small bits of Python code
# https://www.youtube.com/watch?v=EcGWDNlGTNg
import timeit
timeit.timeit('"-".join(str(n) for n in range(100))', number=10000)
timeit.timeit('"-".join([str(n) for n in range(100)])', number=10000)
timeit.timeit('"-".join(map(str, range(100)))', number=10000)

# https://stackoverflow.com/a/7523810/6813490
from timeit import Timer
# doesn't manifest savings in small collections
names_list = ['alice', 'bob', 'candace']
names_set = set(['alice', 'bob', 'candace'])

# setup large collection of numbers and see what happens then
def lookup_list(l):
    return 'alice' in l
def lookup_set(s):
    return 'alice' in s
def cast_to_timer(func, args):
	return Timer(lambda: func(args))
def timeit_ms(func):
	return print(func.timeit(number=1000))
if __name__=='__main__':
    timeit_ms(cast_to_timer(lookup_list, names_list))
    timeit_ms(cast_to_timer(lookup_set, names_set))
```

## timeit

https://github.com/koaning/memo/
https://calmcode.io/course/memo/introduction
https://eli.thegreenplace.net/2025/benchmarking-utility-for-python/

---

https://github.com/zachvalenta/capp-brand-enablement

I have a decorator:
```python
@dataclass
class Util:
    @staticmethod
    def timeit(func=None, *, name=None):
        if func is None:
            return partial(timeit, name=name)
        @wraps(func)
        def wrapper(*args, **kwargs):
            start = time()
            result = func(*args, **kwargs)
            end = time()
            logger.info(f"{name or func.__name__} took {round(end - start, 1)} seconds")
            return result
        return wrapper
```

that I'm using to annotate other methods:
```python
@staticmethod
@Util.timeit
def load_eclipse_tsv():
```

I'd like to make some updates:
* make it just a normal function instead of a class-based static method
* so that it can be used in the REPL: `timeit(load_eclipse_tsv())`
* the function should just print execution time but the return value is coming from whatever function/method it wraps


## start here

https://entropicthoughts.com/practices-of-reliable-software-design
> tracemalloc is built-in to Python, and pretty granular in what it measures; the downside is that not all 3rd party compiled extensions integrate tracemalloc, so for example Polars’ memory allocations won’t show up there https://pythonspeed.com/articles/identifying-resource-leaks-with-pytest/
* https://claude.ai/chat/dd676259-77ee-4cb7-b35d-193695eb80d6
* https://claude.ai/chat/cb57a07d-5aa4-48f2-a568-d75bf3ca2350
> you've extracted everything else from this prompt other than the benchmarking code
```python
from memory_profiler import profile

@profile
def read_standard(path):
    return pl.read_csv(path)

@profile
def read_chunked(path, chunk_size=100_000):
    chunks = []
    for chunk in pl.read_csv(path, rechunk=True).iter_chunks(chunk_size):
        chunks.append(chunk)
    return pl.concat(chunks)
```
* https://byroot.github.io/ruby/json/2024/12/15/optimizing-ruby-json-part-1.html
* _path_: heuristic for thinking about what to optimize i.e. 99% of your app's execution branches can probably be pretty slow https://blog.phusion.nl/2018/09/18/migrating-passenger-from-cxx-to-go/
* https://calmcode.io/shorts/perfplot
* https://thume.ca/2023/12/02/tracing-methods/
* https://blog.miguelgrinberg.com/post/is-python-really-that-slow
* https://martinheinz.dev/blog/13
* https://rednafi.com/python/preallocated_list/
* https://computers-are-fast.github.io/
* https://tech.marksblogg.com/faster-python.html
* https://pycon-archive.python.org/2024/schedule/presentation/36/index.html
* https://github.com/tonybaloney/perflint 
* https://realpython.com/python-timer/
* https://www.roguelynn.com/words/tracing-fast-and-slow/
* https://pythonspeed.com/articles/faster-json-library/
* https://wsvincent.com/python-optimizations-with-guido/
* https://madebyme.today/blog/python-dict-vs-curly-brackets/
* https://realpython.com/python-profiling/
* https://pythonspeed.com/articles/measuring-python-performance/
* https://pythonspeed.com/memory/
* https://switowski.com/blog/how-to-benchmark-python-code/
* https://pythonspeed.com/articles/blocking-cpu-or-io/
* https://pythonspeed.com/articles/live-debugging-python/
* https://log.beshr.com/python-311-speedup-part-1/
* https://www.markkeller.dev/2018-07-14-optimize_python/
* https://codesolid.com/how-do-i-profile-python-code/
* https://adamj.eu/tech/2023/03/02/django-profile-and-improve-import-time/
* `py3 -m trace --trace example.py`
* https://www.petermcconnell.com/posts/perf_eng_with_py12/
* https://www.youtube.com/watch?v=2hWfLiRGaNM
* https://github.com/s7nfo/Cirron
* https://bernsteinbear.com/blog/silly-perf/
* where to put perf? https://roadmap.sh/best-practices/backend-performance
> The notes on benchmark performance graphs often read "higher is better" and performance improvements are even called "optimisations". But the truth is, at least as a user, once performance reaches a satisfactory level - enough for your own data analysis to complete in a reasonable about of time - there is no further benefit from increased speed. Instead of being called "performance optimisation" it should probably be called "performance satisfaction" as once it is satisfactory you have finished. Usability is different. The whole point of computers is as an aid to productivity so user-friendliness is actually the bit you want to optimise. Unlike speed, being easier to use is always better and there is very little limit to that. So it's "usability improvements" that should be called "optimisations" but perhaps the relevant ships on all of these terms have sailed. https://csvbase.com/blog/6

## options

* _asv_: https://github.com/airspeed-velocity/asv
* _austin_: frame stack sampler https://github.com/P403n1x87/austin https://github.com/P403n1x87/austin-tui https://talkpython.fm/episodes/show/265/why-is-python-slow 54:00
* _cProfile_: 🎯 https://www.pythonmorsels.com/cli-tools/ https://martinheinz.dev/blog/64 https://hakibenita.com/django-rest-framework-slow https://stackabuse.com/why-does-python-code-run-faster-in-a-function/ https://adamj.eu/tech/2023/07/23/python-profile-section-cprofile/ https://www.pythonmorsels.com/cli-tools/#other-python-related-tools
* _Fil_: https://pythonspeed.com/products/filmemoryprofiler/ https://pythonspeed.com/articles/memory-profiler-data-scientists/
* _FunctionTrace_: 🎯 https://functiontrace.com/ https://news.ycombinator.com/item?id=36605730
* _gosivy_: 🎯 CPU utilization, heap https://github.com/nakabonne/gosivy https://github.com/nakabonne/ali/releases/tag/v0.7.0
* _hunter_: https://github.com/ionelmc/python-hunter
* _instruments_: https://registerspill.thorstenball.com/p/did-you-know-about-instruments
* _line profiler_: https://github.com/pyutils/line_profiler https://news.ycombinator.com/item?id=41910590
* _memory profiler_: https://github.com/pythonprofilers/memory_profiler https://news.ycombinator.com/item?id=27025829
* _memray_: 🎯 https://github.com/bloomberg/memray https://textual.textualize.io/blog/2024/02/20/remote-memory-profiling-with-memray/ https://realpython.com/podcasts/rpp/128/ https://talkpython.fm/episodes/show/425/memray-the-endgame-python-memory-profiler https://news.ycombinator.com/item?id=41910590
* _perf_: Linux https://pycon-archive.python.org/2024/schedule/presentation/69/index.html
* _phlare_: Grafana https://martinheinz.dev/blog/89
* _pyflame_: https://medium.com/zendesk-engineering/hunting-for-memory-leaks-in-python-applications-6824d0518774 
* _pyheat_: https://github.com/csurfer/pyheat
* _pyinstrument_: 🎯 https://news.ycombinator.com/item?id=41910590 https://github.com/joerick/pyinstrument https://calmcode.io/course/pyinstrument/introduction https://daniel.feldroy.com/posts/2025-03-using-pyinstrument-to-profile-fasthtml-apps
* _pyroscope_: 🎯 https://github.com/pyroscope-io/pyroscope https://news.ycombinator.com/item?id=43290917 https://github.com/grafana/pyroscope https://grafana.com/blog/2023/04/19/how-to-troubleshoot-memory-leaks-in-go-with-grafana-pyroscope/
* _pystack_: https://talkpython.fm/episodes/show/419/debugging-python-in-production-with-pystack https://martinheinz.dev/blog/101
* _pyspy_: 🎯 https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust https://tinkering.xyz/fmo-optimization-story/ https://www.youtube.com/watch?v=1EZ8oqjLun0 https://jvns.ca/blog/2018/12/23/2018--year-in-review/
* _tracy_: https://github.com/wolfpld/tracy
* _speedscope_: https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust
* _Sciagraph_: https://news.ycombinator.com/item?id=31826872
* _Valgrind_: https://github.com/benfred/py-spy/ https://www.gauge.sh/blog/parsing-python-asts-20x-faster-with-rust

## types

* _sampling_: interrupts program, snapshots stack trace, aggregates sample of these interruptions and tells you where you're spending most of your time
> Sampling profilers, the most common performance debugging tool, are notoriously bad at debugging problems caused by tail latency because they aggregate events into averages. But tail latency is, by definition, not average. https://danluu.com/perf-tracing/
> The general shape of it is you take a system and you point a tool at it that stops the world every so often. Let's say every hundred microseconds maybe. And it stops the world and asks, where are you right now? And it looks at where the instruction pointer is, what are we currently executing? And it generally looks at the stack trace, how did you get here? And then it writes this down and it lets the program keep going. And profilers only really differ on how do they stop the world and how do they write this down. My favorite is the Linux kernel profiler. It's called perf, and it just uses a bunch of hardware features to get an interrupt at exactly the right moment in time. And then it just very quickly writes down the stack trace in this compressed format. It's very optimized. And then you take all these stack traces. The profile is really just a list of stack traces and sometimes a little bit of augmented information, but that's fundamentally the core idea. And then you present it to the user in some way that adds them up. And like I say, the key thing is it tells you, okay, 30% of the stack traces ended in the function foo. That's a hotspot. You're spending 30% of your time there. https://signalsandthreads.com/performance-engineering-on-hard-mode/

---

* "perf matters": stablizer, memory layout https://www.youtube.com/watch?v=r-TLSBdHe1A
* BYO https://blog.mattstuchlik.com/2024/02/16/counting-syscalls-in-python.html https://jvns.ca/blog/2017/12/02/taking-a-sabbatical-to-work-on-ruby-profiling-tools/ https://jvns.ca/blog/2017/12/17/how-do-ruby---python-profilers-work-/ https://pythonspeed.com/articles/custom-python-profiler/
* statistical profiler https://www.youtube.com/watch?v=d5SGUscT2GA Linux perf https://realpython.com/python312-perf-profiler/ https://github.com/brendangregg/FlameGraph https://hacker-tools.github.io/program-introspection/
* performance profiler https://www.youtube.com/watch?v=CjG_Ub_gCL4 [2:10]
* sampling profiler

# 🔬 TRACING

🗄
* processes
* `python.md` profiling
* `telemetry.md` tracing
📚
* Evans debug tools
* Evans perf
* Evans strace
* Evans tracing

VOCAB
* _monitor_: track errors; continuous
* _trace_: capture exact sequence of events/function calls with timestamps and context
* _profile_: aggregate stats re: resource usage (CPU time, memory, etc.) by function/line

TOOLS
* _beetrace_: 🐍 https://github.com/furkanonder/beetrace

---

flamegraph https://github.com/laixintao/flameshow

https://events.linuxfoundation.org/wp-content/uploads/2022/10/elena-zannoni-tracing-tutorial-LF-2021.pdf

* strace, ptrace https://nullprogram.com/blog/2018/06/23/
* magic trace https://github.com/janestreet/magic-trace
* ptrace https://medium.com/@lizrice/a-debugger-from-scratch-part-1-7f55417bc85f
* strace https://jvns.ca/blog/2021/04/03/what-problems-do-people-solve-with-strace/
* dtruss https://blog.safia.rocks/post/173241985600/unraveling-rm-what-happens-when-you-run-it

❌ normal debugging: know the language, look at src, print statements/debugger
✅ `strace` debugging: 'these are the system calls your program is making'
📝 don't run strace on production processes (or anything that needs to run at normal speed)

UM
* previous https://developers.signalfx.com/basics/apm.html
> Datadog under hood uses monkey patches whereas signalfx required manual monkey patch
> how does Datadog work under the hood?
* __span__: unit of tracing https://www.elastic.co/guide/en/apm/get-started/current/transaction-spans.html https://docs.splunk.com/observability/apm/span-formats.html
* start/end time, span ID
* can contain / be contained by other spans
* use trace IDs
* tracing system can send span information across network between systems, so you can track a thread of execution across multiple systems
* https://www.youtube.com/watch?v=idDu_jXqf4E https://www.youtube.com/watch?v=YGWA54nEEy0 https://www.youtube.com/watch?v=r8UvWSX3KA8

za
* https://github.com/itamarst/eliot
* https://www.brandur.org/request-ids
* https://microservices.io/patterns/observability/distributed-tracing.html
* https://softwareengineering.stackexchange.com/questions/158198/http-response-header-for-a-unique-request-id-for-rest-service
* https://www.roguelynn.com/words/tracing-fast-and-slow/
* https://danluu.com/perf-tracing/
* https://github.com/JonasKs/django-guid
* https://danluu.com/tracing-analytics/
* https://netflixtechblog.com/building-netflixs-distributed-tracing-infrastructure-bb856c319304

## bpf

---

https://cgmathprog.home.blog/2025/02/17/bpf-or-how-i-stopped-worrying-and-loved-the-kernel/
EBPF https://www.brendangregg.com/
* XDP/eBPF https://mas-bandwidth.com/xdp-for-game-programmers/
* https://blog.smidt.dev/posts/0003/
* _flamegraph_: visualization for CPU usage https://heap.io/blog/engineering/basic-performance-analysis-saved-us-millions https://flamegraph.com/ https://github.com/laixintao/flameshow https://terminaltrove.com/flamelens/
* https://www.youtube.com/watch?v=bGAVrtb_tFs
* https://coroot.com/blog/engineering/instrumenting-python-gil-with-ebpf/
* https://github.com/ZingerLittleBee/netop
* https://sazak.io/articles/an-applied-introduction-to-ebpf-with-go-2024-06-06
* https://news.ycombinator.com/item?id=27435081
* https://www.brendangregg.com/blog/2022-04-15/netflix-farewell-1.html
* https://ebpf.io/what-is-ebpf/ https://softwareengineeringdaily.com/2023/03/06/ebpf-with-thomas-graf/
* https://www.polarsignals.com/blog/posts/2023/10/04/profiling-python-and-ruby-with-ebpf
* https://about.gitlab.com/blog/2022/11/28/how-we-diagnosed-and-resolved-redis-latency-spikes/
* https://softwareengineeringdaily.com/2022/07/15/continuous-profiling-using-ebpf-with-frederic-branczyk/
* https://github.com/keyval-dev/odigos
* https://github.com/google/gops
* https://thume.ca/2023/12/02/tracing-methods/

# 🟨 ZA

> And there's actually this new feature that we had added to our help Slack channel. There's a channel that's just alerting us when a person logs into the tool. And we get their username, and we can easily find where they are in the office, and we can go up and talk to them. One of the engineers on the team added a very rough estimation of how close they are to you. So, it'll tell you, "Oh, this person's right around the corner. This person is 54 meters away from you, or this person is two floors above you." And so, I don't know, even just knowing where they're located and having an awareness of, "Oh, I just walked by," there is a lot of connection you can build. And I feel like the design itself becomes just stronger by having that constant iteration that is informed by these discussions with real users. https://signalsandthreads.com/from-the-lab-to-the-trading-floor/

## analytics

🗄
* `db.md` data eng / OLAP
* `db.md` non-relational / time series

FEATURES
* feature flagging `system.md` deployment / feature flagging
* _event collection_: store user events e.g. Segment https://github.com/ksensehq/eventnative https://news.ycombinator.com/item?id=24737244
* _segmentation_: A/B testing https://www.bwplotka.dev/2024/go-microbenchmarks-benchstat/
* segmented = care about individual (paying) user https://www.pythonpodcast.com/posthog-product-analytics-episode-266/ 8:00
* non-segmented = don't care about individual (non-paying) user; Google Analytics https://www.pythonpodcast.com/posthog-product-analytics-episode-266/ 8:00
* _session replay_: view user session + their browser info, req/res from browser dev tools https://www.youtube.com/watch?v=UWpzJ7bqoF8

SEMANTICS
* _analytics_: aka customer data infra
* howto: use cookies https://marvinblum.de/blog/server-side-tracking-without-cookies-in-go-OxdzmGZ1Bl https://healeycodes.com/privacy-focused-analytics-from-scratch https://www.youtube.com/watch?v=SMRaHSZiwWE
* howto: sessions https://pcmaffey.com/roll-your-own-analytics
> Track sessions, not people, mostly events. All I want to know is referrer and some session metadata like language, timezone, and device. And then I want to log what happened using events and summarize that in the session table.
> document.referrer where are visitors coming from?
> waitlist -(bool) did they signup for the waitlist?
* _clickstream_: path of links/buttons followed by user
* personal analytics: for personal site, likes on social sites https://www.arp242.net/personal-analytics.html

## incidents

* _fault_: when something goes wrong [Kleppmann 7]
* _incident_: when system stops serving user https://softwareengineeringdaily.com/2019/10/16/incident-reproduction-with-tammy-butow/ 
* _monitor_: metric you care about
* _alert_: conditional re: monitor
* _notification fatigue_: when alerts stop mattering https://brandur.org/alerting
* _management_: https://github.com/monzo/response https://response.pagerduty.com/ https://netflixtechblog.com/introducing-dispatch-da4b8a2a8072 Pager Duty alternative https://github.com/target/goalert
* https://x.com/ycombinator/status/1858555769513537751
* _post-mortem_: https://blog.github.com/2018-10-30-oct21-post-incident-analysis/ https://status.sr.ht/issues/2020-10-08-git.sr.ht-disk-usage/

## Honeycomb

https://www.honeycomb.io/

## logging

📙 Kreps i love logs
🗄
* `python/stdlib.md` logging
* `serde.md` JSON

LEVELS
* debug
* info
* warn
* error
* fatal

LOG STORES
* BYO https://avi.im/blag/2024/s3-log/
* _parseable_: https://github.com/parseablehq/parseable

FORMAT https://github.com/charmbracelet/log
* _JSONL_: https://github.com/textualize/toolong

TOOLING 🗄️ `golang.md` `python.md`
* https://github.com/dloss/klp
* https://github.com/aurc/loggo
* _Axiom_: https://axiom.co/ https://github.com/axiomhq https://repobeats.axiom.co/ cheaper than CloudWatch? https://x.com/AxiomFM/status/1842206872813674807
* _fblog_: JSON log viewer https://github.com/brocode/fblog
* _hl_: https://github.com/pamburus/hl
* _toolong_: 🎯 https://github.com/textualize/toolong https://calmcode.io/shorts/toolong.py

FS LOCATIONS https://missing.csail.mit.edu/2019/machine-introspection/ 🗄️ `linux.md` fs
> Traditionally, logs were all stored in `/var/log`, and many still are. Usually there's a file or folder per program.
> There's also a kernel log that you can see using the `dmesg` command. This used to be available as a plain-text file, but nowadays you often have to go through `dmesg`.
> Finally, there is the "system log", which is increasingly where all of your log messages go. On most, though not all, Linux systems, that log is managed by `systemd`, the "system daemon", which controls all the services that run in the background (and much much more at this point). That log is accessible through the somewhat inconvenient `journalctl` tool if you are root, or part of the admin or wheel groups.

---

* Clickhouse https://github.com/mr-karan/logchef
* buffered https://blog.bytebytego.com/p/how-amex-processes-millions-of-daily

```txt
loguru (what you're using) - Great defaults, structured out of the box
structlog - Most flexible, industrial strength
python-json-logger - Simple JSON logging
standard logging + custom formatter (shown above)

The broader domain here is observability, which includes:
Metrics
Traces
Logs (what we're discussing)
Event correlation
System state

Narrower focus areas:
Log routing
Log aggregation
Log parsing
Log retention

Key considerations for structured logging:
Performance impact of serialization
Storage costs of structured vs unstructured
Query capabilities needed
Integration with existing tools
```

https://www.openmymind.net/2012/4/11/Lets-Talk-About-Logging/
* https://calmcode.io/course/vector/introduction
* you'll need to rotate if you don't want to store everything 
* live log view `tail -f foo.log`
* https://github.com/ptmcg/logmerger
* https://github.com/ReagentX/Logria
* https://github.com/tstack/lnav
* https://github.com/textualize/toolong
* https://logdy.dev/
* https://github.com/bensadeh/tailspin
* https://terminaltrove.com/logss/
* https://github.com/Textualize/toolong
* GoAccess: https://news.ycombinator.com/item?id=26848827 https://github.com/allinurl/goaccess https://benhoyt.com/writings/replacing-google-analytics/
* request ID https://jvns.ca/blog/2022/12/07/tips-for-analyzing-logs/
* BYO https://news.ycombinator.com/item?id=37600019 https://github.com/Dicklesworthstone/automatic_log_collector_and_analyzer
* structured https://betterstack.com/community/guides/logging/logging-in-go/ https://news.ycombinator.com/item?id=37047785
* rolling https://github.com/natefinch/lumberjack
* https://www.16elt.com/2023/01/06/logging-practices-I-follow/
* https://jvns.ca/blog/2022/12/07/tips-for-analyzing-logs/
* https://tech.marksblogg.com/minimalist-guide-tutorial-flume.html
* log to stdout https://www.youtube.com/watch?v=aQikNWEaJUQ
* https://blog.twitter.com/engineering/en_us/topics/infrastructure/2021/logging-at-twitter-updated
* https://github.com/GothenburgBitFactory/clog
https://news.ycombinator.com/item?id=30394152
> If you are building an API, having a mechanism that provides detailed logs—including the POST bodies passed to the API—is invaluable. It’s an inexpensive way of maintaining a complete record of what happened with your application—invaluable for debugging, but also for tricks like replaying past API traffic against a new implementation under test. Logs like these may become infeasible at scale, but for a new project they’ll probably add up to just a few MBs a day—and they’re easy to prune or switch off later on if you need to. https://simonwillison.net/2021/Jul/1/pagnis/
* _Logflare_: middleman btw app and storage; most logging services (datadog) make money by marking up storage; available as Cloudflare app https://runninginproduction.com/podcast/11-logflare-is-a-log-management-and-event-analytics-platform
* _sources_: clickstream, proxy, web server, app server
* event streams https://apenwarr.ca/log/20190216
* _formats_: CLF, Amazon, Nginx https://github.com/allinurl/goaccess common log format https://vicki.substack.com/p/logs-were-our-lifeblood-now-theyre https://brandur.org/logfmt https://medium.com/hiredscore-engineering/logging-lets-do-it-right-41d568d3bfcd
* _tools_: Logstash https://github.com/edmocosta/tuistash Fluentd https://github.com/itamarst/eliot https://news.ycombinator.com/item?id=21461617 https://github.com/rcoh/angle-grinder https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-log-analyzers https://github.com/allinurl/goaccess Honeycomb https://www.honeycomb.io/blog/tell-me-more-nginx/ https://hynek.me/talks/beyond-grep/
* _sink_: log growth roughly linear https://www.youtube.com/watch?v=-6Hk9rcgM94 https://stripe.com/gb/blog/canonical-log-lines

## uptime / healthcheck

---

* https://onlineornot.com/ https://maxrozen.com/on-four-years-running-saas-competitive-market
* Kuma, Pager Duty / Gotify https://kiranet.org/posts/self-hosting-like-its-2025/ https://kiranet.org/posts/self-hosting-like-its-2025/
* useful 404 https://calmcode.io/static/data
* https://calmcode.io/course/better-uptime/overview
UPTIME / HEALTHCHECK / HEARTBEAT
* https://status.calmcode.io/
* https://news.ycombinator.com/item?id=41452339
* https://pythonbytes.fm/episodes/show/395/pythont-compatible-packages
* baseline https://healthchecks.io/
* db connection https://www.youtube.com/watch?v=GT9WmExDbXQ
* downstream services
* aaS: UptimeRobot, Checkly, lcurl https://www.youtube.com/watch?v=um24VlkkqGo https://github.com/brotandgames/ciao
> I setup a 3rd party service to monitor the heartbeats and the return code to validate they are up and properly returning what I expect, notify me if not. I don't have to do sophisticated response processing at the 3rd party service because I can just use http return codes 99% of the time. The detailed response checking is done at the heartbeat level, then a response code generated. https://news.ycombinator.com/item?id=22823230
* https://updown.io/
* https://github.com/megaease/easeprobe
