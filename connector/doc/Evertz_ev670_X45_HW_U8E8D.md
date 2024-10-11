---
uid: Connector_help_Evertz_ev670_X45_HW_U8E8D
---

# Evertz ev670-X45-HW U8E8D

TThis connector can be used to monitor and configure the Evertz ev670-X45-HW U8E8D. This is a FPGA-accelerated compute blade that supports both 12G/3G/HD-SDI and IP interfaces.

## About

### Version Info

| **Range**            | **Key Features**               | **Based on** | **System Impact**                                                                                              |
|----------------------|--------------------------------|--------------|----------------------------------------------------------------------------------------------------------------|
| 1.0.0.x              | Initial implementation.        | -            | -                                                                                                              |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector polls most of the tables using subtable functionalities to reduce the amount of time it takes to poll tables and also to poll essential rows.

In range **1.0.0.x**, the following pages are available in the element:

- **General**: Includes general parameters such as Serial Number and MAC Address.
- **System**: Includes the Data Port Control table as well as some controls such as Reboot, Trap Port Select, System Mode, and various monitoring controls.
- **System** **Data** **Port**: Includes the System Data Port Monitor and QSFP Monitor tables.
- **PTP Control**: Includes various PTP-related configuration parameters.
- **System** **Time** **Management**: Includes various time and NTP configurables.
- **UMD** **Control**: Includes the UMD Control and Dynamic Input tables.
- **Input** **Monitor**: Includes various monitor tables for Input/Video/ANC/Audio.
- **Video** **Input** **Control**: Includes the Input Control and Video Input Control tables. The **Input Control Table** is where you **set the custom description for all input tables**.
- **Audio** **Input** **Control**: Includes the Audio Input Control and Audio Shuffle Control tables.
- **ANC** **Input** **Control**: Includes the ANC Input Control table.
- **Input** **Properties** **Control**: Includes the Input Properties control table.
- **System** **Notify**: Includes the Data Port and System Notify tables, as well as CPU configurables.
- **Video** **Notify**: Includes the Video Monitoring Control and Video Notify tables. As of 1.1.1.x, each row in the Video Notify table represents an input instead of an input fault. The **individual fault statuses** can be found in the **columns**.
- **Audio Notify**: Includes the Audio Monitoring Control and Audio Channel/Group Notify tables. As of 1.1.1.x, each row in the Audio Notify table represents an input instead of an input fault. The original table is also split into the Channel and Group tables based on the fault types. The **individual fault statuses** can be found in the **columns**.
- **System** **Monitor**: Includes the various system monitoring parameters.
- **Output** **Control**: Includes the Output Control, Output Video IP Control, Output Audio, and Layout Control tables.
- **Advanced** **Notify** **Control**: Includes the Picture Level, CC, TXT, Nielsen, EIA 708, ANC, LTC, Video, and Scte 104 control tables.
- **Advanced** **Notify**: Includes the Advanced Notify table. As of 1.1.1.x, each row in this table represents an input instead of an input fault. The **individual fault statuses** can be found in the **columns**.
- **Advanced Loudness**: Includes the Audio Loudness Control/Audio Loudness tables.
- **Advanced** **Loudness** **Notify**: Includes the Audio Loudness Notify table.
- **NMOS** **Control**: Contains various NMOS configurables.
- **Output** **Encoder**: New for 1.1.1.x. Includes the Output Encoder control table.
- **Input** **Control**: New for 1.1.1.x. Includes the Input Video, Input Audio, and Input ANC Control tables, as well as the Input Video/Audio/ANC Notify tables.
- **Traps**: Includes the Traps Log table and trap control parameters.



