---
uid: Connector_help_Druid_Raemis
description: "Monitor Druid Raemis alarms, heartbeat health, 4G cells, users, and MGW control flow statistics in DataMiner."
---

# Druid Raemis

## About

Raemis is a cellular core network platform by Druid Software that combines 5G, 4G, 3G, 2G, and Wi-Fi radios. The Druid Raemis connector collects alarms, heartbeat status, 4G cell and user data, and MGW control flow statistics for monitoring in DataMiner.

## Key Features

- **Active alarms**: Get the active alarms from Raemis, retrieved through the REST API.
- **Heartbeat monitoring**: Monitor missed heartbeats using the configured heartbeat delay and status, based on received SNMP heartbeat traps.
- **Cell and user visibility**: View 4G cell and user data on dedicated element pages.
- **MGW control flow statistics**: Review control and flow identifiers, measurement period, aggregation value, and ingress, egress, and dropped packet/octet counts, including cumulative totals.
- **Configurable polling**: Configure polling for datasets, including MGW Control Flow Stats.

## Use Cases

### Monitor Raemis Health

**Challenge**: Operators need visibility on active alarms and platform availability.

**Solution**: The connector retrieves active alarms and monitors periodic heartbeat traps. Missed-heartbeat alarms use the configured **Heartbeat Delay**.

**Benefit**: Operators can view alarm and heartbeat status in DataMiner.

### Review MGW Traffic Statistics

**Challenge**: Operators need to inspect ingress, egress, and dropped traffic across media gateway (MGW) control flows.

**Solution**: Review per-entry packet and octet counters, along with cumulative totals, on the **Flow Stats** page.

**Benefit**: Compare traffic counters for each control and flow identifier over the reported measurement periods.

## Technical Reference

### Prerequisites

- Supported Raemis firmware: 5.2.6.0-1, rd974ae4.

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

The MGW Control Flow Stats dataset has a default polling interval of 60 seconds. Use the **Polling Configuration** page to enable or disable the dataset or to change its interval.
