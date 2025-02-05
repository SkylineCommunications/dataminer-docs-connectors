---
uid: Connector_help_Newtec_USS0202
---

# Newtec USS0202

## About

### Version Info

| Range              | Key Features                                               | Based on | System Impact |
|--------------------|------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Initial version<br>- SNMP parameters and trap processing | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.9.2.r1.588           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How To Use

The connector uses a retry mechanism to update its tables after changing a cell value.

The parameters that are located on the pages USS Control and USS Operation Config are only relevant for devices with a single protection group. This means that these pages are not useful when multiple protection groups are available.

The Group Name column of several tables can show wrong names. If it seems that the names are shifted, please change the Control Group Index parameter located on the USS Setup page. The default value (Check First ID) will instruct the connector to decide how to poll the groups, based on the ID of the first group. The One Based option will poll the groups without incrementing the ID. Example: group with ID 0 will be polled at //cgi-bin/pegui-cgi/uss0, group with ID 1 will be //cgi-bin/pegui-cgi/uss1, etc.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
