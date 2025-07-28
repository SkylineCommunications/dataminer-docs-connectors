---
uid: Connector_help_Telenor_EPM_MAM_Consumer_Technical
---

# Telenor EPM MAM Consumer

## About

In the Telenor DMS, MAM messages are stored inside RabbitMQ queues. This **Telenor EPM MAM Consumer** connector is used to retrieved those messages and forward them to the matching collector element.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

On the **Sources** page, a table list all the RabbitMQ servers monitored by this connector. New servers can be added and removed using a context menu. The queue name is identical for all the servers and can be configured on the **General** page.

The **Collectors** page displays a table containing all the collectors detected in the system and their current state. The path and access details to the folder containing the provisioning files can be configured on this same page.

The **Log** page can be used to configure the custom logging. The connector uses custom logging to display the messages received for specific devices. The log files are stored in the folder *C:\Skyline DataMiner\Telenor\Elements\<ElementName>\Logging*. The devices table is used to configure the list of devices for which the received messages should be logged. Via the right-click menu of the table, you can add devices to the table or remove them.