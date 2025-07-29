---
uid: Connector_help_Paradise_SSPA_CO_Technical
---

# Paradise SSPA CO

## About

This connector is used to monitor and control compact outdoor solid-state power amplifiers (SSPAs) via serial communication. It provides visibility into amplifier performance, electrical readings, and fault indicators, and allows configuration of system behavior and alarm thresholds.

## Configuration

### Connections

#### Serial connection

This connector uses a serial connection and requires the following input during element creation:

- **Type of port**: The type of port of the connection. By default: *TCP/IP*.
- **IP address/host**: The polling IP or URL of the destination, e.g. *10.245.83.199*.
- **IP port**: The port of the destination, e.g. *7008*.
- **Bus address**: The bus address of the connected device, e.g. *1*.

## Usage

### System Info

Displays RF metrics and internal voltages:

- RF Power Level
- Reflected RF Power
- Present Attenuation Level
- SSPA Current
- Power Supply Voltage
- Temperature

### Communication Info

Shows communication configuration:

- Protocol Select  
- Baudrate  
- Network Address  

### Fault Status

Displays the state of key fault indicators:

- Summary Fault
- High Temperature Fault
- Low DC Voltage Fault
- Low DC Current Fault
- BUC Fault
- Auxiliary and Spare Faults
- RF Switch 1 and 2 State
- Unit Online Status

### Fault Monitoring Setup

Used to configure alarm thresholds and logic:

- Fault Logic (BUC, Spare, Auxiliary)
- Handling settings per fault type
- Thresholds for high temperature, low current, and spare fault window
- Normalize RF Power Level

### System Setup

Allows basic device control and configuration:

- Attenuation Level
- Standby Mode
- Mute State
- Gain Control Authority
- SSPA Calibration Mode
- System Mode
- Unit Startup State
- System Hierarchical Address

> [!NOTE]
> The connector was tested using firmware version *3.53* of the SSPA.