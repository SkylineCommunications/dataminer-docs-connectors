---
uid: Connector_help_ZDF_Prismon_Mapper_Technical
description: Configure the ZDF Prismon Mapper to monitor Prismon elements and match active TAP streams to services with regex rules.
---

# ZDF Prismon Mapper

## About

The ZDF Prismon Mapper monitors Rohde & Schwarz Prismon elements. It subscribes to their stream discovery tables, identifies active TAP streams with configurable matching rules, and updates the corresponding Prismon services.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require input during element creation. The mapper monitors the Prismon elements configured on the **Elements** page.

### Initialization

After creating the element, [enable the Prismon elements](#enabling-the-prismon-elements) to monitor and define the [service mapping rules](#mappings). The mapper discovers the available Prismon elements during initialization and starts subscriptions for the enabled elements. No direct device credentials are required.

#### Enabling the Prismon Elements

To enable monitoring for a Rohde & Schwarz Prismon element:

1. Go to the **Elements** page.

   The mapper automatically lists the Rohde & Schwarz Prismon elements available in the DataMiner System.

1. Enable the **Monitored** toggle for each element that the mapper must monitor.

   The mapper then subscribes to the stream discovery and service tables of each enabled element.

The table also shows the element name, state, and alarm level. Use the **Reinitialize** button on the **General** page to rerun the initialization logic after changing the monitored elements.

#### Mappings

##### Manual Configuration

On the **Mappings** page, configure one row for each service that the mapper must assign. Use the table context menu to add, duplicate, edit, or delete mapping rows.

The mapping table contains the following fields:

| Field | Description |
|---|---|
| **Element ID** | ID of the Prismon element that contains the service. |
| **Service ID** | Primary key of the Prismon service to update. |
| **Service Name** | Name of the service, retrieved from the Prismon element. |
| **Stream ID** | Stream identifier to match. Set this to `N/A` to disable Stream ID matching. |
| **Stream Type** | Stream protocol to match: `HLS` or `DASH`. |
| **Backup** | Whether the `Backup` regex group must match. Use **Enabled**, **Disabled**, or **N/A**. |
| **Geo** | Value that the `Geo` regex group must match, or `N/A` to ignore the group. |
| **Stream URL Regex** | Regular expression used to match the stream URL. |

##### CSV Import

The mapper can import service mapping rules from CSV files stored in:

`C:\Skyline DataMiner\Documents\DMA_COMMON_DOCUMENTS\ZDF Prismon Mapper`

Subfolders are supported. CSV files in this directory and its subfolders are available in the **CSV Import Path** selector on the **Mappings** page.

To import mappings:

1. Copy a CSV file to the import directory.

   The file becomes available in the **CSV Import Path** selector after the file list is refreshed.

1. Select the CSV file in the **CSV Import Path** selector on the **Mappings** page.

1. Select **Import & Merge** or **Import & Synchronize**.

   - **Import & Merge** imports the CSV rows and overwrites matching mappings without removing any other mappings.

   - **Import & Synchronize** imports the CSV rows and also removes mappings that are not present in the CSV file.

The CSV file must contain the following columns:

| Column | Expected value |
|---|---|
| `ElementID` | DataMiner element ID in `agent ID/element ID` format, for example `123/456`. |
| `ServiceID` | Numeric Prismon service ID. |
| `StreamID` | Numeric stream ID or `-1`. |
| `StreamType` | `HLS`, `DASH`, or `-1`. |
| `Backup` | `Yes`/`No`, `Enabled`/`Disabled`, `True`/`False`, `1`/`0`, or `N/A`. |
| `Geo` | A geo value, an empty value, or `N/A`. |
| `UrlRegex` | Regular expression used to match the stream URL. |

For example:

```csv
ElementID,ServiceID,StreamID,StreamType,Backup,Geo,UrlRegex
123/456,41,2115426,HLS,N/A,N/A,https?:\/\/(.*?)\.(.*?)\.(.*?)\/(?<StreamId>\d+)(?<Backup>-b)?\/(?<Geo>\w+)\/(.*)\/1\/1.m3u8
```

Rows with invalid element or service IDs are skipped during import and logged by the connector.

## How to Use

The Generic Prismon connector polls the TAP endpoints and stores the discovered stream objects in the Prismon stream discovery table. The mapper receives table updates through DataMiner subscriptions and processes the initial table and every new or updated entry. The mapper does not use a direct device connection or generate its own TAP polling traffic.

For each candidate stream, the mapper checks the configured matching rules:

- The stream state is **Active**.
- The stream protocol matches the configured protocol, such as **HLS** or **DASH**.
- The backup state matches when a backup value is configured.
- The geo value matches when a geo value is configured.
- The URL matches the configured regular expression.

When a match is found, the mapper uses the service ID from the mapping table and the stream object ID from the discovery table to update the corresponding Prismon service through a DataMiner set. The set updates the service's stream assignment and triggers the Prismon service restart action.

The mapper does not send an update when the service already references the active stream object ID. It also does not update a service when no mapping matches the discovered stream.

## Notes

### Stream Correlation

Stream object IDs can change after a stream restart or a primary/backup switchover. To keep the service assignment correct, the mapper correlates streams using stable identifiers in the URL rather than relying on the object ID alone.

The URL pattern is configured as a regular expression. The expression can use the optional named groups `StreamId`, `Geo`, and `Backup` to correlate a URL with the corresponding mapping values. This allows the mapper to distinguish services that share the same stream ID while ignoring changes to the stream object ID.

For backup matching, **Enabled** requires the `Backup` group to match, **Disabled** ignores the `Backup` group value, and **N/A** ignores backup matching entirely. For geo matching, configure a value to require a matching `Geo` group, or use `N/A` to ignore the group.

### Processing Flow

1. The Generic Prismon connector polls the TAP endpoints.
1. Prismon stores the discovered TAP stream objects in the stream discovery table.
1. The mapper processes the initial table and subsequent new or updated entries.
1. The mapper selects active entries and compares them with the Service Mapping table.
1. For each matching entry, the mapper updates the corresponding Prismon service with the stream object ID.
1. The mapper skips the update when the service already references that stream object ID.
