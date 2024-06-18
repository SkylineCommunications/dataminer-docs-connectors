---
uid: Evertz_HDSD9545DLY-PRO
---

# Evertz HDSD9545DLY-PRO

The Evertz HDSD9545DLY-PRO is a time-shifting delay processor with two program paths, which are HD- and SD-compatible.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | Yes             | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Port number**: The port of the connected device (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

The element created with this connector will have 5 data pages.

- The **General** page includes the card type, *HDSD9545DLY-PRO* or *HDSD9545DLY-PRO-HD40*.

- On the **Control Parameters** page, you can configure general video/audio parameters, such as Video Standard, Delays, GPI, etc.

- The **Transition Control** and **Output Control** pages contain info and configurable data for sources or outputs.

- The **Fault Management** page lists the fault statuses indexed by fault name and by input index. Here you can configure whether traps are sent in certain situations.
