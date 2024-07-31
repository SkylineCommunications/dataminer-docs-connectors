---
uid: Connector_help_EATON_9390_UPS
---

# EATON 9390 UPS

This connector is used to monitor the EATON 9390 UPS device.

The energy-efficient Eaton 9390 UPS (formerly Powerware 9390 UPS) provides backup power and scalable battery runtimes in a small footprint for mid-size data centers, medical equipment and other critical systems.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

|Range  | Supported Model | Supported Firmware  |
|---------|---------|---------|
|1.0.0.x     |PXGX UPS + EATON 9390   |2.12         |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *public*).

## How to use

### General

This page displays information about the device, such as the **System Description, System Up Time, System Location, UPS Manufacturer, UPS Software Version**, etc.

### Battery

This page displays monitoring information about the battery, such as the **Battery Status**, **Battery Time Remaining**, **Battery Voltage/Current**, etc.

The **Input** page contains important data regarding the inputs, such as the **Input Source**, **Input Frequency**, **Input Table**, etc.

The **Output** page displays information about the outputs, such as the state of the **Output Source**, **Output Frequency**, **Output Load**, **Output Table**, etc.

The **Bypass**  page, you can find the **Bypass Frequency** and the **Bypass Table**.

### Receptacles

This page displays information on the Receptacles, such as the **Receptacle Table**.

### Environment

This page displays information on the Environment, such as the **Ambient Temp/Humidity**, **Remote Temp/Humidity**, **Contact Sense Table**, etc.

The **Enviroment Settings** page contains configuration parameters for Temparature and Humidity.

### Alarms

This page shows the number of alarms,**Alarms** and the **Alarm Table**. As well as the number of events, **Events** and the **Event Table**.

### UPS Configuration

This page displays information on the configured parameters, such as **Configured Output Voltage**, **Configured Low Output Voltage Limit**, etc.

The **UPS Settings** page button displays configuration parameters for, among others, **shutdown**, **startup** or **reboot** operations.

The **UPS Test** page where you can select a type of test procedure in the **Test Setup** section with the parameter **UPS Test Type**, **UPS Test ID** and **UPS Test Spin Lock**. Additionally you can review the **Results**, such as **UPS Test Battery Status**, **UPS Test Duration**, etc.

The **UPS Topology** page displays information on the topology, such as **Topology Type**, **Topology Machine Code**, **Topology Unit Number**, and **Topology Power Strategy**.

The **UPS Traps** page contains information on the traps, such as **Max Trap Level**, **Send Trap Type**, and **Heartbeat Mins Interval**.

### Web Interface

This page displays the web interface of the device.

The client machine has to be able to access the device. If not, it will not be possible to open the web interface.
