---
uid: Connector_help_Thales_TDU2K5DD_UHF_DVB-T
description: "Monitor and control a Thales TDU2K5DD UHF DVB-T transmitter over SNMP, including exciter A/B redundancy, amplifiers, supplies, cooling, and power."
---

# Thales TDU2K5DD UHF DVB-T

## About

The **Thales TDU2K5DD UHF DVB-T** connector integrates a Thales TDU2K5DD UHF DVB-T transmitter into DataMiner over SNMP. The transmitter can be built as a single-drive or dual-drive unit; in a dual-drive unit, two exciters (Exciter A and Exciter B) back each other up, and the transmitter switches over to the reserve exciter when the active one fails.

The connector gives operators one place to follow the complete transmitter chain: the exciters, the amplifiers and their transistors, the power supplies, the cooling system, and the cabinets. Besides polling the device, it listens for the status traps the transmitter sends, so that a fault, a change-over, or a power reduction is visible in DataMiner right away. Key transmitter commands can be sent from the same element.

## Key Features

- **Transmitter health at a glance**: Follow the transmitter status, major fault, RF presence, VSWR, temperature, switch, synthesizer, GPS, and cooling faults from a single Status page, with alarm monitoring on each of them.
- **Power monitoring and trending**: Track the calibrated, measured, and requested power, and the forward, reflected, and antenna reflected power calculated in watts, with trending to spot a slow degradation of the output.
- **Exciter redundancy awareness**: See which exciter is on air, which one is the reserve, whether a change-over has occurred, and whether the change-over mode is manual or automatic. Each exciter has its own page with its modulator, synchronization, GPS, and correction status.
- **Full amplification chain**: Browse the amplifiers, pre-amplifiers, transistors, supplies, cooling units, and cabinets in tables that combine the live fault status with the physical location and structure information of each component.
- **Remote control**: Switch the transmitter on or off, change the switch-over mode, reduce the output power by 3 or 6 dB, choose the exciter on antenna, start or stop the reserve exciter, set the requested power, set the date and time, and reset the transmitter.
- **Polling load control**: Switch between full polling and a reduced mode that only refreshes a small set of parameters, and enable or disable a dedicated fast poll of the key alarm parameters.
- **Device supervision settings**: Manage the SNMP trap managers, email contacts, user profiles, and per-event trap and email settings of the transmitter.

## Use Cases

### Catching a Silent Change-Over

**Challenge**: In a dual-drive transmitter, a change-over to the reserve exciter keeps the service on air, so it can go unnoticed until the second exciter also fails.

**Solution**: The connector monitors the **Exciter On Air**, **Reserve Exciter**, and **Change Over Occured** parameters and refreshes them as soon as the transmitter sends its change-over or exciter fault trap.

**Benefit**: Operators are alerted to the loss of redundancy immediately and can plan the repair before the site goes off air.

### Spotting Output Power Degradation Early

**Challenge**: A gradual drop in forward power or a rising reflected power is hard to see in percentages that are refreshed only when somebody looks at the device.

**Solution**: The connector converts the measured percentages into **Forward Power (W)**, **Reflected Power (W)**, and **Reflected Antenna Power (W)**, trends them, and allows alarm thresholds on them.

**Benefit**: Antenna or amplifier problems show up as a trend before they become a fault.

### Keeping SNMP Load Low on Remote Sites

**Challenge**: A transmitter on a remote site with limited bandwidth should not be flooded with SNMP requests.

**Solution**: With **Polling All Active** set to *No*, the connector stops polling the detailed pages and only refreshes a handful of parameters every hour or every day, while **Fast Polling Active** keeps the key alarm parameters refreshed every 10 seconds.

**Benefit**: Critical alarms still arrive quickly, without the polling load of the full element.

## Technical Reference

### Prerequisites

- **SNMP connectivity**: The transmitter must be reachable via SNMP from the DataMiner Agent.
- **Trap destination**: To benefit from the trap-driven refresh of the status parameters, add the IP address of the DataMiner Agent to the managers of the transmitter (this can be done from the Supervision page of the element).
- **Web interface access**: To use the **Webinterface** page, the client machine must have network access to the transmitter on its HTTP port.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Thales_TDU2K5DD_UHF_DVB-T_Technical).
