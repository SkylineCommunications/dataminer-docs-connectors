---
uid: Connector_help_Novella_Satcoms_B356_Technical
---

# Novella Satcoms B356

## About

​The Novella Satcoms B356 is an L-band beacon tracking receiver designed to track and measure beacons from various commercial and military satellites. It operates within an input frequency range of 940 MHz to 2,150 MHz and is commonly used in antenna tracking controllers and uplink power controllers.

## Configuration

### Connections

#### Serial Connection - 1

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600* (range: *300* - *9600*).
  - **Databits**: Databits specified in the manual of the device, e.g. *7*.
  - **Stopbits**: topbits specified in the manual of the device, e.g. *1*.
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No*.

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.
  - **Bus address**: The bus address of the device.

## How to use

The **General** page displays the following parameters:

- Control Status
- Selected Input
- Frequency
- DC Output
- Alarm Status

The **Offset Status** page displays both read and write parameters for DC Offset and Display Level Offset. The result of DC Offset changes may be the saturation of the DC output voltage at one of the DC supply rails of the applicable operational amplifiers (±15 V). Changing the Display Level Offset directly affects the level display on the front panel.
