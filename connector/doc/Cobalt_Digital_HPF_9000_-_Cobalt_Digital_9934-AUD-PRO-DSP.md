---
uid: Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9934-AUD-PRO-DSP
---

# Cobalt Digital HPF 9000 - Cobalt Digital 9934-AUD-PRO-DSP

## About

This is an exported Dynamic Virtual Element (DVE) representing a Cobalt Digital 9934-AUD-PRO-DSP (Audio Processor with DSP) openGear card. It is created on demand from the parent [Cobalt Digital HPF 9000](xref:Connector_help_Cobalt_Digital_HPF_9000) frame connector and exposes the card's audio processing data, along with the frame slot in which the card is inserted.

The connector consolidates the card's per-group SNMP audio array tables into single per-function tables, so each audio function is presented as one table covering all channels.

## Configuration

### Connections

This element is created by the parent **Cobalt Digital HPF 9000** connector through the DVE toggle button in the Slots table. No additional configuration is needed.

### Initialization

This exported element is defined by the 9934-AUD-PRO-DSP card tables of the parent **Cobalt Digital HPF 9000** connector.

## How to use

This dynamic virtual element is created by toggling DVE creation for a 9934-AUD-PRO-DSP card in a slot on the parent connector. Its pages cover:

- **Input Audio Delay**: Auto adjust delay per DSP channel, with a writable delay offset and an auto adjust delay toggle.
- **Input Bus** and **Input Flex Mix**: Input bus and flex mix source routing, with writable source, gain, mute, and invert controls. Sources include the card's 64 audio DSP channels.
- **Output Audio Routing/Controls**, **AES Output**, **Analog Output**, and **Output Flex Mix**: Embedded, AES, analog, and flex-mix output routing, with writable source, gain, mute, invert, and flex bus controls.
- **Input Audio Status**: Embedded, AES, and analog input audio status.

Values changed on these tables are written back to the card over SNMP. The element updates as long as the card is set to be displayed on the Card Display page of the parent element.
