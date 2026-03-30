---
uid: Connector_help_Alpha_Combi_UPS_AC_DC_Technical
---

# Alpha Combi UPS AC DC

## About

The Alpha Combi UPS AC DC connector enables monitoring of an uninterruptible power supply system. It allows operators to oversee the power system health and performance through a centralized interface.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Once the element has been configured, the connector will automatically begin polling data from the device via SNMP. It retrieves information on the power system status, network interfaces, rectifier and inverter modules, and battery health.

Overview of the UPS system, including the controller information, is provided on the **General** page.

All the network interfaces, along with the overall status and traffic information, are present on the **Interfaces** page.

Information regarding the voltage and current levels and the overall status of the rectifier module is provided on the **Rectifier** page.

The **Battery** page provides the overview of all the battery parameters, including voltage, current, temperature, and capacity.

The **Inverter** page provides the general, output and input parameters of the inverter module.

Comprehensive view of all the parameters available from the device controller is present on the **Cordex HP Controller** page. Providing complete information regarding the UPS system.