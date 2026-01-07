---
uid: Connector_help_Ciena_Navigator_Technical
---

# Ciena Navigator

## About

Ciena Navigator integrates Ciena device APIs with DataMiner using HTTP requests to collect status, alarms, and performance metrics. It enables centralized monitoring, dashboards, and reporting for Ciena infrastructure.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### HTTP Connection - Redundancy

This connector can optionally use a secondary HTTP connection for high availability:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the secondary destination.
- **IP port**: The IP port of the secondary destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

If authentication is required, configure the credentials or tokens on the card immediately after creation. Ensure the device/API endpoint is reachable and any required headers are set via parameters.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Redundancy

If redundancy is configured, ensure both endpoints are reachable and that failover conditions are defined according to the connector’s parameters. Verify alarms and KPIs continue on failover.

### Automation Scripts

If Automation scripts are used (e.g. provisioning or bulk polling adjustments), configure and link them to the element as required.

### Correlation rules

If Correlation is applicable (e.g. grouping related alarms across devices), configure correlation rules to reflect service impact.

### Visio Files

If customized visualizations are required, attach Visio files to the element to display status and KPIs on shapes.

### Report Templates

If reporting is needed, associate report templates to summarize KPIs and health over time.

### Dashboards

Create dashboards to visualize key metrics, alarms, and states for operations teams.

## How to use

- **Communication**: HTTP requests are used to retrieve device information and KPIs.
- **After creation**: Set credentials or tokens if required, verify polling succeeds, and confirm alarms/trending are active.
- **Monitoring**: Use dashboards to track critical KPIs. Use the Alarm Console for actionable events.
- **Stream Viewer**: If applicable, verify requests/responses during troubleshooting.
- **Tips**: Validate firewall, certificates (for HTTPS), and proxy bypass settings (`BypassProxy` as needed).

## DataMiner Connectivity Framework

If DCF is supported in the connector range, configure interfaces and connections via the DataMiner DCF UI or compatible manager connectors.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).

## Notes

- Ensure API rate limits and paging are respected if the source enforces them.
- For secure environments, validate TLS settings and certificate trust.
