---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_UDP-RTP_GW_Service_Technical
description: Configure and use the UDP-RTP GW Service connector in DataMiner, with connection settings and operational guidance.
---

# Vodafone Kabel Deutschland GmbH UDP-RTP GW Service

## About

The Vodafone Kabel Deutschland GmbH UDP-RTP GW Service connector monitors the streaming states of ProStream X multiplexers included in an enhanced service.

## Configuration

### Connections

This connector is a service protocol and only requires the following input during service creation:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
2. Specify the name for the service.
3. Open the advanced options and select *Vodafone Kabel Deutschland GmbH UDP-RTP GW Service* as the service protocol, using the latest or production version.
4. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

The **General** page contains the overview of the active stream states per site.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
