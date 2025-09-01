---
uid: JPEPBiH_AMM_Meter_Data_Collector_Technical
---

# JPEPBiH AMM Meter Data Collector

## About

This connector provides the ability for users to collect real-time power data from grid plant meters via the AMM system.

## Configuration

### Connections

#### HTTP Connection – IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### General

The General page displays a **Distributed Grid Plants** table.
This table contains all the data regarding meters that are being monitored by the connector.

Users are able to add, edit, and delete meters from the table, by right-clicking on the table and selecting the appropriate option from the context menu.
When adding or editing the meter data in the table, the user is required to provide the **Meter Serial Number**.

The table contains the following columns:
- **Name**: The name of the meter.
- **Meter Serial Number**: The serial number of the meter.
- **BOS**: The balance responsible party of the meter.
- **Measurement Point Name**: The name of the measurement point.
- **Result Type Name**: The name of the result type.
- **Constant**: The constant of the meter.
- **Last Received Power Value**: The last received power value from the meter.
- **Power**: The current power value of the meter.

### Configuration

This page contains one configuration parameter, which enabled the user to define the **Job Execution Interval**. This configuration parameter defines how often the connector will execute job to obtain the power data.
The interval can be set to 5, 10 and 15 minutes.