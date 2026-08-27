---
uid: Connector_help_Thales_S7HP_Technical
---

# Thales S7HP

## About

The Thales S7HP is a high-power shortwave radio transmitter. This connector uses SNMP to monitor and control the transmitter, covering transmitter and modulator functions, alarms, faults, modules, status information, measurements, and events.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

This connector provides monitoring and control capabilities for the Thales S7HP transmitter through SNMP. It enables operators to monitor transmitter performance, supervise hardware and software status, track alarms and faults, and perform remote operational and configuration actions.

Typical use cases include:

Monitoring transmitter operation and verifying that transmission parameters remain within expected operating conditions.
Investigating alarms, faults, and hardware issues by correlating status information with reported events and measurements.
Validating software and firmware versions during commissioning, maintenance, or upgrade activities.
Managing audio, modulation, synchronization, and network-related settings from a centralized interface.
Performing remote control actions such as transmitter power management and operational adjustments.
Integrating transmitter notifications into monitoring workflows through SNMP events and alarm reporting.

The connector also provides access to detailed operational measurements, device status information, transmitter configuration settings, and polling controls, allowing monitoring behavior to be adapted to operational requirements.
