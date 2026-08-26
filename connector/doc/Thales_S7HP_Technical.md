---
uid: Connector_help_Thales_S7HP_Technical
---

# Thales S7HP

## About

The Thales S7HP is a high-power shortwave radio transmitter. This connector uses SNMP to monitor and control the transmitter, covering transmitter and modulator functions, alarms, faults, modules, status information, measurements, and events.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The element has the following data pages:

### General

This page displays the system information of the device, such as the **MIB Version**, **MIB Soft**, **Equipment**, **Family Equipment**, **Update Version**, **System Time**, and **Config Language**. It also contains the **Command TX** and **Command Rearm** buttons, which allow you to switch the transmitter on/off and rearm it.

Via the **Software Versions** page button, you can access a subpage displaying the **Software Versions** table, which contains the versions of the different software parts running in the transmitter.

### Transmitter

This page displays the main transmitter functions, such as the **TX Name**, **TX Frequency**, **Frequency Number**, **Measured Power**, **Requested Power**, **Modulation Mode**, **Switchover Mode**, **Operator**, and **Exploitation** mode.

### Modulator

This page displays the modulator structure and functions, including:

- **Audio settings**: Audio mode, process, level, clipping, bandwidth, and input.
- **Modulator settings**: Physical ports, PFT configuration, phase delay, feedback adjustment, simulcast, and synchronization settings.
- **SFN settings**: SFN delay mode, time delay, delay adjustment, and compensation.
- **DRM settings**: DRM mode, spectrum occupation, interleaving, code mapping, constellations, and code rates.
- **GPS timing**: GPS antenna, PPS, PLL, satellite number, UTC offset, and SFN delay status.
- **MDI settings**: MDI input, PFT/AF layers, version, multistream, and frame buffer information.
- **Version information**: Boot loader, Linux, software, FPGA firmware, and board versions.

### Alarms

This page displays the number of active alarms and the **Alarm** table, which contains the description, status, dates, and comments of each alarm.

### Faults

This page displays the number of active faults and the **Fault 1** and **Fault 2** tables, which contain the description, status, dates, and comments of each fault.

### Modules

This page displays the number of modules and the **Module** table, which contains the description, status, dates, and comments of each module.

### Status

This page displays the global connection and hardware status of the device, as well as the **Status Global**, **Status Alarm**, **Status Fault 1**, **Status Fault 2**, and **Status Module** tables, which contain the current status and date information.

### Measurements

This page displays the **Measurement** table, which contains the measured values of the device, along with their units and update dates.

### Commands

This page allows you to control the transmitter. Available commands include switching the transmitter on/off, rearming, setting the power, frequency, date/time, language, audio mode, audio process, audio level, clipping, bandwidth, audio input, and modulation mode.

### Configuration

This page allows you to configure the modulator remotely. Available settings include the switchover mode, audio configuration, MDI configuration, PFT settings, phase delay, feedback adjustment, simulcast, synchronization, SFN settings, output settings, LAN and NTP configuration, alarm timing parameters (TDIG, TMUX, NERR), and alarm enabling settings.

### Events

This page displays the **Events** table, which contains the SNMP traps supported by the device, along with their descriptions and OIDs.

### Polling Settings

This page contains the **Polling Manager** table, which allows you to customize the polling interval of each data group, enable or disable polling, and trigger an immediate poll.
