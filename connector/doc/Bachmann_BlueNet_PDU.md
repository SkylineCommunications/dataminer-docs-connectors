---
uid: Connector_help_Bachmann_BlueNet_PDU
---

# Bachmann BlueNet PDU

## About

The Bachmann BlueNet PDU is an intelligent power distribution unit (PDU) for data centers and IT racks, available in the BN3000 to BN7500 series. With this connector, you can monitor the PDU's power distribution, energy consumption, and environmental data with DataMiner's alarm monitoring and trending features.

## Key Features

- **Device and inventory monitoring**: Monitor the general device information, such as product details, firmware versions, and the full inventory of connected devices.
- **Power monitoring**: Keep track of the electrical measurements per circuit, phase, fuse, and socket, including voltage, current, power, and energy values.
- **RCM and SPD monitoring**: Monitor the residual current monitoring (RCM) and surge protective device (SPD) states.
- **Sensor monitoring**: Monitor the connected environmental sensors, such as temperature, humidity, dew point, and pressure sensors.
- **Variable data overview**: Consult all measured variables, organized in dedicated overviews per type and per source, with configurable set points and thresholds.
- **Socket group management**: Keep track of the configured socket groups and their states.
- **Remote configuration**: Configure the device's SNMP, SMTP, NTP, Modbus, and syslog settings remotely.
- **Customizable polling**: Fine-tune the polling frequency of each data group via the Polling Manager.

## Use Cases

Typical use cases include:

- Monitoring power distribution across circuits, phases, fuses, and sockets to verify that load and consumption remain within expected operating conditions.
- Tracking energy consumption over time using trending on power and energy measurements for capacity planning and reporting.
- Investigating electrical issues by correlating residual current (RCM), surge protection (SPD), and fuse states with reported alarms and measurements.
- Monitoring the rack environment through connected sensors, such as temperature, humidity, dew point, and pressure, to prevent overheating and condensation.
- Validating firmware versions and device inventory during commissioning, maintenance, or upgrade activities.
- Managing thresholds and set points on measured variables to receive early warnings before critical limits are reached.
- Configuring SNMP, SMTP, NTP, Modbus, and syslog settings from a centralized interface.

## Technical Reference

### Prerequisites

- **SNMP connectivity**: The device must be reachable via SNMP from the DataMiner Agent.
- **Web interface access**: To use the **web interface** feature, the client machine must have network access to the device.

