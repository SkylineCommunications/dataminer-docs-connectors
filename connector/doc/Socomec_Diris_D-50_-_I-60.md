---
uid: Connector_help_Socomec_Diris_D-50_-_I-60
description: "Monitor a Socomec Diris I-60 current measurement module exported by the Diris D-50 connector in DataMiner, with measurements, energy, and alarms."
---

# Socomec Diris D-50 - I-60

## About

The Socomec Diris I-60 is a current measurement module that connects to the DIRIS Digiware bus. It is a panel-mounted multifunction meter with enhanced data logging functions and curve recording for power quality events. The sensors can be adapted to all types of new or existing installations.

This connector is exported by the [Socomec Diris D-50](xref:Connector_help_Socomec_Diris_D-50) connector. The parent element polls the I-60 module through the D-50 gateway and shows its measurements, energy counters, and alarms in this DVE.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!IMPORTANT]
> Do not create elements with this connector manually. The parent Socomec Diris D-50 element creates a DVE automatically for each I-60 module for which **DVE Creation** is enabled.

## How to Use

### General

This page shows the product information of the module, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, the product version and build information, **Vendor Name**, **Product Name**, **Extended Name**, and **Resource Version**.

### Measurement

This page contains the **Instruments Measurement**, **Instruments Fundamental Measurement**, and **Energy Measurement** tables.

The **Energy Measurement** table also contains the **Reset Partial Meters** button, which resets the partial hour meter and partial energy counters of the module. The reset uses the **I60 Password** configured on the **Connection Info** page of the parent element, which must match the unlock code configured on the module.

### System Alarms

This page contains the **System Alarm** table, which lists the active system alarms of the module with their type, cause, criticality, start date, and duration.
