---
uid: Connector_help_Skyline_Spectrum_Simulation
---

# Skyline Spectrum Simulation

This connector is used to simulate a spectrum analyzer. It allows you to test DataMiner Spectrum Analysis without the need for an actual device or special debug code directly in SLSpectrum.

## About

### Version Info

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware    |
|-----------|-----------------------|
| 1.0.0.x   | -                     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components    | Exported Components    |
|-----------|---------------------|-------------------------|----------------------|------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

### Spectrum Analyzer

This page contains the spectrum analyzer, allowing you to view the simulated trace data.

### General

This page contains general information, as well as the following parameters:

- **Track Parameter Sets**: Open the button next to this parameter to open a tracking window. This window allows you to trace which parameter sets were done. In the window, sets will only be logged if the **Track Sets** parameter is enabled. If **Track Status Sets** is also enabled, status sets (communication between SLSpectrum and the protocol, e.g. requesting a new trace) are also logged.

- **Simulation Mode**: Allows you to switch between the two different modes of the connector:

  - The *Center Trace Pattern* mode creates a waveform at the center of the spectrum analyzer trace. The type of waveform is based on the value of the Trace Pattern parameter.

  - The *Carriers from Table* mode creates a waveform based on the Center Frequency, Bandwidth, and Amplitude specified in the **Carrier Table**.

- **Trace Pattern**: Allows you to select a specific trace pattern instead of the default pattern. The following patterns are available:

  - *Default*: A single flat line at the center of the trace window, simulating no available signals or carriers.

  - *Jump Up*: A single spike at the center of the window, wider than the channel pattern. This can be used to simulate e.g. a band pass filter.

  - *Jump Down*: Inverse pattern of *Jump Up*. This can be used to simulate e.g. a notch filter.

  - *Channel*: A single spike in the center of the trace window, simulating a typical view of one channel.

  - *Band*: A set of 8 spikes spread over the trace window, simulating a band with several channels.

  - *Floor*: A single line in the lower part of the trace window, simulating no available signals or carriers.

  - *Frequencydependent*: An asymmetrical trace with five carriers, spread over the trace window, which have a different bandwidth but all have the same amplitude.

- **Noise**: Allows you to disable noise in the simulated pattern.

- **Noise Depth**: Allows you to modify the amount of random noise added to the simulated pattern, so that you can for instance simulate environments with poor reception.

### Tracking

This page allows you to trace which sets have been made on the spectrum analyzer 641xx write parameters. (From the SLSpectrum point of view, these are settings on the device.)

### Mirror Values

This page shows the current values of the spectrum interfacing parameters and allows you to change them as if they were changed directly on the device. Note that the connector will automatically sync start/stop frequency or center frequency/frequency span if one of these settings is changed.

### Measurement Points

This page shows the current values of the 64xxx spectrum interfacing parameters and allows you to change them as if they were changed directly on the device.
