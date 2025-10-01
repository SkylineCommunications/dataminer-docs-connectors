---
uid: Connector_help_Evertz_7707LTA
---

# Evertz 7707LTA

The Evertz 7707LTA is a fiber-optic transmitter that converts L-band RF signals into fiber-optic output signals at various wavelengths, including 1310 nm, 1550 nm, CWDM, and DWDM

This connector is used to monitor and configure 7707LTA cards using SNMP communication.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware           |
|---------|------------------------------|
| 1.0.0.x | Evertz 7707LTA Version 1.0.3 |

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
- **Device address**: The card slot.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector uses SNMP to retrieve information from the card. It displays the information on the pages and allows you to perform changes on it.

### Trap Logging

This page lists all the received traps in the **Traps** table.

With the **Max Traps** parameter, you can limit how many traps can be stored in the table.

With the **Clear Traps** button, you can clear the table completely.
