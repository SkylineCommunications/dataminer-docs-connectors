---
uid: Connector_help_Linux_Platform_Memory_Calculation
---

# Memory Calculation

Below, you can find how the Linux Platform connector calculates memory-related parameters. The connector supports two connection types (SSH and SNMP), each with its own method for retrieving and computing memory metrics such as real memory, swap memory, and physical memory usage.

The sections below detail the parameters retrieved from the system, the formulas used for calculated values, and the mapping between raw system data and connector parameters.

> [!IMPORTANT]
> The below calculations are available starting from version 2.0.2.8.

| Parameter Name                   | PID | Display              | SSH Command    | SNMP OID                     | Comments                        |
| -------------------------------- | --- | -------------------- | -------------- | -----------------------------| ------------------------------- |
| Total Memory                     | 172 | General, Memory Info | N/A            | N/A                          | Value calculated                |
| Total RAM Memory                 | 114 | Memory Info          | `MemTotal`     | OID: 1.3.6.1.4.1.2021.4.5.0  | N/A                             |
| Total Swap Memory                | 118 | Memory Info          | `SwapTotal`    | OID: 1.3.6.1.4.1.2021.4.3.0  | N/A                             |
| Available Memory                 | 112 | General, Memory Info | `MemAvailable` | OID: 1.3.6.1.4.1.2021.4.6.0  | N/A                             |
| Available Swap Memory            | 119 | Memory Info          | `SwapFree`     | OID: 1.3.6.1.4.1.2021.4.4.0  | N/A                             |
| Memory Buffer                    | 121 | Memory Info          | `Buffers`      | OID: 1.3.6.1.4.1.2021.4.14.0 | N/A                             |
| Memory Cached                    | 122 | Memory Info          | N/A            | OID: 1.3.6.1.4.1.2021.4.3.0  | Value calculated (only for SSH) |
| Memory Usage                     | 111 | General, Memory Info | N/A            | N/A                          | Value calculated                |
| Swap Memory Usage                | 110 | General, Memory Info | N/A            | N/A                          | Value calculated                |
| Memory Used                      | 113 | General, Memory Info | N/A            | N/A                          | Value calculated                |

## Total Memory

Total memory on this host (both real and swap memory). Since the value is returned in KB, it is divided by 1024 to convert it to MB.

- **SNMP**

$$
\text{Total Memory}=\frac{\text{Total Swap Memory}+\text{Total RAM Memory}}{1024}
$$

- **SSH**

$$
\begin{equation}
\begin{split}
\text{Total Memory}&=\frac{\text{Total RAM Memory}+\text{Total Swap Memory}}{1024}\\[10pt]
&=\frac{\text{MemTotal}+\text{SwapTotal}}{1024}
\end{split}
\end{equation}
$$

### Memory Usage

The percentage of total memory currently in use. This metric indicates how much of the combined RAM and swap memory is being utilized by the system.

- **SNMP**

$$
\text{Memory Usage}=\left(1-\left(\frac{\text{Available Memory}}{\text{Total Memory}}\right)\right)\times{100}
$$

- **SSH**

$$
\begin{equation}
\begin{split}
\text{Memory Usage}&=\left(1-\frac{\text{Available Memory}}{\text{Total Memory}}\right)\times 100\\[10pt]
&=\left(1-\frac{\text{MemAvailable}}{\text{MemTotal}}\right)\times{100}
\end{split}
\end{equation}
$$

## Swap Memory Usage

The percentage of swap space currently in use. Swap memory is disk space used as virtual memory when physical RAM is full. High swap usage may indicate memory pressure on the system.

- **SNMP**

$$
\text{Swap Memory Usage}=\left(1-\left(\frac{\text{Available Swap Memory}}{\text{Total Swap Memory}}\right)\right)\times{100}
$$

- **SSH**

$$
\begin{equation}
\begin{split}
\text{Swap Memory Usage}&=\left(1-\frac{\text{Available Swap Memory}}{\text{Total Swap Memory}}\right)\times{100}\\[10pt]
&=\left(1-\frac{\text{SwapFree}}{\text{SwapTotal}}\right)\times{100}
\end{split}
\end{equation}
$$

## Memory Used

The absolute amount of memory currently in use, expressed in MB. This represents the difference between total available memory and free memory.

- **SNMP**

$$
\text{Memory Used}=\frac{\text{Total Memory}-\text{Available Memory}}{1024}
$$

- **SSH**

$$
\begin{equation}
\begin{split}
\text{Memory Used}&=\frac{\lvert\text{Total Memory}-\text{Available Memory}\rvert}{1024}\\[10pt]
&=\frac{\lvert(\text{MemTotal})-(\text{MemAvailable})\rvert}{1024}
\end{split}
\end{equation}
$$

## Memory Cached

The amount of memory used for caching file data to improve system performance, expressed in MB. This includes page cache (`Cached`) and reclaimable slab memory (`SReclaimable`). Cached memory can be freed by the system when applications need more memory.

- **SSH Only**

$$
\begin{equation}
\begin{split}
\text{Memory Cached}&=\frac{\text{Cached}+\text{SReclaimable}}{1024}\\[10pt]
\end{split}
\end{equation}
$$

## Additional Changes

- The following parameters were renamed to better reflect their purpose:
  - Total Physical Memory (PID: 172) is now Total Memory.
  - Available Physical Memory (PID: 112) is now Available Memory.
  - Used Physical Memory (PID: 113) is now Memory Used.

- The following parameters were removed as they are no longer necessary due to the updated calculations:
  - Actual Available Physical Memory (PID: 173)
  - Actual Used Physical Memory (PID: 123)
  - Actual Physical Memory Usage (PID: 174)
  - Physical Memory Usage (PID: 124)

- For SNMP, the available memory was retrieved initially using the  OID: 1.3.6.1.4.1.2021.4.11.0 (`MemTotalFree`), which has now been replaced with OID: 1.3.6.1.4.1.2021.4.6.0 to align with the SSH command `MemAvailable`.
