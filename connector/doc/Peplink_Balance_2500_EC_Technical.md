---
uid: Connector_help_Peplink_Balance_2500_EC_Technical
---

# Peplink Balance 2500 EC

## About

This connector integrates the Peplink Balance 2500 EC device into DataMiner using both HTTP and SNMP communication. It monitors system performance, WAN connectivity, and client activity.

## Configuration

### Connections

#### HTTP Connection – Peplink API

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address or hostname of the device.
- **IP port**: The web interface port (typically *80* or *443*).

#### SNMP Connection – Peplink SNMP

This connector also uses an SNMP connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The IP address of the device.

SNMP Settings:

- **Port number**: Default: *161*.
- **Get community string**: Typically *public*.
- **Set community string**: Typically *public*.

### Initialization

After element creation:

1. Configure username and password.
1. Verify HTTP login status.
1. Ensure SNMP connectivity is operational.

## How to Use

### General Page

This page provides system-level information:

- Firmware Version (Primary and Secondary)
- System Description
- Uptime
- Device Name
- TX Since Last Reboot
- RX Since Last Reboot
- TX Since Installation
- RX Since Installation
- Device Total Memory
- Device Memory Usage
- Memory Usage (%)

### Authentication Page

On this page, you can specify the username and password for the HTTP connection and view the login status.

### WAN Page

This page displays the WAN connections in a table, with the following information:

- Instance
- Interface Name
- Enabled/Disabled
- Status Message
- IP Address
- IP Method
- Gateway
- DNS Server
- Type
- RX
- TX

### Clients Page

This page displays the following information for the connected clients:

- Instance
- IP Address
- Connection Type
- Name
- MAC Address
- Activity
- Download Speed
- Upload Speed

## Notes

- HTTP is used for structured data retrieval and authentication.
- SNMP is used for efficient polling of system metrics.
- Some parameters depend on active WAN links and connected clients.
