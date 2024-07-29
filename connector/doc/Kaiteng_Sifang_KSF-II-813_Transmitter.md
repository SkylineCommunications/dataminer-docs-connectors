---
uid: Connector_help_Kaiteng_Sifang_KSF-II-813_Transmitter
---

# Kaiteng Sifang KSF-II-813 Transmitter

This driver monitors the parameters of devices connected to the Kaiteng Sifang KSF-II-813 Transmitter.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |GB/T 37345-2019       |

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

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector contains the following pages:
- **General**: Displays the general system information of the device, as well as the number of Power Amplifiers, DC Supplies and Exciters currently connected to this driver.
- **Time Table**: Displays the Scheduled Working and Standby time of the device. *Select from Time Table Entries 1-35 to be displayed*.
- **Power Amplifier**: Expand to view displayed parameters of power amplifiers 1-8.
- **DC Power Supply**: Display parameters of DC power supplies 1-4.
- **Exciter**: Displays parameters for Exciters 1 and 2.

## Note
Each amplifier, power supply and exciter has the option to be polled by the driver. This option is disabled for all components by default.