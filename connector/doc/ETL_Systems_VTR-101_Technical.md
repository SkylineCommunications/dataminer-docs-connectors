---
uid: Connector_help_ETL_Systems_VTR-101_Technical
---

# ETL Systems VTR-101

## About

The ETL Systems VTR-101 is an L-band routing matrix. This connector allows you to route the inputs of the device to its outputs, to label and lock those inputs and outputs, and to configure the gain of each matrix module.

**Alarm monitoring** and **trending** can be enabled for parameters in the connector.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

### General Page

This page contains the **Router Control Inputs** and **Router Control Outputs** tables, which hold the routing configuration of the device.

The **Router Control Inputs** table contains the following columns:

- **Number**: The index of the input.
- **Label**: The label of the input.
- **Lock State**: Indicates whether the input is locked.

The **Router Control Outputs** table contains the same columns, extended with a **Connected Input** column, which indicates the input that is currently connected to the output.

The **Label** and **Lock State** columns of both tables, and the **Connected Input** column of the outputs table, can be edited directly in the table. Note that an output can only be connected to one input at a time.

### Matrix Page

This page displays the matrix containing the connections present on the device.

The matrix interface allows you to do the following actions:

- Set a new connection, by clicking the desired crosspoint. Note that setting a new connection disconnects the connection that was previously active on that output.
- Lock an input or output, so that its connections can no longer be modified from the matrix.

### Config Page

This page contains the **Vtr 101 Gain Settings** table, which allows you to configure the gain of each matrix module. Every row contains the gain values **Vtr 101 Gain 1** to **Vtr 101 Gain 16** for the corresponding module. When a gain value is changed, it is written to the device and the affected tables are refreshed automatically.

## Notes

- The routing, locking and gain information is polled every 10 seconds. The input and output alias information is polled every 15 minutes.
