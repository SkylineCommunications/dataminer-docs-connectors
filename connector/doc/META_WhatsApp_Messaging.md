---
uid: Connector_help_META_WhatsApp_Messaging
---

# META WhatsApp Messaging

The META WhatsApp Messaging connector acts as a link between the DataMiner System Alarm Console and the WhatsApp API. It allows users to receive the alarms they want directly in their WhatsApp apps.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 20.0                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation

See [Installing the META WhatsApp Messaging solution](https://docs.dataminer.services/user-guide/Standard_Apps/Monitoring_Solutions/META_WhatsApp_Messaging/META_WhatsApp_Messaging_Installation.html).

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. For this connector, it should be set to `https://graph.facebook.com`.
- **IP port**: The IP port of the destination. For this connector, it should be set to 443.

## How to use

See [Using the META WhatsApp Messaging solution](https://docs.dataminer.services/user-guide/Standard_Apps/Monitoring_Solutions/META_WhatsApp_Messaging/Using_META_WhatsApp_Messaging.html).
