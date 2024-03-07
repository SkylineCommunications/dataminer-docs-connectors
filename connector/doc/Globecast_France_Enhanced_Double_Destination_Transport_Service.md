---
uid: Connector_help_Globecast_France_Enhanced_Double_Destination_Transport_Service
---

# Globecast France Enhanced Double Destination Transport Service

The Globecast France Enhanced Double Destination Transport service is an enhanced service protocol. It oversees two "Globecast France Enhanced Single Destination Transport" services. It retrieves the active alarms and determines the overall severity.

## About

### Version Info

| Range              | Features                                                                                          | Based on | System Impact |
|--------------------|---------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version: Calculates the severity of the service based on the state of its child elements. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

This connector is an enhanced service protocol and uses a virtual connection. It can be applied to a service that includes two "Globecast France Enhanced Single Destination Transport" services.

## How to use

On the **Service Status** page, the computed severity is displayed as the standalone parameter **Severity**. By activating alarm monitoring on this parameter only, you can align the calculated severity with the overall severity of the service.

The table **Service Element Status** on this same page illustrates the health of the nodes associated with the service.

The **Service Alarms** page shows the active and the clear alarms belonging to the service, each in their own table.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
