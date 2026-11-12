---
uid: Connector_help_Thales_Amber_Technical
description: "Learn how to use the Thales Amber connector, including the SNMP connection, trap configuration, polling settings, and the stream, service, and PID pages."
---

# Thales Amber

## About

The Thales Amber is a compact 1RU MPEG-2 remultiplexer that combines up to eight ASI transport streams into a DVB/ATSC-compliant output, with service, PID, and PSI/SI table filtering and re-mapping.

This connector retrieves information from the device via SNMP and processes the alarm traps of the device. It monitors the unit information, the state of the inputs and outputs, the transport streams and their bit rates, the services, and the PIDs.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The connector starts polling as soon as the element is created; no further configuration is required.

To benefit from the trap-driven refresh of the tables, configure the device to send its SNMP traps to the IP address of the DataMiner Agent hosting the element.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The element has a **General** page with the unit information, an **IO Status** page, one page each for the **Streams**, **Services**, and **PIDs** of the multiplex, a **Configuration** page, and an **Overview** page that shows the multiplex as a tree.

### General Page

This page shows the unit type, product model, serial number, part number, and software versions, and the capabilities of the unit: whether it supports redundancy and scrambling, the number of configurations, and the number of ASI, Ethernet, QPSK, 8VSB, Topaz, and Open Mux inputs, ASI outputs, HD and SD services, processors, GPI inputs, and DPI programs. This information is polled once a minute. The capability counts are monitored, so an alarm template can flag a change in the hardware configuration.

The **Polling...** page button opens the **Polling Settings** subpage with two toggles. Both toggles are empty on a new element, which the connector treats as *Yes*.

- **Polling All Parameters**: When set to *Yes*, the input and output status, stream, service, and PID tables are polled every 10 seconds and the unit information and TDT configuration every minute. When set to *No*, the element switches to slow polling: only the service, PID, and output status tables are still polled, once an hour, and only the unit type, serial number, software version, product model, and number of ASI inputs are refreshed, once a day. The Transport Stream table, the PID bit rates (PID Bandwidth table), the TDT configuration, and the remaining General page parameters are not polled at all in slow mode, so their values and trends freeze; the input status, service, and PID tables are still refreshed when the device sends an alarm trap. Use the slow mode only when the device is sensitive to SNMP load.
- **Fast Polling**: When set to *Yes*, the input status and TDT configuration tables are polled every 10 seconds, regardless of the setting above. Set it to *No* to stop this extra poll; in slow polling mode, the input status table is then only refreshed by traps.

### IO Status Page

This page lists the inputs and outputs of the unit, with their ID, type (for inputs: *ASI*, *Ethernet*, *VSB*, *QPSK*, *SDI*, *CVBS*, *Analog Audio*, or *AESEbu*; for outputs: *ASI* or *Ethernet*), type index, and state. The **Input State** and **Output State** columns are monitored and show *Not Configured*, *OK*, *Warning*, or *Error*; check them first when a stream or service alarm appears, as a failing input explains all downstream alarms at once.

### Streams Page

The **Transport Stream Table** shows, per stream, the useful rate, the stuffing rate, and the total rate, with the minimum and maximum useful and stuffing rates, and the number of services and PIDs in the stream. All rates and counters are monitored and trended. A rising stuffing rate at a constant total rate means that the useful content of the stream is shrinking, which is often the first sign of a service or PID that is no longer delivered.

### Services Page

The **Service Table** shows every service with its stream ID, service ID, name, running state (*Not Running*, *Starts In A Few Seconds*, *Pausing*, or *Running*), and bit rate. The running state, bit rate, and name are monitored. The **Service State** column shows how the row compares to the previous poll (*New*, *Updated*, *Equal*, *Deleted*, or *Recreated*).

Services that disappear from the device are not removed from the table immediately but marked as *Deleted*, so that an alarm on a vanished service remains visible. Click **Remove Not Available Service Entries** to clear these rows once the situation has been handled.

### PIDs Page

The **View PIDs** page shows a read-only view of every PID with its stream ID, service ID, PID, type (*Video*, *Audio*, *Audio-Ext*, *Private SI*, *Teletext-6*, or *ECM*), scrambling state, and current, minimum, and maximum bit rate. The bit rates are monitored and trended.

The **PIDs...** page button opens the underlying **PID Table** and **PID Bandwidth Table**. As on the Services page, PIDs that disappear from the device are kept with the state *Deleted* until you click **Remove Not Available PID Entries**.

### Configuration Page

This page shows the **TDT** (Time and Date Table) configuration of the unit: the configured TDT entries, the input they are taken from, and their row status. This table is polled once a minute, or every 10 seconds when **Fast Polling** is enabled on the Polling Settings subpage.

### Overview Page

This page shows the multiplex as a **tree view**: each transport stream with the services it carries and the PIDs of each service. Alarms on a PID bubble up to its service and stream, so the tree is the quickest way to locate the origin of an alarm on the element. Use the Streams, Services, and PIDs pages for the detailed values.

### Trap Handling

The connector processes the alarm appearance and alarm disappearance traps of the device. When such a trap is received, the input and output status, service, and PID tables are polled immediately, independently of the polling settings. The traps themselves are not shown as alarms; the resulting parameter changes are.

### Embedded Web Server Page

This page embeds the web interface of the device, which you can use to change the configuration of the multiplex. The connector itself is read-only, apart from the polling settings and the buttons that clean up the service and PID tables.
