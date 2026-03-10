---
uid: Connector_help_Eutelsat_TAOS_Manager_Range_1.0.0.x
---

# Eutelsat TAOS Manager — Range 1.0.0.x

This range targets **standard Eutelsat satellites**. It polls two redundant CMRS MySQL databases, merges the results, and presents consolidated transponder telemetry organized by **parameter type**.

## Element Configuration

### Connections

This is a virtual connector — no connections are configured in the element wizard.

On the **Setup** page, configure two MySQL database connections:

| Database        | Parameters                                                          |
|-----------------|---------------------------------------------------------------------|
| **CMRS Main**   | Address, Port (default 3306), Database Name, Username, Password     |
| **CMRS Backup** | Address, Port (default 3306), Database Name, Username, Password     |

## How to Use

1. On the **Setup** page, set the **Satellite ID** and database connection details for both Main and Backup databases.
2. The connector polls the databases every **20 seconds** (with a random initial offset of 0–30 s).
3. On the **Configuration** page, populate the **Association Table** to map each transponder to its TM_IDs for all 14 parameter types.
4. Transponder data appears on the parameter pages, grouped by category.

### Data Merge Logic

For each parameter, Main and Backup database results are compared:

- If both return valid data → the **most recent** value (by `Update_Time`) is used.
- If only one has valid data → that value is used.
- If neither has valid data → the most recent invalid value is shown.
- The **Source DB** column on every table indicates which database supplied the displayed value.

## Pages

### General Overview

- **General Overview table** — Displays SCC Heartbeat and SCC TM Status parameters from the merged result (columns: TM_ID, Update_Time, Description, Units, Type, Value, Validity, Sample_Time, Spare 1–3).
- **Connection Status MAIN / BACKUP** — Discreet status: *OK* or *CONNECTION FAILED*. Shows *Disabled (Force Retrieval)* when force retrieval excludes that database.
- **Main/Backup DB Last Update** — Timestamp of the last successful poll for each database.
- **Main/Backup DB Time Since Last Update** — Elapsed seconds since each database was last polled.
- **Force Retrieval...** — Page button opening the Force Retrieval subpage.

### Parameter Overview

A **tree control** providing a hierarchical view:

**Satellite** → **Transponders** → 14 parameter tables (TWTA Status, Mute Status, Mode, ALC Input Power, FGM Output Power, Gain Step FGM, Gain Step ALC, Gain Step Ageing/Tuning, Gain Step FGM/ALC, Anode Voltage, Helix Current, Bus Current, Uplink Coverage, Downlink Coverage).

### Params TWTA/Mute/Mode

Three tables with discreet status values:

| Table              | Accepted Raw Values                                   | Discreets          |
|--------------------|-------------------------------------------------------|--------------------|
| **TWTA Status**    | ON, OFF, HV_ON                                        | 1 = ON, 0 = OFF    |
| **Mute Status**    | ON, OFF, MUTE, RF_ON, MUTE_ON, MUTE_OFF               | 1 = ON, 0 = OFF    |
| **Mode (FGM/ALC)** | FGM, ALC, FG_MODE, ALC_MODE                           | 0 = FGM, 1 = ALC   |

Each table includes: Transponder Name, Station Code, Customer, Status/Value, Update Time, Param Age, Sample Time, Sample Age, and Source DB.

### Params Power

Two tables with **threshold-based alarming** and **deviation tracking**:

- **ALC Input Power** (dBm) — Min/Max Threshold, Nominal Value, Deviation (dB), Deviation Alarm State (Normal/Major/Critical), Alarm State (Enabled/Disabled). Linked to Mode (FGM/ALC) table via foreign key.
- **FGM Output Power** (dBm) — Same threshold and deviation features.

Each table has a **Severity Offset** subpage (page button) where Major and Critical offsets can be configured. Default offsets: Major = 3, Critical = 6.

### Params Gain Step

Four tables, each with Min/Max Threshold and Alarm State columns:

- **Gain Step FGM (FCA Level)** — Unit: step
- **Gain Step ALC (GCA Level)** — Unit: step
- **Gain Step Ageing/Tuning (SCA Level)** — Unit: step
- **Gain Step (FGM/ALC)** — Unitless

Each table has a corresponding **Severity Offset** subpage.

### Params Voltage and Currents

Three tables, each with Min/Max Threshold and Alarm State columns:

- **Anode Voltage** — Unit: V
- **Helix Current** — Unit: mA
- **Bus Current** — Unit: A

Each table has a corresponding **Severity Offset** subpage.

### Params Coverage

Two tables with string-based coverage values:

- **Uplink Coverage**
- **Downlink Coverage**

These tables do not have threshold or severity offset features.

### Satellite Info

Editable table with satellite metadata: Name, Position, Number of Transponders, Launch Date, Contact Person.

### Configuration

- **Sync Alarm Template** button — Manually synchronizes the alarm template with current transponder display keys.
- **Show Disabled Transponders** toggle — Controls whether disabled transponders appear in parameter tables.
- **Import/Export CSV** — Import or export the Association Table via CSV files. Use *Refresh List* to update the file dropdown.
- **Association Table** — 19-column table mapping each transponder to its TM_IDs for all 14 parameter types, plus Transponder ID, Transponder Name, Station Code, Customer, and Enabled status.
- **Add/Remove Transponder** — Add or remove rows by entering a Transponder ID.

### Setup

Database connection parameters for Main and Backup CMRS databases, plus the Satellite ID.

### Full Load

Raw unprocessed database contents:

- **Full Load Main** table — All rows from the Main database for the configured satellite (columns: TM_ID, Update_Time, Description, Units, Type, Value, Validity, Sample_Time, Spare 1–5).
- **Full Load Backup** table — Same structure from the Backup database.
- **Last Update** timestamps and **Time Since Last Update** for each database.
- **Refresh All** button — Manually triggers a full database reload.

### Force Retrieval (subpage)

Accessible via a page button on the General Overview page. Restricts database polling to a single source:

| Option                      | Behavior                                              |
|-----------------------------|-------------------------------------------------------|
| **Disable Force Retrieval** | Both Main and Backup databases are polled (default)   |
| **Main**                    | Only the Main database is polled                      |
| **Backup**                  | Only the Backup database is polled                    |

- **Duration** (minutes) — When set to 0, the restriction is indefinite (max: 525600 minutes / 1 year).
- **Apply** button — Activates the selected force retrieval configuration.
- **Force Retrieval Status** — Displays the current active configuration.

## Exception Values

The following exception values are used across all parameter tables:

| Value     | Display               | Meaning                                              |
|-----------|-----------------------|------------------------------------------------------|
| **-9999** | NOT VALID             | Data exists in DB but validity flag is false         |
| **-9998** | NOT PRESENT IN DB     | TM_ID not found in the database                      |
| **-9997** | TRANSPONDER DISABLED  | Transponder is disabled in the Association Table     |

## Notes

- Alarm templates are auto-synced when a Transponder Name (display key) changes in the Association Table.
- The ALC Input Power table has a foreign key relation to the Mode (FGM/ALC) table, enabling alarm correlation based on the current operating mode.
- Station Code and Customer are included as alarm properties on monitored parameters.
