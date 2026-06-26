---
uid: Connector_help_ADLINK_NuDAM-6053
---

# ADLINK NuDAM-6053

## About

ADLINK NuDAM provides a series of digital input or output (DIO) modules to sense the digital signal or to control the remote devices. The NuDAM-6053 provides 16 digital input channels for dry contact or wet contact signals.

With this connector, you can monitor a device connected to an ADLINK NuDAM-6053 through its serial interface.

## Key Features

- **Input monitoring**: Monitor the digital inputs to get notified of any issues with the connected device.

## Use Cases

### Amplifier Monitoring

**Challenge**: DEV 2185 L-band distribution amplifiers provide alarm indication via LED and via dry contacts only.

**Solution**: The contacts of the DEV 2185 can be connected to the digital inputs of the ADLINK NuDAM-6053. With this connector, these contacts can be read and compared with predefined byte sequences.

**Benefit**: The Digital Inputs table contains the byte sequences for which a DataMiner alarm has to be generated. If the received bytes match the defined bytes, the alarm is generated.

![Digital Inputs table on the General page of an ADLINK NuDAM-6053 element](~/connector/images/AdlinkNudam6053DigitalInputs.png)

## Technical Reference

### Prerequisites

- **DataMiner 10.4** or higher.

- **Address ID**: When you configure the element, enter the module's address ID in the **Bus address** field. This 2-character hexadecimal value must be in the range of 00 - FF.
