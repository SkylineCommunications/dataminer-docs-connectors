---
uid: Connector_help_Evertz_TR-4800E
description: "Monitor GPI inputs and control GPO tally outputs of the Evertz TR-4800E tally router, with immediate and scheduled tally automation."
---

# Evertz TR-4800E

## About

The Evertz TR-4800E is an Ethernet-controlled tally router with 32 general-purpose inputs (GPIs) and 48 general-purpose outputs (GPOs). With the +BP16 option, it has up to 64 of each. It is the successor of the TR-3200E.

This connector uses the Quartz protocol over TCP/IP to poll the status of all GPIs and GPOs, process unsolicited tally updates from the device, and switch GPO tallies on or off. Tallies can be switched manually, by Automation scripts, or at a scheduled time through a command table.

## Key Features

- **GPI monitoring**: The status of every general-purpose input is shown in a table and can be monitored for alarms.

- **GPO tally control**: Each general-purpose output can be switched on or off directly from the Outputs table.

- **Real-time updates**: Unsolicited tally changes sent by the device are processed immediately, in addition to regular polling.

- **Tally automation**: Automation scripts can switch several tallies on or off in one command.

- **Scheduled commands**: Tally commands can be scheduled for a specific time, for example to follow a booking, and are executed automatically.

## Use Cases

### On-Air Tally Control

**Challenge**: Studio tally lights and on-air signals must be switched reliably when a production goes live.

**Solution**: Operators switch the GPO tallies from the Outputs table, or an Automation script switches several tallies at once.

**Benefit**: Tally control is centralized in DataMiner, next to the rest of the broadcast chain.

### Booking-Driven Tally Automation

**Challenge**: Tallies need to go on and off at exact times that follow the broadcast schedule, without manual intervention.

**Solution**: An Automation script adds scheduled ON and OFF commands to the command table, and the connector executes them at the scheduled time.

**Benefit**: Fewer manual actions and fewer mistakes during live transitions.

### GPI Status Monitoring

**Challenge**: Contact closures from external equipment are only visible on the device.

**Solution**: The connector polls and shows the status of every GPI, and updates it as soon as the device reports a change.

**Benefit**: Operators see GPI changes in DataMiner and can use them for alarms and correlation.

## Technical Reference

### Prerequisites

- **An Evertz TR-4800E** reachable over TCP/IP from the DataMiner Agent, with Quartz control enabled.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Evertz_TR-4800E_Technical).
