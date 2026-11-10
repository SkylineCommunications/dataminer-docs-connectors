---
uid: Connector_help_2WCOM_FM2TS_MPEG_Encoding_Gateway
---

# 2WCOM FM2TS MPEG Encoding Gateway

## About

This connector monitors the status of the **2WCOM FM2TS MPEG Encoding Gateway**.

This connector uses **SNMP** to retrieve information from the device to monitor the temperature, fans, power supplies and Gateway tuner status.

## Configuration

### Creation

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

## How to Use

### General

This page displays the system information.

### Device Status

This page displays the device temperature, the fan and power supply unit readings, and the alarm status.

### Tuner Status

This page displays the status of the tuner.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
