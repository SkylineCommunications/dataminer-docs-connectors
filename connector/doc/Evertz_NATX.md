---
uid: Connector_help_Evertz_NATX
---

# Evertz NATX

The Evertz NATX switch is a network-based broadcast distribution system that is used for routing video and audio.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware             |
|---------|--------------------------------|
| 1.0.0.x | exe-guest-v1.4-natx-pln-r32789 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

This connector uses two Simple Network Management Protocol (SNMP) connections. To facilitate network redundancy, the device's two IP interfaces should be filled in during element creation.

#### SNMP Connection - Main

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### SNMP Connection - Backup

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector displays only read-only information. The following data pages are available:

- **General**: Displays general information of the connector and its status.
- **Faults**: Displays alarm status parameters raised on a device level.
- **Ports**: Displays the port status as well as various alarm statuses associated with the ports of the device.
- **PTP**: Displays the status of the PTP, ports, and its masters.
- **Web interface**: Web GUI of the Evertz NATX device.
