# ⛩️

## 参考

📜 https://git-scm.com/docs `help <cmd>`

## 进步

* ⭐️ managing many Git repos https://github.com/alajmo/mani
* https://github.com/sinclairtarget/git-who
* need way to toggle git diff away from delta for copying plaintext 🗄️ `bin/gco`
> or can delta itself provide a toggle?
* backup to Codeberg https://github.com/AkashRajpurohit/git-sync
* autogit https://github.com/zackproser/automations
* What might be the cause of autocompletions around Git just stopping working?
> this doesn't happen in every dir, just `capp/mapper`
```sh
git --version
# git version 2.39.3 (Apple Git-146)
# most current version is 2.47

# If using Zsh, the completion cache might be corrupted.
rm -f ~/.zcompdump* && compinit
```

* Git Town https://www.youtube.com/watch?v=oLaUsUlFfTo https://github.com/git-town/git-town
* https://github.com/zackproser/automations
* https://www.gitkraken.com/gitlens https://www.youtube.com/watch?v=oJdlGtsbc3U https://switowski.com/blog/plugins-for-python-in-vscode/

* _24_: pager (delta, diffnav) porcelain (lazygit) utils (`jiancha`, `ghc`, `xmp`, `zp`)
* _21_: prepopulate commit msg
> no memory of doing this, nor knowledge of how to do now
* _20_: stash commands, 📙 Chacon ch 1-2, Gitlab as secondary remote for notes, auth for BNY (Gitlab token types, server protocols and set up, lots of debugging)
* _19_: hooks (pre-commit) branches (another pass at merge squash rebase) tooling (GitUp, Tig, diff-so-fancy for pager)
* _18_: PR workflow
* _17_: desultory corporate usage, tutorial w/ Roberto

# 🐙 GITHUB

🗄️ `src.md` CICD > Actions
📜 https://docs.github.com
🔗 https://github.com/github/roadmap

SHORTCUTS https://darrenburns.net/posts/github-tips
* `t`: file search in repo
* `t`: jump to symbol in code review
* `b`: blame view in file

FEATURES https://buttondown.com/hillelwayne/archive/github-has-too-many-hidden-features/
* topics https://github.com/topics/copier-template
* wiki: not searchable https://stackoverflow.com/questions/12535602/search-for-a-keyword-within-a-github-wiki can't find out how to edit project names https://github.com/kraanzu/dooit/wiki
* README for org: `.github-private` repo w/ `profile/README.md` https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile#adding-a-member-only-organization-profile-readme
* contributions: won't count unless user pushing them using same email tied to account in `.gitconfig`
```sh
# attempt to get daily contributions without having to check site 🗄️ `denv/bin/gstat`
gh api "/users/zachvalenta/events" | jq 'map(select(.created_at | startswith("2024-10-24")))' | jl
```
* feedback https://github.com/isaacs/github/issues/6 https://github.com/orgs/community/discussions
* all forks are public https://news.ycombinator.com/item?id=41060102
* _repo language_: https://github.com/github/linguist#overrides
* _repo config_: branch protections http://blog.jaredsinclair.com/post/183676881105/think-twice-before-downgrading-to-a-free-github owners https://blog.github.com/2017-07-06-introducing-code-owners/

## Actions

🗄️ `infra.md` CICD
📜 https://docs.github.com/en/actions
🔬 https://github.com/GothenburgBitFactory/taskwarrior/actions

SEMANTICS
* _workflow_: collection of jobs (test|deploy|add label to issue) defined in `.github/workflows`; triggered by event|chron|API
* _job_: collection of steps
* _step_: user-defined action (script) https://docs.github.com/en/actions/about-github-actions/understanding-github-actions
> Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another. For example, you can have a step that builds your application followed by a step that tests the application that was built.
* _runner_: container in which steps are run
> A runner is a server that runs your workflows when they're triggered. Each runner can run a single job at a time.
* _action_: GH-defined extension
> An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task. Use an action to help reduce the amount of repetitive code that you write in your workflow files. An action can pull your Git repository from GitHub, set up the correct toolchain for your build environment, or set up the authentication to your cloud provider.

EVENTS
* properties: id, type, payload, actor (user that triggers), repo (where event happens)
* `CreateEvent`: branch|tag created https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows
* `GollumEvent`: wiki page created|updated https://docs.github.com/en/rest/using-the-rest-api/github-event-types?apiVersion=2022-11-28#gollumevent
* `IssueCommentEvent`: comment on issue|PR
* `IssuesEvent`: opened, edited, closed, assigned, labeled
* `PullRequestEvent`: opened, edited, closed, review_requested
* `PushEvent`: commits pushed to branch

---

* shell https://yossarian.net/til/post/any-program-can-be-a-github-actions-shell/
* https://news.ycombinator.com/item?id=43419701
* use on AWS https://github.com/CloudSnorkel/cdk-github-runners
telemetry https://github.com/catchpoint/workflow-telemetry-action/issues/39 https://blog.smidt.dev/posts/0003/
can manipulate tags, create releases in repo using CLI https://cli.github.com/manual/gh_release

TOOLING
* _act_: run locally https://github.com/nektos/act https://github.com/bahdotsh/wrkflw
* _gama_: https://github.com/termkit/gama

* linking https://blog.github.com/2011-10-12-introducing-issue-mentions/
* draft PR https://github.blog/2019-02-14-introducing-draft-pull-requests/
* https://hynek.me/articles/python-github-actions/
* https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow
* https://github.com/sdispater/mixology/blob/master/.github/workflows/tests.yml
* https://github.com/github/super-linter
* https://www.youtube.com/watch?v=E1OunoCyuhY
* https://news.ycombinator.com/item?id=30060765
* https://towardsdatascience.com/ultimate-ci-pipeline-for-all-of-your-python-projects-27f9019ea71a
* python https://brntn.me/blog/open-source-python-ci/
* https://github.com/carderne/postmodern-python/blob/main/.github/workflows/pr.yml

## CLI

🗄️ `task-mgmt.md` 2024 workflow
📜 https://cli.github.com/manual/ https://github.com/cli/cli

REPOS
```sh
gh search repos $QUERY  # search all
gh search repos --owner=$OWNER $QUERY  # gh search repos --owner=zachvalenta markov

gh browse  # open $CWD repo on site
gh browse --repo $OWNER/$REPO  # open arbitrary

gh repo clone $OWNER/$NAME  # gh repo clone zachvalenta/markov-monte

gh repo create $NAME --private

gh repo edit --description $DESC
```

TOPICS https://simonwillison.net/2020/Oct/9/git-scraping/
```sh
# read
gh search repos --owner=zachvalenta "topic:$TOPIC"

# create (shows up in UI under description)
gh repo edit $REPO --add-topic "cli,python,utils"
gh repo edit https://github.com/zachvalenta/eliza --add-topic "publish"

# delete
gh repo edit $REPO --remove-topic "topic1,topic2"
```

GIST
```sh
gh gist list|clone|edit
```

---

EXTENSIONS
* howto https://docs.github.com/en/github-cli/github-cli/using-github-cli-extensions
* _hub_: https://hub.github.com/#developer https://github.com/mislav/hub https://mislav.net/2020/01/github-cli/
> used to work for Github? https://github.com/github/hub
* _gitsome_: https://github.com/donnemartin/gitsome

```sh
# alias https://cli.github.com/manual/gh_alias https://github.com/zachvalenta/dotfiles-um
gh alias set --shell prl "gh pr list --author zachvalenta --repo tommyboytech/t3"  # get PR number
gh alias set --shell prv 'gh pr view "$1" --repo tommyboytech/t3 -w'               # view PR in browser

##################3

# get PRs
gh pr list --author zachvalenta --repo tommyboytech/t3

# ❌ reviews requested
gh pr list --search "user-review-requested:zachvalenta" --repo tommyboytech/t3
gh pr list --search "user-review-requested:@me" --repo tommyboytech/t3
gh pr list --search "review-requested:zachvalenta" --repo tommyboytech/t3

# get PR number
gh pr list --author zachvalenta --repo tommyboytech/t3 | rg "\d" | awk '{ print $1 }'

# view PR
gh pr view 9985 --repo tommyboytech/t3 
gh pr view 9985 --repo tommyboytech/t3 -w
gh pr view 9985 --repo tommyboytech/t3 --comments

# view PR in browser
gh pr list --author zachvalenta --repo tommyboytech/t3 | rg '\d' | awk '{ print $1 }' | xargs gh pr view --repo tommyboytech/t3 -w

# ❌ awk needs single quotes to work but Github CLI removes column parameter
gh alias set --shell prv "gh pr list --author zachvalenta --repo tommyboytech/t3 | rg '\d' | awk '{ print $1 }' | xargs gh pr view --repo tommyboytech/t3 -w"
gh alias list
# prl:  !gh pr list --author zachvalenta --repo tommyboytech/t3
# prv:  !gh pr list --author zachvalenta --repo tommyboytech/t3 | rg '\d' | awk '{ print  }' | xargs gh pr view --repo tommyboytech/t3 -w
```

## Markdown

📜 https://docs.github.com/en/get-started/writing-on-github
🔗 https://calmcode.io/course/readme-files/dearme-readme

* use GIF https://github.com/Melkeydev/go-blueprint -> screws up the headers, no?
```md
## Way to Keep Headers?
![](./public/advanced.gif)

![Alt text](path/to/your.gif)
```
* link to header: `[Link text](#header-name)`
* add a welcome video! https://github.com/grafana/pyroscope
* use SVG https://github.com/zachvalenta/capp-prod-cat-alt https://github.com/pommee/Pocker
* use webp https://github.com/zachvalenta/capp-handbook/commit/0e4e94e78f7e4854b4ae4e1437d509dc86384c84
* use HTML https://github.com/catppuccin/delta/blame/main/README.md
* "try without installing!" https://zellij.dev/
* directory tree https://github.com/koaning
* alerts https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts https://github.blog/changelog/2023-12-14-new-markdown-extension-alerts-provide-distinctive-styling-for-significant-content/ https://github.com/orgs/community/discussions/16925
* note highlighting: note, tip, important, warning, caution
```markdown
> [!NOTE]
> general
> [!TIP]
> shortcuts
> [!IMPORTANT]
> announcements
> [!CAUTION]
> questions
> [!WARNING]
> mutations
```

---

* project logos https://github.com/PaulJuliusMartinez/jless https://chatgpt.com/share/66eb331c-04e4-8004-9b25-b7bb5d5a5b78 https://github.com/lambda-fairy/maud https://github.com/cosimameyer
* how to link to images outside of repo https://github.com/textualize/toolong
* _profile README_: create repo with same name as user, add README https://github.com/willmcgugan/willmcgugan https://github.com/mrjackwills
* _video_: https://github.com/textualize/toolong

## repos

> https://github.com/rubysolo/brows
> learn how to use browser shortcuts for faster nav

ISSUES
* surface top-ranking https://github.com/zed-industries/zed/issues/6952
* `TODO` checker https://github.com/preslavmihaylov/todocheck
* dashboard https://github.com/dlvhdr/gh-dash https://github.com/pwntester/octo.nvim https://github.com/skanehira/github-tui
* templates https://github.com/GabAlpha/basilk/tree/master/.github/ISSUE_TEMPLATE
```txt
We also encourage you to put up a PR yourself! Who cares if you've never written Go before, neither did any of the existing contributors before their first lazygit PR! Check out the PR tutorial here: https://www.youtube.com/watch?v=kNavnhzZHtk&ab_channel=JesseDuffield
```

TOOLS
* https://github.com/skanehira/gh.vim https://github.com/skanehira/denops-gh.vim
* template repo https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository https://github.com/jackyzha0/quartz
* browse releases https://github.com/rubysolo/brows
* repo stats https://github.com/o2sh/onefetch https://github.com/oleander/git-fame-rb
* heat map https://github.com/jmforsythe/Git-Heat-Map

### assessment tool

💡 TUI for quick sustainability assessment of Github repo https://chatgpt.com/c/671692f3-9ca8-8004-8b71-8ae027bdbbad
💻 https://github.com/zachvalenta/capp-denv-bin/blob/main/ghgj

* profile views instead of stars? https://github.com/xnacly
> stars https://github.com/github/feedback/discussions/8293 https://github.com/korosuke613/gh-user-stars https://webapps.stackexchange.com/a/41800 https://github.com/maguowei/starred#use-awesome-stars-as-template https://github.com/maguowei/awesome-stars/blob/master/topics.md https://github.com/DaveParr/starpilot https://github.com/den-is/gh-stars-scraper
> good for: https://github.com/veggiemonk/awesome-docker
> Terminal Trove
> https://github.com/gitbutlerapp/gitbutler https://repobeats.axiom.co/
> make this into a meta svc for awesome-$SOFTWARETYPE repos
> https://json-schema.org/tools
> do existing repo browsers offer?
* total stars
* commits: frequency, rate over time, first & last
* issues: open vs. closed, most recently closed
```sh
# https://github.com/ponyorm/pony

# OVERALL
gh repo view ponyorm/pony --json stargazerCount,primaryLanguage,createdAt,description,contactLinks,fundingLinks,homepageUrl,isArchived,issues,labels,latestRelease,licenseInfo,milestones,name,openGraphImageUrl,owner,parent,primaryLanguage,pullRequests,pushedAt,repositoryTopics,updatedAt,url,viewerHasStarred,visibility,watchers

# ISSUES
gh issue list --repo ponyorm/pony --state open --json number --jq 'length'
gh issue list --repo ponyorm/pony --state closed --json number --jq 'length'
```

```txt
https://github.com/pudo/dataset
https://github.com/encode/orm
https://github.com/python-gino/gino
https://github.com/sdispater/orator
https://github.com/coleifer/peewee
https://github.com/piccolo-orm/piccolo
https://github.com/tiangolo/sqlmodel
https://github.com/sqlc-dev/sqlc
https://github.com/tortoise/tortoise-orm
```
```sh
#!/usr/bin/env bash
INPUT_FILE=$1
echo "Repository,Stars"

# PROCESS INPUT FILE
while IFS= read -r URL; do
    # extract owner/repo name using parameter expansion
    REPO=${URL#https://github.com/}
    # use cli to get the star count
    STARS=$(gh repo view "$REPO" --json stargazerCount --jq '.stargazerCount' 2>/dev/null)
    # err handle
    if [ $? -ne 0 ]; then
        echo "Failed to fetch data for $REPO"
        STARS="N/A"
    fi
    echo "$REPO,$STARS"
done < "$INPUT_FILE"
```
```sh
#!/usr/bin/env bash
TODAY=$(date -I)  # Current date in YYYY-MM-DD format
gh api "/users/zachvalenta/events" | jq 'map(select(.created_at | startswith("2024-10-24")))' | jless -r
# gh api "/users/zachvalenta/events" | jq 'map(select(.created_at | startswith("$TODAY")))' | jl
# gh api "/users/zachvalenta/events" | jq 'map(select(.created_at | startswith("2024-10-24")))'
# gh api "/users/zachvalenta/events" | jq --arg today "$TODAY" and .type == "PushEvent"
# gh api "/users/zachvalenta/events" | \
# jq --arg today "$TODAY" '
#   map(select(.created_at | startswith($today) and .type == "PushEvent"))
# '

# gh api "/users/zachvalenta/events" | jq --arg today "$(date -I)" 'map(select(.created_at | startswith($today) and .type == "PushEvent"))'
# gh api "/users/zachvalenta/events" | jq --arg today "$(date -I)" '.[] | select(.created_at | startswith($today) and .type == "PushEvent")'
# gh api "/users/zachvalenta/events" | jq --arg today "$(date -I)" '[.[] | select(.created_at | startswith($today) and .type == "PushEvent")] | length'
# gh api "/users/zachvalenta/events" --jq '.[] | select(.type == "PushEvent" and .created_at | startswith("'"$(date -I)"'"))'

# Fetch events and filter relevant contribution events
# gh api "/users/your-username/events" | \
# jq --arg today "$TODAY" '
#   map(select(.created_at | startswith($today) and 
#     (
#       .type == "PushEvent" or
#       .type == "IssuesEvent" or
#       .type == "PullRequestEvent" or
#       .type == "PullRequestReviewEvent"
#     )
#   ))
# '
```

## search

* doesn't search non-main branches https://github.com/search?q=owner%3Azachvalenta+bullet+language%3APython&type=code&l=Python https://github.com/zachvalenta/capp-prod-cat/blob/link-nodes/tree_viz.py 🗄️ `stdlib.md` UI / IO / input / bullet
* filters: `org:freeCodeCamp language:python path:**/Makefile user:zachvalenta extension:py` https://stackoverflow.com/a/28347129 https://stackoverflow.com/a/42418887

---

https://buttondown.com/hillelwayne/archive/github-search-for-research-and-learning/
https://docs.github.com/en/github/searching-for-information-on-github/searching-on-github
* https://github.blog/2021-12-08-improving-github-code-search/ https://github.com/features/code-search 🗄 `vim.md` code completion
* files in repo: `t`
* filters: `org:freeCodeCamp language:python filename:.tigrc user:zachvalenta extension:py` https://stackoverflow.com/a/28347129 https://stackoverflow.com/a/42418887
> path:**/Makefile -> this the current query syntax as of 24.12?
> doesn't seem to work for hidden files
> doesn't seem to work for exact searches e.g. `[behave]`
* can use regex https://news.ycombinator.com/item?id=22396824
* file with text inside: `callback_whitelist filename:ansible.cfg`
* issues you created `author:zachvalenta`

# 🔬️ INTERNALS

> No idea. Just memorize these shell commands and type them to sync up. If you get errors, save your work elsewhere, delete the project, and download a fresh copy https://xkcd.com/1597/
🪚 BYO
* https://maryrosecook.com/
* https://www.youtube.com/playlist?list=PLrmY5pVcnuE_jPv620IWQV0TsJ_RCmg13
* https://www.leshenko.net/p/ugit/
* https://zserge.com/posts/git/
🎨
* https://onlywei.github.io/explain-git-with-d3
* https://github.com/initialcommit-com/git-sim https://initialcommit.com/blog/git-sim
📚
* https://xosh.org/explain-git-in-simple-words/
* https://zwischenzugs.com/2018/05/14/beyond-punk-rock-git-in-eleven-steps/
* Chacon https://git-scm.com/book/en/v2
* Evans https://wizardzines.com/zines/git/
* Perrotta https://www.pluralsight.com/courses/how-git-works

---

CLEANUP
* https://beej.us/guide/bggit/html/split/
* https://smusamashah.github.io/explain-git-in-simple-words
* http://www-cs-students.stanford.edu/~blynn/gitmagic/
* https://thoughtbot.com/upcase/mastering-git
* https://news.ycombinator.com/item?id=22200222
* https://betterexplained.com/articles/aha-moments-when-learning-git/
* https://rachelcarmena.github.io/2018/12/12/how-to-teach-git.html
* design http://aosabook.org/en/git.html
* write your own https://wyag.thb.lt/
* https://benhoyt.com/writings/pygit/
* https://codewords.recurse.com/issues/two/git-from-the-inside-out
* https://www.kenneth-truyers.net/2016/10/13/git-nosql-database/

EVANS
* https://jvns.ca/blog/2024/01/26/inside-git/
* https://jvns.ca/blog/2023/11/23/branches-intuition-reality/
* https://jvns.ca/blog/2023/09/14/in-a-git-repository--where-do-your-files-live-/
* https://jvns.ca/blog/2023/11/01/confusing-git-terminology/
* https://jvns.ca/blog/2023/10/20/some-miscellaneous-git-facts/
* https://jvns.ca/blog/2024/02/16/popular-git-config-options/#core-pager-delta

* _snapshot_: files at particular time e.g. a commit https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
* `checkout`: will move rm changes to file in working tree e.g. if file is updated and staged, then updated again, checkout will only rm most recently updates i.e. changes in staging area won't be affected
> use switch instead https://martinheinz.dev/blog/109 https://adamj.eu/tech/2023/10/04/boost-your-git-dx-out-now/
* _reference_: human-readable name acting as point to commit SHA-1

EXPLAIN TO NON-USER
```yaml
working tree = current state of the files
sprint so far = commits so far
think of a commit as a named save. could be updates to single file or many, and then you save the current state of the file system and write a message e.g. "learn about string theory".
"sprint" is just the name of a branch.
think of a branch as a version.
for example, you have a bundle of notes for a novel. your branch is called "chanels-big-novel".
you get chantel to provide feedback. she makes a branch for herself, "chantels-edits".
she can then edit away and it won't touch your work.
she can propose merging the two branches i.e. her edits would become part of "chanels-big-novel."
```

## states

file state https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
* _untracked_: anything that wasn't in the last snapshot and not currently in the staging area i.e. files that Git doesn't know about
* _unmodified_: not updated since last commit
* _modified_: updated since last commit
* _staged_: to be incl in next commit, after which it will return to unmodified

sections https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
* _working directory_: modified; aka 'working tree'; 'clean' = empty = no modified files
* _index/staging area_: staged; file changes marked for save in next commit
* _repository_: committed; `.git`

## design

* future https://blog.waleedkhan.name/git-ui-features/
* distributed: less network latency than centralized https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control
* full version of repo history https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository
* reversible: Git database onlys adds data so it's hard to do something that's not reversible https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
* no server: no predefined client/server relationship among repos i.e. Github acts as a server but could be just another client https://zwischenzugs.com/2018/05/14/beyond-punk-rock-git-in-eleven-steps/
* text-first: meant for smaller repos and text https://superuser.com/q/13376 GFVS for large repos https://pythonbytes.fm/episodes/show/53/getting-started-with-devpi-and-git-virtual-fs
```sh
db/query-sandbox  $ git push -u origin main
Writing objects: 100% (17/17), 40.31 MiB | 596.00 KiB/s, done.
Total 17 (delta 0), reused 0 (delta 0), pack-reused 0
remote: warning: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
remote: warning: See http://git.io/iEPt8g for more information.
remote: warning: File data/housing.csv is 66.34 MB; this is larger than GitHub's recommended maximum file size of 50.00 MB
```

HISTORY https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control
* _version control_: stores content and tracks changes to content https://medium.com/@willhayjr/the-architecture-and-history-of-git-a-distributed-version-control-system-62b17dd37742
* _first generation_: SCCS 📙 Thomas pragmatic programmer [60]
* _second generation_: 2000 - centralized - CVS, SVN/Subversion, Perforce, Bitkeeper https://twobithistory.org/2018/07/07/cvs.html https://blog.gitbutler.com/why-github-actually-won/
* _third generation_: 2005 - distributed - Git (dominance such Stack Overflow dev survery no longer asks about VCS and people even use as a client to other VCS https://git-scm.com/book/en/v2/Git-and-Other-Systems-Git-as-a-Client) https://blog.gitbutler.com/why-github-actually-won/ alternatives (FB uses Mercurial http://aosabook.org/en/mercurial.html SQLite uses Fossil https://fnc.bsdbox.org/index)
> absorb Mercurial https://news.ycombinator.com/item?id=41653191
> people like revsets https://news.ycombinator.com/item?id=10968135
> used by Facebook, Unity https://news.ycombinator.com/item?id=20745393
> Mercurial design https://news.ycombinator.com/item?id=18029498
* Git for everything https://news.ycombinator.com/item?id=30522175
* _fourth generation_: https://github.com/martinvonz/jj https://news.ycombinator.com/item?id=42934427 https://tonyfinn.com/blog/jj/ https://v5.chriskrycho.com/essays/jj-init/ https://news.ycombinator.com/item?id=42310386 Gerrit https://techspot.zzzeek.org/2016/04/21/gerrit-is-awesome/
> Jujutsu is a version control system. They aim to be independent at some point but for now it is a heady frontend on top of git (a big advantage – all of your existing git repos and tools are trivially compatible with it). https://drewdevault.com/2024/12/10/2024-12-10-Daily-driving-jujutsu.html

LINKABLE LIBRARIES 🗄 `python.md` Git
* reference impl of Git doesn't include i.e. can only as an executable, not as lib https://medium.com/@willhayjr/the-architecture-and-history-of-git-a-distributed-version-control-system-62b17dd37742 
* reimplementations include e.g. `libgit2` (C) which is used by other language implementations e.g. pygit2 (Python) https://github.com/gitpython-developers/GitPython/issues/240 Rugged (Ruby) https://git-scm.com/book/en/v2/Appendix-B%3A-Embedding-Git-in-your-Applications-Libgit2

## db of hashes

* _Git_: fs db of objects impl as DAG
* _object_: hash https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
* _blob_: hash of file contents
* _tree_: blob + metadata (file name, permissions)
* _commit_: tree + more metadata (msgs, committer, author) + parent commit
* _branch_: reference to a commit; stored in `.git/ref/head`
* _HEAD_: most recent commit of current branch; `.git/ref/head/<current_branch>`
* compressed https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

# 🛠️ TOOLING

🗄️ `vim.md` utils / code intel / git

## ⬆️ GUI (GitUp)

* _gitbutler_: 🎯 不明觉厉 https://github.com/gitbutlerapp/gitbutler https://blog.gitbutler.com/ https://jackevans.bearblog.dev/some-notes-on-git/
* _GitKraken_: corporate https://www.gitkraken.com/
* _GitUP_: ✅ https://github.com/git-up/GitUp
* good for granular stages
* switch views `cmd #`
* open commit into quick view `space`
* _SmartGit_: https://www.syntevo.com/smartgit/ https://news.ycombinator.com/item?id=42262047
* _Recon_: https://retcon.app/ https://news.ycombinator.com/item?id=42262047
* _Tower_: 🎯 reorder commits https://www.git-tower.com

---

* alternatives https://git-scm.com/downloads/guis/ https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Graphical-Interfaces

## 🔻 pager (delta)

🗄️ `os/tools.md` pager

* set to use external tool via `git difftool -help` 📙 Chacon [2.54]
* _diff-so-fancy_: ✅ https://github.com/so-fancy/diff-so-fancy
* _delta_: ✅ https://github.com/dandavison/delta
* themes file https://dandavison.github.io/delta/custom-themes.html https://github.com/dandavison/delta/blob/main/themes.gitconfig
> don't understand why catpuccin relies on their bat theme https://github.com/catppuccin/delta can you just use straight from repo? https://raw.githubusercontent.com/catppuccin/delta/refs/heads/main/catppuccin.gitconfig
* ❓ diff colors https://gist.github.com/zachvalenta/a3666ef47d9489e515d78548e85f139e
* _diffnav_: ✅ obviated w/ lazygit https://github.com/dlvhdr/diffnav
* _diffview_: 🎯 neovim https://github.com/sindrets/diffview.nvim https://www.youtube.com/watch?v=aJikrPnTOtI
* _drft_: https://codeberg.org/nightsail/drft
* _dunk_: similar to delta https://github.com/darrenburns/dunk
* _git split diffs_: 🎯 node version https://github.com/banga/git-split-diffs https://news.ycombinator.com/item?id=27007844
* _riff_: 🎯 https://github.com/walles/riff

## 🐼 porcelain (lazygit)

LAZYGIT 📜 https://github.com/jesseduffield/lazygit https://git-how.com/
* sections: side panels + main panel / diffview https://git-how.com/
* all panel cmds: search `/` scroll `jk|JK` drill `ENTER|ESC` default action `SPACE` commit `c` commit using $EDITOR `C` push `P`
* main panel: toggle staged|unstage `TAB`
* stage: line `SPACE` stage hunk `a` stage all `a` (when in side panel) https://git-how.com/basics/staging
* working with multiple repos: status pain > `ENTER` repos https://github.com/jesseduffield/lazygit/issues/1071
* working with multiple repos: locking `state.yml` https://github.com/jesseduffield/lazygit/issues/4017
* working with multiple repos: check out gfold! https://github.com/nickgerace/gfold/issues/261
* readline for commit pane still pending https://github.com/jesseduffield/lazygit/issues/1712
> litecli allows emacs|vi readline

ALTERNATIVES
* _bit_: 💀 unmaintained, autcomplete https://github.com/chriswalz/bit
* _forgit_: good UI, for `gai`, no Vim keybindings https://github.com/wfxr/forgit#-features
* _gitu_: no Vim keybindings https://github.com/altsem/gitu
* _gitui_: 🎯 https://github.com/extrawurst/gitui
* _magit_: looks great, Emacs-only https://github.com/magit/magit https://emacsair.me/2017/09/01/magit-walk-through/ https://github.com/dandavison/delta/issues/194 https://github.com/dandavison/magit-delta
* _Neogit_: 🎯 magit port https://github.com/NeogitOrg/neogit
* _vimagit_: inspired by magit https://github.com/jreybert/vimagit
* _vim-fugitive_: 🎯 https://github.com/tpope/vim-fugitive https://www.youtube.com/watch?v=kFVjoIish0E https://gumroad.com/vimtricks https://github.com/TimUntersberger/neogit http://vimcasts.org/episodes/archive/ https://www.semicolonandsons.com/episode/IDE-like-refactors-snippets-tests-hover-docs-commenting-and-git 3:15 http://vimcasts.org/episodes/archive/ https://www.youtube.com/watch?v=F7JZdAwGmpU https://www.youtube.com/watch?v=vpwJ7fqD1CE https://nimbleind.gumroad.com/l/hsOVI

---

LAZYGIT
* go through all these https://github.com/jesseduffield/lazygit/wiki/Custom-Commands-Compendium
* BYO menu https://github.com/jesseduffield/lazygit/wiki/Custom-Commands-Compendium
> are people aware that this guy has written the de facto docs? https://git-how.com/
* config https://github.com/jesseduffield/lazygit/blob/master/docs/Config.md
* theme https://github.com/catppuccin/lazygit
* howto https://git-how.com/ https://www.youtube.com/watch?v=Ihg37znaiBo @ 2:30
* pager https://github.com/jesseduffield/lazygit/blob/master/docs/Custom_Pagers.md
* use for `git add .` commits, staging lines, nuking work tree https://www.youtube.com/watch?v=CPLdltN7wgE

## ⛳️ repo browser (Tig)

* _gitk_: can come with git but if not `brew install git-gui` https://git-scm.com/docs/gitk
* _grv_: 💀 unmaintained, no brew formula https://github.com/rgburke/grv https://github.com/rgburke/grv/issues/109
* _serie_: ✅ better UI than Tig https://github.com/lusingander/serie
* no date in commit description
* no diff in commit detail https://github.com/lusingander/serie/issues/53
* config fs: `.config/serie/config.toml` https://github.com/lusingander/serie?tab=readme-ov-file#config
* example config https://github.com/lusingander/serie?tab=readme-ov-file#config-file-format
* _Tig_: ✅ https://github.com/jonas/tig https://jonas.github.io/tig/doc/manual.html
* modes: main `m` diff `d` log `l` blame `b`; main view with message body https://github.com/jonas/tig/issues/1032
* all commits: `tig` in repo 
* file history: `tig path/to/file`
* blame: `tig blame path/to/file` https://stackoverflow.com/q/15304804 or tree view `t` then `b`
> binding to view full file https://www.youtube.com/watch?v=goNodOWENEg

## tracker (gfold / Atalanta)

there's some bullshit project squatting on the domain https://pypi.org/project/atl/

what I realized after 90 mins debugging gfold: it can only surface git repos that are subdirs of the paths you're specifying i.e you can't just give it paths to git repos. this is a problem bc it's not granular enough e.g. it will surface everything inside `capp` or `notes` https://github.com/nickgerace/gfold/issues/261

# 🏗️ WORKFLOW

---

📜 cmd https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config
* _add - chunks_: `add -p`

## branch

https://x.com/asbradbury/status/1804565477605458259

```sh
branch -a                     # list all on remote
co master -- my_dir/          # pull from master into feature branch https://stackoverflow.com/a/2364223

# REMOVE https://github.com/matt-harvey/git_curate
branch -d $BRANCH             # local, merged
branch -D $BRANCH             # local, unmerged
push origin --delete $BRANCH  # remote
```

---

* pull in files from another branch: `git checkout $BRANCH -- $PATH` https://stackoverflow.com/a/2364223

default
* _default branch_: branch against which PRs are raised https://docs.github.com/en/github/administering-a-repository/changing-the-default-branch
* typically main/master but can be anything https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup `sw/git/master-to-main-personal-site.md`
* set: `branch -M <name>`

* use current branch name in commit msg https://stackoverflow.com/a/2111099 `branch=$(git branch | sed -n -e 's/^\* \(.*\)/\1/p')`
* get current branch: `git rev-parse --abbrev-ref HEAD` https://stackoverflow.com/a/6245587

strategies
* _Gitflow_: https://news.ycombinator.com/item 
* _trunk based_: https://trunkbaseddevelopment.com/ https://dev.to/alediaferia/git-tips-for-trunk-based-development-1i1g
* Linux kernel and other email-based workflows https://stackoverflow.com/a/23108169/6813490 https://drewdevault.com/2020/08/27/Microsoft-plays-their-hand.html https://drewdevault.com/2024/12/10/2024-12-10-Daily-driving-jujutsu.html https://git-send-email.io/

---

* _everything on branch not on other branch_: `git cherry -v develop mybranch` https://stackoverflow.com/a/24668421 to master `git cherry -v master`
* _checkout previous_: `git checkout -`
* _switch to different commit on same branch_: `checkout <hash>`
* switch back: `checkout <urbranch>`
* split branch into repo https://stackoverflow.com/questions/40340194/git-how-to-split-a-branch-in-its-own-repository
* pull in branch name for script https://stackoverflow.com/a/2111099/6813490
* _sink_: https://learngitbranching.js.org/

## commit

🗄️ `doc.md` repo

MESSAGE
* msg components: subject/header, description
* _COMMIT EDITMSG_: tmp file storing commit msg
* fmt: subject 50 col, desc 72 col https://drewdevault.com/2019/02/25/Using-git-with-discipline.html automate https://github.com/commitizen/cz-cli

CONVENTIONAL COMMIT https://www.conventionalcommits.org/
* labels: lowers cognitive overhead = enables more frequent commits https://github.com/commitizen/cz-cli https://github.com/zachvalenta/interview-capp/commits/main/
* _add_: new func|test
* _fix_: fix incorrect func|test
* _tidy_: improve impl of src|test
* _doc_: add|improve documentation
```sh
src: add|tidy|fix
doc
dep
test
```
* tried out the Gum impl but didn't like loss of readline and didn't understand what scope was doing https://github.com/charmbracelet/gum
> 📍 gotta think Charm has a realine component somewhere
```sh
#!/bin/sh
TYPE=$(gum choose "func" "doc" "rf" "test")
# scope is optional so wrap in parens if it has a value
SCOPE=$(gum input --placeholder "scope")
test -n "$SCOPE" && SCOPE="($SCOPE)"
# pre-populate input with the type(scope) so user can update it
SUMMARY=$(gum input --value "$TYPE$SCOPE: " --placeholder "summary")
DESCRIPTION=$(gum write --placeholder "description")
# commit on confirm
gum confirm "commit changes?" && git commit -m "$SUMMARY" -m "$DESCRIPTION"
```

---

AI https://news.ycombinator.com/item?id=43454690

commits as documentation https://mislav.net/2014/02/hidden-documentation/
> https://github.com/SKalt/git-cc/
> https://github.com/muandane/goji
> https://gitmoji.dev/ https://github.com/juftin/browsr

MESSAGE https://github.com/cococonscious/koji
* `shortlog` should tell a story https://news.ycombinator.com/item?id=22518813
* how to https://drewdevault.com/2021/08/05/In-praise-of-Postgres.html
* prepopulate
```sh
# https://stackoverflow.com/a/53804934
git config commit.template <template_file.txt>
```

delete git push origin HEAD --force https://stackoverflow.com/questions/1338728/how-do-i-delete-a-commit-from-a-branch
* prepare message beforehand https://stackoverflow.com/a/20447988/6813490
* mv most recent msg: `commit --amend`; actually replaces with entirely new commit https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things
* mv n msgs: `rebase -i HEAD~commit_count` then replace `pick` w/ `reword` https://stackoverflow.com/a/7070976

* commit stacks https://engineering.fb.com/2022/11/15/open-source/sapling-source-control-scalable/ https://github.com/tummychow/git-absorb
* sign/verify https://www.youtube.com/watch?v=4166ExAnxmo
* _tilde_: refers to parent; w/ args refers to nth parent `HEAD~2` (two parents prior); w/out args defaults to most proximate parent i.e. `HEAD~1` https://stackoverflow.com/a/23714994
* _entry mode_: inline (`-m`) verbose (`-v`) https://github.com/so-fancy/diff-so-fancy/issues/365 [Chacon 2.54]
> be nice if there was a way to commit that combined `commit -v` (show diff) and `di` (show some previous messages)
* _checkout previous commit_: `checkout <commit>` enters 'detached HEAD state' (exit via `checkout - `); to actually do work based off old commit, better off creating branch `git checkout -b version2 <has>` https://git-scm.com/book/en/v2/Git-Basics-Tagging

update old
* _add changes_: `add <file>; commit --amend --no-edit` https://stackoverflow.com/a/40503483
* _update n prev msgs_: `rebase -i HEAD~num_of_commits` then use `reword` https://stackoverflow.com/a/7070976
* _rm previous commit_: `reset --hard <hash>`
* rewrite w/ amend/rebase https://www.youtube.com/watch?v=efJhX4SONVA

view https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History
* _specific commit_: `show <hash>` https://stackoverflow.com/a/7663506/6813490
* _all commits that touched file_: `git log --follow -- <file>` https://stackoverflow.com/a/8808453
* _change for commit_: diff `--patch` files and lines change `--stat`
* `--format`: msg description for single commit (`log --format=%B -n 1`) msg subj and desc `log --pretty=format:"%s %b"` https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History#pretty_format
* `--pretty`: oneline, short, full, fuller https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History
* filter out merges: `--no-merges`
* _date_: `--relative-date`, `--since=2.weeks`

* _sink_: https://chris.beams.io/posts/git-commit/ https://fatbusinessman.com/2019/my-favourite-git-commit https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html https://stackoverflow.com/a/40506149/6813490 https://drewdevault.com/2019/02/25/Using-git-with-discipline.html use file for Git commit https://stackoverflow.com/a/20438380/6813490 https://medium.com/@hugooodias/the-anatomy-of-a-perfect-pull-request-567382bb6067 https://news.ycombinator.com/item?id=23739633 https://til.simonwillison.net/git/backdate-git-commits

tags
* _tag_: way to label commits
* _use cases_: label release version https://softwareengineering.stackexchange.com/a/165731
* _types_: lightweight (just label on commit) annotated (itself a Git obj); can push only annotated tags to remote but not vice versa https://git-scm.com/book/en/v2/Git-Basics-Tagging
* _list_: `tag`
* _search_: `tag -l <glob>` https://git-scm.com/book/en/v2/Git-Basics-Tagging
* rm from local/remote https://git-scm.com/book/en/v2/Git-Basics-Tagging

## diff

* _modified_: `diff`
* _staged_: `--staged`/`--cached` [Chacon 2.53]
* _branches_: `diff <branch>..<branch>`
* _file across branches_: `diff <branch>..<branch> -- path/to/file` https://stackoverflow.com/a/4099805/6813490
* _commits_: `diff HEAD~2..HEAD`
* _LOC add/rm_: `git diff --numstat` https://stackoverflow.com/a/14879457/6813490
* no line numbers https://stackoverflow.com/a/24456418/6813490
* language-aware https://tekin.co.uk/2020/10/better-git-diff-output-for-ruby-python-elixir-and-more
* _sink_: https://www.atlassian.com/git/tutorials/saving-changes/git-diff 

## hooks

GIT HOOKS 📜 https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks https://githooks.com/
* BYO https://stefaniemolin.com/articles/devx/pre-commit/hook-creation-guide/
* https://rdrn.me/postmodern-python/
* actions: client-side (commit, merge) server (push)
* file-system location: `.git/hooks` 
* ignore failed hooks w/ `git commit --no-verify` http://omerkatz.com/blog/2013/2/15/git-hooks-part-1-the-basics

PRE-COMMIT https://pre-commit.com https://github.com/pre-commit/pre-commit/issues https://gitlab.com/zachvalenta/pre-commit-test https://learndjango.com/tutorials/pre-commit-django
* bypass for commit: `git commit -m "your message" --no-verify`
* bypass for push: `git push --no-verify`
* set: `pre-commit install -t pre-commit; pre-commit install -t pre-push` (i.e. copy Python scripts in place of Git samples) https://pre-commit.com/#3-install-the-git-hook-scripts https://pre-commit.com/#pre-commit-install
* skip: `SKIP=<stage> git commit -m "foo"`
* uninstall: `pre-commit uninstall -t <action>`
* conf: `.pre-commit-config.yaml`
* run in parallel, can cause random failures, run in serial using `require_serial = true` https://pre-commit.com/#hooks-require_serial
* official hooks: black handles `trailing-whitespace` and `end-of-file-fixer` https://github.com/pre-commit/pre-commit-hooks/tree/master/pre_commit_hooks https://www.youtube.com/watch?v=BzC3ft8rm4c
* pylint is a pain https://github.com/pre-commit/pre-commit/issues/266#issuecomment-399682269 black https://github.com/pre-commit/pre-commit-hooks/issues/356 https://github.com/psf/black#version-control-integration pytest 

```yaml
---
- repo: local  #  https://pre-commit.com/#repository-local-hooks https://github.com/pre-commit/pre-commit/issues/1245
  hooks:
  - id: lint
    stages: [commit]
    name: run lint
    entry: make lint
    language: system
    types: [python]
  - id: test
    stages: [push]
    name: run test
    entry: make test
    language: system
    types: [python]
```

## log

SEARCH https://www.youtube.com/watch?v=BaBKBy2vHmM
* `-- <file>` (commits that touched file)
```sh
log --grep $QUERY # header + message
log --grep $QUERY -p # header + message + patches
log --S $QUERY # src
log --S $QUERY --all # src across all branches
log --S $QUERY -- **/*.md # all Markdown
log --S $REGEX # regex
```

ZA
* all commits that touched LOC: `log -Lstart,end:path/to/file` https://stackoverflow.com/a/27108677
* overview of commits: `shortlog -sne`
* color fmt https://stackoverflow.com/questions/5889878/color-in-git-log https://git-scm.com/docs/git-config#Documentation/git-config.txt-color https://github.com/zachvalenta/bin-mini23/commit/5fba7f8e3d24a449e18287ba884619571340bea0

---

* _unmerged commits on current branch_: `git log master..sprint --oneline` https://stackoverflow.com/a/4649377
* _time_: during a month `--since="2008-10-01" --before="2008-11-01"`
* _msg_: `log --format=%B -n 1"`

* git log no merges and only current branch https://stackoverflow.com/a/4649377/6813490
🔗 https://zwischenzugs.com/2018/03/26/git-log-the-good-parts/

* graph https://stackoverflow.com/q/5382255/6813490
* _time_: `log --since=2.weeks`

* _search commit content_: `log -S <query>` https://stackoverflow.com/a/2928721/6813490
* _search commit content by file_: `log -S <query> -- <path/to/file>`

## merge

semantics
* three-way merge https://news.ycombinator.com/item?id=38222596
* conflict https://www.youtube.com/watch?v=HJtxQPJUcJc
* _merge_: interleave n commits 📙 Chacon 144
* _cherry pick_: put 1 commit onto tip of branch https://stackoverflow.com/a/9339460
* can always just merge other branch if it's only one commit ahead of master
* _rebase_: put n commits onto tip of branch https://stackoverflow.com/a/43551395 https://jvns.ca/blog/2023/11/06/rebasing-what-can-go-wrong-/
* interactive https://www.youtube.com/watch?v=H7RFt0Pxxp8
* can also use `squash` https://stackoverflow.com/q/2427238
* squash everything after certain commmit: `git rebase -i $LAST_COMMIT_YOU_DONT_WANT_TO_SQUASH`
```sh
d004585 (HEAD -> main, origin/main) the third and final commit I want to squash
831f811 another commit I want to squash
7d3b486 start of commits I want to squash
1dae68b another commit I want to keep
502f903 commit I want to keep

$ git rebase -i 1dae68b

pick 7d3b486 start of commits I want to squash
squash 831f811 another commit I want to squash
squash d004585 the third and final commit I want to squash
```
* my notes workflow: `git rebase -i main`
```sh
# https://stackoverflow.com/a/5340773

# main
git init
echo "hi" > ex.txt
ga
gc  # init

# feature
git nb feature
echo "hey" > feat.txt
ga
gc  # on feature

# master
echo "hola" > ex.txt
ga
gc   # on main

# before rebase
* 353382c (main) on main
| * dd8a610 (HEAD -> feature) on feature
|/
* 44496c2 init

# rebase
git rebase main

# after rebase
* 99f30ad (HEAD -> feature) on feature
* 353382c (main) on main
* 44496c2 init
```


scenarios
* squash commits on feature: `rebase -i main` (pick first commit)
* squash commits on master itself: `rebase -i $HASH_OF_FIRST_COMMIT` https://chatgpt.com/c/671ab992-0e84-8004-b938-6afdf084485b
* changes from master onto feature: `rebase main` https://medium.com/front-end-weekly/avoid-80-of-merge-conflicts-with-git-rebase-b5d755a082a6
> this calls into question the above definition of rebase insofar as commits from master go onto tip of feature *and then feature commits go after that*

---

scenarios
* fetch: 
* pull: 
* pull --rebase https://goiabada.blog/git-tricks-avoiding-merge-when-dealing-with-remote-conflicts-52c175e526e6 https://stackoverflow.com/questions/2472254/when-should-i-use-git-pull-rebase https://gitolite.com/git-pull--rebase

* use case is maintaining linear history https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase apparently the use case for why you'd want to rebase instead of merge becomes more clear if you understand directed acyclic graphs https://stackoverflow.com/a/9147389/6813490 use rebase to split up a commit https://github.com/thoughtbot/til/blob/master/git/split-up-a-commit.md rebase faster https://github.com/thoughtbot/til/blob/master/git/squashing-commits.md
* _grab file from another branch_: https://github.com/thoughtbot/til/blob/master/git/grab-a-file-from-another-branch.md

__how to__

* _squash feature already on remote_: `rebase -i develop; push --f` https://davidwalsh.name/squash-commits-git
* _put feature on master as single commit_: `rebase -i master; checkout master; merge <feature>` (irl open PR) https://stackoverflow.com/a/3697230/6813490 

* _rebase_: feature branch onto master as single commit  (everything in one commmit, but probably skip merging directly into master in favor of PR) `merge --squash my_feature` (still includes commit history) https://stackoverflow.com/a/3697263/6813490 more complex use case https://stefanoborini.com/beautiful-git-rebasing-of-version-branch/
* _squash_: everything on branch `git rebase --root -i` https://stackoverflow.com/a/9254257/6813490 could just blow away `.git` but would lose all other branches https://stackoverflow.com/a/1657287/6813490
```sh
$ echo "hey" > foo.txt  # 'first'
$ echo "hi" > foo.txt  # 'second'
$ echo "hello" > foo.txt  # 'third'

pick 80658a7 first  # have to squash newer commits into older ones i.e. pick the oldest commit and squash everything else https://stackoverflow.com/a/51516360/6813490 
squash a573038 second
squash c211c5b third
```

## remotes

📜 https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

* force pull
```sh
git fetch --all; git reset --hard origin/main
```

* initial push
```sh
git remote add origin git@github.com:$OWNER/$NAME.git
git push -u origin main
```

```sh
# rm branch from remote
push origin --delete $BRANCH
# get rid of remote branch that you've deleted
git fetch --prune
```

---

https://stackoverflow.com/a/2432799
```sh
# CREATE
remote add $NAME $URL  # defaults to `origin`
git remote add gl git@gitlab.com:zachvalenta/calendar.git

# READ
remote -v  # all
remote show $NAME  # single
$NAME/$BRANCH  # reference non-origin remote

# UPDATE
remote rename $OLD_NAME $NEW_NAME  # name
remote set-url $NAME git@$PROVIDER.com:$USER/$PROJECT.git  # URL
git remote set-url origin git@github.com:cappusa/product-categories.git
remote rm $NAME

git remote set-url origin git@github.com:zachvalenta/logs.git
git remote set-url gl git@gitlab.com:zachvalenta/logs.git
```

misc
* _upstream_: SSoT repo forked from w/ `remote -v show <repo` https://gist.github.com/Chaser324/ce0505fbed06b947d962 https://en.wikipedia.org/wiki/Downstream_(software_development)

push
* push to specific remote: `push <remote>`
* push specific branch: `push <branch>`
* push specific commit: `push <remote> <hash>:<branch>`
* _alias clone_: `clone <url> <alias>` https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository

---

* setup so you can pull sans args `push -u origin master` https://stackoverflow.com/a/18868188/6813490
* _branch - track_: `branch --set-upstream <local> <origin/remote`; think that `git checkout` from remote will automatically create local branch of same name already setup to track upstream
* _branch - check for changes_: `log origin/<branch>` https://stackoverflow.com/a/3278427/6813490
* _branch - view all_: `git branch -r`
* _log_: `log --no-merges HEAD..<remote>/<branch>`

## stash

CREATE
* interactive: `stash -p` https://stackoverflow.com/a/12421642
* single file: `stash -- <file>`
* single file + msg: `stash push -m "my msg" <file>` https://stackoverflow.com/a/55073847
* all + msg: `stash save "my msg"` https://dev.to/srebalaji/useful-tricks-you-might-not-know-about-git-stash-117e

VIEW
* list all: `stash list`
* show most recent: `stash show`
* show single: `stash show stash@{num}`
* show single - contents: `stash show -p stash@{num}`

USE https://dev.to/srebalaji/useful-tricks-you-might-not-know-about-git-stash-117e
* _apply_: use but don't rm from stack; specific `stash apply stash@{1}`
* _pop_: use and rm from stack; specific `stash pop stash@{1}`
* _drop_: rm from stack; specific `drop stash@{index}` all `stash clear`
* undo bad stash apply: `git checkout -f` https://stackoverflow.com/a/40446387

---

* worktree as alternative https://www.youtube.com/watch?v=IK_mjDqGUYE https://adamj.eu/tech/2023/10/04/boost-your-git-dx-out-now/ https://martinheinz.dev/blog/109

## undo

UNSTAGE
* single file: `reset HEAD $FILE` https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things
* all files: `reset` https://michaelsoolee.com/git-unstage-all/

* undo local commit: `git reset HEAD~` https://stackoverflow.com/a/927386
* undo updates to already staged file: `git restore $FPATH`

---

restore https://martinheinz.dev/blog/109 https://adamj.eu/tech/2023/10/04/boost-your-git-dx-out-now/
* restore deleted file: `git checkout HEAD <filename>`

🔗 https://wizardzines.com/zines/oh-shit-git/ https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things#_undoing https://git-scm.com/book/en/v2/Git-Internals-Maintenance-and-Data-Recovery#_data_recovery

* find deleted file https://devblogs.microsoft.com/oldnewthing/20240909-00
* rm tracked file: `rm --cached $FILE` 📙 Chacon [2.56-57] 

REPOSITORY
* ?: `reset --hard HEAD`
* rm most recent commit: `reset --hard HEAD~1`
```sh
# recover from screwing this up
git reflog
git reset --hard $SHA_FROM_COMMIT_YOU_JUST_NUKED
```
* rm most recent commit from remote: `git push origin +HEAD` https://stackoverflow.com/a/8225166/6813490
* mv most recent commit to index: `reset --soft HEAD~1`

STAGING AREA
* `git add .` is a bug magnet https://www.semicolonandsons.com/episode/how-to-make-less-mistakes-when-programming 2:20

THE PAST
* _blame_: https://github.com/casperdcl/git-fame
* _bisect_: search for bug https://drewdevault.com/2019/02/25/Using-git-with-discipline.html https://lchsk.com/debugging-with-git-bisect.html remove secrets from commit https://startcodingnow.com/removing-secrets-from-django-project-in-docke https://news.ycombinator.com/item?id=26567969
* _reflog_: find stuff you've deleted e.g. reset back a few commits but need something from one of the commits you've skipped past, reflog will help you find it http://gitready.com/intermediate/2009/02/09/reflog-your-safety-net.html ❓ so Git doesn't rm stuff it sends to a trash can https://news.ycombinator.com/item?id=34487201


---

* run background server to commit for you e.g. dura https://news.ycombinator.com/item?id=29784238
https://news.ycombinator.com/item?id=27579701
* revert to previous commit (if unpublished) `reset --hard <hash>` https://stackabuse.com/git-revert-to-a-previous-commit/
* reset modified files to working directory: `git checkout`

notas post-mortem
* outcome: messed up looking git log
* cause: `commit --amend --no-edit` on feature branch (`sprint`) and then merged to main
* work around: forked repo, then realized I could just create new `main` in existing repo bc `sprint` and `master` had always been aligned (my workflow was squashing `sprint` at week's end and merging that to `master`). so, spent a week working in a new repo and moving those file changes to old repo, and then at week's end, once I confirmed the git log looked better, just replaced new repo w/ old repo.

## workflow

* stage deleted file: `gai`

---

https://drewdevault.com/2019/02/25/Using-git-with-discipline.html
https://drewdevault.com/2020/04/06/My-weird-branchless-git-workflow.html
https://registerspill.thorstenball.com/p/how-i-use-git
* git flow, github flow, branching stategies https://www.alexhyett.com/git-flow-github-flow/

🗄
* merge
* `di`: one-step add and commit for single file 
* `ding`: same as `di` but for multiples files 
* `gr`: one-step hard reset 

PR 🗄 `pr-workflow.pdf`
* fork
* clone fork
* cut feature branch
* impl
* pull upstream (`pull https://github.com/<ORIGINAL_OWNER>/<ORIGINAL_REPOSITORY>.git <BRANCH_NAME>` https://help.github.com/en/articles/merging-an-upstream-repository-into-your-fork)
* run tests
* push to your remote
* open PR against upstream

* UM
```sh
git commit
git checkout master
git pull
git checkout -
git rebase master
git push
# To github.com:tommyboytech/t3.git
# ! [rejected]            ur-branch -> ur-branch (non-fast-forward)
# error: failed to push some refs to 'repo'
# hint: Updates were rejected because the tip of your current branch is behind
# hint: its remote counterpart. Integrate the remote changes (e.g.
# hint: 'git pull ...') before pushing again.
# hint: See the 'Note about fast-forwards' in 'git push --help' for details.
git pull
# fatal: Not possible to fast-forward, aborting.
git push -f  # https://stackoverflow.com/a/39400690
```
---

* https://zaiste.net/15-git-commands-you-may-not-know/ autocompletion https://git-scm.com/book/en/v1/Git-Basics-Tips-and-Tricks https://git-scm.com/book/en/v2/Appendix-A%3A-Git-in-Other-Environments-Git-in-Bash  https://apple.stackexchange.com/q/55875* https://stackoverflow.com/questions/33495152/enabling-auto-completion-in-git-bash-on-windows https://github.com/donnemartin/gitsome
* undoing - https://gitexplorer.com/ https://github.com/k88hudson/git-flight-rules https://ohshitgit.com/ https://cheat.readthedocs.io/en/latest/git.html https://www.youtube.com/watch?v=FdZecVxzJbk https://blog.github.com/2015-06-08-how-to-undo-almost-anything-with-git/ rm sensitive data from history https://dev.to/edmondso006/removing-sensitive-data-from-git-history-5g63 艘 Gith Guardian 
* pager https://github.com/dandavison/delta these are the config that diff-so-fancy updates https://github.com/so-fancy/diff-so-fancy#usage
* Nick J https://www.youtube.com/watch?v=S0_pOvrfN0U https://www.youtube.com/watch?v=IL1ktpzfT8E

* crd git workflow
```sh
git fetch --prune origin
git rebase -i --autosquash origin/master
git push -f origin crd/my-feature-branch
git checkout master
git merge origin/master
git merge origin crd/my-feature-branch
git push origin master
git push origin :crd/my-feature-branch
git branch -d crd/my-feature-branch
```

# 🟨 ZA

VERSION MGMT / INSTALL https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
* macOS: 10.9 onwards handled by Command Line Tools https://github.com/creationix/nvm#important-notes ❓ Homebrew install being used?
* Linux: `git-all`

---

`.gitattributes`: specify EOL https://stackoverflow.com/questions/73086622/is-a-gitattributes-file-really-necessary-for-git

SUBMODULES https://www.cyberdemon.org/2024/03/20/submodules.html
* _submodules_: `.gitmodules` separate Git repo w/in main repo https://news.ycombinator.com/item?id=42291833
* for pulling dependencies https://longair.net/blog/2010/06/02/git-submodules-explained/ https://github.com/sharkdp/bat/blob/master/.gitmodules https://www.youtube.com/watch?v=8Z4Cmhji_FQ https://www.youtube.com/watch?v=ZYq3NJnO08U https://www.youtube.com/watch?v=iv7WwDgyb0U https://www.youtube.com/watch?v=De8Bc1VxcGQ
* howto: add child dir to parent dir `.gitignore`, init new Git repo in child https://stackoverflow.com/a/4660048 🗄️ `denv/bin`
* my use case: sharing dev notes btw personal/work machines, just `.gitignore` subdir and make subdir it's own repo 🗄 `km.md` file system https://github.com/zachvalenta/test-biji https://github.com/zachvalenta/test-keji
```txt
* add `stem/dev` to gitignore
* rm `stem/dev` from git index
* rename remote
* repoint local to remote
* add dev to gitignore
* create new repo inside dev
* point local dev repo to remote
* update VS Code workspace
* rm previous test repos
* pull dev repo to work machine
* update Git notes
```

za
* file diff: `git diff --no-index <file1> <file2>` https://stackoverflow.com/a/54656539
* do code review before story starts https://calpaterson.com/wasting-time.html
* _patch_ https://github.blog/2023-01-17-git-security-vulnerabilities-announced-2
* _patch set_: diff btw files [Chacon 1.28] making patches more granular when staging, stashing https://stackoverflow.com/a/34610928 📍 add answer re: using GitUp
* _worktree_: check out separate branch into separate directory https://stackoverflow.com/a/31951225 https://huonw.github.io/blog/2020/04/worktrees-and-pyenv/
* can't add empty dir https://git.wiki.kernel.org/index.php/Git_FAQ#Can_I_add_empty_directories.3F don't deploy `.git` to PROD https://slashcrypto.org/2018/11/28/eBay-source-code-leak/

## config

🗄️ `protocols.md` INI
📜 https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

FILE LOCATION
> be nice to switch btw using bullet, not as nice to set in zprofile, but I'll settle for symlinks for now
* `$HOME/.gitconfig`
* `GIT_CONFIG_GLOBAL`: `export GIT_CONFIG_GLOBAL="/Users/zach/Documents/denv/dotfiles/git/diffnav.ini"`
* `GIT_CONFIG`

---

https://blog.gitbutler.com/how-git-core-devs-configure-git/
https://chatgpt.com/c/67141929-cb80-8004-86dc-201dc864fdad

* set based on repo https://utf9k.net/blog/conditional-gitconfig/
* _list_: `git config --list --show-origin` https://stackoverflow.com/a/2115116 might see dupes bc Git reads from all config files, with most local (e.g. repo-level) taking precedence
* _precedence_: repo-level (`.git/config`) user-level/global? (`~/.gitconfig`) system-level (`/etc/gitconfig`; don't touch)
* _rm attribute from config_: `git config --unset <attr>`
```sh
# update config from shell
git config           # local ($CWD/.git/config)
git config --user    # user (~/.gitconfig)
git config --system  # system
```

ALIASES 📜 https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases
* aliases in gitconfig or zprofile? https://github.com/zachvalenta/dotfiles-mini23/commit/ddecff7a70e14d7a545e4d9fc72837e1a378b203
* aliases split btw `.gitconfig` and `.bash_profile` 

GITIGNORE https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
* _user_: `~/.config/git/ignore`
* _repo_: `.gitignore`
* `/` interpolated as the root of your directory i.e. `/app/logs` will ignore anything in `/app/logs` but not, say, `/logs` (that is, a `logs` dir located in your root direct)
* this works recursively; [all subdirectories are affected as well](http://qr.ae/TU1tsk) i.e. any `logs` deeper inside `app/logs` will also be ignored
* `logs`, on the other hand, will ignore anything in *any* `logs` directory located *anywhere* in your project

## monorepo

🔍 keeping size down https://github.com/github/git-sizer

CONSIDERATIONS
* activity: thousands of commits / day
* perf: MS had a 300GB monorepo as of 2017, cloning Odoo takes ~7 minutes

---

* 📙 Thomas pragmatic programmer [142]
* GLFS for large files https://stackoverflow.com/a/38313259 people don't like GLFS https://news.ycombinator.com/item?id=34875020 diffing binary https://tech.marksblogg.com/git-track-changes-in-media-office-documents.html https://www.git-tower.com/blog/git-performance/
* sparse checkout, LFS https://martinheinz.dev/blog/109 https://www.git-tower.com/blog/git-performance/
* Deno https://docs.deno.com/runtime/fundamentals/workspaces/
* Madge https://blog.codepen.io/2023/01/25/398-devoops/
* https://news.ycombinator.com/item?id=42062074
* https://steinkamp.us/posts/2022-11-10-what-i-learned-at-stripe
* https://monadical.com/posts/from-chaos-to-cohesion.html
* https://jackevans.bearblog.dev/python-monorepo-tooling-with-pants/

## review

---

* dates with confidence % https://steinkamp.us/posts/2022-11-10-what-i-learned-at-stripe
> this is more about releases
* https://drewdevault.com/2022/07/25/Code-review-with-aerc.html
* https://drewdevault.com/2016/04/11/Please-use-text-plain-for-emails.html
* https://drewdevault.com/2018/07/02/Email-driven-git.html
* https://drewdevault.com/2022/04/01/git-snail-mail.html

## server

FORGES
* BYO https://github.com/honza/smithy
* avoid centralization https://gitlab.com/pdfgrep/pdfgrep/-/issues/36#note_2232721446
* _Bitbucket_: 💀 https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek
* _Codeberg_: Gitea for Europeans https://codeberg.org/ https://news.ycombinator.com/item?id=33234965 https://codeberg.org/a-j-wood/pv
* _Forgejo_: powers Codeberg, can self-host https://forgejo.org/
* _Gitea_: fork of Gogs https://gitea.io/en-us/ https://news.ycombinator.com/item?id=13296717
* now for-profit and licensing issues https://news.ycombinator.com/item?id=34011581
* _Gitlab_: selling soon https://news.ycombinator.com/item?id=42333052
* _Gitweb_: built-in GUI for server https://git-scm.com/book/en/v2/Git-on-the-Server-GitWeb
* _Gogs_: https://gogs.io/
* _soft-serve_: 🎯 https://github.com/charmbracelet/soft-serve https://www.youtube.com/watch?v=9xCwBdlo85g
* _SourceHut_: you signed up for an account to use their static site hosting https://git.sr.ht/~shulhan/gotp https://drewdevault.com/2018/06/05/Should-you-move-to-sr.ht.html

---

* https://gemini.nytpu.com/gemlog/2021-03-07.gmi
* admin setup: create bare repository, scp to server with Git installed, if devs on your team have ssh access to server you're set https://git-scm.com/book/en/v2/Git-on-the-Server-Getting-Git-on-a-Server
* user setup: add public key

* _bare repository_: only git data (`.git`) with no working directory i.e. no actual files https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols
* _snippets_: Gist, pastebin https://softwareengineeringdaily.com/2020/06/08/tilt-kubernetes-tooling-with-dan-bentley/ 46:45

AUTH
* identity: https://www.micah.soy/posts/setting-up-git-identities/ https://news.ycombinator.com/item?id=42233524
* store credentials using macos Keychain https://gist.github.com/nepsilon/0fd0c779f76d7172f12477ba9d71bb66 https://github.com/thoughtbot/til/blob/master/git/osx-keychain.md

protocols for data transfer https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration
* _local_: use own machine (or NFS mount) as remote
* _http_: smart version uses auth and allows writes, dumb version read-only and no auth; can cache user/pass using macos Keychain
* _ssh_: non-anonymous, need to futz with keys
* _Git_: daemon that comes packaged with Git, hard to set up, for reads only

* no auth: this is server dependent e.g. work servers prompt user/pw for public repos but Github/lab do not
```sh
# PUBLIC REPOS
git clone https://gitlab.com/zachvalenta/pre-commit-test  # ✅ yours
git clone https://gitlab.com/esr/microjson.git  # ✅ others

# PRIVATE REPOS
# error msg ("No such device or address") suggests resource doesn't exist (bc it doesn't, for your user)
git clone https://gitlab.com/zachvalenta/dummy-repo.git  # ❌ yours
git clone https://gitlab.com/pulphead/film-censorship.git  # ❌ others
```

GITLAB TOKENS AND KEYS https://gist.github.com/zachvalenta/d7187130c63c75aa7ea86465e82198ec 🗄 `gitlab-deploy-token.md` `python.md` libs/Git
|  type        | protocol | ownership     | scope | actions           | notes
| ------------ | -------- | ------------- | ----- | ---------------   | --------------
| access token | https    | user          | ?     | API, read, write  | https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#limiting-scopes-of-a-personal-access-token
| deploy token | https    | project/group | ?     | read              | https://docs.gitlab.com/ee/user/project/deploy_tokens/
| deploy key   | ssh      | service       | ?     | read, write       | https://docs.gitlab.com/ee/user/project/deploy_keys

* docs: https://docs.gitlab.com/ee/user/project/deploy_keys/#differences-between-deploy-keys-and-deploy-tokens
* deploy tokens belong to a project/group and also *seem* like they're only able to interact with the project/group to which they belong
|  type        | actions     | protocol | scoped to        | used for                                                           |
| ------------ | ----------- | -------- | ---------------- | ------------------------------------------------------------------ |
| deploy key   | read, write | ssh      | service          | clone repo to run build in CICD pipeline, merge feature branch     |
| deploy token | read        | https    | project or group | clone repo to run build in CICD pipeline                           |
| access token | read        | https    | user             | hit Gitlab API (get info on repo/group, download repo as tarball)  |

* CE used to only have deploy keys
* EE used to not have deploy token
```sh
# ACCESS TOKEN (personal, project)
# clone - needs to be enabled on server (e.g. didnt' work on corporate network)
git clone https://user_name:access_token@gitlab.com/zachvalenta/dummy-repo.git
# API - get repo stats https://stackoverflow.com/a/54383282
curl --header "PRIVATE-TOKEN: <access_token>" https://gitlab.com/api/v4/users/zachvalenta/projects

# DEPLOY TOKEN
git clone https://token_name:token@gitlab.com/zachvalenta/dummy-repo.git
```

GITLAB CICD
💻 https://gitlab.com/zachvalenta/pre-commit-test.git 
📜 https://docs.gitlab.com/ee/ci/yaml/ https://docs.gitlab.com/ https://docs.gitlab.com/runner/
* _job_: declarative series of steps
* _stage_: grouping mechanism for jobs e.g. test, deploy
* _pipeline_: collection of stages; can force manual interaction https://docs.gitlab.com/ee/ci/pipelines/index.html#add-manual-interaction-to-your-pipeline to run without, toggle off in project (visibility and merge requests)
* conditionals https://docs.gitlab.com/ee/ci/yaml/#rulesif
* _artifact_: static files produced by pipeline e.g. coverage report from tests
* generate report: `pytest --junitxml=report.xml` https://docs.gitlab.com/ee/ci/unit_test_reports.html#python-example
```yaml
# basic
unit_tests:
  image: python:3.7
  script:
    - "pip install -r requirements.txt"
    - "ln -sf .env.dev .env"
    - "pytest -v app_test.py"

# ref env var set via GL instance
ax2: "${ax2}"
```
