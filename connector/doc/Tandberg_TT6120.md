---
uid: Connector_help_Tandberg_TT6120
description: "Monitor Tandberg TT6120 transport stream processor boards, transport streams, carried services, demodulators, and ATM interfaces in DataMiner."
---

# Tandberg TT6120

## About

The Tandberg TT6120 is a modular 1RU transport stream processor that converts MPEG transport streams between DVB ASI, satellite/cable/terrestrial RF, IP, G.703, and ATM interfaces, with PID, component, and service filtering and PSI/SI/PSIP table handling.

This SNMP connector gives you real-time visibility into the unit's installed boards, incoming and outgoing transport streams, carried services and components, satellite demodulator status, and ATM receive/transmit interfaces, without logging in to the device.

## Key Features

- **Transport stream monitoring**: input and output bit rate, effective bit rate, packet length, interface, output mode and alarm status per slot.
- **Service and component overview**: all services in the stream with their PCR and PMT PIDs, plus the individual components and PSI/SI analysis.
- **Demodulator supervision**: LNC voltage and frequency, satellite frequency, symbol rate, inner code, BER, AGC level and sync status.
- **ATM Rx/Tx interface status**: cell rate, cell discard, HEC sync/correction, MPEG sync, PDH framing and VPI/VCI per interface.
- **Chassis inventory**: board list with slot, type, serial number, and software, hardware, PLD and Xilinx firmware versions.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Tandberg_TT6120_Technical).
