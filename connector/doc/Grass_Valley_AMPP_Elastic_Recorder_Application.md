---
uid: Connector_help_Grass_Valley_AMPP_Elastic_Recorder_Application
---

# Grass Valley AMPP Elastic Recorder Application

The Elastic Recorder is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## About

### Key Features

- **View Elastic Recorder workloads**: With this connector, you can get an overview of the workloads for the "Elastic Recorder" application type, along with their status information.
- **Send configuration commands**: Using this connector, you will be able to configure specific Elastic Recorder applications.
- **Get up-to-date status info**: Whenever this connector makes an adjustment to the configuration, it will immediately retrieve status information from the GVAMPP Manager element.
- **Recover from an element restart**: The manager element monitors the state of the Elastic Recorder element, so it will automatically know when that element is available again after a restart and send the workload status to it.

## Use Case

- **Challenge**: Operators with thousands of workloads need to be able to monitor only the Elastic Recorder workloads, using separate elements.
- **Solution**: Create one or multiple elements of the Elastic Recorder Application type, and point each workload to the respective element.
- **Benefit**: No more need to sift through the filtering of the large workloads table. All your Elastic Recorder status information is available in one place.

> [!NOTE]
> While this connector is only applicable for Elastic Recorder workloads, standalone connectors for other workload types are also available.

### Prerequisites

- **Grass Valley AMPP Manager** is required for this connector to function properly.
- **DataMiner version 10.3 or higher** is required for compatibility with the Grass Valley AMPP Clip Player HD Application connector.

## Technical info

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for the Grass Valley AMPP Elastic Recorder Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_Elastic_Recorder_Application_Technical).
