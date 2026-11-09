---
uid: Connector_help_Socomec_Diris_D-50
description: "Monitor Socomec Diris Digiware modules through the Diris D-50 gateway in DataMiner, with automatic DVE creation, measurements, energy, and alarms."
---

# Socomec Diris D-50

## About

The Socomec DIRIS Digiware D-50 is a display and gateway module that acts as the master on the RS485 bus and on the DIRIS Digiware bus. It centralizes the measurements of up to 32 Socomec measurement modules, such as the Diris B-30, I-60, U-30, S-130, U-10, and I-35, and makes them available over Modbus/JBUS.

This connector polls the D-50 over a serial connection, discovers the modules connected to it, and creates a DVE (dynamic virtual element) for each module. Each DVE shows the electrical measurements, energy counters, and alarm status of its module, so you can monitor a complete Digiware installation from DataMiner through a single gateway element.

> [!NOTE]
> Connectivity for all exported connectors is managed by this connector.

## Key Features

- **Automatic module discovery and DVE creation**: The modules connected to the D-50 are detected automatically and listed with their type, Modbus address, and detection status. For each module, you choose whether a DVE is created.

- **Lifecycle management**: Modules that disappear from the D-50 are flagged in the device table, and their DVEs can be removed automatically per module type.

- **Electrical measurement and energy tables**: Each module DVE shows the voltages, currents, power, power factor, and energy counters that the module provides, in tables that are ready for alarming and trending.

- **Module alarm status**: System, analog, logical, combination, inrush, and EN50160 alarm status tables are available per module, depending on the module type.

- **Partial energy meter reset**: Partial hour meters and partial energy counters of the B-30, I-60, and I-35 modules can be reset from DataMiner, using the unlock code configured on the module.

- **Gateway identification and network settings**: Product identification, software versions, JBUS settings, and Ethernet settings of the D-50 itself are available in the parent element.

## Use Cases

### Centralized Monitoring of a Digiware Installation

**Challenge**: A Digiware installation can consist of dozens of measurement modules behind a single gateway, and each module exposes a large number of registers.

**Solution**: The connector polls the D-50 once, discovers all connected modules, and creates one DVE per module with its measurements grouped in clear tables.

**Benefit**: Operators monitor every module from one DataMiner element without configuring addresses or registers manually.

### Energy Consumption Tracking per Circuit

**Challenge**: Energy consumption must be tracked per circuit or per department, and partial counters must be reset at the start of each reporting period.

**Solution**: The energy measurement tables of the B-30, I-60, and I-35 DVEs expose total and partial energy counters, and the **Reset Partial Meters** button restarts the partial counters from DataMiner.

**Benefit**: Energy reports can be trended and reset centrally, without accessing each module on site.

### Module Alarm Surveillance

**Challenge**: Alarms raised by the measurement modules, such as voltage dips, inrush events, or system faults, are only visible on the D-50 display or in the Socomec software.

**Solution**: The alarm status tables of each DVE list the active alarms with their type, cause, criticality, start date, and duration.

**Benefit**: Module alarms are integrated in the DataMiner alarm console next to the rest of the infrastructure.

## Technical Reference

### Prerequisites

- **DataMiner 10.2.0.0-12603 or higher** is required to run the connector.

- **A Diris D-50 gateway** that is reachable from the DataMiner Agent, either through a direct serial port or through a serial-over-IP interface.

- **The unlock codes of the B-30, I-60, and I-35 modules**, if you want to reset partial meters from DataMiner.

### Exported Connectors

The parent element creates a DVE for each module for which **DVE Creation** is enabled. The following exported connectors are available:

- [Socomec Diris D-50 - B-30](xref:Connector_help_Socomec_Diris_D-50_-_B-30)
- [Socomec Diris D-50 - I-35](xref:Connector_help_Socomec_Diris_D-50_-_I-35)
- [Socomec Diris D-50 - I-60](xref:Connector_help_Socomec_Diris_D-50_-_I-60)
- [Socomec Diris D-50 - S-130](xref:Connector_help_Socomec_Diris_D-50_-_S-130)
- [Socomec Diris D-50 - U-10](xref:Connector_help_Socomec_Diris_D-50_-_U-10)
- [Socomec Diris D-50 - U-30](xref:Connector_help_Socomec_Diris_D-50_-_U-30)

### Connections

#### Serial Main Connection

This connector uses a serial connection (Modbus/JBUS RTU) and requires the following input during element creation:

- **Direct connection**:

  - **Baud rate**, **Data bits**, **Stop bits**, **Parity**, and **Flow control**: The serial settings specified in the device manual and configured on the D-50.

- **Interface connection** (serial over IP):

  - **IP address/host**: The IP address or hostname of the serial interface or of the D-50.
  - **IP port**: The IP port of the serial interface.
  - **Bus address**: The Modbus/JBUS slave address of the D-50.

### Initialization

After you create the element, go to the **Connection Info** page and fill in the **B30 Password**, **I60 Password**, and **I35 Password** parameters if you want to reset partial meters from DataMiner. Each password must match the unlock code configured on the module. If you do not change these parameters, the default values preconfigured in the connector are used.

Then, on the **Device Overview** page, set **DVE Creation** to *Enabled* for each module for which you want a DVE. Optionally, on the **DVE Overview** subpage, set **Automatic Delete Missing Devices** to *Enabled* for the module types for which missing devices and their DVEs must be removed automatically.

### How to Use

#### General

This page shows the product identification of the D-50 itself, such as the **Product Order ID**, **Product ID**, **JBUS Table Version**, **Product Software Version**, serial number fields, **Vendor Name**, **Product Name**, **Extended Name**, and the product version and build information.

#### Connection Info

This page shows the common settings of the D-50, including the **DHCP Status**, **JBUS Gateway Status**, **JBUS RTU Over Ethernet Status**, the external JBUS baud rate, parity, and stop bit, the **JBUS Slave Address**, the Ethernet IP address, gateway, and mask, and the **JBUS Gateway Master Timeout Request**.

The **B30 Password**, **I60 Password**, and **I35 Password** parameters contain the unlock codes that the connector sends when you reset the partial meters of a module.

#### Device Overview

This is the default page of the element. The **Devices** table lists all modules known to the D-50, with their **Name**, **Device Type**, **Modbus Address**, **IP Address**, **Network ID**, and **Detection Status** (*Updated*, *Equal*, *New*, *Deleted*, or *Recreated*).

- Set **DVE Creation** to *Enabled* to create a DVE for a module, or to *Disabled* to delete its DVE.
- Use the **Enable All DVEs** and **Disable All DVEs** buttons to create or delete the DVEs of all modules at once.
- Use the **Remove** button to remove a module from the table together with its DVE.

The **Overall Polling Status** (*Done* or *Busy*) and **Polling Steps** parameters show the progress of the polling cycle, from *Get Devices* through the detail polling of each module type. **Buffer Timeout Time** defines the number of minutes after which the polling buffer is reset.

#### DVE Overview

This subpage contains the **B30 DVEs**, **I60 DVEs**, **U30 DVEs**, **S130 DVEs**, **U10 DVEs**, and **I35 DVEs** tables, which list the created DVEs with their key, name, and linked element.

With the **Automatic Delete Missing Devices** toggles for the B30, I60, U30, and I35 module types, you can specify whether modules that disappear from the D-50 and their linked DVEs are removed automatically.
