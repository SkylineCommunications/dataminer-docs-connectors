---
uid: Connector_help_Kaiteng_Sifang_KSF-II-813_Transmitter
---

# Kaiteng Sifang KSF-II-813 Transmitter

This connector monitors the parameters of devices connected to the Kaiteng Sifang KSF-II-813 Transmitter.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | GB/T 37345-2019    |

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
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays the general system information of the device, as well as the number of power amplifiers, DC supplies, and exciters currently connected to the element.
- **Time Table**: Displays the scheduled working time and standby time of the device. In a dropdown box, you can select which time table entry should be displayed (from 1 to 35).
- **Power Amplifier**: Contains page buttons to information about power amplifiers 1 to 8.
- **DC Power Supply**: Display parameters of DC power supplies 1 to 4.
- **Exciter**: Displays parameters for exciters 1 and 2.

## Note

Polling for each amplifier, power supply, and exciter can be enabled or disabled. By default, polling is disabled for all components.
