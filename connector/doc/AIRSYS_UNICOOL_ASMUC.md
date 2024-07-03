---
uid: Connector_help_AIRSYS_UNICOOL_ASMUC
---

# AIRSYS UNICOOL ASMUC

Driver contains general overview parameters about the HVAC controller and it's cooling units. 

## About

### Version Info
|Range                  |Features              |Based on  |System Impact  |
|-----------------------|----------------------|----------|---------------|
|1.0.0.x [SLC Main]     |Initial version       |-         |-              |

### Product Info

|Range  |Supported Firmware |
|------------|--------------|
|1.0.0.x     |2.1.049       |

### System Info

In this subsection, insert a table with five columns. Indicate whether the range features **DCF integration** and whether it is **Cassandra compliant**.

In the "Linked Components"; column, list all DataMiner components that have a link, in any way, with this connector range, e.g. mediation connectors, Automation scripts, custom report, etc.

In the "Exported Components" column, list all the connectors that are exported by the parent connector in question.
**This can only be omitted for an exported connector or for a connector that cannot have exported connectors.**

|Range      |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components |
|-----------|-----------------|---------------------|-------------------|--------------------|
|1.0.0.x    |No               |Yes                  |-                  |                    |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**

SNMP port is set by default to 161.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector has no capability to do sets on the device and is for display purposes only. Connector will frequently poll the device through its SNMP interface to retrieve real-time parameters such as power consumption, fan speeds and many alarm states.

The controller can monitor up to 16 HVAC units. Instantaneous and average power consumptions can be seen for each component on the **Power** page.

**Component Run-Time** page has run and start times for the HVAC components. Most critical alarms can be seen on the **DI-Inputs** page (when one of the fans gets clogged with dust, supply fan overload, etc.).

Sensor readings, such as humidity, temperatures or fan speeds, can be found on the **Sensors** and **Driver Outputs** pages.