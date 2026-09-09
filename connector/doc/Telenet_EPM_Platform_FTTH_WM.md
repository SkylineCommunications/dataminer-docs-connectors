---
uid: Connector_help_Telenet_EPM_Platform_FTTH_WM
---

# Telenet EPM Platform FTTH WM

## About

The Telenet EPM Platform FTTH WM connector is the workflow manager for ONT event distribution in the Telenet FTTH EPM Solution.

The connector reads GZIP event files created by the Kafka consumer, identifies the FTTH Collector element responsible for each ONT, and forwards the events to that collector. It supports ONT status changes, periodic status synchronization, and optional RX/TX measurements.

The connector does not connect directly to Kafka and does not create a separate CSV file for each ONT change. Kafka access and the creation of the event files are handled outside this connector.

## Role in the FTTH EPM Solution

The solution uses the following elements:

- **Telenet EPM Platform FTTH WM**: Imports the routing information, processes Kafka event files, and distributes ONT events to the correct collector elements.
- **Skyline EPM Platform FTTH Collector**: Receives and processes the events for the ONTs assigned to it.
- **Skyline EPM Platform FTTH backend**: Aggregates information received from the collector elements.
- **Skyline EPM Platform FTTH frontend**: Provides the main user view of the FTTH topology and its aggregated information.

### How events are forwarded to collector elements

Each event contains an **NCPID** (Netco Connectivity Product ID), which identifies the ONT-related service in the FTTH solution. The WM uses a routing file that links every known NCPID to a specific FTTH Collector element.

The event flow is as follows:

1. A Kafka consumer writes the received events to GZIP files in the configured event directory.
1. The WM periodically checks this directory and processes eligible files for the configured topic.
1. The WM reads and validates the events. Supported event types are:
   - `statusChange`: Reports that an ONT has changed to in service or out of service. It can also include a reason such as power loss or loss of signal.
   - `statusSync`: Periodically confirms the current ONT status.
   - `lightpathInfo`: Provides optional RX and TX measurements.
1. For each event, the WM looks up the NCPID in the routing table to find the responsible collector's DataMiner Agent ID and element ID.
1. The WM groups all events intended for the same collector and forwards them together to that collector element.
1. Each collector processes the events for the ONTs it manages. The resulting information is then available to the rest of the FTTH EPM Solution for aggregation and presentation.

If an NCPID is not present in the routing table, the event cannot be assigned to a collector and is not forwarded. These events are counted in **Last Import Unknown Entity Count**. If the collector is unavailable or the event batch cannot be sent, the events are counted in **Last Import Events Not Sent Count**.

> [!NOTE]
> **Last Import Events Sent Count** indicates that the WM submitted the events to the collector. The WM does not wait for confirmation that the collector finished processing them.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

The connector requires DataMiner 10.4.0 or later.

After creating the element, open the **Configuration** page. From there, open the **Routing File** and **Kafka Event File** pages and configure the settings below.

#### Routing File

- **System Directory Type**: Select **Local** when the routing directory is on the same DataMiner Agent as the WM element. Select **Remote** when it is on another server.
- **Routing File Directory**: Enter the directory containing the routing file.
- **Routing File Access Username** and **Routing File Access Password**: For a remote directory, enter an account that can access the share. These fields are not required for a local directory.

The routing file maps an NCPID to the DataMiner Agent ID and element ID of its collector. Its expected name is `routing_<WM DMA ID>_<WM element ID>.csv`, for example `routing_1_25.csv`. Each row contains:

```text
NCPID;Collector DMA ID;Collector element ID
```

When the FTTH solution requests a routing-file import, the WM validates the file and replaces its routing table. If the import fails, the existing valid routing information remains in use.

#### Kafka Event File

- **Event Directory Type**: Select **Local** when the event directory is on the same DataMiner Agent as the WM element. Select **Remote** when it is on another server.
- **Topic File Directory**: Enter the directory where the Kafka consumer stores the GZIP event files.
- **Event File Access Username** and **Event File Access Password**: For a remote directory, enter an account that can access the share. These fields are not required for a local directory.
- **Topic**: Enter the Kafka topic represented by the file names. Select **All** to process files for every topic.
- **Maximum Files Per Iteration**: Set the maximum number of event files processed during one cycle. Remaining eligible files are handled in later cycles, oldest first. The default is 100.
- **File Retry Limit**: Set the number of failed processing attempts allowed for an event file. The default is 3.
- **Maximum File Age**: Set how old an event file may be, based on the timestamp in its file name. Older files are not processed. The default is 60 minutes.
- **Event Processing**: Set this to **Enabled** after a valid routing file has been loaded and the event settings have been verified.

## Operation and monitoring

The **General** page shows the outcome of routing-file imports and event-file processing. The most relevant parameters are:

- **Loaded Route File Name** and **Loaded Entries Count**: Identify the active routing file and the number of NCPID-to-collector mappings it contains.
- **Result Last Routing File Processed** and **Message Last Route Routing File Processed**: Show whether the latest routing-file import succeeded and provide details if it failed.
- **Last Import Event File Count** and **Last Event Import Time**: Show when event files were last processed and how many were imported.
- **Last Import Event Count**: Shows the total number of events read during the latest successful import.
- **Last Import Mapped Event Count**: Shows how many events were matched to collector elements through their NCPID.
- **Last Import Unknown Entity Count**: Shows how many events could not be matched and were therefore not forwarded.
- **Last Import Events Sent Count**: Shows how many events were submitted to collector elements.
- **Last Import Events Not Sent Count**: Shows how many mapped events could not be sent to their collector elements.
- **Total Excluded File Count**: Shows how many event files reached the retry limit. Excluded files remain in the source directory but are no longer processed.

The **Routing** page lists the active mapping between each NCPID and its collector element. Use this table when investigating unknown NCPIDs or events sent to an unexpected collector.

## Recommended setup order

1. Configure access to the routing-file directory.
1. Configure access to the Kafka event-file directory and select the required topic.
1. Let the FTTH solution request and complete the routing-file import.
1. Confirm on the **General** and **Routing** pages that the routing table contains the expected NCPID-to-collector mappings.
1. Set **Event Processing** to **Enabled**.
1. Verify that the import, mapped, unknown, sent, and not-sent counters reflect the expected event flow.

## How to use

After the initial configuration, the WM automatically checks for event files every five seconds while **Event Processing** is enabled and a routing table is available. No manual action is required for normal event forwarding.

When troubleshooting, first verify that the expected routing file is loaded. Then compare **Last Import Event Count**, **Last Import Mapped Event Count**, **Last Import Unknown Entity Count**, **Last Import Events Sent Count**, and **Last Import Events Not Sent Count** to determine whether the issue occurred while reading the event, mapping its NCPID, or forwarding it to the collector element.