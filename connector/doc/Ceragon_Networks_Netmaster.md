---
uid: Connector_help_Ceragon_Networks_Netmaster
---

# Ceragon Networks Netmaster

## About

The Ceragon Networks Netmaster connector serves as a bridge to the Ceragon Netmaster Network Management System (NMS), offering a centralized interface for operation and maintenance. By leveraging SNMP polling and trap processing, this connector provides comprehensive monitoring of alarms, redundancy status, and inventory data for a wide range of network elements managed by the Netmaster system. It is designed to enhance visibility by dynamically modeling individual devices as virtual elements within the DataMiner environment.

## Key Features

- **DVEs**: Automatically generates Dynamic Virtual Elements (DVEs) for each device monitored by the NMS, allowing for granular control and visualization.
- **Alarm monitoring**: Retrieves and processes alarms via SNMP polling and supports critical traps such as HeartBeat, Shutdown, and Alarm traps.
- **Inventory management**: Detailed tracking of hardware and software inventory, including serial numbers, article codes, revisions, and memory bank details.
- **Redundancy monitoring**: Includes a Connection Redundancy Status table to track the active, standby, or unreachable status of element connections.
- **EPM provisioning and configuration**: Supports provisioning via CSV file imports and EPM entity integration for automated device configuration and management.

## Use Cases

### Full Visibility on Each Device

- **Challenge**: Gaining clear visibility into the status of specific devices within a large network managed by a central NMS can be difficult when data is aggregated.
- **Solution**: The connector gets the Entity Physical table and creates individual Dynamic Virtual Elements (DVEs) for specific devices based on user selection.
- **Benefit**: Operators gain a focused view of alarms and status for each specific device, isolating issues effectively without losing the context of the central NMS.

### Fast Troubleshooting

- **Challenge**: Ensuring rapid response to critical network faults and hardware changes in real time.
- **Solution**: The connector actively listens for SNMP traps, including netmasterAlarmTrap and netmasterHWInventoryChange, while simultaneously polling for current alarm states.
- **Benefit**: Reduces network downtime by providing immediate notifications of outages, hardware changes, or critical errors, facilitating faster troubleshooting.

### Centralized Inventory Report

- **Challenge**: Maintaining an accurate and up-to-date record of hardware assets and software versions across a distributed network.
- **Solution**: The connector automatically populates Hardware and Software Inventory tables, detailing resources, serial numbers, and firmware versions (for example, R14 Rev. A04).
- **Benefit**: Simplifies asset management and audit processes by providing a centralized, automated inventory report that indicates exactly when data was last updated.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Ceragon_Networks_Netmaster_Technical).
