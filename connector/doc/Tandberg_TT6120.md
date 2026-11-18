---
uid: Connector_help_Tandberg_TT6120
description: "Monitor the Tandberg TT6120 transport stream processor over SNMP, including boards, transport streams, services, demodulators, and ATM interfaces."
---

# Tandberg TT6120

## About

The **Tandberg TT6120** connector integrates the Tandberg TT6120 transport stream processor into DataMiner over SNMP. The TT6120 is a modular transport stream processor that converts transport streams between ASI, satellite RF, IP, G.703, and ATM interfaces, with PID, component, and service filtering.

This connector gives headend operators a single view of the unit's **boards, transport streams, services, demodulators, and ATM interfaces**. It exposes the processor's MMI alarms and per-component status, so that faults in the incoming or outgoing transport stream can be spotted and attributed to the right slot, service, or component.

## Key Features

- **Monitor transport stream services and components**: Track every service, its PCR and PMT PIDs, and the individual components carried in the stream, including their type, bit rate, and language.
- **Supervise satellite demodulators**: Monitor LNC voltage and frequency, satellite frequency, symbol rate, inner code, BER, and AGC level per demodulator slot, together with the clock, carrier, Viterbi, and frame sync status.
- **Inventory the chassis**: See every installed board at a glance, including its slot, type, serial number, and software, hardware, PLD, and Xilinx firmware versions.
- **Track ATM Rx/Tx interfaces**: View the ATM receive and transmit slots, their VPI/VCI configuration, cell and MPEG rates, HEC and MPEG sync, and PDH framing status.
- **Monitor transport stream input and output per slot**: Follow the bit rate, effective bit rate, packet length, output interface, and alarm status of the selected slot.

## Use Cases

### Attributing a Transport Stream Fault to the Right Slot

**Challenge**: When a downstream service drops, operators need to know quickly whether the problem is on the incoming feed, in the processor, or on the output interface.

**Solution**: The connector shows the input and output alarm status and bit rates for the selected slot, the demodulator sync and BER, and the ATM sync status in one element, on the Transport Stream, Demodulator, and ATM Information pages.

**Benefit**: Isolate faults to a specific slot and stage of the signal path from DataMiner, without any need to open the interface of the device.

### Keeping an Up-to-Date Inventory of TT6120 Units

**Challenge**: Headends with several TT6120 chassis need to know which boards and firmware versions are installed in each unit.

**Solution**: The board list can be retrieved on demand and shows the board type, serial number, and all firmware versions per slot.

**Benefit**: Base your spare-part planning and firmware upgrades on actual, centrally available inventory data.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Tandberg_TT6120_Technical).
