---
uid: Connector_help_Brandywine_Communications_FDU-160i
---

# Brandywine Communications FDU-160i

This connector allows you to monitor and set different variables on the Brandywine FDU-160i device using SNMP.

The FDU-160i is a signal distribution amplifier contained in a compact 1U rack-mount chassis, which is among others used in secure communication systems, satellite ground stations, digital television broadcasting, and systems requiring highly reliable frequency outputs. The system accepts two frequency inputs (typically 10 MHz). It provides automatic changeover if one of the online source inputs fails, and each input is capable of driving all sixteen outputs. Manual source selection override is available on the front panel or through the Ethernet interface.

User control of the unit happens via a built-in web browser with graphical interface or directly through this connector via SNMP.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

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

### General

The General page contains information about the device: the Serial Number, Product Name, Version, and Location.

### Reference and Inputs

On this page, you can view and change the configuration of the reference data and input data, including the thresholds and volt unit selection.

### Output Status

This page displays status information for output data.

### Output Config

This page allows you to configure the different output ports (1-16) as well as their alarm thresholds.

### Traps

This page contains a table with the trap configuration.

### Offsets

This page allows the user to configure offsets based on time and units.

### Configuration

On this page, you can configure IP addresses and view the currently configured IP addresses.
