---
uid: Connector_help_Microsoft_Platform_Technical
---

# Microsoft Platform (Older Ranges)

## About

The Microsoft Platform connector enables the monitoring of servers that run the Microsoft Windows OS. Leveraging Windows Management Instrumentation (WMI), it provides visibility on system performance, health metrics, and operational status.

To query data from the monitored server, the connector uses Windows Management Instrumentation ([WMI](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page)) extensions.

All versions of Microsoft Windows are supported, as long as the connector is able to retrieve data using WMI.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.1.3.x [SLC Main - Virtual Machine Environment] | Branched from 1.1.0.97: Contains partitionedTrending database option. Difference between 1.1.3.x and 1.1.0.x branch will not be noticeable with Cassandra general database, only with MySQL general database. Version 1.1.3.5 merged with 1.1.0.106. | Yes | Yes |
| 6.0.0.x [SLC Main - Physical Hardware Environment] | Branched from 1.1.2.31: Microsoft WMI interface + interface for DELL-, HP-, and Supermicro-specific SNMP parameters. | Yes | Yes |

> [!IMPORTANT]
> Currently, ranges 1.1.3.x and 6.0.0.x are still supported. However, we strongly recommend switching to [range 7.0.0.x](xref:Connector_help_Microsoft_Platform_Technical_7.0.0.x) as soon as it is available.

## Configuration

When you create an element using this connector, apart from the element name and the protocol fields, the only field you have to fill in is the **IP address**. In this field, you must specify the IP address assigned to the Windows server that will be monitored.

> [!IMPORTANT]
> When you create an element to monitor the DataMiner Agent hosting the element, the administrator built-in account will be used to query the server. In case the element will monitor a remote server, you must configure the appropriate credentials on the [Security](#security) page.

In addition, WMI and DCOM must be properly configured on the server to be monitored, as detailed below.

### WMI configuration

1. To go to WMI Control Properties, go to **Start** \> **Run** and enter *wmimgmt.msc*.
1. Right-click **WMI Control (Local)** and select **Properties**.
1. On the **Security** tab page, go to \\Root\CIMV2 and click the **Security** button.
1. Add the user that will be used to query data from the remote server to the list and give the user all rights.
1. Apply all.

### DCOM configuration

1. Go to **Start** \> **Run** and enter *dcomcnfg* (Component Services).
1. Under **Component Services** \> **Computers**, right-click **My Computer** and select **Properties**.
1. Go to the tab **COM Security**.
1. Under **Launch and Activation Permissions**, click **Edit Limits**.
1. Add the user and give the user the *Local Launch*, *Remote Launch*, and *Remote Activation* permissions.
1. Apply all.

> [!NOTE]
>
> - After DCOM settings have been changed, the WMI services sometimes need to be restarted.
> - This method works fine for a Windows XP system but cannot be used on a Windows Server 2003 SP1.
> - On a Win2K3, the local user must be added to the administrators group.
> - On a Win2K8, the local user must be added to the administrators group, Distributed COM Users, and Performance Monitor Users.

## Usage

### Performance

#### Security

This page displays settings that will be used by WMI to query the remote server.

- **Username**: The user account used for querying the remote server.
- **Password**: The password associated with the user account.
- **Domain Name**: Required only if the user account belongs to a domain controller. If a local user is used to query the server, this parameter can be left blank.

#### Port Monitoring

This page allows you to configure the port monitoring feature in this connector, which enables you to verify whether a port is opened or closed and to measure any response delay.

To enable this feature:

1. On the **Performance** page, click the **Port monitoring** button.
1. Define a **Polling Period.**
1. Use the **Add Port** box to add one or more ports that need to be monitored in the **Port List**.
1. Finally, enable the port monitoring feature by clicking the toggle button next to **Port Monitoring Status**.

#### Ping Monitoring

This page allows you to configure the ping monitoring feature available in this connector. This feature allows you to perform a ping command on the remote server.

To enable this feature:

1. On the **Performance** page, click the **Ping monitoring** button.
1. Click the toggle button next to **Ping Query** to execute the ping.
1. Configure the **Ping Cycle**, i.e. the interval between each ping. The default value is *60 s*.
1. Configure the **Ping Timeout** and **Ping Number**. The default values are *1500 ms* and *4* respectively.

### Task Manager

The Task Manager page lists all the processes run by the monitored server (similar to the Task Manager tool available in any Microsoft Windows OS). Each entry in the **Task Manager** table represents a process active on the monitored server.

By default, the connector will poll all the running processes on the monitored server. You can modify this behavior by setting the parameter **Poll Task Manager** to *Off*.

Also by default, the connector will remove any process that is no longer running from the Task Manager table. You can modify this behavior by setting the parameter **Auto Clear Task Manager** to *Off*

> [!TIP]
> If you wish to monitor when a process is no longer running, set the parameter **Auto Clear Task Manager** to *Off*. By enabling monitoring on the parameter **Row Status**, you can then generate an alarm when a process is no longer running.

The button **Clear Task Manager** allows you to clear the Task Manager table manually. This button is useful only if the parameter **Auto Clear Task Manager** is set to *Off*

To set the current values in the table as the normal reference for alarms, click the button **Normalize Alarms**. You can then view these references via the **Nominal Values** button at the bottom of the page.

> [!IMPORTANT]
> The Normalize Alarms feature is deprecated. Instead, we recommend [configuring dynamic alarm thresholds](https://aka.dataminer.services/configuring-dynamic-alarm-thresholds).

It is also possible to add a filter to calculate the sum of the memory usage of all processes that match this filter. To do so:

1. Click the button **Cumulated Memory** at the bottom of the page.

1. Enter a filter in the box **Add Filter Param**. An asterisk (\*) wildcard is supported in this filter. You can also use an exclamation mark (\!\) to return the opposite cumulated memory of the filter parameter. (See examples below.)

   |Examples|Description|
   |--------|-----------|
   |SLDatam\*|Searches for processes that begin with "SLDatam"|
   |\*Dataminer\*|Searches for processes that contain the word "DataMiner"|
   |miner:0*|Searches for processes that end with "miner:0"|
   |SLDataminer:0|Searches for the process "SLDataminer:0"|
   |!SLDatam*|Searches for processes that do not begin with "SLDatam"|
   |!\*Dataminer*|Searches for processes that do not contain the word "DataMiner"|
   |!miner:0*|Searches for processes that do not end with "miner:0"|
   |!SLDataminer:0|Searches for processes that are not equal to "SLDataminer:0"|

If necessary, add more filters, or delete filters using the **Delete** button next to the filtered parameter.

#### Task Manager Measurement

Clicking the button **Measurement Config** will open the **Task Measurement Config** page. This page allows you to customize the processes listed in the **Task Manager** table. The following parameters are available for this:

- The parameter **Task Manager Default Measurement State** will enable/disable the measurement of new processes.
- The parameter **Task Manager Auto Refresh Measurement Table** allows you to automatically refresh the Task Manager Measurement Config table.
- The parameter **Task Manager Auto Clear Measurement Table** allows you to automatically remove processes that are no longer running on the server.

In addition, the buttons **Disable All**, **Enable All**, **Clear**, and **Refresh** allow you to manually perform the actions covered by the parameters listed above.

To disable or enable the monitoring of a specific process in the Task Manager table (i.e. remove or add the process from/to the Task Manager table), proceed as follows:

1. Locate the process to be removed in the **Task Manager Measurement Config** table.
1. In the column **Task Polling**, set the value to *Disable* or *Enable* accordingly.

> [!NOTE]
> By default, the **Task Manager Measurement Config** table will list the same processes as the **Task Manager** table, and the column **Task Polling** will be set to *Not Initialized*.

### Network Interface

This page displays the **Network Adapter** table. This table monitors the network adapters available in the server.

> [!NOTE]
> The bandwidth of an adapter can be very high (e.g. 10 GB/s). Therefore, as the utilization gets calculated as the total speed divided by the bandwidth, the utilization value can be extremely low. It can even be rounded down to 0.00 % if Total Speed \< 0.005 \* Bandwidth.

By default, the column **Adapter Description** will contain the name of the adapter as retrieved by [WMI](https://learn.microsoft.com/en-us/previous-versions/aa394293(v=vs.85)). However, in some cases, the connector will not be able to retrieve the name. If this is the case, it is possible to customize this name of the adapter.

> [!IMPORTANT]
> Once the column **Adapter Description** is set manually, the connector will not overrule this setting. Updating the name could cause metrics related to this network adapter to not be retrieved. If you set a network adapter to a description that is already used by another adapter, the description of the other adapter will be set to an empty string.

On the **Network Adapter Measurement** page, you can disable processes to remove them from the **Network Adapter** table.

- The parameter **Network Adapter Default Measurement State** allows you to enable/disable the measurement of new adapters.

- The **Clear** button removes all deleted processes from the **Network Adapter Measurement** and **Network Adapter** table. This is by default followed by a refresh.

- The **Refresh** button can be used to manually refresh the list of network adapters and the additional information.

You can also entirely disable the polling of the network adapters with the toggle button **Poll Network Adapters**.

Once an adapter is disconnected and not found by the connector, its status will be set to *Disconnected*. You can choose to either remove such adapters automatically (using the button **Auto Clear Disconnected Adapters**) or manually delete them using the parameter **Manually Clear Disconnected Adapters**.

> [!NOTE]
> The parameter **Manually Clear Disconnected Adapters** will only list disconnected adapters.

### Disk Info

This page provides information about local storage devices on a server running Windows.

> [!TIP]
> A sign that could indicate that the disk is busy is the *Latency*, i.e. how long it takes before it can process something. This metric can be tracked with the parameter **Avg Disk sec/Transfer Rate**.

### Event Viewer

This page displays information regarding selected or created events.

When you enable the Event Viewer, you can monitor the events displayed in the **Event Viewer** table.

If you want to add events, click the **Add event** page button. If you click **Load**, all the event messages from a specific time interval will be retrieved and displayed on the page. You can then select the events you want to monitor by clicking the **Monitor Event** button. The time interval can be changed using the slider.

To delete a monitored event, click the **Delete** button in the **Event Viewer** table.

The event details can be configured. For each type of event (information, warning, or error), the severity of the created alarm can be selected from the dropdown list. For example: "Disk Crash" event with a **Severity Error Type** equal to *Critical*.

When the configured **Alarm Type** equals ***Normal*** and an event occurs that matches one of the added filters in the **Event Viewer Messages** table, the new event will automatically trigger an alarm or an information event. **Alarm Type** ***Grouped*** will add the row to the **Grouped Event Alarms** with the most recent severity of the event. When the **Grouped Event Active Time** expires, the event is removed from the table. Grouped events will not create alarms automatically, but you can configure alarm monitoring on the **Grouped Event Type** column.

From version 1.1.0.100 onwards, it is possible to get all events except those with a specific **Event ID**. In each row of the table, a toggle button **Exclude Event ID** has been added:

- If it is set to the default setting ***Include***, you can insert a **single event ID** or the value **"\*"** to **get all event IDs** for the relevant source/category (= **equal to all previous versions**).

- If it is set to ***Exclude***, you can select a **single event ID**, which will be omitted from the results. All other event IDs will be selected.

### Performance Monitor

This page monitors performance counters added by the user.

On the **Config Performance Counters** page, you can search for performance counters and add them to the **Performance Monitor** table:

1. Click **Refresh Categories** to create a dropdown list with the **Categories**.
1. Select the category and then select a **Counter**. If the counter has multiple instances, you can either select the **Instance** you want, or select *\<All Instances\>.*
1. Finally, click the **Add Counter** button to add the selected counter to the table.

With the **Performance Monitor Sample Time**, you can configure the sample time for all created performance counters.

### Dell

This page focuses on Dell computer hardware.

It monitors certain high-level parameters, such as the name, version, and model. It also includes pages with more information on specific categories:

- The **Temperature Probe Table** provides information about the temperature of the device.
- A page is available for the **power supply**, **fans**, **CPU**, and **memory** information for the device.
- The **Disk** page provides an overview of all the disks included in the system.

> [!IMPORTANT]
> In order to monitor these parameters, you have to enable polling on the **Dell** page.

### HP

This page focuses on HP computer hardware.

It monitors the same set of parameters as the Dell page described above.

> [!IMPORTANT]
> In order to monitor these parameters, you have to enable polling on the **HP** page.

### Software Info

This page contains the **Software Info Table**, which displays a list of all installed programs.

> [!IMPORTANT]
> USERNAME and PASSWORD have to be set for this to work (under **Performance** > **Security Settings**).

Above the table, you can select the polling method. (Alternative methods are available to circumvent issues with WMI queries.)

- *No Polling*: Nothing will be retrieved, and the table will remain empty.
- *Win32_Product*: A list of all installed programs will be retrieved using a WMI query. We strongly advise **not to use this method**, as this can perform a Windows Installer "reconfiguration" on every MSI package as it is performing the query.
- *Win32reg_AddRemoveProgram*: A list of all installed programs will be retrieved using a WMI query, if Microsoft CSSM software is installed. This is a better alternative to the Win32_Product method.
- *Registry Keys*: **Recommended method.** This method will use WMI to read the registry keys to display a list of all installed programs in the system.
