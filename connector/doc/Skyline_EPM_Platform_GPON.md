---
uid: Connector_help_Skyline_EPM_Platform_GPON
description: "Learn how to use the Skyline EPM Platform GPON connector to manage GPON topology, CPE data, and provisioning workflows."
---

# Skyline EPM Platform GPON

## About

Skyline EPM Platform GPON is a virtual DataMiner connector that manages GPON EPM topology and CPE data. It turns collector-provided provisioning data into a consistent hierarchy of networks, markets, hubs, OLTs, slots, ports, ONTs, subscribers, and passive split entities.

## Key Features

- Deploys as either a backend data import element or a frontend CPE view element from the same connector.
- Imports GPON topology through configured CSV import and export paths.
- Coordinates provisioning work between elements through InterApp calls and a frontend messaging buffer.
- Maintains reset state to remove stale topology data after a successful provisioning cycle.
- Calculates overview KPI percentages for GPON topology and passive entities.

## Use Cases

### Maintain a CPE-Facing GPON Topology View

**Challenge**: GPON provisioning data originates from multiple collector elements and must be presented as one navigable topology.

**Solution**: Deploy a frontend element to coordinate requests and expose the CPE hierarchy.

**Benefit**: Operators can navigate from network to subscriber and passive-split data in a consistent EPM view.

### Consolidate Collector Provisioning Data

**Challenge**: Raw provisioning data must be imported and retained before it can drive CPE topology views.

**Solution**: Deploy a backend element to process collector data and populate backend topology tables.

**Benefit**: The provisioning workflow is separated from the frontend presentation role while using one connector package.

## Prerequisites

- DataMiner **10.3.0.0 - 12752** or higher
- A GPON EPM deployment with the required collector, backend, and frontend elements.

## Technical Reference

You can find more detailed information on the configuration and operation of this connector in our [technical documentation](xref:Connector_help_Skyline_EPM_Platform_GPON_Technical).
