---
uid: Connector_help_Generic_IP_Resolve_JSON
description: "Explore key features and use cases of the Generic IP Resolve JSON connector, which enables DataMiner collectors to resolve MAC addresses to IP addresses."
---

# Generic IP Resolve JSON

## About

This connector helps DataMiner collectors retrieve IP addresses when they only have a device's MAC address. It connects collectors to an OSSI service that exposes MAC-to-IP mappings through an authenticated HTTP API.

By centralizing these lookups, the connector helps collectors maintain their address information while controlling the number of requests sent to the external service.

## Key Features

- **Collector integration**: Receive MAC address lookup requests from compatible DataMiner collectors and return resolved IP addresses to the requesting elements.
- **Controlled API usage**: Limit external lookup requests per minute and process queued requests in order of arrival.
- **Reusable lookup results**: Cache MAC-to-IP mappings to answer repeated requests without querying the external service again.
- **Lookup activity insights**: Track request volumes, resolved and unresolved queries, timeouts, server errors, and retry activity.
- **CSV offload**: Export resolved MAC-to-IP mappings for downstream processing.

## Use Cases

### Complete Collector Address Information

**Challenge**: A collector knows a device's MAC address but lacks the IP address needed to complete its address information.

**Solution**: The collector submits a lookup request to the Generic IP Resolve JSON connector, which queries the OSSI service and returns the resolved mapping.

**Benefit**: Collectors can retrieve address information through a shared integration instead of each implementing its own API connection.

### Manage Repeated Lookup Requests

**Challenge**: Repeated requests for the same MAC addresses increase traffic to the external lookup service.

**Solution**: The connector reuses cached results and applies a configurable limit to external requests.

**Benefit**: Reduce unnecessary lookups and keep request volumes within the configured operational limit.

### Supply Mappings to Downstream Processing

**Challenge**: Another processing workflow needs the MAC-to-IP mappings resolved for collectors.

**Solution**: Enable CSV offload to periodically write resolved mappings to a configured directory.

**Benefit**: Make lookup results available to file-based integrations without requiring those integrations to query the OSSI service themselves.

## Technical Reference

### Prerequisites

- **A compatible OSSI service** exposing the authentication and MAC-to-IP lookup endpoints used by the connector.
- **Valid service credentials**, including the username, password, and internal username required for authentication.
- **Network access from the DataMiner Agent** to the service over HTTPS.
- **Compatible DataMiner collector elements** that use the connector's request and response message format.
- **A writable output directory** if CSV offload is required.

> [!NOTE]
> For connection settings, authentication, request handling, caching, and CSV offload configuration, refer to the [technical documentation](xref:Connector_help_Generic_IP_Resolve_JSON_Technical).
