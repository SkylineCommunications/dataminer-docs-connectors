---
uid: Connector_help_Newtec_Dialog_Platform_VSAT
---

# Newtec Dialog Platform VSAT

The **Newtec Dialog Platform VSAT** connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a Time Series Database (TSDB, i.e. Influx DB). This connector was designed to work with the DataMiner EPM Solution.

## About

The Newtec Dialog monitoring system collects metrics from the Newtec dialog platform and stores them in a Time Series Database. This connector retrieves data from the Newtec Dialog Platform via its **REST API** and via the **TSDB API**. Data from both sources is aggregated into the connector.

The connector uses the following APIs:

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API.
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals and Sat Networks are retrieved using the Time Series Database API.
- Newtec Dialog underlying DMA Web Services API: Events of the entities within the Dialog system.

### Version Info

| Range              | Key Features         | Based on | System Impact |
|--------------------|----------------------|----------|---------------|
| 1.0.0.x [obsolete] | Initial version      | -        | -             |
| 1.0.1.x [SLC Main] | New connection added | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.2.1                  |
| 1.0.1.x   | 2.4.2                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

This connector uses several HTTP connections and requires the following input during element creation.

#### HTTP Connection 1, 2 & 3

These are used to communicate with the Newtec Dialog Restful Standard API.

- **IP address/host**: The IP of the Newtec Central NMS.
- **IP port**: *80* (Default Connection 1) & *8086* (Default Connection 2 & 3)
- **Device address**: *BypassProxy*

### HTTP Connection 4 (added in range 1.0.1.x)

This connection is used to communicate with the underlying Dialog DMA Web Services API.

- **IP address/host**: The hostname of the underlying Dialog DMA.
- **IP PORT**: By default *443*.
- **Device address**: *ByPassProxy*

### Initialization

On the **General** page, specify the **credentials** for user authentication of the REST API in order to collect data from the Dialog platform.

On the **TSDB Polling** page, add the TSDBs that need to be polled to the **Database Configuration** table.

On the **Polling Status** page, enable the Event Config Status parameter and set up the polling interval and event cleanup timer to start retrieving events.

In addition, two toggle buttons need to be enabled to poll both the dialog REST and TSDB API.

### Redundancy

There is no redundancy defined.

## How to use

This connector was designed to follow the other collectors and to work with the DataMiner EPM Solution.

Before data can be displayed by the connector, the credentials and TSDBs must be configured, as detailed in the "Initialization" section above.
