---
uid: Connector_help_Druid_Raemis_Technical
---

# Druid Raemis

## About

The **Druid Raemis** connector monitors the Raemis platform through its REST API and SNMP heartbeat traps. It provides active alarm, user, 4G cell, and MGW control flow statistics data.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to access the Raemis REST API. Configure the following during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

#### SNMP Connection - Traps

This connector uses an SNMP connection to receive heartbeat traps. Configure the following during element creation:

- **IP address/host**: The IP address of the trap source.
- **IP port**: The port used for SNMP communication.

SNMP settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

On the **General** page, configure the HTTP API **Username** and **Password**. Configure a proxy server on the same page if required.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Active Alarms

The **Active Alarms** table on the **Alarms** page displays alarms retrieved from the REST API.

### Heartbeat

The connector monitors platform availability using periodic SNMP heartbeat traps. If the time between heartbeats exceeds **Heartbeat Delay**, an alarm is raised on **Heartbeat Status**.

### MGW Control Flow Stats

The **Flow Stats** page displays the **MGW Control Flow Stats** table. Use the entry ID, **Control ID**, and **Flow ID** to identify each record. The table also includes the aggregation value and measurement period, along with ingress, egress, and dropped packet and octet counts for the measurement period and cumulative totals.

Use **Polling Configuration** to enable or disable this dataset and set its polling interval. The default interval is 60 seconds.