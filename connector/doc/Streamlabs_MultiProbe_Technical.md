---
uid: Connector_help_Streamlabs_MultiProbe
---

# Streamlabs MultiProbe

## About

MultiProbe is a comprehensive software-based monitoring system designed for digital television and radio broadcasting. It monitors both compressed and uncompressed signals and provides automated analysis, visualization, and alerting to ensure high-quality broadcast delivery.

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
- **Alarms**: Displays the active and history alarms.
