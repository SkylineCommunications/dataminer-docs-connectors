---
uid: Connector_help_Teleste_HDO907
---

# Teleste HDO907

The HDO907 is a transmitter. The **Teleste HDO907** connector can be used to display and configure information of the related device.

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

## About

### Version Info

| Range              | Description     | DCF Integration | Cassandra Compliant |
|--------------------|-----------------|-----------------|---------------------|
| 1.0.0.x [SLC Main] | Initial version | No              | Yes                 |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO907 device.
- **IP port**: The IP port of the HDO907 device.

### Usage

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.
