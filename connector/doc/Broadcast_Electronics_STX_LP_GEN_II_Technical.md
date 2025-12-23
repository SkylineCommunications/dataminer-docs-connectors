---
uid: Connector_help_Broadcast_Electronics_STX_LP_GEN_II
---

# Broadcast Electronics STX LP GEN II

## About

The STX LP Generation II is a compact, low-power FM transmitter series (available in 1, 2, 3, and 5 kW models), engineered by Broadcast Electronics for professional broadcasting environments

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element has the following data pages:

- **General**: Displays the device information.
- **Transmitter**: Displays the transmiter information.
- **Power Amplifier**: Displays the Power Amplifier information.
- **Logs**: Displays the Latest Events.
