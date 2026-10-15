---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_WM_Technical
---

# Telefonia por Cable S.A de C.V. Ticketing WM

## About

The Telefonia por Cable S.A de C.V. Ticketing WM connector is a virtual DataMiner element that
periodically evaluates critical-incident aggregations produced by the
Telefonia por Cable S.A de C.V. Topology Aggregator element, turns qualifying incidents into
tickets, enriches them with branch/region context, and forwards them to one or more
Telefonia por Cable S.A de C.V. Ticketing BE elements over InterAppCalls.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you have created the element, configure the following parameters on the **Configuration**
page:

- **Aggregation Polling Time**: How often the aggregation data on the Topology Aggregator element
  is polled to build new tickets (default: *3600 seconds*).
- **Ticket Retention Time**: How long a ticket remains in the Tickets Overview table before being
  deleted (default: *3600 seconds*; set to *0* for *Real Time*, i.e. no retention).
- **Critical SNR Low/High Thresholds**, **Critical US Low/High Thresholds**, and
  **Critical DS Low/High Thresholds**: The threshold values that qualify an aggregated
  SNR/upstream/downstream row as a critical incident worth ticketing.

## How to use

This connector retrieves critical-incident data from the **SNR Upstream Channel Aggregation**,
**DS Service Group Aggregation**, and **US Service Group Aggregation** tables on the
Telefonia por Cable S.A de C.V. Topology Aggregator element, and builds a ticket for every
aggregation row that qualifies as a critical incident against the configured thresholds.

Ticket calculation self-throttles based on the configured **Aggregation Polling Time** rather than
relying purely on the timer interval, so the effective polling cadence can be tuned independently.
A poll can also be forced immediately via **Force Aggregation Poll** on the **General** page.

Every new ticket is enriched with branch, region, and subregion metadata from the
**Branches** table before being processed. Once processed, tickets are sent via InterApp
communication to all available Telefonia por Cable S.A de C.V. Ticketing BE elements.

Tickets older than the configured **Ticket Retention Time** are automatically removed from the
**Tickets Overview** table.

As this is a virtual connector, **no data traffic** will be shown in **Stream Viewer**.

### General Page

This page displays the overall polling and ticketing status, including:

- **Aggregation Polling Status** and **Ticketing State**.
- **Last Aggregation Polling**, **Last Successful Aggregation Polling**, and
  **Last Aggregation Ticket Count**.
- **Force Aggregation Poll**, to trigger an immediate aggregation poll outside the configured
  interval.

### Tickets Page

This page displays the **Tickets Overview** table, containing one row per detected/ticketed
incident with its entity, entity type, alarm type, last aggregation update, received date, alarm
count, state, ticket information, and completed date.

### Branches Page

This page displays the **Branches** table (branch ID, region, and subregion), used to enrich
tickets with location context. Branches can be maintained interactively via the context menu
(add/edit/delete/clear), or refreshed in bulk by specifying an **Import File Path** and triggering
**Import Branches File**.

### Configuration Page

This page exposes the polling cadence, ticket retention, and critical-threshold parameters
described under [Configuration](#configuration) above.

## Prerequisites

- A **Telefonia por Cable S.A de C.V. Topology Aggregator** element (Production version, active)
  must be present, since ticket calculation reads its aggregation/topology tables.
- One or more **Telefonia por Cable S.A de C.V. Ticketing BE** elements (Production version,
  active) must be present to receive tickets via InterAppCalls.
