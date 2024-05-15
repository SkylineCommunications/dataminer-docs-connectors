---
uid: Connector_help_Cisco_IMC
---

# CISCO IMC

The Cisco Integrated Management Controller (IMC) is a baseboard management controller that provides embedded server management for Cisco UCS C-series rack servers and Cisco UCS S-series storage servers. The Cisco IMC enables system management in the data center and across distributed branch office locations.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware     |
|---------|------------------------|
| 1.0.0.x | CISCO UCSC Rack Server |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

This connector needs a valid session ID to be able to communicate with the device API.

When you have created an element, fill in the credentials on the **General** page to generate this session ID.

## How to use

On the **General** page of this connector, you can configure the username and password to access the device, as mentioned above.

The **Chassis** page provides an overview of all chassis-related parameters.

The **Networks** page provides an overview of the configured network and DHCP settings.

The **System** page provides an overview of the system status and processor information.

The **Thermal** page provides an overview of physical device temperatures and fan status information.

The **Power** page provides an overview of status and other information for the power supplies.

The **Log Services** page contains a collection of SEL, CIMC, and fault logs.
