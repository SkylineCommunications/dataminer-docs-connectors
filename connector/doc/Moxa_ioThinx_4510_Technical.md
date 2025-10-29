---
uid: Connector_help_Moxa_ioThinx_4510_Technical
---

# Moxa ioThinx 4510

The Moxa ioThinx 4510 Series is an advanced I/O and Ethernet network adapter featuring 3-in-1 serial ports and a rugged design built to operate reliably in temperatures ranging from –20°C to 60°C.

## Supported Modules

The following modules are supported by the Moxa ioThinx 4510 Connector (Firmware Version: **V1.5.0_Build22060217**):

|Module Type|Model(s)|Description|
|---|---|---|
|Digital Input|45MR-1600 / 1601|16 digital inputs (DI)|
||45MR-2606|8 digital inputs (DI) + 8 digital outputs (DO)|
|Digital Output|45MR-2600 / 2601|16 digital outputs (DO)|
|Relay Output|45MR-2404|4 relay outputs|
|Analog Input|45MR-3800 / 3810|8 analog inputs (AI)|
|Analog Output|45MR-4420|4 analog outputs (AO)|
|RTD|45MR-6600|6 RTD channels|
|Thermocouple|45MR-6810|8 thermocouple (TC) channels|
|Power|45MR-7210|System and field power input module|
|Field Power Expansion|45MR-7820|8 FP+ and 8 FP– terminals for field power|

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

This connector uses SNMP polling to periodically retrieve data from the device and distribute it across the General, System Parameters, Digital I/O, Relay, and Analog I/O pages. Configuration is straightforward and requires only that the SNMP parameters are correctly set in the element’s edit menu. If the element enters a timeout state after configuration, please verify network connectivity to the device and ensure that the SNMP service is enabled under Service Settings on the Security page of the device’s web interface.