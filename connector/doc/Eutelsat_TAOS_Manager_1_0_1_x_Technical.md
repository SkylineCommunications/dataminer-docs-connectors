---
uid: Connector_help_Eutelsat_TAOS_Manager_1_0_1_x_Technical
---

# Eutelsat TAOS Manager — Range 1.0.1.x

## About

This range targets **Eutelsat Quantum satellites**. It extends the 1.0.0.x architecture by adding **SCC Gateway** database support and reorganizing telemetry pages by **equipment type** instead of parameter type.

> [!NOTE]
> This range was branched from version 1.0.0.27. The Association Table schema and page layout are **not compatible** with range 1.0.0.x because of the different equipment types and additional database sources used by Quantum satellites.

## Element Configuration

### Connections

This is a virtual connector. No connections need to be configured during element creation.

### Initialization

1. On the **Setup** page, set the **Satellite ID** and database connection details for all four databases.

   | Database            | Parameters                                                           |
   |---------------------|----------------------------------------------------------------------|
   | CMRS Main           | Address, Port (default 3306), Database Name, Username, Password      |
   | CMRS Backup         | Address, Port (default 3306), Database Name, Username, Password      |
   | SCC Gateway Main    | Address, Port (default 3306), Database Name, Username, Password      |
   | SCC Gateway Backup  | Address, Port (default 3306), Database Name, Username, Password      |

   The connector will poll the databases periodically.

1. On the **Configuration** page, populate the **Association Table** to map each transponder/beam to its TM_IDs for all equipment-specific parameter types.

   Transponder data will be shown on the equipment type pages.

## Data Merge Logic

The same redundancy logic as [for range 1.0.0.x](xref:Connector_help_Eutelsat_TAOS_Manager_1_0_0_x_Technical#data-merge-logic) applies, but extended across four databases. The **Source DB** column indicates the origin: *CMRS Main*, *CMRS Backup*, *SCC Gateway Main*, or *SCC Gateway Backup*.

## Pages

### General Overview

These are the main features of this page:

- **Connection Status** for all four database connections.
- **Last Update** timestamps and **Time Since Last Update** for each database.
- Overview table with heartbeat and status parameters.
- **Force Retrieval** page button.

### Force Retrieval (Subpage)

Accessible from the General Overview page. Allows restricting database retrieval to a specific source:

| Option                  | Behavior                                                |
|-------------------------|---------------------------------------------------------|
| Disable Force Retrieval | All configured databases are polled (default)           |
| CMRS Main               | Only the CMRS Main database is polled                   |
| CMRS Backup             | Only the CMRS Backup database is polled                 |
| SCC Gateway Main        | Only the SCC Gateway Main database is polled            |
| SCC Gateway Backup      | Only the SCC Gateway Backup database is polled          |

An optional **Duration** (in minutes) can be set. If this is set to 0, the restriction is indefinite.

### Parameter Overview

This page contains a **tree control** with a hierarchical view from satellite to transponders to all related equipment-specific parameter tables.

### Equipment Pages

Telemetry is organized by equipment type. Each page contains parameter tables specific to that Quantum satellite equipment:

| Page   | Description                                      |
|--------|--------------------------------------------------|
| SCACE  | SCACE equipment telemetry parameters             |
| AIDA   | AIDA equipment telemetry parameters              |
| MPM    | MPM equipment telemetry parameters               |
| RASE   | RASE equipment telemetry parameters              |
| IRASE  | IRASE equipment telemetry parameters             |
| DRA    | DRA equipment telemetry parameters               |
| BFN    | BFN equipment telemetry parameters               |

Each equipment page displays tables with the Transponder Name, Station Code, Customer, Value, Update Time, Param Age, Sample Time, Sample Age, and Source DB. Threshold management and severity offset features are available where applicable.

### Satellite Info

This page contains a table where you can view and configure satellite metadata: Name, Position, Number of Transponders, Launch Date, and Contact Person.

### Configuration

These are the main features of this page:

- **Sync Alarm Template** button.
- **Show Disabled Transponders** toggle button.
- **Import/Export CSV** option for the Association Table.
- **Association Table**: Maps each transponder/beam to its TM_IDs for all equipment-specific parameter types. The column schema differs from range 1.0.0.x to accommodate Quantum equipment types.
- **Add/Remove Transponder** buttons.

### Setup

On this page, you can configure the database connection parameters for all four databases (CMRS Main/Backup and SCC Gateway Main/Backup), plus the Satellite ID.

There is also a Database table at the bottom. When communication fails, this table is used to check if it is possible to retrieve data via another database source. Right-clicking the table opens a context menu that allows you to add or remove databases.

### Full Load

This page displays the raw database contents for all database sources, with Last Update timestamps and the Time Since Last Update.

## Dynamic Threshold Feature

The connector implements a **dynamic threshold** system for all numeric parameter tables (e.g., Derived Input/Output Power TM, ALC Settings, FGM Settings, etc.). This feature enables both automatic and manual alarm threshold management per unit.

### Threshold Mode

Each row in a numeric parameter table has a **Threshold Mode** setting:

| Mode   | Behavior                                                                                                               |
|--------|------------------------------------------------------------------------------------------------------------------------|
| Auto   | Threshold values (Hard Min, Soft Min, Nominal, Soft Max, Hard Max) are automatically synchronized from the database on every polling cycle. If a database value changes, the connector detects the change and triggers an alarm template update.             |
| Manual | Threshold values are user-defined and **not** overwritten by database updates. The operator has full control over the Hard Min, Soft Min, Nominal Value, Soft Max, and Hard Max thresholds. Write controls for these fields are disabled when the mode is set to Auto.      |

New rows default to **Auto** mode with **Alarm State** set to **Enabled**.

### Alarm State

Each row has an **Alarm State** toggle option:

- **Enabled**: The row participates in alarm monitoring.
- **Disabled**: Alarm monitoring is suppressed for that row.

### Severity Offset

Each numeric parameter category provides configurable **Major** and **Critical Severity Offset** values (accessible via page buttons on the subpages). These offsets control how far a measured value must deviate from its nominal value before triggering major or critical alarms. Default values are 3 (Major) and 6 (Critical).

### Deviation Tracking

Each numeric parameter row calculates a **Deviation** from the nominal value, along with a **Deviation Alarm Property** and **Deviation Alarm State** (Normal, Major, or Critical), which are included as alarm properties for correlation purposes.

## Exception Values

Like in range 1.0.0.x, the following exception values are used across all parameter tables:

| Value | Display               | Meaning                                              |
|-------|-----------------------|------------------------------------------------------|
| -9999 | NOT VALID             | Data exists in DB but validity flag is false         |
| -9998 | NOT PRESENT IN DB     | TM_ID not found in the database                      |
| -9997 | TRANSPONDER DISABLED  | Transponder is disabled in the Association Table     |

## Notes

- The Quantum satellite architecture uses different equipment types (SCACE, AIDA, RASE, MPM, IRASE, DRA, BFN) compared to the standard GFP parameter types in range 1.0.0.x, which is why a separate range is required.
- The additional SCC Gateway databases provide an extra source of telemetry data specific to the Quantum platform.
