---
uid: Connector_help_Robustel_R2011
---

# Robustel R2011

The Robustel R2011 Industrial Cellular Router is a rugged, versatile 4G router with 5 Ethernet ports, dual SIM single standby capability and a range of advanced functions for mission critical IoT or M2M applications.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |5.2.1 or higher        |

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
- **IP port**: [The IP port of the destination.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page contains an overview of system information, internet, mode anf Wi-Fi station statuses.

The **Polling Configuration** page contains parameters to enable or disable polling of specific groups of parameters, allowing users to focus only on the relevant information.

The **Interface** page eatures several management options.

**Link Manager Settings** allow for the management of network link connecitons to optimize performance.

**Lan Port Settings** enable configuration of the LAN port, including IP address assignments and network masks.

**Ethernet Settings** provide adjustments for Ethernet connections.

**Cellular Settings** manage configurations for mobile data connectivity.

**Wi-Fi Settings** contain Wi-Fi options, including SSID, security settings, and channel selection for optimal wireless performance.

The **Network** Page includes information and settings related to network management. It covers **Firewall Filtering**, which provides options for managing network traffic and security. 

The **Network Status** section displays the current state of the network. 

**Firewall Custom Rules** allow users to define specific rules for network traffic.

The **OpenVPN Page** includes settings related to VPN management. Tunnel settings allow for configuration of the VPN tunnel parameters. Password settings enable the management of authentication credentials.

## Notes

It takes anywhere from 10 to 30 seconds to perform set actions due to device processing time. Each set command is followed by a save command to ensure that the changes are applied to the device.
