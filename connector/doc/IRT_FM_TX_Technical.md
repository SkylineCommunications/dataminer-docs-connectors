---
uid: Connector_help_IRT_FM_TX_Technical
---

# IRT FM TX

## About

With this connector, you can monitor and configure your IRT FM transmitter. The connector supports several IRT FM transmitter types, i.e. Single Transmitter, Active Reserve, Passive Reserve, Dual Drive, and N+1.

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

### Polling Manager

On the Polling Manager page, you can change the **interval** and **state** of each polling group to cater to your specific use case. With the **Poll** button, you can manually trigger the polling.

This page also displays the last time the polling occurred.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

For each of the supported transmitter types, different pages can be displayed:

- **Single Transmitter**: Contains general information for the Single Transmitter type.

  - **ST - Configurations**: Contains Single Transmitter configurations for the device.
  - **ST - Event Configurations**: Contains a list of SNMP traps for the Single Transmitter that can be enabled/disabled and given a priority.

- **Active Reserve**: Contains general information for the Active Reserve type.

  - **AR - Configurations**: Contains Active Reserve configurations for the device.
  - **AR - Event Configurations**: Contains a list of SNMP traps for the Active Reserve that can be enabled/disabled and given a priority.
  - **AR - Amplifier A - Monitoring** / **AR - Amplifier B - Monitoring**: Contain the Active Reserve's amplifier information.
  - **AR - Amplifier A - Event Configurations** / **AR - Amplifier B - Event Configurations**: Contain a list of SNMP traps for the Active Reserve's amplifiers that can be enabled/disabled and given a priority.
  - **AR - Exciter A - Monitoring** / **AR - Exciter B - Monitoring**: Contain the Active Reserve's exciter information.
  - **AR - Exciter A - Event Configurations** / **AR - Exciter B - Event Configurations**: Contain a list of SNMP traps for the Active Reserve's exciters that can be enabled/disabled and given a priority.

- **Passive Reserve**: Contains general information for the Passive Reserve type.

  - **PR - Configurations**: Contains Passive Reserve configurations for the device.
  - **PR - Event Configurations**: Contains a list of SNMP traps for the Passive Reserve that can be enabled/disabled and given a priority.
  - **PR - Transmitter A - Monitoring** / **PR - Transmitter B - Monitoring**: Contain the Passive Reserve's transmitter information.
  - **PR - Transmitter A - Event Configurations** / **PR - Transmitter B - Event Configurations**: Contain a list of SNMP traps for the Passive Reserve's transmitters that can be enabled/disabled and given a priority.

- **Dual Drive**: Contains general information for the Dual Drive type.

  - **DD - Configurations**: Contains Dual Drive configurations for the device.
  - **DD - Event Configurations**: Contains a list of SNMP traps for the Dual Drive that can be enabled/disabled and given a priority.
  - **DD - Exciter A - Monitoring** / **DD - Exciter B - Monitoring**: Contain the Dual Drive's exciter information.
  - **DD - Exciter A - Event Configurations** / **DD - Exciter B - Event Configurations**: Contains a list of SNMP traps for the Dual Drive's exciters that can be enabled/disabled and given a priority.

- **N+1**: Contains general information for the N+1 type.

  - **N+1 - Configurations**: Contains configurations for the N+1 devices.
  - **N+1 - Event Configurations**: Contains a list of SNMP traps for the N+1 devices that can be enabled/disabled and given a priority.
  - **N+1 - Main Transmitter - Monitoring**: Contains main transmitter information for N+1 devices.
  - **N+1 - Main Transmitter - Event Configurations**: Contains a list of SNMP traps for the N+1 devices's main transmitter that can be enabled/disabled and given a priority.
  - **N+1 - Reserve Transmitter - Monitoring**: Contains reserve transmitter information.
  - **N+1 - Reserve Transmitter - Event Configurations**: Contains a list of SNMP traps for the reserve transmitter that can be enabled/disabled and given a priority.
  - **N+1 - Transmitter A - Monitoring** / **N+1 - Transmitter B - Monitoring**: Contain transmitter information for N+1 devices.
  - **N+1 - Transmitter A - Event Configurations** / **N+1 - Transmitter B - Event Configurations**: Contain a list of SNMP traps for the N+1 devices's transmitters that can be enabled/disabled and given a priority.
