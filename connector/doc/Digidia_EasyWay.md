---
uid: Connector_help_Digidia_EasyWay
---

# Digidia EasyWay

## About

The Digidia EasyWay is an IP-to-ETI gateway used in DAB/DMB (Digital Audio/Multimedia Broadcasting) distribution networks. It receives an Ensemble Transport Interface (ETI) stream over IP, using either the EDI protocol or the Digidia proprietary protocol, and delivers a synchronized ETI output toward DAB/DMB modulators.

This connector monitors and configures a Digidia EasyWay gateway over SNMP, giving operators full visibility on the device status, the IP input, GPS/NTP synchronization, alarms, and the event log from within DataMiner.

## Key Features

- **Device monitoring**: Retrieves system information, firmware and hardware versions, the equipment state, and the last reported error of the gateway.
- **IP input and ETI output configuration**: Reads and configures the IP input connection mode (unicast/multicast), the used protocol (EDI or Digidia proprietary), the ETI output type, and the auxiliary output clock frequency.
- **Synchronization insight**: Monitors the synchronization mode (SFN/MFN) and the synchro source, including detailed GPS status such as lock state, visible satellites, position, SNR, leap seconds, and cable delay.
- **Alarm and event handling**: Processes SNMP trap alarm notifications, exposes the alarm relay status, and converts the device event log into a human-readable table.
- **Customizable polling**: Includes a Polling Manager that lets you enable, disable, and fine-tune the polling interval of each data set independently.

## Use Cases

### Centralized monitoring of DAB/DMB head-end gateways

**Challenge**: Broadcast operators run multiple EasyWay gateways across different sites and need a single pane of glass to follow their health and synchronization status.

**Solution**: The connector polls every gateway over SNMP and surfaces system state, GPS lock, and input status in DataMiner, while SNMP traps raise alarms in real time.

**Benefit**: Faster detection of synchronization or input issues and reduced time to resolution.

### Verifying SFN synchronization

**Challenge**: Single Frequency Network operation requires correct GPS synchronization and consistent timing across all transmitters.

**Solution**: The connector exposes the GPS status, number of visible satellites, SNR, leap seconds, cable delay, and the gateway-to-modulator maximum delay.

**Benefit**: Operators can confirm that timing is correct before and during transmission, preventing on-air degradation.

### Reducing maintenance effort with adaptive polling

**Challenge**: Polling every parameter at the same rate generates unnecessary load for slow-changing configuration data.

**Solution**: The Polling Manager lets operators tune or disable polling per data set.

**Benefit**: Lower device and network load while keeping critical data up to date.

## Technical Reference

### Prerequisites

- **SNMP access** to the Digidia EasyWay gateway is required for the connector to poll and configure the device.
- **SNMP traps** must be enabled on the device, with the DataMiner system configured as a trap target, in order to receive alarm notifications.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Digidia_EasyWay_Technical).
