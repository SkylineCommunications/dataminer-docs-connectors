---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_DVB-T2_Service_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH DVB-T2 Service connector to monitor stream states, active configuration, and XSwitch sources."
---

# Vodafone Kabel Deutschland GmbH DVB-T2 Service

## About

The Vodafone Kabel Deutschland GmbH DVB-T2 Service connector monitors the active configuration and stream states of elements included in a DVB-T2 service, including XSwitch source status.

## Configuration

### Connections

To create a service using this service protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
1. Specify the name for the service.
1. Open the advanced options and select *Vodafone Kabel Deutschland GmbH DVB-T2 Service* as the service protocol, using the latest or production version.
1. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

The **General** page contains the overview of the active stream states per site.

The **Service Active Configuration** page contains the overview of the input and output devices configuration.

The **Source Status** page contains a table displaying the current status of the XSwitches.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

The **General Parameters** page contains the list of parameters with important information regarding the system.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
