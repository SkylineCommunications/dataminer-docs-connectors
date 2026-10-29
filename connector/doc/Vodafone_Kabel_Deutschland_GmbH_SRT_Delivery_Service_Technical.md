---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_SRT_Delivery_Service_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH SRT Delivery Service connector to monitor SRT Techex MWCore devices and stream status in DataMiner."
---

# Vodafone Kabel Deutschland GmbH SRT Delivery Service

## About

The **Vodafone Kabel Deutschland GmbH SRT Delivery Service** connector monitors the active configuration and operational status of SRT Techex MWCore devices and their associated edges.

For each edge, the connector determines whether the outgoing stream is active, and it uses this information to evaluate the overall delivery status.

## Configuration

### Connections

To create a service using this service protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select **Create service**.
1. Specify the name for the service.
1. Open the advanced options and select *Vodafone Kabel Deutschland GmbH SRT Delivery Service* as the service protocol, using the latest or production version.
1. Go to the **parameters** tab and include the service you want to monitor.

## How to Use

### General Page

The **General** page displays aggregated status information per site and per system.

The following pages provide more detailed information about the service configuration and monitored elements:

- **Active Service Configuration**: Displays the currently active service configuration.
- **Elements**: Lists the monitored MWCore elements.
- **Alarms**: Shows the active alarms related to the service.

Tables on these pages support additional actions through the context menu. To access these options, right-click a table.

## Notes

### Linked Components

- [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform)
