---
uid: Connector_help_British_Telecom_Encoder_Resource_Manager
---

# British Telecom Encoder Resource Manager

The purpose of this connector is to manage various Elemental Live encoder elements.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No additional configuration of parameters is necessary in a newly created element.

## How to use

The **General** page contains an **Encoders** table that provides an overview of all available Elemental Live encoder elements in the system. By configuring each encoder with details such as Location, Event Name Filter, and Booking Name Format, new rows will be generated in the **Channel Overview** table.

When entering a regular expression in the Event Name Filter filed, the system will utilize the content matched by the first capturing group. The channel name that should be extracted needs to be placed within the parentheses of the first capturing group in a regex pattern.

When entering a format in the Booking Name Format field, placeholder {0} must be used, and it will be replaced with the channel name. Any desired text can be added before or after the placeholder to customize the booking name.

A context menu is available for Encoders table with the Encoder Swap option that enables swapping encoding events from one encoder to the another.

The **Live Events** page contains **Live Events** that provides an overview of all live events from each encoder available in the system.

### Examples

Example of an Event Name Filter configuration:
<ul>
<li>Event Name Filter: [0-9]* - (.\*) - \w*</li>
<li>Live Event Name: 78 - IPsky Nick Toons SD - Main</li>
<li>Result (Channel Name): IPsky Nick Toons SD</li>
</ul>

Example of a Booking Name Format configuration:
<ul>
<li>Booking Name Format: {0}_CH</li>
<li>Channel Name: IPsky Nick Toons SD</li>
<li>Result (SRM Booking CH): IPsky Nick Toons SD_CH</li>
</ul>


