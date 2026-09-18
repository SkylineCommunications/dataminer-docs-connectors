---
uid: Connector_help_Generic_Database_Technical
description: "Configure and use the Generic Database DataMiner connector to run queries against MySQL, MSSQL, ODBC, and Elasticsearch data sources."
---

# Generic Database

## About

This connector is used to make queries on demand. It retrieves data from a query inserted in a box in the element and provides information such as the Query Result String, Query Result Numeric, Query Status, Query Status Config OK, Query Status Config Alarm, Query Execution Time, and Query Execution Status.

> [!NOTE]
> Version, product, and system information is maintained directly in the connector through the `VersionHistory` tags in the Protocol.xml and is therefore no longer duplicated here.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use (1.0.0.x range)

### General page

This page displays the **Query Execution Interval**, which allows you to choose the interval between queries. This interval can also be disabled.

You can select the appropriate **Date Time Mode** and specify the **Date Time Format**.

If you want to monitor more than one query at once, you can add multiple queries with the **Add Query** button.

In order to execute a query on demand, you can use the **Force Execution** drop-down box to select which query should be executed. The result will be displayed in the table below.

### Configuration page

To configure the element using this connector, go to the **Configuration** page and select the appropriate **Database Type**. Then fill in the **Server Address**, **Database Name**, **User Name**, and **Password**.

Via the **Test Connection** page button, you can check if the connection has been established. Click the **Connect** button and then check the **Connection Result** field.

## How to Use (2.0.0.x range)

### General page

On this page, a **Query Overview** table is used to create and display queries. With the **Result Configuration** option, you can select how the query result will be parsed. The possible options are *String* and *Array*. After each query result of type String, the tables Table Result and Table Result 2 will be cleared. That means if you first execute a query of type Array, and then execute a query of type String, the data for the query of type Array will be lost.

### Table Result page

This page displays the array result as a table. It supports a maximum of 10 columns in the query result. It supports both string and numeric results. The primary key of this table will be the value from the first column in the query result. If there are duplicate values in the first column of the query result, then only the first row with this value will be displayed. It has a very basic way of converting a string result to numeric, which causes the numeric result to not always be accurate. For example, a date string may be parsed to a numeric value that only contains the day number.

### Table Result 2 page

This page displays the array result as a table where each value in the query result column is a separate row. It supports both string and numeric results. The primary key of this table is a combination of the column name and the value from the first column in the query result. If there are duplicate values in the first column of the query result, only the first row with this value will be displayed. It has the same method of parsing string values to numeric as Table Result.

### Configuration page

To configure the element using this connector, go to the **Configuration** page and select the appropriate **Database Type**. Then fill in the **Server Address**, **Database Name**, **User Name**, and **Password**.

Via the **Test Connection** page button, you can check if the connection has been established. Click the **Connect** button and then check the **Connection Result** field.

It is also possible to specify the **Port** for MySQL database type.

## How to Use (2.0.1.x range)

### General page

On this page, a **Query Overview** table is used to create and display queries. With the **Result Configuration** option, you can select how the query result will be parsed. The possible options are *String*, *Numeric*, and *Array*. Unlike the 2.0.0.x range, after a query result of type String or Numeric, the existing data in the tables Table Result and Table Result 2 will not be cleared.

### Table Result page

This page displays the array result as a table. It supports both string and numeric results. The primary key is a combination of the IDX of the query from the query overview table and the query result row number. It displays a maximum of 10 columns from the query result. If less than 10 columns are used, the value of the unused columns will be set to N/A. At the end of the table, there is a **Raw Result** column that contains a JSON representation of the complete row, including all original columns from the query result. For each column, it will try to parse string values as a number in an improved way compared to the 2.0.0.x range. If it is not possible, N/A will be displayed as the corresponding numeric value.

### Table Result 2 page

This page displays the array result as a table where each value in the query result column is a separate row. It supports both string and numeric results. The primary key is a combination of the IDX of the query from the query overview table, the query result row number, and the column name. For each row, it will try to parse string values as a number using the same method as Table Result. If this is not possible, N/A will be displayed.

### Configuration page

#### Database type

To configure the element using this connector, go to the **Configuration** page and select the appropriate **Database Type**. The different possibilities are *MySQL*, *MSSQL*, *ODBC*, and *Elasticsearch*.

For the **MySQL** database type, specify the **User Name**, **Password**, **Server Address**, and **Database Name**. You can also specify the **Port** and the **MySQL SSL Mode**. The latter can be used to select the SSL mode when connecting with MySQL. The different options are:

- *None*: Do not use SSL.
- *Preferred*: Use SSL if the server supports it. This is the default option.
- *Required*: Always use SSL. Deny the connection if the server does not support SSL. Does not validate CA or hostname.

For the **ODBC** database type, specify the **User Name**, **Password**, and **ODBC Data Source Name**.

For the **MSSQL** database type, specify the **User Name**, **Password**, **Server Address**, and **Database Name**.

For the **Elasticsearch** database type, specify the **Server Name**. Optionally, the **User Name** and **Password** can be filled in if authentication is required. When creating an Elasticsearch query, you need to define the **ES Endpoint URI** in the **Query Overview** table.

#### General configuration

Via the **Test Connection** page button, you can check if the connection has been established. Click the **Connect** button and then check the **Connection Result** field.

Enabling the **Override Table Results** parameter will limit the data in Table Result and Table Result 2 to only one array result for all queries. That means that each time a new array result is retrieved, the old data will be completely removed and only the new array result will be displayed. This is also the default behavior, continued from the 2.0.0.x range. Disabling this parameter will allow Table Result and Table Result 2 to store the array result for all queries at the same time. In this case, when there is a new array result for a query that has no data yet in the Table Result and Table Result 2 tables, the array result will be added to the tables. If there already is data in those tables for that query, the old data will be overridden with the new array result.

The parameters **Table Result Maximum Rows** and **Table Result 2 Maximum Rows** can be used to limit the number of rows that can be added to the tables.

## How to Use (2.1.0.x range)

This range builds on the 2.0.1.x range and adds automatic CSV export of array results, a per-query retry mechanism, and an export status indicator. All other pages behave as described for the 2.0.1.x range.

### CSV export of array results

On the **Configuration** page, you can enable automatic export of the full result of each successful query with **Result Configuration** set to *Array*. This is supported for the **MySQL**, **MSSQL**, and **ODBC** database types.

- **Query Results Export**: Enables or disables the CSV export.
- **Export Folder**: The folder where the CSV files are written. A default location is provided and can be changed.
- **Export Status**: Indicates whether an export is currently *Processing* or *Idle*.

Each export produces a UTF-8 CSV file named after the query and a timestamp. Results triggered through a manual execution are suffixed accordingly. Existing files are never overwritten; if a name already exists, an incrementing counter is appended.

### Per-query retry attempts

Each row in the **Query Overview** table has a **Retry Attempts** value (0-5, default 0). When a query fails with a non-permanent error, it is retried immediately, up to the configured number of attempts. Permanent errors (such as SQL syntax errors, unknown tables or columns, permission issues, or an invalid login) are not retried.

The retry cycle is aborted as soon as the elapsed time would exceed the query's **Execution Interval**, so a retry cycle can never outlive its own schedule. The failure result is written only after the retries are exhausted, so the Status alarm is raised only once.

## DataMiner Connectivity Framework (DCF)

This connector does not support the DataMiner Connectivity Framework (DCF).

## Notes

- Only queries with **Result Configuration** set to *Array* are exported to CSV, and only for the MySQL, MSSQL, and ODBC database types.
- Elasticsearch manages its own authentication and retry flow and is excluded from the per-query retry mechanism.