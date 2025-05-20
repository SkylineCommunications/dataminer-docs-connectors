---
uid: Connector_help_Technetix_NCC-2222_Technical
---

# Technetix NCC-2222

## About

An NCC-2222 chassis, as part of the Narrowcast Controller system, combines broadcast amplification with advanced controller functionality. It manages all connected NarrowCast inserters (NCI-521/WB or NCI-521-12, up to 22 units) while supporting dual broadcast input (A/B) for redundancy. A DVE element will be created in DataMiner for each connected unit.

An **SNMP** connection is used to retrieve and configure device information.

Only one element should poll a device at a time. Polling the same device with multiple elements simultaneously may result in unexpected behavior.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

## How to Use

### General

This page contains generic parameters such as the **name** of the device, the **IP address** and **software** **versions**.

### NCI Overview

This page provides an overview of all installed **NCI-521** **cards**, together with the **status** of each card.

### NCC Status

This page displays the **status** of the **NCC module**. The **input attenuation** and **input equalization** can be changed. With the configuration parameters, you can enable or disable the displayed alarms.

### RPS-UNI

This page contains the same information as the **RPS-UNI** page in the web interface. With the alarm configuration page button, you can enable or disable the alarms.

### Traps

This page displays the last generated trap. With the table displayed via the configuration page button, you can control the SNMP manager that sends the traps.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
