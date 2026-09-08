## How to use

The element consists of the data pages detailed below.

### General

This page provides general information and network configuration details for the Norsat 1:1 LNB redundant controller.

#### Device Information

This section provides general information about the connected Norsat device, including device identification and other available device information.

#### Network Settings

This section provides information about the network configuration of the device, including its network-related settings.

### Device Status

This page provides an overview of the current operating status of the Norsat 1:1 LNB redundant controller and the connected LNBs.

#### Device Status

This section provides information about the currently active and standby LNB devices and the redundancy operating mode.

- **Active Device**: Displays the device(s) currently selected as the active LNB and allows the selection of a different active device.
- **Standby Device**: Displays the standby LNB device.
- **Automatic Mode Override**: Displays the current override status and allows the setting of override mode.

#### LNB Measurements

This section provides measurement information for the connected LNBs.

It displays the current LNB frequency band and the measured current for each LNB:

- **LNB Frequency Band**: Displays the frequency band currently in use and allows the user to select a different frequency band.
- **LNB 1 Current**: Displays the measured current of LNB 1 in mA.
- **LNB 2 Current**: Displays the measured current of LNB 2 in mA.
- **LNB 3 Current**: Displays the measured current of LNB 3 in mA.

### Device Config

This page provides configuration options for the Norsat 1:1 LNB redundant controller.

The following device configuration parameters can be viewed and modified through the DataMiner element:

- **ULC Status**: Displays the current ULC status and allows the user to enable or disable ULC.
- **Number of Supported Multiband LNB Bands**: Displays the number of multiband LNB bands supported by the device and allows the user to configure this value.

#### Alarm Thresholds

The Alarm Thresholds subpage allows configuration of the current warning and fault thresholds used to monitor the LNBs.

The following thresholds can be configured:

- **Maximum Current Fault Threshold**: Defines the upper current limit at which an over-current fault is generated.
- **Minimum Current Fault Threshold**: Defines the lower current limit at which an under-current fault is generated.
- **Maximum Current Warning Threshold**: Defines the upper current limit at which an over-current warning is generated.
- **Minimum Current Warning Threshold**: Defines the lower current limit at which an under-current warning is generated.

The configured thresholds are validated to ensure that the maximum thresholds are greater than or equal to their corresponding minimum thresholds before they are applied to the device.

### Alarms

This page provides an overview of the active LNB alarms and warnings reported by the device.

It provides visibility into current fault and warning conditions, allowing operators to identify abnormal LNB operating conditions and take appropriate corrective action.