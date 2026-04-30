---
uid: Connector_help_T-Vips_CP525_Technical
---

# T-Vips CP525

## About

This connector is used for the CP525 multiplexer model from T-Vips and allows SNMP monitoring and configuration of this device.

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

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector contains parameters for monitoring **alarms**, **input**, **outputs**, and **transport streams** on the corresponding (sub)pages.

On the **Configuration** page, configuration files can be both uploaded and downloaded.
