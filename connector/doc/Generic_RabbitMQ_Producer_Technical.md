---
uid: Connector_help_Generic_RabbitMQ_Producer_Technical
---

# Generic RabbitMQ Producer

The Generic RabbitMQ Producer connector facilitates the sending of files from a specified directory to a RabbitMQ queue. It locates the designated directory, reads any files present, publishes their content as messages to the configured queue, and subsequently deletes the files. This enables a simple file-based integration with RabbitMQ for message queuing.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |RabbitMQ 4.0.x, 4.1.x         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

#### Configuration Page

* **RabbitMQ Username**: User name for RabbitMQ authentication.
* **RabbitMQ Password**: Password for RabbitMQ authentication.
* **IP Address**: The hostname or IP address of the RabbitMQ server.
* **Port**: The port number of the RabbitMQ server.
* **Queue Name**: The name of the queue to which messages will be sent.
* **Virtual Host**: The virtual host of the RabbitMQ server.

* **Import Directory Path**: The directory where files to be published are located, it can be a local or a remote directory.
* **Import Directory Type**: The type of the directory where the files to be published are located, either Local or Remote.
* **System Username**: The system username to be used if **Import Directory Type** is set to Remote.
* **System Password**: The system password to be used if **Import Directory Type** is set to Remote.

## How to use

Based on the interval time configured in **File Process Interval** (1 hour by default), the connector will try to process the files and send them to the specified Queue, this is going to be reflected on the **Processing State** parameter.
This process can be manually started by pressing the **Process Files** button, this will start the process immediately, without waiting for the next interval.

After the files have been processed, all files processed will be available on the **Messages** table, this table will contain the name of the file and the time of its process.
The retention time for this table can be configured with the **Message Retention Time** parameter, and the table can be cleaned up based on that time, or completely cleared with **Clean Now and Clear** buttons respectively.

The file process can be disabled or enabled with the **File Process Status** parameter.

### Examples

On the **General** page of this connector, you can see the a table with messages that have been sent previously, you can configure the retention period of these messages to keep old messages if needed.

The **Configuration** page contains the configuration for the RabbitMQ server connection and queue, it also contains the configuration for the directory where the files to be processed will be, and finally the configuration to enable or disable the file processing as well as configuring its frequency.