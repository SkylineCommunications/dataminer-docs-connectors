---
uid: Connector_help_TDF_BIP_Collector
---

# TDF BIP Collector

This connector is used to collect data from the **BIP (Production Incident Database)** system, responsible for interfacing all the collector subsystems, the storage subsystem, and all potential customers using the collected and correlated data.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.58               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Should always start with `https://`
- **IP port**: Default: *8443*.

##### Initialization

In order to perform requests, first the **Domains List** parameter needs to be configured. You can define only one domain or define multiple domains separated by semicolons (";").

## How to use

The connector contains the following data pages:

- **General**: Contains the **Domains List** parameter, which allows you to define from which domain requests should be directed. If this parameter is not defined, the connector cannot request any data.

- **Resources**: Contains the **Resources Table**, with all the information obtained from the get resources request.

- **Alarms**: Contains the **Event Types Table**, with all the possible event types, and the **Event Table**, with the active events, limited to the last 15 minutes.

  On this page, you can also define the display key of the Events Table, by means of the parameter **Events Table Display Key Selection**. If *Internal Description* is selected, the display key will have the following format: `Event ID/Event Internal Description/Resource Internal Description`. If *External Description* is selected, the format will be `Event ID/Event External Description/Resource External Description`.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table. With the **Poll All** button, you can poll all requests on demand at once.
