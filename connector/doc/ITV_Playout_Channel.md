---
uid: Connector_help_ITV_Playout_Channel
---

# ITV Playout Channel Service

The ITV Playout Channel Service protocol monitors the overall channel status of all ingress monitoring probes on every leg (red/blue/green A/green B) in the chain.

Channel Status Options:

- OK: no critical alarms present on any leg
- P1: highest priority = 3 or more different legs have critical alarms
- P2: 2 different legs have critical alarms
- P3: One of the legs has a critical alarm

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
|--|--|--|--|---|
| 1.0.0.x | No | Yes | - | - |

## Configuration

To create a service using this service protocol:

1. In DataMiner Cube, Navigate to **Apps** > **Service Templates**.
1. Select the Playout Channels Template *(Default: CHORD Playout Channels)*.
1. Click on **Apply** in the bottom action bar.
1. Press **Load**.
1. If the template requires input data such as the Name or Probe Element, the window will now ask to provide this information and continue.
1. A new Service will now be created based on the selected template automatically including this service protocol.

Alternatively, the Service Templates App allows you to 'bulk' import a set of services from an Excel-file. Please refer to the DataMiner Docs for more information on **Service Templates**.

## How to use

The **General** page contains the overall channel status.

The **Alarms** page contains display all active alarms for the included services and elements.

The **Elements** page displays the elements configured under the service together with the highest severity state.

The **General Parameters** page contains the list of parameters with important information regarding the system.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
