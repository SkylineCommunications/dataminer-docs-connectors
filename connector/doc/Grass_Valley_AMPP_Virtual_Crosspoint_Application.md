---
uid: Connector_help_Grass_Valley_AMPP_Virtual_Crosspoint_Application
---

# Grass Valley AMPP Virtual Crosspoint Application

The Virtual Crosspoint is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **View Virtual Crosspoint workloads**: With this connector, you can get an overview of the workloads for the "Virtual Crosspoint" application type, along with their status information.
- **Send configuration commands**: Using this connector, you will be able to configure specific Virtual Crosspoint applications.
- **Get up-to-date status info**: Whenever this connector makes an adjustment to the configuration, it will immediately retrieve status information from the GVAMPP Manager element.
- **Automatically recover from an element restart**: The manager element monitors the state of the Virtual Crosspoint element, so it will automatically know when that element is available again after a restart and send the workload status to it.

## Use Case

- **Challenge**: Operators with thousands of workloads need to be able to monitor only the Virtual Crosspoint workloads, using separate elements.
- **Solution**: Create one or multiple elements using the Virtual Crosspoint Application connector, and point each workload to the respective element.
- **Benefit**: No more need to sift through the filtering of the large workloads table. All your Virtual Crosspoint status information is available in one place.

> [!NOTE]
> While this connector is only applicable for Virtual Crosspoint workloads, standalone connectors for other workload types will also become available in the future.

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP Virtual Crosspoint Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Grass Valley AMPP Virtual Crosspoint Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_Virtual_Crosspoint_Application_Technical).
