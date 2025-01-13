---
uid: Connector_help_GatesAir_MSCx_1P1_Main_Alt_Controller
---

# GatesAir MSCx 1P1 Main Alt Controller

The GatesAir MSCx 1P1 Main Alt Controller is designed for seamless broadcast transmission control, with redundancy to ensure uninterrupted operation.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                                        |
|-----------|-----------------------------------------------------------|
| 1.0.0.x   | -                                                         |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *161*

SNMP Settings:

- **Get community string**: *public*
- **Set community string**: *private*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The element created with this connector has the following data pages:

- **General**: Displays different types of parameters dealing with general information for the device, for example: **MIB revision**, **System Name**, **Switch and Remote State**.

- **Power Supply**: Contains parameters regarding the health and status of the power supply.

- **TX A**: Displays metrics for TX A, including **Frequency**, **Remote State**, **Out Forward Power**, and more.

- **TX B**: Displays metrics information for TX B similar to TX A.
