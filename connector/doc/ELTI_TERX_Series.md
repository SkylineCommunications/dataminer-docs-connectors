---
uid: Connector_help_ELTI_TERX_Series
description: "Monitor and control ELTI TERX digital TV transmitter changeover systems over SNMP, including device states, RF power, VSWR, power supplies, and safety inputs."
---

# ELTI TERX Series

## About

The **ELTI TERX Series** connector integrates ELTI TERX digital TV transmitter systems into DataMiner over SNMP. TERX transmitters are typically deployed in a **changeover (redundancy) setup**, in which two transmitting devices and a reserved device are supervised by the changeover controller (ECOS) of the system, which decides which device feeds the antenna.

The connector polls the TERX system and shows, in one element, the mode, RF connection, and state of each device, the power supplies, the safety inputs, the cooling data, and the summary warnings and alarms. It also lets operators drive the changeover from DataMiner. Through two additional SNMP connections to the TERX exciters, it reads their forward and reflected power and transmit frequency, and calculates the VSWR of each exciter.

## Key Features

- **Supervise the changeover system**: Follow the device mode, the RF connection (antenna or dummy load), and the state, mode, connection, communication, and output power of transmitting devices 1 and 2 and the reserved device, and see whether the reserved device is in standby or has taken over the role of device 1 or device 2.
- **Operate the changeover remotely**: Set the Auto/Manual and Remote/Local configuration, issue general and changeover standby and reset commands, change the RF switch position, and switch the transmitting and reserved devices on or off.
- **Track RF performance per exciter**: Monitor the TX output power percentage of each exciter and, through the dedicated exciter connections, the forward power, reflected power, transmit frequency, and calculated VSWR.
- **Watch power supplies, safety inputs, and cooling**: Detect low or high 5 V, 12 V, and 24 V supplies, external standby, missing system power supply, dummy load failure, AC power and UPS faults, and keep an eye on the power amplifier temperature, water temperature, pressure, and water pump status of liquid-cooled systems.
- **Open the device web interface from the element**: The embedded Web Interface page uses an address that is automatically filled in from the polling IP on first startup and can be changed afterwards.

## Use Cases

### Knowing Which Transmitter Is on Air at a Remote Site

**Challenge**: At an unmanned transmitter site, a changeover to the reserved device can go unnoticed until the next site visit, leaving the network without redundancy in the meantime.

**Solution**: The connector shows the RF connection, state, and mode of each transmitting device and of the reserved device, whether the reserved device has taken over the role of device 1 or device 2, and the summary warnings and alarms of the system.

**Benefit**: Operators see immediately that a switchover has happened, which device is now on the antenna, and which device needs attention.

### Following the Antenna Match of Each Exciter

**Challenge**: A gradual change in the reflected power of a transmitter is hard to notice from the controller status alone, because the controller status does not include the reflected power.

**Solution**: Through the connections to the exciters, the connector reads the forward and reflected power of each exciter and calculates its VSWR.

**Benefit**: The VSWR of each exciter is available as a value in DataMiner, so a change over time becomes visible instead of being noticed only when the system reports a fault.

## Technical Reference

### Prerequisites

- **DataMiner version**: 10.3.0 (build 12752) or higher.
- **SNMP connectivity**: The TERX system (changeover controller) and each TERX exciter must be reachable via SNMP from the DataMiner Agent.
- **Web interface access**: To use the **Web Interface** page, the client machine must have network access to the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ELTI_TERX_Series_Technical).
