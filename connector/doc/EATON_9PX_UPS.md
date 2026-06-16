---
uid: Connector_help_EATON_9PX_UPS
---

# EATON 9PX UPS

## About

The EATON 9PX UPS is an online uninterruptible power supply with ABM technology, extending battery lifespan by up to 50%. This connector enables DataMiner to monitor and control the device via SNMP, giving operators real-time visibility into power health, battery status, environmental conditions, and active alarms — all from a single pane of glass.

## Key Features

- **Complete power chain visibility**: Monitor input and output voltage, current, power, frequency, and bypass status across all phases, so you always know the state of your power infrastructure.

- **Battery health and protection control**: View battery charge, runtime, and status in real time, and configure the thresholds that protect the battery from over-discharge, trigger low-battery warnings, and control when the UPS safely restarts after a power event.

- **Environmental monitoring**: Track temperature and humidity from both the built-in probe and any attached Environment Monitoring Probe (EMP), with clear alerts if the EMP connection itself is lost.

- **Remote alarm and control**: Acknowledge active alarms with human-readable descriptions, trigger UPS self-tests, and adjust device settings — including the audible alarm — directly from DataMiner without physical access to the unit.

- **Comprehensive alarm reporting**: The active alarms table resolves all UPS fault conditions into clear, readable descriptions, covering charger faults, short circuits, thermal overloads, battery communication issues, and more.

## Use Cases

### Preventing unplanned shutdowns due to battery over-discharge

**Challenge**: In environments with frequent short power events, the UPS battery can deplete faster than expected, risking an uncontrolled shutdown before the protected load is safely powered down.

**Solution**: Operators can configure the Battery Capacity Threshold and Battery Time Remaining Threshold directly from DataMiner. When either threshold is breached, a monitored alarm fires, giving the operations team time to react before the UPS shuts down.

**Benefit**: Reduces the risk of unexpected load loss by ensuring the UPS acts at the right charge level, and that operators are alerted early enough to take corrective action.

### Detecting silent sensor failures before they cause blind spots

**Challenge**: If an Environment Monitoring Probe (EMP) loses its connection to the UPS, temperature and humidity readings may go stale without any visible indication, leaving operators unaware of potentially unsafe environmental conditions.

**Solution**: The EMP Remote Communication Status parameter actively monitors the link between the UPS agent and the probe. A dedicated monitored alarm immediately flags when communication is lost, unknown, or restored.

**Benefit**: Ensures environmental monitoring gaps are detected and escalated immediately, preventing situations where hazardous conditions go unnoticed due to a failed sensor connection.

### Remotely managing UPS behavior across distributed sites

**Challenge**: In distributed or unmanned sites, adjusting UPS settings — such as silencing nuisance alarms or initiating a battery test — normally requires a physical visit or direct device access.

**Solution**: The connector exposes full read/write control over key settings (audible alarm behavior, battery thresholds) and UPS test initiation, all accessible from the DataMiner Cube interface or automatable via scripts.

**Benefit**: Reduces truck rolls and on-site interventions, enabling NOC teams to manage and verify UPS health remotely across all sites from a central platform.

## Technical Reference

### Prerequisites

- **SNMP access** to the EATON 9PX UPS is required (default port 161). Ensure the device is reachable from the DataMiner Agent and that SNMP community strings are correctly configured.

- **Network access to the device web interface** is required if operators intend to use the embedded Web Interface or HTTPS Web Interface pages within the connector.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_EATON_9PX_UPS_Technical).
