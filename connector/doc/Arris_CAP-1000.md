---
uid: Connector_help_Arris_CAP-1000
---

# Arris CAP-1000

The **Arris CAP-1000** connector is an **HTTP** connector that can be used to monitor and configure the **Arris CAP-1000**.

The version (**1.0.0.1**) of the connector supports software version **v4.1** with **XML protocol 4.0**.

## About

The **Arris CAP-1000** is an IP-centric MPEG-2/MPEG-4 digital stream processor capable of high-quality rate shaping, splicing, and multiplexing. It features field-replaceable processing modules, dual hot-swappable power supplies, and fan trays, all in a **single 1-RU chassis**.

There are multiple ways to monitor and configure the settings for the Arris CAP-1000. This connector is based on The **CherryPicker Element Manager**. The CherryPicker Element Manager is a browser-based Java interface that enables you to **remotely configure, control, and monitor each Arris CAP-1000** unit in your network.

### Version Info

| Range              | Key Features                                    | Based on | System Impact |
|--------------------|-------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                | -        | -             |
| 1.0.1.x [SLC Main] | Display key added to the Alarms Overview Table. | -        | -             |

### Product Info

| Range   | Device Firmware Version             |
|---------|-------------------------------------|
| 1.0.0.x | **v4.1** with **XML protocol 4.0**. |
| 1.0.1.x | **v4.1** with **XML protocol 4.0**. |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 1.0.1.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses a HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device (default: *80*).
- **Device address**: The device address (default: *ByPassProxy*).

### Initialization

Before all the functions of the element are available, you need to **log in**. On the **Device** page, click the **Security** button and fill in the correct **username** and **password**. After that, click the **Login** button, and the element will start working.

When the element is stopped or restarted later, the username and password will be remembered, so this step only needs to be done once. When the element is started and a username and password have already been provided, you only need to click **Login**.

## Usage

### Device

The **Device** page displays general information about the device (**name**, **version**, and **model**.). On this page, you can also **reboot** the device, **restart the core**, or **restart the controller**. The **Security** page button is also available here (see [Initialization](#initialization)).

The **Device Redundancy Slate** parameter makes it possible to configure redundancy slate for the entire device. This will put all output muxes and programs in the selected redundancy slate configuration. This is also possible on a mux or program level, but this is available on different pages.

This page also has several subpages, which you can access through page buttons:

- **Permissions**: Displays the **Users** table, containing a list of users available to login on the device. You can also add new users to the system.
- **SimulCrypt**: Displays the **CA Systems** and **ECM Generators** tables, containing the available CA systems and ECM Generators. You can also add new CA System and ECM Generators.
- **Preferences**: Displays the **PRED** and **DVBSI** tables with information related to Video Tables.
- **Ports**: Displays the **ASI Ports** and **Ethernet Ports** tables. The **ASI Ports** table can be used to configure the ASI port settings for the Arris CAP-1000. The **Ethernet Ports** table is used to view and configure the network configuration.
- **Hardware Profiles**: Displays the **Hardware** table. This table contains an entry for all the hardware components available on the system.
- **Licenses**: Displays the **Licenses** table, which has an entry for every license that is used by the system. You can also add a new license to the system.
- **Statistics**: Displays the latest information related with number of active input multiplexers, output multiplexers etc.
- **Security**: Allows you to configure the **user name** and **password** to **log in** to the system. You can also **log out** on this page.

### Recoders

This page displays the **Recoder Cluster Allocation** and **Device Resources** tables. These tables can be used to view, configure, and manage recoder used for optimal allocation.

### Interfaces

The **Interfaces** page displays two tables. The first table is the **Interfaces** table, who has an entry for every **input** and **output**. This is a basic table that displays the interface type and name.

The other table on this page is the **Mux** table. This table contains information for every mux that is connected to an interface specified in the **Interfaces** table. This table also contains a setting for redundancy slate, but here it is the **Mux Redundancy Slate**, which means the setting will be configured on a mux level. All the programs connected to this mux will get the same configuration when changed.

As of version 1.0.1.11, **Create Output Mux** is changed to **Output Mux**, and an additional page, **Input Mux**, is available. The **Output Mux** page is for creating new Output muxes and editing existing ones. The **Input Mux** page is for creating new input muxes and editing existing ones.

### Multiplexers

The **Multiplexers** page displays the **Multiplexers** and **Tables** tables. The **Multiplexers** table has information related to every multiplexer and is also used for the creation of new multiplexers. As of version 1.0.1.11, it also allows for the editing of the mux name and the deletion of the mux. The **Tables** table has information related to video tables and the corresponding ID of PIDs, PMT, and PCR.

### Program

The **Program** page contains the **Program** table. This table has an entry for every program. As of version 1.0.1.11, it also allows for the editing of the program number and name. The **Program Redundancy Slate** column can be used to set the slate configuration on a program level. Setting this will only change the setting for the chosen program. Note that these settings can only be done for programs connected to an output interface.

### PID

The **PID** table contains an entry for all the PIDs that are connected to a program.

### Grooming

The **Grooming** page contains the **Grooming Definitions**, **Grooming Info**, and **Program Intervals** tables. These tables have the information about the grooming available on the system.

There are also two subpages in order to create a new **Unreferenced Table** and also a new **Unreferenced Stream**.

- **Create Unreferenced Table**: Information need to create a new Unreferenced Table.
- **Create Unreferenced Stream**: Information to create a new Unreferenced Stream.

### Create Groom

The Create Groom page displays the **Inputs** and **Outputs** tables. These two tables are needed in order to create a new groom. To create a **new groom**, select one input and one output in each table.

This page also has a **Settings** subpage where you can change some parameters of the groom.

### Alarm

The **Alarm** page displays all the alarms that are generated by the system. This table is almost exactly the same as the **Alarm** table in The CherryPicker Element Manager.

The **Alarm** table has a customizable **IDX** column (v. 1.0.1.9) that allows for different formats of that column via dropdown. The default format is **Primarykey/Description**.

Alarms can be cleared in two different ways:

- You can clear alarms one by one. For this, use the setting in the **Cleared** column. However, note that event alarms cannot be cleared.
- You can clear all alarms at once, using the **Clear All Alarms** button, which is situated underneath the **Alarms** table.

The **Alarms Overview** table has the information about the multiplexer alarms.

### Service Overview

The **Service Overview** page contains a tree view for every interface. This is an easy way to quickly find a certain program or PID. The treeview is constructed as follows: Interface \> Muxes \> Programs \> PIDs.

For each program, it is also possible to find information about its **Programs**, **Tables**, and **Alarms**.

### Grooming Overview

The **Grooming Overview** page contains a tree view for every grooming. This is an easy way to quickly find a certain program. The tree view is constructed as follows: Groom \> Programs.

For each groom, it is also possible to find information about its **Grooming Definitions** and **Program Intervals**.

### Web Interface

This page displays the web interface of the device.

Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

### Number of sessions

There is a limitation to the number of active sessions for the **Arris CAP-1000**. Only **8 sessions** can be active at a time. Therefore, it is very important to **log out** of the element (via the **Security** button) before stopping it. Otherwise the sessions will not be terminated, and after a few stops, this could result in an error that can only be solved by restarting the entire device.

When you restart the device using the buttons on the Device page, you do not need to log out, because the element will reconnect with the device as soon as it is rebooted. However, when you restart the device using another method than the one described above (for example The CherryPicker Element Manager), it is important that you log in again manually (even if the element displays that you are currently logged in).
