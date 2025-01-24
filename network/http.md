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

START HERE
* https://hpbn.co/brief-history-of-http/
* https://hpbn.co/http1x/
* https://hpbn.co/http2/
* https://hpbn.co/primer-on-browser-networking/
* https://hpbn.co/xmlhttprequest/
* https://hpbn.co/server-sent-events-sse/

HISTORY https://softwareengineeringdaily.com/2023/10/11/the-future-of-http/
* 0.9 (1991): methods
* 1.1 (1996): + user-agent, Accept
* 1.1. (1999): Connection: keep-alive https://tools.ietf.org/html/rfc7230 https://tools.ietf.org/html/rfc7231
* 2.0: https://victoriametrics.com/blog/go-http2/
* _Gopher_: predecessor of HTTP https://drewdevault.com/2020/11/01/What-is-Gemini-anyway.html https://blog.devgenius.io/tired-of-the-modern-web-discover-some-retro-protocols-you-still-can-use-today-30bbca48d3f2 https://github.com/xvxx/phetch
* _Gemini_: alternative to HTTP https://www.youtube.com/watch?v=PQBWkkXSfSY https://drewdevault.com/gemini.html https://sotiris.papatheodorou.xyz/

BYO
* server https://news.ycombinator.com/item?id=40642865 https://news.ycombinator.com/item?id=33280605
* _SNI (server name indication)_: first HTTP message in connection, client tells server who it wants to connect to https://www.agwa.name/blog/post/writing_an_sni_proxy_in_go https://jvns.ca/blog/2016/07/14/whats-sni/

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

THINGS TO KNOW https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/
* what HTTP request looks like
* send HTTP request from scratch - netcat https://jvns.ca/blog/2016/07/14/whats-sni/
* how to inspect network packet
* how TCP works - inspect packet, BYO

## what happens when

* browser looks up IP addr for domain via DNS
* browser establishes connection to web server
* browser sends HTTP req
* website processes the req and returns res
* browser renders page

---

📙 `evans-networking-ack.pdf` https://www.youtube.com/watch?v=AlkDbnbv7dk
* https://danluu.com/navigate-url/
* https://intronetworks.cs.luc.edu/
* https://drewdevault.com/2016/12/06/A-broad-intro-to-networking.html
* https://www.warp.dev/blog/what-happens-when-you-open-a-terminal-and-enter-ls
* https://github.com/reorx/httpstat
* _request flow_: browser cache, hosts file (`/private/etc/hosts` on macOS) router [`evans-tcpdump.pdf`], DNS cache, DNS server (local ISP, then eventually if you're unlucky to a root server, who point your query to the .coms or .govs or what have you)
* https://eater.net/inet
* https://wsvincent.com/what-happens-when-url/ DNS, req, res, render HTML, go get further (css, img, js), async as necessary
* https://wsvincent.com/how-does-the-internet-work/ https://wsvincent.com/how-the-web-works/ 

# 📇 HEADERS

----

```txt
b'{"result":{"email":"example@example.com","verdict":"Valid","score":0.79798,"local":"example","host":"example.com","checks":{"domain":{"has_valid_address_syntax":true,"has_mx_or_a_record":true,"is_suspected_disposable_address":false},"local_part":{"is_suspected_role_address":false},"additional":{"has_known_bounces":false,"has_suspected_bounces":false}},"source":"NEWSLETTER","ip_address":"72.94.2.75"}}'
Server: nginx
Date: Mon, 13 Jan 2025 13:28:46 GMT
Content-Type: application/json
Content-Length: 403
Connection: close
x-amzn-requestid: 05f0a3e7-6046-4267-949c-6c2dc6b0b19b
x-amz-apigw-id: EVA6SHYTiYcEm6A=
x-amzn-trace-id: Root=1-6785150e-0fa4e01142ccd6350f016809;Parent=35d4809259c0d1ad;Sampled=0;Lineage=1:3bae0364:0
access-control-allow-methods: HEAD, GET, PUT, POST, DELETE, OPTIONS, PATCH
access-control-max-age: 21600
access-control-expose-headers: Link, Location
access-control-allow-origin: *
access-control-allow-headers: AUTHORIZATION, Content-Type, On-behalf-of, x-sg-elas-acl, X-Recaptcha, X-Request-Source, Browser-Fingerprint
content-security-policy: default-src https://api.sendgrid.com; frame-src 'none'; object-src 'none'
x-content-type-options: nosniff
strict-transport-security: max-age=31536000
x-robots-tag: noindex, nofollow
x-client-ff: 1000
x-ratelimit-remaining: 6
x-ratelimit-limit: 7
x-ratelimit-reset: 1736774927
twilio-request-id: RQ2rZmMtSDlZOINuptlW1SkR2KDcE
x-envoy-upstream-service-time: 337
Powered-By: Mako
Cache-Control: no-cache
Referrer-Policy: strict-origin-when-cross-origin
```

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

## caching

📙 Enberg latency https://www.manning.com/books/latency
🗄 
* `distributed.md` caching
* `system/infra.md` caches

```txt
├── Caching-Headers/
│   ├── Cache-Control (Request/Response)
│   ├── Pragma (Request)
│   ├── ETag (Response)
│   ├── Expires (Response)
│   ├── Last-Modified (Response)
│   └── If-* Conditional Headers (Request)
│       ├── If-Modified-Since
│       ├── If-None-Match
│       └── If-Match
```

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

## cookies

🗄 `application.md` caching
📚 `gourley-http.pdf` chapter 11
🔗 https://tools.ietf.org/html/rfc7235 

---

https://grayduck.mn/2024/11/21/handling-cookies-is-a-minefield/ shadowing https://news.ycombinator.com/item?id=42206556
* _cookie_: val set by server
```python
from http import cookies
c = cookies.SimpleCookie()
c['foo'] = 'foo val'
c.output()
'Set-Cookie: foo="foo val"'
```

auth flow https://security.stackexchange.com/q/87269
* req: form data to auth
* res: server generates session id -> uses session id to generate cookie for 'set-cookie' header -> res w/ 302
* req: browser redirects to new URL -> sends its new cookie value along
* res: server maps cookie to session id -> auths req

---

https://www.alexedwards.net/blog/working-with-cookies-in-go

🔗 https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies https://en.wikipedia.org/wiki/HTTP_cookie

authorization types https://testdriven.io/blog/flask-spa-auth/
* _session-based_: uses cookies
* _token-based_: uses localStorage

* HTTP basic auth https://blog.luisrei.com/articles/flaskrest.html https://www.youtube.com/watch?v=VW8qJxy4XcQ
* https://www.youtube.com/channel/UCnWO-PRzuPnPBg0KCg_RVPA https://developer.mozilla.org/en-US/docs/Web/HTTP
* HTTPS https://howhttps.works/ https://realpython.com/python-https/
* https://lchsk.com/stay-paranoid-and-trust-no-one-overview-of-common-security-vulnerabilities-in-web-applications.html https://24ways.org/2018/securing-your-site-like-its-1999/ https://hackernoon.com/10-common-security-gotchas-in-python-and-how-to-avoid-them-e19fbe265e03 https://kushaldas.in/posts/highest-used-python-code-in-the-pentesting-security-world.html https://www.freecodecamp.org/learn/information-security/information-security-projects/

diff btw cookie and token
* https://stackoverflow.com/q/17000835
* lots of people have this question https://stackoverflow.com/questions/1592534/what-is-token-based-authentication
* does user/pw on Django use cookies?
* token (identification) cookie (association); sites arent' after whether you are really you, just want to know associations around you (age, credit worthiness) in order to server ads?
* https://stackoverflow.com/a/38470665
* SSO https://workos.com
* https://stackoverflow.com/a/50002308
* https://testdriven.io/blog/web-authentication-methods/
* https://www.youtube.com/watch?v=dinuA2KM3B4
* https://increment.com/apis/land-before-modern-apis/
* https://fly.io/blog/api-tokens-a-tedious-survey/ https://news.ycombinator.com/item?id=28295348
* cookies and sessions https://eli.thegreenplace.net/2011/06/24/django-sessions-part-i-cookies/
* email/pass https://learndjango.com/tutorials/django-log-in-email-not-username user/pass https://www.arp242.net/email-auth.html https://news.ycombinator.com/item?id=18767767 https://news.ycombinator.com/item?id=2861288

cookies https://tools.ietf.org/html/rfc2965
* _cookie_: opaque string sent to server for use as key to map to session https://eli.thegreenplace.net/2011/06/24/django-sessions-part-i-cookies/ https://stackoverflow.com/a/38470665
```js
// res
Set-Cookie: my_cookie_name=my_cookie_value
// req
Cookie: my_cookie_name=my_cookie_value
```
* can also store metadata (whether or not to remember your previous login) https://www.youtube.com/watch?v=QWw7Wd2gUJk 2:30
* view in browser via: dev tools > application > cookie https://www.youtube.com/watch?v=nfNrfi7HmLs
* https://news.ycombinator.com/item?id=25459530
* https://www.jefftk.com/p/why-i-work-on-ads
* _container_: separate cookies for different services (social, banking) https://hacker-tools.github.io/security/
* sessions 🗄 `system.md` caching

session
* collection of info re: instance of user interaction https://medium.com/@peterchang_82818/difference-session-cookie-token-vs-token-authentication-based-traditional-store-a177e8474ee3
* stored on server (typically via KV store like Redis bc non-volatile)
* _sticky_: each req from same user goes to same server (via load balancer)
* _fat URL_: URL incl user info [Gourley 11.5]

cookie types https://en.wikipedia.org/wiki/HTTP_cookie#Terminology
* _persistent_: login info
* _session_: date on this particular visit to site
* _3rd party_: tracking i.e. data brokerage

tracking w/ cookies
> Why does a website that orders food from restaurants need a Megabyte of javascript?6 I tried to figure that out by inspecting the API calls. It turned out they were tracking every mouse event. https://whatisjasongoldstein.com/writing/help-none-of-my-projects-want-to-be-spas/
* how it works: sent back to originator (e.g. FB) when 3rd party site include scripts (e.g. Like button, Google analytics) https://www.youtube.com/watch?v=QWw7Wd2gUJk 4:00
* _cookie policy_: list of other sites to whom cookies sent [ibid 5:00]
* regulation: ubiquitous GDPR banner to accept cookies
* block tracking cookies w/ extension (Privacy Badget, Ghostery) or browser (Brave, Safari)
* https://robertheaton.com/2017/11/20/how-does-online-tracking-actually-work/ https://robertheaton.com/2017/11/21/cookie-syncing-how-online-trackers-talk-about-you-behind-your-back/ https://robertheaton.com/2017/11/24/identity-graphs-how-online-trackers-follow-you-across-devices/ https://marvinblum.de/blog/server-side-tracking-without-cookies-in-go-OxdzmGZ1Bl

## connection

```txt
├── Connection-Management-Headers/
│   ├── Host (Request)
│   ├── Connection (Request/Response)
│   ├── Keep-Alive (Request/Response)
│   ├── Transfer-Encoding (Response)
│   └── Trailer (Response)
├── Redirection-Headers/
│   ├── Location (Response)
│   └── Retry-After (Response)
├── Client-Information-Headers/
│   ├── User-Agent (Request)
│   ├── From (Request)
│   └── Via (Request/Response)
```

* do not track: sites just ignore https://lwn.net/Articles/826575/
* _Allow_: what verbs applicable for endpoint
* _Location_: for 301 or 3xx 🗄 `book-db`
* _User-Agent_: info on client 🗄️ crawlers
* _Keep-Alive_: keeps the underlying TCP connection open for period of time
* normally this would close after each request https://lob.com/blog/use-http-keep-alive

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

## custom

```txt
x-amzn-requestid: 05f0a3e7-6046-4267-949c-6c2dc6b0b19b
x-amz-apigw-id: EVA6SHYTiYcEm6A=
x-amzn-trace-id: Root=1-6785150e-0fa4e01142ccd6350f016809;Parent=35d4809259c0d1ad;Sampled=0;Lineage=1:3bae0364:0
x-content-type-options: nosniff
x-robots-tag: noindex, nofollow
x-client-ff: 1000
x-ratelimit-remaining: 6
x-ratelimit-limit: 7
x-ratelimit-reset: 1736774927
x-envoy-upstream-service-time: 337
Cache-Control: no-cache
```

## rate limiting

🗄️ `api.md` rate limiting

```txt
Retry-After          # Client suggests delay before retry
Rate-Limit-Rules     # Client indicates its rate limiting capabilities (draft spec)
Retry-After          # Server specifies delay before retry (seconds or HTTP date)
RateLimit-Limit      # Request limit
RateLimit-Remaining  # Requests remaining in window
RateLimit-Reset      # Window reset time in seconds
RateLimit-Policy     # Machine-readable rate limit policy (draft spec)
X-RateLimit-*        # Non-standard but common variations used by many APIs
```
```txt
A few key points:
* Many APIs use custom X- prefixed headers for rate limits
* The standardized RateLimit-* headers are relatively new (2022)
* Retry-After can be either seconds or HTTP date format
* The reset time is Unix timestamp in UTC

When implementing retry logic, the hierarchy usually goes:
* Honor Retry-After if present
* Use RateLimit-* headers to calculate optimal retry timing
* Fall back to exponential backoff if no headers available

If you're building an API, the most backward-compatible approach is to implement both standard and X- prefixed versions of the rate limit headers.
```

```txt
x-ratelimit-remaining: 6
x-ratelimit-limit: 7
x-ratelimit-reset: 1736774927
```

## security

```txt
├── Security-Headers/
│   ├── Authentication/
│   │   ├── Authorization (Request)
│   │   ├── Proxy-Authenticate (Response)
│   │   └── WWW-Authenticate (Response)
│   ├── Transport-Security/
│   │   ├── Strict-Transport-Security (Response)
│   │   └── Upgrade-Insecure-Requests (Request)
│   ├── Content-Security/
│   │   ├── Content-Security-Policy (Response)
│   │   ├── X-Content-Type-Options (Response)
│   │   ├── X-Frame-Options (Response)
│   │   └── Permissions-Policy (Response)
│   └── Privacy/
│       ├── Referrer-Policy (Request/Response)
│       └── Sec-Fetch-* Headers (Request)
```

🗄 `security.md` auth

* https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Authentication_schemes https://tools.ietf.org/html/rfc7235#section-2.1
* _WWW-Authenticate_: res to auth https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate
* _Authorization_: req w/ credentials in the form `<scheme> <credentials>` https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization

security https://securityheaders.com/
* _Access-Control-Allow-Headers_: headers accepted by server; if doesn't support method from client, server throws error https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers
* _CORS_: 
* _Strict-Transport-Security (HSTS)_: tell browser only use HTTPS (browser automatically makes subsequent requests using HTTPS) https://jvns.ca/blog/2017/04/30/using-strict-transport-security/

## tokens

* _token_: opaque obj (string, JSON) sent to server for auth https://stackoverflow.com/a/38470665
```js
// req
Authorization: Bearer my_bearer_token_value
```

types
* _basic_: base64 encoded https://blog.luisrei.com/articles/flaskrest.html
* _bearer_: crypto signed
* used by OAuth https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Authentication_schemes
* _JWT_: 📍 http://eradman.com/posts/practical-jwt.html https://github.com/jwt-rs/jwt-ui

approaches
* _stateless_: contains hashed version of user info (id, auth) https://en.wikipedia.org/wiki/Access_token
* _stateful_: hash used to lookup info about user server-side https://drewdevault.com/2020/06/21/BARE-message-encoding.html the token store become SPoF https://www.jbspeakr.cc/purpose-jwt-stateless-authentication/

JWT
* _JWT_: JSON obj holds claims; RFC 7519
* _claim_: key in dict https://auth0.com/docs/tokens/json-web-tokens/json-web-token-claims https://softwareengineering.stackexchange.com/a/350094/322090
* _JWS_: thing signing JWT https://stackoverflow.com/a/27642457
* _JWE_: thing encrypting JWT https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/
* req/res flow similar to cookie/session but JWT is encrypted and thus able to be stateful https://medium.com/@peterchang_82818/difference-session-cookie-token-vs-token-authentication-based-traditional-store-a177e8474ee3 https://softwareengineering.stackexchange.com/a/350094/322090
* apparently the spec is too murky and the implementations conflict and thus people are moving away from JWT https://simonwillison.net/2020/Aug/1/jwt/
* https://www.youtube.com/watch?v=tfKatqbZicA https://github.com/dwyl/learn-json-web-tokens/
* https://github.com/jpadilla/pyjwt

# 🔢 STATUS CODES

🔗
* Julia Evans https://www.youtube.com/watch?v=xYv8wcNJiKw
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
* https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
* https://www.youtube.com/watch?v=_qKgO8BPHWc
* https://wompa.land/articles/http-status-codes

* _100s_: info

## 🟢 200s

* _200_: "GET/PUT worked + data for you"
* _201_: "POST worked"
* _204_: "PUT/PATCH/DELETE worked"

## 🔄 300s (redirect)

* _301_: "what you're looking for isn't there, here is it's actual URL" (e.g. Django when trailing slash is missing)
* _302_: "POST worked, let's go there now" (followed by a GET from the browser and 200 from server i.e. POST-redirect-GET)
* _303_: "can't POST bc resource already exists"; could also be a 409 https://stackoverflow.com/q/3825990/6813490
* _304_: "based on `Cache-Control` the resource hasn't change so I'll redirect you to browser cache"

## 🙈 400s (client err)

* _400_: bad request e.g. sent POST but missing required field
* _401_: "plz authenticate"
* _403_: "ur not authorized" https://stackoverflow.com/a/6937030
* _404_: resource not found
* _405_: auth-ed, resource found, but method unallowed
* _406_: can't find resource with right content type
* _429_: rate limited

## 🛑 500s (server err)

* _500_: general (in the same way 200 and 400 are general)
* _501_: client not supported e.g. you want to tell Android client it needs to upgrade
* _502_: server handling your request got an error from a downstream
* _503_: server down
> 502-504 all have similar meanings and it ends up being that the service you're trying to reach can't respond to the request
* _504_: server handling your request is tired of waiting for a downstream
* _522_: time out; TCP connection btw web server and CDN (bc server is overloaded) https://www.youtube.com/watch?v=axYMNCuL_hE

# 🛠️ TOOLING

🗄 `shell.md` userland

https://github.com/monasticacademy/httptap
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

## kulala

https://github.com/mistweaverco/kulala.nvim

## posting

https://github.com/darrenburns/posting 
https://pythonbytes.fm/episodes/show/409/weve-moved-to-hetzner-write-up

## xh

https://github.com/ducaale/xh

# 🟨 ZA

* _tarpit_: purposefully slow responses e.g. delay, send partial, add artificial latency between headers and body https://news.ycombinator.com/item?id=31509523 https://chatgpt.com/c/674a3d23-5e98-8004-aa33-c1cde00d2bea https://news.ycombinator.com/item?id=42725147

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
