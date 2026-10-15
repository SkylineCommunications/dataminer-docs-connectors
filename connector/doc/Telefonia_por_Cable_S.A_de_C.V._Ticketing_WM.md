---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_WM
---

# Telefonia por Cable S.A de C.V. Ticketing WM

## About

The **Telefonia por Cable S.A de C.V. Ticketing WM** connector is a virtual DataMiner element that
acts as the middleware between infrastructure health monitoring and the customer's ticketing
back end. It periodically evaluates critical-incident aggregations produced by the
Telefonia por Cable S.A de C.V. Topology Aggregator element, turns qualifying incidents into
tickets, enriches them with branch/region and topology context, and forwards them to one or more
Telefonia por Cable S.A de C.V. Ticketing BE elements over InterAppCalls.

- **IntegrationID:** DMS-DRV-9278
- **Element type:** Ticketing System (virtual — no physical device connection)

## Key Features

- **Automated ticket creation**: detects critical SNR/upstream/downstream service-group incidents
  from aggregated topology data and automatically raises a ticket, with no manual triage required.

- **Branch/region enrichment**: every ticket is annotated with the branch, region, and subregion it
  belongs to, using a maintainable Branches table (context-menu managed or bulk-imported from CSV).

- **Configurable thresholds and retention**: critical SNR/US/DS thresholds and ticket retention
  time are all exposed as element parameters, so behavior can be tuned per deployment without code
  changes.

- **Self-throttling polling**: ticket calculation only re-runs once the configured aggregation
  polling interval has elapsed (or on a forced poll), avoiding unnecessary load on the aggregator
  element.

- **Resilient integration**: every processing step is wrapped in structured error handling that
  surfaces failures back onto element parameters/logs instead of failing silently, and stale
  tickets are cleaned up automatically after a configurable retention period.

## Use Cases

### Turning infrastructure alarms into actionable tickets

**Challenge**: Critical service-impacting incidents (SNR, upstream, downstream) are visible in
topology/aggregation data, but operators still need a manual step to translate that data into a
trackable ticket in the back-end ticketing system.

**Solution**: The connector polls the aggregation element on a configurable interval, identifies
new critical incidents, and automatically creates a corresponding ticket row with all the context
(entity, entity type, alarm type, branch/region) needed by support teams.

**Benefit**: Faster time-to-ticket, consistent ticket content, and no incidents missed due to
manual monitoring gaps.

### Keeping the branch/region reference data in sync

**Challenge**: Ticket routing and reporting depend on up-to-date branch/region/subregion metadata,
which can change over time and is impractical to hardcode.

**Solution**: The Branches table can be maintained interactively (add/edit/delete/clear via the
element's context menu) or refreshed in bulk by importing a CSV file.

**Benefit**: Ticket enrichment stays accurate without requiring a connector update whenever the
branch topology changes.

## Technical Reference

> [!NOTE]
> For setup and configuration instructions, refer to the [technical documentation](xref:Connector_help_Telefonia_por_Cable_S.A_de_C.V._Ticketing_WM_Technical).

