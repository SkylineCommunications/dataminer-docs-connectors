---
uid: Connector_help_Skyline_Logical_Layer
---

# Skyline Logical Layer

This connector give you the ability to subscribe on Parameter Values, Parameter Alarms, Element Alarms and View Alarms.
With these values being updated in real time you can define conditions that will be evaluated on change and gives you a result that can be reused in DataMiner.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Feature1</li><li>Feature2</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |No firmware         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Indicate if additional configuration of parameters is necessary in a newly created element.

## How to use

To be able to use this driver you will have to install the Skyline Logical Layer package.
This package contains the connector and automation script.
The AS is being used to be able to fill the tables with data, it's an interactive script that helps you select and populate the tables.

The first that should be done is defining Parameter Value, Element Alarm or View Alarm Monitors.
Next is defining conditions, this can be done in the automation script as well.

### Examples

The **Conditions** page has 1 table with the defined conditions and the result and settings.

The **Monitors** page has 3 tables for the Parameter Value, Element Alarm and the View Alarm Monitors.
