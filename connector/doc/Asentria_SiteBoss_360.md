---
uid: Connector_help_Asentria_SiteBoss_360
---

# Asentria SiteBoss 360

This connector allows you to monitor general parameters (e.g. system uptime, location, tech support details, etc.) as well as input and output interfaces such as contacts, relays, sensors, and analog inputs.

## About

### Version Info

**This subsection can only be omitted for an exported connector**

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>SNMP Monitoring</li><li>SNMP Traps</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     | -        |

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
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

## How to use

The connector is divided in three main parts
- A single General page with standard device information
- A few pages containing information regarding data traffic (Interface, Ports, Ethernet)
- The specific device functions, such as the power, battery en event sensor information

All tables are polled over SNMP
For event sensor information, trap support is added to updated information when a trap comes in to provide accurate alarming.
