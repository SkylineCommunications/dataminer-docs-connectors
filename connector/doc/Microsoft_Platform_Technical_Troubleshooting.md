---
uid: microsoft_platform_technical_troubleshooting
---

# Troubleshooting

## Access is denied with error code 0x80070005 (or 0x80041003)

**Symptom**

The following errors are shown in the Stream Viewer (when looking at the communication of any group):

- Access is denied with error code 0x80070005
- Access is denied with error code 0x80041003

**Cause**

The username does not have enough permissions to query the server, specifically when performing remote WMI queries using non-admin users.

**Resolution**

- Access is denied with error code 0x80070005: See [DCOM configuration](xref:Connector_help_Microsoft_Platform_Technical#dcom-configuration)
- Access is denied with error code 0x80041003: See [WMI configuration](xref:Connector_help_Microsoft_Platform_Technical#wmi-configuration)
- If the above options do not solve the issue, try to open Windows Explorer on the monitored server, using the username that you configured on the [Settings](xref:Connector_help_Microsoft_Platform_Technical#security) page. If it is not possible to connect to the server because you have to log on with the account *guest*, execute the following steps:

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
> At this point, you will receive the following error:
>
> ```text
> Failed to connect to [\\%RemoteIP%](file:///) because "Win32 Access is denied".
> ```
>
> If the above steps are not possible, you could also run **wmimgmt.msc** directly on the server (from CMD or PowerShell). You will receive the following error: Microsoft Management Console "An attempt was made to reference a token that does not exist".

## Not all parameters are initialized

**Symptom**

A Microsoft element displays a partial set of the data. Some parameters, such as *Local Time*, *Total Physical Memory*, etc. are populated, while others like *Total Processor Load*, *Total Handles* remain not initialized. Looking at the **Stream Viewer**, you notice certain queries do not return any results.

**Cause**

There can be different possible causes for this behavior. Refer to the possible resolutions below.

**Resolution**

- Check the element timeout settings. When an element is created, these are the default values:

  - Timeout of a single command: 6000 ms
  - Number of retries: 3

  Update the timeout value if necessary, and validate whether the element is now able to poll all parameters.

- Execute the following command (using CMD or PowerShell) to manually reset the counters with WMI (for more information, refer to [Microsoft Learn](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/manually-rebuild-performance-counters)):

  ```cmd
  winmgmt.exe /resyncperf
  ```

- Verify whether the user used to query the server is included in the group *Performance Monitor Users*.

## Query failed: Retrieving the data failed. (hr = 0x80041010)

**Symptom**

Stream Viewer shows the following error:

```text
Query failed : Retrieving the data failed. (hr = 0x80041010) for numerous WQL SELECT queries.
```

**Cause**

Some or all related Disable Performance Counters in regedit for `PerfDisk`, `PerfNet`, `PerfOS`, `PerfProc`, `Tcpip`, or `W3SVC` are set to **1**. With the path below, you can confirm if these counters are disabled:

```text
"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance\
```

When wbemtest is used and these queries are performed, or the classes are listed, this results in similar errors mentioning "Invalid class".

**Solution**

Set all these to **0**, and after a couple of minutes the query errors should disappear and the related data should get filled in.

## Contacting Server Failed: Connection to root/cimv2 failed. The RPC server is unavailable

**Symptom**

The following error occurs:

```text
Contacting server failed: Connection to \[//server/root/cimv2\] failed. The RPC server is unavailable. (hr = 0x800706BA).
```

**Cause**

Configuration issue on the remote server.

**Solution**

- Make sure TCP/135 and TCP/49000-65535 (WMI) are open.
- Make sure the user is created on server and host.

## Performance Monitoring not working

**Symptom**

The element is able to populate all parameters, except the Performance Monitor. Clicking *Refresh Categories* triggers the following error in element logging:

```text
Exception Perf Counters The network path was not found.
```

**Cause**

Possible configuration issue on the remote server.

**Solution**

Check if the destination computer has the "Remote Registry" service running. If not, start this service. (Note that you may need to adjust the Startup Type from *Disabled* to *Manual/automatic* first.)

## Percent Disk Busy Time goes above 100%

**Symptom**

The parameter **Percent Disk Busy Time** shows values higher than 100%.

**Cause**

By design.

**Resolution**

Not applicable. More information can be found in the [Microsoft Knowledge Base](http://support.microsoft.com/kb/310067).

## Additional Notes

### Windows Vista

From Windows 2000 onwards, WMI is installed by default. Except in Windows Vista, WMI uses random ports. To configure a fixed port in Windows Vista:

1. In the command prompt window, type *winmgmt -standalonehost.*
1. Stop the WMI service by typing the command *net stop "Windows Management Instrumentation"*.
1. Restart the WMI service in a new service host by typing *net start "Windows Management Instrumentation"*.
1. Establish a new port number for the WMI service by typing *netsh firewall add portopening port=24158 name=WMIFixedPort*.

If you want to have access to the WMI interface of a Windows XP computer, you can work with a local user (a group user, not an administrator) that has the necessary Windows security rights, so extra configuration is necessary on the client computers.

### Re-registering the WMI component on the monitored server

In some situations, you will need to re-register the WMI component in the monitored server.

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
