---
uid: Connector_help_General_Dynamics_Model_820A_Technical
---

# General Dynamics Model 820A Technical Documentation

## About

The General Dynamics Model 820A connector provides monitoring of satellite antenna control and tracking systems. It exposes controller status, antenna positioning data, alarm states, signal tracking parameters, and navigation-related information.

## Configuration

### Connections

#### Serial / Network Connection - Model 820A System

This connector uses a serial connection and requires the following input during element creation:

COMMUNICATION SETTINGS:

- **IP address/host**: IP address or hostname of the Model 820A controller.
- **IP Port**: 6767 default.

### Initialization

No additional configuration is required after element creation. Once communication is established, the connector automatically retrieves all available telemetry data.

## How to Use

The connector organizes monitoring information across the following pages: **General**, **Device Status**, **Alarm**, and **Navigation Data**.

### General

The General page provides controller-level information including:

- Controller Type
- Version Number
- Device Display (live system display output)

### Device Status

The Device Status page provides real-time antenna tracking data:

- Satellite Name
- Azimuth Position
- Elevation Position
- Polarization Position
- Automatic Gain Control Level
- Automatic Gain Control Channel
- Lock Status
- Track Mode Status
- Frequency Band
- Azimuth Limits
- Elevation Limits
- Polarization Limits
- Polarization Equipment Movement
- Azimuth Pulse
- Elevation Pulse

### Alarm

The Alarm page provides system alarm and movement status:

- Alarm Code
- Azimuth Alarm Status
- Elevation Alarm Status
- Polarization Alarm Status
- Azimuth Movement
- Elevation Movement
- Polarization Movement

### Navigation Data

The Navigation Data page provides positioning reference data:

- Latitude/Longitude Source (GPS, user-entered, etc.)
- Longitude Degrees
- Longitude Minutes
- Latitude Degrees
- Latitude Minutes
- Magnetic Variation Status
- Magnetic Variation
- True Heading
