---
uid: Connector_help_iDirect_VSAT_Broadband_Observability_Technical
---

# iDirect VSAT Broadband Observability

## About

With the iDirect VSAT Broadband Observability connector, network administrators can achieve better visibility, optimize traffic management, and ensure uninterrupted broadband connectivity with ease.

This connector is based on the iDirect NMS platform but differs in its use case. Its primary purpose is to aggregate data across the networks in a teleport, so the VSAT Broadband Observability solution can present these in a low-code app.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To use the connector, on the **General** page, you will need to configure the different database servers and specify the credentials to access them.

- The **Config** server is the server where the configured details of the teleports/networks/net modems are stored.
- The **Archive** servers are the servers where the statistics data are stored.
- The **Site Count Archive** server refers to the server with the event message/state changes of the net modems.
- The **Congestion and Traffic Capacity** archive server refers to the server with the bandwidth and traffic data.

## How to use

The iDirect Evolution Platform updates a MySQL database as it gets data. This connector uses MySQL queries to that database to update itself with data. As such, no traffic will be shown in Stream Viewer for this connector.

On the **General** page, you will need to specify the details to access the MySQL database, as mentioned above.

If there are data consolidation periods, you should block out an appropriate period of time that the server needs to consolidate data for. The connector will not poll data within that time period and then use history sets to backpoll data for the period where data was not being polled.

On the **Resources** page, the total information captured for the net modems, networks, group QOS, and Beams is collated. This page can be used to see an overview of how a network is performing for all the different observed metrics.

### Site Count Monitoring

Each site refers to a remote/net modem. The Site Count information is calculated using two methods. The original method is via the state change logs and the other (UCP) method is via event messages:

- **Original** (state change logs): When a change is recorded in the MySQL Database, the state of the net modem is updated to the new state.
- **UCP** (event message logs): Sites are considered online if they have an event message captured within the past 30 seconds. Otherwise, they are considered offline.

On the network level, the total number of sites online and offline is aggregated and the health of the network is monitored.

On the teleport level, teleport site count and health are also monitored across all networks in the teleport.

### Network Congestion

The downstream network congestion is measured in terms of kilosymbols per second.

The upstream network congestion is measured in the allocated slots against the free slots.

### Traffic and Capacity

The traffic and capacity measures and monitors the bandwidth upstream and downstream of each network. The utilization of each network is measured by the 95th percentile bandwidth against the configured bandwidth value.

The Traffic Capacity Configuration page allows you to fix the value of the configured upstream and downstream bandwidths if they do not match the expected reading because of differences in calculation that are proprietary to iDirect.

The Monthly Calculations page calculates data for each network across the past month. This calculation runs every first day of the month. The 95th percentile values of the total data are taken for each network for reporting purposes.

### Group QOS Congestion

The group QOS congestion measures the upstream and downstream congestion for a Group QOS and shows the status of that Group QOS in the form of criticality.
