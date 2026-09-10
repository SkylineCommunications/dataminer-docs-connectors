---
uid: Connector_help_NTI_ENVIROMUX_5D_Technical
---

# NTI ENVIROMUX-5D

## About

This connector uses SNMPv2 communication to monitor the NTI ENVIROMUX-5D Enterprise Environment Monitoring System. It retrieves data from internal temperature and humidity sensors, up to five external configurable sensors, digital inputs, IP devices, output relays, and power supplies. It also provides smart alert management, network configuration visibility, and access to extended sensor types such as TAC, IP, and auxiliary sensors.

## Configuration

### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

## Usage

### General Page

This page displays general system and device information, including:

- **System Time**
- **System Enterprise Name**, **Location**, **Branch**, **Rack**, **Contact**, and **Phone**
- **System Firmware Version**
- **Device Model**, **Serial Number**, **Hardware Revision**, and **Manufacturer**

With the **System Reset** option, you can initiate a device reboot.

In addition, several subpages are available via page buttons:

- **Message Registers**: Displays the **Message Registers Table** with the description and status of each configured message register.
- **Siren Beacons**: Displays the **Siren Beacons Table** with the current status of each siren beacon output.
- **Remote**: Displays the **Remote Inputs Table** and **Remote Relays Table** for monitoring cascaded remote unit inputs and relay states.
- **Smoke Detectors**: Displays the **Smoke Detectors Table**, showing the description, group, value, and status of each connected smoke detector.

### Sensors Page

This page displays sensor data across three tables:

- **Internal Sensors Table**: Lists the two built-in temperature and humidity sensors with columns for **Type**, **Description**, **Group**, **Value**, **Unit**, **Status**, and configurable **Min/Max** and **Warning Thresholds**, as well as **Offset**.
- **Auxiliary Sensors Table**: Lists auxiliary port sensors with columns for **Type**, **Description**, **Connector**, **Group**, **Value**, **Unit**, **Status**, and configurable **Min/Max** and **Warning Thresholds**.
- **External Sensors Table**: Lists the external configurable sensors with columns for **Type**, **Description**, **Connector**, **Group**, **Value**, **Unit**, **Status**, **Min/Max Thresholds**, **Warning Thresholds**, and **Offset**.

This page also provides access to the following subpages via page buttons:

- **Auxiliary 2 Sensors**: Displays additional auxiliary sensor data including **Type**, **Description**, **Value**, **Unit**, **Status**, and threshold settings.
- **TAC Sensors**: Displays TAC sensor readings including **Type**, **Description**, **Value**, **Unit**, **Status**, and threshold settings.
- **External Sensors ACLM**: Displays AC line monitoring data for power-type external sensors, including **Peak Value**, **Frequency**, **Current**, **Spikes**, **Swells**, **Sags**, **Relay**, and **Min/Max Thresholds**.
- **All External Sensors**: Provides a unified view of all external sensors from all categories in a single table, including **UID**, **Type**, **Description**, **Value**, **Unit**, **Status**, **Thresholds**, **Int Value**, and **Offset**.

### Digital Inputs Page

This page displays the **Digital Inputs Table**, which contains the following columns: **Index**, **Type**, **Description**, **Connector**, **Group Number**, **Group**, **Value**, **Status**, and **Normal Value**.

### IP Devices Page

This page displays the **IP Devices Table**, which allows monitoring of network-reachable devices. Columns include **Index**, **Address**, **Description**, **Group Number**, **Group**, **Timeout**, **Retries**, **Value**, and **Status**.

### IP Sensors Page

This page displays the **IP Sensors Table** for sensors accessed over the network. Columns include **Micro Unit**, **Type**, **Description**, **Connector**, **Group Number**, **Group**, **Value**, **Unit**, **Unit Name**, **Status**, **Min Threshold**, **Max Threshold**, and **Offset**.

### Output Relays Page

This page displays the **Output Relays Table**, showing the **Description** and **Status** of each of the two configurable output relays used for controlling external devices.

### Power Supplies Page

This page displays the **Power Supplies Table**, showing the **Status** of each monitored power supply input.

### Smart Alerts Page

This page displays two tables:

- **Events Table**: Shows active and historical events with **Description**, **Status**, and **Value**.
- **Smart Alerts Table**: Shows configured smart alert rules with their **Description** and **Status**.

### Network Configuration Page

This page provides read and write access to the device's network settings, organized in three sections:

- **IPv4 Settings**: **IPv4 Mode** (DHCP or Static), **IPv4 Address**, **Mask**, **Gateway**, **Preferred DNS**, **Alternate DNS**, and **DNS Timeout**.
- **IPv6 Settings**: **IPv6 Mode**, **IPv6 Address**, **Gateway**, **IPv6 to IPv4 Tunnel**, **Local IP Address**, and **Remote IPv4 Address**.
- **VLAN Settings**: **Enable 802.1Q VLAN** and **VLAN ID**.

Additional controls include **Save Network Configuration** and **Enable Network Security**.

### Web Interface Page

This page provides direct access to the device's embedded web interface at `http://[Polling IP]/`. Note that the client machine must be able to reach the device on the network for the web interface to load.
