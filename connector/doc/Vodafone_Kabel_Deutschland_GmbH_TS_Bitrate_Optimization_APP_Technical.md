---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_TS_Bitrate_Optimization_APP_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH TS Bitrate Optimization APP connector to calculate and adjust CISCO DCM bitrates in DataMiner."
---

# Vodafone Kabel Deutschland GmbH TS Bitrate Optimization APP

## About

The Vodafone Kabel Deutschland GmbH TS Bitrate Optimization APP connector calculates optimal bitrates and lets you adjust output transport stream bitrates on CISCO DCM devices.

## Configuration

### Prerequisites

This connector supports Corbaloc IIOP 1.1.

### Connections

No connection needs to be configured during element creation.

### Initialization

Once the element has been created, on the **General** page, fill in the CISCO DCM **IIOP credentials**, and specify the necessary devices in the **Devices Table**.

## How to Use

This connector is deployed as an app. This means that you can easily access it in Cube via the **Apps** pane of the sidebar.

The connector will poll all devices configured in the **Devices Table** (on the **General** page). All data will be parsed, and the **Streams** table (on the **Streams** page) will be populated with all CBR output streams.

For each output stream, the max bitrate will be shown, and an optimal bitrate will be calculated based on the **configuration settings**:

- **Bitrate Delta Setting [Value]**: Calculates the optimal bitrate by adding a fixed (Mbps) value to the maximum bitrate.
- **Bitrate Delta Setting [Percentage]**: Calculates the optimal bitrate by adding a percentage to the maximum bitrate.

The **Streams** table provides several options to manipulate the output stream bitrates, using buttons on the row level or using the context menu.
