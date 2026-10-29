---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Descrambling_Service_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH Descrambling Service connector to monitor site-level streaming states and alarms in DataMiner."
---

# Vodafone Kabel Deutschland GmbH Descrambling Service

## About

The Vodafone Kabel Deutschland GmbH Descrambling Service connector monitors outgoing streaming states per site for the services included in an enhanced service.

## Configuration

### Connections

This is a service protocol. To create a service using this protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
1. Specify the name for the service.
1. Open the advanced options and select *Vodafone Kabel Deutschland GmbH Descrambling Service* as the service protocol, using the latest or production version.
1. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

The **General** page contains an overview of the active stream states per site.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
