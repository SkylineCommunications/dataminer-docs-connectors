---
uid: Connector_help_Skyline_Custom_Offload_Technical
---

# Skyline Custom Offload

## About

The Skyline Custom Offload connector offloads files from a local folder on the DataMiner Agent to a remote AWS S3 storage endpoint. It monitors a configured source directory, uploads matching files on a scheduled basis, and provides full audit logging with retry logic for failed transfers.

### Minimum DataMiner Version

10.4.0.0 - 14003

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

After creating the element, navigate to the **Configuration** page and configure the following parameters:

1. **Storage Type**: Select the remote storage type (currently only *S3*).

2. **Source Folder Path**: Local folder path where files to offload are located.

3. **Failed Folder Path**: Local folder path where permanently failed files are moved.

4. **File Types Filter**: Regex pattern to match file extensions (e.g., `.*\.(csv|txt)$`).

5. **Max Retries**: Maximum number of upload retries per file before marking it as failed (range: 1–5, default: 3).

6. **Schedule Mode**: Choose between *Interval* or *Recurrence*.

   - **Interval mode**: Configure the *Offload Interval* (range: 1 min–60 min, default: 60 min).
   - **Recurrence mode**: Configure the *Recurrence Details*, *Recurrence Time of the Day*, and *Next Execution Time* via the *Edit* button.

7. **Offload Enabled**: Toggle to enable or disable the offload operation.

8. Open the **S3 Configuration** subpage and configure:

   - **S3 Bucket Name**: Name of the target S3 bucket.
   - **S3 Region**: AWS region for the S3 bucket.
   - **S3 Root Folder**: Root folder (key prefix) for uploaded files (e.g., `dataminer/offload/`).
   - **S3 Access Key ID**: AWS Access Key ID for authentication.
   - **S3 Secret Access Key**: AWS Secret Access Key for authentication.

9. Click **Apply and Test** to save the configuration and verify connectivity.

### Redundancy

There is no redundancy defined in the connector.

## How to Use

### General Page

The General page provides an at-a-glance status overview:

- **Connection Information**:
  - *Connection Status*: Indicates whether the connector can reach the configured storage endpoint (Not Initialized / Fail / Success).
  - *Connection Endpoint*: The resolved endpoint URL currently in use.
  - *Last Package Sent Time*: Timestamp of the last successful offload batch.

- **Processing Summary**:
  - *Total Files*: Cumulative total of files discovered for offload.
  - *Sent Files*: Total number of files successfully offloaded.
  - *Failed Files*: Total number of files that permanently failed offload.
  - *Retried Files*: Total number of files currently in retry state.

### Offload Page

The Offload page provides detailed offload monitoring and control:

- **Processing Summary**: Same KPI counters as displayed on the General page.

- **Offload Log Table**: A detailed log of all file offload attempts with the following columns:
  - *Index*: Unique row identifier.
  - *File Name*: Name of the offloaded file.
  - *Date Sent*: Timestamp of the offload attempt.
  - *Status*: Result (Success / Failed / Retry).
  - *Retry Count*: Number of retries for this file.
  - *Error Message*: Error details from the last failed attempt.

- **Log Retention**: Configures how long log entries are kept (range: 1 hour–7 days, default: 1 hour).

- **Manual Offload**: Button to trigger an immediate offload cycle.

- **Clear Log Table**: Button to remove all entries from the offload log.

- **Reset KPIs**: Button to reset all file counters to zero.

### Configuration Page

The Configuration page contains all operational settings organized into:

- **Storage Type Configuration**: Selects the target storage backend.
- **Files Path Configuration**: Source folder, failed folder, file type regex, and max retries.
- **Schedule Configuration**: Offload enabled toggle, schedule mode, interval or recurrence settings.
- **S3 Configuration** (subpage): All AWS S3-specific credentials and bucket settings.

## Notes

- Successfully offloaded files are removed from the source folder after upload.
- Files that exceed the maximum retry count are moved to the configured failed folder for manual review.
- The log table is automatically cleaned up based on the configured log retention period.
- The DataMiner Agent must have outbound HTTPS connectivity to the AWS S3 endpoint for the configured region.
- The DataMiner Agent must have read access to the source folder and write access to the failed folder.
