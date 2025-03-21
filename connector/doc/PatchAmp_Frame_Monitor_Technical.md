---
uid: Connector_help_PatchAmp_Frame_Monitor_Technical
---

# PatchAmp Frame Monitor

The **PatchAmp Frame Monitoring System** (RMS) integrates standard distribution amplifiers with a remote software package, creating a comprehensive signal verification solution. The system provides real-time monitoring and instant reporting of critical parameters such as signal presence, lock status, module temperature, fiber transmit and receive levels, and fiber laser metrics. This universal frame can accommodate any combination of cards, with the monitoring circuit being a standard feature across all PatchAmp distribution amplifiers. 

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

You will find other pages such as **Supply Voltage**, **Optical Power**, **Data Rage** and more which they call consist of a table with the current value for each card in the frame.

**Notes**
Only cards that have their status enabled are retrieved to populate all the tables above.