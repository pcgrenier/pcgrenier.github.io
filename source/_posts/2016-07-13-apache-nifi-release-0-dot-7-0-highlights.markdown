---
layout: post
title: "Apache Nifi Release 0.7.0 Highlights"
date: 2016-07-13 02:07:13 +0000
comments: true
sharing: true
published: true
footer: true
description: Nifi release 0.7.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.7.0, Apache Nifi Release 0.7.0
categories: [Apache Nifi, Release]
---

Apache Nifi's newest release is out, 0.7.0.  You can grab the binaries from [their site](https://nifi.apache.org/download.html) as always.  So lets dive in and see what to look for in this release!

* [Bug Fixes](#bugfixes): 			72
* [Improvements](#improvements): 	49
* [New Features](#new-features): 	10

As always, a bunch of bug fixes, but this time there are quite a few improvements.

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
Where to begin!  This release has the second most bug fixes we've seen.  Again, there are a ton to cover so take a peak at the full [release notes](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12335078) if you want to see more, since this is just a quick highlight.  Lots of processor fixes - NullPointerException to non-responsive processors, a few nifi startup fixes, and other fixes such as fixing OS specific issues, looking at you Windows bugs.  UI interaction was fixed when many HDFS and HBase processors were on the graph.  Bug fixes are hard to highlight, since they are so user specific for what you might have run into, but it is nice to know that reported bugs are getting fixed.

### <a name="improvements"></a>Improvements
I didn't know where to start for Bug fixes, but really don't know where to begin for Improvements.  I'll start by saying there are a few new processors that they included in this section, but I'm going to list in the New Features below to remain consistent.  Other actual improvements were updates to HTTP Processors to allow proxy authentication which I know I saw someone on here asked about, so it's nice to see that it is now doable!  You are now able to use SSL with AMQP processors.  ExecuteScript processors can now be executed concurrently too.  Performance improvements in StreamScanner, SSL for the mongo processors, and the Mock framework can now register FlowFile Assertions.

It's good to mentiont that new documentation has been created for an in depth dive for developers, with Nifi and it's design decisions.  This is a great read and I will try to do a quick 

### <a name="new-features"></a>New Features
A few new processors here, but outside of that Apache Nifi now supports custom properties in the Expression Language.

New Processors:

* [ConsumeKafka]({{site.url}}/apache-nifi-processors/#ConsumeKafka)
* [ConsumeMQTT]({{site.url}}/apache-nifi-processors/#ConsumeMQTT)
* [DebugFlow]({{site.url}}/apache-nifi-processors/#DebugFlow)
* [DeleteDynamoDB]({{site.url}}/apache-nifi-processors/#DeleteDynamoDB)
* [ExtractMediaMetadata]({{site.url}}/apache-nifi-processors/#ExtractMediaMetadata)
* [GetDynamoDB]({{site.url}}/apache-nifi-processors/#GetDynamoDB)
* [GetHDFSEvents]({{site.url}}/apache-nifi-processors/#GetHDFSEvents)
* [GetSNMP]({{site.url}}/apache-nifi-processors/#GetSNMP)
* [JoltTransformJSON]({{site.url}}/apache-nifi-processors/#JoltTransformJSON)
* [ListenLumberjack]({{site.url}}/apache-nifi-processors/#ListenLumberjack)
* [ListS3]({{site.url}}/apache-nifi-processors/#ListS3)
* [PublishKafka]({{site.url}}/apache-nifi-processors/#PublishKafka)
* [PublishMQTT]({{site.url}}/apache-nifi-processors/#PublishMQTT)
* [PutDynamoDB]({{site.url}}/apache-nifi-processors/#PutDynamoDB)
* [PutHiveQL]({{site.url}}/apache-nifi-processors/#PutHiveQL)
* [PutSlack]({{site.url}}/apache-nifi-processors/#PutSlack)
* [PutTCP]({{site.url}}/apache-nifi-processors/#PutTCP)
* [PutUDP]({{site.url}}/apache-nifi-processors/#PutUDP)
* [SelectHiveQL]({{site.url}}/apache-nifi-processors/#SelectHiveQL)
* [SetSNMP]({{site.url}}/apache-nifi-processors/#SetSNMP)

Most of these could be seen in the pipleine since they had some similarties to current ones, for example AMQP or JMS consume and publish, and now adding MQTT to be supported.  Apache Nifi now has more support for AWS services, Amazon's Dynamo and S3, with the ListS3 and the Delete/Put DynamoDB Processors.  The biggest upgrade, I think, for processors is the DebugFlow processor, which allows you to produce a behavior you'd like to test for a flow.  This could be transfering a flow file to a success/failure relationship, wanting to rollback a FlowFile to test behaviour without penalty, or just throwing an exception.
I encourage you to take a look at the descriptions of these procesors on our [Processors Page]({{site.url}}/apache-nifi-processors/) which lists all current processors, and is updated after every release.  

