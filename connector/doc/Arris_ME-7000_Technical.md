---
uid: Connector_help_Arris_ME-7000_Technical
---

# Arris ME-7000

## About

The **Arris ME-7000** is a multi-channel video processing platform used in broadcast and cable headend environments. It encodes, transcodes, and multiplexes video, audio, and data services for delivery over IP or RF networks.

This connector communicates with the device over its HTTPS XML API and an SNMP interface.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTPS connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the Arris ME-7000 device.
- **IP port**: The HTTPS port of the device. Default: *443*.
- **Device address**: Not used. If a proxy server must be bypassed, specify *BypassProxy*.

#### SNMP Connection

This connector also uses a Simple Network Management Protocol (SNMP) connection for SNMP-based parameters. No additional configuration is required beyond the IP address shared with the HTTP connection.

### Initialization

After the element is created, configure the following parameters on the **General** page:

- **Username** and **Password**: Credentials for authenticating with the device's XML API. Polling does not begin until valid credentials have been entered.
- **Protocol Version** (optional): The XML API version to use when communicating with the device. Default: *4.9*. The connector auto-detects the correct version at login and updates this parameter automatically, so manual configuration is not usually required.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Polling

The connector authenticates to the device via an XML API over HTTPS. On startup, it reads the configured credentials and attempts to log in. Once logged in, it enables all timer-driven polling groups.

Polling cadence:

- **60 s**: Full device configuration (encoders, muxes, interfaces, PSIP, routing) and heartbeat.
- **5 min**: Active alarms list.
- **60 min**: Alarm settings, licenses, users, configuration file lists, software update packages, and audio/video configuration file libraries.

If the device becomes unreachable, the connector stops polling and retries the login every 60 seconds automatically. Many pages include write parameters and action buttons that apply changes to the device immediately and re-poll the configuration on success.

### General and System

- The **General** page displays device information such as **Software Version**, **Platform Name**, and **Protocol Version**, and the **Users** table listing all user accounts and their roles.

  - The **Protocol Version** parameter reflects the XML API version in use. In range 1.1.2.x, this is set **automatically** at login. The default value is *4.9*.
  - The **Add User** subpage adds new accounts.
  - The **Change Password** subpage changes a user's password (select the username first).

- The **System** page displays system parameters including **Name**, **Mode**, **Version**, **Model**, **Memory Utilization**, **Time Format**, **Time Zone**, and **Reset Filter Time Remaining**. It also allows you to configure the **SDT Path**.

  - The **NTP Settings** subpage contains the **NTP Server Table**, the active NTP server, controls to add new servers, and the **NTP Sync** and **Reboot Device** buttons.

### Network and Infrastructure

- The **Network** page displays the **GigE Interface Port Configuration Table** for configuring MPEG status, port status, virtual IP address, virtual netmask, DSCP, routing protocol, and MPEG output per interface.

  - The **Port Analyzer** subpage configures the port analyzer direction, source, destination, and speed.
  - When active, the **PAN Configuration Edit Mode** switches to *Read Only* and editing is locked until canceled.
  - The **Static Routes** subpage manages the **Static Routes Table** with per-row and bulk delete.

- The **SNMP** page displays SNMP configuration including the agent status and version, community tables (read and read/write), trap listeners, NMS hosts, SNMPv3 settings, and the SNMP security level.

  > [!NOTE]
  > To change the **SNMP Version** from v2 to v3, at least one entry must exist in the **SNMPv3 User Settings Table** first. Changing the **SNMP Security Level** clears the table and requires a new user entry. When **Accept All Hosts** is enabled, NMS hosts cannot be added manually.

- The **Hardware** page displays the **Hardware Profile Table** and the **SFP Information Table**.

### Security and Sessions

- The **Security** page displays the RADIUS status, local fallback setting, number of retries, the **Authentication Servers Table**, and the **Accounting Servers Table**.

  - The **Add Server** subpage adds a new security server by specifying the type, IP address, timeout, and shared secret.

    > [!IMPORTANT]
    > Use the **Test** button to verify connectivity before clicking **Add**. The test result is shown on the subpage.

- The **Sessions** page displays the **Sessions Table**, listing the active HTTPS sessions between the connector and the device.

### Device Management

- The **Software Updates** page displays the **Software Updates Table** along with controls for executing a software update: update source (*Remote Server* or *File System on PC*), server communication protocol (*SCP* or *TFTP*), server IP address, build identifier, remote credentials, and local folder path.

- The **Tools** page displays the **License Status Table** and the **License Options** control (*Generate License Request*, *Apply License File*, *Revoke License File*).

- The **Backup & Restore** page allows you to configure the **Backup File Path** and **Restore Options**, and to execute a backup via the **Backup** button.

### Redundancy

The **Redundancy** page displays CRED parameters including **Mode**, **Backup Device IP Address and Name**, **Auto Fail Back**, **Checking Frequency**, **Check Frequency Type**, **Start Checking On**, **Checking Duration**, **Backup Table**, and **Primary Device IP Address to Backup**.

Buttons allow you to **Cancel** or **Apply** failback settings and trigger a **Failback** or **Failover**.

### Alarms, Status, and Thumbnails

- The **Alarms** page displays the **Alarms Table** listing all active and historical alarms.

  - **Maximum History Entries** and **Maximum History Days** control when entries are removed.
  - The **Alarm Settings** subpage contains the **Alarm Settings Table**.

- The **Status** page displays operational counters: **Total Critical/Major/Minor Alarms**, **Total Configured Rate**, **Total Active/Inactive Input Multiplex**, **Total Groomed Program**, **Chassis Redundancy Status**, **Device Date/Time**, **Software Started Since**, **Database Status**, **Write Pending**, **Last Write**, **Last Failed Write**, and **Failed Write Reason**.

- The **Thumbnails** page displays the **Thumbnails Table**, listing the name, group, multiplexer, and URL for each encoder output thumbnail.

### Files

The **Files** page displays the **Files Configuration Table**.

- The **Audio** subpage contains the **Custom Audio Files Table** and **Audio Files Table**.

- The **Video** subpage contains the **Video Files Table** and **Custom Video Files Table**.

### Inputs

- The **BNC Inputs** page displays five tables covering SDI/BNC inputs: **Input BNC Lines**, **SDI Input Multiplex**, **SDI Input Programs**, **SDI Input Program Streams**, and **ARIB Input Channels**.

  - The **Add SDI Multiplex** subpage adds new SDI multiplex entries.

- The **GigE Inputs** page displays five tables covering GigE inputs: **GigE Interfaces Port Configuration**, **GigE Input Multiplex**, **GigE Tables**, **GigE Input Mux Programs**, and **GigE Input Streams**.

  - The **Add GigE Input Multiplex** subpage adds new GigE multiplex entries.

  > [!NOTE]
  > In range 1.1.2.x, the row identifier format for the **GigE Input Mux Programs** and **GigE Input Streams** tables changed to a compound key (multiplex reference + program ID). Existing trending and alarm templates targeting specific rows in these tables must be reconfigured after upgrading from range 1.1.0.x.

- The **Input Tree** page displays a tree control for navigating through all configured inputs hierarchically.

### Outputs

- The **Outputs** page displays four tables: **GigE Output Multiplex**, **GigE Output Programs**, **GigE Output Tables**, and **GigE Output Program Streams**.

  - The **Add CBR Group** subpage adds new CBR output multiplex groups.
  - The **CVCT & TVCT** subpage allows you to edit the **Cable Virtual Channel Table** and **Terrestrial Virtual Channel Table**.

- The **PSIP** page displays the **PSIP Table** with GPS UTC offset, daylight saving configuration, and interval settings.

- The **TOT** page displays the **Time Offset Table** per country/region entry.

  - The **TOT Settings** subpage allows you to add new entries to the Time Offset Table.

- The **Network Descriptors** page displays the **Network Information**, **Network Name Descriptor**, **Linkage Descriptor**, **Multilingual Network Name Descriptor**, **Private Descriptors**, and **Stuffing Descriptor** tables.

- The **NIT Transport Streams** page displays the **Transport Streams**, **Services List Descriptors**, **Satellite/Cable/Terrestrial Delivery System Descriptor**, **Logical Channel Number Descriptors**, **Stuffing Descriptor**, and **Private Descriptor** tables.

- The **Output Tree** page displays a tree control for navigating through all configured outputs hierarchically.

### Processing and Encoding

- The **Grooming** page displays the **Input Grooming**, **Output Programs Grooming**, and **Files Grooming** tables.

  - The **Create Groom** button creates a new entry
  - The **Refresh** button updates the input list.
  - The **Grooming Settings** subpage allows you to configure **Priority**, **Maximum Bitrate**, and **Minimum Bitrate**.

  > [!NOTE]
  > Only one program can be configured at a time in the grooming tables.

- The **Processing** page displays the **Output Programs Processing**, **Grooming Output Programs**, **Backup 2 Output Programs**, **STATMUX Processing**, and **MBR Processing** tables.

- The **Encoding Configuration** page displays the **Encoder Video Properties**, **Encoder Audio Properties**, **Encoding SCTE-35 Configuration**, **Encoder OP-47 Configuration**, **Teletext Configuration**, and **Encoder WSS Configuration** tables.

- The **Metadata** page displays the **Audio Metadata Table** with audio encoding metadata per stream.

## Notes

This connector uses a single HTTPS connection for all 31 XML API sessions. All request and response bodies are XML documents. The SNMP connection runs in parallel for SNMP-based parameters; SNMP timeouts do not affect the HTTP polling flow.
