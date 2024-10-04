---
uid: Connector_help_Evertz_7707LTA
---

# Evertz 7707LTA

The Evertz 7707LTA is a fiber optic transmitter that converts L-band RF signals into a fiber optic output signal at various wavelengths, including 1310nm, 1550nm, CWDM, and DWDM
This connector is used to monitor and configure 7707LTA cards using SNMP communication.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |Evertz 7707LTA Version 1.0.3         |

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
- **Device address**: The card slot
SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector uses SNMP to retrieve information from the card. It displays the information on the pages and allows you to perform changes on it.

### Trap Logging

In this page you can see all traps received in the **Traps** table.

You can also configure how many traps are stored in the table with the **Max Traps** parameter.
Additionally, you can clear the table completely using the **Clear Traps** button.
