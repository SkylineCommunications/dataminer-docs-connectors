---
uid: Connector_help_Socomec_Diris_D-50_-_U-30
description: "Monitor a Socomec Diris U-30 voltage measurement module exported by the Diris D-50 connector in DataMiner, with network voltages and alarm status."
---

# Socomec Diris D-50 - U-30

## About

The Socomec Diris U-30 is a voltage measurement module that is part of the DIRIS Digiware system. It measures the system voltages and detects voltage dips, interruptions, and swells. It also captures alarms and keeps a history of the average values.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the U-30 module through the D-50 gateway and shows its voltage measurements and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each U-30 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, the product version and build information, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Network Settings

This page shows the network measurements of the module, including the date of the last instance, the integration time, the system phase-to-neutral and phase-to-phase voltages, the frequency, the phase-to-neutral voltages V1, V2, V3, and Vn, and the phase-to-phase voltages U12, U23, and U31.

### Alarm Pages

The **System Alarms**, **Analog Alarms**, **Combination Alarms**, and **EN50160 Alarms** pages each contain a table with the current status of the alarms of that type, including the cause, criticality, start date, and duration.
