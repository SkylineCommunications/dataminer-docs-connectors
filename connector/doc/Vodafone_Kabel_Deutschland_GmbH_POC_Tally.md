---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_POC_Tally
---

# Vodafone Kabel Deutschland GmbH POC Tally

## About

This is a dedicated connector intended to aggregate the SI System status of the different Lineups and systems.

The POC Tally status is determined for each SI Stream to showcase if the status is: On-Air, Off-Air, On-Air Locally, Off-Air Locally, On-Air Locally Inverted or Off-Air Locally Inverted.

## Key Features

- **Status overview**: Aggregated status and individual status data is available per lineup, system and site.
- **24/7 monitoring**: Constant monitoring to support continuous status updates.
- **Integrated endpoint**: the connector comes with a user-defined API endpoint to retrieve the status data from external systems, not only from within DataMiner ({DMA IP}/api/custom/poc-tally).

## Use Case

**Challenge**: The SI Team needs a way to test, deploy and monitor changes to their SI Systems without causing outages.

**Solution**: The On-Air and Off-Air aggregated status indicates which systems can be used for testing and the foreseen switching mechanisms in the connector allows them to activate or switch to a certain system.

**Benefit**: Improves uptime and reliability.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_POC_Tally_Technical).
