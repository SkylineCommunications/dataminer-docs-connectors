---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_SI_Stream_Mapping
description: "Explore key features and use cases of the Vodafone Kabel Deutschland GmbH SI Stream Mapping connector for SRM bookings and stream mappings in DataMiner."
---

# Vodafone Kabel Deutschland GmbH SI Stream Mapping

## About

The Vodafone Kabel Deutschland GmbH SI Stream Mapping connector stores links between DataMiner bookings, input transport stream information, and outgoing SDT/EIT PID information. These mappings are used by the Service and Resource Management (SRM) framework to configure SI streams for IP Gateway, IP Peering, and SRT Gateway use cases.

## Key Features

- **Reservation mapping**: Store links between bookings and transport stream information.
- **SI output mapping**: Associate bookingss with outgoing SDT/EIT PID information.
- **Use case views**: Review mappings on dedicated IP GW, IP Peering, and SRT pages.

## Use Cases

### Maintaining SI Stream Configuration Mappings

**Challenge**: SRM needs booking-to-stream mappings to configure SI streams for different gateway and peering use cases.

**Solution**: The connector stores the required associations and exposes them in use-case-specific tables.

**Benefit**: You can review and maintain the mappings used for SI stream setup.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_SI_Stream_Mapping_Technical).
