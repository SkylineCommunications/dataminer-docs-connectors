---
uid: Connector_help_RevGo_BUC_Technical
---

# RevGo BUC

## About

This connector integrates the RevGo BUC device into DataMiner, providing monitoring of RF performance, device health, alarms, and configuration settings via SNMP.

## Configuration

### Connections

#### SNMP Connection – RevGo BUC

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The IP address of the device.

SNMP Settings:

- **Port number**: Default 161.
- **Get community string**: Typically *public*.
- **Set community string**: Typically *private*.

## How to Use

### General Page

This page provides system and network information:

- Firmware Version
- Hardware Version
- Device Name
- Runtime
- Number
- System Description
- System Contact
- System Location
- IP Address
- IP Mask
- IP Gateway

### Device Status Page

This page provides real-time operational metrics:

- Input Power
- RF Power
- BUC Gain
- Mute Status
- Fan Speeds (Fan 1–4)
- Redundancy State
- ALC State
- Current Band
- ALC Target Power
- Temperature
- Device Clock Reference
- ALC Offset
- Redundancy Type

The **Restart** button on this page triggers a device reboot. Use this button with caution.

### Alarms Page

This page displays alarm status information:

- PLL Alarm
- Fans Alarm
- HPA Alarm
- Input Overdrive Alarm
- RF Alarm
- Temperature Alarm
- ALC Alarm

### Interface Setup Page

This page contains configuration-related parameters:

- LED State
- Serial Port
- OpenBMIP Support

### Web Interface Page

This page provides direct access to the web interface of the device.

## Notes

- SNMP must be enabled on the device.
- RF-related parameters depend on active transmission conditions.
- Alarm states should be monitored continuously for safe operation.
