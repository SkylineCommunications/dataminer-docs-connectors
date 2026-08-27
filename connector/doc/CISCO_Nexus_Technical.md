---
uid: Connector_help_CISCO_Nexus_Technical
---

# CISCO Nexus

The Cisco Nexus switches are modular and fixed-port network switches designed for data centers. With this connector, you can monitor and control these switches in DataMiner.

## About

This help page only applies from range **1.0.2.x onwards**, except the section on the IGMP page, which was included in range 1.0.4.x. Sections describing the **Element Settings** page, the **Interactive CLI** page, the **GNMI Settings** page, and the **Debug Page** apply from version **3.0.9.x onwards**.

The connector uses an **SNMP** main connection to monitor the device. In addition, depending on the configuration, it can communicate with the device via **SSH**, **NX API** (HTTPS), **gNMI**, and **APIC** (HTTPS). The connector also supports the **DataMiner Connectivity Framework (DCF)**.

From version **3.0.0.3 onwards**, this connector uses an external DLL, **Renci.SshNet.dll**, to be able to communicate via SSH.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

> [!NOTE]
> An SNMPv3 variant of this connector is available in range 1.0.3.x/1.0.4.x. For that variant, the SNMPv3 settings (username, security level, authentication type and password, privacy type and password) need to be configured instead of the community strings.

### Initialization

To use the SSH, NX API, gNMI, and interactive CLI functionality of the connector, configure the following settings on the **Element Settings** page, in the **SSH/NX API Configuration** section:

- **User Name** and **Password**: The SSH credentials of the device. These shared credentials are used for all SSH, NX API, gNMI, and CLI operations.
- **NX API Version**: The NX API version, by default *1.0*. This could change after firmware updates.
- **Command Timeout Time**: The maximum wait time (in milliseconds) for a command response.
- **NX API Use Cookie**: Determines whether a session cookie is reused for NX API requests.
- **SSH Port**: The port used for the SSH connection.

The **Communication Status** parameter on the **Interactive CLI** page reflects the result of the last communication attempt using these credentials (see [Interactive CLI page](#interactive-cli-page)).

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

## How to Use

### General page

This page displays general information about the device, such as the **Name**, **Location**, **CPU Usage**, and **Memory Usage**.

It also contains the **Reset Device** button, which resets the Cisco Nexus device, and the following page buttons:

- **ICMP...**: Displays a page with all ICMP statistics.
- **TCP...**: Displays a page with all TCP statistics.
- **UDP...**: Displays a page with all UDP statistics.
- **System Services...**: Displays a page listing the state of the services of each OSI layer.
- **Copy Configuration...**: Displays a page that allows you to generate a CISCO configuration copy.
- **DCF Settings...**: Displays a page with the DCF-related settings.

### Interactive CLI page

With the interactive Command Line Interface (CLI), commands can be sent to the device through SSH or via the NX API (from version 3.0.0.4 onwards). The credentials configured on the **Element Settings** page are used for this.

This page contains the following parameters:

- **CLI Communication Type**: Allows you to select either *CLI (SSH)* or *NX API*. Based on the selection, the CLI commands will be sent via SSH or via HTTPS.
- **Communication Status**: The result of the last communication attempt for all communication based on the SSH credentials (SSH, NX API, gNMI, and CLI). Possible values: *Disconnected*, *Connected*, *Server Timeout*, and *Authentication Failed*.
- **Add Command**: Adds a new command to be executed.
- **Command History**: Table containing all the recently executed commands and their output.
- **Command Entries to Keep**: Allows you to set the maximum number of rows visible in the Command History table.
- **Total Communication Issues**: The total number of detected communication issues present in the Command History table.
- **Clear Command History**: Clears the Command History table entries.

> [!NOTE]
> On systems where authentication is handled by a slow AAA/TACACS setup (e.g. when configured TACACS servers are unreachable), the authentication verdict from the device can take longer than the configured **Command Timeout Time**. In that case, the connector will report *Server Timeout* instead of *Authentication Failed*.

### Element Settings page

This page centralizes the communication configuration of the connector:

- The **SSH/NX API Configuration** section contains the shared SSH credentials and related settings (see [Initialization](#initialization)).
- The **Debug Page Visibility** toggle (*Disabled*/*Enabled*) controls whether the hidden [Debug Page](#debug-page) is displayed.

The page also contains the following page buttons:

- **Polling Configuration...**: Displays a page where you can enable or disable the polling of the different device features.
- **GNMI Settings...**: Displays the [GNMI Settings page](#gnmi-settings-page).
- **SSH Configurations Saver...**: Displays a page where you can configure the automatic saving of the device configuration via SSH.

### Debug Page

This page is hidden by default. To make it visible, enable the **Debug Page Visibility** toggle on the **Element Settings** page.

The page contains debug functionality, including the **Traps...** page button, which displays a page with the trap debug information.

### GNMI Settings page

Version 3.0.5.x of the connector introduces support for **OpenConfig** data collection via **gNMI**. This can be used to update some columns of the **Detailed Interface**, **Interface Rx**, and **Interface Tx** tables. When this is used, the data from SNMP will be removed in those tables and filled in with the values retrieved via gNMI.

The **GNMI Settings** page can be accessed via the **GNMI Settings...** page button on the **Element Settings** page. It contains the following parameters:

- **Data Source Port**: The port used for the gNMI connection.
- **Client Certificate** (optional): The client certificate used for the gNMI connection.

The gNMI connection uses the polling IP of the element and the SSH credentials configured on the **Element Settings** page.

> [!NOTE]
> gNMI should only be used with CISCO Nexus devices running version 10.2(7)/10.3(4) or higher. When gNMI is used in a DataMiner System with multiple Agents, you currently have to make sure you only have one Communication Gateway DxM active in the system (pending a fix to avoid that every Communication Gateway will make a connection).

### Sensor page

This page contains the **Sensor** table, which lists the type, scale, and present value of each sensor.

### System Health page

This page contains the following tables:

- **Fan**: Displays the operational status of all the fans.
- **Power Status**: Lists the power-related administrative status and operational status of the manageable components in the system.
- **CPU Memory Pool**: Displays overall CPU statistics.
- **NV Memory Pool**: Displays information regarding the RAM.

### PTP page

The Precision Time Protocol (PTP) pages display information regarding this functionality (from version 3.0.0.10 onwards). PTP polling uses the SSH credentials configured on the **Element Settings** page.

The **PTP Feature - Operational Status** parameter indicates the state of the PTP feature on the device, as reported by the "show feature" command. Possible values: *Enabled*, *Disabled*, *Unknown*, *Installed*, *Uninstalled*, and *Enabled (Not Running)*.

This page contains the following subpages:

- **PTP Clock**: Displays parameters regarding the clock.
- **PTP Interfaces**: Displays the Foreign Master Records and PTP Interfaces tables.
- **PTP Grandmaster**: Displays parameters related to the grandmaster clock.
- **PTP Time Sync**: Displays parameters related to the time sync.
- **PTP VLAN**: Displays the VLAN table.
- **PTP Corrections**: Displays the PTP Corrections table.

### Interface Detailed page

This page contains the **Detailed Interface** table. This table provides general information about each interface.

From version **1.0.3.7 onwards**, the polling period of the **Detailed Interface** table (as well as the **Interface Rx** and **Interface Tx** tables) can be configured using the **Detailed Interface Polling Interval** parameter. The default value of this parameter is *2 minutes*. Its possible values range between 30 seconds and 1 hour.

From version **3.0.3.1 onwards**, you can add or delete VLANs from an interface via the right-click menu.

### Interface Rx page

This page contains the **Interface Rx** table, which contains the input statistics of each interface.

### Interface Tx page

This page contains the **Interface Tx** table, which contains the output statistics of each interface.

### L2 L3 Interface page

This page contains the **L2 L3 Interface** table. The table shows the administratively requested and actual operating configuration for switch port interfaces.

### PoE page

This page displays the **PoE** table. This table contains information about power Ethernet ports on a Powered Sourcing Equipment (PSE) device. Some settings can be configured in this table, such as the maximum amount of power that the PSE will make available for the powered device.

### BGP page

This page displays the **BGP Peer** table. This table contains information about the connections with BGP peers. Some settings can be configured in this table, such as the time intervals for the ConnectRetry and KeepAlive timer.

### HSRP page

This page contains the **HSRP Group** table, which displays information about each HSRP group for each interface.

### OSPF page

This page contains general information regarding the Open Shortest Path First protocol.

The page also contains the following page buttons:

- **Area-Stub Area**: Displays a page containing the **Area** and **Stub Area** tables. The Area table displays the configured parameters and cumulative statistics of the attached areas of the router. The Stub Area table contains the set of metrics that is advertised by a default Area Border Router in a stub area.
- **LSDB**: Displays the **LSDB** table, which displays information about the Link State Database of the OSPF process.
- **Interface**: Displays a page containing the **Interface**, **Interface Metric**, and **Virtual Interface** tables.
- **Host**: Displays a page containing the **Host** table, which displays the metrics of the hosts that the router will advertise as host routes.
- **Neighbor**: Displays a page with the **Virtual Neighbor** and **Non Virtual Neighbor** tables.

### IP page

This page displays general IP statistics such as **requests**, **discards**, and **fragment fails**.

The page also contains the following page buttons:

- **IP Route**: Displays a page containing the **IP Route** table.
- **IP Statistics**: Displays a page with the **IP System Statistic Input** and **IP System Statistic Output** tables.
- **ARP**: Displays a page containing the **ARP** table.
- **IP Multicast**: Displays a page containing the **IP Multicast Interface** and **IP Multicast SSM Range** tables. The first table can be used to manage the multicast protocol active on an interface. The second table can be used to create and manage the range(s) of group addresses to which SSM semantics should be applied.

### IGMP page

This page contains two tables, the **IGMP Interface** and **IGMP Cache** tables. Both tables display the interface description in the index column.

From version **3.0.9.x onwards**, the "show ip igmp snooping groups" command (disabled by default) can be used to fully populate the **IP IGMP Snooping** table.

### NBM page

This page contains the **NBM Interfaces Bandwidth** table.

NBM flow statistics are retrieved via the **APIC** controller, using HTTPS communication.

> [!NOTE]
> Because of rounding issues in the device itself, bit rates may be slightly inaccurate. Because of this, bandwidth utilization can exceed 100% without dropped bytes indication. Keep this in mind when configuring alarm templates.

### VTP VLAN page

This page displays the **VTP VLAN** and **VTP Internal VLAN** tables.

The page also contains the following page buttons:

- **VTP Authentication**: Displays a page containing the **VTP Authentication** table. The table shows the authentication information of VTP for the local system.
- **VTP Management Domain**: Displays a page containing the **VTP VLAN Management Domain** table. This table shows information on the management domains for the local system.
- **VTP Statistics**: Displays a page with the **VTP Statistics** table.
- **VTP Edit Control**: Displays a page that contains the **VTP Edit Control** table. This table allows you to control the editing of the VLANs for a particular management domain.
- **VTP VLAN Membership**: Displays a page with the **VLAN Membership** table.
- **VTP VLAN Status**: Displays a page with general VTP information such as the **VTP Version** and **VTP Maximum VLAN Storage**.
- **VTP VLAN Trunk Port**: Displays a page that contains the **VLAN Trunk Port** table. This table shows information on the VLAN trunk ports of the local system.

## DataMiner Connectivity Framework

From version **1.0.2.1** onwards, the CISCO Nexus connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g., a manager).

### Interfaces

#### Dynamic Interfaces

Physical dynamic interfaces:

- For each Ethernet interface in the **Detailed Interface** table (2800), a physical dynamic interface of type **inout** is created.
- For each VLAN in the **VLANs (DCF Interfaces)** table (7400), a physical dynamic interface of type **inout** is created.

## Notes

- From version 3.0.9.x onwards, an **NX API cache** is available for all NX API-related operations, reducing the number of requests towards the device.
- From version 3.0.9.x onwards, an **InterApp message** is available that allows DataMiner Automation scripts to send NX API requests through the connector.
