---
uid: Connector_help_Skyline_Custom_Offload_Technical
---

# Skyline Custom Offload

## About

The Skyline Custom Offload connector offloads files from a local folder on the DataMiner Agent to a remote AWS S3 storage endpoint. It monitors a configured source directory, uploads matching files on a scheduled basis, and provides full audit logging with retry logic for failed transfers.

## Configuration

> [!TIP]
> Before you configure an element with this connector, make sure the [prerequisites](xref:Connector_help_Skyline_Custom_Offload#prerequisites) are met.

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

1. In the newly created element, navigate to the **Configuration** page and configure the following parameters:

   - **Storage Type**: Select the remote storage type (currently only *S3* is supported).

   - **Source Folder Path**: Specify the local folder path where files to offload are located.

     > [!NOTE]
     > After they have been successfully offloaded, files will be removed from the source folder.

   - **Failed Folder Path**: Specify the local folder path where permanently failed files are moved.

   - **File Types Filter**: Specify the regex pattern to match file extensions (e.g., `.*\.(csv|txt)$`).

   - **Max Retries**: Specify the maximum number of upload retries per file before it is marked as failed (range: 1–5, default: 3).

   - **Schedule Mode**: Choose between *Interval* or *Recurrence*.

      - **Interval mode**: Configure the **Offload Interval** (range: 1 min–60 min, default: 60 min).
      - **Recurrence mode**: Use the **Edit** button to configure the **Recurrence Details**, **Recurrence Time of the Day**, and **Next Execution Time**.

   - **Offload Enabled**: Enable or disable the offload operation.

1. Open the **S3 Configuration** subpage and configure the following parameters:

   - **S3 Bucket Name**: Name of the target S3 bucket.
   - **S3 Region**: AWS region for the S3 bucket.
   - **S3 Root Folder**: Root folder (key prefix) for uploaded files (e.g., `dataminer/offload/`).
   - **S3 Access Key ID**: AWS Access Key ID for authentication.
   - **S3 Secret Access Key**: AWS Secret Access Key for authentication.

1. Open **Configuration** page again and click **Apply and Test** to save the configuration and verify connectivity.

## How to Use

### General Page

The General page provides an at-a-glance status overview:

- **Connection Information**:

  - **Connection Status**: Indicates whether the connector can reach the configured storage endpoint.
  - **Connection Endpoint**: The resolved endpoint URL currently in use.
  - **Last Package Sent Time**: Timestamp of the last successful offload batch.

- **Processing Summary**:

  - **Total Files**: Cumulative total of files discovered for offload.
  - **Sent Files**: Total number of files successfully offloaded.
  - **Failed Files**: Total number of files that permanently failed to be offloaded.
  - **Retried Files**: Total number of files currently in retry state.

### Offload Page

The Offload page provides detailed offload monitoring and control:

- **Processing Summary**: Shows the same KPI counters as displayed on the General page.

- **Offload Log Table**: A detailed log of all file offload attempts, with the following columns:

  - **Index**: Unique row identifier.
  - **File Name**: Name of the offloaded file.
  - **Date Sent**: Timestamp of the offload attempt.
  - **Status**: Result (*Success*, *Failed*, or *Retry*).
  - **Retry Count**: Number of retries for this file. Files that exceed the maximum retry count are moved to the configured failed folder for manual review.
  - **Error Message**: Error details from the last failed attempt.

- **Log Retention**: Configures how long log entries are kept (range: 1 hour–7 days, default: 1 hour). The log table will be automatically cleaned up based on the configured retention period.

- **Manual Offload**: Button to trigger an immediate offload cycle.

- **Clear Log Table**: Button to remove all entries from the offload log.

- **Reset KPIs**: Button to reset all file counters to zero.

### Configuration Page

The Configuration page contains all operational settings:

- **Storage Type Configuration**: Selects the target storage backend.
- **Files Path Configuration**: Source folder, failed folder, file type regex, and max retries.
- **Schedule Configuration**: Toggle button to enable or disable offloading, schedule mode, and interval or recurrence settings.
- **S3 Configuration** (subpage): All AWS S3-specific credentials and bucket settings.

## Notes

### External Libraries

| Library | Purpose |
|---|---|
| `AWSSDK.S3` | AWS S3 file upload and bucket operations. |
| `AWSSDK.Core` | AWS authentication and request signing. |
| `AlphaFS` | Extended file system operations on Windows. |
| `ICSharpCode.SharpZipLib` | File compression support (future-ready). |
| `Newtonsoft.Json` | JSON serialization for control manifests |
