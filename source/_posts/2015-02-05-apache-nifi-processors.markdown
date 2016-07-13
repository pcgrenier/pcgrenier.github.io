---
layout: post
title: "Apache Nifi: What Processors are there?"
date: 2015-02-05 03:00:06 +0000
updated: 2016-07-13 12:00:00 +0000
author: Chad Zobrisky
comments: true
sharing: true
footer: true
description: Apache Nifi processors and processors list.
keywords: Apache Nifi, apache nifi, Nifi, Processors, Nifi Processors, Apache Nifi Processors
categories: [Apache Nifi, Processors]
---

** Includes all processors through release 0.7.0 **

I looked around at what can be done with Apache NiFi and didn't notice a list of processors without looking at the code or building the project.  I think a list of available processors, the work horse of Apache Nifi, would greatly help decide if it is right for certain needs.  So, I went into the usage guide in the Apache Nifi UI and pulled a list of processors and a quick description for those who want to know what possibilities there are before getting into nifi itself!

# List of processors
With new releases of Nifi, the number of processors have increased from the original 53 to 154!
Here is a list of all 154 processors, listed alphabetically, that are currently in Apache Nifi as of the most rescent release.  Each one links to a description of the processor further down.  The Usage documentation available in the web ui has much more detail about each processor, it's properties, modifiable attributes, and relationships and each processor has it's own page in the UI, so here is just a quick overview.  Again, this content is taken directly from Nifi's Usage guide in their web UI and all credit/rights belong to them under the Apache 2.0 License.

Nifi has improved their documentation, which was originally only available when running apache nifi.  The documentation now is produced through the build process and has been added to [their website](https://nifi.apache.org/docs.html).  So if you need more information or more detail about each processor just check there.

<!--more -->
* [AttributesToJSON](#AttributesToJSON)
* [Base64EncodeContent](#Base64EncodeContent)
* [CompressContent](#CompressContent)
* [ConsumeAMQP](#ConsumeAMQP)
* [ConsumerJMS](#ConsumeJMS)
* [ConseumeKafka](#ConsumeKafka)
* [ConsumeMQTT](#ConsumeMQTT)
* [ControlRate](#ControlRate)
* [ConvertAvroSchema](#ConvertAvroSchema)
* [ConvertAvroToJSON](#ConvertAvroToJSON)
* [ConvertCharacterSet](#ConvertCharacterSet)
* [ConvertCSVToAvro](#ConvertCSVToAvro)
* [ConvertJSONToAvro](#ConvertJSONToAvro)
* [ConvertCSVToSQL](#ConvertCSVToSQL) DEPRECATED - no longer available as of 0.5.0
* [ConvertJSONToSQL](#ConvertJSONToSQL)
* [CreateHadoopSequenceFile](#CreateHadoopSequenceFile)
* [DebugFlow](#DebugFlow)
* [DeleteS3Object](#DeleteS3Object)
* [DeleteSQS](#DeleteSQS)
* [DetectDuplicate](#DetectDuplicate)
* [DistributeLoad](#DistributeLoad)
* [DuplicateFlowFile](#DuplicateFlowFile)
* [EncryptContent](#EncryptContent)
* [EvaluateJSONPath](#EvaluateJSONPath)
* [EvaluateRegularExpression](#EvaluateRegularExpression) 
* [ExtractMediaMetadata](#ExtractMediaMetadata)
DEPRECATED-Use [ExtractText](#ExtractText)
* [EvaluateXPath](#EvaluateXPath)
* [EvaluateXQuery](#EvaluateXQuery)
* [ExecuteFlumeSink](#ExecuteFlumeSink)
* [ExecuteFlumeSource](#ExecuteFlumeSource)
* [ExecuteProcess](#ExecuteProcess)
* [ExecuteScript](#ExecuteScript)
* [ExecuteSQL](#ExecuteSQL)
* [ExecuteStreamCommand](#ExecuteStreamCommand)
* [ExtractAvroMetadata](#ExtractAvroMetadata)
* [ExtractHL7Attributes](#ExtractHL7Attributes)
* [ExtractImageMetadata](#ExtractImageMetadata)
* [ExtractText](#ExtractText)
* [FetchDistributedMapCache](#FetchDistributedMapCache)
* [FetchElasticSearch](#FetchElasticSearch)
* [FetchFile](#FetchFile)
* [FetchHDFS](#FetchHDFS)
* [FetchS3Object](#FetchS3Object)
* [FetchSFTP](#FetchSFTP)
* [GenerateFlowFile](#GenerateFlowFile)
* [GeoEnrichIP](#GeoEnrichIP)
* [GetAzureEventHub](#GetAzureEventHub)
* [GetCouchbaseKey](#GetCouchbaseKey)
* [GetDynamoDB](#GetDynamoDB)
* [GetFile](#GetFile)
* [GetFTP](#GetFTP)
* [GetHBase](#GetHBase)
* [GetHDFS](#GetHDFS)
* [GetHDFSEvents](#GetHDFSEvents)
* [GetHDFSSequenceFile](#GetHDFSSequenceFile)
* [GetHTMLElement](#GetHTMLElement)
* [GetHTTP](#GetHTTP)
* [GetJMSQueue](#GetJMSQueue)
* [GetJMSTopic](#GetJMSTopic)
* [GetKafka](#GetKafka)
* [GetMongo](#GetMongo)
* [GetSFTP](#GetSFTP)
* [GetSNMP](#GetSNMP)
* [GetSolr](#GetSolr)
* [GetSplunk](#GetSplunk)
* [GetSQS](#GetSQS)
* [GetTwitter](#GetTwitter)
* [HandleHttpRequest](#HandleHttpRequest)
* [HandleHttpResponse](#HandleHttpResponse)
* [HashAttribute](#HashAttribute)
* [HashContent](#HashContent)
* [IdentifyMimeType](#IdentifyMimeType)
* [InferAvroShema](#InferAvroShema)
* [InvokeHTTP](#InvokeHTTP)
* [InvokeScriptedProcessor](#InvokeScriptedProcessor)
* [JoltTransformJSON](#JoltTransformJSON)
* [ListenHTTP](#ListenHTTP)
* [ListenLumberjack](#ListenLumberjack)
* [ListenRELP](#ListenRELP)
* [ListenSyslog](#ListenSyslog)
* [ListenTCP](#ListenTCP)
* [ListenUDP](#ListenUDP)
* [ListFile](#ListFile)
* [ListHDFS](#ListHDFS)
* [ListS3](#ListS3)
* [ListSFTP](#ListSFTP)
* [LogAttribute](#LogAttribute)
* [MergeContent](#MergeContent)
* [ModifyBytes](#ModifyBytes)
* [ModifyHTMLElement](#ModifyHTMLElement)
* [MonitorActivity](#MonitorActivity)
* [ParseSyslog](#ParseSyslog)
* [PostHTTP](#PostHTTP)
* [PublishAMQP](#PublishAMQP)
* [PublishJMS](#PublishJMS)
* [PublishKafka](#PublishKafka)
* [PublishMQTT](#PublishMQTT)
* [PutAzureEventHub](#PutAzureEventHub)
* [PutCassandraQL](#PutCassandraQL)
* [PutCouchbaseKey](#PutCouchbaseKey)
* [PutDistributedMapCache](#PutDistributedMapCache)
* [PutDynamoDB](#PutDynamoDB)
* [PutElasticsearch](#PutElasticsearch)
* [PutEmail](#PutEmail)
* [PutFile](#PutFile)
* [PutFTP](#PutFTP)
* [PutHBaseCell](#PutHBaseCell)
* [PutHBaseJSON](#PutHBaseJSON)
* [PutHDFS](#PutHDFS)
* [PutHiveQL](#PutHiveQL)
* [PutHTMLElement](#PutHTMLElement)
* [PutJMS](#PutJMS)
* [PutKafka](#PutKafka)
* [PutKinesisFirehose](#PutKinesisFirehose)
* [PutLambda](#PutLambda)
* [PutMongo](#PutMongo)
* [PutRiemann](#PutRiemann)
* [PutS3Object](#PutS3Object)
* [PutSlack](#PutSlack)
* [PutSFTP](#PutSFTP)
* [PutSNS](#PutSNS)
* [PutSolrContentStream](#PutSolrContentStream)
* [PutSplunk](#PutSplunk)
* [PutSQL](#PutSQL)
* [PutSQS](#PutSQS)
* [PutSyslog](#PutSyslog)
* [PutTCP](#PutTCP)
* [PutUDP](#PutUDP)
* [QueryCassandra](#QueryCassandra)
* [QueryDatabaseTable](#QueryDatabaseTable)
* [ReplaceText](#ReplaceText)
* [ReplaceTextWithMapping](#ReplaceTextWithMapping)
* [ResizeImage](#ResizeImage)
* [RouteHL7](#RouteHL7)
* [RouteOnAttribute](#RouteOnAttribute)
* [RouteOnContent](#RouteOnContent)
* [RouteText](#RouteText)
* [ScanAttribute](#ScanAttribute)
* [ScanContent](#ScanContent)
* [SelectHiveQL](#SelectHiveQL)
* [SegmentContent](#SegmentContent)
* [SetSNMP](#SetSNMP)
* [SplitAvro](#SplitAvro)
* [SplitContent](#SplitContent)
* [SpringContextProcessor](#SpringContextProcessor)
* [SplitJson](#SplitJson)
* [SplitText](#SplitText)
* [SplitXML](#SplitXML)
* [StoreInKiteDataset](#StoreInKiteDataset)
* [TailFile](#TailFile)
* [TransformXML](#TransformXML)
* [UnpackContent](#UnpackContent)
* [UpdateAttribute](#UpdateAttribute)
* [ValidateXML](#ValidateXML)
* [YandexTranslate](#YandexTranslate)

### <a name="AttributesToJSON"></a>AttributesToJSON
Generates a JSON representation of the input FlowFile Attributes. The resulting JSON can be written to either a new Attribute 'JSONAttributes' or written to the FlowFile as content.

### <a name="Base64EncodeContent"></a>Base64EncodeContent
This processor base64 encodes FlowFile content, or decodes FlowFile content from base64.

### <a name="CompressContent"></a>CompressContent
This processor compresses or decompresses the contents of FlowFiles using a user-specified compression algorithm and updates the mime.type attribute as appropriate

### <a name="ConsumeAMQP"></a>ConsumeAMQP
Consumes AMQP Message transforming its content to a FlowFile and transitioning it to 'success' relationship

### <a name="ConsumeJMS"></a>ConsumeJMS
Consumes JMS Message of type BytesMessage or TextMessage transforming its content to a FlowFile and transitioning it to 'success' relationship.

### <a name="ConsumeKafka"></a>ConsumeKafka
This Processors polls Apache Kafka for data using KafkaConsumer API available with Kafka 0.9+. When a message is received from Kafka, this Processor emits a FlowFile where the content of the FlowFile is the value of the Kafka message.

### <a name="ConsumeMQTT"></a>ConsumeMQTT
Subscribes to a topic and receives messages from an MQTT broker

### <a name="ControlRate"></a>ControlRate
This processor controls the rate at which data is transferred to follow-on processors.

### <a name="ConvertAvroSchema"></a>ConvertAvroSchema
Convert records from one Avro schema to another, including support for flattening and simple type conversions.

This processor is used to convert data between two Avro formats, such as those coming from the ConvertCSVToAvro or ConvertJSONToAvro processors. The input and output content of the flow files should be Avro data files. The processor includes support for the following basic type conversions:

Anything to String, using the data's default String representation
String types to numeric types int, long, double, and float
Conversion to and from optional Avro types
In addition, fields can be renamed or unpacked from a record type by using the dynamic properties.

### <a name ="ConvertAvroToJSON"></a>ConvertAvroToJSON
Converts a Binary Avro record into a JSON object. This processor provides a direct mapping of an Avro field to a JSON field, such that the resulting JSON will have the same hierarchical structure as the Avro document. Note that the Avro schema information will be lost, as this is not a translation from binary Avro to JSON formatted Avro. The output JSON is encoded the UTF-8 encoding. If an incoming FlowFile contains a stream of multiple Avro records, the resultant FlowFile will contain a JSON Array containing all of the Avro records.

### <a name="ConvertCharacterSet"></a>ConvertCharacterSet
This processor converts a FlowFile's content from one character set to another.

### <a name="ConvertCSVToAvro"></a>ConvertCSVToAvro
Converts CSV files to Avro according to an Avro Schema

### <a name="ConvertCSVToJSON"></a>ConvertCSVToJSON
Converts JSON files to Avro according to an Avro Schema

### <a name="ConvertCSVToSQL"></a>ConvertCSVToSQL - DEPRECATED as of 0.5.0
Converts JSON files to Avro according to an Avro Schema
Converts a JSON-formatted FlowFile into an UPDATE or INSERT SQL statement. The incoming FlowFile is expected to be "flat" JSON message, meaning that it consists of a single JSON element and each field maps to a simple type. If a field maps to a JSON object, that JSON object will be interpreted as Text. If the input is an array of JSON elements, each element in the array is output as a separate FlowFile to the 'sql' relationship. Upon successful conversion, the original FlowFile is routed to the 'original' relationship and the SQL is routed to the 'sql' relationship.

### <a name="ConvertJSONToSQL"></a>ConvertJSONToSQL
Converts a JSON-formatted FlowFile into an UPDATE or INSERT SQL statement. The incoming FlowFile is expected to be "flat" JSON message, meaning that it consists of a single JSON element and each field maps to a simple type. If a field maps to a JSON object, that JSON object will be interpreted as Text. If the input is an array of JSON elements, each element in the array is output as a separate FlowFile to the 'sql' relationship. Upon successful conversion, the original FlowFile is routed to the 'original' relationship and the SQL is routed to the 'sql' relationship.

### <a name="CreateHadoopSequenceFile"></a>CreateHadoopSequenceFile
This processor is used to create a Hadoop Sequence File, which essentially is a file of key/value pairs. The key will be a file name and the value will be the flow file content. The processor will take either a merged (a.k.a. packaged) flow file or a singular flow file. Historically, this processor handled the merging by type and size or time prior to creating a SequenceFile output; it no longer does this. If creating a SequenceFile that contains multiple files of the same type is desired, precede this processor with a RouteOnAttribute processor to segregate files of the same type and follow that with a MergeContent processor to bundle up files. If the type of files is not important, just use the MergeContent processor. When using the MergeContent processor, the following Merge Formats are supported by this processor:

TAR
ZIP
FlowFileStream v3
The created SequenceFile is named the same as the incoming FlowFile with the suffix '.sf'. For incoming FlowFiles that are bundled, the keys in the SequenceFile are the individual file names, the values are the contents of each file.
NOTE: The value portion of a key/value pair is loaded into memory. While there is a max size limit of 2GB, this could cause memory issues if there are too many concurrent tasks and the flow file sizes are large.

### <a name="DebugFlow"></a>DebugFlow
The DebugFlow processor aids testing and debugging the FlowFile framework by allowing various responses to be explicitly triggered in response to the receipt of a FlowFile or a timer event without a FlowFile if using timer or cron based scheduling. It can force responses needed to exercise or test various failure modes that can occur when a processor runs.

### <a name="DeleteDynamoDB"></a>DeleteDynamoDB
Deletes a document from DynamoDB based on hash and range key. The key can be string or number. The request requires all the primary keys for the operation (hash or hash and range key)

### <a name="DeleteS3Object"></a>DeleteS3Object
Deletes FlowFiles on an Amazon S3 Bucket. If attempting to delete a file that does not exist, FlowFile is routed to success.

### <a name="DeleteSQS"></a>DeleteSQS
Deletes a message from an Amazon Simple Queuing Service Queue

### <a name="DetectDuplicate"></a>DetectDuplicate
This processor detects duplicate data by examining flow file attributes, thus allowing the user to configure what it means for two FlowFiles to be considered "duplicates". This processor does not read the contents of a flow file, and is typically preceded by another processor which computes a value based on the flow file content and adds that value to the flow file's attributes; e.g. HashContent. Because this Processor needs to be able to work within a NiFi cluster, it makes use of a distributed cache service to determine whether or not the data has been seen previously.

If the processor is to be run on a standalone instance of NiFi, that instance should have both a DistributedMapCacheClient and a DistributedMapCacheServer configured in its controller-services.xml file.

### <a name="DistributeLoad"></a>DistributeLoad
This processor distributes FlowFiles to downstream processors based on a distribution strategy. The user may select the strategy "round robin", the strategy "next available", or "load distribution service". If using the round robin strategy, the default is to assign each destination (i.e., relationship) a weighting of 1 (evenly distributed). However, the user may add optional properties to change this weighting. When adding a property, the name must be a positive integer between 1 and the number of relationships (inclusive). For example, if Number of Relationships has a value of 8 and a property is added with the name 5 and the value 10, then relationship 5 (among the 8) will receive 10 FlowFiles in each iteration instead of 1. All other relationships will receive 1 FlowFile in each iteration.

### <a name="DuplicateFlowFile"></a>DuplicateFlowFile
Intended for load testing, this processor will create the configured number of copies of each incoming FlowFile

### <a name="EncryptContent"></a>EncryptContent
Encrypts or Decrypts a FlowFile using either symmetric encryption with a password and randomly generated salt, or asymmetric encryption using a public and secret key.

### <a name="EvaluateJsonPath"></a>EvaluateJsonPath
Evaluates one or more JsonPath expressions against the content of a FlowFile. The results of those expressions are assigned to FlowFile Attributes or are written to the content of the FlowFile itself, depending on configuration of the Processor. JsonPaths are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed (if the Destination is flowfile-attribute; otherwise, the property name is ignored). The value of the property must be a valid JsonPath expression. If the JsonPath evaluates to a JSON array or JSON object and the Return Type is set to 'scalar' the FlowFile will be unmodified and will be routed to failure. A Return Type of JSON can return scalar values if the provided JsonPath evaluates to the specified value and will be routed as a match. If Destination is 'flowfile-content' and the JsonPath does not evaluate to a defined path, the FlowFile will be routed to 'unmatched' without having its contents modified. If Destination is flowfile-attribute and the expression matches nothing, attributes will be created with empty strings as the value, and the FlowFile will always be routed to 'matched'.

### <a name="EvaluateRegularExpression"></a>EvaluateRegularExpression
WARNING: This has been deprecated and will be removed in 0.2.0. Use ExtractText instead.

### <a name="EvaluateXPath"></a>EvaluateXPath
This processor evaluates one or more XPaths against the content of a FlowFile. The results of those XPaths are assigned to FlowFile Attributes or are written to the content of the FlowFile itself, depending on configuration of the Processor. XPaths are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed (if the Destination is flowfile-attribute; otherwise, the property name is ignored). The value of the property must be a valid XPath expression. If the XPath evaluates to more than one node and the Return Type is set to 'nodeset' (either directly, or via 'auto-detect' with a Destination of 'flowfile-content'), the FlowFile will be unmodified and will be routed to failure. If the XPath does not evaluate to a Node, the FlowFile will be routed to 'unmatched' without having its contents modified. If Destination is flowfile-attribute and the expression matches nothing, attributes will be created with empty strings as the value, and the FlowFile will always be routed to 'matched'

### <a name="EvaluateXQuery"></a>EvaluateXQuery
This processor evaluates one or more XQueries against the content of a FlowFile. The results of those XQueries are assigned to FlowFile Attributes or are written to the content of the FlowFile itself, depending on configuration of the Processor. XQueries are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed (if the Destination is 'flowfile-attribute'; otherwise, the property name is ignored). The value of the property must be a valid XQuery. If the XQuery returns more than one result, new attributes or FlowFiles (for Destinations of 'flowfile-attribute' or 'flowfile-content' respectively) will be created for each result (attributes will have a '.n' one-up number appended to the specified attribute name). If any provided XQuery returns a result, the FlowFile(s) will be routed to 'matched'. If no provided XQuery returns a result, the FlowFile will be routed to 'unmatched'. If the Destination is 'flowfile-attribute' and the XQueries matche nothing, no attributes will be applied to the FlowFile.

### <a name="ExecuteFlumeSink"></a>ExecuteFlumeSink
This processor executes a Flume sink. Each input FlowFile is converted into a Flume Event for processing by the sink.

### <a name="ExecuteFlumeSource"></a>ExecuteFlumeSource
Execute a Flume source. Each Flume Event is sent to the success relationship as a FlowFile

### <a name="ExecuteProcess"></a>ExecuteProcess
Runs an operating system command specified by the user and writes the output of that command to a FlowFile. If the command is expected to be long-running, the Processor can output the partial data on a specified interval. When this option is used, the output is expected to be in textual format, as it typically does not make sense to split binary data on arbitrary time-based intervals.

### <a name="ExecuteScript"></a>ExecuteScript
Experimental - Executes a script given the flow file and a process session. The script is responsible for handling the incoming flow file (transfer to SUCCESS or remove, e.g.) as well as any flow files created by the script. If the handling is incomplete or incorrect, the session will be rolled back. Experimental: Impact of sustained usage not yet verified.

### <a name="ExecuteSQL"></a>ExecuteSQL
Execute provided SQL select query. Query result will be converted to Avro format. Streaming is used so arbitrarily large result sets are supported

### <a name="ExecuteStreamCommand"></a>ExecuteStreamCommand
This processor executes an external command on the contents of a FlowFile, and creates a new FlowFile with the results of the command.

### <a name="ExtractAvroMetadata"></a>ExtractAvroMetadata
Extracts metadata from the header of an Avro datafile.

### <a name="ExtractHL7Attributes"></a>ExtractHL7Attributes
Extracts information from an HL7 (Health Level 7) formatted FlowFile and adds the information as FlowFile Attributes. The attributes are named as <Segment Name> <dot> <Field Index>. If the segment is repeating, the naming will be <Segment Name> <underscore> <Segment Index> <dot> <Field Index>. For example, we may have an attribute named "MHS.12" with a value of "2.1" and an attribute named "OBX_11.3" with a value of "93000^CPT4".

### <a name="ExtractImageMetadata"></a>ExtractImageMetadata
Extract the image metadata from flowfiles containing images. This processor relies on this metadata extractor library https://github.com/drewnoakes/metadata-extractor. It extracts a long list of metadata types including but not limited to EXIF, IPTC, XMP and Photoshop fields. For the full list visit the library's website.NOTE: The library being used loads the images into memory so extremely large images may cause problems

### <a name="ExtractMediaMetadata"></a>ExtractMediaMetadata
Extract the content metadata from flowfiles containing audio, video, image, and other file types. This processor relies on the Apache Tika project for file format detection and parsing. It extracts a long list of metadata types for media files including audio, video, and print media formats.NOTE: the attribute names and content extracted may vary across upgrades because parsing is performed by the external Tika tools which in turn depend on other projects for metadata extraction. For the more details and the list of supported file types, visit the library's website at http://tika.apache.org/.

### <a name="ExtractText"></a>ExtractText
Evaluates one or more Regular Expressions against the content of a FlowFile. The results of those Regular Expressions are assigned to FlowFile Attributes. Regular Expressions are entered by adding user-defined properties; the name of the property maps to the Attribute Name into which the result will be placed. The first capture group, if any found, will be placed into that attribute name.But all capture groups, including the matching string sequence itself will also be provided at that attribute name with an index value provided.The value of the property must be a valid Regular Expressions with one or more capturing groups. If the Regular Expression matches more than once, only the first match will be used. If any provided Regular Expression matches, the FlowFile(s) will be routed to 'matched'. If no provided Regular Expression matches, the FlowFile will be routed to 'unmatched' and no attributes will be applied to the FlowFile.

### <a name="FetchDistributedMapCache"></a>FetchDistributedMapCache
Computes a cache key from FlowFile attributes, for each incoming FlowFile, and fetches the value from the Distributed Map Cache associated with that key. The incoming FlowFile's content is replaced with the binary data received by the Distributed Map Cache. If there is no value stored under that key then the flow file will be routed to 'not-found'. Note that the processor will always attempt to read the entire cached value into memory before placing it in it's destination. This could be potentially problematic if the cached value is very large.

### <a name="FetchElasticSearch"></a>FetchElasticSearch
Retrieves a document from Elasticsearch using the specified connection properties and the identifier of the document to retrieve. If the cluster has been configured for authorization and/or secure transport (SSL/TLS) and the Shield plugin is available, secure connections can be made. This processor supports Elasticsearch 2.x clusters.

### <a name="FetchFile"></a>FetchFile
Reads the contents of a file from disk and streams it into the contents of an incoming FlowFile. Once this is done, the file is optionally moved elsewhere or deleted to help keep the file system organized.

### <a name="FetchHDFS"></a>FetchHDFS
Retrieves a file from HDFS. The content of the incoming FlowFile is replaced by the content of the file in HDFS. The file in HDFS is left intact without any changes being made to it.

### <a name="FetchS3Object"></a>FetchS3Object
Retrieves the contents of an S3 Object and writes it to the content of a FlowFile

### <a name="FetchSFTP"></a>FetchSFTP
Fetches the content of a file from a remote SFTP server and overwrites the contents of an incoming FlowFile with the content of the remote file.

### <a name="GenerateFlowFile"></a>GenerateFlowFile
This processor creates FlowFiles of random data to be used for load testing purposes.

### <a name="GeoEnrichIP"></a>GeoEnrichIP
Looks up geolocation information for an IP address and adds the geo information to FlowFile attributes. The geo data is provided as a MaxMind database. The attribute that contains the IP address to lookup is provided by the 'IP Address Attribute' property. If the name of the attribute provided is 'X', then the the attributes added by enrichment will take the form X.geo.<fieldName>

### <a name="GetAzureEventHub"></a>GetAzureEventHub
Receives messages from a Microsoft Azure Event Hub, writing the contents of the Azure message to the content of the FlowFile

### <a name="GetCouchbaseKey"></a>GetCouchbaseKey
Get a document from Couchbase Server via Key/Value access. The ID of the document to fetch may be supplied by setting the <Document Id> property. NOTE: if the Document Id property is not set, the contents of the FlowFile will be read to determine the Document Id, which means that the contents of the entire FlowFile will be buffered in memory.

### <a name="GetDynamoDB"></a>GetDynamoDB
Retrieves a document from DynamoDB based on hash and range key. The key can be string or number.For any get request all the primary keys are required (hash or hash and range based on the table keys).A Json Document ('Map') attribute of the DynamoDB item is read into the content of the FlowFile.

### <a name="GetFile"></a>GetFile
This processor obtains FlowFiles from a local directory. NiFi will need at least read permissions on the files it will pull otherwise it will ignore them.

### <a name="GetFTP"></a>GetFTP
This processor fetches files from an FTP server and creates FlowFiles from them.

### <a name="GetHBase"></a>GetHBase
This Processor polls HBase for any records in the specified table. The processor keeps track of the timestamp of the cells that it receives, so that as new records are pushed to HBase, they will automatically be pulled. Each record is output in JSON format, as {"row": "<row key>", "cells": { "<column 1 family>:<column 1 qualifier>": "<cell 1 value>", "<column 2 family>:<column 2 qualifier>": "<cell 2 value>", ... }}. For each record received, a Provenance RECEIVE event is emitted with the format hbase://<table name>/<row key>, where <row key> is the UTF-8 encoded value of the row's key.

### <a name="GetHDFS"></a>GetHDFS
Fetch files from Hadoop Distributed File System (HDFS) into FlowFiles. This Processor will delete the file from HDFS after fetching it.

### <a name="GetHDFSEvents"></a>GetHDFSEvents
This processor polls the notification events provided by the HdfsAdmin API. Since this uses the HdfsAdmin APIs it is required to run as an HDFS super user. Currently there are six types of events (append, close, create, metadata, rename, and unlink). Please see org.apache.hadoop.hdfs.inotify.Event documentation for full explanations of each event. This processor will poll for new events based on a defined duration. For each event received a new flow file will be created with the expected attributes and the event itself serialized to JSON and written to the flow file's content. For example, if event.type is APPEND then the content of the flow file will contain a JSON file containing the information about the append event. If successful the flow files are sent to the 'success' relationship. Be careful of where the generated flow files are stored. If the flow files are stored in one of processor's watch directories there will be a never ending flow of events. It is also important to be aware that this processor must consume all events. The filtering must happen within the processor. This is because the HDFS admin's event notifications API does not have filtering.

### <a name="GetHDFSSequenceFile"></a>GetHDFSSequenceFile
Fetch sequence files from Hadoop Distributed File System (HDFS) into FlowFiles

### <a name="GetHTMLElement"></a>GetHTMLElement
Extracts HTML element values from the incoming flowfile's content using a CSS selector. The incoming HTML is first converted into a HTML Document Object Model so that HTML elements may be selected in the similar manner that CSS selectors are used to apply styles to HTML. The resulting HTML DOM is then "queried" using the user defined CSS selector string. The result of "querying" the HTML DOM may produce 0-N results. If no results are found the flowfile will be transferred to the "element not found" relationship to indicate so to the end user. If N results are found a new flowfile will be created and emitted for each result. The query result will either be placed in the content of the new flowfile or as an attribute of the new flowfile. By default the result is written to an attribute. This can be controlled by the "Destination" property. Resulting query values may also have data prepended or appended to them by setting the value of property "Prepend Element Value" or "Append Element Value". Prepended and appended values are treated as string values and concatenated to the result retrieved from the HTML DOM query operation. A more thorough reference for the CSS selector syntax can be found at "http://jsoup.org/apidocs/org/jsoup/select/Selector.html"

### <a name="GetHTTP"></a>GetHTTP
This processor fetches files via HTTP and creates FlowFiles from them.

### <a name="GetJMSQueue"></a>GetJMSQueue
This processor pulls messages from a JMS Queue, creating a FlowFile for each JMS message or bundle of messages, as configured.

### <a name="GetJMSTopic"></a>GetJMSTopic
This processor pulls messages from a JMS Topic, creating a FlowFile for each JMS message or bundle of messages, as configured.

### <a name="GetKafka"></a>GetKafka
This Processors polls Apache Kafka for data. When a message is received from Kafka, this Processor emits a FlowFile where the content of the FlowFile is the value of the Kafka message. If the message has a key associated with it, an attribute named kafka.key will be added to the FlowFile, with the value being the UTF-8 Encoded value of the Message's Key.

Kafka supports the notion of a Consumer Group when pulling messages in order to provide scalability while still offering a publish-subscribe interface. Each Consumer Group must have a unique identifier. The Consumer Group identifier that is used by NiFi is the UUID of the Processor. This means that all of the nodes within a cluster will use the same Consumer Group Identifier so that they do not receive duplicate data but multiple GetKafka Processors can be used to pull from multiple Topics, as each Processor will receive a different Processor UUID and therefore a different Consumer Group Identifier.

### <a name="GetMongo"></a>GetMongo
Creates FlowFiles from documents in MongoDB

### <a name="GetSFTP"></a>GetSFTP
This processor pulls files from an SFTP server and creates FlowFiles to encapsulate them.

### <a name="GetSNMP"></a>GetSNMP
Retrieves information from SNMP Agent and outputs a FlowFile with information in attributes and without any content.

### <a name="GetSolr"></a>GetSolr
Queries Solr and outputs the results as a FlowFile

### <a name="GetSplunk"></a>GetSplunk
Retrieves data from Splunk Enterprise.

### <a name="GetSQS"></a>GetSQS
Fetches messages from an Amazon Simple Queuing Service Queue

### <a name="GetTwitter"></a>GetTwitter
Pulls status changes from Twitter's streaming API

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
This processor attempts to identify the MIME Type used for a FlowFile. If the MIME Type can be identified, an attribute with the name 'mime.type' is added with the value being the MIME Type. If the MIME Type cannot be determined, the value will be set to 'application/octet-stream'. In addition, the attribute mime.extension will be set if a common file extension for the MIME Type is known.

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

### <a name="InferAvroShema"></a>InferAvroShema
Examines the contents of the incoming FlowFile to infer an Avro schema. The processor will use the Kite SDK to make an attempt to automatically generate an Avro schema from the incoming content. When inferring the schema from JSON data the key names will be used in the resulting Avro schema definition. When inferring from CSV data a "header definition" must be present either as the first line of the incoming data or the "header definition" must be explicitly set in the property "CSV Header Definition". A "header definition" is simply a single comma separated line defining the names of each column. The "header definition" is required in order to determine the names that should be given to each field in the resulting Avro definition. When inferring data types the higher order data type is always used if there is ambiguity. For example when examining numerical values the type may be set to "long" instead of "integer" since a long can safely hold the value of any "integer". Only CSV and JSON content is currently supported for automatically inferring an Avro schema. The type of content present in the incoming FlowFile is set by using the property "Input Content Type". The property can either be explicitly set to CSV, JSON, or "use mime.type value" which will examine the value of the mime.type attribute on the incoming FlowFile to determine the type of content present.

### <a name="InvokeHTTP"></a>InvokeHTTP
Making requests to remote HTTP servers. Supporting common HTTP methods. Storing results as new flowfiles upon success. Routing to failure on error.

An HTTP client processor that converts FlowFile attributes to HTTP headers with configurable HTTP method, URL, etc.

### <a name="InvokeScriptedProcessor"></a>InvokeScriptedProcessor
Experimental - Invokes a script engine for a Processor defined in the given script. The script must define a valid class that implements the Processor interface, and it must set a variable 'processor' to an instance of the class. Processor methods such as onTrigger() will be delegated to the scripted Processor instance. Also any Relationships or PropertyDescriptors defined by the scripted processor will be added to the configuration dialog. Experimental: Impact of sustained usage not yet verified.

### <a name="JoltTransformJSON"></a>JoltTransformJSON
Applies a list of Jolt specifications to the flowfile JSON payload. A new FlowFile is created with transformed content and is routed to the 'success' relationship. If the JSON transform fails, the original FlowFile is routed to the 'failure' relationship.

### <a name="ListenHTTP"></a>ListenHTTP
This processor starts an HTTP service that is used to receive FlowFiles from remote sources. The URL of the service is http://{hostname}:{port}/contentListener.

### <a name="ListenLumberjack"></a>ListenLumberjack
Listens for Lumberjack messages being sent to a given port over TCP. Each message will be acknowledged after successfully writing the message to a FlowFile. Each FlowFile will contain data portion of one or more Lumberjack frames. In the case where the Lumberjack frames contain syslog messages, the output of this processor can be sent to a ParseSyslog processor for further processing.

### <a name="ListenRELP"></a>ListenRELP
Listens for RELP messages being sent to a given port over TCP. Each message will be acknowledged after successfully writing the message to a FlowFile. Each FlowFile will contain data portion of one or more RELP frames. In the case where the RELP frames contain syslog messages, the output of this processor can be sent to a ParseSyslog processor for further processing.

### <a name="ListenSyslog"></a>ListenSyslog
Listens for Syslog messages being sent to a given port over TCP or UDP. Incoming messages are checked against regular expressions for RFC5424 and RFC3164 formatted messages. The format of each message is: (<PRIORITY>)(VERSION )(TIMESTAMP) (HOSTNAME) (BODY) where version is optional. The timestamp can be an RFC5424 timestamp with a format of "yyyy-MM-dd'T'HH:mm:ss.SZ" or "yyyy-MM-dd'T'HH:mm:ss.S+hh:mm", or it can be an RFC3164 timestamp with a format of "MMM d HH:mm:ss". If an incoming messages matches one of these patterns, the message will be parsed and the individual pieces will be placed in FlowFile attributes, with the original message in the content of the FlowFile. If an incoming message does not match one of these patterns it will not be parsed and the syslog.valid attribute will be set to false with the original message in the content of the FlowFile. Valid messages will be transferred on the success relationship, and invalid messages will be transferred on the invalid relationship.

### <a name="ListenTCP"></a>ListenTCP
Listens for incoming TCP connections and reads data from each connection using a line separator as the message demarcator. The default behavior is for each message to produce a single FlowFile, however this can be controlled by increasing the Batch Size to a larger value for higher throughput. The Receive Buffer Size must be set as large as the largest messages expected to be received, meaning if every 100kb there is a line separator, then the Receive Buffer Size must be greater than 100kb.

### <a name="ListenUDP"></a>ListenUDP
This processor listens for Datagram Packets on a given port and concatenates the contents of those packets together generating flow files

### <a name="ListFile"></a>ListFile
Retrieves a listing of files from the local filesystem. For each file that is listed, creates a FlowFile that represents the file so that it can be fetched in conjunction with ListFile. This Processor is designed to run on Primary Node only in a cluster. If the primary node changes, the new Primary Node will pick up where the previous node left off without duplicating all of the data. Unlike GetFile, this Processor does not delete any data from the local filesystem.

### <a name="ListHDFS"></a>ListHDFS
This processor retrieves a listing of files from HDFS. For each file that is listed in HDFS, creates a FlowFile that represents the HDFS file so that it can be fetched in conjunction with ListHDFS. This Processor is designed to run on Primary Node only in a cluster. If the primary node changes, the new Primary Node will pick up where the previous node left off without duplicating all of the data. Unlike GetHDFS, this Processor does not delete any data from HDFS.

### <a name="ListS3"></a>ListS3
Retrieves a listing of objects from an S3 bucket. For each object that is listed, creates a FlowFile that represents the object so that it can be fetched in conjunction with FetchS3Object. This Processor is designed to run on Primary Node only in a cluster. If the primary node changes, the new Primary Node will pick up where the previous node left off without duplicating all of the data.

### <a name="ListSFTP"></a>ListSFTP
Performs a listing of the files residing on an SFTP server. For each file that is found on the remote server, a new FlowFile will be created with the filename attribute set to the name of the file on the remote server. This can then be used in conjunction with FetchSFTP in order to fetch those files.

### <a name="LogAttribute"></a>LogAttribute
This processor reads the attributes on incoming FlowFiles and prints those attributes and their values to the log at the logging level specified by the user.

### <a name="MergeContent"></a>MergeContent
This processor merges a group of FlowFiles together into a "Bundle" based on a user-defined strategy and packages them into a single FlowFile. It is recommended that the processor be configured with only a single incoming connection, as groups of FlowFiles will not be created from FlowFiles in different connections. This processor updates the mime.type attribute as appropriate. After files have been merged by this processor, they can be unpackaged later using the UnpackContent processor.

### <a name="ModifyBytes"></a>ModifyBytes
This processor updates the content of a FlowFile by removing bytes from start or end of a file.

### <a name="ModifyHTMLElement"></a>ModifyHTMLElement
Modifies the value of an existing HTML element. The desired element to be modified is located by using CSS selector syntax. The incoming HTML is first converted into a HTML Document Object Model so that HTML elements may be selected in the similar manner that CSS selectors are used to apply styles to HTML. The resulting HTML DOM is then "queried" using the user defined CSS selector string to find the element the user desires to modify. If the HTML element is found the element's value is updated in the DOM using the value specified "Modified Value" property. All DOM elements that match the CSS selector will be updated. Once all of the DOM elements have been updated the DOM is rendered to HTML and the result replaces the flowfile content with the updated HTML. A more thorough reference for the CSS selector syntax can be found at "http://jsoup.org/apidocs/org/jsoup/select/Selector.html"

### <a name="MonitorActivity"></a>MonitorActivity
This processor monitors the flow for activity and sends out an indicator when the flow has not had any data for some specified amount of time and again when the flow's activity is restored.

### <a name="ParseSyslog"></a>ParseSyslog
Parses the contents of a Syslog message and adds attributes to the FlowFile for each of the parts of the Syslog message

### <a name="PostHTTP"></a>PostHTTP
This processor performs an HTTP post with the content of each incoming FlowFile.

### <a name="PublishAMQP"></a>PublishAMQP
Creates a AMQP Message from the contents of a FlowFile and sends the message to an AMQP Exchange.In a typical AMQP exchange model, the message that is sent to the AMQP Exchange will be routed based on the 'Routing Key' to its final destination in the queue (the binding). If due to some misconfiguration the binding between the Exchange, Routing Key and Queue is not set up, the message will have no final destination and will return (i.e., the data will not make it to the queue). If that happens you will see a log in both app-log and bulletin stating to that effect. Fixing the binding (normally done by AMQP administrator) will resolve the issue.

### <a name="PublishJMS"></a>PublishJMS
Creates a JMS Message from the contents of a FlowFile and sends it to a JMS Destination (queue or topic) as JMS BytesMessage.

### <a name="PublishKafka"></a>PublishKafka
Sends the contents of a FlowFile as a message to Apache Kafka. The messages to send may be individual FlowFiles or may be delimited, using a user-specified delimiter, such as a new-line.

### <a name="PublishMQTT"></a>PublishMQTT
Publishes a message to an MQTT topic

### <a name="PutAzureEventHub"></a>PutAzureEventHub
Sends the contents of a FlowFile to a Windows Azure Event Hub. Note: the content of the FlowFile will be buffered into memory before being sent, so care should be taken to avoid sending FlowFiles to this Processor that exceed the amount of Java Heap Space available.

### <a name="PutCassandraQL"></a>PutCassandraQL
Execute provided Cassandra Query Language (CQL) statement on a Cassandra 1.x or 2.x cluster. The content of an incoming FlowFile is expected to be the CQL command to execute. The CQL command may use the ? to escape parameters. In this case, the parameters to use must exist as FlowFile attributes with the naming convention cql.args.N.type and cql.args.N.value, where N is a positive integer. The cql.args.N.type is expected to be a lowercase string indicating the Cassandra type.

### <a name="PutCouchbaseKey"></a>PutCouchbaseKey
Put a document to Couchbase Server via Key/Value access.

### <a name="PutDistributedMapCache"></a>PutDistributedMapCache
Gets the content of a FlowFile and puts it to a distributed map cache, using a cache key computed from FlowFile attributes. If the cache already contains the entry and the cache update strategy is 'keep original' the entry is not replaced.'

### <a name="PutDynamoDB"></a>PutDynamoDB
Puts a document from DynamoDB based on hash and range key. The table can have either hash and range or hash key alone. Currently the keys supported are string and number and value can be json document. In case of hash and range keys both key are required for the operation. The FlowFile content must be JSON. FlowFile content is mapped to the specified Json Document attribute in the DynamoDB item.

### <a name="PutElasticsearch"></a>PutElasticsearch
Writes the contents of a FlowFile to Elasticsearch, using the specified parameters such as the index to insert into and the type of the document. If the cluster has been configured for authorization and/or secure transport (SSL/TLS) and the Shield plugin is available, secure connections can be made. This processor supports Elasticsearch 2.x clusters.

### <a name="PutEmail"></a>PutEmail
This processor sends an e-mail to configured recipients for each incoming FlowFile.

### <a name="PutFile"></a>PutFile
This processor writes FlowFiles to the local file system.

### <a name="PutFTP"></a>PutFTP
This processor sends FlowFiles via FTP to an FTP server.

### <a name="PutHBaseCell"></a>PutHBaseCell
Adds the Contents of a FlowFile to HBase as the value of a single cell

### <a name="PutHBaseJSON"></a>PutHBaseJSON
Adds rows to HBase based on the contents of incoming JSON documents. Each FlowFile must contain a single UTF-8 encoded JSON document, and any FlowFiles where the root element is not a single document will be routed to failure. Each JSON field name and value will become a column qualifier and value of the HBase row. Any fields with a null value will be skipped, and fields with a complex value will be handled according to the Complex Field Strategy. The row id can be specified either directly on the processor through the Row Identifier property, or can be extracted from the JSON document by specifying the Row Identifier Field Name property. This processor will hold the contents of all FlowFiles for the given batch in memory at one time.

### <a name="PutHDFS"></a>PutHDFS
This processor writes FlowFiles to an HDFS cluster. It will create directories in which to store files as needed based on the Directory property.

When files are written to HDFS, the file's owner is the user identity of the NiFi process, the file's group is the group of the parent directory, and the read/write/execute permissions use the default umask. The owner can be overridden using the Remote Owner property, the group can be overridden using the Remote Group property, and the read/write/execute permissions can be overridden using the Permissions umask property.

NOTE: This processor can change owner or group only if the user identity of the NiFi process has super user privilege in HDFS to do so.

NOTE: The Permissions umask property cannot add execute permissions to regular files.

### <a name="PutHiveQL"></a>PutHiveQL
Executes a HiveQL DDL/DML command (UPDATE, INSERT, e.g.). The content of an incoming FlowFile is expected to be the HiveQL command to execute. The HiveQL command may use the ? to escape parameters. In this case, the parameters to use must exist as FlowFile attributes with the naming convention hiveql.args.N.type and hiveql.args.N.value, where N is a positive integer. The hiveql.args.N.type is expected to be a number indicating the JDBC Type. The content of the FlowFile is expected to be in UTF-8 format.

### <a name="PutHTMLElement"></a>PutHTMLElement
Places a new HTML element in the existing HTML DOM. The desired position for the new HTML element is specified by using CSS selector syntax. The incoming HTML is first converted into a HTML Document Object Model so that HTML DOM location may be located in a similar manner that CSS selectors are used to apply styles to HTML. The resulting HTML DOM is then "queried" using the user defined CSS selector string to find the position where the user desires to add the new HTML element. Once the new HTML element is added to the DOM it is rendered to HTML and the result replaces the flowfile content with the updated HTML. A more thorough reference for the CSS selector syntax can be found at "http://jsoup.org/apidocs/org/jsoup/select/Selector.html"

### <a name="PutJMS"></a>PutJMS
This processor creates a JMS message from the contents of a FlowFile and sends the message to a JMS server.

### <a name="PutKafka"></a>PutKafka
This Processors puts the contents of a FlowFile to a Topic in Apache Kafka. The full contents of a FlowFile becomes the contents of a single message in Kafka. This message is optionally assigned a key by using the <Kafka Key> Property.

The Processor allows the user to configure an optional Message Delimiter that can be used to send many messages per FlowFile. For example, a \n could be used to indicate that the contents of the FlowFile should be used to send one message per line of text. If the property is not set, the entire contents of the FlowFile will be sent as a single message. When using the delimiter, if some messages are successfully sent but other messages fail to send, the FlowFile will be FORKed into two child FlowFiles, with the successfully sent messages being routed to 'success' and the messages that could not be sent going to 'failure'.

### <a name="PutKinesisFirehose"></a>PutKinesisFirehose
Sends the contents to a specified Amazon Kinesis Firehose. In order to send data to firehose, the firehose delivery stream name has to be specified.

### <a name="PutLambda"></a>PutLambda
Sends the contents to a specified Amazon Lamba Function. The AWS credentials used for authentication must have permissions execute the Lambda function (lambda:InvokeFunction).The FlowFile content must be JSON.

### <a name="PutMongo"></a>PutMongo
Writes the contents of a FlowFile to MongoDB

### <a name="PutRiemann"></a>PutRiemann
Send events to Riemann (http://riemann.io) when FlowFiles pass through this processor. You can use events to notify Riemann that a FlowFile passed through, or you can attach a more meaningful metric, such as, the time a FlowFile took to get to this processor. All attributes attached to events support the NiFi Expression Language.

### <a name="PutS3Object"></a>PutS3Object
Puts FlowFiles to an Amazon S3 Bucket

### <a name="PutSFTP"></a>PutSFTP
This processor sends FlowFiles via SFTP to an SFTP server.

### <a name="PutSlack"></a>PutSlack
The PutSlack processor sends messages to Slack, a team-oriented messaging service.

This processor uses Slack's incoming webhooks custom integration to post messages to a specific channel. Before using PutSlack, your Slack team should be configured for the incoming webhooks custom integration, and you'll need to configure at least one incoming webhook.

### <a name="PutSNS"></a>PutSNS
Sends the content of a FlowFile as a notification to the Amazon Simple Notification Service

### <a name="PutSolrContentStream"></a>PutSolrContentStream
This processor streams the contents of a FlowFile to an Apache Solr update handler. Any properties added to this processor by the user are passed to Solr on the update request. If a parameter must be sent multiple times with different values, properties can follow a naming convention: name.number, where name is the parameter name and number is a unique number. Repeating parameters will be sorted by their property name.

Example: To specify multiple 'f' parameters for indexing custom json, the following properties can be defined:

* split: /exams
* f.1: first:/first
* f.2: last:/last
* f.3: grade:/grade
This will result in sending the following url to Solr: 
split=/exams&f=first:/first&f=last:/last&f=grade:/grade

### <a name="PutSplunk"></a>PutSplunk
Sends logs to Splunk Enterprise over TCP, TCP + TLS/SSL, or UDP. If a Message Delimiter is provided, then this processor will read messages from the incoming FlowFile based on the delimiter, and send each message to Splunk. If a Message Delimiter is not provided then the content of the FlowFile will be sent directly to Splunk as if it were a single message.

### <a name="PutSQL"></a>PutSQL
Executes a SQL UPDATE or INSERT command. The content of an incoming FlowFile is expected to be the SQL command to execute. The SQL command may use the ? to escape parameters. In this case, the parameters to use must exist as FlowFile attributes with the naming convention sql.args.N.type and sql.args.N.value, where N is a positive integer. The sql.args.N.type is expected to be a number indicating the JDBC Type. The content of the FlowFile is expected to be in UTF-8 format.

### <a name="PutSQS"></a>PutSQS
Publishes a message to an Amazon Simple Queuing Service Queue

### <a name="PutSyslog"></a>PutSyslog
Sends Syslog messages to a given host and port over TCP or UDP. Messages are constructed from the "Message ___" properties of the processor which can use expression language to generate messages from incoming FlowFiles. The properties are used to construct messages of the form: (<PRIORITY>)(VERSION )(TIMESTAMP) (HOSTNAME) (BODY) where version is optional. The constructed messages are checked against regular expressions for RFC5424 and RFC3164 formatted messages. The timestamp can be an RFC5424 timestamp with a format of "yyyy-MM-dd'T'HH:mm:ss.SZ" or "yyyy-MM-dd'T'HH:mm:ss.S+hh:mm", or it can be an RFC3164 timestamp with a format of "MMM d HH:mm:ss". If a message is constructed that does not form a valid Syslog message according to the above description, then it is routed to the invalid relationship. Valid messages are sent to the Syslog server and successes are routed to the success relationship, failures routed to the failure relationship.

### <a name="PutTCP"></a>PutTCP
The PutTCP processor receives a FlowFile and transmits the FlowFile content over a TCP connection to the configured TCP server. By default, the FlowFiles are transmitted over the same TCP connection (or pool of TCP connections if multiple input threads are configured). To assist the TCP server with determining message boundaries, an optional "Outgoing Message Delimiter" string can be configured which is appended to the end of each FlowFiles content when it is transmitted over the TCP connection. An optional "Connection Per FlowFile" parameter can be specified to change the behaviour so that each FlowFiles content is transmitted over a single TCP connection which is opened when the FlowFile is received and closed after the FlowFile has been sent. This option should only be used for low message volume scenarios, otherwise the platform may run out of TCP sockets.

### <a name="PutUDP"></a>PutUDP
The PutUDP processor receives a FlowFile and packages the FlowFile content into a single UDP datagram packet which is then transmitted to the configured UDP server. The user must ensure that the FlowFile content being fed to this processor is not larger than the maximum size for the underlying UDP transport. The maximum transport size will vary based on the platform setup but is generally just under 64KB. FlowFiles will be marked as failed if their content is larger than the maximum transport size.

### <a name="QueryCassandra"></a>QueryCassandra
Execute provided Cassandra Query Language (CQL) select query on a Cassandra 1.x or 2.x cluster. Query result may be converted to Avro or JSON format. Streaming is used so arbitrarily large result sets are supported. This processor can be scheduled to run on a timer, or cron expression, using the standard scheduling methods, or it can be triggered by an incoming FlowFile. If it is triggered by an incoming FlowFile, then attributes of that FlowFile will be available when evaluating the select query. FlowFile attribute 'executecql.row.count' indicates how many rows were selected.

### <a name="QueryDatabaseTable"></a>QueryDatabaseTable
Execute provided SQL select query. Query result will be converted to Avro format. Streaming is used so arbitrarily large result sets are supported. This processor can be scheduled to run on a timer, or cron expression, using the standard scheduling methods, or it can be triggered by an incoming FlowFile. If it is triggered by an incoming FlowFile, then attributes of that FlowFile will be available when evaluating the select query. FlowFile attribute 'querydbtable.row.count' indicates how many rows were selected.

### <a name="ReplaceText"></a>ReplaceText
This processor updates the content of a FlowFile by evaluating a regular expression (regex) against the content and replacing the section of content that matches the regular expression with an alternate, user-defined, value.

### <a name="ReplaceTextWithMapping"></a>ReplaceTextWithMapping
This processor updates the content of a FlowFile by evaluating a Regular Expression against it and replacing the section of the content that matches the Regular Expression with some alternate value provided in a mapping file.

### <a name="ResizeImage"></a>ResizeImage
Resizes an image to user-specified dimensions. This Processor uses the image codecs registered with the environment that NiFi is running in. By default, this includes JPEG, PNG, BMP, WBMP, and GIF images.

### <a name="RouteHL7"></a>RouteHL7
Routes incoming HL7 data according to user-defined queries. To add a query, add a new property to the processor. The name of the property will become a new relationship for the processor, and the value is an HL7 Query Language query. If a FlowFile matches the query, a copy of the FlowFile will be routed to the associated relationship.

### <a name="RouteOnAttribute"></a>RouteOnAttribute
This processor routes FlowFiles based on their attributes using the NiFi Expression Language. Users add properties with valid NiFi Expression Language Expressions as the values. Each Expression must return a value of type Boolean (true or false).

Example: The goal is to route all files with filenames that start with ABC down a certain path. Add a property with the following name and value:

* property name: ABC
* property value: ${filename:startsWith('ABC')}
In this example, all files with filenames that start with ABC will follow the ABC relationship.

### <a name="RouteOnContent"></a>RouteOnContent
This processor applies user-added regular expressions to the content of a FlowFile and routes a copy of the FlowFile to each destination whose regular expression matches. The user adds properties where the name is the relationship that the FlowFile should follow if it matches the regular expression, which is defined as the property's value. User-defined properties do support the NiFi Expression Language, but in such cases, the results are interpreted as literal values, not regular expressions.

### <a name="RouteText"></a>RouteText
Routes textual data based on a set of user-defined rules. Each line in an incoming FlowFile is compared against the values specified by user-defined Properties. The mechanism by which the text is compared to these user-defined properties is defined by the 'Matching Strategy'. The data is then routed according to these rules, routing each line of the text individually.

### <a name="ScanAttribute"></a>ScanAttribute
This processor scans the specified attributes of FlowFiles, checking to see if any of their values are present within the specified dictionary of terms.

### <a name="ScanContent"></a>ScanContent
This processor scans the content of FlowFiles for terms that are found in a user-supplied dictionary file. If a term is matched, the UTF-8 encoded version of the term is added to the FlowFile using the matching.term attribute. This allows for follow-on processors to use the value of the matching.term attribute to make routing decisions and so forth.

### <a name="SegmentContent"></a>SegmentContent
This processor segments a FlowFile into multiple smaller segments on byte boundaries. Each segment is given attributes that can then be used by the MergeContent processor to reconstruct the original FlowFile.

### <a name="SelectHiveQL"></a>SelectHiveQL
Execute provided HiveQL SELECT query against a Hive database connection. Query result will be converted to Avro or CSV format. Streaming is used so arbitrarily large result sets are supported. This processor can be scheduled to run on a timer, or cron expression, using the standard scheduling methods, or it can be triggered by an incoming FlowFile. If it is triggered by an incoming FlowFile, then attributes of that FlowFile will be available when evaluating the select query. FlowFile attribute 'selecthiveql.row.count' indicates how many rows were selected.

### <a name="SetSNMP"></a>SetSNMP
Based on incoming FlowFile attributes, the processor will execute SNMP Set requests. When founding attributes with name like snmp$<OID>, the processor will atempt to set the value of attribute to the corresponding OID given in the attribute name

### <a name="SplitAvro"></a>SplitAvro
Splits a binary encoded Avro datafile into smaller files based on the configured Output Size. The Output Strategy determines if the smaller files will be Avro datafiles, or bare Avro records with metadata in the FlowFile attributes. The output will always be binary encoded.

### <a name="SplitContent"></a>SplitContent
This processor splits incoming FlowFiles by a specified byte sequence.

### <a name="SplitJson"></a>SplitJson
This processor splits a JSON File into multiple, separate FlowFiles for an array element specified by a JsonPath expression. Each generated FlowFile is comprised of an element of the specified array and transferred to relationship 'split,' with the original file transferred to the 'original' relationship. If the specified JsonPath is not found or does not evaluate to an array element, the original file is routed to 'failure' and no files are generated.

### <a name="SplitText"></a>SplitText
This processor splits a text file into multiple smaller text files on line boundaries, each having up to a configured number of lines.

### <a name="SplitXML"></a>SplitXML
This processor splits an XML file into multiple separate FlowFiles, each comprising a child or descendant of the original root element.

### <a name="SpringContextProcessor"></a>SpringContextProcessor
A Processor that supports sending and receiving data from application defined in Spring Application Context via predefined in/out MessageChannels.

### <a name="StoreInKiteDataset"></a>StoreInKiteDataset
Stores Avro records in a Kite dataset.

### <a name="TailFile"></a>TailFile
"Tails" a file, ingesting data from the file as it is written to the file. The file is expected to be textual. Data is ingested only when a new line is encountered (carriage return or new-line character or combination). If the file to tail is periodically "rolled over", as is generally the case with log files, an optional Rolling Filename Pattern can be used to retrieve data from files that have rolled over, even if the rollover occurred while NiFi was not running (provided that the data still exists upon restart of NiFi). It is generally advisable to set the Run Schedule to a few seconds, rather than running with the default value of 0 secs, as this Processor will consume a lot of resources if scheduled very aggressively. At this time, this Processor does not support ingesting files that have been compressed when 'rolled over'.

### <a name="TransformXML"></a>TransformXML
This processor transforms the contents of FlowFiles based on a user-specified XSLT stylesheet file. XSL versions 1.0 and 2.0 are supported.

### <a name="UnpackContent"></a>UnpackContent
This processor unpacks the content of FlowFiles that have been packaged with one of several different packaging formats, emitting one to many FlowFiles for each input FlowFile.

### <a name="UpdateAttribute"></a>UpdateAttribute
This processor updates the attributes of a FlowFile using properties or rules that are added by the user. There are two ways to use this processor to add or modify attributes. One way is the "Basic Usage"; this allows you to set default attribute changes that affect every FlowFile going through the processor. The second way is the "Advanced Usage"; this allows you to make conditional attribute changes that only affect a FlowFile if it meets certain conditions. It is possible to use both methods in the same processor at the same time.

### <a name="ValidateXML"></a>ValidateXML
This processor validates the contents of FlowFiles against a user-specified XML schema file.

### <a name="YandexTranslate"></a>YandexTranslate
Translates content and attributes from one language to another

If you have questions about a processor, I'd encourage you to download the binaries and start up Apache Nifi.  Now you can see the documentation for processors in [their documentation](https://nifi.apache.org/docs.html), which is now built with each release.  If you really want more information, let me know and I'll try to compile a more complete post about each and every processor.