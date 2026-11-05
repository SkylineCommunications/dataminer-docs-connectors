---
uid: Connector_help_ND_Satcom_RCU5000
---

# ND Satcom RCU5000

The **ND SatCom RCU5000** redundancy controller manages 1:1 redundant transmit chains and up to 3:1 redundant transmit chains as an option.

## About

The **ND Satcom RCU5000** is an SNMP connector designed to communicate with RCU 5000 ND Satcom devices. The Redundancy Control Unit (RCU) is used for Monitoring and Control (M&C) of satellite ground station equipment.

### Version Info

| Range       | Description                                          | DCF Integration     | Cassandra Compliant |
|-------------|------------------------------------------------------|---------------------|-------------------------|
| 1.0.0.x     | Initial version                                      | No                  | No                      |
| 2.0.0.x     | Branch version based on 1.0.0.x. Added DVE functionality and HPA tables | No                  | No                      |
| 3.3.3.x     | New tables added                                     | No                  | No                      |
| 3.3.11.x    | Added DCF support                               | Yes                 | No                      |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 3.3.11.x         | 1.8.9 (application version) |

### Exported connectors

| Exported Connector | Description |
|-----------------------|-----------------|
| ND Satcom RCU5000 HPA | HPA modules     |
| ND Satcom RCU5000 RFT | RFT modules     |

## Installation and configuration

### Creation

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

**SNMP CONNECTION**:

- **IP address/host**: The polling IP of the device*.*
- **Device address**: Not used.

**SNMP Settings**:

- **Port number**: The port of the connected device, by default *161.*
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

## Usage

### General page

This page displays some general information:

- **Application Version**: Displays the application version of the RCU, in particular the SMACS software version.
- **Access Status**: Allows the user to change the access status.
- **RCU Reboot**: N/A

### Device/Switch

The left side of this page displays the **Device** **Table**. This table contains all the devices that are controlled by the RCU. The table also displays the status of these devices. For every HPA device that is displayed in the table, an extra element will be created with the name: *\[name of ND Satcom RCU5000 element\].\[HPA \]\[idx\]*.

This page also displays the **Redundancy** **Controller** **Status, Redundancy Switching Mode**, and the **Switch Position** for the switches 1 and 2

### Alarms

This page displays the **RCU Notification Table**, which contains all the notifications in the RCU and all the alarms in the devices controlled by the RCU. The type of alarm is also displayed for each alarm, and can be *Alarm*, *Warning* or *Info*.

### Web Interface

This page allows access to the web interface provided by the device's web server. This is only available if the LAN where it is accessed has access to the IP of the device.
