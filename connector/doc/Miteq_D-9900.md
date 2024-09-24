---
uid: Connector_help_Miteq_D-9900
---

# Miteq D-9900

This connector allows monitoring and control of the downconverter

## About

### Version Info

| Range              | Key Features                                                                 | Based on | System Impact |
|--------------------|------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Monitoring and control.<br>- Same UX as Miteq U-9900 (upconverter) 1.0.0.x | -        | -             |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | D172138V1.191 D179861V1.001 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector will allow monitoring and control of the converter. No special actions are required.
