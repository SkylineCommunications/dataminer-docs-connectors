---
uid: Connector_help_Eutelsat_TAOS_Manager
---

# Eutelsat TAOS Manager

## About

The **Eutelsat TAOS Manager** connector retrieves satellite transponder telemetry from Eutelsat's TAOS (Telemetry Acquisition and Operations System) MySQL databases. It polls redundant databases on a configurable schedule, merges results based on validity and recency, and presents consolidated per-transponder telemetry.

An **Association Table** maps each transponder to its TM_IDs, allowing flexible per-transponder configuration. Custom alarm thresholds with major/critical severity offsets provide fine-grained alarm control.

This connector has two separate ranges:

- **1.0.0.x**: Intended for Standard Eutelsat satellites
- **1.0.1.x**: Targets Eutelsat Quantum satellites support. Because of the different equipment types and additional database sources used by Quantum satellites, this range is very different from the 1.0.0.x range. As such, you should not upgrade existing elements that use the 1.0.0.x range to this range.

## Key Features

- **Monitor satellite telemetry**: The connector polls different databases on a configurable schedule and displays consolidated telemetry per transponder.
- **Fine-tune alarm thresholds**: Manually adjust alarm thresholds to match your preferences, or use automatically configured thresholds (in range 1.0.1.x only).

## Configuration

### Connections

This is a **virtual** connector. No connections are configured in the element wizard.

Database connections are configured on the **Setup** page after element creation.

### Initialization

1. Create an element using this connector.
1. On the **Setup** page, enter the **Satellite ID** matching the target satellite in the TAOS database.
1. Configure the database connection parameters (address, port, name, username, password) for each database source.
1. On the **Configuration** page, populate the **Association Table** to map transponders to TM_IDs.

The connector will begin polling automatically on a 20-second cycle.

## How to use

This connector is available in two version ranges depending on the **satellite type**.

> [!IMPORTANT]
> The two ranges are **not interchangeable**. The Association Table schema and telemetry page layout differ between ranges. Select the range that matches your satellite type when creating the element.

### Range 1.0.0.x

Use this range for **standard Eutelsat satellites**.

Telemetry is organized by **parameter type**, such as:

- TWTA / Mute / Mode
- Power
- Gain Step
- Voltage / Current
- Coverage

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Eutelsat_TAOS_Manager_1_0_0_x_Technical).

### Range 1.0.1.x

Use this range for **Eutelsat Quantum satellites**.

Telemetry is organized by **equipment type**, including:

- SCACE
- AIDA
- MPM
- RASE
- IRASE
- DRA
- BFN

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Eutelsat_TAOS_Manager_1_0_1_x_Technical).

## Notes

- The connector uses the **MySql.Data** NuGet package (v9.0.0) for database connectivity.
- The polling timer has a random initial start offset (0–30 s) to prevent multiple elements from querying the database simultaneously.
