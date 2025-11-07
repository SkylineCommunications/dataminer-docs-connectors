---
uid: Connector_help_Utah_Scientific_100_X_Technical
---

# Utah Scientific 100 X

## About

The **Utah Scientific 100 X** is a connector that control and presents the router in a **Matrix** view.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main]   | Initial version | Yes                 | Yes                     |


## Configuration

### Connections

This connector uses both a **serial** and **SNMP** connection.

#### Serial Connection

The serial communication retrieves and updates the crosspoints for the matrix. It requires the following input during element creation:

- **Type of port:** TCP/IP
- **IP address/host**: the IP Address of the device
- **IP port**: This is the **IP Port** of the device on which you want to communicate.
- **Bus address**: The router level. The matrix shows the routing crosspoints of the specified level.

### SNMP

The SNMP communication is used to poll the device status. It requires the following input during element creation:

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
