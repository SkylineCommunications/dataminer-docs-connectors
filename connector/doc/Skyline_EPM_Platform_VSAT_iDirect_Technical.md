---
uid: Connector_help_Skyline_EPM_Platform_VSAT_iDirect_Technical
---

# Skyline EPM Platform VSAT iDirect

## About

The **Skyline EPM Platform VSAT iDirect** is an Experience and Performance Management (EPM) Manager for VSAT circuits. It aggregates data from the **iDirect Evolution Platform VSAT** collector, providing centralized monitoring and management through the DataMiner Topology app.

A deployed EPM VSAT Solution contains one front-end element and can have one or multiple back-end elements. The front-end element is responsible for top-level data aggregation from different back-end elements. Each back-end element is responsible for the aggregation of data from the collectors.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

1. **Front-end element**:

   - Set **Element Manager Type** to *Frontend*.
   - Configure the **Import Path** and **Export Path** directories for data files. These same directories must be configured on all the elements of the EPM Solution.
   - If the **Import Path** or **Export Path** are in a remote location, fill in the **Username** and **Password** fields in the File Handling Credentials section of the **Configuration** page.
   - Add the **back-end** element IDs to the **Backend Registration** table.
   - Add the **front-end** element ID to the **Frontend Registration** table.
   - Add the **iDirect Evolution Platform VSAT** element IDs across the entire system to the **Collector Registration** table.

1. **Back-end elements**:

   - Set **Element Manager Type** to *Backend*.
   - Configure the **Import Path** and **Export Path** directories for data files. These same directories must be configured on all the elements of the EPM Solution.
   - If the **Import Path** or **Export Path** are in a remote location, fill in the **Username** and **Password** fields in the File Handling Credentials section of the **Configuration** page.
   - Add the **front-end** element ID to the **Frontend Registration** table.
   - Add the **iDirect Evolution Platform VSAT** element IDs, on the same DMA as the **back-end element**, to the **Collector Registration** table.

## How to Use

Once the front-end and back-end elements have been created and configured, you can:

- Use the **Topology App** in DataMiner Cube to display the EPM VSAT topology chains and fields defined in the connector.
- Adjust the configuration as needed using the settings on the **Configuration** page.
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
