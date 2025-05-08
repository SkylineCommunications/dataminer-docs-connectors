---
uid: Connector_help_Ramiaudio_AUF800_Technical
---

# Ramiaudio AUF800

## About

The AUF800 is a digital MPX autofader capable of seamlessly mixing two MPX sources in AES/EBU 192kHz format. This professional broadcast equipment features automatic and manual switching modes between primary and backup audio streams. With network connectivity via Ethernet, it offers remote control through a built-in web server, SNMP, and Ember+ protocols. The device includes comprehensive monitoring capabilities with a built-in MPX demodulator, front panel display, and remote GPI/GPO interfaces. Optional analog MPX input/output support and redundant power supply ensure maximum flexibility and reliability in radio broadcasting environments.

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

- **General**: Contains general device information, settings, and power supplies.
- **Input Channels**: Contains input channel status information and general channel settings.
- **GPIO**: Contains input GPIO status information and general GPIO settings.
- **SNTP Server Settings**: Contains SNTP settings.
- **CSS Core Setting**: Contains core device settings.
- **Trap Configurations**: Contains SNMP trap settings and trap destination settings.
