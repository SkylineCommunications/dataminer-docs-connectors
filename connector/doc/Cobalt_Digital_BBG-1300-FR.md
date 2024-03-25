---
uid: Connector_help_Cobalt_Digital_BBG-1300-FR
---

# Cobalt Digital BBG-1300-FR

The Cobalt Digital BBG-1300-FR is a 1RU enclosure frame capable of housing up to 2 cards as a basic standalone desktop unit, or up to 3 units racked together as a 1RU group for rack mounting. It has to be used with an odd slot rear I/O.  The BBG-1300-FR allows openGear cards to be supported.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.22-release-a516eb93         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |<ul><li><xref:Connector_help_Cobalt_Digital_BBG-1300-FR_-_9940-ACO></li></ul>   |

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

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Polling of the different parameters can be configured on the Polling Configuration page.

The export of connectors is made automatically when polling the Cobalt HPF Slot Table, visible on the Cards page.
