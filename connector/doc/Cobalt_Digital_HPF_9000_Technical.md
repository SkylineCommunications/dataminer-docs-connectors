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
- **Per-card toggles** (9001, 9121, 9410DA, 9220, 9911, 9902, 9934): With these toggle options per card you can show or hide the corresponding card page, keeping cards from being polled when this is not necessary. When a card is disabled, its page is hidden and its polling stops (no SNMP requests are sent for it).

### 9001 / 9121 / 9410DA / 9220 / 9911 / 9902-UDX / 9934

These pages display the data of each detected card type. The 9410DA page contains page buttons to **9410DA Routing**, **9410DA Coax Routing**, and **9410DA Fiber Routing** subpages. The 9220 page contains page buttons to **IP**, **Connectivity**, **Licensing**, and **Admin** subpages; the 9902-UDX and 9934 pages contain page buttons to their audio input, output, and status subpages.

On the 9902-UDX and 9934 audio pages, the per-group SNMP audio array tables are consolidated into single per-function tables, and the source, gain, mute, invert, flex bus, and delay offset columns are writable; changes are written back to the card over SNMP.

## Exported DVE cards

Each active card can be exported as a DVE child element. Each exported card type has its own documentation page:

- [Cobalt Digital 9001](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9001)
- [Cobalt Digital 9121](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9121)
- [Cobalt Digital 9410DA](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9410DA)
- [Cobalt Digital 9220](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9220)
- [Cobalt Digital 9911DA-8-BPX](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9911DA-8-BPX)
- [Cobalt Digital 9902-UDX](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9902-UDX)
- [Cobalt Digital 9934-AUD-PRO-DSP](xref:Connector_help_Cobalt_Digital_HPF_9000_-_Cobalt_Digital_9934-AUD-PRO-DSP)

## Supported Device Versions

The connector was developed and verified against the following device software revisions:

| Device | Software revision |
|---|---|
| HPF-9000 Frame Controller (HPF-FC) | 4.0 |
| Cobalt Digital 9410DA | 1.2.11 |
| Cobalt Digital 9220 (MVN-MX260) | 1.3.3 |
| Cobalt Digital 9911DA-8-BPX | 1.151 |
| Cobalt Digital 9902-UDX | 2.098 |
| Cobalt Digital 9934-AUD-PRO-DSP | 2.116 |
