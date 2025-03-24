---
uid: Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application
---

# Grass Valley AMPP Clip Player HD Application

## About

The Clip Player HD is an application connector for the GV AMPP (Agile Media Processing Platform) solution. It will allow you to view the status of the workloads added to a fabric in AMPP and also to configure these workloads.

## Key Features

- **View Clip Player workloads**: With this connector, you can get an overview of the workloads for the "Clip Player" application type, along with their status information.
- **Send configuration commands**: Using this connector, you will be able to configure specific Clip Player HD applications.
- **Get up-to-date status info**: Whenever this connector makes an adjustment to the configuration, it will immediately retrieve status information from the GVAMPP Manager element.
- **Recover from an element restart**: The manager element monitors the state of the Clip Player HD element, so it will automatically know when that element is available again after a restart and send the workload status to it.

## Use Case

- **Challenge**: Operators with thousands of workloads need to be able to monitor only the Clip Player HD workloads, using separate elements.
- **Solution**: Create one or multiple elements of the Clip Player HD Application type, and point each workload to the respective element.
- **Benefit**: No more need to sift through the filtering of the large workloads table. All your Clip Player HD status information is available in one place.

> [!NOTE]
> While this connector is only applicable for Clip Player HD workloads, standalone connectors for other workload types are also available.

## Technical info

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for the Grass Valley AMPP Clip Player HD Application, refer to the [Technical help page](xref:Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application_Technical).
