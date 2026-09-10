---
uid: Connector_help_Advantech_Wireless_Genesis-HP_Ku_SSPA-SSPB_Technical
---

# Advantech Wireless Genesis-HP Ku SSPA/SSPB

## About

This connector links DataMiner with an Advantech Wireless Genesis-HP Ku-band SSPA/SSPB system through a single **SNMPv3 connection**. It is a read-only, monitoring-only connector, which means it polls the system's SNMP agent for status, fault, and configuration information and does not send any configuration commands to the device.

## Configuration

### Connections

#### SNMPv3 connection - Main

This connector uses an SNMPv3 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device, by default *161*.
- **Bus address**: Not required.
- **Security level and protocol**: The SNMPv3 security level and protocol configured on the device.
- **User name**: The SNMPv3 user name configured on the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

Below you can find more information on how to use the different pages of the connector.

### General

The **General** page displays overall system information (e.g., description, model number, and serial number) as well as system-level status and fault summaries, including RF switch and redundancy status.

### RF Units

The **RF Units** page contains a table listing all RF units in the system, along with their attenuation, temperature, mute status (external/fault), RF switch status, and redundancy identification/hierarchy.

### Devices

The **Devices** page contains a table listing the individual devices that make up the system (e.g., controllers and sensors), along with their temperature, fault status, and RF switch position.

### Redundancy

The **Redundancy** page displays the redundancy configuration of the system, including the current switch position (e.g., mechanical, position 1, position 2, disconnect) and the redundancy hierarchy (e.g., 1:1, N+1, switch role).

### Unit 1 / Unit 2 / Unit 3

The **Unit 1**, **Unit 2**, and **Unit 3** pages provide the same information as the **RF Units** and **Devices** pages, but for each individual RF unit separately, displaying attenuation, temperature, mute status, RF switch status, and device-level fault status.

### Web Interface

This page displays the device's own web interface, accessed using the element's polling IP address. Note that the web interface is only accessible when the client machine has network access to the device.
