---
uid: Connector_help_GatesAir_MCSx_1P1_Main_Alt_Controller
---

# GatesAir MCSx 1P1 Main Alt Controller

The GatesAir MCSx 1P1 Main Alt Controller is a sophisticated system designed for seamless broadcast transmission control, offering robust redundancy to ensure uninterrupted operation. It features intuitive user interfaces and advanced monitoring capabilities, making it an essential tool for maintaining high reliability in broadcast environments.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                                        |
|-----------|-----------------------------------------------------------|
| 1.0.0.x   |                                                           |

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

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector provides the following pages:

- **General:** Displays different types of parameters dealing with general information for the device for example **MIB revision**, **System Name**, **Switch and Remote State**.

- **Power Supply:** Has parameters regarding the health and status for the power supply..

- **TX A** Metrics for TX A are found here including, **Frequency**, **Remote State**, **Out Forward Power** and more.

- **TX B** Displays metrics information for TX B similiar to TX A.