---
uid: Connector_help_Alea_MCxPTT
---

# Alea MCxPTT

Alea MCxPTT is a system that guarantees immediate communication services and makes it possible to decide, disclose information, and effectively carry out mission-critical tasks.

This connector can be used to consult the service alarms of this system.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays the system information.

The **Alarms** page displays the list of services available in the MCxPTT system and their alarm status.

On the **Polling** page, you can define the frequency of the polling groups.
