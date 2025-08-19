---
uid: Connector_help_Skyline_DataMiner_Labs_Monitoring_Technical
---

# Skyline DataMiner Labs Monitoring (Technical Reference)

## Overview

This protocol ingests historical “New client registered” alarm events using SLNet history queries. It aggregates logins per (User, Client Type, Date) and persists a rolling window based on a retention threshold.

## Data Acquisition

| Mechanism | Details |
| --------- | ------- |
| Source | Alarm history (GetAlarmDetailsFromDbMessage) |
| Filter | ParameterID = 64503 |
| Interval | Hourly timer (Slow Timer) or manual Refresh button |
| Range | From last processed OLE Automation date (lookupLastDatetime) to Now |
| Aggregation | Key = User Name + Normalized Client + Calendar Date |

## Normalization Logic

- Impersonation suffix: Any “ - impersonated for …” segment in the client string is removed.
- User Category:
  - Internal: Email ends with @skyline.be
  - Local: No email address
  - External: All others

## Retention / Cleanup

- DaysThreshold defines maximum allowed age (difference between today and Last Login date).
- Daily timer invokes cleanup (QAction 3), deleting rows older than threshold.
- Rows with unparsable timestamps are considered invalid and removed.

## Table Behavior

- One row per day per (User, Client Type).
- Multiple logins in the same day update:
  - Timestamp (advances to latest)
  - Times Accessed (increment)
- Display key combines: Device;Category;Event Type (per NamingFormat).

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

- Only processes one event type (New client registered).
- Daily aggregation loses intra-day chronological order beyond last timestamp.

## Troubleshooting

| Symptom | Possible Cause | Action |
| ------- | -------------- | ------ |
| No new rows | lookupStartDatetime not set or no events | Configure start or verify event generation |
| Rows not removed | DaysThreshold too high | Adjust write parameter |
| Unexpected client strings | Normalization rule not matching | Review impersonation suffix |
| Counter does not increment | Events share different client strings | Confirm normalization outcome |
