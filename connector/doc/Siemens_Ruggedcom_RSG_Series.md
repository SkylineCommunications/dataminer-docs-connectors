---
uid: Connector_help_Siemens_RUGGEDCOM_RSG_Series
---

# Siemens RUGGEDCOM RSG Series

The Siemens Ruggedcom RSG Series is a series of SNMP-based network switches.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | Initial version. | - | - |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page contains basic information about the device such as the **System Name**, **System Description**, and **Serial Number**.

### Interfaces

This page and its subpages contain information related to the device interfaces.
- Interface Rates: Current rates of the interfaces based on the reported counters.
- Interface Counters: Raw counters reported by the device.
- Interface Config: Configure the Interface Table with additional information.
  - `Blank Interfaces` accepts a semicolon-separated list of interface indices for which to create blank rows on the Interface Table if they do not exist. This allows better visualization of the Interface Table on the Visio because the interfaces are modular and could be blanked out (and thus not show up on the table).
  - `Ethernet Types` accepts a JSON dictionary mapping interface indices to their Ethernet Port types `{ "Undefined", "10BASE-T", "100BASE-TX", "100BASE-FX", "1000BASE-T", "1000BASE-TX", "1000BASE-FX" }`, e.g. `{ "2": "10BASE-T", "3": "100BASE-TX" }`. These are used to augment the SNMP data as it does not report the Ethernet Port type.
- IP Config: Configure **Management IP Address**, **Default IP Gateway**, **Default Management IP Address** etc.

 ### RS-232

 This page only appears if any of the ports on the Interface Table are of type RS-232. It displays the **Serial Ports**, **Modbus Servers**, **Raw Sockets**, and **Premptive Raw Sockets**. Whether each of the latter three tables is polled can be controlled in the **RS-232 Settings** subpage.

 The **RS-232 Settings** subpage also allows specified ports to be reset, or for their stats to be cleared. After resetting or clearing, the tables will be re-polled for data.

 ### STP

 This page and its subpages allow monitoring and configuration of the **Spanning Tree Protocol**.

 ### Dot1q

 This page and its subpages allow monitoring and configuration of VLAN-related data.

 ### Device Errors & Events

 These pages show the device errors and events. When SNMP traps are received, if they do not correspond to any known alarm, they will be forwarded to the Device Events table. On the Device Events page, the number of rows to keep can be configured. For performance reasons, the rows are not always cleared immediately when the maximum number of rows is reached. For instance, if the number of rows to keep is configured to be 1000, the table will accept another 200 rows before the table is culled to 1000 entries again.
