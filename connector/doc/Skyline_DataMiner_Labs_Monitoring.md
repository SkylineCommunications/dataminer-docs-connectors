---
uid: Connector_help_Skyline_DataMiner_Labs_Monitoring
---

# Skyline DataMiner Labs Monitoring

## About

The Skyline DataMiner Labs Monitoring connector provides a consolidated user activity overview inside DataMiner. It collects DataMiner user login events ("New client registered") and aggregates them per user, client type, and day. This enables quick insight into which users (and client types) are actively accessing the system and how often.

## Key Features

- Daily aggregation of user login activity (one row per user, client type, and day).
- Incremental event retrieval based on configurable lookup start and last processed timestamps.
- Classification of users (internal, local, or external).
- Login count per day with persistent history.
- Configurable retention with automatic cleanup based on a maximum number of days.
- Manual controls to refresh the lookup or clear all rows.
- Automated periodic refresh (hourly) and cleanup (daily).

## Use Cases

- **Auditing user access patterns**: Track how frequently different client interfaces are used per user each day.
- **Security and hygiene**: Automatically purge stale user activity older than a configurable number of days.
- **Operational dashboards**: View the data in dashboards as a compact daily activity metric.

## Technical Reference

### Prerequisites

- DataMiner 10.3.0 or higher.

> [!NOTE]
> For more technical details, refer to the [technical documentation](xref:Connector_help_Skyline_DataMiner_Labs_Monitoring_Technical).
