---
uid: Connector_help_Tandberg_TT6120_Technical
description: Configure and use the Tandberg TT6120 connector, including the SNMP connection, slot selection per board type, and the configuration status workflow.
---

# Tandberg TT6120

## About

The Tandberg TT6120 is a modular transport stream processor that converts transport streams between ASI, satellite RF, IP, G.703, and ATM interfaces, with PID, component, and service filtering.

This connector retrieves information from the device via SNMP. It monitors the installed boards, the transport stream input and output of a selected slot, the services and components carried in the stream, the satellite demodulators, and the ATM receive and transmit interfaces.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The general device information and the service and component tables are polled as soon as the element is created.

The slot-specific data is only polled after you select a slot number on the corresponding page:

- On the **Transport Stream** page, select the **TS Slot Number** of the board you want to monitor.
- On the **Demodulator** page, select the **Demodulator Slot Number** of the satellite demodulator board.
- On the **ATM Information** page, select the **ATM Rx Slot Number** and the **ATM Tx Slot Number** of the ATM boards.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

All device data is retrieved via SNMP polling; the connector does not process traps. The element has a **General** page and a **Services** page for the unit as a whole, and one page per board type (**Transport Stream**, **Demodulator**, and **ATM Information**).

### General page

This page shows the network settings, model number, and MIB and TCF versions of the unit, together with the **Summary Alarm**, which reflects the state of the device as a whole and is the first indicator to check when something is wrong.

The **MMI Alarms** subpage shows the state of the front panel (man-machine interface): whether the configuration was changed locally, whether that configuration is valid, whether the display is locked, and whether an input board is fitted. The device MIB advises against accessing the device while the display is locked.

The **Board Info** subpage lists the boards installed in the chassis, with their type, serial number, and firmware versions. This list is not polled continuously, so click **Load** to refresh it, for example after a board has been replaced.

Two settings on this page need particular care:

- **Reset** restarts the device itself, not the element.
- **Configuration Status** and **TS Configuration Status** are part of the configuration workflow of the device (see [Changing settings](#changing-settings)). Do not change them unless you are applying a configuration change.

### Services page

This page shows the services and components that the device detects in the transport stream, independently of the selected slot. Use it to verify that the expected services are present and that their PIDs and bit rates are as expected. The **Default Service Handling** and **PSI/SI Analyse** settings on this page control the default handling of services and whether the device analyzes the PSI/SI tables at all. As the service and component information depends on that analysis, check the **PSI/SI Analyse** setting first when these tables stay empty.

Two subpages are retrieved on demand with a **Load** button, to limit the load on the device: **Service Handling Information** (via the **More Info** page button) shows how each service is handled per slot and port, and **PSI/PS Info** shows the PSI/SI tables and their repetition rates. The data on these subpages reflects the moment you clicked **Load**, so reload it before drawing conclusions.

### Transport Stream, Demodulator, and ATM Information pages

Each of these pages monitors one board of the corresponding type. You first have to select the slot number at the top of the page. The connector polls only the selected slot, so when the chassis contains several boards of the same type, you can only follow one of them at a time, and switching the slot replaces the displayed data. Keep this in mind when alarm templates or trending are configured on these parameters, as they refer to whichever slot is selected at that moment.

- On the **Transport Stream** page, watch the input and output alarm status. A large difference between the bit rate and the effective bit rate means that the stream mainly carries null packets.
- On the **Demodulator** page, check the demodulator alarm bits (absence of RF, BER above 10e-4, no frame sync) first, and then the clock, carrier, Viterbi, and frame sync parameters to see how far the demodulator has locked onto the satellite signal. A loss of lock or a rising BER typically indicates an RF or tuning problem rather than a transport stream problem. The extended tuner limits are available on the **More Settings** subpage.
- On the **ATM Information** page, the receive and transmit slots are selected separately. Check the HEC and MPEG sync and PDH framing status before looking at the cell and MPEG rates.

### Changing settings

The input selection and output settings of the transport stream board, the tuning settings of the demodulator, and the VPI/VCI, output selection, cell discard, HEC correction, and payload scrambler settings of the ATM interfaces can be changed from the corresponding pages. A setting is only sent to the device when a slot is selected on that page; otherwise, the change is ignored.

According to the device MIB, the TT6120 applies configuration changes as a transaction: set the **Configuration Status** (or the **TS Configuration Status** for transport stream settings) on the **General** page to *In Progress*, change the settings, and then set it to *Complete* (*Update Complete* for the TS Configuration Status) to activate them. For the Configuration Status, the device reverts to the previous values if it does not accept the new configuration. Check the resulting status after a change to confirm that it is *Active*.

### Webinterface page

This page embeds the web interface of the device, which you can use for settings that are not exposed by the connector.
