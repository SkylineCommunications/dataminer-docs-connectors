---
uid: Connector_help_META_WhatsApp_Messaging
---

# META WhatsApp Messaging

The META WhatsApp Messaging connector is part of the [META WhatsApp Messaging solution](). This connector is in charge of taking the alarm information retrieved from the ***META Alarm Detection*** script and send it to the contacts defined.

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

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. For this connector, it should be set to `https://graph.facebook.com`.
- **IP port**: The IP port of the destination. For this connector, it should be set to 443.

### Initialization

#### Prerequisites

All prerequisites are described in the [META WhatsApp Messaging solution installation guide]().

#### Installation

1. Once the element created automatically by the package installation is running, fill in the *Phone Number ID*, *WhatsApp Business ID*, and *Token* parameters on the **Configuration** page with the values you saved earlier.
1. In the Contacts table, add the phone numbers that should receive WhatsApp alarm notifications.

   > [!NOTE]
   > The numbers must start with the country code and exclude any non-numeric characters.

## How to Use

If everything went well during the installation and configuration, and an alarm occurs that matches the filtering criteria defined in the Correlation rule, the people in the Contacts table will receive an alarm message in their WhatsApp apps, informing them about the generated alarm.
