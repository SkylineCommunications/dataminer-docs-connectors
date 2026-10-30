---
uid: Connector_help_Tandberg_TT6120
description: Monitor the Tandberg TT6120 Transport Stream Processor in DataMiner over SNMP, including boards, transport streams, services, demodulators, and ATM interfaces.
---

# Tandberg TT6120

The Tandberg TT6120 is a modular 1RU transport stream processor that converts transport streams between ASI, satellite RF, IP, G.703, and ATM interfaces, with PID, component, and service filtering.

This connector retrieves information from the device via SNMP. It provides a single view of the installed boards, the transport stream input and output of a selected slot, the services and components carried in the stream, the satellite demodulators, and the ATM receive and transmit interfaces.

## About

### Version Info

| Range                | Key Features                                                                                                                              | Based on | System Impact |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------|----------|---------------|
| 1.1.0.x [Obsolete]   | Initial version.                                                                                                                          | -        | -             |
| 1.1.1.x [SLC Main]   | Tables migrated to the newer table format, board list QAction converted to C#, **TCF Version** parameter made visible on the General page. | 1.1.0.5  | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.1.0.x | -                  |
| 1.1.1.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.1.0.x | No              | No                  | -                 | -                   |
| 1.1.1.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: This is not required.

SNMP Settings:

- **Port number**: The port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

### Initialization

Range 1.1.1.x of this connector requires DataMiner version **10.3.0.0 - 12752** or higher.

No further configuration is required. The general device information is polled as soon as the element is created. Polling of the slot-specific data (transport stream, demodulator, and ATM interfaces) only starts after you select a slot number on the corresponding page, as described below.

## How to use

The element consists of the following data pages:

- **General**: Displays the network configuration of the device (**IP Address**, **Subnet Mask**, **Gateway Address**, **MAC Address**, and **Use of BootP**), as well as the **MIB Version**, **Model Number**, **TCF Version**, **Configuration Status**, and **Summary Alarm**, and the **TS Configuration Status** and **Default PID Handling** settings. The **Use of BootP**, **Configuration Status**, **TS Configuration Status**, and **Default PID Handling** settings can be changed from this page. The **Reset** button resets the device.

  - The **MMI Alarms** page button opens a subpage with the alarm states derived from the device alarm status: **MMI Configuration**, **MMI Configuration Status**, **MMI Display**, and **MMI Interface**.
  - The **Board Info** page button opens a subpage where you can click **Load** to retrieve the **BoardList Table**, a text overview that lists every installed board with its slot number, board type, channel number, software, hardware, PLD, and Xilinx firmware versions, serial number, and description.

- **Services**: Displays the **Ts Service Overview** table, which lists each service detected in the transport stream with its slot number, service ID, name, PCR PID, PMT PID, original network ID, provider, and type. The **Ts Component Overview** table lists the individual components (PIDs) with their type, bit rate, language, decoded component type, and the service they belong to. The page also contains the **Default Service Handling** and **PSI/SI Analyse** settings.

  - The **More Info** page button opens the **Service Handling Information** subpage. Click **Load** to retrieve the **Service Handling Overview** table, which shows the slot number, port number, ID, and service state of each handled service.
  - The **PSI/PS Info** page button opens a subpage where you can click **Load** to retrieve the **PSI/SI Information Overview** table, which shows the type, repetition rate, and mode of each PSI/SI table.

- **Transport Stream**: Select the **TS Slot Number** of the board you want to monitor. Once a slot is selected, the page displays the **TS Input** parameters of that slot (**Input Selection**, **Bit Rate**, **Effective Bitrate**, **Packet Length**, and **Alarm Status**) and the **TS Output** parameters (**Rate**, **Packet Length**, **External Clock**, **Interface**, **Effective Bitrate**, and **Alarm Status**). The **Input Selection** and most of the output settings can be changed from this page.

- **Demodulator**: Select the **Demodulator Slot Number** of the satellite demodulator board you want to monitor. The page then displays and allows you to configure the **LNC Voltage**, **LNC Frequency**, **Satellite Frequency**, **Symbol Rate**, **Inner Code**, **Tuner Type**, **Spectral Invertion**, and **Output Select**, and shows the measured **BER**, **AGC Level**, and **AFC**. The sync status (**Clock Sync**, **Carrier Sync**, **Viterbi Sync**, and **Frame Sync**) and the demodulator alarms (**Response**, **Absence RF**, **BER above 10e-4**, **No Frame Sync**, and **Sync**) are also shown here.

  - The **More Settings** page button opens a subpage with the **Minimum**, **Maximum**, and **Step Tuner Frequency** settings and the **LNC 22kHzTone** setting.

- **ATM Information**: Select the **ATM Rx Slot Number** and **ATM Tx Slot Number** of the ATM boards you want to monitor. For both the receive and transmit side, the page displays and allows you to configure the **Output Select**, **Cell Discard**, **HEC Correction**, **Payload Scrambler**, **Virtual Path Identifier**, and **Virtual Channel Identifier**, and shows the measured **Cell Rate** and **Mpeg Rate**. The status parameters (**Response**, **MPEG Sync**, **HEC Sync**, **PDH Framing**, **G703 Signal**, **Fluctuating Input**, **PDH Remote**, and **PDH Local**) are also shown for each side.

- **Webinterface**: Displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
