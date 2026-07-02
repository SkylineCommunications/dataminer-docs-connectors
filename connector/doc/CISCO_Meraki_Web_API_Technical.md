---
uid: Connector_help_CISCO_Meraki_Web_API_Technical
---

# CISCO Meraki Web API

CISCO Meraki Web API is used to monitor Cisco Meraki environments via the Meraki Dashboard API and webhook notifications.

## About

This connector supports two operating models:

- **1.0.x**: Polling and monitoring via HTTPS requests to the Meraki Dashboard API.
- **2.0.x**: Event-driven alarm capture using webhook notifications.

## Configuration

### Connections

#### HTTP Connection - Meraki Dashboard API (1.0.x)

This connector uses an HTTP connection for API polling in the 1.0.x range and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: `https://api.meraki.com/`
- **IP port**: `443`

#### Virtual Connection - Webhook Listener (2.0.x)

This connector uses a virtual connection in the 2.0.x range and receives inbound webhook notifications.

### Initialization

#### Cisco Meraki API Key (1.0.x)

The connector in the 1.0.x range captures alarms through communication with the Meraki API via HTTPS requests.

Create an element and fill in the connection details in the element settings. Enter `https://api.meraki.com/` in the IP address/host field.

On the General page of the new element, fill in the **Authorization Value** parameter. This is the API key used for authorization to access the API.

#### Webhook Configuration (2.0.x)

The connector in the 2.0.x range captures alarms through webhook notifications.

Configure the **Configuration** page to define where the connector listens for webhook notifications.

The following parameters must be set:

- **Webhooks Status**: Toggle to determine whether the connector is receptive to webhook notifications.
- **Webhooks URI**: URI where webhook notifications are caught.
- **Webhooks Port**: Port for webhook notifications.
- **Webhooks Protocol**: Select HTTP or HTTPS.
- **Webhooks Certificate**: Certificate used by the connector (HTTPS only).

The status of the webhook service is shown by the parameter **Webhooks Web Service Status**. If everything has been configured correctly, it should display *Opened*.

> [!IMPORTANT]
> Notifications sent by Meraki include a **sharedSecret** property. Add the expected value to the **Shared Secrets Table** to accept only authorized webhook payloads.

Example payload:

```json
{
    "version": "0.1",
    "sharedSecret": "commonSecret",
    "sentAt": "2026-05-29T12:42:26.375558Z",
    "organizationId": "658651445502938393",
    "organizationName": "Lunchgarden_TFB_1166564739",
    "organizationUrl": "",
    "networkId": "L_658651445502952912",
    "networkName": "631_CCESCOLCG02_Schoten_120-1743553",
    "networkUrl": "",
    "networkTags": [],
    "deviceSerial": "Q2JY-9KYS-3UGD",
    "deviceMac": "98:18:88:c7:bb:f5",
    "deviceName": "CCESCOLCG02",
    "deviceUrl": "",
    "deviceTags": ["recently-added"],
    "deviceModel": "MX67C-WW",
    "alertId": "658651445547679670",
    "alertType": "Uplink status changed",
    "alertTypeId": "failover_event",
    "alertLevel": "warning",
    "occurredAt": "2026-05-29T12:41:43.969000Z",
    "alertData": { "uplink": "0" }
}
```

## How to Use

### 1.0.x Workflow (API Polling)

Create the element with the HTTP connection settings and configure the **Authorization Value** parameter with a valid Meraki API key.

Once configured, the element polls the Meraki Dashboard API over HTTPS and processes the retrieved data.

### 2.0.x Workflow (Webhook Ingestion)

Once the webhook web service is configured, the element is ready to receive and process webhook notifications.

Notifications are processed and displayed on the following pages:

- **General**: Displays the last notification captured as a string (removed in 2.0.x).
- **Alarms**: Saves and displays notifications in an alarm table.
- **Alarm Settings**: Allows configuration of automatic clearing behavior and alarm lifetime.

## Notes

### Support for Webhook Alerts

The element currently supports the following `alertTypeId` values:

- stopped_reporting
- started_reporting
- vrrp (Failover event detected)
- failover_event (Uplink status changed)
