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

On the **General** page:

- The parameter **Last Client KPI Log Entry Timestamp** contains the last timestamp read from the client log files.
- The parameter **Last Processing Timestamp** contains the timestamp from the last time the client log files where processed.
- The average parameters for each KPI. The average is calculated each time the client log files are processed.
- The table **Cube Event Cube Connection**
- The **Clear Data Client KPI** button which will clear all tables and reset the Last log entry timestamp.

On the **Metrics** page, you can find the following tables:

- Cube Metric Initial Data Duration
- Cube Metric Initial Subscriptions Duration
- Cube Metric Full Connect Duration
- Cube Metric Visual Overview Load Duration

On the **Outliers** page, you can find the following tables:

- Cube Metric Initial Data Duration Outliers
- Cube Metric Initial Subscriptions Duration Outliers
- Cube Metric Full Connect Duration Outliers
- Cube Metric Visual Overview Load Duration Outliers

On the **Settings** page, you can configure the table cleanup by specifying the number of days entries should be kept and the maximum number entries to keep.
