---
uid: Connector_help_GatesAir_Maxiva_UAXT_Transmitter
---

# GatesAir Maxiva UAXT Transmitter

This connector monitors information from the GatesAir Maxiva UAXT Transmitter, an ultra-compact low-power **UHF/VHF transmitter** for both analog and digital broadcasting. The Maxiva UAXT/VAXT Ultra-Compact is a platform available in transmitter, transposer, or SFN gap filler configurations for DVB-T, DVB-T2, ATSC, ISDB-Tb, DTMB, DAB/DAB+, and NTSC/PAL analog networks.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 01.21.0004             |

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
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- **General** page: Contains system information data, providing an overview of the current status and configuration of the device.
- **Version** page: Contains information about the software and firmware versions that are currently installed.
- **Cooling** page: Contains information about the current temperatures and fan speeds.
- **Time Source** page: Contains settings related to time synchronization sources, such as GPS or NTP servers.
- **Amplifier** and **External Amplifier** pages: Contains status, alarming, and output configuration for both internal and external amplifiers used in the system.
- **Inputs** and **Inputs Alarming** pages and subpages: Contains the status and alarming of inputs, along with any relevant settings.
- **Satellite Receiver** page: Contains information about the satellite receiver.
- **Gigabit Ethernet** page: Contains the status and alarming for the Gigabit Ethernet connections, along with any relevant settings.
- **EDI** page: Contains information about EDI-ETI alarming.
- **Modulator**, **DVB-T**, **DVB-T2**, **DAB**, **Multi DAB**, **DTMB**, **ISDB-T**, **ATSC**, **Analog**, and **Repeater** pages and subpages: Contain modulator-related information, settings, and alarming for various modulation standards, including DVB-T, DVB-T2, DAB, Multi DAB, DTMB, ISDB-T, ATSC, Analog, and Repeater.
- **Transposer** page and subpage: Contains the status and alarming of the transposer, along with any relevant settings.
- **Power Supply** page and subpage: Contains the status and alarming for the power supplies, along with any relevant settings.
- **RTAC** page: Contains information about the RTAC.
- **FTR** page and subpage: Contains the status and alarming of FTR.
