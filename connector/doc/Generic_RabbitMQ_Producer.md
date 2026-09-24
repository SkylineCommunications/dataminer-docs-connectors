---
uid: Connector_help_Generic_RabbitMQ_Producer
---

# Generic RabbitMQ Producer

## About

The Generic RabbitMQ Producer connector facilitates sending messages to a RabbitMQ queue from any source within the DataMiner system. These messages can be available in files or retrieved from other DataMiner elements via [InterApp framework](https://docs.dataminer.services/develop/devguide/Core.InterAppCalls/InterAppCalls_Introduction.html).

## Key Features

- **File-based message queuing**: Enables sending data available in files to a RabbitMQ queue.
- **InterApp framework integration**: Supports retrieving messages from other DataMiner elements using the InterApp framework.
- **Message publishing**: Publishes the messages to the configured queue.

## Use Cases

### Integrating File-Based Data into RabbitMQ Workflows

**Challenge**: It can be difficult to incorporate data from various file formats into a RabbitMQ message queuing system.
**Solution**: The Generic RabbitMQ Producer connector automates the process of reading files from a directory and sending their contents as messages to a RabbitMQ queue.
**Benefit**: This connector streamlines the integration of file-based data sources into RabbitMQ workflows, enabling efficient message processing and distribution.

### Forwarding DataMiner Element Data to RabbitMQ

**Challenge**: Data generated or collected by other DataMiner elements needs to be exposed to external systems through a messaging platform, without relying on intermediate files.
**Solution**: Using the InterApp framework, this connector can receive messages directly from other DataMiner elements and publish them to the configured RabbitMQ queue.
**Benefit**: This enables real-time, in-memory integration between DataMiner and RabbitMQ-based systems, eliminating the overhead of file-based transfers and simplifying end-to-end data flows.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Generic_RabbitMQ_Producer_Technical).

### Prerequisites

- **DataMiner version 10.3 or higher** is required for compatibility with the Generic RabbitMQ Producer connector.
- **RabbitMQ username and password**: Required for RabbitMQ authentication.
