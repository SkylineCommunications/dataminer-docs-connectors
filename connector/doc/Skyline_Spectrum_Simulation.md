---
uid: Connector_help_Skyline_Spectrum_Simulator
---

# Skyline Spectrum Simulator

This connector is used to simulate a spectrum analyzer. It allows you to test DataMiner Spectrum Analysis without the need for an actual device or special debug code directly in SLSpectrum.

## About

### Version Info

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | -            | -                |

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

On this page, you can configure the basic parameters required to create the simulated trace.

It has two modes:

- The *Center Trace Pattern* mode creates a waveform at the center of the spectrum analyzer trace. The type of waveform is based on the value of the Trace Pattern parameter.

- The *Carriers from Table* mode creates a waveform based on the Center Frequency, Bandwidth, and Amplitude specified in the Carrier Table.

### Tracking

This page allows you to trace which sets have been made on the spectrum analyzer 641xx write parameters. (From the SLSpectrum point of view, these are settings on the device.)

### Mirror Values

The parameters on this page mirror the 64xxx special spectrum parameters.

### Measurement Points

This page shows the current values of the 64xxx spectrum interfacing parameters and allows you to change them as if they were changed directly on the device.
