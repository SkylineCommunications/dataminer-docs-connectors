---
uid: Connector_help_Red_Bee_Media_Playout_Desk
---

# Red Bee Media Playout Desk

This connector is intended to be used with the Rbm_playout DOM module. It has a configurable DOM instance (for the Playout Desk definition). Based on the instance of the Desk, information about Channel Services, Region Services and Output services is retrieved.

## About

### Version Info

|Range               |Features         |Based on   |System Impact  |
|--------------------|-----------------|-----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -         | -             |

### System Info

|Range    |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|-----------------|---------------------|-------------------|----------------------|
| 1.0.0.x | No              | Yes                 | -                 |                      |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

In order for tables to be populated, it is necessary to specify the Desk ID.


## How to use

After initializing the Desk ID parameter, you should press the "Reload the Data" button, in order to retrieve the data from DOM.
Desk ID is saved. Data is refreshed after click on the "Reload the Data" button.

### Examples

You can find all information about the tables on the corresponding pages, and on the General page, you can specify the Desk ID.