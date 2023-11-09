---
uid: Connector_help_Shelly_Bulb_RGBW
---

# Shelly Bulb RGBW

Dimmable lighting with RGB colors and white temperatures that can be connected to any network through wifi.

Features
No HUB required.

Bulb supports 110V and 220V power supplies.

Two light modes – Colour and White

Dimmable white light by fine-tuning your brightness.


## About

### Version Info

**This subsection can only be omitted for an exported connector**


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>http polling communication</li></ul>         |-         |-         |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |        |


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
  - **IP port**: [The IP port of the destination. (default: *80*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

On the General page, optionally add the username & password for access to the device.

### Redundancy

There is no redundancy defined.

## How to use

Under the Light page you can toggle the light on or off and see its power usage.
In there you can change the mode from 'white' to 'rbgw'. 
Depending on the mode you can then adjust the light temperature under the *White Mode* page or adjust the color in the *Color Mode* page.

The page *Settings* will allow you to configure its wifi and Backup wifi configuration.

> [!NOTE]
> Changed to the page *Settings* can break the connection between the device and the network/dma. Be careful when changing these settings.

## Notes

The device supports MQTT, but this is currently not implemented in the driver.
