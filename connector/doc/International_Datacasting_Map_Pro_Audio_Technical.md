---
uid: Connector_help_Evertz_MUXIP-10GE-v52-2RU
---

# Evertz MUXIP-10GE-v52-2RU

The **Evertz MUXIP-10GE-v52-2RU** is a versatile IP re/de-multiplexer designed for video delivery. It supports up to 128 IP inputs and outputs, handles both SPTS and MPTS, and offers advanced stream processing features like program and PID remapping. With robust redundancy options and flexible configuration, it's ideal for broadcasters and service providers managing high-quality video content across networks.

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

### Examples

For general device information, data can be found in the *General*, *Status*, *System Configuration*, and *Ethernet Ports Control/Monitor* Pages.

The device can forward any faults via SNMP traps. To do so, enable the *Send Trap* option for any modules on the *Fault* page then configure where to send the traps in the *SNMP Configuration* page
 
To configure the Input and Output channels, all that information can be found on the *Input Configuration* and *Output Configuration* pages respectively. You can also configure route rules on the *Routes* page.