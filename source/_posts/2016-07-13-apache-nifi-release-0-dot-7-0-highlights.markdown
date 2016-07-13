---
layout: post
title: "Apache Nifi Release 0.7.0 Highlights"
date: 2016-07-13 02:07:13 +0000
comments: true
sharing: true
published: false
footer: true
description: Nifi release 0.7.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.7.0, Apache Nifi Release 0.7.0
categories: [Apache Nifi, Release]
---

Apache Nifi's newest release is out, 0.7.0.  You can grab the binaries from [thier site](https://nifi.apache.org/download.html) as always.  So lets dive in and see what to look for in this release!

* [Bug Fixes](#bugfixes): 			72
* [Improvements](#improvements): 	49
* [New Features](#new-features): 	10

As always, a bunch of bug fixes, but this time there are quite a few improvements.

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
Where to begin!  This release has the second most bug fixes we've seen.  Again, there are a ton to cover so take a peak at the full [release notes](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12335078) if you want to see more, since this is just a quick highlight.  Lots of processor fixes - NullPointerException to non-responsive processors, a few nifi startup fixes, and other fixes such as fixing OS specific issues, looking at you Windows bugs.  UI interaction was fixed when many HDFS and HBase processors were on the graph.  Bug fixes are hard to highlight, since they are so user specific for what you might have run into, but it is nice to know that reported bugs are getting fixed.

### <a name="improvements"></a>Improvements
I didn't know where to start for Bug fixes, but really don't know where to begin for Improvements.  I'll start by saying there are a few new processors that they included in this section, but I'm going to list in the New Features below to remain consistent.  Other actual improvements were updates to HTTP Processors to allow proxy authentication which I know I saw someone on here asked about, so it's nice to see that it is now doable!  You are now able to use SSL with AMQP processors.  ExecuteScript processors can now be executed concurrently too.  Performance improvements in StreamScanner, SSL for the mongo processors, and the Mock framework can now register FlowFile Assertions.

### <a name="new-features"></a>New Features
A few new processors here, but outside of that Apache Nifi now supports custom properties in the Expression Language.

New Processors:
* 
*
*
*
*
*
*