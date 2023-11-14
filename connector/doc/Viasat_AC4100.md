---
uid: Connector_help_Viasat_AC4100
---

# Viasat AC4100

This connector can be used to monitor and configure a Viasat AC4100 ACU (Antenna Control Unit) device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.2.0.3                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device. Default: *6100*.

#### Smart-Serial Connection

This connector uses a smart-serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device. Default: *4133*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The **General** page displays general info about the device (System Model, Software Version, etc.).
The **Positioning** page displays info about the current position of the ACU and the tracking configuration.
All the alarms and warnings are displayed on the **Faults** page.

This connector uses two communication methods with the ACU:
 - A **TCP** poll connection: the connector polls data from the ACU at a regular interval. Some set commands can also be sent towards the ACU.
 - A **UDP** push connection: the ACU pushes the data towards the DataMiner element at a regular interval. To keep this connection open, the connector sends a *Keep Alive* message towards the ACU at a regular interval (that interval can be configured using the **Keep Alive Period** parameter). Some set commands can also be sent towards the ACU.

 Here's a summary of how the different parameters are retrieved:

 |Page|TCP poll| UDP push|
 |-|-|-|
 |General|-|All parameters|
 |Status|-|All parameters|
 |Positioning|<ul><li>Azimuth Mode</li><li>Elevation Mode</li><li>Azimuth Pedestal Stow</li><li>Elevation Pedestal Stow</li><li>Tilt Pedestal Stow</li><li>Azimuth Pedestal Mode</li><li>Elevation Pedestal Mode</li><li>Tilt Pedestal Mode</li><li>**All set commands**</li></ul>|All other parameters|
 |Faults|Alarms Table|Faults Table|
 |Interlock|Interlocks Table|-|