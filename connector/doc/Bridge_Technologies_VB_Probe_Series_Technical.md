---
uid: Connector_help_Bridge_Technologies_VB_Probe_Series_Technical
---

# Bridge Technologies VB Probe Series

This connector allows you to monitor and control **Bridge Technologies probe** devices.

It uses the **EII API (Enterprise Information Integration)** provided by the vendor for regular polling of the probes over **HTTP**, as well as **SNMP traps** in order to get quick alarm updates.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | - Monitoring of ETR-enabled **streams/services/PIDs**. <br>- Monitoring of **ETR checks**. <br>- Monitoring of **OTT channels** and **OTT profiles**. <br>- Monitoring of the probe **alarms** with precise probe times match (history set). | - | - |
| 1.1.0.x | - **Ethernet streams provisioning** from **Automation script**. | 1.0.0.x | This branch requires the same minimum DataMiner version as branch 1.0.0.x, but the "Ethernet streams provisioning from Automation script" feature requires DataMiner feature release 9.6.3 or higher. |
| 1.1.1.x | - InterApp Messages available via NuGet package. | 1.1.0.x | Consumers of the InterApp calls should be adapted. They should now make use of the newly released NuGet package instead of duplicating the InterApp Messages code. |
| 1.2.0.x | - | 1.1.1.x | Minimum required DataMiner version brought up to 10.2.0.0. |
| **1.4.0.x [SLC Main]** | Display key format change for Streams, Ethernet Streams, Services and PIDs Tables. Source Multicast Group (S,G)-format added for Ethernet streams | 1.3.0.x | Revise the alarm templates, scripts and visios which are based Service PIDs table. |
| 1.4.1.x | Alarm tables: The Time columns will now display the alarm times according to the DataMiner server time zone rather than the probe one. | 1.4.0.x | The trending data will now be based on the DataMiner server time zone rather than the probe one.

### Product Info

| Range | Supported Firmware |
|--|--|
| 1.0.0.x / 1.1.0.x | **Firmware 5.4** or higher is required, and the following probe models are supported:<br>- Bridge Technologies VB120<br>- Bridge Technologies VB220<br>- Bridge Technologies VB240<br>- Bridge Technologies VB242<br>- Bridge Technologies VB250<br>- Bridge Technologies VB252<br>- Bridge Technologies VB260<br>- Bridge Technologies VB262<br>- Bridge Technologies VB270<br>- Bridge Technologies VB272<br>- Bridge Technologies VB330<br>- Bridge Technologies VB258 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.1.x   | No                  | Yes                     | -                     | -                       |
| 1.2.0.x   | No                  | Yes                     | -                     | -                       |
| 1.4.0.x   | No                  | Yes                     | -                     | -                       |
| 1.4.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (fixed value: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### SNMP Traps Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

Once the element has been created in DataMiner, the **Element Configuration** page allows you to configure different aspects of the element behavior:

- Configuring credentials for **HTTP Authentication** (if HTTP authentication is enabled on the probe).
- Enabling/disabling part of the polling (e.g. polling of data source alarms is disabled by default).
- Configuring how to handle probe alarms.
- Configuring how to handle old entries in the different tables.
- etc.

### Redundancy

You can access RF redundancy on the Redundancy page. The active input can only be set while *Manual* mode is active.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. The **Thumbnail Mosaic** is only accessible depending on the device configuration and also requires that the client machine has network access to the product.

## How to use

The **Overview** page contains a tree control that can be used to monitor **Inputs**, **Streams**, **Services**, and **PIDs**. Only the streams for which ETR checks are enabled are present in the tree view.

You can configure monitoring via the right-click menu on the **ASI Available Streams**, **Ethernet Available Streams**, **COFDM Available Streams**, and **Satellite Available Streams** tables, which can be found on subpages of the **Streams** page.

The **Polling Configuration** page contains a table that allows you to define the polling periodicity of some groups within the protocol.

The **Service Audio PIDs** page contains a table showing the result of loudness analysis for each audio channel with real-time audio analysis enabled. This table contains a **Metering Method** column that allows you to configure the loudness data reported for each element. At the moment, the table only supports entries with the **Metering Method** set to *EBU R128 Momentary.*

The **Alarm Stream Impact Configuration** page has a table that allows you to define alarm message filters to mark what kind of alarms should have a stream impact. The result of this stream impact is shown in the **Alarm State** column in the Streams table (*OK, Alarms Active*). Via the context menu of the configuration table you can add/remove filter match items. With these match items you can define which alarm messages are taken into account. **Behavior** *Inclusion* will look if one of the defined match items is present, while **Behavior** *Exclusion* will verify if none of the defined match items are present in the alarm message (case insensitive). Note that **only active alarms** with an alarm severity (Warning, Error, Major, or Fatal) are taken into account.

## Notes

### Software Probes

Support for software probes is added in version 1.0.0.10.

If the device is a software probe, it should be configured as such in the **Probe Type** parameter, available on the **Element Configuration** page.
