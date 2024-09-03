# ⛩️

## 参考

📙 https://sre.google/sre-book/table-of-contents/

## 进步

* _23_: Datadog with CRD
* _17_: Google SRE book first 20 chapters

# 🩻 MONITORING

🗄 `python.md` profiling

---

TAXONOMY
* user sessions https://news.ycombinator.com/item?id=40318542 https://jam.dev/ https://trackjs.com/
* tracing

PROVIDERS https://sourcehut.org/blog/2020-07-03-how-we-monitor-our-services
> taxonomy from Sentry and this https://rdrn.me/observability/
* _Grafana_: visualize metrics https://www.youtube.com/watch?v=9TJx7QTrTyo [14:00] https://www.reddit.com/r/devops/comments/sevtqs/whats_your_monitoring_stack/
* replace with Textual? https://textual.textualize.io/
* _HyperDX_: 🎯 https://github.com/hyperdxio/hyperdx
> HyperDX is an open-source observability platform that unifies all three pillars of observability: logs, metrics and tracing. With it, you can correlate end-to-end and go from browser session replay to logs and traces in just a few clicks. The platform leverages ClickHouse as a central data store for all telemetry data, and it scales to aggregate log patterns and condense billions of events into distinctive clusters. Although you can choose from several observability platforms, we want to highlight HyperDX for its unified developer experience. https://www.thoughtworks.com/radar/platforms/hyperdx
* _Jam_: error reporting https://jam.dev/ https://news.ycombinator.com/item?id=40318542 🗄️ `test.md` friction logs
* _Prometheus_: time-series db as metrics store https://sourcehut.org/blog/2020-07-03-how-we-monitor-our-services/ https://prometheus.io/docs/introduction/overview/ https://github.com/yolossn/Prometheus-Basics https://softwareengineeringdaily.com/2020/07/09/chronosphere-scalable-metrics-database-with-rob-skillington/ https://tech.marksblogg.com/clickhouse-prometheus-grafana.html https://monzo.com/blog/2018/07/27/how-we-monitor-monzo/ https://www.youtube.com/watch?v=9TJx7QTrTyo [13:00]
* _Moderato_: 🎯 https://github.com/moderato-app/live-pprof
* _New Relic_: 
* _Rollbar_: https://pythonbytes.fm/episodes/show/24/i-have-a-local-pypi-server-and-so-do-you 
* _Sentry_: suspected commit behind break

https://www.thediff.co/archive/the-data-business-at-three-resolutions/

OPENTELEMETRY
* https://opentelemetry.io/ 
* https://github.blog/2021-05-26-why-and-how-github-is-adopting-opentelemetry/
* https://news.ycombinator.com/item?id=37559506
* https://andydote.co.uk/2023/09/19/tracing-is-better/

UPTIME / HEALTHCHECK / HEARTBEAT
* https://news.ycombinator.com/item?id=41452339
* https://pythonbytes.fm/episodes/show/395/pythont-compatible-packages
* baseline https://healthchecks.io/
* db connection https://www.youtube.com/watch?v=GT9WmExDbXQ
* downstream services
* aaS: UptimeRobot, Checkly, lcurl https://www.youtube.com/watch?v=um24VlkkqGo https://github.com/brotandgames/ciao
> I setup a 3rd party service to monitor the heartbeats and the return code to validate they are up and properly returning what I expect, notify me if not. I don't have to do sophisticated response processing at the 3rd party service because I can just use http return codes 99% of the time. The detailed response checking is done at the heartbeat level, then a response code generated. https://news.ycombinator.com/item?id=22823230
* https://updown.io/
* https://github.com/megaease/easeprobe

* _chaos engineering_: trigger fault to see if it causes a failure https://github.com/powerfulseal/powerfulseal
* https://news.ycombinator.com/item?id=40573790&utm_term=comment

https://github.com/pydantic/logfire
https://news.ycombinator.com/item?id=36469147&
https://jvns.ca/blog/2022/07/09/monitoring-small-web-services/
have a health check page https://www.thoughtworks.com/radar/techniques/health-check-pages
https://www.ryancheley.com/2023/10/29/error-culture/

* Datadog alternative https://news.ycombinator.com/item?id=33049046 https://github.com/SigNoz/signoz
* users online https://analytics.usa.gov/
* uptime https://news.ycombinator.com/item?id=25553445 depends on system component https://www.openmymind.net/Im-Not-Sold-On-High-Availability/
* _dead man's switch_: cease operation in absence of human operator e.g. carts at airport [Conery 6; think his usage wrong]

🗄 `link.md` speed
> rf `link.md` then this section

https://www.semicolonandsons.com/episode/error-tracking-and-monitoring
* exception reporting
* logging (production, retention, search)
* downtime alerting
* system monitoring
* financial reporting

* https://hodovi.ch/blog/monitoring-django-applications
* _path_: heuristic for thinking about what to optimize i.e. 99% of your app's execution branches can probably be pretty slow https://blog.phusion.nl/2018/09/18/migrating-passenger-from-cxx-to-go/

load parameters
* _load parameter_: metric; way to describe load on system [Kleppmann 11]
* _node_: CPU, mem, storage 
* _service_: req volume (RPS https://stackexchange.com/performance), simultaneously active users, error rate (5xx per M req), uptime (five nines https://sourcehut.org/blog/2020-06-10-how-graphql-will-shape-the-alpha/)
* _db_: queries per req (statsd) https://www.youtube.com/watch?v=-6Hk9rcgM94 ratio of reads to write, hit rate on cache [Kleppmann 11]

* _percentiles_: p50 (median) p90 (worst case); mean doesn't tell you how many nodes/users
* _skew_: uneven distibution re: load across worker processes [Kleppmann 20] what prevents run time of batch job being data divided by throughput

https://news.ycombinator.com/item?id=24006697

* _statsd_: https://github.com/jsocol/pystatsd https://www.youtube.com/watch?v=-6Hk9rcgM94 https://www.datadoghq.com/blog/statsd/ https://docs.datadoghq.com/developers/dogstatsd/ https://www.digitalocean.com/community/tutorials/an-introduction-to-tracking-statistics-with-graphite-statsd-and-collectd https://www.youtube.com/watch?v=R4kMwckrUlg Graphite visualization tool for statsd https://www.digitalocean.com/community/tutorials/how-to-configure-statsd-to-collect-arbitrary-stats-for-graphite-on-ubuntu-14-04

how to start
* _get metrics_: point Uptime Robot at a URL https://www.youtube.com/watch?v=o9ekAeoBXDs https://statusgator.com/ Lighthouse https://forgeperf.org/ https://www.thoughtworks.com/radar/tools?blipid=1158
* _measure metrics_: https://news.ycombinator.com/item?id=23360794
* _sink_: https://serversforhackers.com/s/process-monitoring https://blog.appoptics.com/the-four-golden-signals-for-monitoring-distributed-systems/ https://infrequently.org/2018/09/the-developer-experience-bait-and-switch/ https://3perf.com/talks/web-perf-101/ https://medium.baqend.com/web-performance-made-simple-fc61d81d0c0e http://mediatemple.net/blog/tips/low-hanging-fruit-web-performance/ https://medium.com/observability/want-to-debug-latency-7aa48ecbe8f7 https://ferdychristant.com/amp-the-missing-controversy-3b424031047 https://medium.freecodecamp.org/a-beginners-guide-to-website-optimization-2185edca0b72 https://panic.com/blog/mystery-of-the-slow-downloads/ https://github.com/monitoror/monitoror

black box
* _black box_: user-facing; symptom-oriented
* _options_: https://news.ycombinator.com/item?id=23880071

white box
* _white box_: internals; cause-oriented

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

## incidents

* _fault_: when something goes wrong [Kleppmann 7]
* _incident_: when system stops serving user https://softwareengineeringdaily.com/2019/10/16/incident-reproduction-with-tammy-butow/ 
* _monitor_: metric you care about
* _alert_: conditional re: monitor
* _notification fatigue_: when alerts stop mattering https://brandur.org/alerting
* _management_: https://github.com/monzo/response https://response.pagerduty.com/ https://netflixtechblog.com/introducing-dispatch-da4b8a2a8072 Pager Duty alternative https://github.com/target/goalert
* _post-mortem_: https://blog.github.com/2018-10-30-oct21-post-incident-analysis/ https://status.sr.ht/issues/2020-10-08-git.sr.ht-disk-usage/

## metrics

---

* _frecency_: frequency + recency https://missing.csail.mit.edu/2020/shell-tools/ https://github.com/rupa/z

SEMANTICS https://www.datadoghq.com/ebook/monitoring-modern-infrastructure/
* _event_: change to system e.g. build, release, add/substract host/container, alert going off
* _metric_: value from system at a particlar point in time
* _throughput_: amount of work per unit of time e.g. RPS
* _latency_: time required to complete unit of work e.g. % of requests returns with X time e.g. 99% of requests return w/in 0.2 ms https://www.youtube.com/watch?v=FqR5vESuKe0
* metrics: success rate, error rate
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

## tracing

🗄 `linux.md` tracing

---

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

# 🟨 ZA

## analytics

🗄
* `db.md` data eng / OLAP
* `db.md` non-relational / time series

FEATURES
* feature flagging `system.md` deployment / feature flagging
* _event collection_: store user events e.g. Segment https://github.com/ksensehq/eventnative https://news.ycombinator.com/item?id=24737244
* _segmentation_: A/B testing
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

PROVIDERS
* howto: server logs (GoAccess), CSS https://herman.bearblog.dev/how-bear-does-analytics-with-css/
* _Amplitude_: https://satchel.com/web-analytics/
* _Braze_: 
* _Chartbeat_: publishing
> The most influential is Chartbeat, which shows you every article on your site, indicates the number of people on each article at any given second, and colors the dots representing those people to tell you how they found the article. Green dots mean they found you through a search engine. Purple dots mean they came from a social network, usually Facebook, Twitter, or Reddit. It’s pure pleasure to watch the display for an article you worked hard on fill with dots. https://www.vox.com/2020/1/28/21077888/why-were-polarized-media-book-ezra-news
* _Clickhouse_: https://tech.marksblogg.com/install-clickhouse-faster.html https://tech.marksblogg.com/faster-clickhouse-imports-csv-parquet-mysql.html https://tech.marksblogg.com/billion-nyc-taxi-rides-clickhouse-cluster.html https://github.com/azat/chdig https://posthog.com/handbook/engineering/clickhouse https://clickhouse.com/docs/en/operations/utilities/clickhouse-local/ https://news.ycombinator.com/item?id=34071918 https://clickhouse.com/blog/extracting-converting-querying-local-files-with-sql-clickhouse-local https://news.ycombinator.com/item?id=24696149 https://tech.marksblogg.com/clickhouse-prometheus-grafana.html https://softwareengineeringdaily.com/2021/05/17/clickhouse-data-warehousing-with-robert-hodges/ https://softwareengineeringdaily.com/2022/09/12/serverless-clickhouse-for-developers/ https://tech.marksblogg.com/billion-taxi-rides-doublecloud-clickhouse.html https://tech.marksblogg.com/install-clickhouse-faster.html https://tech.marksblogg.com/faster-clickhouse-imports-csv-parquet-mysql.html https://tech.marksblogg.com/clickhouse-prometheus-grafana.html
* _Hotjar_: https://www.hotjar.com/
* _GoatCounter_: Visidata uses https://www.goatcounter.com/ alternative https://github.com/ihucos/counter.dev https://news.ycombinator.com/item?id=26379569 https://simpleanalytics.com/ https://newcss.net/
* _Google Analytics_: https://satchel.com/web-analytics/ alternatives https://tedium.co/2023/03/04/self-hosted-saas-app-alternatives/
* Ackee https://github.com/electerious/Ackee
* BYO https://minimalanalytics.com/
* Countly https://thomashunter.name/posts/2018-12-28-migrating-from-google-analytics
* Fathom https://usefathom.com/
* Plausible https://plausible.io/privacy-focused-web-analytics https://www.erichgrunewald.com/posts/ravi-zacharias-solves-the-problem-of-evil/ https://plausible.io/blog/remove-google-analytics
* Shynet https://github.com/milesmcc/shynet
* Simple https://simpleanalytics.io
* _Heap_: https://satchel.com/web-analytics/
* _Highlight_: https://news.ycombinator.com/item?id=34897645
* _LogRocket_: https://news.ycombinator.com/item?id=34897645
* _Mixpanel_: https://satchel.com/web-analytics/ https://news.ycombinator.com/item?id=40432213
* _Posthog_: https://github.com/posthog/posthog https://www.pythonpodcast.com/posthog-product-analytics-episode-266/
* _Umami_: https://github.com/umami-software/umami

---

ZA
* https://danluu.com/metrics-analytics/ https://www.kalzumeus.com/greatest-hits/ https://danluu.com/web-bloat https://thoughtbot.com/upcase/analytics-for-developers 

## logging

🗄 `python/stdlib.md` logging

LOG STORES
* _parseable_: https://github.com/parseablehq/parseable

FORMAT
* _JSONL_: https://github.com/textualize/toolong

TOOLING
* _toolong_: 🎯 https://github.com/textualize/toolong

---

* https://github.com/pamburus/hl
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
https://news.ycombinator.com/item?id=30394152
> If you are building an API, having a mechanism that provides detailed logs—including the POST bodies passed to the API—is invaluable. It’s an inexpensive way of maintaining a complete record of what happened with your application—invaluable for debugging, but also for tricks like replaying past API traffic against a new implementation under test. Logs like these may become infeasible at scale, but for a new project they’ll probably add up to just a few MBs a day—and they’re easy to prune or switch off later on if you need to. https://simonwillison.net/2021/Jul/1/pagnis/
* _Logflare_: middleman btw app and storage; most logging services (datadog) make money by marking up storage; available as Cloudflare app https://runninginproduction.com/podcast/11-logflare-is-a-log-management-and-event-analytics-platform
* _sources_: clickstream, proxy, web server, app server
* event streams https://apenwarr.ca/log/20190216
* _formats_: CLF, Amazon, Nginx https://github.com/allinurl/goaccess common log format https://vicki.substack.com/p/logs-were-our-lifeblood-now-theyre https://brandur.org/logfmt https://medium.com/hiredscore-engineering/logging-lets-do-it-right-41d568d3bfcd
* _tools_: Logstash, Fluentd https://github.com/itamarst/eliot https://news.ycombinator.com/item?id=21461617 https://github.com/rcoh/angle-grinder https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-log-analyzers https://github.com/allinurl/goaccess psutil (get system info like CPU, mem, users) Honeycomb https://www.honeycomb.io/blog/tell-me-more-nginx/ https://hynek.me/talks/beyond-grep/
* _sink_: log growth roughly linear https://www.youtube.com/watch?v=-6Hk9rcgM94 https://stripe.com/gb/blog/canonical-log-lines

## perf

🗄️ `databases.md` perf
📙 Gregg systems performance

---

https://blog.pecar.me/sqlite-wal
https://blog.pecar.me/django-sqlite-benchmark
https://blog.pecar.me/django-sqlite-dblock
https://testdriven.io/blog/django-performance-optimization-tips/
https://www.youtube.com/watch?v=gpbpVheR3gM
https://blog.pecar.me/django-streaming-responses
