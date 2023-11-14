---
uid: Connector_help_Imagine_Communications_Platinum_VX_CQ_Router
---

# Imagine Communications Platinum Router VX CQ Router

This is an SNMP connector that is used to monitor and control the device **Imagine Communications Platinum VX CQ.**

A platinum router is a matrix that can switch different types of sources (audio/video). The matrix can also be divided into several "virtual" matrixes, which each create a new level.

This connector requires **DataMiner version 8.5.3** or higher.

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
| 1.0.0.x | Yes             | Yes                  | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses an SNMP connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *62.245.205.52.*
- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, e.g. *public*.
- **Set community string**: The community string used when setting values on the device, e.g. *private*.

#### Serial secondary connection

This connector uses a smart serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The default value is *52116*.
- **Bus address**: A one-based number between 1 and 16, 16 included. Defines the level that is monitored by the connector.

> [!NOTE]
>
> - **Ignore** the **Timeout of a single command** and **Number of retries** settings (the latter should be *0*).
> - The element timeout can be configure in the **advanced element settings**.

### Configuration in case the matrix remains empty

In case the matrix remains empty after you have created the element, check if the IP address, bus address, and port are correct. Also verify if the DataMiner software is version 8.0.5.4 or later.

If this is the case and all settings seem correct, check the element log file and verify if there is no firewall blocking traffic on port 52116.

## How to Use

### Frame Controller Page

This page contains all the basic information about the frame, as well as some configuration/status subpages: Switchpoint, Power Supply and Fan, SNMP, Network, and Clock.

### Slot 1 PV 32x32 Page

This page contains the all input/output tables related to slot 1. Note that these are not linked to the matrix: the matrix tables are the source/destinations tables found on the routing subpages.

### Slot 2 PV-CQ-16 Page

This page contains the various parameters and tables related to slot 2. It includes the advanced settings for video and audio on separate subpages, as well as the Audio TSG and Miscellaneous sections.

### Faults Page

This page contains the Trap Outstanding Table, listing the current alarms across all 3 modules. For more detailed information about the faults, you can look at the subpages, which include every possible frame fault and slot 2 fault. (Slot 1 faults will be added in a next iteration).

### Routing Page

This page contains the basic LRC parameters and the channels table. This page also has the Destinations and Sources subpages, containing the respective tables.

### Destination Channels Page

This page contains the destination channels table.

### Matrix Page

This page contains the matrix.

### Labels Page

This page contains the  matrix labels table.

## Notes

- Once the element has been created, the connector shows the connected crosspoints on the configured level. You can change the connected input for an output by clicking the new input. The Platinum Router will then automatically disconnect the originally connected input in order to connect the new input. This means that the connector will not send a disconnect command. It is currently not possible to disconnect a connected input, so the connector will never send a disconnect command. All communication happens through the LRC (Logical Router Control) protocol, which also sends notifications when a change occurs, so that changes are updated in real time.
- All sets are (currently) done ONLY on the level that is being monitored.
