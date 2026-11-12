---
uid: Connector_help_Techex_MWCore_Technical
description: "Configure Techex MWCore connections, authentication, redundancy, telemetry, TXCore monitoring, device DVEs, and troubleshooting in DataMiner."
---

# Techex MWCore

## About

The Techex MWCore connector is an **HTTP-based** connector that integrates the **Techex TXCore** platform (formerly known as MWCore) with DataMiner.

The Techex TXCore platform manages TXEdges (formerly known as MWEdges) and captures telemetry data for real-time monitoring.

Through the TXCore REST API, the connector monitors and configures devices, channels, TXEdges, streams, sources, and outputs. In addition, you can configure a **statistics connection** with each TXCore node to receive telemetry data for sources and outputs, including **ETR 290 statistics**.

Optionally, the connector can **export a DVE for each device** monitored by the TXCore platform.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the TXCore node.
- **IP port**: The IP port of the TXCore node (default: 443).
- **Bus address**: If the proxy server has to be bypassed, specify *BypassProxy*.

This connection is used for the regular polling, which retrieves data from TXCore based on a request/response mechanism.

#### HTTP Connection - Secondary (Prior to Range 1.0.4.x)

Prior to range 1.0.4.x, this connector also uses a redundant HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the secondary TXCore node.
- **IP port**: The IP port of the secondary TXCore node (default: 443).
- **Bus address**: If the proxy server has to be bypassed, specify *BypassProxy*.

This redundant connection is used for the regular polling when the main connection fails. From range 1.0.4.x onwards, this connection is no longer used. Instead, you can specify additional TXCore nodes of the same cluster in the **Connections** table on the **General** page (see [Redundancy](#redundancy)).

### Initialization

To initialize the element, configure the following parameters on the **General** page:

- **Username**: The name of the user used for the HTTP login.
- **Password**: The password of the user used for the HTTP login.

To enable the statistics connection, configure the following parameters on the **General** > **Statistics Configuration** subpage:

- **Client Certificate Path**: The path to the .pfx client certificate. The .pfx certificate file contains both the public and the private key.
- **Client Certificate Password**: The password of the client certificate at the specified path.

> [!NOTE]
> If the public and private key certificates are in the .pem format, export them to a .pfx file as documented in the [OpenSSL documentation](https://www.openssl.org/docs/man1.0.2/man1/pkcs12.html), for example with the command `openssl pkcs12 -inkey private_key.pem -in public_key.pem -export -out client_certificate.pfx`. The *openssl.exe* tool is included in a [Git](https://git-scm.com/) installation.

### Redundancy

From range 1.0.4.x onwards, a **Connections** table is available on the **General** page, where you can specify additional TXCore nodes for DataMiner to automatically connect to if the primary connection becomes unavailable. The first entry (with priority 1) is added automatically and always matches the connection defined in the element editor.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The information in this section applies to range 1.0.4.x and higher.

The Techex MWCore connector offers management and monitoring capabilities for the Techex TXCore platform.

Configuration settings are retrieved through a polling mechanism that integrates with the TXCore REST API (documented at `<txcore-ip-address>/doc/`). Additionally, a socket connection can be established with each TXCore node to asynchronously receive telemetry data about the attached TXEdges. This connection uses client certificate authentication.

The connector also integrates an [InterApp library](https://github.com/SkylineCommunications/SLC-S-Techex_MWCore_ConnectorAPI), which enables a running element to communicate with other DataMiner elements and Automation scripts. This library supports create, read, update, and delete actions for streams, sources, and outputs.

Below you can find more information about the different data pages available in the element.

### General

On this page, specify the username and password for connecting to TXCore during element initialization.

The **Connections** table allows you to specify additional TXCore nodes for DataMiner to automatically connect to if the primary connection becomes unavailable. The active connection is indicated by the **Active Connection** parameter.

The first entry in the **Connections** table (with priority 1) is added automatically and always matches the connection defined in the element editor. You can edit a connection or force a specific connection to become active via the right-click menu of the table. The state of each node address is monitored at 10-second intervals.

This page has several subpages:

- **Polling Configuration**: Allows you to define the polling settings, including the polling interval, the TXEdges to be polled, and the fields to be retrieved. If no TXEdges are specified, all TXEdges will be polled at once. Otherwise, a buffer mechanism is applied and the data for each TXEdge will be polled individually.

- **Statistics Configuration**: Allows you to specify the connection settings for the processing of statistics and telemetry data. Note that the **Export to Logger Tables** feature is only available for DataMiner Systems with an indexing database (Elasticsearch or OpenSearch).

- **Thumbnail Configuration**: Allows you to configure the settings for thumbnail retrieval. If thumbnails are needed for a low-code app, the path can be updated to `C:\Skyline DataMiner\Webpages\public\TechexMWCoreThumbnails`.

- **Debug**: Allows you to enable more detailed **logging** for statistics data. New log files are generated in the specified folder with a rolling window of 2 days and a file size of 10 MB, using the following file name format: `{Protocol.ElementName}-statisticslog[{DnsName}].txt`. The **Statistics Buffer State** parameter indicates whether DataMiner is struggling to handle the volume and frequency of the data pushed by TXCore (see below). For SRM integrations, you can enable the **SRM Information** parameter, which makes the SRM Resources page and its subpages visible in the element.

#### Telemetry Buffer

Telemetry data is sent to DataMiner asynchronously. To facilitate this, DataMiner establishes a dedicated connection with each TXCore node to receive the telemetry data for streams, sources, and outputs.

> [!IMPORTANT]
> To prevent issues caused by excessive data volumes and high frequency rates, the connector uses an **internal buffer** for message processing. This buffer can queue up to **300 messages**. Any message received when the queue is full will be dropped, and the **Statistics Buffer State** parameter will display *Overflow*. The parameter will revert to *Normal* once approximately 50% of the queue has been freed up and incoming messages can be added to the queue again. The system waits until 20% of the queue has been freed up before clearing the state, in order to avoid the alarm toggling.

### Devices

The Devices page lists all devices monitored by TXCore. Here you can select whether DataMiner should create a DVE for each detected device. If DVEs are created, you can configure them on the **Configuration** subpage.

### Channels

On this page, you can view and monitor the TXCore channels listed in the Channels table. Via the subpages, you can add or edit channels.

### MWEdges

The MWEdges page displays a table listing either all TXEdges or only the TXEdges specified on the **Polling Configuration** subpage. In this table, you can monitor the state of each TXEdge, including its addresses, licenses, number of streams, and more.

> [!NOTE]
> The bandwidth usage metrics (**Source Total**, **Output Total**, **Total Usage**, and **License Left**) are not retrieved through polling. Instead, DataMiner receives this data asynchronously via the statistics connections and periodically calculates the metrics based on the values available in the Sources and Outputs tables. This feature is **disabled by default**. To enable it, configure the **Total MWEdge Bitrate Calculation Interval** parameter on the **General** > **Statistics Configuration** subpage.

The information for the monitored TXEdges is further detailed on the following subpages:

- **Streams**: Lists the streams of all monitored TXEdges. You can add and delete streams via the right-click menu, and edit streams directly in the table columns. Via the right-click menu, you can also clear the statistics for all sources and outputs of the selected stream.

- **Sources**: Lists the sources of all monitored TXEdges. You can add and delete sources via the right-click menu of the Sources table, and edit sources directly in the table columns. Via the right-click menu, you can also clear the statistics for the selected source. When the statistics connection is enabled, telemetry data such as bit rates and missing packets is added to the Sources Statistics table.

- **Outputs**: Lists the outputs of all monitored TXEdges. You can add and delete outputs via the right-click menu of the Outputs table, and edit outputs directly in the table columns. Via the right-click menu, you can also clear the statistics for the selected output. When the statistics connection is enabled, telemetry data such as bit rates and missing packets is added to the Output Statistics and Output Listener Statistics tables.

- **ETR 290**: When the statistics connection is enabled, the table on this subpage lists the ETR 290 messages related to the sources.

- **Sources States**: The table on this subpage lists the source states (e.g., an error caused by a zero bit rate detected in the last 10 seconds). You can choose to include all sources or only the active ones.

- **Outputs States**: The table on this subpage lists the output states (e.g., an error caused by an invalid passphrase). You can choose to include all outputs or only the active ones.

### Cluster Members

The Cluster Members page lists all nodes of the TXCore cluster. Here you can monitor the health of each node, including memory, CPU, and disk usage, as well as the number of devices and TXEdges connected to each node.

In the table on this page, you can also enable the statistics interface for each node and override the IP address that DataMiner uses to open the statistics connection with that node by specifying the desired IP address in the **Public IP Address** column.

If communication with a TXCore node fails more than a predefined number of times (monitored in the **Retries** column), the connection will be disabled automatically, and you will need to enable it again manually. You can configure the number of retries on the **General** > **Statistics Configuration** subpage.

The **Statistics Status** column displays the current status of the statistics connection (*OK*, *Timeout*, or *Warning*):

- *Timeout* indicates that DataMiner has not received any communication, including keep-alives, from the TXCore node for longer than the rate limit configured on the **General** > **Statistics Configuration** subpage.

- *Warning* indicates that DataMiner has not received valid telemetry information from the TXCore node for longer than three times the configured rate limit.

### SRM Resources

The SRM Resources page and its subpages contain tables that can be linked to SRM solutions. These resource tables are categorized into streams, sources, outputs, and ports. Via the right-click menu, you can create, update, and delete resources.

These tables are linked to their respective counterparts containing the data retrieved from TXCore.

This page is only visible if the **SRM Information** parameter is enabled on the **General** > **Debug** subpage.

### Web Interface

This page displays the TXCore web interface. The web interface is only accessible when the client machine has network access to the TXCore platform.

## DataMiner Connectivity Framework

All ranges of the Techex MWCore connector support the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g., a manager).

Connectivity for all exported connectors ([Techex MWCore - Generic Device](xref:Connector_help_Techex_MWCore_-_Generic_Device)) is managed by this connector.

### Interfaces

#### Dynamic Interfaces

Virtual dynamic interfaces:

- **Output**: Created for the DVE table, with interface type *out*.

## Troubleshooting

### DataMiner Does Not Display Statistics or Telemetry

In most cases, this issue is related to the firewall or to the client certificate. To troubleshoot the issue:

1. Verify that the DataMiner host can reach the TXCore node on the telemetry port by running the following command from the DataMiner host:

   ```powershell
   Test-NetConnection -ComputerName <TXCore node IP> -Port <port>
   ```

   Replace `<TXCore node IP>` with the IP address of the node that has to send the telemetry data, and `<port>` with the port configured in TXCore for telemetry data (default: 7834).

   By default, DataMiner uses the IP address listed in the **IP Address** column of the table on the **Cluster Members** page. As TXCore does not always provide the public IP address of a node, this IP address may not be accessible from the DataMiner host. In that case, specify the IP address that DataMiner should use in the **Public IP Address** column of the same table.

1. Once you have confirmed that the DataMiner host can connect to the TXCore node on the telemetry port, enable the statistics connection for that node on the **Cluster Members** page.

1. If the connection still fails, check the log file of the element.

   If the issue is related to the certificate, the log will contain a message similar to the following:

   ```txt
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

   In that case, verify the **Client Certificate Path** and **Client Certificate Password** parameters on the **General** > **Statistics Configuration** subpage.

### Incorrect Alarm Description After Switching Streams

TXCore allows you to update an output by switching from one stream to another within the same TXEdge. If an alarm exists in DataMiner before this action, the alarm description may still display the original stream after the switch. However, any alarm actions, such as clearing and escalation, will be processed correctly.
