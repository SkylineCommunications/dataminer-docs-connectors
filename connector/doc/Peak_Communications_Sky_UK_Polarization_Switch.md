---
uid: Connector_help_Peak_Communications_Sky_UK_Polarization_Switch
---

# Peak Communications Sky UK Polarization Switch

The Peak Communications Sky UK Polarization Switch is custom connector which can be used to display and configure information of the Peak Communications switches.

## About
Serial connection is used in order to retrieve and configure the information of the device.
### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                     |
## Configuration

### Connections
#### Serial connection - [Serial Connection]

This connector uses a serial connection and requires the following input during element creation:
Default value for TimeOut for single command is set to 2000ms and default value for retries is set to 1.

SERIAL CONNECTION:
- Interface connection:

  - **IP address/host**: [The polling IP of the device.]
  - **IP port**: [The IP port of the device.]
  - **Bus address**: [The bus address of the device. This field is required because connector use bus address to create commands]

### Initialization
Default value for TimeOut for single command is set to 2000ms and default value for retries is set to 1.

## How to use

General Page displays general data retrieved from "Get Monitor Switches" Command. On this page user can see positions per switches and also user can perform set for changing switch position.
On Switch Labels page user can configure labels for all retrieved switches and positions.

## Notes

Default value for TimeOut for single command is set to 2000ms and default value for retries is set to 1. This setup is because device need time to process sets.
