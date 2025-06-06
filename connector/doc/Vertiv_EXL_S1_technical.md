---
uid: Connector_help_Vertiv_EXL_S1_Technical
---

# Vertiv EXL S1

## About

The Vertiv EXL S1 connector enables data integration and monitoring of Vertiv's high-efficiency uninterruptible power supply (UPS) system, the EXL S1 series. This connector retrieves operational and performance data via SNMP from the UPS, including parameters such as input/output voltage, battery status, bypass, alarms, and configuration. The source of the data is the UPS's SNMP interface, which must be correctly configured and reachable on the network.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **Device address**: [Indicate if required or not. If it is, specify default value and range.]

SNMP Settings:

- **Port number**: [The port of the connected device, by default 161.]
- **Get community string**: [The community string used when reading values from the device (default: *public*).]
- **Set community string**: [The community string used when setting values on the device (default: *private*).]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.


## How to Use

### General Page

On the general page, system information and battery information are available. These include the Firmware version, device name, battery status, battery charge, and more.

### Inputs, Outputs, and Bypass

The Inputs, Outputs, and Bypass pages have any information regarding their respective title, allowing the monitoring of voltages, currents, power and frequencies of the device.

### Alarms Page

Any alarms thrown up by the UPS are shown on the Alarms page. The status of certain well known alarms can be found in the Well-Known Alarms subpage.

### Configuration Page

Any information regarding the configuration of the device can be found on the configuration page, like nominal voltage and nominal frequency.

## Notes

The Vertiv EXL S1 requires the configuration of SNMP on the device to allow the connector to poll data.
