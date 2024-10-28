# ⛩️

## 参考

🔍 https://networkengineering.stackexchange.com/
📙 Kozierok tcp-ip guide

## 进步

DNS 🗄 `html-css.md` Zola deployment
* go through books
* maybe buy other Evans zines https://wizardzines.com/zines/bite-size-networking/ https://wizardzines.com/zines/dns/
* clean up below

THINGS TO KNOW https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/
* what HTTP request looks like
* send HTTP request from scratch - netcat https://jvns.ca/blog/2016/07/14/whats-sni/
* how to inspect network packet
* how TCP works - inspect packet, BYO
* how DNS works - inspect query
* _SNI(server name indication)_: first HTTP message in connection, client tells server who it wants to connect to https://www.agwa.name/blog/post/writing_an_sni_proxy_in_go https://jvns.ca/blog/2016/07/14/whats-sni/

WHAT HAPPENS WHEN 📙 `evans-networking-ack.pdf` https://www.youtube.com/watch?v=AlkDbnbv7dk
* https://drewdevault.com/2016/12/06/A-broad-intro-to-networking.html
* https://www.warp.dev/blog/what-happens-when-you-open-a-terminal-and-enter-ls
* https://github.com/reorx/httpstat
* _request flow_: browser cache, hosts file (`/private/etc/hosts` on macOS) router [`evans-tcpdump.pdf`], DNS cache, DNS server (local ISP, then eventually if you're unlucky to a root server, who point your query to the .coms or .govs or what have you)
* https://eater.net/inet
* https://wsvincent.com/what-happens-when-url/ DNS, req, res, render HTML, go get further (css, img, js), async as necessary
* https://wsvincent.com/how-does-the-internet-work/ https://wsvincent.com/how-the-web-works/ 

CLEAN UP
* https://www.youtube.com/watch?v=j9QmMEWmcfo
* https://softwareengineeringdaily.com/2023/10/11/the-future-of-http/
* https://www.charlesproxy.com/
* https://twobithistory.org/2018/06/10/birth-of-the-web.html
* HTTP  https://news.ycombinator.com/item?id=33280605
* https://adhoc.team/2022/01/18/covidtests-usps-aws-managed-services/
* packet switching 📙 Christian chapter 10
* 📙 Evans http
* CORS
* das protocols https://explained-from-first-principles.com/internet
* https://news.ycombinator.com/item?id=31509523

* _20_: TLS (openssl, debug openssl)
* _17_: 📙 Ross network know how

# 📡 HTTP

🗄️ `infra.md` web servers
🛠️ debug requests https://github.com/cle-b/httpdbg
📜 https://httpwg.org/specs/
🔍 dummy endpoints https://example.org/ https://http.cat/ https://httpstat.us https://httpbin.org/ https://dogapi.dog/ https://news.ycombinator.com/item?id=41371170
📚
* Eloquent Javascript
* Evans http
* Gourley http
* Hafner where wizards stay up late
* Kozeriok tcp-ip guide (ch. 79-84)

BYO server https://news.ycombinator.com/item?id=40642865

message structure https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages
* encodings: ascii (start-line, header keys) octet (header value, body) https://stackoverflow.com/q/818122 🗄 `math.md` encoding/info theory
```sh
# START-LINE = resource + verb, protocol version
GET /item?id=23588896 HTTP/1.1

# HEADERS = metadata
Host: news.ycombinator.com  # server
Connection: keep-alive

# BLANK LINE DELIMITS END OF HEADERS

# BODY = data
{
    "name": "alice"
}
```

history
* 0.9 (1991): methods
* 1.1 (1996): + user-agent, Accept
* 1.1. (1999): Connection: keep-alive https://tools.ietf.org/html/rfc7230 https://tools.ietf.org/html/rfc7231
* _Gopher_: predecessor of HTTP https://drewdevault.com/2020/11/01/What-is-Gemini-anyway.html https://blog.devgenius.io/tired-of-the-modern-web-discover-some-retro-protocols-you-still-can-use-today-30bbca48d3f2
* _Gemini_: alternative to HTTP https://www.youtube.com/watch?v=PQBWkkXSfSY https://drewdevault.com/gemini.html https://sotiris.papatheodorou.xyz/

## caching

🗄 
* `system.md` caching
* `system.md` proxy

design
* TTL https://calpaterson.com/ttl-hell.html
> just set an absurdly long TTL and browsers and CDNs will obey it - to the extent they care to.
* namespacing/cache busting https://calpaterson.com/ttl-hell.html
> A common usage is to put version strings or release timestamps into URL paths or query-strings to ensure the that the browser downloads only the latest JavaScript bundle.
* adverts not cached bc clients want those fresh bc each counts

---

* https://www.youtube.com/watch?v=HiBDZgTNpXY

etag
* _etag_: id for specific version of resource
* used to prevent update conflicts
* used w/ HEAD verb

* https://fideloper.com/quick-caching-explanation
* https://blog.octo.com/en/cache-me-if-you-can-1/
* ❓ why would GET w/ payload break caching? https://stackoverflow.com/questions/978061/http-get-with-request-body/983458#983458

## CORS

📙 Zalewski chapters 9-11

* only for browsers, not other REST clients https://stackoverflow.com/a/57712789

---

https://github.com/simonw/datasette-cors
* http://eradman.com/posts/cross-origin-requests.html
https://jakearchibald.com/2021/cors/
https://ieftimov.com/post/deep-dive-cors-history-how-it-works-best-practices/
header as well?

* _CORS_: ❓ your domain (`mydomain.com`) can serve resources under its control (`mydomain/img/foo.png`) or redirect elsewhere (`s3://bardomain/img/bar.png`)

https://fosterelli.co/developers-dont-understand-cors

* some people don't like https://news.ycombinator.com/item?id=18767767

📙 Eloquent JavaScript chap. 17 ‘HTTP Sandboxing'

🔗 https://frontendian.co/cors

* https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html
* origin: host that serves initial resource
    * same-origin: further resources come from same host
    * cross-origin: ‘’ can come from different hosts
    * cross-origin resource sharing (CORS): 
        * = Access-Control-Allow-Origin: <otherDomain>
        * header that server adds to tell browser (who by default normally block CORS) to whitelist other domains from whom further resources can be fetched
* difference btw ‘method’ and ‘access-control-request-method’ and relationship to preflight requests
* https://www.html5rocks.com/en/tutorials/cors/

## headers

🔗
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
* https://questions.wizardzines.com/http-request-headers.html

* _header_: KV pair of req/res meta data
* will have data types soon https://dunglas.fr/2020/08/a-structured-http-fields-parser-and-serializer-for-the-go-programming-language/

za
* _Content-Type_: set on both req and res https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type
* multipart/form-data for binary https://stackoverflow.com/a/4073451
* application/x-www-form-urlencoded for everything else
* application/json for json

---

* security headers https://github.com/TypeError/secure
* `Accept-Language` https://news.ycombinator.com/item?id=41497139

req
```yaml
Host: examplecat.com  # req destination
User-Agent: curl      # software sending req
Accept: */*           # https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept also used to hold API version number
Content-Type: multipart/form-data;
```
* _Accept-Encoding_: compression algos browser can unzip; Brotil allows for smaller sizes that gzip

res
```yaml

```
* _Content-Type_: what media type is being sent

----

accept-language https://borretti.me/article/uselessness-accept-language-header
* range https://github.com/psanford/sqlite3vfshttp
* `Cache-Control`: tells client how long to wait before fetching new copy of resource
* won't stop browser requesting, but if resource still fresh server res w/ 304
* `Expires`: time after which response should be considered stale i.e "browser store this response in browser cache until then"
* e.g. Wikipedia homepage featured article, instead of every user requesting all day long, set an expires header so that after first visit to homepage each subsequent visit will just use the browser cache

* https://www.twilio.com/blog/a-http-headers-for-the-responsible-developer https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers https://www.fastly.com/blog/headers-we-dont-want

* _media type_: serialization; json `application/json` form `application/x-www-form-urlencoded` file `multipart/form-data` https://github.com/zachvalenta/pacific-flask/blob/master/templates/index.html#L22 
* _MIME type_: old name for media type https://stackoverflow.com/a/9277778 https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types https://drewdevault.com/2022/01/28/Implementing-mime-in-xxxx.html

misc
* do not track: sites just ignore https://lwn.net/Articles/826575/
* _Allow_: what verbs applicable for endpoint
* _Location_: for 301 or 3xx 🗄 `book-db`
* _User-Agent_: info on client 🗄️ crawlers
* _Keep-Alive_: keeps the underlying TCP connection open for period of time
* normally this would close after each request https://lob.com/blog/use-http-keep-alive

## methods / verbs

📜 https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
🗄 `system.md` REST

IDEMPOTENT
* _GET_: retrieve; should not handle the body https://stackoverflow.com/a/983458
* _OPTIONS_: see what verbs allowed for resource i.e. prompt `Allow` header https://stackoverflow.com/a/47602072
* _HEAD_: GET sans body; useful for seeing size of resource, last update https://stackoverflow.com/a/6660062 just use GET though https://www.jefftk.com/p/debug-headers-with-get
* _QUERY_: proposed https://www.ietf.org/archive/id/draft-ietf-httpbis-safe-method-w-body-05.html

MUTATIVE
* _PUT_: idempotent (`x = 5`) create/update specific resource (`PUT /expense-report/10929`) https://stackoverflow.com/a/2691891
* _POST_: not idempotent (`x++`) ask for create/update from resource 'factory' (`POST /expense-report`)
* _PATCH_: updates only part of resource
* _DELETE_: rm
```makefile
patch:
	poetry run http PATCH $(api_url)/1/ team="$(team)"
put:
	poetry run http PUT $(api_url)/1/ team="$(team)" playbook="$(play)"
```

DESIGN
* unclear https://changelog.com/podcast/189
* GET and POST sufficient https://www.freecodecamp.org/news/rest-is-the-new-soap-97ff6c09896d/

## security

🗄 `security.md` auth

* https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Authentication_schemes https://tools.ietf.org/html/rfc7235#section-2.1
* _WWW-Authenticate_: res to auth https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate
* _Authorization_: req w/ credentials in the form `<scheme> <credentials>` https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization

security https://securityheaders.com/
* _Access-Control-Allow-Headers_: headers accepted by server; if doesn't support method from client, server throws error https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers
* _CORS_: 
* _Strict-Transport-Security (HSTS)_: tell browser only use HTTPS (browser automatically makes subsequent requests using HTTPS) https://jvns.ca/blog/2017/04/30/using-strict-transport-security/

## status codes

🔗
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
* https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
* https://www.youtube.com/watch?v=_qKgO8BPHWc
* https://wompa.land/articles/http-status-codes

* _100s_: info

200 SUCCESS
* _200_: "GET/PUT worked + data for you"
* _201_: "POST worked"
* _204_: "PUT/PATCH/DELETE worked"

300 REDIRECT
* _301_: "what you're looking for isn't there, here is it's actual URL" (e.g. Django when trailing slash is missing)
* _302_: "POST worked, let's go there now" (followed by a GET from the browser and 200 from server i.e. POST-redirect-GET)
* _303_: "can't POST bc resource already exists"; could also be a 409 https://stackoverflow.com/q/3825990/6813490
* _304_: "based on `Cache-Control` the resource hasn't change so I'll redirect you to browser cache"

400 CLIENT ERROR
* _400_: bad request e.g. sent POST but missing required field
* _401_: "plz authenticate"
* _403_: "ur not authorized" https://stackoverflow.com/a/6937030
* _404_: resource not found
* _405_: auth-ed, resource found, but method unallowed
* _406_: can't find resource with right content type

500 SERVER ERROR
* _500_: ❓general (in the same way 200 and 400 are general)
* _501_: client not supported e.g. you want to tell Android client it needs to upgrade
* _502_: server handling your request got an error from a downstream
* _503_: server down
> I think a 503 response is usually from the load balancer when it has no downstream to proxy the request to
> 502-504 all have similar meanings and it ends up being that the service you're trying to reach can't respond to the request
* _504_: server handling your request is tired of waiting for a downstream
* _522_: time out; TCP connection btw web server and CDN (bc server is overloaded) https://www.youtube.com/watch?v=axYMNCuL_hE

## tooling

🗄 `shell.md` userland

https://news.ycombinator.com/item?id=41650905
https://github.com/dnaeon/go-vcr
postman alternative https://github.com/darrenburns/posting https://github.com/Julien-cpsn/ATAC
https://readme.com/
https://github.com/ducaale/xh
https://github.com/Julien-cpsn/ATAC
https://github.com/qustavo/httplab
https://github.com/usebruno/bruno
https://github.com/Orange-OpenSource/hurl
* query w/ SQL https://github.com/turbot/steampipe https://www.hytradboi.com/2022/how-to-query-almost-everything

HTTPIE 📜 https://httpie.org/doc
* no ability to yet config base URL https://github.com/httpie/httpie/pull/1377
* _CLI_: http://docs.http-prompt.com/en/latest/
* _post_: use `POST` or include payload
* _form_: `http --form POST http://localhost:5000 user_email="testing from shell"` https://httpie.org/doc#regular-forms
* _config file_: `~/.httpie/config.json`; find via `http --debug` https://httpie.org/docs/0.9.7#configurable-options can set per project (`export HTTPIE_CONFIG_DIR=./http-local-conf.json`) but in absence of project-local conf will just use global conf
* _output_: `-v` all `-print=HhBb` show headers/body `--body` only show JSON [docs 14] `--style` (monokai, native, autumn)
* _json_: https://httpie.org/doc#json
```sh
# simple
http POST httpbin.org/post title=hi description="hi desc"
# use quotes in Makefile for strings with spaces
http PATCH $(api_url)/1/ team="$(team)"
# boolean https://httpie.org/doc#non-string-json-fields
http POST httpbin.org/post toogle:=true array:="[]"
# from file https://stackoverflow.com/a/63343972
http POST httpbin.org/post < post.json
# stdin https://stackoverflow.com/a/37266537
echo '{ "user": { "name": "john", "age": 10 } }' | http httpbin.org/post
```

CURL
* https://github.com/rs/curlie
* https://martinheinz.dev/blog/113
* guide https://catonmat.net/cookbooks/curl https://everything.curl.dev/
```sh
# basic
curl -X <method> <URL>

# input
-d / -F  # form data
-T foo.txt
-d '{"k": "v"}; type=application/json'  # https://daniel.haxx.se/blog/2022/02/02/curl-dash-dash-json/

# auth
- u user:pw
-H "Authorization: Bearer {token}"
-k  # HTTP vs. HTTPS

# output
-s       # don't show progress bar
-f       # swallow server error
-w "\n"  # add newline
-w "timing: %{time_total}"
```
* convert to scripting language https://github.com/NickCarneiro/curlconverter/
* might need quotes for url https://stackoverflow.com/a/22906231

HTTP-PROMPT 📜 http://http-prompt.com/ https://docs.http-prompt.com/en/latest/
* uses httpie config
* _conf_: `~/.config/http-prompt/config.py` https://docs.http-prompt.com/en/latest/user-guide.html#configuration
```sh
# specify initial path
http-prompt http://localhost:8000
# add to URL path
cd ../api  #  http://localhost:8000/api
# make req
get
```
```bash_profile
function htp(){
    if [ $# -eq 0 ]; then
        port=8000
    else
        port="$1"
    fi
    base_url="http://localhost"
    full_url="${base_url}:${port}"
    http-prompt "${full_url}"
}
```

# 🟨 ZA

* audio https://github.com/xehl/campus-fm/blob/main/src/stations.js https://www.campus-fm.com/ https://news.ycombinator.com/item?id=33608892
* video https://tyrrrz.me/blog/reverse-engineering-youtube-revisited
* _BGP_: how things get routed https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/
* _CSP_: header returned by server; to prevent XSS and other attacks; if browser doesn't support defaults to same-origin policy https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP way to beef up security; don't turn on right away, `tf plan` and see what would be blocked before applying https://www.laac.dev/blog/content-security-policy-using-django
* _dat_: p2p HTTP https://beakerbrowser.com
* _Gemini_: alternative web protocol https://news.ycombinator.com/item?id=23161922

WWW
* _WWW_: internet + protocols + hypertext https://twobithistory.org/2018/06/10/birth-of-the-web.html
* _clear web_: accessible to web crawlers; 4% of WWW
* _deep web_: not accessible to web crawlers; 90% of WWW
* _dark web_: accessible to TOR browser; 6% of WWW

## DNS

🗄 `aws.md` Route53
🛠 https://jvns.ca/blog/2021/12/15/mess-with-dns/ https://messwithdns.net/
🔗 https://news.ycombinator.com/item?id=36909427
📚
* Evans https://wizardzines.com/zines/dns/
* Kozierok guide ch. 52-57
* Liu dns and bind
* Sanders packet analyis

ZONE DATA
* _zone_: single domain inside the DNS
* _zone file_: mapping of subdomains to IP https://help.dyn.com/how-to-format-a-zone-file/
* _record_: entity inside of zone file i.e. instructions on what to do with each request

RECORD TYPES
* _A_: maps name to 32-bit IPV4 address
* _AAAA_: maps name to 128-bit IPV6 address
* _CNAME_: maps name to another name
* _MX_: mail server

URL RESOURCES
* _URI_: identifier e.g. page in a book
* _URL_: URI + protocol e.g. `https://google.com` https://danielmiessler.com/study/difference-between-uri-url/ https://wsvincent.com/url-vs-uri/
* trailing slash: problem is that users might accidentally add/forget, mitigated by some browsers (Chrome) and server might be able to figure out (Django) https://learndjango.com/blog/trailing-url-slashes-django
* should be case sensitive https://stackoverflow.com/a/7996997
* _well-known URL_: name space for serving static files for other systems e.g. `/.well-known/security.txt` for security policy https://adamj.eu/tech/2020/06/28/how-to-add-a-well-known-url-to-your-django-site

URL FQDN
* _FQDN_: `http://math.mit.edu/about`
* _scheme/protocol_: `http://` http, https, et al.
* _sub/domain_: `math.mit` namespace
* domain: 
* subdomain: https://www.shortcut.com/blog/building-a-saas-app-you-should-probably-stick-to-a-single-subdomain
* _TLD_: `.edu` set of domains doled out by the same authority https://tech.marksblogg.com/rdns-domain-name-tld-extract-golang.html https://tech.marksblogg.com/rdns-domain-name-tld-extract-rust.html
* _path_: `about` namespace targeting specific resource
* _query string_: `?prof=lambeau` way to filter resources https://stackoverflow.com/a/31261026 way to send KV to server (if you don't want to put in HTTP body)
* _fragment_: `#will-hunting` navigation internal to page

ZA
* settings: `/etc/resolv.conf` https://hacker-tools.github.io/machine-introspection/
* find domains https://www.domainsfortherestofus.com/
* check record config https://github.com/fcambus/dnc
* _whois_: get info on domain https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/

---

TOOLS
* traceroute
* _dig_: https://nickjanetakis.com/blog/monitor-the-output-of-a-program-for-changes-using-the-watch-command https://jvns.ca/blog/2021/12/04/how-to-use-dig/
* _dog_: https://github.com/ogham/dog

* https://jpetazzo.github.io/2024/05/12/understanding-kubernetes-dns-hostnetwork-dnspolicy-dnsconfigforming/
* https://entropicthoughts.com/secure-dns-on-a-laptop-with-debian
* whitelist/blacklist https://github.com/plutov/ultrafocus
* https://www.youtube.com/watch?v=27r4Bzuj5NQ
* https://jvns.ca/blog/2024/08/19/migrating-mess-with-dns-to-use-powerdns/
* https://github.com/mr-karan/doggo
* https://news.ycombinator.com/item?id=37531801&utm_term=comment
* DNS, ints/floats https://jvns.ca/blog/2023/06/23/new-zine--how-integers-and-floats-work/
* TLD https://textslashplain.com/2023/05/13/new-tlds-not-bad-actually/
* client https://github.com/natesales/q
* https://www.netmeister.org/blog/nsauth-diversity.html
* use in Python + ICMP https://news.ycombinator.com/item?id=33494386
* is a DNS service like Route53 serving anything or is this just loose semantics? https://vickiboykis.com/2022/01/08/migrating-to-hugo/
* domain security https://news.ycombinator.com/item?id=30818950
* https://www.youtube.com/watch?v=Wj0od2ag5sk
* https://www.youtube.com/watch?v=7lxgpKh_fRY
* https://www.nslookup.io/learning/the-life-of-a-dns-query-in-kubernetes/
* resolver https://jvns.ca/blog/2022/02/01/a-dns-resolver-in-80-lines-of-go/
* https://github.com/resyncgg/ripgen
* https://cuddly-octo-palm-tree.com/posts/2021-10-17-dns/
* Namecheap https://news.ycombinator.com/item?id=30504812
* https://news.ycombinator.com/item?id=29812736&utm_term=comment
* https://news.ycombinator.com/item?id=34485815
* https://jvns.ca/blog/2021/11/04/how-do-you-tell-if-a-problem-is-caused-by-dns/
clients: dig, dog https://github.com/ibraheemdev/modern-unix https://github.com/ogham/dog
> Subsequent requests can (but don't always) reuse the DNS, TCP and TLS setup but a new roundtrip is still needed each time the server is consulted, for example for an API call or a new page. https://calpaterson.com/latency.html
* TTL https://news.ycombinator.com/item?id=26620730 https://calpaterson.com/ttl-hell.html
* levels of understanding https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/

* _impl_: unencrypted
* _A record_: map of URL to IP address
* _CNAME_: alias e.g. `www.zachvalenta.com` -> `https:///www.zachvalenta.com` [`evans-linux.pdf` 5]
* _NS record_: DNS server that has more info on sub-hosts for domain https://serverfault.com/a/224924/415712
* _ICANN_: authority on domains 艘 Namecheap email
* _registrar_: buy rights to domain from ICANN, sells domains to consumers; most popular services (Name Cheap) are actually middlemen between registrars (like eNom) and consumer
* _providers_: DNS Simple, Google, OpenDNS; ❓ what do they actually provide?
* _server_: resolves query for domain w/ IP address https://news.ycombinator.com/item?id=24886120
* _zone_: https://stackoverflow.com/questions/22440582/difference-between-a-dns-zone-and-dns-domain/22440611#22440611
* `@` in DNS zone file https://serverfault.com/questions/83874/whats-the-meaning-of-in-a-dns-zone-file
* _poisoning_: provide malformed translation of domain/IP to DNS server
* _sink_: https://jvns.ca/blog/how-updating-dns-works/ https://danielmiessler.com/study/dns/ https://www.youtube.com/watch?v=LUFn-QVcmB8 Nick Janetakis course, https://www.roguelynn.com/words/explain-like-im-5-dns/ https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/ https://https://blog.ironbastion.com.au/abandoned-domain-names-are-risk-to-businesses/ https://howdns.works/ https://softwareengineeringdaily.com/2017/06/06/dns-with-phil-stanhope/ https://powerdns.org/hello-dns/ https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-network-dns https://eradman.com/posts/run-your-own-server.html
📝 [iterative query](https://www.raspberrypi.org/learning/networking-lessons/lesson-4/plan/): initial DNS server passes along to other server(s) to resolve; first server will cache resolved query for next time
* _recursive service_: provided by ISP, will cache lookups by TTL
* apex/root domain: `example.com`; [cannot be aliased](https://news.ycombinator.com/item?id=8825519) + https://help.github.com/articles/about-supported-custom-domains/
BYO https://github.com/kahun/awesome-sysadmin#dns
📙 TCP/IP Guide - chapters 50-57
https://github.com/tanrax/maza-ad-blocking
https://www.roguelynn.com/words/explain-like-im-5-dns/  
https://www.youtube.com/watch?v=kV1u701wxgg
https://blog.codepen.io/2016/02/23/078-com/ how do people steal domains? how do people get control of host?

## email

PROTCOLS https://news.ycombinator.com/item?id=22989186 https://valyent.substack.com/p/build-your-own-smtp-server-in-go
* _mbox_: Gmail export fmt; most clients support if they support IMAP https://www.quora.com/How-can-one-open-mbox-files-on-Mac viewer https://softwarerecs.stackexchange.com/q/11177
* _SMTP_: used for sending and receiving emails between mail servers https://nullprogram.com/blog/2017/06/15/ https://jetmore.org/john/code/swaks/
* _IMAP_: allows users to read and manage emails directly from the server
* _POP3_: downloads emails from the server to the local device, typically removing them from the server
* _JMAP_: email protocol https://fastmail.blog/2018/12/27/jmap-is-on-the-home-straight/ https://news.ycombinator.com/item?id=36127703

GMAIL ALTERNATIVES 🗄 `security.md` privacy
* https://www.youtube.com/watch?v=iH626CXyNtE
* https://drewdevault.com/2020/06/19/Mail-service-provider-recommendations.html
* don't bikeshed https://news.ycombinator.com/item?id=23423548 bc accounts tied to email are hard to move https://news.ycombinator.com/item?id=24245817
* howto: try out new service with some newsletters and the zjayv.com domain
> eventually: clean out Gmail, export business/personal to separate accounts, and then can continually export personal to local mbox viewer
* why: search ('in:sent label:personal' doesn't show recent emails w/ YQ or Ellen but 'in:sent' shows)
* why: lose account https://news.ycombinator.com/item?id=24791357 https://news.ycombinator.com/item?id=34581090
* why not: works well, only marginal return for time invested, apparently Gmail search is better than others https://hobo.house/2015/09/09/take-control-of-your-email-with-mutt-offlineimap-notmuch/
* _Hey_: https://www.hey.com/
* _Fastmail_: https://news.ycombinator.com/item?id=24245817
* _pop_: https://github.com/charmbracelet/pop

---

* _Maddy_: send email https://blog.healthchecks.io/2023/08/notes-on-self-hosted-transactional-email/
https://github.com/sdushantha/tmpmail

SPF, DKIM, and DMARC https://news.ycombinator.com/item?id=40708476
* content/templates https://news.ycombinator.com/item?id=40280490
* archive: Mailstore https://news.ycombinator.com/item?id=34070957 sync https://news.ycombinator.com/item?id=27446156
* images: https://news.ycombinator.com/item?id=26661430
* HTML: https://news.ycombinator.com/item?id=26659553
* spam: Google, spamhaus https://news.ycombinator.com/item?id=33595442 https://news.ycombinator.com/item?id=34865695
* popular addresses are trouble https://news.ycombinator.com/item?id=24359980

for SMB
* https://myemma.com/
* https://tedium.co/2023/03/04/self-hosted-saas-app-alternatives/

LEAVING GMAIL
* lockout https://www.jefftk.com/p/how-likely-is-losing-a-google-account
* off Google https://news.ycombinator.com/item?id=34581090
* get away from Microsoft, too https://www.jeffgeerling.com/blog/2023/my-daughters-school-took-over-my-personal-microsoft-account
* Shotgun, AWS SES, Postal https://github.com/postalserver/postal https://news.ycombinator.com/item?id=14201562 Sendgrid https://news.ycombinator.com/item?id=18223645 https://news.ycombinator.com/item?id=24317634 https://news.ycombinator.com/item?id=30358290
* tldr https://explained-from-first-principles.com/email/

thing to do #2: email resiliency
* _what I want_: avoid possibility of arbitrary account lockout https://blog.viktomas.com/posts/losing-google-account/ https://myaccount.google.com/privacycheckup
* _questions_: what's the reputation of Fastmail here? should you just host email server? worth it given risk of lockout?
* self-hosting is near impossible https://news.ycombinator.com/item?id=31180379 email servers https://news.ycombinator.com/item?id=34908528
* don't forget all your Gmail emails forwarding to Microsoft

backup
* _manual_: Gmail export
* _automated_: https://news.ycombinator.com/item?id=22846851
* _reading old email_: periodic export from Gmail, `neomutt -f <file>.mbox` https://askubuntu.com/a/114083 can also just read old email and convert to docs like `hu-xiaodi.md`

components https://www.youtube.com/watch?v=obY1um6ehDM https://hobo.house/2015/09/09/take-control-of-your-email-with-mutt-offlineimap-notmuch/
* _client_: CLI (mutt, neomutt, aerc) native (macOS, Thunderbird requires extension https://askubuntu.com/a/912985) -> neomutt seems like only viable option https://www.youtube.com/watch?v=2U3vRbF7v5A Emacs https://www.erichgrunewald.com/posts/setting-up-gmail-in-doom-emacs-using-mbsync-and-mu4e/
> watch out for clients that use intermediate servers https://news.ycombinator.com/item?id=24423032
* _services_: Fastmail, Gmail, Zoho https://www.jefftk.com/p/dont-let-personal-domains-expire Hey https://twitter.com/patio11/status/1274576125394513921 https://drewdevault.com/2020/06/19/Mail-service-provider-recommendations.html

🔍 https://restoreprivacy.com/google-alternatives/ https://nullprogram.com/blog/2013/09/03/ https://nullprogram.com/blog/2017/06/15/
* _sending_: from app (via Postmark) or setup email server https://www.openmymind.net/2010/7/21/Using-PostMark-To-Send-Mail/
https://kevq.uk/how-to-host-email-with-your-own-domain/
* _decouple_: email (Google) browser (Firefox) search engine (DDG) mobile OS (Android) https://kevq.uk/about/ ask him about this
 https://tutanota.com/blog/posts/gmail-end-to-end-encryption-is-dead/
* _options_: Fastmail, Posteo, Protonmail https://cmpwn.com/@sir/100419028736559194 https://lukesmith.xyz/blog/a-script-that-automatically-sets-up-your-personal-mail-server.html https://github.com/trimstray/the-book-of-secret-knowledge#black_small_square-mail https://superhuman.com/
* _auth_: https://blog.jonlu.ca/posts/spf-dkim
* _servers_: Postfix, Sendmail https://github.com/kahun/awesome-sysadmin#mail-servers https://prefet.ch/blog/2020/email-server/ https://aosabook.org/en/v1/sendmail.html
* _self-hosting_: https://www.garron.blog/posts/host-your-email-server.html https://github.com/foxcpp/maddy
* search: notmuch https://www.reddit.com/r/commandline/comments/ddkyap/can_some_give_me_the_dummies_guide_to_properly/ http://richardmavis.info/so-long-macbook-hello-again-linux
> I wish Gmail had better search re: links. I think other people solve this by using things like Pinboard https://pinboard.in/
mbsync https://www.c0ffee.net/blog/mail-server-guide/

## file transfer

TOOLING
* _aim_: client https://github.com/mihaigalos/aim
* _aria_: ❌ client, bad presentation https://github.com/aria2/aria2
* _croc_: 🎯 relay via PAKE https://github.com/schollz/croc
> Yes, all data goes through the relay. I haven't found a way that can reliably send data directly between two computers that don't have port-forwarding enabled. croc differs from a utility like scp because it doesn't require any two computers to have enabled port-forwarding, nor does it require computers having any server setup. Instead, croc will uses a relay - a temporary server setup locally (if both computers are on LAN) or publicly (default is at croc4.schollz.com). Any two computers can connect to the relay, and after securing their channel with PAKE, they can transfer encrypted metadata and data through the relay. The relay works by first having the computers communicate the PAKE protocol via websockets, and then exchanging encrypted metadata, and then stapling the TCP connections directly so that they can transfer directly. https://github.com/schollz/croc/issues/104
* _Cyberduck_: ❌ looks like malware https://cyberduck.io/ https://fabiensanglard.net/html/index.html
* _filestash_: GUI client https://github.com/mickael-kerjean/filestash
* _FileZilla_: 🎯 client, used in first job! https://filezilla-project.org/
* _magic wormhole_: relay https://github.com/magic-wormhole/magic-wormhole impl https://www.youtube.com/watch?v=oFrTqQw0_3c
* _portal_: relay via PAKE https://github.com/SpatiumPortae/portal
* _sftpgo_: server https://github.com/drakkan/sftpgo
* _sshfs_: client? server? both https://github.com/libfuse/sshfs https://fabiensanglard.net/html/index.html
> SSHFS allows you to mount a remote filesystem using SFTP. Most SSH servers support and enable this SFTP access by default, so SSHFS is very simple to use - there's nothing to do on the server-side.
* _tran_: ❌ https://github.com/abdfnx/tran 
* _termscp_: 🎯 SFTP client https://github.com/veeso/termscp
* _VSFTPD_: FTP server

PROTOCOLS
* _FTP_: sends binary instead of metadata https://blog.devgenius.io/tired-of-the-modern-web-discover-some-retro-protocols-you-still-can-use-today-30bbca48d3f2
* _SFTP_: FTP + security https://goteleport.com/blog/scp-familiar-simple-insecure-slow/
```sh
$ sftp sftp://user@hostname:port
put /local/path/to/file /remote/path/to/destination/
exit
```
* _scp_: https://en.wikipedia.org/wiki/Secure_copy
* need to create dir first w/ `ssh` https://stackoverflow.com/a/25157693
```sh
ssh user@ftpserver.com "mkdir -p /data/install/somefolder"
scp -r /data/install/somefolder user@ftpserver.com:/data/install/somefolder
```
* insecure?  https://goteleport.com/blog/scp-familiar-simple-insecure-slow/
```sh
# to remote https://haydenjames.io/linux-securely-copy-files-using-scp/
scp /local/file.txt user@host:/src
# from remote
scp user@host:/src/file.txt /local/
```

## IRC

🗄️ `info.md` chat

---

* _libera.chat_: https://taskwarrior.org/docs/help/
https://drewdevault.com/2021/03/29/The-worlds-dumbest-IRC-bot.html
https://webchat.freenode.net/#sr.ht
https://sr.ht/~delthas/senpai/
* channels https://news.ycombinator.com/item?id=7161436
* clients: irssi https://weechat.org/ Textual
* _connect_: /connect irc.freenode.net
* _login_: /nick <urNick>
* [validate](https://superuser.com/a/322897)
* _join channel_: /join #pocoo
* _quit_: /quit
* _ignore noise_: /ignore -channels #<channel> * JOINS PARTS QUITS NICKS
* _grep_: /lastlog <query> <occurences>
* _save log_: /lastlog -file <pathAndFileToBeCreated>

## NTP

🗄️ `python/stdlib/datetime.md`

* https://buttondown.com/hillelwayne/archive/time-zones-are-hard-because-people-are-hard/
* YYYY-MM-DD is the only correct answer https://twitter.com/VitalikButerin/status/1547161382373756928
* https://www.libertysys.com.au/2024/05/aws-microsecond-accurate-time-second-look/?ck_subscriber_id=512830619
* _Internet Time Service_: current time as provided by NIST https://news.ycombinator.com/item?id=37778496
* _NTP_: protocol to handle keeping correct time packets move geographically [Network Flow Analysis 6] https://sookocheff.com/post/time/how-does-ntp-work/
* _NTPsec_: fork meant to replace NTP
* _UTC_: Iceland right on it, UK +1, NYC -4; typically the default https://stackoverflow.com/a/19801806/6813490
* _bit slip_: lost bit from clock drift https://www.youtube.com/watch?v=8BhjXqw9MqI 3:00 https://en.wikipedia.org/wiki/Bit_slip
* atomic clocks, earth spinning faster by milliseconds https://news.ycombinator.com/item?id=25684661
* IANA, daylight savings https://news.ycombinator.com/item?id=24951473
* _sink_: https://zachholman.com/talk/utc-is-enough-for-everyone-right https://alexwlchan.net/2019/05/falsehoods-programmers-believe-about-unix-time/ https://app.pluralsight.com/library/courses/date-time-fundamentals/table-of-contents https://news.ycombinator.com/item?id=24746836 timezones https://pyvideo.org/pycon-us-2019/working-with-time-zones-everything-you-wish-you-didnt-need-to-know.html

## SSH

🗄
* `barrett-ssh.pdf`

* basics
```sh
# FILES
├── .ssh                 # chmod 700
│   └── authorized_keys  # clients that have connected
│   └── config           # URL of server you typically connect to (e.g. vscode uses this w/ remote dev tooling)
│   └── id_rsa           # private key
│   └── id_rsa.pub       # public key
│   └── known_hosts      # servers connected to

# CREATE KEYPAIR
ssh-keygen -o -t rsa -b 4096 -C 'first.last@domain.com'
ssh-add -K ~/.ssh/id_rsa  # Identity added: /Users/zv_mac/.ssh/id_rsa (first.last@domain.com)

# LOGIN
# add public key to remote's authorized_keys i.e. need server pw https://hacker-tools.github.io/remote-machines/
ssh <user>@<host>

# port forwarding
# -L = forward, -N = dont exec remote cmd (used w/ forwarding)
ssh -NL local-port:env-host.domain.io:remove-port env-jumpbox.domain.io
```

za
* https://news.ycombinator.com/item?id=41785511
* https://github.com/quantumsheep/sshs
* https://www.youtube.com/watch?v=5JvLV2-ngCI
* https://news.ycombinator.com/item?id=37240187
* https://tech.marksblogg.com/hardening-ssh.html
* use another shell on remote https://github.com/xxh/xxh
* quotes https://www.chiark.greenend.org.uk/~cjwatson/blog/ssh-quoting.html
* design: rides on top of TCP, encrypted (vs. Telnet)
* clients: OpenSSH (Linux) Putty (Win) Mosh https://github.com/mobile-shell/mosh
* update private key to not use password: `ssh-keygen -p`
* can run cmd directly e.g. `ssh foobar@server ls` https://hacker-tools.github.io/remote-machines/
> It works with pipes, so ssh foobar@server ls | grep PATTERN will grep locally the remote output of ls and ls | ssh foobar@server grep PATTERN will grep remotely the local output of ls.
* tunneling https://news.ycombinator.com/item?id=29946144 https://ittavern.com/visual-guide-to-ssh-tunneling-and-port-forwarding/
* _mosh_: deal more gracefully with the shutdowns/lag that come w/ ssh, doesn't do port forwarding https://hacker-tools.github.io/remote-machines/
* mount remote fs w/ `sshfs` https://hacker-tools.github.io/remote-machines/

client config https://news.ycombinator.com/item?id=23027833
* global: `/etc/ssh/sshd_config` https://hacker-tools.github.io/remote-machines/
* user: `~/.ssh/config`

---

* tailscale https://news.ycombinator.com/item?id=33986430
* https://github.com/charmbracelet/wish https://www.youtube.com/watch?v=0YoHqRfKE1k
https://stackoverflow.com/a/33243564/6813490
process https://help.ubuntu.com/community/SSH/OpenSSH/Keys
* _agent_: https://smallstep.com/blog/ssh-agent-explained/ https://drewdevault.com/2022/05/09/hare-ssh.html
* _debug_: https://unix.stackexchange.com/a/229432/331460
* _keys_: private (held on client) public (held on server, incl all text in file) use them bc user/pw can be brute force; generate new w/ `ssh-keygen`
* _port_: defaults to 22
* _server_: SSHD; can set config so that no one can become root from ssh session
* non-anonymous https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols

* _sink_: https://www.youtube.com/watch?v=eQJX9DlKHy0 https://smallstep.com/blog/use-ssh-certificates/ https://news.ycombinator.com/item?id=22750850

* _copy public key to server_: `ssh-copy-id @dev123.foocorp.net` need pw access to server https://www.digitalocean.com/docs/droplets/how-to/add-ssh-keys/to-existing-droplet/
* _login sans password_: `ssh <user>@<host_ip_addr>`; adds the server's IP to your `known_hosts` ❓ how does the server match the user to the key? assume that `ssh-copy-id` copies public key to `~` of whatever user name is running the cmd and so to for `ssh`
* _session - start_: `ssh <user>@<host_domain_or_IP>`; if you don't specify user, server figures out which user you should be bc 1) you first logged into server via user/pw and put your SSH public key in the server's `authorized_keys` 2) server seems to somehow map that public key to your user so that when you come back later via SSH w/ a private key for that public key the server is just like "oh, it's Alice/Bob/<foo_user>"
* _session - quit_: `exit` or `~` to escape dead/frozen session https://lonesysadmin.net/2011/11/08/ssh-escape-sequences-aka-kill-dead-ssh-sessions/ https://www.remembertheusers.com/2020/07/0668-terminating-a-frozen-ssh-session.html

## TLS

📙 https://unixsheikh.com/articles/are-you-a-tls-master.html

---

https://questions.wizardzines.com/tls-certificates.html
https://news.ycombinator.com/item?id=41876741

* certs for local dev https://github.com/FiloSottile/mkcert
https://www.youtube.com/watch?v=k3rFFLmQCuY
https://jvns.ca/blog/2016/04/29/cdns-arent-just-for-caching/

PKI
* _ACME_: protocol to automate certificate mgmt https://letsencrypt.org/docs/client-options/ client https://github.com/caddyserver/certmagic
* _certificate_: SHA key https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/ https://questions.wizardzines.com/tls-certificates.html
* _CA_: issue digital certificates (DigiCert, Comodo, Symatec, Amazon Trust Services) to servers that demonstrate ownership of domain https://opensource.com/article/19/4/certificate-authority
* Let's Encrypt uses other CAs to cross-sign (apparently starting your own CA takes years)
* CAs not necessarily trustworthy https://www.theregister.co.uk/2017/11/01/francisco_buys_comodo/
* _local development_: generate self-signed cert (openssl) to put onto your own box

handshake
* _client (un)_: sends highest level of TLS it will support
* _server (un)_: agrees on TLS level, sends public key
* _client (un)_: verifies public key against list of certificate authorities
* _client (encrypted)_: res using server public key
* _server (encrypted)_: ack

TLS
* protocol for two parties to establish secure connection
* released in 2006 https://davidwong.fr/tls13/ preceded by SSL (released by Netscape in 1995) browsers starting to only support 1.2 and beyond https://utcc.utoronto.ca/~cks/space/blog/web/FirefoxOldTLSWarning
* requires more server maintenance https://utcc.utoronto.ca/~cks/space/blog/web/HTTPSNoOldServers
* sink https://robertheaton.com/2018/11/28/https-in-the-real-world/ https://blog.cloudflare.com/how-to-build-your-own-public-key-infrastructure/ https://blog.behrang.org/articles/creating-a-ca-with-openssl.html https://smallstep.com/blog/everything-pki.html https://www.nginx.com/blog/lets-encrypt-tls-nginx https://www.badssl.com https://www.expeditedssl.com/ https://flak.tedunangst.com/post/ssh-in-https https://tls.ulfheim.net/ https://tls.ulfheim.net/ https://github.com/jpalardy/warp https://hpbn.co/transport-layer-security-tls/ https://smallstep.com/blog/everything-pki/ https://blog.filippo.io/mkcert-valid-https-certificates-for-localhost/
* _HTTPS_: HTTPS over TLS; slower bc adding TLS handshake after TCP handshake https://jvns.ca/blog/2017/04/01/slow-down-your-internet-with-tc/ https://blog.codepen.io/2017/05/23/131-going-https/ headers are encrypted https://news.ycombinator.com/item?id=39765630 redirect https://news.ycombinator.com/item?id=40504756&utm_term=comment
* config https://hacker-tools.github.io/security/ https://mattsegal.dev/simple-django-deployment.html https://testdriven.io/blog/django-lets-encrypt testing https://hacker-tools.github.io/security/
* _HSTS_: tells browser to use HTTPS https://really-simple-ssl.com/knowledge-base/what-does-hsts-mean/ https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security
* if site uses HTTPS then embedded content must be as well, apparently this conflicts w/ adverts which is why many news sites aren't https://robertheaton.com/2014/03/27/how-does-https-actually-work/ https://howhttps.works/episodes/ https://whydoesaptnotusehttps.com/ https://stackoverflow.com/a/187685/6813490
* Let's Encrypt https://drewdevault.com/2018/06/27/My-lets-encrypt-setup.html

OpenSSL
* generate self-signed cert for local dev
* verify server certs (youtube-dl, requests) https://github.com/psf/requests/blob/master/setup.py#L105
* create hashes `vimv-openssl.log`
* verify checksum `openssl sha -sha256 path/to/foo`; `shasum -a 256` https://apple.stackexchange.com/a/230919

OpenSSL and Python
* _libraries_: ssl, pyopenssl
* Python expects openssl to be present on os https://docs.python.org/3.3/library/ssl.html 
* macos system Python comes with own version of openssl https://www.python.org/downloads/release/python-2715/
* to what extend can any Python version play nice with openssl 1.1? https://bugs.python.org/issue30008
```dockerfile
FROM python:3.6-slim
ARG project_name=youtube-dl-docker
WORKDIR /$project_name
RUN sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
RUN sudo chmod a+rx /usr/local/bin/youtube-dl
```
```sh
###############
# SOLUTIONS
# repoint to Homebrew Python? 
# https://stackoverflow.com/questions/18752409/updating-openssl-in-python-2-7
# disable Homebrew cleanup / automatic upgrades
# Dockerize
# reimage machine?
# pipx ⤵️
###############

# Python 3.6 can roll with openssl 1.1
/u/l/C/p/2/F/P/Versions $ python3 -c "import ssl; print(ssl.OPENSSL_VERSION)"
OpenSSL 1.0.2k  26 Jan 2017

# seems like I still have openssl 1.0 around
ls /usr/bin/openssl
.rwxr-xr-x 488k root 20 Sep  2019 /usr/bin/openssl*

# use pipx? https://stackoverflow.com/a/43855394/6813490 https://pypi.org/project/certifi/
/U/z/Desktop $ youtube-dl --extract-audio --audio-format m4a https://www.youtube.com/watch?v=lAL-725e0Ko
ERROR: Unable to download webpage: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:749)> (caused by URLError(SSLError(1, '[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:749)'),))

###############
# PROBLEM
###############

# Homebrew removed openssl 1.0 (for compatibility reasons?)  https://github.com/ytdl-org/youtube-dl/issues/24810#issuecomment-616678783
$ python -c "import ssl; print ssl.OPENSSL_VERSION"
ImportError: dlopen(/usr/local/Cellar/python@2/2.7.15_2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/lib-dynload/_ssl.so, 2): Library not loaded: /usr/local/opt/openssl/lib/libssl.1.0.0.dylib

# which Python 2 needed (is this on Homebrew or Python for not keeping up?) https://stackoverflow.com/a/59184347/6813490 https://brew.sh/2019/11/27/homebrew-2.2.0/
$ brew info python@2
==> Dependencies
Build: pkg-config ✔, sphinx-doc ✔
Required: gdbm ✔, openssl ✔, readline ✔, sqlite ✔

# which is problem that youtube-dl is running into
$ ytd https://www.youtube.com/watch?v=kIVnmlEjUG8&list=WL&index=5&t=0s
File "/usr/local/Cellar/python@2/2.7.15_2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/hashlib.py", line 147, in <module>
ImportError: dlopen(/usr/local/Cellar/python@2/2.7.15_2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/lib-dynload/_ssl.so, 2): Library not loaded: /usr/local/opt/openssl/lib/libssl.1.0.0.dylib

# vimv as well
/V/m/r/p/7/r/1984-too-tough-to-die $ vimv
ERROR:root:code for hash md5 was not found.
Traceback (most recent call last):
  File "/usr/local/Cellar/python@2/2.7.15_2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/hashlib.py", line 147, in <module>
ValueError: unsupported hash type md5
```

## WebSocket

🗄 `system.md` servers

* _WebSockets_: protocol to send msg to client outside req-res cycle e.g. pub-sub to push data to frontend i.e. way to do full duplex
* next gen alternative https://www.thoughtworks.com/radar/platforms/webtransport

---

* https://gotify.net/
* https://discord.com/blog/how-discord-reduced-websocket-traffic-by-40-percent
* Sendgrid (send emails to customers) Braze (Sendgrid++?)
* IETF RFC 6455 and browser API https://hpbn.co/websocket/
* compared to `Keep-Alive` https://stackoverflow.com/questions/7620620/whats-the-behavioral-difference-between-http-stay-alive-and-websockets
* _HTTP2_: multiplexed i.e n assets from single request; servers can push (in same way as Web Sockets); binary instead of HTTP's text https://serversforhackers.com/s/http2 https://hpbn.co/http2/ https://news.ycombinator.com/item?id=26263085
* _libraries_: Pusher https://www.youtube.com/watch?v=h4kIkPxhXPs
* _multiplex_: combine multiple signals into one
* perf: only sends 2 bytes instead of 100s of bytes for HTTP
* _sink_: https://www.fullstackpython.com/websockets.html Django https://www.untangled.dev/2020/08/02/django-websockets-minimal-setup
