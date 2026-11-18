---
uid: Connector_help_Radeus_Labs_3500_BTR_Technical
description: "Configure the Radeus Labs 3500 BTR connector, connect it over RS-232, RS-485, or Ethernet, and monitor and control the beacon tracking receiver."
---

# Radeus Labs 3500 BTR

## About

The **Radeus Labs 3500 BTR** connector monitors and controls the Radeus Labs Model 3500 Beacon Tracking Receiver through its remote monitoring and control (M&C) protocol. It supports the L-band, C-band, and Ku-band models of the receiver.

The receiver has three M&C ports: RS-232, RS-485, and Ethernet. Only the port selected as active on the front panel of the receiver responds. The connector sends the same ASCII commands on every port; in RS-485 mode, each command is prefixed with the unit address.

The connector polls the receiver at the following intervals:

- Every **10 seconds**: Receive frequency, reference level, signal strength voltage, carrier lock, AFC status, and Accu-Trac state and offset.
- Every **minute**: RF input, Accu-Trac search width and delay, configuration settings, control mode, and active interface.
- Every **hour**: Model and firmware version.

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Interface connection**: Select the connection that matches the active M&C port of the receiver:

  - For the **Ethernet** port of the receiver, or the RS-232 or RS-485 port connected through a serial-to-IP converter, use an IP connection:

    - **IP address/host**: The IP address of the receiver or of the serial-to-IP converter. The factory default IP address of the receiver is *192.168.1.200*.
    - **IP port**: The TCP port of the receiver or of the serial-to-IP converter port.

  - For a serial port of the DataMiner Agent, select the COM port and use the following settings:

    - **Baudrate**: The baud rate configured on the front panel of the receiver (*1200*, *2400*, *4800*, *9600*, or *19200*). The default is *9600*.
    - **Databits**: *8*
    - **Stopbits**: *1*
    - **Parity**: *No*
    - **FlowControl**: *No*

- **Bus address**:

  - **RS-232** or **Ethernet**: Leave the bus address empty.
  - **RS-485**: Enter the unit address configured on the receiver as a decimal number. For example, enter *70* for address 0x46. The addresses *0*, *10*, and *13* cannot be used. Replies from other units on the bus are ignored.

### Initialization

No additional configuration is needed after the element is created. To control the receiver from DataMiner, set it to **Remote** mode with the **L/R** button on the front panel.

## How to Use

### General Page

This page shows the main receiver status:

- **Receive Frequency** and **Reference Level**: The frequency the receiver is tuned to, and the RF input level that gives 7.5 V on the signal strength output. Both parameters are trended.
- **Signal Strength Voltage**: The DC output voltage (0 to 10 V) proportional to the received signal level. This parameter is trended and can be alarmed, but it has no default thresholds, because the normal level depends on the reference level and the DAC slope. Set the thresholds per site in the alarm template.
- **Carrier Lock**: *OK* when the receiver is locked on to the carrier, *Fail* otherwise. *Fail* raises a critical alarm.
- **AFC Status**: The automatic frequency control status. *High* and *Low* raise a warning, and *Alarm* raises a critical alarm.
- **RF Input Selection**: The RF input (1 to 4) in use.
- **Last Device Error**: The last command error returned by the receiver, with a timestamp, for example *FREQ ERROR* or *REF ERROR*.

The receiver sets the frequency and the reference level with a single command. When you change one of them, the connector sends it together with the value of the other one reported by the receiver, or with the value you set just before if the receiver has not answered that set yet. Before sending them, the connector checks that the frequency is within one of the supported bands, and that the reference level is valid for that band:

- **L-band**: 930 to 2300 MHz, with a reference level from -100 to -40 dBm.
- **C-band**: 3400 to 4200 MHz, with a reference level from -90 to -30 dBm.
- **Ku-band**: 10700 to 12750 MHz, with a reference level from -90 to -30 dBm.

The frequency has a 1 kHz resolution, and the reference level has a 0.5 dB resolution. Once the **Model** is known, the connector also rejects a frequency outside the band of your receiver model, e.g., a C-band frequency on a 3500-L. Rejected values are not sent to the receiver: a pop-up window shows the reason, which is also logged in the element log.

### Accu-Trac Page

Accu-Trac keeps the receiver on the carrier when the carrier frequency drifts. This page shows:

- **Accu-Trac State**: *Track*, *Search*, *Delay*, *Alarm*, or *Disabled*. *Search* and *Delay* raise a warning, and *Alarm* raises a critical alarm.
- **Accu-Trac Offset**: The frequency offset from the configured receive frequency in kHz. It shows *Disabled* when Accu-Trac is off.
- **Accu-Trac Search Width** and **Accu-Trac Delay**: The search range and the delay before a search starts. Select *Disabled* to turn Accu-Trac off.

As with the frequency and reference level, the search width and the delay are sent together.

### Configuration Page

This page contains the receiver settings. The parameter names match the front panel of the receiver:

- **FFT AFC**: *Enabled* selects AFC mode and *Disabled* selects MFC mode (front panel AFC MFC selection). AFC mode is recommended in most cases.
- **FFT Average**: The low-pass filter bandwidth of the signal strength output (*Disabled*, *0.5 Hz*, or *5 Hz*).
- **FFT Width**: The FFT pre-detection bandwidth, from *3* to *280 kHz*. A narrow width rejects more interference, and a wide width tolerates more frequency drift.
- **5G Filter Mode**: Enables or disables the 5G filter.
- **DAC Slope**: The scaling of the signal strength output in V/dB (*0.25*, *0.50*, or *1.00 V/dB*).

When the receiver does not report a valid value for a setting, for example because the setting does not apply to the current receiver configuration, the connector shows the parameter as *Not Available*.

### Device Info Page

This page shows the **Model**, **Firmware Version**, **Control Mode**, **Active Interface**, **Baud Rate**, and **Unit Bus Address** of the receiver. These settings can only be changed on the front panel.

**Control Mode** raises a warning when the receiver is in *Local* mode, because changes from DataMiner may then not be applied.

## Notes

- After a setting is changed, the connector reads it back from the receiver, so the displayed value always reflects the receiver.
- If the receiver rejects a command, the error is shown in **Last Device Error**, and the displayed value does not change.
- The baud rate, the active interface, and the RS-485 address cannot be changed remotely.
