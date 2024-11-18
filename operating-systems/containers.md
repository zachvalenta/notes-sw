# ⛩️

## 参考

🗄
* `aws.md` compute > containers
* `django.md` denv
* `linux.md` denv
* `src.md` denv

## 进步

PLAN GOING FORWARD
* air-capp: Docker Desktop
* mini23: Colima + see if you can run `product-workflow`
* get a handle on specs/OCI/CRI https://chatgpt.com/c/673a53d0-f3fc-8004-99ce-c0355d67d2f8

---

REPRO
* nix > apt? https://pythonspeed.com/articles/reproducible-docker-builds-python/
* using Poetry and uv inside Docker 🗄️ Python

HOWTO https://pythonspeed.com/docker/
* https://danielquinn.org/blog/developing-with-docker/ https://news.ycombinator.com/item?id=41935741
* basic https://www.youtube.com/watch?v=Ud7Npgi6x8E https://www.youtube.com/watch?v=YFl2mCHdv24
* ergonomics https://www.youtube.com/watch?v=3e8J_pv-xJI https://github.com/deluan/zsh-in-docker https://pythonbytes.fm/episodes/show/402/how-to-monetize-your-blog
* compose https://www.youtube.com/watch?v=HGKfE-cn9y4
* making things actually reproducible https://pythonspeed.com/articles/reproducible-docker-builds-python/
* Celery, Redis https://saasitive.com/tutorial/django-celery-redis-postgres-docker-compose
* Nginx https://github.com/zachvalenta/nginx-wsgi https://www.youtube.com/watch?v=Qw9zlE3t8Ko https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx
* TLS https://testdriven.io/blog/django-lets-encrypt/
* AWS https://testdriven.io/blog/django-docker-https-aws/
* https://pythonspeed.com/products/pythoncontainer/#changelog https://pythonspeed.com/products/productionquickstart/#changelog
* https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/
* https://www.untangled.dev/2020/06/06/docker-django-local-dev
* https://testdriven.io/courses/tdd-django
* https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
* https://github.com/godd0t/django-docker-quickstart

* _22_: rf Kubernetes notes
* _20_: docker-compose (handle container startup order) skeletons (SQLite, gunicorn, Postgres), secrets mgmt, workflow (build cache to speed rebuilds, use ARGs, Makefile rules for rebuild and shell) compose (variables for db creds, envs using multiple compose files)
* _19_: another course, Flask skeleton
* _17_: Pluralsight course, explain what a container is in a work meeting :)

# 🚢 DOCKER

📜 https://docs.docker.com/reference/
🔍 https://github.com/veggiemonk/awesome-docker
💻 repos (SQLite, Postgres, gunicorn, secrets) https://github.com/zachvalenta?tab=repositories&q=docker HTTPS https://testdriven.io/blog/django-docker-traefik/ https://www.youtube.com/watch?v=-hfejNXqOzA

---

ZA
* running as root https://blog.bejarano.io/how-to-write-great-container-images/ https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/ https://pythonspeed.com/articles/root-capabilities-docker-security/ https://pythonspeed.com/articles/vscode-broken-docker/ https://github.com/genuinetools/img 🗄 Docker alternatives
* create super user in container https://learndjango.com/tutorials/django-docker-and-postgresql-tutorial
* Docker as a company: still the default registry and runtime for development, but no longer the main runtime for prod https://news.ycombinator.com/item?id=26479921
* load balancing: single container w/ single app service https://stackoverflow.com/a/40872526/6813490 single container w/ n app services (with something to restart if they crash?) https://devops.stackexchange.com/questions/2089/what-are-the-advantages-of-dockerizing-nginx-and-php-in-different-containers#comment3231_2090
* logging: https://pythonspeed.com/articles/gunicorn-in-docker/ https://docs.docker.com/engine/reference/commandline/container_restart/
* ssh: https://stackoverflow.com/q/18136389/6813490
* socket https://blog.quarkslab.com/why-is-exposing-the-docker-socket-a-really-bad-idea.html

## 🟩 cmd

---

* https://www.youtube.com/watch?v=3e8J_pv-xJI
* cron, exec https://github.com/mcuadros/ofelia/
* stop inactive jobs https://github.com/sablierapp/sablier
* what files to ignore: `.git`, `local.db`, not `.dockerfile` https://gist.github.com/wassname/b25471b0f3bb2f9ff81f build context = tarball sent to daemon for image build https://codefresh.io/blog/not-ignore-dockerignore-2/

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

DEBUG
* https://www.youtube.com/watch?v=YRt1aB0iAlM
* `docker info`, attach to container process https://stackoverflow.com/q/19688314
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

## components

🗄️ engines

DOCKER DESKTOP COMPONENTS https://docs.docker.com/desktop/ 🧠 https://chatgpt.com/c/673bb2a2-0114-8004-86c3-c6e64defd3b3
> uninstall via AppCleaner? https://docs.docker.com/desktop/uninstall/
> start from shell https://stackoverflow.com/a/35979292
* Engine https://docs.docker.com/engine/install/
* GUI
* CLI
* Docker Compose
* Kubernetes client/server https://docs.docker.com/desktop/features/kubernetes/

FS
* images/containers/volumes: `~/Library/Containers/com.docker.docker`
* settings/metadata: `~/Library/Application Support/Docker`

---

OS STORAGE
* `docker.raw`: allocated 32GB but only 3-4GB of images https://apple.stackexchange.com/q/391377
> reset mine from 64 to 32GB
* cleanup https://stackoverflow.com/a/39890025

CONFIG
* CLI: `~/.docker/config.json` https://docs.docker.com/engine/reference/commandline/cli/#configuration-files https://docs.docker.com/engine/reference/commandline/config/
* daemon: `/etc/docker/daemon.json` https://docs.docker.com/config/daemon/#configure-the-docker-daemon
> why does `~/.docker` also have `daemon.json`?
* toomanyrequests -> fixed by rm `config.json` and restarting daemon https://github.com/docker/hub-feedback/issues/1250

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
* pipe into container https://travisjeffery.com/b/2015/09/piping-into-a-docker-container/
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

## 🛠️ tooling

* VSC Docker extension https://github.com/Microsoft/vscode-docker/issues/150#issuecomment-462079524 https://www.youtube.com/watch?v=dihfA7Ol6Mw
* Dockerfile lint https://github.com/hadolint/hadolint https://hadolint.github.io/hadolint/ https://github.com/goodwithtech/dockle
* image explore https://github.com/wagoodman/dive https://news.ycombinator.com/item?id=38913425
* CLI https://github.com/j-bennet/wharfee

TUI
* 🎯 https://github.com/jesseduffield/lazydocker
* https://github.com/will-moss/isaiah
* https://github.com/pommee/Pocker
* https://github.com/bcicen/ctop
* 🎯 https://github.com/mrjackwills/oxker
* https://github.com/moncho/dry
* https://github.com/amir20/dozzle
* https://github.com/robertpsoane/ducker

## volumes

🗄️ `system.md` Capp data eng
📜 https://docs.docker.com/storage/

---

https://roadmap.sh/docker

VOLUMES
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

TYPES https://stackoverflow.com/a/55366707 https://www.youtube.com/watch?v=YFl2mCHdv24 8:27
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

🗄️ `linux.md` perms
📚
* Clinton linux in action
* Evans containers
* Galvin dinosaur ch 16
* Takemura book of xen
* Tanenbaum circus ch 7

EVANS CONTAINERS https://x.com/b0rk/status/1227244309621215233 https://roadmap.sh/docker
* why: avoid dependency diffs by separating host/container filesystem
* _image_: tarball of OS + system libs (libc) + language (runtime, libs) + your src
* _cgroup (control group)_: `cgroup_id` create ID `cgset` set CPU/mem limits `cgexec $ARGS unshare $ARGS` create cgroup 
* v2 not supported on macOS https://github.com/facebookincubator/below/issues/8239 https://chatgpt.com/c/6734fc58-e87c-8004-a6aa-29f218382928 
* _namespaces_: https://man7.org/conf/meetup/understanding-user-namespaces--Google-Munich-Kerrisk-2019-10-25.pdf
* _seccomp_: 
* _capability_: https://pythonspeed.com/articles/root-capabilities-docker-security/
* _union filesystems_: overlay https://x.com/tim_raymond/status/1227250152248877056

layers
* _layer_: tarball i.e. files https://jvns.ca/blog/2019/11/18/how-containers-work--overlayfs/
* _build cache_: creates intermediates images along the way (w/ own ids https://cameronlonsdale.com/2018/11/26/whats-in-a-docker-image/) Dockerfile executed top to bottom so put stuff that will change most frequently (e.g. source) at the bottom so that it doesn't invalidate the build cache (any invalidated layer will invalidate all subsequent layers) https://pythonspeed.com/articles/docker-caching-model/ aka 'layer cache' https://testdriven.io/blog/faster-ci-builds-with-docker-cache/
* caching https://roadmap.sh/docker
* _rebuilding_: can use existing layers or force a fresh build https://stackoverflow.com/a/35595021

---

https://bitfieldconsulting.com/blog/container-security

https://blog.lizzie.io/linux-containers-in-500-loc.html

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

## engines

🗄
*️ components
* `aws.md` compute > containers

HOW DOCKER WORKS 🧠 https://chatgpt.com/c/673bb2a2-0114-8004-86c3-c6e64defd3b3
* macOS: macOS Hypervisor Framework (Desktop) VirtualBox (Docker Toolbox, Docker Machine) https://stackoverflow.com/a/38624540
* Windows: Hyper-V, WSL2

---

OCI vs. Docker, Docker Engine vs. Docker Desktop https://roadmap.sh/docker

> tldr for now is that Docker for Desktop is slow/bad security/registry weirdness but also the best option for getting everyone up and running

🧠 https://chatgpt.com/c/6724c43a-a9cc-8004-809b-2b53075f84af

> desktop macos app too heavy https://github.com/docker/for-mac/issues/2297 https://news.ycombinator.com/item?id=41987857

HN AGG
* https://news.ycombinator.com/item?id=33539019
* https://news.ycombinator.com/item?id=33538199
* https://news.ycombinator.com/item?id=28369570
* registry weirdness https://news.ycombinator.com/item?id=35166317
* dont use https://www.youtube.com/watch?v=wVil7wG-1yg https://news.ycombinator.com/item?id=26746280
* next-gen images https://yonkeltron.com/posts/why-cloud-native-buildpacks-should-excite-companies/

RUNTIMES
* _container engine_: runtime
* mostly Docker for now, but things like the Open Container Initiative (OCI) and the Runtime Spec could lead to a new runtime https://blog.technodrone.cloud/2019/02/goodbye-docker-and-thanks-for-all-fish.html https://github.com/containers/skopeo
* _containerd_: container engine
* used in Kubernetes https://www.thoughtworks.com/radar/platforms?blipid=202203015
* used in Colima https://www.thoughtworks.com/radar/platforms?blipid=202203015
* used to be Docker but now OSS https://news.ycombinator.com/item?id=26479921 https://github.com/containerd/containerd https://github.com/google/gvisor
* BYO https://github.com/kelseyhightower/kubernetes-the-hard-way
* _runC_: Docker's runtime https://www.docker.com/blog/runc/
* API to Docker daemon https://github.com/fussybeaver/bollard https://github.com/mrjackwills/oxker https://docker-py.readthedocs.io/en/stable/index.html

DOCKER DESKTOP ALTERNATIVES
* _Colima_: https://github.com/abiosoft/colima
> Colima is becoming a popular open alternative to Docker Desktop. It provisions the Docker container run time in a Lima VM, configures the Docker CLI on macOS and handles port-forwarding and volume mounts. Colima uses containerd as its run time, which is also the run time on most managed Kubernetes services — improving the important dev-prod parity. With Colima you can easily use and test the latest features of containerd, such as lazy loading for container images. We've been having good results with Colima in our projects. When in the Kubernetes space, we also use nerdctl, a Docker-compatible CLI for containerd. Since Kubernetes has deprecated Docker as container run time and most managed-services (EKS, GKE, etc) are following its lead, more people will be looking to containerd native tools, hence the importance of tools like nerdctl. In our opinion, Colima is realizing its strong potential and becoming a go-to option as an alternative to Docker Desktop.
* _Lima_: containerd for macOS https://jvns.ca/blog/2023/07/10/lima--a-nice-way-to-run-linux-vms-on-mac/
* _Podman_: no daemon, rootless, Red Hat https://news.ycombinator.com/item?id=20542915 `podman play kube` = `docker-compose up` https://www.thoughtworks.com/radar/tools?blipid=202104064
* _Packer_: build VM/container for use on cloud provider https://news.ycombinator.com/item?id=22491170
* _Vagrant_: build VM/container for local dev env using VirtualBox as sandbox https://www.mattlayman.com/blog/2019/web-development-environments/ used to be more popular https://news.ycombinator.com/item?id=15395601

## images

🔍 https://github.com/docker-library/official-images

* _image_: blueprint for container
* built from read-only file system layers
* _repository_: n images w/ same name but diff version tags https://stackoverflow.com/q/34004076
* _registry_: stores images

REGISTRIES
* _ECR_: AWS
* commercial: AWS ECR, Docker Trusted Registry https://github.com/veggiemonk/awesome-docker#registry

---

* publishing https://github.com/tiangolo/uwsgi-nginx-docker https://github.com/jessfraz/dockerfiles/blob/master/httpie/Dockerfile

* dont use Alpine? https://martinheinz.dev/blog/92
* view fs changes https://github.com/wagoodman/dive https://fzakaria.com/2020/05/31/containers-from-first-principles.html
* copy images from one registry to another https://www.thoughtworks.com/radar/tools?blipid=202203084 https://github.com/containers/skopeo
* security scan https://github.com/anchore/grype https://www.thoughtworks.com/radar/tools?blipid=202203019
* _get image size_: `docker image ls --format "{{ .Size }}" <image_name>` https://pythonspeed.com/articles/system-packages-docker/
* _create new image_: pull base image, start container and run some commands, then save as new image `docker container commit -m "my new image" <container-id> my-new-image:<version>`

MULTI-STAGE
* _raison d'etre_: smaller images, esp. w/out separate Dockerfiles per env https://docs.docker.com/develop/develop-images/multistage-build/#before-multi-stage-builds https://labs.iximiuz.com/tutorials/docker-multi-stage-builds
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

* Dockerfile: instructuions to build image https://stackoverflow.com/a/45549372
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

## Kubernetes

* good for on-prem? https://danluu.com/simple-architectures/
> As for Kubernetes, we use Kubernetes because knew that, if the business was successful (which it has been) and we kept expanding, we'd eventually expand to countries that require us to operate our services in country. The exact regulations vary by country, but we're already expanding into one major African market that requires we operate our “primary datacenter” in the country and there are others with regulations that, e.g., require us to be able to fail over to a datacenter in the country.

---

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
* anti-pattern https://changelog.com/shipit/126
* once you have cluster set up, easy to add services https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/
* easy to see exact state of all services https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/
* use when you have more services than docker-compose
> Kubernetes sees itself as solving a problem statement closer to "CloudFormation" - in the sense that it wants to be sufficient to define your entire infrastructure - except that it also attempts to do so in a way that is generic over the underlying cloud provider or hardware. https://buttondown.email/nelhage/archive/two-reasons-kubernetes-is-so-complex/
* complexity https://k8s.af/ easier if managed https://news.ycombinator.com/item?id=22491794 https://www.lastweekinaws.com/blog/the-baffling-maze-of-kubernetes/ https://www.lastweekinaws.com/blog/a-brief-history-of-kubernetes-its-use-cases-and-its-problems/ https://www.lastweekinaws.com/blog/how-to-learn-something-new-kubernetes-the-much-harder-way/
* history: emerges from Borg (C++ 100M LOC) and moved to Linux Foundation (CNCF) in 2014
* previous competition: Swarm, Mesos, Nomad, Marathon https://technodrone.blogspot.com/2019/02/goodbye-docker-and-thanks-for-all-fish.html
* https://news.ycombinator.com/item?id=30767393
* https://news.ycombinator.com/item?id=42042163

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

## 🐍 Python

---

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

## secrets

---

RUNTIME
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

BUILDTIME
* present in image layer
* _good idea_: over the network, either from vault or your own workaround https://pythonspeed.com/articles/docker-build-secrets/
* _not yet_: BuildKit and `--secret` https://docs.docker.com/develop/develop-images/build_enhancements/#new-docker-build-secret-information https://ponderosa.io/blog/docker/2019/04/13/secrets-in-docker-builds/ leaves trace of image file https://github.com/moby/moby/issues/38667
* _bad ideas_: `ARG`/`ENV` https://docs.docker.com/engine/reference/builder/#arg https://vsupalov.com/docker-arg-env-variable-guide/ env file https://stackoverflow.com/a/46919859 `–build-arg` https://pythonspeed.com/articles/docker-build-secrets/

https://www.youtube.com/watch?v=MlzbHXMQZY4
* _docker-compose_: https://pythonspeed.com/articles/build-secrets-docker-compose https://keepgrowing.in/tools/set-up-a-postgresql-database-with-docker/ https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/ https://blog.rogs.me/2020/05/how-i-manage-multiple-development-environments-in-my-django-workflow-using-docker-compose/ https://vsupalov.com/docker-arg-env-variable-guide/
