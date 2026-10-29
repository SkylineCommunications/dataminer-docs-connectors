---
uid: Connector_help_Tandberg_TT6120
---

# Tandberg TT6120

The Tandberg TT6120 is a modular 1RU transport stream processor that converts MPEG transport streams between DVB ASI, satellite/cable/terrestrial RF, IP, G.703 and ATM interfaces, with PID, component and service filtering and PSI/SI/PSIP table handling.

This is an **SNMP** connector that is used to monitor the boards, transport streams, services, demodulators and ATM interfaces of a Tandberg TT6120.

## About

The connector gives you real-time visibility into the unit's installed boards, incoming and outgoing transport streams, carried services and components, satellite demodulator status, and ATM receive/transmit interfaces, without logging in to the device.

### Key Features

- **Transport stream monitoring**: input and output bit rate, effective bit rate, packet length, interface, output mode and alarm status per slot.
- **Service and component overview**: all services in the stream with their PCR and PMT PIDs, plus the individual components and PSI/SI analysis.
- **Demodulator supervision**: LNC voltage and frequency, satellite frequency, symbol rate, inner code, BER, AGC level and sync status.
- **ATM Rx/Tx interface status**: cell rate, cell discard, HEC sync/correction, MPEG sync, PDH framing and VPI/VCI per interface.
- **Chassis inventory**: board list with slot, type, serial number, and software, hardware, PLD and Xilinx firmware versions.

### Prerequisites

- DataMiner 10.3.0.0 (build 12752) or higher.
- SNMP access from the DataMiner Agent to the TT6120 management interface.

## Installation and configuration

### Creation

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

No additional initialization is required. The connector starts polling as soon as the element is created.

## Usage

### General

Shows the unit identity and network settings: **Model Number**, **MIB Version**, **TCF Version**, **IP Address**, **Subnet Mask**, **Gateway Address**, **MAC Address** and **Use of BootP**.

The **Summary Alarm** and **Configuration Status** parameters give the overall device health at a glance. **Default PID Handling** shows how PIDs not covered by a filtering rule are treated.

The **MMI Alarms** page button opens the status of the front panel (MMI) display, interface and configuration. The **Board Info** page button opens the **BoardList Table**, which shows every installed board with its slot number, board type, channel number, serial number, board description, and software, hardware, PLD and Xilinx firmware versions.

### Services

The **Ts Service Overview** table lists every service carried in the transport stream with its PCR PID and PMT PID. The **Ts Component Overview** table lists the individual elementary stream components and their PIDs. **PSI/SI Analyse** indicates whether table analysis is active.

The **Service Handling Information** and **PSI/PS Info** page buttons open detail tables for service handling rules and PSI/SI table information.

### Transport Stream

Monitors the TS input and output per slot: **TS Input Selection**, **Port Number**, **Bit Rate**, **Effective Bitrate**, **Packet Length** and **Alarm Status** on the input side; **TS Output Interface**, **Mode**, **Rate**, **Effective Bitrate**, **Packet Length**, **External Clock**, **Backplane TS ID** and **Alarm Status** on the output side.

### Demodulator

Shows the satellite demodulator board state: **LNC Voltage**, **LNC Frequency**, **Satellite Frequency**, **Symbol Rate**, **Inner Code**, **Tuner Type**, **Spectral Invertion**, **BER**, **AGC Level** and the sync indicators (**Carrier**, **Clock**, **Frame**, **Viterbi Sync**, **Absence RF**, **BER above 10e-4**).

The **More Demodulator Settings** page button exposes the tuner frequency range and step and the **LNC 22kHzTone** setting.

### ATM Information

Lists the ATM receive (**Rx**) and transmit (**Tx**) interface status: **Slot Number**, **Cell Rate**, **Cell Discard**, **HEC Sync**, **HEC Correction**, **MPEG Sync**, **Mpeg Rate**, **PDH Framing**, **PDH Local**, **PDH Remote**, **G703 Signal**, **Payload Scrambler**, **Virtual Path Identifier** and **Virtual Channel Identifier**.

### Web Interface

Opens the on-board web server of the TT6120 using the element's polling IP.

The web interface is only accessible when the client machine has network access to the product.
