---
uid: Connector_help_ZTE_ZXA10_C600_Technical
description: "Learn how to configure and use the ZTE ZXA10 C600 connector to monitor OLT chassis health, optical links, and subscriber interfaces."
---

# ZTE ZXA10 C600 Technical

## About

The **ZTE ZXA10 C600** connector monitors and manages ZTE ZXA10 C600 GPON OLT chassis via SNMPv2. It provides real-time visibility into chassis health, board/power status, uplink optical status, and GPON/XGS-PON/Ethernet interfaces.

## Configuration

### Connections

#### SNMP Connection — Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

### General Page

Two key parameters are included on this page:

- **DisplayKey Config**: If you have write permission, this parameter allows you to select the format for the Display Key column in the following tables: Ethernet Interfaces, PON Interfaces, PON Interfaces Status, and Optic Status. The available options use the information extracted from the IfTable and IfXTable (ifDescription, IfName, IfAlias) and combine these in different ways:

  - Alias
  - Name
  - Alias + Name
  - Name + Alias

- **DisplayKey Separator**: Works together with the DisplayKey Config parameter to fully customize the row identifier.

For example, imagine the interface identifiers have the following values:

- Alias: `My Interface`
- Description: `Test Interface`
- Name: `Interface01`

The table below shows the possible display key format, depending on the selected options:

| Separator (Quotes are ignored) | Alias | Name | Alias+Name | Description+Alias | Name+Alias |
|---|---|---|---|---|---|
| `-` | MyInterface | Interface01 | MyInterface-Interface01 | Test Interface-MyInterface | Interface01-MyInterface |
| ` - ` | MyInterface | Interface01 | MyInterface - Interface01 | Test Interface - MyInterface | Interface01 - MyInterface |
| `/` | MyInterface | Interface01 | MyInterface/Interface01 | Test Interface/MyInterface | Interface01/MyInterface |

> [!TIP]
> Try to use separators that are not included in any of the interface identification fields. This allows easier searching for alarm or trend information.

### Board & Power Pages

These pages display tables with the board temperature, board power, power module, and CPU/system status. This information is polled using the "Medium Timer (5m) Regular SNMP" timer.

### Uplink Optical Page

This page displays the Uplink Optical (SFP) table, including Rx/Tx optical power and (since v1.0.2.4) SFP power thresholds.

### GPON / XGS-PON Pages

This page displays the GPON Interfaces, GPON Channels, XGS-PON Channels, and PON Interface Status tables.

### LLDP Page

This page displays the LLDP local port and remote neighbor tables, polled using the "Medium Timer (6m)" timer.
