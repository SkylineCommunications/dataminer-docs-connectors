---
uid: Connector_help_Skyline_Station_Monitor_Technical
---

# Skyline Station Monitor

This connector retrieves the state and performs minor control functions of Control By Web modules attached to the X-600M.
## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### **Data Polling Process**
1. The system reads the **Element ID** to identify the device and component.
2. It retrieves the specified **Parameter ID** value at the configured polling frequency.
3. If a **Row Key** is provided, it accesses the corresponding row in a table.
4. The collected values are stored, including timestamps, alarm states, and results.
5. Errors are logged if polling fails.

### **Element ID Format**
Each monitored element is identified using a **DMAID/ElementID** format:
- **DMAID**: A unique identifier for the monitored device or system.
- **ElementID**: The specific component within that system being monitored.

#### **Example Format**
```
123/456
```

### **Parameter ID**
The **Parameter ID** is a numerical identifier representing the specific attribute being monitored within an element. It defines what data will be polled from the specified **Element ID**.

- Each parameter ID corresponds to a predefined metric (e.g., CPU usage, voltage, temperature).
- The polling frequency determines how often the parameter value is retrieved.

#### **Example**
```
Element ID: 123/456
Parameter ID: 789
```
In this example, **parameter 789** is being polled from **Element 123/456**.

### **Using Row Key for Table-Based Parameters**
If a **Row Key** is specified, the system assumes the parameter belongs to a table structure within the element. In this case:
- The **Row Key** determines the specific entry within the table (the primary key).
- The **Parameter ID** defines the column ID to be retrieved from that row.

#### **Example Format**
```
Element ID: 123/456
Parameter ID: 789
Row Key: analog1
```
This setup retrieves the **789** parameter from the **analog1** row within **Element 123/456**.
