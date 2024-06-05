---
uid: Connector_help_AdvancedDigital_ADV-6410
---

# AdvancedDigital ADV-6410

This connector monitors the activity of the AdvanceDigital ADV-6410 device.

AdvanceDigital ADV-6410 is an integrated receiver/decoder (IRD). It provides operators with ideal solution for multi receiving, descrambling, remultiplexing, and decoding operations.

## About

### Version Info

| Range   | Key Features                                       | Based on | System Impact |
|---------|----------------------------------------------------|----------|---------------|
| 1.0.0.x | Initial version                                    | -        | -             |
| 1.1.0.x | New SNMP tables and layout because of new firmware | -        | -             |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 34PA2046                    |
| 1.1.0.x          | 34PA600A                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: public).
- **Set community string**: The community string used when setting values on the device (default: private).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

The General page has some system parameters and device parameters like **SNMP** and **MIB** version, **Inputs** and **Outputs** .

On the **Configuration** subpage, you can configure the **BISS** and the **Traps**.

The **Trap Events** subpage displays the latest device events.

### Tuner

On this page, you can check the status and the configuration of the tuner.

### Decoder (Not Available in 1.1.0.x)

On this page, you can check the status and the configuration of the decoder.
