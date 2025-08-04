---
uid: Connector_help_AvL_Technologies_AAQ_Controller_Technical
---

# AvL Technologies AAQ Controller – Technical

## Abouts

The AvL Technologies AAQ Controller connector enables DataMiner to monitor AvL Technologies' Antenna Acquisition and Pointing (AAQ) systems. It communicates with the device using SNMPv2, providing real-time access to system state, health, positioning, and configuration data. The connector retrieves information such as antenna position, motor status, limit switches, GPS data, and more, allowing for comprehensive remote monitoring of the antenna system.

### Version Info

| Range         | Features                                                                                                         | Based on | System Impact |
|---------------|------------------------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | <ul><li>Initial release of the AvL Technologies AAQ Controller connector.</li><li>SNMPv2-based monitoring of antenna system state, health, position, and configuration.</li></ul> | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|-------------------|
| 1.0.0.x | 2.9.2.r1.588      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|----------------|--------------------|-------------------|---------------------|
| 1.0.0.x | No             | Yes                | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No additional configuration of parameters is required for a newly created element. The connector will automatically start polling the device for all supported parameters.

### Web Interface

The web interface of the device is only accessible when the client machine has network access to the product.

## How to Use

The connector provides a structured view of the AvL AAQ Controller, with dedicated pages for System, Azimuth, Elevation, Polarity, Wing, and GPS data. Each page displays real-time values for key parameters such as position, health, limit switches, and motor status. The connector uses SNMPv2 polling to retrieve all data; no SNMP traps are processed.

- **System**: Monitor overall system state, health, uptime, and configuration.
- **Azimuth/Elevation/Polarity**: View and monitor axis positions, limit switch statuses, and motor health.
- **Wing**: Monitor deployment and safety status of reflector wings.
- **GPS**: Access GPS status, heading, and location data.

All relevant alarms are automatically generated based on parameter thresholds and status values as defined in the protocol.

### Examples

#### Monitoring Antenna State

*On the **System** page, you can view the current system state, check if the antenna is homed, and see if the signal is locked. This allows you to quickly assess the operational status of the antenna system.*

#### Position and Limit Switches

*The **Azimuth** and **Elevation** pages display the current positions and the status of limit switches. For example, you can verify if the antenna is stowed or if any axis has reached its movement limit, which is essential for safe operation.*

#### Motor and Safety Status

*On the **Polarity** and **Wing** pages, you can monitor the health and initialization status of the motors, as well as the deployment state of reflector wings. This helps in identifying hardware issues or misconfigurations.*

#### GPS Data

*The **GPS** page provides real-time information about the antenna's location, heading, pitch, and roll, which is useful for mobile or transportable systems.*
