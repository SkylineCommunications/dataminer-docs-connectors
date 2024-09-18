---
uid: Connector_help_CISCO_CBR-8_CCAP_UTSC
---

# CISCO CBR-8 CCAP UTSC

This connector helps to visualize the Spectrum Analyzer functionality of the CISCO CBR-8 CCAP by ingesting CSV files with trace data that will be displayed using the native Spectrum Analyzer UI in DataMiner.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version         |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

There are few steps that are needed during the initialization of an element running this connector.

- In the **element wizard** under the drop down **Advanced element settings** in **Spectrum settings** check the **shared session mode** option. This prevents multiple users sending a request for a new trace, this is not ideal due to this driver reading static CSV files.
- After the element is created, nagivate to the **Configuration Page** to fill in the **Entity Import Directory**. This directory should include the offloaded CSV files by the CISCO CBR-8 CCAP


## How to use

The connector is straightforward to use after the intial setup mentioned in the **Intialization section** above. 

To use the connector, nagivate to the **Configuration Page** and click the **Update Trace button**. This will read all the CSV files in the location specified in the **File Import Settings section**. Navigate to the **Spectrum Analyzer** page to see the trace on the **DataMiner Spectrum Analyzer UI**. Once there you will have the wide range of tools provided by the **Spectrum UI**, for more information check out the **Spectrum Analyzer section** in [DataMiner Docs](https://docs.dataminer.services/user-guide/Advanced_Modules/Spectrum_Analysis/Spectrum_Analysis.html)

Other settings provided by the connector is the ablity to read the CSV files from a remote server. To configure this, navigate to the **Configuration Page** and perform the following steps
- Enter a remote directory path in the **Entity Import Directory** parameter
- Fill in the **System Username** and **System Password** with account that has access to the remote directory.
- Toggle the **Entity Import Directory Type** to remote.
