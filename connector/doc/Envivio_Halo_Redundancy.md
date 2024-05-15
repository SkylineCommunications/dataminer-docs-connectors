---
uid: Connector_help_Envivio_Halo_Redundancy
---

# Envivio Halo Redundancy

## About

The **Envivio Halo Redundancy** connector will retrieve a list of configured **Envivio Halo** elements in the DMS. You can then subscribe to **maximum 2** of those elements to receive the alarm status. When both of the configured elements have the same alarm, the redundancy element will also show the alarm in the Alarm table.

## Creation

This connector uses a virtual connection and does not require any input during element creation.

## Timing

Every hour, the list of configured Envivio Halo elements will be updated.

Every 5 minutes, the connector checks if the elements are active or not and cleans alarm entries if needed.

## Usage

The element contains 5 pages:

- **Redundancy Config**: Provides an overview of all the installed Envivio Halo elements that are using the "production" version. Using the **Registration** button, it is possible to enable or disable the registration on the alarms table of maximum 2 elements.

- **Services**/**Outputs**/**Recording**: These pages are currently not used yet.

- **Alarms**: This page provides a summary alarm overview of the configured Envivio Halo elements. When the **same alarms** are active on both devices, these will also be shown in the alarm table for the Halo Redundancy.

## Latest Version

1.0.0.3
