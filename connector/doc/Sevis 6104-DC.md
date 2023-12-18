---
uid: Connector_help_Sevis_6104-DC
---

# Sevis 6104-DC

The Sevis 6104-DC is a backhaul optimization solution that employs GSM A-bis, 3G, and CDMA optimization algorithms to reduce backhaul bandwidth.

This connector retrieves information from the device via SNMP. It displays basic information about the device, as well as the alarm status.

## About

### Version Info

| Range              | Key Features     | Based on    | System Impact    |
|--------------------|------------------|-------------|------------------|
| 1.0.0.x [SLC Main] | Initial version  | -           | -                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.6.2-S08              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Displays general parameters such as IP address, system up time, software, and hardware version.
- **Alarms**: Displays the alarm status, the power supply status, and the fan and temperature status of the device.
