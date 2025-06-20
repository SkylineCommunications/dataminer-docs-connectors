---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_POC_Tally_Technical
---

# Vodafone Kabel Deutschland GmbH POC Tally

This is a dedicated connector intended to aggregate the SI System status of the different Lineups and systems.

The POC Tally status is determined for each SI Stream to showcase if the status is: On-Air, Off-Air, On-Air Locally, Off-Air Locally, On-Air Locally Inverted or Off-Air Locally Inverted.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Redundancy

There is no redundancy defined.

## How to use

The **General** page displays the aggregated Tally Status information per lineup, site and system.  
The following pages are foreseen with the status of each lineup or system individually:
1. iSIMS System
1. National MUX
1. Catweazle RegioMUX

Note: each table can be interfaced with through the means of a context-menu (right-click).
