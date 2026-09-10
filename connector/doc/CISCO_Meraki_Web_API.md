---
uid: Connector_help_CISCO_Meraki_Web_API
---

# CISCO Meraki Web API

## About

The CISCO Meraki Web API connector enables the monitoring of Cisco Meraki environments through the Meraki Dashboard API and webhook notifications.

## Key Features

- **API-based monitoring**: Retrieve Meraki data over HTTPS from the Meraki Dashboard API.
- **Webhook-based alarm ingestion**: Receive and process real-time Meraki alerts through a configurable webhook endpoint.
- **Alarm lifecycle handling**: Store incoming alerts and optionally clear alarms automatically when they expire.
- **Operational visibility**: Track network and device alerts from a central DataMiner element.

> [!TIP]
> For detailed setup and behavior information for each version range, refer to the [technical help page](xref:Connector_help_CISCO_Meraki_Web_API_Technical).

## Use Cases

### Centralized Meraki Alert Monitoring

**Challenge:** Meraki alerts are distributed across Dashboard views and are difficult to monitor centrally in an NOC workflow.

**Solution:** Use the connector to collect webhook alerts and display them in DataMiner alarm-focused views.

**Benefit:** Improve operational awareness by consolidating Meraki alerting into a single monitoring platform.

### Faster Incident Response

**Challenge:** Incident handling is delayed when alerts are not automatically ingested and normalized.

**Solution:** Configure webhook reception and shared-secret validation so alerts are captured and processed immediately.

**Benefit:** Reduce mean time to detect and respond to network events.

## Technical info

### Prerequisites

- **DataMiner connectivity** to `api.meraki.com` over HTTPS is required for API polling modes.
- **Meraki Dashboard access** with API permissions is required to generate and manage API keys.
- **Webhook network reachability** is required for webhook modes so the Meraki cloud can reach the configured endpoint.
- **Certificate configuration** is required when HTTPS is used for webhook reception.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector, refer to the [technical help page](xref:Connector_help_CISCO_Meraki_Web_API_Technical).
