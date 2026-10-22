---
uid: Connector_help_Generic_Database
description: "Learn how to use the Generic Database connector to query MySQL, MSSQL, ODBC, and Elasticsearch sources and display results in DataMiner."
---

# Generic Database

## About

The **Generic Database** connector lets you turn virtually any relational or search database into a live data source inside DataMiner. Instead of building a dedicated integration per system, you define your own queries and let the connector run them on demand or on a schedule, bringing the results straight into DataMiner for monitoring, trending, and alarming.

The connector supports **MySQL, Microsoft SQL Server (MSSQL), ODBC data sources, and Elasticsearch**, and can present query results as a single value or as a fully structured table, making it a flexible bridge between your databases and your operational overview.

## Key Features

- **Multi-database support**: Connect to MySQL, MSSQL, ODBC, and Elasticsearch data sources from a single connector.

- **Flexible result parsing**: Present each query result as a **string**, **numeric value**, or as an **array** rendered in structured tables.

- **On-demand and scheduled queries**: Manage multiple queries in one overview, each with its own execution interval, or trigger them manually when needed.

- **Automatic CSV export**: Write array query results to timestamped CSV files in a configurable folder for reporting and offline processing.

- **Resilient collection**: Configure a per-query retry mechanism that automatically retries transient failures within the query's own scheduling budget.

## Use Cases

### Bringing Database Data Into Your Operational Overview

Run custom queries against business or operational databases and surface the results directly in DataMiner, so key figures from external systems live next to the rest of your monitored infrastructure.

![Generic Database Query Overview](~/connector/images/Generic_Database_marketing_query_overview.png)

### Structured Array Results

Return multi-column, multi-row query results and display them as structured tables in DataMiner, ready for trending and alarming on the individual values.

![Generic Database Table Result](~/connector/images/Generic_Database_marketing_table_result.png)

### Reporting Through Automated Exports

Automatically export array query results to timestamped CSV files, enabling scheduled reporting workflows and easy integration with downstream tools without manual extraction.

![Generic Database CSV Export](~/connector/images/Generic_Database_marketing_csv_export.png)

## Technical Reference

For detailed information on connections, configuration, and usage of each range, see the [technical documentation](xref:Connector_help_Generic_Database_Technical).
