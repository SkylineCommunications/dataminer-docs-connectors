---
uid: Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9001
---

# Cobalt Digital HPF 9000 - Cobalt Digital 9001

## About

This is an exported Derived Virtual Element (DVE) representing a Cobalt Digital 9001 openGear card. It is created on demand from the parent [Cobalt Digital HPF 9000](xref:Connector_help_Cobalt_Digital_HPF_9000) frame connector and exposes the card's data, including temperature, voltage, and the frame slot in which the card is inserted.

## Configuration

### Connections

This element is created by the parent **Cobalt Digital HPF 9000** connector through the DVE toggle on the Slots table. No additional configuration is needed.

### Initialization

This exported element is defined by the 9001 card table of the parent **Cobalt Digital HPF 9000** connector.

## How to use

This dynamic virtual element is created by toggling DVE creation for a 9001 card in a slot on the parent connector. Its **General** and **Status** pages display the card's parameters. The element updates as long as the card's display remains enabled on the parent's Card Display page.
