---
uid: Connector_help_IDirect_Pulse_Terminal
---

# IDirect Pulse Terminal

This protocol represents a **terminal** in an iDirect Pulse NMS platform.

## About

This connector is automatically generated by the connector **IDirect Pulse Terminal Manager**. A terminal element represents an iDirect installation, for example on a vessel.

## Installation and configuration

### Creation

Virtual elements are automatically created by an **IDirect Pulse Terminal Manager** element.

## Usage

### General

This page contains general configuration information regarding this terminal, such as **DID, Satellite Router, IP addresses, Contact information**, ...

### Alarms

This page displays a table with all open alarms related to this terminal.

### Status

This page displays statistical information for this terminal, such as the **current operating beam, latency, jitter, CRC errors, acquisition data**, **power and SNR levels**, ...

### Config

This page displays general configuration parameters. These are the parameters that can be found on the "General" config page of the web interface.

### Packages

This page displays all installed software packages of this terminal.

### Performance Optimization

This page displays performance optimization configuration parameters. These are the parameters that can be found on the "Performance Optimization" config page of the web interface.

### Advanced

This page displays advanced configuration settings.

### Traffic

This page contains all Tx and Rx data traffic rates.

Apart from the total rate, also the separate rates for TCP, UDP, HTTP, ICMP, IGMP and other are available.

### Geolocation

This page displays all information related to the GPS position of the terminal.

The GPS trace is stored in a table with previous and current positions. The GPS trace is updated every 10 minutes, and data is stored for 30 days.

### Web Interface

This page displays the web interface of this terminal. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
