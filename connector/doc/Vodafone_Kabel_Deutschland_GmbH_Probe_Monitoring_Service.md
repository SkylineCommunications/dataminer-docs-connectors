---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service
description: Explore Probe Monitoring Service in DataMiner, including connector capabilities, operational benefits, and use cases.
---

# Vodafone Kabel Deutschland GmbH Probe Monitoring Service

## About

The Vodafone Kabel Deutschland GmbH Probe Monitoring Service connector monitors and controls the life cycle of an Ethernet stream configured on a probe. Services are created automatically by the Ad Hoc Probe Monitoring Solution.

This connector is an enhanced service connector designed for a specific project and is not intended for general reuse.

## Key Features

- **Automatic Service Creation**: Create and configure the service when a new probe session starts.
- **Session Management**: Review session details and adjust the session end time.
- **Automatic Expiration**: Finish expired sessions and remove their DataMiner services to limit concurrent probe streams.
- **Service Diagnostics**: Inspect related alarms and monitored elements.

## Use Cases

### Managing Temporary Probe Monitoring Sessions

**Challenge**: Temporary probe streams need a defined monitoring period to avoid accumulating concurrent streams.

**Solution**: The connector tracks each session, allows end-time changes, and automatically finishes the session at expiration.

**Benefit**: You can manage temporary monitoring while limiting the number of streams left configured on probes.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service_Technical).
