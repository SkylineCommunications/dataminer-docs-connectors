---
uid: Connector_help_Tredess_MultiTX_Technical
---

# Tredess MultiTX

## About

The Tredess MultiTX is a modular DVB-T/DVB-T2 terrestrial transmitter platform. A chassis can contain transmitter (TX) modules, an NP1 redundancy switching unit, power supply units (PSU), and synchronization (SYNC/GNSS) modules.

This connector polls the device over SNMP and processes SNMP traps to monitor and configure all modules in the chassis.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No additional configuration is required in a newly created element. Polling of the different data groups can optionally be tuned on the **Polling Settings** page.

To receive traps, configure the device to send SNMP traps to the IP address of the DataMiner Agent hosting the element.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. The **Webpage** page of the element links directly to the device web interface using the polling IP.

## How to Use

The element provides comprehensive monitoring and configuration for all modules in the MultiTX chassis using SNMP polling and real-time trap processing.

### Transmitter (TX) Module Monitoring and Control

On the **TX Module** pages, you can supervise the operation of each transmitter module and configure its transmission parameters:

- **RF and Power**: Monitor forward power, amplifier status, and input levels. You can mute or enable the RF output, configure input/output settings, and adjust precorrection and echo cancellation parameters.
- **Modulation and Transmission Standards**: Configure DVB-T and DVB-T2 parameters, including system, network, frame, and modulation settings, as well as per-PLP (Physical Layer Pipe) configurations.
- **Input Switching**: Monitor the ASI 1/2 and IP socket inputs, review the active input status, and configure automatic or manual input switching behavior.

### Redundancy Management (NP1)

The **NP1** pages allow you to manage 1+1 transmitter redundancy:

- View active redundancy status and verify that the backup transmission chain is operational before an incident occurs.
- Check switching causes and configure automatic verification settings to ensure seamless switchover during input or transmitter failures.

### Synchronization and Chassis Health

- **Synchronization (SYNC)**: On the **SYNC** pages, monitor the GNSS 1 and GNSS 2 receivers to verify satellite lock, reference clocks, and timing status for Single Frequency Network (SFN) and Multi-Frequency Network (MFN) operations.
- **Power and Cooling (PSU)**: On the **PSU** pages, track power intake, power supply health, and fan speeds to detect cooling or power degradation early.
- **Chassis Management**: On the **Management** pages, configure and monitor chassis-level settings, including network interfaces, modem, battery status, and date and time.

### Traps and Alarming

Incoming SNMP traps are received in real time and displayed on the **Trap** page, updating alarm states immediately. Key parameters across all modules are enabled for alarming and trending out of the box.

### Polling Settings

The **Polling Settings** page contains a Polling Manager table that lets you optimize SNMP communication:

- Adjust the polling interval or disable polling for individual groups (such as slow-changing configuration tables) to reduce network load.
- Use the table context menu to refresh specific groups on demand.

## Notes

- Trap processing is based on the wildcard trap OID `1.3.6.1.4.1.23180.2.1.1.4.10.*`; ensure the device firmware sends traps under this OID branch.
- Configuration changes performed outside DataMiner (e.g., via the device web interface) are picked up during the next poll cycle of the corresponding group.
