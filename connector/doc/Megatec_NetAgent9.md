---
uid: Connector_help_Megatec_NetAgent9
---

# MegaTec NetAgent9

This connector is used to monitor the NetAgent9 UPS management device, which allows configuration via web browser, NMS, Telnet, or SNMP. The NetAgent9 supports the MegaTec single- and three-phase UPS protocols.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 3.8.CY504          |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMPv2) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element mainly displays SNMP parameters as defined in the device MIB.

The *Alarms* page contains an Alarms table that displays SNMP traps forwarded by the connected device. You can delete alarms via the right-click menu of the table. On the *Alarm Settings* page, you can also configure a fixed lifetime for the alarms, after which they are automatically cleared by the connector.
