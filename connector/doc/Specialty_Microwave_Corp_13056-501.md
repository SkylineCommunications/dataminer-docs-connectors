---
uid: Connector_help_Specialty_Microwave_Corp_13056-501
---

# Specialty Microwave Corp 13056-501

The HPA 1:2 protection switch (Part No. 13056-501) consists of a logic panel used in satellite communication earth stations.

## About

The system mechanism operates waveguide and coaxial switches to operator desired positions on assembly 13056-101. The mechanisms provide switching and combining operations for the radio frequency (RF) outputs of high power amplifiers (HPA) in an automatic (unattended) or manual (local and or remote) mode.

The 1000-600 Series of Serial to Digital I/O Interface Boards (SIB) provides three serial interfaces. The first Serial Communication Interface (SCI0) is jumper selectable for RS-232C, RS-422, or RS-485, while the second Serial Communication Interface (SCI1) is only RS-422 or RS-485.

The third serial interface is a virtual Serial Communications Interface (SCI2) delivered over TCP/IP using the embedded RJ-45 Ethernet Interface.

Up to 6 virtual SCI2 connections can be established simultaneously.

SCI0 and SCI2 control and read 8 to 256 user-selectable input and output positions and allow the management of all user-configurable settings.

SCI1 can be configured for a pass-through connection allowing multiple SIBs to be connected in a daisy-chain manner, a connection to an HPA or a mirror control link to another SIB.

At power-up the unit configures itself for serial protocol, byte width, input/output assignment, and initial output levels.

The Ethernet port is configured with the necessary IP addresses and net masks as defined by the user, and if a mirror control link is defined, SCI1 attempts to establish communication with its connected SIB.

These items are stored in non-volatile EEPROM memory, which can be configured by the user.

The unit can communicate over SCI0 or 1 operating between 300 and 19200 baud, and over the Ethernet interface at 10 or 100 Mbps and either half or full duplex.

| Version | Description     |
|---------|-----------------|
| 1.0.0.1 | Initial version |

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a **serial** connection and requires the following input during element creation:

Serial connection:

- Type of port: TCP/IP
- IP address/host: The polling IP of the device, e.g. 10.11.12.13.
- IP port: The port designated to be used for serial communication.
- Bus address: A value between 0x21 (33) to 0x7F (127).

## Usage

### Device Information

The **Device Information** consists of the following parameters:

- Firmware version
- Management of front panel customer configuration data options
- Management of parallel interface data
- Management of actual state of pins as initial value
- Management of the mask into the EEPROM to apply or ignore bits in command responses by the Upstream Mirror SIB
- Management of the mask that determines which bits are assigned as input or output
- IP link statistics
- Internal control commands, such as stop or initiate monitoring of front panel, status poll, remote reset, save and read EEPROM from flash, and restart Ethernet without boot.

### SCI Information

The **SCI Information** displays information related to SCI0, SCI1 and SCI2 serial interfaces.

### Bit Change Output Operations

The **Bit Change Output Operations** displays information related to operations to modify the communication data:

- Change bit high/low by giving position
- Establish pulse width
- Pulse bit operations to change a single output bit data on transitions of hi-lo-hi or lo-hi-lo
- Pulse bit operations to change 16 bit data on transitions hi-lo-hi or lo-hi-lo
- Pulse bit operation to change all the bits on transitions hi-lo-hi or lo-hi-lo
