---
uid: Connector_help_Teleste_HDO908
---

# Teleste HDO908

The HDO908 is a transmitter. The **Teleste HDO908** connector can be used to display and configure information of the related device. This device has 2 configurable inputs.

## About

A **serial** connection is used in order to successfully retrieve and configure the information of the device. There are also different possibilities available for **alarm monitoring** and **trending**.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main] | Initial version | No                  | Yes                     |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the HDO908 device.
- **IP port**: The IP port of the HDO908 device.

### How to Use

HDO908 connector is structured by 3 pages (General, monitoring and adjustment page).

All general details information about the device, you can see on **general** page. Also, setting device name is also supported on general page.
**Monitoring** page contains two tables for both analog and discreet alarm limits. User can configure those two tables.
**Adjustment** page contains all important parameters. There, user can adjust parameters related to transmitting signal. 

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.
