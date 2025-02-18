---
uid: Connector_help_Anevia_ViaDemand
---

# Anevia ViaDemand

Monitors and controls which content should be played, for how long, and when. You can also edit the settings of the tasks.

The connector is the same as the scheduled play of the webpage; it gives an overview of all the tasks that are scheduled to play, with the possibility to create a new task or edit a task.

## Configuration

### Connections

This connector uses an **HTTP** connection and requires the following input during element creation:

**SERIAL CONNECTION**:

- **IP address/host**: The polling IP or URL of the destination, e.g. *10.24.5.10*.
- **IP port**: The port of the destination, e.g. *80*.

### Initialization

On the **General** page, click the **Credentials** page button and configure the **username** (by default *admin*) and the **password** (by default *paris*).

## Usage

### General

Similar to the General page of the Anevia Soap System connector, this page contains an overview of general server parameters, including the **RAM memory** parameters, **API version**, and CPU usage.

The page also allows you to reboot the server.

Via the **Credentials** button, you can set the username en password to communicate with the server.

### Configurations

On this page, you can export and import configurations from/to the device. The **Import/Export Status** parameter shows the status of the export/import.

The exported configurations are stored in the folder `C:\Skyline DataMiner\Documents\Anevia ViaDemand`.

### Tasks

This page gives an overview of all the tasks that are scheduled to play.

It also allows you to create a new task to play.

In the table, you can see the **task ID**, which is used to edit a task.

Via the parameter **Select Task**, you can choose a task and then click **Edit** to edit that task. On the **Edit** page, you can fill in all the settings for the task and then choose to either create a new task or edit this task. Some task parameters cannot be edited, e.g. **source** and **destination**, so editing these will automatically result in a new task.

### Disk Overview

This page is also in the Anevia Soap System connector.

On this page, you can find information about the used memory of the hard disks.

### Interfaces

This page is also in the Anevia Soap System connector.

On this page, you can find information about the different interfaces that you can use to play a scheduled task.

### Web Interface

This page shows the webpage of the device.
