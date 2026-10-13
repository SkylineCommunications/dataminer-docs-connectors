---
uid: Connector_help_TestTree_StreamProbe_Technical
description: "Learn how to configure the TestTree StreamProbe connector to monitor transport streams, RF reception, OTT services, and provisioning over HTTP and SNMP."
---

# TestTree StreamProbe

## About

The **TestTree StreamProbe** connector monitors transport streams, programs, PIDs, RF reception, and OTT services using HTTP data and SNMP traps. It also exposes provisioning information and stream provisioning controls.

See the [connector overview](xref:Connector_help_TestTree_StreamProbe) for key capabilities and supported firmware. This page describes connector version **1.0.1.20**, which requires DataMiner **10.3.0.0 - 12752** or higher.

## Configuration

### Connections

#### HTTP Connection

The HTTP connection retrieves monitoring and provisioning data and sends stream provisioning commands. The following settings need to be configured during element creation:

- **IP address/host**: The polling IP address or host of the StreamProbe server.
- **IP port**: The destination port. Default: *433*. Set this to the port configured on the server.
- **Bus address**: Default: *ByPassProxy*, to bypass the proxy.

#### SNMP Connection

The SNMP connection handles probe traps. The probe ID also identifies the probe used by HTTP commands.

- **IP address/host**: The IP address of the probe.
- **Device address**: The probe ID, for example, *1*.
- **Port number**: Default: *161*.
- **Get community string**: Default: *public*. Match the device configuration.
- **Set community string**: Default: *private*. Match the device configuration.

### Initialization

1. Check **Probes** to confirm that the expected probe is listed.
1. Check **General** to confirm the selected probe's identity and software version.
1. Review **Polling Settings** and enable the datasets needed for your monitoring workflow.

### Web Interface

The **Web Interface** page opens the product interface at the HTTP polling IP address. It is only accessible when the client machine has network access to the product.

## How to Use

### General

Use **Probe Status**, CPU and memory usage, and **Total Bitrate** to distinguish probe availability or resource issues from a problem affecting individual content. Compare declared and active stream and program counts to identify missing monitored content.

**Automatic Removal Delay** exposes a retention setting with a default of *5 days*; *0* is displayed as **N/A**. The current source does not register the legacy delayed-cleanup actions, so do not rely on this setting alone to remove unavailable entries. See [Notes](#notes).

### Streams

Use the **Transport Stream Table** to identify the affected stream and compare its status and bitrate with expected delivery. **Stream Filter** provides a user-defined label used in display keys; it does not restrict polling. Follow the same stream into **ETR** or **Overview** to investigate its programs, PIDs, and alarms.

**Remove Stream** is a device-side deletion action, not a way to hide a row. For provisioning changes, use [Stream Provisioning](#stream-provisioning).

### ETR

Use the **Stream ETR Table** to investigate transport-level errors for the affected stream, such as sync byte errors and PAT repetition or PCR measurements. Correlate these measurements with stream availability and related alarms before investigating individual program quality.

### Program Status

Use the **Program Status Table** to check whether the expected service is present in its transport stream and whether audio, video, or signaling alarms affect it. **Service Filter** labels the program in display keys; it is not a polling filter. Follow the program into **PID Status** or **Programs QOE** for more detail.

**Remove Program** deletes a program from the probe; it is not a display-only cleanup action.

### PID Status

Use the **PIDs Status Table** to check the coding and status of individual PIDs and correlate continuity, decoding, or signaling errors with their parent program and stream.

**Automatically Remove Missing PIDs** enables removal in the SNMP no-packet alarm path. Although its tooltip says qualified PIDs are retained, that trap handler does not check qualification before deleting a row. **Remove Missing PID** is also displayed, but this version does not register its legacy removal QAction; do not rely on it for manual cleanup.

### Programs QOE

Use the **Programs QOE Table** to relate viewer symptoms to program-level indicators. Video black or freeze indicators help investigate picture problems, while missing audio or silence indicators help investigate sound problems. Compare these with **ETR** and **PID Status** to distinguish transport errors from content quality symptoms. Audio measurements cover up to four audio PIDs per program.

### RF

Compare RF configuration with receiver status when investigating reception problems. Check tuning settings such as frequency, bandwidth, and symbol rate against the intended input, then relate receiver measurements to the affected stream.

### Alarms

Use the **Alarms Table** to correlate active probe alarms with their stream, program, or PID. **Alarms Retrieve Method** selects **HTTP Request** (the default) or **SNMP Traps**. HTTP alarm requests run only when **HTTP Request** is selected, so enabling **Alarm List** alone does not ensure HTTP alarm retrieval.

**Last Trap Received** indicates when a trap was last received; it does not confirm that all HTTP datasets are current. Check the selected retrieval method, **Alarm List** polling, and trap reception when investigating missing alarm information.

### OTT Services

Use the OTT service information to identify affected monitored URLs and compare their diagnostic information and profile counts. Compare the monitoring results with the ABR provisioning views to check that the intended service and components are configured.

### Probes

Use the probe list to verify discovery, availability, software versions, and resource usage across probes. Confirm the element's probe ID before investigating unexpected or missing content for a particular probe.

### ABR Probe Provisioning

Review the configured ABR streams and URLs to confirm that the intended content is assigned to the probe. Compare this configuration with **OTT Services**, rather than treating a configured entry as proof of successful monitoring.

### ABR Provisioning Tree

Expand a configured ABR stream to inspect its related components. Use this hierarchy to locate the profiles belonging to an affected service before comparing them with monitoring results.

### ABR Profiles

Open **ABR Profiles** from **ABR Probe Provisioning** to inspect the component details. Compare the configured profiles with the expected media variants when a service or individual variant is unavailable.

### Stream Provisioning

The **Transport Stream Provisioning** page displays the **Stream Provisioning Table**. The same configuration is accessible by selecting a stream in **Overview** and opening its **Stream Provision** tab.

The table has editable settings for stream configuration. Verify addressing, input selection, monitoring state, and media format before applying changes to the probe.

The context menu of the table has the options **Add item ST2022-6**, **Add item ST2110-20**, **Add item ST2110-30**, and **Add item MPEG-2 Transport Stream**. Choose the format matching the intended input and supply the corresponding configuration.

> [!CAUTION]
> **Delete selected item** permanently deletes the selected provisioning item. Disable its monitoring before deleting it, and verify that you selected the intended stream.

### Service Provisioning

The **Service Provisioning Table** is a read-only view of configured SMPTE ST 2110 services. Each row represents one constituent stream of a service on the **Blue** or **Red** network. This page is not a service creation editor.

1. Filter the table by **Service ID** to collect the rows belonging to the service.
1. Compare **Network** and **Type** to verify the intended constituent media streams on each network.
1. Check **Service State** and **Stream State** against the intended enabled/disabled configuration.
1. Compare **Multicast IP**, **Port**, **Source IP**, **Interface IP**, **VLAN ID**, and **Input Link** with the expected routing.
1. Compare video or audio format settings with the intended media format.
1. Use **Stream ID** to correlate the configured stream with monitoring data; distinguish it from **Stream ID NMS** when comparing external identifiers.

Enabled/disabled states describe configuration, not service health. Blank or **N/A** media fields can be inapplicable to that stream type and are not, by themselves, evidence of a fault.

### Groups

Use the read-only group memberships to identify content related to an affected group. Map the listed program and URL IDs to the corresponding source content before continuing the investigation. This page does not create groups or execute operations on their members.

### Macros

Use the read-only **Macro Services Table** to inspect configured macro service names, descriptions, and memberships. **Program IDs** and **URL IDs** identify the source content included in a macro service; these lists are not controls for executing macros.

### Overview

The tree links streams to programs, PIDs, and alarms. Expand the affected stream, then its program, then its PID to narrow the investigation. Use the related **Programs**, **PIDs**, and **Alarms** tabs to compare entries at the selected level. The stream's **Stream Provision** tab links monitoring to its configuration.

### Polling Settings

The **Polling Manager** controls dataset intervals and administrative states. All datasets default to *1 minute*: **Probe List**, **Stream List**, **Stream ETR List**, **Stream Programs List**, **PID List**, **Alarm List**, **Stream Provisioning**, **Probe Provisioning**, **Service Provisioning**, **Groups**, and **Macro Services**. **Probe List** is mandatory. **Stream Programs List** updates both **Program Status** and **Programs QOE**.

1. Ensure the dataset relevant to the affected page is enabled using **Admin Status** or the context menu's **Enable** action.
1. Use the row's **Poll** control or the context menu's **Poll** action to request a manual poll.
1. Check **Last Poll Time**, **Last Poll Status**, and **Last Poll Status Info** before assuming a device fault.

The context menu also provides **Enable (Forced)**, **Disable**, **Disable (Forced)**, **Enable All**, **Disable All**, **Poll All**, and **Reset to Default**. The page's **Refresh All** button requests a refresh of all datasets. Mandatory polling constraints still apply.

### Normalization Subpages

Open **Normalization** from **Streams**, **Program Status**, or **PID Status** to access **Transport Stream Normalization**, **Program Status Normalization**, or **Pids Status Normalization**, respectively.

These tables store reference measurements used for DataMiner normalization. The bulk controls copy current measurements into normalized references, while editable cells update individual references. Establish references only when the monitored content is in the intended operating state; these changes affect DataMiner references, not probe provisioning.

## DataMiner Connectivity Framework

The connector declares two fixed, external, bidirectional DCF interfaces: **IP 1** and **IP 2**. Use these interfaces when modeling the probe's network connectivity in DataMiner. The **Blue** and **Red** values in Service Provisioning describe service stream configuration; they do not configure redundant element polling.

## Notes

- Provisioning changes and device-side removal affect monitored content. Use an account authorized to make these changes and confirm the selected probe and content before applying them.
- Table cleanup and device-side deletion are different operations. Cleanup can remove monitoring history from the element without removing content from the probe.
- Qualified missing entries can be retained for investigation, but qualification is not a guarantee against removal. In particular, the SNMP no-packet cleanup path does not check PID qualification.
- This version does not expose the older **Automatically Remove Missing Streams**, **Remove Missing Stream**, **Automatically Remove Missing Programs**, and **Remove Missing Program** controls included in previous versions of the connector.
