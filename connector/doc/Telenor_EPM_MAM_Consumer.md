---
uid: Connector_help_Telenor_EPM_MAM_Consumer
---

# Telenor EPM MAM Consumer
## About
This **Telenor EPM MAM Consumer** is used to collect messages stored in RabbitMQ queues and forward them to multiple **Telenor EPM Collector** elements.

To be aware of the collector elements available in the system, the connector will read provision files created by the **Telenor EPM Manager** element.

## Key Features
 - **Consume RabbitMQ Messages**: the connector can connect to multiple Rabbit MQ servers.
 - **Message forwarding**: the connector automatically detects to which collector the messages needs to be forwarded.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telenor_EPM_MAM_Consumer_Technical).