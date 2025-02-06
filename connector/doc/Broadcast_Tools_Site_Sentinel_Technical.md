---
uid: Connector_help_Broadcast_Tools_Site_Sentinel
---

# Broadcast Tools Site Sentinel

The Site Sentinel® 16 G2 is a robust, full-featured, web-enabled sixteen channel remote control featuring a desktop/mobile browser compatible web interface (HTML5.) The system is equipped with 16 metering inputs (0 to 10 VDC), four virtual metering channels, 16 optically-isolated status (logic) inputs, 33 programmable SPDT relays which may be configured for ON, OFF and pulsed operation, four temperature probe inputs, one internal temperature sensor, stereo silence sensor, and power failure input. Includes built-in support for email alarms and SNMP.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |       |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection - Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Initialization

No additional configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

An SNMP connection is used to retrieve all relevant data needed to monitor the Site Sentinel.

The **Meter** table on the **Meters** page contains custom columns (**Calibration Formula**, **Calibration Multiplier**, and **Expected Calculated Value**) that can be used to alter the incoming **Value** from the device. If no alteration is needed, leave the columns with their default values.
