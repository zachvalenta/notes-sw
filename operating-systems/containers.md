# ⛩️

## 参考

📜 https://docs.docker.com/reference/
🔍 https://github.com/veggiemonk/awesome-docker
📚
* Clinton linux in action
* Evans https://wizardzines.com/zines/containers/ 
* Galvin dinosaur ch 16
* Takemura book of xen
* Tanenbaum circus ch 7

## 进步

CLEANUP
https://github.com/sablierapp/sablier
next-gen images https://yonkeltron.com/posts/why-cloud-native-buildpacks-should-excite-companies/
https://github.com/moncho/dry
https://github.com/bcicen/ctop
* https://roadmap.sh/docker
https://github.com/pommee/Pocker
https://www.youtube.com/watch?v=3e8J_pv-xJI
https://www.youtube.com/watch?v=Ud7Npgi6x8E
https://news.ycombinator.com/item?id=38913425
https://github.com/robertpsoane/ducker
https://github.com/mrjackwills/oxker
* making things actually reproducible https://pythonspeed.com/articles/reproducible-docker-builds-python/
* https://github.com/deluan/zsh-in-docker https://pythonbytes.fm/episodes/show/402/how-to-monetize-your-blog

IMPROVE WORKLOW
* hot reload https://www.youtube.com/watch?v=YFl2mCHdv24 8:30
> DRF/crud app already seems to be hot reloading
* fresh volume when running locally
* _ignore_: .git, local.db https://gist.github.com/wassname/b25471b0f3bb2f9ff81f build context https://codefresh.io/docker-tutorial/not-ignore-dockerignore-2/ https://alecthegeek.github.io/docker/2019/06/06/Docker-Build-With-No-Build-Context.html
* _deps_: export prod-only deps, add `http` as dev dep
* _tooling_: lint image, GUI https://github.com/amir20/dozzle https://github.com/jesseduffield/lazydocker https://github.com/will-moss/isaiah CLI https://github.com/j-bennet/wharfee https://github.com/veggiemonk/awesome-docker#terminal

* _22_: rf Kubernetes notes
* _20_: docker-compose (handle container startup order) skeletons (SQLite, gunicorn, Postgres), secrets mgmt, workflow (build cache to speed rebuilds, use ARGs, Makefile rules for rebuild and shell) compose (variables for db creds, envs using multiple compose files)
* _19_: another course, Flask skeleton
* _17_: Pluralsight course, explain what a container is in a work meeting :)

# 🚢 DOCKER

OS STORAGE
* `docker.raw`: allocated 32GB but only 3-4GB of images https://apple.stackexchange.com/q/391377
> reset mine from 64 to 32GB
* cleanup https://stackoverflow.com/a/39890025

ZA
* running as root https://blog.bejarano.io/how-to-write-great-container-images/ https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/ https://pythonspeed.com/articles/root-capabilities-docker-security/ https://pythonspeed.com/articles/vscode-broken-docker/ https://github.com/genuinetools/img 🗄 Docker alternatives
* publishing https://github.com/tiangolo/uwsgi-nginx-docker https://github.com/jessfraz/dockerfiles/blob/master/httpie/Dockerfile
* create super user in container https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
* Docker as a company: still the default registry and runtime for development, but no longer the main runtime for prod https://news.ycombinator.com/item?id=26479921
* load balancing: single container w/ single app service https://stackoverflow.com/a/40872526/6813490 single container w/ n app services (with something to restart if they crash?) https://devops.stackexchange.com/questions/2089/what-are-the-advantages-of-dockerizing-nginx-and-php-in-different-containers#comment3231_2090
* logging: https://pythonspeed.com/articles/gunicorn-in-docker/ https://docs.docker.com/engine/reference/commandline/container_restart/
* ssh: https://stackoverflow.com/q/18136389/6813490
* socket https://blog.quarkslab.com/why-is-exposing-the-docker-socket-a-really-bad-idea.html

## commands

workflow
* _start_: compose (`make up`) single container (`make build`, `make start`)
* _iterate_: `make rebuild`
> rm rebuild/restart and just blow away previous container as prereq to start?
* _clean up_: `mtp`
> scope your clean up comand in project only to resources associated with project name

images
* _get_: `pull`
* `build -t <repository:tag> .`: build your own image from Dockerfile `build -t my_img .`; `-t` tag (will just use repositiry if omit tag); `.` use `Dockerfile` in $CWD https://www.freecodecamp.org/news/an-introduction-to-docker-tags-9b5395636c2a/ https://pythonspeed.com/products/justenoughdockerpackaging/
* _list_: `images`
* _rm by id_: `rmi <image_id>`
* _rm all - dangling_: `image prune` https://stackoverflow.com/a/17237701
* _rm all - dangling/unused_: `image prune -a` https://stackoverflow.com/a/17237701
* _dangling_: layer with no relationship to tagged image https://stackoverflow.com/a/60756668 image with no tag https://stackoverflow.com/a/58520908 image with no name / name as `<none>` https://stackoverflow.com/a/45143234 https://stackoverflow.com/a/61931789
* _unused_: image not referenced by container https://stackoverflow.com/a/45143234

containers
* _list running_: `ps`
* _list all_: `ps -a`
* _stop by id_: `stop <id>`; with `-v` to rm attached volume
* _stop all_: `stop $(docker ps -a -q)` https://gist.github.com/evanscottgray/8571828#gistcomment-1830482 docker ps -qa | xargs docker stop https://gist.github.com/evanscottgray/8571828#gistcomment-3297059
* _rm single_: `rm <id>/<name>`
* _rm all_: rm containers before images https://stackoverflow.com/a/32723127
```sh
# rm all containers https://gist.github.com/evanscottgray/8571828#gistcomment-1830482
rm $(docker ps -a -q) 
# rm all containers https://stackoverflow.com/a/17237701 
container prune -f
# rm all containers + attached volumes
system prune --volumes -f
```
* run syntax
```sh
docker run poc  # run img named `poc`
docker run --name poc poc  # name container `poc` as well
docker run --name poc -d poc  # run it in the background so you can still use the shell
docker run --name poc -d -p 5000:5000 poc  # map port 5000 on local machine to port 5000 in the container -> vs. EXPOSE https://stackoverflow.com/q/22111060 [Wahlin 6.3 @ 3:15]
```

volumes
* _list all_: `volume ls` https://stackoverflow.com/a/31997267
* _prune unused_: `volume prune` https://stackoverflow.com/a/40654726 all https://gist.github.com/evanscottgray/8571828#gistcomment-2866236 https://docs.docker.com/config/pruning/#prune-everything

## components

> my Docker version didn't have this GUI, diff btw Comunity Edition and Docker Desktop? https://docs.docker.com/desktop/mac/install/#uninstall-docker-desktop

✅ Community Edition
* native version for Win/macOS
* comes w/ client, server/Engine and `docker-compose` (and sometimes `docker-machine`)
* installation: get download from release notes (vs creating DockerHub account) https://docs.docker.com/docker-for-mac/release-notes/ for M1 https://docs.docker.com/desktop/mac/apple-silicon/ https://docs.docker.com/desktop/mac/apple-silicon/ https://docs.docker.com/desktop/mac/install/
* uninstall: App Cleaner + 
> doesn't seem like you need to be signed in to use
* start: can use CLI but most people use GUI https://stackoverflow.com/a/35979292
```txt
Version 2.0.0.3 (31259)
8858db33c8
Engine: 18.09.2
Compose: 1.23.2
Machine: 0.16.1
Notary: 0.6.1
Credential Helper: 0.6.0
Kubernetes: v1.10.11
```

config
* CLI: `~/.docker/config.json` https://docs.docker.com/engine/reference/commandline/cli/#configuration-files https://docs.docker.com/engine/reference/commandline/config/
* daemon: `/etc/docker/daemon.json` https://docs.docker.com/config/daemon/#configure-the-docker-daemon
> why does `~/.docker` also have `daemon.json`?

* snippets
```sh
#
# VERSIONS
#

# Docker version 18.09.2, build 6247962
$ docker --version

# docker-compose version 1.23.2, build 1110ad01
$ docker-compose --version

# docker-machine version 0.16.1, build cce350d7
$ docker-machine --version

#
# GOTCHAS
#

# toomanyrequests -> fixed by rm `config.json` and restarting daemon https://github.com/docker/hub-feedback/issues/1250

# failed to dial gRPC -> fixed bytoggled on 'experimental features' (preferences > daemon) https://github.com/docker-library/docker/issues/71#issuecomment-457757840
/U/z/D/docker-flask-skeleton $ make image
docker build -t docker-flask-skeleton .
ERRO[0000] failed to dial gRPC: unable to upgrade to h2c, received 502
context canceled
```

❌ Machine
* wrapper for Mac/Win before native Docker
* requires VirtualBox https://stackoverflow.com/a/38624540
* not required for Docker CE [Wahlin 3.1 @ 4:45-5:45] but seems to come w/ Docker CE https://realpython.com/docker-in-action-fitter-happier-more-productive/#docker-setup
* afaik no one else mentions this except the Real Python tutorials https://realpython.com/dockerizing-flask-with-compose-and-machine-from-localhost-to-the-cloud/
* my work machine has Docker 19.03 and doesn't have docker-machine bundled

❌ Toolbox
* for Windows 7/8 and macOS 10.8
* requires VirtualBox

## compose

🔍 https://github.com/docker/awesome-compose
📜
* https://docs.docker.com/compose/
* https://docs.docker.com/compose/compose-file/
* https://news.ycombinator.com/item?id=34940920

basics
* `docker-compose.yml`: run n processes w/ single command, all logs to single terminal
* when Dockerfile's `RUN` not enough https://stackoverflow.com/a/45549372
* alternatives: Foreman, Honcho https://www.mattlayman.com/blog/2019/web-development-environments/ Colima https://www.thoughtworks.com/radar/platforms?blipid=202203015 Orbstack https://news.ycombinator.com/item?id=41421846 Podman https://news.ycombinator.com/item?id=38981844 https://container-desktop.com/
* _service_: container https://www.youtube.com/watch?v=aetqo2nkQcA 1:30

multi-env https://docs.docker.com/compose/extends/
* per-environment files can inherit, add to and replace config options from the base file https://github.com/jenish4096/express-restful-apis https://stackoverflow.com/a/63585954
* _read by default_: `docker-compose.yml` and `docker-compose.override.yml`
* _specifiy compose file for `exec`_: `exec -f <file> exec <service> <cmd>` https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/#production-dockerfile
* could use single entry point file reading start cmd from env but this doesn't seem common https://stackoverflow.com/q/52942913
* `extends`: deprecated https://stackoverflow.com/a/63585954
```yaml
# BASE - docker-compose.base.yml
version: "3"
services:
  api:
    build: .

# DEV - docker-compose.dev.yml
version: "3"
services:
  api:
    command: npm run dev

# PROD - docker-compose.dev.yml
version: "3"
services:
  api:
    command: npm run prod
```

env var
* list: `exec <service> env` https://testdriven.io/blog/dynamic-secret-generation-with-vault-and-flask/
* looks for `.env` https://docs.docker.com/compose/compose-file/#variable-substitution 
* can also specify env file (file location is relative to project dir on host machine, not in container) https://docs.docker.com/compose/compose-file/#env_file

cmds
* build and start: `up --build` https://wsvincent.com/beginners-guide-to-docker/ `-d` run as daemon
* view running services: `ps`
* run cmd in service: `docker-compose exec <service> <cmd>` https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
> preceded by nsenter https://github.com/jpetazzo/nsenter https://jvns.ca/blog/2018/03/05/things-ive-learned-networking/
* rm service/volume created on up: `down -v` https://docs.docker.com/compose/reference/down/ https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/
* non-interactive: `exec -it`  or `exec -T` (TTY error) https://stackoverflow.com/a/57565119

* `docker-compose.yml`
```yml
# see `db.md/POSTGRES` for db specifics
version: '3.7'  # correspond to versions of Docker Engine https://docs.docker.com/compose/compose-file/
services:
  web:
    build: .  # file location of src and Dockerfile https://docs.docker.com/compose/compose-file/compose-file-v3/#build
    command: flask run --host 0.0.0.0  # same as (and will override) Dockerfile CMD command https://docs.docker.com/compose/compose-file/#command https://www.reddit.com/r/docker/comments/8xuay1/dockercompose_command_not_waiting_for_dockerfile/
    volumes:  # c.f. 'storage'
      - .:/docker-flask-postgres
    ports:
      - 5000:5000  # port forwarding -> target (addressable inside container) to published (addressable from host) https://docs.docker.com/compose/compose-file/#ports
    depends_on:  # run this other service first
      - db
        # only waits for container start (no definition of 'ready'), will get 'connection refused' error https://www.youtube.com/watch?v=aetqo2nkQcA 9:30
        # https://www.youtube.com/watch?v=jqqIQoSpxxA
        # workarounds: wait_for_it https://www.youtube.com/watch?v=aetqo2nkQcA 10:00 wait-until https://www.youtube.com/watch?v=jqqIQoSpxxA retry logic https://www.youtube.com/watch?v=A9bA5HpOk30 4:30 https://stackoverflow.com/a/35841740 restart https://docs.docker.com/compose/compose-file/#deploy Bash script https://stackoverflow.com/a/50108745
        # docs https://docs.docker.com/compose/startup-order/
```

---

* alternative https://github.com/F1bonacc1/process-compose
* _lifecycle hook_: hook on container status https://github.com/afroisalreadyinu/miniboss
* running multiple instances of single service, restart policy https://www.youtube.com/watch?v=aetqo2nkQcA 1:40 https://github.com/willfarrell/docker-autoheal
* read this https://nickjanetakis.com/blog/best-practices-around-production-ready-web-apps-with-docker-compose
* different db setups https://github.com/alexmacarthur/local-docker-db

## debug

---

https://www.youtube.com/watch?v=YRt1aB0iAlM
* _sink_: `docker info`, attach to container process https://stackoverflow.com/q/19688314

* run shell in container: `docker exec -it <name> bash` https://stackoverflow.com/a/30173220
* run new container off snapshot image from existing container https://stackoverflow.com/a/20816397 seems like `run` just `start` + run cmd and typically used for debugging
* cp container to host: `container cp <container>:/<project>/path/to/file` beware that shell autocomplete will be local fs, not container
* send req from inside container https://stackoverflow.com/a/41752668
* security scan https://github.com/quay/clair
```sh
make shell
apt-get -y update
apt-get install wget
wget http://0.0.0.0:8000/healthcheck
```

* inspect
```sh
inspect <container_name>  # all
inspect --format='{{ .Id }}' <container_name>  # top-level
docker inspect --format='{{ .NetworkSettings.Networks.crud_default.Gateway }}' <container_name>  # drill down
```

logs
* recap: `docker logs <container/id>` https://stackoverflow.com/a/41752668
* tail: `logs --follow` https://github.com/zachvalenta/docker-flask/blob/master/Makefile#L57
* show full output from dev server https://stackoverflow.com/a/36585076
```yaml
services:
  web:
    tty: true
```

## images

🔍 https://github.com/docker-library/official-images

* _image_: blueprint for container
* built from read-only file system layers
* _repository_: n images w/ same name but diff version tags https://stackoverflow.com/q/34004076
* _registry_: stores images
* commercial: AWS ECR, Docker Trusted Registry https://github.com/veggiemonk/awesome-docker#registry

---

* dont use Alpine? https://martinheinz.dev/blog/92
* view fs changes https://github.com/wagoodman/dive https://fzakaria.com/2020/05/31/containers-from-first-principles.html
* copy images from one registry to another https://www.thoughtworks.com/radar/tools?blipid=202203084 https://github.com/containers/skopeo
* security scan https://github.com/anchore/grype https://www.thoughtworks.com/radar/tools?blipid=202203019
* _get image size_: `docker image ls --format "{{ .Size }}" <image_name>` https://pythonspeed.com/articles/system-packages-docker/
* _create new image_: pull base image, start container and run some commands, then save as new image `docker container commit -m "my new image" <container-id> my-new-image:<version>`

multi-stage
* _raison d'etre_: smaller images, esp. w/out separate Dockerfiles per env https://docs.docker.com/develop/develop-images/multistage-build/#before-multi-stage-builds
* _use cases_: create more granular image containing only what's needed. e.g. Redis image (use full os to compile, then copy Redis src and its runtime deps to new image and discard the os used to compile) https://blog.bejarano.io/how-to-write-great-container-images/ or for app dependencies https://www.youtube.com/watch?v=A9bA5HpOk30 7:30 https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/#production-dockerfile
* _how_: single Dockerfile with multiple `FROM` https://pmac.io/2019/02/multi-stage-dockerfile-and-python-virtualenv
```dockerfile
###########
# BUILDER #
###########

FROM python:3.8.3-alpine as builder
RUN pip wheel --no-cache-dir --no-deps --wheel-dir /usr/src/app/wheels -r requirements.txt

#########
# FINAL #
#########
COPY --from=builder /usr/src/app/wheels /wheels
COPY --from=builder /usr/src/app/requirements.txt .
RUN pip install --no-cache /wheels/*
```

layers
* _layer_: tarball i.e. files https://jvns.ca/blog/2019/11/18/how-containers-work--overlayfs/
* _build cache_: creates intermediates images along the way (w/ own ids https://cameronlonsdale.com/2018/11/26/whats-in-a-docker-image/) Dockerfile executed top to bottom so put stuff that will change most frequently (e.g. source) at the bottom so that it doesn't invalidate the build cache (any invalidated layer will invalidate all subsequent layers) https://pythonspeed.com/articles/docker-caching-model/ aka 'layer cache' https://testdriven.io/blog/faster-ci-builds-with-docker-cache/
* _rebuilding_: can use existing layers or force a fresh build https://stackoverflow.com/a/35595021

* reproducibility 
```dockerfile
# 📍 https://pythonspeed.com/articles/base-image-python-docker-images/ https://pythonspeed.com/articles/reproducible-docker-builds-python/ https://pythonspeed.com/articles/dockerizing-python-is-hard https://twitter.com/b0rk/status/1237528379097616388 https://pythonspeed.com/articles/when-update-dependencies/ https://www.docker.com/blog/intro-guide-to-dockerfile-best-practices/ https://pythonspeed.com/articles/official-docker-best-practices/ https://docs.docker.com/develop/develop-images/dockerfile_best-practices/ 

# 
# 🐍 PYTHON
# 

# official Python image based on latest Debian LTS
FROM python:3
# use explicit version
FROM python:3.8
# can point to specific image hash (Dockerhub makes no promises about how long they'll keep up, so might need to copy to internal repo)
FROM python@sha256:89d719142de465e7c80195dff820a0bbbbba49b148fbd97abf4b58889372b5e3

# 
# 🐧 OS
# 

# can be more explicit about Debian version
FROM python:3.8-buster
# slim version: smaller but won't have some common packages
FROM python:3.8-slim-buster

# 
# 📦 OS PKGS
# 

# upgrade to get latest security patches bc there's sometimes a lag before official Python image gets updated https://pythonspeed.com/articles/vscode-broken-docker/
RUN apt-get update && apt-get -y upgrade
# fetch specific version for deps https://pythonspeed.com/articles/reproducible-docker-builds-python/
RUN apt-get install -y nginx=1.14.2-2+deb10u1
# use an install script https://pythonspeed.com/articles/system-packages-docker/
COPY install-packages.sh .
RUN ./install-packages.sh
# don't install subdeps (or does recommended here mean something else?) https://pythonspeed.com/articles/system-packages-docker/
RUN apt-get -y install --no-install-recommends <pkg>
```

* Dockerfile: instructuions to build image https://stackoverflow.com/a/45549372 lint https://github.com/hadolint/hadolint https://github.com/goodwithtech/dockle
```dockerfile
#######
# 🏁 BASE & MISCELLANEA
#######

# grab base image
FROM python:3-alpine

# contact info (can also add other attributes with LABEL) https://kapeli.com/cheat_sheets/Dockerfile.docset/Contents/Resources/Documents/index
LABEL maintainer Zach Valenta

# run cmds; minimize the number of these https://blog.bejarano.io/how-to-write-great-container-images/
RUN python -m pip install -r requirements.txt

#######
# 🔢 VARIABLES
#######

# arg: set var to dedupe Dockerfile; build-time i.e. available during build process only) https://stackoverflow.com/a/39598751 https://vsupalov.com/docker-arg-env-variable-guide/
# env: normal Linux env var; can also set on app start as well https://vsupalov.com/docker-arg-env-variable-guide/
ARG project_name=my_project
ENV PYTHONDONTWRITEBYTECODE 1

#######
# 🗃 DIRECTORIES
#######

# workdir: set CWD https://wsvincent.com/beginners-guide-to-docker/
WORKDIR /$my_project

# 📍 ADD https://www.idiotinside.com/2020/02/08/docker-file-difference-copy-vs-add/
# ignore files for COPY/ADD with dockerignore https://docs.docker.com/engine/reference/builder/#dockerignore-file
# syntax (src target) 
COPY requirements.txt /$project_name/
# conditional: need to have a file that you know will exist come first https://stackoverflow.com/a/46801962/6813490
COPY requirements.txt secrets.sh /$project_name/
# irl put source as penultimate line
COPY . /$my_project

#######
# 🏎 START
#######

# cmd on container start https://runnable.com/docker/python/dockerize-your-python-application 
# can also feed args to ENTRYPOINT https://stackoverflow.com/a/34245657 [Wahlin 6.3 @ 3:30, 6:00]
# syntax https://stackoverflow.com/a/27615958
CMD flask run --host 0.0.0.0
```

## secrets

https://www.youtube.com/watch?v=MlzbHXMQZY4
* _docker-compose_: https://pythonspeed.com/articles/build-secrets-docker-compose https://keepgrowing.in/tools/set-up-a-postgresql-database-with-docker/ https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/ https://blog.rogs.me/2020/05/how-i-manage-multiple-development-environments-in-my-django-workflow-using-docker-compose/ https://vsupalov.com/docker-arg-env-variable-guide/

runtime
* passed to container on startup https://stackoverflow.com/a/59143768
```sh
# single
make start user="my_user"  # shell
docker run -e "USER_NAME=$(user)"  # Makefile

# multiple
make start user="my_user" pass="my_pass"  # shell
docker run -e "USER_NAME=$(user)" -e "PW=$(pass)" # Makefile

# from file https://docs.docker.com/engine/reference/commandline/run/#set-environment-variables--e---env---env-file
# need to use .dockerignore as well
```

buildtime
* present in image layer
* _good idea_: over the network, either from vault or your own workaround https://pythonspeed.com/articles/docker-build-secrets/
* _not yet_: BuildKit and `--secret` https://docs.docker.com/develop/develop-images/build_enhancements/#new-docker-build-secret-information https://ponderosa.io/blog/docker/2019/04/13/secrets-in-docker-builds/ leaves trace of image file https://github.com/moby/moby/issues/38667
* _bad ideas_: `ARG`/`ENV` https://docs.docker.com/engine/reference/builder/#arg https://vsupalov.com/docker-arg-env-variable-guide/ env file https://stackoverflow.com/a/46919859 `–build-arg` https://pythonspeed.com/articles/docker-build-secrets/

## skeletons

* _base_: https://github.com/zachvalenta/docker-flask
* _Postgres_: https://github.com/zachvalenta/docker-flask-postgres
* _SQLite_: https://github.com/zachvalenta/docker-flask-sqlite
* _SQLite + gunicorn_: https://github.com/zachvalenta/docker-flask-sqlite-gunicorn
* _config_: https://github.com/zachvalenta/docker-flask-envs-secrets
* _config + SQLite_: https://github.com/zachvalenta/docker-flask-sqlite-config
* _config + SQLite + gunicorn_: https://github.com/zachvalenta/docker-flask-sqlite-gunicorn-config

---

* https://pythonspeed.com/products/pythoncontainer/#changelog https://pythonspeed.com/products/productionquickstart/#changelog
* Celery, Redis https://saasitive.com/tutorial/django-celery-redis-postgres-docker-compose
* Nginx https://github.com/zachvalenta/nginx-wsgi https://www.youtube.com/watch?v=Qw9zlE3t8Ko https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx
* uWSGI
* Nginx w/cache
* Caddy
* config templating
* Mongo
* Redis
* TLS https://testdriven.io/blog/django-lets-encrypt/
* AWS https://testdriven.io/blog/django-docker-https-aws/
* publish skeletons! have a personal site with analytics, replace http with curl (if you haven't sorted the dev deps yet), create Github org, send this one out to Michael Kennedy

## storage

📜 https://docs.docker.com/storage/

volumes
* share files from host to container https://stackoverflow.com/a/40568482
* inspect https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/
```yaml
services:
  web:
    build: .
    volumes:
      - .:/docker-django
  proxy:
    depends_on:
      - web
    volumes:
    - .:/docker-django/nginx.conf
```

types https://stackoverflow.com/a/55366707 https://www.youtube.com/watch?v=YFl2mCHdv24 8:27
* _volume_: stored on host but managed by Docker
* _bind mount_: not a good idea, allows container processes to touch host files
* _tmpfs_: Linux version only; stored in-mem, not written to fs
* _named pipe_: Windows version only

---

* _mount container to host fs_: `run -v` https://www.youtube.com/watch?v=YFl2mCHdv24 8:50 https://stackoverflow.com/a/23455537 docker-compose https://www.codemochi.com/blog/2019-08-27-nextjs-hmr https://www.zachjohnsondev.com/posts/go-docker-hot-reload-example/ http://engineering.conversantmedia.com/technology/2019/10/01/typescript-hot-reload/ https://stackoverflow.com/q/44342741/6813490 `--mount` https://docs.docker.com/storage/bind-mounts/
* persist Postgres data Awad https://www.youtube.com/watch?v=AQj_Z1FzAfY
* w/ docker-compose https://devopsheaven.com/docker/docker-compose/volumes/2018/01/16/volumes-in-docker-compose.html
* fs in container is itself just an alias to fs on Docker host [Wahlin 5.3 @ 2:30] 
* persisted even if container deleted unless you explicity wipe it out
* apparently for local dev you mount your src directory onto container file system but for prod you copy your src into container itself

# 🟨 ZA

## containerization

> Linux containers were not built to be secure isolated sandboxes (like Solaris Zones or FreeBSD Jails). Instead they’re built upon a shared kernel model that utilizes kernel features to provide basic process isolation http://tech.paulcz.net/blog/future-of-kubernetes-is-virtual-machines/ https://blog.jessfraz.com/post/containers-zones-jails-vms/

* shared file system https://virtio-fs.gitlab.io/

CONTAINERIZATION
* _layer_: set of changes made to file system
* _container_: thing that runs; writable layer above image [Wahlin 5.2 @ 2:15] lightweight VM administered to by shared kernel (vs. full os) and using slice of hardware (CPU, mem, persistence) [Clinton fig 2.4] https://jvns.ca/blog/2020/04/27/new-zine-how-containers-work/
> A container is a combination of cgroups and namespaces. To a first approximation, namespaces control which processes the container can see and cgroups control how much of the system's resources the processes can consume.
* how to prevent containers from stealing all CPU from host machine https://www.riverphillips.dev/blog/go-cfs/
* _service_: processing running w/in container
* _cluster_: n containers
* setting it up is hard https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/ https://github.com/kelseyhightower/kubernetes-the-hard-way
* _orchestration_: manages clusters
* under the hood: cgroups, namespace, seccomp, bpf https://twitter.com/b0rk/status/1227244309621215233
* doesn't actually solve the 'works on my machine' problem as deployed container involves Kubernetes, networking, monitoring, config management https://www.youtube.com/watch?v=RB6MvSEaMK
* can Dockerize surrounding services while keep web app non-Dockerized for REPL speed https://runninginproduction.com/podcast/4-real-python-is-one-of-the-largest-python-learning-platforms-around#24:14

ALTERNATIVES TO CONTAINERS
* microVMs https://github.com/firecracker-microvm/firecracker
* isolates https://blog.cloudflare.com/cloud-computing-without-containers/
* Solaris Zones
* FreeBSD Jails
* _unikernel_: composition of minimum number of OS libraries necessary to run app https://softwareengineeringdaily.com/2016/09/14/unikernels-with-idit-levine/
* _sink_: https://medium.com/faun/the-missing-introduction-to-containerization-de1fbb73efc5 http://www.smashcompany.com/technology/why-would-anyone-choose-docker-over-fat-binaries 
* Firecracker https://news.ycombinator.com/item?id=25883253 https://www.micahlerner.com/2021/06/17/firecracker-lightweight-virtualization-for-serverless-applications.html
* LXC https://news.ycombinator.com/item?id=30385580
* VirtualBox, qemu, hyper-V, Xen https://drewdevault.com/2022/09/02/2022-09-02-In-praise-of-qemu.html https://chatgpt.com/c/670fec7a-7cd4-8004-bc50-8b790c438edd https://www.qemu.org/ https://drewdevault.com/2018/09/10/Getting-started-with-qemu.html

ALTERNATIVES TO DOCKER AS CONTAINER RUNTIME
* _container engine_: runtime
* mostly Docker for now, but things like the Open Container Initiative (OCI) and the Runtime Spec could lead to a new runtime https://blog.technodrone.cloud/2019/02/goodbye-docker-and-thanks-for-all-fish.html https://github.com/containers/skopeo
* _containerd_: container engine
* used in Kubernetes https://www.thoughtworks.com/radar/platforms?blipid=202203015
* used in Colima https://www.thoughtworks.com/radar/platforms?blipid=202203015
* used to be Docker but now OSS https://news.ycombinator.com/item?id=26479921 https://github.com/containerd/containerd https://github.com/google/gvisor
* BYO https://github.com/kelseyhightower/kubernetes-the-hard-way
* _Colima_: https://github.com/abiosoft/colima
> Colima is becoming a popular open alternative to Docker Desktop. It provisions the Docker container run time in a Lima VM, configures the Docker CLI on macOS and handles port-forwarding and volume mounts. Colima uses containerd as its run time, which is also the run time on most managed Kubernetes services — improving the important dev-prod parity. With Colima you can easily use and test the latest features of containerd, such as lazy loading for container images. We've been having good results with Colima in our projects. When in the Kubernetes space, we also use nerdctl, a Docker-compatible CLI for containerd. Since Kubernetes has deprecated Docker as container run time and most managed-services (EKS, GKE, etc) are following its lead, more people will be looking to containerd native tools, hence the importance of tools like nerdctl. In our opinion, Colima is realizing its strong potential and becoming a go-to option as an alternative to Docker Desktop.
* _Lima_: containerd for macOS https://jvns.ca/blog/2023/07/10/lima--a-nice-way-to-run-linux-vms-on-mac/
* _Podman_: same idea but 1) no daemon 2) allows for rootless 3) Red Hat's baby https://news.ycombinator.com/item?id=20542915 `podman play kube` = `docker-compose up` https://www.thoughtworks.com/radar/tools?blipid=202104064
* _runC_: Docker's runtime https://www.docker.com/blog/runc/
* _Packer_: build VM/container for use on cloud provider https://news.ycombinator.com/item?id=22491170
* _Vagrant_: build VM/container for local dev env using VirtualBox as sandbox https://www.mattlayman.com/blog/2019/web-development-environments/ used to be more popular https://news.ycombinator.com/item?id=15395601

HYPERVISORS
* _host_: os running hypervisor
* _hypervisor_: emulates host for vm
* _vm (guest)_: run atop hypervisor https://www.mattlayman.com/blog/2019/web-development-environments/ https://hacker-tools.github.io/virtual-machines/
* types: type 1 (used in data center, boots before os; ESXi, Hyper-V, Xen, KVM) type 2 (personal machines; VirtualBox, Parallels)

VMWARE
* _ESXi_: VMWare version of Docker Engine https://en.wikipedia.org/wiki/VMware_ESXi
* _VCenter_: manages ESXi hosts
* _VRops_: telemetry for VCenter?
* _OpenShift_: Kubernetes-aaS
* _OpenStack_: general IaaS https://www.youtube.com/watch?v=_gWfFEuert8
* _contention_: vm can't get resources scheduled from host

## Kubernetes

https://github.com/vladimirvivien/ktop
https://roadmap.sh/kubernetes
https://github.com/ghik/kubernetes-the-harder-way https://news.ycombinator.com/item?id=41393160
* _dstack_: OSS alternative https://github.com/dstackai/dstack https://www.youtube.com/watch?v=Kqp_LI85qVQ

🗄 `system.md` distributed
🔍 https://ramitsurana.github.io/awesome-kubernetes/
📚
* Luksa kubernetes in action
* basics https://cloud.google.com/kubernetes-engine/kubernetes-comic
* design https://jvns.ca/blog/2017/06/04/learning-about-kubernetes/
* course https://testdriven.io/blog/running-flask-on-kubernetes/

BASICS
* _Kubernetes_: declaratively run multiple containers and load balance btw
* _container_: app runtime/deps https://www.mattlayman.com/blog/2019/web-development-environments
* _pod_: define CPU, mem https://www.mattlayman.com/blog/2019/web-development-environments
* smallest obj in K8s obj model https://cloud.google.com/kubernetes-engine/kubernetes-comic
* container in which other containers (typically 1) are running
* _group_: n pods running on a node
* _node_: machine (physical, virtual) w/ container runtime (Docker, containerd) + Kubes agent
* _cluster_: n nodes https://www.mattlayman.com/blog/2019/web-development-environments 
* _etcd_: db on cluser state https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/ use Postgres https://martinheinz.dev/blog/100
* _Helm_: pkg manager for cluster; Cue https://github.com/stefanprodan/timoni
* _chart_: Helm pkg
* _Rancher_: hardened K8s for enterprise https://www.rancher.com/
* _controller_: program that talks to K8s API e.g. "start new server for each branch in GH repo" https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/
* also how K8S internals work? https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/

DESIGN
* once you have cluster set up, easy to add services https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/
* easy to see exact state of all services https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/
* use when you have more services than docker-compose
> Kubernetes sees itself as solving a problem statement closer to "CloudFormation" - in the sense that it wants to be sufficient to define your entire infrastructure - except that it also attempts to do so in a way that is generic over the underlying cloud provider or hardware. https://buttondown.email/nelhage/archive/two-reasons-kubernetes-is-so-complex/
* complexity https://k8s.af/ easier if managed https://news.ycombinator.com/item?id=22491794 https://www.lastweekinaws.com/blog/the-baffling-maze-of-kubernetes/ https://www.lastweekinaws.com/blog/a-brief-history-of-kubernetes-its-use-cases-and-its-problems/ https://www.lastweekinaws.com/blog/how-to-learn-something-new-kubernetes-the-much-harder-way/
* history: emerges from Borg (C++ 100M LOC) and moved to Linux Foundation (CNCF) in 2014
* previous competition: Swarm, Mesos, Nomad, Marathon https://technodrone.blogspot.com/2019/02/goodbye-docker-and-thanks-for-all-fish.html
* https://news.ycombinator.com/item?id=30767393

UTIL
* debugging Python https://martinheinz.dev/blog/99
* https://www.faizanbashir.me/interacting-with-kubernetes-deployments-and-services-using-python-sdk
* https://terminaltrove.com/kubecolor/
* GUI https://aptakube.com/
* _caretta_: dependency map https://github.com/groundcover-com/caretta
* _minikube_: run locally https://kubernetes.io/docs/tasks/tools/#minikube
* alternatives https://github.com/windmilleng/tilt https://github.com/kubernetes-sigs/kind
* _Karpenter_: autoscale nodes https://www.thoughtworks.com/radar/tools?blipid=202210013 https://karpenter.sh/
* _kubectl_: CLI
* switched btw namespaces and contexts/clusters https://github.com/ahmetb/kubectx
* _k9s_: better CLI https://github.com/derailed/k9s
* _Lens_: Electron app https://k8slens.dev/
* _mizu_: view API traffic https://www.thoughtworks.com/radar/tools?blipid=202210007 https://github.com/kubeshark/kubeshark/tree/main
* _skaffold_: https://github.com/GoogleContainerTools/skaffold https://www.mattlayman.com/blog/2019/web-development-environments
> run a process that will watch code files for changes and build and deploy to a Kubernetes cluster when changes are detected.
* tracing https://github.com/keyval-dev/odigos
* GUI https://github.com/lensapp/lens view as graph https://github.com/nevalla/lens-resource-map-extension/ web UI https://github.com/kinvolk/headlamp
* edit pod code locally https://github.com/metalbear-co/mirrord
* viz network policies https://editor.cilium.io/?id=keEeyzaunMgYXczJ https://artturik.github.io/network-policy-viewer/
* viz roles/RBAC https://github.com/appvia/krane https://github.com/alcideio/rbac-tool
* create roles/RBAC https://github.com/sighupio/permission-manager/ https://github.com/sighupio/permission-manager/tree/master/docs/assets

ZA
* networking https://jvns.ca/blog/2016/12/22/container-networking/
* certificates https://jvns.ca/blog/2017/08/05/how-kubernetes-certificates-work/
* certification https://www.cncf.io/certification/ckad/ https://www.youtube.com/watch?v=AplluksKvzI
* static scan https://www.thoughtworks.com/radar/tools?blipid=202203022
* test config https://github.com/open-policy-agent/conftest https://www.thoughtworks.com/radar/tools?blipid=202110014

## Python

* https://hynek.me/articles/docker-virtualenv/
* can install Poetry into the container and use it to install deps (vs. export deps from Poetry to `reqs.txt` bc Poetry doesn't current have a way to export only prod deps) https://jacobian.org/2019/nov/11/python-environment-2020/
* avoid deps reinstall https://stackoverflow.com/a/25307587/6813490 https://wsvincent.com/beginners-guide-to-docker/ 
* use venv for deps https://hynek.me/articles/python-app-deps-2018/ 
* Python versions
```Dockerfile
# images with Python baked in 

# official https://pythonspeed.com/articles/official-python-docker-image
# https://docs.docker.com/compose/django/
FROM python:3
# https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
FROM python:3.7
# https://wsvincent.com/beginners-guide-to-docker/
FROM python:3.7-alpine

# add to image yourself https://www.youtube.com/watch?v=prlixoDIfrc 7:50
FROM alpine:latest
RUN apk add --no-cache python3-dev
```
