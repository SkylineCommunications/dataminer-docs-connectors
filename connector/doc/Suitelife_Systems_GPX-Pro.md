---
uid: Connector_help_Suitelife_Systems_GPX-Pro
description: "Monitor and control Suitelife Systems GPX-8 Pro and GPX-32 Pro remote site units over MQTT, with relay control and device alarm handling."
---

# Suitelife Systems GPX-Pro

## About

The Suitelife Systems GPX-Pro (GPX-8 Pro and GPX-32 Pro) is a remote site monitoring and control unit that collects status inputs, analog sensor readings, and ping and SNMP checks, and drives relay outputs. It publishes its data through the GPX-Pro MQTT API.

This connector connects to the MQTT broker used by the GPX-Pro, for example [Eclipse Mosquitto](https://mosquitto.org/), and receives device updates in near real time. It shows all device channels, alarms, and connections, and lets operators control relays and change channel settings on the device. The connector also has an HTTP connection to the device IP address, but this is only used to open the device web interface.

## Key Features

- **Automatic channel discovery**: Status inputs, analog inputs, relays, and SNMP and ping channels are received from the broker as soon as the device publishes them, and placed in separate tables.

- **Relay control**: Latching relays can be switched on and off, and pulse relays can be triggered, with a confirmation before each command.

- **Device alarm overview**: Active GPX alarms are listed with severity, value, and acknowledgment details, and can be acknowledged individually or all at once.

- **Write-through channel configuration**: Labels, on/off texts, GPX channel numbers, ping hosts, pulse durations, and analog calibration can be changed and are sent to the device.

- **Secure broker connection**: Username/password authentication and server or mutual TLS are supported.

## Use Cases

### Remote Site Monitoring

**Challenge**: Remote sites such as transmitter or cabinet locations have door contacts, power and HVAC status inputs, and environmental sensors that must be monitored centrally.

**Solution**: The GPX-Pro publishes all status and analog channels to an MQTT broker, and the connector shows them as soon as they change.

**Benefit**: Operators see site conditions next to the rest of the infrastructure and are informed as soon as a sensor or input changes.

### Remote Equipment Power Cycling

**Challenge**: Recovering equipment at an unmanned site often requires a truck roll to power cycle a device.

**Solution**: Operators switch or pulse a GPX relay from the Relays table, for example to power cycle a frozen device.

**Benefit**: Faster recovery and fewer site visits.

### Centralized Alarm Handling and Acknowledgment

**Challenge**: Alarms raised by the GPX-Pro are only visible in its own web interface, so they are easily missed.

**Solution**: The connector lists the active GPX alarms and lets operators acknowledge them on the device.

**Benefit**: One place to handle alarms from all GPX-Pro units.

## Technical Reference

### Prerequisites

- **An MQTT broker**, such as Eclipse Mosquitto, reachable from both the GPX-Pro and the DataMiner Agent.

- **A GPX-Pro with firmware 3.0.x**, with MQTT enabled and a known topic prefix.

- **DataMiner 10.4.0.0-14003 or higher**.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Suitelife_Systems_GPX-Pro_Technical).
