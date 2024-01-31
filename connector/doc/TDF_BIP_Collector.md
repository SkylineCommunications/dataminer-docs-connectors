---
uid: Connector_help_TDF_BIP_Collector
---

# TDF BIP Collector

This connector is used to collect from the **BIP (Production Incident Database)** system, responsible for interfacing all the Collector subsystems, the storage subsystem and all potential customers using the collected and correlated data.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.58              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses HTTPA connection  and requires the following input during element creation:
HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.Should always start with _https://_
- **IP port**: Default:*8443*.

##### Initialization
In order to perform requests, first the **Domains List** parameter needs to be configured.
It is possible to define only one Domain or multiple separated by **;**.

## How to use

The connector contains the following data pages:

- **General**: This page contains the **Domains List** parameter that allows the user to define from each domain should the requests be directed. Without this parameter defined there is no possibility to perform requests.

- **Resources**: This page contains the **Resources Table** that contains all the information obtained from the get resources request.  

- **Alarms**: This page contains the **Event Types Table** that contains all the possible Event Types and the  **Event Table** that contains the active events limited to the last 15 minutes. Also from this page it is possible to define the Display key of the Events Table. The parameter **Events Table Display Key Selection** is used to select this. If **Internal Description** is selected the Display Key will have the following format _Event ID/Event Internal Description/Resource Internal Description_ if **External Description** is selected th format will be _Event ID/Event External Description/Resource External Description_. 

- **Polling Configuration**: From this page it is possible to select which and when the 3 available requests are polled. Also it is possible to poll the requests on demand pressing the button **Poll** available on every entry of the table. There is also a **Poll All** button that allows the user to poll all requests at once. 
