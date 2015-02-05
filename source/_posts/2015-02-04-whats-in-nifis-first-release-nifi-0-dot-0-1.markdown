---
layout: post
title: "What's in Nifi's first release: Nifi 0.0.1"
date: 2015-02-04 21:54:57 +0000
author: Chad Zobrisky
comments: true
sharing: true
footer: true
description: Nifi built their first release, 0.0.1. Let's take a look at what is in it.
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 0.0.1
categories: [Apache Nifi, Release]
---

Apache Nifi just had their first release, [0.0.1](https://nifi.incubator.apache.org/downloads/).  It showed good movement forward with 75 bug fixes, 24 improvements, and 2 new features.  A list of [Release Notes](https://issues.apache.org/jira/secure/ReleaseNote.jspa?projectId=12316020&version=12329078) is on their Jira page.  With the release, it gives the users source downloads to start from, which is great, but lets look at the highlights of this release.

## Apache Nifi Release 0.0.1 Highlights

* One of the biggest changes was the directory structure to allow parrallel maven builds.  This took the build time down from 20-30 minutes to 3-7 minutes. [Nifi Jira 169](https://issues.apache.org/jira/browse/NIFI-169)
* The improvement of the assembly process also allowed for more stream lined packaging. [Nifi Jira 228](https://issues.apache.org/jira/browse/NIFI-228)

Outside of the build process, most of the updates were cleaning up the code base to make it more developer friendly and fixing alot of small bugs;

* Updating libraries to their most current version
* Adding documentation/users guides
* Guarantee builds on varying OSes: OSX, Linux, Windows.

I'm pretty excited to see what's in the next release, but also excited that I don't have to build nifi to use it.  Release binaries are available on the [nifi website](https://nifi.incubator.apache.org/downloads/).