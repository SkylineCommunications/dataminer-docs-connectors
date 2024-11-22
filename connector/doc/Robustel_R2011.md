---
uid: Connector_help_Robustel_R2011
---

# Robustel R2011

The Robustel R2011 industrial cellular router is a versatile 4G router with 5 Ethernet ports, dual SIM single standby capability, and a range of advanced functions for IoT or M2M applications.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 5.2.1 or higher    |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page contains an overview of system information and internet, mode, and Wi-Fi station status information.

On the **Polling Configuration** subpage, you can enable or disable the polling of specific groups of parameters, so that only the relevant information is shown.

## Notes

Because of the processing time of the device, performing set actions can take between 10 to 30 seconds. Each set command is followed by a save command to ensure that the changes are applied to the device.
Due to the device's limitations in processing speed, the timeout for each individual command is set to 30 seconds by default to accommodate the necessary data retrieval time.

