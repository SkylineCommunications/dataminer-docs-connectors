---
uid: Connector_help_Eutelsat_TAOS_Manager_1_0_0_x_Technical
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
1. The connector polls the databases every **20 seconds** (with a random initial offset of 0–30 s).
1. On the **Configuration** page, populate the **Association Table** to map each transponder to its TM_IDs for all 14 parameter types.
1. Transponder data appears on the parameter pages, grouped by category.

### Data Merge Logic

For each parameter, Main and Backup database results are compared:

- If both return valid data → the **most recent** value (by `Update_Time`) is used.
- If only one has valid data → that value is used.
- If neither has valid data → the most recent invalid value is shown.
- The **Source DB** column on every table indicates which database supplied the displayed value.

## Pages

### General Overview

These are the main features of this page:

- **General Overview table**: Displays SCC Heartbeat and SCC TM Status parameters from the merged result (columns: TM_ID, Update_Time, Description, Units, Type, Value, Validity, Sample_Time, Spare 1–3).
- **Connection Status MAIN / BACKUP**: Status can be *OK* or *CONNECTION FAILED*. Shows *Disabled (Force Retrieval)* when force retrieval excludes that database.
- **Main/Backup DB Last Update**: Timestamp of the last successful poll for each database.
- **Main/Backup DB Time Since Last Update**: Elapsed seconds since each database was last polled.
- **Force Retrieval**: Page button opening the Force Retrieval subpage.

### Force Retrieval (Subpage)

Accessible via a page button on the General Overview page. Restricts database polling to a single source:

| Option                      | Behavior                                              |
|-----------------------------|-------------------------------------------------------|
| **Disable Force Retrieval** | Both main and backup databases are polled (default).  |
| **Main**                    | Only the main database is polled.                     |
| **Backup**                  | Only the backup database is polled.                   |

- **Duration** (minutes): When set to 0, the restriction is indefinite (max: 525600 minutes / 1 year).
- **Apply** button: Activates the selected force retrieval configuration.
- **Force Retrieval Status**: Displays the current active configuration.

### Parameter Overview

This page contains a **tree control** providing a hierarchical view: **Satellite** > **Transponders** > 14 parameter tables (TWTA Status, Mute Status, Mode, ALC Input Power, FGM Output Power, Gain Step FGM, Gain Step ALC, Gain Step Ageing/Tuning, Gain Step FGM/ALC, Anode Voltage, Helix Current, Bus Current, Uplink Coverage, Downlink Coverage).

### Params TWTA/Mute/Mode

This page contains three tables with status values:

| Table              | Accepted Raw Values                                   | Discrete values    |
|--------------------|-------------------------------------------------------|--------------------|
| **TWTA Status**    | ON, OFF, HV_ON                                        | 1 = ON, 0 = OFF    |
| **Mute Status**    | ON, OFF, MUTE, RF_ON, MUTE_ON, MUTE_OFF               | 1 = ON, 0 = OFF    |
| **Mode (FGM/ALC)** | FGM, ALC, FG_MODE, ALC_MODE                           | 0 = FGM, 1 = ALC   |

Each table includes the Transponder Name, Station Code, Customer, Status/Value, Update Time, Param Age, Sample Time, Sample Age, and Source DB.

### Params Power

This page contains two tables with **threshold-based alarming** and **deviation tracking**:

- **ALC Input Power** (dBm): Min/Max Threshold, Nominal Value, Deviation (dB), Deviation Alarm State (Normal/Major/Critical), Alarm State (Enabled/Disabled). Linked to Mode (FGM/ALC) table via foreign key.
- **FGM Output Power** (dBm): Same threshold and deviation features.

Each table has a **Severity Offset** subpage (page button) where Major and Critical offsets can be configured. Default offsets: Major = 3, Critical = 6.

### Params Gain Step

This page contains four tables, each with Min/Max Threshold and Alarm State columns:

- **Gain Step FGM (FCA Level)**: With unit "step".
- **Gain Step ALC (GCA Level)**: With unit "step".
- **Gain Step Ageing/Tuning (SCA Level)**: With unit "step".
- **Gain Step (FGM/ALC)**: Unitless.

Each table has a corresponding **Severity Offset** subpage.

### Params Voltage and Currents

This page contains three tables, each with Min/Max Threshold and Alarm State columns:

- **Anode Voltage**: With unit "V".
- **Helix Current**: With unit  "mA".
- **Bus Current**: With unit "A".

Each table has a corresponding **Severity Offset** subpage.

### Params Coverage

This page contains two tables with string-based coverage values:

- **Uplink Coverage**
- **Downlink Coverage**

These tables do not have threshold or severity offset features.

### Satellite Info

This page contains a table where you can view and configure satellite metadata: Name, Position, Number of Transponders, Launch Date, and Contact Person.

### Configuration

- **Sync Alarm Template** button: Manually synchronizes the alarm template with current transponder display keys.
- **Show Disabled Transponders** toggle: Controls whether disabled transponders appear in parameter tables.
- **Import/Export CSV**: Allows you to import or export the Association Table via CSV files. Use **Refresh List** to update the file dropdown.
- **Association Table**: 19-column table mapping each transponder to its TM_IDs for all 14 parameter types, plus Transponder ID, Transponder Name, Station Code, Customer, and Enabled status.
- **Add/Remove Transponder**: Allows you to add or remove rows by entering a Transponder ID.

### Setup

On this page, you can configure the database connection parameters for Main and Backup CMRS databases, plus the Satellite ID.

### Full Load

This page displays raw unprocessed database contents:

- **Full Load Main** table: All rows from the Main database for the configured satellite (columns: TM_ID, Update_Time, Description, Units, Type, Value, Validity, Sample_Time, Spare 1–5).
- **Full Load Backup** table: Same structure as above, but for the Backup database.
- **Last Update** timestamps and **Time Since Last Update** for each database.
- **Refresh All** button: Manually triggers a full database reload.

## Exception Values

The following exception values are used across all parameter tables:

| Value     | Display               | Description                                          |
|-----------|-----------------------|------------------------------------------------------|
| **-9999** | NOT VALID             | Data exists in database but validity flag is false.  |
| **-9998** | NOT PRESENT IN DB     | TM_ID not found in the database.                     |
| **-9997** | TRANSPONDER DISABLED  | Transponder is disabled in the Association Table.    |

## Notes

- Alarm templates are auto-synced when a Transponder Name (display key) changes in the Association Table.
- The ALC Input Power table has a foreign key relation to the Mode (FGM/ALC) table, enabling alarm correlation based on the current operating mode.
- Station Code and Customer are included as alarm properties on monitored parameters.
