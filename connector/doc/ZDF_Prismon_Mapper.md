---
uid: Connector_help_ZDF_Prismon_Mapper
description: Monitors Rohde & Schwarz Prismon elements and maps active TAP streams to services using configurable URL matching rules.
---

# ZDF Prismon Mapper

## About

The ZDF Prismon Mapper monitors Rohde & Schwarz Prismon elements and automatically maps discovered TAP streams to the correct services. It helps you keep service assignments aligned with the active stream, even when Prismon creates a new stream object after a restart or switchover.

The mapper uses the stream discovery data from the configured Prismon elements and applies service-specific matching rules to identify the correct stream.

## Key Features

- **Automatic TAP stream mapping**: Assigns discovered Prismon streams to the corresponding services without manual intervention.

- **Active stream detection**: Selects the stream that is currently active for each configured service.

- **Resilient stream correlation**: Maintains service assignments when stream object IDs change after a restart or switchover.

- **Flexible matching rules**: Supports HLS and DASH streams, with optional backup and geo criteria.

- **CSV mapping import**: Imports service mapping rules from CSV files, with merge and synchronize options for managing larger configurations.

- **Reduced service churn**: Prevents duplicate updates when a service already references the active TAP stream object.

## Use Cases

### Keeping Prismon Service Assignments Current

**Challenge**: TAP stream object IDs can change after a stream restart or primary/backup switchover, making manual service reassignment unreliable.

**Solution**: The mapper monitors Prismon stream discovery data and automatically assigns the active stream object to the matching service.

**Benefit**: Services remain connected to the correct active stream without manual intervention after a stream change.

### Supporting Multiple Stream Variants

**Challenge**: A deployment can contain multiple stream variants for the same service, including different protocols, geo variants, or backup streams.

**Solution**: The mapper applies configurable protocol, backup, geo, and URL matching rules for each service.

**Benefit**: You can model the stream variants used in your deployment while keeping service mapping behavior predictable.

## Technical Reference

### Prerequisites

- Rohde & Schwarz Prismon elements must be available in DataMiner and expose their stream discovery tables.

- DataMiner version **10.5.0.0 - 15485** or higher is required for the NATS-based column subscriptions used by the mapper.

- Service matching rules must be configured for the services that the mapper needs to update.

> [!NOTE]
> For configuration details and the stream matching workflow, refer to the [technical documentation](xref:Connector_help_ZDF_Prismon_Mapper_Technical).
