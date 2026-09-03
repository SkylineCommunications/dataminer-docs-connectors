---
uid: Connector_help_Skyline_EPM_Platform_GPON
---

# Skyline EPM Platform GPON

## About

Skyline EPM Platform GPON is a virtual DataMiner connector that manages GPON EPM topology and CPE data. It turns collector-provided provisioning data into a consistent hierarchy of networks, markets, hubs, OLTs, slots, ports, ONTs, subscribers, and passive split entities.

## Key Features

- Deploys as either a Backend data-import element or a Frontend CPE-view element from the same connector.
- Imports GPON topology through configured CSV import and export paths.
- Coordinates provisioning work between elements through InterApp calls and a Frontend messaging buffer.
- Maintains reset state to remove stale topology data after a successful provisioning cycle.
- Calculates overview KPI percentages for GPON topology and passive entities.

## Use Cases

### Maintain a CPE-facing GPON topology view

**Challenge:** GPON provisioning data originates from multiple collector elements and must be presented as one navigable topology.

**Solution:** Deploy a Frontend element to coordinate requests and expose the CPE hierarchy.

**Benefit:** Operators can navigate from network to subscriber and passive-split data in a consistent EPM view.

### Consolidate collector provisioning data

**Challenge:** Raw provisioning data must be imported and retained before it can drive CPE topology views.

**Solution:** Deploy a Backend element to process collector data and populate backend topology tables.

**Benefit:** The provisioning workflow is separated from the Frontend presentation role while using one connector package.

## Technical Reference

This connector requires DataMiner `10.3.0.0 - 12752` or later and a GPON EPM deployment with the required collector, Backend, and Frontend elements. The technical reference describes configuration and operation: <xref:Connector_help_Skyline_EPM_Platform_GPON_Technical>.

The published technical page is maintained in the `dataminer-docs-connectors` repository and must be kept synchronized with this README's marketing content.
