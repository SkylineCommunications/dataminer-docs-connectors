---
uid: Connector_help_Red_Bee_Media_UK_Virtual_Desk_Manager
---

# Red Bee Media UK Virtual Desk Manager

The **Red Bee Media UK Virtual Desk Manager** provides an overview of the states of the **desks**, **groups**, and **services**, and how they are associated with each other.

It provides an overview of:

- **Desks** in a specified playout view
- **Services** assigned to the **desks**
- Unassigned **services**

## About

> [!IMPORTANT]
> Minimum supported DataMiner version: 10.1.11

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | RBM Con Booth Desk <br>RBM MCR Desk<br>Red Bee Media UK Service Alarm Channel<br>Red Bee Media UK Service Alarm Region<br>Skyline Booking Manager | - |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To initialize the connector, first fill in the following fields on the **Configuration** page:

- **Main Playout View**: Fill in the name of the selected view as shown in the **Surveyor** in DataMiner Cube.

- **Unassigned Services View**: Fill in the name of the selected view as shown in the **Surveyor** in DataMiner Cube.

- **Media Service Function Protocol**: Fill in the name of the media service protocol has shown in the **Protocol & Templates** module in DataMiner Cube.

- **Booking Manager**: Fill in the name of the element created using the **Skyline Booking Manager** protocol.

After that, toggle the **Configuration Status** parameter to *Configured* and click the **Reload Tables** button.

## How to use

The pages of the connector display information about the **desks**, **groups**, and **services** in the views specified on the **Configuration** page.

- **Desks** page: Provides information about the desks, their positions on the visual overview, their desk type, and assigned services.
- **Groups** page: Provides information about the service groups and services associated with each group.
- **Services** page: Provides information about the services and their desk assignments.
- **Configuration** page: Allows you to configure the connector. See [Initialization](#initialization).
