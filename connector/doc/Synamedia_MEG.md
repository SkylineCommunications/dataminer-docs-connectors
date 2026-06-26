---
uid: Connector_help_Synamedia_MEG
---

# Synamedia MEG

## About

The Synamedia MEG (Media Edge Gateway) is a software-based platform for professional broadcast signal processing, multiplexing, and content delivery. This DataMiner connector integrates with the MEG via its REST API and Prometheus metrics endpoint, giving operators centralized visibility and control over transport streams, services, sources, and conditional access systems — all within the DataMiner ecosystem.

## Key Features

- **Full transport stream lifecycle management**: Monitor and configure input and output transport streams across all supported protocols, including SRT, Zixi, RIST, RTMP, ASI, and Xgress, with access to settings for FEC, VLAN, RIP, scrambling, and auto-pass rules.
- **Service-level monitoring and control**: View detailed data for input and output services, including PID compositions, scrambling state, component tracking rules, service backup settings, and alternate routing configurations.
- **Real-time performance data**: Collect bitrate, packet loss, jitter, round-trip time, and error rate metrics via both the REST API and a dedicated Prometheus connection, covering sources, transport streams, SRT sessions, and Zixi channels.
- **Configurable poll manager**: Control polling frequency and enable or disable individual API commands through an interactive polling configuration table, with support for forced-enabled commands and firmware-version gating.
- **InterApp integration**: Expose a structured API to other DataMiner connectors and automation scripts for programmatic creation, editing, and deletion of sources, output transport streams, output services, and associated components.
- **Conditional access and scrambling oversight**: Monitor and configure ECMg connections, SCS global settings, and per-service/per-TS scrambling parameters, including algorithm selection, session words, and descriptor rules.

## Use Cases

### Centralized Monitoring of Broadcast Signal Chains

**Challenge**: Operations teams managing large MEG deployments need a single pane of glass to track the health of every input source, transport stream, and output service without logging into each device individually.

**Solution**: The connector populates a hierarchical tree control in DataMiner that mirrors the MEG's board, port, folder, source, and service topology. Alarm monitoring on key parameters — connection status, service loss, bitrates, and packet errors — surfaces issues automatically.

**Benefit**: Operators reduce mean time to detect by correlating MEG alarms with the rest of the broadcast chain inside DataMiner, eliminating context switching and manual log review.

### Automated Service Provisioning via DataMiner Automation

**Challenge**: Provisioning new transport streams or output services on the MEG is time-consuming when done manually, and error-prone when repeated across multiple nodes in a network.

**Solution**: The connector's InterApp interface exposes typed request/response messages for creating, editing, and deleting sources, output transport streams, and output services. DataMiner Automation scripts or Orchestration workflows can call these operations directly and receive structured confirmation responses.

**Benefit**: Provisioning workflows that previously required manual configuration steps can be fully automated, reducing operational overhead and ensuring consistent configuration across all MEG instances.

### Performance Benchmarking and SLA Reporting

**Challenge**: Proving SLA compliance for contribution and distribution streams requires continuous collection of bitrate, packet loss, and error metrics, which are not natively stored in long-term trend databases by the device itself.

**Solution**: The connector retrieves per-source and per-TS bitrate data from both the REST API and the Prometheus endpoint, storing current, average, minimum, and maximum values in dedicated trending tables. SRT and Zixi channel statistics — including retransmitted packets, FEC recovery, buffer levels, and round-trip times — are captured separately for deeper analysis.

**Benefit**: DataMiner trending and reporting capabilities provide the historical data needed for SLA reporting, capacity planning, and protocol performance comparisons without additional third-party tooling.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.0.0 or higher** is required to deploy this connector.
- **Network connectivity** to the MEG management interface on the configured HTTP(S) port (default: 8443) is needed for REST API polling and configuration sets.
- **Prometheus endpoint access** on the configured port (default: 9123) is required to collect real-time performance metrics for sources, transport streams, SRT sessions, and Zixi channels.
- **Valid API credentials** (username and password) with sufficient permissions on the Synamedia MEG are required to authenticate and execute GET and PUT/POST/DELETE operations.

### Supported Protocols and Technologies

The connector supports monitoring and configuration of transport streams using the following output and input protocol types:

| Protocol | Direction |
|---|---|
| Xgress (IP) | Input / Output |
| SRT | Input / Output |
| Zixi | Input / Output |
| RIST | Input / Output |
| RTMP | Output |
| DEPI | Output |
| ASI | Input / Output |
| ST 2110 | Input |
| SDI / SDI 2022-6 | Input / Output |
| DVB-S/S2 | Input |

### Connection Configuration

The connector uses two connections:

- **HTTP Connection** — Primary REST API connection to the MEG management interface.
- **HTTP Connection - Prometheus** — Secondary connection to the Prometheus metrics scrape endpoint for real-time performance data.

Both connection addresses, ports, and credentials are configured at element creation time in DataMiner.