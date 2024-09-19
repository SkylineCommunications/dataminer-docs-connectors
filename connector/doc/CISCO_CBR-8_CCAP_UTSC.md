---
uid: Connector_help_CISCO_CBR-8_CCAP_UTSC
---

# CISCO CBR-8 CCAP UTSC

This connector helps to visualize the Spectrum Analyzer functionality of the CISCO CBR-8 CCAP by ingesting CSV files with trace data that will be displayed using the native Spectrum Analyzer UI in DataMiner.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

- When you are creating the element, expand the **Advanced element settings** section, and enable the **Shared session mode** option (under Spectrum settings). This prevents multiple users from sending a request for a new trace at the same time, which is necessary because this connector reads static CSV files. See [Sharing spectrum sessions](https://aka.dataminer.services/Sharing_spectrum_sessions).

- When the element has been created, go to the **Configuration page** and fill in the **Entity Import Directory**. This directory should contain the CSV files offloaded by the CISCO CBR-8 CCAP.

## How to use

After the initial setup mentioned above, this is how you use the connector:

1. Go to the **Configuration** page and click the **Update Trace button**. This will read all the CSV files in the location specified in the File Import Settings section.
1. Go to the **Spectrum Analyzer** page to see the trace in the DataMiner Spectrum Analysis UI. On this page, you have a wide range of tools available. For detailed information, refer to [DataMiner Spectrum Analysis](https://aka.dataminer.services/Spectrum_Analysis).

The connector can also read CSV files from a remote server. To configure this:

1. Go to the **Configuration** page.
1. Enter a remote directory path in the **Entity Import Directory** parameter.
1. Fill in the **System Username** and **System Password** with an account that has access to the remote directory.
1. Toggle the **Entity Import Directory Type** to *Remote*.
