---
layout: post
title: "Apache Nifi Release 0.4.0 highlights"
date: 2015-12-15 03:00:56 +0000
comments: true
sharing: true
published: true
footer: true
description: Nifi release 0.4.0. What's new and release highlights
keywords: Apache Nifi, apache nifi, Nifi, Release, Nifi Release 04.0
categories: [Apache Nifi, Release]
---

Apache Nifi kicked out thier second release since graduating this past Friday.  With the release of 0.4.0, they are one step closer to a 1.0.0 release which will contain some very interesting things.  While we look forward to the first big release of Apache Nifi, lets break down the changes in the current build.  As always, release 0.4.0 is available on [Apache Nifi's download page](https://nifi.apache.org/download.html).

* [Bug Fixes](#bugfixes): 			93
* [Improvements](#improvements): 	44
* [New Features](#new-features): 	13

The release notes are available on [Nifi's confluence page](https://cwiki.apache.org/confluence/display/NIFI/Release+Notes#ReleaseNotes-Version0.4.0) and a quick highlight can be found below.  First lets just say, this is the biggest release so far, with almost double the amount of bug fixes, and over double the amount of improvements and new features! 

* General UI improvements to usability
* Multiple Authentication Mechanisms
* New Provenance event types and ability to searh provenance events
* Idle CPU usage was reduced
* [New Processors!](#newprocessors)
* Improved OS support

<!--more-->
### <a name="bugfixes"></a>Bug Fixes
Bug fixes, bug fixes everywhere!  So many bug fixes that it's almost impossible to list them all here.  Some of the big ones include fixing quite a few issues with MergeContent (efficiencies with 10,000+ files, queue swapping and an issue with delimiters), improved S3 support with PutS3 and FetchS3 fixes (now works with java 8, logs the URL correctly, corrected provenance evnet) and HDFS now acts accordingly with failures (passes to failure relationship and acts as expected for permission failures).  There were also fixes with the database connection pooling and with the PutSQL supporting multiple data types and booleans.  ConvertJSONToSQL also had quite a few fixes including caching results and metadata.  For the full list, either fire up nifi and check it out or look at the release notes! 

### <a name="improvements"></a>Improvements
There are a few new provenance events with this release, including download event, fetch event, and REMOTE_INVOCATION event.  ExecuteSQL can now be run periodically without an input FlowFile allowing for expanded use of SQL tasks.  InvokeHTTP has been improved, it now has unique ids across clusters and has additional unit tests. The management side of nifi has been refactored slightly, mainly to clean up the shell scripts and fix some whitespace bugs.  SSL support has been added to the PutS3 processor. It's good to see improvements in so many different areas of nifi!

### <a name="new-features"></a>New Features
The 13 new features include a few <a name="newprocessors"></a>new processors:

* AttributesToJSON
* DeleteS3Object
* ExtractAvroMetadata
* FetchFile
* FetchSFTP
* GetAzureEventHub
* GetCouchbaseKey
* GetHBase
* ListenSyslog
* ListFile
* ListSFTP
* ParseSyslog
* PutAzureEventHub
* PutCouchbaseKey
* PutDistributedMapCache
* PutHBaseCell
* PutHBaseJSON
* PutSyslog
* RouteText
* SplitAvro
* TailFile

To see more information about all Nifi Processors, checkout our full list of [nifi processors and their quick descriptions]({{ site.url }}/apache-nifi-processors/).  You can also check [Nifi's Documentation](https://nifi.apache.org/docs.html) for a little more information.  In addition to the new processors, Nifi now supports LDAP authentication ontop of username/password and two way SSL.  An enhancement to the UI now allows users to drop queued FLowFiles.  Before you had to stop the processor, add a new processor with a failure to discard the file and restart Nifi just to clear a queue!  Now it's much easier!  

There is talks already about the first major release of Apache Nifi, 1.0.0 and redoing some of the decisions they made which would break backwords compatability.  We look forward to their next release which seems to be about every 6-8 weeks.  See you guys then!