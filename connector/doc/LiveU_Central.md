---
uid: Connector_help_LiveU_Central
description: Learn how to configure LiveU Central with legacy token authentication or API v10.8 keys, and check REST and WebSocket communication.
---

# LiveU Central

## About

The **LiveU Central** connector monitors and manages LiveU units, channels, inventories, groups, and network connections. Operators can inspect unit status and control transmission settings, including starting and stopping streams.

From connector version 1.1.0.9, you can select legacy token authentication or API v10.8 key authentication. Existing elements default to *Legacy*; upgrading does not select API v10.8 automatically.

## Configuration

### Connections

#### HTTP Connection

- **IP address/host**: The LiveU Central REST host for the selected deployment.
  - Legacy deployments: Keep the existing host, for example `https://lu-central.liveu.tv`.
  - API v10.8: Use `https://lu-central-api.liveu.tv`.
- **IP port**: *443*.
- **Bus address**: *bypassProxy*.

The **API Endpoint** parameter supplies the REST path. Its default is *rest-v2/v2/*. In API v10.8 mode, the resulting REST base URL must be `https://lu-central-api.liveu.tv/rest-v2/v2`. Do not repeat this path in the HTTP host setting. Older deployments must retain the endpoint supplied for their backend; the older REST base can be `https://lu-central.liveu.tv/luc/luc-core-web/rest/v2`.

#### WebSocket Interface

- **IP address/host**: The WebSocket host supplied for the deployment. Configure this separately from the REST host.
- **IP port**: *443*.
- **Bus address**: *bypassProxy*.

The connector uses secure WebSocket communication. If only a host is configured, the existing `/luc/luc-core-web/pubsub/` path is used. A secure URL with a different path can be configured when LiveU supplies one. Do not include credentials, a token query, or a URL fragment in the connection setting.

### Initialization

#### Legacy Authentication

1. Select *Legacy* under **Authentication Method** on the **Connection** page.
1. Enter **Username** and **Password**.
1. Enter the deployment's **Application ID** and **API Key**.
1. Keep the existing **API Login Endpoint** and **API Endpoint** values.

The connector obtains an SSO token, a bearer token, and a one-time WebSocket token. The default login endpoint is *auth/login/*; it is used for `token_grant` and `onetime_token_grant`. These paths are relative to the configured HTTP host.

#### API v10.8 Authentication

1. Configure the HTTP connection host as `https://lu-central-api.liveu.tv`.
1. Set **API Endpoint** to `rest-v2/v2/`.
1. Enter the API gateway key under **API Key**.
1. Enter the **Application ID** supplied for the deployment.
1. Enter the Central **User Key** and **User Secret Key** supplied by LiveU.
1. Select *API v10.8* under **Authentication Method**.

The gateway key, application identifier, and Central user credentials are separate values. LiveU must provision the gateway key and authorize the application and user for the target deployment. Do not reuse a legacy gateway key unless LiveU confirms that it is valid for the new gateway.

The connector generates the following headers:

```http
X-API-Key: <gateway_api_key>
Application-Id: <application_id>
Authorization: luc-api-key <user_key>:<user_secret>
Content-Type: application/json
```

In this mode, **Username**, **Password**, and **API Login Endpoint** are not required. The connector does not request or refresh SSO, bearer, or one-time tokens for REST access.

**Authentication Method**, **User Key**, and **User Secret Key** are saved. Credential changes reinitialize communication. The masked **Bearer Token** field contains the generated Authorization value; it is an output, not a credential input.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The **General** page contains a tree view of units in the selected inventory. Select an inventory on the **Units** page to inspect its units and start or stop streams.

Use **HTTP Status** and **WebSocket Status** on the **Connection** page to check communication. Missing credentials block polling with a configuration message. HTTP 401 or 403 errors require checking the gateway key, Application ID, user credentials, and deployment permissions.

After an API v10.8 REST failure, the medium timer retries initialization without entering legacy login. A closed API v10.8 WebSocket is retried by that timer; its default interval is one minute. After reconnection, the connector resubscribes to unit status/configuration, channel state/allocations, streaming-session, and geolocation topics for the current inventories.

## Notes

> [!IMPORTANT]
> API v10.8 WebSocket compatibility is a best-effort adaptation, not vendor-confirmed or live-verified. Confirm the endpoint and authentication support with LiveU before production rollout.

The migration guide specifies the API v10.8 REST headers but does not define a replacement WebSocket contract. In this mode, the connector applies the gateway key, Application ID, and generated Authorization header to the opening handshake, retains the configured WebSocket host/path, and omits the legacy one-time token.

Successful REST authentication does not prove that the configured WebSocket endpoint accepts the same headers. A handshake failure is reported separately and does not initiate a legacy token request in API v10.8 mode.
