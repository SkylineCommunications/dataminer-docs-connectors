---
uid: Connector_help_Telenor_TVTnD_Manager_Technical
---

# Telenor TVTnD Manager

## About

In the Telenor DMS, the **Telenor TVTnD Manager** is in charge of customer devices diagnosis. Customer diagnosis input parameters are the customer ID, diagnosis period (start and end time), and response message language.

Diagnosis is performed on request, based on the configurable DOM diagnosis configurations in the **TVTnD Manager Configurator** low-code app. A diagnosis combines device information, trend data, and MAM events into detected issues and diagnoses, and can also collect related service alarms.

Results of the diagnosis are stored in three categories represented by tables:

- **Diagnosis Log**: Information about the diagnosis process, including the diagnosis time, the start and end times, the customer ID, the user or process that started the diagnosis, and the JSON response containing diagnosis results.
- **Diagnosis**: Linked with the diagnosis configurations, this table contains the diagnoses generated when the run for a specific diagnosis configuration results in a diagnosis for the device.
- **Detected Issue**: Table containing all detected issues, linked with the specific diagnosis run.

Diagnoses and detected issues aggregation by device class type is performed every 5 minutes. Diagnosis results are stored in tables dedicated for each device class type, while detected issues are stored in a single table with a device class type column. These tables support further analysis and reporting.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Before running diagnoses, configure the diagnosis definitions in the **TVTnD Manager Configurator** low-code app. The automated nightly diagnosis additionally relies on **Telenor EPM Collector** elements being present in the system; these are enumerated to determine which customer devices to diagnose.

## How to Use

Diagnosis can be started in three ways:

- **On demand** from the **General** page, for a single customer and time range.
- **Automatically** through the nightly diagnosis, which diagnoses all customer devices per collector element.
- **Externally** through Inter-App Calls: other systems send a `StartDiagnosis` message that the connector processes to run a diagnosis.

As this is a virtual connector, it does not poll a device directly, so **no traffic appears in the Stream Viewer**. Data is retrieved from the EPM infrastructure, trend information, and MAM events (via OpenSearch), and results are persisted as DOM instances.

### General

On the **General** page, you can:

- Configure input parameters (Diagnosed Customer ID, Start Time, End Time, and Diagnosis Language).
- View information about the last diagnosis run, including the time it was started, its duration, and the status of the last run.

![General Page](~/connector/images/Telenor_TVTnD_Manager_General.png)

### Nightly Diagnosis Run

The nightly diagnosis is a scheduled batch that diagnoses all customer devices, per collector element, for the previous day.

On the **Nightly Diagnosis Run** page, you can:

- Enable or disable the nightly check with **Nightly Check Enabled**.
- Start a nightly run manually with the **Run Nightly Check** button.
- Follow progress through **Nightly Check Diagnosed Customers** (the number of customers diagnosed so far) and **Nightly Diagnosis Status**, which reflects the current state of the run (for example, *Running* or *Completed*).

When a nightly run starts, the diagnosis log, diagnosis, and detected issue tables are cleared, all collector elements are enumerated, and each customer device is diagnosed for the previous day. The run details are also persisted as dedicated DOM instances (Nightly Diagnosis Run, Nightly Diagnosis, and Nightly Detected Issue).

### Nightly Run Collectors

The **Nightly Run Collectors** page shows the **Nightly Diagnosed Collectors** table, which lists the collector elements (of the **Telenor EPM Collector** protocol) processed during the last nightly diagnosis batch. For each collector, it shows the ID, name, county, and household count.

Because the nightly diagnosis can be distributed across multiple manager elements, this table also indicates whether a collector was already diagnosed by another element during the nightly run. This filtering ensures each collector is diagnosed only once, so the workload can be shared between elements without duplicating diagnoses.

### Diagnosis Duration Statistics

The **Diagnosis Duration Statistics** page shows how long the last diagnosis and its individual phases took (all values in milliseconds):

- **Last Diagnosis Duration**: total duration of the last diagnosis.
- **Last API Diagnosis Duration**: time spent in the diagnosis API call.
- **Last Device Fetch Duration**: time spent retrieving device information.
- **Last Device Diagnosis Duration**: time spent diagnosing devices (excluding infrastructure and service diagnosis).
- **Last Infrastructure Diagnosis Duration**: time spent diagnosing infrastructure.
- **Last Service Diagnosis Duration**: time spent diagnosing services.

These values help identify which phase dominates the diagnosis time and support performance tuning.

### Diagnosis Results

Diagnosis results are shown on a separate page, in the **Diagnosis Log**, **Diagnosis**, and **Detected Issue** tables.

![Diagnosis Results](~/connector/images/Telenor_TVTnD_Manager_Diagnosis_Results.png)

### Alarms

The **Alarms** page consolidates the alarms related to the diagnosed services, so they can be reviewed together with the diagnosis results:

- **Channel Services Alarms**: alarms for channel-based services (for example, OTT and Broadcast), including channel and service identifiers, alarm timing, severity, active state, and type.
- **Other Services Alarms**: alarms for other services, including alarm timing, severity, and active state.

Active alarms are kept up to date, and rows are marked inactive when the corresponding alarms clear.

### Detected Issues Statistics

In the detected issues statistics, you can find the error count for each configured detected issue in the last hour and the last day, aggregated by device class type (*STB*, *Smartphone*, *Tablet*, *Chromecast*, *PC Portal*, *Apple TV*, *Android TV*, *Android TV Launcher*):

![Detected Issues Statistics](~/connector/images/Telenor_TVTnD_Manager_Detected_Issues_Statistics.png)

#### Diagnoses Statistics

In the diagnoses statistics, you can find the error count for each configured diagnosis in the last hour and the last day, aggregated by device class type (*STB*, *Smartphone*, *Tablet*, *Chromecast*, *PC Portal*, *Apple TV*, *Android TV*, *Android TV Launcher*):

![Diagnoses Statistics](~/connector/images/Telenor_TVTnD_Manager_Diagnosis_Statistics.png)
