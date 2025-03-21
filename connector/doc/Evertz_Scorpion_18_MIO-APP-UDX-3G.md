---
uid: Connector_help_Evertz_Scorpion_18_MIO-APP-UDX-3G
---

# Evertz Scorpion 18 MIO-APP-UDX-3G

This connector is used to monitor the Evertz Scorpion 18 MIO-APP-UDX-3G module.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

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
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Once the element has been set up, no further configuration is needed.

This connector is mainly used to monitor the device and adjust some important settings of the device.

The layout of the connector is very similar to that of the web UI, with the following sections:

- **System**: Contains the same parameters as the **System section of the web UI**. The parameters are **read-only**.
- **Video**: Contains the same parameters as the **Video section of the web UI**. Some parameters allow you to adjust settings on the device.
- **Audio**: Contains the same parameters as the **Audio section of the web UI**. Some parameters allow you to adjust settings on the device.
- **ANC**: Contains the same parameters as the **ANC section of the web UI**. Some parameters allow you to adjust settings on the device.
