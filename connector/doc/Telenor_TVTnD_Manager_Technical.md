---
uid: Connector_help_Telenor_TVTnD_Manager_Technical
---

# Telenor TVTnD Manager

## About

In the Telenor DMS, the **Telenor TVTnD Manager** is in charge of customer devices diagnosis. Customer diagnosis input parameters are customer ID, diagnosis period(start and end time) and response message language.

Diagnosis is performed on request. It is performed by the configurable DOM diagnosis configurations, found in **TVTnD Manager Configurator** Low-code App.

Results of the diagnosis are stored in three categories represented by tables:

- **Diagnosis log** - Information about the diagnosis process, including diagnosis time, start and end times, customer ID, user or the process who started diagnosis, and JSON response containing diagnosis results.
- **Diagnosis** - Linked with the diagnosis configurations, this table contains the diagnoses generated when specific diagnosis configuration's run results in a diagnosis for the device.
- **Detected Issue** - Table containing all detected issues, linked with the specific diagnosis run.

Diagnoses and detected issues aggregation by device class type is performed every 5 minutes, and the results are stored in tables dedicated for each device class type.

These tables support further analysis and reporting.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

On the **General** page, you can:

- Configure input parameters (Diagnosed Customer ID, Start Time, End Time and Diagnosis Language).
- View information about the last diagnosis run, including the time it was started, its duration, and the status of the last run.

### Diagnosis Results

Diagnosis Results are saved on a separate page, in already mentioned three tables (*Diagnosis Log, Diagnosis, Detected Issue*):
![Diagnosis Results](~/connector/images/Telenor_TVTnD_Manager_Diagnosis_Results.png)

### Detected Issues Statistics

Detected issues statistics represent each configured detected issue's last hour and the last day errors count, aggregated by device class type (*STB, Smartphone, Tablet, Chromecast, PC Portal, Apple TV, Android TV, Android TV Launcher*):
![Detected Issues Statistics](~/connector/images/Telenor_TVTnD_Manager_Detected_Issues_Statistics.png)


#### Diagnoses Statistics

Diagnoses statistics represent each configured diagnosis' last hour and the last day errors count, aggregated by device class type (*STB, Smartphone, Tablet, Chromecast, PC Portal, Apple TV, Android TV, Android TV Launcher*):
![Diagnoses Statistics](~/connector/images/Telenor_TVTnD_Manager_Diagnosis_Statistics.png)


