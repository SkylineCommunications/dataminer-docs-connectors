---
uid: Connector_help_ADLINK_NuDAM-6053
---

# ADLINK NuDAM-6053

## About

ADLINK NuDAM provides a series of digital input or output (DIO) modules to sense the digital signal or to control the remote devices. The NuDAM-6053 provides 16 digital input channels for dry contact or wet contact signals.

With this connector, you can monitor an ADLINK NuDAM-6053 device through its serial interface.

## Key Features

- **Amplifier monitoring**: Monitor the Amplifier State parameter to get notified of any issues with the built-in amplifier.

## Use Cases

### Power Supply Monitoring

**Challenge**: The device does not immediately indicate if the primary or the secondary power supply is in trouble.

**Solution**: The Primary/Secondary Power Supply State parameters, available in the DataMiner element, instantly signal issues with the power supply.

**Benefit**: Get instant notifications in case a power supply is struggling.

## Technical Reference

### Prerequisites

- **DataMiner 10.4** or higher.

- **Address ID**: When you configure the element, enter the module's address ID in the **Bus address** field. This 2-character hexadecimal value must be in the range of 00 - FF.
