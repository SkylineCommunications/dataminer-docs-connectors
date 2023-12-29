---
uid: Connector_help_Specialty_Microwave_Corp_13361-501
---

# Specialty Microwave Corp 13361-501

This is a DataMiner connector for the ADSS Uplink Switching Control Panel. The equipment consist of a logic panel used in satellite communications earth stations. 

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version.         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |13361-501        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |No         |-         |   |

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:


- Direct connection:

  - **Baudrate**: [Baudrate specified in the manual of the device, e.g. *9600*(default:9600).]
  - **Databits**: [Databits specified in the manual of the device, e.g. *7*(default:8).]
  - **Stopbits**: [Stopbits specified in the manual of the device, e.g. *1*(default:1).]
  - **Parity**: [Parity specified in the manual of the device, e.g. *No*(default:No).]
  - **FlowControl**: [FlowControl specified in the manual of the device, e.g. *No*(default:No).]


- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]

## How to use

On the **General** page of this connector, you can configure the position of a switch by selecting the position in the drop down menu of the switch parameter.*
