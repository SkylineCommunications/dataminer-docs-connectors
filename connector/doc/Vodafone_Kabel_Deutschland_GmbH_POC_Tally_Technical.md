---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_POC_Tally_Technical
---

# Vodafone Kabel Deutschland GmbH POC Tally

## About

This is a dedicated connector intended to aggregate the SI system status of the different lineups and systems.

The POC tally status is determined for each SI stream, so its status can be shown as *On-Air*, *Off-Air*, *On-Air Locally*, *Off-Air Locally*, *On-Air Locally Inverted*, or *Off-Air Locally Inverted*.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### General Page

The **General** page displays the aggregated tally status information per lineup, site, and system.

On the following pages, you can see the status of each lineup or system individually:

- iSIMS System
- National MUX
- Catweazle RegioMUX

You can interface with each table by right-clicking it to access the context menu.

### User-Defined API Endpoint

The connector comes with a user-defined API endpoint so that it is possible to not only retrieve the status data within DataMiner but also from external systems: `{DMA IP}/api/custom/poc-tally`.
