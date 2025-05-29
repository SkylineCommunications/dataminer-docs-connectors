---
uid: Connector_help_Newtec_Dialog_Platform_VSAT
---

# Newtec Dialog Platform VSAT

## About

The **Newtec Dialog Platform VSAT** connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a Time Series Database (TSDB, i.e. Influx DB). This connector can work as a standalone collector or alongside the DataMiner EPM Solution.

The Newtec Dialog monitoring system collects metrics from the Newtec Dialog Platform and stores them in a Time Series Database. This connector retrieves data from the Newtec Dialog Platform via its **REST API** and via the **TSDB API**. Data from both sources is aggregated into the connector.

The connector uses the following APIs:

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API.
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals and sat networks are retrieved using the Time Series Database API.

![Newtec Dialog Platform VSAT](~/connector/images/NewtecDialogPlatformVSAT_Overview.png)

## Key Features

- **Centralized monitoring and control**: Provides unified oversight of the entire VSAT infrastructure within the DataMiner platform.

- **Improved operational efficiency**: Reduces the need for manual intervention and streamlines fault detection, troubleshooting, and reporting.

- **EPM compatibility**: This connector can operate independently as a standalone collector or in conjunction with the DataMiner EPM Solution.

- **Remotes configuration insight**: Provides access to configuration information on remotes, such as modem type, return technology, state, FCP name, RCP name, etc.

- **Monitoring of performance metrics**: Provides access to performance metrics on modems, forward and return technologies, and remotes.

## Technical info

> [!NOTE]
> For detailed technical information, refer to the [Technical help page](xref:Connector_help_Newtec_Dialog_Platform_VSAT_Technical).
