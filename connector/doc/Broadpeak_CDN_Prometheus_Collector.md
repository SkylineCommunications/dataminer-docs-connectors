---
uid: Connector_help_Broadpeak_CDN_Prometheus_Collector
description: "Explore key features and use cases of the Broadpeak CDN Prometheus Collector connector for monitoring CDN metrics and Grafana alerts in DataMiner."
---

# Broadpeak CDN Prometheus Collector

## About

This connector connects to a Prometheus system monitoring a Broadpeak CDN system and retrieves all metrics that Prometheus provides for the CDN. The metrics are made available in DataMiner for monitoring and analysis. Optionally, the connector can also connect to a Grafana system to retrieve the CDN alerts.

## Key Features

- **Live hardware metrics**: Retrieve detailed metrics about each Broadpeak node, including CPU, storage, and memory.

- **CDN channel metrics**: Retrieve metrics for all channels in the Broadpeak CDN system.

- **Grafana Alerts**: Retrieve detailed CDN alerts from Grafana.

## Use Cases

### Troubleshooting CDN Channel Degradation

**Challenge**: When a CDN channel is degraded, identifying the component responsible can be difficult across a distributed delivery network.

**Solution**: Use detailed metrics from the CDN's origin servers, cache nodes, and edge servers to pinpoint where performance issues occur.

**Benefit**: Quickly identify the root cause of channel degradation and reduce troubleshooting time.
