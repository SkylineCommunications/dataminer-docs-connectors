---
uid: Connector_help_Miteq_DNB1-XTR
---

# Miteq DNB1-XTR

This connector allows monitoring and control of the downconverter. The connector is compatible with the Miteq DNB1 and DNB2 models.

## About

### Version Info

| Range              | Key Features                          | Based on | System Impact |
|--------------------|---------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | This range uses SNMP communication.   | -        | -             |
| 1.0.1.x            | This range uses serial communication. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | D163995V2.121.25       |
| 1.0.1.x   | D163995V2.121.25       |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection — Main — 1.0.0.x only

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### Serial Connection — Main — 1.0.1.x only

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device. Range: *64 - 95* (ASCII character "@" to "_").

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

No special actions are required to use this connector.
