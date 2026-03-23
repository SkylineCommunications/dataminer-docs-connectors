---
uid: Connector_help_SED_32x8_Technical
---

# SED 32x8

## About

The SED 32x8 is a signal routing matrix device. This connector uses GPIB communication to monitor and configure the SED 32x8 matrix, providing visibility into routing states, temperature status, and power status.

## Configuration

### Connections

#### GPIB Main Connection

This connector uses a GPIB connection and requires the following input during element creation:

GPIB CONNECTION:

- **I/O API**: Choose between SICL or VISA.
- **Device address**: Specify the IP address and GPIB bus address of the device. Default: `lan[machinename]:gpib0,1`

  - For SICL communication, use the format `lan[machineName]:gpib0,<busAddress>`, where:
    - `lan` is the SICL Interface name in the IO configuration.
    - `machineName` is the IP address of the network GPIB interface.
    - `gpib0` is the Remote SICL Interface Name.
    - `<busAddress>` is the GPIB bus address set on the device (range: 0–30).
  - For VISA communication, use the format `GPIB10::<busAddress>::INSTR`, where:
    - `GPIB10` is the VISA Interface Name.
    - `<busAddress>` is the GPIB bus address set on the device.
    - `INSTR` is a fixed string.
    - Alternatively, you can use an alias defined in the Keysight Connection Expert application.

The following serial communication settings are used by default:

| Setting      | Value |
|--------------|-------|
| Baud rate    | 19200 |
| Data bits    | 8     |
| Stop bits    | 1     |
| Parity       | None  |
| Flow control | None  |

## How to Use

The following pages are available in an element created with this connector:

- **General**: Displays the device **Application Information** (firmware version, board type, and manager health), **Temperature Status**, and **Power Status**.

- **Matrix View**: Displays the full 32x8 signal routing matrix, allowing crosspoint connections to be viewed and set.

- **Table View**: Displays the **Inputs** and **Outputs** tables. Labels for inputs and outputs can be edited directly from the tables. Note that label changes are stored at the DataMiner level only, as the device does not support label configuration via the protocol.

## Notes

The connector exposes serialized matrix parameters (`MatrixConnectionsBuffer` and `MatrixSerialized`) that can be used by a virtual router control driver to aggregate multiple SED 32x8 elements into a single combined routing topology.