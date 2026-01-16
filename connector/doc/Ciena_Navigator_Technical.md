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

When you have created an element, configure the following settings:

1. On the **Configuration** page, enter the **username** and **password** to authenticate with the Ciena Navigator API.

   Once these credentials have been configured, the connector automatically acquires and manages authentication tokens. Make sure the device/API endpoint is reachable before you continue.

1. Click the **Polling Config** button on the Configuration page to access the **Polling Configuration** subpage.

1. Enable polling for each data set (Network Constructs) by setting the **Admin Status** column to *Enabled*.

1. Optionally adjust the **Interval** for each data set to control the polling frequency.

1. Use the **Poll** button in the Polling Manager table to manually trigger immediate data retrieval for a specific data set.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Redundancy

If redundancy is configured, ensure both endpoints are reachable and that failover conditions are defined according to the connector’s parameters. Verify alarms and KPIs continue on failover.

## How to use

### Communication

HTTP requests are used to retrieve device information and KPIs. Token acquisition occurs automatically when credentials are configured.

### Monitoring

- View the total number of network constructs on the **General** page.
- Browse detailed network construct information on the **Network Constructs** page.
- Use the Alarm Console for actionable events.

### Troubleshooting

- Check the **Last Poll Status** and **Last Poll Status Info** columns in the Polling Manager table to diagnose any polling issues.

## Notes

- Ensure API rate limits and paging are respected if the source enforces them.
- For secure environments, validate TLS settings and certificate trust.
- The connector automatically manages authentication tokens. If credentials are changed, the token is automatically refreshed on the next request.
