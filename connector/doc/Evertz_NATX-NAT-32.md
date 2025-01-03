---
uid: Connector_help_Evertz_NATX-NAT-32
---

# Evertz NATX-NAT-32

This connector communicates with the layer of the NATX to get information about the LAN to WAN, WAN to LAN cores and flows.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                            |
|-----------|-----------------------------------------------|
| 1.0.0.x   | N/A                                           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The data in this connector is divided into two main sections: **LAN to WAN** and **WAN to LAN**.

In the **Core Configuration Page LAN to WAN or WAN to LAN** there is a table displaying the number of supported cores and their status. Depending on the core's status, the flow information is polled.

-The connector only polls information for cores that are enabled and displays flow information exclusively for those that are enabled as well. This applies to both the **Input Flow Configuration** and the **Input Flow Translation Configuration**.

In the **General** page you can find system parameters such as the name, description and sytem up time.