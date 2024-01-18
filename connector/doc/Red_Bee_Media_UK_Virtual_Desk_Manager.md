---
uid: Connector_help_Red_Bee_Media_UK_Virtual_Desk_Manager
---

# Red Bee Media UK Virtual Desk Manager

The **Red Bee Media UK Virtual Desk Manager** provides an overview of the states of the **Desks**, **Groups** and **Services**, and how they are associated with each other.

## About

This driver is a monitoring tool that provides an overview of the follwowing:
  * **Desks** in a specified Playout view
  * **Services** assigned to the **Desks**
  * Unassigned **Services**

*Mininum supported DataMiner version: 10.1.11*

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|----------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main]   | Initial version | -                  | -                      |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         | RBM Con Booth Desk <br> RBM MCR Desk <br> Red Bee Media UK Service Alarm Channel <br> Red Bee Media UK Service Alarm Region <br> Skyline Booking Manager      | -  |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

This driver needs to be initialized by filling in the fields on the **Configuration** page.
  1. **Main Playout View** - Fill in the name of the selected view as shown in the **Surveyor** tab of the DataMiner Cube.
  2. **Unassigned Services View** - Fill in the name of the selected view as shown in the **Surveyor** tab of the DataMiner Cube.
  3. **Media Service Function Protocol** - Fill in the name of the Media Service Protocol has shown in the **Protocol & Templates** app of the DataMiner Cube.
  4. **Booking Manager** - Fill in the name of the element created using the **Skyline Booking Manager** protocol.

After that, toggle the **Configuration Status** parameter to **Configured** and press the **Reload Tables** button.

## How to use

Each page of the connector displays information on the **Desks**, **Groups** and **Services** in the views specified on the **Configuration** page.

### Desks

Provides information of the desks, their positions on the visual overview, desk type and assigned services.

### Groups

Provides information of the service groups and services associated with each group.

### Services

Provides information of the services and their desk assignments.

### Configuration

Allows the user to configure this connector using the instructions stated in the **Initialization** section above.
