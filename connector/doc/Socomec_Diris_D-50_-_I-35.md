---
uid: Connector_help_Socomec_Diris_D-50_-_I-35
description: "Monitor a Socomec Diris I-35 module exported by the Diris D-50 connector in DataMiner, with measurements, energy meters, partial reset, and alarms."
---

# Socomec Diris D-50 - I-35

## About

The Socomec Diris I-35 is a measurement module of the DIRIS Digiware system. It measures voltages, currents, power, and energy on the monitored circuit and reports system alarms.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the I-35 module through the D-50 gateway and shows its measurements, energy counters, and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each I-35 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, **Customization Data Loaded**, the product version and build information, **Software Technical Base Version**, **Customization Version**, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Measurement

This page contains the following tables:

- **Instruments Measurement**: The status and date of the last instance, the integration time, the frequency, the phase-to-neutral voltages V1, V2, and V3, the phase-to-phase voltages U12, U23, and U31, the currents I1, I2, I3, and In, the nominal apparent power, the total active, reactive, lagging reactive, leading reactive, and apparent power, and the total power factor and its type.

- **Instruments Fundamental Measurement**: The fundamental (H1) voltages, currents, and phase angles.

- **Energy Measurement**: The load status, the total hour meter, the total active, reactive, and apparent energies (including residual, lagging, and leading variants), the partial hour meter and partial energies, the date of the last partial reset, and the values at the time of that reset.

To reset the partial hour meter and partial energy counters, click the **Reset Partial Meters** button in the **Energy Measurement** table. The **Partial Reset Result** parameter shows the result of the last reset.

The reset command uses the **I35 Password** configured on the **Connection Info** page of the parent element, which must match the unlock code configured on the module. After the reset, **Partial Reset Result** shows *Succeeded* or a failure reason, e.g., when the module does not respond or the reset date does not change.

### System Alarms

This page contains the **System Alarm** table, which lists the active system alarms of the module with their acknowledge ID, status, alarm type, alarm cause, criticality, start date, duration, startup delay, dropout delay, and line.
