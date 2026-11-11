---
uid: Connector_help_Socomec_Diris_D-50_-_B-30
description: "Monitor a Socomec Diris B-30 power monitoring module exported by the Diris D-50 connector in DataMiner, including measurements, I/O, and alarms."
---

# Socomec Diris D-50 - B-30

## About

The Socomec Diris B-30 is a modular power monitoring device that can communicate wirelessly or over RS485. Its four independent RJ12 current inputs allow it to manage circuits of different types and in different numbers.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the B-30 module through the D-50 gateway and shows its measurements, energy counters, I/O status, and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each B-30 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, **Customization Data Loaded**, the product version and build information, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Measurement

This page contains the **Energy Measurement**, **Instruments Measurement**, and **Instantaneous Temperature** tables.

The **Energy Measurement** table also contains the **Reset Partial Meters** button, which resets the partial hour meter and partial energy counters of the module. The reset uses the **B30 Password** configured on the **Connection Info** page of the parent element, which must match the unlock code configured on the module.

### Network Settings

This page shows the network measurements of the module, including the date of the last instance, the integration time, the system phase-to-neutral and phase-to-phase voltages, the frequency, the phase-to-neutral voltages V1, V2, V3, and Vn, and the phase-to-phase voltages U12, U23, and U31.

### I/O

This page shows the number of inputs and outputs, their status, activation, and connection status, and the function assigned to each input and output.

### Analog Inputs

This page contains the **Analog Inputs** table.

### Alarm Pages

The **System Alarms**, **Analog Alarms**, **Logical Alarms**, **Combination Alarms**, **Inrush Alarms**, and **EN50160 Alarms** pages each contain a table with the current status of the alarms of that type, including the cause, criticality, start date, and duration.
