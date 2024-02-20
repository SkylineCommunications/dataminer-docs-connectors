---
uid: Connector_help_Teleste_HDO613_TSEMP
---

# Teleste HDO613 TSEMP

The HDO613 is an RF forward path amplifier that supports frequencies up to 1218 MHz. The module provides a fixed gain of 29 dB with a single output port. The module has a front panel RF test point.
The HDO613 module’s wide gain range and clever control of the RF attenuation and gain stages allow it to be used as a universal amplifier block in headend and hub systems. The amplifier is mechanically compatible with HDX002 and HDX003 installation frames.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Key Features      | Based on | System Impact |
|--------------------|-------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version.  | -        | -             |

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

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO613 device.
- **IP port**: The IP port of the HDO613 device.

### How to Use

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The element using the HDO613 connector has several data pages:

- On the **General** page, you can find all the details related to general information about the device, and you can set the device name.

- The **Monitoring** page contains two tables for analog and discrete alarm limits. You can configure those two tables.

- The **Adjustment** page contains the most important parameters. Here you can configure amplifier.
