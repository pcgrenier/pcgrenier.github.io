---
layout: post
title: "Developing a Custom Apache Nifi Processor-Unit Tests (Part I)"
date: 2015-04-04 16:54:52 +0000
author: Chad Zobrisky
comments: true
sharing: true
footer: true
description: How to write unit tests in Apache Nifi.
keywords: Apache Nifi, apache nifi, Nifi, Processors, Unit Tests, unit testing
categories: [Apache Nifi, Processors, Unit Tests]
---


The Apache Nifi framework has built in unit testing with Junit using test runners.  They have a few examples in their code base, but learning first hand really helps.  In this post we'll go over adding unit tests to the [JSON Processor]({{ site.url }}/developing-a-custom-apache-nifi-processor-json/) that we developed previously.

To start, we'll checkout the JSON Processor code from [Github](https://github.com/pcgrenier/nifi-examples) and then open it up in your favorite text editor.  There is already a test package/folder in the project that contains a unit test, [rocks.nifi.examples.processors/JsonProcessorTest.java](https://github.com/pcgrenier/nifi-examples/blob/master/src/test/java/rocks/nifi/examples/processors/JsonProcessorTest.java).

When unit testing in Apache Nifi, there are a few items on top of the normal JUnit annotations that are required.  While you can unit test with just JUnit, using the built in method in Apache Nifi makes it much easier.  In a future post we'll show you how to unit test using Mockito and JUnit to test helper methods where actually invoking a full processor seems excessive, or if you just don't want to use Nifi's test runner.

<!-- more -->
The first thing to do to unit test Apache Nifi is grabbing the necessary dependencies from maven.

{% codeblock lang:xml pom.xml https://github.com/pcgrenier/nifi-examples/blob/master/pom.xml#L42 %}
		<dependency>
            <groupId>org.apache.nifi</groupId>
            <artifactId>nifi-mock</artifactId>
            <version>${nifi.version}</version>
            <scope>test</scope>
        </dependency>

{% endcodeblock %}

After including the nifi-mock dependency, there will be a few includes from the org.apache.nifi.utils package that will be necessary to import; mainly TestRunner, TestRunners and MockFlowFile.

Since we are using JUnit, the usual tags apply for defining a test function inside the class and we'll use the @Test for this one, although the other annotations can be used.  After adding the JUnit tag, there are a few requirements that Nifi puts on you in order to utilize the test runners they have provided.  The first is to create a test runner to use and then to set a flow file or flow file content inorder to run the processor.  In this example, we are using a ByteArrayInputStream as the flow file content, although you could use a JSON file in a resource folder just as well.  

Once a test runner is created, you can set flow file properties on it using `runner.setProperties(PropertyDescriptor)` method and can enqueue a file using `runner.enqueue(content)`.  Then you can run the test runner and make assertions.

Nifi makes it easy to test assertions with some built in assertions for flowfiles.  You can test the flowfile was transfered to the appropriate relationship and get the flowfile to test for expected attributes and content.

Below is how we test the JSON Processor, with a typical test setup for Apache Nifi.

{% codeblock lang:java JSON Processor Unit Test https://github.com/pcgrenier/nifi-examples/blob/master/src/test/java/rocks/nifi/examples/processors/JsonProcessorTest.java JsonProcessorTest.java %}
@org.junit.Test
    public void testOnTrigger() throws IOException {
        // Content to be mock a json file
        InputStream content = new ByteArrayInputStream("{\"hello\":\"nifi rocks\"}".getBytes());
        
        // Generate a test runner to mock a processor in a flow
        TestRunner runner = TestRunners.newTestRunner(new JsonProcessor());
        
        // Add properites
        runner.setProperty(JsonProcessor.JSON_PATH, "$.hello");
        
        // Add the content to the runner
        runner.enqueue(content);
        
        // Run the enqueued content, it also takes an int = number of contents queued
        runner.run(1);
        
        // All results were processed with out failure
        runner.assertQueueEmpty();
        
        // If you need to read or do aditional tests on results you can access the content
        List<MockFlowFile> results = runner.getFlowFilesForRelationship(JsonProcessor.SUCCESS);
        assertTrue("1 match", results.size() == 1);
        MockFlowFile result = results.get(0);
        String resultValue = new String(runner.getContentAsByteArray(result));
        System.out.println("Match: " + IOUtils.toString(runner.getContentAsByteArray(result)));
        
        // Test attributes and content
        result.assertAttributeEquals(JsonProcessor.MATCH_ATTR, "nifi rocks");
        result.assertContentEquals("nifi rocks");
        
    }
{% endcodeblock %}

Watch for our next post about unit testing Apache Nifi with Mockito and JUnit without using nifi's testrunner class.