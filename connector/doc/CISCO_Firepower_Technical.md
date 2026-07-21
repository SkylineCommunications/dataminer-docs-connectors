---
uid: Connector_help_CISCO_Firepower_Technical
---

# CISCO Firepower

## About

This connector uses SNMP or HTTP communication in order to monitor a CISCO Firepower device. It retrieves fan statistics, monitor statistics, power supply statistics, and more. It also provides an overview of how all these components are behaving, and it displays the average, maximum, and minimum values for specific parameters such as the fan speed and the motherboard input and output current.

## Configuration

#### SNMP connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

## Usage

### General Page

This page displays general system information, including the **System Description**, **Model**, **System Up Time**, **System Contact**, **System Name**, **System Location**, **CPU Usage**, and **Memory Usage**.

The **System Services** page button displays a subpage with the status (*Active* or *Not Active*) for the following layers:

- Physical
- Data Link
- Network
- Transport
- Session
- Presentation
- Application

### SM Monitor Page

This page contains the **SM Monitor Statistics Table**, which contains information such as **CPU Total Load Average**, **Disk File System Count**, **Memory Free**, **Memory Total**, **OS Version**, etc.

### Chassis Page

This page displays the following statistics tables:

- **Fan Statistics Table**: Includes information such as the current, average, maximum, and minimum value of the fan speed.
- **Fan Module Statistics**: Includes information such as the current, average, maximum, and minimum value of the ambient temperature.
- **Chassis Statistics**: Includes information such as the current, average, maximum, and minimum value of the input and output power.
- **Power Supply Statistics**: Includes information such as Ambient Temperature, Input Volts, Output Volts, Output Current, Output Power, and PSU Temperature.
- **IO Card Statistics**: Includes information such as Ambient Temperature, DIMM Temperature, and Processor Temperature.

### Motherboard Page

This page displays the following tables with motherboard statistics:

- **Motherboard Power Statistics Table**: Includes information such as the Consumed Power, Input Current, and Input Voltage.
- **Motherboard Temperature Statistics Table**: Includes information such as Temperature Sensor IO, Temperature Sensor Rear, Temperature Sensor Rear L, and Temperature Sensor Rear R.

### Processor Page

This page displays the **Processor Environment Statistics Table**, which for example includes the **current, average, maximum, and minimum** value of the **input current and temperature**.

### Ethernet Statistics Page

This page displays several Ethernet statistics tables, for example:

- **Error Statistics Table**: Includes the columns Align, Deferred Tx, Frame Check Sequence, Internal MAC Rx, Internal MAC Tx, and Out Discard.
- **Loss Statistics Table**: Includes the columns SQE Test Delta, Carrier Sense, Excess Collision, Giants, and Late Collision.
- **Pause Statistics Table**: Includes the columns Receive Pause, Resets, and Transmit Pause.

### Interface Detailed Page

This page displays the Interface Details Table, in which you can among others find the following information:

- **Name**
- **Bandwidth**
- **Utilization**
- **Utilization Percentage**
- **Type**
- **MTU**
- **Duplex**
- **Physical Address**
- **Administrator Status**
