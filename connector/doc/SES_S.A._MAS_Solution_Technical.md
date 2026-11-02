---
uid: Connector_help_SES_S.A._MAS_Solution_Technical
---

# SES S.A. MAS Solution Technical Documentation

The **SES S.A. MAS Solution** provides an integrated orchestration, monitoring, and reporting environment for SES Monitoring and Analysis Systems (MAS). This technical guide details system requirements, solution architecture, installation and configuration steps, the interactive migration workflow, DataMiner Connectivity Framework (DCF) matrix routing, and Cassandra storage compliancy.

## About

The SES Monitoring and Analysis Systems (MAS) framework manages complex satellite transmission chains. It interfaces with RF routing matrices, spectrum analyzers, digital video monitoring systems (DVMS), integrated receiver/decoders (IRDs), and IP multicast streaming equipment.

This solution package coordinates:
- Consolidated monitoring through the **SES S.A. MAS** protocol.
- Multi-format transmission path switching (SAT/DVB-S/S2, ASI, IF, L-Band, IP).
- Automated interactive migration from legacy numbered protocols (`SES S.A. MAS 1`, `SES S.A. MAS 2`, and `SES S.A. MAS 3`).
- IRD control and PID tuning for MediaKind RX8200 and Sencore MRD6000 decoders.
- Ad hoc query analytics via the Generic Query Interface (GQI) and Low-Code Apps.

## Configuration & Deployment

### Package Installation
The solution is deployed as a DataMiner Application Package (`.dmapp`). On package installation :
1. Included protocols are installed (`SES S.A. MAS`).
2. Default solution contents (Automation scripts, Low-Code Apps, Dashboards, and Visio drawings) are unpacked and installed.
3. The custom installer script executes `SetProtocolsToProduction` to ensure the target protocol (`SES S.A. MAS`) is placed into active production.

> [!NOTE]
> On every installation of the script the elements using protocol `SES S.A. MAS` will restart.

### Visual Overview Deployment

Visual overview files are:
- `SES S.A. MAS MediaKind.vsdx`
- `SES S.A. MAS Sencore.vsdx`

Assign the appropriate Visio file to the MAS element depending on whether the linked primary IRD is a MediaKind or Sencore device.

### Connections

#### Protocol Connection — SES S.A. MAS
The `SES S.A. MAS` protocol operates as a virtual supervisory driver coordinating linked hardware elements.

#### Linked Hardware Elements
Hardware devices (matrix switches, spectrum analyzers, DVMS units, and IRDs) are managed by their respective dedicated DataMiner connectors and linked to the MAS element via **Table 1100 (Linked Elements)**:
- **Spectrum Analyzer**: SNMP or Smart-Serial driver.
- **DVMS Analyzer**: Digital Video Monitoring System driver (SNMP/HTTP).
- **Primary IRD**: MediaKind RX8200 / Ericsson RX8200 or Sencore MRD6000 driver.
- **RF Matrix Routers**: Matrix switch drivers for IF, L-Band, ASI, and SDI routing.

### Initialization & Setup
1. **Assign Linked Elements (Table 1100)**: Configure the element references (`dmaId/elementId`) for the assigned Spectrum Analyzer, DVMS, IRD, and Matrix Routers.
2. **Channel List Configuration**: Enter the Channel URL, Channel User, and Channel Password to permit automated channel preset retrieval.
3. **Delay Times (Table 1200)**: Configure operational delay offsets for matrix switching and hardware lock stabilization.

### Automation Scripts Catalog
- **`SES S.A. MAS Migration`**: Interactive script orchestrating the migration and consolidation of legacy MAS elements into the `SES S.A. MAS` protocol.
- **`Change Mode MAS`**: Switches operational modes between Satellite, ASI, IF, L-Band, and IP, triggering cross-point and IRD adjustments.
- **`Manual Settings MAS`**: Manages manual override settings for matrix input ports and RF configurations.
- **`Set ASI Mode MAS`, `Set IF Mode MAS`, `Set LBand Mode MAS`**: Targeted mode switching scripts for specific RF and transport feeds.
- **`Set Multicast MAS` & `Set Multicast From LCA`**: Configures destination multicast IP addresses and instances from the *SES - Multicasts* Low-Code App.
- **`SES S.A. MAS MediaKind Sets` & `SES S.A. MAS Sencore Sets`**: Sends tuning and demodulation commands to MediaKind RX8200 and Sencore MRD6000 IRDs.
- **`Sencore Video PID set`**: Updates targeted video, audio, and PCR PIDs on Sencore decoders.
- **`MAS Report Generator`**: Executes scheduled or on-demand report exports.

## Migration Workflow (SES S.A. MAS Migration)

The `SES S.A. MAS Migration` Interactive Automation Script (IAS) safely transitions elements from legacy numbered protocols (`SES S.A. MAS 1`, `SES S.A. MAS 2`, `SES S.A. MAS 3`) to the unified `SES S.A. MAS` production driver.

### Workflow Stages
1. **Discovery**:
   The script queries the DataMiner Agent for active elements matching `SES S.A. MAS 1..3` (excluding elements already bearing the `_OLD` suffix).
2. **Concurrency Guard**:
   An internal lock registry prevents duplicate or overlapping migrations for the same element.
3. **Pre-flight Checks**:
   - Confirms element reachability in the DataMiner System.
   - Verifies the production version of `SES S.A. MAS` is installed and ready.
4. **Configuration Snapshot & Backup**:
   - Captures all operational values: Table 1100 (Element Assignments), Table 1200 (Delay Times), Channel URLs/credentials, Matrix cross-points, Spectrum presets, and Visio bindings.
   - Stops the original element and renames it to `<OriginalName>_OLD` to serve as an immediate fallback backup.
5. **New Element Creation & Data Transfer**:
   - Creates a new element with the original name running the consolidated `SES S.A. MAS` protocol.
   - Re-applies all captured configuration tables, channel settings, presets, and view assignments.
6. **Parity Verification**:
   The script runs comprehensive parity comparisons between original and migrated settings:
   - *General Settings*: URL IRD, IRD Protocol.
   - *Table 1100*: Spectrum Analyzer, DVMS, IRD, and Matrix element linkages.
   - *Table 1200*: Mode-specific delay offsets.
   - *Channel Settings*: URL Channel, credentials.
   - *Matrix Parameters*: Downlink L-Band, ASI, ACF34, SDI, IF, Uplink L-Band inputs/outputs.
   - *Spectrum Parameters*: Presets, bandwidth factor, amplitude scale, resolution/video bandwidth, trace colors.
   - *Visual Settings*: Visio drawing assignment.
7. **Rollback Safeguard**:
   If an error occurs or parity fails, the script removes the partial new element, restarts the `<OriginalName>_OLD` backup, restores its original name, and logs diagnostic details.

## DataMiner Connectivity Framework (DCF)

The solution models RF matrix switching, demodulation, and baseband routing using DCF interfaces.

> [!NOTE]
> DCF requires DataMiner version **10.1.0** or higher. The minimum DataMiner version for this package is **10.4.0.0 - 14003**.

## Notes

- **Channel List Password**: When executing migrations via the `SES S.A. MAS Migration` script, the operator is prompted for the channel list download password to authenticate against the secure channel CSV repository.
- **Spectrum Analyzer Auto Parameters**: Video bandwidth, resolution bandwidth, sweep time, and input attenuation support "Auto" presets. The GQI reporting layer automatically resolves active values when "Auto" is enabled.
- **Concurrent Execution Guard**: A single MAS element cannot undergo multiple simultaneous migrations. If a migration is triggered while another is active, the operation will be rejected.
