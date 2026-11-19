---
uid: Connector_help_EverExceed_Inverter_UPS
description: "Monitor EverExceed inverter and UPS devices in DataMiner over SNMP, including electrical measurements, operating status, environmental data, and alarms."
---

# EverExceed Inverter UPS

## About

The EverExceed Inverter UPS connector monitors inverter and UPS operating conditions over SNMP. It brings key electrical measurements, environmental readings, operating state, and device alarm information into DataMiner to support operational visibility.

## Key Features

- **Electrical measurements**: Monitor DC and AC input voltage and frequency, output voltage and frequency, output current and apparent power, and load ratio.
- **Operating status**: Track inverter mode, AC/DC supply priority, fan and buzzer status, and internal and ambient temperatures.
- **Alarm decoding**: Decode the device alarm register into a bit-level status table and an active-alarm summary.
- **Device information**: View product name and firmware information reported by the device.
- **Device controls**: Where supported by the device, select AC or DC supply priority, set the turn-off timer, synchronize system time, and clear the device alarm record.

## Use Cases

### Monitor Power Conditions

**Challenge**: Power input or output conditions can change without being obvious from a device's front panel.

**Solution**: The connector collects input and output electrical measurements and load ratio in DataMiner.

**Benefit**: Operators can follow power conditions centrally and apply their own alarm thresholds to the reported values.

### Identify Inverter and Equipment Alarms

**Challenge**: A single device alarm register can be difficult to interpret during troubleshooting.

**Solution**: The connector decodes the register into named bit states and summarizes active alarm conditions.

**Benefit**: Operators can quickly see reported conditions such as inverter faults, overloads, temperature shutdown, and AC or DC input problems.

### Keep Operational Context Together

**Challenge**: Device state, environmental readings, and firmware details may be spread across separate interfaces.

**Solution**: The connector presents operating state, temperatures, fan and sound status, and product information alongside electrical measurements.

**Benefit**: Operators have more context when assessing device behavior and investigating service impact.

## Prerequisites

- **DataMiner 10.4.0.0 (build 14003) or higher** is required to host the connector.
- The target device must expose the OIDs used by the connector; confirm compatibility with the target device and its SNMP implementation before deployment.

## Technical Reference

For SNMP setup, polling intervals, page-by-page parameter details, writable controls, and alarm interpretation, refer to the [technical documentation](xref:Connector_help_EverExceed_Inverter_UPS_Technical).
