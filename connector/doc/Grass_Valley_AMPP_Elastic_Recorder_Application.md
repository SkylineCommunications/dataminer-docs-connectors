---
uid: Connector_help_Grass_Valley_AMPP_Elastic_Recorder_Application
---

# Grass Valley AMPP Elastic Recorder Application

The Elastic Recorder is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **Displaying Workloads for a specific Application Type**: This connector is able to display workloads for the "Elastic Recorder" application type, and their status.
- **Send Configuration commands to a specific elastic recorder application**: This connector is able to configure specific Elastic Recorder applications via HTTP POST request.
- **Request status from GVAMPP Manager**: This connector is able to retrieve its status from the manager element immediately after performing a configuration POST.
- **Recover from an element restart**: When the connector comes back to active, the manager element knows to send workload status to it because of an element state monitor.


## Use Case

- **Challenge**: Operator has thousands of workloads, but want to monitor only the Elastic Recorder workloads, in separate elements.
- **Solution**: Operator can create one or multiple elements of the Elastic Recorder Application type, and point each workload to the respective element.
- **Benefit**: Don't have to sift through the filtering of the large workloads table, all your Elastic Recorder status information would be under one roof. 
    - <em> Note: More workload types will be added as standalone connectors in the future.</em>
## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP Elastic Recorder Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Grass Valley AMPP Elastic Recorder Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_Elastic_Recorder_Application_Technical).
