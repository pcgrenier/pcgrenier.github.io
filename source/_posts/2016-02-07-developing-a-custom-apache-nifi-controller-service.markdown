---
layout: post
title: "Developing a Custom Apache Nifi Controller Service"
date: 2016-02-07 00:37:57 +0000
author: Phillip Grenier
comments: true
sharing: true
footer: true
description: How to develop a custom Apache Nifi controller service. The example in this post will utilize Java Properties files.
keywords: Apache Nifi, apache nifi, Nifi, controller service, properties
categories: [Apache Nifi, Controller service]
---

Controller services are shared between processors, controller services and reporting tasks. Normally they provide access to a shared resource, or externally managed content. We will cover the basics of a controller service through a simple example. This example with take a file path that contains one or more properties files, and provide a processor access to those properties. The full source is hosted on [Github](https://github.com/pcgrenier/nifi-examples/tree/sample-processor).

<!-- more -->

## Setup

This project will use a more advanced maven structure then the simple one used in the [developing a custom processor]({{site.url}}//developing-a-custom-apache-nifi-processor-json) post.

{% codeblock Apache Nifi Controller Servcie Folder Structure %}
./sample-bundle
├── pom.xml
├── sample-bundle-nar
│   ├── pom.xml
│   └── src
├── sample-controller-service
│   ├── pom.xml
│   └── src
├── sample-controller-service-api
│   ├── pom.xml
│   └── src
├── sample-controller-service-api-nar
│   ├── pom.xml
│   └── src
└── sample-processor
    ├── pom.xml
    └── src
{% endcodeblock %}

I will not go into details on the pom files but the general idea is that you want a seperate nar for the api interface. This allows something much smaller to be used as a dependency in your other bundles. So the sample-bundle-nar will pull in the sample-processor and sample-controller-service packages. The sample-controller-service-api-nar will just pull in the sample-controller-service-api.

## The Controller Service API Interface

{% codeblock lang:java Controller Service API https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service-api/src/main/java/rocks/nifi/examples/PropertiesFileService.java PropertiesFileService.java %}
public interface PropertiesFileService extends ControllerService{
    String getProperty(String key);
}
{% endcodeblock %}

Again not much to talk about here, simple interface that extends nifi's ControllerService. We also provide the only entry point to processors, the getProperty function.

## The Controller Service

Again if you have read the [developing a custom processor]({{site.url}}//developing-a-custom-apache-nifi-processor-json) post a lot of this will be review. Controller services provide the same interfaces for configuration and validation. The initialization method only differs in taking a ControllerServiceInitializationContext.

Just like with the processors, tags are useful for finding your controller services. The capability description annotation provides a simple explanation of what the controller service will provide.

{% codeblock lang:java Controller Service https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service/src/main/java/rocks/nifi/examples/StandardPropertiesFileService.java StandardPropertiesFileService.java %}
@Tags({"nifirocks", "properties"})
@CapabilityDescription("Provides a controller service to manage property files.")
public class StandardPropertiesFileService extends AbstractControllerService implements PropertiesFileService{
{% endcodeblock %}

Next we create the property descriptors. One will take the file or directory holding the property files, the other will describe how often to check. Unlike processors controller services do not contain relationships.

{% codeblock lang:java Controller Service https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service/src/main/java/rocks/nifi/examples/StandardPropertiesFileService.java StandardPropertiesFileService.java %}
public static final PropertyDescriptor CONFIG_URI = new   PropertyDescriptor.Builder()
        .name("Configuration Directory")
        .description("Configuration directory for properties files.")
        .defaultValue(null)
        .addValidator(StandardValidators.NON_EMPTY_VALIDATOR)
        .build();

public static final PropertyDescriptor RELOAD_INTERVAL = new PropertyDescriptor.Builder()
        .name("Reload Interval")
        .description("Time before looking for changes")
        .defaultValue("60 min")
        .required(true)
        .addValidator(StandardValidators.TIME_PERIOD_VALIDATOR)
        .build();

private static final List<PropertyDescriptor> serviceProperties;

static{
    final List<PropertyDescriptor> props = new ArrayList<>();
    props.add(CONFIG_URI);
    props.add(RELOAD_INTERVAL);
    serviceProperties = Collections.unmodifiableList(props);
}

{% endcodeblock %}
