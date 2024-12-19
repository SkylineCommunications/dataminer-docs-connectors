---
uid: Connector_help_Evertz_9000RF-Probe
---

# Evertz 9000RF-Probe

The Evertz 9000RF-Probe is a real-time radio frequency (RF) and transport stream (TS) monitoring system that is able to monitor multiple RF sources simultaneously. Each RF probe is a 1RU rack-based unit and can have 8x, 16x, or 32x RF inputs. The RF probe is able to tune and demodulate satellite DVBS/S2/S2x, ATSC, DVBT/T2, ISDBT, QAM, and DVBC/C2 signals.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2.2.b130       |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components                                                                  |
|---------|-----------------|---------------------|-------------------|--------------------------------------------------------------------------------------|
| 1.0.0.x | No              | Yes                 | -                 | - [Evertz 9000RF-Probe - RF Input](xref:Connector_help_Evertz_9000RF-Probe_-_RF_Input) |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### SNMP traps

The connector also receives traps from the device, and it will repoll the RF inputs and channels for the received traps.

## How to use

This connector communicates with the 9000RF-Probe device via SNMP, and it can export DVEs for each of the RF inputs. To enable DVE creation, select the **Enable DVE child creation** checkbox in the advanced element settings.

### On Startup

The connector starts up by polling the list of available channels for the channel polling manager. The RF Tune, RF Status, and Transport Stream Status tables will initially be empty because polling is disabled by default for all channels.

The following data pages are available in the main element:

- **General/System**: Displays general and system info for the device, including system features, system products, system security, system faults, and system license.

- **Data Ports/SFP/IP**: Contains the Data Port, SFP, and IP tables, which are related to the communication settings of the device. We recommend updating this info from the device's web interface.

- **RF Inputs/RF Configuration**: Contains the data and settings of the RF Probe inputs and channels. The monitoring and alarming of the data from the RF Inputs and channels occur here.

- **DVE Manager/Channel Polling Manager**: Allows the enabling or disabling of polling for certain channels. We recommend disabling the polling for channels that are not in use. Using the **Disable All Polling** and **Enable All Polling** options, you can disable or enable polling for all channels at once. DVEs can also be created via the DVE Manager, which will create an element for the specific RF input to enable better visualization and monitoring of data.

### Maintenance Windows

During maintenance windows, traps can be sent very frequently for channels under maintenance, which can cause excessive polling of data in the tables. To prevent this, we recommend **disabling polling** on the channels undergoing maintenance (on the Channel Polling Manager page).
