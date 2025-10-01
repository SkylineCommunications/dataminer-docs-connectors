---
uid: Connector_help_Utah_Scientific_100_X
---

# Utah Scientific 100 X

The **Utah Scientific 100 X** is a connector that control and presents the router in a **Matrix** view.

## About

The **Utah Scientific 100 X** is a **Compact HD/SDI Router** that is complant with the various SDI formats: SD-, HD- and 3G-SDI (SMPTE 259M, 292M and 424M). It comes in different models and have a routing capacity of 8x8 or 16x16. It also allows you to route inputs to outputs across different levels.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main]   | Initial version | Yes                 | Yes                     |


## Installation and configuration

This connector uses both **Serial** and **SNMP**. The Serial communication retrieves and updates the crosspoints for the Matrix. The SNMP communication is used to poll the **Device Status**.

### Serial
- **Type of port:** TCP/IP

- **IP address/host**: the IP Address of the device

- **IP port**: This is the **IP Port** of the device on which you want to communicate.

- **Bus address**: The **Bus address** stores the address of the device.

### SNMP
- **IP address/host**: The polling IP of the device.

- **Port number**: The port of the connected device, by default *161*.

- **Get community string**: The community string used when reading values from the device, by default *public.*

- **Set community string**: The community string used when setting values on the device, by default *private*.

## Usage

### Main View

The **Main View**, Displays the **Matrix**.

### Device Status

The **Device Status** page shows **General Device Information**.

## Web Interface
Links to the **web interface** of the device
