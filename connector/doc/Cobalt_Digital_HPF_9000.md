---
uid: Connector_help_Cobalt_Digital_HPF_9000
---

# Cobalt Digital HPF 9000

## About

This connector uses SNMP communication to monitor the Cobalt Digital HPF 9000, a modular openGear frame controller. It monitors the frame chassis — power supplies, network configuration, and overall frame status — and detects the openGear cards installed across the frame's slots. Each active card can be published as its own Derived Virtual Element (DVE), so operators get one dedicated child element per physical card, showing that card's detailed data alongside a single unified view of the whole frame.

## Key Features

- **Frame chassis monitoring**:

  - Real-time frame status, power supply, and network configuration monitoring.
  - Slot inventory overview showing which openGear card occupies each frame slot.

- **Per-card monitoring via DVEs**:

  - Automatic detection of installed cards from the slot inventory.
  - One DVE child element per active card, exposing that card's detailed parameters and tables.
  - On-demand DVE creation and deletion per slot, with a clear-all control.
  - Supported card families: **9001**, **9121**, **9410DA** (product info, status, routing, SFP, and crosspoint routing), and **9220 (MVN-MX260)**.

- **Adaptive polling and display**:

  - A Card Display page with an Auto-Detect master that shows and polls only the card types actually present in the frame.
  - Per-card show/hide and polling controls, so absent or irrelevant cards add no SNMP load and never clutter the UI.

## Use Cases

### Centralized openGear Frame Monitoring

**Challenge**: An openGear frame hosts many independent processing cards, each with its own data, but operators need a single, consistent view of the whole chassis and its health.

**Solution**: The connector polls the frame controller for power, network, and frame status, and builds a slot inventory that identifies every installed card in one element.

**Benefit**: Provides a single pane of glass for frame health and slot occupancy, making it easy to spot power or connectivity issues affecting the entire chassis.

### Card-Level Visibility Without Clutter

**Challenge**: Operators responsible for a specific processing card need detailed, card-focused monitoring without wading through data for every other slot in the frame.

**Solution**: Each active card is exported as its own DVE child element keyed to its slot, presenting that card's parameters and tables on a clean, dedicated element.

**Benefit**: Teams can monitor, alarm, and build workflows around individual cards independently, while the parent element retains the full frame overview.

### Efficient Monitoring of Mixed-Card Frames

**Challenge**: Frames are rarely fully populated or uniform, and polling data for card types that are not present wastes bandwidth and adds noise.

**Solution**: The Auto-Detect feature derives the installed card types from the slot scan and conditionally enables the matching card pages and polling groups; absent card types are hidden and skipped entirely.

**Benefit**: Reduces unnecessary SNMP traffic and keeps the interface focused on the cards that actually exist in each frame, with no manual configuration required.

## Technical Reference

> [!NOTE]
> For setup and configuration instructions, refer to the [technical documentation](xref:Connector_help_Cobalt_Digital_HPF_9000_Technical).
