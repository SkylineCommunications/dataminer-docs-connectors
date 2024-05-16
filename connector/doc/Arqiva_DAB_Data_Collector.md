---
uid: Connector_help_Arqiva_DAB_Data_Collector
---

# Arqiva DAB Data Collector

This connector is used for a DAB Service Manager application. It gathers information across a DataMiner Agent for **IP-8e** elements (outputs), **MoIN** elements (inputs and outputs), and **Mux** elements.

The **Arqiva DAB Data Collector** connector can be installed on any DataMiner Agent, as long as there are **IP-8e**, **MoIN**, and **Mux** elements available that the expected data can be retrieved from.

The data is collected every minute.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [Obsolete]   | Initial version.  | -            | -                 |
| 1.0.1.x [SLC Main]   | Mux data added. Refresh button implemented. MoIN tables are now grouped into one table. Script execution controls added.  | -            | -                 |

### Product Info

| Range              | Supported Firmware |
|--------------------|--------------------|
| 1.0.0.x [Obsolete] | -                  |
| 1.0.1.x            | -                  |

### System Info

| Range              | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--------------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x [Obsolete] | No              | Yes                 | -                 | -                   |
| 1.0.1.x            | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual connection

This is a virtual connector. No user input is required during the creation of the element.

## How to Use

### General Page

This page contains three dropdown boxes: for **IP-8e** versions, for **MoIN** versions, and for **Mux** versions. You can use these to select the connector versions from which data should be retrieved. Once you have selected the versions, the element will gather data from all elements running the specific version of the connectors for the inputs and outputs.

There are also three page buttons: **Mux Data**, **MoIN Data**, and **Ip-8e Data**. The tables on these subpages will be filled in as soon as you have selected the connector versions in the IP-8e and MoIN dropdown boxes.

#### IP-8e Data Page

On this page, the **Data Collections Time (IP-8e)** parameter indicates the time data collection took for all elements.

Below this parameter, the **IP 8e Outputs** table displays the collected data for each of the outputs from the IP-8e elements.

#### MoIN Data Page

On this page, the **Data Collections Time (MoIN)** parameter indicates the time data collection took for all elements.

Below this parameter, the **MoIN Data** table displays the collected data for each of the inputs and outputs assigned to a decoder on the MoIN elements.

#### Mux Data Page

On this page, the **Data Collections Time (Mux)** parameter indicates the time data collection took for all elements.

Below this parameter, the **Mux data** table displays the collected data for each of the active inputs.

#### Execute Script

This page is dedicated to the execution of specific scripts from the connector. You can set the **Script Name** and **Script Input**, and then click the **Execute** button to execute a script.

Below that, the **Execution Status** and **Script Output** are displayed.
