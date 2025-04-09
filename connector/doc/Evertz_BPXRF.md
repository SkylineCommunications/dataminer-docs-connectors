---
uid: Connector_help_Evertz_BPXRF
---

# Evertz BPXRF

The **Evertz BPXRF** connector is used to monitor and control an Evertz chassis containing two Evertz 7703 cards.

## About

This connector monitors the input and output of different Evertz cards inside a single chassis.

Supported Cards:

- Evertz 7703PA
- Evertz 7703BPX

15 slots are available, which means that 14 cards can be added. Slot zero is reserved for the frame carrier.

Data is polled via SNMP protocol.


## Key Features

- **Monitor and control both BPXRF and 7703PA cards**: With this driver, you have multiple pages for both the Evertz BPXRF and the Evertz 7703-PA cards.
- **View and configure faults**: With multiple fault statuses across both cards, you can easily monitor and control various fault types.


## Use Case

- **Challenge**: User has multiple BPXRF/7703PA cards under one frame.
- **Solution**: User can use this connector to monitor and control all their cards under one connector.
- **Benefit**: Includes DVE tables for separate monitoring/views of each card.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for the Evertz BPXRF, refer to the [Technical help page](xref:Connector_help_Evertz_BPXRF_Technical).
