---
uid: Connector_help_Evertz_7800R4x4-RFI
---

# Evertz 7800R4x4-RFI

This connector allows you to manage the Evertz 7800R4x4-RFI card. It communicates using SNMP.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware           |
|-----------|------------------------------|
| 1.0.0.x   | VLProProd_R4X4-RFI |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: The card slot.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

This connector uses SNMP to retrieve information from the card. It displays the information on the pages and allows you to perform changes to it.
It also contains a matrix, that shows routing between the input and the output. By clicking in the crosspoint, the user can enable/disable the correspondent crosspoint.

The Debugging page can be enabled to view all snmp tables that are being polled, by default it should be disabled.
