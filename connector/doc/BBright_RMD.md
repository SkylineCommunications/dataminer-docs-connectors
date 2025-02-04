---
uid: Connector_help_BBright_RMD
---

# BBright RMD

This connector implements the BBright RMD API. Communication happens via HTTP using JSON format.

## About

### Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|---------------|
| 1.0.0.x | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.0.2.0                |

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
- **IP port**: Default: *80*.
- **Bus address**: Default: *bypassproxy.*

### Initialization

The API requires the use of a token for authentication. You can get the API token in the web GUI of the device by going to **ADMIN** > **Server** and clicking **REST API TOKEN**.

Copy this token to the **Authentication Token** parameter on the **General** page of the DataMiner element.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the General page, the token used for the communication should be specified.

With this connector, you will be able to monitor everything for the channels, including streams and ETR 290 metrics. Different metrics are available for TS, SDI, SRT, and ST 2110.

It is currently not possible to edit the channel configuration with this connector. However, the following commands are available:

- Get List Of Channels
- Start/Stop Decoding
- Start/Stop Monitoring
- Delete Channel
- Reset ETR 290 Stats
- Get Alarms
- Get Logs
- Create Channel
