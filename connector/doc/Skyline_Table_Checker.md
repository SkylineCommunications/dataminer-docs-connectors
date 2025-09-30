---
uid: Connector_help_Skyline_Table_Checker
---

# Skyline Table Checker

## About

With this connector, you can search through all the elements in your DataMiner System that use a specific connector and look for specific entries in a table of your choice.

### Key Features

- **Automated table checks**: Periodically scans tables based on a configurable update interval (default: 30 minutes).
- **Detailed check results**: Provides a comprehensive table with information about the checked elements, including the connector name, table and column IDs, match status, and instance counts.
- **Regex-based filtering**: Supports an optional element name regex filter to refine element searches for more precise results.

## Use Cases

### Proactive System Monitoring

**Challenge:** Ensuring that critical table entries (e.g. device status, service configurations) exist and remain updated.

**Solution:** The connector automatically checks specified tables at a set interval, verifying if key entries are present and up to date.

**Benefit:** Provides real-time visibility into the system’s health.

### Troubleshooting & Diagnostics

**Challenge:** Finding the root cause of missing or incorrect entries often requires manual effort.

**Solution:** The tool quickly scans tables to identify missing values, incorrect mappings, or unexpected data changes.

**Benefit:** Speeds up troubleshooting by instantly detecting configuration issues.

## Prerequisites

- **DataMiner version 10.3 or higher** is required.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Table_Checker_Technical).
