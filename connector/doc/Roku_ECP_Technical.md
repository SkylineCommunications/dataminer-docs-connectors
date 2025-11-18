---
uid: Connector_help_Roku_ECP_Technical
---

# Roku ECP

The Roku ECP (External Control Protocol) connector enables DataMiner to monitor and control Roku streaming devices through Roku’s native HTTP-based API. It provides full visibility into device information, installed applications, and active playback sessions, while allowing operators to send remote control commands directly from the DataMiner platform.

## About

### Version Info

| Range                | Key Features                  | Based On     | System Impact     |
|----------------------|-------------------------------|--------------|-------------------|
| 1.0.0.x              | Initial version.              | -            | -                 |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | -                           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |


## Configuration

### HTTP Connection

This connector communicates with Roku devices using HTTP requests over port 8060, which is the default Roku ECP port.


## How to use

No credentials are required, only that the device is enable for remote control using the API.
The element dynamically uses the IP address configured for the Roku device within the element settings, so the IP entered during element creation is not important.
On the **General** page, there is a text field named **Device IP** where you can enter the Roku device’s IP address. This automatically adds the entry to the **Devices** table.
Once the device has been added, the information is refreshed every minute.