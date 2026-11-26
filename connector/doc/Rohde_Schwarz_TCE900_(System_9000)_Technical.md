---
uid: Connector_help_Rohde_Schwarz_TCE900_(System_9000)_Technical
description: Technical help for the Rohde Schwarz TCE900 (System 9000) connector, with SNMP connection setup, page overview, and control cautions.
---

# Rohde Schwarz TCE900 (System 9000)

## About

The **Rohde Schwarz TCE900 (System 9000)** connector monitors and controls the Rohde & Schwarz TCE900 transmitter control unit via SNMP. It covers the transmitter state and power, input interfaces and automatic input switching, modulation setup for the transmission standards exposed by the TCE900 (DVB-T, DVB-T2, ATSC, ATSC 3.0, ISDB-T, DTMB, DAB, FM, and analog TV), redundancy (N+1, multi-transmitter, backup), amplifiers, cooling, sensors, and the site environment.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the TCE900.
- **Device address**: Not required.

SNMP Settings:

- **IP port**: The IP port of the TCE900 (default: *161*).
- **Get community string**: The community string used when reading values from the TCE900 (default: *public*).
- **Set community string**: The community string used when setting values on the TCE900 (default: *private*).

### Web Interface

The Web Interface page embeds the web interface of the TCE900 using the **Web Interface** address on the General page. This address is filled in automatically with the polling IP of the element when it is empty. You can overwrite it if the web interface must be reached on a different address, for example when the element polls through a gateway.

The web interface is only accessible when the client machine has network access to the product.

## How to Use

All data is retrieved by SNMP polling on three cycles (1 min, 1 h, and 24 h); each cycle also runs once immediately after element startup, so the slow-changing configuration pages are filled in without waiting for the daily cycle.

### General Page

This page shows the identification and status of the controller: system type (transmitter, multi-transmitter, or N+1), software and firmware versions, operation hours, power-up cycles, and the hardware and configuration status of the device. The **Date Time Configuration** table allows you to enable NTP and configure the time server and time offset.

The **Reboot**, **Software Update**, and **Software Update Mode** parameters act directly on the device. Rebooting the controller interrupts transmission, and a software update should only be started after the update file has been prepared on the device, as described in the vendor documentation.

### Transmitter Configuration Page

The **Control Table** shows and sets the redundancy mode, modulation mode, and amplifier type of the transmitter. These settings define the overall configuration of the transmitter and should normally only be changed during commissioning.

### SNMP Page

This page configures the trap behavior of the device itself: it allows you to enable or disable the IRT and R&S notifications (all, faults only, or warnings only), send a test notification, synchronize the trap sinks, and follow the trap counter.

> [!NOTE]
> The connector does not process incoming traps. All data is polled, so the trap settings on this page only affect other trap receivers and do not influence the DataMiner element.

### Management Page

The **Install Option**, **Option Key**, and **Deactivation** tables allow you to view the installed software options and to enter option or deactivation keys. Entering a key changes the licensed functionality of the transmitter.

### UPS, GPS, Device Information, Environment, and Rack Control Pages

These pages show the status of the site infrastructure connected to the controller: the UPS state and battery, the GPS receiver configuration, antenna state, and satellite count, the general device state and configuration, the temperature, humidity, and dew point readings with configurable temperature warning and fault limits, and the overvoltage protection (OVP) assignment and state of the rack.

### Transmitter Page

The **Transmitter State** table shows the forward and reflected power, modulation mode, and PA efficiency of each transmitter. The **Transmitter Commands** table exposes the control actions: reset, operation mode, nominal power, reserve exciter operation mode, change modulation, and reflection check. The **Exciter Automatic** table shows the exciter switching settings. Use the **Reserve** page button to open the reserve exciter status.

Changing the operation mode or nominal power takes effect immediately on the transmitter. Reducing the nominal power or switching to standby affects the on-air service.

### Exciter, Frequency Regulation, SFN, Precorrection, Output Stage, Amplifier, and Switchless Combiner Pages

These pages show the signal path of the transmitter from the exciter to the antenna: the exciter status, the frequency reference and regulation, the SFN synchronization status and delays, the linear and non-linear precorrection and signal quality (use the **Linear** and **Non Linear** page buttons on the Precorrection page), the output stage and amplifier status, and the switchless combiner status.

### Input Interfaces and Automatic Input Pages

The **Input Interfaces** page shows the IP feed statistics (packets, errors), the TS feed status, and the RF front end. Use the **Sattelite Feed** and **Receiver Feed** page buttons to open the satellite tuner, LNB, CAM, BISS, and service information, and the RX feed MER and BER values.

The **Automatic Input** page shows the automatic input switching configuration, the currently active input, and whether seamless switching is possible. When a transmitter unexpectedly switched input, check the active input and the quality of the feeds on this page first.

### Presets Page

The **Preset Commands** table allows you to load or save program presets 1 to 4, and the **Preset Status** table shows the active preset and program settings. Loading a preset immediately reconfigures the transmitter and may interrupt the service; saving a preset overwrites the stored preset on the device.

### Sensors and SDE Pages

The **Sensors** page shows the RF sensors with their forward and reflected power limits and VSWR. The **SDE** page shows the NTP synchronization status (stratum, delay, offset, jitter) and the TAI/UTC time reference used for SFN operation.

### Gapfiller Transposer Page

This page shows the gap filler or transposer configuration and status, and is only relevant for transmitters that are used in this mode.

### Multi Transmitter, N+1, and Backup Transmitter Pages

These pages show the redundancy status of each transmitter in a multi-transmitter, N+1, or backup transmitter system, including the automatic switches and automatic program presets used by the N+1 controller. They are only relevant when the **System Type** on the General page is configured accordingly.

### Modulation Pages (DVBT2, DVBT, ATSC, ISDBT, ATV, DAB, FM, DTM, ATSC30)

Each supported transmission standard has its own page group with the setup, input, and output parameters of that standard. Only the pages of the standard that is configured as **Modulation Mode** on the Transmitter Configuration page are relevant for a given transmitter.

### Liquid Cooling and Air Cooling Pages

These pages show the status of the cooling system of the transmitter. The **Liquid Cooling** page shows the pump and fan state and the cooling configuration; the **Air Cooling** page shows the cooling state, pressure, and configuration. Only the page matching the installed cooling type is relevant.
