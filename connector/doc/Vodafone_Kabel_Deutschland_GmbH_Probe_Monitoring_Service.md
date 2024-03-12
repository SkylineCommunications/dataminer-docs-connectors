---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service
---

# Vodafone Kabel Deutschland GmbH Probe Monitoring Service

The Vodafone Kabel Deutschland GmbH Probe Monitoring Service protocol monitors and controls the life cycle of a configured Ethernet stream on one of the probes.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | [BridgeTech VB Probe Series](xref:Connector_help_Bridge_Technologies_VB_Probe_Series) | - |

## Configuration

Service creation and configuration happens automatically through the *Ad Hoc Probe Monitoring Solution* when a new probe session is created.

No manual configuration is needed to create this service.

## How to use

- The **General** page contains the details of the probe monitoring session and allows you to adjust the session end time.

  > [!NOTE]
  > Once the session end time expires, an automatic action will finish the session to prevent too many concurrent streams being configured on the probes. This also means that the DataMiner service will be removed at expiration and will not be accessible anymore.

- The **Alarms** page shows all alarms linked to this service.

  This page also contains a toggle button to retrieve and display all active alarms for the included services and elements.

- The **Elements** page shows all elements and services monitored by this service.

  This page also contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
