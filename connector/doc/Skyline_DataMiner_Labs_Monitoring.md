---
uid: Connector_help_Skyline_DataMiner_Labs_Monitoring
---

# Skyline DataMiner Labs Monitoring

## About

The Skyline DataMiner Labs Monitoring connector provides a consolidated User Activity Overview inside DataMiner. It collects DataMiner user login events (New client registered) and aggregates them per user, client type, and day. This enables quick insight into which users (and client types) are actively accessing the system and how often.

## Key Features

- Daily aggregation of user login activity (one row per User + Client Type + Day).
- Incremental event retrieval based on configurable lookup start and last processed timestamps.
- Classification of users (Internal, Local, External).
- Login count per day (Times Accessed) with persisted history.
- Configurable retention via Days Threshold with automatic cleanup.
- Manual controls: Refresh lookup, Clear all rows.
- Automated periodic refresh (hourly) and cleanup (daily).

## Use Cases

### Use Case 1: Auditing User Access Patterns
Track how frequently different client interfaces are used per user each day.

### Use Case 2: Security & Hygiene
Automatically purge stale user activity older than a configurable number of days.

### Use Case 3: Operational Dashboards
Expose the aggregated table to dashboards as a compact daily activity metric.

## How It Works

1. A lookup start date is configured (Start Lookup Datetime).  
2. The Refresh action (button or hourly timer) requests alarm history for the “New client registered” event.  
3. Each event is parsed to extract User Name, Device, Client.  
4. A composite key (User | Normalized Client | Date) is used:
   - If the key exists: update Last Login timestamp and increment Times Accessed.
   - If not: create a new row.
5. A daily cleanup (24h timer) removes rows whose last login date exceeds the Days Threshold.

## Main User Activity Overview Columns

| Column | Description |
| ------ | ----------- |
| Event Type | Always “New client registered” (current scope). |
| User Name | DataMiner user full name. |
| User Device | Device/host reported in the event. |
| User Client | Normalized client type (impersonation suffix removed). |
| User Category | Internal / Local / External. |
| Last Login Timestamp | Timestamp of most recent login that day (updates on repeated logins). |
| Times Accessed | Count of logins for that day & client combination. |

## Manual Controls

- Refresh: Fetch new events since last lookup.
- Clear: Remove all entries immediately.
- Days Threshold: Adjust retention (applies at next cleanup).

## Prerequisites

- DataMiner 10.3.0.0 - 12752 or higher.

> [!NOTE]
> For deeper technical details see the [technical documentation](xref:Connector_help_Skyline_DataMiner_Labs_Monitoring_Technical).
