---
uid: Connector_help_Precise_Time_and_Frequency_1226_Technical
---

# Precise Time and Frequency 1226

This connector is designed to interface with the Precise Time and Frequency 1226 system, providing users with access to its high-precision time and frequency signals through SNMP and Telnet protocols. The connector allows the monitoring and configuration of the system's parameters, ensuring accurate and reliable operation.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

When you have created a new element, go to the **Configuration** > **Credentials** page and make sure the Telnet credentials are configured correctly.

## How to Use

The **Configuration** page includes the following settings:

- **Credentials**: The Telnet credentials to connect to the system must be specified here. This is crucial for Telnet functionality.
- **Module Polling**: Allows you to enable polling for each module if the device includes that module.
- **Telnet Settings**: Allows you to adjust polling state, timer, and timeout according to your preferences.

The **Operational Status** page contains three tables:

- **Input Config Table**: The table where you can configure the *Role* and the *Source* for the Channels in use. 
- **Output Channel Status Table**: The table where the output channel statuses can be monitored. You are also able to activate or inactivate individual channels with the *Activate/Inactivate* column.
- **Input/Aux Channel Status Table**: The table where the input and auxilary channel statuses can be monitored. You are also able to activate or inactivate individual channels with the *Activate/Inactivate* column.

The **Analog Readings** page contains three tables to monitor the voltages of each of the output, input and auxilary channels.

The **Advance Configuration** page constains the overall status of the device and the *Reset* button, to reset the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. It provides a comprehensive set of monitoring and configuration options, similar to the command line interface.
