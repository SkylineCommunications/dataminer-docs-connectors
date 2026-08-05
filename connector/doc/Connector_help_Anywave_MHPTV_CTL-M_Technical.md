---
uid: Connector_help_Anywave_MHPTV_CTL-M_Technical
---

# Anywave MHPTV CTL-M Technical

## About

The **Anywave MHPTV CTL-M** connector monitors and manages Anywave MHPTV transmitters equipped with a CTL-M controller via SNMP. It provides real-time visibility into RF performance metrics, alarm states, and system configuration for transmitters with more than three post amplifiers.

> [!NOTE]
> Version info is maintained via `<VersionHistory>` tags in protocol.xml. See the connector's version history for range details.

## Configuration

### Connections

#### SNMP Connection — Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

| Setting | Value |
|--|--|
| **IP address/host** | The polling IP of the device |
| **IP port** | The IP port of the device (default: *161*) |
| **Get community string** | The community string used for reading values (default: *public*) |
| **Set community string** | The community string used for writing values (default: *private*) |
| **Bus address** | Not required |

### Web Interface

The web interface is accessible directly from DataMiner via the **Web Interface** page. The client machine must have network access to the device for the web interface to load.

## How to Use

### General Page

The General page displays system identity and network configuration.

- **System Description**: Description string reported by the device.
- **System Uptime**: Time elapsed since the last device restart.
- **System Name**: Configured name of the device.
- **Controller Version**: Firmware version of the CTL-M controller.
- **Post Amplifier Version**: Firmware version of the post amplifier module.
- **Network IP Address**: Current IP address of the device.
- **Network Subnet Mask**: Subnet mask of the device network interface.
- **Network Gateway**: Default gateway configured on the device.

### Transmitter Page

The Transmitter page displays live RF performance metrics and the corresponding alarm state for each measurement.

**Run Information:**

- **Forward Power**: Output power measured at the transmitter forward port (mW).
- **Reflective Power**: Reflected power at the transmitter output (mW).
- **Voltage Standing Wave Ratio (VSWR)**: Impedance mismatch ratio between transmitter and antenna.
- **Rejected 1–4 Power**: Power rejected by each of the up to four post amplifier stages (mW).
- **Attenuator Current**: Current through the attenuator stage.

**Alarm Status:**

- **Forward Alarm**, **Reflective Alarm**, **VSWR Alarm**: Alarm state for the main RF metrics.
- **Rejected 1–4 Power Alarm**: Per-amplifier alarm state.
- **Input Power Alarm**: Alarm state for the input power level.

### System Configuration Page

The System Configuration page provides read/write access to transmitter operating parameters and exciter settings.

**System Configuration:**

- **Automatic Gain Control Switch**: Enables or disables AGC on the transmitter.
- **Post Amplifier Number**: Number of active post amplifier stages.
- **AGC Forward Standard**: AGC reference power level (W).
- **Transmit Switch**: Toggles the transmit output on or off.
- **Control Status**: Current operational control state.
- **Boot Set**: Triggers a device boot sequence.
- **Repeat Boot Times**: Number of boot repetitions (1–3).
- **Clear System Alarm**: Button that clears all active system alarms. A confirmation dialog is shown before the command is sent.

**Exciter Configuration:**

- **Exciter Type**: Type of exciter module installed.
- **Exciter Mode**: Operating mode of the exciter.
- **Exciter Used**: Selects the active exciter.
- **Exciter Band**: Frequency band of the exciter.
- **Exciter Frequency**: Carrier frequency of the exciter (MHz/GHz).
