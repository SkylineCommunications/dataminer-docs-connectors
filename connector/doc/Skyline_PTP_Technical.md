---
uid: Connector_help_Skyline_PTP_Technical
description: "Explore Skyline PTP technical documentation for DataMiner, including technical architecture, connections, data pages, and supported device connectors."
---

# Skyline PTP Technical

## About

The **Skyline PTP** connector is used as an application in the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) to monitor the different PTP devices in a network.

For range 2.0.0.x, monitoring and configuration are handled via the **PTP Monitor** custom web app. For range 1.0.0.x, a Visio file provides access to the functionality of the PTP Solution.

Starting with range 2.0.0.X, the Skyline PTP connector also introduces an **in-connector mediation** architecture that replaces the legacy Standard DataMiner PTP Device mediation protocol used ith the 1.0.0.x range.

Instead of relying on an external mediation protocol, the Skyline PTP connector communicates directly with remote vendor elements. It subscribes to parameter changes on monitored vendor devices, providing real-time data ingestion, reduced processing overhead, and higher scalability across complex PTP networks.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

This element should not be created manually:

- For range 2.0.0.x, creation is handled through the **PTP Monitor** web app.
- For range 1.0.0.x, creation is handled using the **PTP_SetupWizard** automation script.

For more information, refer to the [Initialization](#initialization) section below.

### Initialization

The initialization process depends on the connector range:

- **Range 2.0.0.x**: Configuration and domain setup are handled directly through the **PTP Monitor** web app (via the **Admin** page, using the **Add Domain** and **Role Assignment** wizards).

- **Range 1.0.0.x**: The configuration of the Skyline PTP application and the full DataMiner PTP Solution must be done using the PTP_SetupWizard and PTP_SetupWizard_Roles automation scripts:

  The **PTP_SetupWizard** script must be executed initially to configure the DataMiner PTP Solution. This script will:

  - Create the top view for the PTP Solution items.
  - Create the Skyline PTP element.
  - Execute the initial configuration of the Skyline PTP element.
  - Execute the PTP_SetupWizard_Roles automation script.

  - The **PTP_SetupWizard_Roles** script is used to configure the PTP devices and update this in the Skyline PTP element. This script is executed from the PTP_SetupWizard script once the initial configuration is done. However, it can also be manually executed later to update the PTP devices managed by the Skyline PTP application. The PTP_SetupWizard_Roles script will:

  - Configure the PTP devices in the Skyline PTP application with their respective roles.
  - Update the PTP Role element property on each PTP device added to the PTP Solution.
  - Create a PTP information template for each protocol that has at least one element added as PTP device in the Solution.

  When both of these scripts have been executed, the PTP Solution should be fully configured and the Skyline PTP element will start monitoring the PTP topology using range 1.0.0.x of this connector.

## How to use

For range 2.0.0.x, monitoring is done through the **PTP Monitor** web app. For more detailed information on how to use this web app, refer to [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp). For an overview of the data pages of the connector and a [list of supported connectors](#supported-ptp-connectors), refer to the text below.

For range 1.0.0.x, the data pages of the Skyline PTP element are not intended to be used directly. All the necessary data can be found on the Visual pages. For more information on how to use these pages, refer to the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) documentation.

### Supported PTP Protocols Page

**Table 7000 (Supported PTP Protocols)** defines all vendor protocols supported by the in-connector mediation engine, including their parameter mappings, supported clock types, and configuration rules. This table serves as the internal protocol registry used by the connector to handle incoming element data.

### Mediated Parameters Page

**Table 3000 (Mediated Parameters)** contains real-time PTP parameters collected per device:

- Clock identity and domain number
- PTP clock class, accuracy, and priority settings (Priority 1 and Priority 2)
- Offset from master and mean path delay
- Parent dataset information (parent clock identity, grandmaster identity, and grandmaster clock quality)
- Device communication and synchronization status

### Mediated Ports Page

**Table 3200 (Mediated Ports)** contains port-level PTP operational status and performance metrics for all monitored devices:

- Port identity and port number
- Port state (such as *Master*, *Follower*, *Passive*, *Listening*, or *Disabled*)
- Log message intervals (announce, sync, and delay request intervals)
- Peer mean path delay and delay mechanism

### Mediated Foreign Masters Page

**Table 3400 (Mediated Foreign Masters)** tracks foreign master records received by PTP ports on boundary clocks and follower devices:

- Foreign master clock identity
- Foreign master port number
- Number of announce messages received from the foreign master

### Mediated Transparent Clock Ports Page

**Table 3600 (Mediated Transparent Clock Ports)** contains operational parameters specific to transparent clock ports:

- Port identity and port state
- Log minimum delay request interval
- Peer mean path delay

## Supported PTP Connectors

This section is the **single definitive source of truth** for all vendor connectors supported by the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) and the Skyline PTP in-connector mediation engine.

The following table lists all supported vendor connectors:

| Connector |
|----------------------|
| ADVA Optical Networking OSA 5422 |
| Arista Manager |
| Arista eOS Manager |
| Bridge Technologies VB Probe Series |
| CISCO Nexus |
| directOut montone.42 |
| Evertz 5700MSC |
| Evertz 5700MSC - PTP Interface |
| Evertz DreamCatcher |
| Generic Edge Chassis |
| Generic Edge Chassis - PTP Card |
| Generic Switch |
| Hirschmann - a Belden Brand MAR 1040 |
| Imagine Communications Selenio Network Processor |
| Juniper Networks Manager |
| Lawo HD Core Ravenna |
| Lawo Power Core |
| Lawo V__matrix |
| Meinberg LANTIME IMS-HPS - PTPv2 Instance |
| Meinberg LANTIME IMS-HPS API V10 - PTPv2 Instance |
| Meinberg LANTIME IMS-PSX API V17 - PTPv2 Instance |
| Meinberg Lantime M3000 - PTPv2 Module |
| Mellanox Technologies MLNX-OS Manager |
| Pebble Beach Dolphin |
| Riedel Communications MediorNet MuoN (FusioN and VirtU) |
| Ross Video Iggy-AES16.16 |
| Ross Video Newt-IPR-3G-4S |
| Seiko Time Server Pro. TS-1550 |
| Seiko Time Server Pro. TS-2950 |
| Tektronix Prism |
| Tektronix SPG8000 - PTP Interface |
