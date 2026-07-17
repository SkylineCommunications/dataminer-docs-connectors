---
uid: Connector_help_Delta_Power_Solutions_Orion_Controller_Technical
---

# Delta Power Solutions Orion Controller

## About

This connector can be used to monitor and configure the Orion Controller from Delta Power Solutions.

It uses SNMP to communicate with the device. The version 1.1.0.x is an overhaul of the previous version 1.0.1.x.

> [!NOTE]
> This connector **requires .Net Framework 4.0** or higher.

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the data pages detailed below.

### General

This page contains general information about the system, such as the System Name and System Date Time.

It also shows the information about the system itself, such as the System Voltage, Battery Temperature, and System Power. In addition, it also shows the IP details, such as the IP Address, Subnet Mask, and Default Gateway.

### Rectifier

This page shows the Rectifier Table, which contains information about the rectifiers in the system. Page buttons provide access to the Rectifier Group Table, Rectifier Functions, and Rectifier subpages.

### Battery

This page contains general information about the battery. Several page buttons are available that lead to subpages with more detailed information and settings.

### Load

This page allows you to monitor input power quality and detect supply issues. It displays three-phase AC mains input measurements, including voltages for Line 1, Line 2, Line 3, and line-to-line voltages.

The page also contains a page button to display Load String Measurements table.

### Inventory

This page allows you to identify the hardware configuration and system composition. It shows the Inventory Table, which contains information about the inventory of the system, including installed components such as rectifiers, controllers, and modules.

### PDUs

This page allows you to monitor and configure power distribution across channels. It displays Power Distribution Unit (PDU) information, including device details, channel configuration, and channel measurements.
