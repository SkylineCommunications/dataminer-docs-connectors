---
uid: Connector_help_Peak_Communications_ISUxH_Series
---

# Peak Communications ISUxH Series

ISUxH series of IF/ L-Band & SHF switching units from Peak Communications are designed to provide high quality signal switching, primarily for satellite earth station signal selection (monitoring) and signal distribution applications.

A serial connection is used in order to retrieve and configure the information of the device.

## About

This driver use serial connection to communicate with device. User can check all general information about unit but also perform sets to selected switch position.

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | Unknown            |

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
  - **Bus address**: The bus address of the device. The connector uses this to create commands. (Decimal value range: 32 to 57.)

## How to use

The **General** page displays general infomation about unit and "Set Switch Position" option where user can perform switch position sets.

Unit type depends on where "01" is located in the unit name. If we have the case "ISUSH2101" it means that it is an input type, if the name is "ISUSH0121" then it is an output type. Depending on which type we have, we will also have a disabled opposite type for the set switch position.

On the **Switch Labels** page, you can configure labels for all positions related to used switch unit.
