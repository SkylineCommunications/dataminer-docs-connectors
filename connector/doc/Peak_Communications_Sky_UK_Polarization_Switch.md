---
uid: Connector_help_Peak_Communications_Sky_UK_Polarization_Switch
---

# Peak Communications Sky UK Polarization Switch

The Peak Communications Sky UK Polarization Switch is a custom connector that can be used to display and configure information of the Peak Communications switches.

A serial connection is used in order to retrieve and configure the information of the device.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | Unknown            |

## Configuration

### Connections

#### Serial connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device. The connector uses this to create commands.

> [!NOTE]
> The default value for *Timeout of a single command* is set to 2000 ms and the default value for *Number of retries* is set to 1.

## How to use

The **General** page displays general data retrieved from the "Get Monitor Switches" Command. It shows the positions per switch and also allows you to change the switch position.

On the **Switch Labels** page, you can configure labels for all retrieved switches and positions.

## Notes

The default value for *Timeout of a single command* is set to 2000 ms and the default value for *Number of retries* is set to 1. This setup is required because the device needs time to process sets.
