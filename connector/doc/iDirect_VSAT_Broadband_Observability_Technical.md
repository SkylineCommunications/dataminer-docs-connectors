---
uid: Connector_help_iDirect_VSAT_Broadband_Observability
---

# iDirect VSAT Broadband Observability

This driver is based of the iDirect NMS platform but differs in its use case. It's primary purpose is to aggregate data across the networks in a teleport to present in a low code app for the VSAT Broadband Observability solution.

## About

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial connector         |-         |-         |

### System Info
|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To use the connector, the credentials to access the MySQL database need to be entered on the General page. The Config server is the server where the Configured details of the teleports/networks/netmodems are stored. The Archive servers are the servers where the statistics data are stored. 

The Site Count archive server refers to the server with the event message/state changes of the netmodems. The Congestion and Traffic Capacity archive server refers to the server with the bandwidth and traffic data.

### Redundancy

There is no redundancy defined.

## How to use

The iDirect Evolution Platform updates a MySQL Database as it gets data. This driver uses MySQL queries to that database to update itself with data.

As such, we will see no traffic on Stream Viewer.

On the **General** Page, users can key in the details to access the MySQL database. 

If there are data consolidation periods, users should use block out an appropriate period of time that the server needs to consolidate data for. The driver will not poll data within that time period and then use history sets to backpoll data for the period where data is not being polled.

On the **Resources** page, the total information captured for the netmodems, networks, group QOS and Beams are collated.
This page can be used to see an overview of how a network is performing for all the different metrics being observed.

### Site Count Monitoring

Each site refers to a remote/netmodem.

The Site Counts are calculated using two methods, the original method is via the state change logs and the other (UCP) method is via event messages.

*Original* (State Change Logs): When a change is recorded in the MySQL Database, we update the state of the netmodem to the new state.

*UCP* (Event Message Logs): Sites are considered Online if they have an event message captured within the past 30 seconds. Otherwise they are considered Offline. 

On the network level, we aggregate the total number of sites online and offline and monitor the health of the network.

On the Teleport level, we also monitor the teleports site count and health across all networks in the teleport. 

### Network Congestion

The downstream network congestion is measured in terms of kilosymbols per second. 

The upstream network congestion is measured in the allocated slots against the free slots. 

### Traffic and Capacity

The traffic and capacity measures and monitors the bandwidth upstream and downstream of each network. The utilization of each network is measured by the 95th percentile bandwidth against the configured bandwidth value.

The configuration page allows the user to fix the value of the configured upstream and downstream bandwidths if they are inaccurate from the expected reading due to differences in calculation that are proprietary to iDirect.

The Monthly calculation page calculates data for each network across the past month and runs every 1st of the month. The 95th percentile values of the total data is taken for each network for reporting purposes.

### Group QOS Congestion

The group QOS congestion measures the upstream and downstream congestion for a Group QOS and show the status of that Group QOS in the form of criticality.