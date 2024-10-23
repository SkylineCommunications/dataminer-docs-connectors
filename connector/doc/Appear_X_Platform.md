---
uid: Connector_help_Appear_X_Platform
---

# Appear X Platform

The Appear X Platform connector allows users to configure and display information from the Appear X10/X20 Chassis and its associated module cards. 

> [!NOTE]
> This connector is the successor of the **AppearTV X20 platform** connector which will be gradually phased out and eventually become deprecated. New greenfield deployments are strongly advised to use the new **Appear X platform** connector instead.

In the U.S. market, the same chassis is also offered under the Sencore brand, with the following model names: **Sencore DMG-3200** (X10 Chassis), **Sencore DMG-4100**, and **Sencore DMG-4200** (X20 Chassis).

The connector establishes an **HTTP connection**, utilizing the MMI, IpGateway, XGER, ASI, SDI APIs, and Prometheus endpoints to retrieve and configure device data. Information is exchanged in JSON format.

The connector operates sequentially, requesting data from the device, processing responses, and displaying the results. Users can send configuration requests and receive updated information in real-time.

## About

### Version Info

| Range | Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x **[SLC Main]** |-     |-     |-       |

### Product Info

| Range | Card Type | Supported (Card) Firmware | API Version | Supported System Release |
|--|--|--|--|--|
|  | IP Switch Control (SWx)  | SW 3.10 | MMI API 4.1+ | SR 5 |
|  | IP I/O (SWx)             | SW 3.22 | IP Gateway API 1.31+ | SR 7 |
|  | IP I/O (IPx)             | SW 3.22 | IP Gateway API 1.31+ | SR 7 |
|  | SRT (IPx)                | SW 1.12 | IP Gateway API 1.31+ | SR 10 |
|  | IP 2022 Coder (ECx)      | SW 3.12 | XGER API 2.40+ | SR 7 |
|  | IP 2110 Coder (ECx)      | SW 1.16 | XGER API 2.40+ | SR 7 |
|  | SDI Decoder (ECx)        | SW 6.2 | XGER API 2.40+ | SR 8 |
|  | SDI Encoder (ECx)        | SW 5.24 | XGER API 2.40+ | SR 7 |
|  | SDI Transcoder (ECx)     | SW 2.2 | XGER API 2.40+ | SR 8 |
|  | SDI I/O (SIx)     | SW 2.14 | SDI API 2.17+ | SR 7 |
|  | IP JPEG XS TS Encoder (IPx) | SW 1.8 | HipEnc API 1.2+ | SR 8 |
|  | IP JPEG XS TS Decoder (IPx) | SW 1.10 | HipDec API 1.3+ | SR 9 |
|  | ASI I/O (SIx)            | SW 2.14 | ASI API 1.17+ | SR 7 |
|  | DVB-S/2/X (SRx)          | SW 2.12 | S2XIn API 2.40+ | SR 7 |
|  | DVB-S/2/X (SMx)          | SW 3.22 | S2XOut API 2.40+ | SR 7 |
|  | Scrambler (CAx)          | SW 2.6 | API 1.5+ | SR 7 |
|  | Descrambler (DSx)        | SW 2.4 | Descr API 1.1+ | SR 7 |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | Yes | Yes | - |   |

## Configuration

### Edit Element parameters

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Element Configuration parameters

### API login credentials

Once you've finished the new element wizard and have an element created with this connector or protocol, you need to navigate to the **General** \> **Authentication** page available in the DATA pages section of the element. Here you can specify the API account (username and password) which the element needs to use for gaining authenticated API access.

> [!IMPORTANT]
> Only after successful API login the element will be able to establish proper communication with the Appear X platform API.

#### Configurable API Versions

It is possible to configure a specific API version for each card type. To do so, go to the **General** \> **Module Config** page.  
Increasing the API version will result in extra data being filled in if that API version is supported on the chassis.

### Redundancy

When the Appear Chassis is configured with 2 MMI boards, the device is able to present the API's we are consuming with DataMiner on IP interfaces of both MMI boards. This will bring the possibility to DataMiner to implement API level redundancy where we will automatically switch over to the secondary IP interface if we detect that the first one becomes unavailable or unresponsive.

The setup of this API level redundancy can be found on the following pages of an active Appear X platform element: **General** \> **Redundancy**

### Configurable API Polling

Through element page **General** \> **Poll Manager** the user is able to tailor the API requests issued by DataMiner towards the Appear X platform API. Specific API endpoints can be enabled/disabled as well as updated with a different polling frequency.

### DCF Connections

#### External Connections

- **[IP Physical Ports]** connection property of type **[inout]**.
- **[IP Coder Interfaces]** connection property of type **[inout]**.
- **[IP JPEG XS Interfaces]** connection property of type **[inout]**.
- **[ASI Input Ports]** connection property of type **[in]**.
- **[ASI Output Ports]** connection property of type **[out]**.
- **[SDI Input Ports]** connection property of type **[in]**.
- **[SDI Output Ports]** connection property of type **[out]**.
- **[S2X Input Ports]** connection property of type **[in]**.
- **[S2X Output Ports]** connection property of type **[out]**.

### Automation

It's possible to interface with this connector and all available cards by using the available Appear-X-ConnectorApi.

> [!NOTE]
> To make use of the Inter Application Framework (InterApp) from any automation script, please install the Appear X application which can be downloaded from the catalog.

## How to use

### General

This page displays the **Chassis Cards Table**, which contains one row per card in the chassis, detailing **Serial**, **Name**, **Hardware**, **Software**, **Slot**, **Features**, **Licenses**, and **State** information.

The following page buttons are available:

- **Authentication**: This page displays the current authentication status and allows you to specify a **Username** and **Password** to connect to the device.
- **Redundancy**: The chassis can have 2 management boards with two separate IP addresses to communicate with. On this subpage, you can specify the redundant IP address and port to be polled for the second gateway in case the first IP gateway goes into timeout. If a redundant IP is configured, the connector will try and switch to this address if timeouts occur.
- **Module Config**: It is possible to also select the implemented API version per card. Increasing the API version for a card will result in extra data being retrieved from the device.
  For compatibility reasons, the lower API version can be selected to ensure a functional connector in case you are not running a higher API version yet.

### Alarms

This page displays two tables, the **Active Alarms Table** and **Alarms History Table.** These contain information regarding the alarm **Name**, **Severity**, **Time Set** and, for cleared alarms in the history table, **Time Clear**.

### Web Interface

The web interface page is only accessible when the client machine, hosting the DataMiner Cube application, has network access to the device web GUI.

### Backplane Media

This page displays the **Flow Sources Table**, with information about the service **ID**, **Name**, **Bitrate** status, **CC Errors**, **RTP Errors**, and **Slot** of the flow source.

> [!TIP]
> All Parameters within the connector called 'Source' or 'Source Selection' use the Display Key references to this Flow Sources Table.  
> To create or edit items, it suffices to look up the correct flow source within this table and provide the display key as input.

### Output Service Config

This page displays the content of all Outputs configured with the chassis.  
Currently supported types: **IP**, **SRT**, **Modulator**.

> [!TIP]
> Adding a new service to an existing output can be done from the subpage 'Add Output Content'.

> [!TIP]
> To Replace the existing content of an output, edit the 'Source' parameter [1705] within the 'Output Contents' table. This action is the same as **Replace Content** from the Web Interface.

This page also allows to configure and manage the following Output related content through a right-click context menu action:

- PID Component Filtering
- Component Generation
- Extra PMT Descriptors

### Output Redundancy Config

This page allows you to manage the redundancy settings per Output or Output Service.  
Currently supported types: **IP**, **SRT**, **Modulator**.

The Redundancy Settings table contains details on which Source is currently active and when or how to switch to the backup.
The Redundant Sources table contains the configured backups per output.

Adding a new backup to an existing Output or Output service can be done through the 'Add Input Backup Source'.

### Output Mapping Config

This page allows you to add extra PID Mapping to existing outputs through a right-click context menu action.  
Currently supported types: **IP**, **SRT**, **Modulator**.

### IP Ports

This page contains two tables with information about **physical and virtual ports**.

There are 3 sub-pages available with information on the IP Interfaces connected to the Ports:

- IP Interfaces
- IP Coder Interfaces (IP 2022/IP 2110)
- IP JPEG XS Interfaces

### ASI Ports

Contains an overview of all ASI ports, indicating for each port whether it is configured as **Input** or **Output**. This table also allows you to adjust this configuration.

### SDI Ports

This page contains the **Cards Info Table**, **SDI IO Physical Ports Table** and **Status Tables**.

### S2X Ports

This page allow you to manage the amount of demodulators per port and tune the port according to the **LNB Frequency**, **LNB DC Voltage** and **LNB 22KHz Tone**.

### IP Inputs

This page displays the **IP Inputs Table** with configurable information related to the IP inputs.

This page contains the following page button:

- **Add Input**: Allows you to add a new input to the selected IP Switch card. To do so, you must specify the **Label**, **Type** (*Single* or *Seamless*), **Analyze Mode** (*DVB*, *MPEG* or *RTP*), **Slot**, and **Interface ID**, **IP** and **Port** for the selected type.

### IP Outputs

This page displays the **IP Outputs Table** with configurable information related to the IP outputs.

This page contains the following page buttons:

- **Add Output**: Allows you to add a new output to the selected IP Switch card. To do so, you must specify the **Label**, **Type** (*Single* or *Cloned*), **Service**, **Slot**, and **Interface ID**, **IP** and **Port** for the selected type.

### IP Output TS Status

The total overview of all IP Outputs are listed here with their respective **effective bitrates**.
Per Output, the list of services with their outgoing configurations are visible.
Per Output/Service, the list of pids with their outgoing configuration, bitrate and CC Errors are visible.

### SRT Inputs

This page displays the **SRT Inputs Table** with configurable information related to the SRT inputs.
The Input Status is available as well showcasing the **Bitrate** and **Socket State**.

> [!NOTE]
> The Status information is only available through the Prometheus API Endpoint on the chassis. Please verify if the Prometheus setting has been enabled. This can also be enabled under the **General > Module Overview Config page**.

### SRT Outputs

This page displays the **SRT Outputs Table** with configurable information related to the SRT inputs.

### SRT Output TS Status
The Output Status is available per output showcasing the **Bitrate** and **Socket State**.
Per Output, the list of services with their outgoing configurations are visible.
Per Output/Service, the list of pids with their outgoing configuration, bitrate and CC Errors are visible.

> [!NOTE]
> The Status information is only available through the Prometheus API Endpoint on the chassis. Please verify if the Prometheus setting has been enabled. This can also be enabled under the **General > Module Overview Config page**.

### Encoder Services

This page contains the **Encoder Services**, **Audio Encoder Services**, and **VANC Services** tables. The Audio Encoder Services table links the data with encoder services and audio profiles. The VANC Services table links the data with encoder services and VANC profiles.

The page contains the page buttons **Add IP/SDI Encoder Service**, **Add IP/SDI Audio Encoder Services**, and **Add IP/SDI VANC Services**, which can be used to add new entries to the tables.

The **IP/SDI Options** are applicable for the different card types, IP (ECx210) and SDI (ECx100). To delete one or more table entries, use the right-click menu.

### Encoder Services - Overview

This page contains a tree control for the **Encoder Services** and **Audio Encoder Services** per encoder service.

### Decoder Services

This page contains the **Decoder Services** and **Audio Decoder Services** tables.
The page contains two page buttons, **Add Decoder Service** and **Add Audio Decoder Services**, which can be used to add new entries to the tables.

To delete one or more table entries, use the right-click menu.

### Decoder Services - Overview

This page contains a tree control for the **Decoder Services** and **Audio Decoder Services** per decoder service.

### Input Profiles

This page contains the **Input Profiles** table. Via the **Add Input Profile** page button, you can add new entries to this table.
To delete one or more table entries, use the right-click menu.

### Output Profiles

This page contains the **Output Profiles** table. Via the **Add Output Profile** page button, you can add new entries to this table.
To delete one or more table entries, use the right-click menu.

### Video Profiles

This page contains the **Video Profiles** table. Via the **Add Video Profile** page button, you can add new entries to this table.
To delete one or more table entries, use the right-click menu.

### Audio Profiles

This page contains the **Audio Profiles** table. Via the **Add Audio Profile** page button, you can add new entries to this table.
To delete one or more table entries, use the right-click menu.

### VANC Profiles

This page contains the **VANC Profiles**, **VANC Services** and **Teletext Pages** tables. The VANC Services table links data with encoder services and VANC profiles.

For each of the tables, a page button is available that allows you to add more entries to the table.
To delete one or more table entries, use the right-click menu.

### Color Profiles

This page contains the **Color Profiles** table. Via the **Add Color Profile** page button, you can add new entries to the table.
To delete one or more table entries, use the right-click menu.

### Multi Services

This page displays two tables.

- The **Multi Services** table lists the current services with detailed information, including the current profile used by each service.
- The **Service Profiles** table contains all the data about the profiles. For each profile, the audio and video resolution are displayed.

Note: To retrieve the information on this page, an **additional external DLL is required**. This DLL must be added **in the ProtocolScripts folder**.

### ASI I/O

This page contains the **ASI Input** and **ASI Output Table**.

> [!NOTE]
> To configure the contents of the ASI Output, please refer to the *Output Service Config*, *Output Redundancy Config*, and *Output Mapping* pages.

### S2X Input

This section contains an overview of all Demodulators with their configuration (**Port**, **Frequency**, **Symbol Rate**, **State**, ...) as well as status information (**Lock**, **Bitrate**, ...).
More detailed information on the contents received from the tuned Demodulators can be visited on the following pages:

- S2X Input Descrambling
- S2X Input Services

### S2X Output

This page contains an overview of the **S2X Ports**, related **Port Profiles** and **Modulators**.  
Status data per port can be viewed on the **S2X OUT Physical Port Status** Table.

### Scrambler

Overview of all **Conditional Access Groups** and configured **Scrambled Services** available per slot.

### Descrambler

Overview of all **descrambled services**. Possible to manage or add descrambled services by using the *Flow Descrambling* section on this page.

### Flow Engineering

Reserved tables for integration with the Flow Engineering solution.