---
uid: Connector_help_Grass_Valley_AMPP_SRT_Input_Application
---

# Grass Valley AMPP SRT Input Application

The SRT Input is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **View SRT Input workloads**: With this connector, you can get an overview of the workloads for the "SRT Input" application type, along with their status information.
- **Send configuration commands**: Using this connector, you will be able to configure specific SRT Input applications.
- **Get up-to-date status info**: Whenever this connector makes an adjustment to the configuration, it will immediately retrieve status information from the GVAMPP Manager element.
- **Automatically recover from an element restart**: The manager element monitors the state of the SRT Input element, so it will automatically know when that element is available again after a restart and send the workload status to it.

## Use Case

- **Challenge**: Operators with thousands of workloads need to be able to monitor only the SRT Input workloads, using separate elements.
- **Solution**: Create one or multiple elements using the SRT Input Application connector, and point each workload to the respective element.
- **Benefit**: No more need to sift through the filtering of the large workloads table. All your SRT Input status information is available in one place.

> [!NOTE]
> While this connector is only applicable for SRT Input workloads, standalone connectors for other workload types are also available.

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Grass Valley AMPP SRT Input Application connector.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for the Grass Valley AMPP SRT Input Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_SRT_Input_Application_Technical).
