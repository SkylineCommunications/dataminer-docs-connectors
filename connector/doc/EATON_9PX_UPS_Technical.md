---
uid: Connector_help_EATON_9PX_UPS_Technical
---

# EATON 9PX UPS

## About

This connector is used to monitor the EATON 9PX UPS device via SNMP.

The Eaton 9PX is an online UPS featuring ABM technology, which extends battery service life up to 50 percent. It is used in IT, edge networks, healthcare, universities, K-12, industrial automation, and harsh electrical environments.

## Configuration

### Connections

#### SNMP Connection - Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The connector exposes both a **Web Interface** page (`http://[Polling Ip]/`) and an **HTTPS Web Interface** page (`https://[Polling Ip]/`).

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Page overview

The element created with this connector has the following pages:

- **General**: System identification (manufacturer, model, software version, serial number) and battery status, including Battery Time Remaining, Battery Voltage, Battery Current, Battery Capacity, Advanced Battery Management Status, Battery Status, Battery Failure Status, Availability of Battery, Battery Aged, and Battery Low Capacity. From here, operators can also navigate to the Battery Thresholds page ([from 1.1.0.x onwards](#new-in-110x-battery-configuration-thresholds)).
- **Interfaces**: Network interface table.
- **Inputs / Input Details**: Input voltage, frequency, and related electrical parameters.
- **Outputs / Output Details**: Output voltage, current, power, frequency, and Output Status.
- **Bypasses / Bypass Details**: Bypass voltage, frequency, and status.
- **Environment / Environment Details**: Ambient and remote (EMP) temperature and humidity, including the EMP communication status parameter ([from 1.1.0.x onwards](#new-in-110x-emp-remote-communication-status)).
- **Sensors, Temperature, Humidity, Digital Inputs**: Sensor probe identification, configuration, monitoring, and min/max values.
- **Tests**: Allows you to start a UPS self-test (e.g., Test Battery) and reports the resulting test status (Passed, Failed, In Progress, etc.).
- **Configurations**: General UPS configuration (output voltage, install date, max trap level, agent/serial info), plus the Audible Alarm Control parameter ([from 1.1.0.x onwards](#new-in-110x-audible-alarm-control)).
- **Battery Threshold Configurations / Battery Thresholds**: Dedicated pages for the battery protection thresholds (see [Battery Configuration Thresholds](#new-in-110x-battery-configuration-thresholds)).
- **Alarms**: Active alarm table, with alarm descriptions resolved to readable text.
- **Web Interface / HTTPS Web Interface**: Embedded links to the device's own web interface.

### New in 1.1.0.x: Battery Configuration Thresholds

Three read/write parameter pairs introduced in 1.1.0.x allow operators to view and adjust the battery protection thresholds, displayed on the **Battery Threshold Configurations** and **Battery Thresholds** page:

- **Battery Capacity Threshold**: Battery charge percentage below which the UPS turns off to protect the battery from over-discharge.
- **Battery Time Remaining Threshold**: Remaining runtime, in seconds, below which the UPS declares a low battery condition.
- **Battery Safe Restart Threshold**: Battery charge percentage that must be reached before the UPS automatically restarts its output after AC input power returns.

All three parameters are monitored and can be written back to the device.

### New in 1.1.0.x: EMP Remote Communication Status

A read-only, monitored parameter on the **Environment** page reports the communication status between the UPS agent and an attached Environment Monitoring Probe (EMP): Unknown, Communication OK, or Communication Lost. This gives an early warning when temperature/humidity readings from the probe may be stale because of a lost connection.

### New in 1.1.0.x: Audible Alarm Control

A read/write parameter on the **Configurations** page lets operators control the UPS audible alarm behavior:

- **Enabled**: The audible alarm sounds for every alarm condition.
- **Disabled On Battery**: The alarm stays quiet while the UPS is running on battery power.
- **Disabled Always**: The alarm is permanently muted.

### New in 1.1.0.x: Output Status — Additional Value

Starting from 1.1.0.x, the Output Status parameter on the **Outputs** page also reports a fourth state, *Powered - No Continuity*, indicating the output is powered but the continuity feature is turned off.

### New in 1.1.0.x: Additional alarm descriptions

Starting from 1.1.0.x, the active alarms table on the **Alarms** page translates 11 additional alarm conditions into readable descriptions: Alarm Charger Voltage, Alarm Short Circuit, Emergency Switch Off, Alarm Battery Not Present, Alarm Thermal Overload, Alarm Input Wiring Fault, Battery Communication Lost, On Buck, On Boost, On High Efficiency, and Degraded Mode Alarm.

## DataMiner Connectivity Framework

This connector does not support the DataMiner Connectivity Framework (DCF).

## Notes

### Outstanding follow-up items

- **Alarm template for EMP communication status**: Severity mapping (Communication Lost = Critical, Unknown = Warning, Communication OK = Normal) needs to be configured via DataMiner alarm templates.
- **Battery test verification**: The existing Test Battery functionality should be exercised on a live element to confirm it remains functional, ideally during a low-risk window.