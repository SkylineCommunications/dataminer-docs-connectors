---
uid: Connector_help_ADLINK_NuDAM-6053
---

# ADLINK NuDAM-6053

## About

The purpose of this connector is to monitor a ADLINK NuDAM-6053 device through its serial interface.

ADLINK NuDAM provides a series of digital input or output (DIO) modules to sense the digital signal or to control the remote devices. The NuDAM-6053 provides 16 digital input channels for dry contact or wet contact signals.

## Key Features

- **Amplifier Monitoring**: The Amplifier State parameter indicates if the build-in amplifier is fine or not.

## Use Cases

### Power Supply Monitoring

**Challenge**: The device doesn't immediately indicate if the primary or the secondary power supply is in trouble.

**Solution**: The Primary/Secondary Power Supply State parameters, available in the DataMiner element, show if one of them has an alarm.

**Benefit**: DataMiner will notify you if a power supply is struggling.

## Technical Reference

### Prerequisites

- **DataMiner Main Release 10.4** or higher.

- **Address ID**: The module's address ID has to be entered in the element configuration wizards **Bus address** field. This 2-character hexadecimal value must be in the range of 00 - FF.