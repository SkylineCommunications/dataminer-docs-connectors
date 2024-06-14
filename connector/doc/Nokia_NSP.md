---
uid: Connector_help_Nokia_NSP
---

# Nokia NSP

This connector is used to collect alarm data from the **Nokia NSP** system, which is a network management system that is designed to manage Nokia proprietary devices.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 23.11              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

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

The connector contains the following data pages:

- **General**: This page is divided in two sections:
  - **XML APIConnection** , that contains the **User Name** and **Password** parameters. If these parameters are not defined, the connector cannot request any data.
  - **JMS Connection**
    - In order to establish a live events JMS connection with the NSP the following parameters need to be filled:
      - **JMS Host IP**, **JMS Port**, **JMS User Name**, **JMS Password**,**JMS Client ID**
      - **JMS Directory Path** The specified path where all the required .jar, .java and .class files are available (you can find more info about this directory on the **Notes** section).
      - **JMS Java Executable Path** The specified path of the java.exe.
      - **JMS Keystore File Name** The file name of the .keystore file name that must be located on the JMS Directory.
      - **JMS Topic** The topic to connect to.Possible Topics: 5620-MAP-topic, 5620-SAM-topic-xml-filtered, 5620-AUX-SAM-topic,5650-CPAM-topic-xml, 5620-SAM-topic, 5620-GRAPH-topic,5620-SAM-topic-xml, 5620-SAM-topic-xml-general, 5620-SAM-topic-xml-file,5620-SAM-topic-xml-fault, 5620-SAM-topic-xml-stats.
      - **JMS Connection Type** If Persistent is selected it makes the connection durable.
    - After all these parameters are correctly configured you can press the **Connect** button to establish a connection.
        
- **Alarms**: Contains the **Alarms Filtering Path** parameter, which allows you to to define a path to an .xml file containing a fault filter. This .xml file is used to retrieve only some filtered alarms defined by the user. It must have the structure detailed in section **11.6.2** of the **Nokia NSP XML API Developer Guide**. If no path is defined to the .xml file, or if the file does not have the correct structure, the connector will retrieve all alarms present in the system. The retrieved information is displayed in the **Alarms** table. If **JMS Connection is establish this table will be lively updated**.

- **Probable Cause Configuration/Alarm Name Configuration/Alarm Type Configuration**: By default, for the columns **Probable Cause/Alarm Name/Alarm Type** in the Alarms table, what is retrieved from the device are the IDs of the respective columns. On these configuration pages, you can define descriptions for these IDs, to be shown in the Alarms table for these columns.

  For example, on the **Probable Cause Configuration** page, to **add** a new entry to the **Alarm Probable Cause** table, first fill in the **Alarm Probable Cause ID** and **Alarm Probable Cause Description** parameters (both of these parameters need to be unique), then click **Add entry**. You can also **edit** an existing description in the **Description** column, and you can **remove** an entry with the **Delete Entry** button in the table.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table.
## Notes
For the **JMS Connection** some pre requesites must be followed.
As metioned above on the **JMS Directory Path** there are some .jar files that are required. 
The required .jar files required are the following:
- samOss.jar, jul-to-slf4j-1.7.25.jar, slf4j-api-2.0.7.jar, javax.servlet-api-3.0.1.jar, logback-classic-1.2.3.jar, logback-core-1.2.3.jar, postgresql-42.1.4.jar, tomcat-juli-9.0.30.jar
The required .java file is the JmsTest.java file edited according to the customer properties.
The edit that must be done in order for the connection to work on theJmsTest.java file is on the  _initializeConnection_ method and it is the folowing:

`Properties properties = new Properties();
 properties.setProperty("jboss.naming.client.ejb.context", "true");
 properties.setProperty("java.naming.provider.url", "remote://"+ hostIp +":" + hostPort);
 properties.setProperty(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
 properties.setProperty("java.naming.factory.initial", "org.wildfly.naming.client.WildFlyInitialContextFactory");
 properties.setProperty("jboss.naming.client.connect.timeout", "60000");
 properties.setProperty("jboss.naming.client.connect.options.org.xnio.Options.SASL_POLICY_NOPLAINTEXT", "false");
 properties.setProperty("jboss.naming.client.remote.connectionprovider.create.options.org.xnio.Options.SSL_ENABLED", "true");
 properties.setProperty("jboss.naming.client.connect.options.org.xnio.Options.SSL_STARTTLS", "true");`
 
After these changes are made the .java file needs to be compiled on the directory with the following comand:
_javac -classpath .;samOss.jar;slf4j-api-2.0.7.jar;logback-classic-1.2.3.jar;logback-core-1.2.3.jar;jul-to-slf4j-1.7.25.jar;javax.servlet-api-3.0.1.jar;postgresql-42.1.4.jar;tomcat-juli-9.0.30.jar JmsTest.java_

An example code is available at internal docs.
The required .class file is the JmsTest.class compiled from JmsTest.java file.
The other required files is the .keystore file.


