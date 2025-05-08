---
uid: Connector_help_Newtec_Dialog_Platform_VSAT
---

# Newtec Dialog Platform VSAT

## About

The **Newtec Dialog Platform VSAT** connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a Time Series Database (TSDB, i.e. Influx DB). This connector can work as a stand alone collector or alongside the DataMiner EPM solution.

The Newtec Dialog monitoring system collects metrics from the Newtec dialog platform and stores them in a Time Series Database. This connector retrieves data from the Newtec Dialog Platform via its **REST API** and via the **TSDB API**. Data from both sources is aggregated into the connector.

The connector uses the following APIs:

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API.
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals and Sat Networks are retrieved using the Time Series Database API.

![Newtec Dialog Platform VSAT](~/connector/images/NewtecDialogPlatformVSAT_Overview.png)

## Key Features

- **Centralized Monitoring & Control**: Provides unified oversight of the entire VSAT infrastructure within the DataMiner platform.

- **Improved Operational Efficiency**: Reduces the need for manual intervention and streamlines fault detection, troubleshooting, and reporting.

- **EPM Compatability**: This connector can operate independently as a standalone collector or in conjunction with the DataMiner EPM solution.

- **Remotes Configuration Insight**: Provides access to configuration information on Remotes, such as Modem Type, Return Technology, State, FCP Name, RCP Name, etc.

- **Monitor Performance Metrics**: Provides access to performance metrics on Modems, Forward and Return Technologies, and Remotes.

## Technical info

> [!NOTE]
> For detailed technical information, refer to the [Technical help page](xref:Connector_help_Newtec_Dialog_Platform_VSAT_Technical).