---
uid: Connector_help_Arqiva_DAB_Data_Collector
---

# Arqiva DAB Data Collector

**Arqiva DAB Data Collector** connector is used for DAB Service Manager application, it gathers information across the DMA for **IP-8e** elements (outputs) and **MoIN** elements (inputs and outputs).

## About

The **Arqiva DAB Data Collector** connector can be installed on any DMA, but the prerequisite is that there are **IP-8e** and **MoIN** elements, so it would be able to gather the expected data.

The data is collected every 1 minute.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                      |

## Installation and configuration

### Creation

#### Virtual connection

This is a virtual connector. No user input is required during the creation of the element.

## Usage

### General Page

This page contains two dropdowns one for **IP-8e** versions and the second one for the **MoIN** versions and three page buttons **Mux Data**, **MoIN Data** and **Ip-8e Data**.

User is required to select the protocol versions in the mentioned dropdowns for elements to be able to gather data from all elements running the specific version of the protocols in regard to their inputs and outputs. Once the versions are selected the tables on the mentioned subpages are going to be filled with the appropriate data.

#### IP-8e Data Page

This page contains one standalone parameter **Data Collections Time (IP-8e)** which indicates the time data collection took for all of the elements.

Below the parameter is a table **IP 8e Outputs** where the collected data is being displayed, for each of the outputs from the IP-8e's.

#### MoIN Data Page

This page contains one standalone parameter **Data Collections Time (MoIN)** which indicates the time data collection took for all of the elements.

Below the parameter there are two tables **MoIN Inputs** where the collected data is being displayed, for each of the inputs that is assigned to a decoder on the MoIN elements.

The second table **MoIN Outputs** is displaying the collected data for each active output.
