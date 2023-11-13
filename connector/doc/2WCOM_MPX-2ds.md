---
uid: Connector_help_2WCOM_MPX-2ds
---

# 2WCOM MPX-2ds

The MPX-2ds is a 2-channel decoder designed for MPX distribution via satellite or IP.  
The 2WCOM MPX-2ds connector's main purpose is to monitor these 2 channels of the decoder.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |TBD         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
