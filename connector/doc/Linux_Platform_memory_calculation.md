---
uid: Connector_help_Linux_Platform_Memory_Calculation
---

# Memory Calculation

The Linux Platform connector retrieves memory information through SSH or SNMP and calculates RAM, swap, and combined RAM and swap metrics.

> [!NOTE]
> The calculations on this page apply from connector version 2.1.0.4 onward. Earlier versions can use different calculations.

| Parameter Name | PID | Display | SSH (`/proc/meminfo`) | SNMP: hrStorageTable (preferred) | SNMP: UCD-SNMP-MIB (fallback) | Comments |
|---|---|---|---|---|---|---|
| Total Memory | 172 | General, Memory Info | N/A | N/A | N/A | Value calculated: Total RAM Memory + Total Swap Memory |
| Total RAM Memory | 114 | Memory Info | `MemTotal` | `Physical memory` row, `hrStorageSize` (OID: 1.3.6.1.2.1.25.2.3.1.5) | `memTotalReal` (OID: 1.3.6.1.4.1.2021.4.5.0) | N/A |
| Total Swap Memory | 118 | Memory Info | `SwapTotal` | `Swap space` row, `hrStorageSize` (OID: 1.3.6.1.2.1.25.2.3.1.5) | `memTotalSwap` (OID: 1.3.6.1.4.1.2021.4.3.0) | N/A |
| Available Memory | 112 | General, Memory Info | N/A | N/A | N/A | Value calculated: Available RAM + Available Swap Memory |
| Available RAM | 177 | Memory Info | `MemAvailable` | `Available memory` row, `hrStorageSize` (OID: 1.3.6.1.2.1.25.2.3.1.5) | `memSysAvail` (OID: 1.3.6.1.4.1.2021.4.27.0) | Estimated when `MemAvailable` or `memSysAvail` is unavailable (see [Available RAM](#available-ram)) |
| Available Swap Memory | 119 | Memory Info | `SwapFree` | N/A | `memAvailSwap` (OID: 1.3.6.1.4.1.2021.4.4.0) | hrStorageTable: value calculated as Total Swap Memory - Used Swap |
| Memory Buffer | 121 | Memory Info | `Buffers` | `Memory buffers` row, `hrStorageUsed` (OID: 1.3.6.1.2.1.25.2.3.1.6) | `memBuffer` (OID: 1.3.6.1.4.1.2021.4.14.0) | N/A |
| Memory Cached | 122 | Memory Info | `Cached` + `SReclaimable` | `Cached memory` row, `hrStorageUsed` (OID: 1.3.6.1.2.1.25.2.3.1.6) | `memCached` (OID: 1.3.6.1.4.1.2021.4.15.0) | SSH value includes reclaimable slab memory |
| Memory Usage | 111 | General, Memory Info | N/A | N/A | N/A | Value calculated; includes RAM and swap |
| Memory RAM Usage | 124 | Memory Info | N/A | N/A | N/A | Value calculated; RAM only |
| Swap Memory Usage | 110 | General, Memory Info | N/A | N/A | N/A | Value calculated |
| Memory Used | 113 | General, Memory Info | N/A | N/A | N/A | Value calculated: Used RAM + Used Swap |
| Used RAM | 178 | Memory Info | N/A | N/A | N/A | Value calculated: Total RAM Memory - Available RAM |
| Used Swap | 179 | Memory Info | N/A | `Swap space` row, `hrStorageUsed` (OID: 1.3.6.1.2.1.25.2.3.1.6) | N/A | SSH and UCD-SNMP-MIB: value calculated as Total Swap Memory - Available Swap Memory |

- Memory amounts are displayed in MB, using binary conversion: 1 MB = 1024 kB, and 1 kB = 1024 bytes.
- Through SNMP, the connector uses `hrStorageTable` only if it contains all five required rows: `Physical memory`, `Memory buffers`, `Cached memory`, `Available memory`, and `Swap space`. Otherwise, it uses the UCD-SNMP-MIB objects.
- The hrStorageTable OIDs are column OIDs. Rows are identified by their `hrStorageDescr` value (OID: 1.3.6.1.2.1.25.2.3.1.3). Row indexes depend on the SNMP agent. To query a single value, append the row index to the column OID, e.g., `1.3.6.1.2.1.25.2.3.1.5.<row index>`.

> [!IMPORTANT]
> **Memory Usage** (PID 111), **Memory Used** (PID 113), **Available Memory** (PID 112), and **Total Memory** (PID 172) include both RAM and swap. For RAM only, use **Memory RAM Usage** (PID 124), **Used RAM** (PID 178), **Available RAM** (PID 177), and **Total RAM Memory** (PID 114).

## RAM

```text
Used RAM = Total RAM Memory - Available RAM

Memory RAM Usage = Used RAM / Total RAM Memory * 100
```

**Memory Buffer** and **Memory Cached** are not subtracted again when calculating **Used RAM**. They only contribute to the **Available RAM** estimates described below.

## Swap

Through SSH and UCD-SNMP-MIB, the connector retrieves the available swap memory and calculates the used swap memory:

```text
Used Swap = Total Swap Memory - Available Swap Memory
```

Through hrStorageTable, the connector retrieves the used swap memory and calculates the available swap memory:

```text
Available Swap Memory = Total Swap Memory - Used Swap
```

For all sources, the usage is calculated as follows:

```text
Swap Memory Usage = Used Swap / Total Swap Memory * 100
```

## Total (RAM + Swap)

```text
Total Memory = Total RAM Memory + Total Swap Memory

Available Memory = Available RAM + Available Swap Memory

Memory Used = Used RAM + Used Swap

Memory Usage = Memory Used / Total Memory * 100
```

Because **Memory Usage** includes swap in both its used amount and its total, unused swap can make this percentage considerably lower than **Memory RAM Usage**.

## Available RAM

The source of **Available RAM** depends on the connection type:

- **SSH**: `MemAvailable`, if present and greater than 0. Otherwise, the connector estimates it:

  ```text
  Available RAM = MemFree + Buffers + Cached + SReclaimable - Shmem
  ```

- **SNMP, hrStorageTable**: the `hrStorageSize` value of the `Available memory` row, as reported by the SNMP agent.

- **SNMP, UCD-SNMP-MIB**: `memSysAvail`, if greater than 0. Otherwise, the connector estimates it:

  ```text
  Available RAM = memAvailReal + memBuffer + memCached - memShared
  ```

  This estimate uses `memAvailReal` (OID: 1.3.6.1.4.1.2021.4.6.0) and `memShared` (OID: 1.3.6.1.4.1.2021.4.13.0). `memAvailReal` is free RAM, comparable to `MemFree`, not to `MemAvailable`.

Both fallback formulas are estimates and can differ from the kernel's `MemAvailable` value.

## hrStorageTable Values

`hrStorageSize` and `hrStorageUsed` are counts of allocation units, not kB. The connector converts each value using `hrStorageAllocationUnits` (OID: 1.3.6.1.2.1.25.2.3.1.4) of the same row:

```text
Amount (kB) = count * hrStorageAllocationUnits / 1024
```

The result is rounded down to whole kB and then converted to MB.

**Used RAM** is always calculated from **Total RAM Memory** and **Available RAM**. The `hrStorageUsed` value of the `Physical memory` row is not used.

## Percentages and Special Cases

- Percentages are calculated from the source values before they are rounded for display. Recalculating a percentage from the displayed MB values can therefore give a slightly different result.
- If the corresponding total is 0, the usage is 0%. For example, a host without swap reports 0% for **Swap Memory Usage**.
- Negative memory amounts are displayed as 0 MB.

## Comparing SSH and SNMP Values

Values retrieved through SSH, through SNMP, or with tools on the host do not necessarily match:

- Memory use changes continuously, so samples taken at different times can differ.
- The SNMP agent determines how its values are calculated. The `Available memory` row is not guaranteed to match `MemAvailable` in `/proc/meminfo`.
- The fallback formulas for **Available RAM** are estimates.
- **Memory Cached** includes `SReclaimable` through SSH, but contains the cached value reported by the agent through SNMP.
- Tools such as `free`, `top`, and `htop` can define used memory differently and use different units.

For a meaningful comparison, use samples taken at the same time, compare RAM-only values with RAM-only values, and use the same units.
