---
uid: Connector_help_Tandberg_TT6120_Technical
description: Configure and use the Tandberg TT6120 connector: SNMP connection settings, slot selection for transport stream, demodulator, and ATM data.
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

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The general device information and the service and component tables are polled as soon as the element is created.

The slot-specific data is only polled after you select a slot number on the corresponding page:

- On the **Transport Stream** page, select the **TS Slot Number** of the board you want to monitor.
- On the **Demodulator** page, select the **Demodulator Slot Number** of the satellite demodulator board.
- On the **ATM Information** page, select the **ATM Rx Slot Number** and the **ATM Tx Slot Number** of the ATM boards.

Until a slot is selected, the parameters on that page remain empty.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

All device data is retrieved via SNMP polling. The device does not send traps to the connector.

### Monitoring a specific board

The TT6120 is a modular chassis, and the connector polls one slot at a time for each board type. Select the slot number on the **Transport Stream**, **Demodulator**, or **ATM Information** page to switch the monitored board. The parameters on that page are then refreshed for the selected slot. Only the selected slot is polled, so to compare several slots of the same type, you have to switch the slot selection.

The input selection and most output settings of the transport stream board, the tuning settings of the demodulator, and the VPI/VCI, output selection, cell discard, HEC correction, and payload scrambler settings of the ATM interfaces can be changed from these pages.

### Retrieving the board inventory and PSI/SI details

Some overviews are not polled continuously, in order to limit the load on the device. They are retrieved on demand with a **Load** button:

- **Board Info** subpage (page button on the **General** page): Click **Load** to retrieve the board list, with the slot number, board type, channel number, serial number, software, hardware, PLD, and Xilinx firmware versions, and the description of each installed board.
- **Service Handling Information** subpage (**More Info** page button on the **Services** page): Click **Load** to retrieve the handling state of each service per slot and port.
- **PSI/PS Info** subpage (page button on the **Services** page): Click **Load** to retrieve the type, repetition rate, and mode of each PSI/SI table.

### Following the services in the stream

The **Services** page shows the services detected in the transport stream, with their PCR and PMT PIDs, and the individual components (PIDs) with their type, bit rate, and language and the service they belong to. The default PID and service handling and the PSI/SI analysis can be configured on the **General** and **Services** pages.

### Alarms

The **General** page shows the **Summary Alarm** of the device. The **MMI Alarms** subpage (page button on the **General** page) breaks this down into the MMI configuration, configuration status, display, and interface alarms. In addition, the transport stream, demodulator, and ATM pages show the alarm and sync status of the selected slot.
