# ⛩️

## 参考

🛣️ https://roadmap.sh/aws
📊 https://console.aws.amazon.com/console/home
🩻 https://health.aws.amazon.com/health/status
📜 https://aws.amazon.com/documentation/ https://github.com/awsdocs
📻 https://podcast.cloudonaut.io/
📙 https://github.com/open-guides/og-aws
🔍 https://www.expeditedssl.com/aws-in-plain-english https://www.youtube.com/@BeABetterDev https://cloudonaut.io/tag/
📹 Brown ccp https://www.youtube.com/watch?v=NhDYbskXRgc

## 进步

> Lambda, API Gateway, SQS, SNS, DynamoDB, Aurora Serverless, and more. We don’t run a single server. - Stedi job posting

https://www.youtube.com/watch?v=jFrGhodqC08
* https://roadmap.sh/best-practices/aws
* Brown ccp @ 2:15:00
* https://www.aws.training/
* https://cloudonaut.io/my-mental-model-of-aws/ @ storage

* _17_: try out for Comcast interview

# 🤖 COMPUTE

CONTAINERS 🗄️ `containers.md`
* _ECS (Elastic Container Svc)_: run Docker containers on EC2, autoscales, can be used for jobs or service mesh https://www.youtube.com/watch?v=I9VAMGEjW-Q
* howto: Dockerfile, build image and put to ECR, define ECS task (how to start container, what ports to open, what to connect to)
* _Fargate_: serverless ECS
* _EKS_: managed Kubernetes https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html

DATA ENG 🗄️ storage / data eng
* _Athena_: how is this different than CloudSearch? https://docs.aws.amazon.com/athena/latest/ug/what-is.html
* _Data Pipeline_: ETL
* _CloudSearch_: search plaintext in S3/RDS; 类似 ElasticSearch
* _EMR_: Spark i.e. MapReduce over huge text files
* _Glue_: run ETL using Spark https://aws.amazon.com/blogs/aws/aws-glue-version-2-0-featuring-10x-faster-job-start-times-and-1-minute-minimum-billing-duration/

ZA
* _Elastic Beanstalk_: PaaS https://testdriven.io/blog/flask-elastic-beanstalk/
* _Elastic Transcode_: deal w/ video (fmt, compress)

CORPORATE
* _AppStream_: run Windows app and give remote access to
* _Directory Service_: Active Directory
* _WorkMail_: give employees a cal/email
* _Workspaces_: remote desktop
* _Service Catalog_: setup user perms for AWS services for employees
* _Storage Gateway_: S3 for corporate network

---

https://www.lastweekinaws.com/blog/why-your-cpu-based-utilisation-metric-is-absolute-nonsense/
https://www.lastweekinaws.com/blog/17-final-ways-to-run-containers/

* _scaling_: ElasticBeanstalk (autoconf mem) IaaS (set CloudWatch alert for cluster and add instances behind LB when load triggers alert)
* _Compute Engine_: EC2; compare prices https://ec2.shop/

## EC2

* sizing https://x.com/dvassallo/status/1154516923335376896
* log into instance by name https://github.com/jessebye/awser
* monitoring https://lp.datadoghq.com/rs/875-UVY-685/images/ec2_monitoring_cheatsheet.pdf
* _burstable_: autoscale https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances.html https://cloudonaut.io/my-mental-model-of-aws/
* _spot instance_: auctioned instances https://blog.codepen.io/2016/03/08/080-spot-instances/

---

https://www.lastweekinaws.com/blog/why-aws-might-be-the-next-backbone-provider/

## Lambda

💡 run scripts

> For example, I have a user service with several endpoints for user management...it became apparent that I would need to do http routing inside each of the Lambda functions. After some research I found out that the most popular approach is to use aws-lambda-go-api-proxy along with your favorite HTTP router like Gin or Chi. While this approach let’s you use a popular HTTP router, it comes with the overhead of converting the APIGatewayProxyRequest to http.Request, so that it can be processed by the router. Another good HTTP routing library I found is LmdRouter which works directly with the APIGatewayProxyRequest and doesn’t have the overhead of the conversion. The router implementation uses a hashmap to store the keys, however, matching a route to a handler is still O(n) where n is the number of routes. It iterates every route and uses a regex to match the path. Considering I wanted my lambda functions to execute as fast as possible to decrease request time and possibly reduce costs I started to wonder if I could do better. https://blog.dimitarandreev.com/posts/writing-an-http-router-for-aws-lambda-functions-from-scratch-with-go/

---

https://news.ycombinator.com/item?id=41941308

https://www.lastweekinaws.com/blog/aws-is-asleep-at-the-lambda-wheel/

https://docs.aws.amazon.com/lambda/latest/operatorguide/profile-functions.html

> It might be tempting to use Lambda & API Gateway to save $70/mo, but then you’re going to have to write your software to fit a new immature abstraction and deal with all sorts of limits and constraints. Basic stuff such as using a cache, debugging, or collecting telemetry/analytics data becomes significantly harder when you don’t have access to the server. But probably the biggest disadvantage is that it makes local development much harder. And that’s the last thing you need. I can’t emphasize enough how important it is that you can easily start your entire application on your laptop, with one click.  With Lambda & API Gateway you’re going to be constantly battling your dev environment. Not worth it, IMO. https://x.com/dvassallo/status/1154516910265884672

* https://github.com/zappa/Zappa
* _alternatives_: Zappa https://www.youtube.com/watch?v=Vl5wroVmSuk https://www.reddit.com/r/django/comments/psddt8/zappa_is_no_longer_maintained/ w/ db https://romandc.com/zappa-django-guide/
* _blueprint_: bootstrap e.g. canary (cron to hit site)
* _debug_: get function running in EC2 (uses the same AMZ Linux AMI)
* _dependencies_: must be less than 250MB (uncompressed) and 50MB (compressed)
* frameworks Sparta (Golang) Chalice (Python)
* _internals_: https://brandur.org/go-lambda
* _perms_: necessar for the other services you're integrating with
* _runtimes_: need custom for something like jq https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html
* _startup time_: can reuse the container the function runs in https://medium.com/capital-one-tech/best-practices-for-aws-lambda-container-reuse-6ec45c74b67e
* _Step Functions_: flowchart for Lambda
* _time limit_: 300 sec; workaround is chaining functions and using something else (S3) to persist in the meantime

# 🕸️ NETWORK

* _ENI (Elastic Network Interface)_: all traffic goes through this e.g. each EC2|RDS instance comes with https://cloudonaut.io/my-mental-model-of-aws/

SERVICES
* _API Gateway_: proxy so you can version, throttle bad traffic
* _CloudFront_: CDN https://alexkudlick.com/blog/ila-cloudfront/index.html
* _Firewall Manager_: manage multiple WAF
* _ELB_: load balancer; can do ALB, NLB, GLB
* _KMS_: password vault; handling keypairs https://www.tastycidr.net/using-aws-vault-with-linux
* _WAF_: firewall for Cloudfront https://aws.amazon.com/waf/ https://news.ycombinator.com/item?id=20570332

REGIONS https://awsnetwork.lastweekinaws.com https://benjdd.com/aws/
* _region_: collection of AZ http://cloudping.bastionhost.org/en/
* factors: svc, cost, distance to users 📹 Brown ccp [2:12:45]
* svc by region; != every feature of a svc is available https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
* some svc are global (CloudFront, S3) 📹 Brown ccp [1:30:10]
* `us-east-1` the original region, billing and cost only show up here 📹 Brown ccp [1:29:50]
* `us-west-1` has fewer svc/features and costs more https://www.lastweekinaws.com/blog/us-west-1-the-flagship-aws-region-that-isnt

---

* https://grahamlyons.com/article/everything-you-need-to-know-about-networking-on-aws

REGIONS
* https://www.lastweekinaws.com/blog/my-mental-model-of-aws-regions/
* _availability zone (AZ)_: 
* _local zone (LZ)_: https://aws.amazon.com/about-aws/whats-new/2024/04/aws-local-zones-honolulu-hawaii/ https://www.lastweekinaws.com/blog/us-west-1-the-flagship-aws-region-that-isnt
* _ACM_: certificates
* _GovCloud_: regions for gov https://www.lastweekinaws.com/blog/its-extremely-likely-you-should-not-use-govcloud/

* WAF, SSRF https://ejj.io/blog/capital-one https://news.ycombinator.com/item?id=20560594 https://wafris.org/
* egress, Cloudfare https://news.ycombinator.com/item?id=28707317

## Route53

---

* https://terminaltrove.com/dns53/
* = DNS
* https://stackoverflow.com/questions/51452111
* https://github.com/cloudkj/scar

__setup Route 53 as DNS service__: copy zone file to AWS, copy DNS info from AWS to DNS provider
* add zone file
```
Error parsing zone file: Error in line 1: no owner (encountered after 0 correct records) In line: @ 3601 IN SOA parkingpage.namecheap.com.
```
* add `$origin example.com.` to first line 
https://ubuntuforums.org/showthread.php?t=1216801 
https://hathaway.cc/2011/02/how-to-import-bind-zone-files-into-amazon-route-53/
```
Error parsing zone file: Unsupported directive: $origin
```
* add `@origin example.com.` to first line http://shon.github.io/2014/12/21/dns_migration_story.html
```
Error parsing zone file: Error in line 1: Invalid type 'example.com.' (encountered after 0 correct records) In line:@origin example.com.
```
* add `$ORIGIN www.zjayv.com` to first line, rm white space from each line --> WORKS!

__other options if that doesn't work__ 
* remove white space from beginning of each line
* add TTL thing to second line
* try cli53
* ask Stack Overflow

https://www.youtube.com/watch?v=W4FPZ29Trpw
https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/migrate-dns-domain-inactive.html
https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html
http://shon.github.io/2014/12/21/dns_migration_story.html
http://blog.alfredcalayag.com/development/2015/03/02/personal-site-hosted.html
https://www.youtube.com/watch?v=D6qB7MEFOe0

## VPC

💡 makes it appear as if all of your AWS services are on the same little network instead of being small pieces in a much bigger network.

* _NACL_: network ACL; don't need if using security group https://cloudonaut.io/my-mental-model-of-aws/ https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
* _Flow Logs_: logging within VPC https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html

---

* route table https://cloudonaut.io/my-mental-model-of-aws/
* _security group_: firewall; whitelist IPs your services can connect to (and vice versa) https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html
* https://www.verypossible.com/blog/aws-development-dark-art-of-vpc-networking
* https://dev.to/davidk01/aws-and-gcp-networking-differences-1fb1 https://twitter.com/paulg/status/1408442886023176198

# 🧳️ STORAGE

DATA ENG 🗄️ compute / data eng
* _Redshift_: data warehouse https://tech.marksblogg.com/billion-nyc-taxi-rides-redshift.html
* _Snowball_: like having a hard drive for import/export to/from AWS

ZA
* _DMS_: db migrations
* _DynamoDB_: NoSQL https://www.freecodecamp.org/news/ultimate-dynamodb-2020-cheatsheet/ https://github.com/guregu/dynamo
* _Elasticache_: 类似 Redis

---

data transfer https://www.lastweekinaws.com/blog/aws-data-transfer-charges-ingress-actually-is-free/

## RDS

* _RDS_: DBaaS; dbms on top of EC2 but w/ backups/updates for free (vs. doing yourself)
* supports Aurora + others
* snapshots https://aws.amazon.com/blogs/database/programmatic-approach-to-optimize-the-cost-of-amazon-rds-snapshots/
* OSS alternative https://github.com/Vonng/pigsty
* _parameter group_: config for RDS https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html

---

* _RDS_:  https://www.lastweekinaws.com/blog/running-relational-databases-on-aws/
* _Aurora_: dbms; can migrate from/to MySQL/Postgres; fastest growing service
* RDS but https://www.lastweekinaws.com/blog/aurora-vs-rds-an-engineers-guide-to-choosing-a-database/ https://softwareengineeringdaily.com/2022/10/05/open-source-serverless-postgres/ http://blog.cleverelephant.ca/2019/07/aws-aurora.html https://www.lastweekinaws.com/blog/no-aws-aurora-serverless-v2-is-not-serverless/

## S3

DESIGN
* FTP server
> Objects were popular at the time and S3 was labelled an object store, but everyone really knows that S3 is for files. S3 is a cloud filesystem, not an object-whatever. https://calpaterson.com/s3.html
> S3 isn't a regular file system, it's a distributed object storage service with an API https://tech.marksblogg.com/minio-aws-s3-hdfs.html

TOOLING
* create creds https://github.com/simonw/s3-credentials
* TUI viewer https://github.com/lusingander/stu
* find misconfigured buckets https://github.com/sa7mon/S3Scanner

ZA
* logging: none by default but can do with CloudTrail or S3 Server Access Logging https://medium.com/@maciej.pocwierz/how-an-empty-s3-bucket-can-make-your-aws-bill-explode-934a383cb8b1
* you used to get charged for 400 requests https://medium.com/@maciej.pocwierz/how-an-empty-s3-bucket-can-make-your-aws-bill-explode-934a383cb8b1 https://aws.amazon.com/about-aws/whats-new/2024/05/amazon-s3-no-charge-http-error-codes/
> So, if I were to open my terminal now and type: `aws s3 cp ./file.txt s3://your-bucket-name/random_key` I would receive an AccessDenied error, but you would be the one to pay for that request. And I don't even need an AWS account to do so.
* _Glacier_: S3 but cheaper in exchange for higher latency
* _MinIO_: https://tech.marksblogg.com/minio-aws-s3-hdfs.html

---

alternative https://pinata.cloud/
https://github.com/s3tools/s3cmd https://tech.marksblogg.com/website-cdn-with-pelican-and-s3cmd.html
https://blog.plerion.com/things-you-wish-you-didnt-need-to-know-about-s3/

FILE
* _block_: mount to instance, 1 clients; EBS can be snapshot, instance volume is default and temporary
* _file_: mount to instance, n clients
* _object_: don't mount to instance, used by n clients
* _EBS_: attachable storage for EC2; can be snapshot
* _EFS_: like S3 but mimics filesystem (slower bc file locked over wire vs. OS calls) https://blog.codepen.io/2017/05/09/129-projects-infrastructure/

* https://www.lastweekinaws.com/blog/s3-as-an-eternal-service/
* https://www.lastweekinaws.com/blog/s3-is-not-a-backup/
* https://www.lastweekinaws.com/blog/s3-intelligent-tiering-breaking-even-on-cost/
* https://www.lastweekinaws.com/blog/s3-encryption-at-rest-does-not-solve-for-bucket-negligence/
* _S3_: obj storage
* not as file system https://calpaterson.com/s3.html
* S3 bucket viewer https://terminaltrove.com/stree/ https://github.com/juftin/browsr https://github.com/lusingander/stu
* file client https://news.ycombinator.com/item?id=35155944
* Backblaze as alternative https://news.ycombinator.com/item?id=26427333
* scale https://news.ycombinator.com/item?id=36894932 https://www.allthingsdistributed.com/2023/07/building-and-operating-a-pretty-big-storage-system.html
* _bucket_: holds obj https://www.youtube.com/watch?v=Ia-UEYYR44s 15:50
* don't have to work about file systems or disk space https://www.youtube.com/watch?v=Ia-UEYYR44s 14:50
* can take 0.5 million RPS https://www.dataengineeringpodcast.com/upsolver-data-lake-database-administrator-episode-135/ 13:30
* client https://github.com/Miserlou/NoDB https://github.com/s3tools/s3cmd
* https://medium.hostux.net/@maciej.pocwierz/how-an-empty-s3-bucket-can-make-your-aws-bill-explode-934a383cb8b1
* https://news.ycombinator.com/item?id=30371604
* _block-level storage_: hard drive aaS e.g. AWS EBS for db backups

tighten perms for S3 buckets
* domains: www.zjayv.com, zjayv.com, zvtest1234
* yolo perms I used at the time
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": {
        "AWS": "*"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::zjayv.com/*"
    }
  ]
}
```

# 🟨 ZA

* _ARN_: ID for resource https://everythingdevops.dev/what-is-amazon-resource-name-arn/

CODE
* _CodeCommmit_: Github
* _Code Deploy_: mv code from CodeCommmit to EC2
* _CodePipeline_: CICD

DEPLOYMENT
* https://cloudonaut.io/aws-velocity-series/
* _CodeArtifact_: https://aws.amazon.com/about-aws/whats-new/2024/04/aws-codeartifact-rubygems/
* _CodeCatalyst_: https://aws.amazon.com/about-aws/whats-new/2024/05/amazon-codecatalyst-file-commit-history/?ck_subscriber_id=512830619

MOBILE SVC
* _Cognito_: OAuth
* _Device Farm_: mobile testing across device types
* _SNS_: Twilio (push notifications) https://github.com/nikoksr/notify https://github.com/caronc/apprise https://github.com/fonoster/fonos
> An area where there’s unavoidable complexity for us is with telecom integrations. In theory, we would use a SaaS SMS provider for everything, but the major SaaS SMS provider doesn’t operate everywhere in Africa and the cost of using them everywhere would be prohibitive. The earlier comment on how the compensation cost of engineers dominates the cost of our systems wouldn’t be true if we used a SaaS SMS provider for all of our SMS needs; the team that provides telecom integrations pays for itself many times over. https://danluu.com/simple-architectures/

## certification 

🔗
* https://www.aws.training/Account/Profile/Basic
* https://www.reddit.com/r/AWSCertifications/
* https://www.exampro.co/ https://tutorialsdojo.com/
* questions https://www.youtube.com/watch?v=8zsdpwvTxos

CERTS
* _cloud practioner (CCP/CLF-C02)_: replaced CLF-C01 in 2024 https://www.pluralsight.com/resources/blog/cloud/new-aws-clf-c02-exam0
* _dev associate_: CP++, same level as SA https://aws.amazon.com/certification/certified-developer-associate/
* _solutions architect associate (SA)_: 🎯 https://aws.amazon.com/certification/certified-solutions-architect-associate/
* _solutions architect professional_: SA++ https://news.ycombinator.com/item?id=12198316
* _data eng associate_: 🎯 https://aws.amazon.com/certification/certified-data-engineer-associate https://news.ycombinator.com/item?id=27580134 https://www.pluralsight.com/cloud-guru/courses/aws-certified-data-engineer-associate-dea-c01-data-security-and-governance https://www.pluralsight.com/cloud-guru/courses/aws-certified-data-analytics-specialty-das-c01 https://www.pluralsight.com/cloud-guru/courses/aws-certified-devops-engineer-professional-dop-c02 https://www.pluralsight.com/cloud-guru/courses/aws-certified-database-specialty-dbs-c01
* _db speciality_: 📹 Brown ccp [5:00]
* _machine learning speciality_: https://aws.amazon.com/certification/certified-machine-learning-specialty https://medium.com/@adam.dejans/my-path-to-passing-the-aws-machine-learning-certification-e8fc45ad7762 https://skillbuilder.aws/exam-prep/machine-learning-specialty https://www.udemy.com/course/aws-machine-learning/?couponCode=ST2MT43024 https://www.pluralsight.com/cloud-guru/courses/aws-certified-machine-learning-specialty-mls-c01

ZA
* show on your LinkedIn https://www.linkedin.com/in/joshua-kelley-058b284a/ https://www.linkedin.com/posts/derhabicht_aws-certified-developer-associate-was-issued-activity-7190907898024071169-186-
* job board https://iq.aws.amazon.com/

## IaC

> The fourth stage managing cloud infrastructure is "clicking around in the web console, then lying about it." I call it "ClickOps." https://www.lastweekinaws.com/blog/clickops/

* _CDK_: script (Python, Golang) https://docs.aws.amazon.com/cdk/v2/guide/home.html
* complaints: https://www.lastweekinaws.com/blog/the-cdks-most-fundamental-flaw-is-fixable/ https://www.lastweekinaws.com/blog/9-ways-aws-cdk-headdesk/
* _CloudFormation (CFN)_: JSON/YAML; Terraform for AWS
> If something is likely to be static, it’s a good candidate for CFN. Ex: VPCs, load balancers, build & deploy pipelines, IAM roles, etc. If something is likely to be modified over time, then using CFN will likely be a big headache. Ex: Autoscaling settings. I like having a separate shell script to create things that CFN shouldn’t know about. And for things that are hard/impossible to script, I just do them manually. Ex: Route 53 zones, ACM cert creation/validation, CloudTrail config, domain registration. https://x.com/dvassallo/status/1154516910265884672
* _System Initiative_: https://www.systeminit.com/ https://github.com/systeminit/si https://nickgerace.dev/posts/system-initiative-the-second-wave-of-devops/

---

* latency https://www.stedi.com/blog/relative-performance-tradeoffs-of-aws-native-provisioning-methods
* list resources https://github.com/jckuester/awsls
* https://github.com/PaulleDemon/AWS-deployment
* clean up old resources https://github.com/genevieve/leftovers https://github.com/rebuy-de/aws-nuke https://github.com/servian/aws-auto-cleanup https://github.com/gruntwork-io/cloud-nuke
* _Config_: track overall AWS setup

## IAM

SEMANTICS https://stackoverflow.com/a/51888634/6813490
* _account_: ID, alias
* _user_: operator w/ permanent credentials
* _role_: user w/ tmp credentials
* _credentials_: pw, access key, secret key
* _group_: collection of users
* _policy_: JSON doc of perms; resource (S3) action (read) effect (bool)

POLICY
* _Root_: sometimes customer service will only deal with root https://security.stackexchange.com/a/211698
* _Administrator_: root but cannot close account, rm root https://security.stackexchange.com/a/211698
* _PowerUser_: Administrator but can't do IAM

---

* https://cloudonaut.io/aws-security-primer/
* https://news.ycombinator.com/item?id=39714155

LEAST PRIVILEGE
* root https://docs.aws.amazon.com/IAM/latest/UserGuide/root-user-tasks.html
* create admin account and use that instead of root; it's root and then everyone else https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html
* give someone scoped access to account https://kevinslin.com/aws/aws_account_access_policies
* https://github.com/Netflix/repokid https://netflixtechblog.com/introducing-aardvark-and-repokid-53b081bf3a7e
* users default principal of least-permission
* https://www.spaceblocks.cloud/blog/hello-world
* SSO https://www.lastweekinaws.com/blog/the-trials-and-travails-of-aws-sso/ https://www.lastweekinaws.com/blog/taking-aws-account-logins-for-granted/
* secret mgmt https://www.lastweekinaws.com/blog/handling-secrets-with-aws/

* _access key_: public key 💻 `~/.aws/config` https://github.com/Fullscreen/aws-rotate-key
* _secret access key_: private key
* _account ID_: https://www.lastweekinaws.com/blog/are-aws-account-ids-sensitive-information/

can access across accounts? https://cloudonaut.io/my-mental-model-of-aws/
internal accounts https://www.lastweekinaws.com/blog/the-aws-service-i-hate-the-most/
* _Cognito_: https://www.lastweekinaws.com/blog/the-strange-too-familiar-tale-of-uncle-suitcase/
* _SCP_: https://cloudonaut.io/my-mental-model-of-aws/

## interfaces

CLI
* https://hackingthe.cloud/aws/general-knowledge/aws_cli_tips_and_tricks/
* _CloudShell_: in-broswer shell as alternative to CLI https://aws.amazon.com/blogs/aws/aws-cloudshell-command-line-access-to-aws-resources/
* _saws_: official CLI + autocomplete https://github.com/donnemartin/saws 
* _aws-shell_: official CLI https://github.com/awslabs/aws-shell 
* eventually consistent https://cloudonaut.io/my-mental-model-of-aws/
* config: `~/.aws/config`
```sh
aws configure  # ~/.aws/config
```

LIBS
* query w/ SQL https://github.com/turbot/steampipe https://www.hytradboi.com/2022/how-to-query-almost-everything https://github.com/stackql/stackql
* _LocalStack_: run AWS locally https://github.com/localstack/localstack https://www.lastweekinaws.com/blog/localstack-why-local-development-for-cloud-workloads-makes-sense/
* _boto3_: Python lib for AWS https://realpython.com/python-boto3-aws-s3/
* _Moto_: mock resources https://github.com/spulec/moto https://news.ycombinator.com/item?id=34070272 

## messaging

QUEUE
* _Eventbridge_: route events btw AWS services https://cloudonaut.io/versus/messaging/eventbridge-vs-msk/
* _SNS_: pub sub 🔗 `amqp.md`
* _SQS_: queue; Postgres impl https://github.com/CoreDB-io/coredb/tree/main/extensions/pgmq https://github.com/poundifdef/SmoothMQ https://github.com/zillow/python-sqs-logging-handler
* API-based queue - you publish to an SQS queue and you consume from the queue https://stackoverflow.com/a/60543786
* _SWF_: SQS + logic
* _SES_: email https://testdriven.io/blog/sending-confirmation-emails-with-flask-rq-and-ses/

KAFKA
* _MSK (Managed Streaming Kafka)_: take away operations overhead of running Kafka
* don't need to worry about patching infra, storage performance, monitoring replication across AZ https://www.youtube.com/watch?v=5yMzTwumD_g 3:20
* can also manual deploy Kafka https://aws.amazon.com/blogs/big-data/best-practices-for-running-apache-kafka-on-aws/
* removing brokers used to bring the whole cluster down https://aws.amazon.com/blogs/big-data/safely-remove-kafka-brokers-from-amazon-msk-provisioned-clusters/
* _Kinesis_: AWS Kafka https://engineering.statefarm.com/blog/comparison-of-aws-services-for-event-driven-architecture/
* used for high throughput data ingestion

| FACTOR             | MSK             | EVENTBRIDGE   |
|--------------------|-----------------|---------------|
| pricing            | per broker      | per msg       |
| protocol           | Kafka           | REST          |
| persistance        | forever         | awhile        |
| delivery guarantee | can config      | at least once |
| integrations       | Lambda          | all AWS       |
| encryption         | rest, transit   | rest, transit |

## telemetry

https://cloudonaut.io/aws-monitoring-primer/
status page https://www.lastweekinaws.com/blog/status-paging-you/

* _User Notifications_: 
* _log driver_: sw that stores your logs e.g. awslogs, Splunk https://stackoverflow.com/questions/58001403/how-to-get-all-logs-from-an-ecs-cluster https://stackoverflow.com/questions/58001403/how-to-get-all-logs-from-an-ecs-cluster https://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_awslogs.html
* getting logs from AWS ECS service (at UM just forwarded to Datadog) https://stackoverflow.com/q/58001403/6813490
* _Cloudwatch_: alerts for services
* almost everything sends logs to CloudWatch https://cloudonaut.io/my-mental-model-of-aws/
* e.g. if Lambda throws error then raise alarm https://www.youtube.com/watch?v=lHWrAAzoxJA
* e.g. if ECS Kafka consumer writes log then forward to Datadog
* _CloudTrail_: logging
* _Inspector_: 🎯 security scan
* _OpsWorks_: 🎯 auto-scaling
* _X-Ray_: trace HTTP req through n services https://www.freecodecamp.org/news/pass-the-aws-developer-associate-exam-with-this-free-16-hour-course/
