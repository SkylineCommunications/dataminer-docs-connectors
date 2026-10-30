---
uid: Connector_help_Tandberg_TT6120_Technical
description: "Monitor Tandberg TT6120 transport stream processor boards, transport streams, carried services, demodulators, and ATM interfaces in DataMiner."
---

# Tandberg TT6120

## About

The Tandberg TT6120 is a modular 1RU transport stream processor that converts MPEG transport streams between DVB ASI, satellite/cable/terrestrial RF, IP, G.703, and ATM interfaces, with PID, component, and service filtering and PSI/SI/PSIP table handling.

This SNMP connector gives you real-time visibility into the unit's installed boards, incoming and outgoing transport streams, carried services and components, satellite demodulator status, and ATM receive/transmit interfaces, without logging in to the device.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

No additional initialization is required. The connector starts polling as soon as the element is created.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page shows general parameters related to the unit identity, as well as network settings. In addition, the **Summary Alarm** and **Configuration Status** parameters give the overall device health at a glance. **Default PID Handling** shows how PIDs not covered by a filtering rule are treated.

The **MMI Alarms** page button opens the status of the front panel (MMI) display, interface, and configuration. The **Board Info** page button opens the **BoardList Table**, which shows every installed board with its slot number, board type, channel number, serial number, board description, and software, hardware, PLD, and Xilinx firmware versions.

### Services Page

The **Ts Service Overview** table lists every service carried in the transport stream with its PCR PID and PMT PID. The **Ts Component Overview** table lists the individual elementary stream components and their PIDs. **PSI/SI Analyse** indicates whether table analysis is active.

The **Service Handling Information** and **PSI/PS Info** page buttons open detail tables for service handling rules and PSI/SI table information.

### Transport Stream Page

This page allows you to monitor the TS input and output per slot.

### Demodulator Page

This page shows the satellite demodulator board state, including **LNC Voltage**, **LNC Frequency**, and **Satellite Frequency**, as well as sync indicators such as **Carrier**, **Clock**, and **Frame**.

The **More Demodulator Settings** page button exposes the tuner frequency range and step, and the **LNC 22 kHz Tone** setting.

### ATM Information Page

This page displays the ATM receive (Rx) and transmit (Tx) interface status.

### Web Interface Page

This page shows the on-board web server of the TT6120 using the element's polling IP.
