---
uid: Connector_help_Generic_IP_Resolve_JSON_Technical
---

# Generic IP Resolve JSON

## About

Generic IP Resolve JSON receives MAC-address lookup requests from compatible DataMiner collectors, retrieves the corresponding IP addresses from an OSSI service through an authenticated HTTP API, and returns resolved mappings to the requesting collectors.

The connector queues incoming requests, caches lookup results, and can export resolved mappings to CSV files.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to an OSSI service and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The hostname or base URL of the OSSI service. The connector constructs HTTPS lookup URLs from this setting.
- **IP port**: The HTTPS port exposed by the service, typically *443*. Use the port required by your deployment.
- **Device address**: Use *ByPassProxy* to bypass the proxy server. This is the default value configured in the connector.

The service must support these endpoints:

| Purpose | Method | Endpoint |
| --------- | -------- | ---------- |
| Obtain an authentication token | POST | `oauth/oauth/token` |
| Look up an IP address by MAC address | GET | `accessnet/api/v2/accessnet/ip/{MAC}` |

The lookup response is JSON containing an `ip` field. This connector is designed for these OSSI endpoints; it is not a configurable integration for arbitrary DHCP or JSON APIs.

### Initialization

1. On the **General** page, select **Credentials...**.
2. Configure **Username** and **Password** for the OSSI service.
3. Configure **Internal Username** for the authentication request.
4. After configuring the internal username, restart the element so that the connector rebuilds the authentication header using that value.
5. In connector version **1.0.0.12** and later, configure **Token Refresh Interval** to suit the service's token lifetime.
6. Verify that **Token Last Time Refresh** updates after a token is retrieved. This parameter is available from version **1.0.0.12**.
7. On the **General** page, review the request limit and cache settings before connecting collectors.

The token request uses the password grant with the configured username and password. Its Basic authorization header is constructed from the internal username and an empty password. The returned token type and access token are used to authorize lookup requests.

From version **1.0.0.12**, **Token Refresh Interval** accepts values from **1 to 24 hours**, with a default of **2 hours**. Choose an interval shorter than the token's validity period.

## How to Use

### Control External Request Volume

On the **General** page, configure **Maximum Number of Requests** to limit external lookups.

The default is **10 requests per minute**, and the configurable range is **1 to 65535**. Cached results can be returned without consuming this external-request allowance.

Incoming requests are stored in the **Stack Table** and processed oldest first. Requests that require a fresh lookup wait when the request allowance has been reached.

The queue is keyed by MAC address. If another request arrives for a MAC address already queued, the connector updates the existing entry rather than creating a separate row. The collector information is replaced by that of the latest request, while the original queue timestamp is retained.

### Configure Caching and Retry Eligibility

The **General** page contains the following settings:

| Setting | Purpose | Default |
| --------- | --------- | --------- |
| **Cache Time** | Retention time for cached lookup results, in minutes. Configurable from 1 to 1440 minutes, or *Disabled*. | 60 minutes |
| **Resend Time (Not Found / 0.0.0.0)** | Minimum age of an unresolved cached result before another normal collector request can trigger a fresh lookup. Configurable from 1 to 1440 minutes, or *Disabled*. | 60 minutes |
| **Maximum Cached Items** | Maximum number of cached entries retained during cache maintenance. Configurable from 0 to 65535. | 1000 |

> [!IMPORTANT]
> When caching and resend handling are enabled, **Cache Time must be longer than Resend Time**. The connector validates changes to these settings and rejects invalid combinations. Both values initially default to 60 minutes, so review them during initialization. For example, use a Cache Time of 60 minutes and a Resend Time of 15 minutes.

For a normal lookup request:

- If no cached entry exists, the connector queries the service when the request allowance permits.
- If the cached entry contains a resolved IP address, the connector returns it to the collector without a new external lookup.
- If the cached entry contains `0.0.0.0`, the connector can query the service again only when resend handling is enabled, the resend interval has elapsed, and the request allowance permits.
- If an unresolved cached entry is not eligible for another lookup, the queued request is removed without a fresh service query.

A forced lookup bypasses these cache checks, but remains subject to the external request limit.

> [!NOTE]
> Resend Time does not create an autonomous retry schedule. A subsequent collector request is required to trigger another lookup.

Cache maintenance removes expired entries and, when the configured capacity is exceeded, retains the newest entries.

Disabling **Cache Time** also disables **Resend Time**. Setting **Maximum Cached Items** to **0** causes cache maintenance to clear the cache. Lookup responses can still be inserted between maintenance cycles, so these settings should not be treated as a guarantee that no temporary cache entries exist.

### Monitor Lookup Activity

On the **Tables** page:

- Use the **Stack Table** to inspect pending MAC addresses, collector destinations, request timestamps, and whether a lookup is forced.
- Review the per-minute counters for requested, resolved, unresolved, timed-out, and server-error queries.
- Review **Number of Cached Entries** and **Number of Stacked Entries** to monitor cache and queue size.
- Select **Advanced Metrics...** to inspect external lookup requests, distinct requested MAC addresses, and resend requests over 15-minute and one-hour periods.

The advanced metrics are updated every 15 minutes. The one-hour values are calculated from the latest four 15-minute samples.

> [!NOTE]
> The hourly distinct-MAC metric is the sum of the distinct-MAC counts in those four samples. A MAC address requested in multiple samples can therefore be counted more than once.

### Export Resolved Mappings to CSV

On the **General** page:

1. Configure **DSL Path** with an output directory accessible to the DataMiner Agent.
2. Configure **DSL File Name** with the filename prefix.
3. Configure **DSL Offload Frequency** in minutes.
4. Enable **DSL Offload**.

When offload is enabled, resolved mappings from service responses and cache hits are added to the internal buffer. The buffer is keyed by MAC address, so later results for the same MAC replace earlier buffered results.

The output filename follows this pattern:

```text
{DSL File Name}_{DataMiner ID}_{Element ID}_{dd_MM_yyyy_HH_mm_ss}.csv
```

Files are UTF-8 encoded and contain semicolon-separated records:

```text
ActionType;MAC;IP;TIMESTAMP
Update;00:11:22:33:44:55;192.0.2.10;2026-10-02 12:00:00
#EOF#
```

The timestamp uses the DataMiner Agent's local time.

## Notes

### Version and Compatibility Information

This documentation describes the current **1.0.0.12** implementation. Configurable token refresh and the token refresh timestamp were introduced in **1.0.0.12**. Advanced request metrics were introduced in **1.0.0.9**.

The following information is retained from the previous documentation because it is not fully represented in the connector's version-history metadata:
