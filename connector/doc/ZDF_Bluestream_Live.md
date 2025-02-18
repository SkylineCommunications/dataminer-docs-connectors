---
uid: Connector_help_ZDF_Bluestream_Live
---

# ZDF Bluestream Live

Bluestream-Live (BL) is an **editorial tool** with which **event live streams are registered and functionally managed**. The system can be accessed from the internal ZDF network. Bluestream-Live is on the one hand an interface for registration, management, and control of all live streams, Live2File recordings, and social meta broadcasts (Facebook, Youtube, Yuzzit, Twitch, TikTok, etc.), and on the other hand a large collection of APIs between the systems involved such as the broadcast automation ScadaMon (Bluestream Importer = CoyoNet_API), Sophora (live stream service), ECMS (additional event management system ARD + ZDF), PTMD-Service (Player Technical Metadata Service), etc.

In short, Bluestream-Live is the **middleware** that receives all status changes in real time and delivers their specially formed metadata (application-related formatted) via API to all components affected for the respective case at ZDF. It also receives metadata from externally connected systems, converts it where possible, and returns the expected metadata in response.

The **coyonet_api** and **coyonet247_api** are the REST interfaces of Bluestream-Live and Bluestream24/7, which are contacted every 1-30 seconds via GET queries by the CoyoNet scheduler, which is today a ScadaMon scheduler called Bluestream Importer (Daemon).

This connector provides access to the planning data for the 24/7 streams so that the exclusions technically realized in the SAWs (i.e. sending "cardboard" instead of live video content) can be displayed in a scheduler view in DataMiner and thus checked.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **General** page, configure the **User Name** and **Password** to be able to access the API.

## How to use

HTTP calls are used to retrieve the API information.

On the **General** page of this connector, you can configure the username and password to access the API.

The **Events** page contains information about all 24/7 future events. Every hour the old events will be automatically removed based on the configured **Events Storage Time**.
