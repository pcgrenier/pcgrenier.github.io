---
layout: post
title: "Apache Nifi Release 0.5.0 Highlights"
date: 2016-02-16 20:09:49 +0000
comments: true
sharing: true
published: true
footer: true
description: Nifi release 0.5.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.5.0
categories: [Apache Nifi, Release]
---

Apache Nifi just voted on another release and have annouced and released 0.5.0, probably their most interesting release to date.  This release contains quite a few big features that expand what nifi has to offer and also how you can use it; notably script execution in a flow.  This new processor allows you to execute scripts in Javascript, Groovy, JRuby, Jython, Lua, and Python.  To grab the latest binaries, go to
[Apache Nifi's download page](https://nifi.apache.org/download.html)  The full release notes are also available on [Apache Nifi's wiki page](https://cwiki.apache.org/confluence/display/NIFI/Release+Notes#ReleaseNotes-Version0.5.0).

* [Bug Fixes](#bugfixes): 			64
* [Improvements](#improvements): 	28
* [New Features](#new-features): 	10

This release is substantial and really expands Apache Nifi's usablity, specificall for those users who don't feel comfortable with Java.  Lets take a deeper look at what else is included!

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
Since Nifi is quite a young project, less than a year old in the open source world, it still has quite a few bugs coming up as the user base expands.  It's great to see that as bugs come up, they are getting the attention of the community and developers.  Each release is getting better and better.  For this release, quite a few of the bugs are just under the covers, rewording error messages or documentation fixes.  There are also some functionality bugs that were corrected in this release; Controller Service sorting by type and state now works, PutS3 now allows larger than 5GB files, Unit tests are performing better - no time outs on certain environments, a few fixes to PutSQL processor for improved functionality also.  The full list of bugs addressed in this release can be found in [Apache Nifi's Jira](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12334158)

### <a name="improvements"></a>Improvements
Apache Nifi Expression language suppport has been added to a few fields for some processors with this release - the MergeContent Processor's Correlation Attribute Field and the xxxS3Object SECRET_KEY and ACCESS_KEY properties.  The UI now deletes an object when it is selected and the backspace key is pressed, which is a step in the right direction to improve usability.  Their are talks of a new UI that is in the works to allow for better user role management and also use HTML5 and newer web technology for the UI.  Some other improvements were new method for the Expression Langauge, getDelimitedField, PutJMS now works as expected for the uri shcema specified.

### <a name="new-features"></a>New Features
Some big changes for this release!  As I talked about before, there are a few new processors - 14 total - and also one that was deprecated/removed - ConvertCSVToSql.  The big new processors are a new processor to execute scripts and allow them access to the flowfile attributes - the ExecuteScript processor.  There is also a new processor for writing events to Riemann - the PutRiemann processor.  ElasticSearch is also now suppported through it's own processors.  The last big processor for this release is Get/PutAMQP processors for the AMQP connections - similar to JMS for newer message servers such as rabbitMQ and [Apache's QPID](http://qpid.apache.org/).  For a full list of processors, check out our [full updated list of nifi processors]({{site.url}}/apache-nifi-processors/).

All 14 new processors, with links to their description: 

* [ConsumeAMQP]({{site.url}}/apache-nifi-processors/#ConsumeAMQP)
* [ConvertJSONToSQL]({{site.url}}/apache-nifi-processors/#ConvertJSONToSQL)
* [ExecuteScript]({{site.url}}/apache-nifi-processors/#ExecuteScript)
* [FetchDistributedMapCache]({{site.url}}/apache-nifi-processors/#FetchDistributedMapCache)
* [FetchElasticSearch]({{site.url}}/apache-nifi-processors/#FetchElasticSearch)
* [GetHTMLElement]({{site.url}}/apache-nifi-processors/#GetHTMLElement)
* [InferAvroShema]({{site.url}}/apache-nifi-processors/#InferAvroShema)
* [InvokeScriptedProcessor]({{site.url}}/apache-nifi-processors/#InvokeScriptedProcessor)
* [ListenRELP]({{site.url}}/apache-nifi-processors/#ListenRELP)
* [ModifyHTMLElement]({{site.url}}/apache-nifi-processors/#ModifyHTMLElement)
* [PutHTMLElement]({{site.url}}/apache-nifi-processors/#PutHTMLElement)
* [PutRiemann]({{site.url}}/apache-nifi-processors/#PutRiemann)


Another big new feature in this release is the ability to inspect/interact with FlowFiles inside of the Apache Nifi UI - flow files inside of the flow!  This is so awesome!  You can now select a processor/connection and peak at what is happening in a sense and upload/remove files from a queue!  Exciting stuff!!

This release contained quite a few new and interesting additions that we plan on follwing up on with future posts, so be sure to check back to see how these new features can be used.