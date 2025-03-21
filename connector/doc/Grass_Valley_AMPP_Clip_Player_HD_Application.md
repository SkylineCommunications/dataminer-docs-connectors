---
uid: Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application
---

# Grass Valley AMPP Clip Player HD Application

The Clip Player HD is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **Displaying Workloads for a specific Application Type**: This connector is able to display workloads for the "ClipPlayer" application type, and their status.
- **Send Configuration commands to a specific Clip Player HD application**: This connector is able to configure specific Clip Player HD applications via HTTP POST request.
- **Request status from GVAMPP Manager**: This connector is able to retrieve its status from the manager element immediately after performing a configuration POST.
- **Recover from an element restart**: When the connector comes back to active, the manager element knows to send workload status to it because of an element state monitor.


## Use Case

- **Challenge**: Operator has thousands of workloads, but want to monitor only the Clip Player HD workloads, in separate elements.
- **Solution**: Operator can create one or multiple elements of the Clip Player HD Application type, and point each workload to the respective element.
- **Benefit**: Don't have to sift through the filtering of the large workloads table, all your Clip Player HD status information would be under one roof. 
    - <em> Note: More workload types will be added as standalone connectors in the future.</em>
## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP Clip Player HD Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Grass Valley AMPP Clip Player HD Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application_Technical).
