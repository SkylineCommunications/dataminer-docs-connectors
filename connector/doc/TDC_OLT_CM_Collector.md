---
uid: Connector_help_TDC_OLT_CM_Collector
---

# TDC OLT CM Collector

## About

The **TDC OLT CM Collector** brings cable-modem and channel measurements from cable modems and Huawei MA5800-MA5633 equipment into your TDC CPE monitoring environment. Use the data to investigate service and signal-quality problems.

The collector works with the [TDC CPE Manager](xref:Connector_help_TDC_CPE_Manager), which brings the data together and provides the operator interface. It runs in the background rather than serving as a standalone monitoring interface.

## Key Features

- **Modem Health**: Review registration status, uptime, latency, and packet loss when investigating a modem's service.

- **Channel Measurements**: Collect power levels, modulation error ratio, and codeword statistics across QAM, OFDM, and OFDMA channels.

- **CPE Manager Integration**: View the collected data in your existing TDC CPE monitoring environment.

- **CSV Exports**: Choose which modem, interface, and channel measurements to export, and how long to keep the files.

- **Amplifier-Chain Mapping**: Link modem channels to their amplifier paths using data from the CPE backend manager.

## Use Cases

### Investigate Poor Modem Service

**Challenge**: A modem can remain registered even when signal problems affect its service.

**Solution**: Review its status alongside power levels, modulation error ratio, and codeword statistics in the CPE Manager.

**Benefit**: Get a clearer picture of the affected modem and channels before deciding what to investigate next.

### Investigate a Shared Amplifier Path

**Challenge**: It can be hard to tell whether channel problems on several modems share the same amplifier path.

**Solution**: Import amplifier-chain mappings from the CPE backend manager and view the associations in your existing views or dashboards.

**Benefit**: See which modems and channels share an amplifier path and narrow down the source of the problem.

### Supply Measurements to External Analysis

**Challenge**: External reporting or analysis needs selected measurements outside the live monitoring environment.

**Solution**: Choose the columns to export and collect the timestamped CSV files from the OLT folders.

**Benefit**: Make selected measurements available to your other workflows without extracting them by hand.

## Technical Reference

### Prerequisites

- A DataMiner release that meets the requirements for your connector version.
- A configured [TDC CPE Manager](xref:Connector_help_TDC_CPE_Manager) and a connection between the collector and the appropriate backend manager.
- Network and SNMP read access to the cable modems and Huawei MA5800-MA5633 equipment. Supported modem standards include DOCSIS 2.0, 3.0, and 3.1.
- Access to your CPE deployment's IAM provisioning database.
- A writable output folder and, if you use a network share, credentials with the necessary access.
- To use amplifier-chain mapping, AMP Chain export files from the CPE backend manager.

> [!NOTE]
> For connection settings, provisioning, CSV export configuration, and amplifier-chain import procedures, see the [technical documentation](xref:Connector_help_TDC_OLT_CM_Collector_Technical).
> 
