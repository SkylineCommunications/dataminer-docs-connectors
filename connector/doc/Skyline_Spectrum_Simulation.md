---
uid: Connector_help_Skyline_Spectrum_Simulator
---

# Skyline Spectrum Simulator

## About

This connector is used to simulate the DataMiner Spectrum Analyzer. This driver allows to test SLSpectrum without the need for an actual device or special debug code directly in SLSpectrum.


### Version Info

| **Range** | **Description** | **DCF Integration** | **Cassandra Compliant** |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial Version | No                  | Yes                     |

## Installation and configuration

### Creation

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### Spectrum Analyzer

This page contains the Spectrum Analyzer, allowing you to view the simulated trace data.

### General

Allows you to configure the basic parameters required to create the simulated trace. 

It is has 2 modes. 

The Center Trace Pattern mode creates a waveform at the center of the Spectrum Analyzer trace.  The type of waveform is based on the Trace Pattern Parameter's value. 

The Carriers from Table mode creates a waveform based on the Center Frequency, Bandwidth, Amplitude that is declared in the Carrier Table.

### Tracking
Allows to trace which sets were made on the spectrum analyzer 641xx write parameters. (from SLSpectrum point of view, these are settings on the device)

### Mirror Values
The parameters on this page mirror the 64xxx special spectrum parameters.

### Measurement Points
Shows the current values from the 64xxx spectrum interfacing parameters, and allows to change them as if they change directly on the device.