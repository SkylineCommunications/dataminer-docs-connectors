---
uid: Connector_help_Hiltron_HCS4
---

# Hiltron HCS4

The Hiltron HCS4 is a unit controller that can manage different types of modules: DBT modules, power supply modules, etc.

The connector retrieves information about all the modules using the SNMP protocol.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 0.10                   |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | - | - Hiltron HCS4 - Double Bias Tee<br>- Hiltron HCS4 - PSA Power Supply<br>- Hiltron HCS4 - SWI Waveguide Switch<br>- Hiltron HCS4 - L-Band 2+1 Redundancy Switch<br>- Hiltron HCS4 - LNB |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default:*161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The list of modules managed by the connector can be found in the **Modules** table on the **General** page.

This connector will export different connectors and create DVEs based on the retrieved modules. You can find a list of the supported modules in the "System Info" section above.
