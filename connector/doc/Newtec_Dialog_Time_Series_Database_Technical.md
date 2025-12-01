---
uid: Connector_help_Newtec_Dialog_Time_Series_Database_Technical
---

# Newtec Dialog Time Series Database

## About

The Newtec Dialog NMS (Network Management System) is the unified management interface for the ST Engineering iDirect (formerly Newtec) Dialog satellite communication platform. It uses a Time Series Database (TSDB) to store performance metrics for monitoring and analysis.

The Dialog NMS provides a single, unified interface for all configuration, monitoring, and troubleshooting operations across the entire Dialog platform, from small private hubs to large, globally distributed High-Throughput Satellite (HTS) networks. The Newtec Dialog Platform VSAT connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a TSDB (i.e. Influx DB).

This connector retrieves data from the Newtec Dialog Platform via its REST API and via the TSDB API. Data from both sources is aggregated into the connector.

The connector uses the following APIs:

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API.
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals, and sat networks are retrieved using the TSDB API.

## Configuration

### Connections

This connector uses three HTTP connections.

#### HTTP Connection 1, 2 & 3

These are used to communicate with the Newtec Dialog Restful Standard API. The following input is required during element creation:

- **IP address/host**: The IP of the Newtec Central NMS.
- **IP port**: *80* (default connection 1) and *8086* (default connection 2 and 3)
- **Device address**: *BypassProxy*

### Configuration of Main and Backup CNMS

If a main and backup CNMS are present, additional settings need to be filled in on the **Standard API Polling** page. On this page, the IP and port of the main and backup should be configured, and polling can be enabled to either main or backup. The IP addresses specified in the element editor will then not matter.

Note that if there is only one CNMS, it is enough to simply configure the HTTP connections above only.

**Polling IP format**: 10.0.0.1:80

### TSDB configuration

All TSDBs that need to be polled need to be added to the **Database Configuration** table on the **TSDB Polling** page.

## How to use

Below you can find more information on how to use the most important pages of the connector.

### General page

On this page, you can configure and apply the **credentials** for user authentication of the REST API in order to collect data from the Dialog platform.

### Standard API Polling page

On this page, you can:

- **Enable polling** of the restful API.
- **Configure** the main and backup **CNMS IP address and port**.
- **Switch polling** between the main and backup CNMS.

### TSDB Polling page

On this page, you can:

- **Enable** or disable TSDB **polling**.
- **Configure TSDB database details** to be polled in the Database Configuration table.
- **Configure the time span** of the queries sent to the databases for each measurement.

### TSDB page

This page displays three tables that contain important information about each remote, forward satellite network, and return satellite network. For each row in the tables, a DVE can be created with all relevant information.

The following settings are also available:

- **Auto enable DVEs**: When this is enabled, if the connector detects a new remote or network, a new DVE element will automatically be created
- **Auto Delete DVEs**: When this is enabled, if a remote or network is deactivated or removed, the corresponding DVE element will automatically be deleted in DataMiner. When this is disabled, you can delete the DVE manually by clicking the **Delete** button in the table.

### Remotes TSDB page

This page displays tables with information about each remote. All the information is available in the "Remotes" DVE.

### Forward Link TSDB page (range 1.0.0.x)

This page displays tables with information about each forward link. All the information is available in the "Network Forward" DVE.

### Return Link TSDB page (range 1.0.0.x)

This page displays tables with information about each return link. All the information is available in the "Network Return" DVE.

### Networks TSDB page (range 1.0.1.x)

This page displays tables with information about each satellite network/beam.

The page contains several tables with info regarding the forward and return links statistics.

## Notes

For more details, visit the DataMiner Catalog or contact your system administrator.
