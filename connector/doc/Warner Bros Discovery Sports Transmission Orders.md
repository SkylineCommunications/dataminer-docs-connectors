---
uid: Connector_help_Warner_Bros_Discovery_Sports_Transmission_Orders
---

# Warner Bros Discovery Sports Transmission Orders

The Warner Bros Discovery Sports Transmission Connector will be used to parse and display the Sports Transmission Orders pushed through the **Warner Bros Discovery Transmission Orders** User-defined API.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |10.1.0.0         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |Warner Bros Discovery Transmission Orders API Endpoint         |   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No extra initialization is required.

### Redundancy

There is no redundancy defined.


## How to use

This driver parses Transmission Orders Json requests received from the **Warner Bros Discovery Transmission Orders API Endpoint**, therefor no communication will be shown in the streamviewer.

This driver has a (hidden) DEBUG Page, this page can be displayed by executing a multiple set on the *Show Debug Page* parameter.

### Examples

A high level Transmission Orders overview can be found on the **Transmission Orders Page**.

Each Transmission Order can have one or multiple services, these are aggregated and displayed on the **Services Page**.

In case a service has Facilities or Audio's, these will be displayed on the **Facilities** or **Audio's page** respectively.

A treecontrol displaying these relations can be found on the **Overview Page**.