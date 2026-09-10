---
uid: Connector_help_Skyline_Custom_Offload
---

# Skyline Custom Offload

## About

The **Skyline Custom Offload** connector enables DataMiner to automatically discover and offload CSV files from a local folder to a remote cloud storage location. It is designed for deployments where DataMiner's native offload process redirects trend and alarm data to CSV files instead of a database, and those files need to be securely and reliably forwarded to a centralized storage backend.

In its initial version, the connector supports offloading to **AWS S3 buckets**, with a configurable interval, file-type filtering, retry logic, and a full audit log of every offload attempt.

## Key Features

- **Automated file offload to AWS S3**: Continuously monitors a local source folder and transfers matching files to a configured S3 bucket on a scheduled interval, without manual intervention.

- **Pre-offload control manifest**: Before uploading the data files, the connector sends a summary manifest to the S3 bucket, giving downstream applications a reliable inventory of what to expect — enabling data integrity validation.

- **Configurable file filtering**: Uses a configurable regex pattern to match only the desired file types (e.g., `.*\.(csv|txt)$`), ensuring that unintended files are never transferred.

- **Retry logic with failed file quarantine**: Files that fail to upload are automatically retried up to a configurable limit and then moved to a dedicated failed folder, preventing processing loops and enabling easy human review.

- **Live offload audit log**: Every file transfer attempt is recorded in a persistent, filterable log table (file name, timestamp, status, retry count, error message), giving operators full visibility into what was sent and what failed.

- **On-demand manual offload**: An operator can trigger an immediate offload cycle at any time via a dedicated button, without waiting for the next scheduled interval.

## Use Cases

### Centralizing DataMiner CSV Offload Data in the Cloud

**Challenge**: DataMiner Systems configured to offload to CSV files generate large volumes of data locally. Without automation, these files accumulate on the server and require manual effort to transfer to a centralized data lake.

**Solution**: The Skyline Custom Offload connector automatically picks up the CSV files as they are generated and uploads them to an AWS S3 bucket on a scheduled basis. The configurable interval (1 minute to 1 hour) and file filter ensure only the right files are moved at the right cadence.

**Benefit**: Eliminates manual file management, ensures consistent data availability in the cloud, and reduces local disk consumption — all without human intervention.

### Ensuring Data Integrity for Downstream Consumers

**Challenge**: Applications consuming the offloaded data need to know in advance how many files and which files to expect, to detect missing or incomplete transfers.

**Solution**: Before uploading the batch of data files, the connector sends a control manifest file to the S3 bucket listing all files in the current offload cycle. Downstream systems can validate the received files against this manifest.

**Benefit**: Provides a reliable, automated integrity check mechanism for any pipeline that consumes DataMiner offload data from S3.

### Rapid Incident Diagnosis for Failed Transfers

**Challenge**: When an offload fails — because of network issues, invalid credentials, or S3 service disruptions — operators need to quickly identify which files were affected and why.

**Solution**: The connector's Offload Log table records every attempt with a status (*Success*, *Failed*, or *Retry*), a retry counter, and the full error message from the last failed attempt. The table is filterable and sortable, and failed files are automatically moved to a configurable failed folder for human review.

**Benefit**: Dramatically reduces mean time to diagnose offload failures, and provides a clear audit trail for SLA reporting.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.0.0 - 14003 or higher** is required to run this connector.

- **AWS S3 bucket** is required as the target storage. The following details must be configured in the connector:

  - S3 Bucket Name
  - AWS Region
  - S3 Root Folder (key prefix)
  - AWS Access Key ID
  - AWS Secret Access Key

- **Local file system access**: The DataMiner Agent running this connector must have read access to the configured source folder and write access to the failed folder path.

- **Network connectivity**: The DataMiner Agent must have outbound HTTPS connectivity to the AWS S3 endpoint for the configured region.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Custom_Offload_Technical).
