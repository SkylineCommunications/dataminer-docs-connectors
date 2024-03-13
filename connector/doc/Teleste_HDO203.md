---
uid: Connector_help_Teleste_HDO203
---

# Teleste HDO203

HDO203 is a dual receiver module for fibre optic return path (upstream) links in CATV networks. It is installed into HDX installation frame. HDO203 has an integrated alarm receiver to enable a monitoring data of AC800 FTTLA node or CXE880 node. The **Teleste HDO203** connector can be used to display and configure information of this device.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.73               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO203 device.
- **IP port**: The IP port of the HDO203 device.

### How to Use

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The element using the HDO203 connector has a General, Monitoring, and Adjustment page.

- On the **General** page, you can find all the details related to general information about the device, and you can set the device name.

- The **Monitoring** page contains two tables for analog and discrete alarm limits. You can configure those two tables.

- The **Node 1** page contains information about Node 1.

- The **Node 2** page contains information about Node 2.

- The **Adjustment** page contains the most important parameters. Here you can configure and monitor receivers.
