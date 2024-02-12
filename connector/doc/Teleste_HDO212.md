---
uid: Connector_help_Teleste_HDO212
---

# Teleste HDO212

The HDO212 is a dual receiver module for fibre optic return path links in CATV networks. The module contains an integrated route backup function and has an extended frequency range to fulfil DOCSIS 3.1 requirements. The **Teleste HDO212** connector can be used to display and configure information of the related device.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
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

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO212 device.
- **IP port**: The IP port of the HDO212 device.

### How to Use

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The element using the HDO212 connector has a General, Monitoring, and Adjustment page.

- On the **General** page, you can find all the details related to general information about the device, and you can set the device name.

- The **Monitoring** page contains two tables for both analog and discrete alarm limits. You can configure those two tables.

- The **Adjustment** page contains the most important parameters. Here, you can configure and monitor receivers.
