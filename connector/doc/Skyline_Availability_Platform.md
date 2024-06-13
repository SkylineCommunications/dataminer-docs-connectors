---
uid: Connector_help_Skyline_Availability_Platform
---

# Skyline Availability Platform

This collector will ping various endpoints provided by the Availability EPM manager and then aggregate various ping statistics to higher levels in the topology.

## About

### Version Info

**This subsection can only be omitted for an exported connector**

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

For the collector to import which endpoints it needs to ping, the **Import Settings** section in the **Configuration** page need to be properly filled out with the correct directory and user information if importing from a remote directory.

This will automatically be filled out after using the EPM Setup Wizard script.

### Redundancy

There is no redundancy defined.

## How to use

This driver is a self sufficient collector to be used with the **Skyline EPM Platform Availability** driver.
