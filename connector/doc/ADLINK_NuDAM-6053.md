---
uid: Connector_help_ADLINK_NuDAM-6053
---

# ADLINK NuDAM-6053

## About

ADLINK NuDAM provides a series of digital input or output (DIO) modules to sense the digital signal or to control the remote devices. The NuDAM-6053 provides 16 digital input channels for dry contact or wet contact signals.

With this connector, you can monitor a device connected to an ADLINK NuDAM-6053 through its serial interface. Each polling cycle reads all 16 digital input channels at once. You define which input states constitute an alarm condition by configuring rows in the Digital Inputs table.

## Key Features

- **Input monitoring**: Monitor the 16 digital inputs of the NuDAM-6053 to get notified of any issues with the connected device.

- **Configurable alarm conditions**: Each row in the Digital Inputs table defines an independent alarm condition. You choose which input channels matter and whether an alarm should be triggered for them.

- **Flexible bit masking**: Set input channels that are irrelevant to a condition to be ignored, so only the bits you care about are evaluated.

## Use Cases

### Amplifier Monitoring

**Challenge**: DEV 2185 L-band distribution amplifiers provide alarm indication via LED and via dry contacts only.

**Solution**: The contacts of the DEV 2185 can be connected to the digital inputs of the ADLINK NuDAM-6053. With this connector, these contacts can be read and compared with predefined bit patterns configured in the Digital Inputs table.

**Benefit**: The Digital Inputs table contains the bit patterns for which a DataMiner alarm has to be generated. If the received digital input state matches the defined pattern, the alarm is generated.

![Digital Inputs table on the General page of an ADLINK NuDAM-6053 element](~/connector/images/AdlinkNudam6053DigitalInputs.png)

## Technical Reference

### Prerequisites

- **DataMiner 10.4** or higher.

- **Address ID**: When you configure the element, enter the module's address ID in the **Bus address** field. This 2-character hexadecimal value must be in the range of 00 - FF.

### Configuration

When you configure the DataMiner element using this connector, make sure **at least one row** is added in the **Digital Inputs table**. The connector will only start polling the device when at least one row has been added.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ADLINK_NuDAM-6053_Technical).
