---
uid: Connector_help_Skyline_PTP
description: "Discover how to use the Skyline PTP connector to monitor PTP network topologies, grandmasters, and clock synchronization in DataMiner."
---

# Skyline PTP

## About

The **Skyline PTP** connector is used as part of the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) to monitor the different PTP devices in a network.

## Key Features

- **Real-time synchronization health**: Instant tracking of active grandmaster status, BMCA parameters, lock states, and probe metrics (Offset from Master and Mean Path Delay).
- **Focused dual-scope alarm triage**: Distinct filtering between general device hardware alarms and dedicated PTP timing alarms for rapid root cause isolation.
- **Proactive configuration comparison**: Side-by-side node parameter comparisons that immediately highlight drift and mismatches.
- **Interactive DCF network topology**: Dynamic visualization of PTP hierarchy and DataMiner Connectivity Framework (DCF) signal paths with live drag-and-drop node positioning.
- **Multi-domain operational agility**: Seamless switching and independent tracking across multiple PTP domains from a single interface.

## Use Case: End-to-End Timing and Synchronization Observability

- **Challenge**: In all-IP broadcast production environments, clock synchronization is mission-critical. Modern PTP infrastructures face major operational hurdles, such as architectures spanning devices from diverse vendors, each with proprietary management tools, general hardware alarms obscuring critical PTP timing issues, subtle configuration mismatches, and dependency on desktop client installations, limiting accessibility for distributed engineering and NOC teams.

- **Solution**: DataMiner PTP addresses these challenges by replacing legacy client-bound setups with a browser-native web application deployed directly on DataMiner. Supported by in-connector mediation, the solution monitors devices out of the box without requiring intermediate mediation connectors.

## Technical Reference

For technical parameters and the supported connectors list, refer to the [Skyline PTP Technical](xref:Connector_help_Skyline_PTP_Technical) page.

For more information on the PTP Solution, refer to the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) documentation.
