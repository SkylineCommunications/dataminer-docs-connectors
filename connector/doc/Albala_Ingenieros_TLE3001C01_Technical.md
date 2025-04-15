---
uid: Connector_help_Albala_Ingenieros_TLE3001C01_Technical
---

# Albala Ingenieros TLE3001C01

The Albala Ingenieros frame is designed to house and power various modules from the TL3000 family. It provides a robust and flexible infrastructure for mounting and connecting multiple modules, ensuring efficient operation and communication within the system. The frame supports both serial and Ethernet communication, allowing for remote control and supervision of the installed modules.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [Obsolete]     |<ul><li>Initial Version</li></ul>         |-         |-         |
|1.0.1.x [SLC Main]     |<ul><li>Added TLE3001C03V1 and ISW3000C01V2 modules</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.1.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.1.x    |No       |Yes         |-         |<ul><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_PDC3002C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HFS3000C01V2></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HVD3001C04V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_DVM3001C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_TLE3001C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HAD3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HAE3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HVD3001C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HVD3001C02V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HSW3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HDE3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HSW3000C01V2></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HDC3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HLI3000C01V2></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_AVD3001C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_AVD3001C02V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HOP3147C02V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_HXC3000C01V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_TLE3001C03V1></li><li><xref:Connector_help_Albala_Ingenieros_TLE3001C01_-_ISW3000C01V2></li></ul>   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default:*161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

No additional configuration is required after element creation.

### Redundancy

There is no redundancy defined.



## How to use

This frame facilitates the housing and powering of TL3000 modules, ensuring efficient operation and communication within the system. SNMP calls are used to retrieve device information, and SNMP traps can be received if enabled on the device. No data traffic will be seen in the Stream Viewer.

Note:

As a parent connector, it exports various connectors based on retrieved data. A list can be found under 'Exported Components'.
