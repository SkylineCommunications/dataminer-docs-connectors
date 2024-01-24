---
uid: Connector_help_British_Telecom_Encoder_Resource_Manager
---

# British Telecom Encoder Resource Manager

The purpose of this connector is to manage various Elemental Live encoder elements.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No additional configuration of parameters is necessary in a newly created element.

## How to use

On the **General** page, the **Encoders** table provides an overview of all available Elemental Live encoder elements in the system. When you configure each encoder with details such as Location, Event Name Filter, and Booking Name Format, new rows will be generated in the **Channel Overview** table.

When a regular expression is entered in the **Event Name Filter** field, the system will utilize the content matched by the first capturing group. The channel name that should be extracted needs to be placed within the parentheses of the first capturing group in a regex pattern.

When a format is entered in the **Booking Name Format** field, placeholder {0} must be used, and it will be replaced with the channel name. You can add any desired text before or after the placeholder to customize the booking name.

When you right-click the Encoders table, the **Encoder Swap** option is available in the context menu. This enables swapping encoding events from one encoder to another.

The **Live Events** page provides an overview of all live events from each encoder available in the system.

### Examples

Example of an Event Name Filter configuration:

- Event Name Filter: `[0-9]* - (.\*) - \w*`
- Live Event Name: `78 - IPsky Nick Toons SD - Main`
- Result (Channel Name): `IPsky Nick Toons SD`

Example of a Booking Name Format configuration:

- Booking Name Format: `{0}_CH`
- Channel Name: `IPsky Nick Toons SD`
- Result (SRM Booking CH): `IPsky Nick Toons SD_CH`
