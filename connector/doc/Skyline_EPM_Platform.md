---
uid: Connector_help_Skyline_EPM_Platform
---

# Skyline EPM Platform

## About

The Skyline EPM Platform connector is the front-end component of the Skyline EPM Solution, designed for Experience and Performance Management across DOCSIS and GPON infrastructures. It aggregates KPIs from multiple collector and back-end elements, consolidating large volumes of operational and performance data into a single, unified view.

It provides visual topologies for DOCSIS and GPON networks, showing the hierarchy of network elements from high-level network views down to detailed device-level insights. This enables operators to quickly navigate and analyze performance across complex infrastructures.

## Key Features

- **Centralized KPI aggregation**: Collects and consolidates KPIs from DOCSIS and GPON back-end elements.
- **Visual network topologies**: Displays DOCSIS and GPON hierarchical network views, including quick navigation options.
- **DOCSIS and GPON quick access**: Provides fast access to key topology levels using filter-based quick views.
- **Topology export/import**: Manages topology data exchange with back-end elements for provisioning and synchronization.
- **Integration with external data**: Supports KPI collection from various back-end systems, including passives and KAFKA data sources.

## Use Cases

### Use Case 1

**Challenge**: Aggregating performance metrics from multiple DOCSIS and GPON monitoring systems.

**Solution**: Deploy the Skyline EPM Platform connector as the central front-end element to collect and organize KPIs from multiple sources.

**Benefit**: Provides a unified performance view, enabling faster network issue detection and resolution.

### Use Case 2

**Challenge**: Navigating large and complex DOCSIS or GPON topologies.

**Solution**: Use the connector's built-in visual overviews and quick access filters to navigate from high-level topology views to individual devices.

**Benefit**: Improves operational efficiency and speeds up troubleshooting.

### Use Case 3

**Challenge**: Keeping topology and provisioning data consistent across multiple systems.

**Solution**: Utilize the connector's export/import capabilities to synchronize topology and provisioning data between the front-end and back-end elements.

**Benefit**: Reduces configuration errors and ensures data accuracy across the network.

## Technical Reference

### Prerequisites

- **Integration with Skyline EPM back-end elements** for DOCSIS and GPON data collection.
- **Correctly configured file import/export paths** for topology and provisioning data sharing.
- **automation scripts and correlation rules** for handling message-based data exchange.
- Access credentials for remote directories if using remote export/import functionality.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_EPM_Platform_Technical).
