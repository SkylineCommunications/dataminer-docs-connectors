---
uid: Connector_help_Advantech_Wireless_Genesis-HP_Ku_SSPA-SSPB
---

# Advantech Wireless Genesis-HP Ku SSPA/SSPB

## About

The **Advantech Wireless Genesis-HP Ku SSPA/SSPB** connector monitors Advantech Wireless Genesis-HP Ku-band Solid State Power Amplifier (SSPA) and Solid State Power Block (SSPB) systems via SNMP. It provides real-time visibility into the overall system, redundancy configuration, individual RF units, and their internal devices.

## Key Features

- **RF unit monitoring**: Tracks attenuation, temperature, mute status, and RF switch status for each RF unit.
- **Device-level monitoring**: Monitors the individual devices (e.g., controllers, sensors) that make up each RF unit, including temperature and fault status.
- **Redundancy configuration**: Allows configuration of 1:1 and N+1 redundancy configurations, including switch position and redundancy hierarchy.

## Use Cases

### Monitor Amplifier Health and Faults Centrally

**Challenge**: Operators need a single view of the health of Ku-band SSPA/SSPB amplifiers spread across a redundant configuration.

**Solution**: Use the Advantech Wireless Genesis-HP Ku SSPA/SSPB connector to poll system, RF unit, and device status and surface faults such as mute conditions, temperature issues, and RF switch problems as DataMiner alarms.

**Benefit**: Reduces the time needed to detect and diagnose amplifier issues, minimizing the risk of service-affecting outages.

### Track Redundancy Switchover Status

**Challenge**: In 1:1 or N+1 redundant amplifier setups, operators need to know which unit is active and whether a switchover has occurred.

**Solution**: Use the connector's Redundancy page to monitor the current switch position and redundancy hierarchy of the system.

**Benefit**: Gives operators immediate insight into the redundancy state, supporting faster root-cause analysis after a switchover.

## Technical Reference

### Prerequisites

- **SNMPv3 access** to the Genesis-HP Ku SSPA/SSPB system, with read credentials configured on the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Advantech_Wireless_Genesis-HP_Ku_SSPA-SSPB_Technical).
