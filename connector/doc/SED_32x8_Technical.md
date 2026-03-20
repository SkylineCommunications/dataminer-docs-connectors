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
- **Device address**: Specify the IP address and GPIB address. For example: `lan[192.168.122.19]:gpib0,30`

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

## How to Use

The following pages are available in an element created with this connector:

- **General**: Displays the device **Application Information**, **Temperature Status**, and **Power Status**.
- **Matrix View**: Displays the 32x8 routing matrix.
- **Table View**: Displays the **Inputs** table and the **Outputs** table.