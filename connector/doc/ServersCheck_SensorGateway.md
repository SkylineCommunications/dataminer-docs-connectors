---
uid: Connector_help_ServersCheck_SensorGateway
---

# ServersCheck SensorGateway

## About
This connector is used to monitor the ServersCheck SensorGateway device, which acts as a hub for multiple sensors. The range of sensors that can be connected to the hub includes among others environmental, power, security, and industrial sensors.

All device information is retrieved via SNMP. The appropriate parameters are updated, and meaningful alarms are generated.

## Key Features

- **General**: Displays general information such as the System Name, Location, Product Name, and Version.
- **Control Sensors**: Contains information about all of control sensors and their respective Name, Value, Error Message, and Time. The display key can be updated for each sensor.
- **Temperature/Sound/Humidity/Dew Sensors**: Contains information about each type of control sensors. This list is not exhaustive but needs to be updated for new tyes of sensors.
- **Trap Errors**: Provides error information that is sent via traps from the sensors and the IO sensors.
- **Input Errors**: Displays information about the input errors such as the Sensor Name, Value, and Last Error Message.
- **Sensor Information**: Contains the Sensor Information table and shows when the last polling took place.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_ServersCheck_SensorGateway_Technical).
