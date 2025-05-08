---
uid: Connector_help_PatchAmp_Frame_Monitor_Technical
---

# PatchAmp Frame Monitor

## About

The **PatchAmp Frame Monitoring System** (RMS) integrates standard distribution amplifiers with a remote software package, creating a comprehensive signal verification solution. The system provides real-time monitoring and instant reporting of critical parameters such as signal presence, lock status, module temperature, fiber transmit and receive levels, and fiber laser metrics. This universal frame can accommodate any combination of cards, with the monitoring circuit being a standard feature across all PatchAmp distribution amplifiers.

With this **PatchAmp Frame Monitor** connector, you can monitor the status of all 32 possible cards. For active cards, you can access metrics such as temperature, supply voltage, optical power, and more.

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *9097*).

## How to use

The element created with this connector has the following data pages:

- **General**: Contains the **Modules** table which will give you an overview of all the 32 possible cards with their status.
- **Status**: Contains information about the five LEDs for each card.
- **Temperature**: Contains the **Temperature** table for the current value for each card.

The element will also have other pages such as **Supply Voltage**, **Optical Power**, **Data Rate**, and more, which each contain a table with the current value for each card in the frame.

> [!NOTE]
> The tables mentioned above will only display information for cards that have the status *Enabled*.
