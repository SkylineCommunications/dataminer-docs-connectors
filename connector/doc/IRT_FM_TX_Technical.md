---
uid: Connector_help_IRT_FM_TX_Technical
---

# IRT FM TX

## About

This connector is capable of supporting several IRT FM transmitter types, such as, Single Transmitter, Active Reserve, Passive Reserve, Dual Drive, and N+1.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. (default: *161*)


SNMP Settings:

- **Get community string**: The community string used when reading values from the device. (default: *public*)
- **Set community string**: The community string used when setting values on the device. (default: *private*)

### Polling Manager

This page contains a polling table where it is possible to change the **interval** and **state** of each polling group to cater to your specific use case. It also displays the last polled time and a **Poll** button that can be used to manually trigger the polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **Single Transmitter**: Contains general information on the Single Transmitter device.
	- **ST - Configurations**: Contains Single Transmitter configurations for the device.
	- **ST - Event Configurations**: Contains a list of SNMP Traps for the Single Transmitter that can be Enabled/Disabled and given a priority.
- **Active Reserve**: Contains general information on the Active Reserve device.
	- **AR - Configurations**: Contains Active Reserve configurations for the device.
	- **AR - Event Configurations**: Contains a list of SNMP Traps for the Active Reserve that can be Enabled/Disabled and given a priority.
	- **AR - Amplifier A - Monitoring**: Contains Active Reserve's Amplifier A information.
	- **AR - Amplifier A - Event Configurations**: Contains a list of SNMP Traps for the Active Reserve's Amplifier A that can be Enabled/Disabled and given a priority.
	- **AR - Amplifier B - Monitoring**: Contains Active Reserve's Amplifier B information.
	- **AR - Amplifier B - Event Configurations**: Contains a list of SNMP Traps for the Active Reserve's Amplifier B that can be Enabled/Disabled and given a priority.
	- **AR - Exciter A - Monitoring**: Contains Active Reserve's Exciter A information.
	- **AR - Exciter A - Event Configurations**: Contains a list of SNMP Traps for the Active Reserve's Exciter A that can be Enabled/Disabled and given a priority.
	- **AR - Exciter B - Monitoring**: Contains Active Reserve's Exciter B information.
	- **AR - Exciter B - Event Configurations**: Contains a list of SNMP Traps for the Active Reserve's Exciter B that can be Enabled/Disabled and given a priority.
- **Passive Reserve**: Contains general information on the Passive Reserve device.
	- **PR - Configurations**: Contains Passive Reserve configurations for the device.
	- **PR - Event Configurations**: Contains a list of SNMP Traps for the Passive Reserve that can be Enabled/Disabled and given a priority.
	- **PR - Transmitter A - Monitoring**: Contains Passive Reserve's Transmitter A information.
	- **PR - Transmitter A - Event Configurations**: Contains a list of SNMP Traps for the Passive Reserve's Transmitter A that can be Enabled/Disabled and given a priority.
	- **PR - Transmitter B - Monitoring**: Contains Passive Reserve's Transmitter B information.
	- **PR - Transmitter B - Event Configurations**: Contains a list of SNMP Traps for the Passive Reserve's Transmitter B that can be Enabled/Disabled and given a priority.
- **Dual Drive**: Contains general information on the Dual Drive device.
	- **DD - Configurations**: Contains Dual Drive configurations for the device.
	- **DD - Event Configurations**: Contains a list of SNMP Traps for the Dual Drive that can be Enabled/Disabled and given a priority.
	- **DD - Exciter A - Monitoring**: Contains Dual Drive's Exciter A information.
	- **DD - Exciter A - Event Configurations**: Contains a list of SNMP Traps for the Dual Drive's Exciter A that can be Enabled/Disabled and given a priority.
	- **DD - Exciter B - Monitoring**: Contains Dual Drive's Exciter B information.
	- **DD - Exciter B - Event Configurations**: Contains a list of SNMP Traps for the Dual Drive's Exciter B that can be Enabled/Disabled and given a priority.
- **N+1**: Contains general information on the N+1 devices.
	- **N+1 - Configurations**: Contains configurations for the N+1 devices.
	- **N+1 - Event Configurations**: Contains a list of SNMP Traps for the N+1 devices that can be Enabled/Disabled and given a priority.
	- **N+1 - Main Transmitter - Monitoring**: Contains Main Transmitter information for N+1 devices.
	- **N+1 - Main Transmitter - Event Configurations**: Contains a list of SNMP Traps for the N+1 devices's Main Transmitter that can be Enabled/Disabled and given a priority.
	- **N+1 - Reserve Transmitter - Monitoring**: Contains Reserve Transmitter information.
	- **N+1 - Reserve Transmitter - Event Configurations**: Contains a list of SNMP Traps for the Reserve Transmitter that can be Enabled/Disabled and given a priority.
	- **N+1 - Transmitter A - Monitoring**: Contains Transmitter A information for N+1 devices.
	- **N+1 - Transmitter A - Event Configurations**: Contains a list of SNMP Traps for the N+1 devices's Transmitter A that can be Enabled/Disabled and given a priority.
	- **N+1 - Transmitter B - Monitoring**: Contains Transmitter B information.
	- **N+1 - Transmitter B - Event Configurations**: Contains a list of SNMP Traps for the Transmitter B that can be Enabled/Disabled and given a priority.