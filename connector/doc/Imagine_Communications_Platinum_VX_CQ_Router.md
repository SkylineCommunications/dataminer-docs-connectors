---
uid: Connector_help_Imagine_Communications_Platinum_VX_CQ_Router
---

# Imagine Communications Platinum Router VX CQ Router

This is an snmp connector that is used to monitor and control the device **Imagine Communications Platinum VX CQ.**

## About

A platinum router is a matrix that can switch different types of sources (Audio/Video). The matrix can also be divided into several "virtual" matrixes, which each create a new level.

This connector requires **DataMiner version 8.5.3** or higher.

### Version Info

| **Range** | **Description**                                         | **DCF Integration** | **Cassandra Compliant** |
|------------------|---------------------------------------------------------|---------------------|-------------------------|
| 1.1.0.x          | Initial version.                                        | Yes                 | No                      |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.1.0.x 1.1.2.x  | Unknown                     |

## Installation and configuration

### Creation


#### SNMP main connection

This connector uses an snmp connection and requires the following input during element creation

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
- **Ignore** the **Timeout of a single command** and **Number of retries** settings (the latter should be *0*).
  (Note: it is possible to configure an element timeout in the **Advanced element settings**.)


### Configuration in case the matrix remains empty

In case the matrix remains empty after you have created the element, check if the IP address, bus address and port are correct. Also verify if the DataMiner software is version 8.0.5.4 or later.
If this is the case and all settings seem correct, check the element log file and verify if there is no firewall blocking traffic on port 52116.

## Usage

### Frame Controller Page
This page contains all the basic information about the frame, as well as some configuration/status subpages: Switchpoint, Power supply and Fan, SNMP, Network, and Clock
### Slot 1 PV 32x32 Page
This page contains the all input/output tables related to the slot 1: please note that these are not linked to the matrix: the matrix tables are the source/desetinations tables found under the routing sub pages.
### Slot 2 PV-CQ-16 Page
This page contains the various Slot 2 related parameters/tables. It also includes all video/audio advanced settings in separate subpages, as well as Audio TSG and Miscellaneous sections.
### Faults Page
Here you can view the Trap Outstanding Table, which is the current alarm listing across all 3 modules. For more detailed information about the faults, you can look at the sub pages, which include every possible frame fault and slot 2 fault (slot 1 faults to be added in the next version).
### Routing Page
Here you can view basic LRC parameters and the channels table. There is also pop up windows for Destinations and Sources pages which contain their respective tables.
### Destination Channels Page
This page contains the destination channels table.
### Matrix Page
This page contains the matrix.
### Locks Page
This page contains the  matrix locks table.
### Labels Page
This page contains the  matrix labels table.
### States Page
This page contains the matrix states table.


## Notes

- Once the element has been created, the connector shows the connected crosspoints on the configured level. You can change the connected input for an output by clicking the new input. The Platinum Router will then automatically disconnect the originally connected input in order to connect the new input. This means that the connector will not send a disconnect command. It is currently not possible to disconnect a connected input, so the connector will never send a disconnect command. All communication happens through the LRC (Logical Router Control) protocol, which also sends notifications when a change occurs, so that changes are updated in real time.
- All sets are (currently) done ONLY on the level that is being monitored.