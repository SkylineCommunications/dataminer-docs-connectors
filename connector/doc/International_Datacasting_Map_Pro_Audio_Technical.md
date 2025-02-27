---
uid: Connector_help_International_Datacasting_Map_Pro_Audio
---

# International Datacasting Map Pro Audio

The **International Datacasting Map Pro Audio** device is a professional audio distribution and monitoring solution designed for broadcasters and content providers. It allows for high-quality audio delivery via satellite, Internet, or IP-based systems. The device is typically used in environments that require reliable, high-performance audio transport for both live and pre-recorded content. It provides functionalities such as real-time monitoring, signal analysis, and seamless integration with existing broadcast infrastructures. It is known for its stability and efficiency in managing large-scale audio transmissions across multiple platforms.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

**This subsection can only be omitted for a virtual connector**

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

Indicate if additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is not currently integrated.

## How to use

Once the element is created, all information will be polled and displayed. Navigating to the appropriate pages will show the desired information, no other configuration is required.