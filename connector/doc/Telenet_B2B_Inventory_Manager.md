---
uid: Connector_help_Telenet_B2B_Inventory_Manager
---

# Telenet B2B Inventory Manager

## About

The Telenet B2B Inventory Manager connector polls CPE and cable modem inventory from Telenet's B2B inventory APIs and keeps a live view of both estates in DataMiner. It also automatically distributes each polled CPE and modem address to a configured Generic Ping element, so that connectivity monitoring for the full estate can be spread across multiple ping elements without any address ever being monitored by more than one element at a time.

## Key Features

- **Unified CPE and Modem inventory**: Polls both the CPE and cable modem inventory APIs on a single element and presents each estate in its own table.

- **Automatic ping distribution**: Every polled CPE/modem address is automatically assigned to one of the configured Generic Ping elements, load-balanced across whichever element currently has the fewest addresses.

- **Safe, controlled redistribution**: Newly discovered addresses are distributed automatically; existing addresses are only ever moved to a different ping element through an explicit, operator-triggered redistribution action, never silently.

## Use Case

**Challenge**: Operators need to keep continuous connectivity monitoring on a large and constantly changing estate of CPEs and cable modems, spread across multiple Generic Ping elements to keep each element's load manageable.

**Solution**: Use the Telenet B2B Inventory Manager connector to poll the CPE and modem inventory APIs and automatically hand out each address to the least-loaded configured Generic Ping element, with a manual redistribution option to rebalance the estate evenly when needed.

**Benefit**: Removes the need for manual bookkeeping of which ping element monitors which CPE or modem, while guaranteeing that no address is ever pinged from more than one element at the same time.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telenet_B2B_Inventory_Manager_Technical).