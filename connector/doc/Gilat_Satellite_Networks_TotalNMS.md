---
uid: Connector_help_Gilat_Satellite_Networks_TotalNMS
---

# Gilat Satellite Networks TotalNMS

The purpose of this connector is to monitor the Gilat Satellite Networks TotalNMS platform over HTTP using its northbound interface (SkyEdge II-c NBI).

The physical devices of the system are called CPE (Customer Peripheral Equipment) devices. This connector arranges CPE devices based on CPE groups, with managed groups as a subsection. For each CPE instance, a separate dynamic virtual element (DVE) will be created, which will display more detailed information (see [Gilat Satellite Networks TotalNMS - CPE](xref:Connector_help_Gilat_Satellite_Networks_TotalNMS_-_CPE)).

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware      |
|-----------|-------------------------|
| 1.0.0.x   | SkyEdge II-c NBI v5.5P2 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components                                                                                                                                | Exported Components                                                                                              |
|-----------|---------------------|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| 1.0.0.x   | No                  | Yes                     | - [Generic Ping](xref:Connector_help_Generic_Ping) connector version 3.1.2.5 or higher (supported from version 1.0.0.2 of this connector onward) | [Gilat Satellite Networks TotalNMS - CPE](xref:Connector_help_Gilat_Satellite_Networks_TotalNMS_-_CPE) |

## Configuration

### Connections

#### SNMP Connection - Traps

This connector uses a Simple Network Management Protocol (SNMP) connection to be able to retrieve alarm traps and requires the following input during element creation:

SNMP CONNECTION:

- **SNMP version**: SNMPv2
- **IP address/host**: The polling IP of the platform.

SNMP Settings:

- **Port number**: 162
- **Get community string**: public
- **Set community string**: private

#### HTTP Connection

This connector uses an HTTP connection to be able to interact with the NBI and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: The polling IP of the platform.

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

### Initialization

A newly created element will only start polling data when both **User Name** and **Password** are filled in on the General page. In case no data traffic is shown in Stream Viewer, verify if both are correctly filled in.

By default, the communication between the element and a different element that runs the **Generic Ping** connector is disabled. This means that no ping-related data will be available. To make ping-related data visible, follow the steps mentioned in the "Settings Page" section below.

### Redundancy

No redundancy is defined in the connector.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector uses SOAP calls to retrieve most of its data. Alarms are retrieved via SNMP traps and ping information is collected through the Generic Ping connector. To be able to retrieve alarms, make sure that **SNMP traps** are **enabled on the TotalNMS platform**.

This connector can export a child connector based on the retrieved data (see "Exported Components" above).

To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting View \> Stream Viewer. A healthy element will show Groups 900-903, Groups 905-907, and Group 915 in Stream Viewer. Optionally, Group 904, Group 914, Groups 908-910, and Groups 912-913 can also be shown.

### General Page

The General page contains the **Login** field, where you can enter the credentials needed to perform a valid request to the NBI. When both username and password are accepted by the TotalNMS platform, data will start entering the element and tables will be filled in.

Below the Login field, the total **Number of CPEs** and **Active CPEs** are displayed. Each row of the Active CPEs table represents the corresponding managed group.

The connector can request basic CPE information using different approaches, depending on the number of CPE devices. If this number is less than or equal to 100, the GetCPEsByManagedGroup bulk API call is used. When more CPE devices are available, the GetCPEbyID API call is used.

### Topology Page

The Topology page shows a **tree structure** of all the components and their parent/child components. Select a component to view more detailed information on the right side of the page.

### Network Segments Page

This page contains data regarding the network segments. This includes the general **Network Segments** table, the **VLANs** table, and the **FWD Links** table. Both the NS VLANs table and the FWD Links table are linked to the Network Segments table by means of the Network Segment ID.

### Profiles Page

This page contains the **SLAs** table, which contains basic SLA information.

### CPEs Page

This page contains a table listing the CPE devices that are currently known to the TotalNMS platform.

If a CPE device was known earlier but no longer seems to be present in the **CPEs** table, you should check the **CPE DVEs** table. You can find this table by clicking the **CPE DVEs Configurations** page button at the bottom of this page.

CPE DVEs will be created for devices for which the **DVE Created** parameter is set to *Enabled*. For new CPE devices that are added to the table, this parameter is set to *Disabled* by default. You can change this parameter setting on the **Settings** page.

After startup, the Severity column can indicate the *Unknown* state. This is expected behavior, caused by the fact that the Severity column will only be updated when an alarm trap is received. For example, when a *Major Open* alarm comes in, *Major* will be the severity. When after a number of minutes the same alarm comes in with the *Cleared* state, the new severity will be *Normal*.

To see the **Subscriber Public IPv4 address**, make sure a valid VLAN ID is selected. The VLAN ID can be selected on the Settings page. In case the dropdown list is empty, open Stream Viewer and wait until Group 906 is displayed in the column on the left. When Group 906 has been executed successfully, try again. The dropdown list should now contain the available IDs. There is no need to change the other parameters located on that page.

The CPEs table also contains some important reports such as **Forward Data Throughput**, **Return Data Throughput**, **Forward Es/N0**, and **Return Tx Capability C/N0**. The mechanism used to poll these reports can produce several log lines in the element logging. It can take a couple of minutes until these columns are filled in completely after an element restart. This is all expected behavior. If an entire report column indicates "N/A", check the CPE report polling toggle buttons on the Settings page. When a CPE report polling toggle button is set to *Disabled*, the corresponding column will show "N/A".

Similar to the report columns, it can take a couple of minutes until the columns **Administrative State**, **Last Modification**, **Latitude**, and **Company Name** are filled in completely after an element restart. Executing HTTP SOAP calls in a loop takes time and seems to put extra load on the NBI. From time to time, this results in responses that have an unexpected status code. If you notice that a column has been *Not initialized* for a while already, open the Stream Viewer and check which group contains a request with an unexpected status code.

### CPE DVE Configurations Page

By default, the **CPE DVEs** table will contain the entries of all the CPE devices that were retrieved at least once after element creation. This table is used to generate the dynamic virtual elements. When a CPE device was returned earlier but is not currently known to the TotalNMS (because of maintenance for example), the corresponding entry in the CPE DVEs table will indicate *Deleted* (in the State column). Both the DVE and the data that has been retrieved for it will be kept in memory and can be reused when the CPE device returns.

The corresponding Delete button only becomes available when the State column indicates that a CPE is *Deleted* or *Not initialized*. This allows you to fully delete the entry, along with the DVE and all its data.

The **Automatic DVE Removal** toggle button at the top of the CPE DVEs Configuration page can be enabled to use the CPE DVEs table as an exact copy of the CPEs table. In other words, when this is enabled, the CPE DVEs table will constantly be in sync with the CPEs table. In this situation, when a CPE device was known earlier but is currently not returned by the TotalNMS, the corresponding entry will be removed along with all data that was retrieved for it.

In the **View** column, you can enter the name of the parent view you want to assign to the DVE. This view must be **created in advance**. Be careful to avoid unintentional white spaces in the name. When the view is left blank, the DVE will be created under the same view as the parent element.

### Alarms Page

The alarms page contains the **Alarms** table. By default, when an alarm for example changes from the state *Open* to the state *Cleared*, the table will contain two entries. In this situation, the alarm will not be overwritten.

The **Automatic Alarm Removal** toggle button at the top of the page can be enabled to remove an alarm when its state changes to *Cleared*. That way, the table will only contain currently active alarms.

Note: The Alarms table will **only show up to 100 alarms**, and all **alarms can be removed** from the table at any time if needed.

### Active Reports Page

Each row in the **Active Reports** table represents a report that is actively being polled.

If you click the **Add Report** button in the lower right corner of the page, a new entry will be added with a default element type and element name. Once the entry has been added to the table, select a **Name** and a **Graph Type** to start polling the report. For now, only the Element Type CPE is supported. By default, the report will be polled for all CPE devices. You can request a report for a specific CPE instance as well by selecting the corresponding element name.

All active reports can be removed from the table at any time if needed. You can also clear the entire table in one go with the **Clear Reports** button, located in the lower right corner of the page. When the Active Reports table is completely empty, Group 910 will not be polled.

Keep in mind that the TotalNMS database itself gets an update regularly. During such an update, it is not possible to poll a report, and the corresponding value will indicate N/A. After the next poll cycle, the value should contain a number again.

When a report seems to be missing even though it was present in the table at some point in time, check the CPEs table. The Active Reports table will be kept in sync with the CPEs table. This means that report requests configured for CPE devices that are no longer known by the TotalNMS will be removed.

### Settings Page

An element that runs this connector is able to communicate with a different element that runs the Generic Ping connector (from version 3.1.2.5 onwards) in order to display ping information such as **Average Success**, **Packet Loss**, and the **Jitter** of a CPE device.

To set this up, follow these steps:

1. Enable the **Generic Ping Connection** toggle button.
1. Fill in the **Generic Ping Element ID**. You can find this ID by right-clicking the Generic Ping element name in the Surveyor and selecting *Properties*. The ID, e.g. 772/914, will be displayed in the Properties window.
1. Select the **VLAN ID** assigned to the CPE devices you want to know ping information about.

When you have done so, new entries will be added to the Ping table of the element that runs the Generic Ping connector. Each entry represents a CPE device. If you want to retrieve the ping information for all CPE devices, select the VLAN ID that is assigned to all CPE devices. To do so, check the VLAN ID column of the CPEs table.

A log line will be added to the element log when a ping sync was triggered. A ping sync means that the Ping table of the linked Generic Ping element is synchronized with the CPEs table of the Gilat element.

For each report that is part of the CPEs table, a **Polling toggle button** is available. With these toggle buttons, you can disable or enable the polling of the CPE reports. For instance, if you disable the CPE Forward Data Throughput Polling toggle button, the CPE Forward Data Throughput will not be polled. This means that the Forward Data Throughput column of the CPEs table will show N/A and Group 908 will not be displayed in Stream Viewer.

Note that the **minimum required version of the Generic Ping connector is** **3.1.2.5**.

On the Settings page, you can also find settings related to CPE DVE creation:

- **Automatic CPE DVE Creation**: Allows you to set the **DVE Created** parameter to *Enabled* for all future added CPE devices. By default, is set to *Disabled*.
- **Enable/Disable All DVEs** Allows you to set the state of all CPE devices in the table to *Enabled* or *Disabled*.

### Reports

The connector is able to poll the following reports. Report responses often contain values for multiple graph types. The Used Graph Type column indicates which graph type is processed and therefore visible on the element.

| Name | Element Type | Used Graph Type | Ignored Graph Type(s) | Description |
| ---- | ------------ | --------------- | ---------------------- | ----------- |
| FWD Throughput | CPE | Data | FWD Traffic, C2P | The total CPE FWD Throughput, also the graph shows the total DATA throughput and total C2P throughput. |
| RTN Throughput | CPE | Data | RTN Traffic, C2P | The total CPE RTN Throughput, also the graph shows the total DATA throughput and total C2P throughput (Burst traffic/resources only). |
| FWD Rx Level | CPE | Last FWD received Es/N0 | Minimum FWD received Es/N0, Maximum FWD received Es/N0 | The CPE FWD signal to noise measurements as reported by the CPE to the HSP. |
| RTN Tx Capability C/N0 | CPE | Last Tx Capability C/N0 | Last Tx Continuous Capability C/N0 | The CPE RTN C/N0 capability as measured at the hub by the HSP. |
| FWD Backbone Retransmissions | Network Segment | FWD Backbone Retransmissions |  | The ratio between the number of retransmitted FWD Backbone packets and the total number of transmitted FWD Backbone packets (including the retransmitted ones). |
| RTN Backbone Retransmission | Network Segment | RTN frame loss |  | The ratio between the number of retransmitted RTN Backbone packets and the total number of transmitted RTN Backbone packets (including the retransmitted ones). |
| FWD Link Throughput and Limit | Network Segment | Throughput | Throughput Limit | The total Forward data transmission rate in Kbps and the theoretical limit as calculated by the Integrated Performance Manager (Available bit rate). |
| RTN Link Throughput Available and Limit | Network Segment | Throughput | Limit, Available | The total Return data transmission rate in Kbps and the theoretical limit as calculated by the Hub-Side Processor (Burst traffic/resources only). |
| L2 Online CPEs | Network Segment | Online (L2) |  | Number of CPEs that are currently logged on to all the Network Segments in the Network/Teleport/Satellite/RF Cluster/Single Network Segment/Hub-Side Processor. |
| L3 Online CPEs | Network Segment | Online (L3) |  | Number of CPEs that are currently logged on to the Dynamic Provisioning System. |
| VLAN Throughput | Network Segment | FWD Throughput VLAN - VLAN ID, RTN Throughput VLAN - VLAN ID |  | Summed up traffic of all Very Small Aperture Terminals in the same Virtual Local Area Network per Network Segment. |
| CPEs FWD Maximal Capability | Network Segment | ModCod - xPSK x/x |  | Distribution of CPEs linked to the Network Segment/Hub-Side Processor according to their maximal Forward ModCod capability. |
| CPEs RTN Maximal Capability | Network Segment | Slot Type - TRF x xxxKsps QPSK x/x xK |  | Distribution of CPEs according to their maximal Return slot type capability per Network Segment/Hub-Side Processor. |
| FWD Link Load per MG | Network Segment | AVG - Managed Group ID |  | The ratio between the demands on the Forward link to the actual traffic per Managed Group in the network overload scenario (per Network Segment/Dynamic Provisioning System). |
| FWD Link Throughput Utilization | Network Segment | Utilization |  | The ratio, in %, between the total transmitted data in the Network Segment and the total available throughput in the Network Segment Forward channel. |
| MCR AGC Level | Network Segment | Current: NGMCR 100 | Minimum: NGMCR 100, Maximum: NGMCR 100 | The Master Control Room's Automatic Gain Control attenuator value (current, minimum and maximum). |
