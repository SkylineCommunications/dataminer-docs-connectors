---
uid: Connector_help_Newtec_Dialog_Inventory
---

# Newtec Dialog Inventory

## About

The **Newtec Dialog Inventory** connector provides comprehensive visibility into the hardware and virtual infrastructure of the Newtec Dialog VSAT platform. It communicates with Network Management Systems (NMS) of types **4IF**, **XIF** and **NIF** via **DataMiner Web Services** to collect, organize, and display configuration items (CIs) such as modulators, demodulators, and other network infrastructure components. This connector integrates with ServiceNow to provide enhanced capabilities in monitoring and provisioning.

Leveraging an intuitive **TreeControl** interface, the connector reflects the hierarchical structure of these CIs, enabling seamless monitoring and inventory tracking.

## Key Features

- **NMS Integration**: Connects to different Dialog NMS types (4IF, XIF, NIF) for centralized data collection.

- **CI Inventory with TreeControl**: Presents collected CIs in a structured, expandable tree layout for enhanced visibility.

- **Real-Time Polling**: Polls system components via DataMiner Web Services for updated inventory and status.

- **Data Aggregation Across Layers**: Unifies data from hub enclosures, segments, virtual machines, and more.

## Use Cases

### Use Case 1: Centralized Infrastructure Management

**Challenge**: Managing dispersed NMS systems over the cloud without needing direct access into NMS.

**Solution**: The connector unifies communication with 1IF, 4IF, and XIF systems, enabling a centralized view.

**Benefit**: Simplified management and faster response to infrastructure changes or issues.

### Use Case 2: CI Visualization and Auditing

**Challenge**: Difficulty understanding the hierarchy and relationships between system components.

**Solution**: The TreeControl view organizes all CIs in a clear, browsable tree format.

**Benefit**: Improved situational awareness and simplified auditing of platform assets.

### Use Case 3: Data Aggregation Across Layers

**Challenge**: Gaps in visibility across different CIs of the Dialog platform.

**Solution**: Unifies data collection from physical and virtual components including hub enclosures, processing segments, servers, and VMs.

**Benefit**: Provides a holistic view of the infrastructure, ensuring better monitoring, analysis, and decision-making.

## Technical Reference

### Prerequisites

- **DataMiner Platform** with Web Services enabled is required for connector communication.

- **Newtec Dialog NMS** instances (4IF, XIF or NIF) must be accessible via network.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Newtec_Dialog_Inventory_Technical).

