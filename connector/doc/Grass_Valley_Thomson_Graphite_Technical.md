---
uid: Connector_help_Grass_Valley_Thomson_Graphite_Technical
---

# Grass Valley Thomson Graphite Technical

## About

### Version Info

| Range | Key Features | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x | Initial version. | No | Yes |

### Product Info

| Range | Supported Firmware | Supported Hardware |
|--|--|--|
| 1.0.0.x   | 14.10.X | 6.0 |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a Serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port**: By Default *UDP*.
- **IP address/host**: The polling IP of the destination.
- **IP port**: The IP port of the destination, by default *2901*.

## How to use

Depending on the version of the connector, it can consist of the data pages detailed below.

### General (v.1.0.0.x+)

On this page, check the device Connection Status and general details (Firmware Version, etc...).

### Inputs (v.1.0.0.x+)

This page displays the **Inputs** Table details, used to periodically poll the Input informations and allow for Input configuration.

Inputs can be added, edited or removed by right clicking on the table and selecting the desired action.
- **Add input**: By specifying the Type, input number and the polling frequency it add a new Input to read.
- **Configure input**: It allows for editing the Input configuration and sends the changes to the device.
- **Delete selected input(s)**: It deletes the selectedInputs from the Inputs table. Does not affect Device.