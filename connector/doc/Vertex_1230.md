---
uid: Connector_help_Vertex_1230
---

# Vertex 1230

The Vertex 1230 connector is a **virtual** connector that can interact with **Ethernet remote I/O control** devices.

Note: Version 2.0.0.1 of the connector is designed to work with **Moxa ioLogic E1214**.

The Moxa ioLogic E1214 manages 6 digital input channels and 6 relay output channels supporting a 3k VDC isolation, supports Modbus/TCP protocol, and handles 2 Ethernet ports to be able to switch for daisy chain topologies.

## About

The connector has been designed to display information on and allow management of Ethernet remote I/O control devices.

Note: To be able to manage the configuration, you must make sure **Ambient temperature status** is set to *On*, and **Mode** is set to *Remote*.

### Version Info

| Range | Description                                                                 | DCF Integration | Cassandra Compliant |
|-----------|---------------------------------------------------------------------------------|---------------------|-------------------------|
| 1.0.0.x   | Initial version.                                                                | No                  | No                      |
| 1.1.0.x   | Alarm tag to Ref Stage Heat 2.                                                  | No                  | No                      |
| 2.0.0.x   | Changed behavior of operational validation for:<br>- Ref Stage Heat 1 & 2<br>- Feed Sub<br>- Control Mode<br>Added Ambient Temperature Manual control. | No                  | No                      |

## Installation and configuration

This connector uses a virtual connection.

Element connections between Ethernet remote I/O devices must be configured when the element is created in order to establish the input/output relationship between channels.

## Usage

### Main View page

This page displays the following general status parameters:

- **Power Status**
- **Ice Detection Status**
- **Ambient Temperature Status**
- **On Fault**
- **Reference Stage Heaters**
- **Feed/Sub Heat Status**
- **Mode**
- **Control Mode**

### General page

This page displays the following status values, which can also be configured:

- **Reference Stage Heaters**
- **Feed/Sub Heat**
- **Control Mod**
- **Ambient Temperature**
