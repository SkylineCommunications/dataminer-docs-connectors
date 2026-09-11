---
uid: Connector_help_Telenet_Casa_Systems_C100G_Video_Monitoring
---

# Telenet Casa Systems C100G Video Monitoring

## About

The **Telenet Casa Systems C100G Video Monitoring** connector provides centralized, real-time visibility on the video-delivery performance of Casa Systems C100G platforms across a multi-cluster DataMiner deployment. Instead of connecting directly to the device, it collects the video KPIs of an existing Casa Systems C100G element that lives on another DataMiner Agent, using the DataMiner Web Services API. This makes it possible to consolidate video-quality monitoring from several DataMiner System (DMS) clusters into a single, unified overview.

## Key Benefits

- **Cross-DMS video visibility**: Aggregate the video KPIs of Casa Systems C100G elements running on remote DataMiner Agents into one central element, without direct device access.

- **Video-quality assurance**: Follow QAM port utilization, channel statistics, input-port activity and per-session KPIs (bitrate, jitter, continuity and sync errors) to safeguard the subscriber video experience.

- **Proactive fault detection**: Rely on alarming and trending on key video KPIs and session states to detect degradations before they impact customers.

- **Simple onboarding**: The remote element is resolved automatically from its name, so a single element name is enough to start collecting data.

- **Controlled polling**: A built-in Polling Manager lets you tune polling cycles per data set and trigger an immediate refresh when needed.

## Use Cases

### Centralized Video KPI Overview

The connector aggregates the video-delivery status of a remote Casa Systems C100G platform, giving operators a single place to follow QAM ports, channel statistics and input ports without switching between DataMiner clusters.

![Telenet Casa Systems C100G Video Monitoring General](~/connector/images/telenet_casa_systems_c100g_video_monitoring_marketing_general.png)

### QAM Port and Channel Monitoring

On the Video Overview page, the connector exposes per-QAM-port bandwidth utilization and per-channel active-session counts, helping operators spot congestion and capacity issues on the edge-QAM side of the platform.

![Telenet Casa Systems C100G Video Monitoring Video Overview](~/connector/images/telenet_casa_systems_c100g_video_monitoring_marketing_video_overview.png)

### Per-Session Quality Analysis

The Video Sessions page provides detailed per-session KPIs such as detected and requested bitrate, jitter, continuity errors and sync-loss counters, enabling fast root-cause analysis of individual video sessions.

![Telenet Casa Systems C100G Video Monitoring Video Sessions](~/connector/images/telenet_casa_systems_c100g_video_monitoring_marketing_video_sessions.png)

## Technical Reference

This connector uses an HTTP connection to the DataMiner Web Services API and requires authentication and the name of the remote element before it can start collecting data.

> [!NOTE]
> For detailed technical information, refer to the [technical information](xref:Connector_help_Telenet_Casa_Systems_C100G_Video_Monitoring_Technical).
