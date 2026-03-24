---
uid: Connector_help_Kymeta_U8_Technical
---

# Kymeta U8 Antenna

## About

The Kymeta U8 Antenna connector enables monitoring and control of the Kymeta U8 flat-panel antenna via HTTPS. It provides access to system status, RF parameters, GPS data, orientation metrics, and hardware sensor information, as well as configuration capabilities.

## Configuration

### Connections

#### HTTP Connection – Kymeta U8 API

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address of the Kymeta U8 antenna.
- **IP port**: The HTTP port of the device.

### Initialization

After creating the element, users must configure authentication credentials (username and password) to enable communication with the device.

## How to Use

The connector is structured into multiple pages, each focusing on a specific aspect of the antenna:

### General

Provides an overview of system and RF-related parameters:

- System time  
- BUC status  
- Model and serial number  
- Firmware version  
- HPA status  
- Output power and attenuation  
- Mute status  
- Temperature and alarms  
- Input voltage and power consumption  
- Reference settings (10 MHz source)  
- Redundancy mode  
- Active RF object  
- Modem, Multi-WAN, and XDG status  

### Authentication

Handles access control:

- Username  
- Password  
- Authentication status  

### Orientation

Displays antenna alignment:

- Pitch  
- Yaw  
- Roll  

### Position

Provides GPS-based location data:

- Last update timestamp  
- Speed and direction  
- Longitude and latitude  
- Altitude  

### Hardware Sensors

Monitors detailed hardware metrics:

- Input voltage and current  
- Aperture voltage and current  
- Quadrant temperatures (1–4)  
- Internal device temperature  
- Terminal power  
- Heater mode and status  
- LED lights mode, status, and off timer  

### Antenna Setup

Allows configuration of key RF parameters:

- RX frequency
- TX frequency  
- Polarization type  

## Notes

- Ensure HTTPS access is not blocked by firewalls or network policies.  
- Incorrect authentication credentials will prevent data retrieval.  
