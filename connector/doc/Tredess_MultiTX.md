---
uid: Connector_help_Tredess_MultiTX
description: "Learn how the Tredess MultiTX connector monitors and controls transmitter, redundancy, power, cooling, and synchronization modules."
---

# Tredess MultiTX

## About

The **Tredess MultiTX** is a multi-module digital terrestrial television (DTT) transmitter platform from Tredess, supporting DVB-T and DVB-T2 modulation. A single chassis can host transmitter (TX) modules together with a redundancy switching unit (NP1), power supply units (PSUs), and synchronization (SYNC/GNSS) modules.

This connector allows DataMiner to monitor and control the Tredess MultiTX platform over SNMP, providing full visibility of all modules in the chassis, from RF output power and modulation settings down to power supplies, cooling, and GNSS synchronization.

## Key Features

- **Complete TX module monitoring and control**: Monitor detailed information for every transmitter module, including input levels, forward power, RF input/output configuration, IF processor, echo canceller, precorrector, modulator, and amplifier status.

- **DVB-T and DVB-T2 configuration**: Access and configure a multitude of settings from DataMiner, including system, network, modulation, frame, and PLP settings.

- **Input redundancy and switching**: Configure ASI 1/2 and IP socket input switching, and manage 1+1 redundancy through the NP1 unit, including monitoring switching causes and automatic verifications.

- **Infrastructure health**: Monitor the complete transmission chain, including power supply units, cooling and fan tables, battery, modem, and network status.

- **Alarming, trending, and trap processing**: Get notified instantly in case of faults thanks to hundreds of monitored and trended parameters, combined with real-time SNMP trap processing.

- **Flexible polling**: Use the built-in polling manager to tune the polling rate of each data group individually, optimizing SNMP load per element.

## Use Cases

### Nationwide DTT Transmitter Fleet Monitoring

**Challenge**: Broadcast network operators run large fleets of terrestrial transmitters at remote sites, where undetected degradation (e.g., reduced forward power or drifting MER) leads to viewer-impacting outages.

**Solution**: The connector continuously polls each MultiTX chassis and raises DataMiner alarms on RF measurements, module status, and infrastructure health, while SNMP traps deliver instant fault notifications.

**Benefit**: Faults and gradual degradation are detected early, reducing off-air time and avoiding unnecessary site visits.

### Redundancy Assurance

**Challenge**: 1+1 transmitter redundancy is only useful if the reserve chain is genuinely healthy and switching logic is correctly configured, which is hard to verify manually.

**Solution**: The connector exposes the NP1 redundancy unit's configuration, switching causes, automatic verifications, and live status, so redundancy readiness is always visible in DataMiner.

**Benefit**: Operators can trust their redundancy setup and are alerted whenever the protection chain is compromised.

### Efficient Remote Configuration

**Challenge**: Adjusting modulation, frequency plans, or output settings across many remote transmitters via individual web interfaces is slow and error-prone.

**Solution**: DVB-T/DVB-T2 modulation, network, frequency, and RF output settings are configurable directly from DataMiner element cards, with a direct link to the device web page when needed.

**Benefit**: Faster, centralized, and auditable configuration changes across the whole transmitter network.

## Prerequisites

- **DataMiner 10.4.0.0 or higher** is required to run this connector.
- **SNMP network access** from the DataMiner Agent to the Tredess MultiTX device is needed for polling and configuration.
- **SNMP trap forwarding** must be configured on the device toward the DataMiner Agent to receive real-time event notifications.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Tredess_MultiTX_Technical).
