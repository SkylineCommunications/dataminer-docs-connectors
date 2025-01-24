---
uid: Connector_help_Evertz_Scorpion_18_MIO-APP-UDX-3G
---

# Evertz Scorpion 18 MIO-APP-UDX-3G

This connector is used to monitor the Evertz Scorpion 18 MIO-APP-UDX-3G module.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-       |

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
- **IP port**: [The IP port of the destination.]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector is self reliant after the element is set up. This connector is mainly used to monitor the device and perform some configuration to important section of device. The connector models the Web UI closely and have the following sections:

**System** - Has all the parameters that are shown in the **Web UI under the System section**, The parameters are **read-only**.

**Video** - Has all the parameters that are shown in the **Web UI under the Video section**, Some parameters have both **read and write ablities**.
