---
uid: Connector_help_Telestream_Argus_Probe
---

# Telestream Argus Probe

The **Telestream Argus Probe** is a management system for OTT/multi-screen adaptive streaming. The Argus Probe module will list all the connected probes with their respective data. Alarm monitoring and trending can be used to keep track of the probes, assets, streams, alarms, and their data. For easier navigation, a Visual Overview layer is available for this connector.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] |initial version| - | - |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | - | - [Telestream Argus Probe - Inspector Probe](xref:Connector_help_Telestream_Argus_Probe_-_Inspector_Probe) <br>- [Telestream Argus Probe - Surveyor ABR Probe](xref:Connector_help_Telestream_Argus_Probe_-_Surveyor_ABR_Probe) <br>- [Telestream Argus Probe - IQDialogue Probe](xref:Connector_help_Telestream_Argus_Probe_-_IQDialogue_Probe) |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When the element has been created, specify the **Username** and **Password** on the **General** page so that the connector can retrieve all the probes, assets, streams, and alarms info.

## How to use

In this range, the DVEs **Inspector Probe**, **Surveyor ABR Probe**, and **IQDialogue Probe** are available. These DVEs can be configured on the **Probes** page and **DVE Options** subpage.
