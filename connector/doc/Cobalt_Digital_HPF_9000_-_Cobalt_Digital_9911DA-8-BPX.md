---
uid: Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9911DA-8-BPX
---

# Cobalt Digital HPF 9000 - Cobalt Digital 9911DA-8-BPX

## About

This is an exported Dynamic Virtual Element (DVE) representing a Cobalt Digital 9911DA-8-BPX (Dual Input 1x8 Reclocking Distribution Amplifier) openGear card. It is created on demand from the parent [Cobalt Digital HPF 9000](xref:Connector_help_Cobalt_Digital_HPF_9000) frame connector and exposes the card's product identification, temperature and power readings, input and failover status, reclocker and output status, and event log, along with the frame slot in which the card is inserted.

## Configuration

### Connections

This element is created by the parent **Cobalt Digital HPF 9000** connector through the DVE toggle button in the Slots table. No additional configuration is needed.

### Initialization

This exported element is defined by the 9911DA-8-BPX card table of the parent **Cobalt Digital HPF 9000** connector.

## How to use

This dynamic virtual element is created by toggling DVE creation for a 9911DA-8-BPX card in a slot on the parent connector. Its **General** page displays the card identity (including a writable custom card name) and slot details, and its **Status** page displays the card health and signal status alongside the event log. The element updates as long as the card is set to be displayed on the Card Display page of the parent element.
