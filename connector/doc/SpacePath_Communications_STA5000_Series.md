---
uid: Connector_help_SpacePath_Communications_STA5000_Series
---

# SpacePath Communications STA5000 Series

The SpacePath Communications STA5000 Series is a high-power satellite amplifier system designed for ground station applications, providing reliable and efficient signal amplification for satellite communication links. 

It features advanced thermal management, high linearity, and robust construction, ensuring optimal performance and longevity in demanding environments.

## About

SpacePath Communications STA5000 Series connector uses SNMPv2 to monitor and configure SpacePath Communications STA5000 Series equipment.


### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version       |-         |-         |

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

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

The connector does not require credentials, so setting it up is rather straightforward. 

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays generic system information of the device. 

The **Status** page contains several parameters that monitor the device state, such as Forward and Reflected Power, internal Voltage values, and temperatures.

On the **Control** page, control options are provided for several parameters for the device power amplification (for example, Attenuation, State, Control Mode).

The **RF Setup** page provides alarm and fault threshold parameters for Minimum and Maximum Forward Power and Forward Power Offset parameter. The setting of thresholds on these parameters is enabled.

The **Redundancy** shows which Block Upconverter Unit is in online or in standby mode.

On the **Beacon Rx** parameters related to the Beacon Rx component are displayed and configured.

The **Fault** page contains the fault detection configuration, along with flag parameters.

The **Web Interface**  page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
