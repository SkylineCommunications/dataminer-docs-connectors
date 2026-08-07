---
uid: Connector_help_Sencore_SMD989
---

# Sencore SMD989

The **SMD-989** is a versatile DVB-S/S2/S2X/TurboPSK modulator platform capable of one or two channels of modulation per rack unit. The **SMD-989** comes standard with IP and ASI inputs to offer flexibility for future changes in network architecture or sourcing content from two different interfaces. The SMD also supports advanced DVB-S2 features such as 16APSK and 32APSK modulation as well as the carriage of multiple streams on a single RF carrier. It also supports the advanced modulator coding scheme turbo PSK and S2X.

## About

This **SNMP** connector is used to monitor and configure the **Sencore SMD-989** modulator.

## Key Features

- **System monitoring**: Monitor the reference clock, mute behavior, network settings, cloning settings, and bay licenses.
- **Input management**: Monitor and configure primary/backup input sources, failover conditions, and IP input settings.
- **Modulation control**: Configure modulation mode, symbol rate, spectral inversion, carrier ID, PRBS, and TS analysis.
- **Output control**: Configure the IF output frequency, level, tilt, and mute mode.
- **Web interface access**: Access the device's native web interface directly from the element.

## Use Cases

### Keep a Satellite Carrier On Air During an Input Feed Failure

**Challenge**: Operators need the modulator to keep transmitting without interruption if the primary contribution feed is lost.

**Solution**: Use the SMD-989 connector to configure a primary and backup input source with automatic failover and restore conditions.

**Benefit**: Reduces service outages and manual intervention by letting the modulator switch to the backup feed automatically.

### Monitor Modulator Health from DataMiner

**Challenge**: Operators need visibility into the modulator's reference clock, output level, and TS analysis errors without accessing the device directly.

**Solution**: Use the SMD-989 connector's System, Modulator, and Output pages to monitor clock status, IF output parameters, and transport stream error thresholds.

**Benefit**: Enables proactive detection of degraded carriers and hardware issues from a single monitoring platform.

### Provision Multiple Bays Quickly

**Challenge**: Configuring modulation and output settings on each new SMD-989 bay individually is time-consuming.

**Solution**: Use the SMD-989 connector's Clone Settings to copy the configuration of a reference unit to other bays.

**Benefit**: Speeds up deployment and ensures consistent configuration across the fleet.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Sencore_SMD989_Technical).
