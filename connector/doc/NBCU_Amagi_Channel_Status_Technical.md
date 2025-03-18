---
uid: Connector_help_NBCU_Amagi_Channel_Status_Technical
---

# NBCU Amagi Channel Status

## About

This connector is designed to retrieve and monitor Amagi channel statuses, providing an overview of the health state of each channel. It communicates using HTTP requests to fetch real-time data. The retrieved information includes channel names and agent states, which are displayed in the Channel Status Table.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version      |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-     |


### System Info

In this subsection, insert a table with five columns. Indicate whether the range features **DCF integration** and whether it is **Cassandra compliant**.

In the "Linked Components"; column, list all DataMiner components that have a link, in any way, with this connector range, e.g. mediation connectors, Automation scripts, custom report, etc.

In the "Exported Components" column, list all the connectors that are exported by the parent connector in question.
**This can only be omitted for an exported connector or for a connector that cannot have exported connectors.**

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. (default: *443*)
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization

On the General page, you will need to configure a token obtained from the GUI or vendor. This will be used for all the requests sent by the connector.


## How to use

### General Page  
On the **General** page, you can configure parameters such as **Core ID** and **Strategy**, enabling better identification of each switcher control.  

### Channel Status Page  
On the **Channel Status** page, you can view the real-time statuses of channels retrieved from the device. The table displays the **channel name** and its **agent state**.  

### Polling Frequency  
The connector allows you to **set the desired polling frequency** to retrieve channel statuses at your preferred intervals.  



