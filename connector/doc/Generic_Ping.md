---
uid: Connector_help_Generic_Ping
---

# Generic Ping

The Generic Ping connector provides a virtual element for checking connectivity to configured IP addresses or hostnames. It sends ICMP or TCP pings, measures jitter, calculates availability statistics, and can trace the route to a destination.

## About

Use the **Ping** page to manage destinations and monitor ping results. The connector also provides a **Trace Route** page and element-level settings for ping defaults and pump diagnostics.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and requires no connection input during element creation.

### Initialization

The connector initializes default ping and jitter settings when the element starts. To change the defaults used for new Ping Table rows, open **Ping Configuration** from the **Ping** page and edit the **Ping Default Values** and **Jitter Default Values**.

The connector requires DataMiner 10.4.0.0 or later.

## How to Use

### Ping

The **Ping Table** contains one row per configured destination. Use the table context menu to add rows, enable or disable all rows, delete selected rows, or delete all rows. **Unique Description** identifies each row and must be unique.

One timer-triggered QAction runs the ping and jitter pumps every second. The pumps keep independent schedules and runtime limits.

Set **Destination Address** to an IP address or hostname and set **Admin Status** to **Enabled** to schedule regular pings. Disabling **Admin Status** also disables jitter for that row. Configure the following settings as needed:

- **Protocol**: Choose **ICMP** or **TCP**. ICMP is the default. For TCP, specify **Port**; **Buffer Size** and **TTL** apply to ICMP and are disabled for TCP.
- **Interval**: Time between ping cycles, in seconds.
- **Pings per Cycle**: Number of probes sent in each ping cycle. The probes in a cycle are sent concurrently.
- **Timeout Time**, **Buffer Size**, and **TTL**: Configure the ping timeout, packet buffer size, and time to live.
- **Jitter Admin Status**: Enable or disable jitter measurement independently of regular ping. Jitter probes use ICMP, regardless of the row's selected ping protocol.

Each enabled row reports the latest ping result, minimum, maximum and average response times, success percentages, packet loss per cycle, and daily, weekly, and monthly availability. The **Ping Status** and **Jitter Status** columns indicate whether a cycle is running. Completed results are published on a subsequent pump run, which occurs every second.

### Jitter

Jitter is measured by sending the configured probes sequentially for each enabled row. **Jitter Interval** sets the time between cycles in seconds, **Jitter Ping Interval** sets the spacing between probes in milliseconds, and **Jitter Pings per Cycle** sets the number of probes in a cycle.

The connector calculates the absolute differences between consecutive successful probe response times and displays the minimum, maximum, average, and median delta. At least two probes in a cycle must succeed to produce jitter values.

The illustration shows the order and spacing of jitter probes. The initial defaults are a 2-second cycle interval, a 15-millisecond probe interval, and 4 probes per cycle.

![Sequence of jitter probes within and between cycles](~/connector/images/Generic_Ping_ping_sequence.jpg)

### General

The **General** page displays aggregated ping statistics:

- **Maximum**, **Minimum**, and **Average Success** show the success percentages across enabled ping rows.
- **Maximum**, **Minimum**, and **Average Ping Time** show response-time statistics for enabled ping rows.
- **Current Responding Ping** shows the percentage of enabled destinations currently responding.
- **AVG Window Size** sets the number of ping cycles used for the rolling statistics.
- **Daily**, **Weekly**, and **Monthly Availability Average** show availability averages across enabled ping rows.

### Ping Configuration

Open **Ping Configuration** from the **Ping** page to edit element defaults and monitor the ping and jitter pumps. The default values are applied to new rows; existing rows keep their own settings.

The pump limits can be adjusted while the element is running. Changes take effect on the next pump run:

- **Ping Maximum in-Flight Probes** limits reserved probe capacity for unfinished ping cycles (default: *1200*).
- **Ping Maximum Cycle Starts per Run** limits the ping row cycles started in one run (default: *500*).
- **Jitter Maximum in-Flight Cycles** limits unfinished jitter cycles (default: *300*).
- **Jitter Maximum Cycle Starts per Run** limits the jitter row cycles started in one run (default: *500*).

Increasing these limits can increase resource use or QAction execution time. The page also exposes trended diagnostics for due cycles waiting, in-flight work, completed cycles awaiting processing, and ICMP sends that remain pending after their deadline or have exceeded it in total. The pending and total ICMP diagnostics are maintained separately for ping and jitter; TCP sends are not included.

### Trace Route

On the **Trace Route** page, enter a destination address and select **Start Trace Route** to run a trace. The **Trace Route Nodes** table shows the hops and their status; enable **Calculate Round Trip Times** in **Trace Route Settings** to include intermediate-hop round-trip times.

Use **Max Hops** and **Timeout** in **Trace Route Settings** to configure the maximum number of hops and timeout per hop. Their defaults are 30 hops and 5000 milliseconds. Select **Stop Trace Route** to stop an active trace.

## DataMiner Connectivity Framework

The connector supports DataMiner Connectivity Framework (DCF).

## Notes

The connector supports the Generic Ping Connector API through InterApp. The API can add or update Ping Table entries, update settings in bulk, clear the table, and request table data. The InterApp receiver is parameter 9000000; the connector returns responses through parameter 9000001.
