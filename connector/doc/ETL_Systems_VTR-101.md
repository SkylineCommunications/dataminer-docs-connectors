---
uid: Connector_help_ETL_Systems_VTR-101
---

# ETL Systems VTR-101

## About

This connector is used to monitor and control the ETL Systems VTR-101, an L-band routing matrix. It allows you to route any input to any output, to label and lock the inputs and outputs, and to configure the gain of each matrix module.

## Key Features

- **Matrix routing**: Connect any input to any output from an interactive matrix display, with one input per output.
- **Labeling and locking**: Assign labels to inputs and outputs and lock them so that their connections can no longer be modified.
- **Gain configuration**: Configure the gain of each matrix module directly from the element.

## Use Cases

### Centralized Signal Routing

**Challenge**: Operators need to reroute L-band signals quickly without logging in to the device itself.

**Solution**: Use the matrix display to set crosspoints directly from DataMiner, with labels that make each input and output immediately recognizable.

### Preventing Accidental Routing Changes

**Challenge**: Critical feeds must not be disconnected by mistake.

**Solution**: Lock the relevant inputs and outputs so that their crosspoints can no longer be modified.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.0 (build 14003) or higher** is required.
- SNMP must be enabled on the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ETL_Systems_VTR-101_Technical).
