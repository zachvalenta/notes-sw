# ⛩️

## 参考

🧪 https://github.com/zachvalenta?tab=repositories&q=django
🗣 https://djangochat.com/episodes https://forum.djangoproject.com/
📜 
* https://docs.djangoproject.com/en/stable
* https://github.com/HackSoftware/Django-Styleguide
* https://github.com/wsvincent/lithium
📚
* Layman https://www.mattlayman.com/understand-django/
* ⭐️ Palmieri zero to prod in rust https://www.amazon.com/Zero-Production-Rust-introduction-development/dp/B0BHLDMFDQ https://www.zero2prod.com/index.html
* Trudeau https://www.manning.com/books/django-in-action 🗄️ checklist
* Vincent beginners (3.0) https://learndjango.com/courses/django-for-beginners https://github.com/wsvincent/djangoforbeginners
> (no longer available as PDF) but you have access to his course https://wsvincent.com/year-in-review-2024/

## 进步

* _25_: 📙 Vincent beginners https://learndjango.com/courses/django-for-beginners/chapter-2-hello-world-website/ @ initial setup https://github.com/zachvalenta?tab=repositories&q=vincent&type=&language=&sort=
* _21_: DML
* _20_: CRUD (ORM, serialization, repl) env (conf, Docker) CQ (testing) DRF (views, nested serializers, testing, read_only) middleware (403 req based on IP addr)
* _19_: 📙 Osborn hello web app
* _18_: skim official tutorial and Ekker course, DRF and ORM at work

# 🛰️ API

## DRF

📙 Vincent api
🗄 `python/stdlib.md` serde

---

SPEED
* caching https://www.screamingatmyscreen.com/caching-and-django-rest-framework
* read-only fields, `serializers.Serializer` 3x faster than `serializers.ModelSerializer` https://hakibenita.com/django-rest-framework-slow

ZA
* https://learndjango.com/tutorials/official-django-rest-framework-tutorial-beginners
* refresh https://learndjango.com/tutorials/official-django-rest-framework-tutorial-beginners
* https://www.youtube.com/watch?v=06DJBu1zwoY https://www.laceyhenschel.com/blog/2021/2/22/what-you-should-know-about-drf-part-1-modelviewset-attributes-and-methods
* serialization can be expensive, can drop when you need perf https://hakibenita.com/django-rest-framework-slow
* exclude field https://www.django-rest-framework.org/community/3.4-announcement/#use-fields-or-exclude-on-serializer-classes
* fields defaults to string https://www.django-rest-framework.org/tutorial/1-serialization/#creating-a-serializer-class
* dataclasses https://github.com/oxan/djangorestframework-dataclasses
* similar to Django forms
```python
class Thing(models.Model):
    name = models.CharField(max_length=255)
    description = models.TextField()
    slug = models.SlugField(unique=True)

class ThingForm(ModelForm):
    class Meta:
        model = Thing
        fields = ('name', 'description')

if request.method == 'POST':
    form = ThingForm(data=request.POST, instance=thing)
    if form.is_valid():
        form.save()
        return redirect('thing_detail', slug=thing.slug)
```

## middleware

📜
* https://docs.djangoproject.com/en/3.1/topics/http/middleware/
* https://docs.djangoproject.com/en/5.1/topics/db/instrumentation/ https://adamj.eu/tech/2024/12/05/django-sql-breakpoint/

* hook in req/res cycle
* middleware obj takes req and return res
* can put anywhere in your src
* used in logging?
* called in order of elements in `MIDDLEWARE` in `settings.py` https://docs.djangoproject.com/en/3.1/topics/http/middleware/#middleware-order-and-layering

```python
# api/middleware.py
class Safelist:
    def __init__(self, get_response):
        self.get_response = get_response
    def __call__(self, request):
        print("BEFORE VIEW")
        response = self.get_response(request)
        print("AFTER VIEW")
        return response

# settings.py
MIDDLEWARE = [
    'api.middleware.Safelist',
]
```

restrict requests by IP
* DRF https://www.django-rest-framework.org/api-guide/permissions/ https://www.laurencegellert.com/2019/04/django-rest-framework-how-to-whitelist-safelist-ip-addresses/
* middleware https://riptutorial.com/django/example/6909/middleware-to-filter-by-ip-address https://stackoverflow.com/questions/12383540/authenticate-by-ip-address-in-django
* Nginx https://stackoverflow.com/a/20831562/6813490
```python
class IPSafelist:
    safe = os.getenv("SAFELIST")

    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        print(f"\nreq sent from: {request.META['REMOTE_ADDR']}\n")  # https://stackoverflow.com/a/12384539
        if not request.META["REMOTE_ADDR"] == self.safe:
            return HttpResponseForbidden()
        response = self.get_response(request)
        return response
```

---

https://www.youtube.com/watch?v=3yKuKQ2fuys

* provides thread info (req, user) to app components that otherwise wouldn't have access

* `MIDDLEWARE = []`: everything inside called on each request
```python
from threading import local

_thread_locals = local()

def get_current_request():
    return getattr(_thread_locals, 'request', None)

def get_current_user():
    request = get_current_request()
    if request:
        user = getattr(request, 'user', None)
        if isinstance(user, User):
            return user
```

## serialization

🗄 `system.md` serialization `python.md` serialization
🔗 https://books.agiliq.com/projects/django-api-polls-tutorial/en/latest/

```python
###
# DRF https://www.django-rest-framework.org/api-guide/serializers/ https://testdriven.io/blog/drf-serializers/
###

# basics
class PostSerializer(serializers.ModelSerializer):
    class Meta:
        model = models.Post
        fields = ('id', 'title', 'content')  # defaults to __all__ https://www.django-rest-framework.org/api-guide/serializers/#specifying-which-fields-to-include

class FooView(generics.ListViewAPI):
    queryset = Post.objects.all()
    serializer_class = PostSerializerer

# type flow
from rest_framework.renderers import JSONRenderer
foo = Foo.objects.get(id=1)  # model instance
foo_serial = FooSerializer(foo)  # DRF instance
foo_serial.data  # DRF typed dict
JSONRenderer().render(foo_serial.data)  # byte string

# read_only = shows up in GET but not required for POST https://www.django-rest-framework.org/api-guide/serializers/#specifying-read-only-fields
from rest_framework.serializers import BooleanField
class FooSerializer(ModelSerializer):
    success = BooleanField(read_only=True)
    class Meta:
        fields = ['foo', 'bar', 'success']
        model = FooModel

###
# vanilla https://docs.djangoproject.com/en/3.0/topics/serialization/
###

from django.core import serializers
from django.http import JsonResponse
JsonResponse({"things" : list(Things.objects.all())})  # https://www.youtube.com/watch?v=dfIF7qDDbW8& 14:30
serializers.serialize("things", Thing.objects.all())

# add field to payload before deserialize
class Serializer:
    def to_internal_value(self, data): 
        data['foo'] = 'foo content' 
        return super().to_internal_value(data)
```

nested
* `StringRelatedField` https://www.django-rest-framework.org/api-guide/relations/#stringrelatedfield https://stackoverflow.com/questions/31936401/string-related-field-in-djangorest https://github.com/zachvalenta/django-crud/commit/f0e1b0b4be18289d807e6b012c1ecc11cfa545ef#diff-39f8266a93579ae5dbdb3790c2bfda58R6
* GET nested attr e.g. `parent/1/children` https://www.django-rest-framework.org/api-guide/relations/#custom-hyperlinked-fields https://stackoverflow.com/questions/62156484/drf-create-object-with-nested-serializers-and-foreign-keys
* POST parent and child: impl `create()` https://www.django-rest-framework.org/api-guide/relations/#writable-nested-serializers
```json
{
    "parent_field": "foo val",
    "children": [
        {
            "child_field": "foo val"
        }
    ]
}
```

## URLs

howto
* show all: django-extensions + `manage.py show_urls` https://stackoverflow.com/a/8844834
* split into n modules https://stackoverflow.com/q/26047610
```python
# parent module
urlpatterns = patterns(
    # child module = /src/api.urls.py
    url(r'^api', include('src.api.urls')),
)
```

wiring
* each urlpattern iterated, first match returned
* if call from DTL link, looks for name as opposed to route https://docs.djangoproject.com/en/2.2/topics/http/urls/#how-django-processes-a-request

---

* wiring
```python
from django.urls import path  # create URL obj
from django.urls import include  # point to app-level URLs

urlpatterns = [
    # syntax: route - view - name [Osborn 1 10.64]

    # function-based
    path('', func_views.foo, name='foo_func'),  # use kwarg for name https://stackoverflow.com/a/19670235/6813490 [Osborn 1 4.14]
    # class-based
    path('', ClassView.as_view(), name='bar_class'),
    # template-only https://wsvincent.com/django-about-page-three-ways/
    url(r'^about/', TemplateView.as_view(template_name='about.html'), name='about'),
]

# URL forwarding
return redirect('thing_detail', slug=thing.slug)
path('thing/<slug>', views.thing_detail, name='thing_detail'),
```

---

* public facing IDs https://spikelantern.com/articles/options-for-public-facing-ids-in-django
* _trailing slash_: if URL has trailing slash but user/browser doesn't input Django will 301 to correct URL via `APPEND_SLASH` https://learndjango.com/tutorials/trailing-url-slashes-django
```makefile
# n.b. these URLs don't need trailing slash bc: req via Chrome, Django 301, Chrome redirect
gui:
	open $(api_url)/
```
* `urlpatterns`: ways to map to view; more accurate to think of this way than simply 'URLs' bc actually two ways to map to view (URL, pattern name) and DTL links dont' even need the patterns URL to perform lookups (will still interpolate query string KV pairs but otherwise the FQDN kinda incidental here)
* _why named URL pattern?_ modularity; can change internal naming without update links for external consumers
* `urls.py`: manifest of all routes; project-level
* _methods_: `render()` take files `redirect()` take URL name `url` take URL name
* can override built-in admin templates when using built-in views [Osborn 1.10.73]

## views

🔗 https://spookylukey.github.io/django-views-the-right-way/

* https://spookylukey.github.io/django-views-the-right-way/

* get query string https://www.django-rest-framework.org/api-guide/filtering/#filtering-against-query-parameters
```txt
http://app.com/foo/?top=10
request.query_params
```

status codes
* 200: `HttpResponse` https://docs.djangoproject.com/en/3.1/ref/request-response/#httpresponse-objects
* 500: `HttpResponseServerError` https://docs.djangoproject.com/en/3.1/ref/request-response/#django.http.HttpResponseServerError `Response(content, status=status.HTTP_500_INTERNAL_SERVER_ERROR)` https://www.django-rest-framework.org/api-guide/status-codes/#server-error-5xx

DRF http://www.cdrf.co/ https://www.django-rest-framework.org/api-guide/views/
* setup: register DRF with project, register model with serializer, use serializer in view, urls (map to views, register w/ project)
* _view_: handles impl for HTTP method(s)
* _viewset_: collection of views; designed to be used with routers vs. explicit URLs https://www.django-rest-framework.org/tutorial/6-viewsets-and-routers/
* _ListAPIView_: GET all
* _ListCreateAPIView_: GET all, POST single
* _RetrieveAPIView_: GET single
* _RetrieveUpdateDestroyAPIView_: GET/PUT/PATCH/DELETE single
* _ModelViewSet_: combination of ListCreateAPIView and RetrieveUpdateDestroyAPIView

vanilla https://wsvincent.com/class-function-based-views/
* _function-based_: route on control flow
* https://406.ch/writing/composition-over-inheritance-the-case-for-function-based-views/
* https://github.com/carltongibson/neapolitan
* _class-based_: route on method sig https://docs.djangoproject.com/en/2.2/topics/class-based-views/
* _generic class-based_: 类似 DRF views http://ccbv.co.uk/
```python
###
# FBV
###

def index(request):
    if request.method == 'GET':
        return HttpResponse("GET")
    elif request.method == 'POST':
        return HttpResponse("POST")

###
# CBV
###

class PollsViews(View):
    def get(self, request):
        return HttpResponse("GET")
    def post(self, request):
        return HttpResponse("POST")

###
# GCBV
###

# single entity
class DetailView(generic.DetailView):
    model = Question
    template_name = 'polls/detail.html'

# all entities
class IndexView(generic.ListView):
    template_name = 'polls/index.html'
    context_object_name = 'latest_question_list'
    def get_queryset(self):
        return Question.objects.order_by('-pub_date')[:5]
```

# 🔑 AUTH

🗄 `security.md` users

history https://wsvincent.com/django-user-model-talk/ https://www.youtube.com/watch?v=458KmAKq0bQ 
> Django's leaky battery is its recommendation that you create a custom user model. Auth is so central and so standard that, into the high-nines (99.99%?), the vast majority of projects should never need to customise the central auth model. This is a battery that Django should very much provide. There's a complexity tax from exposing the auth model. There's a performance tax as the auth model becomes a generic dumping ground for User related data that has nothing to do with authentication. There's a learning tax as users hit the custom user model, and the (frankly, misplaced) warnings about it's importance. https://github.com/carltongibson/django-unique-user-email

## users

* mgmt https://realpython.com/django-user-management/
* email https://github.com/carltongibson/django-unique-user-email
* current user https://github.com/zsoldosp/django-currentuser
* groups https://github.com/bennylope/django-organizations
* automate admin user creation https://stackoverflow.com/a/26091252
* mimic user's account https://www.mattlayman.com/blog/2020/hijack-to-help-customers/
* referencing user model https://learndjango.com/tutorials/django-best-practices-referencing-user-model

## permissions

* https://learndjango.com/tutorials/django-best-practices-user-permissions
* https://wsvincent.com/django-tips-user-permissions/
* https://coderbook.com/@marcus/how-to-restrict-access-with-django-permissions
* https://testdriven.io/blog/drf-permissions/

## default

* built-in https://wsvincent.com/django-user-authentication-tutorial-login-and-logout/ 
* basic https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Authentication https://tech.marksblogg.com/passwords-in-django.html
* https://docs.djangoproject.com/en/5.1/ref/contrib/auth/#user-model
* https://learndjango.com/tutorials/django-login-and-logout-tutorial
* login/out https://learndjango.com/tutorials/django-login-and-logout-tutorial
* signup https://learndjango.com/tutorials/django-signup-tutorial
* reset https://learndjango.com/tutorials/django-password-reset-tutorial
* with email https://learndjango.com/tutorials/django-log-in-email-not-username
* keep track of failed logins https://github.com/jazzband/django-axes

## custom

```txt
There are two modern ways to create a custom user model in Django: AbstractUser and AbstractBaseUser. In both cases, we can subclass them to extend existing functionality; however, AbstractBaseUser requires much, much more work. Seriously, only mess with it if you know what you're doing. And if you did, you wouldn't be reading this tutorial, would you?

So we'll use AbstractUser, which subclasses AbstractBaseUser but provides more default configuration.
```

* `AbstractUser`: everything from default user model except `PermissionsMixin`
```python
# myapp/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    phone_number = models.CharField(max_length=15, blank=True, null=True)

# settings.py
AUTH_USER_MODEL = "myapp.CustomUser"
```
* `AbstractBaseUser`: gives you pw and last_login, necessary for pw refresh tokens https://www.youtube.com/watch?v=458KmAKq0bQ @ 14:00 
* https://learndjango.com/tutorials/django-custom-user-model
* https://docs.djangoproject.com/en/5.0/topics/auth/customizing/#using-a-custom-user-model-when-starting-a-project
* https://testdriven.io/blog/django-custom-user-model/
* Kerberos/LDAP/Active Directory, `AbstractBaseUser` https://www.roguelynn.com/words/django-custom-user-models/
* https://brntn.me/blog/six-things-i-do-every-time-i-start-a-django-project/

## magic links

* https://github.com/aaugustin/django-sesame
* https://news.ycombinator.com/item?id=42627453
* https://www.photondesigner.com/articles/email-sign-in

## registration-redux

* _routes_: Registration Redux owns everything under `accounts/` except when overridden by built-in auth [Osborn 1.10.69]
* sequence diagram
```
title Django auth flows w/ Registration Redux

group #orange change (logged in)
client->server:req reset
note right of server:validate
note right of server:update db
client<-server:ack
end

group #pink reset (can't login)
client->server:req reset
note right of server:update db
client<-server:email

group #lightgreen registration (new user)
client->server:input credentials
note right of server:validate
note right of server:update db (if not part of reset)
client<-server:ack
end

end
```
> 💡 RR is just view impl validation logic, so templates need to conform to RR names so that their views can render 
* _Osborn chapter 10_: `templates/registration/registration_form.html` and `registration_complete.html` are unnecessary, `/accounts/register` is owned by Registration Redux, we link to it from our `base.html` but after that RR calls its own view and renders its own templates, neither of which are overriden by the aforementioned ones
* _migrations_: let RR know about your user models
* _URLs_: add base domain to `urls.py` and reference subdomain URL pattern names in templates e.g. `base.html/auth_logout`
* _views_: you don't interact with these, but presumably implement password constraint validation 
what is this for? ⬇️
* 💡 this is a mix of Registration Redux and Django's built-in auth
* _registration_: `base.html` links to pattern name `registration_register` which is owned by Registration Redux, so clicking that matches the route to which the pattern name is mapped (`accounts/register`) and invokes that pattern's view, which handles the validation logic
* _login_: `base.html` links to pattern name `auth_login` (route `/accounts/login`) which is owned by Registration Redux, so it calls its own view and renders `registration/login.html` (if we've placed that template in that directory location, that is) --> `login.html` on POST will be handled by the same RR view that renders its GET and if successful will redirect to whatever we've specified in `settings.py/LOGIN_REDIRECT_URL` [Osborn 65]
* _reset_: `login.html` also kicks off our reset flow with a link to pattern name `password_reset`, which sends out an email using `pw_reset_email.txt` and then calls ` password_reset_done`, which just renders a template to ack; when the user follows the link they've been emailed they'll hit the `password_reset_confirm` view and if their guid is still valid that view will render `password_reset_confirm.html` and allow them to input a new pw (idk if same view is used for validation or if separate validation -only view is hit e.g. doesn't care about link validity) and if everything goes well 

## allauth

* https://wsvincent.com/django-allauth-tutorial/
* https://learndjango.com/tutorials/django-allauth-tutorial
* rest-auth https://testdriven.io/blog/django-rest-auth
* JWT https://www.mikesukmanowsky.com/blog/authentication-with-django-and-spas https://testdriven.io/blog/django-rest-authjs/

# ⚙️ CONFIG

---

* https://docs.djangoproject.com/en/stable/topics/settings/
* https://www.mattlayman.com/understand-django/settings/
* https://news.ycombinator.com/item?id=40688336
* https://docs.djangoproject.com/en/stable/ref/settings/

## denv

🗄️ `src.md` denv

---

https://blog.pecar.me/django-tui
* https://adamj.eu/tech/2021/12/08/pre-order-boost-your-django-dx/
* https://blog.ovalerio.net/archives/2420
* reload: watchman instead of django file watcher https://adamj.eu/tech/2021/01/20/efficient-reloading-in-djangos-runserver-with-watchman/ https://github.com/adamchainz/django-browser-reload

DEV SERVER ON REMOTE
* start cmd: `python manage.py runserver 0.0.0.0:8000`
* `ALLOWED_HOSTS`: if running on server need to add hostname; `localhost` seems to be implicit https://docs.djangoproject.com/en/dev/ref/settings/#allowed-hosts https://stackoverflow.com/a/46443432/6813490
* Docker: set `DEBUG=False` https://stackoverflow.com/a/60832028

🐚 SHELL https://docs.djangoproject.com/en/3.0/ref/django-admin/#shell https://docs.bpython-interpreter.org/en/latest/django.html
* kill server: https://startcodingnow.com/kill-django-development-server
```sh
ps aux | head --lines=1 && ps aux | grep 'manage.py runserver' | kill
```
* run script: `./manage.py shell < myscript.py` https://stackoverflow.com/a/16853799
* run script w/ env: https://django-extensions.readthedocs.io/en/latest/runscript.html https://www.b-list.org/weblog/2007/sep/22/standalone-django-scripts/
* autload models: `poetry run python manage.py shell_plus --bpython` https://django-extensions.readthedocs.io/en/latest/shell_plus.html
* `dbshell`: passes env var from `settings.py` to default CLI for dbms; https://github.com/dbcli/pgcli.com/blob/2f7a5aac0a9f5fa81670019301a12e9394a416da/content/django-pgcli.md 

🩻 SYSTEM CHECK
* https://github.com/metalogico/django-sonar
* https://adamj.eu/tech/2024/03/23/django-optimizing-system-checks/
* introspection for coding standards https://lukeplant.me.uk/blog/posts/enforcing-conventions-in-django-projects-with-introspection/
* https://adamj.eu/tech/2023/03/02/django-profile-and-improve-import-time/

## project structure

PROJECT
* _project_: dir w/ `settings.py` https://stackoverflow.com/q/50090341
```sh
poetry run django-admin startproject conf .
```
* `django-admin`: CLI for project https://docs.djangoproject.com/en/3.0/ref/django-admin/

APPS
* _app_: unit of functionality https://forum.djangoproject.com/t/why-do-we-need-apps/827
* name as normal package 🗄️ `python/runtime.py` packages
* don't overdo it https://news.ycombinator.com/item?id=26492798 https://news.ycombinator.com/item?id=26492043 https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/
* `manage.py`: CLI for app https://docs.djangoproject.com/en/3.0/ref/django-admin/

---

* different ways to structure https://learndjango.com/tutorials/hello-world-5-different-ways
* https://www.mostlypython.com/django-from-first-principles/ https://news.ycombinator.com/item?id=40140396
* https://noumenal.es/notes/django/single-folder-layout/
* check https://docs.djangoproject.com/en/3.0/ref/django-admin/#check https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework
* create `django-admin startapp <name>` https://hellowebbooks.com/setup/ `python manage.py startapp <name>` https://djangoforbeginners.com/hello-world/
* multiple ways to register app with project https://learndjango.com/tutorials/django-rest-framework-tutorial-todo-api https://wsvincent.com/django-rest-framework-tutorial/
* API in own app https://learndjango.com/tutorials/django-rest-framework-tutorial-todo-api in main app https://wsvincent.com/django-rest-framework-tutorial/

## security

---

https://snyk.io/blog/django-security-tips
* throttle auth
* don't use raw queries
* cookies over HTTPS
* no user uploads https://news.ycombinator.com/item?id=40221210
* mv admin url from `/admin/`; csrf = necessary for stuff w/ `POST` [📙 Osborn 1 9.59] 
* https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/web_application_security
* https://www.mattlayman.com/understand-django/secure-apps
* https://www.ponycheckup.com/ https://www.youtube.com/watch?v=8W4MGggwgfM https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/web_application_security generate secret key https://humberto.io/blog/tldr-generate-django-secret-key https://github.com/jamesturk/django-honeypot https://learndjango.com/tutorials/django-search-tutorial

## settings

---

https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/
https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/

* `settings.py`: just a Python module w/ buncha attributes; fmt installed apps same as imports https://wsvincent.com/django-rest-framework-tutorial/ uses pathlib as of 3.1 https://learndjango.com/tutorials/whats-new-django-31
* https://adamj.eu/tech/2022/11/24/django-settings-patterns-to-avoid/
* use OS https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment
* django-environ https://github.com/joke2k/django-environ
* python-dotenv https://www.untangled.dev/2020/05/31/django-environment-variables/

```conf
# dev
ENV=dev
SQLITE_DB_FILE="local.db"

# prod
ENV=prod
HOST=db
PORT=5432
NAME=postgres
USER=postgres
PASSWORD=postgres
```
```python
# https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
from dotenv import load_dotenv
load_dotenv()
if os.getenv("APP_ENV") == "dev":
    DEBUG = True
    DATABASES = {
        "default": {
            "ENGINE": "django.db.backends.sqlite3",
            "NAME": os.path.join(BASE_DIR, os.getenv("SQLITE_DB_FILE"))
        }
    }
if os.getenv("APP_ENV") == "prod":
    DEBUG = False
    DATABASES = {
        "default": {
            "ENGINE": 'django.db.backends.postgresql',
            "HOST": os.getenv("HOST"),
            "PORT": os.getenv("PORT"),
            "NAME": os.getenv("NAME"),
            "USER": os.getenv("USER"),
            "PASSWORD": os.getenv("PASSWORD"),
        }
    }
```

## static files

* `collectstatic`: rifle through `static` of each app and copy assets to project-level `static` https://www.smashingmagazine.com/2020/06/django-highlights-wrangling-static-assets-media-files-part-4/
* default is app-level `static` dir but everyone uses project-level directory `static` dir
* in production: WhiteNoise handles first request and subsequent hit Cloudflare cache https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#49:30 S3 https://0of1.com/blog/posts/django-staples/ https://testdriven.io/blog/storing-django-static-and-media-files-on-amazon-s3/ https://www.youtube.com/watch?v=E613X3RBegI more cache https://testdriven.io/blog/django-low-level-cache https://news.ycombinator.com/item?id=30324608
```python
# this is where admin static images are located -> django/contrib/admin/static/admin/img/icon-addlink.svg
# idk how it works but maybe something to do with installed_apps
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.staticfiles",
]
```

# 🍱 DB

🗄 `sql.md` SQLAlchemy

FLOW http://lucumr.pocoo.org/2011/7/19/sqlachemy-and-you/
* generates SQL i.e. lazy
* exec
* deserialize result set into Py obj
* update/save Py obj in mem
* `UPDATE` in SQL

---

* https://github.com/wagtail/queryish
* _F expression_: perform SQL operation without serializing data into Python obj first https://docs.djangoproject.com/en/3.1/ref/models/expressions/#f-expressions
* lazy evaluation https://docs.djangoproject.com/en/3.1/topics/db/queries/#querysets-are-lazy https://davit.tech/django-queryset-examples/#section-contents dangerous for property calls https://news.ycombinator.com/item?id=38518978
calculated property https://lukeplant.me.uk/blog/posts/django-pagni-efficient-bulk-properties/
```python
qs = Foo.objects.all()  # no eval
qs.filter(foo='foo val')  # no eval
qs.values_list  # eval on queryset access
```
* more focused on application logic than SQLAlchemy http://jmoiron.net/blog/about-sqlalchemy-and-djangos-orm/
```python
# SQLAlchemy - SQL
session.query(Book).join(Book, Author).filter(Author.age==27)
# Django - objects
Book.objects.filter(author__age=27)
```

TRANSACTIONS 🗄 `db.md` consistency
* enter atomic context:	`START TRANSACTION`
* exit atomic context w/out exception: `COMMIT`
* exit atomic context w/ exception: `ROLLBACK`
* default is autocommit mode i.e. "Each query is immediately committed to the database, unless a transaction is active." https://docs.djangoproject.com/en/3.2/topics/db/transactions/#django-s-default-transaction-behavior
* there is much more to learn https://charemza.name/blog/posts/django/postgres/transactions/not-as-atomic-as-you-may-think/

📜 https://docs.djangoproject.com/en/3.2/#the-model-layer
🔍
* https://djangocentral.com/django-orm-cheatsheet/
* https://books.agiliq.com/projects/django-orm-cookbook/en/latest/

* https://github.com/dabapps/django-zen-queries
> QuerySets are lazy – the act of creating a QuerySet doesn’t involve any database activity. You can stack filters together all day long, and Django won’t actually run the query until the QuerySet is evaluated. https://docs.djangoproject.com/en/3.1/topics/db/queries/#querysets-are-lazy
how to
* http://blog.abedmaatalla.me/2020/12/django-orm-optimization-tips.html
* ❓ implicit queries https://news.ycombinator.com/item?id=34936023
* GeneratedField https://www.paulox.net/2023/11/07/database-generated-columns-part-1-django-and-sqlite/
* catch dirty model instances https://github.com/romgar/django-dirtyfields
* anonymize data https://github.com/Tesorio/django-anon
* audit table https://github.com/jazzband/django-simple-history https://github.com/jazzband/django-auditlog
* graph ER model https://github.com/meshy/django-schema-graph/
* generate view from queryset https://schinckel.net/2020/03/03/postgres-view-from-django-queryset
* rich text / blob https://github.com/withlogicco/django-prose

## admin

---

> The admin's recommended use is limited to an organization's internal management tool. It's not intended for building your entire front end around. https://docs.djangoproject.com/en/5.1/ref/contrib/admin/

* TUI https://github.com/valberg/django-admin-tui
* theme https://github.com/sjbitcode/django-admin-dracula
* management commands https://adamj.eu/tech/2024/08/14/django-management-command-sub-commands/
* https://github.com/cuducos/django-public-admin
* https://github.com/simonw/django-sql-dashboard
* https://roman.pt/posts/django-admin-and-service-layer/
* https://testdriven.io/blog/customize-django-admin/
* https://github.com/koleror/django-admin-views
* https://www.youtube.com/watch?v=CgJziscOafw
* https://news.ycombinator.com/item?id=30321330
* db GUI [Osborn 1.6.37]
* styling won't work unless `debug=True` https://stackoverflow.com/a/50868962
* register model w/ `admin.py` https://books.agiliq.com/projects/django-admin-cookbook/en/latest/
* for analytics https://github.com/otto-torino/django-baton
* config color https://www.dothedev.com/blog/django-admin-change-color/ https://realpython.com/customize-django-admin-python/ https://github.com/farridav/django-jazzmin https://www.mattlayman.com/understand-django/administer-all-the-things
* config timezone https://til.simonwillison.net/django/show-timezone-in-django-admin

## DDL

* https://blog.bmispelon.rocks/articles/2024/2024-05-09-django-getting-a-full-model-instance-from-a-subquery.html
* create uuid for record for API https://0of1.com/blog/posts/django-staples/
* phone numbers https://0of1.com/blog/posts/django-staples
* make everything read-only https://github.com/adamchainz/django-read-only
* multi-table inheritance https://monadical.com/posts/django-packages.html
* _custom fields_: https://docs.djangoproject.com/en/dev/howto/custom-model-fields/
* _index_: `db_index=True` https://www.djangorocks.com/snippets/indexing-your-django-models.html without downtime https://realpython.com/create-django-index-without-downtime/ https://adamj.eu/tech/2020/07/27/how-to-modernize-your-django-index-definitions
* _meta_: anything that's not a field
* _PK_: uuid https://docs.djangoproject.com/en/dev/ref/models/fields/#uuidfield https://books.agiliq.com/projects/django-orm-cookbook/en/latest/uuid.html https://books.agiliq.com/projects/django-orm-cookbook/en/latest/slugfield.html

* related_name and 1-M https://books.agiliq.com/projects/django-orm-cookbook/en/latest/one_to_many.html https://docs.djangoproject.com/en/dev/ref/models/fields/#django.db.models.ForeignKey.related_name 🗄 
```python
class Parent(models.Model):

# no change to underlying table
+-----+----------+--------------+---------+------------+----+
| cid | name     | type         | notnull | dflt_value | pk |
+-----+----------+--------------+---------+------------+----+
| 0   | id       | integer      | 1       | <null>     | 1  |
| 1   | name     | varchar(255) | 1       | <null>     | 0  |
+-----+----------+--------------+---------+------------+----+
# gets virtual column from related_name
Parent.objects.get(pk=1).children.all()  # <QuerySet [id: 1, id: 2]>
Parent.objects.get(pk=1).children.get(pk=3).child_field  # nested lookups

class Child(models.Model):
    # unlike SQLAlchemy, both FK and backref go on child
    parent = models.ForeignKey(Parent, on_delete=models.CASCADE, related_name='children')

# FK = adds constraint via column on underlying table
# unlike Flask column name seems autogenerated
+-----+-----------+---------+---------+------------+----+
| cid | name      | type    | notnull | dflt_value | pk |
+-----+-----------+---------+---------+------------+----+
| 0   | id        | integer | 1       | <null>     | 1  |
| 1   | parent_id | integer | 1       | <null>     | 0  |
+-----+-----------+---------+---------+------------+----+
# constraint
Child.objects.create(parent_id=1)
# physical column reflected in ORM obj
Child.objects.get(pk=2).parent_id  # 1
# but also gets virtual column as well
Child.objects.get(pk=2).parent_id  # name is parent_name_one
```

* fields
```python
class Post(models.Model):

    # PRIMARY KEY
    # pk: instance attr, regardless of whether self-defined or auto-defined by Django https://docs.djangoproject.com/en/3.0/ref/models/instances/#the-pk-property
    # id: instance attr if auto-defined by Django

    # JSON / JSONField
    # 3.1 - works for all supported db backends https://docs.djangoproject.com/en/3.1/releases/3.1/#jsonfield-for-all-supported-database-backends but requires installing extesion for sqlite https://docs.djangoproject.com/en/3.1/ref/models/fields/#django.db.models.JSONField 🗄 `linux.md` SQLite extension and DYLD_LIBRARY_PATH; I had to use this 3rd party pkg https://pypi.org/project/jsonfield/
    # ^3.0 - Postgres only https://docs.djangoproject.com/en/3.0/ref/contrib/postgres/fields/#jsonfield
    # alternatives: TextField https://stackoverflow.com/q/48172299/6813490 ArrayField (Postgres-only) https://stackoverflow.com/a/44630696
    # edit from admin https://github.com/jmrivas86/django-json-widget

    # TYPES
    title = models.CharField(max_length=50)  # length limit
    content = models.TextField()  # no length limit

    # VALIDATION 
    # https://www.b-list.org/weblog/2006/jun/28/django-tips-difference-between-blank-and-null/ https://simpleisbetterthancomplex.com/tips/2016/07/25/django-tip-8-blank-or-null.html
    # both default to False
    # use case for blank and not null is value will be created after form validation
    author = models.TextField(null=True)  # nullable
    editor = models.TextField(blank=True)  # form validation

    # TIME
    created_at = models.DateTimeField(auto_now_add=True)  # current time on instance creation
    updated_at = models.DateTimeField(auto_now=True)  # current time on instance save
```

## DML

* check column present: `Foo.objects.filter(col__isnull=False)`
* https://johnnymetz.com/posts/slow-django-database-queries/
clean up
* select related, prefetch related https://www.youtube.com/watch?v=TzgZBg7oXNA
* use count instead of len() https://docs.djangoproject.com/en/3.2/ref/models/querysets/#django.db.models.query.QuerySet.count
* https://github.com/PaulGilmartin/django-queryhunter
* https://dev.to/amitness/django-orm-if-you-already-know-sql-k80
* https://davit.tech/django-queryset-examples/#section-comparsion
* prefetch https://www.laac.dev/blog/five-common-django-mistakes
* https://chriswedgwood.com/blog/htmx-with-django-example-2-bulk-update/

lookups
* https://docs.djangoproject.com/en/3.1/topics/db/queries/#lookups-that-span-relationships
* are Django lookups joins or subqueries? https://mattrobenolt.com/the-django-orm-and-subqueries/ https://stackoverflow.com/questions/8556297/how-to-subquery-in-queryset-in-django https://docs.djangoproject.com/en/3.1/ref/models/expressions/#subquery-expressions

```python
###
# LOOKUP = where clause https://docs.djangoproject.com/en/3.1/topics/db/queries/#field-lookups
###

# defaults to __exact
get(id__exact=14)  # explicit form
get(id=14)  # __exact implied
get(id__iexact=14)  # ILIKE https://docs.djangoproject.com/en/3.1/ref/models/querysets/#iexact

# FILTER https://ctrlzblog.com/django-queryset-filter-15-examples/
filter(name__contains='hello')  # LIKE '%foo%'
filter(id__in=group)  # membership
filter(date_joined__range=[start, end])  # range https://davit.tech/django-queryset-examples/#section-between

all()[:10]  # limit https://davit.tech/django-queryset-examples/#section-limit
order_by('name')  # order by

Entry.objects.filter(blog__name='beatles blog') # https://docs.djangoproject.com/en/3.1/topics/db/queries/#lookups-that-span-relationships
select * from entry where blog_id in 
    (select id from blog where name = 'beatles blog')

# ManyRelatedManager also used for joins? need to call all()
Foo.objects.get(name="bar").m2m.all()

###
# GET/UPDATE
### 

* `first()` isn't appropriate if you're querying for a unique obj, use `get()`

# get
filter(name='foo')  # queryset
get(name='foo')  # single instance but errs if None or n 
filter(name='foo').first()  # return 1 or None https://stackoverflow.com/a/3090342
get(name="foo_key").json_col["bar_key"]  # single instance but errs if None or n 

# update
get_or_create()
create(name="name", desc="desc")  # returns tuple of instance/bool
foo.save()  # update
```

misc
* _queryset_: collection of model instances
* _manager_: default name is `.objects` but can rename by using custom manager https://docs.djangoproject.com/en/3.1/topics/db/managers/#custom-managers
* _flush_: rm data (won't change schema) https://docs.djangoproject.com/en/3.1/ref/django-admin/#flush
* _meta_: https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing https://docs.djangoproject.com/en/3.1/ref/models/meta/
* view SQL from query: `all().query()` https://stackoverflow.com/a/1074224 `shell_plus --print-sql` https://davit.tech/django-queryset-examples/#section-bonus-tip
* rm obj: mask it instead https://github.com/makinacorpus/django-safedelete

## migrations

🗄 `sql.md` migrations
🔍 https://stackoverflow.com/questions/tagged/django-migrations

```sh
migrate <app> <num>  # rollback
migrate <app>        # reapply
```
clean up
* https://github.com/kennethlove/django-migrator
* https://www.youtube.com/watch?v=mnr_fJhbMzc
* https://django-migration-zero.readthedocs.io/en/latest/
* https://docs.djangoproject.com/en/3.0/howto/initial-data/
* https://github.com/Brobin/django-seed https://eli.thegreenplace.net/2014/02/15/programmatically-populating-a-django-database
* https://eli.thegreenplace.net/2014/02/20/clearing-the-database-with-django-commands
* https://www.mattlayman.com/blog/2020/django-testing-toolbox/ factory boy https://djangotricks.blogspot.com/2024/05/generating-fake-django-model-instances-with-factory-boy.html
* https://jefftriplett.com/2020/how-do-i-test-1000-objects-in-django https://github.com/model-bakers/model_bakery
* https://kite.com/blog/python/django-database-migrations-overview/ https://realpython.com/django-migrations-a-primer https://realpython.com/digging-deeper-into-migrations/
* https://www.mattlayman.com/understand-django/test-your-apps/

schema (DDL) migrations
* downtime https://pankrat.github.io/2015/django-migrations-without-downtimes/
* prevent autonaming https://adamj.eu/tech/2020/02/24/how-to-disallow-auto-named-django-migrations/ 

data (DML) migrations
* https://docs.djangoproject.com/en/dev/topics/migrations/#data-migrations

fixture
* https://realpython.com/django-pytest-fixtures/
* https://docs.djangoproject.com/en/3.1/topics/testing/tools/#django.test.TransactionTestCase.fixtures
* https://docs.djangoproject.com/en/3.0/howto/initial-data/#providing-data-with-fixtures

factory
* 

factory-light
```python
class YourTestClass(TestCase):
    @classmethod
    def setUpTestData(cls):
        print("setUpTestData: Run once to set up non-modified data for all class methods.")
        pass

    def setUp(self):
        print("setUp: Run once for every test method to setup clean data.")
```

misc
* create migration file manually `manage.py makemigrations --empty <app> --name <migration>`
* view migration file as SQL `manage.py sqlmigration <app> <migration>`
* squash migration files for feature branch: rm files and re-run `makemigrations` https://stackoverflow.com/a/40029119
* squash migration files for cleaning up codebase: `squashmigrations` https://docs.djangoproject.com/en/stable/topics/migrations/#squashing-migrations
* internals https://www.youtube.com/watch?v=u6cVvbuUzlk https://speakerdeck.com/andrewgodwin/migrations-under-the-hood

---

rollback
* _revert_: rm latest, wipe db, apply previous migrations, seed db; impl might be `DELETE FROM django_migrations where id=<id>`
* _rollback_: `migrate <app> <num>`; `migrate <app> zero` https://docs.djangoproject.com/en/dev/topics/migrations/#reversing-migrations 
* _non-autogenerated name_: `--name` https://docs.djangoproject.com/en/dev/ref/django-admin/#makemigrations
* not everything can be reversed https://stackoverflow.com/q/63123919
* can use something like RemoveField under the hood https://stackoverflow.com/q/63123919

misc
* _ordering issues_: make db changes on local, generate a new migration script `001-foo`, at some later point pull in `develop` and there's already `001-bar` migration and Django complains about `001-foo`, solve by rm `001-bar` and running `make makemigrations` then `make migrate`

# 💳 LIBS

🔍 https://learndjango.com/tutorials/essential-django-3rd-party-packages
* extensions https://monadical.com/posts/django-packages.html
https://learndjango.com/tutorials/essential-django-3rd-party-packages
https://talkpython.fm/episodes/show/379/17-libraries-you-should-be-using-in-django
* https://github.com/adamspd/django-appointment
* reports https://github.com/RamezIssac/django-slick-reporting
* _3rd-party apps_: anything installed by adding to `settings.py/INSTALLED_APPS` https://djangopackages.org https://realpython.com/installable-django-app/
* _editor_: https://406.ch/writing/django-prose-editor-prose-editing-component-for-the-django-admin/
* _email_: https://learndjango.com/tutorials/django-email-contact-form https://softwarecrafts.co.uk/100-words/day-76
* _favicon_: https://learndjango.com/tutorials/django-favicon-tutorial
* _internationalization_: https://testdriven.io/blog/multiple-languages-in-django/
* _maps_: https://www.paulox.net/2020/12/08/maps-with-django-part-1-geodjango-spatialite-and-leaflet/
* _Markdown_: https://learndjango.com/tutorials/django-markdown-tutorial
* _sessions_: https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Sessions https://www.youtube.com/watch?v=SMRaHSZiwWE https://eli.thegreenplace.net/2011/06/24/how-django-sessions-work-introduction/ for user anlytics https://www.reddit.com/r/django/comments/16p2gp0/comment/k1ovnqp/

## code quality

* _CORS_: https://github.com/adamchainz/django-cors-headers
* _type checking_ https://sobolevn.me/2019/08/typechecking-django-and-drf
* _Swagger_: https://github.com/axnsan12/drf-yasg
* _secrets_: https://github.com/LeeHanYeong/django-secrets-manager https://adamj.eu/tech/2024/08/30/django-rotate-secret-key/
* _internals_: https://djangodeconstructed.com/ how do class names (`PasswordChangeView`) resolve to import names (`from django.contrib.auth.views import password_change`)?

## debug

* perf: https://openfolder.sh/django-faster-speed-tutorial
https://www.bugsink.com/blog/better-error-tracking-in-django/
* _analytics_: https://github.com/jazzband/django-analytical
* _debug_ https://django-debug-toolbar.readthedocs.io/en/latest/installation.html https://talkpython.fm/episodes/show/464/seeing-code-flows-and-generating-tests-with-kolo
* _logging_: https://mattsegal.dev/django-gunicorn-nginx-logging.html https://djangodeconstructed.com/2018/12/18/django-and-python-logging-in-plain-english/ https://www.willmcgugan.com/blog/tech/post/richer-django-logging
* _tracing_: https://github.com/dabapps/django-log-request-id

## money

* _payments_: https://testdriven.io/blog/django-stripe-tutorial/ https://github.com/zinmyoswe/Django-Ecommerce https://github.com/dinoperovic/django-salesman
* _SEO_: https://github.com/kapt-labs/django-check-seo https://github.com/kapt-labs/django-check-seo https://learndjango.com/tutorials/django-sitemap-tutorial
* _taxes_: https://github.com/lowercase-app/django-taxtea

## need for prod

* _backups_: https://github.com/django-dbbackup/django-dbbackup
* _caching_: https://wsvincent.com/django-caching-for-beginners/ https://eralpbayraktar.com/blog/django/2020/caching-with-django
* _search_: https://findwork.dev/blog/optimizing-postgres-full-text-search-django/ https://www.youtube.com/watch?v=is3R8d420D4 https://youtu.be/is3R8d420D4 https://jamesturk.net/posts/websearch-in-django-31 https://www.youtube.com/watch?v=kOKwEDHeBX4 https://github.com/ivelum/djangoql https://pganalyze.com/blog/full-text-search-django-postgres Haystack https://django-q.readthedocs.io/en/latest/examples.html https://github.com/etianen/django-watson https://www.paulox.net/2017/12/22/full-text-search-in-django-with-postgresql https://fly.io/blog/a-no-js-solution-for-dynamic-search-in-django/ https://fly.io/blog/a-no-js-solution-for-dynamic-search-in-django/ sort https://rednafi.com/python/sort_by_a_custom_sequence_in_django/ https://www.photondesigner.com/articles/database-search-django-htmx

## real-time

https://centrifugal.dev/docs/tutorial/intro
* _channels_: https://www.aeracode.org/2018/06/04/django-async-roadmap/ https://testdriven.io/blog/django-async-views/ https://www.youtube.com/watch?v=j6IOuD5WD8c https://testdriven.io/courses/real-time-app-with-django-channels-and-angular/ https://testdriven.io/courses/real-time-app-with-django-channels-and-angular kinda live Phoenix LiveView? https://github.com/edelvalle/reactor https://runninginproduction.com/podcast/11-logflare-is-a-log-management-and-event-analytics-platform

## TUI

REPL https://github.com/selectnull/django-pyrepl/
TUI commands https://github.com/anze3db/django-tui
TUI admin https://github.com/valberg/django-admin-tui https://github.com/valberg/django-htmx-admin https://github.com/adamghill/django-unicorn

# 🟨 ZA

---

* deployment: https://github.com/PaulleDemon/AWS-deployment https://github.com/Never-Over/bridge https://james.walters.click/what-django-deployment-is-really-about.html https://github.com/gauge-sh/bridge

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

## design

🗄
* `design-patterns` dependency injection
* `python/core.md` functions > metaprogramming

> Web development is often broad, not deep - problems span many domains. https://docs.djangoproject.com/en/2.0/intro/whatsnext/
> The framework defines the grammar, you bring some of the words. https://blog.startifact.com/posts/framework-patterns.html

```txt
           +------------+
           |  browser   |
           +------------+
             |       ^
HTTP request |       | HTTP response
             |       |
             v       |
+----------------+   |
| url dispatcher |   |
+----------------+   | 
            |        |
            v        |
    +----------------+     +-----------+
    |      view      | <-> |  template |
    +----------------+     +-----------+
            ^
            |
            v
    +----------------+
    |     model      |
    +----------------+
            ^
            |
            v
    +----------------+
    |   database     |
    +----------------+
```

---

MVC 🔗 https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
* _model_: manages data and core business logic
* _view_: renders model data
* _controller_: accepts user input and performs application-specific logic

MVT
> it can take a little while to shift your thinking to the "Django way" which is more loosely coupled and allows for easier modifications than the MVC approach https://learndjango.com/courses/django-for-beginners/chapter-2-hello-world-website/
* https://lukeplant.me.uk/blog/posts/mvc-is-not-a-helpful-analogy-for-django/
* _model_: manages data and core business logic
* _template_: presents data as html + CSS/JS/static assets
* view in MVC
* _view_: desc data sent to user but not its presentation
* _URL config_: regex components configured to a view
* controller in MVC

RAILS
* still the best https://rubyonrails.org/doctrine/
* https://news.ycombinator.com/item?id=42856766
> It's productive, it's fast enough, it scales just fine, and perhaps most importantly there's a "right" way to do just about everything your web application will ever need to do: background jobs, websockets, read-only database replicas. https://news.ycombinator.com/item?id=42014906
* vs. Django https://news.ycombinator.com/item?id=42388340
* https://news.ycombinator.com/item?id=42569236
* https://literallythevoid.com/blog/rails_for_everything.html
* https://www.openmymind.net/2010/6/23/My-Rails-Journey-The-Expected-Speed-Bumps/
* https://www.openmymind.net/2010/10/18/Weekend-NET-Pains/
* https://www.openmymind.net/2010/8/30/How-I-would-fix-ASP-NET/

COMPONENTS
* HTTP, routes, ORM
> any framework that accepts POST request also needs to be able to protect against Cross-Site Request Forgery (CSRF)...implementing it properly involved first adding in database support so that I could build the session middleware...roughly 1/3rd of the total development time went into CORS and CSRF protection alone. https://itsthejoker.github.io/spiderweb-the-tiny-web-framework/
* router: receives req and returns res
* WSGI https://wsgi.tutorial.codepoint.net/application-interface
* middleware: processes req/res
* sessions

ALTERNATIVES
* https://github.com/vitalik/django-ninja https://news.ycombinator.com/item?id=30221016 https://talkpython.fm/episodes/show/490/django-ninja
* https://github.com/hbakri/django-ninja-crud
* single file https://github.com/radiac/nanodjango https://radiac.net/blog/2025/01/monkeypatching-django/
* https://www.loopwerk.io/articles/2024/django-vs-flask-vs-fastapi/
* https://www.david-dahan.com/blog/comparing-fastapi-and-django

htmx https://talkpython.fm/episodes/show/484/from-react-to-a-django-htmx-based-stack
https://github.com/CrocoFactory/sensei

https://treypiepmeier.com/words/2024/08/django-is-for-everyone
https://www.david-dahan.com/blog/10-reasons-i-stick-to-django

BYO
* https://www.destroyallsoftware.com/screencasts/catalog https://www.youtube.com/watch?v=7kwnjoAJ2HQ https://testdriven.io/courses/python-web-framework/ https://www.amazon.com/dp/1937785637 https://github.com/iklobato/LightAPI https://news.ycombinator.com/item?id=41914544 https://blog.dimitarandreev.com/posts/writing-an-http-router-for-aws-lambda-functions-from-scratch-with-go/

## governance

* contribute https://www.better-simple.com/django/2024/12/25/getting-started-contributing-django/
* consulting https://lincolnloop.com/ https://wsvincent.com/thoughts-on-pyconnz/  https://www.saaspegasus.com/
* creators: Simon https://news.ycombinator.com/user?id=simonw Adrian https://www.soundslice.com/ Jacob https://jacobian.org/ Andrew Godwin (did south and migrations)
* history https://jacobian.org/2024/mar/20/django-chat/ https://buttondown.com/carlton/archive/thoughts-on-djangos-core/
* users: https://octopus.energy/ https://talkpython.fm/episodes/transcript/487/building-rust-extensions-for-python
* versions: https://www.codestasis.com/ https://github.com/ambient-innovation/django-removals/
> Django 5.0 was released in December 2023...Django's versioning policy is time-based rather than feature-based. Roughly every eight months, a new feature release occurs, along with monthly bug fixes and security patches as needed...meaning you can expect Django 5.1 in August 2024, Django 5.2 in April 2025, Django 6.0 in December 2025, and so on. Django has such a large and active community of contributors that the decision was made years ago to focus on regular rollouts rather than wait for specific features to be completed...Specific releases (those that end in .2, like Django 5.2 and 6.2) are designated as long-term support (LTS) releases and receive security and data loss fixes applied for a guaranteed period, typically three years. This policy is designed for larger companies struggling to keep up with Django's rapid release schedule. https://learndjango.com/courses/django-for-beginners/introduction/
* _DSF_: admin https://wsvincent.com/how-django-works-behind-the-scenes/ 501 non-profit https://www.b-list.org/weblog/2018/nov/20/core/
* _DEP_: PEP for Django https://github.com/django/deps
* _fellows_: paid devs https://www.b-list.org/weblog/2018/nov/20/core/
* _technical board_: engineering; replaced core teams https://jacobian.org/2020/mar/12/django-governance/

## templates

---

* _convention > conf_: Django will serve your templates provided they are in `templates/registration` and have the expected name, otherwise will serve its own default https://github.com/zachvalenta/hello-django1/commit/6503b460490fb85f085f3a277fbdd80360291fa0
* forms https://kodare.net/2024/09/11/why-we-wrote-a-new-form-library-for-django.html
* components https://github.com/wrabit/django-cotton
* https://django-formset.fly.dev/
* https://girlthatlovestocode.com/django-template-tags
* charting https://www.youtube.com/watch?v=B4Vmm3yZPgc
* linting https://github.com/thibaudcolas/curlylint
* _DTL_: default template engine; stick with this over jinja2 https://blog.doismellburning.co.uk/django-an-unofficial-opinionated-faq/
* _syntax_: `{{ }}` insert from context `{% %}` block, inheritance 🙃 percentage signs have to be right against braces
* `context`: dict of template variable to Django obj https://docs.djangoproject.com/en/2.0/intro/tutorial03/#write-views-that-actually-do-something vs. DRF's notion of context, which is the way to get access to entire request (like URL) i.e. more info than the obj you're trying to serialize
* `user`: always in context [Osborn 1.10.68]
* `templates`: inside app (official tutorial, Osborn) inside project (Cookiecutter, Vincent https://wsvincent.com/django-about-page-three-ways/ https://wsvincent.com/django-tips-template-structure/)
* `static`: alongside `templates`; reference from html via `{% load staticfiles %}` and `<link rel="stylesheet" href="{% static 'styles.css' %}" />` [Osborn 1.4.15]
* can provide default values for templates [Osborn 1.5.21]
* `{% load staticfiles %}`: children can inherit for CSS, not for images [Osborn 1.5.22]
* can use Markdown for templates as well https://github.com/rgs258/django-markdown-view

* snippets
```python
# set project-wide templates dir https://learndjango.com/tutorials/template-structure
TEMPLATES = [{ 'DIRS': [os.path.join(BASE_DIR, 'templates')] }]

# render with context
return render(request, 'thing_detail.html', context={'thing':thing})
```

## signals

https://docs.djangoproject.com/en/5.0/topics/signals/

* https://blinker.readthedocs.io/en/stable/
* _signals_: emit/consume msgs (btw separate Django apps) e.g. pre/post-save https://stackoverflow.com/a/17658156
* are not async i.e. consumer(s) must finish before further execution https://www.mattlayman.com/blog/2023/django-signals-async/
* hooks as replacement https://monadical.com/posts/django-packages.html

## testing

📜 https://docs.djangoproject.com/en/dev/topics/testing/
🔗 https://www.obeythetestinggoat.com/pages/book.html#toc
🔍 https://www.valentinog.com/blog/testing-django/

impl
```python
###
# GET
###
from django.test import TestCase
class HealthcheckTest(TestCase):
    def test_healthcheck(self):
        res = self.client.get('/healthcheck/')
        self.assertEqual(res.status_code, 200)

###
# POST
###
from rest_framework.test import APIClient  # only worked w/ DRF client and setting fmt as json
res = self.client.post("/api/", data, format="json")
```

misc
* _client_: acts as dummy browser https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing#content DRF https://www.django-rest-framework.org/api-guide/testing/#apiclient vanilla https://docs.djangoproject.com/en/3.1/topics/testing/tools/#the-test-client
* _request factory_: add stuff onto req (middleware, user) vs. mimicking browser like client https://docs.djangoproject.com/en/stable/topics/testing/advanced/#the-request-factory
* `TestCase`: creates tmp db for each transaction using same dbms from `setting.py/databases/default` https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing#what_does_django_provide_for_testing
* `SimpleTestCase`: for when you don't need db e.g. templates https://learndjango.com/tutorials/django-testing-tutorial inherits from unittest's `unittest.TestCase` https://docs.djangoproject.com/en/2.0/topics/testing/tools/#simpletestcase
* `tearDown()`: TestCase does teardown itself so this isn't typically used https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing#content
* internals https://adamj.eu/tech/2020/09/05/what-happens-when-you-run-manage.py-test
* DRF: https://www.youtube.com/playlist?list=PLP1DxoSC17LZTTzgfq0Dimkm6eWJQC9ki
* testing admin https://til.simonwillison.net/django/testing-django-admin-with-pytest

execution
* everything prepended w/ `test_` is run
* coverage integration https://docs.djangoproject.com/en/3.1/topics/testing/advanced/#integration-with-coverage-py https://adamj.eu/tech/2019/04/30/getting-a-django-application-to-100-percent-coverage/
```sh
# https://stackoverflow.com/a/18834222
python3 manage.py test app  # app
python3 manage.py test app.tests.mod  # module
python3 manage.py test app.tests.mod.cls  # class
python3 manage.py test app.tests.tests.mod.cls:my_method  # method
```
