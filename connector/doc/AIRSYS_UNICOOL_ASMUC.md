---
uid: Connector_help_AIRSYS_UNICOOL_ASMUC
---

# AIRSYS UNICOOL ASMUC

This connector provides a general overview of parameters related to the HVAC controller and its cooling units. The controller can monitor up to 16 HVAC units.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2.1.049            |

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
- The **SNMP port** is by default set to 161.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector only allows you to view information from the device. It cannot be used to implement changes on the device. The connector will frequently poll the device through its SNMP interface to retrieve real-time parameters such as power consumption, fan speeds, and many alarm states.

On the **Power** page, you can see the instantaneous and average power consumption for each component.

The **Component Run-Time** page shows the run and start times for the HVAC components.

On the **DI-Inputs** page, you can see critical alarms, for example when one of the fans gets clogged with dust, when there is a supply fan overload, etc.

Sensor readings, such as humidity, temperatures, or fan speeds, can be found on the **Sensors** and **Driver Outputs** pages.
