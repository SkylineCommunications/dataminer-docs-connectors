---
uid: Connector_help_Microsoft_Platform
---

# Microsoft Platform

The Microsoft Platform connector enables the monitoring of servers that run the Microsoft Windows OS.

## About

The Microsoft Platform connector gathers key performance indicators from a server running the Microsoft Windows OS. To accomplish this, the connector utilizes Windows Management Instrumentation ([WMI](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page)) extensions to query data from the monitored server.

All versions of Microsoft Windows OS are supported, as long as the connector is able to retrieve data using WMI.

<!--Extra information can be enabled or disabled, e.g. Task Manager, Service List, etc.-->
<!-- On the Task Manager page, a button allows you to normalize alarms in order to set the current values as normal.
-->

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.1.3.x [SLC Main - Virtual Machine Environment] | Branched from 1.1.0.97: Contains partitionedTrending database option. Difference between 1.1.3.x and 1.1.0.x branch will not be noticeable with Cassandra general database, only with MySQL general database. Version 1.1.3.5 merged with 1.1.0.106. | Yes | Yes |
| 6.0.0.x [SLC Main - Physical Hardware Environment] | Branched from 1.1.2.31: Microsoft WMI interface + interface for DELL-, HP- and Supermicro specific SNMP parameters. | Yes | Yes |

> [!IMPORTANT]
> Currently only the driver ranges listed above are supported. In case a driver from a different driver range is used, it is recommended to migrate to one of the supported ranges.

<!--
| 1.0.0.x [Obsolete] |Microsoft WMI interface implementation. | Yes | Yes |
| 1.1.0.x [Obsolete] | Microsoft WMI interface implementation. | Yes | No |
| 1.1.1.x [Obsolete] [move to 1.1.2.x] | Branched from 1.1.0.89: Microsoft WMI interface + interface for DELL- and HP-specific SNMP parameters. | Yes | Yes |
| 1.1.2.x [Obsolete] |Branched from 1.1.1.x: Microsoft WMI interface + interface for DELL- and HP-specific SNMP parameters. | Yes | Yes |
| 1.2.0.x [Obsolete] | Multiple tables now use naming instead of displayColumn to make the database for these tables Cassandra-compliant. | Yes | Yes |
| 2.1.0.x [Obsolete] | Branched from 1.1.0.41: Network Interface table adjustments. | Yes | Yes |
| 3.0.0.x [Obsolete] | Branched from 1.1.0.71: Implemented a workaround for a WMI bug in the network adapter table. | Yes | Yes |
| 4.0.0.x [Obsolete] | Branched from 1.1.0.78: Customer-specific branch including functionality to see if the element is running on the active DMA (Failover) with specific security configuration settings in the elements. | Yes | Yes |
| 5.0.0.x [Obsolete] | Branched from 1.1.1.5: Temporary branch to be used as workaround for a problem with retrieving the service table via WMI calls. | Yes | Yes |
-->

## Configuration

When creating an element using this connector, apart from the element name and the protocol fields, the only required field to be populated is the *IP address*. In this field, you must specify the IP address assigned to the server running Microsoft Windows OS that will be monitored.

> [!IMPORTANT]
> When creating an element to monitor the DataMiner Agent hosting the element, the administrator built-in account will be used to query the server.
> In case the element will monitor a remote server, you must set the appropriate credentials in the Security page (see [Security](#security))

In addition, WMI and DCOM must be properly configured on the server to be monitored. Follow the steps below to correctly configure these components:

### WMI configuration

1. To go to WMI Control Properties, go to **Start** \> **Run** and enter *wmimgmt.msc*.
1. Right-click **WMI Control (Local)** and select **Properties**.
1. On the **Security** tab page, go to \\Root\CIMV2 and click the **Security** button.
1. Add the user that will be used to query data from the remote server to the list and give the user all rights.
1. Apply all.

### DCOM configuration

1. Go to **Start** \> **Run** and enter *dcomcnfg* (Component Services).
1. Under **Component Services** \> **Computers**, select **My Computer** and press right-click to open **Properties**.
1. Go to the tab **COM Security**.
1. Under **Launch and Activation Permissions**, choose **Edit Limits**.
1. Add the user and give the user the Local Launch, Remote Launch, and Remote Activation permissions.
1. Apply all.

>[!NOTE]
>
> - After DCOM settings have been changed, the WMI services sometimes need to be restarted.
> - This method works fine for a Windows XP system but cannot be used on a Windows Server 2003 SP1.
> - On a Win2K3, the local user must be added to the administrators group.
> - On a Win2K8, the local user must be added to the administrators group, Distributed COM Users, and Performance Monitor Users.

## Usage

### Performance

#### Security

This page displays settings that will be used by WMI to query the remote server.

- Username: The user account used for querying the remote server
- Password: The password associated with the user account
- Domain Name: Required only if the user account belongs to a domain controller. If a local user is used to query the server, this parameter can be left blank.

#### Port Monitoring

This page lets you configure the *port monitoring* feature in this connector, which enables you to verify that a port is opened or closed and to measure any response delay.

To enable this feature, proceed as follows:

1. On the **Performance** page, click the **Port monitoring** button.
1. Define a **Polling Period.**
1. Use the **Add Port** box to add one or more ports that need to be monitored in the **Port List**.
1. Finally, enable the port monitoring feature by clicking the toggle button next to **Port Monitoring Status**.

#### Ping Monitoring

This page lets you configure the *ping monitoring* feature available in this connector. This feature allows you to perform a ping command on the remote server.

To enable this feature, proceed as follows:

1. On the **Performance** page, click the **Ping monitoring** button.
1. Click the toggle button next to **Ping Query** to execute the ping.
1. Configure the **Ping Cycle**, i.e. the interval between each ping. The default value is *60 s*.
1. Configure the **Ping Timeout** and **Ping Number**. The default values are *1500 ms* and *4* respectively.

### Task Manager

The Task Manager page lists all the processes run by the monitored server (similar to the *Task Manager* tool available on any Microsoft Windows OS). Each entry in the **Task Manager** table represents a process active in the monitored server.

By default, the connector will poll all the running processes in the monitored server. This behavior can be modified by setting the parameter **Poll Task Manager** to **Off**.

Additionally, the connector will remove from the **Task Manager** table any process that is no longer running. This behavior can be modified by setting the parameter **Auto Clear Task Manager** to **Off**

> [!TIP]
> If you wish to monitor when a process is no longer running, set the parameter **Auto Clear Task Manager** to **Off**. By enabling monitoring on the parameter **Row Status**, you can generate an alarm when a process is no longer running.

The button **Clear Task Manager** allows you to clear the Task Manager table manually.

> [!NOTE]
> This button is useful only if the parameter **Auto Clear Task Manager** is set to **Off**

To set the current values in the table as the normal reference for alarms, click the button **Normalize Alarms**. You can then view these references via the **Nominal** **Values** button at the bottom of the page.

> [!IMPORTANT]
> This feature is deprecated. Use [Configuring dynamic alarm thresholds](https://docs.dataminer.services/user-guide/Basic_Functionality/Protocols_and_templates/Alarm_templates/Configuring_alarm_templates/Configuring_dynamic_alarm_thresholds.html)

It is also possible to add a filter to calculate the sum of the memory usage of all processes that match this filter. To do so:

1. Click the button **Cumulated Memory** at the bottom of the page.

1. Enter a filter in the box **Add Filter Param**. An asterisk (\*) wildcard is supported in this filter. You can also use an exclamation mark (\!\) to return the opposite cumulated memory of the filter parameter. (cf. examples below)

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

If necessary, add more filters or delete filters using the **Delete** button next to the filtered parameter.

#### Task Manager Measurement

When clicking on the button **Measurement Config**, you will open the **Task Measurement Config** page.
This page allows you to customize the processes listed in the **Task Manager** table. For this purpose, the **Task Manager Measurement Config** lets you determine the processes that will be listed in the **Task Manager** table. The behavior of this table can be customized using the following parameters:

- The parameter **Task Manager Default Measurement State** will enable/disable the measurement of new processes.
- The parameter **Task Manager Auto Refresh Measurement Table** allows you to automatically refresh the **Task Manager Measurement Config** table.
- The parameter **Task Manager Auto Clear Measurement Table** allows you to automatically remove processes that are no longer running int the server.

In addition, the buttons **Disable All**, **Enable All**, **Clear**, and **Refresh** allows you to perform manually the actions covered by the parameters listed above.

>[!NOTE]
>
> - By default, the **Task Manager Measurement Config** table will contain the same processes listed in the **Task Manager** table.
> - In addition, the column **Task Polling** will be **Not Initialized**.

To disable (or enable) the monitoring of a specific process In the **Task Manager** table (i.e. remove the process from the **Task Manager** table), proceed as follows:

- Find the process to be removed in the **Task Manager Measurement Config** table
- In the column **Task Polling**, set the value to **Disable** or **Enable** accordingly

### Network Interface

This page displays the **Network Adapter** table. This table monitors the network adapters available in the server.

> [!NOTE]
> The bandwidth of an adapter can be very high (*e.g. 10 GB/s*). Therefore, as the utilization gets calculated as the total speed divided by the bandwidth, the utilization value can be extremely low. It can even be rounded down to 0.00 % if *Total Speed \< 0.005 \* Bandwidth*.

<!--
For most interfaces, the **MAC Address** and **Status** are available. For a server of the type Microsoft Server 2000 or Microsoft 2000 Professional, the **MAC Address** is not available.
-->

By default, the column **Adapter Description** will contain the name of the adapter as retrieved by [WMI](https://learn.microsoft.com/en-us/previous-versions/aa394293(v=vs.85)). However, in some cases, the connector will not be able to retrieve the name. If this is the case, it is possible to customize this name of the adapter.

> [!IMPORTANT]
> Once the column **Adapter Description** is set manually, the connector will not overrule this setting.
> Updating the name could cause that metrics related to this network adapter cannot be retrieved.
> If you set a network adapter to a description that is already used by another adapter, the description of the other adapter will be set to an empty string.

<!--
If you set the **Adapter Description** to the correct name (from Win32_PerfRawData_Tcpip_NetworkInterface), additional info will be retrieved. The connector will try to match the adapters to the correct default description on initializing, but in some cases, you will still need to set this description manually.

Once this has been set manually, the connector will not overrule this setting. The options displayed in the dropdown box are the names of the network interfaces that were found by the connector. You can also choose a custom name that is not from this list, but then no match will be found, no additional info will be shown, and the description can be overruled by the connector. You can only assign a network interface to one network adapter. If you set a network adapter to a description that is already used by another adapter, the description of the other adapter will be set to an empty string.
-->

On the **Network Adapter Measurement** page, you can disable processes to remove them from the **Network Adapter** table.

- The parameter **Network Adapter Default Measurement State** allows you to enable/disable the measurement of new adapters.

- The **Clear** button removes all deleted processes from the **Network Adapter Measurement** and **Network Adapter** table. This is by default followed by a refresh.

- The **Refresh** button can be used to manually refresh the list of network adapters and the additional information.

It is also possible to entirely disable the polling of the network adapters with the toggle button **Poll Network Adapters**.

Once an adapter is disconnected and not found by the connector, its status will be set to *Disconnected*. You can choose to either remove such adapters (using the button **Auto Clear Disconnected Adapters**), or manually delete them using the parameter **Manually Clear Disconnected Adapters**.

>[!NOTE]
> The parameter **Manually Clear Disconnected Adapters** will only list disconnected adapters

### Disk Info

This page provides information about local storage devices on a server running Windows.

>[!TIP]
> A sign that could indicate that the disk is busy is the *Latency*, i.e. how long it takes before it can process something. This metric can be tracked in the parameter **Avg Disk sec/Transfer Rate**.

### Event Viewer

This page displays information regarding selected or created events.

When you enable the Event Viewer, you can monitor the events displayed in the **Event Viewer** table. If you want to add events, click the **Add event** page button. If you click **Load**, all the event messages from a specific time interval will be retrieved and displayed on the page. You can then select the events you want to monitor by clicking the **Monitor Event** button. The time interval can be changed using the slider.

To delete a monitored event, click the **Delete** button in the **Event Viewer** table.

The event details can be configured. For each type of event (information, warning, or error), the severity of the created alarm can be selected from the dropdown list. For example: "Disk Crash" event with a **Severity Error Type** equal to *Critical*.

When the configured **Alarm Type** equals ***Normal*** and an event occurs that matches one of the added filters in the **Event Viewer Messages** table, the new event will automatically trigger an alarm or an information event. **Alarm Type** ***Grouped*** will add the row to the **Grouped Event Alarms** with the most recent severity of the event. When the **Grouped Event Active Time** expires, the event is removed from the table. Grouped events will not create alarms automatically, but you can configure alarm monitoring on the **Grouped Event Type** column.

From version 1.1.0.100 onwards, it is possible to get all events except those with a specific **Event ID**. In each row of the table, a toggle button **Exclude Event ID** has been added:

- If it is set to the default setting ***Include***, you can insert a **single event ID** or the value **"\*"** to **get all event IDs** for the relevant source/category (= **equal to all previous versions**).

- If it is set to ***Exclude***, you can select a **single event ID**, which will be omitted from the results. All other event IDs will be selected.

### Performance Monitor

This page monitors performance counters added by the user.

On the **Config Performance Counters** page, you can search for performance counters and add them to the **Performance Monitor** table. Proceed as follows:

1. Click **Refresh Categories** to create a dropdown list with the **Categories**.
1. Select the category and then choose a **Counter**. If the counter has multiple instances, you can either select the **Instance** you want, or select *\<All Instances\>.*
1. Finally, click the **Add Counter** button to add the selected counter to the table.

With the **Performance Monitor Sample Time**, you can configure the sample time for all created performance counters.

### Dell

This page is focused on Dell computer hardware.

It monitors certain high-level parameters, such as the name, version, model and others. It also includes pages with more information on specific categories:

- The **Temperature Probe Table** provides information about the temperature of the device.
- The **Power supply**, **Fans**, **CPU** and **Memory** of the device.
- The **Disk** page provides an overview of all the disks included in the system.

>[!IMPORTANT]
> In order to monitor these parameters, you have to enable polling on the **Dell** page.

### HP

This page is focused on HP computer hardware.

It monitors the same set of parameters as the Dell page described above.

>[!IMPORTANT]
> In order to monitor these parameters, you have to enable polling on the **HP** page.

### Software Info

This page contains the **Software Info Table**, which displays a list of all installed programs.
**Note: USERNAME and PASSWORD have to be set! (Under Performance \> Security Settings).**

Above the table, it is possible to select the polling method. (Alternative methods were introduced after problems were encountered with the used WMI Query.)

- *No Polling*: Nothing will be retrieved, and the table will remain empty.
- *Win32_Product*: WMI Query used to retrieve a list of all installed programs. We strongly advise **not to use this method**, as this can perform a Windows Installer "reconfiguration" on every MSI package as it is performing the query.
- *Win32reg_AddRemoveProgram*: WMI Query used to retrieve a list of all installed programs if Microsoft CSSM software is installed. This is a better alternative to the Win32_Product method.
- *Registry Keys*: **Recommended method.** This method will use WMI to read the registry keys to display a list of all installed programs in the system.

## Troubleshooting

### Access is denied with error code 0x80070005 (or 0x80041003)

**Symptom**

The following errors are shown in the Stream Viewer (when looking at the communication of any group):

- Access is denied with error code 0x80070005
- Access is denied with error code 0x80041003

**Cause**

The username does not have enough permissions to query the server, specifically when performing remote WMI queries using non-admin users.

**Resolution**

- Access is denied with error code 0x80070005: See [DCOM configuration](#dcom-configuration)
- Access is denied with error code 0x80041003: See [WMI configuration](#wmi-configuration)
- If the above options don't solve the issue, try to open Windows Explorer on the monitored server, using the username that you configured in the [Settings](#security) page. If it is not possible to connect to the server because you have to log on with the account *guest*, execute the following steps:

1. Go to **Control Panel** \> **Administrative Tools** \> **Local Security Policy**.
1. Go to **Local Policies** \> **Security Options**.
1. Double-click **Network access: Sharing and security model for local accounts**.
1. Select **Classic- local users authenticate as themselves**.

> [!NOTE]
> To confirm that a user does not have the rights to perform WMI queries, you can proceed as follows:
>
> 1. Click **Start** \> **Run** and execute *wmimgmt.msc*.
> 1. Right-click **WMI Control (Local)** and select **Connect to another computer**.
> 1. Select **Actions** \> **More Actions** \> **Properties**.
>
> At this point, you will receive the following error
>
> ```text
> Failed to connect to [\\%RemoteIP%](file:///) because "Win32 Access is denied".
> ```
>
> If the above steps are not possible, you could also run **wmimgmt.msc** directly on server (from CMD or PowerShell). You will receive the following error: Microsoft Management Console "An attempt was made to reference a token that does not exist".

### Not all parameters are initialized

**Symptom**

A Microsoft element displays a partial set of the data. Some parameters, such as *Local Time*, *Total Physical Memory*, etc. are populated, while others like *Total Processor Load*, *Total Handles* remain not initialized. Looking at the **Stream Viewer**, you notice certain queries do not return any results.

**Cause**

There are different possible causes that could cause this behavior. Please see below possible resolutions.

**Resolution**

- Check that the element timeout settings. When creating an element, the default values are:

  - Timeout of a single command: 6000 ms
  - Number of retries: 3

Update the timeout value and validate that the element is now able to poll all parameters.

- Execute the following command (using CMD or PowerShell) to manually reset the counters with WMI (more information in [Microsoft Learn](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/manually-rebuild-performance-counters)):

```cmd
winmgmt.exe /resyncperf
```

- Verify that the user used to query the server is included in the group *Performance Monitor Users*.

<!--
#### Possible memory leak on remote machines that are running 2008/Vista

- Possible memory leak on remote machines that are running 2008/Vista: <http://support.microsoft.com/kb/970520/en-us>

**Solution:**

When the remote server is running Vista, UAC must be disabled.
-->

<!--
**Problem:**

- Task Manager data through WMI cannot be retrieved. This can be related to missing "Process Performance Counters".
  Refer to this technet post for more info: <http://blogs.technet.com/b/mscom/archive/2008/12/18/the-mystery-of-the-missing-process-performance-counter-in-perfmon.aspx>

  **Solution**:

  - Disable a specific flag on the Windows Register. Set the "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance\Disable Performance Counters" to *0*.
-->

### Query failed: Retrieving the data failed. (hr = 0x80041010)

**Symptom**

Stream Viewer shows the following error

```text
Query failed : Retrieving the data failed. (hr = 0x80041010) for numerous WQL SELECT queries.
```

**Cause**

Some or all related Disable Performance Counters in regedit for `PerfDisk`, `PerfNet`, `PerfOS`, `PerfProc`, `Tcpip` or `W3SVC` are set to **1**. Below the path to confirm if these counters are disabled:

```text
"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance\
```

When wbemtest is used and these queries are performed, or the classes are listed, this results in similar errors mentioning "Invalid class".

**Solution**

Set all these to **0**, and after a couple of minutes the query errors should disappear and the related data should get filled in.

### Contacting Server Failed: Connection to root/cimv2 failed. The RPC server is unavailable

**Symptom**

The following error occurs:

```text
Contacting server failed: Connection to \[//server/root/cimv2\] failed. The RPC server is unavailable. (hr = 0x800706BA).
```

**Cause**

Configuration issue on the remote server

**Solution**

- Make sure TCP/135 and TCP/49000-65535 (WMI) are open.
- Make sure the user is created on server and host.

### Performance Monitoring not working

**Symptom**

The element is able to populate all parameters, except the Performance Monitor. Pressing *Refresh Categories* triggers the following error in element logging:

```text
Exception Perf Counters The network path was not found.
```

**Cause**

Possible configuration issue on the remote server

**Solution**

Check if the destination computer has the "Remote Registry" service running. If not, start this service. (Note that you may need to adjust the Startup Type from *Disabled* to *Manual/automatic* first.)

### Percent Disk Busy Time goes above 100%

**Symptom**

The parameter **Percent Disk Busy Time** shows values higher than 100%.

**Cause**

By design

**Resolution**

Not applicable. More information can be found in [Microsoft Knowledge Base](http://support.microsoft.com/kb/310067)

## Additional Notes

### Windows Vista

From Windows 2000 onwards, WMI is installed by default. Except in Windows Vista, WMI uses random ports.
To configure a fixed port in Windows Vista:

1. In the command prompt window, type *winmgmt -standalonehost.*
1. Stop the WMI service by typing the command *net stop "Windows Management Instrumentation"*.
1. Restart the WMI service in a new service host by typing *net start "Windows Management Instrumentation"*.
1. Establish a new port number for the WMI service by typing *netsh firewall add portopening port=24158 name=WMIFixedPort*.

If you want to have access to the WMI interface of a Windows XP computer, you can work with a local user (a group user, not an administrator) that has the necessary Windows security rights, so extra configuration is necessary on the client computers.

<!--
### Global Configuration

1. Create a user and add the user in the user group.
1. If the firewall is enabled, open a command prompt and execute "*netsh firewall set service RemoteAdmin enable*".

-->

### Re-registering the WMI component on the monitored server

In some situations, it is required to re-register the WMI component in the monitored server.

- For 32-bit Windows OS, the `.dll` and `.exe` files used by WMI are located in `%windir%\system32\wbem`.
- For 64-bit Windows OS, these files are located in `%windir%\sysWOW64\wbem`.

To re-register the WMI components, run the following commands with the command prompt:

```cmd
cd /d %windir%\system32\wbem*
for %i in (*.dll) do RegSvr32 -s %i
for %i in (*.exe) do %i /RegServer
```

### Information Resources

- [How to Enable Remote WMI Access for a Domain User Account](https://martellotech.com/blog/enable-remote-wmi-access-for-a-domain-user-account/)
