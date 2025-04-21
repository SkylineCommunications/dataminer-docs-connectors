---
uid: Connector_help_Work_Microwave_AX60_Series_Modulator_Technical
---

# Work Microwave AX60 Series Modulator

The AX60 Series Modulator is designed to support high-speed IP connectivity and advanced modulation schemes up to 256APSK. It provides robust and flexible data transmission capabilities, making it suitable for a wide range of applications, including governmental, IP networking, and space communications. The modulator supports both native network operation and data streaming over IP, ensuring seamless integration into modern communication systems.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version        |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

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


### Initialization

All that is needed to initialize an element is the IP and get/set SNMP community string.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
