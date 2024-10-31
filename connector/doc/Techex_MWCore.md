---
uid: Connector_help_Techex_MWCore
---

# Techex MWCore

The Techex MWCore connector is an **HTTP-based** connector that integrates the **Techex TXCore** product (formerly known as MWCore).
The Techex TXCore platform manages TXEdges (formerly known as MWEdge) and captures telemetry data for real-time monitoring.

This connector offers a monitoring and configuration interface for the **Techex TXCore Platform**. 
Through the REST API, it enables operations on monitored Devices, Channels, MWEdges, Streams, Sources, and Outputs. 
Additionally, you can configure a **Statistics Connection** to provide telemetry data for sources and output sources, including **ETR290 statistics**.

Optionally, the connector can **export a DVE for each device** monitored by the Techex MWCore Platform.

> [!NOTE] 
> The Techex MWCore connector requires the DataMiner system to have an indexing database configured or use STaaS.

## 1. About

### 1.2. Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version (includes DCF integration). | - | - |
| 1.0.1.x [Obsolete] | Reformat of the MWEdge stream keys. | 1.0.0.2 | **Old trend and alarm data will be lost for Streams, Input Sources, and Outputs.** |
| 1.0.2.x [Obsolete] | - Single output/input is retrieved upon context menu operation instead of MwEdge polling. <br>- MWEdges are retrieved separately instead of all at once. <br>- Reverse foreign key relation between Streams Resources table and Streams table. | 1.0.1.19 | **Because NuGets are now used, the minimum DataMiner version is now 10.0.10.** |
| 1.0.3.x | - Statistics Connections table and "IP Connection <br>- Statistics Interface" connection removed. <br>- Columns added to the Servers Info table to enable the statistics interface for each server. | 1.0.2.3 | **Existing elements need to be reconfigured to account for the connection changes.** |
| 1.0.4.x [SLC Main] | - Secondary interface has been removed from element creation (additional MWCore nodes of the same cluster are now added in the connections table).<br>- Pages associated with SRM resources and debugging are now hidden by default. They can be displayed using the parameters on the "Debug" page.<br>- The debugging logs for the statistics interface have been enhanced (serilog is now used), and the default path is now the logging folder.<br>- The Sources and Output tables have been divided into configurations and metrics/statistics.<br>- Logger tables have been restructured to include more metrics and are now designed to use DirectConnection. This can be activated on the Statistics Configuration page by enabling the "Elastic Export".<br>- Support for the 2022-7 version has been added.<br>| 1.0.3.33 | **Existing elements need to be reconfigured to accommodate the connection changes. It is highly advisable to recreate the elements.** |

### 1.3. Product Info

| Range                             | Supported Firmware                             |
|-----------------------------------|------------------------------------------------|
| 1.0.0.x [Obsolete]<br>1.0.1.x [Obsolete]<br> 1.0.2.x [Obsolete] | **MWCore version:** 5.2.3, 5.2.4 <br> **MWEdges version:**  1.9.2, 1.9.3 |
| 1.0.3.x | **MWCore version:** 5.22.4 <br> **MWEdges version:** 1.24.1 |
| 1.0.4.x [SLC Main]| **MWCore version:** 5.22.4, 5.29.0 <br> **MWEdges version:** 1.24.1, 1.34.0 |

### 1.4. System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | Yes | Yes | - | [Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device) |
| 1.0.1.x | Yes | Yes | - | [Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device) |
| 1.0.2.x | Yes | Yes | - | [Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device) |
| 1.0.3.x | Yes | Yes | - | [Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device) |
| 1.0.4.x | Yes | Yes | - | [Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device) |

## 2. Configuration

### 2.1. Connections

#### 2.1.1. HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

This connection is used to perform the regular polling, to retrieve data from the device based on a request/response mechanism.

#### 2.1.2. HTTP Secondary Connection (Prior to Range 1.0.3.x)

This connector also uses a redundant HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

> [!NOTE] 
> This redundant connection is used for regular polling when the main connection fails. Starting from range 1.0.4.x, it is no longer in use. The 1.0.4.x range employs dynamic IPs and enables users to specify additional MWCore nodes within the same cluster in the Connections table.

### 2.2. Initialization

In order to initialize the connector, you need to specify the following input configuration on the **General** page and **Statistics Configuration** subpage:

**HTTP Communication**:

- **Username:** Name of the user used in the HTTP login operation.
- **Password:** Password of the user used in the HTTP login operation.

**Statistics Configuation**:
- **Client Certificate Path:** Path to the .pfx client certificate. Note that the .pfx certificate file contains both public and private keys.
- **Client Certificate Password:** Password of the client certificate related to the referred path.

> [!NOTE]
> Note that if the public and private key certificates are in the .pem format, they have to be exported to a .pfx file, as documented in [OpenSSL](https://www.openssl.org/docs/man1.0.2/man1/pkcs12.html) (e.g. openssl pkcs12 -inkey private_key.pem -in public_key.pem -export -out client_certificate.pfx).

In addition, note that *openssl.exe* comes alongside a [Git](https://git-scm.com/) installation.

### 2.3. Redundancy
From range 1.0.4.x [SLC Main], a connections table is available on the General page, allowing users to specify additional TXCore nodes for DataMiner to automatically connect to if the primary connection becomes unavailable. 
The first entry is automatically added and always matches the one defined in the element creation edit menu.

### 2.4. DataMiner Connectivity Framework

The Techex MWCore - Generic Device connector supports DCF usage. DCF can be implemented via the DataMiner DCF user interface and/or through DataMiner third-party connectors, such as a manager connector. This connector manages connectivity for all exported connectors.

**Interfaces type**: Virtual dynamic interfaces 
- **Output:** Created to interface with the DVE table with **interface type out**.

## 3. How to use - SLC Main version

The Techex MWCore connector offers management and monitoring capabilities for the Techex TXCore Platform. 
Configuration settings are retrieved through a polling mechanism that integrates with Techex's REST API (available at ```<URL>/doc/```). 
Additionally, a socket connection can be established with each TXCore node to asynchronously receive telemetry data from each TXCore node about the attached TXEdges. 
This connection uses client-certificate authentication.

The Techex MWCore also integrates an [InterApp library](https://github.com/SkylineCommunications/SLC-S-Techex_MWCore_ConnectorAPI), enabling the a running element to communicate with other DataMiner elements and automation scripts.
This library supports CRUD actions for streams, sources, and outputs.

The connector's layout is structured as follows.

### General
On the General page, users specify the username and password for connecting to TXCore. 
A connections table is available, allowing users to specify additional TXCore nodes for DataMiner to automatically connect to if the primary connection becomes unavailable. 
The active connection can be monitored via the Active connection parameter.

In the connections table, the first entry (with priority 1) is automatically added and always matches the one defined in the element creation edit menu. 
Users can also edit or force a specific connection to become active through the context menu. 
The state of the node address is monitored at 10-second intervals.

On the General's subpages:
- **Polling Configuration**: 
Users can define preferred polling settings, including the polling interval, edges to be polled, and fields to be retrieved. 
If the retrieved MWEdges list is empty, all edges will be polled simultaneously. 
Otherwise, a buffer mechanism is applied, and data for each edge will be polled individually. 
- **Statistics Configuration**: 
Users can specify the connection settings for statistics/telemetry data processing. 
Note that the "Export to Logger Tables" feature is only available for DataMiner systems with an indexing database (ElasticSearch or OpenSearch).
- **Thumbnail Configuration**:
Users can configure the desired settings for Thumbnails retrieval. 
If thumbnails are needed for a low-code app, the path can be updated to ```C:\Skyline DataMiner\Webpages\public\TechexMWCoreThumbnails```.
- **Debug**:
Users can enable more detailed logging specifically for statistics data, generating new log files in the specified folder with a rolling window of 2&nbsp;days and file size of 10&nbsp;MB.
Files are generated with in the following format: ```{Protocol.ElementName}-statisticslog[{DnsName}].txt```. 
For SRM integrations, users can enable the SRM Information parameter, making the SRM Resources page and its subpages visible in the element's data layout.

### Devices
The Devices page lists all devices monitored by TXCore. 
Here, users can also choose whether DataMiner should create a DVE for each detected device. 
If so, DVEs can be configured in the Configuration subpage.

### Channels
TXCore channels are listed and can be monitored in the Channels table available on this page. 
Channels can be added or edited through the subpages.

### MWEdges
The MWEdges page displays a table listing either all TXEdges or those specified on the Polling Configuration page. 
In this table, users can monitor the state of each edge, including addresses, licenses, number of streams, and more. 
The information for the monitored TXEdges is further detailed in the following subpages:

- **Streams**:
Lists streams of all monitored TXEdges. 
Streams can be added and deleted via the context menu. 
Streams can be edited directly from the table columns.
- **Sources**: 
Lists sources of all monitored TXEdges. 
Sources can be added and deleted via the context menu on the Sources table. 
Sources can be edited directly from the table columns. 
The sources statistics table is populated when the statistics connection is enabled, providing telemetry data such as bitrates, missing packets, and more.
- **Outputs**:
Lists outputs of all monitored TXEdges. 
Outputs can be added and deleted via the context menu on the Outputs table. 
Outputs can be edited directly from the table columns. 
The output statistics and output listener statistics tables are populated when the statistics connection is enabled, providing telemetry data such as bitrates, missing packets, and more.
- **ETR 290**:
The table on this subpage is populated when the statistics connection is enabled. 
It lists ETR messages related to the sources.
- **Sources States**:
Displays a table listing sources states, which is populated when statistics connection is enabled.
Users can choose to include all sources or only the active ones.
- **Outputs States**:
Displays a table listing outputs states, which is populated when statistics connection is enabled. 
Users can choose to include all outputs or only the active ones.

### Cluster Members
The Cluster Members page lists all nodes of the TXCore cluster. 
Here, users can monitor the health of each node, including memory, CPU, and disk usage, as well as the number of devices and TXEdges connected to each TXCore node.
Users can also enable the statistics interface from the table on this page and manually overwrite the IP address that DataMiner should use to open the statistics connection with the TXCore node by specifying the desired IP in the "Public IP Address" column.

If communication with a TXCore node fails more than a predefined number of times (monitored in the "Retries" column), the connection will be automatically disabled, and users will need to manually enable it again. 
The number of retries can be configured on the "General&nbsp;>&nbsp;Statistics&nbsp;Configuration" page.

### SRM Resources
On the SRM Resources page and its subpages, users will find tables that can be linked to SRM solutions. 
These resource tables are categorized into streams, sources, outputs, and ports. 
CRUD actions are available via the context menu. 
These tables are linked to their respective counterparts that hold the data retrieved from TXCore.

This page is only visible if the "SRM Information" parameter is enabled on the "General&nbsp;>&nbsp;Debug" page.

### Web Interface
Opens the TXCore web interface. The web interface is only accessible when the DataMiner host has network access to the TXCore platform.

## 4. Known Issues

### DataMiner is not displaying statistics/telemetry
In most cases the issue is related to firewall or to the certificate.

To test the firewall rules the following command can be run from the DataMiner host, where the \<TXCore node ip\> is replaced by the IP address ofthe node that want to receive telemetry data for, and \<port\> the port configured in TXCore for telemetry data (default: 7834)
In most cases, the observed issues are related to the firewall or the certificate. To test the firewall rules, run the following command from the DataMiner host, replacing \<TXCore node ip\> with the IP address of the node you want to receive telemetry data for, and \<port\> with the port configured in TXCore for telemetry data (default: 7834).

```console
Test-NetConnection -ComputerName <TXCore node ip> -Port <port>
```
> [!NOTE]
> Please note that, by default, DataMiner will use the IP address listed in the "IP Address" column of the Servers Info table, which is available on the Cluster Members page. 
It is known that Techex TXCore does not always provide the public IP of the node. 
If the IP provided by TXCore is not accessible from the DataMiner host, you can manually set the IP that DataMiner should use in the "Public IP Address" column of the same table.

After confirming that the DataMiner host can reach and connect to the desired TXCore node on the specified telemetry port, try enabling the statistics connection for the specified node on the cluster members page. If it fails, check the log file of the DataMiner element. If the issue is related to the certificate, a log message similar to the following should be present.

```console
2024/10/31 10:20:36.595|SLManagedScripting.exe|ManagedInterop|DBG|0|77|QA10000|FAILED: Processing Statistics Interface Notifications: System.Security.Cryptography.CryptographicException: The specified network password is not correct.

   at System.Security.Cryptography.CryptographicException.ThrowCryptographicException(Int32 hr)
   at System.Security.Cryptography.X509Certificates.X509Utils._LoadCertFromFile(String fileName, IntPtr password, UInt32 dwFlags, Boolean persistKeySet, SafeCertContextHandle& pCertCtx)
   at System.Security.Cryptography.X509Certificates.X509Utils.LoadCertFromFile(String fileName, IntPtr password, UInt32 dwFlags, Boolean persistKeySet, SafeCertContextHandle pCertCtx)
   at System.Security.Cryptography.X509Certificates.X509Certificate.LoadCertificateFromFile(String fileName, Object password, X509KeyStorageFlags keyStorageFlags)
   at System.Security.Cryptography.X509Certificates.X509Certificate2..ctor(String fileName, String password)
   at X509Certificates.GetClientCertificates(SLProtocol protocol)
   at QAction.TryCreateSession(SLProtocolExt protocol, IpConnection ipConnection)
   at QAction.RequestStatistics(SLProtocolExt protocol, IpConnection ipConnection, IpStatsDebugInfo debugInfo)
```

### Update the output by switching from one stream to another
TXCore allows users to update an output by switching from one stream to another within the same TXEdge. However, if an alarm exists in DataMiner before this action, the alarm description may still display the original stream after switching. Nevertheless, any alarm actions, such as clearing and escalation, will be properly updated.