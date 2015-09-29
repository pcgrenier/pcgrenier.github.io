---
layout: post
title: "Apache Nifi Release 0.3.0 highlights"
date: 2015-09-29 01:17:47 +0000
comments: true
sharing: true
published: true
footer: true
description: Nifi release 0.3.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.3.0
categories: [Apache Nifi, Release]
---

Apache Nifi released their third release, [0.3.0](https://nifi.apache.org/download.html) since graduating to a TLP.  It was a minor release but still included a descent number of changes.

* [Bug Fixes](#bugfixes): 			56
* [Improvements](#improvements): 	20
* [New Features](#newfeatures): 	5

Release Highlights according to nifi can be found on their [confluence page](https://cwiki.apache.org/confluence/display/NIFI/Release+Notes#ReleaseNotes-Version0.3.0), but are also listed below.

* Performance improvements in handling large volumes of small files.
* Performance improvements in Provenance repositories.
* Added Reporting Task for ApacheTM AmbariTM.
* Improved stability of nifi bootstrap.
* Added Processors for working with images.
* Support for interacting with Kerberos enabled Hadoop clusters
* Added additional Avro capabilities - merging datafiles & converting to json
* Added processors for performing INSERT, UPDATE, DELETE statements against relational databases

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
The bug fixes in this version are plenty.  Quite a few were related to the management of a nifi instance, the starting and stopping and how the nifi.sh script works.  It's good to see that all parts of the code are getting worked on and not just the core nifi framework.  There were also quite a few fixes dealing with some of the current processors, most notably GetSFTP, GetFTP, GetKafka, GetTwitter, EncryptContent, ExecuteSQL, ExecuteFlumeSource, and the Nifi Spark Receiver.  Processor fixes are great since they are the major part of the flow!

### <a name="improvements"></a>Improvements
The 20 improvements is a gain substantial considering the quick turn around between release 0.2.1 and 0.3.0.  Documentation was updated which is always good, both the admin guide and user guide.

### <a name="new-features"></a>New Features
New features are always the exciting stuff that you've been waiting for, and if you were waiting for Apache Flume support, this might just be the release for you!  The 5 new features are listed below:

* Add processors that can run Apache Flume sources/sinks
* Create reporting task to deliver metrics to Apach Ambari
* Add location bounding box filter to twitter processor
* Create a NAR for handling images
* Kerberos support for Hadoop processors

As always, new features are warmly welcomed.  It's great to see the incorporation of more Apache projects into Apache Nifi processors, with both Flume and Ambari processors being included in this release.

The next release, 0.4.0, has 90 issues currently in [Jira](https://issues.apache.org/jira/browse/NIFI/fixforversion/12333070/?selectedTab=com.atlassian.jira.jira-projects-plugin:version-issues-panel).  I'm not completely sure if Nifi has settled on firm release dates or not, but I imagine this one should be out in a month or two, if anything by the end of the year.

The full list of release notes can be found on [Apache Nifi's Jira](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12329653)  This release is available through Nifi's site [download's section](https://nifi.apache.org/download.html), along with their previous releases.

We've missed a few of Nifi's releases, 0.2.0-incubating and 0.2.1 since they graduated but hopefully will continue to give you a break down of Nifi releases as they come!