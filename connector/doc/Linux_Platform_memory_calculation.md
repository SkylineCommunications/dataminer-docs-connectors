---
uid: Connector_help_Linux_Platform_Memory_Calculation
---

# Memory Calculation

Below, you can find how the Linux Platform connector calculates memory-related parameters. The connector supports two connection types (SSH and SNMP), each with its own method for retrieving and computing memory metrics such as real memory, swap memory, and physical memory usage.

The sections below detail the parameters retrieved from the system, the formulas used for calculated values, and the mapping between raw system data and connector parameters.

## SSH Connection

| Parameter Name                   | PID | Type       | Display              | Comments    |
| -------------------------------- | --- | ---------- | -------------------- | ----------- |
| Available Real Memory            | 120 | SSH        | Memory Info          | `MemFree`   |
| Total Real Memory                | 114 | SSH        | Memory Info          | `MemTotal`  |
| Total Swap Memory                | 118 | SSH        | Memory Info          | `SwapTotal` |
| Available Swap Memory            | 119 | SSH        | Memory Info          | `SwapFree`  |
| Memory Buffer                    | 121 | SSH        | Memory Info          | `Buffers`   |
| Real Memory Usage                | 111 | Calculated | General, Memory Info | N/A         |
| Swap Memory Usage                | 110 | Calculated | General, Memory Info | N/A         |
| Total Physical Memory            | 172 | Calculated | General, Memory Info | N/A         |
| Available Physical Memory        | 112 | Calculated | General, Memory Info | N/A         |
| Used Physical Memory             | 113 | Calculated | Memory Info          | N/A         |
| Physical Memory Usage            | 124 | Calculated | Memory Info          | N/A         |
| Memory Cached                    | 122 | Calculated | Memory Info          | N/A         |
| Actual Available Physical Memory | 173 | Calculated | Memory Info          | N/A         |
| Actual Used Physical Memory      | 123 | Calculated | Memory Info          | N/A         |
| Actual Physical Memory Usage     | 174 | Calculated | Memory Info          | N/A         |

## QAction Mapping

| Parameter Name        | PID | Type | Comment                                                                 |
|-----------------------|-----|------|-------------------------------------------------------------------------|
| Total Real Memory     | 114 | SSH  | `MemTotal`.                                                             |
| Available Real Memory | 120 | SSH  | `MemFree`.                                                              |
| UsedMemoryBuffers     | N/A | SSH  | `Buffers`. Used in `Actual Available Physical Memory`.                  |
| UsedMemoryCache       | N/A | SSH  | `Cached`. Used in `Actual Memory Cache`.                                |
| SReclaimableMemory    | N/A | SSH  | `SReclaimable`. Used in `Actual Memory Cache`.                          |
| TotalRealMemory       | N/A | SSH  | `MemTotal`. Used in `Real Memory Usage` and `Total Physical Memory`.    |
| AvailableRealMemory   | N/A | SSH  | `MemFree`. Used in `Real Memory Usage` and `Available Physical Memory`. |
| TotalSwapMemory       | N/A | SSH  | `SwapTotal`. Used in `Swap Usage` and `Total Physical Memory`.          |
| AvailableSwapMemory   | N/A | SSH  | `SwapFree`. Used in `Swap Usage` and `Available Physical Memory`.       |

The connector performs the following command to retrieve information related to the memory utilization:

```bash
cat /proc/meminfo
```

Below you can find a description of the content available in this response:

- **MemTotal**: Total usable RAM (i.e. physical RAM minus a few reserved bits and the kernel binary code).
- **MemFree**: The sum of `LowFree` + `HighFree`.
- **MemAvailable**: An estimate of how much memory is available for starting new applications without swapping.
- **Buffers**: Relatively temporary storage for raw disk blocks that should not get very large (approximately 20 MB).
- **Cached**: In-memory cache for files read from the disk (the page cache). Does not include `SwapCached`.
- **SwapCached**: Memory that once was swapped out, which is swapped back in but still also in the swap file. If memory pressure is high, these pages do not need to be swapped out again because they are already in the swap file. This saves I/O.
- **SwapTotal**: Total amount of swap space available.
- **SwapFree**: Amount of swap space that is currently unused.
- **SReclaimable**: Part of `Slab`, which might be reclaimed, such as caches.
- **Slab**: In-kernel data structures cache.

> [!NOTE]
>
> - Even though cache and buffer memory can be freed up when needed and are thus available for use, these are returned as **used** memory by default (this applies for each parameter).
> - Compared with SNMP, the values displayed are identical, except `Available Physical Memory` and `Used Physical Memory`.

### Real Memory Usage (SSH)

$$
\begin{equation}
\begin{split}
\text{Real Memory Usage}&=\left(1-\frac{\text{Available Real Memory}}{\text{Total Real Memory}}\right)\times 100\\
&=\left(1-\frac{\text{MemFree}}{\text{MemTotal}}\right)\times{100}
\end{split}
\end{equation}
$$

### Swap Memory Usage (SSH)

$$
\begin{equation}
\begin{split}
\text{Swap Memory Usage}&=\left(1-\frac{\text{Available Swap Memory}}{\text{Total Swap Memory}}\right)\times{100}\\
&=\left(1-\frac{\text{SwapFree}}{\text{SwapTotal}}\right)\times{100}
\end{split}
\end{equation}
$$

### Total Physical Memory (SSH)

Total physical memory on this host (both real and swap memory). The value is divided by 1024.

$$
\begin{equation}
\begin{split}
\text{Total Physical Memory}&=\text{Total Real Memory}+\text{Total Swap Memory}\\
&=\text{MemTotal}+\text{SwapTotal}
\end{split}
\end{equation}
$$

### Available Physical Memory (SSH)

The total amount of memory free or available for use on this host (both real and swap memory).

$$
\begin{equation}
\begin{split}
\text{Available Physical Memory}&=\text{Available Real Memory}+\text{Available Swap Memory}\\
&=\text{MemFree}+\text{SwapFree}
\end{split}
\end{equation}
$$

### Used Physical Memory (SSH)

$$
\begin{equation}
\begin{split}
\text{Used Physical Memory}&=\frac{\lvert\text{Total Physical Memory}-\text{Available Physical Memory}\rvert}{1024}\\
&=\frac{\lvert(\text{MemTotal}+\text{SwapTotal})-(\text{MemFree}+\text{SwapFree})\rvert}{1024}
\end{split}
\end{equation}
$$

### Physical Memory Usage (SSH)

$$
\begin{equation}
\begin{split}
\text{Physical Memory Usage}&=100\times\frac{\text{Used Physical Memory}}{\text{Total Physical Memory}}\\
&=100\times\frac{\lvert(\text{MemTotal}+\text{SwapTotal})-(\text{MemFree}+\text{SwapFree})\rvert}{\text{MemTotal}+\text{SwapTotal}}
\end{split}
\end{equation}
$$

### Actual Memory Cached (SSH)

The total amount of real virtual memory currently allocated for use as cached memory. This object will not be implemented on hosts where the underlying operating system does not explicitly identify memory as specifically reserved for this purpose.

$$
\begin{equation}
\begin{split}
\text{Actual Memory Cached}&=\text{Used Memory Cached}+\text{Reclaimable Memory} \\
&=\text{Cached}+\text{SReclaimable}
\end{split}
\end{equation}
$$

### Actual Available Physical Memory (SSH)

Actual available physical memory on this host (both real and swap memory), where buffer and cached memory are considered as available.

$$
\begin{equation}
\begin{split}
\text{Actual Available Physical Memory}&=\frac{\left(\text{Available Physical Memory}+\text{Used Memory Buffers}+\text{Actual Memory Cached}\right)}{1024} \\
&=\frac{((\text{MemFree}+\text{SwapFree})+(\text{Buffers})+(\text{Cached}+\text{SReclaimable}))}{1024}
\end{split}
\end{equation}
$$

### Actual Used Physical Memory (SSH)

$$
\begin{equation}
\begin{split}
\text{Actual Used Physical Memory}&=\frac{\lvert\text{Total Physical Memory}-\text{Available Physical Memory}-\text{Used Memory Buffers}-\text{Actual Memory Cached}\rvert}{1024} \\
&=\frac{\lvert(\text{MemTotal}+\text{SwapTotal})-(\text{MemFree}+\text{SwapFree})-(\text{Buffers})-(\text{Cached}+\text{SReclaimable})\rvert}{1024}
\end{split}
\end{equation}
$$

### Actual Physical Memory Usage (SSH)

$$
\begin{equation}
\begin{split}
\text{Actual Physical Memory Usage}&=\frac{\text{Actual Used Physical Memory}}{\text{Total Physical Memory}}\times{100}
\end{split}
\end{equation}
$$

## SNMP Connection

| Parameter Name                   | PID | Type       | Display              | Comment                      |
| -------------------------------- | --- | ---------- | -------------------- | ---------------------------- |
| Total Swap Memory                | 118 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.3.0  |
| Available Swap Memory            | 119 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.4.0  |
| Total Real Memory                | 114 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.5.0  |
| Available Physical Memory        | 112 | SNMP       | General, Memory Info | OID: 1.3.6.1.4.1.2021.4.11.0 |
| Memory Cached                    | 122 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.3.0  |
| Available Real Memory            | 120 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.6.0  |
| Memory Buffer                    | 121 | SNMP       | Memory Info          | OID: 1.3.6.1.4.1.2021.4.14.0 |
| Swap Memory Usage                | 110 | Calculated | General, Memory Info | N/A                          |
| Real Memory Usage                | 111 | Calculated | General, Memory Info | N/A                          |
| Total Physical Memory            | 172 | Calculated | General, Memory Info | N/A                          |
| Used Physical Memory             | 113 | Calculated | General, Memory Info | N/A                          |
| Physical Memory Usage            | 124 | Calculated | Memory Info          | N/A                          |
| Actual Available Physical Memory | 173 | Calculated | Memory Info          | N/A                          |
| Actual Used Physical Memory      | 123 | Calculated | Memory Info          | N/A                          |
| Actual Physical Memory Usage     | 174 | Calculated | Memory Info          | N/A                          |

### Swap Memory Usage (SNMP)

$$
\text{Swap Memory Usage}=\left(1-\left(\frac{\text{Available Swap Memory}}{\text{Total Swap Memory}}\right)\right)\times{100}
$$

### Memory Usage Real (SNMP)

$$
\text{Memory Usage Real}=\left(1-\left(\frac{\text{Available Real Memory}}{\text{Total Real Memory}}\right)\right)\times{100}
$$

### Total Physical Memory (SNMP)

$$
\text{Total Physical Memory}=\text{Total Swap Memory}+\text{Total Real Memory}
$$

### Used Physical Memory (SNMP)

$$
\text{Used Physical Memory}=\text{Total Physical Memory}-\text{Available Physical Memory}
$$

### Physical Memory Usage (SNMP)

$$
\text{Physical Memory Usage}=\frac{\text{Used Physical Memory}}{\text{Total Physical Memory}}\times{100}
$$

### Actual Available Physical Memory (SNMP)

$$
\text{Actual Available Physical Memory}=\text{Available Physical Memory}+\text{Memory Buffer}+\text{Memory Cached}
$$

### Actual Physical Memory Used (SNMP)

$$
\text{Actual Physical Memory Used}=\lvert\text{Total Physical Memory}-\text{Available Physical Memory}-\text{Memory Buffer}-\text{Memory Cached}\rvert
$$

### Actual Physical Memory Usage (SNMP)

$$
\text{Actual Physical Memory Usage}=\frac{\text{Actual Physical Memory Used}}{\text{Total Physical Memory}}\times{100}
$$

## Updated Calculations

Starting from version 2.0.x.x, the calculations for the following Linux Platform memory parameters have been updated to provide more accurate values.

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

### Total Memory

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

### Swap Memory Usage

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

### Memory Used

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

### Memory Cached

The amount of memory used for caching file data to improve system performance, expressed in MB. This includes page cache (`Cached`) and reclaimable slab memory (`SReclaimable`). Cached memory can be freed by the system when applications need more memory.

- **SSH Only**

$$
\begin{equation}
\begin{split}
\text{Memory Cached}&=\frac{\text{Cached}+\text{SReclaimable}}{1024}\\[10pt]
\end{split}
\end{equation}
$$

### Additional Changes

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
