---
uid: Connector_help_Peak_Communications_TLTH
---

# Peak Communications TLTH

The TLTH(B) series test loop translators are designed to take a sample of a transmit signal and convert it to a frequency at which it can be monitored or analyzed. Often monitoring of the transmit signal is required in the L-Band, or it requires a translation of the transmit signal to the receive band, which is then applied to the receive equipment in a test mode.

## About

### Version Info

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 0005.03                |

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

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays general parameters for the unit and allows you to reboot the unit.

The element also displays the **Alarms**, **Test Loop Translator**, **Redundancy**, and **Ethernet** information for the unit.
