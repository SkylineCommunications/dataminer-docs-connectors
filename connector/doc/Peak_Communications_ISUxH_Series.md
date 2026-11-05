---
uid: Connector_help_Peak_Communications_ISUxH_Series
---

# Peak Communications ISUxH Series

The ISUxH series of IF/L-Band and SHF switching units from Peak Communications are designed to provide high-quality signal switching, primarily for satellite earth station signal selection (monitoring) and signal distribution applications.

This connector uses a serial connection to communicate with the device, so that users can check general information about the unit and also set the switch position in DataMiner.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 5.24            |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device. The connector uses this to create commands.

## How to use

The **General** page displays general information about the unit. With the **Set Switch Position** option, you can set the switch position.

The unit type depends on where "01" is located in the unit name. "ISUSH2101" indicates an input type, while "ISUSH0121" indicates an output type. Depending on the type, the opposite type will be disabled for the Set Switch Position option.

On the **Switch Labels** page, you can configure labels for all positions related to the used switch unit.
