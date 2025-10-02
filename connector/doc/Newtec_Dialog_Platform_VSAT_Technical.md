---
uid: Connector_help_Newtec_Dialog_Platform_VSAT_Technical
---

# Newtec Dialog Platform VSAT

The **Newtec Dialog Platform VSAT** connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a Time Series Database (TSDB, i.e. Influx DB). This connector can work as a standalone collector or alongside the DataMiner EPM Solution.

## About

The Newtec Dialog monitoring system collects metrics from the Newtec Dialog Platform and stores them in a Time Series Database. This connector retrieves data from the Newtec Dialog Platform via its **REST API** and via the **TSDB API**. Data from both sources is aggregated into the connector.

The connector uses the following APIs:

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API.
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals and sat networks are retrieved using the Time Series Database API.
- Newtec Dialog underlying DMA Web Services API: Events of the entities within the Dialog system.

## Configuration

### Connections

This connector uses several HTTP connections and requires the following input during element creation.

#### HTTP Connection 1, 2, and 3

These are used to communicate with the Newtec Dialog Restful Standard API.

- **IP address/host**: The IP of the Newtec Central NMS.
- **IP port**: *80* (Default Connection 1) and *8086* (Default Connection 2 and 3)
- **Device address**: *BypassProxy*

### HTTP Connection 4 (added in range 1.0.1.x)

This connection is used to communicate with the underlying Dialog DMA Web Services API.

- **IP address/host**: The hostname of the underlying Dialog DMA.
- **IP PORT**: By default *443*.
- **Device address**: *ByPassProxy*

### Initialization

On the **Configuration** page, specify the **credentials** for user authentication of the REST API in order to collect data from the Dialog platform. 

- You can enable or disable the **EPM and CMDB**, which will hide or show the EPM and CMDB configuration pages.

On the **Polling Config** page, add the TSDBs that need to be polled to the **Database Configuration** table.

On the **Polling Status** page, enable the Event Config Status parameter and set up the polling interval and event cleanup timer to start retrieving events.

In addition, two toggle buttons need to be enabled to poll both the dialog REST and TSDB API.

#### EPM Configuration

On the **EPM Configuration** page of the Intelsat Flex Platform VSAT element, you can find the controls for the ID Notify mechanism. To be able to see this page, enable the EPM toggle button on the **Configuration page**.

- The **ID Import Settings** section contains controls to enable/disable the process of importing IDs from CSV files, as well as the path where the files are located and the current status of this process.
- The **ID Export Settings** section is similar to the ID Import Settings section, except that its controls apply to the process of exporting CSV files with ID requests.

#### CMDB Configuration

On the **CMDB Configuration** page of the Intelsat Flex Platform VSAT element, you can configure the settings for the **provisioning files** mechanism. To be able to see this page, enable the CMDB toggle button on the **Configuration page**.

The connector periodically exports configuration data for remotes, by updating an XML provisioning file on the DMA server, and retrieves information from the database contained in another provisioning file in JSON format. These mechanisms can be configured using the controls on this page.

For each process, file path controls allow you to specify the directory where the provisioning files should be located, and a processing timer parameter allows you to configure the interval for automatic processing.

## How to use

This connector was designed to follow the other collectors.

Before data can be displayed by the connector, the credentials and TSDBs must be configured, as detailed in the [Initialization](#initialization) section above.
