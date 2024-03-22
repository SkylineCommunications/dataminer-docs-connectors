---
uid: Connector_help_Ovarro_Kingfisher_Sensor
---

# Ovarro Kingfisher Sensor

This connector provides a more detailed way of representing cards of the Ovarro Kingfisher device. Elements using this connector are created via the [Ovarro Kingfisher](xref:Connector_help_Ovarro_Kingfisher) parent connector.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

At present, this connector does not depend on a specific device firmware version.

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

This connector is used by DVEs that are **created by the parent element** using the [Ovarro Kingfisher](xref:Connector_help_Ovarro_Kingfisher) parent connector.

## How to use

Depending on the selected type of sensor during the creation of the sensor element, a different page is shown.

### Digital Input / Digital Output

On the Digital Input/Output page, all 16 bit values of the card are shown.

The subpage with settings allows the configuration of these values. You can:

- Change the string representation that corresponds with the 0 or 1 value of each bit.
- Change the name of the parameter itself to better represent the meaning of each bit.

### Analog Input

On the Analog Input page, all 8 sensor values are shown.

The subpage with settings allows the configuration of these values. You can:

- Change the name of the parameter itself to better represent the meaning of each bit.
- Change the units that go with the sensor value, depending on what is being measured. Currently supported units are "deg C" (degrees Celsius) and "V" (volt).
- Change the range of the sensor by setting the minimum and maximum value.
