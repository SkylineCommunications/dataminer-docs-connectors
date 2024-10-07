---
uid: Connector_help_Lancier_Monitoring_PSC
---

# Lancier Monitoring PSC

The **Lancier Monitoring PSC** is a modernized, fully automatic compressed air system designed for the compression and drying of clean air, primarily for injection into cables and hollow conductors. This system ensures the efficient delivery of dry, compressed air by incorporating advanced control mechanisms and safety features.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V1.19                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## How to use

Lancier Monitoring PSC is a plug-and-play type of connector.

### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### General Page

The **General** page displays information about the system, configuration, compressor, and tank.

### Time Settings

On the **Time Settings** page, you can configure the date and time settings of the device.

### Operating Hours

On the **Operating Hours** page, you can configure the operating hours of the device.