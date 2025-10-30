---
uid: Connector_help_Utah_Scientific_100_Router_RCPv3
---

# Utah Scientific 100 Router RCPv3

> [!IMPORTANT]
> This connector is deprecated. [Utah Scientific 100 UDS](xref:Connector_help_Utah_Scientific_100_UDS) or [Utah Scientific 100 X](xref:Connector_help_Utah_Scientific_100_X) should be used instead.

## About

The Utah Scientific 100 UDS is a **compact, modular routing/distribution system**. The device can distribute signals like a DA (distribution amplifier) but also route them like a digital switcher.

With this connector, you can monitor and control the router using a **matrix** view.

## Configuration

### Connections

This connector uses both a **serial** and **SNMP** connection.

#### Serial Connection

The serial communication retrieves and updates the crosspoints for the matrix. It requires the following input during element creation:

- **Type of port:** TCP/IP
- **IP address/host**: The IP address of the device.
- **IP port**: The IP port of the device on which you want to communicate.
- **Bus address**: The bus address stores the address of the device.

#### SNMP Connection

The SNMP connection requires the following input during element creation:

- **IP address/host**: The polling IP of the device.
- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public.*
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector has the following data pages:

- **Main View**: Displays the matrix.
- **Device Status**: Shows general information about the device.
- **Web Interface**: Links to the web interface of the device
