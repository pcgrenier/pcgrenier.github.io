---
layout: post
title: "Apache Nifi Release 0.6.0 Highlights"
date: 2016-07-12 02:25:08 +0000
comments: true
sharing: true
published: true
footer: true
description: Nifi release 0.6.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.6.0, Apache Nifi Release 0.6.1, Nifi Release 0.6.1
categories: [Apache Nifi, Release]
---

Apache Nifi release 0.6.0 and 0.6.1 recently and I wanted to go throught and highlight some of the key changes that may affect you Nifi users.  So far Nifi has kept pretty well to thier 6 week release schedule that they have discussed.  That's a really agressive release schedule so we'll see if they can keep that up once they hit the 0.7.0/1.0.0 release, which they say is going to actually be pushed back a little.  The 0.6.0 release was again substantial with 52 bug fixes, 15 improvements and 7 new features.  0.6.1 didn't take to long to follow with 11 bug fixes and 1 improvement.  The release binaries are on the [Apache Nifi download page](https://nifi.apache.org/download.html)The full release notes are avaialble on [Apaches Nifi's wiki page](https://cwiki.apache.org/confluence/display/NIFI/Release+Notes#ReleaseNotes-Version0.6.1).  The combined 0.6.* release information is below.

* [Bug Fixes](#bugfixes): 			63
* [Improvements](#improvements): 	16
* [New Features](#new-features): 	7

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
So many bug fixes, yet again! Even though Apache Nifi has not released a major version, Apache Nifi is going strong and fixing those annoying issues.  There are quite a few bug fixes that resolve issues with Apache Nifi Processors, which is great since these are the main part of nifi; PutKafka, InferAvroSchema, GetHttp, ControlRate, PutElsaticSearch, GetKafka, ListFile, SplitText, all had fixes!  And this just touches on some of the bug fixes.  If you really want to see if a specific bug fix was completed, you can check [here](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12334372), but really no need, just reset assured the bugs are getting fixed!

### <a name="improvements"></a>Improvements
The big improvements in this release are proxy support for the AWS Processors and RouteText to use Nifi Expression Language to route lines.  The other improvements are pretty good too, but mostly under the covers, for example ListHDFS to set the correct state in Zookeeper.

### <a name="new-features"></a>New Features
Let's get straight to them, new features an new processors:

* Processors for Apache [Cassandra]({{site.url}}/apache-nifi-processors/#PutCassandraQL)
* Kerberos authentication
* [PublishJMS Processor]({{site.url}}/apache-nifi-processors/#PublishJMS)
* [ConsumeJMS Processor]({{site.url}}/apache-nifi-processors/#ConsumeJMS)
* [AWS Lambda Processor]({{site.url}}/apache-nifi-processors/#PutLambda)

That's pretty much it.  To see all processors, checkout our [processor page]({{site.url}}/apache-nifi-processors/) which lists all current processors and their descriptions.  Check back after next release for a quick break down!