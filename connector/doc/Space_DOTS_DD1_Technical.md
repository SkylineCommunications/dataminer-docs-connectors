---
uid: Connector_help_Space_DOTS_DD1_Technical
---
# Space DOTS DD1 Technical

## About

The **Space DOTS DD1** connector monitors Space DOTS DD1 telemetry through an HTTP API and transforms raw API responses into operational monitoring data.

It includes an authentication flow, periodic public/protected health checks, raw frame polling, and dataset-driven table population for power/radiation and thermal telemetry.

### Version Info

> [!NOTE]
> Version info is maintained via `<VersionHistory>` tags in `protocol.xml`.

## Configuration

### Connections

#### HTTP Connection — API

This connector uses an HTTP connection and requires the following input during element creation:

| Setting | Value |
|---------|-------|
| **IP address/host** | API host of the Space DOTS DD1 service |
| **IP port** | Destination IP port (default: *443*) |
| **Bus address** | Not required |

### Initialization

After creating the element:

1. On **General**, set **Client ID** and **Client Secret**.
2. Click **Authenticate** to request a bearer token.
3. Confirm **Authentication** is `Successful` and verify **Public Health Status** is `ok`.
4. Allow timers to populate position and table telemetry:
   - Raw frame polling every ~30 seconds.
   - Public health and token watchdog checks every ~60 seconds.
   - Last execution validation every ~10 seconds.

## How to Use

### General Page

Use this page to configure API credentials and validate connector/API health.

Key usage points:

- **Client ID** / **Client Secret**: Credential pair used by `/token`.
- **Authenticate**: Manual trigger to force token retrieval.
- **Authentication**: Indicates token acquisition outcome.
- **Token Expiry Timestamp** and **Last Auth Attempt**: Verify token freshness and recent auth activity.
- **Public Health Status**: Quick service health indicator from `/health/public`.

### Position Page

This page shows core orbital/telemetry recency metrics:

- **Latitude**, **Longitude**, **Altitude**, **Velocity Magnitude**
- **Last Frame Timestamp**
- **Time Since Last Execution**

Use this page for rapid operational confirmation that new telemetry frames are being received and parsed on time.

### Power & Radiation Page

Contains the **Power and Radiation** table with one row per dataset.

Primary operational use:

- Validate per-channel bus voltages/currents and computed totals.
- Monitor dosimeter health and radiation behavior (dose/count/count rate).
- Correlate dataset-level timestamps with frame ingestion behavior.

### Thermal Sensors Page

Contains three complementary telemetry views:

- **Thermal Summary**: Per-dataset min/max/average PT1000 temperatures.
- **PT1000 Sensors**: Per-sensor temperature details with customizable sensor labels.
- **Magnetometer Sensors**: Per-sensor temperature and magnetic field components (X/Y/Z), with customizable labels.

Use display keys (dataset/sensor context) and labels to make fleet operations and troubleshooting faster.

## DataMiner Connectivity Framework

This connector does not define DCF interfaces in `protocol.xml`.

## Notes

- Authentication is required for protected endpoints (`/health/protected`, `/dd1-raw-frame/synthetic`).
- The connector also performs `/health/public` polling, which can be used as a baseline reachability indicator even when authentication fails.
- Internal status/response parameters are present for troubleshooting API interactions and parser behavior.
