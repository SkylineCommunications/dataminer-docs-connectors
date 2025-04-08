---
uid: Connector_help_Generic_RabbitMQ_Producer_Technical
---

# Generic RabbitMQ Producer

## About

The Generic RabbitMQ Producer connector facilitates the sending of files from a specified directory to a RabbitMQ queue. It locates the designated directory, reads any files present, publishes their content as messages to the configured queue, and subsequently deletes the files. This enables a simple file-based integration with RabbitMQ for message queuing.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **Configuration** page, configure the following parameters to set up the element:

- **RabbitMQ Username**: User name for RabbitMQ authentication.
- **RabbitMQ Password**: Password for RabbitMQ authentication.
- **IP Address**: The hostname or IP address of the RabbitMQ server.
- **Port**: The port number of the RabbitMQ server.
- **Queue Name**: The name of the queue to which messages will be sent.
- **Virtual Host**: The virtual host of the RabbitMQ server.
- **Import Directory Path**: The directory where files to be published are located, which can be a local or a remote directory.
- **Import Directory Type**: The type of the directory where the files to be published are located, either *Local* or *Remote*.
- **System Username**: The system username to be used if **Import Directory Type** is set to *Remote*.
- **System Password**: The system password to be used if **Import Directory Type** is set to *Remote*.

## How to use

Based on the interval time configured in **File Process Interval** (1 hour by default) on the **Configuration** page, the connector will try to process the files and send them to the specified queue. This will be reflected in the **Processing State** parameter.

The file processing can be disabled or enabled with the **File Process Status** parameter.

You can start the processing manually by clicking the **Process Files** button. This will start the processing immediately, without waiting for the next interval.

After the files have been processed, all processed files will be listed in the **Messages** table on the **General** page. This table will contain the name of the file and the time when it was processed.

The retention time for this table can be configured with the **Message Retention Time** parameter, and the table can be cleaned up based on that time or completely cleared with the **Clean Now** and **Clear** buttons, respectively.
