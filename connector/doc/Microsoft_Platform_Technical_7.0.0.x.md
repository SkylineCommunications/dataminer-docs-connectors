---
uid: Connector_help_Microsoft_Platform_Technical_7.0.0.x
---

# Microsoft Platform

The Microsoft Platform connector enables the monitoring of servers that run the Microsoft Windows OS.

## About

The Microsoft Platform connector empowers organizations to achieve comprehensive, real-time monitoring of your Microsoft Windows-based servers. Leveraging Windows Management Instrumentation (WMI), this connector provides deep visibility into system performance, health metrics, and operational status, ensuring proactive management and swift resolution.

## Key Benefits

- Broad Compatibility: Supports all versions of Microsoft Windows, ensuring seamless integration across diverse server environments.

The Microsoft Platform connector gathers key performance indicators from a server running the Microsoft Windows OS. To accomplish this, the connector utilizes Windows Management Instrumentation ([WMI](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page)) extensions to query data from the monitored server.

All versions of Microsoft Windows are supported, as long as the connector is able to retrieve data using WMI.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
|7.0.0.x [SLC Main]| Initial version| No | Yes |

> [!IMPORTANT]
> Currently, range versions 1.1.3.x and 6.0.0.x are still supported. However, we strongly recommend to use new driver range 7.0.0.x.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation. However, once the element is created, it is necessary to configure the connection settings (available in the page General -> Connections).

In addition, WMI and DCOM must be properly configured on the server to be monitored, as detailed below.

> [!IMPORTANT]
> Since this is a virtual connector, WMI queries sent to the target server are not displayed in the [Stream Viewer](https://docs.dataminer.services/user-guide/Troubleshooting/Logging/Monitoring_real-time_communication/Connecting_to_an_element_using_Stream_Viewer.html)
> Currently the default timeout is set to XXX

Default timeouts;

- Default timeout for a single command: 1.5 seconds
- 

TODO: Check what is the hardcoded timeout

#### WMI configuration

1. To go to WMI Control Properties, go to **Start** \> **Run** and enter *wmimgmt.msc*.
1. Right-click **WMI Control (Local)** and select **Properties**.
1. On the **Security** tab page, go to \\Root\CIMV2 and click the **Security** button.
1. Add the user that will be used to query data from the remote server to the list and give the user all rights.
1. Apply all.

#### DCOM configuration

1. Go to **Start** \> **Run** and enter *dcomcnfg* (Component Services).
1. Under **Component Services** \> **Computers**, right-click **My Computer** and select **Properties**.
1. Go to the tab **COM Security**.
1. Under **Launch and Activation Permissions**, click **Edit Limits**.
1. Add the user and give the user the *Local Launch*, *Remote Launch*, and *Remote Activation* permissions.
1. Apply all.

>[!NOTE]
>
> - After DCOM settings have been changed, the WMI services sometimes need to be restarted.
> - This method works fine for a Windows XP system but cannot be used on a Windows Server 2003 SP1.
> - On a Win2K3, the local user must be added to the administrators group.
> - On a Win2K8, the local user must be added to the administrators group, Distributed COM Users, and Performance Monitor Users.

### Initialization

Once the element is created, you can configure the credentials used to query the target server on the **Connections** page (located under the **General** section).

- If the element monitors the same DataMiner agent on which it is hosted, you can use either *localhost*, or *127.0.0.1* as hostname.

- If the element monitors a different DataMiner agent, specify the IP address or hostname of the remote agent.

- When using credentials from a domain controller, be sure to include the domain name (e.g. domain\myDomainUser).

>[!IMPORTANT]
> After modifying the settings on the **Connections** page, it is required to click the button *Connect* to apply the changes. The connector will not use the updated settings this action is completed.
> When the element is created, it will not start polling any data until the hostname **and** credentials are set in the **Connections** page.

### Connection States

![Connection States](../images/microsoft_platform_connection_state.png)

## How to use

The **General** page provides details about the operating system running on the monitored server. The page *OS Updates* displays details about the recently installed patches on the server.

The **CPU** page offers information related to the processor, including usage metrics, as well as thread and handle counters. The **Logical Processors** page presents utilization metrics for each logical processor.

The **Memory** page provides information about the physical and virtual memory allocation of the monitored server.

The **Disk** page offers information about the local storage in the monitored server. The page **Disk Details** provides more insightful information such as rates, read, write and transfer times.

>[!TIP]
> A sign that could indicate that the disk is busy is the *Latency*, i.e. how long it takes before it can process something. This metric can be tracked with the parameter **Avg. Transfer Rate**.

The **Network** page contains information about the network adapters available in the monitored server. Additional metrics, such as rates, are available in the page **Details**.

> [!NOTE]
> By default, the column **Name** will contain the name of the adapter as retrieved by [WMI](https://learn.microsoft.com/en-us/previous-versions/aa394293(v=vs.85)). However, in some cases, the connector will not be able to retrieve the name.

The **Process** page lists all the current processes run by the monitored server (similar to the *Task Manager* tool available in any Microsoft Windows OS). The connector will remove any process from the table that is no longer running in the monitored server.

Under the **Process** page, there are two pages:

- **Process Details**: Provides counters and rates for the current processes run by the monitored server.

- **Process Overview**: This page display the table **Processes**. This table allows you:

  - Monitor process that are no longer running on the monitored server. This is useful when you would like to monitor if a process stopped running. By default, this table is empty. You can right click in the table to display the context menu and add or remove rows. If the process is not running in the monitored server, the column *Count* will be set to 0.

  - Monitor multiple instances from the same process. For example, if you would like to monitor all the instances from the *Microsoft Edge* browser, you can add the process *msedge.exe*.

> [!TIP]
>
> - The process to be added does not need to be previously running in the operating system. Make sure that you use the exact process name (including the extension).
> - You can also add an existing process to the table **Processes** by right-clicking in a process in the table **Process Instances**, and select the option *Validate process*.

> [!NOTE]
> Currently wildcards are not supported.

The **Services** page provides information about the services available in the monitored server. The **Service Validation** page allows you to track if services are still available in the monitored server. By default, this table is empty.You can right click in the table to display the context menu and add or remove rows.

> [!TIP]
> You can also add an existing service to the table **Service Validation** by right-clicking in a process in the table **Services**, and select the option *Validate service*. You could also add multiple services.

The **Software** page displays the list of installed applications on the monitored server.

## Notes

- The list of WMI queries implemented in the connector can be found in [Microsoft Platform - WMI Queries](xref:microsoft_platform_technical_wmi_queries)

- In case the element is not able to poll the monitored server, please follow the [Troubleshooting guide](xref:microsoft_platform_technical_troubleshooting)
