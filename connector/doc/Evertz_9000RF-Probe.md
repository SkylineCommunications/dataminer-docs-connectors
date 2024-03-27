---
uid: Connector_help_Evertz_9000RF-Probe
---

# Evertz 9000RF-Probe

The Evertz 9000RF-Probe is a real-time Radio Frequency(RF) and Transport Stream(TS) monitoring system that is able to monitor multiple RF sources simultaneously. 
Each RF Probe is 1RU rack-based unit and can have 8x, 16x or 32x RF inputs.
The RF Probe is able to tune and demodulate satellite DVBS/S2/S2x, ATSC, DVBT/T2, ISDBT, QAM and DVBC/C2 signals.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Driver</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |<ul><li><xref:Connector_help_Evertz_9000RF-Probe_-_Channel></li></ul>   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

## How to use

This connector communicates with the 9000RF-Probe device via SNMP and it can export DVEs for each of the RF Inputs.

**General**: This page of the connector has the generic system info of the device. This includes the type and features of the device.

**Data Ports**: This page contains the Data Port, SFP and IP tables that relate to the communication settings of the device. It is recommended to update these info from the device's web interface.

**RF Inputs**: This page contains the details of the RF Probe Inputs and Channels. In the *RF Configuration* Table, the *Device DVE* setting allows generation of DVEs based on the RF Input.
**Channel Polling Manager**: This page allows the enabling or disabling of polling for certain channels. This can be used to disable polling for channels not in use.

**Traps**: This page contains the received Traps from the Device.

**LNB** This page contains the Low-Noise Block Table.