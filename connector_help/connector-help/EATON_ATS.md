---
uid: Connector_help_EATON_ATS
---

# EATON ATS

The EATON ATS is a device that can automatically switch between two power sources to provide uninterrupted power to connected equipment. 
It is designed for customers who want to add power redundancy to their networking equipment, such as switches and routers. .

## About

### Version Info

| **Range**            | **Key Features** | **Based on** | **System Impact** |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version. | \-           | \-                |

### Product Info

| **Range** | **Supported Firmware** |
|-----------|------------------------|
| 1.0.0.x   | 00.00.0012      |

### System Info

| **Range** | **DCF Integration** | **Cassandra Compliant** | **Linked Components** | **Exported Components** |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

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

The connector also uses traps to receive alarm status updates.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element displays the available information of the device on the following pages: **General**, **Input**, **Output**, **Bypass**, **Alarms** and **Sensors**.

On the **Polling page**, you can configure the polling of the parameters.
