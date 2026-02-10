---
uid: Connector_help_Skyline_Mode_Configuration_Manager_Technical
---

# Skyline Mode Configuration Manager

## About

The Skyline Mode Configuration Manager is a generic DataMiner connector designed to centrally manage and expose mode-related configuration data. It provides read-only visibility into the current operational mode and the last mode change, together with a configurable table that allows users to define mode-specific properties for alarming and trending.

This connector is intended to act as a shared configuration and reference element that can be consumed by other applications, automation scripts, or dashboards.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

The connector exposes two standalone read-only parameters:

- **Current Mode**: Displays the currently active mode.

- **Last Mode Changed**: Displays the timestamp or value associated with the last mode change.

In addition, the connector includes a **Mode Configuration** table with the following columns:

- **Instance**: Unique identifier for the mode configuration entry.

- **Label** (read/write): User-defined label describing the mode.

- **Alarm Property** (read/write): Property used to define alarm behavior for the mode.

- **Trend Property** (read/write): Property used to define trending behavior for the mode.

- **Delete**: Action column used to remove a row from the table.

### Table Management

The table fully supports row management directly from the UI:

- Users can **add new rows** using the **Add Row** button below the table.
- Users can **delete existing rows** using the **Delete** button embedded within each table row.
- Users can **edit** the **Label**, **Alarm Property**, and **Trend Property** fields inline.

All changes are applied immediately and stored within the element.

## Notes

This connector is intended to be lightweight and generic, focusing solely on mode configuration management. It does not perform any active control logic and is designed to be safely used as a shared configuration reference across multiple solutions.
