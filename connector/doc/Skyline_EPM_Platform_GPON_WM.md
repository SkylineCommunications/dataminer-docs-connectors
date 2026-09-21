---
uid: Connector_help_Skyline_EPM_Platform_GPON_WM
description: "Learn how to use the Skyline EPM Platform GPON WM connector to orchestrate GPON workflows, distribute jobs, and process ONT and subscriber data."
---

# Skyline EPM Platform GPON WM

## About

The Skyline EPM Platform GPON WM connector is a virtual DataMiner element that acts as the **master/slave orchestration layer** for GPON-related workflows inside the Skyline EPM Platform. It distributes work across slave elements via InterApp messaging, tracks job and workflow status, and coordinates KAFKA-based ONT/subscriber data processing without requiring direct device communication.

## Key Features

- **Master/slave orchestration**: Automatic master-slave discovery and health/status validation of connected slave elements.
- **Workflow management**: Tracks requested workflows end to end (request, response, retries, processing time) via the Workflow Overview table.
- **Job distribution & tracking**: Creates, assigns, and monitors jobs across slaves, including job file grouping and per-slave job reporting.
- **KAFKA integration**: Configurable import/export directories, polling interval, and streams for processing KAFKA ONT and subscriber data.
- **InterApp messaging**: Slave job completions and workflow results are exchanged with the master exclusively through InterApp messages, with configurable auto-delete/housekeeping of processed messages and jobs.
- **File and table housekeeping**: Scheduled cleanup of processed files and stale table entries.

## Use Case

- **Challenge**: Processing GPON ONT/subscriber data at scale requires distributing work across multiple slave elements while keeping a consistent, centralized view of workflow and job status.
- **Solution**: The connector's master element automatically discovers slaves, assigns jobs, and tracks their lifecycle (requested → in progress → completed) through dedicated Workflow and Job Overview tables, while all cross-element communication is handled through InterApp messaging.
- **Benefit**: Operators get a single-pane-of-glass view of GPON workflow and job processing across the entire slave fleet, with automatic housekeeping of completed jobs, messages, and files to safeguard the system's performance over time.

## Technical Reference

For configuration details and page-by-page usage instructions, refer to the [technical documentation page](xref:Connector_help_Skyline_EPM_Platform_GPON_WM_Technical).
