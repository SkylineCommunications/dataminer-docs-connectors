---
uid: Connector_help_Skyline_EPM_Platform_VSAT_iDirect
---

# Skyline EPM Platform VSAT iDirect

## About

The **Skyline EPM Platform VSAT iDirect** connector enables end‑to‑end monitoring and management of iDirect‑based VSAT networks within DataMiner. It consolidates data from multiple collectors to expose KPIs and large volumes of operational and performance data into a single, unified view.

## Key Features

- **Centralized KPI aggregation**: Aggregates key remote and service metrics (e.g. Rx/Tx power, carrier utilization, errors) from collectors.
- **Visual network topologies**: Displays total network topology views, including trending and alarming at the topology level.
- **Scalable operations**: Designed for large fleets with bulk updates, provisioning helpers, and efficient polling.
- **Trending & reporting**: Supports long‑term trending as well as dashboards and scheduled reports.

## Use Cases

### Use Case 1

**Challenge**: Operators need real-time visibility on VSAT terminal RF performance and carrier quality across large fleets.

**Solution**: Aggregate KPI metrics from iDirect Connectors (Rx/Tx OTA Traffic, Symbol Rate, C/N), and trigger alarms when thresholds are crossed.

**Benefit**: Faster detection of degradations and SLA breaches, as well as reduced mean time to resolution.

### Use Case 2

**Challenge**: Capacity planning requires historical trends across networks.

**Solution**: Aggregate historical trending for RX/TX carriers, networks, teleports, and remotes. Export views to dashboards and reports.

**Benefit**: Evidence-based planning and optimized bandwidth allocation.

### Use Case 3

**Challenge**: Navigating large topologies and keeping provisioning data consistent across multiple systems.

**Solution**: Utilize the connector's export/import capabilities to synchronize topology and provisioning data between the front-end and back-end elements.

**Benefit**: Reduces configuration errors and ensures data accuracy across the network

## Technical Reference

### Prerequisites

- **Integration with iDirect Platform VSAT Collector** for iDirect data collection across DMAs.
- **Access credentials** for remote directories if remote export/import functionality is used.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_EPM_Platform_VSAT_iDirect_Technical).
