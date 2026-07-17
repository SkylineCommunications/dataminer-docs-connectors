---
uid: Connector_help_Telenor_TVTnD_Manager
---

# Telenor TVTnD Manager

## About

In the Telenor DMS, the **Telenor TVTnD Manager** is in charge of customer device diagnosis. It automates the troubleshooting and diagnosis (TVTnD) of customer devices by combining device data, trend information, and MAM events into actionable detected issues and diagnoses.

Diagnosis can be triggered **on demand** for a single customer, run automatically as a **nightly batch** across all customer devices, or started **externally** by other systems through Inter-App Calls. Results are consolidated into log, diagnosis, and detected-issue tables that feed statistics and reporting.

## Key Features

- **On-demand customer diagnosis**: Diagnose a specific customer over a chosen time range and in a chosen response language, using the configurable diagnosis definitions from the **TVTnD Manager Configurator** low-code app.
- **Automated nightly diagnosis**: Run a scheduled batch that diagnoses all customer devices per collector element for the previous day, with progress tracking and a clear run status.
- **Detected issues and diagnoses**: Automatically translate device, infrastructure, and service data into linked detected issues and diagnoses that are easy to analyze.
- **Statistics and duration insights**: Track error counts per detected issue and diagnosis (last hour and last day) aggregated by device class, and monitor how long each diagnosis phase takes.
- **External triggering**: Let other systems start a diagnosis through Inter-App Calls, integrating the manager into automated troubleshooting workflows.

## Use Cases

### Proactively catch customer issues overnight

**Challenge**: Manually diagnosing every customer device is not scalable, and issues often surface only after customers call support.

**Solution**: The automated nightly diagnosis runs across all collector elements, diagnosing every customer device for the previous day and storing detected issues and diagnoses for review.

**Benefit**: Support and operations teams start the day with an up-to-date overview of device problems, enabling proactive follow-up before customers are affected.

### Speed up individual troubleshooting

**Challenge**: When a customer reports a problem, agents need a fast, consistent way to pinpoint what is wrong across devices, infrastructure, and services.

**Solution**: An on-demand diagnosis for a single customer and time range returns detected issues and diagnoses, complemented by related channel and service alarms.

**Benefit**: Agents resolve cases faster with a consistent, data-driven diagnosis instead of manual investigation.

## Technical Reference

### Prerequisites

- **Telenor EPM Collector** elements, which the nightly diagnosis enumerates to diagnose customer devices.
- Diagnosis definitions configured in the **TVTnD Manager Configurator** low-code app.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telenor_TVTnD_Manager_Technical).
