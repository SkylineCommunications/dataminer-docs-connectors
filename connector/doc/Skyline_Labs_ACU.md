---
uid: Connector_help_Skyline_Labs_ACU
---
# Skyline Labs ACU

The **Skyline Labs ACU** connector simulates an antenna control unit and exposes the current pointing state in DataMiner.
It is intended for demo and test scenarios where a virtual ACU is needed instead of a physical device.

## What It Monitors

- **Current Position**: the selected target name.
- **Azimuth**, **Elevation**, and **Polarization**: the current pointing values for the selected target.
- **Azimuth State** and **Elevation State**: the simulated axis status.
- **Target Table**: the available targets that can be selected from the **Current Position** parameter.

## Key Capabilities

- Preloaded target list for quick startup.
- Editable target coordinates for simulation workflows.
- Dynamic selection of the current target from the target table.
- Virtual connection model with no external device dependency.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Labs_ACU_Technical).