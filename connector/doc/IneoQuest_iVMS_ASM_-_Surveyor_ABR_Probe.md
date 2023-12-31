---
uid: Connector_help_IneoQuest_iVMS_ASM_-_Surveyor_ABR_Probe
---

# IneoQuest iVMS ASM - Surveyor ABR Probe

To check whether all adaptive bitrate (ABR) content is available at all times, the Surveyor ABR Probe is used for monitoring. It uses active monitoring to request the video content from various parts of the delivery network, allowing for rapid fault detection and troubleshooting. IneoQuest's proprietary VeriStream metric (VS Score) shows the QoS status for each video chunk of each stream.

This connector is automatically generated by the connector **IneoQuest iVMS ASM**.

## About

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.1.0.x   | 4.01.01.23             |
| 1.2.4.x   | 5.06.00                |

## Configuration

This connector is used by DVEs that are **automatically created** by the parent element. No user input is required.

## Usage - Range 1.1.0.x

### Probe

Generic probe information is available such as **IP** and **MAC** **Address**, **Type**, **Location**, **Status**, and **Device Status**.

There is also ASM-specific probe information, with an overview of the VeriStream metrics. These parameters are **Avg VS**, **VS1**, **VS2**, **VS3**, **VS4** and **VS5 Stream Count**.

The Surveyor ABR-specific parameters include aggregated statistics and status information: **Stream State Aggregated** and **Active**, **Good**, **Outage**, **Alarmed**, **Warning** and **History Stream Count**.

### Assets

On this page, you will find the linked asset instances per probe. This table contains some generic info such as the **Alias**, **Stream Alias**, **URL**, **Program Reference**, **Server IP**, and **Server Hostname**. VeriStream Scores per asset (**Avg VS** and **Current VS**) are also displayed, as well as the number of **Current**, **History** and **Monitored Alarms**.

### Events

The events tables on this page contain the alarm info per type. These tables are updated via the device L4 traps. The polled open alarms table is used to sync up these tables.

The **System, Program and Transport Alarm Table** will be filtered for each probe element based on the probe link. This way you will only see relevant information in each DVE.

## Usage - Range 1.2.4.x

The DVE element displays the general information of the probe as well as the related Synthetic Assets and Alarms.
