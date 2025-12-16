---
uid: microsoft_platform_technical_cpu_load_calculation
---

# CPU Load Calculation

> [!NOTE]
> This calculation is available in all main connector ranges:
>
> - Microsoft Platform connector range 1.1.3.x
> - Microsoft Platform connector range 6.0.0.x
> - Microsoft Platform connector range 7.0.0.x

## Metrics

The following metrics are used to calculate the CPU load:

- [Timestamp_Sys100NS](#timestamp_sys100ns)
- [Percent Processor Time](#percent-processor-time)

### Timestamp_Sys100NS

The timestamp value in 100 nanoseconds units. Available in `Win32_PerfRawData_PerfOS_Processor`.

### Percent Processor Time

The percentage of elapsed time that the processor spends executing a non-idle thread. This value is calculated by measuring the percentage of time the processor spends executing the idle thread and subtracting that value from 100%.

Key characteristics:

- Each processor has an idle thread that consumes cycles when no other threads are ready to run.
- This counter is the primary indicator of processor activity.
- This displays the average percentage of busy time observed during the sample interval.

> [!IMPORTANT]
> The accounting calculation of whether the processor is idle is performed at an internal sampling interval of the system clock (10 ns). On modern fast processors, `PercentProcessorTime` can underestimate processor utilization because the processor may spend significant time servicing threads between system clock sampling intervals. Workload-based timer applications are more likely to be measured inaccurately, as timers are signaled just after the sample is taken.

The counting type for this property is `PERF_100NSEC_TIMER_INV`, which measures the percentage of time the counter **is not in use**, in 100 nanosecond units. This is essentially an inverse timer that tracks idle time rather than busy time.

WMI Query:

```sql
SELECT PercentProcessorTime, Timestamp_Sys100NS, Name FROM Win32_PerfRawData_PerfOS_Processor
```

This query returns the percent processor time for each logical processor available in the server. In addition, it returns an extra entry that provides the total processor load (`_Total`).

The performance counter is based on **idle time**, not directly on busy time. Windows tracks how long the processor spends in the **idle thread** as follows:

- Raw counter values ($N_{1}$, $N_{2}$) represent cumulative idle time ticks at two sampling points of `Percent Processor Time`.

  $$
  \Delta\,\,\text{Percent Processor Time}= N_{2}-N_{1}
  $$

- Raw base values ($D_{1}$, $D_{2}$) represent cumulative total ticks at those points (from `Timestamp_Sys100NS`).

  $$
  \Delta\,\,\text{Timeticks} = D_{2}-D_{1}
  $$

Since the counter type identifies it as inverse, the CPU load is calculated as follows (based on [Using Raw Performance Data Classes](https://learn.microsoft.com/en-us/windows/win32/wmisdk/monitoring-performance-data#using-raw-performance-data-classes)):

$$
\text{CPU Load}=100\times\left(1-\frac{\Delta\,\,\text{Percent Processor Time}}{\Delta\,\,\text{Timeticks}}\right)
$$

## Characteristics of the CPU load calculation

- The `Percent Processor Time` is a time-based metric computed from idle vs. busy time over a sampling interval. It does not depend on the CPU's clock frequency.

- The metric `Percent Processor Time` is capped at 100%.

- The use of `Current Speed` and `Base Speed` can lead to CPU usage higher than 100%. (See [CPU usage exceeds 100% in Task Manager and Performance Monitor if Intel Turbo Boost is active](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/cpu-usage-exceeds-100).)

## References

- [WMI Tasks: Performance Monitoring](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-tasks--performance-monitoring)
- [Monitoring Performance Data](https://learn.microsoft.com/en-us/windows/win32/wmisdk/monitoring-performance-data#using-raw-performance-data-classes)
