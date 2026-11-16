---
uid: Connector_help_Tandberg_TT1222_SNMP
description: "Monitor the Tandberg TT1222 MPEG-2 integrated receiver decoder in DataMiner through SNMP traps for input lock, video, audio, data, and BER alarms."
---

# Tandberg TT1222 SNMP

## About

The **Tandberg TT1222 SNMP** connector integrates the Tandberg TT1222 MPEG-2 standard definition integrated receiver decoder (IRD) into DataMiner. The TT1222 receives DVB satellite (QPSK) or ASI transport streams, decrypts and decodes the selected service, and outputs it as analog or SDI video with analog or digital audio. It is widely used in cable and satellite headends for channel turnaround and redistribution.

This connector listens to the **SNMP traps** that the TT1222 sends when its reception, decoding, or data path changes state, and turns them into DataMiner alarms with the severity reported by the device. Headend operators can see at a glance which decoder lost its input, which output has a video or audio problem, and where the bit error rate is too high, without logging in to each unit.

## Key Features

- **Input lock supervision**: A trap-driven **No Input Lock** status flags a decoder that no longer locks onto its satellite or ASI input.
- **Video and audio decoding status**: Separate **Video**, **Audio 1**, and **Audio 2** error states point directly to the affected output.
- **Data path and BER monitoring**: **Data Error** and **BER Exceeded** states warn when the data channel fails or the bit error rate crosses the device threshold.
- **Device-reported severity**: Each trap carries the severity assigned by the TT1222, which the connector maps to the DataMiner alarm level.
- **Trap destination management**: Read and set the **TrapServer** IP address of the device, so that the unit can be pointed to the DataMiner Agent from the element itself.

## Use Cases

### Spotting a Lost Feed Across a Fleet of Decoders

**Challenge**: A headend with dozens of TT1222 units needs to know immediately which decoder lost its satellite or ASI input, before the downstream channel goes black.

**Solution**: Every TT1222 sends a trap to DataMiner as soon as input lock is lost or restored. The connector turns this into a **No Input Lock** alarm on the right element, with the severity reported by the device.

**Benefit**: Operators are alerted per decoder, instead of having to discover the outage on a monitoring wall or in a customer complaint.

### Separating Reception Problems from Decoding Problems

**Challenge**: When a channel has a picture or sound problem, it is not always clear whether the cause is a weak signal or a decoding fault.

**Solution**: The connector shows **BER Exceeded** and **No Input Lock** separately from **Video**, **Audio 1**, **Audio 2**, and **Data** errors, so the reception and decoding stages can be told apart.

**Benefit**: Faults are routed to the right team, RF or video, the first time.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Tandberg_TT1222_SNMP_Technical).
