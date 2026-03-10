---
uid: Connector_help_Eutelsat_TAOS_Manager_Range_1.0.1.x
---

# Eutelsat TAOS Manager — Range 1.0.1.x

This range targets **Eutelsat Quantum satellites**. It extends the 1.0.0.x architecture by adding **SCC Gateway** database support and reorganizing telemetry pages by **equipment type** instead of parameter type.

> [!NOTE]
> This range was branched from version 1.0.0.27. The Association Table schema and page layout are **not compatible** with range 1.0.0.x due to the different equipment types and additional database sources used by Quantum satellites.

## Element Configuration

### Connections

This is a virtual connector — no connections are configured in the element wizard.

On the **Setup** page, configure four MySQL database connections:

| Database                | Parameters                                                           |
|-------------------------|----------------------------------------------------------------------|
| **CMRS Main**           | Address, Port (default 3306), Database Name, Username, Password      |
| **CMRS Backup**         | Address, Port (default 3306), Database Name, Username, Password      |
| **SCC Gateway Main**    | Address, Port (default 3306), Database Name, Username, Password      |
| **SCC Gateway Backup**  | Address, Port (default 3306), Database Name, Username, Password      |

## How to Use

1. On the **Setup** page, set the **Satellite ID** and database connection details for all four databases.
2. The connector polls the databases periodically.
3. On the **Configuration** page, populate the **Association Table** to map each transponder/beam to its TM_IDs for all equipment-specific parameter types.
4. Transponder data appears on the equipment-type pages.

### Data Merge Logic

The same redundancy logic as range 1.0.0.x applies, extended across four databases. The **Source DB** column indicates the origin: *CMRS Main*, *CMRS Backup*, *SCC Gateway Main*, or *SCC Gateway Backup*.

## Pages

### General Overview

- **Connection Status** for all four database connections.
- **Last Update** timestamps and **Time Since Last Update** for each database.
- Overview table with heartbeat and status parameters.
- **Force Retrieval...** page button.

### Parameter Overview

A **tree control** with a hierarchical view from Satellite to Transponders to all related equipment-specific parameter tables.

### Equipment Pages

Telemetry is organized by equipment type. Each page contains parameter tables specific to that Quantum satellite equipment:

| Page       | Description                                      |
|------------|--------------------------------------------------|
| **SCACE**  | SCACE equipment telemetry parameters             |
| **AIDA**   | AIDA equipment telemetry parameters              |
| **MPM**    | MPM equipment telemetry parameters               |
| **RASE**   | RASE equipment telemetry parameters              |
| **IRASE**  | IRASE equipment telemetry parameters             |
| **DRA**    | DRA equipment telemetry parameters               |
| **BFN**    | BFN equipment telemetry parameters               |

Each equipment page displays tables with: Transponder Name, Station Code, Customer, Value, Update Time, Param Age, Sample Time, Sample Age, and Source DB. Threshold management and severity offset features are available where applicable.

### Satellite Info

Editable table with satellite metadata: Name, Position, Number of Transponders, Launch Date, Contact Person.

### Configuration

- **Sync Alarm Template** button.
- **Show Disabled Transponders** toggle.
- **Import/Export CSV** for the Association Table.
- **Association Table** — Maps each transponder/beam to its TM_IDs for all equipment-specific parameter types. The column schema differs from range 1.0.0.x to accommodate Quantum equipment types.
- **Add/Remove Transponder**.

### Setup

Database connection parameters for all four databases (CMRS Main/Backup and SCC Gateway Main/Backup), plus the Satellite ID.

There is also a Database table at the bottom. You can use a context menu (right click) to add or remove extra databases.
This table is used to check, when a communication fails, if it is possible to retrieve data via another database source.

### Full Load

Raw database contents for all database sources, with Last Update timestamps and Time Since Last Update.

### Force Retrieval (subpage)

Accessible from the General Overview page. Allows restricting database retrieval to a specific source:

| Option                      | Behavior                                                |
|-----------------------------|---------------------------------------------------------|
| **Disable Force Retrieval** | All configured databases are polled (default)           |
| **CMRS Main**               | Only the CMRS Main database is polled                   |
| **CMRS Backup**             | Only the CMRS Backup database is polled                 |
| **SCC Gateway Main**        | Only the SCC Gateway Main database is polled            |
| **SCC Gateway Backup**      | Only the SCC Gateway Backup database is polled          |

An optional **Duration** (in minutes) can be set. When set to 0, the restriction is indefinite.

## Exception Values

Same as range 1.0.0.x:

| Value     | Display               | Meaning                                              |
|-----------|-----------------------|------------------------------------------------------|
| **-9999** | NOT VALID             | Data exists in DB but validity flag is false         |
| **-9998** | NOT PRESENT IN DB     | TM_ID not found in the database                      |
| **-9997** | TRANSPONDER DISABLED  | Transponder is disabled in the Association Table     |

## Notes

- The Quantum satellite architecture uses different equipment types (SCACE, AIDA, RASE, MPM, IRASE, DRA, BFN) compared to the standard GFP parameter types in range 1.0.0.x, which is why a separate range was required.
- The additional SCC Gateway databases provide an extra source of telemetry data specific to the Quantum platform.
