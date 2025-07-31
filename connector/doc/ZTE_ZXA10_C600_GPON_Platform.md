---
uid: Connector_help_ZTE_ZXA10_C600_GPON_Platform
---

# ZTE ZXA10 C600 GPON Platform Connector

## About

The ZTE ZXA10 C600 GPON Platform connector integrates with the ZXA10 C600 optical line terminal (OLT), a large-capacity optical access platform used in GPON networks. The connector uses SNMP to collect operational and configuration data, enabling centralized monitoring and integration with the Skyline EPM GPON solution.

This connector supports visibility into the OLT’s performance, connected optical network terminals (ONTs), and topology information for GPON deployments. It also facilitates interaction with external data sources, such as KAFKA streams, for retrieving ONT KPI data.

## Key Features

- **OLT Monitoring**: Monitors operational state, configuration, and performance metrics of the ZXA10 C600.
- **ONT Management**: Provides access to ONT status and key performance indicators within the GPON network.
- **Topology Integration**: Exports and imports topology configuration files for integration with the Skyline EPM GPON solution.
- **External Data Source Support**: Retrieves KPI data from sources such as KAFKA (in applicable versions).
- **Split Information Management**: Displays GPON split topology information, including route, distribution, and FAT segments (in latest connector versions).

## Use Cases

### Use Case 1

**Challenge**: Managing large-scale GPON deployments with many ONTs while ensuring network reliability.

**Solution**: Deploy the ZXA10 C600 connector to collect OLT and ONT metrics, integrating with the Skyline EPM GPON solution for aggregation and visualization.

**Benefit**: Improved network oversight, enabling faster fault detection and optimized maintenance.

### Use Case 2

**Challenge**: Need to keep GPON topology information synchronized across multiple systems.

**Solution**: Use the connector’s export/import capabilities to maintain up-to-date topology files between the OLT and EPM solution.

**Benefit**: Ensures consistent and accurate topology data for planning and operations.

### Use Case 3

**Challenge**: Efficiently processing ONT performance data from multiple sources.

**Solution**: Integrate the connector with external data feeds (e.g., KAFKA) to centralize ONT KPI collection and analysis.

**Benefit**: Provides a unified view of ONT health and performance across the GPON network.

## Technical Reference

### Prerequisites

- **ZTE ZXA10 C600 GPON OLT** running supported firmware (e.g., V1.1.2).
- **SNMP access** with appropriate community strings (default: `public` for GET, `private` for SET).
- **Integration with Skyline EPM GPON Solution** for topology aggregation and visualization (optional but recommended).
- Access credentials for remote directories if using remote export/import functionality.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ZTE_ZXA10_C600_GPON_Platform_Technical).
