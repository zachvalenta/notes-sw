# ⛩️

## 参考

## 进步

* test heatmap https://threedots.tech/post/go-test-parallelism/
* literate testing, literate programming https://simonw.substack.com/p/video-scraping-using-google-gemini
* start here https://github.com/okken/cards

* _24_: rf + approaches (fuzz, mutation, property-based)
* _20_: pre-commit for Git hooks, behave for bdd
* _19_: switch to pytest
* _18_: exposure to coverage and Git hooks, course on unit testing in Python
* _17_: integration test suite using Selenium
* _16_: basics at Zip Code

# 🧪 APPROACHES

## BDD

* origins: RSpec, Cucumber https://martinfowler.com/bliki/GivenWhenThen.html https://martinfowler.com/bliki/BusinessFacingTest.html
* _step_: line of human readable text corresponding to step definition (code)
* _scenario_: collection of steps
* _feature_: collection of scenarios
* keywords: given (preconditions) when (start) and (intermediate steps) then (assertion)
* be declarative, not imperative https://wiki.saucelabs.com/display/DOCS/Best+Practice%3A+Imperative+v.+Declarative+Testing+Scenarios
```text
# THIS
Given I am on the Login Page
When I sign in with correct credentials
Then I should see a welcome message

# NOT THIS
* Given I open a browser
* And I navigate to http://example.com/login
* When I type in the username field bob97
* And I type in the password field F1d0
* And I click on Submit button
* Then I should see the message Welcome Back Bob
```

## formal methods (TLA+)

---

https://buttondown.com/hillelwayne/archive/tla-from-first-principles/
https://news.ycombinator.com/item?id=41866752
https://buttondown.com/hillelwayne/archive/how-to-convince-engineers-that-formal-methods-is/
https://buttondown.com/hillelwayne/archive/the-seven-specification-ur-languages/
https://buttondown.com/hillelwayne/archive/what-could-be-added-to-tla/
https://buttondown.com/hillelwayne/archive/an-idea-for-teaching-formal-methods-better/
https://buttondown.com/hillelwayne/archive/what-if-the-spec-doesnt-match-the-code/
https://buttondown.com/hillelwayne/archive/strings-do-too-many-things/
https://buttondown.com/hillelwayne/archive/planning-vs-model-checking/
https://buttondown.com/hillelwayne/archive/what-does-tla-mean-anyway/
https://buttondown.com/hillelwayne/archive/some-thoughts-on-good-spec-properties/
https://buttondown.com/hillelwayne/archive/formal-methods-cant-fix-everything-and-thats-okay/
https://buttondown.com/hillelwayne/archive/the-best-model-checker-is-your-head/

https://en.wikipedia.org/wiki/TLA%2B
https://nchammas.com/writing/how-not-to-die-hard-with-hypothesis
https://en.wikipedia.org/wiki/Automated_theorem_proving
smt https://en.wikipedia.org/wiki/Satisfiability_modulo_theories https://github.com/philzook58/knuckledragger

* _formal methods_: use algebra for testing instead of all possible values; aka automated reasoning
> Automated-reasoning tools can be incredibly fast, even when the domains are infinite (e.g., unbounded mathematical integers rather than finite C ints). Unfortunately, the tools may answer "Don’t know" in some instances.
```c
// QUESTION: could f ever return false?
bool f(unsigned int x, unsigned int y) {
   return (x+y == y+x);
}

// ALGEBRA PROOF: that x + y = y + x -> f always returns true

// TESTING PROOF: call f on all possible pairs of values of the type unsigned int
// UINT_MAX typically 4B = 20 quintillion f calls to consider = need 1500 years
void main() {
   for (unsigned int x=0;1;x++) {
      for (unsigned int y=0;1;y++) {
         if (!f(x,y)) printf("Error!\n");
         if (y==UINT_MAX) break;
      }
      if (x==UINT_MAX) break;
   }
}
```

* characterization, snapshot, golden-master https://news.ycombinator.com/item?id=23268911

TLA+
* https://buttondown.email/hillelwayne/archive/a-very-brief-intro-to-formal-methods-aka-my-job/ https://www.hillelwayne.com/post/why-dont-people-use-formal-methods/ https://www.learntla.com/introduction/ https://lamport.azurewebsites.net/tla/tla.html https://medium.com/@bellmar/introduction-to-tla-model-checking-in-the-command-line-c6871700a6a2 Pact, contract testing https://www.thoughtworks.com/radar/tools?blipid=202110074 https://colorsofcode.ghost.io/counting-sheeps-with-contracts-in-python/ Jepsen https://news.ycombinator.com/item?id=38525968&utm_term=comment https://tratt.net/laurie/blog/2024/what_factors_explain_the_nature_of_software.html

## fuzz

* provide random input, see what breaks https://www.fuzzingbook.org/ https://github.com/ffuf/ffuf https://github.com/google/atheris https://blog.burntsushi.net/projects/ https://github.com/ffuf/ffuf https://bitfieldconsulting.com/golang/bugs-fuzzing
> generally used to test software that parses complex inputs that follow a particular format, protocol, or are otherwise structured...from a security standpoint, fuzzing is also used to uncover security vulnerabilities in programs that parse inputs from untrusted sources (e.g. the internet). Fuzzing for long periods without any bugs being reported increases the confidence in the stability of the code. However, no amount of Fuzzing can guarantee an absence of bugs in the code...fuzzing is a good candidate for some classes of software, especially ones that include networking protocols, file formats, and query languages. These software classes require input to follow a strictly defined format adhering to the specifications defined in an RFC/IETF, a standard, formal grammar, or finite state machine. https://dgraph.io/blog/post/continuous-fuzzing-with-go/
* cousin to chaos engineering https://en.wikipedia.org/wiki/Chaos_engineering
> Google runs Disaster Recovery Training annually (DiRT) where security teams are tasked with simulating these "black swan" events. Seems like this practice needs to expand to more industries. https://news.ycombinator.com/item?id=34149340
* https://packagemain.tech/p/fuzzing-http-services-golang

## mutation

* change src and see if tests detect https://github.com/mutpy/mutpy
> Mutation testers modify (mutate) your project code in small ways, then run your test suite. If the tests all pass, then that mutation is considered a problem: a bug that your tests didn’t catch. The theory is that a mutation will change the behavior of your program, so if your test suite is testing closely enough, some test should fail for each mutation. If a mutation doesn’t produce a test failure, then you need to add to your tests. There are a few problems with this plan. The first is that it is time-consuming. Most people feel like it takes too long to run their entire test suite just once. Mutation testers run the whole suite once for each mutation, and there can be thousands of mutations. But my larger concern is false positives: not all mutations are bugs, and if the mutation tester reports too many non-bugs as bugs, then its usefulness is diminished or even negated. https://nedbatchelder.com/blog/201903/mutmut.html
* seems like just coverage? https://blog.scottlogic.com/2017/09/25/mutation-testing.html https://rachelcarmena.github.io/2017/09/01/do-we-have-a-good-safety-net-to-change-this-legacy-code.html

## property-based

* test case doesn't use example data (supplied by engineer) but random data (based on type) https://florian-dahlitz.de/blog/test-your-python-code-using-hypothesis
> Of course, you can write more tests to test both functions with different values or even parametrize your tests. However, in the end, you test both functions using predefined values. Writing tests using a property-based testing library like Hypothesis is different. Here, you specify the types you are testing against and the way the software should work or behave. The library then generates random values in accordance with the specified types to actually test the functions. Thereby, you won't miss edge cases as they are tested once in a while. https://florian-dahlitz.de/articles/test-your-python-code-using-hypothesis
> At its simplest, property-based testing is the inverse of normal unit testing. Instead of providing some amount of data and a transformation so the computer can assert a property, you provide a property and a transformation, so the computer can provide some data. https://bytes.yingw787.com/posts/2021/02/02/property_based_testing/
> Testing-by-example (as opposed to property-based testing) is based on the programmer coming up with examples of inputs and asserting that when given those inputs the program produces the right outputs - or at least - the right sort of outputs. https://calpaterson.com/against-database-teardown.html
```python
# UNIT TESTING - YOU PROVIDE THE DATA
def test_addOne():
    assert addOne(5) == 6

# PROPERTY TESTING - YOU JUST MAKE THE ASSERTION
@given(st.integers())
def test_addOne(_input):
    assert addOne(_input) == _input + 1
```

ZA
> If we have a function that operates on data and have a hard time figuring out what to test, hypothesis is a great library that can help. Rather than explicitly state the exact objects you want to run through a test, hypothesis generates examples of inputs that follow certain properties you define. https://www.peterbaumgartner.com/blog/testing-for-data-science/
* https://nchammas.com/writing/how-not-to-die-hard-with-hypothesis
* https://github.com/pandera-dev/pandera
* https://pandera.readthedocs.io/en/stable/hypothesis.html#hypothesis 
* https://increment.com/testing/in-praise-of-property-based-testing/
* https://datascience.blog.wzb.eu/2019/11/08/property-based-testing-for-scientific-code-in-python/
* https://www.youtube.com/playlist?list=PLP1DxoSC17LZTTzgfq0Dimkm6eWJQC9ki
* https://www.hillelwayne.com/post/property-testing-complex-inputs/
* using API schemas https://www.youtube.com/watch?v=1lo7idI7uq8
* https://github.com/schemathesis/schemathesis
* https://www.youtube.com/watch?v=uN6JjpzVsAo&list=PL2Uw4_HvXqvYk1Y5P8kryoyd83L_0Uk5K&index=71
* https://nchammas.com/writing/how-not-to-die-hard-with-hypothesis
* https://semaphoreci.com/blog/property-based-testing-python-hypothesis-pytest
* https://github.com/flyingmutant/rapid

# 🕳️ INTEGRATION

* _golden file_: reference for tests covering src that has large text output https://chatgpt.com/c/672a6850-7af0-8004-abe9-710f95ad83da https://lucapette.me/writing/writing-integration-tests-for-a-go-cli-application/

IDEAS
* functional? https://terrastruct.com/blog/post/functional-testing-with-your-database-in-go/
* _testing external resources_: use real thing, use Docker version https://github.com/schireson/pytest-mock-resources/ https://yanglinzhao.com/posts/test-elasticsearch-in-django
* use actual deps instead of mocks https://testcontainers.com/ https://news.ycombinator.com/item?id=39531536 microcontainers https://github.com/maelstrom-software/maelstrom https://github.com/maelstrom-software/maelstrom
* spin up db in docker, run migrations, run integration tests; alternately, use CTEs https://news.ycombinator.com/item?id=34603691 https://news.ycombinator.com/item?id=34603244
* don't teardown db btw test runs
> Better yet, when your tests don't assume they're starting from a clean sheet, you can run your tests with a dump from production loaded into your database. This can help confirm that data access patterns you're using will work when the database, as a whole, is at production size. https://calpaterson.com/against-database-teardown.html

## API

---

* generate test suite from spec https://kusho.ai/
* https://www.youtube.com/watch?v=qquIJ1Ivusg
* synthetic https://docs.datadoghq.com/synthetics/
* mocking API = faster test runs but highe chance of rot; tooling (json-server, duckrails) https://github.com/SpectoLabs/hoverfly
* replay: https://github.com/kevin1024/vcrpy https://github.com/hiredscorelabs/cornell
> use case: day #0 run suite w/ VCR and create cassette file day #1 run test suite and use cassette files instead of hitting third-party service (to make your tests run faster, to avoid false negatives e.g. latency/downtime from service, internet is down, etc.)
* testing object store (S3) https://www.sanjaysiddhanti.com/2020/04/08/s3testing/ https://www.youtube.com/watch?v=NBICMF0i4Ok

LOAD TESTING
* _load testing_: send many requests at system
* https://github.com/hatoo/oha https://github.com/nakabonne/ali https://github.com/tsenart/vegeta https://github.com/wg/wrk https://github.com/giltene/wrk2 https://news.ycombinator.com/item?id=35781728 https://github.com/grafana/k6 https://github.com/fcsonline/drill
* https://github.com/wfxr/rlt
* _locust_: 📜 https://docs.locust.io/en/stable/ CLI + via code https://github.com/locustio/locust https://github.com/rednafi/stress-test-locust 🗄 `htmx-demo`
* alternatives
* config: num concurrent users, spawn rate (new users per second)
* telemetry: save as CSV https://docs.locust.io/en/stable/retrieving-stats.html
* 📍 telemetry: TPS, RPS, response (p50, p95) https://github.com/locustio/locust/wiki/FAQ#increase-my-request-raterps RPS https://docs.locust.io/en/stable/increase-performance.html#increase-performance-with-a-faster-http-client
> Interpreting performance test results is quite complex (and mostly out of scope for this manual), but if your graphs start looking like this, the target service/system cannot handle the load and you have found a bottleneck. When we get to around 9 users, response times start increasing so fast that even though Locust is still spawning more users, the number of requests per second is no longer increasing. The target service is “overloaded” or “saturated”. If your response times are not increasing then add even more users until you find the service’s breaking point, or celebrate that your service is already performant enough for your expected load.
```python
pip install locust
locust --headless --users 10 --spawn-rate 1 -H http://your-server.com # CLI https://docs.locust.io/en/stable/quickstart.html#direct-command-line-usage-headless
poetry run locust -f locustfile.py --headless -t 10s -u 5 -r 1 --host "http://127.0.0.1:5002" # CLI + LOCUSTFILE https://docs.locust.io/en/stable/running-without-web-ui.html#running-without-the-web-ui
# LOCUSTFILE
from locust import HttpUser, task
class HelloWorldUser(HttpUser):
    @task
    def hello_world(self):
        self.client.get("/hc")
```

## browser

* friction logs https://steinkamp.us/posts/2022-11-10-what-i-learned-at-stripe

---

* visual diff https://css-tricks.com/video-screencasts/178-percy-catches-visual-changes-in-any-workflow/
* view user flow, Chrome recorder panel https://developer.chrome.com/docs/devtools/recorder/ https://www.thoughtworks.com/radar/tools?blipid=202203004
* capture disappearing element https://stackoverflow.com/a/38783090/6813490
* cross browser https://www.browserling.com/

BROWSER AUTOMATION
* _Cypress_: https://github.com/cypress-io/cypress
* _Puppeteer_: https://github.com/puppeteer/puppeteer https://switowski.com/blog/web-automation/
* _Selenium_: https://github.com/SeleniumHQ/selenium
* _Playwright_: https://github.com/microsoft/playwright-python https://talkpython.fm/episodes/show/368/end-to-end-web-testing-with-playwright https://www.sakisv.net/2024/08/tracking-supermarket-prices-playwright/ https://til.simonwillison.net/playwright/testing-tables

## db

🗄
* `db.md` migrations
* `django.md` migrations
* `src.md` application config

---

https://jackevans.bearblog.dev/auto-rollback-database-transactions-with-flask-sqlalchemy-and-pytest/
* _dummy data_: fake/seed data for development https://github.com/zachvalenta/flask-CRUD/blob/master/db_seed.py https://github.com/joke2k/faker#providers https://mimesis.name/ https://mockaroo.com/ https://github.com/Qovery/replibyte
* _synthetic data_: real data but anonymized https://softwareengineeringdaily.com/2021/02/16/synthetic-data-with-ian-coe-andrew-colombi-and-adam-kamor/ https://gretel.ai/blog/what-is-synthetic-data https://github.com/GreenmaskIO/greenmask

https://www.semicolonandsons.com/
* lots of test data https://gogognome.nl/how-to-write-tests-that-need-a-lot-of-data.html https://sqlfordevs.com/fill-table-test-data

approaches
* anonymous https://news.ycombinator.com/item?id=40443927 https://github.com/nucleuscloud/neosync
* seed https://tla.wtf/posts/django-seed-db/ https://sqlfordevs.com/fill-table-test-data
* get subset of data for testing https://github.com/Wisser/Jailer
* clone https://github.com/postgres-ai/database-lab-engine
* db as normal and eat the speed costs https://changelog.com/podcast/145 https://corecursive.com/045-david-heinemeier-hansson-software-contrarian/ 48:00
* speed up by disabling `fsync` (system call to write to disk) bc you don't care if the data is actually written to disk https://pythonspeed.com/articles/faster-db-tests/ http://aosabook.org/en/nosql.html https://www.mongodb.com/docs/manual/reference/glossary/#std-term-fsync
* db in container https://github.com/orlangure/gnomock https://www.dudley.codes/posts/2020.10.02-golang-docker-integration-tests/ https://github.com/testcontainers https://www.thoughtworks.com/radar/languages-and-frameworks?blipid=201911027 https://www.youtube.com/watch?v=sNg0bnMF_qY
> Imagine you have some application code that opens a connection to a Postgres database and queries some customer data. The customary way to test this code would be to create a test database and populate it with test customer data. However, what if application code modifies rows in the database, like removing customers? If the above code runs on a modified database, it may not return the expected customer. Therefore, it's important to reset the state of the database between test cases so that tests behave predictably. But connecting to a database is slow. Running queries is slow. And resetting the state of an entire database between every test is really slow. Various mocking libraries are another alternative to using a test database. These libraries intercept calls at some layer of the application or data access stack, and return canned responses without needing to touch the database. The problem with many of these libraries is that they require the developer to manually construct the canned responses, which is time-consuming and fragile when application changes occur. copyist includes a Go sql package driver that records the low-level SQL calls made by application and test code. When a Go test using copyist is invoked with the "-record" command-line flag, then the copyist driver will record all SQL calls. When the test completes, copyist will generate a custom text file that contains the recorded SQL calls. The Go test can then be run again without the "-record" flag. This time the copyist driver will play back the recorded calls, without needing to access the database. The Go test is none the wiser, and runs as if it was using the database. https://github.com/cockroachdb/copyist
* testing writes http://eradman.com/posts/database-test-isolation.html
* broken connection https://neilkakkar.com/test-database-connection-django.html

# 🟨 ZA

SOURCE CODE
* _production code_: app itself
* _SUT_: prod code + env + collaborators + fixture/factory 🗄 `db.md` migration
* _collaborator_: system deps e.g. db, cache, server

TEST CODE
* _test code_: code testing app
* _case_: smallest unit of test code
* generate https://www.unit-test.dev/ https://github.com/randoop/randoop https://www.reddit.com/r/Python/comments/63e7sm/automated_test_case_generation/ https://github.com/usagitoneko97/klara https://github.com/tjkendev/python-testcase-generator https://eli.thegreenplace.net/2014/04/02/dynamically-generating-python-test-cases https://github.com/se2p/pynguin
* _suite_: collection of cases
* _runner_: run tests, reports results; BYO https://www.destroyallsoftware.com/screencasts/catalog
* aka harness https://stackoverflow.com/a/11628329/6813490

TEST TYPES
* _unit test_: test on a method; runs in memory; some people consider smallest unit as including db https://calpaterson.com/against-database-teardown.html
* _integration test_: uses IO (fs, network), db, another app; two flavors (API-only, UI + API)
* _smoke test_: integration that tests something basic
* _regression test_: prod data

## doubles

---

https://pythonspeed.com/articles/faster-db-tests/

https://pycon-archive.python.org/2024/schedule/presentation/26/index.html

* _mock_: override method so you can test; `unittest.mock` vs. `pytest.monkeypatch` https://www.b-list.org/weblog/2020/feb/03/how-im-testing-2020/ mock vs. magicmock https://stackoverflow.com/questions/17181687/mock-vs-magicmock https://realpython.com/python-mock-library/ https://joshpeak.net/posts/2019-06-18-Advanced-python-testing.html env var https://adamj.eu/tech/2020/10/13/how-to-mock-environment-variables-with-pytest https://www.b-list.org/weblog/2023/dec/08/mock-python-httpx/
* mocks https://github.com/tommyboytech/t3/pull/11146/files https://testing.googleblog.com/2013/05/testing-on-toilet-dont-overuse-mocks.html
* https://blog.cleancoder.com/uncle-bob/2014/05/14/TheLittleMocker.html

TAXONOMY https://blog.thea.codes/my-python-testing-style-guide/
* _double_: replace dependencies to isolate SUT e.g. "assume API is working, does my code work?" https://nedbatchelder.com/text/test3/test3.html#51 + 53, 56, 56
* _stub_: hard-coded answer; if double returns value it should be a stub https://www.quora.com/Software-Testing-What-is-the-difference-between-Mocks-and-Stubs
* _fake_: 类似 stub but w/ impl (still diff than real impl); common fakes incl. db, fs, server; verified fake https://pythonspeed.com/articles/verified-fakes/
* _mock_: 类似 fake but record what calls were made https://nedbatchelder.com/text/test3/test3.html#61

__terms__

* _spy_: 类似 mock but can view post-mortem

* _why use?_ prevent unit tests from becoming integration tests; isolation i.e. don't let test of A break bc A's call to B failed i.e. test one thing at a time
* _dummy object_: when you have to pass in something for a required argument; `fun(a=real_obj,b=None)`

https://nedbatchelder.com//blog/201908/why_your_mock_doesnt_work.html

📰  https://stackoverflow.com/questions/3459287/whats-the-difference-between-a-mock-stub https://martinfowler.com/articles/mocksArentStubs.html https://nedbatchelder.com//blog/201908/why_your_mock_doesnt_work.html https://blog.cleancoder.com/uncle-bob/2014/05/14/TheLittleMocker.html

🗣 mocking promotes unnecessary abstraction http://250bpm.com/blog:86

* https://www.quora.com/Software-Testing-What-is-the-difference-between-Mocks-and-Stubs
* https://blog.pragmatists.com/test-doubles-fakes-mocks-and-stubs-1a7491dfa3da
* https://stackoverflow.com/questions/3459287/whats-the-difference-between-a-mock-stub/51998394#51998394

## design

SPEED https://gumroad.com/l/suydt
* fast to slow: autofmt, lint, unit tests, integration tests https://pythonspeed.com/articles/slow-tests-fast-feedback/ https://pythonspeed.com/articles/slow-tests-fast-feedback/
* run relevant tests first https://pythonspeed.com/articles/slow-tests-fast-feedback/
* _test splitting_: parallelize https://devblog.kogan.com/blog/django-test-splitting-on-circleci
* slow = time waste = less testing https://pythonspeed.com/articles/high-cost-slow-tests/

APPROACHES
* _test last_: write code -> write tests
* _test first_: design tests -> write code -> write tests
* _TDD_: (write some code -> write a test) * ∞
* _BDD_: README-driven

---

* test shape / distribution https://martinfowler.com/articles/2021-test-shapes.html
* testing as just another form of feedback, along with production error logs, user response https://softwareengineeringdaily.com/2019/08/28/facebook-engineering-process-with-kent-beck/
* people don't take testing seriously https://news.ycombinator.com/item?id=26156924
* one assertion per test case
* super specific method names
* write tests for the code you wish you had, write tests that aren't more trouble than they're worth https://lukeplant.me.uk/blog/posts/test-smarter-not-harder/
* testing pyramid http://blog.codepipes.com/testing/software-testing-antipatterns.html more integration than anything else https://kentcdodds.com/blog/write-tests https://www.semicolonandsons.com/episode/continuous-integration-testing-basics-and-what-to-test
* settings create exponential increase in test cases https://www.youtube.com/watch?v=glZ1C-Yu5tw
* there's no way to re-write something that isn't tested without losing functionality https://danluu.com/julialang/
* tests are the only docs that don't rot https://return.co.de/blog/articles/why-you-should-start-using-junit-5/
* everything that's not tested will break https://return.co.de/blog/articles/everything-not-tested-will-break/
* tests are about design (if the src is britter so, too, the tests) https://www.openmymind.net/Tests-Are-About-Design/
* writing tests takes time, debugging without them takes more
* coverage https://corecursive.com/066-sqlite-with-richard-hipp/ as a treemap https://github.com/nikolaydubina/go-cover-treemap
> I’d been doing some work for Rockwell Collins, an avionics manufacturer, Rockwell Collins, and they introduced me to this concept of DO-178B. It’s a quality standard for safety-critical aviation products, and unlike so many quality standards, this one’s actually readable. Now, it does have a lot of bureaucratic stuff in it, but you can actually buy a copy of this. You do have to buy it. It’s a couple hundred dollars, but it’s a reasonably thin volume and you can read through it, and with sufficient study you can understand what they’re talking about, so I did that, and I actually started following some of their processes, and one of the key things that they push is, they want 100% MCDC test coverage. That’s modified condition decision coverage of the code. Your tests have to cause each branch operation in the resulting binary code to be taken and to fall through at least once.
> It’s pretty easy to get up to 90 or 95% test coverage. Getting that last 5% is really, really hard and it took about a year for me to get there, but once we got to that point, we stopped getting bug reports from Android.
> How do you count tests? We’ll have a test case but it’ll be parametrized, so that one test case might run 100, 1,000, 100,000 tests, just by looping, by changing one of the parameters. For a typical release, we’ll do billions of tests, but we have, I think it’s on the order of 100,000 distinct test cases. Yes, so we’ll do billions of tests.
>  There is a huge difference between covering all lines and covering all code path permutations. You can have 100% code coverage and still have bugs. https://twitter.com/kamranahmedse/status/1070773424644083712
