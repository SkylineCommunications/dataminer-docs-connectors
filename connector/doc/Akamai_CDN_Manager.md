---
uid: Connector_help_Akamai_CDN_Manager
---

# Akamai CDN Manager

Akamai is a **C**ontent **D**elivery **N**etwork services provider. This connector uses both the Akamai Alerts and the todaytraffic-by-time APIs to allow you to monitor traffic and capture significant changes, based on continuous tracking by Akamai's network monitoring platform.

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

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |[Akamai CDN Manager - CP Code](xref:Connector_help_Akamai_CDN_Manager_-_CP_Code)   |

## Configuration

### Connections

#### HTTP main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device.
- **Device address**: The device address. Default: *ByPassProxy*.

## How to Use

On the **General** page, you should enter the necessary information to establish an HTTP connection with the vendor API. Some of the displayed parameters are the **Secret**, **Client Token**, **Access Token**, and **Login Status.**

In order for DataMiner to monitor the Akamai CDN, an authorized account must be created. Details on how to create this account can be found on the [Akamai website](https://developer.akamai.com/introduction/Luna_Setup.html).

If a connection has been established, data will be displayed on the following pages:

- **Contracts**: Displays the Contracts table.
- **Groups**: Displays the Groups table.
- **CP Codes**: Displays the CP Codes table. Enable the **Poll Metrics** parameter to get data in the Traffic per CP Code table. Enable the **Poll Real-Time Metrics** parameter to get data in the Real-Time Traffic per CP Code table and Dimensions table.
- **Network Storage**: Displays the storage groups and associated upload accounts.
- **Traffic**: Displays the Traffic per CP Code table and Real-Time Traffic per CP Code table.
- **Structure Overview**: Contains the Structure Overview tree control.
- **Media Services Live**: Displays a list of all streams.
- **Alert Summaries**: Displays the Alert Summaries table.
- **Alert Details**: Displays the Alert Details table.
- **Alert Overview**: Displays the relationship between the Alert Summaries and Alert Details tables.
- **Dimensions**: Displays the dimension information per CP Code from the Media Services Live 4 Reports API.
