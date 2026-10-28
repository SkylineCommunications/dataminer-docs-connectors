---
uid: Connector_help_Raisecom-RAX-721
description: Monitor Raisecom RAX 721 device health, interface traffic, optical diagnostics, power supplies, and fans in DataMiner using SNMP.
---

# Raisecom-RAX-721

## About

The **Raisecom-RAX-721** connector brings Raisecom RAX 721 device health, interface performance, and optical diagnostics into DataMiner through SNMP. It helps network operations teams investigate connectivity problems and helps maintenance teams distinguish traffic issues from optical, cooling, or power supply problems.

For service troubleshooting, start with the interface overview and inspect receive and transmit statistics. For equipment maintenance, combine system resource measurements with the power supply and fan tables.

## Key Features

- **Device Health**: Monitor system uptime, CPU and memory utilization, and device temperature.
- **Interface Performance**: Compare administrative and operational status, traffic rates, and bandwidth utilization, with detailed receive and transmit packet, discard, and error rates.
- **Optical Diagnostics**: Inspect reported transmit and receive power, bias current, transceiver and laser temperatures, and optical alarm states.
- **Hardware Monitoring**: Check power supply presence, input and warning states, and fan presence, status, and speed.
- **Operational Context and Control**: Label interfaces in DataMiner independently of device aliases, receive supported Ethernet OAM threshold-crossing events, and manage selected interface settings through SNMP writes.

## Use Cases

### Investigate a Connectivity Degradation

**Challenge**: A connectivity complaint does not immediately identify whether an interface is down, congested, or experiencing errors.

**Solution**: Check interface status and bandwidth utilization, then inspect the associated receive and transmit error and discard rates. Compare these with the optical measurements reported for that interface.

**Benefit**: You can narrow the investigation to the affected interface and select the next troubleshooting step using a shared operational view.

### Prioritize Equipment Maintenance

**Challenge**: Traffic measurements alone do not reveal cooling, power supply, or system resource problems.

**Solution**: Review device temperature, CPU and memory utilization alongside power supply warnings and fan status and speed.

**Benefit**: Maintenance teams can focus their investigation on the equipment condition behind a service risk.

### Identify Interfaces Without Changing Device Labels

**Challenge**: Operations teams need service-specific interface labels but cannot always change the device configuration.

**Solution**: Use DataMiner-side custom descriptions and choose a display key format that combines descriptions and aliases across the interface tables.

**Benefit**: You can make troubleshooting views easier to navigate without requiring a device-side alias change.

## Technical Reference

### Prerequisites

- **Supported Model**: Raisecom RAX 721. Compatibility with other RAX or ISCOM models is not established by this connector.
- **DataMiner**: Minimum version **10.4.0.0 - 14003**.
- **Connectivity**: SNMPv2 access to the device. Device-side write permissions are required for SNMP controls; event monitoring also requires device traps to reach DataMiner.
- **Firmware**: No validated firmware version is specified in the connector source.

> [!NOTE]
> For connection settings, polling behavior, supported controls, and page descriptions, refer to the [technical documentation](xref:Connector_help_Raisecom-RAX-721_Technical).
