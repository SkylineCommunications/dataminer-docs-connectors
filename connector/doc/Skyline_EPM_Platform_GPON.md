---
uid: Connector_help_Skyline_EPM_Platform_GPON
---

# Skyline EPM Platform GPON Connector

## About

The Skyline EPM Platform GPON connector is the back-end component of the Skyline EPM Solution for GPON infrastructures. It aggregates KPIs from multiple OLT platform elements, consolidating data for higher-level visualization and analysis in the Skyline EPM Platform front-end.

It supports integration with GPON OLT devices from multiple vendors, including ZTE, Huawei, and Nokia, and organizes the data into visual topologies for network navigation. This connector is designed to handle large volumes of GPON performance and topology data, making it suitable for large-scale deployments.

## Key Features

- **Back-End KPI Aggregation**: Collects and processes KPIs from GPON OLT platform elements for central aggregation.
- **Multi-Vendor OLT Support**: Compatible with ZTE ZXA10 C600, Huawei 5600-5800, and Nokia ISAM 7300 FX GPON platforms.
- **Visual GPON Topologies**: Displays GPON service hierarchy from network level down to ONTs, including Split Route, Split Distribution, and Split FAT.
- **Topology Provisioning**: Handles GPON topology and provisioning file exchange with the Skyline EPM Platform front-end.
- **Automated Workflow**: Supports automated data flow between OLTs, GPON back-end, and the EPM front-end.

## Use Cases

### Use Case 1

**Challenge**: Aggregating performance and topology data from multiple GPON OLT vendors.

**Solution**: Deploy the Skyline EPM Platform GPON connector as the GPON back-end component to collect and standardize KPI data.

**Benefit**: Provides a unified, vendor-agnostic performance view for GPON networks.

### Use Case 2

**Challenge**: Navigating and managing complex GPON network structures.

**Solution**: Use the connector’s visual topologies to explore the network hierarchy and understand the relationships between network, OLT, ports, and ONTs.

**Benefit**: Improves operational efficiency and accelerates troubleshooting.

### Use Case 3

**Challenge**: Keeping provisioning data synchronized across multiple systems.

**Solution**: Utilize the connector’s import/export functionality to manage GPON topology and provisioning file exchange between EPM components.

**Benefit**: Reduces configuration errors and ensures accurate, consistent network data.

## Technical Reference

### Prerequisites

- **Integration with Skyline EPM Platform front-end** for data aggregation and visualization.
- **Installed Automation Scripts**: `EpmBeToOlt` and `EpmBeToOltPassives` must be deployed.
- **Correctly configured file import/export paths** for topology and provisioning data.
- Access credentials for remote directories if using remote import/export.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_EPM_Platform_GPON_Technical).
