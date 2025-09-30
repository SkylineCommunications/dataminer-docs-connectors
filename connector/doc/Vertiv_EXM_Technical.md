---
uid: Connector_help_Vertiv_EXM_Technical
---

# Vertiv EXM

## About

With this connector, you can monitor EXM UPS devices through SNMP communication to validate the UPS battery status and levels, inputs, outputs and bypass data.

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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector contains multiple pages. The pages structure is the same as on the web interface of the device.

- **General**: Displays basic system information, such as the name, description, uptime, location, and interfaces of the device.
- **Inputs**: Displays input power, frequency, and phase information.
- **Bypass**: Displays the bypass voltages and frequencies.
- **Battery**: Displays the battery percentage, temperature, and charge status.
- **Inverter**: Displays the inverter state and status.
- **Outputs**: Displays output power, RMS phase, and voltage information.
- **Power Modules**: Displays the device power supply input voltages, frequency, and status information.
- **Status**: Displays the main operational status information of the device.
