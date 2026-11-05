---
uid: Connector_help_EEG_Alta-TS_Caption_Encoder_Technical
---

# EEG Alta-TS Caption Encoder

## About

This connector allows DataMiner to monitor and manage the EEG / AI-Media Alta-TS Caption Encoder.

Alta-TS is a software-based caption encoder designed for MPEG Transport Stream (MPEG-TS) workflows. It enables insertion, transport, and monitoring of closed captions and subtitles in IP video environments and can integrate with the AI-Media iCap cloud captioning platform. Alta-TS is typically deployed as a virtual machine.

The connector communicates with Alta-TS over HTTP(S) and provides visibility into encoder instances, stream configuration, captioning status, system alarms, logs, and operational statistics.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

Enter the **username** and **password** on the **General** page before the connector can start communicating with the Encoder endpoint.

## How to Use

The **Instance Settings** page contains a table with basic information about the existing instances, as well as logs for every instance. You can monitor and configure the different instance components in the corresponding subpages under the **Instance Settings** page.

You can create new encoder instances on the **New Instance** subpage.
