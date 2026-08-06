---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_SRT_Delivery_Service
---

# Vodafone Kabel Deutschland GmbH SRT Delivery Service

## About

The **Vodafone Kabel Deutschland GmbH SRT Delivery Service** connector monitors the active configuration and operational status of SRT Techex MWCore devices and their associated edges.

For each edge, the connector determines whether the outgoing stream is active, and it uses this information to evaluate the overall delivery status.

> [!NOTE]
> This is a dedicated connector that can only be applied to a service template to create an enhanced element.

## Key Features

- **Status overview**: Provides both the aggregated service status and individual device status per system and site.
- **Edge monitoring**: Evaluates the streaming state of each edge based on the outgoing SRT stream status.
- **24/7 monitoring**: Continuously monitors the environment to ensure up-to-date status information.

## Use Case

**Challenge**: Services often include multiple devices to provide redundancy within a site and across multiple sites. Determining the overall streaming health requires evaluating whether at least one device is operating correctly.

**Solution**: The connector aggregates the status of all devices and indicates the overall service state, including how many devices are currently in a healthy streaming state.

**Benefit**: Improves monitoring visibility, increases reliability, and enables faster operational response when issues occur.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_SRT_Delivery_Service_Technical).
