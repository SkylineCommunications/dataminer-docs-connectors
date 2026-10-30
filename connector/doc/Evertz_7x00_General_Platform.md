---
uid: Connector_help_Evertz_7x00_General_Platform
description: Monitor and control an Evertz 7700/7800/7801 chassis and its inserted cards, with SNMP-based polling and trap support.
---

# Evertz 7x00 General Platform

## About

The **Evertz 7x00 General Platform** connector lets you monitor and control an Evertz chassis that hosts a wide range of Evertz 7700/7800-series cards. It communicates with the chassis' Frame Controller (**7700-FC**, **7800-FC**, or **7801-FC**) over **SNMP**, discovering and exposing the cards installed in the surrounding slots. Each supported card is represented as a separate DVE, so you get dedicated, card-specific monitoring alongside a unified view of the whole frame.

## Key Features

- **Automatic card discovery**: The connector polls the Frame Controller to detect which cards are installed in the chassis and automatically creates a DVE for each supported card.

- **SNMP polling with trap support**: Data is retrieved via SNMP, and incoming traps trigger targeted re-polling so you always see up-to-date values without relying on continuous full polling.

- **Broad hardware coverage**: A single platform connector supports dozens of Evertz card types, including distribution amplifiers, up-/down-/cross-converters, fiber transmitters/receivers, decoders, encoders, and RF switching/protection modules.

- **Frame health monitoring**: The **General** page gives you visibility into chassis-level parameters such as temperature and power supply status, while the **Input Cards** page lets you refresh and manage the cards currently present in the frame.

- **Trap logging**: You can enable trap logging per card so that received traps are stored directly in the database for further analysis.

## Use Cases

### Use Case 1

**Challenge**: Broadcast facilities running large Evertz 7700/7800 chassis need a single, reliable view of dozens of interchangeable cards without manually configuring monitoring for every card type.

**Solution**: The connector automatically discovers the cards present in each slot and creates a dedicated DVE per card, so no manual mapping is required when cards are added, removed, or swapped.

**Benefit**: Reduced configuration effort and faster onboarding of new or replaced cards, with monitoring available as soon as a card is detected.

### Use Case 2

**Challenge**: Continuously polling every parameter on every card in a busy frame can create unnecessary network and system load.

**Solution**: The connector relies on SNMP traps to flag changes, triggering a targeted re-poll of only the affected parameter instead of constant full polling.

**Benefit**: Lower polling overhead while still keeping parameter values accurate and up to date in near real time.

### Use Case 3

**Challenge**: Operators need to quickly assess the overall health of a chassis, including environmental conditions and the status of individual cards.

**Solution**: The **General** page surfaces chassis-level health data such as temperature and power supply status, while the **Input Cards** page provides an overview of all installed cards with the ability to refresh their status on demand.

**Benefit**: Faster fault detection and troubleshooting, helping to minimize downtime for critical broadcast signal paths.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Amazon_AWS_CloudWatch_Technical).
