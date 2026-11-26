---
uid: Connector_help_Rohde_Schwarz_TCE900_(System_9000)
description: SNMP connector for the Rohde & Schwarz TCE900 transmitter controller (System 9000), covering power, inputs, modulation, redundancy, and cooling.
---

# Rohde Schwarz TCE900 (System 9000)

## About

The **Rohde Schwarz TCE900** is the transmitter control unit of the Rohde & Schwarz System 9000 (Tx9) transmitter family, used for both digital and analog TV and radio transmission. It controls the exciter, amplifiers, output stage, cooling, and input signal processing of a transmitter, and it coordinates redundancy setups such as N+1, multi-transmitter, and backup transmitter systems.

With this connector, you get a single DataMiner element per transmitter that shows the transmitter state and output power, the active input feed, the modulation configuration, and the health of the hardware, and that lets you operate the transmitter remotely.

## Key Features

- **Transmitter output and redundancy monitoring**: Follow the forward and reflected power, PA efficiency, and modulation mode of every transmitter, together with the reserve exciter, N+1, multi-transmitter, and backup transmitter switching status.

- **Input feed supervision and automatic input switching**: Track the IP, TS, satellite, and RF receiver feeds, including packet loss, bit error rate, MER, and link margin, and see which input is active and why the automatic input changeover switched.

- **Support for all transmission standards of the TCE900**: Access the input and output configuration for DVB-T, DVB-T2, ATSC, ATSC 3.0, ISDB-T, DTMB, DAB, FM (including HD Radio), and analog TV, including SFN and frequency regulation settings.

- **Hardware and site environment monitoring**: Monitor the amplifiers, output stage, liquid and air cooling, RF sensors, GPS receiver, UPS, and the temperature and humidity sensors of the rack.

- **Remote control**: Switch the transmitter and exciter operation mode, change the nominal power, load and save presets, manage option keys, and trigger software updates from DataMiner.

## Use Cases

### Transmitter site health at a glance

**Challenge**: A terrestrial broadcast network has many unattended transmitter sites. When a service goes off air, the operator needs to know within seconds whether the problem is the input feed, the exciter, the amplifier, or the cooling.

**Solution**: The connector polls the TCE900 and exposes the transmitter state, forward and reflected power, input feed quality, amplifier status, and cooling system on dedicated pages.

**Benefit**: Locate the failing stage of a transmitter from the control room, so that a site visit is only dispatched when it is actually needed.

### Redundancy verification

**Challenge**: N+1 and backup transmitter systems only pay off when the switchover actually works. Operators need to know which transmitter is on air, whether the reserve is ready, and when a switchover has happened.

**Solution**: The N+1, Multi Transmitter, and Backup Transmitter pages show the redundancy status of each transmitter in the system, and the Transmitter page shows the reserve exciter status.

**Benefit**: Confirm that the reserve is ready and that a switchover completed as expected, without opening the web interface of each transmitter.

### Controlled remote operation

**Challenge**: Routine actions such as switching a transmitter to standby for maintenance, loading a different program preset, or reducing the nominal power during a thermal event normally require a technician on site or a session on the device web interface.

**Solution**: The connector exposes these actions as parameters, so that they can be performed from DataMiner instead of on the device web interface.

**Benefit**: Carry out routine transmitter operations for all sites from one place, with the result of the action visible on the same element.

## Technical Reference

### Prerequisites

- **DataMiner 10.3.0.0 (build 12752)** or higher is required to use this connector.
- **SNMP access** from the DataMiner Agent to the management interface of the TCE900 is needed for polling and control.
- **Network access from the client machine** to the TCE900 is needed to use the embedded web interface page.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Rohde_Schwarz_TCE900_(System_9000)_Technical).
