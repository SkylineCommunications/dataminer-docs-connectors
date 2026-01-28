---
uid: Connector_help_Verimatrix_RTES_Pair
---

# Verimatrix RTES Pair

## About

With this connector, you can monitor a redundant pair of **Verimatrix RTES** (Real-Time Encryption System) devices using SNMP. Two SNMP connections are used to connect to the two RTES devices. Through HTTP SOAP communication, the connector also allows you to retrieve the names and key times of the channels that are defined in an Oracle database.

## Key Features

- **Monitor your redundant pair of Verimatrix RTES devices**: Monitor and visualize the state of your two Verimatrix RTES devices side by side.

- **Channel information and health**: Keep track of the state of each individual channel side by side with its redundant counterpart. Channel names and their key times can optionally also be polled from an Oracle database.

- **Configure your redundancy system based on channel health**: You can define stream types and their expected rate intervals, and assign them to the channels of your choosing. Server Preference will dictate which server will have the best conditions for encryption in near real-time, which you can then combine with the redundancy solution of your choosing to reroute the network automatically and assure optimal uptime from your encryption device pair.

- **Main element and separate DVE elements**: This connector will create two separate DVE elements on the same view as the parent element, each one representing and displaying information of a different Verimatrix RTES device connected to it.

- **DCF connections with network switch elements**: The connector supports DCF connections with supported network switch elements. This allows you to track down and change network connections with the pair devices easily during redundancy switches, while being able to visualize the current connection routing each device has been assigned to within the network (currently supported devices/connectors: CISCO Manager, CISCO Nexus).

## Use Case

**Challenge**: Two redundant devices can display fluctuating behavior over time, while expected or unexpected disconnections can occur at a moment's notice and independently from one another. Preferably, this system should provide optimal uptime for its encryption service, as encryption should be handled by the healthiest device at any point in time, ideally with as little human intervention needed as possible.

**Solution**: By setting up and using the provided connector, you can have data of both devices displayed at the same time so both monitoring and server preference can be provided for the current pair of devices. These can then be complemented by a redundancy solution of choice, monitoring the current server preference dictated by the driver, to ensure seamless availability between your pair of encryption devices.

**Benefit**: This solution provides a way to keep a redundant pair of Verimatrix RTES devices in function by analyzing their connection status and channel health states in near real-time, providing the tools necessary for both redundancy and data visualization, unified into a single connector.

## Prerequisites

- **A redundant pair of Verimatrix RTES devices** is required for the connector to operate correctly.

- If you need channel names or key times to be displayed, you will need **an Oracle database with the required information**.

## Technical Reference

For detailed technical information about this connector, refer to the [technical documentation page](xref:Connector_help_Verimatrix_RTES_Pair_Technical).

For information about the DVEs used by the connector, refer to the [DVE documentation page](xref:Connector_help_Verimatrix_RTES_Pair_-_DVE).
