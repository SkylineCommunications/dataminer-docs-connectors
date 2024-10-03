---
uid: Connector_help_Nokia_NSP
---

# Nokia NSP

This connector is used to collect alarm data from the **Nokia NSP** system, which is a network management system that is designed to manage Nokia proprietary devices.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact                                                               |
|--------------------|------------------|----------|-----------------------------------------------------------------------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -                                                                           |
| 2.0.0.x            | EPM version.     | 1.0.0.2  | This version impacts the UX and functionality. It is intended for EPM only. |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 23.11              |
| 2.0.0.x | 23.11              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 2.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. This should always start with `https://`.
- **IP port**: Default: *8443*.

##### Initialization

In order to perform requests, you first need to configure the **User Name** and **Password** parameters on the General page.

## How to use

### General

This page is divided in two sections, **XML APIConnection**, and **JMS Connection**.

#### XML APIConnection

In this section, the **User Name** and **Password** need to be defined, so that the connector can request data.

#### JMS Connection

In order to establish a live events JMS connection with the NSP, fill in the following parameters:

- **JMS Host IP**, **JMS Port**, **JMS User Name**, **JMS Password**, and **JMS Client ID**.

- **JMS Directory Path**: The path where all the required .jar, .java, and .class files are available (see [Notes](#notes)).

- **JMS Java Executable Path**: The path of the java.exe.

- **JMS Keystore File Name**: The file name of the .keystore file that must be located in the JMS directory.

- **JMS Topic**: The topic to connect to. Possible topics: 5620-MAP-topic, 5620-SAM-topic-xml-filtered, 5620-AUX-SAM-topic,5650-CPAM-topic-xml, 5620-SAM-topic, 5620-GRAPH-topic,5620-SAM-topic-xml, 5620-SAM-topic-xml-general, 5620-SAM-topic-xml-file, 5620-SAM-topic-xml-fault, 5620-SAM-topic-xml-stats.

- **JMS Connection Type**: If *Persistent* is selected, the connection will be durable.

After you have configured these parameters, click the **Connect** button to establish a connection.

### Alarms

This page contains the **Alarms Filtering Path** parameter, which allows you to to define a path to an .xml file containing a fault filter.

This .xml file is used to retrieve only some filtered alarms defined by the user. It must have the structure detailed in section **11.6.2** of the **Nokia NSP XML API Developer Guide**.

If no path is defined to the .xml file, or if the file does not have the correct structure, the connector will retrieve all alarms present in the system.

The retrieved information is displayed in the **Alarms** table. If a **JMS Connection** is established, this table will be **updated live**.

### Probable Cause/Alarm Name/Alarm Type Configuration

By default, for the columns **Probable Cause/Alarm Name/Alarm Type** in the Alarms table, what is retrieved from the device are the IDs of the respective columns. On these configuration pages, you can define descriptions for these IDs, to be shown in the Alarms table for these columns.

For example, on the **Probable Cause Configuration** page, to **add** a new entry to the **Alarm Probable Cause** table, first fill in the **Alarm Probable Cause ID** and **Alarm Probable Cause Description** parameters (both of these parameters need to be unique), then click **Add entry**. You can also **edit** an existing description in the **Description** column, and you can **remove** an entry with the **Delete Entry** button in the table.

### Polling Configuration

On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table.

### In range **2.0.0.X**

  The UX has been re-arranged to have the same look and feel as other EPM collectors, which is comprised of making the **General page** a landing page with an overview of entities in the connector and **all relevant settings** moved to the **Configuration section** of the connector.

  #### Configuration

  This section contains most of the settings in the connector that are crucial to the way the connector works, Here you will be able to configure the:

  - **Entity Export/Import Settings**: These sections allow the exporting of the configuration files and importing of the provisioning files.

    - **Entity Export** and **Entity Import**: These parameters allow you to enable/disable the exporting and importing feature.
    - **Export Directory** and **Entity Import Directory**: It is necessary to specify the paths where the files will be exported and imported.
    - **Entity Export Directory Type** and **Entity Import Directory Type**: Specify whether the export/import paths are **local or remote**. Just so you know, for the remote file handling to work, you must enter the credentials for the system in the System Credentials section and enter the path to the remote directory in the Export Directory or Import Directory parameter. The path must be shared/accessible, or this feature will not work.
    - **Apply Button**: This button allows the user to manually export/import the files.

- **System Credentials**: This section is to be used if the element is configured to a remote file location.

  - **System Username**: The username of the user with access to the directory. If no domain is specified, the domain from the element's DMA location will be used.
  - **System Password**: The password of the user to access the remote directory.
 
- **HTTP Credentials**: This section contains the parameters that were previously on the general page.

  - **User Name**: This allows the user to configure the user name to communicate with the endpoint.
  - **Password**: This allows the user to configure the password to communicate with the endpoint.

 - The **Polling Configuration Section** in the previous range is now a sub-page in the **Configuration Section**. All settings from the previous range still apply here.

 - The **JMS Connection Section** in the previous range is now a sub-page in the **Configuration Section**. All settings from the previous range still apply here. Additionally, there is a new parameter **JMS Heartbeat Timer** that allows the user to configure the interval that checks the **Heartbeat from the JMS endpoint**.
    
## Notes

For the **JMS Connection**, some prerequisites must be met:

- Via the **JMS Directory Path** specified on the General page, as mentioned above, the connector has to be able to access specific **.jar files**:

  - samOss.jar
  - jul-to-slf4j-1.7.25.jar
  - slf4j-api-2.0.7.jar
  - javax.servlet-api-3.0.1.jar
  - logback-classic-1.2.3.jar
  - logback-core-1.2.3.jar
  - postgresql-42.1.4.jar
  - tomcat-juli-9.0.30.jar

- In addition, the **JmsTest.java** file is required, edited according to the customer properties. The file must be edited as follows on the *initializeConnection* method:

  ```java
  Properties properties = new Properties();
   properties.setProperty("jboss.naming.client.ejb.context", "true");
   properties.setProperty("java.naming.provider.url", "remote://"+ hostIp +":" + hostPort);
   properties.setProperty(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
   properties.setProperty("java.naming.factory.initial", "org.wildfly.naming.client.WildFlyInitialContextFactory");
   properties.setProperty("jboss.naming.client.connect.timeout", "60000");
   properties.setProperty("jboss.naming.client.connect.options.org.xnio.Options.SASL_POLICY_NOPLAINTEXT", "false");
   properties.setProperty("jboss.naming.client.remote.connectionprovider.create.options.org.xnio.Options.SSL_ENABLED", "true");
   properties.setProperty("jboss.naming.client.connect.options.org.xnio.Options.SSL_STARTTLS", "true");
  ```

  After you have made these changes, compile the .java file on the directory with the following command:

  ```txt
  javac -classpath .;samOss.jar;slf4j-api-2.0.7.jar;logback-classic-1.2.3.jar;logback-core-1.2.3.jar;jul-to-slf4j-1.7.25.jar;javax.servlet-api-3.0.1.jar;postgresql-42.1.4.jar;tomcat-juli-9.0.30.jar JmsTest.java
  ```

- The required .class file is the **JmsTest.class**, compiled from the JmsTest.java file.

- Finally, the .keystore file is also required.
