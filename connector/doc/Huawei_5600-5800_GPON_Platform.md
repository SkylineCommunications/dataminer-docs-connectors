---
uid: Connector_help_Huawei_5600-5800_GPON_Platform
---

# Huawei 5600-5800 GPON Platform Connector

## About

The Huawei 5600-5800 GPON Platform connector integrates with Huawei OLT devices in the 5600 and 5800 series used in GPON networks. It communicates with the devices via SNMP to collect operational, configuration, and performance data. This information is centralized for monitoring and integrated with the Skyline EPM GPON solution for aggregation and visualization.

The connector provides insight into the health and status of the OLT, connected ONTs, and the GPON network topology. It supports external data integration for ONT KPIs and includes functionality for exporting and importing topology configurations.

## Key Features

- **OLT Monitoring**: Tracks operational status, configuration parameters, and key performance metrics of Huawei 5600/5800 OLTs.
- **ONT Management**: Displays ONT status and retrieves KPIs from internal or external sources (e.g., KAFKA).
- **Topology Export/Import**: Synchronizes GPON topology data with the Skyline EPM GPON solution.
- **Enhanced Split Topology**: Separates GPON split information into route, distribution, and FAT segments for clearer network visualization.
- **Customizable Polling**: Configurable intervals for fast, slow, and virtual polling to optimize performance.

## Use Cases

### Use Case 1

**Challenge**: Monitoring large-scale GPON deployments and maintaining service quality.

**Solution**: Use the Huawei 5600-5800 GPON connector to collect real-time data from OLTs and ONTs, integrating with the Skyline EPM GPON solution for centralized visibility.

**Benefit**: Enables proactive fault detection, reduced downtime, and improved service reliability.

### Use Case 2

**Challenge**: Keeping GPON topology synchronized between systems.

**Solution**: Leverage the connector’s export/import capabilities to maintain accurate and consistent topology information across the network.

**Benefit**: Improves network planning, reduces configuration errors, and ensures operational consistency.

### Use Case 3

**Challenge**: Efficiently processing ONT KPI data from multiple sources.

**Solution**: Integrate the connector with external systems, such as KAFKA, for centralized ONT KPI retrieval and analysis.

**Benefit**: Delivers a unified view of ONT performance and facilitates faster issue resolution.

## Technical Reference

### Prerequisites

- **Huawei 5600 or 5800 GPON OLT** running supported firmware.
- **SNMP access** with correct community strings (default: `public` for GET, `private` for SET).
- **Integration with Skyline EPM GPON Solution** for topology aggregation and visualization (optional but recommended).
- Credentials for remote directories if using remote export/import functionality.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Huawei_5600-5800_GPON_Platform_Technical).
