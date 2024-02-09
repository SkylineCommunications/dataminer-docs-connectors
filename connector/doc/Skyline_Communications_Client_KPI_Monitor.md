---
uid: Connector_help_Skyline_Communications_Client_KPI_Monitor
---

# Skyline Communications Client KPI Monitor

This connector can be used to process SLClient log files to retrieve performance KPIs.

## About

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version  | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

On the **General** page, there are several tables each related to a KPI:

- Cube Metric Initial Data Duration
- Cube Metric Initial Subscriptions Duration
- Cube Metric Full Connect Duration
- Cube Connection
- Visual Overview Load Duration

On the **Settings** page, you can configure the table cleanup by specifying the number of days entries should be kept and the maximum number entries to keep.
