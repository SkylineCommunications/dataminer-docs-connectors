---
uid: Connector_help_Grass_Valley_AMPP_SRT_Input_Application
---

# Grass Valley AMPP SRT Input Application

The SRT Input is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **View SRT Input workloads**: With this connector, you can get an overview of the workloads for the "SRT Input" application type, along with their status information.
- **Send configuration commands**: Using this connector, you will be able to configure specific SRT Input applications.
- **Get up-to-date status info**: Whenever this connector makes an adjustment to the configuration, it will immediately retrieve status information from the manager element.

## Use Case

- **Challenge**: SRT Input Application element is stopped, restarted, or in an error state for some time.
- **Solution**: In conjunction with the GVAMPP Manager, this connector is able to receive/parse workload status information from the GVAMPP Manager element when it comes back from stop/restart/error element status.
- **Benefit**: Potential element issues will not cause you to be out of sync — the GVAMPP Manager will send out initialization messages periodically and on element state changes.

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP SRT Input Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Grass Valley AMPP SRT Input Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_SRT_Input_Application_Technical).
