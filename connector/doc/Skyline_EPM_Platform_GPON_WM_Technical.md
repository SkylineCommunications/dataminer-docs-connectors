---
uid: Connector_help_Skyline_EPM_Platform_GPON_WM_Technical
---

# Skyline EPM Platform GPON WM

## About

The **Skyline EPM Platform GPON WM** connector monitors and manages distributed workflow execution for the **Skyline EPM Platform GPON** solution through a virtual connection.

It operates with role-based behavior:

- **Master**: Receives work, creates job entries, assigns slaves, and tracks execution.
- **Slave**: Executes the existing local processing flows and reports results back to the master.

The connector processes three workflow types:

- **KAFKA ONT DATA**
- **Subscriber**
- **Split**

### Version Info

> [!NOTE]
> Version info is maintained via `<VersionHistory>` tags in `protocol.xml`.
> See the connector's version history for range details.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection.

### Initialization

After element creation, configure the role and related pages.

1. On the **General** page, set **Element Role** to **Master** or **Slave**.
1. Configure shared settings (available on both **Master Configuration** and **Slave Configuration**):
   - **System Credentials**:
     - **System Username**
     - **System Password**
   - **Import Settings**:
      - **Entity Import Directory**: Generic GPON entity import path used across the EPM solution. This path is used to retrieve ONT CSV files and Subscriber/Splitter CSV files for workflow processing.
      - **KAFKA Import Directory**: Path where KAFKA stream update files are located.
      - **Entity/KAFKA Import Directory Type**: Defines whether import paths are local or remote.
   - **Export Settings**:
       - **Entity Export Directory**: Generic GPON entity export path where compatible Subscriber and Splitter CSV files are written for Passive Data workflows.
      - **KAFKA Export Directory**: Path where generated KPI provisioning JSON files are exported for ONT KPI workflows.
      - **Entity/KAFKA Export Directory Type**: Defines whether export paths are local or remote.
   - **Workflow Settings**:
      - **Status**: Enables or disables workflow processing.
      - **Processing Timer**: Frequency for checking pending workflow requests.
      - **Wait Time**: Delay before reprocessing failed requests.
      - **Retries**: Maximum retry count before a request is considered failed.
1. Configure role-specific settings:
   - **Master role**:
      - **KAFKA Streams**
      - **KAFKA Interval**
      - **Maximum Time Stream Process**
      - **Processed File Directory** and **Processed File Directory Type**
      - **Processed File Retention Period**
       - **Processed File Housekeeping Interval**
   - **Slave role**:
      - **Master Name** and **Master Id** (discovered and displayed on the **Slave Configuration** page).

## How to Use

### Main Pages

#### General Page

- Set **Element Role** to define Master or Slave behavior.

#### Workflows Page (Slave)

- Displays the **Workflow Overview** queue and status tracking.
- Tracks workflow lifecycle including:
  - **Received**
  - **Dropped-Redundant**
  - **Completed**
  - **Failed**
  - **Failed - No ONT Data**
  - **Failed - No ONT Updates**
  - **Failed - Exception**

#### Jobs Page (Master)

- Displays the **Job Overview** table used for master-side orchestration.
- Job statuses include:
  - **New**
  - **Sent**
  - **Accepted**
  - **Completed**
  - **Failed**
  - **Timed Out**
  - **Dead Letter**
- Includes a **Clear All** action to remove all job entries.

#### Slaves Page (Master)

- Displays **Slave Overview** with registered slave elements, processing status, and last usage time.

#### InterApp Messages Page

- Displays inbound and outbound InterApp traffic and response status for distributed processing visibility.

### Workflow Processing

#### KAFKA ONT DATA

1. The connector creates timer-driven Kafka workflow requests.
1. Workflow rows are queued and processed according to configured timing and retry settings.
1. ONT inventory and KAFKA stream data are correlated and exported through configured output paths.
1. Generated output files are moved to the configured processed-files directory after successful processing.

#### Subscriber and Split

1. Requests are received through InterApp and queued in the workflow table.
1. Passive workflows are processed through slave-side execution logic.
1. Export files are generated and response notifications are sent through the configured script integration.

## Notes

- Workflow processing can use local or remote paths; when remote paths are used, credentials and share accessibility are required.
- The distributed architecture preserves existing slave-side processing behavior while adding master-side job orchestration.
- Kafka output handling includes improved file processing and ONT-serial-based exported file creation in recent versions.
