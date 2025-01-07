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

- When you are creating the element, expand the **Advanced element settings** section, and enable the **Shared session mode** option (under Spectrum settings). This prevents multiple users from sending a request for a new trace at the same time, which is necessary because this connector reads static binary files. See [Sharing spectrum sessions](https://aka.dataminer.services/Sharing_spectrum_sessions).

- When the element has been created, go to the **Configuration page** and fill in the **Entity Import Directory**. This directory should contain the binary files offloaded by the CISCO CBR-8 CCAP. This connector is used in conjunction with the **Generic SFTP Client** connector to retrieve the files exported by the CISCO CBR-8 on the TFTP server and copy them to a local directory.

## How to use

After the initial setup mentioned above, configure which port to request trace data for on the **UTSC** page.

### UTSC

This section allows you to **request Spectrum Analyzer trace data** from the CCAP via SNMP based on the configurations for **a selected upstream port**. There are the steps to follow when requesting Spectrum Analyzer trace data. Here are the **steps upon landing on the UTSC main page**:

1. Select an upstream port from the **Upstream Port** dropdown menu.

   This step is crucial. Without a selected port, you will not be able to configure the CCAP to retrieve Spectrum Analyzer data.

1. Check the **Status parameter** below this.

   Based on the selected upstream port, this parameter will indicate if the upstream port has already been configured.

   - If the status is **N/A**, the port is **not configured**, which means you must click the **Update Config button** to configure the port with the default configuration.

     This will return a status of *Not Ready*.

   - If the status has a valid value, no further action is needed for this step.

1. Fill out the desired **configuration parameters**, and click the **Update Config** button to send the settings to the device.

1. Once the desired settings have been applied to the selected upstream port, click the **Start Capture or Stop Capture button**, depending on what you want to do.
