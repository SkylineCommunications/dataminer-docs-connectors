---
uid: Connector_help_Skyline_EPM_Platform_GPON_WM
---

# Skyline EPM Platform GPON WM

## About

The **Skyline EPM Platform GPON WM** connector is a distributed workflow manager for the **Skyline EPM Platform GPON** solution. It supports a **Master/Slave** operating model to orchestrate and execute GPON data workflows at scale.

The connector coordinates **KAFKA ONT DATA**, **Subscriber**, and **Split** workflows using InterApp messaging, role-based processing, and file-based exchange across the platform.

## Key Features

- **Distributed processing model**: Uses a Master to register and dispatch jobs, and Slaves to execute workflow processing.
- **Three workflow types**: Handles **KAFKA ONT DATA**, **Subscriber**, and **Split** requests.
- **Operational visibility**: Includes dedicated **Jobs**, **Slaves**, **Workflows**, and **InterApp Messages** pages.
- **Lifecycle management**: Adds processed-file and table housekeeping controls for long-running operation.

## Technical Reference

> [!NOTE]
> For detailed setup and operational guidance, refer to the [technical documentation page](xref:Connector_help_Skyline_EPM_Platform_GPON_WM_Technical).
