---
uid: Connector_help_Vertiv_EXM_Technical
---

# Vertiv EXM

## About

This connector will allow the monitoring of the EXM UPS devices through SNMP communication to validate UPS battery status and levels, inputs, outputs and bypass data.

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

### Initialization

The user needs to set the IP Address of the device on the element settings to start polling the device information.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector contains multiple pages. The pages structure is the same as the device shows on its UI.

- **General:** On this page, the user will see the basic system information, like name, description, uptime, location and interfaces.
- **Inputs:** On this page, the user will see the input powers, frequencies and phases.
- **Bypass:** On this page, the user will see the bypass voltages and frequencies.
- **Battery:** On this page, the user will see the battery percentage, temperature and  charge status.
- **Inverter:** On this page, the user will see the inverter state and status.
- **Outputs:** On this page, the user will see the output powers, RMS phases and voltages.
- **Power Modules:** On this page, the user will see the device power supply input voltages, frequency and statuses.
- **Status:** On this page, the user will see the device main operational statuses.
