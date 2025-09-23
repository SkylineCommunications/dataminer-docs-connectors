---
uid: Connector_help_Bridge_Technologies_VB_Probe_Series_Technical
---

# Bridge Technologies VB Probe Series

## About

This connector allows you to monitor and control **Bridge Technologies probe** devices.

It uses the **EII API (Enterprise Information Integration)** provided by the vendor for regular polling of the probes over **HTTP**, as well as **SNMP traps** in order to get quick alarm updates.

 **Firmware 5.4** or higher is required, and the following probe models are supported:
 
 - Bridge Technologies VB120
 - Bridge Technologies VB220
 - Bridge Technologies VB240
 - Bridge Technologies VB242
 - Bridge Technologies VB250
 - Bridge Technologies VB252
 - Bridge Technologies VB260
 - Bridge Technologies VB262
 - Bridge Technologies VB270
 - Bridge Technologies VB272
 - Bridge Technologies VB330
 - Bridge Technologies VB258

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
