---
uid: Connector_help_Site_Sentinel_Technical
---

# Broadcast Tools Site Sentinel

## About

The Site Sentinel® 16 G2 is a robust, full-featured, web-enabled sixteen-channel remote control featuring a desktop/mobile browser-compatible web interface (HTML5.) The system is equipped with 16 metering inputs (0 to 10 VDC), four virtual metering channels, 16 optically isolated status (logic) inputs, 33 programmable SPDT relays, which may be configured for ON, OFF, and pulsed operation, four temperature probe inputs, one internal temperature sensor, stereo silence sensor, and power failure input. It also includes built-in support for email alarms and SNMP.

## Configuration

### Connections

#### SNMP Connection - Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

An SNMP connection is used to retrieve all relevant data needed to monitor the Site Sentinel.

The **Meter** table on the **Meters** page contains custom columns (**Calibration Formula**, **Calibration Multiplier**, and **Expected Calculated Value**) that can be used to alter the incoming value from the device. If no alteration is needed, you can leave the columns set to their default values.
