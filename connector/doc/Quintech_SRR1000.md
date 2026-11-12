---
uid: Connector_help_Quintech_SRR1000
description: "Learn how to use the Quintech SRR1000 connector in DataMiner to monitor and control input routing and assign custom labels to signal sources."
---

# Quintech SRR1000

## About

The **Quintech SRR1000** connector brings your Quintech IF switching unit into DataMiner, giving you a single place to see and control which input is routed to your output.

## Key Features

- **Switch inputs in one click**: Change the routed input straight from DataMiner, without any need for separate control software.

- **Always know what is connected**: The current routing is kept up to date at all times, so you always know exactly what is active.

- **Name your inputs**: Give each input a custom label, so you recognize sources by name instead of by number.

## Use Cases

### Centralized Switching Control

**Challenge**: Operators need to reroute signals through the Quintech SRR1000 switch without relying on separate vendor software.

**Solution**: Switching is available directly from DataMiner, next to everything else operators already monitor.

**Benefit**: One tool to monitor and control, saving time and reducing the risk of mistakes.

### Instant Insight Into What Is Routed

**Challenge**: Operators need to know at a glance which input is currently active, without checking the device itself.

**Solution**: The current routing is always visible in DataMiner.

**Benefit**: Operations teams always have an accurate, up-to-date view of the signal path.

## Technical Reference

### Prerequisites

- A **serial connection** to the Quintech SRR1000 unit is needed to poll and control the device.

- The device **bus address** must be known so the connector can address the correct unit on a shared serial bus.
