---
uid: Connector_help_Evertz_NATX
---

# Evertz NATX

The Evertz NATX Switch is a network-based broadcast distribution system that is used for routing video and audio.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |exe-guest-v1.4-natx-pln-r32789         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection.
To facilitate network redundancy, the device's two IP interfaces should be filled in the following inputs during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

#### SNMP Connection - Backup

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.


### Examples

The driver contains read-only information that is sectioned into the following pages:

- **General**: Displays General Information of the driver and its status.
- **Faults**: Displays alarm status parameters raised on a device level.
- **Ports**: Displays port status as well as various alarm status associated with the ports of the device.
- **PTP**: Displays the status of the PTP, ports and its masters.
- **Web interface**: Web GUI of the Evertz NATX device.
