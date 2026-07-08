---
uid: Connector_help_ADLINK_NuDAM-6053_Technical
---

# ADLINK NuDAM-6053 - Technical

## About

This connector reads all 16 digital input channels of the NuDAM-6053 every 10 seconds over a serial connection, then compares the result against each row in the configurable Digital Inputs table to determine whether an alarm condition is active.

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

**SERIAL CONNECTION:**

- **IP address/host**: The IP address or hostname of the NuDAM module.
- **IP port**: The TCP port of the serial device server.
- **Bus address**: The Bus address of the NuDAM-6053 module.

### Initialization

> [!IMPORTANT]
> The connector does **not** poll the device until at least one row is added to the **Digital Inputs** table.

## How it works

### Serial command and response

Every 10 seconds the connector sends a digital input read command and parses the response:

- **Command:** `$[BusAddr]6\r` — e.g. `$016\r` for bus address `01`
- **Valid response:** `![4 hex chars]00\r` — e.g. `!FFFC00\r`
- **Invalid response:** starts with `?`; all Parameter Values are set to **Unknown**

### Decoding the response

The 4 hex characters are converted to a 16-bit binary string. Each bit maps to one input channel, from Input 15 (leftmost bit) to Input 0 (rightmost bit). A `1` means **On**; a `0` means **Off**.

**Example:** `FFFC` → `1111111111111100` → Inputs 15–2 are On, Inputs 1–0 are Off.

### Matching against the Digital Inputs table

Each row in the table is evaluated independently against the decoded binary string:

- All input columns set to **Ignore** are skipped.
- If **all** non-Ignore bits match → **Parameter Value = Alarm**.
- If **any** non-Ignore bit does not match → **Parameter Value = Unknown**.

## How to use

### Digital Inputs table

Located on the **General** page. Each row defines one alarm condition.

| Column | Description |
|---|---|
| **Parameter Name** | User-defined label for this alarm condition. |
| **Input 15 – Input 0** | Expected state per channel: **On** (1), **Off** (0), or **Ignore** (-1). |
| **Parameter Value** | Read-only. **Alarm** when the pattern matches; **Unknown** otherwise. |

New rows default all input columns to **Ignore**. Set only the channels relevant to the alarm condition; leave the rest as **Ignore**.

### Adding and configuring a row

1. Right-click the Digital Inputs table and select **Add row**.
2. Enter a **Parameter Name** and click **OK**.
3. In the new row, set each relevant Input column to **On** or **Off** to define the alarm pattern.

To delete a row, right-click it and select **Delete selected item(s)**. If all rows are deleted, polling stops.

### Configuration example

**Scenario**: A DEV 2185 amplifier signals faults via digital inputs 7 and 8. Input 7 goes On for a primary power supply failure; Input 8 goes On for an amplifier fault.

| Parameter Name | Input 15–9 | Input 8 | Input 7 | Input 6–0 |
|---|---|---|---|---|
| Primary Power Supply Alarm | Ignore | Off | On | Ignore |
| Amplifier Fault | Ignore | On | Off | Ignore |
| Combined Fault | Ignore | On | On | Ignore |

After the first successful poll, the **Parameter Value** column updates automatically. Configure DataMiner alarm thresholds on **Parameter Value** to generate an alarm when a condition is active.
