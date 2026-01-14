---
uid: Connector_help_RFS_MSV_Monitoring_System_Technical
---

# RFS MSV Monitoring System

## About

The RFS MSV Monitoring System connector enables data integration and monitoring of RFS Multi-Sector Vector (MSV) RF distribution systems. This connector retrieves operational and performance data from the MSV platform, including parameters such as forward and reflected power, VSWR/return loss, and device status combiners and RF paths. The connector uses SNMP to communicate with the device.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
