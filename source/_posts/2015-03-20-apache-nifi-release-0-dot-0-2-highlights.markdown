---
layout: post
title: "Apache Nifi Release 0.0.2 Highlights"
date: 2015-03-20 01:45:11 +0000
author: Chad Zobrisky
comments: true
sharing: true
footer: true
description: Nifi built second release, 0.0.2.  What it contains and release highlights.
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.0.2 Highlights, Release Highlights
categories: [Apache Nifi, Release]
---

Apache Nifi just kicked out their second release, [0.0.2](https://nifi.apache.org/download.html).  It doesn't have too many new features in it, hence a patch release according to [semantic versioning](http://semver.org), but it is definitely an improvement over the previous version, with it's bug fixes, improvements, and new features numbers below.

* [Bug Fixes](#bugfixes):		35
* [Improvements](#improvements):		17
* [New Features](#new-features):		5

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
The nifi community came in with some big fixes with this release.  The biggest ones I feel are the ability to now build on Mac OSX and increasing documentation.  There were quite a few other fixes that greatly improved the overall NiFi experience, processors now stop correctly and aren't continued to be scheduled and some clustering issues were resolved for example.

### <a name="improvements"></a>Improvements
The improvements in this release included a few maintanence related tasks and again some over all usability tasks, with most of them falling on the usability side.  The main improvements in Nifi release 0.0.2 were document related and overall usability updates, the cleanup of development documents, and too many to name for the usability.  In this release though, you should expect the following usability improvements:

* proxy support for the GetFTP Processor
* Component toolbox improvements
* Dragging/drawing relationships
* Labeling with the same color for multiple items

### <a name="new-features"></a>New Features
Now on to the good stuff, new features!  This release only had a few additional features added, but from what I've read there are quite a few more coming.  The highlights in this category are:

Multiple new processors
* JSON Processors
* ExecuteProcess processor
* StoreInKiteDataset processor
 
New processors are great and mean more possibilities and use cases for Apache Nifi.  We showed you how to create a JSON processor in a previous post, [Developing a custom Nifi Processor: JSON]({{site_url}}/developing-a-custom-apache-nifi-processor-json), and now someone has contributed a JSON processor to Nifi.  For a full list of Nifi Processors, including the newly added ones, see our [previous post]({{ site_url }}/apache-nifi-processors).

It has been rumored that the next release will contain quite a few changes and be a minor release bumping up to version 0.1.0.  With over 200 tickets open on their JIRA, Nifi could see a great amount of change in the coming months.

The full list of release notes can be found on Apache Nifi's [JIRA page](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12329373) and downloads for all of their releases, source code and binaries, are available from their [website](https://nifi.apache.org/download.html).  Nifi is also making thier releases available through maven via apaches [maven repository](https://repository.apache.org/content/repositories/releases/org/apache/nifi/).

As always, check back for how-tos and Apache Nifi related updates.  New videos and posts are coming!!