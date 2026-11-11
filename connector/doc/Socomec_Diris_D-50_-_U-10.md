---
uid: Connector_help_Socomec_Diris_D-50_-_U-10
description: "Monitor a Socomec Diris U-10 measurement module exported by the Diris D-50 connector in DataMiner, with instruments measurements and system alarms."
---

# Socomec Diris D-50 - U-10

## About

The Socomec Diris U-10 is a voltage measurement module of the DIRIS Digiware system. It provides the frequency and the phase-to-neutral and phase-to-phase voltages of the monitored network and reports system alarms.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the U-10 module through the D-50 gateway and shows its measurements and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each U-10 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, the product version and build information, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Measurement

This page contains the **U10 Instruments Measurement** table, with the date of the last instance, the integration time, the frequency, the phase-to-neutral voltages V1, V2, and V3, and the phase-to-phase voltages U12, U23, and U31.

### Alarms

This page contains the **U10 System Alarm Current Status** table, which lists the active system alarms of the module with their type, cause, criticality, start date, and duration.
