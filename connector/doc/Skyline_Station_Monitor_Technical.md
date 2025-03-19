---
uid: Connector_help_Skyline_Station_Monitor_Technical
---

# Skyline Station Monitor

The Skyline Station Monitor connection is designed to facilitate real-time data collection, parameter tracking, and automated actions for generic Apps for quick deployment of new stations.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### Standard Monitoring

Standard monitoring is consistent across all stations. It must be routed to the predefined parameters that hold information for each KPI, meaning that rows cannot be added or removed. The collected data is then displayed on the Standard Monitoring page.

### Custom Monitoring

Custom monitoring allows for flexible mapping, enabling users to define their own parameters to retrieve. Unlike with standard monitoring, users can add or remove rows as needed to accommodate specific monitoring requirements that are not predefined within the standard framework.

### Data Polling Process

1. The system reads the **Element ID** to identify the device and component.
1. It retrieves the specified **Parameter ID** value at the configured polling frequency.
1. If a **Row Key** is provided, it accesses the corresponding row in a table.
1. The collected values are stored, including timestamps, alarm states, and results.
1. Errors are logged if polling fails.

### Element ID Format

Each monitored element is identified using a **DMAID/ElementID** format:

- **DMAID**: A unique identifier for the monitored device or system.
- **ElementID**: The specific component within that system being monitored.

For example:

```
123/456
```

### Parameter ID

The **Parameter ID** is a numerical identifier representing the specific attribute being monitored within an element. It defines what data will be polled from the specified **Element ID**.

- Each parameter ID corresponds to a predefined metric (e.g. CPU usage, voltage, temperature).
- The polling frequency determines how often the parameter value is retrieved.

For example:

```
Element ID: 123/456
Parameter ID: 789
```

In the example above, **parameter 789** is being polled from **Element 123/456**.

### Using a Row Key for Table-Based Parameters

If a **Row Key** is specified, the system assumes the parameter belongs to a table structure within the element. In this case:

- The **Row Key** determines the specific entry within the table (the primary key).
- The **Parameter ID** defines the column ID to be retrieved from that row.

For example:

```
Element ID: 123/456
Parameter ID: 789
Row Key: analog1
```

The setup from the example above retrieves the **789** parameter from the **analog1** row within **Element 123/456**.
