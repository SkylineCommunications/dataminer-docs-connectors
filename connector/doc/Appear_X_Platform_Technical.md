---
uid: Connector_help_Appear_X_Platform_Technical
---

# Appear X Platform

## About

The Appear X Platform connector allows users to configure and display information from the Appear X10/X20 chassis and its associated module cards.

> [!IMPORTANT]
> This connector is the successor of the **[AppearTV X20 platform](https://catalog.dataminer.services/details/7bb327a7-0844-4c2b-b5bc-fbfd4e3bc8de)** connector, which will be gradually phased out and will eventually become deprecated. For new greenfield deployments, we strongly recommend using this **Appear X platform** connector instead.

On the U.S. market, the same chassis is also offered under the Sencore brand, with the following model names: **Sencore DMG-3200** (X10 chassis), **Sencore DMG-4100**, and **Sencore DMG-4200** (X20 chassis).

The connector establishes an **HTTP connection**, utilizing the MMI, IpGateway, XGER, ASI, SDI APIs, and Prometheus endpoints to retrieve and configure device data. Information is exchanged in JSON format.

The connector operates sequentially, requesting data from the device, processing responses, and displaying the results. Users can send configuration requests and receive updated information in real-time.

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

#### Range 1.0.0.x

| Card Type                   | Supported (Card) Firmware | API Version          | Supported System Release |
|-----------------------------|---------------------------|----------------------|--------------------------|
| IP Switch Control (SWx)     | SW 3.10                   | MMI API 4.1+         | SR 5                     |
| IP I/O (SWx)                | SW 3.22                   | IP Gateway API 1.31+ | SR 7                     |
| IP I/O (IPx)                | SW 3.22                   | IP Gateway API 1.31+ | SR 7                     |
| SRT (IPx)                   | SW 1.12                   | IP Gateway API 1.31+ | SR 10                    |
| IP 2022 Coder (ECx)         | SW 3.12                   | XGER API 2.40+       | SR 7                     |
| IP 2110 Coder (ECx)         | SW 1.16                   | XGER API 2.40+       | SR 7                     |
| SDI Decoder (ECx)           | SW 6.2                    | XGER API 2.40+       | SR 8                     |
| SDI Encoder (ECx)           | SW 5.24                   | XGER API 2.40+       | SR 7                     |
| SDI Transcoder (ECx)        | SW 2.2                    | XGER API 2.40+       | SR 8                     |
| SDI I/O (SIx)               | SW 2.14                   | SDI API 2.17+        | SR 7                     |
| IP JPEG XS TS Encoder (IPx) | SW 1.8                    | HipEnc API 1.2+      | SR 8                     |
| IP JPEG XS TS Decoder (IPx) | SW 1.10                   | HipDec API 1.3+      | SR 9                     |
| ASI I/O (SIx)               | SW 2.14                   | ASI API 1.17+        | SR 7                     |
| DVB-S/2/X (SRx)             | SW 2.12                   | S2XIn API 2.40+      | SR 7                     |
| DVB-S/2/X (SMx)             | SW 3.22                   | S2XOut API 2.40+     | SR 7                     |
| Scrambler (CAx)             | SW 2.6                    | API 1.5+             | SR 7                     |
| Descrambler (DSx)           | SW 2.4                    | Descr API 1.1+       | SR 7                     |

> [!NOTE]
> To create or remove the DVE for a card, toggle the *DVE State* column in the **Module Overview Table** within the element. By default not exported.

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | Yes             | Yes                 | -                 | - [Appear X Platform - IP IO](xref:Connector_help_Appear_X_Platform_-_IP_IO)<br/>- [Appear X Platform - ASI IO](xref:Connector_help_Appear_X_Platform_-_ASI_IO)<br/>- [Appear X Platform - Coder](xref:Connector_help_Appear_X_Platform_-_Coder)<br/>- [Appear X Platform - Demodulator](xref:Connector_help_Appear_X_Platform_-_Demodulator)<br/>- [Appear X Platform - Modulator](xref:Connector_help_Appear_X_Platform_-_Modulator)<br/>- [Appear X Platform - Scrambler](xref:Connector_help_Appear_X_Platform_-_Scrambler)<br/>- [Appear X Platform - Descrambler](xref:Connector_help_Appear_X_Platform_-_Descrambler) |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

#### API Login Credentials

When you have created an element with this connector , navigate to the **General** > **Authentication** data page of the element, and specify the API account (username and password) that the element needs to use to gain authenticated API access.

> [!IMPORTANT]
> Only after a successful API login, will the element be able to establish proper communication with the Appear X platform API.

#### Configurable API Versions

It is possible to configure a specific API version for each card type. To do so, go to the **General** > **Module Config** page.

Increasing the API version will result in extra data being filled in if that API version is supported on the chassis.

### Redundancy

When the Appear Chassis is configured with 2 MMI boards, the device is able to present the APIs DataMiner is consuming on IP interfaces of both MMI boards. This will allow DataMiner to implement API-level redundancy. It will automatically switch over to the secondary IP interface if it detects that the first one becomes unavailable or unresponsive.

To set up this API-level redundancy, go to the **General** > **Redundancy** page of an active Appear X platform element

### Configurable API Polling

To tailor the API requests issued by DataMiner towards the Appear X platform API, go to the data page **General** \> **Poll Manager**. You can enable or disable specific API endpoints as well as set a different polling frequency.

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

<!-- ### Automation

It is possible to interface with this connector and all available cards by using the available **Appear-X-ConnectorApi**.

> [!NOTE]
> To make use of the Inter Application Framework (InterApp) from any automation script, install the Appear X application, which can be downloaded from the DataMiner Catalog. -->

## How to use

### General

This page displays the **Chassis Cards Table**, which contains one row per card in the chassis, detailing **Serial**, **Name**, **Hardware**, **Software**, **Slot**, **Features**, **Licenses**, and **State** information.

The following page buttons are available:

- **Authentication**: Displays the current authentication status and allows you to specify a **Username** and **Password** to connect to the device.
- **Redundancy**: The chassis can have two management boards with two separate IP addresses to communicate with. On this subpage, you can specify the redundant IP address and port to be polled for the second gateway in case the first IP gateway goes into timeout. If a redundant IP is configured, the connector will try and switch to this address if a timeout occurs.
- **Module Config**: On this subpage, you can select the implemented API version per card. Increasing the API version for a card will result in extra data being retrieved from the device. For compatibility reasons, the lower API version can be selected to ensure a functional connector in case you are not running a higher API version yet.

### Alarms

This page displays two tables, the **Active Alarms Table** and **Alarms History Table**. These contain information regarding the alarm **Name**, **Severity**, **Time Set** and, for cleared alarms in the history table, **Time Clear**.

### Web Interface

The web interface page is only accessible when the client machine hosting the DataMiner Cube application has network access to the device web GUI.

### Backplane Media

This page displays the **Flow Sources Table**, with information about the service **ID**, **Name**, **Bitrate** status, **CC Errors**, **RTP Errors**, and **Slot** of the flow source.

> [!NOTE]
> All parameters within the connector that are named "Source" or "Source Selection" use display key references to this Flow Sources Table. To create or edit items, look up the correct flow source within this table and provide the display key as input.

### Output Service Config

This page displays the content of all outputs configured with the chassis. Currently supported types: **IP**, **SRT**, **Modulator**.

To add a **new service** to an existing output, go to the **Add Output Content** subpage.

To **replace the existing content** of an output, edit the **Source** parameter [1705] within the **Output Contents** table. This action is the same as the **Replace Content** action from the web interface.

You can also configure and manage the following output-related content through the right-click menu:

- PID component filtering
- Component generation
- Extra PMT descriptors

### Output Redundancy Config

This page allows you to manage the redundancy settings per output or output service. Currently supported types: **IP**, **SRT**, **Modulator**.

The **Redundancy Settings** table contains details on which source is currently active and when or how to switch to the backup. The **Redundant Sources** table contains the configured backups per output.

Adding a new backup to an existing output or output service can be done via **Add Input Backup Source**.

### Output Mapping Config

This page allows you to add extra PID mapping to existing outputs via the right-click menu. Currently supported types: **IP**, **SRT**, **Modulator**.

### IP Ports

This page contains two tables with information about **physical and virtual ports**.

Several subpages are available with information on the IP interfaces connected to the ports:

- IP Interfaces
- IP Coder Interfaces (IP 2022/IP 2110)
- IP JPEG XS Interfaces

### ASI Ports

This page contains an overview of all ASI ports, indicating for each port whether it is configured as **input** or **output**. You can also adjust this configuration in the table.

### SDI Ports

This page contains the **Cards Info Table**, **SDI IO Physical Ports Table**, and **Status Table**.

### S2X Ports

This page allows you to manage the number of demodulators per port and tune the port according to the **LNB Frequency**, **LNB DC Voltage**, and **LNB 22KHz Tone**.

### IP Inputs

This page displays the **IP Inputs Table**, with configurable information related to the IP inputs.

Via the **Add Input** page button, you can add a new input to the selected IP switch card. To do so, you must specify the **Label**, **Type** (*Single* or *Seamless*), **Analyze Mode** (*DVB*, *MPEG*, or *RTP*), **Slot**, and **Interface ID**, **IP**, and **Port** for the selected type.

### IP Outputs

This page displays the **IP Outputs Table**, with configurable information related to the IP outputs.

Via the **Add Output** page button, you can add a new output to the selected IP switch card. To do so, you must specify the **Label**, **Type** (*Single* or *Cloned*), **Service**, **Slot**, and **Interface ID**, **IP** and **Port** for the selected type.

### IP Output TS Status

This page lists all IP outputs with their respective **effective bit rates**.

Per output, the list of services with their outgoing configurations is shown, and per output/service, the list of PIDs with their outgoing configuration, bit rate, and CC errors is shown.

### SRT Inputs

This page displays the **SRT Inputs Table**, with configurable information related to the SRT inputs. You can view the Input Status, with the **Bitrate**, and **Socket State**.

> [!NOTE]
> The status information is only available through the Prometheus API endpoint on the chassis. To verify if the Prometheus setting has been enabled, go to the **General** > **Module Overview Config** page.

### SRT Outputs

This page displays the **SRT Outputs Table**, with configurable information related to the SRT inputs.

### SRT Output TS Status

For each output, you can see the Output Status, with the **Bitrate** and **Socket State**, as well as a list of services with their outgoing configurations.

In addition, per output/service, the list of PIDs with their outgoing configuration, bit rate, and CC errors is shown.

> [!NOTE]
> The status information is only available through the Prometheus API endpoint on the chassis. To verify if the Prometheus setting has been enabled, go to the **General** > **Module Overview Config** page.

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

This page contains the **VANC Profiles**, **VANC Services**, and **Teletext Pages** tables. The VANC Services table links data with encoder services and VANC profiles.

For each of the tables, a page button is available that allows you to add more entries to the table.

To delete one or more table entries, use the right-click menu.

### Color Profiles

This page contains the **Color Profiles** table. Via the **Add Color Profile** page button, you can add new entries to the table.

To delete one or more table entries, use the right-click menu.

### Multi Services

This page displays two tables.

- The **Multi Services** table lists the current services with detailed information, including the current profile used by each service.
- The **Service Profiles** table contains all the data about the profiles. For each profile, the audio and video resolution are displayed.

> [!NOTE]
> To retrieve the information on this page, an **additional external DLL** is required. This DLL must be added **in the ProtocolScripts folder**.

### ASI I/O

This page contains the **ASI Input** and **ASI Output Table**.

> [!NOTE]
> To configure the contents of the ASI Output, refer to the [Output Service Config](#output-service-config), [Output Redundancy Config](#output-redundancy-config), and [Output Mapping Config](#output-mapping-config) pages.

### S2X Input

This section contains an overview of all demodulators with their configuration (Port, Frequency, Symbol Rate, State, etc.) as well as status information (Lock, Bitrate, etc.).

More detailed information on the contents received from the tuned demodulators is available on the following pages:

- S2X Input Descrambling
- S2X Input Services

### S2X Output

This page contains an overview of the **S2X Ports**, related **Port Profiles** and **Modulators**.

Status data per port is available in the **S2X OUT Physical Port Status Table**.

### Scrambler

Here you can find an overview of all **Conditional Access Groups** and configured **Scrambled Services** available per slot.

### Descrambler

Here you can find an overview of all **descrambled services**. You can manage or add descrambled services using the **Flow Descrambling** section on this page.

### Flow Engineering

This page contains reserved tables for integration with the Flow Engineering solution.

