---
uid: Connector_help_CISCO_Meraki_Web_API
---

# CISCO Meraki Web API

CISCO Meraki Web API is used by Kordia to monitor their Meraki devices (Cisco Meraki MX64, MX67, MX84, MX100, MS120-8, MS120-8FP, and vMX100) exclusively through the Meraki Web API.

## About

### Version Info

| Range              | Key Features                                                                                                | Based on | System Impact |
|--------------------|-------------------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x (obsolete) | Initial version Polling and Monitoring via Meraki API over HTTPS                                            | -        | -             |
| 1.0.1.x            |                                                                                                             | -        | -             |
| 2.0.0.x            | Virtual connector captures and processes webhook notifications automatic clearing of cleared/expired alarms | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Not Applicable         |
| 1.0.1.x   | Not Applicable         |
| 2.0.0.x   | Not Applicable         |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | No                      | -                     | -                       |

## Configuration 1.0.1.x

### Cisco Meraki API Key

The connector in version range 1.0.0.x captures alarms through communication with the Meraki API via HTTPS requests.

Create an element and fill in the connection details in the element settings. Enter `https://api.meraki.com/` in the IP address/host field.

On the General page of the new element, fill in the **Authorization Value** parameter. This is the API key used for authorization to access the API.

## Configuration 2.0.0.x

### Webhook Connections

The connector in version range 2.0.0.x captures alarms through webhook notifications.

The **Configuration** page needs to be set where the connector catches the webhooks from.

The user is required to set the following parameters:

- **Webhooks Status**: Toggle to determine if connector is receptive to webhook notifications
- **Webhooks URI**: URI webhook notifications will be caught with
- **Webhooks Port**: Port webhook notifications
- **Webhooks Protocol**: Select between HTTP and HTTPS protocol
- **Webhooks Certificate**: Select the certificate to be used by the connector (Applicable only for HTTPS protocol)

The status of the webhooks service is reflected below under the parameter **Webhooks Web Service Status**. If all parameters are configured correctly, it should display "Opened".

## How To Use

Once the webhook web service is configured, the element is ready to receive and process webhook notifications.

The notifications are processed and displayed in the following pages:

- **General**: Displays the last notification captured in a string. (*removed in version 2.0.0.X*)

- **Alarms**: Saves and displays notifications into an alarm table

- Alarm Settings: User can determine if the table automatically clears alarms that have been cleared/expired. User may determine the lifetime of these alarms.

## Notes

### Support for Webhook Alerts

The element currently supports the following alertTypeIds:

- stopped_reporting
- started_reporting
- vrrp (Failover event detected)
- failover_event (Uplink status changed)
