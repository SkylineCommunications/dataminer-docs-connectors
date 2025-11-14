---
uid: Connector_help_Benning_MCU_1868
---

# Benning MCU 1868

## About

This is an SNMP connector for the Benning MCU 1868 device.

The connector is designed to retrieve information from the UPS.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 192.168.236.59

SNMP Settings:

- **Port number**: 161

## Usage

### General

Here you can find some general parameters for the device such as **Manufacturer, Software Version, Agent Software Version**, and **Model**. You can also define the **Name** and the number of **Attached Devices**.

At the bottom, of the page there are two page buttons:

- **Configuration**: Allows you to configure the values of the **Input/Output Voltage**, **Input/Output Frequency**, **Low Battery Time**, **Low/High Voltage Transfer Point**, and **Audible Status**. You can also view the current **Output Power** and **Output Apparent Power**.
- **Control**: Contains the various properties that can control the shutdown and restart times and also the reboot duration.

### Battery

On this page, you can see various details related to the **Battery** information.

### Test

Here you can initiate tests for the UPS.

### Input

This page contains the **Input Line Bads**, which represents a count of the number of times the input entered an out-of-tolerance condition as defined by the manufacturer, the **Number of Lines** on the input that corresponds to the number of entries on the table. The table has four columns showing the **Input Frequency**, **Voltage**, **Current**, and **True Power**.

### Output

This page contains the three parameters plus a table. The first contains the present source of output power, the second indicates the current frequency and the last corresponds to the number of lines that also corresponds to the number of entries in the table. The columns provide information about **Output Voltage**, **Current**, **Power**, and **Percentage Load**.

### ByPass

This page shows the **Frequency** of the bypass and the number of lines, which also corresponds to the number of lines in the table, where each column represents respectively the **Voltage**, **Current**, and **Power**.

### Alarms

This page provides an overview of the alarms of the device.
