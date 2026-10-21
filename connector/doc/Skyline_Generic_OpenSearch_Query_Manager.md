---
uid: Connector_help_Skyline_Generic_OpenSearch_Query_Manager
---
# Skyline Generic OpenSearch Query Manager

## About

The **Skyline Generic OpenSearch Query Manager** connects OpenSearch data to DataMiner workflows. From one virtual DataMiner element, teams can define and schedule JSON-based OpenSearch queries, inspect their results, and route successful results to configured DataMiner destination elements. Queries and routing are managed through element tables, so they can be adapted without creating a custom connector for each query.

This connector is intended for DataMiner teams that need to retrieve selected data from OpenSearch and make the raw query results available to other DataMiner elements. It executes the queries; destination elements remain responsible for interpreting or processing the returned data.

## Key Features

- **Manage multiple scheduled queries:** Configure each query's index, JSON query body, polling interval, enabled state, timeout, and partition count in the Queries table. Review its latest status, response, execution time, duration, and error.
- **Authenticate to OpenSearch:** Configure an endpoint and choose Basic authentication or API key authentication.
- **Route results to DataMiner elements:** Map queries to one or more destinations in the Dispatch table. After a successful query, the connector sends the raw response to the configured destination elements using DataMiner InterApp messaging.
- **Adapt queries at runtime:** Use time-bound and partition template variables in scheduled query bodies, and configure multiple partitions for sequential execution.
- **Test and transfer query definitions:** Run an on-demand query from the Query Tool page and import or export query definitions.
- **Operate without a device connection:** The connector is virtual; OpenSearch endpoint and authentication settings are configured on the element.

## Use Cases

### Retrieve OpenSearch data on a schedule

**Challenge:** DataMiner workflows need selected logs, events, or other indexed data from OpenSearch, but maintaining a separate custom integration for each query is cumbersome.

**Solution:** Define the index, JSON query, and polling interval for each query in the connector's Queries table. Enable or disable individual queries and monitor their latest execution status and response.

**Benefit:** Teams can manage recurring OpenSearch data retrieval in a single DataMiner element and adjust query definitions through configuration rather than custom connector code.

### Deliver query results to existing DataMiner workflows

**Challenge:** OpenSearch query results need to reach the DataMiner elements that use them, without coupling query execution to each consumer's processing logic.

**Solution:** Add destination elements and map each query to one or more destinations in the Destinations and Dispatch tables. The connector forwards a successful query's raw response through InterApp messaging.

**Benefit:** Query execution and result processing stay decoupled, allowing multiple DataMiner consumers to receive results from a centrally managed query.

### Iterate on queries and handle large result sets

**Challenge:** Query authors need to validate JSON query bodies against the configured OpenSearch endpoint and tailor scheduled queries for time windows or large indices.

**Solution:** Test a query interactively with the Query Tool. For scheduled queries, use the supported time-bound template variables and configure sequential partitions where appropriate.

**Benefit:** Operators can validate queries before scheduling them and adapt query execution to their data retrieval needs using element configuration.

## Technical Reference

For configuration details and usage guidance, see the [technical documentation](xref:Connector_help_Skyline_Generic_OpenSearch_Query_Manager_Technical).
