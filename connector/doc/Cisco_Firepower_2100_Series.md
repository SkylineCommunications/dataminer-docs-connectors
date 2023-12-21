---
uid: Connector_help_Cisco_Firepower_2100_Series
---

# CISCO Firepower 2100 Series

This connector uses SNMP communication in order to monitor a CISCO device from the Cisco Firepower 2100 Series.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes/No                  | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

This connector functions as a basic monitor tool. Only a limited number of setting can be set through this connector.

The bulk of the tables are polled every hour, but the General Information is polled every 30 seconds, and the Interface and Interface X table are polled every 10 seconds.

On the **Interface Detailed** page, you can find the interfaces. The standalone tables can be found via the **Raw Tables** button at the bottom of the page.
