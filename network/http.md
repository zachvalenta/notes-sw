# ⛩️

## 参考

🛠️ debug requests https://github.com/cle-b/httpdbg

🔍 dummy endpoints https://example.org/ https://http.cat/ https://httpstat.us https://httpbin.org/ https://dogapi.dog/ https://news.ycombinator.com/item?id=41371170
🗄️ `infra.md` web servers
📜 https://httpwg.org/specs/
🔍 https://networkengineering.stackexchange.com/
📚
* Evans http https://www.youtube.com/watch?v=91OKnEIFyGs
* Gourley http
* Haverbeke eloquent javascript https://eloquentjavascript.net/18_http.html
* Hafner where wizards stay up late
* Kozeriok tcp-ip guide (ch. 79-84)

## 进步

* _24_: mv to own file

---

* https://news.ycombinator.com/item?id=33280605
* _SNI (server name indication)_: first HTTP message in connection, client tells server who it wants to connect to https://www.agwa.name/blog/post/writing_an_sni_proxy_in_go https://jvns.ca/blog/2016/07/14/whats-sni/
* https://softwareengineeringdaily.com/2023/10/11/the-future-of-http/

THINGS TO KNOW https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/
* what HTTP request looks like
* send HTTP request from scratch - netcat https://jvns.ca/blog/2016/07/14/whats-sni/
* how to inspect network packet
* how TCP works - inspect packet, BYO

WHAT HAPPENS WHEN 📙 `evans-networking-ack.pdf` https://www.youtube.com/watch?v=AlkDbnbv7dk
* https://danluu.com/navigate-url/
* https://intronetworks.cs.luc.edu/
* https://drewdevault.com/2016/12/06/A-broad-intro-to-networking.html
* https://www.warp.dev/blog/what-happens-when-you-open-a-terminal-and-enter-ls
* https://github.com/reorx/httpstat
* _request flow_: browser cache, hosts file (`/private/etc/hosts` on macOS) router [`evans-tcpdump.pdf`], DNS cache, DNS server (local ISP, then eventually if you're unlucky to a root server, who point your query to the .coms or .govs or what have you)
* https://eater.net/inet
* https://wsvincent.com/what-happens-when-url/ DNS, req, res, render HTML, go get further (css, img, js), async as necessary
* https://wsvincent.com/how-does-the-internet-work/ https://wsvincent.com/how-the-web-works/ 

# 🛠️ TOOLING

🗄 `shell.md` userland

https://news.ycombinator.com/item?id=41650905
https://github.com/dnaeon/go-vcr
postman alternative https://github.com/Julien-cpsn/ATAC
https://readme.com/
https://github.com/ducaale/xh
https://github.com/Julien-cpsn/ATAC
https://github.com/qustavo/httplab
https://github.com/usebruno/bruno
https://github.com/Orange-OpenSource/hurl
* query w/ SQL https://github.com/turbot/steampipe https://www.hytradboi.com/2022/how-to-query-almost-everything

## curl

🔍 https://catonmat.net/cookbooks/curl

* https://everything.curl.dev/
* https://github.com/rs/curlie
* https://martinheinz.dev/blog/113
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

## httpie

📜 https://httpie.org/doc

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

## http-prompt

📜 http://http-prompt.com/ https://docs.http-prompt.com/en/latest/

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

## posting

https://github.com/darrenburns/posting 
https://pythonbytes.fm/episodes/show/409/weve-moved-to-hetzner-write-up

# 🟨 ZA

* _tarpit_: purposefully slow responses e.g. delay, send partial, add artificial latency between headers and body https://news.ycombinator.com/item?id=31509523 https://chatgpt.com/c/674a3d23-5e98-8004-aa33-c1cde00d2bea

---

BYO transport?!?
> Some areas where we’re happy with our choices even though they may not sound like the simplest feasible solution is with our API, where we use GraphQL, with our transport protocols, where we had a custom protocol for a while, and our host management, where we use Kubernetes. For our transport protocols, we used to use a custom protocol that runs on top of UDP, with an SMS and USSD fallback, for the performance reasons described in this talk. With the rollout of HTTP/3, we’ve been able to replace our custom protocol with HTTP/3 and we generally only need USSD for events like the recent internet shutdowns in Mali. https://danluu.com/simple-architectures/
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
* _Gopher_: predecessor of HTTP https://drewdevault.com/2020/11/01/What-is-Gemini-anyway.html https://blog.devgenius.io/tired-of-the-modern-web-discover-some-retro-protocols-you-still-can-use-today-30bbca48d3f2 https://github.com/xvxx/phetch
* _Gemini_: alternative to HTTP https://www.youtube.com/watch?v=PQBWkkXSfSY https://drewdevault.com/gemini.html https://sotiris.papatheodorou.xyz/

## caching

🗄 
* `distributed.md` proxy
* `security.md` cookies/tokens

design
* TTL https://calpaterson.com/ttl-hell.html
> just set an absurdly long TTL and browsers and CDNs will obey it - to the extent they care to.
* namespacing/cache busting https://calpaterson.com/ttl-hell.html
> A common usage is to put version strings or release timestamps into URL paths or query-strings to ensure the that the browser downloads only the latest JavaScript bundle.
* adverts not cached bc clients want those fresh bc each counts

---

https://grayduck.mn/2021/09/13/cache-control-recommendations/
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

* _media type_: serialization; json `application/json` form `application/x-www-form-urlencoded` file `multipart/form-data` https://github.com/zachvalenta/pacific-flask/blob/master/templates/index.html#L22 mimetype https://stackoverflow.com/a/9277778 https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types https://drewdevault.com/2022/01/28/Implementing-mime-in-xxxx.html https://www.pythonmorsels.com/cli-tools/#mimetypes

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
* Julia Evans https://www.youtube.com/watch?v=xYv8wcNJiKw
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
* _500_: general (in the same way 200 and 400 are general)
* _501_: client not supported e.g. you want to tell Android client it needs to upgrade
* _502_: server handling your request got an error from a downstream
* _503_: server down
> 502-504 all have similar meanings and it ends up being that the service you're trying to reach can't respond to the request
* _504_: server handling your request is tired of waiting for a downstream
* _522_: time out; TCP connection btw web server and CDN (bc server is overloaded) https://www.youtube.com/watch?v=axYMNCuL_hE
