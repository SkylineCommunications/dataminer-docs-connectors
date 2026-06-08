---
uid: Connector_technical_Anywave_PA-8D-C-FA
---

# Anywave PA-8D-C-FA — Technical Documentation

## About

The Anywave PA-8D-C-FA is a high-power broadcast RF power amplifier with nine parallel solid-state amplifier modules and a 50 V DC supply rail. This connector polls the device over SNMP to retrieve run-status telemetry, alarm state, configurable thresholds, and system configuration, and allows write-back of all configurable parameters.

## Configuration

### Connections

#### SNMP Connection — SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The management IP address of the amplifier.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Initialization

After element creation, verify that **Control Mode** (on the System Settings page) is set to *Remote*. When the device is in *Local* mode, SNMP write commands are silently ignored by the device — threshold changes, attenuation adjustments, exciter selection, and all other set operations will have no effect.

### Web Interface

The web interface is accessible at `http://<device-ip>/` and provides the same status, settings, and alarm information as the connector pages. The web interface is only accessible when the client machine has network access to the device.

## How to Use

The connector is organised across four pages.

### General

Displays static system identification and version information polled at a slow rate (hourly):

| Parameter | Description |
|---|---|
| System Description | Full hardware and software description string reported by the device. |
| System Uptime | Time elapsed since the last system restart. |
| System Name | Administratively assigned hostname. |
| Firmware Version | Software version number of the PA controller board. |

### Status

The main operational page. Divided into two columns.

**Run Information (left column)** — polled every 10 seconds:

| Parameter | Unit | Notes |
|---|---|---|
| Forward Power | mW (displays as W / kW) | RF output power at the PA port. |
| Reflected Power | mW (displays as W / kW) | Reflected power at the PA output. Elevated values indicate load mismatch. |
| VSWR | — | Voltage Standing Wave Ratio. Scaled ÷1000 from raw value. |
| DC Supply Voltage | mV (displays as V) | 50 V supply rail voltage. |
| Module 1–9 Current | mA (displays as A) | Per-module DC current draw. Nine individual readings. |
| Total Current | mA (displays as A) | Sum of all module currents. |
| DC Supply Power | mW (displays as W / kW) | Total power drawn from the 50 V rail. |
| DC Efficiency | % | RF output power ÷ DC input power. Scaled ÷1000. |
| Current Attenuation | dB | Active attenuation applied at the PA input. |
| Exciter Mode Status | — | Runtime exciter mode: *Single* or *Dual*. |
| Temperature | °F | Internal PA temperature. Scaled ÷1000. |
| Operating Frequency | MHz | Active transmit frequency as reported by the PA. |

**Alarm Status (right column)** — polled every 10 seconds:

Each alarm shows *Normal* or *Alarm*:

- Forward Power Alarm
- Reflected Power Alarm
- VSWR Alarm
- Temperature Alarm
- DC Current Alarm
- DC Voltage Alarm
- Input Power Alarm
- Frequency Lock Alarm

A **System Settings...** page button in the alarm column provides quick navigation to the System Settings page.

### System Settings

Groups all writable configuration parameters. Polled at medium rate (every minute) so the displayed values reflect any out-of-band changes.

**TX Status**

| Parameter | Values | Notes |
|---|---|---|
| Transmitter State | ON / OFF | Mutes RF output without removing power from the PA. |

**Hardware Parameters**

| Parameter | Unit | Notes |
|---|---|---|
| Forward Power Calibration | — | Coupler/cable loss compensation factor for forward power measurement. Range 0–120. Encoded ×1000. |
| Reflected Power Calibration | — | Same for reflected power measurement. |
| Input Power Calibration | — | Same for input power measurement. |
| AC Input Voltage Minimum | mV (displays as V) | Lower bound for AC supply alarm. |
| AC Input Voltage Maximum | mV (displays as V) | Upper bound for AC supply alarm. |
| AGC Enable | OFF / ON | Enables Automatic Gain Control loop. |
| AGC Forward Power Setpoint | mW (displays as W / kW) | Target output power for the AGC loop. Only active when AGC is enabled. |
| Exciter Standard | CMMB / CTTB / DVB-T / ATSC / ISDB-T / DVB-T2 / ATV / CDR | Broadcast standard of the connected exciter. |
| Exciter Mode | Single / Dual | Configures single or dual exciter operation. |
| Attenuation | dB | Manual RF input attenuation. Range 0–111 dB in integer steps. |
| Active Exciter | Exciter A / Exciter B / None | Selects the active exciter in dual mode. |
| Control Mode | Local / Remote | Must be *Remote* for SNMP writes to take effect. |

**Alarm Thresholds** — all encoded ×1000 on the wire; values shown and entered in human-scale units:

| Parameter | Unit | Device Max |
|---|---|---|
| Forward Power Maximum | mW (displays as W / kW) | 2000 W |
| Reflected Power Maximum | mW (displays as W / kW) | 100 W |
| VSWR Maximum | — (÷1000) | 2.3 |
| Module 1 Current Maximum | mA (displays as A) | 12 A |
| Input Power Maximum | dBm (÷1000) | 31 dBm |
| Temperature Maximum | °F (÷1000) | 158 °F |
| Temperature Target | °F (÷1000) | 158 °F |

**Actions** — one-shot write-only controls; the device automatically resets these to their inactive state after execution:

| Parameter | Action |
|---|---|
| Clear System Alarms | Clears all latched alarms whose underlying fault has been resolved. |
| Clear System Log | Erases the device system event log. |
| Remote System Restart | Triggers a controller restart. Will interrupt transmission briefly. |
| Save Boot Configuration | Persists the current configuration to non-volatile memory. |

**Boot and Frequency Settings**

| Parameter | Values | Notes |
|---|---|---|
| Save Boot Configuration | OFF / ON | Saves current settings as power-on defaults. |
| Alarm Repeat Count | 1 / 2 / 3 | Number of times an alarm notification is repeated. Encoded ×1000. |
| Frequency Source | Auto / Manual | Auto locks to the exciter frequency; Manual uses the configured channel. |
| Manual Frequency Channel | 2–83 | Active when Frequency Source is *Manual*. Encoded ×1000. |

### Network Settings

Polled once per hour alongside system information. All three parameters are read/write.

| Parameter | Notes |
|---|---|
| IP Address | Management IP of the PA. Changing this will break SNMP connectivity until the element is updated. |
| Subnet Mask | Subnet mask for the management interface. |
| Default Gateway | Default gateway for the management interface. |

## Polling Architecture

The connector uses three timer groups to balance polling frequency against device load:

| Timer | Interval | Groups polled | Parameters |
|---|---|---|---|
| Fast | 10 s | Get RF and Power Status, Get Current and Thermal Status, Get Alarm Status | Run status (100–120), alarm status (121–128), forward power max (129) |
| Medium | 1 min | Get Alarm Thresholds and Calibration, Get System Configuration | Remaining thresholds (130–135), calibration and config (136–149) |
| Slow | 1 h | Get System Info, Get Network and Device Info | MIB-II system OIDs, control mode, freq/boot settings, network settings, firmware version |

## Value Encoding

All numeric parameters in the device's vendor MIB are encoded as integer × 1000. The connector decodes them for display as follows:

- **W, mW**: Dynamic units — base unit is milliwatts (mW). DataMiner automatically scales to W or kW based on magnitude.
- **A, mA**: Dynamic units — base unit is milliamps (mA). DataMiner automatically scales to A.
- **V, mV**: Dynamic units — base unit is millivolts (mV). DataMiner automatically scales to V.
- **°F, dBm, %, dB**: `div:1000` sequence applied in the Interprete block. Two decimal places displayed.
- **Write parameters (°F, dBm, %, dB)**: `*:1000` sequence applied so that values entered in human-scale units are multiplied back to the device's native encoding before being written via SNMP.
- **Write parameters (W, V, A)**: No sequence needed — DataMiner's dynamic units feature handles the back-conversion automatically when the user sets a value.

## Notes

The **Input Power** parameter (OID `.23.1.15.0`) is a DisplayString returning a signed value in millidBm. Values below 0 dBm will display as negative numbers after the ÷1000 decode (e.g., the device reporting `-16440` decodes to `-16.44 dBm`).

The **Operating Frequency** parameter (OID `.23.1.21.0`) is reported by the device in kHz × 1000. After ÷1000 decoding the value is in kHz; the unit label is set to MHz but the displayed value should be divided by 1000 once more in a QAction if true MHz display is required.

Write operations on all configuration parameters require **Control Mode** to be set to *Remote* on the device. In *Local* mode the device accepts SNMP SET requests without error but does not apply them.
