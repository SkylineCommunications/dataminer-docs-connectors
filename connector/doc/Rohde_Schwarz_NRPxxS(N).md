---
uid: Connector_help_Rohde_Schwarz_NRPxxS(N)
---

# Rohde Schwarz NRPxxS(N)

This sensor measures the power of a given frequency. With this connector, you can configure the frequency, resolution, aperture time, average count, averaging filter mode and terminal control mode to obtain the measured power.

## About

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x [SLC Main] | Initial version. | No | Yes |
| 1.0.1.x | Version based on the VISA library. Fewer parameters are available using this range, so range 1.0.0.x is preferred in most cases. | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | Unknown                     |
| 1.0.1.x          | Unknown                     |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |
| 1.0.1.x | No              | Yes                 | -                 |                     |

## Configuration

### Connection

#### Serial Connection — Main — 1.0.0.x only

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device.

  - **Databits**: Databits specified in the manual of the device.

  - **Stopbits**: Stopbits specified in the manual of the device.

  - **Parity**: Parity specified in the manual of the device.

  - **FlowControl**: FlowControl specified in the manual of the device.

- Interface connection:

  - **IP address/host**: The polling IP of the device.

  - **IP port**: The IP port of the device.

#### Virtual Connection — Main — 1.0.1.x only

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

In range **1.0.1.x**, the dll *RsInstrument.dll* must be present in the ProtocolScripts folder.

The IP address of the device must be set on the **General** page.

## Usage

On the **General** page, you can set the configuration parameters for the measurement calculation. By default, these parameters will have the following values:

- **Frequency**: 10 MHz
- **Resolution**: 3
- **Aperture Time**: 0.02 ms
- **Average Count**: On
- **Averaging Filter Mode**: Resolution
- **Terminal Control Mode**: Repeat

In addition, you can configure the alarm threshold for the power measurement results, either in dBm or in nanowatts.

Extra functions that are available in this page are **Zero Calibration**, **Reset Sensor** and **Reboot**.

> [!NOTE]
> If **Reset Sensor** or **Reboot** are activated, the configuration parameters must be set again, as otherwise the measurement result will be "Not Available".
