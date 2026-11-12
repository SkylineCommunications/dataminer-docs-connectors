---
uid: Connector_help_EverExceed_Inverter_UPS_Technical
---
# EverExceed Inverter UPS Technical

## About

The **EverExceed Inverter UPS** connector monitors EverExceed inverter and UPS devices over SNMP v2c. It reads device identity, power and environmental measurements, operating state, and alarm information from the device's enterprise MIB.

The protocol does not list specific supported product models or firmware versions. Confirm that the target device exposes the OIDs used by the connector before deployment. The connector requires DataMiner 10.4.0.0 build 14003 or later.

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMP v2c connection. Configure the following when creating the element:

| Setting | Value |
|---------|-------|
| **IP address/host** | IP address of the inverter/UPS |
| **IP port** | *161* by default |
| **Bus address** | Not required |
| **Get community string** | Community configured on the device for reading |
| **Set community string** | Community configured on the device for control actions |

The element requires network access from the DataMiner Agent to the device. Read-only monitoring requires a valid get community. To use the connector's write controls, configure a set community with the required device permissions.

### Initialization

After creating the element, verify that SNMP polling is enabled on the device and that the configured community strings are accepted. No additional connector-specific initialization is required. Set thresholds for analog measurements according to the device specifications and operational requirements; vendor-confirmed threshold values are not provided by the protocol.

## How to use

The connector starts polling after the element is created. The following sections describe the data pages and controls exposed by the connector.

### General page

The **General** page presents the inverter operating mode and main supply priority, along with power and environmental readings:

- DC input voltage, AC input voltage and frequency.
- Output frequency, voltage, current, apparent power, and load ratio.
- Internal and ambient temperatures.
- Fan and alarm-sound status.

The main supply priority parameter shows whether AC or DC is preferred. A control on this page allows the priority to be changed on devices that accept the corresponding SNMP set.

### Alarms page

The **Alarms** page shows the raw alarm code, a summary and count of active alarms, and a table decoding bits B0 through B15. The table identifies each bit and shows whether it is active. The summary and count are derived from bits B3 through B15, excluding reserved bit B9.

The raw alarm code is polled every 10 seconds. The connector does not process the device's alarm-change trap.

### Utility page

The **Utility** page displays the product name, firmware version, and firmware date reported by the device.

### Options page

The **Options** page displays device system time and provides these controls:

- **Synchronize System Time** sets the device time to the current DataMiner time.
- **Turn off Timer** displays and sets the device turn-off timer in minutes.
- **Clear Alarm Record** sends the device command to clear its alarm record.

The synchronization, timer, and alarm-record controls send SNMP set requests. Ensure the set community is configured and that the device permits these operations before using them.

### Polling intervals

| Data | Interval |
|------|----------|
| Alarm code | 10 seconds |
| Electrical measurements, environmental values, supply priority, power state, and timer/alarm-record values | 30 seconds |
| System time | 5 minutes |
| Product name and firmware version/date | 1 hour |

Each polling group is also polled at startup.
