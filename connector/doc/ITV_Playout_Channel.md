---
uid: Connector_help_ITV_Playout_Channel
---

# ITV Playout Channel Service

The ITV Playout Channel Service protocol monitors the overall channel status of all ingress monitoring probes on every leg (red/blue/green A/green B) in the chain.

Channel status options:

- OK: No critical alarms present on any leg
- P1: Highest priority = Three or more different legs have critical alarms.
- P2: Two different legs have critical alarms.
- P3: One of the legs has a critical alarm.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

To create a service using this service protocol:

1. In DataMiner Cube, Navigate to **Apps** > **Service Templates**.
1. Select the Playout Channels template (default: *CHORD Playout Channels*).
1. In the action bar at the bottom of the card, click **Apply**.
1. Click **Load**.
1. If the template requires input data such as the Name or Probe Element, provide this information and continue.

A new service will be created based on the selected template. It will automatically include this service protocol.

> [!NOTE]
> The Service Templates module also allows you to import a set of services in bulk from an Excel file. For more information, see [Applying service templates](https://aka.dataminer.services/applying-service-templates).

## How to use

The **General** page contains the overall channel status.

The **Alarms** page displays all active alarms for the included services and elements.

The **Elements** page displays the elements configured under the service together with the highest severity state.

The **General Parameters** page contains the list of parameters with important information regarding the system.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
