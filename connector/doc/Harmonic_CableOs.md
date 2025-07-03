---
uid: Connector_help_Harmonic_CableOs
---

# Harmonic CableOs

**Harmonic CableOs** is a distributed CMTS system that splits the processing from the RF capabilities. This connector monitors the different interfaces, mainly upstream and downstream channels.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Upstream and downstream channels monitoring. | - | - |
| 1.0.1.x | Every bitrate shown as Mbps. New pages added (RF Port, RPD, Out of Band, Video Channels, Memory), and new tables added on those pages. | 1.0.0.5 | - |
| 1.0.2.x [SLC Main] | Parameter and layout adaptation. | 1.0.0.5 | - |
| 2.0.0.x | Recreated to be EPM-compliant. Will work with and without Skyline EPM Platform connector. NOTE: Does not contain any previous tables from 1.x.x.x range. | - | - |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.8.12.0-1             |
| 1.0.1.x   | 1.8.12.0-1             |
| 1.0.2.x   | 1.8.12.0-1             |
| 2.0.0.x   | 1.8.12.0-1             |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

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

### 1.x.x.x Range

You can configure several parameters with this connector, such as the **Interface Alias**, **Admin Status**, and **Upstream/Downstream frequency values** (MHz).

The connector also provides extra information for the **Downstream Channels**, including **Interface Utilization**, **CM Total**, **CM Online**, **CM Registered**, and **CM Offline**. This last parameter is calculated by subtracting the **CM Online** from the **CM Total**.

For the **Upstream Channels**, the table displays the same information as for the **Downstream Channels**, with in addition the **Signal Noise Ratio**.

At the top of some of the columns of the tables, a value is displayed. For most columns, this is the sum of the row values, except for the Signal Noise Ratio column, where it is the average.

The **1.0.1.x** range also shows information about **RF Ports, RPD, Out of Band, Video Channels, CPU**, and **Memory**.

- The Out of Band page contains two tables: **OBB NDF Configuration** and **OBB NDR Configuration**.
- The CPU page contains the **CPU Utilization Status Table** and a page button that leads to the **CPU Total Table**.

### 2.x.x.x Range

Once the initial setup is done, the connector can function without further configuration. However, you can configure the following settings on the **Configuration** page:

- **EPM Lite Mode**: Determines whether the element depends on EPM Manager IDs for aggregated KPIs. If EPM Lite Mode is enabled, all tables will be populated and the element will work without an EPM Manager.
- **Export Topology**: When you click the **Apply** button in the **Entity Export Settings** section, the element's topology files will be exported. These files can be processed by the Skyline EPM Solution.
- **Import Topology**: When you click the **Apply** button in the **Entity Import Settings** section, the element will import the corresponding topology files created by the Skyline EPM Solution. These new files are based on the files originally exported by the CISCO CBR-8 CCAP Platform element.
- **Topology Update Time Interval**: Determines the frequency at which the topology files are automatically exported. By default, the parameter is set to 1 hour.
- **SNMP Fast Interval**: Determines how often the information related to the status of the CCAP will be polled. By default, the parameter is set to 15 minutes.
- **SNMP Slow Interval**: Determines how often the information related to the configuration of the CCAP will be polled. By default, the parameter is set to 4 hours.
- **Virtual Interval**: Determines how often the topology will be synced with EPM. By default, the parameter is set to 2 hours.
