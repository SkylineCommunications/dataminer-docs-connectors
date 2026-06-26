---
uid: Connector_help_Skyline_Labs_ACU_Technical
---
# Skyline Labs ACU - Technical

## About

The **Skyline Labs ACU** connector provides a virtual antenna control unit simulation.
It lets you monitor a selected target and associated pointing values while maintaining a configurable target table for test scenarios.

## Configuration

### Connection

This connector uses a **Virtual Connection** and does not require IP, port, or bus address settings during element creation.

### Initialization

On startup, the connector loads a default set of targets into the **Target** table and sets the current position to the first target.
The **Current Position Selector Source** parameter is populated from the available target names and is used as the source for the selection dropdown.

## How to Use

### General Page

The **General** page shows the current simulation state at a glance:

- **Current Position**: the active target name.
- **Azimuth**, **Elevation**, and **Polarization**: the current pointing values for the selected target.
- **Azimuth State** and **Elevation State**: the active axis state indicators.

### Position Page

The **Position** page is used to manage the target list and update the simulated pointing values.

- Use the **Current Position** selector to switch between available targets.
- Edit the target table to change coordinates or add new simulation targets.
- Use the table context menu to add, duplicate, edit, or delete target rows.
- The selected target drives the displayed azimuth, elevation, and polarization values.

### Target Table

The **Target** table contains the simulation presets used by the connector.
Each row defines a target name together with longitude, azimuth, polarization, and elevation values.
The table is intended to support quick switching between known simulation positions.

## Notes

- This connector is designed as a simulation driver and does not communicate with physical hardware.
- The axis state parameters use a simple **OK/Fault** discreet model for testing and demo purposes.
