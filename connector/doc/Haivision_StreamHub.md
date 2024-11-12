---
uid: Connector_help_Haivision_StreamHub
---

# Haivision StreamHub

The Haivision StreamHub connector will interface with StreamHubs using a REST API. This connector monitors all incoming video streams, manage the transcoding of these streams, and monitor all outgoing video streams. The Haivision StreamHub Series is a range of transceiver platforms that are used to receive, decode, and distribute live video streams coming from any Haivision encoder/transmitter or third-party system.

Up to 8 videos can be decoded simultaneously thanks to 8 SDI outputs, while up to 32 IP outputs are supported to re-stream the video contents over LAN or WAN to CDNs, media servers, streaming platforms, social networks, IRDs, or other StreamHubs. Each StreamHub also features video encoding and transcoding capability, so that incoming feeds can be adapted to the desired output format.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                        |
|-----------|-------------------------------------------|
| 1.0.0.x   | 4.3										|

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the destination (Note: in case https:// is enabled - please prefix this IP Address with 'httpss//' in the element settings).
- **IP port**: 8893. Specify the **default IP port of the StreamHub RESTful API service**, not the IP port of the web interface.
- **Bus address**: If the proxy server has to be bypassed, specify *ByPassProxy.*

### Initialization

To make sure the element can poll data and display information, you need to fill in the **API key** and the **Web Interface IP** on the **General** page.

- The **Web Interface IP** must comply with the following format: 10.10.10.10:8888. By default, the IP port of the web interface is 8888. Note that 10.10.10.10 is merely an example IP address; you will need specify your web interface IP address instead.
- To obtain the **API key**, go to the web interface and log in with your credentials. Then go to admin \> REST API doc and copy the API key located in the top-right corner of the page.

### Redundancy

No redundancy is defined in the connector.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

HTTP REST calls (GET and POST) are used to retrieve the device information. To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting View \> Stream Viewer.
The **Poll Settings** page allows you to disable certain poll items if they are not relevant (Eg. 'Logs'). It also allows you to increase or decrease the polling interval for each item.

