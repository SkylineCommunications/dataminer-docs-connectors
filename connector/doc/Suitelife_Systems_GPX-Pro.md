---
uid: Connector_help_Suitelife_Systems_GPX-Pro
description: "Monitor and control Suitelife Systems GPX-Pro remote site units via MQTT in DataMiner, tracking channels, sensor readings, alarms, and relay control."
---

# Suitelife Systems GPX-Pro

## About

The Suitelife Systems GPX-Pro is a remote site monitoring and control unit that collects status inputs, analog sensor readings, ping and SNMP checks, and drives relay outputs. It publishes its data through the GPX-PRO MQTT API.

This connector connects to the MQTT broker used by the GPX-Pro. It shows all device channels, alarms, and connections in DataMiner, and it lets operators control relays and change channel settings on the device directly from DataMiner.

## Key Features

- **Automatic channel discovery**: Status inputs, analog inputs, relays, SNMP channels, and ping channels are detected from the device and placed in separate tables, without manual configuration per channel.

- **Relay control**: Latching relays can be switched on and off, and pulse relays can be triggered, directly from DataMiner.

- **Device alarm overview**: Active GPX alarms are listed with severity, value, and acknowledgment details, and can be acknowledged individually or all at once.

- **Write-through channel configuration**: Labels, on/off texts, GPX channel numbers, ping hosts, pulse durations, and analog calibration can be changed in DataMiner and are sent to the device.

- **Device health monitoring**: Device online state, firmware version, free storage, uptime, and reboot detection are available for alarming and trending.

- **Secure MQTT connection**: Username/password authentication and server or mutual TLS are supported.

## Use Cases

### Remote Site Monitoring

**Challenge**: Remote sites such as transmitter or cabinet locations have door contacts, power and HVAC status inputs, and environmental sensors that must be monitored centrally.

**Solution**: The GPX-Pro publishes all status and analog channels to MQTT, and the connector shows them in DataMiner as table rows for which alarm monitoring and trending can be enabled.

**Benefit**: Operators see site conditions next to the rest of the infrastructure in DataMiner and get alarms as soon as a sensor or input changes.

### Remote Equipment Power Cycling

**Challenge**: Recovering equipment at an unmanned site often requires a truck roll to power cycle a device.

**Solution**: Operators use the Relay table to switch or pulse a GPX relay from DataMiner, for example to power cycle a frozen device.

**Benefit**: Faster recovery and fewer site visits.

### Centralized Alarm Handling and Acknowledgment

**Challenge**: Alarms raised by the GPX-Pro are only visible in its own web interface, so they are easily missed.

**Solution**: The connector lists the active GPX alarms in DataMiner and lets operators acknowledge them there.

**Benefit**: One place to handle alarms, with acknowledgment status kept in sync with the device.

## Technical Reference

### Prerequisites

- **An MQTT broker** reachable from the DataMiner Agent is needed for the communication between DataMiner and the GPX-Pro.

- **A GPX-Pro with the MQTT API enabled** and a known topic prefix is required to receive data and send commands.

- **DataMiner 10.4.0.0-14003 or higher** is required to run the connector.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Suitelife_Systems_GPX-Pro_Technical).