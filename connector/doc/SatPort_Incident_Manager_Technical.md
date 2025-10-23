---
uid: Connector_help_SatPort_Incident_Manager_Technical
---

# SatPort Incident Manager

## About

The purpose of the **SatPort Incident Manager** connector is to listen to the ticketing application. When a new ticket is detected, the connector automatically attempts to forward it to iPaaS.

**iPaaS** (Integration Platform as a Service) is a cloud-based integration layer that connects different applications, systems, and data sources. In this case, it acts as a bridge between the ticketing system and the external platform ServiceNow, enabling seamless data exchange and automation.

## Configuration

### Connections

#### HTTP Connection – Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The iPaaS endpoint URL (e.g. `https://apim-integration-dev-weu.azure-api.net/itsm/tickets`).
- **IP port**: The port of the destination (e.g. `443`).

### Initialization

After configuring the iPaaS URL, the following parameters must be set on the **General** page:

- **Tenant ID**: The GUID of your tenant (provided by the APIM Administrator).
- **API App ID**: The GUID of the APIM Front registration (provided by the APIM Administrator).
- **Client ID**: The GUID of your app registration in Azure (provided by the APIM Administrator).
- **Client Secret App**: The client secret of your Azure app registration (provided by the APIM Administrator).
- **Subscription Key**: The `Ocp-Apim` subscription key (provided by the APIM Administrator).

## How to Use

When you start using this connector, first provide all required input parameters described above, and verify the **Authentication** parameter. Once this parameter shows **OK**, this means that the connector has successfully communicated with iPaaS and retrieved a valid token. This token is automatically used whenever a new ticket is sent to iPaaS.

## Ticket Forwarding Behavior

When a ticket is created in the ticketing application and its **External Owner** matches the connector’s element name, the connector identifies that the ticket is intended for it and automatically forwards it to **iPaaS**. From there, iPaaS creates the corresponding ticket in **ServiceNow**.
