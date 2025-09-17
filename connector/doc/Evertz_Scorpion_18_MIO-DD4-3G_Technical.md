---
uid: Connector_help_Evertz_Scorpion_18_MIO-DD4-3G_Technical
---

# Evertz Scorpion 18 MIO-DD4-3G

This connector uses SNMP to communicate with the Evertz SCORPION 18 MIO-DD4-3G module, allowing DataMiner to monitor and control various parameters exposed by the device, such as performance metrics, alarms, and configuration settings. By leveraging SNMP, the connector enables real-time data collection, alarm detection, and remote management.

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

The data is organized into tables and standalone parameters spread across multiple pages. The layout of the connector's data pages and corresponding data have been designed to closely represent the device's GUI.

You can configure up to 8 GPOs, by defining the GPO source, polarity, delay, and hold duration. For each GPO, the connector provides a status indicator specifying whether or not the GPO is activated or not.

Various device settings can be configured such as general purpose outputs and SCTE104 controls.
