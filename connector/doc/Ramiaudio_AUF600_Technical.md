---
uid: Connector_help_Ramiaudio_AUF600_Technical
---

# Ramiaudio AUF600

## About

The AUF600 is a digital audio mixer capable of handling cross-fading of three sources in AES/EBU format.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Polling Manager

This page contains a polling table where it is possible to change the **interval** and **state** of each polling group to cater to your specific use case. It also displays the last polled time and a **Poll** button that can be used to manually trigger the polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Contains general device information and settings.
- **Channel Status**: Contains channel status information and general channel settings.
- **Channel Error Frame**: Contains information on the error frames for each channel.
- **Channel Settings**: Contains core channel settings.
- **CSS Core Setting**: Contains core device settings.
- **Trap Configurations**: Contains SNMP trap and trap destination settings.
