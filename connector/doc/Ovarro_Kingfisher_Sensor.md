---
uid: Connector_help_Ovarro_Kingfisher_Sensor
---

# Ovarro Kingfisher Sensor

This connector provides a more detailed way of representing cards on the Ovarro Kingfisher device and therefore, elements should only be created via the Ovarro Kingfisher connector.

## About

### Version Info

| Range     		| Key Features     | Based on     | System Impact     |
|-------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]| Initial version  | -            | -                 |

### Product Info

This connector is not depending on a device firmware version. If a version dependency would occur between this driver and the main Ovarro Kingfisher connector, this wil be added.

### System Info

| Range  	| DCF Integration  	| Cassandra Compliant  	| Linked Components	| Exported Components	|
|-----------|-------------------|-----------------------|-------------------|-----------------------|
| 1.0.0.x  	| No       			| Yes         			| -         		|   					|

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Initialization is not required since elements are created fromt the Ovarro Kingfisher connector.

### Redundancy

There is no redundancy defined.


## How to use

Depending on the selected type of sensor during creation of the sensor element, a different page is shown.

### Digital Input / Digital Output

On the Digital Input/Output page, all 16 bit values of the card are shown.
The subpage with settings allows the configuration of these values.

The following configurations are supported:
- Change the string representation that corresponds to the 0 or 1 value of each bit.
- Change the name of the parameter itself to better represent the meaning of each bit.

### Analog Input

On the Analog Input page, all 8 sensor values are shown.
The subpage with settings allows the configuration of these values.

The following configurations are supported:
- Change the name of the parameter itself to better represent the meaning of each bit.
- Change the Units that goes with the sensor value, depending on what is being measured. (Current supported units are 'deg C' (degrees Celsius) and 'V' (volt)
- Change the range of the sensor by setting the Min and Max value.
