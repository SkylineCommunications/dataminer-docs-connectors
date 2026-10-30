---
uid: Connector_help_Enensys_SmartGate_S2_S2X_Technical
description: "Configure SNMP connections, inspect transmission parameters and encapsulation workflows, and monitor alarms for Enensys SmartGate in DataMiner."
---

# Enensys SmartGate

## About

The **Enensys SmartGate** connector communicates with the **Enensys SmartGate S2/S2X** (formerly TeamCast) IP-to-satellite encapsulation gateway using SNMP. It provides comprehensive monitoring of transmission parameters, encapsulation workflows, network interfaces, and alarms.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device (default: *161*).
- **Bus address**: Not required.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when configuring values on the device (default: *public*).

## How to Use

The connector communicates with the device using SNMP to poll configuration and telemetry data. Asynchronous SNMP traps are processed to capture real-time alarm events.

### General Page

This page presents top-level operational and identity parameters:

- **Device Information**: Displays primary identity data, including the equipment **Serial Number**, **Product Type**, **Product Name** (user-assigned device label), **Hardware Version**, active **Software Version**, and system **Uptime**.
- **System Health**: Summarizes overall equipment health, including chassis **Temperature**, **Startup Status**, **Hardware Status**, **Software Status**, and configuration **Loading Process Status**.
- **Reset & Defaults**: Provides administrative controls to execute a device **Reboot** or **Restore Factory Defaults**.

### Generic Alarms Page

This page monitors hardware and environmental alarm statuses across the chassis. It displays system-wide health summaries, alarm thresholds, and navigation buttons to access dedicated subpages:

- **Temperature Alarms**: Monitors temperature sensors across internal chassis thermal zones (CPU, FPGA, power supplies). Displays current temperature values (°C), lower/upper warning thresholds, and critical temperature shutdown limits.
- **Startup Alarms**: Displays boot-time diagnostics and power-on self-test (POST) states, reporting any initialization faults detected during hardware memory validation, peripheral discovery, or boot-up execution.
- **Hardware Alarms**: Monitors physical component integrity, including internal voltage rails, power supply unit (PSU) redundancy and AC/DC power presence, cooling fan operational speeds (RPM), and fan failure alarms.
- **Software Alarms**: Tracks the health of operating system daemons, core software processes, watchdog timers, and system memory consumption, flagging unexpected process restarts or software execution faults.
- **Loading Process Alarms**: Monitors configuration file loading and deployment, alerting if configuration files cannot be parsed, contain schema syntax errors, or fail to apply to internal processing engines.
- **Internal Communication Alarms**: Monitors high-speed internal buses, PCIe interfaces, and inter-processor communication channels between host controllers, FPGAs, and modulation cards, tracking CRC errors, communication timeouts, and link failures.
- **Software Compatibility Alarms**: Validates compatibility between installed software releases, FPGA firmware bitstreams, driver versions, and hardware board revisions, flagging any detected version mismatches.
- **System Clock Alarms**: Monitors the internal reference oscillator, external 10 MHz reference clock inputs, synchronization lock states, and clock drift or unlock conditions.

### Input Streams & Services Page

This page manages transport stream ingestion and service allocation:

- **MPEG-TS Streams**: Monitors incoming MPEG Transport Streams via a tabular view displaying Stream ID, source interface, input bitrate, effective payload bitrate, lock status, packet format (188/204 bytes), sync loss counters, Continuity Counter (CC) errors, and PID mappings.
- **GSE Streams**: Displays the Generic Stream Encapsulation (GSE) table, detailing stream indexes, encapsulation protocols, target labels, MAC address filtering, protocol types (IPv4, IPv6, Ethernet), input bitrates, encapsulated output bitrates, and encapsulation efficiency metrics.
- **Virtual Channels & Components**: Displays virtual channel configurations and elementary stream components. Shows channel assignments, component PIDs (audio, video, signaling), bitrates, and routing paths to output carriers.

### Input Platforms & Interfaces Page

This page handles IP input platforms and MAC address mappings:

- **Input Platform Table**: Displays configured IP and MAC input platforms, including platform name, index, source/destination IP filtering criteria, MAC addresses, encapsulation protocol rules, platform operational states, and throughput rates.
- **Interface Mapping**: Defines associations between physical/logical network ports and input platforms, showing interface binding status, ingress routing policies, and platform enable/disable toggles.

### Processing Page

This page displays encapsulation and framing configuration:

- **BaseBand Framing (BBF)**: Displays the BBF configuration and status table, including Frame Mode (Normal 64,800 bits or Short 16,200 bits), BaseBand Header (BBHEADER) parameters, Input Stream Synchronization (ISSY) state, continuous/packetized stream modes, padding insertion, and BBF efficiency percentages.
- **Traffic Shaping**: Monitors traffic management and policing engines, displaying bandwidth reservations per service, peak and sustained bitrate policing rules, buffer occupancy levels, dropped packet counters, and PID filtering configurations.

### Output & RF Page

This page monitors satellite RF modulation output:

- **Modulation Settings**: Displays and configures transmission parameters, including standard selection (DVB-S2 or DVB-S2X), Constellation and Code Rate (MODCOD—e.g., QPSK up to 256APSK), Symbol Rate (Mbaud), Roll-off Factor (0.05 to 0.35), Pilot Insertion (on/off), and framing format.
- **RF Parameters**: Monitors physical RF output parameters, including center output frequency, RF output power level (dBm), carrier state (Carrier On, Muted, or Pure Carrier CW mode), Physical Layer Scrambling (PLS) codes (Gold code sequences or root codes), and spectrum inversion.

### Ethernet & Network Page

This page monitors physical and logical Ethernet interfaces:

- **Port Status**: Displays a table of all physical interfaces, covering management control ports (`ctrl1`, `ctrl2`) and high-speed data ports (`data1`, `data2`, `10gige3`, `10gige4`). Columns indicate administrative state (enabled/disabled), operational link state (up/down), negotiated speed (10M/100M/1G/10G), duplex mode (Full/Half), link flow control, and TX/RX packet, byte, and error counters.
- **IP Configuration**: Details network addressing parameters for each interface, including IPv4 and IPv6 addresses, subnet masks / prefix lengths, default gateways, MTU settings, VLAN IDs, and DHCP lease or static addressing modes.

### TSoIP & Protocols Page

This page monitors IP transport protocols and redundancy:

- **Transport Stream over IP**: Manages IP multicast reception of transport streams, displaying multicast group addresses, source-specific multicast (SSM) addresses, UDP/RTP ports, jitter buffer depth, and SMPTE 2022-1/2 Forward Error Correction (FEC) matrix parameters (column/row configurations, FEC overhead, packet recovery count, and uncorrectable packet counters).
- **VRRP Redundancy**: Displays Virtual Router Redundancy Protocol (VRRP) status, including router ID, operational state (Master, Backup, or Init), configured priority, virtual IP address bindings, advertisement intervals, and preemption mode.

### System & Maintenance Page

This page provides maintenance and administrative utilities:

- **Maintenance Tools**: Provides controls for configuration management (backup and restore of configuration files), dual-bank firmware image selection, active/standby partition switching, diagnostic log file exports, and system reboot triggers.
- **Time Synchronization**: Displays Network Time Protocol (NTP) client status, primary/secondary NTP server addresses, synchronization lock state, stratum level, clock offset, jitter, local time zone, and current UTC system time.

### Device Alarms Page

This page lists active equipment alarms generated directly by device subsystems. The table details:

- **Alarm Index**: Unique identifier for the active alarm instance.
- **Alarm ID & Subsystem**: The specific hardware or software subsystem originating the alarm (e.g., Modulation, Power, Network, GSE).
- **Severity**: Alarm level indicator (Critical, Major, Minor, Warning, Information).
- **Description**: Textual explanation of the fault condition.
- **Timestamp**: Time and date when the alarm condition was raised.

### Notification Page

This page displays asynchronous SNMP trap notifications received by the connector:

- Displays real-time event notifications received from the device, including the last received trap timestamp, Trap OID, Trap Name, alarm description, severity level, supervised OID value, and notification sequence number.
- Includes a **Reset Trap Counters** control to clear received trap history and reset notification counters for ongoing operational monitoring.

## Notes

- Supports firmware version 3.1.1.
