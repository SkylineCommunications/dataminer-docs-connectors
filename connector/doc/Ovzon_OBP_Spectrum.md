---
uid: Connector_help_Ovzon_OBP_Spectrum
---

# Ovzon OBP Spectrum
This driver is a smart-serial driver that communicates and retrieves spectrum data from the *Ovzon Control Terminal*, and uses the Spectrum Analyzer feature to display the trace.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Spectrum Analyzer for monitoring and analyzing trace.</li><li>Configurations for retrieving trace data.</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### IP Connection - Primary

This connection defines the connection to the Ovzon Control device where commands requesting spectrum data is sent to. The following input is required during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *21963*)]
  - **Bus address**: [The bus address of the device. (fixed value: *ByPassProxy*)]


#### IP Connection - Notifications

This connection defines where the trace data response should be sent to for Dataminer to process it. It should point to the **Dataminer Agent this element is created on**. The following input is required during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *22000*)]
  - **Bus address**: [The bus address of the device. (fixed value: *ByPassProxy*)]

## How to use

The driver functions by sending individual commands to the device requesting for spectrum data. For adjustments of the frequency range, it should be done through the spectrum analyzer feature. For adjusting device-specific parameters like ports or message source and destination, it should be configured through the parameters on the *General* page.
