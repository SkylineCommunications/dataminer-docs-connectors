---
uid: Connector_help_Druid_Raemis
description: Monitor Druid Raemis alarms, heartbeat health, 4G cells, users, and MGW control flow statistics in DataMiner.
---

# Druid Raemis

## About

Raemis is a cellular core network platform by Druid Software that combines 5G, 4G, 3G, 2G, and Wi-Fi radios. The Druid Raemis connector collects alarms, heartbeat status, 4G cell and user data, and MGW control flow statistics for monitoring in DataMiner.

## Key Features

- **Active alarms**: Retrieve active alarms from Raemis through the REST API.
- **Heartbeat monitoring**: Receive SNMP heartbeat traps and monitor missed heartbeats using the configured heartbeat delay and status.
- **Cell and user visibility**: View 4G cell and user data on dedicated element pages.
- **MGW control flow statistics**: Review control and flow identifiers, measurement period, aggregation value, and ingress, egress, and dropped packet/octet counts, including cumulative totals.
- **Configurable polling**: Configure polling for datasets, including MGW Control Flow Stats, on the **Polling Configuration** page.

## Use Cases

### Monitor Raemis health

**Challenge**: Operators need visibility into active alarms and platform availability.

**Solution**: The connector retrieves active alarms and monitors periodic heartbeat traps. Missed-heartbeat alarms use the configured **Heartbeat Delay**.

**Benefit**: Operators can view alarm and heartbeat status in DataMiner.

### Review MGW traffic statistics

**Challenge**: Operators need to inspect ingress, egress, and dropped traffic across media gateway (MGW) control flows.

**Solution**: Review per-entry packet and octet counters, along with cumulative totals, on the **Flow Stats** page.

**Benefit**: Compare traffic counters for each control and flow identifier over the reported measurement periods.

## Technical Reference

### Prerequisites

- DataMiner 10.2.10.0 (build 12242) or later.
- Supported Raemis firmware: 5.2.6.0-1, rd974ae4.
- The connector is Cassandra-ready.

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to access the Raemis REST API. During element creation, specify:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

#### SNMP Connection - Traps

This connector uses an SNMP connection to receive heartbeat traps. During element creation, specify:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

On the **General** page, configure the HTTP API **Username** and **Password**. Configure a proxy server on the same page if required.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Polling

The MGW Control Flow Stats dataset has a default polling interval of 60 seconds. Use the **Polling Configuration** page to enable or disable the dataset and change its interval.