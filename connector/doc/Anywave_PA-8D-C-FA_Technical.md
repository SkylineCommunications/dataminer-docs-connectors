---
uid: Connector_technical_Anywave_PA-8D-C-FA
---

# Anywave PA-8D-C-FA — Technical Documentation

## About

The Anywave PA-8D-C-FA is a high-power broadcast RF power amplifier with nine parallel solid-state amplifier modules and a 50 V DC supply rail. This connector polls the device over SNMP to retrieve run-status telemetry, alarm state, configurable thresholds, and system configuration, and allows write-back of all configurable parameters.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The management IP address of the amplifier.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Initialization

After element creation, verify that **Control Mode** (on the System Settings page) is set to *Remote*. When the device is in *Local* mode, SNMP write commands are silently ignored by the device — threshold changes, attenuation adjustments, exciter selection, and all other set operations will have no effect.

### Web Interface

The web interface is accessible at `http://<device-ip>/` and provides the same status, settings, and alarm information as the connector pages. The web interface is only accessible when the client machine has network access to the device.

## How to Use

The connector is organised across four for settings and status. The transmitter and exciter configuration can be configured on the **System Settings** page.
