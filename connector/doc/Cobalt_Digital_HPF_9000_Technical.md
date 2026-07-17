---
uid: Connector_help_Cobalt_Digital_HPF_9000_Technical
---

# Cobalt Digital HPF 9000

## About

This is a DataMiner connector for the Cobalt Digital HPF 9000, a modular openGear frame controller. The connector monitors the frame chassis (power, network, and frame status), maintains an inventory of the openGear cards installed in the frame's slots, and can export a dedicated Dynamic Virtual Element (DVE) for each active card.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the frame controller.
- **IP port**: The SNMP port of the device (default SNMP port: *161*, unless configured otherwise).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The device web interface is reachable from the element via the **Web Interface** page link. It is only accessible when the client machine has network access to the frame.

## How to use

### General

This page displays the frame supplier and general frame identity, along with **System Info** parameters (System Description, Uptime, Contact, and Location) read from the SNMP MIB-II system group. The page was designed to mirror the device web interface layout.

### Frame Status

This page displays the overall frame status information.

### Network

This page displays the frame's network configuration.

### Power

This page displays the frame's power supply parameters.

### Slots

This page contains the **Slots Overview** table. This is the master inventory listing every frame slot with the card detected in it. A toggle button per slot allows you to create or delete that card's child element. Buttons are available to delete an individual DVE or to clear all DVEs.

### Card Display

This page controls which card types are shown and polled:

- **Card Display Auto-Detect** (master, default *Enabled*): This option automatically enables only the card types present in the frame, based on the slot scan, and locks the manual toggles. Set it to *Disabled* to control the per-card toggles manually.
- **Per-card toggles** (9001, 9121, 9410DA, 9220): With these toggle options per card you can show or hide the corresponding card page, keeping cards from being polled when this is not necessary. When a card is disabled, its page is hidden and its polling stops (no SNMP requests are sent for it).

### 9001 / 9121 / 9410DA / 9220

These pages display the data of each detected card type. The 9410DA page contains page buttons to **9410DA Routing**, **9410DA Coax Routing**, and **9410DA Fiber Routing** subpages; the 9220 page contains page buttons to **IP**, **Connectivity**, **Licensing**, and **Admin** subpages.

## Exported DVE cards

Each active card can be exported as a DVE child element. Each exported card type has its own documentation page:

- [Cobalt Digital 9001](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9001)
- [Cobalt Digital 9121](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9121)
- [Cobalt Digital 9410DA](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9410DA)
- [Cobalt Digital 9220](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9220)
