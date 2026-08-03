---
uid: Connector_help_Touchstream_StreamCAM
---

# Touchstream StreamCAM

## About

The **Touchstream StreamCAM** connector provides HTTPS-based integration between DataMiner and the Touchstream StreamCAM cloud stream monitoring platform. It enables DataMiner to monitor the health and availability of live and VOD streams, provision the channels, products, stream types and streams that are being monitored, and schedule planned outages and events, all from within DataMiner dashboards and low-code apps.

## Key Features

- **Cloud-based stream monitoring**: Retrieves live stream status, per-bitrate detail and manifest health from the Touchstream StreamCAM API over HTTPS.
- **Availability and reliability metrics**: Exposes availability percentages, outage counts, outage duration, MTBF and MTTR for any configured time period.
- **End-to-end provisioning**: Allows you to add, edit and delete channels, products, stream types and streams directly from DataMiner, without switching to the StreamCAM web interface.
- **VOD monitoring with selective polling**: Monitors VOD status, detailed VOD status and manifest trawl failures, and lets you disable VOD polling for data sources that do not support it.
- **Outage and event scheduling**: Schedules planned outages and events against one or more streams, with a tree view showing the impacted streams.

## Use Cases

### Use Case 1

**Challenge**: Stream health data lived in the StreamCAM portal, separate from the rest of the delivery chain monitored in DataMiner.

**Solution**: Use the StreamCAM connector to bring live status, per-bitrate detail and manifest health into DataMiner alongside encoders, packagers and CDN data.

**Benefit**: A single operational view of the full delivery chain, so operators can correlate a stream failure with the upstream component that caused it.

### Use Case 2

**Challenge**: Reporting on stream availability required manually exporting statistics from the platform for each reporting period.

**Solution**: The connector exposes availability, outage count, outage duration, MTBF and MTTR for a configurable time period as trended DataMiner parameters.

**Benefit**: SLA and availability reporting is automated and always current, and the same data can feed DataMiner dashboards and reports.

### Use Case 3

**Challenge**: Planned maintenance on a stream generated alarm noise, and provisioning changes required work in a separate portal.

**Solution**: Operators schedule planned outages and manage channels, products, stream types and streams straight from the DataMiner element.

**Benefit**: Fewer false alarms during maintenance windows and a single provisioning workflow, reducing context switching and configuration errors.

## Technical Reference

### Prerequisites

- **Touchstream StreamCAM API V9** is required for the current connector range. Earlier connector ranges target API V5.
- **API credentials**: A valid **Authorization Token** and **X-TS-ID Token** are required for authentication.
- **Network access**: The DataMiner Agent must be able to reach the StreamCAM cloud endpoint over HTTPS (port 443).

> [!NOTE]
> For detailed technical information about the connector, refer to our [technical documentation](https://docs.dataminer.services/connector/doc/Touchstream_StreamCAM_Technical.html).
