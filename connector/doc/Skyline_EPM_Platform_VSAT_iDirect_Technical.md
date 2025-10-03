---
uid: Connector_help_Skyline_EPM_Platform_VSAT_iDirect_Technical
---

# Skyline EPM Platform VSAT iDirect – Technical Documentation

## About

The **Skyline EPM Platform VSAT iDirect** is an Experience and Performance Management (EPM) Manager for VSAT circuits. It aggregates data from **iDirect Evolution Platform VSAT** collector, providing centralized monitoring and management through the DataMiner Topology app.

A deployed EPM VSAT Solution contains one front-end element and can have one or multiple back-end elements. The front-end element is responsible for top-level data aggregation from different back-end elements. Each back-end element is responsible for the aggregation of data from the collectors.
### Version Info

| Range              | Features                                                        | Based on | System Impact |
|--------------------|-----------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. 											   | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
## Configuration

### Connections

#### Virtual Connection
This connector uses a virtual connection and does not require any input during element creation.

### Initialization

1. **Front-end element**:

   - Set **Element Manager Type** to *Frontend*.
   - Configure the **Import Path** and **Export Path** directories for data files. These same directorys must be configured on all the elements of the EPM Solution
   - If the **Import Path** or **Export Path** are in a remote location, fill in the **Username** and **Password** fields in the File Handling Credentials section of the **Configuration** page.
   - Add the **Back-End** element ids to the **Backend Registration** table.
   - Add the **Front-End** element id to the **Frontend Registration** table.
   - Add the **iDirect Evolution Platform VSAT** element ids across the entire system to the **Collector Registration** table.

2. **Back-end elements**:
   - Set **Element Manager Type** to *Backend*.
   - Configure the **Import Path** and **Export Path** directories for data files. These same directorys must be configured on all the elements of the EPM Solution
   - If the **Import Path** or **Export Path** are in a remote location, fill in the **Username** and **Password** fields in the File Handling Credentials section of the **Configuration** page.
   - Add the **Front-End** element id to the **Frontend Registration** table.
   - Add the **iDirect Evolution Platform VSAT** element ids, on the same DMA as the **Back-end element**, to the **Collector Registration** table.

## How to Use

Once the front-end and back-end elements are created and configured, you can:

- Use the **Topology App** in DataMiner Cube to display the EPM VSAT topology chains and fields defined in the connector.
- Adjust configurations as needed using the settings on the **Configuration** page.
- Trigger the **Reset** button to start the import and export of all data files and add any new entities, while cleaning up any old or erroneous data.

## Topologies

- **Network**: Network, Teleport, Hub Network, Hub Return, Hub Forward, Circuit
- **Service**: Network, Customer, Customer/NMS, Circuit
- **NMS**: Network, NMS, Hub Network, Hub Return, Hub Forward, Circuit
- **Map**: Network, NMS, Customer, Customer/NMS, Circuit
- **Quick**: Type, Network
- **Infrastructure**: NMS, PP Server, Chassis, Linecards

## Notes

The workflow involves collecting data files from the collectors, assigning IDs to entities, and then distributing this data to the back-end elements for further processing. Back-end elements use the imported data to update their datasets with the assigned IDs, enabling detailed monitoring and analysis of the VSAT network.

Ensure that import/export directories are set correctly to avoid data flow issues.
