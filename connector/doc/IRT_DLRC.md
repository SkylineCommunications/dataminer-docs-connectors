---
uid: Connector_help_IRT_DLRC
---

# IRT DLRC

An IRT DLRC (Downlink Redundancy Controller) is a component in satellite communication systems, specifically within the context of satellite ground stations. Its primary function is to ensure the reliability and availability of downlink communication channels from the satellite to the ground station.

This connector is used to monitor and configure an IRT DLRC device and supports both a 1:2 and 1:1 redundancy system.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMPv3 Settings:

- **Username**: The SNMPv3 username.
- **Security level**: The SNMPv3 security level.
- **Authentication type**: The SNMPv3 authentication type.
- **Authentication password**: The SNMPv3 authentication password (default: *public*).
- **Privacy type**: The SNMPv3 privacy type.
- **Privacy password**: The SNMPv3 privacy password (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector has a total of 6 pages, 4 of which are always visible.

The first page is **General**, which contains general system parameters.

The next page depends on the type of system used:

- If the device has a 1:2 redundancy system, the **1:2 Redundancy** page is displayed. This page contains monitoring and configuration parameters related to the 1:2 redundancy system, such as frequency band selection and switchover.
- If the device has a 1:1 redundancy system, the **1:1 Redundancy** page is displayed. This page contains configuration parameters related to the 1:1 redundancy system.

The **Alarms** page displays a table listing system alarms and device alarms.

The **Modules** page displays a table listing the device's modules.

There is also a **Web Interface** page, which displays the web interface of the device. Note that the client machine must be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

It is important that the parameter **Product Name** (on the web interface) and the **Description** (on the General page) contain the system type designation as the first part of the name, because there is no parameter that clearly indicates which system is used.
