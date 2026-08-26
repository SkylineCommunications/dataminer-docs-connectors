---
uid: Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9220
---

# Cobalt Digital HPF 9000 - Cobalt Digital 9220

## About

This is an exported Dynamic Virtual Element (DVE) representing a Cobalt Digital 9220 (MVN-MX260) openGear card. It is created on demand from the parent [Cobalt Digital HPF 9000](xref:Connector_help_Cobalt_Digital_HPF_9000) frame connector and exposes the card's product information, network interface, ASI port, IP input/output, connection, license status, and admin data, along with the frame slot in which the card is inserted.

## Configuration

### Connections

This element is created by the parent **Cobalt Digital HPF 9000** connector through the DVE toggle button in the Slots table. No additional configuration is needed.

### Initialization

This exported element is defined by the 9220 card tables of the parent **Cobalt Digital HPF 9000** connector.

## How to use

This dynamic virtual element is created by toggling DVE creation for a 9220 card in a slot on the parent connector. Its pages display the card's product information, network and ASI port configuration, IP input/output, connection status, and licensing. The element updates as long as the card is set to be displayed on the Card Display page of the parent element.
