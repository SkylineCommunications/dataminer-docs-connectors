---
uid: Connector_help_Skyline_Generic_OpenSearch_Query_Manager_Technical
description: Configure scheduled OpenSearch queries, authentication, result dispatching, and query testing in DataMiner.
---

# Skyline Generic OpenSearch Query Manager

## About

The **Skyline Generic OpenSearch Query Manager** is a virtual DataMiner connector. It executes OpenSearch queries through a configured endpoint and can forward successful query results to other DataMiner elements through InterApp messaging.

The connector version defined in the protocol is **1.0.0.1**. It requires DataMiner version **10.4.0.0 - 14003** or higher.

## Configuration

### Connections

This connector uses a virtual connection. No device address is required when you create the element.

#### Virtual Connection

| Setting | Value |
|---------|-------|
| **IP address/host** | Not required |
| **IP port** | Not required |
| **Bus address** | Not required |

### General Page

After you create the element, configure the following parameters on the **General** page:

| Parameter | Description |
|-----------|-------------|
| **Endpoint URL** | URL of the OpenSearch endpoint. |
| **Authentication Method** | Select **Basic Authentication** or **API Key**. |
| **Username** | Username used for Basic Authentication. |
| **Password** | Password used for Basic Authentication. The value is masked. |
| **API Key** | API key used for API Key authentication. The value is masked. |

The selected authentication method determines which credentials are validated before a query is sent. The endpoint and credentials are used by both scheduled queries and the **Query Tool**.

> [!WARNING]
> The connector configures the OpenSearch client to accept all server certificates. HTTPS connections therefore do not receive server-certificate chain validation from this connector.

## How to Use

### Queries Page

Use the **Add Row** button to add a query. Each row in the **Queries** table contains the following columns:

| Column | Description |
|--------|-------------|
| **Primary Key** | Internal row identifier. |
| **Name** | Human-friendly query name. This name is used when you configure a dispatch row. |
| **Query Index** | OpenSearch index or index pattern targeted by the request. |
| **Query JSON** | OpenSearch Query DSL request body. |
| **Polling Interval** | Time between scheduled executions, in seconds. The configured range is 10–604800 seconds. |
| **State** | **Enabled** or **Disabled**. Only enabled queries are evaluated by the scheduled execution. |
| **Timeout** | Per-query request timeout, in seconds. The configured range is 0–60 seconds. |
| **Number of Partitions** | Number of times the query is executed in a polling cycle. The minimum configured value is 1. |
| **Last Status Code** | HTTP status code from the last execution, when available. |
| **Last Result** | Response body from the last execution. |
| **Last Error** | Error or debug information from the last execution. |
| **Execution State** | **Failure** or **Success** for the last execution. |
| **Last Execution Time** | Timestamp of the last execution attempt. |
| **Duration** | Time taken by the last execution. |
| **Actions** | **Execute** the selected query immediately or **Delete** the row. |
| **Current Partition** | Zero-based partition value used for the most recent partition execution. |

The **Query JSON** value supports the following replacements at execution time:

| Variable | Replacement |
|----------|-------------|
| `{{gte}}` | Current UTC time minus 15 minutes, formatted as `yyyy-MM-ddTHH:mm:ss.fffZ`. |
| `{{lte}}` | Current UTC time, formatted as `yyyy-MM-ddTHH:mm:ss.fffZ`. |
| `{{num_partitions}}` | The query's **Number of Partitions** value. |
| `{{current_partition}}` | The zero-based partition currently being executed. |

For scheduled execution, the connector evaluates enabled queries on the protocol's **Fast Timer (30s)**. A query is executed when its polling interval has elapsed since the last execution. A query with a non-positive interval is also treated as due by the execution logic, although the protocol-configured range starts at 10 seconds.

When **Number of Partitions** is greater than 1, the connector executes the query once for each partition, updating `{{current_partition}}` for each request. The result from the final partition is written to the table and is the result considered for dispatch.

The **Execute** action on a query row runs the query immediately. A successful manual execution is dispatched through enabled matching rows on the **Dispatch** page.

### Destinations Page

Use the **Add Row** button to add a destination element. Each row in the **Destinations** table contains:

| Column | Description |
|--------|-------------|
| **Primary Key** | Internal row identifier. |
| **Name** | Destination name used by the **Dispatch** table. |
| **Element ID** | Destination address in `DMA ID/Element ID` format, for example `123/456`. |
| **Last Dispatch** | Timestamp recorded for the most recent dispatch processing attempt for this destination. |
| **Last Error** | Error details from the last failed dispatch attempt. |
| **Delete** | Deletes the selected destination row. |

### Dispatch Page

Use the **Add Row** button to add a query-to-destination mapping. Each row in the **Dispatch** table contains:

| Column | Description |
|--------|-------------|
| **Primary Key** | Internal row identifier. |
| **Query** | Query name selected from the configured query names. |
| **Information** | Additional information attached to the InterApp message. |
| **Destinations** | Destination name selected from the configured destination names. |
| **State** | **Enabled** or **Disabled**. Only enabled mappings are processed. |
| **Last Dispatch** | Timestamp of the last dispatch attempt for this mapping. |
| **Last State** | **Failure** or **Success** for the last dispatch attempt. |
| **Last Error** | Error details from the last failed dispatch attempt. |
| **Delete** | Deletes the selected dispatch row. |

After a query succeeds, every enabled dispatch row for the query name is processed. The destination element address must contain a DMA ID and element ID separated by `/`.

### Query Tool Page

The **Query Tool** page provides an on-demand query interface. Enter an **OpenSearch Index** and **OpenSearch Query JSON**, and then click **Execute**.

| Parameter | Description |
|-----------|-------------|
| **OpenSearch Index** | OpenSearch index or index pattern for the request. |
| **OpenSearch Query JSON** | OpenSearch Query DSL request body. The same query-variable replacements are available as for table queries. |
| **Execute** | Sends the request immediately. |
| **Status Code** | HTTP status code from the latest request, when available. |
| **Response Body** | Raw response body from the latest request. |
| **Error** | Error details from the latest failed request. |
| **Clear Response** | Clears the status code, response body, and error fields. |

The Query Tool uses the credentials configured on the **General** page. It does not create a query-table row and does not dispatch its result.

## InterApp Messaging

Successful scheduled and manually executed table queries can be forwarded to enabled dispatch destinations using the `QueryResultMessage` InterApp message. The message is sent to parameter **9000000** of the destination element and contains:

| Field | Description |
|-------|-------------|
| `EndpointUrl` | Endpoint URL configured on the **General** page. |
| `QueryIndex` | Index or index pattern of the query. |
| `ResponseBody` | Response body returned by OpenSearch. |
| `DispatchInfo` | The **Information** value from the dispatch row. |
| `CommandType` | Set to `QUERY`. |
| `ErrorMessage` | Error information associated with the query result. |

If a dispatch cannot be completed, the connector writes the failure state and error to the dispatch row and, when applicable, to the destination row.

## Notes

- The **Timeout** value `0` leaves the request timeout unset for that query; positive values configure a request timeout in seconds.
- Query and destination names are used as the links between the **Queries**, **Destinations**, and **Dispatch** tables. Keep them unique and consistent when configuring mappings.
