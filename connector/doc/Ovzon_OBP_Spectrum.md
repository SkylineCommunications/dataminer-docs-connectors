---
uid: Connector_help_Ovzon_OBP_Spectrum
---

# Ovzon OBP Spectrum

This is a smart-serial connector that communicates and retrieves spectrum data from the **Ovzon Control Terminal**. It uses the Spectrum Analyzer feature to display the trace.

## Configuration

### Connections

#### IP Connection - Primary

This connection defines the connection to the Ovzon Control device, where commands requesting spectrum data are sent. The following input is required during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *21963*).
  - **Bus address**: The bus address of the device (fixed value: *ByPassProxy*).

#### IP Connection - Notifications

This connection defines where the trace data response should be sent for DataMiner to process it. It should point to the **DataMiner Agent this element is created on**. The following input is required during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *22000*).
  - **Bus address**: The bus address of the device (fixed value: *ByPassProxy*).

## How to use

The connector functions by sending individual commands to the device requesting spectrum data.

You can adjust the frequency range using the Spectrum Analyzer features.

Device-specific parameters like ports or the message source and destination can be configured on the General page.
