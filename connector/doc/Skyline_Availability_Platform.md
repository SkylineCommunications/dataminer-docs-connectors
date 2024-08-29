---
uid: Connector_help_Skyline_Availability_Platform
---

# Skyline Availability Platform

This collector will ping various endpoints provided by the Availability EPM manager and then aggregate various ping statistics to higher levels in the topology.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To import the endpoints the collector needs to ping, in the **Import Settings** section on the **Configuration** page, fill in the correct directory, as well as user information in case you will import from a remote directory.

If you use the **EPM Setup Wizard** script, this will be filled in automatically.

## How to use

This is a self-sufficient connector that is intended to be used with the **Skyline EPM Platform Availability** connector.
