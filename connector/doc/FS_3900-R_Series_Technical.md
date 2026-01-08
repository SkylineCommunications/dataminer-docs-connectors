---
uid: Connector_help_FS_3900-R_Series_Technical
---

# FS 3900-R Series

## About

The FS 3900-R Series switches is a 10GE switch with 24 or 48 1G ports. This connector listens for interface data from the device, and reads the status and errors of the device.

The detailed interface table is taken from the Skyline SNMP Example driver.

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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element has the following data pages:

- **General**: Displays the device information.
- **Detailed Interface Info**: Displays information about the switch interfaces.
- **Raw Tables**: Displays unprocessed information about the switch interfaces before being displayed to the Detailed Interface Info page.
- **NTP**: Displays the NTP parameters if they are present.
- **DHCP Server**: Displays the availablility of the DHCP Server and the DHCP IP Address information.
- **IP Addresses**: Displays the IP Addresses and IP Routes.
- **VLAN**: Displays the VLAN Static information.
- **STP**: Displays the Transparent Bridging Ports and STP Ports information.
