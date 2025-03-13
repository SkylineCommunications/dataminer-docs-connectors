---
uid: Connector_help_Elecard_Boro_Monitoring
---

# Elecard Boro Monitoring

![Elecard Logo.png](~/connector/images/Elecard_Logo.png)

The Elecard Boro Monitoring connector can be used to gather information from the Elecard Boro Solution Server, as well as to create and manage tasks. This connector uses the control API of the Elecard Boro Solution Server to collect data and send control signals.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Provides information about:<br>- existing projects<br>- probes (running and stopped)<br>- current consumption of system resources (CPU, RAM, HDD, NICs usage)<br>- tasks (running and stopped)<br>- active alarms<br>Allows you to:<br>- configure alarms individually for each project<br>- create new tasks | - | - |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the Boro Solution Server.
- **IP port**: The IP port of the Boro Solution Server (default: *80*).

### Initialization

To make sure the element in DataMiner will function correctly, first perform the following steps:

1. [Allow the control API of the Boro Solution Server in Nginx](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.SolutionSettings/ConfiguringSolution.html#enableapiaccessnginx)

1. [Enable the control API of the Boro Solution Server](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.ControlAPI/General.Information.html)

1. [Allow Verify HMAC signatures](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.ControlAPI/Signing.Requests.html#signingapirequests) (optionally, if needed)

When this is done, you can create the element with the IP address and port detailed under [Connections](#connections).

Next, on the **Settings** page of the element, specify a **user ID** and an **HMAC authorization token** (in case the digital signature is required, and you have already enabled this setting in the control API). You can get the user ID from the Boro Solution Server. When you have specified these settings, click the green checkmark to confirm your changes. The value you have entered will be displayed in the User ID field.

## How to Use

### Settings Page

On this page, the User ID and Authorization Token From Boro need to be specified (see [Initialization](#initialization)).

This page also allows you to configure alarms individually for each project. To do so, select a required project in the Project ID field and click the green checkmark to confirm. The project ID/name will then be displayed in the Project ID field.

Except for the Level setting, all **alarm settings** are enabled for all projects by default. You can use the **Level** setting to select an alarm level for a project. For example, you can configure the Level setting to receive alarms of Major or Fatal level only.

All alarms are selected depending on the general settings configuration. In case, for example, you have only QOE and OTT fields enabled, and the Major level is set, you will receive only QOE and OTT alarms of the Major level.

When you have changed the alarm settings, remember to click the **Save Settings** button to save and activate your settings. The list of projects will be displayed in accordance with the projects in your table.

### Projects Page

The Projects page displays the following information for each project:

- The project title and ID.
- The project founder.
- The number of live probes and tasks.
- The total number of live streams.

The column header displays the summary values for live probes, tasks, and streams. All projects available for the authorized user will be shown.

### Probes Page

This page contains two tables.

The **Probe Resources Usage** table displays the following information:

- The project title and probe name.
- The total CPU usage.
- The RAM usage.
- The ratio of RAM used to RAM total in percent.
- The hard disk usage (Disk Used)
- The and amount of available disk space (Disk Available).

The **Network Interfaces** table displays the probe and interface names, IPV4 and IPV6 addresses, netmask, and transmission/receiving data rates.

### Tasks Pages (IPTV, OTT, SRT, RTMP, NDI)

These pages include two tables each, with the live tasks and completed tasks, respectively. The **Completed Tasks Info** table displays all tasks, regardless of the protocol.

The tables display the probe name, task name, task state (*Started*, *Stalled*, etc.), protocol (*HLS*, *DASH*, *IPTV*, etc.), URI, task start time, interface name, and streaming interface. In addition, the **Node Type** column shows whether the task is independent (i.e. it does not contain subtasks — SINGLE or ROOT) or it has subtasks (ROOT, CHILD). You can stop or resume tasks with the **Action** field.

### Active Alarms Page

This page includes a table with active alarms and a table with completed alarms.

Both tables display the project title, probe name, and task name. They also contain information about the task URI, alarm level (*OK*, *error*, *warning*, *major*, or *fatal*), alarm start time, and alarm group (ETH — Ethernet, ETR — TR 101 290, QOE — Quality of Experience, OTT — OTT and Progressive Download, or SYS — System and SCTE35).

### Start Task Page

This page is designed for task creation. It displays a form that allows you to create a task in the same way as in the Boro Solution Server web UI. To create a task, fill in the appropriate fields. First, select a **Project ID**, then a **Probe ID**, and then an **Interface**. When you make your selection, always click the green checkmark for the corresponding field to confirm.

The Project ID is taken from the projects table. The Probe ID field is filtered by the connector depending on the selected project. This way, only probes belonging to the project with the selected ID are available. Interfaces are filtered by the protocol depending on the selected probe.

Some settings can be selected from a list, while others should be specified manually. Each time, you need to click the green checkmark to save your settings. When all settings have been configured, click the **Start Task** button to run the task.