---
uid: Connector_help_EverExceed_Inverter_UPS
---
# EverExceed Inverter UPS

## About

The EverExceed Inverter UPS connector monitors inverter and UPS operating conditions over SNMP. It brings key electrical measurements, environmental readings, operating state, and device alarm information into DataMiner to support operational visibility.

The connector reads data from vendor-specific SNMP objects. The protocol does not enumerate specific product models or firmware versions; confirm compatibility with the target device and its SNMP implementation before deployment.

## Key Features

- Monitor DC and AC input voltage and frequency, output voltage and frequency, output current and apparent power, and load ratio.
- Track inverter mode, AC/DC supply priority, fan and buzzer status, and internal and ambient temperatures.
- Decode the device alarm register into a bit-level status table and an active-alarm summary.
- View product name and firmware information reported by the device.
- Where supported by the device, use the connector controls to select AC or DC supply priority, set the turn-off timer, synchronize system time, and clear the device alarm record.
- Review measurements and status through the General, Alarms, Options, and Utility pages.

## Use Cases

### Monitor power conditions

**Challenge:** Power input or output conditions can change without being obvious from a device's front panel.

**Solution:** The connector collects input and output electrical measurements and load ratio in DataMiner.

**Benefit:** Operators can follow power conditions centrally and apply their own alarm thresholds to the reported values.

### Identify inverter and equipment alarms

**Challenge:** A single device alarm register can be difficult to interpret during troubleshooting.

**Solution:** The connector decodes the register into named bit states and summarizes active alarm conditions.

**Benefit:** Operators can quickly see reported conditions such as inverter faults, overloads, temperature shutdown, and AC or DC input problems.

### Keep operational context together

**Challenge:** Device state, environmental readings, and firmware details may be spread across separate interfaces.

**Solution:** The connector presents operating state, temperatures, fan and sound status, and product information alongside electrical measurements.

**Benefit:** Operators have more context when assessing device behavior and investigating service impact.

## Technical Reference

For SNMP setup, polling intervals, page-by-page parameter details, writable controls, and alarm interpretation, see the [technical documentation](xref:Connector_help_EverExceed_Inverter_UPS_Technical).
