---
uid: Connector_help_Haivision_Makito_X4_Platform
---

# Haivision Makito X4 Platform

The Makito X4 Platform is a single solution for both Video Encoding as Decoding, it combines all features available in the Makito X4 Encoders and Makito X4 Decoder.

## About

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info


|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |<ul><li>Encoder: 1.7.0-49</li><li>Decoder: 1.5.0-35</li></ul>       |


### System Info


|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *8443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

Credentials are required to authenticate on the device, these should be filled in on the General Page.

### Redundancy

There is no redundancy defined.


## How to use

The connector either functions as an Encoder or Decoder. When credentials have been filled in correctly, System Status information will be requested from the device.
Based on the response data the Device will be automatically configured as Encoder or Decoder.
However it's still possible to manualy override this setting by adjusting the **Device Type** parameter on the **General Page**.
Based on the configured Device Type the driver will send different commands to the device. Additionaly different pages will be shown based on this settings.

This connector uses a **Poll Manager** to execute commands on certain configured intervals. These intervals can be adjusted for every command by setting the required Poll Frequency.
It's also possible to completely disable certain commands if these would not be required.

This connector has a **DEBUG** page which can be consulted for more detailed communication or behind-the-scenes settings.
This page is hidden by default but can be shown or hidden by setting the **Show Debug Page** parameter on the General Page.

### Examples

*On the **General** page of this connector, you can configure the username and password to access the device.*
You can also find some System Status parameters and some driver configuration settings.

On the **Video Encoders** page you'll find all information related to the configured Video Encoders.
The Video Encoders Table has a **Context Menu** to perform various actions.

On the **Audio Encoders** page you'll find all information related to the configured Audio Encoders.
The Audio Encoders Table has a **Context Menu** to perform various actions.

On the **Encoder Streams** page you'll find all information related to the configured Encoder Streams.
The Encoders Streams has a **Context Menu** to perform various actions.

On the **Decoders** page you'll find all information related to the configured Decoders.
The Decoders Table has a **Context Menu** to perform various actions.

On the **Decoder Streams** page you'll find all information related to the configured Decoder Streams.
The Decoder Streams has a **Context Menu** to perform various actions.

