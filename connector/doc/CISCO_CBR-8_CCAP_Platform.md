---
uid: Connector_help_CISCO_CBR-8_CCAP_Platform
---

# CISCO CBR-8 CCAP Platform

The CISCO CBR-8 CCAP Platform is an **SNMP** connector that collects relevant data from **CISCO CBR-8 devices** based on the **DOCSIS** standard. This data is then centralized within the connector and used by DataMiner EPM for aggregation actions.

## About

### Version Info

| Range                | Key Features                           | Based on     | System Impact     |
|----------------------|----------------------------------------|--------------|-------------------|
| 1.0.0.x              | Initial version.                       | -            | -                 |
| 1.0.1.x              | Compatibility with new EPM Solution.   | -            | -                 |
| 1.0.2.x              | Modifications to improve performance.  | -            | -                 |
| 1.0.3.x              | Updated the minimum DataMiner version. | -            | -                 |
| 1.0.4.x              | Modifications to improve performance   | -            | -                 |
| 1.0.5.x [SLC Main]   | New threshold logic.                   | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 16.10.1g               |
| 1.0.1.x   | 16.10.1g               |
| 1.0.2.x   | 16.10.1g               |
| 1.0.3.x   | 16.10.1g               |
| 1.0.4.x   | 16.10.1g               |
| 1.0.5.x   | 16.10.1g               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.0.3.x   | No                  | Yes                     | -                     | -                       |
| 1.0.4.x   | No                  | Yes                     | -                     | -                       |
| 1.0.5.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (*161* by default).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The connector uses custom properties to configure the Network, Market and Hub of the CCAP, so make sure that these are configured to link the views to the EPM data cards and full EPM functionality.

When you have created the element, configure the following settings:

- **Entity Export/Import Settings**: These sections allow the exporting of the configuration files and importing of the provisioning files.

  - **Entity Export** and **Entity Import**: These parameters allow you to enable/disable the exporting and importing feature.
  - **Export Directory** and **Entity Import Directory**: It is necessary to specify the paths where the files will be exported and imported.
  - **Entity Export Directory Type** and **Entity Import Directory Type**: Specify whether the export/import paths are **local or remote**. Note that for the remote file handling to work, you must enter the credentials for the system in the System Credentials section and enter the path to the remote directory in the Export Directory or Import Directory parameter. The path must be shared/accessible, or this feature will not work.

- **System Credentials**: This section is to be used if the element is configured to a remote file location.

  - **System Username**: The username of the user with access to the directory. If no domain is specified, the domain from the element's DMA location will be used.
  - **System Password**: The password of the user to access the remote directory.

In addition, in range **1.0.0.x**, configure the following settings:

- **Other Settings:** Additional settings to ensure proper data transfer and additional information.

- **Collector:** Fill this out with the DMA ID/element ID of the Generic CM Collector used to provision the CMs of the CCAP.

### Threshold Table

In the threshold table, you can define limits for each polled modulation. The available Key Performance Indicators (KPIs) for setting thresholds are:

- **Maximum Timing Offset Level**: Range from 0 to 10000 µs.
- **Minimum Rx Power Level**: Range from -12 to 12 dBmV.
- **Maximum Rx Power Level**: Range from -12 to 12 dBmV.
- **Minimum SNR Level**: Range from 10 to 60 dB.
- **Post-FEC Maximum Uncorrectable Error Ratio Level**: Range from 0 to 30000 ppm.

When you click the **Apply** button, the status of the specified Key Performance Indicators (KPIs) in the CM table will be updated.

The minimum value for the Rx threshold cannot exceed the maximum boundary; the connector will restrict attempts to set such values.

## How to use

Once the initial setup is done, the connector can function without further configuration. However, you can perform the following actions on the **Configuration** page:

- In range **1.0.0.x**:

  - **Export Topology**: When you click the **Apply** button in the **Entity Export Settings** section, the element's topology files will be exported. These files will be processed by the Skyline EPM Solution.
  - **Import Topology**: When you click the **Apply** button in the **Entity Import Settings** section, the element will import the corresponding topology files created by the Skyline EPM Solution. These new files are based on the files originally exported by the CISCO CBR-8 CCAP Platform element.
  - **Topology Update Time Interval**: This parameter allows you to configure the frequency at which the topology files are automatically exported. This parameter is set to one hour by default.

- In range **1.0.1.x**:

  - **Export Topology**: When you click the **Apply** button in the **Entity Export Settings** section, the element's topology files will be exported. These files will be processed by the Skyline EPM Solution.
  - **Import Topology**: When you click the **Apply** button in the **Entity** **Import Settings** section, the element will import the corresponding topology files created by the Skyline EPM Solution. These new files are based on the files originally exported by the CISCO CBR-8 CCAP Platform element.
  - **SNMP Fast Interval**: Define how often the information related to the status of the CCAP should be polled. By default, the parameter is set to 15 minutes.
  - **SNMP Slow Interval**: Define how often the information related to the configuration of the CCAP should be polled. By default, the parameter is set to 4 hours.
  - **Virtual Interval**: Define how often the topology will be synced with EPM. By default, the parameter is set to 2 hours.

- In range **1.0.3.x**:

  - **Script Name**: Specify the Automation script to be executed.
 
- In range **1.0.5.x**

  - **Auto Correct Status Interval**: On the Debug page, this parameter allows you to adjust the interval for a recurring logic that checks how long the polling statuses have been stuck in processing and revert the statuses to OK. Range: 1 day – 1 week. Default: 1 day.

## Notes

For range **1.0.0.x** of the connector, specific Correlation rules and Automation scripts are required for the communication with auxiliary connectors such as the Generic CM Collector and with EPM connectors such as Skyline Platform EPM and Skyline Platform WM. To get the full functionality of this connector, make sure these Correlation rules and Automation scripts are configured and enabled.

In range **1.0.1.x**, the Correlation rules are no longer required.
