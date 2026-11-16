---
uid: Connector_help_Eltek_Smartpack_S
---

# Eltek Smartpack S

## About

The Eltek Smartpack S is a controller that allows you to monitor and control DC power systems. The connector polls device data over SNMP and provides access to the device's web interface. Optional log-file retrieval is available over HTTP or FTP.

## Configuration

### Connections

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

#### HTTP secondary connection

This connector also uses a secondary HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: *BypassProxy*.

### Log Retrieval

The **Connection Use for Retrieve Log File** parameter defaults to **Only SNMP**, which does not retrieve a log file. Select **HTTP** or **FTP** to enable file retrieval.

For HTTP retrieval, enter the device's web-interface username and password. The connector encrypts the password for the login request. Set **Name of the Log File** to the file name without its extension.

The **Force Fetch Log** action is triggered when **Status of Element** is nonzero, including **Running**, **Fetching File...**, or **Timeout...**. It is ignored when the status is 0.

### Configuration of normal or lite mode

This connector can be run in **NORMAL** mode (default) or in **LITE** mode. In **LITE** mode, only a very limited number of parameters is polled, so that less data traffic is generated.

To toggle between **NORMAL** mode and **LITE** mode, click the **LITE Protocol** toggle button on the **System Overview** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector consists of different pages that cover the various subsections that can be monitored/controlled for this device. You can find more information on these below.

### System Overview

This page displays general information about the device, such as the general **Status**, the physical **Location**, **Information** about the **System Model**, and the **Units** that are used.

The **Access Configuration** controls include the log-retrieval settings and **Status of Element**. Use **Device HTTP IP** to set the address used to access the device's web interface.

### Lite Mode

This page displays **Status** parameters and information related to **Current System, Tenant Power, Flexi Monitor Input Table**, and **Generator Runtime.** The **Generator Runtime Day** and **Generator Runtime Week** can be reset instantly using the **Reset Generator Runtime** button.

### Mains

This page displays information about the **Mains**, such as the **Mains Status**, the **Energy Log**, and the **Outage Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Monitors Tables**, **Outage Tables**, and **Voltage Table** provide access to a number of tables.

### Generator

This page displays information about the **Generator**, such as the **Generator Status**, the **Energy Log**, **Run Hours Log**, and the **Fuel Consumption Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Energy Log Tables**, **Run Hours Tables**, and **Daily Run Setup Table** provide access to a number of tables.

### Rectifiers

This page displays information about the **Rectifiers**, such as the **Rectifiers Status** and the **Energy Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Energy Log Tables** and **Rectifier Table** provide access to a number of tables.

### Solar Chargers

This page displays information about the **Solar Chargers**, such as the **Solar Chargers Status** and the **Energy Log**.

The page contains two page buttons. The **Configuration** page button provides access to all configurable parameters. The page button **Energy Log Tables** provides access to a number of tables.

### DCDC

This page displays information about the **Dcdc**, such as the **Dcdc Number of Groups**.

The **Tables** page button provides access to Dcdc-related tables.

### Wind Chargers

This page displays information about the **Wind Chargers**, such as the **Wind Chargers Status** and the **Energy Log**.

The page contains two page buttons. The **Configuration** page button provides access to all configurable parameters. The page button **Energy Log Tables** provides access to a number of tables.

### Load

This page displays information about the **Load**, such as the **Load Status** and the **Energy Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Energy Log Tables, Group Table, LVLD Table, Fuse Table**, and **Voltage Table** provide access to a number of tables.

### Battery

This page displays information about the **Battery**, such as the **Battery Status,** the **Energy Log**, and the **Cycle Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Bank Tables, Monitor Tables, Energy Log Tables**, and **Cycle Log Tables** provide access to a number of tables.

### Battery Group 2

This page displays information about the **Battery Group 2**, such as the **Battery Group 2 Status**, the **Energy Log**, and the **Cycle Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Energy Log Tables** and **Cycle Log Tables** provide access to a number of tables.

### Inputs

This page displays the **Input Control Unit Tables**, with parameters such as **Status** and **Value**.

### Outputs

This page displays the **Output Control Unit Tables**, with parameters such as **Status** and **Description**.

### Control System

This page displays information about the **Control System**, such as the **Control System Status** and the **Energy Log**.

The page contains two page buttons. The **Configuration** page button provides access to all configurable parameters. The **Tables** page button displays information about the units, such as the **Serial Number**, **HW Version**, **Temperature**, and **Earth Fault.**

### Alarm Groups

This page displays each alarm group's **Status** and **Description**. Alarm Group status alarms include the **IG Code**, **IG Description**, **Node IP Address**, **Node Name**, and **Alarm Description** properties. **Alarm Description** is taken from the alarm group's Description column.

### Inverters

This page displays information about the **Inverters**, such as the **Energy Log** and the **Reactive Energy Log**.

The page contains a number of page buttons. The **Configuration** page button provides access to all configurable parameters. The page buttons **Energy Log Tables** and **Reactive Energy Log Tables** provide access to a number of tables.

### Rectiverters

This page displays rectiverter status and measurements, including DC current, AC output currents and voltages, temperature, and frequency deviation. Related alarm settings are available in the Rectiverters configuration.

### Polling Settings

Use the polling controls to enable or disable polling for supported subsystem pages. These controls are enabled by default.
