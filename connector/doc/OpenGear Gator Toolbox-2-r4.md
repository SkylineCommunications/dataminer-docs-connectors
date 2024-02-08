---
uid: Connector_help_OpenGear_Gator_Toolbox-2-r4
---

# OpenGear Gator Toolbox-2-r4

The OpenGear Gator Toolbox-2-r4 is a UHD signal conversion problems solver.

This connector retrieves information from the device via SNMP. It displays basic information about the device, as well as current status of various device components such as fan door, power supply, and PSU status.

## About

### Version Info

| Range              | Key Features     | Based on    | System Impact    |
|--------------------|------------------|-------------|------------------|
| 1.0.0.x [SLC Main] | Initial version  | -           | -                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Rev 7                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Displays general parameters such as device name, IP addresses, and number of active slots.
- **Frame**: Displays general parameters of the device frame such as the supplier, serial number, and MAC address.
- **Hardware** Displays information of the frame hardware, such as the current and voltage readings and fan speed.
- **Power** Displays power-related details for PSU 1 and 2, alongside temperature and power consumption information for the device.
- **Setup** Displays the settings for certain faults. Allows the configuration of setting for faults.
- **Data Safe** Displays the frame's card instances and details. Allows to mask data safe warning.
- **Frame Glow** Displays the current LED settings of the device, and allows the configuration of settings such as LED mode and theme.
- **Alarms** Displays the device's current PSU 1 power, PSU 2 power, and hardware status.