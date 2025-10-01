---
uid: Connector_help_Utah_Scientific_100_Router_RCPv3
---

# Utah Scientific 100 Router RCPv3

> [!IMPORTANT]
> This connector is deprecated. [Utah Scientific 100 UDS](xref:Connector_help_Utah_Scientific_100_UDS) or [Utah Scientific 100 X](xref:Connector_help_Utah_Scientific_100_X) should be used instead.

The **Utah Scientific 100 Router RCPv3** is a connector that control and presents the router in a **Matrix** view.

## About

The **Utah Scientific 100 UDS** is a **compact, modular routing/distribution system**. The device can distribute signals like a DA (distribution amplifier) but also route them like a digital switcher. Coming in different capacity 32x32. 64x64 and 144x144.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.1.1.x [100 X Series]   | Initial version | Yes                 | Yes                     |
| 1.1.0.x [100 UDS Series]   | Initial version | Yes                 | Yes                     |


## Installation and configuration

This connector uses both **Serial** and **SNMP**. The Serial communication retrieves and updates the crosspoints for the Matrix.

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
