---
uid: Connector_help_Rohde_Schwarz_FPL1026
---

# Rohde Schwarz FPL1026

Rohde & Schwarz FPL1026 is a signal and spectrum analyzer with frequency range from 5 kHz to 26.5 GHz. It can analyze signals with a bandwidth of 40 MHz.

This connector communicates with the spectrum analyzer using serial communication (TCP/IP).

## About

### Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|---------------|
| 1.0.0.x | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.9 and later      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

## Usage

On the **Spectrum Analyzer** page, you can find the spectrum analyzer user interface. For more information on how to work with this, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

On the **General** page, you can find device information such as the Manufacturer, Model, Serial Number, and Firmware Version, and the Sweep Mode that is being currently used.
