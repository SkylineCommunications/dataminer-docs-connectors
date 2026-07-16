---
uid: Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9121
---

# Cobalt Digital HPF 9000 - Cobalt Digital 9121

## About

This is an exported Dynamic Virtual Element (DVE) representing a Cobalt Digital 9121 openGear card. It is created on demand from the parent [Cobalt Digital HPF 9000](xref:Connector_help_Cobalt_Digital_HPF_9000) frame connector and exposes the card's data and the frame slot in which the card is inserted.

## Configuration

### Connections

This element is created by the parent **Cobalt Digital HPF 9000** connector through the DVE toggle button in the Slots table. No additional configuration is needed.

### Initialization

This exported element is defined by the 9121 card table of the parent **Cobalt Digital HPF 9000** connector.

## How to use

This dynamic virtual element is created by toggling DVE creation for a 9121 card in a slot on the parent connector. Its **General** and **Status** pages display the card's parameters. The element updates as long as the card is set to be displayed on the Card Display page of the parent element.
