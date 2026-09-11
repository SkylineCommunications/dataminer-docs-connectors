---
uid: Connector_help_Telenet_Casa_Systems_C100G_Video_Monitoring_Technical
---

# Telenet Casa Systems C100G Video Monitoring

## About

This connector collects the video-delivery KPIs of a Casa Systems C100G platform that is monitored by a Casa Systems C100G element on another DataMiner Agent. Rather than polling the device directly, it uses the DataMiner Web Services API to authenticate against the remote DataMiner System, resolve the target element and retrieve its video tables. This allows the video monitoring of Casa Systems C100G platforms to be consolidated across multiple DataMiner System (DMS) clusters into a single element.

The data source is the DataMiner Web Services API of the remote DataMiner Agent (SOAP), which exposes the parameters and tables of the remote Casa Systems C100G element.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the DataMiner Agent that hosts the remote Casa Systems C100G element and exposes the Web Services API.
- **IP port**: The IP port of the Web Services API (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After the element has been created, configure the following on the **Configuration** page before the connector can retrieve data:

- **API Username** and **API Password**: The credentials used to authenticate the Web Services requests against the remote DataMiner Agent.
- **API Element Name**: The exact name of the remote Casa Systems C100G element to monitor. The connector uses this to automatically resolve the remote DataMiner Agent ID and element ID.

Once these values are set, the connector authenticates automatically and starts polling. If the session is lost, it re-authenticates on its own; you can also force a re-authentication with the **Reconnect** button.

## How to Use

The connector communicates with the remote DataMiner Agent through SOAP calls to the DataMiner Web Services API. It authenticates using the *ConnectApp* method (with automatic session renewal), resolves the target element by name, and retrieves the remote video tables using *GetTableForParameterV2*.

The collected data is organized across the following pages:

- **General**: High-level overview of the monitored platform, including a **Poll Now** action to queue an immediate poll of all enabled data sets.
- **Video Overview**: QAM port statistics (including total bandwidth, used bitrate and utilization), channel statistics (active sessions) and input-port statistics.
- **Video Sessions**: Per-session KPIs, such as detected and requested bitrate, average and maximum jitter, input/output states, and packet-level quality counters (continuity errors, sync-loss packets, PCR interval exceeds, under/overflow).
- **Configuration**: Connection status, authentication credentials, the remote element name, the Reconnect action and the Polling Manager.

### Polling

Polling is controlled through the built-in **Polling Manager**, which allows you to enable or disable individual data sets and configure their polling cycle. Use the **Poll Now** action on the General page to trigger an immediate poll of all enabled data sets.

## Notes

Because this connector retrieves its data from another DataMiner Agent through the Web Services API, the polling DataMiner Agent must have network access to the remote agent on the configured IP and port, and the configured credentials must have sufficient permissions to read the remote element.
