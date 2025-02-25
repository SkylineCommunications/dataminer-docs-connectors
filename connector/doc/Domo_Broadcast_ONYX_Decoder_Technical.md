---
uid: Connector_help_Domo_Broadcast_ONYX_Decoder_Technical
---

# Domo Broadcast ONYX Decoder

## About

The **ONYX Decoder** is a broadcast decoder that offers compression ratios on video resolutions up to 4K UHD. It is suitable for remote production applications over leased lines or satellite, handling 4xHD or 1xUHD feeds with ultra-low latency.

The **Domo Broadcast ONYX Decoder** connector is used to monitor and control ONYX decoders that support both ASI and IP inputs.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Two groups of parameters are available: **Status** and **Config**. For each module, the connector will show a separate page for the status and config parameters. To control/configure the parameters, go to the corresponding Config page of the module.

All the information about the **Unit** module is shown on the **General**, **Device**, **Firmware**, and **Power Supply** pages.

### Available Modules

In the current connector version, the status and/or config parameters of the following modules are currently available:

| Module | Status | Config |
|-------------|---------------------|
| ASI | ✓  |  ✓ |
| SDI | ✓  |  ✓ |
| Genlock | ✓  |  ✓ |
| Streaming | ✓  |  ✓ |
| Demux | ✓  |  ✓ |
| Video | ✓  |  ✓ |
| Audio | ✓  |  ✓ |
| Analog Audio | x  |  ✓ |
| Ancillary Data | ✓  |  x |
| Return Data | ✓  |  x |
| Metadata | ✓  |  x |
| GPS | ✓  |  x |
| Serial | ✓  |  ✓ |
| SFP | ✓  |  ✓ |
| Network | ✓  |  ✓ |
| License | ✓  |  x |
| Unit | ✓  |  ✓ |
| Storage | ✓  |  x |
| USB | ✓  |  x |
| Time | ✓  |  x |
| Certificate | ✓  |  x |
