---
uid: Connector_help_General_Dynamics_Low_Power_Rack_SSPA
---

# General Dynamics Low Power Rack SSPA

This connector can be used to monitor the GD Satcom Low Power Rack SSPA using an SNMP (range 1.0.0.x) or serial (range 2.0.0.x) connection.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version with SNMP connection. | - | - |
| 2.0.0.x [SLC Main] | Initial version with serial connection. | - | - Existing elements using this connector need to be reconfigured when you switch to this range. <br>- Some parameters IDs were removed or changed. |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections - Range 1.0.0.x

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*

### Connections - Range 2.0.0.x

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device.
- **Bus address**: The bus address of the device.

## How to Use

From range 2.0.0.x onwards, the element created with this connector contains the following data pages:

- **General**: Displays generic information about the module, such as the **Unit Type**, **Firmware version**, **Operation Time** and **RF State**.

- **Module**: Displays specific information about the module, such as **General Status**, **Gate Voltage** and **Temperature**.

- **Settings**: Allows you to change device settings such as **Mode**, **Control** and **Attenuation**.

  Note: RF Power Fault Limits only work in dBm because of a device issue when values are set in dBW or Watts. The logic for the other units of measure is still in the connector, but hidden.

- **Active Faults**: Displays the module active faults, such as **Logic Board**, **Fan** and **Power Supply**.

- **Detailed Faults**: Displays the **Detailed Fault Table**, with detailed information about module failures.

- **Events**: Displays the **Event Log Table**, with information about the historical module failures.

## Notes

In range 1.0.0.x, a device issue can occur that makes it impossible to process the detailed fault information.

In range 2.0.0.x, RF Power Fault Limits only work in dBm because of a device issue when values are set in dBW or Watts. The logic for the other units of measure is still in the connector, but hidden.
