---
uid: Connector_help_Vertiv_EXL_S1
---

# Vertiv EXL S1

The Vertiv EXL S1 connector enables data integration and monitoring of Vertiv's high-efficiency uninterruptible power supply (UPS) system, the EXL S1 series. This connector retrieves operational and performance data via SNMP from the UPS, including parameters such as input/output voltage, battery status, bypass, alarms, and configuration. The source of the data is the UPS's SNMP interface, which must be correctly configured and reachable on the network.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version: <li>Reading SNMP data from the device</li>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-      |

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

This connector monitors the operational status of the Vertiv EXL S1 UPS system through SNMP polling. On the **General** page, you can find device and battery information. In the **Input**, **Output**, and **Bypass** pages,
you can find the same information you would find on the equivalent page on the Web Interface. The **Alarm** page has any active alarms on the device and the **Well Known Alarms** page has the status of specific alarms.
The **Configuration** page has information regarding the configuration of the UPS.


## Notes

The Vertiv EXL S1 requires the configuration of SNMP on the device allow the connector to poll data.
