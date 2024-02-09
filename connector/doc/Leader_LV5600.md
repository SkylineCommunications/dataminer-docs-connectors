---
uid: Connector_help_Leader_LV5600
---

# Leader LV5600

With this connector, you can check the information provided by the Leader LV5600 device. Each page provides real-time data from the device.

This device is use to monitor the waveform of each input signal in it.

## About

### Version Info

| Range              | Key Features                       | Based on | System Impact         |
|--------------------|------------------------------------|----------|-----------------------|
| 1.0.0.x [SLC Main] | Initial version                    | -        | -                     |
| 1.1.0.x            | New parameters and discrete values | 1.0.0.2  | Supports firmware 5.3 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Lower than 5.3         |
| 1.1.0.x   | 5.3 or higher          |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: If the proxy server has to be bypassed, specify *BypassProxy.*

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

## How to use

When you have created the element, it will start polling data and fill in the active parameters.

This device works with a menu tree, which has 8 trees. Per section, you can find the menu pages (left side of the page): General, System, Video Signal Waveform (WFM), Vector, Picture, Status, Eye/Jitter, and Audio. The polling time for each parameter is 1 hour but each parameter polls when you set a new value.

For the General tree, the parameters are distributed over one page, and those parameters are Input and Preset parameters.

For the Video Signal Waveform (WFM) tree, the parameters are distributed over 4 pages: WFM (Sweep, Ext. Sync., Gain and Line menus), WFM - Inten/Config (Inten/Config parameters), WFM - Cursor (Cursor parameters) and WFM - Color System (Color system parameters).

For the Vector tree, the parameters are distributed over 3 pages: Vector (Inten/Config, Histogram Scale, 5Bar Scale and Line Select parameters), Vector - Scale (Scale parameters) and Vector - CIE Diagram Scale (Diagram Scale parameters).

For the Picture tree, the parameters are distributed over 4 pages: Picture (Edge, Data, Max Fall and Line Select menu trees parameters), Picture - Configuration (Configuration menu tree parameters), Picture - CineLite (CineLite and CineZone setup parameters) and Picture - Noise Setup (Noise Setup parameters).

For the Status tree, the parameters are distributed over 5 pages: Status (Ext. Ref. Phase, AV Phase, Status Event Log and Dump Operation parameters), Status - Mode (Mode parameters), Status - IP (Packet Jitter, Packet Header PTP, etc.), Status - Ancillary (Ancillary parameters) and Status - Data (Data parameters).

For the Eye/Jitter tree, the parameters are distributed over 3 pages: Eye/Jitter (Data and Peak Hold parameters), Eye/Jitter - Inten/Config (Intensity and Color parameters) and Eye/Jitter - Gain/Filter/Sweep (Gain, Filter and Sweep parameters).

For the Audio tree, the parameters are distributed over 2 pages: Audio (Setup parameters) and Audio - Data (Data parameters).
