---
uid: Connector_help_Teleste_HDO101_TSEMP
---

# Teleste HDO101 TSEMP

HDO101 is an RF measurement switch. This switch module has two inputs with RF wideband detectors and one output.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Key Features      | Based on | System Impact  |
|--------------------|-------------------|----------|----------------|
| 1.0.0.x [Obsolete] | Initial version.  | -        | -              |
| 2.0.0.x [SLC Main] | Full refactoring. | -        | Full refactor. |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 2.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 2.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO101 device.
- **IP port**: The IP port of the HDO101 device.

### How to Use

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The element using the HDO101 connector has several data pages:

- On the **General** page, you can find all the details related to general information about the device, and you can set the device name.

- The **Monitoring** page contains two tables for analog and discrete alarm limits. You can configure those two tables.

- The **Adjustment** page contains the most important parameters. Here you can configure measurement switch.
