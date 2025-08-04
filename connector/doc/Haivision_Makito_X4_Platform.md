---
uid: Connector_help_Haivision_Makito_X4_Platform
---

# Haivision Makito X4 Platform

The Makito X4 Platform is a single solution for both video encoding and decoding. It combines the features available in the Makito X4 encoders and Makito X4 decoder.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |
| 1.0.0.x  | Support for firmware 1.6.0-x. | -        | -             |
| 1.0.0.x  | Added "Displayed Output Frames Stats", "Skipped Output Frames Stats", and "Replayed Output Frames Stats" columns to the "Decoder Statistics" tabke which allows alarming and trending. | -        | -             |

### Product Info

| Range   | Supported Firmware                         |
|---------|--------------------------------------------|
| 1.0.0.x | - Encoder: 1.7.0-49<br>- Decoder: 1.5.0-35 |
| 1.1.0.x | - Encoder: 1.7.0-49<br>- Decoder: 1.6.0-x |
| 1.1.1.x | - Encoder: 1.7.0-49<br>- Decoder: 1.6.0-x |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |
| 1.1.0.x | No              | Yes                 | -                 |                     |
| 1.1.1.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

To authenticate the connection to the device, fill in the credentials on the General page of the element.

## How to use

### Device Type Configuration

The connector functions either as an encoder or as a decoder. When credentials have been filled in correctly, system status information will be requested from the device. Based on the response data, the device will be automatically configured as encoder or decoder. However, you can manually override this setting by adjusting the **Device Type** parameter on the **General page**. Based on the configured device type, the connector will send different commands to the device. Additionally, different pages will be shown based on this setting.

### Poll Manager

This connector uses a **Poll Manager** to execute commands on certain configured intervals. You can adjust these intervals for every command by setting the required **Poll Frequency**.

You can also completely disable certain commands if these are not required.

### Debug

This connector has a **DEBUG** page, which can be consulted for more detailed communication or behind-the-scenes settings.

This page is hidden by default. To show or hide the page, use the **Show Debug Page** parameter on the General page.

### Other Parameters

On the **General** page of this connector, you can configure the username and password to access the device. You can also find some system status parameters and some configuration settings for the connector here.

The **Video Encoders** page, **Audio Encoders** page, **Encoder Streams** page, **Decoders** page, and **Decoder Streams** page contain all information related to the configured video encoders, audio encoders, encoder streams, decoders, and decoder streams, respectively. You can perform various actions via the context menu of the tables.
