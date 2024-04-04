---
uid: Connector_help_Elecard_Boro_Monitoring
---

# Elecard Boro Monitoring

## About

The Elecard Boro Monitoring allows gathering information from the Elecard Boro Solution Server, creating and managing the tasks. This connector uses the control API of Elecard Boro Solution Server to collect the data and send control signals.

### Version Info

| Range     | Key Features                                                         |Based on  |System Impact  |
|-----------|----------------------------------------------------------------------|----------|---------------|
| 1.0.0.x   | Provides the information about:                                      |-         |-              |
|           | - existing projects                                                  |          |               |
|           | - probes (running and stopped)                                       |          |               |
|           | - current consumption of system resources (CPU, RAM, HDD, NICs usage)|          |               |
|           | - tasks (running and stopped)                                        |          |               |
|           | - active alarms                                                      |          |               |
|           |                                                                      |          |               |
|           | Allows to:                                                           |          |               |
|           | - configure alarms individually for each project                     |          |               |
|           | - create new tasks                                                   |          |               |


### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |


### System Info

|Range      |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|-----------|-----------------|---------------------|-------------------|----------------------|
|1.0.0.x    |No               |Yes                  |-                  |-                     |


## Installation and Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the Boro Solution Server.]
  - **IP port**: [The IP port of the Boro Solution Server (default 80).]

### Initialization

[Allow the control API of the Boro Solution Server in Nginx](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.SolutionSettings/ConfiguringSolution.html#enableapiaccessnginx)
[Enable the control API of the Boro Solution Server](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.ControlAPI/General.Information.html)
[Allow Verify HMAC signatures (optionally, if needed)](https://boro.elecard.com/docs/en/boro-solution-userguide/chapter.ControlAPI/Signing.Requests.html#signingapirequests)

Upload the protocol to DataMinerCube, specify an IP address/host and an IP port.

### Redundancy

There is no redundancy defined.

## How to use

### Settings Page

. To start protocol operation specify a User ID that you can get from the Boro Solution Server and a HMAC authorization token (in case the digital signature is required, and you have already enabled this setting in Control API). When a user ID specified, click the green checkmark and confirm changes. After saving, the entered value should be displayed in the field against the User ID.

. In the Settings page, you can configure alarms individually for each project. For that, select a required project and click the green checkmark for confirmation. The project ID/name should display in the Project ID field. 

. All settings are enabled by default for all projects (except for the Level field). The Level field enables us to select alarm level for a project. Using this field, you can configure receiving alarms of Major or Fatal level. 

. Additionally, you need to remember that all alarms are selected depending on the general settings configuration. In case, you have only QOE and OTT fields enabled, and the Major field is set, then you will receive only QOE and OTT alarms of the Major level.

. Click the Save Settings to save and activate your settings. The list of projects will be displayed in accordance with projects in your table.

### Projects Page

In the page with projects, the following information is displayed: a project title and ID, a project founder, number of live probes and tasks, total number of live streams. The column header displays the summary values for live probes, tasks, and streams. All projects available for the authorized user will be shown.

### Probes Page

The page with probes displays project title and probe name, CPU total usage, RAM usage, ratio of RAM Used to RAM Total in percentage, hard disk usage (Disk Used), and amount of available disk space (Disk Available). Network Interfaces table displays probe and interface names, IPV4 and IPV6 addresses, netmask, transmission/receiving data rates.

### Tasks Page (IPTV, OTT, SRT, RTMP)

The page includes two tables - live tasks and completed tasks (the table of completed tasks is one for all, i.e., the table displays all tasks regardless of the protocol). Tables contains the following information: a probe name, a task name, a task state (Started, Stalled…), a protocol (HLS, DASH, IPTV…), URI, a task start time, an interface name, streaming interface. Node Type shows whether the task is independent (i.e., it does not contain subtasks - SINGLE or ROOT) or a task has subtasks (ROOT, CHILD). You can stop or resume tasks in the Action field.

### Active Alarms Page

The page includes the table with active alarms and the table with completed alarms. Both tables contain a project title, the probe name, the task name. Additionally, there is information about a task URI, alarm level (ok, error, warning major, fatal), alarm start time, alarm group (ETH - Ethernet, ETR - TR 101 290, QOE - Quality of experience, OTT - OTT and Progressive Download, SYS - System и SCTE35).

### Start Task Page

The Start Task is designed for a task creation. The form almost completely repeats the process of a task creation in the Boro Solution Server Web-UI. To create a task, fill in the appropriate fields. The process of selecting Project ID, Probe ID and Interface occurs in the following sequence: Project ID → Probe ID → Interface (when choosing, you should click on the green checkmark in the corresponding field to confirm). The Project ID is taken from the projects table. The Probe ID field is selected by the protocol, depending on the previously selected project. Thus, only probes belonging to the project with ID 2 are available. Next, an interface is selected. Interfaces are selected by the protocol, depending on the previously selected probe. Some settings can be selected from the list, while others should be manually specified. Each time, you need to click the green checkmark to save settings. After all settings are made, click the Start Task button to run a task.