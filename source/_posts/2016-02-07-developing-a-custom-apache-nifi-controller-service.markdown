---
layout: post
title: "Developing a Custom Apache Nifi Controller Service"
date: 2016-02-07 00:37:57 +0000
author: Phillip Grenier
comments: true
sharing: true
footer: true
description: How to develop a custom Apache Nifi controller service. The example in this post will utilize Java Properties files.
keywords: Apache Nifi, apache nifi, Nifi, controller service, properties, Apache Nifi example, Apache Nifi tutorial, nifi tutorial, nifi controller service example
categories: [Apache Nifi, Controller service]
---

Controller services are shared between processors, other controller services and reporting tasks. Normally they provide access to a shared resource, such as a database or ssl context, or externally managed content. This post will cover the basics of a controller service through a simple example. This example will take a file path that contains one or more properties files, and provide a processor access to those properties. The full source is hosted on [Github](https://github.com/pcgrenier/nifi-examples/tree/sample-processor).

<!-- more -->

## Setup

This project will use a more advanced maven structure than the simple one used in the [developing a custom processor]({{site.url}}//developing-a-custom-apache-nifi-processor-json) post.  If you have looked at the processor post you'll see that most of the setup for services is very similar.  

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

I won't go into details on the pom files but the general idea is that you want a seperate nar for the api interface and the service itself, this allows something much smaller to be used as a dependency in your other bundles. So the sample-bundle-nar will pull in the sample-processor and sample-controller-service packages. The sample-controller-service-api-nar will just pull in the sample-controller-service-api.

## The Controller Service API Interface

{% codeblock lang:java Controller Service API https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service-api/src/main/java/rocks/nifi/examples/PropertiesFileService.java PropertiesFileService.java %}
public interface PropertiesFileService extends ControllerService{
    String getProperty(String key);
}
{% endcodeblock %}

This is just a simple interface that extends nifi's ControllerService. We also provide the only entry point to processors, the getProperty function.  This is similar to the current services in Apache Nifi such as [DBCPService.java](https://raw.githubusercontent.com/apache/nifi/master/nifi-nar-bundles/nifi-standard-services/nifi-dbcp-service-api/src/main/java/org/apache/nifi/dbcp/DBCPService.java) providing the getConnection() function.

## The Controller Service

If you have read the [developing a custom processor]({{site.url}}//developing-a-custom-apache-nifi-processor-json) post a lot of this will be review. Controller services provide the same interfaces for configuration and validation. The initialization method only differs in taking a ControllerServiceInitializationContext.

Just like with the processors, tags are useful for finding your controller services. The capability description annotation provides a simple explanation of what the controller service will provide.

{% codeblock lang:java Controller Service https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service/src/main/java/rocks/nifi/examples/StandardPropertiesFileService.java StandardPropertiesFileService.java %}
@Tags({"nifirocks", "properties"})
@CapabilityDescription("Provides a controller service to manage property files.")
public class StandardPropertiesFileService extends AbstractControllerService implements PropertiesFileService{
{% endcodeblock %}

Next we create the property descriptors. One will take the file or directory holding the property files, the other will be how often to check. Unlike processors controller services do not contain relationships.

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

The next step is the onConfigured function which will read the properties set and call any other necessary functions needed to start the service.  We just read the two properties we have, configUri and reloadIntervalMilli, and then call loadPropertiesFile().  After the properties file is loaded, we start up a file watcher and executer so that the properties can be dynamic and not just read in at startup.  

{% codeblock lang:java Conroller Service https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-controller-service/src/main/java/rocks/nifi/examples/StandardPropertiesFileService.java StandardPropertiesFileService.java %}
@OnEnabled
public void onConfigured(final ConfigurationContext context) throws InitializationException{
    log.info("Starting properties file service");
    configUri = context.getProperty(CONFIG_URI).getValue();
    reloadIntervalMilli = context.getProperty(RELOAD_INTERVAL).asTimePeriod(TimeUnit.MILLISECONDS);

    // Initialize the properties
    loadPropertiesFiles();

    fileWatcher = new SynchronousFileWatcher(Paths.get(configUri), new LastModifiedMonitor());
    executor = Executors.newSingleThreadScheduledExecutor();
    FilesWatcherWorker reloadTask = new FilesWatcherWorker();
    executor.scheduleWithFixedDelay(reloadTask, 0, reloadIntervalMilli, TimeUnit.MILLISECONDS);

}

{% endcodeblock %}

To see the other private functions you can refer to the github code.  

The last step in the process is to create a processor to use the service.  This is exactly the same as creating a normal processor, but in this instance we want to add some specifics to use the PropertiesFileService.  To do this, we just grab a reference from context of the Controller Service, and then call the getProperty(propertyName) function.  We are just going to get the property and add it to the nifi flowfile properties so it is available to other processors down the line for now.  To specify which property we want we will add a PropertyDescriptor so that the user can set it in the Nifi UI, and another PropertyDescriptor to specify which PropertiesFileService to get the property value from.

{% codeblock lang:java Controll Service Processor https://github.com/pcgrenier/nifi-examples/blob/sample-processor/sample-processor/src/main/java/rocks/nifi/examples/processors/ControllerServiceProcessor.java ControllerServiceProcessor.java %}

public static final PropertyDescriptor PROPERTY_NAME = new PropertyDescriptor.Builder()
            .name("Property Name")
            .required(true)
            .addValidator(StandardValidators.NON_EMPTY_VALIDATOR)
            .build();

    public static final PropertyDescriptor PROPERTIES_SERVICE = new PropertyDescriptor.Builder()
            .name("Properties Service")
            .description("System properties loader")
            .required(false)
            .identifiesControllerService(PropertiesFileService.class)
            .build();
.......

@Override
public void onTrigger(final ProcessContext context, final ProcessSession session) throws ProcessException {
    final ProcessorLog log = this.getLogger();
    final AtomicReference<String> value = new AtomicReference<>();

    final String propertyName = context.getProperty(PROPERTY_NAME).getValue();
    final PropertiesFileService propertiesService = context.getProperty(PROPERTIES_SERVICE).asControllerService(PropertiesFileService.class);
    final String property = propertiesService.getProperty(propertyName);
    log.info("Property = " + property);


    FlowFile flowfile = session.get();
    // Write the results to an attribute

    if(property != null && !property.isEmpty()){
        flowfile = session.putAttribute(flowfile, "property", property);
    }

    session.transfer(flowfile, SUCCESS);
}

{% endcodeblock %}

Once you have the actual service and processor written, if you have followed the directory setup in the source code, you are good to go!  Just build your service project(mvn clean install), from the root pom.xml directory.  Then copy the nar, from the sample-bundle-nar/target/ directory, into your Apache Nifi instance lib directory, .  Once copied, start/restart Apache Nifi and you now have your service available as usual to be used!

## Configuring the Service

Once you have deployed the service nar bundle, go to the Controller Settings in the upper right of the web gui.

{% img /images/nifi-controller-settings.png %}

Then search or select the Controller Services tab and click the '+' button on the upper right of the model.  You can either search for the StandardPropertiesFileService, or just select it since there aren't many services.  From there configure the service as needed.

{% img /images/controller-service.png %}

Once the service is configured, add the ControllerServiceProcessor to the flow and configure the PropertyName and PropertyService, the name of the property that you want from the Java properties file and the PropertiesService that you just setup.

{% img /images/controller-processor.png %}

And that is pretty much it for configuring and setting up a service for use in a flow.  Now you just use the Flow file attribute as you would any other attribute.  This could be extended to grab multiple properties, maybe all of the from a file, and set them as Flow file attributes.  This is just a basic example showing how you can create a controller service that fits your needs.

If you have any questions about custom services, let us know below or at info@nifi.rocks!