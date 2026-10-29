---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_ABR_OTT_Service_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH ABR OTT Service connector to monitor Harmonic VOS/XOS stream states, device settings, and alarms."
---

# Vodafone Kabel Deutschland GmbH ABR OTT Service

## About

The Vodafone Kabel Deutschland GmbH ABR OTT Service connector monitors the active configuration and streaming status of Harmonic VOS/XOS elements per service.

## Configuration

### Prerequisites

This connector requires the [Harmonic VOS](xref:Connector_help_Harmonic_VOS) connector, range 1.1.1.x or later.

### Connections

To create a service using this service protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
1. Specify the name for the service.
1. Open the advanced options and select *Vodafone Kabel Deutschland GmbH ABR OTT Service* as the service protocol, using the latest or production version.
1. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

The **General** page contains the overview of the active stream states per site.

The **Service Active Configuration** page contains the overview of the input and output devices configuration.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

The **General Parameters** page contains the list of parameters with important information regarding the system.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
