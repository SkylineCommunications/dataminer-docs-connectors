---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Qbit_Radio_Service_Technical
description: Configure and use the Qbit Radio Service connector in DataMiner, with connection settings and operational guidance.
---

# Vodafone Kabel Deutschland GmbH Qbit Radio Service

## About

The Vodafone Kabel Deutschland GmbH Qbit Radio Service connector monitors the active configuration of the Qbit element per service.

## Configuration

### Connections

To create a service using this service protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
2. Specify the name for the service.
3. Open the advanced options and select *Vodafone Kabel Deutschland GmbH Qbit Radio Service* as the service protocol, using the latest or production version.
4. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

The **General** page contains the overview of the active stream states per site.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
