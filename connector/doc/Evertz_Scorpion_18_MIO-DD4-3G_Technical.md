---
uid: Connector_help_Evertz_Scorpion_18_MIO-DD4-3G_Technical
---

# Evertz Scorpion 18 MIO-DD4-3G

This connector in DataMiner implements the SNMP interface to enable communication with the Evertz SCORPION 18 MIO-DD4-3G module by sending SNMP requests and processing the responses. It allows DataMiner to monitor and control various parameters exposed by the device, such as performance metrics, alarms, and configuration settings. By leveraging SNMP, the connector enables real-time data collection, alarm detection, and remote management, making it easier for operators to integrate and manage network or broadcast equipment within the DataMiner platform.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

## How to use

The data is organized into tables and stand-alone parameters spread across multiple pages. The layout of the conector's data pages and corresponding data have been designed to closely represent the device's GUI. The various device settings can be configured such as general purpose outputs, and SCTE104 controls. 