---
uid: Connector_help_Thales_S7HP
---

# Thales S7HP

## About

The Thales S7HP is a high-power shortwave radio transmitter. With this connector, you can monitor and control the transmitter's data with DataMiner's alarm monitoring and trending features.

## Key Features

- **Transmitter monitoring**: Monitor the key transmitter functions, such as frequency, measured power, modulation mode, and operating status.
- **Modulator monitoring**: Monitor the full set of modulator parameters, including audio, MDI, DRM, GPS timing, and version information.
- **Alarm and fault management**: Keep track of the device alarms, faults, and module states, including status tables with date information.
- **Transmitter control**: Send commands to the transmitter, such as power on/off, rearm, frequency, and audio configuration changes.
- **Modulator configuration**: Configure the modulator remotely, including audio, SFN, network, and alarm threshold settings.
- **Customizable polling**: Fine-tune the polling frequency of each data group via the Polling Manager.
- **Web interface**: Access the device's web interface directly from the element.

## Use Cases

Typical use cases include:

- Monitoring transmitter operations and verifying that transmission parameters remain within expected operating conditions.
- Investigating alarms, faults, and hardware issues by correlating status information with reported events and measurements.
- Validating software and firmware versions during commissioning, maintenance, or upgrade activities.
- Managing audio, modulation, synchronization, and network-related settings from a centralized interface.
- Performing remote control actions such as transmitter power management and operational adjustments.
- Integrating transmitter notifications into monitoring workflows through SNMP events and alarm reporting.

## Technical Reference

### Prerequisites

- **SNMP connectivity**: The device must be reachable via SNMP from the DataMiner Agent.
- **Web interface access**: To use the **web interface** feature, the client machine must have network access to the device.
