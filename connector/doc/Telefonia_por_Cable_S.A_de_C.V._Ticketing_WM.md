---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_WM
description: "Configure Telefonia por Cable S.A de C.V. Ticketing WM to create incident tickets, add branch context, and dispatch them to Ticketing BE elements."
---

# Telefonia por Cable S.A de C.V. Ticketing WM

## About

The **Telefonia por Cable S.A de C.V. Ticketing WM** connector acts as the middleware between infrastructure health monitoring and a ticketing backend. It periodically evaluates critical-incident aggregations produced by the Telefonia por Cable S.A de C.V. Topology Aggregator element, turns qualifying incidents into tickets, enriches them with branch/region and topology context, and forwards them to one or more Telefonia por Cable S.A de C.V. Ticketing BE elements.

- **Integration ID**: DMS-DRV-9278
- **Element type**: Ticketing System (virtual — no physical device connection)

## Key Features

- **Automated ticket creation**: Turns critical service group incidents from aggregated topology data into trackable tickets, without manual triage.

- **Location-enriched tickets**: Adds branch, region, and subregion details to each ticket. Update the Branches table directly or import a CSV to keep location data up to date.

- **Configurable thresholds and retention**: Allows you to fine-tune critical SNR/US/DS thresholds and ticket retention time directly from the element.

- **Efficient polling**: Checks for new incidents when the configured interval elapses, avoiding unnecessary load on the aggregator. You can also trigger polling on demand.

- **Resilient integration**: Uses structured error handling for every processing step and reports failures in element parameters and logs instead of failing silently. Stale tickets are also automatically removed after the configured retention period.

## Use Cases

### Turning Infrastructure Alarms into Actionable Tickets

**Challenge**: Critical service-impacting incidents (SNR, upstream, downstream) are visible in topology/aggregation data, but operators still need a manual step to translate that data into a trackable ticket in the backend ticketing system.

**Solution**: The connector polls the aggregation element on a configurable interval, identifies new critical incidents, and automatically creates a corresponding ticket row with all the context needed by support teams.

**Benefit**: Faster time-to-ticket, consistent ticket content, and no incidents missed because of manual monitoring gaps.

### Keeping the Branch/Region Reference Data in Sync

**Challenge**: Ticket routing and reporting depend on up-to-date branch, region, and subregion metadata, which can change over time and is impractical to hardcode.

**Solution**: You can maintain the Branches table using its context menu or refresh the information in bulk by importing a CSV file.

**Benefit**: Ticket enrichment stays accurate without requiring a connector update whenever the branch topology changes.

## Prerequisites

The DataMiner System must contain the following elements

- A **Telefonia por Cable S.A de C.V. Topology Aggregator** element.
- One or more **Telefonia por Cable S.A de C.V. Ticketing BE** elements.

## Technical Reference

> [!NOTE]
> For setup and configuration instructions, refer to the [technical documentation](xref:Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_WM_Technical).
