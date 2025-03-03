---
uid: Connector_help_Mitec_ALGA
---

# Mitec ALGA

This connector is used to monitor and configure a Mitec ALGA device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

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

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*
- **Get community string**: The community string used when reading values from the device. By default *public*.
- **Set community string**: The community string used when setting values on the device. By default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

These are the main data pages of the connector:

- The **General** page provides general information about the device.
- On the **Control** page, you can adjust the Mute and Gain settings for BUCs.
- Information about HPA Units is available on the **Status** page.
- Alarm logs are available on the **Alarm Log** page.

**NOTE**
Read and write parameters for the KPIs on the **Control** page are handled separately. To ensure accuracy, the read parameter is updated immediately after setting, and a retry mechanism is implemented.