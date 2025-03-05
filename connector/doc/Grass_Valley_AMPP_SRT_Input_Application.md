---
uid: Connector_help_Grass_Valley_AMPP_SRT_Input_Application
---

# Grass Valley AMPP SRT Input Application

The SRT Input is part of the Application Connectors defined for the GV AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP.
It depends on Interapp messages from the Grass Valley AMPP Manager.

## About

### Key Features

- **Displaying Workloads for a specific Application Type**: This connector is able to display workloads for the "SRT Input" application type, and their status.
- **Send Configuration commands to a specific srt input application**: This connector is able to configure specific SRT Input applications via HTTP POST request.
- **Request status from GVAMPP Manager**: This driver is able to retrieve its status from the manager element immediately after performing a configuration POST.


## Use Case

- **Challenge**: SRT Input Application element is stopped, restarted, or in an error state for some time.
- **Solution**: In conjunction with the GVAMPP Manager, this conenctor is able to receive/parse workload status information from the GVAMPP Manager element when it comes back from stop/restart/error element status. 
- **Benefit**: You don't have to worry about being out of sync during potential element issues - the GVAMPP Manager will send out initialization messages periodically and on element state change.

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP SRT Input Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Grass Valley AMPP SRT Input Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_SRT_Input_Application_Technical).

