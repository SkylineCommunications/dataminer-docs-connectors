---
uid: Connector_help_Agilis_AUC28
---

# Agilis AUC28

The AUC28 wideband series converter is an RF indoor subsystem that provides frequency conversion of 70 MHz/140 MHz (±18 MHz) or 140 MHz (±36 MHz) IF signals to L-Band signals (950 – 2150 MHz or 950 – 1850 MHz) on the transmit side and conversion of L-Band signals (950 – 2150 MHz or 950 – 1850 MHz) to 70 MHz/140 MHz (±18 MHz) or 140 MHz (±36 MHz) IF signals on the receive side.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, in this case *9600*.
  - **Databits**: Databits specified in the manual of the device, default value *8*.
  - **Stopbits**: Stopbits specified in the manual of the device, default value *1*.
  - **Parity**: Parity specified in the manual of the device, default value *No*.

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device.

## How to use

The element has several pages where you can monitor or configure the parameters of the device:

- The **General** page contains information about AUC, BUC, Alarms, and other general parameters related to the device.

- The **Voltage and Temperature** page contains information about the current voltage and temperature of output and SSPA. You can set the SSPA temperature here.

- The **Equipment Status** page shows all information available on the equipment.

- The **Frequency and Attenuation** page contains current information on temperature and attenuation and allows you to set the uplink and downlink frequency and attenuation.
