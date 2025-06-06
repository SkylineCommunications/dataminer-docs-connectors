---
uid: Connector_help_Generic_RabbitMQ_Producer
---

# Generic RabbitMQ Producer

## About

The Generic RabbitMQ Producer connector facilitates sending files from a specified directory to a RabbitMQ queue. It simplifies file-based integration with RabbitMQ for message queuing.

## Key Features

- **File-based message queuing**: Enables sending files as messages to a RabbitMQ queue.
- **Message publishing**: Publishes the content of files as messages to the configured queue.
- **File management**: Deletes files after they are processed.
- **Configurable processing**: Allows configuration of the file processing interval.

## Use Cases

### Integrating File-Based Data into RabbitMQ Workflows

**Challenge**: It can be difficult to incorporate data from various file formats into a RabbitMQ message queuing system.

**Solution**: The Generic RabbitMQ Producer connector automates the process of reading files from a directory and sending their contents as messages to a RabbitMQ queue.

**Benefit**: This connector streamlines the integration of file-based data sources into RabbitMQ workflows, enabling efficient message processing and distribution.

### Automating Data Transfer from Legacy Systems

**Challenge**: Data from legacy systems that output data as files needs to be transferred to a modern messaging system.

**Solution**: By monitoring a designated directory, this connector can automatically capture files generated by legacy systems and publish their data to RabbitMQ.

**Benefit**: This connector provides a simple way to connect legacy systems to RabbitMQ, facilitating data migration and system modernization.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Generic_RabbitMQ_Producer_Technical).

### Prerequisites

- **DataMiner version 10.3 or higher** is required for compatibility with the Generic RabbitMQ Producer connector.
- **RabbitMQ username and password**: Required for RabbitMQ authentication.
