---
layout: post
title: "Apache Nifi: What Processors are there?"
date: 2015-02-05 03:00:06 +0000
updated: 2015-03-20 12:14:00 +0000
author: Chad Zobrisky
comments: true
sharing: true
footer: true
description: Apache Nifi processors and processors list.
keywords: Apache Nifi, apache nifi, Nifi, Processors
categories: [Apache Nifi, Processors]
---

** Includes all processors through release 0.0.2 **

I looked around at what can be done with Apache NiFi and didn't notice a list of processors without looking at the code or building the project.  I think a list of available processors, the work horse of Apache Nifi, would greatly help decide if it is right for certain needs.  So, I went into the usage guide in the Apache Nifi UI and pulled a list of processors and a quick description for those who want to know what possibilities there are before getting into nifi itself!

# List of processors
Here is a list of all 53 processors, listed alphabetically, that are currently in Apache Nifi as of February 5th, 2015.  Each one links to a description of the processor further down.  The Usage documentation available in the web ui has much more detail about each processor, it's properties, modifiable attributes, and relationships and each processor has it's own page in the UI, so here is just a quick overview.  Again, this content is taken directly from Nifi's Usage guide in their web UI and all credit/rights belong to them under the Apache 2.0 License.

<!--more -->

* [Base64EncodeContent](#Base64EncodeContent)
* [CompressContent](#CompressContent)
* [ControlRate](#ControlRate)
* [ConvertCharacterSet](#ConvertCharacterSet)
* [ConvertCSVToAvro](#ConvertCSVToAvro)
* [ConvertJSONToAvro](#ConvertJSONToAvro)
* [CreateHadoopSequenceFile](#CreateHadoopSequenceFile)
* [DetectDuplicate](#DetectDuplicate)
* [DistributeLoad](#DistributeLoad)
* [EncryptContent](#EncryptContent)
* [EvaluateJSONPath](#EvaluateJSONPath)
* [EvaluateRegularExpression](#EvaluateRegularExpression)
* [EvaluateXPath](#EvaluateXPath)
* [EvaluateXQuery](#EvaluateXQuery)
* [ExecuteProcess](#ExecuteProcess)
* [ExecuteStreamCommand](#ExecuteStreamCommand)
* [GenerateFlowFile](#GenerateFlowFile)
* [GetFile](#GetFile)
* [GetFTP](#GetFTP)
* [GetHDFS](#GetHDFS)
* [GetHDFSSequenceFile](#GetHDFSSequenceFile)
* [GetHTTP](#GetHTTP)
* [GetJMSQueue](#GetJMSQueue)
* [GetJMSTopic](#GetJMSTopic)
* [GetKafka](#GetKafka)
* [GetSFTP](#GetSFTP)
* [HandleHttpRequest](#HandleHttpRequest)
* [HandleHttpResponse](#HandleHttpResponse)
* [HashAttribute](#HashAttribute)
* [HashContent](#HashContent)
* [IdentifyMimeType](#IdentifyMimeType)
* [InvokeHTTP](#InvokeHTTP)
* [ListenHTTP](#ListenHTTP)
* [ListenUDP](#ListenUDP)
* [LogAttribute](#LogAttribute)
* [MergeContent](#MergeContent)
* [ModifyBytes](#ModifyBytes)
* [MonitorActivity](#MonitorActivity)
* [PostHTTP](#PostHTTP)
* [PutEmail](#PutEmail)
* [PutFile](#PutFile)
* [PutFTP](#PutFTP)
* [PutHDFS](#PutHDFS)
* [PutJMS](#PutJMS)
* [PutKafka](#PutKafka)
* [PutSFTP](#PutSFTP)
* [ReplaceText](#ReplaceText)
* [ReplaceTextWithMapping](#ReplaceTextWithMapping)
* [RouteOnAttribute](#RouteOnAttribute)
* [RouteOnContent](#RouteOnContent)
* [ScanAttribute](#ScanAttribute)
* [ScanContent](#ScanContent)
* [SegmentContent](#SegmentContent)
* [SplitContent](#SplitContent)
* [SplitJson](#SplitJson)
* [SplitText](#SplitText)
* [SplitXML](#SplitXML)
* [StoreInKiteDataset](#StoreInKiteDataset)
* [TransformXML](#TransformXML)
* [UnpackContent](#UnpackContent)
* [UpdateAttribute](#UpdateAttribute)
* [ValidateXML](#ValidateXML)

### <a name="Base64EncodeContent"></a>Base64EncodeContent
This processor base64 encodes FlowFile content, or decodes FlowFile content from base64.

### <a name="CompressContent"></a>CompressContent
This processor compresses and decompresses the contents of FlowFiles using a user-specified compression algorithm.

### <a name="ControlRate"></a>ControlRate
This processor controls the rate at which data is transferred to follow-on processors.

### <a name="ConvertCharacterSet"></a>ConvertCharacterSet
This processor converts a FlowFile's content from one character set to another.

### <a name="ConvertCSVToAvro"></a>ConvertCSVToAvro
No description is given for this processor.

### <a name="ConvertJSONToAvro"></a>ConvertJSONToAvro
No description is given for this processor.

### <a name="CreateHadoopSequenceFile"></a>CreateHadoopSequenceFile
This processor is used to create a Hadoop Sequence File, which essentially is a file of key/value pairs. The key will be a file name and the value will be the flow file content. The processor will take either a merged (a.k.a. packaged) flow file or a singular flow file. Historically, this processor handled the merging by type and size or time prior to creating a SequenceFile output; it no longer does this. If creating a SequenceFile that contains multiple files of the same type is desired, precede this processor with a RouteOnAttribute processor to segregate files of the same type and follow that with a MergeContent processor to bundle up files. If the type of files is not important, just use the MergeContent processor. When using the MergeContent processor, the following Merge Formats are supported by this processor:

TAR
ZIP
FlowFileStream v3
The created SequenceFile is named the same as the incoming FlowFile with the suffix '.sf'. For incoming FlowFiles that are bundled, the keys in the SequenceFile are the individual file names, the values are the contents of each file.
NOTE: The value portion of a key/value pair is loaded into memory. While there is a max size limit of 2GB, this could cause memory issues if there are too many concurrent tasks and the flow file sizes are large.

### <a name="DetectDuplicate"></a>DetectDuplicate
This processor detects duplicate data by examining flow file attributes, thus allowing the user to configure what it means for two FlowFiles to be considered "duplicates". This processor does not read the contents of a flow file, and is typically preceded by another processor which computes a value based on the flow file content and adds that value to the flow file's attributes; e.g. HashContent. Because this Processor needs to be able to work within a NiFi cluster, it makes use of a distributed cache service to determine whether or not the data has been seen previously.

If the processor is to be run on a standalone instance of NiFi, that instance should have both a DistributedMapCacheClient and a DistributedMapCacheServer configured in its controller-services.xml file.

### <a name="DistributeLoad"></a>DistributeLoad
This processor distributes FlowFiles to downstream processors based on a distribution strategy. The user may select the strategy "round robin", the strategy "next available", or "load distribution service". If using the round robin strategy, the default is to assign each destination (i.e., relationship) a weighting of 1 (evenly distributed). However, the user may add optional properties to change this weighting. When adding a property, the name must be a positive integer between 1 and the number of relationships (inclusive). For example, if Number of Relationships has a value of 8 and a property is added with the name 5 and the value 10, then relationship 5 (among the 8) will receive 10 FlowFiles in each iteration instead of 1. All other relationships will receive 1 FlowFile in each iteration.

### <a name="EncryptContent"></a>EncryptContent
This processor encrypts or decrypts FlowFiles.

### <a name="EvaluateJsonPath"></a>EvaluateJsonPath
Evaluates one or more JsonPath expressions against the content of a FlowFile. The results of those expressions are assigned to FlowFile Attributes or are written to the content of the FlowFile itself, depending on configuration of the Processor. JsonPaths are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed (if the Destination is flowfile-attribute; otherwise, the property name is ignored). The value of the property must be a valid JsonPath expression. If the JsonPath evaluates to a JSON array or JSON object and the Return Type is set to 'scalar' the FlowFile will be unmodified and will be routed to failure. A Return Type of JSON can return scalar values if the provided JsonPath evaluates to the specified value and will be routed as a match. If Destination is 'flowfile-content' and the JsonPath does not evaluate to a defined path, the FlowFile will be routed to 'unmatched' without having its contents modified. If Destination is flowfile-attribute and the expression matches nothing, attributes will be created with empty strings as the value, and the FlowFile will always be routed to 'matched'.

### <a name="EvaluateRegularExpression"></a>EvaluateRegularExpression
This processor evaluates one or more Regular Expressions against the content of a FlowFile. The results of those Regular Expressions are assigned to FlowFile Attributes. Regular Expressions are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed. The value of the property must be a valid Regular Expressions with exactly one capturing group. If the Regular Expression matches more than once, only the first match will be used. If any provided Regular Expression matches, the FlowFile(s) will be routed to 'matched'. If no provided Regular Expression matches, the FlowFile will be routed to 'unmatched' and no attributes will be applied to the FlowFile.

### <a name="EvaluateXPath"></a>EvaluateXPath
This processor evaluates one or more XPaths against the content of FlowFiles. The results of those XPaths are assigned to FlowFile attributes or are written to the content of the FlowFile itself, depending on how the user configures the Destination and Return Type properties in the processor. XPaths are entered by adding user-defined properties; the name of each user-added property maps to the attribute name into which the result should be placed. The value of the property must be a valid XPath expression.

### <a name="EvaluateXQuery"></a>EvaluateXQuery
This processor evaluates one or more XQueries against the content of FlowFiles. The results of those XQueries are assigned to FlowFile attributes or are written to the content of the FlowFile itself, depending on how the user configures the Destination property in the processor. One attribute or FlowFile is produced for each XQuery result. Each produced FlowFile will carry the attributes of the input FlowFile. See the "Examples" section for details on how multiple results can be wrapped or concatenated. XQueries are entered by adding user-defined properties; the name of each user-added property maps to the attribute name into which the result should be placed. The value of the property must be a valid XQuery expression.

### <a name="ExecuteProcess"></a>ExecuteProcess
Runs an operating system command specified by the user and writes the output of that command to a FlowFile. If the command is expected to be long-running, the Processor can output the partial data on a specified interval. When this option is used, the output is expected to be in textual format, as it typically does not make sense to split binary data on arbitrary time-based intervals.

### <a name="ExecuteStreamCommand"></a>ExecuteStreamCommand
This processor executes an external command on the contents of a FlowFile, and creates a new FlowFile with the results of the command.

### <a name="GenerateFlowFile"></a>GenerateFlowFile
This processor creates FlowFiles of random data to be used for load testing purposes.

### <a name="GetFile"></a>GetFile
This processor obtains FlowFiles from a local directory. NiFi will need at least read permissions on the files it will pull otherwise it will ignore them.

### <a name="GetFTP"></a>GetFTP
This processor fetches files from an FTP server and creates FlowFiles from them.

### <a name="GetHDFS"></a>GetHDFS
This processor reads files from an HDFS cluster into NiFi FlowFiles.

### <a name="GetHDFSSequenceFile"></a>GetHDFSSequenceFile
This processor is used to pull files from HDFS. The files being pulled in MUST be SequenceFile formatted files. The processor creates a flow file for each key/value entry in the ingested SequenceFile. The created flow file's content depends on the value of the optional configuration property FlowFile Content. Currently, there are two choices: VALUE ONLY and KEY VALUE PAIR. With the prior, only the SequenceFile value element is written to the flow file contents. With the latter, the SequenceFile key and value are written to the flow file contents as serialized objects; the format is key length (int), key(String), value length(int), value(bytes). The default is VALUE ONLY.

NOTE: This processor loads the entire value entry into memory. While the size limit for a value entry is 2GB, this will cause memory problems if there are too many concurrent tasks and the data being ingested is large.

### <a name="GetHTTP"></a>GetHTTP
This processor fetches files via HTTP and creates FlowFiles from them.

### <a name="GetJMSQueue"></a>GetJMSQueue
This processor pulls messages from a JMS Queue, creating a FlowFile for each JMS message or bundle of messages, as configured.

### <a name="GetJMSTopic"></a>GetJMSTopic
This processor pulls messages from a JMS Topic, creating a FlowFile for each JMS message or bundle of messages, as configured.

### <a name="GetKafka"></a>GetKafka
This Processors polls Apache Kafka for data. When a message is received from Kafka, this Processor emits a FlowFile where the content of the FlowFile is the value of the Kafka message. If the message has a key associated with it, an attribute named kafka.key will be added to the FlowFile, with the value being the UTF-8 Encoded value of the Message's Key.

Kafka supports the notion of a Consumer Group when pulling messages in order to provide scalability while still offering a publish-subscribe interface. Each Consumer Group must have a unique identifier. The Consumer Group identifier that is used by NiFi is the UUID of the Processor. This means that all of the nodes within a cluster will use the same Consumer Group Identifier so that they do not receive duplicate data but multiple GetKafka Processors can be used to pull from multiple Topics, as each Processor will receive a different Processor UUID and therefore a different Consumer Group Identifier.

### <a name="GetSFTP"></a>GetSFTP
This processor pulls files from an SFTP server and creates FlowFiles to encapsulate them.

### <a name="HandleHttpRequest"></a>HandleHttpRequest
This processor starts an HTTP server and creates a FlowFile for each HTTP Request that it receives. The Processor leaves the HTTP Connection open and is intended to be used in conjunction with a HandleHttpResponse Processor.

The pairing of this Processor with a HandleHttpResponse Processor provides the ability to use NiFi to visually construct a web server that can carry out any functionality that is available through the existing Processors. For example, one could construct a Web-based front end to an SFTP Server by constructing a flow such as:

HandleHttpRequest -> PutSFTP -> HandleHttpResponse

The HandleHttpRequest Processor provides several Properties to configure which methods are supported, the paths that are supported, and SSL configuration. The FlowFiles that are generated by this Processor have the following attributes added to them, providing powerful routing capabilities and traceability of all data.

### <a name="HandleHttpResponse"></a>HandleHttpResponse
This processor responds to an HTTP request that was received by the HandleHttpRequest Processor.

The pairing of this Processor with a HandleHttpRequest Processor provides the ability to use NiFi to visually construct a web server that can carry out any functionality that is available through the existing Processors. For example, one could construct a Web-based front end to an SFTP Server by constructing a flow such as:

HandleHttpRequest -> PutSFTP -> HandleHttpResponse

This Processor must be configured with the same <HTTP Context Map> service as the corresponding HandleHttpRequest Processor. Otherwise, all FlowFiles will be routed to the 'failure' relationship.

All FlowFiles must have an attribute named http.context.identifier. The value of this attribute is used to lookup the HTTP Response so that the proper message can be sent back to the requestor. If this attribute is missing, the FlowFile will be routed to 'failure.'

### <a name="HashAttribute"></a>HashAttribute
This processor hashes together the key/value pairs of several FlowFile attributes and adds the hash as a new attribute. The user may add optional properties such that the name of each property is the name of a FlowFile attribute to consider and the value of the property is a regular expression that, if matched by the attribute value, causes that attribute to be used as part of the hash. If the regular expression contains a capturing group, only the value of the capturing group is used.

### <a name="HashContent"></a>HashContent
This processor calculates a hash value for the content of a FlowFile and puts the hash value on the FlowFile as an attribute whose name is determined by the Hash Attribute Name property.

### <a name="IdentifyMimeType"></a>IdentifyMimeType
This processor attempts to identify the MIME type used for a FlowFile. If the MIME type can be identified, an attribute with the name mime.type is added to the FlowFile, and its value is the detected MIME type. Some MIME types require the processor to read a significant amount of data; for these MIME types, their identification is optional. (See the properties Identify ZIP and Identify TAR.) The algorithm may have to read the entire contents of a file for each type of identification. If the MIME Type cannot be determined, its mime.type attribute will be set to application/octet-stream .

The following MIME Types are detected:

* application/gzip
* application/bzip2
* application/flowfile-v3
* application/flowfile-v1 (requires Identify TAR be set to true)
* application/xml
* video/mp4
* video/x-m4v
* video/mp4a-latm
* video/quicktime
* video/mpeg
* audio/wav
* audio/mp3
* image/bmp
* image/png
* image/jpg
* image/gif
* image/tif
* application/vnd.ms-works
* application/msexcel
* application/mspowerpoint
* application/msaccess
* application/x-ms-wmv
* application/pdf
* application/x-rpm
* application/tar
* application/x-7z-compressed
* application/java-archive
* application/zip
* application/x-lzh

### <a name="InvokeHTTP"></a>InvokeHTTP
Making requests to remote HTTP servers. Supporting common HTTP methods. Storing results as new flowfiles upon success. Routing to failure on error.

An HTTP client processor that converts FlowFile attributes to HTTP headers with configurable HTTP method, URL, etc.

### <a name="ListenHTTP"></a>ListenHTTP
This processor starts an HTTP service that is used to receive FlowFiles from remote sources. The URL of the service is http://{hostname}:{port}/contentListener.

### <a name="ListenUDP"></a>ListenUDP
This processor listens for Datagram Packets on a given port and concatenates the contents of those packets together generating FlowFiles roughly as often as the internal buffer fills up or until no more data is currently available.

### <a name="LogAttribute"></a>LogAttribute
This processor reads the attributes on incoming FlowFiles and prints those attributes and their values to the log at the logging level specified by the user.

### <a name="MergeContent"></a>MergeContent
This processor merges a group of FlowFiles together into a "Bundle" based on a user-defined strategy and packages them into a single FlowFile. It is recommended that the processor be configured with only a single incoming connection, as groups of FlowFiles will not be created from FlowFiles in different connections. This processor updates the mime.type attribute as appropriate. After files have been merged by this processor, they can be unpackaged later using the UnpackContent processor.

### <a name="ModifyBytes"></a>ModifyBytes
This processor updates the content of a FlowFile by removing bytes from start or end of a file.

### <a name="MonitorActivity"></a>MonitorActivity
This processor monitors its point in the dataflow for activity and sends a notice when there is a lack of data flowing through it for some user-specified amount of time; it then sends another notice when the flow of data resumes.

### <a name="PostHTTP"></a>PostHTTP
This processor performs an HTTP post with the content of each incoming FlowFile.

### <a name="PutEmail"></a>PutEmail
This processor sends an e-mail to configured recipients for each incoming FlowFile.

### <a name="PutFile"></a>PutFile
This processor writes FlowFiles to the local file system.

### <a name="PutFTP"></a>PutFTP
This processor sends FlowFiles via FTP to an FTP server.

### <a name="PutHDFS"></a>PutHDFS
This processor writes FlowFiles to an HDFS cluster. It will create directories in which to store files as needed based on the Directory property.

When files are written to HDFS, the file's owner is the user identity of the NiFi process, the file's group is the group of the parent directory, and the read/write/execute permissions use the default umask. The owner can be overridden using the Remote Owner property, the group can be overridden using the Remote Group property, and the read/write/execute permissions can be overridden using the Permissions umask property.

NOTE: This processor can change owner or group only if the user identity of the NiFi process has super user privilege in HDFS to do so.

NOTE: The Permissions umask property cannot add execute permissions to regular files.

### <a name="PutJMS"></a>PutJMS
This processor creates a JMS message from the contents of a FlowFile and sends the message to a JMS server.

### <a name="PutKafka"></a>PutKafka
This Processors puts the contents of a FlowFile to a Topic in Apache Kafka. The full contents of a FlowFile becomes the contents of a single message in Kafka. This message is optionally assigned a key by using the <Kafka Key> Property.

The Processor allows the user to configure an optional Message Delimiter that can be used to send many messages per FlowFile. For example, a \n could be used to indicate that the contents of the FlowFile should be used to send one message per line of text. If the property is not set, the entire contents of the FlowFile will be sent as a single message. When using the delimiter, if some messages are successfully sent but other messages fail to send, the FlowFile will be FORKed into two child FlowFiles, with the successfully sent messages being routed to 'success' and the messages that could not be sent going to 'failure'.

### <a name="PutSFTP"></a>PutSFTP
This processor sends FlowFiles via SFTP to an SFTP server.

### <a name="ReplaceText"></a>ReplaceText
This processor updates the content of a FlowFile by evaluating a regular expression (regex) against the content and replacing the section of content that matches the regular expression with an alternate, user-defined, value.

### <a name="ReplaceTextWithMapping"></a>ReplaceTextWithMapping
This processor updates the content of a FlowFile by evaluating a regular expression (regex) against the content and replacing the section of content that matches a specified matching  group of the regular expression with an alternate, user-defined, value provided in a mapping file.  The mapping file is formatted as one key/value pair per line, seperated by tabs.

### <a name="RouteOnAttribute"></a>RouteOnAttribute
This processor routes FlowFiles based on their attributes using the NiFi Expression Language. Users add properties with valid NiFi Expression Language Expressions as the values. Each Expression must return a value of type Boolean (true or false).

Example: The goal is to route all files with filenames that start with ABC down a certain path. Add a property with the following name and value:

property name: ABC
property value: ${filename:startsWith('ABC')}
In this example, all files with filenames that start with ABC will follow the ABC relationship.

### <a name="RouteOnContent"></a>RouteOnContent
This processor applies user-added regular expressions to the content of a FlowFile and routes a copy of the FlowFile to each destination whose regular expression matches. The user adds properties where the name is the relationship that the FlowFile should follow if it matches the regular expression, which is defined as the property's value. User-defined properties do support the NiFi Expression Language, but in such cases, the results are interpreted as literal values, not regular expressions.

### <a name="ScanAttribute"></a>ScanAttribute
This processor scans the specified attributes of FlowFiles, checking to see if any of their values are present within the specified dictionary of terms.

### <a name="ScanContent"></a>ScanContent
This processor scans the content of FlowFiles for terms that are found in a user-supplied dictionary file. If a term is matched, the UTF-8 encoded version of the term is added to the FlowFile using the matching.term attribute. This allows for follow-on processors to use the value of the matching.term attribute to make routing decisions and so forth.

### <a name="SegmentContent"></a>SegmentContent
This processor segments a FlowFile into multiple smaller segments on byte boundaries. Each segment is given attributes that can then be used by the MergeContent processor to reconstruct the original FlowFile.

### <a name="SplitContent"></a>SplitContent
This processor splits incoming FlowFiles by a specified byte sequence.

### <a name="SplitJson"></a>SplitJson
This processor splits a JSON File into multiple, separate FlowFiles for an array element specified by a JsonPath expression. Each generated FlowFile is comprised of an element of the specified array and transferred to relationship 'split,' with the original file transferred to the 'original' relationship. If the specified JsonPath is not found or does not evaluate to an array element, the original file is routed to 'failure' and no files are generated.

Note: The underlying JsonPath library loads the entirety of the streamed content into and performs result evaluations in memory. Accordingly, it is important to consider the anticipated profile of content being evaluated by this processor and the hardware supporting it especially when working against large JSON documents.

### <a name="SplitText"></a>SplitText
This processor splits a text file into multiple smaller text files on line boundaries, each having up to a configured number of lines.

### <a name="SplitXML"></a>SplitXML
This processor splits an XML file into multiple separate FlowFiles, each comprising a child or descendant of the original root element.

### <a name="StoreInKiteDataset"></a>StoreInKiteDataset
No description is given for this processor.

### <a name="TransformXML"></a>TransformXML
This processor transforms the contents of FlowFiles based on a user-specified XSLT stylesheet file. XSL versions 1.0 and 2.0 are supported.

### <a name="UnpackContent"></a>UnpackContent
This processor unpacks the content of FlowFiles that have been packaged with one of several different packaging formats, emitting one to many FlowFiles for each input FlowFile.

### <a name="UpdateAttribute"></a>UpdateAttribute
This processor updates the attributes of a FlowFile using properties or rules that are added by the user. There are two ways to use this processor to add or modify attributes. One way is the "Basic Usage"; this allows you to set default attribute changes that affect every FlowFile going through the processor. The second way is the "Advanced Usage"; this allows you to make conditional attribute changes that only affect a FlowFile if it meets certain conditions. It is possible to use both methods in the same processor at the same time.

### <a name="ValidateXML"></a>ValidateXML
This processor validates the contents of FlowFiles against a user-specified XML schema file.

If you have questions about a processor, I'd encourage you to download the binaries and start up Apache Nifi.  If you really want more information, let me know and I'll try to compile a more complete post about each and every processor.