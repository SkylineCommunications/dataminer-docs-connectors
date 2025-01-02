---
uid: Connector_help_SISELECTRON_SR1
---

# Siselectron SR1

This is a DataMiner connector for the Siselectron SR1, a rack mount server which utilizes Synamedia's Media Edge Gateway which has Decoding, Encoding Transcoding/Processing, and other features.
## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | Initial version | - | - |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | v06.03.01 (Media Edge Gateway)         |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default value: *8443*).

### Initialization

On the "Authentication" page, an "Username" and "Password" must be provided in order to connect with the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays the main "Channels" table that is shown at the front of the device's GUI.


