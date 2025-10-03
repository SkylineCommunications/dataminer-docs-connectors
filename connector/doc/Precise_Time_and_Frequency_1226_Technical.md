---
uid: Connector_help_Precise_Time_and_Frequency_1226_Technical
---

# Precise Time and Frequency 1226

The Precise Time and Frequency 1226 connector is designed to interface with the Precise Time and Frequency 1226 Time and Frequency System, providing users with access to its high-precision time and frequency signals through SNMP and Telnet protocols. The connector allows the monitoring and configuration of the device's parameters, ensuring accurate and reliable operation.

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

When you have created a new element, make sure all necessary SNMP settings and Telnet credentials are properly configured.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. It provides a comprehensive set of monitoring and configuration options, similar to the command line interface.

## How to Use

In the **Configuration** page:

- **Credentials**: Enter the required Telnet credentials. This is crucial for Telnet functionality.
- **Module Polling**: Enable polling for each module if the device includes that module.
- **Telnet Settings**: Adjust polling state, timer, and timeout according to your preferences.


