---
uid: Connector_help_Evertz_7801FC
---

# Evertz 7801FC

## About

The 7801FC VistaLINK Frame Controller handles all SNMP communication between the frame (7801FR) and the network manager (NMS), and serves as a gateway to individual cards in the frame.

This connector can be used to monitor and configure the Evertz 7801FC VistaLINK Frame Controller card.

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

This connector displays product location information in a table on the **General** page. On the **Status** page, you can find status parameters, while on the **Configuration** page, you can configure the device.
