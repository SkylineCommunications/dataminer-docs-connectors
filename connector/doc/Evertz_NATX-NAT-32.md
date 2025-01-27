---
uid: Connector_help_Evertz_NATX-NAT-32
---

# Evertz NATX-NAT-32

This connector communicates with the layer of the NATX to get information about the LAN to WAN and WAN to LAN cores and flows.

## Configuration

### Connections

#### SNMP Main Connection

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

The data in this connector is divided into two main sections: **LAN to WAN** and **WAN to LAN**.

In the **Core Configuration Page LAN to WAN or WAN to LAN**, a table displays the number of supported cores and their status. Depending on the core's status, the flow information is polled.

The connector only polls information for cores that are enabled and displays flow information exclusively for cores and flows that are enabled. This applies to both the **Input Flow Configuration** and the **Input Flow Translation Configuration**.

On the **General** page, you can find system parameters such as the name, description, and system uptime.
