---
uid: Connector_help_Apantac_Tahoma_T-Sharp
---

# Apantac Tahoma T-Sharp

The **Apantac Tahoma T-Sharp** is a Multi-format Modular Multi-viewer.

This connector uses SNMP to poll data from the **Apantac Tahoma T-Sharp** device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version | \-           | \-                |

### Product Info

| Range | Supported Firmware                                                         |
|-----------|--------------------------------------------------------------------------------|
| 1.0.0.x   | K(20190808) |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.


SNMP Settings:

- **Get community string**: The community string used when reading values from the device. (default: *public*)
- **Set community string**: The community string used when setting values on the device. (default: *private*)


### Initialization

No further configuration is required.

### Redundancy

There is no redundancy defined.

## How to use

You can find all the information you need to monitor the **Apantac Tahoma T-Sharp** device on the **General** data page.

## Notes

This connector is similar to the [Apantac LE-20HD](xref:Connector_help_Apantac_LE-20HD) connector: the displayed parameters are identical.

The difference between the two connectors lies in the SNMP communication:

- The **Apantac LE-20HD** uses *multipleGet* requests to poll the tables. This results in better performance but some **Apantac** devices do not support the *multipleGet* requests.
- The **Apantac Tahoma T-Sharp** uses *getNext* requests to poll the tables. This results in lower performance time but most **Apantac** devices support this retrieval method.
