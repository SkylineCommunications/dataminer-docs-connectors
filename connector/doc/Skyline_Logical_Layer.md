---
uid: Connector_help_Skyline_Logical_Layer
---

# Skyline Logical Layer

With this connector, you can subscribe on parameter values, parameter alarms, element alarms, and view alarms in DataMiner.

These values are updated in real time, and you can define conditions that will be evaluated as soon as a change happens. The result of these can then be reused in DataMiner.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | N/A                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

To use this connector, you will need to install the Skyline Logical Layer package. This package contains the connector and an Automation script.
The script is used to fill in data in the tables of the element. It is an interactive script that helps you select and populate the tables.

The first thing you will need to do in the script is define Parameter Value, Element Alarm, or View Alarm Monitors. After that, you will need to define conditions.

Once you have set up the element as detailed above, it will show the following information:

- The **Conditions** page displays a table with the defined conditions and the result and settings.
- The **Monitors** page displays three tables, for the Parameter Value, Element Alarm, and View Alarm Monitors.

The connector supports importing CSV files that are exported with the build in export table function in DataMiner.
For the Parameter Value Monitors table, the export file has to contains the hidden columns as well.

### Condition Syntax

Every comparison has to be started and closed with `< >`.

Example: `<Number==5>`

The following operators can be used for comparisons:

- `=`
- `!`
- `<`
- `>`

You can also use the following combinations:

- `==`
- `!=`
- `<=`
- `>=`

You can also start with an exclamation mark to inverse the used condition: `<!ConditionName>`

Combining multiple comparisons is possible with the keywords `and`, `or`, and `not` (`not` will be translated to `and not`).

Examples:

- `<Number==5>and<String==Test>`

- `<Number==5>not<ConditionName>`

  This can also be written like this: `<Number==5>and<!ConditionName>`

- `<String==Test>or<Discreet==Disconnected>`

Any of the monitors can be used in a condition.

Conditions can be reused inside other conditions.

To make use of the static variables, prefix the name with `@`: `<Number==@StaticNumber>`

Brackets are also supported

Example:

- `(<Condition1> or <Condition2>) and <Condition3>`
