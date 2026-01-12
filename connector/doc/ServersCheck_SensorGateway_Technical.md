---
uid: Connector_help_ServersCheck_SensorGateway_Technical
---

# ServersCheck SensorGateway

This connector is used to monitor the ServersCheck SensorGateway device, which acts as a hub for multiple sensors. The range of sensors that can be connected to the hub includes among others environmental, power, security, and industrial sensors.

All device information is retrieved via SNMP. The appropriate parameters are updated, and meaningful alarms are generated.

## About

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version. | -            | -                 |
| 1.0.1.x   | Update Control Sensors Table and add subtables. | -            | Alarms and trending on control sensors need to be set again on subtables of each sensor type.                 |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 7.31                        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMP connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. 10.11.12.13.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use:

The element created with this connector consists of the following data pages:

- **General**: Displays general information such as the System Name, Location, Product Name, and Version.
- **Control Sensors**: Contains information about all of control sensors and their respective Name, Value, Error Message, and Time. The display key can be updated for each sensor.
- **Temperature/Sound/Humidity/Dew Sensors**: Contains information about each type of control sensors. This list is not exhaustive but needs to be updated for new tyes of sensors.
- **Trap Errors**: Provides error information that is sent via traps from the sensors and the IO sensors.
- **Input Errors**: Displays information about the input errors such as the Sensor Name, Value, and Last Error Message.
- **Sensor Information**: Contains the Sensor Information table and shows when the last polling took place.
