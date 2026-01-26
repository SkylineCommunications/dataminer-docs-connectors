---
uid: Connector_help_Verimatrix_RTES_Pair
---

# Verimatrix RTES Pair

## About

With this connector, you can monitor a redundant pair of **Verimatrix RTES** devices using SNMP.

The Verimatrix RTES Pair connector monitors a redundant pair of Verimatrix RTES devices. The **two SNMP connections** are used to connect to the two RTES devices. Through **HTTP SOAP** communication, the connector also allows the user to retrieve the names and key times of the channels that are defined in an Oracle database.

## Key Features

- **Monitor your redundant pair of Verimatrix RTES devices**: You can monitor and visualize the state of your two Verimatrix RTES devices side to side.

- **Channel Information and Health**: You can also montior the state of each individual channel side by side with their redundant counterpart. Channel Names and their Key Times can also be optionally polled from an Oracle database, given the necessary credentials. 

- **Configure your Redundancy system based on Channel Health**: You can define Stream Types and their expected rate intervals, and assign them to the channels of your choosing. Server Preference will dictate which server will have the best conditions for encryption in near real-time, which you can then combine with the redundancy solution of your choosing to redirect the 

- **Main element and separate DVE elements**: This connector will create two separate DVE elements on the same view as the parent element, each one representing and displaying information of a different Verimatrix RTES device connected to it.

- **DCF Connections with Network Switch elements**: The connector also supports DCF connections between itself and supported Network Switch elements. This permits the user to track down and change network connections with the pair devices easily during redundany while being able to visualize the current connection routing each device has been assigned to within the network (currently supported devices/connectors: CISCO Manager, CISCO Nexus).

## Use Cases

### Best used for a redundant pair of Verimatrix RTES devices

**Challenge**: Two redundant devices can display fluctuating behavior over time, while either expected or unexpected disconnections can occur at any time, which should be handled as much as possible by their redundant partner at a moment's notice, and preferentially, automatically.

**Solution**: By setting up and using the provided connector, it is expected for the user to have data of both devices displayed at the same time so both monitoring and server preference can be provided for the current pair of devices, which can then be completed by their redundancy solution of choice.

**Benefit**: This solution provides a way to keep a redundant pair of Verimatrix RTES devices in function by analyzing their connection status and channel health states in near real-time, providing the tools necessary for both redundancy and data visualization to occur, unified into a single driver.

## Technical Reference

### Prerequisites

- **A redundant pair of Verimatrix RTES devices** are required for the connector to operate correctly. Their SNMP connection information should be introduced in the element's settings.

- If Channel Names or Key Times are necessary to be displayed, **both an Oracle database should be ready with the required information and its credentials should be assigned to the correct parameters under the Database Settings page**.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Verimatrix_RTES_Pair_Technical).

## Other References

> [!NOTE]
> For information on the DVEs used by the driver, refer to our [DVE documentation page](xref:Connector_help_Verimatrix_RTES_Pair_-_DVE).
