---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH Probe Monitoring Service connector to monitor probe sessions and Ethernet stream lifecycles."
---

# Vodafone Kabel Deutschland GmbH Probe Monitoring Service

## About

The Vodafone Kabel Deutschland GmbH Probe Monitoring Service connector monitors and controls the lifecycle of an Ethernet stream configured on a probe. Services are created automatically by the **Ad Hoc Probe Monitoring Solution**.

## Configuration

### Connections

This connector is a service protocol. Service creation and configuration happen automatically through the **Ad Hoc Probe Monitoring Solution** when a new probe session is created.

No manual connection configuration is needed to create this service.

## How to Use

- The **General** page contains the details of the probe monitoring session and allows you to adjust the session end time.

  > [!IMPORTANT]
  > Once the session end time expires, an automatic action will finish the session to prevent too many concurrent streams being configured on the probes. This also means that the DataMiner service will be removed at expiration and will no longer be accessible.

- The **Alarms** page shows all alarms linked to this service.

  This page also contains a toggle button to retrieve and display all active alarms for the included services and elements.

- The **Elements** page shows all elements and services monitored by this service.

  This page also contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.

### Linked Components

- [BridgeTech VB Probe Series](xref:Connector_help_Bridge_Technologies_VB_Probe_Series)
