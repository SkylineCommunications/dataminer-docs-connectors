---
uid: Connector_help_Generic_RabbitMQ_Producer_Technical
description: Technical reference for the Generic RabbitMQ Producer connector, covering configuration, file-based processing, and InterApp framework integration.
---

# Generic RabbitMQ Producer

## About

The Generic RabbitMQ Producer connector facilitates sending messages to a RabbitMQ queue from any source within the DataMiner system. Messages can be read from files in a specified directory or received from other DataMiner elements via the [InterApp framework](https://docs.dataminer.services/develop/devguide/Core.InterAppCalls/InterAppCalls_Introduction.html), and are then published to the configured queue.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **Configuration** page, configure the following parameters to set up the element:

- **RabbitMQ Username**: User name to authenticate with the RabbitMQ broker.
- **RabbitMQ Password**: Password to authenticate with the RabbitMQ broker.
- **IP Address**: The hostname or IP address of the RabbitMQ server.
- **Port**: The port number of the RabbitMQ server.
- **Queue Name**: The name of the queue to which messages will be published.
- **Virtual Host**: The virtual host of the RabbitMQ server.
- **Import Directory Path**: The directory where the files to be published are located, which can be a local or a remote directory.
- **Import Directory Type**: The type of the directory where the files to be published are located, either *Local* or *Remote*.
- **System Username**: The system username to be used if **Import Directory Type** is set to *Remote*.
- **System Password**: The system password to be used if **Import Directory Type** is set to *Remote*.

After configuring the required parameters described above, click the **Connect** button on the **General** page. This will establish the connection and enable the connector to start publishing messages to the specified RabbitMQ queue. The **Message** parameter on the **General** page will display the current status of the connection.

> [!IMPORTANT]
> If the producer cannot connect to the RabbitMQ broker, it will try to reconnect based on the configured retry policy. Currently, the retry policy is hardcoded and set to 3 retries. If the connector cannot establish the connection after the specified number of retries, it will report a connection failure in the **Message** parameter on the **General** page. To retry the connection, click the **Connect** button again.

## How to Use

There are two processing methods available: file-based processing (*File Mode*) and InterApp framework-based processing (*Inter-Element Mode*). This setting is available in the **Processing Mode** parameter on the **Configuration** page.

Depending on the chosen processing method, the connector will either process files from the specified directory or receive messages from other DataMiner elements using the InterApp framework.

### File-Based Processing

Based on the interval time configured in **File Process Interval** (1 hour by default) on the **File Settings** page, the connector will try to process the files and send them to the specified queue. This will be reflected in the **Processing State** parameter.

The file processing can be disabled or enabled with the **File Process Status** parameter.

The table **Messages** on the **File Processing History** page will display all the processed files along with their processing time. The retention time for this table can be configured with the **Message Retention Time** parameter, and the table can be cleaned up based on that time or completely cleared with the **Clean Now** and **Clear** buttons, respectively.

### InterApp Framework-Based Processing

The connector can also receive messages from other DataMiner elements using the InterApp framework and publish them to the specified RabbitMQ queue. This allows for real-time, in-memory integration without relying on intermediate files.

To enable InterApp framework-based processing, configure the necessary parameters on the **Configuration** page and ensure that the connection to the RabbitMQ broker is established. Currently, it is only possible to troubleshoot issues related to InterApp framework-based processing through the element log file.