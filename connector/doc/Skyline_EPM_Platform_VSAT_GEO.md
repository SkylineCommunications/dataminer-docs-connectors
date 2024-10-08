---
uid: Connector_help_Skyline_EPM_Platform_VSAT_GEO
---

# Skyline EPM Platform VSAT GEO

The **Skyline EPM Platform VSAT GEO** is an Experience and Performance Management (EPM) Manager for VSAT circuits. 
It aggregates data from **iDirect Evolution Platform VSAT** and **Newtec Dialog Platform VSAT** collectors, providing 
centralized monitoring and management through the DataMiner Topology app.

A deployed EPM VSAT Solution contains one front-end element and can have one or multiple back-end elements. 
The front-end element is responsible for top-level data aggregation from different back-end elements. Each back-end 
element is responsible for the aggregation of data from the collectors.

### Topologies

- **Network**: Network, Teleport, Hub Network, Hub Return, Hub Forward, Circuit
- **Service**: Network, Customer, Customer/NMS, Circuit
- **NMS**: Network, NMS, Hub Network, Hub Return, Hub Forward, Circuit
- **Map**: Network, NMS, Customer, Customer/NMS, Circuit
- **Quick**: Type, Network
- **Infrastructure**: NMS, PP Server, Chassis, Linecards

## About

### Version Info

| Range              | Features | Based on | System Impact |
|--------------------|----------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version, supports iDirect and Newtec Dialog collectors. | - | - |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

1. **Front-end Element**:
   - Set **Element Manager Type** to *Frontend*.
   - Configure **Import** and **Export** directories for data files.

2. **Back-end Elements**:
   - Set directories for importing data from the front-end and exporting data to the collectors.

3. **Register IDs**:
   - Input necessary DMA IDs and Element IDs in the registration tables of front-end and back-end elements.

### Redundancy

No redundancy is defined.

## How to Use

Once the front-end and back-end elements are created and configured, users can:

- Use the **Topology App** in the DataMiner Cube to display the EPM VSAT topology chains and fields defined in the connector.
- Adjust configurations as needed using the provided settings on the **Configuration** page.
- Trigger the **Provision** button to start the import and export of all data files and add any new entities, notifying the back-end elements.
- Use the **Reset** button to clear existing data from tables and execute provisioning logic to correct any erroneous data.

## Notes

- The workflow involves collecting data files from the collectors, assigning IDs to entities, and then distributing this data 
to the back-end elements for further processing.
- Back-end elements use the imported data to update their datasets with the assigned IDs, enabling detailed monitoring 
and analysis of the VSAT network.
- Ensure that import/export directories are set correctly to avoid data flow issues.
