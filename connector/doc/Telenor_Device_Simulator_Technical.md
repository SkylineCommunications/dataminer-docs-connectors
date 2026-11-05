---
uid: Connector_help_Telenor_Device_Simulator_Technical
---

# Telenor Device Simulator

## About

The Telenor Device Simulator can be used to simulate any kind of device used in the Telenor EPM system.

The connector will generate **MAM** messages for each device. Those messages will be pushed to a collector element. The connector will also generate **Agama** files that will be picked up by an Agama consumer element.

## Configuration

### Connections

#### Serial connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the collector.
  - **IP port**: The IP port of the collector.

## How to Use

The **Devices** table lists all the devices that are currently configured. To add a new device, fill in the **Add Device ID** and **Add Device Type** parameters, and then click the **Add Device** button.

For each device, the **MAM** messages will be sent every 2 minutes. **Agama** files will be generated every 30 seconds.
