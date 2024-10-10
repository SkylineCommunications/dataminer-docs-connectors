---
uid: Connector_help_Skyline_EPM_Platform_FTTH_Collector
---

# Skyline EPM Platform FTTH Collector

The **Skyline EPM Platform FTTH Collector** is in charge of ingesting data towards the integration with EPM platform back-end and front-end elements.

This collector represents an OLT (Optical Line Terminal) in the system, where all the ONTs (Optical Network Terminal) connected to it are displayed.

The connector receives Kafka messages via the InterApp framework, sent by the **Telenet EPM Platform FTTH WM** connector. Depending on the [type of event data](#kafka-event-types) received, it offloads [different files](#types-of-offloaded-files).

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### General

This page contains general information related to the device, i.e. **Number ONT**.

### Configuration

#### System Credentials

- **Network Share Username**: The username that is used to authenticate and access the remote network share.

- **Network Share Password**: The password corresponding to the network share username.

#### Front-End Import Settings

- **Import Directory Type**: Specifies the type of directory used for importing files. It can be either local or remote. In case it is set to *Remote*, files are imported from a network location.

- **Structured Files Directory**: This field indicates the network path where structured files are located for import, e.g. `\10.10.10.10\c$\FE Structured Files`. This refers to a shared folder on a remote machine that contains these files.

#### Offload Settings

- **Offloading Status**: Indicates whether offloading is currently enabled or disabled. If this is enabled, the system offloads files from a source directory to a designated offloading location.

- **Offloading Directory Type**: Specifies the type of directory for offloading. *Remote* means the offloaded files are stored on a network-shared folder, as opposed to a local folder.

- **Offloading Folder Path**: The network path where the system will offload files (e.g. `\10.10.10.10\c$\WM\Offload`). This directory serves as the destination for offloading structured files after processing.

#### Debugging Option

With the Debugging option, you can enable debugging mode, which is typically used to gather more detailed logs for troubleshooting purposes.

### PNM Thresholds

The following parameters are used to restrict the offloading of PNM data. A new CSV file is generated for each ONT if the delta Rx or delta Tx exceeds an adjustable threshold.

- Rx Threshold
- Tx Threshold

### ONT

This page contains a table with an overview of all the ONTs. The following columns are displayed:

- **Name**: Displays the ONT name.

- **Rx Power (dBm)**: Refers to the optical signal power received by the ONT from the OLT. This is an indicator of the quality of the optical link between the OLT and the ONT.

- **Tx Power (dBm)**: Refers to the optical signal power transmitted by the ONT to the OLT. This power level is important for ensuring that the OLT can accurately receive and process the upstream data.

- **Time**: The date and time of the last received event.

- **Status**: Indicates whether the ONT is *In Service* or *Out of Service*.

- **PowerLoss**: Possible values are *Active* and *Inactive*. If *Active*, it refers to a decrease in the strength of the optical signal as it travels through the fiber.

- **Loss of Signal**: Possible values are *Active* and *Inactive*. If *Active*, the ONT is no longer receiving any signal at all from the optical network.

## Notes

### Kafka Event Types

The following Kafka event types are supported:

- **Status** event

  Read from both alarm and IPFIX topics, this event indicates whether the ONT is online or offline. Status changes can be triggered by network issues, alarms, or performance data.

- **PNM** (Proactive Network Maintenance) event

  Read from the IPFIX topic, this event provides the current optical Rx and Tx power levels of the ONT, measured in dBm. These values help monitor the physical health of the network for proactive maintenance and early detection of potential issues.

- **Dying Gasp** event

  Read from the alarm topic, this event indicates the stability of communication between the OLT and ONT. It captures power-related events, such as **PowerLoss**, which signals a loss of electrical power at the ONT, and **LossSignal**, which reflects a loss of optical signal, both affecting the communication between the two devices.

### Types of Offloaded Files

#### Status Offloading Files

- Ivr.ont.offload.[DMA_ID].[ELEMENT_ID].[INDEX].[OPERATOR].dat

  Offloading occurs per collector within a one-minute time window, during which the status changes of the ONTs are recorded. If no changes occur within that time window, no file is created.

- Ivr.ont.sync.offload.[DMA_ID].[ELEMENT_ID].[INDEX].[OPERATOR].dat

  A daily file is generated for each ONT, recording its status at that time, with offloading spread throughout the day by generating a new file every minute.

#### Dying Gasp and Loss of Signal Files

- [DMA_ID].[ELEMENT_ID].PowerLoss.[INDEX].[OPERATOR].dat

  A file is generated for each collector, recording changes in the PowerLoss status of the ONTs within a one-minute time window, but only when a "PowerLoss" clear event is received. If no changes occur during that time window, no file is created.

- [DMA_ID].[ELEMENT_ID].SignalLoss.[INDEX].[OPERATOR].dat

  A file is generated for each collector, recording changes in the SignalLoss status of the ONTs within a one-minute time window, but only when a "SignalLoss" clear event is received. If no changes occur during that time window, no file is created.

#### PNM Offloading File

- basicnetwork.ont.offload.[DMA_ID].[ELEMENT_ID].[INDEX].[OPERATOR].dat

  A file is generated for each collector, recording changes in the Rx or Tx of the ONTs during a one-minute time window, but only if the incoming value exceeds the predefined Tx/Rx threshold.

- basicnetwork.sync.ont.offload.[DMA_ID].[ELEMENT_ID].[INDEX].[OPERATOR].dat

  A daily file is generated for each ONT, recording the Rx and Tx values at that time, with offloading spread throughout the day by generating a new file every minute.
