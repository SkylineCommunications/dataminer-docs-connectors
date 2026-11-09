---
uid: Connector_help_Socomec_Diris_D-50_-_S-130
description: "Monitor a Socomec Diris S-130 measurement module exported by the Diris D-50 connector in DataMiner, with instruments, energy, and alarm tables."
---

# Socomec Diris D-50 - S-130

## About

The Socomec Diris S-130 is a measurement module of the DIRIS Digiware system. It provides instruments, fundamental, and energy measurements for the monitored circuit and reports Boolean and system alarms.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the S-130 module through the D-50 gateway and shows its measurements, energy counters, and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each S-130 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, the product version and build information, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Measurement

This page contains the **S130 Instruments Measurement**, **S130 Instruments Fundamental Measurement**, and **S130 Energy Measurement** tables, with the voltages, currents, power, power factor, fundamental values, hour meters, and energy counters of the module.

### Alarms

This page contains the **S130 Boolean Alarm Current Status** and **S130 System Alarm Current Status** tables, which list the active alarms of the module with their type, cause, criticality, start date, and duration.
