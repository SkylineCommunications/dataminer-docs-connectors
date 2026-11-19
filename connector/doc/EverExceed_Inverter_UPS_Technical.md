---
uid: Connector_help_EverExceed_Inverter_UPS_Technical
description: "Configure the EverExceed Inverter UPS connector in DataMiner, including SNMP setup, monitoring pages, writable controls, alarms, and polling intervals."
---

# EverExceed Inverter UPS Technical

## About

The **EverExceed Inverter UPS** connector monitors EverExceed inverter and UPS devices over SNMP v2c. It reads device identity, power and environmental measurements, operating state, and alarm information from the device's enterprise MIB.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses an SNMP v2c connection. Configure the following when creating the element:

- **IP address/host**: IP address of the inverter/UPS.
- **IP port**: *161* by default.
- **Get community string**: Community configured on the device for reading.
- **Set community string**: Community configured on the device for control actions.

### Initialization

After creating the element, verify that SNMP polling is enabled on the device and that the configured community strings are accepted. No additional connector-specific initialization is required. Set thresholds for analog measurements according to the device specifications and operational requirements; vendor-confirmed threshold values are not provided by the connector.

## How to Use

### General Page

The **General** page presents the inverter operating mode and main supply priority, along with power and environmental readings:

- DC input voltage, AC input voltage and frequency.
- Output frequency, voltage, current, apparent power, and load ratio.
- Internal and ambient temperatures.
- Fan and alarm-sound status.

The main supply priority parameter shows whether AC or DC is preferred. A control on this page allows the priority to be changed on devices that accept the corresponding SNMP set.

### Alarms Page

The **Alarms** page shows the raw alarm code, a summary and count of active alarms, and a table decoding bits B0 through B15. The table identifies each bit and shows whether it is active. The summary and count are derived from bits B3 through B15, excluding reserved bit B9.

The raw alarm code is polled every 10 seconds. The connector does not process the device's alarm-change trap.

### Utility Page

The **Utility** page displays the product name, firmware version, and firmware date reported by the device.

### Options Page

The **Options** page displays device system time and provides these controls:

- **Synchronize System Time** sets the device time to the current DataMiner time.
- **Turn off Timer** displays and sets the device turn-off timer in minutes.
- **Clear Alarm Record** sends the device command to clear its alarm record.

The synchronization, timer, and alarm-record controls send SNMP set requests. Ensure the set community is configured and that the device permits these operations before using them.

### Polling Intervals

| Data | Interval |
|------|----------|
| Alarm code | 10 seconds |
| Electrical measurements, environmental values, supply priority, power state, and timer/alarm-record values | 30 seconds |
| System time | 5 minutes |
| Product name and firmware version/date | 1 hour |

Each polling group is also polled at startup.
