---
uid: Connector_help_Skyline_DataMiner_Labs_Monitoring_Technical
---

# Skyline DataMiner Labs Monitoring (Technical Reference)

## About

This connector ingests historical "New client registered" alarm events using SLNet history queries. It aggregates logins per user, client type, and date, and it keeps a rolling window based on a retention threshold.

## Workflow

The connector uses the following workflow:

1. A lookup start date is configured (*Start Lookup Datetime*).

1. The *Refresh* action (button or hourly timer) requests the alarm history for the "New client registered" event.

1. Each event is parsed to extract the username, device, and client.

1. A composite key (*User | Normalized Client | Date*) is used:

   - If the key exists: The Last Login timestamp and Times Accessed parameters are updated.
   - If the key does not exist yet: A new row is created.

1. A daily cleanup (24h timer) removes rows whose last login date exceeds the Days Threshold value.

## Main User Activity Overview Columns

| Column | Description |
| ------ | ----------- |
| Event Type | Always "New client registered" (current scope). |
| User Name | DataMiner user full name. |
| User Device | Device/host reported in the event. |
| User Client | Normalized client type (impersonation suffix removed). |
| User Category | Internal/Local/External. |
| Last Login Timestamp | Timestamp of most recent login that day (updates on repeated logins). |
| Times Accessed | Count of logins for that day and client combination. |

## Manual Controls

- **Refresh**: Retrieves new events since the last lookup.
- **Clear**: Removes all entries immediately.
- **Days Threshold**: Allows you to adjust how long data is kept. The threshold will be applied during the next cleanup.

## Data Acquisition

| Mechanism | Details |
| --------- | ------- |
| Source | Alarm history (GetAlarmDetailsFromDbMessage) |
| Filter | ParameterID = 64503 |
| Interval | Hourly timer (Slow Timer) or manual Refresh button |
| Range | From last processed OLE Automation date (lookupLastDatetime) to Now |
| Aggregation | Key = User Name + Normalized Client + Calendar Date |

## Normalization Logic

- Impersonation suffix: Any " - impersonated for ..." segment in the client string is removed.
- User categories:
  - *Internal*: Email ends with `@skyline.be`.
  - *Local*: No email address.
  - *External*: All others.

## Retention/Cleanup

- The Days Threshold parameter defines the maximum allowed age of each entry (i.e. the difference between the current date and the last login date).
- A daily timer invokes the cleanup (QAction 3), deleting rows older than the threshold.
- Rows with unparsable timestamps are considered invalid and removed.

## Table Behavior

- One row is added per day per user and client type.
- When multiple logins occur on the same day:
  - The timestamp is adjusted to the latest timestamp.
  - The "Times Accessed" parameter value increases.
- The display key combines Device, Category, and Event Type (per NamingFormat).

## QActions

| QAction | Role |
| ------- | ---- |
| 110 | Event retrieval, aggregation, persistence. |
| 3 | Cleanup logic (triggered manually or by timer). |

## Timers

| Timer | Interval | Purpose |
| ----- | -------- | ------- |
| Slow Timer (1h) | 3600000 ms | Periodic refresh (Group 110). |
| Very Slow Timer (24h) | 86400000 ms | Periodic cleanup (Group 3). |

## Known Limitations

- Only processes one event type ("New client registered").
- The daily aggregation loses intra-day chronological order beyond the last timestamp.

## Troubleshooting

| Symptom | Possible cause | Action |
| ------- | -------------- | ------ |
| No new rows | lookupStartDatetime not set or no events | Configure start or verify event generation. |
| Rows not removed | Days Threshold too high | Adjust the Days Threshold value. |
| Unexpected client strings | Normalization rule not matching | Review the impersonation suffix. |
| Counter does not increment | Events share different client strings | Confirm the normalization outcome. |
