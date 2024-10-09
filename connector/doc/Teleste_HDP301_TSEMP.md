---
uid: Connector_help_Teleste_HDP301_TSEMP
---

# Teleste HDP301 TSEMP

The HDP301 is a switched‐mode power supply module for the HDO optical headend platform. The **Teleste HDP301 TSEMP** connector can be used to display and configure information of this device.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Key Features      | Based on | System Impact  |
|--------------------|-------------------|----------|----------------|
| 1.0.0.x [Obsolete] | Initial version.  | -        | -              |
| 2.0.0.x            | Full refactoring. | -        | Full refactor. |
| 2.0.1.x [SLC Main] | Full refactoring. | -        | -              |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 2.0.0.x | -                  |
| 2.0.1.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 2.0.0.x | No              | Yes                 | -                 | -                   |
| 2.0.1.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDP301 device.
- **IP port**: The IP port of the HDP301 device.

### How to Use

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The element using the HDP301 connector has several data pages:

- On the **General** page, you can find all the details related to general information about the device, and you can set the device name.

- The **Monitoring** page contains two tables for analog and discrete alarm limits. You can configure those two tables.

- The **Measurements** page contains HDP301 power measurements. It also keeps track of peaks.
