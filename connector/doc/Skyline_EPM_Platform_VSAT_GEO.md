---
uid: Connector_help_Skyline_EPM_Platform_VSAT_GEO
---

# Skyline EPM Platform VSAT GEO

## About

The **Skyline EPM Platform VSAT GEO** is an Experience and Performance Management (EPM) Manager for VSAT circuits. It aggregates data from **iDirect Evolution Platform VSAT** and **Newtec Dialog Platform VSAT** collectors, providing centralized monitoring and management through the DataMiner Topology app.

A deployed EPM VSAT Solution contains one frontend element and can have one or multiple backend elements. The frontend element is responsible for top-level data aggregation from different backend elements. Each backend element is responsible for the aggregation of data from the collectors.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

1. **Frontend element**:

   - Set **Element Manager Type** to *Frontend*.
   - Configure the **Import** and **Export** directories for data files.

1. **Backend elements**:

   - Set directories for importing data from the frontend and exporting data to the collectors.

1. **Register IDs**:

   - Enter the necessary DMA IDs and Element IDs in the registration tables of frontend and backend elements.

## How to Use

Once the frontend and backend elements are created and configured, you can:

- Use the **Topology App** in DataMiner Cube to display the EPM VSAT topology chains and fields defined in the connector.
- Adjust configurations as needed using the settings on the **Configuration** page.
- Trigger the **Provision** button to start the import and export of all data files and add any new entities, notifying the backend elements.
- Use the **Reset** button to clear existing data from tables and execute provisioning logic to correct any erroneous data.

## Topologies

- **Network**: Network, Teleport, Hub Network, Hub Return, Hub Forward, Circuit
- **Service**: Network, Customer, Customer/NMS, Circuit
- **NMS**: Network, NMS, Hub Network, Hub Return, Hub Forward, Circuit
- **Map**: Network, NMS, Customer, Customer/NMS, Circuit
- **Quick**: Type, Network
- **Infrastructure**: NMS, PP Server, Chassis, Linecards

## Notes

The workflow involves collecting data files from the collectors, assigning IDs to entities, and then distributing this data to the backend elements for further processing. Backend elements use the imported data to update their datasets with the assigned IDs, enabling detailed monitoring and analysis of the VSAT network.

Ensure that import/export directories are set correctly to avoid data flow issues.
