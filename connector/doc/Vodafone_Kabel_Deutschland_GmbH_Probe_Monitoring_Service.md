---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service
description: "Explore key features and use cases of the Vodafone Kabel Deutschland GmbH Probe Monitoring Service connector for probe stream lifecycles in DataMiner."
---

# Vodafone Kabel Deutschland GmbH Probe Monitoring Service

## About

The Vodafone Kabel Deutschland GmbH Probe Monitoring Service connector monitors and controls the lifecycle of an Ethernet stream configured on a probe. Services are created automatically by the **Ad Hoc Probe Monitoring Solution**.

This connector is an enhanced service connector designed for a specific project and is not intended for general reuse.

## Key Features

- **Automatic service creation**: A service is created and configured when a new probe session starts.
- **Session management**: Review session details and adjust the session end time.
- **Automatic expiration**: Expired sessions are finished and their DataMiner services are removed to limit concurrent probe streams.
- **Service diagnostics**: Inspect related alarms and monitored elements.

## Use Cases

### Managing Temporary Probe Monitoring Sessions

**Challenge**: Temporary probe streams need a defined monitoring period to avoid accumulating concurrent streams.

**Solution**: The connector tracks each session, allows end-time changes, and automatically finishes the session at expiration.

**Benefit**: You can manage temporary monitoring while limiting the number of streams left configured on probes.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Probe_Monitoring_Service_Technical).
