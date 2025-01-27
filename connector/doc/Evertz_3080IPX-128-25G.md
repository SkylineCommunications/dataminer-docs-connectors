---
uid: Connector_help_Evertz_3080IPX-128-25G
---

# Evertz 3080IPX-128-25G

The 3080IPX is an integrated multicast label switching fabric that allows 10GE and 1GE signaling and can be used for video LAN/WAN transport applications.

## About

### Version Info

| Range              | Key Features           | Based on | System Impact |
|--------------------|------------------------|----------|---------------|
| 1.0.0.x            | Initial version.       | -        | -             |
| 1.0.1.x            |                        | 1.0.0.2  | -             |
| 1.0.2.x [SLC Main] | HTTP connection added. | 1.0.1.1  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.3                    |
| 1.0.1.x   | 2.3                    |
| 1.0.2.x   | 2.3                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |

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

#### SNMP Secondary Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### HTTP Connection

This connection is used to poll the Evertz REST API.

### Initialization

For the HTTP connection, the **API Key** parameter on the **General** page needs to be set for the outgoing requests to work.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The **General** page of this connector shows the version running on the device. You can also see and configure the alias name and the API key there.

The **Ports** page contains information about the ports, such as the Maximum Ports, the Port Config Table, and the Port Status Table. This page also contains a Port Measurement subpage, where you can enable or disable the measurement of each port. If the measurement of the port is disabled, it will not be displayed in the Port Config, Port Status, and IGMP Ports tables.

The **Multicast Sources** page contains information such as Multicast Count, Maximum, and Egress Count. It also displays the Multicast Table.

The **IGMP Ports** page contains a table with basic information about the IGMP Ports, including IGMP Routing, Fast Leave, Sources with VLAN, etc.
