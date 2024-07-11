---
uid: Connector_help_NTI_ENVIROMUX_MINI_LXO
---

# NTI ENVIROMUX MINI LXO

The NTI ENVIROMUX MINI LXO is a device that helps with the monitoring of environmental conditions with a set of sensors like temperature, water, humidity and dry contact.
The NTI ENVIROMUX MINI LXO connector allows for the aggregation of the information from the different sensors, configuration and monitoring of each of the sensors.

## About

NTI ENVIROMUX MINI LXO helps users with the monitoring of the sensors by aggregating the information in a single quick access table with the most critical information of each sensor, and a page for each of the sensor to view and configure the sensor details.

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |


### System Info

In this subsection, insert a table with five columns. Indicate whether the range features **DCF integration** and whether it is **Cassandra compliant**.

In the "Linked Components"; column, list all DataMiner components that have a link, in any way, with this connector range, e.g. mediation connectors, Automation scripts, custom report, etc.

In the "Exported Components" column, list all the connectors that are exported by the parent connector in question.
**This can only be omitted for an exported connector or for a connector that cannot have exported connectors.**

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *public*)]

## How to use

### General

This page displays the general information of the device including: **DNS, Name, Location, IP, Mask and Gateway**

### Overview

This page displays the **Summary** table, that contains critical information of the sensors including:
	-**Sensor Name:** The name configured on the device for the sensor 
	-**Sensor Type:** The type of the sensor between Temperature, Humidity, Dry Contact and Water
	-**Sensor Value (Reading):** The value that the sensor has at the moment of the reading
	-**Sensor Status:** Indicates if the sensor is in alert or is not.

### Temperature (1, 2) Pages

This page displays information about the temperature sensor and allows the user to configure it:

-**Temperature Current Value:** Displays the current value (sensor reading).
-**Temperature Alert:** Displays the current alert state (On/Off).
-**Temperature Sensor Name:** Allows the user to view and edit the sensor name.
-**Temperature Sensor Unit:** Allows the user to view and edit the sensor unit of measurement.
-**Temperature Sensor Low Threshold:** Allows the user to view and edit the sensor low threshold, when the value is below this parameter the sensor alert will be set to the value On.
-**Temperature Sensor High Threshold:** Allows the user to view and edit the sensor high threshold, when the value is above this parameter the sensor alert will be set to the value On. 

### Humidity (1, 2) Pages

This page displays information about the humidity sensor and allows the user to configure it:

-**Humidity Current Value:** Displays the current value (sensor reading).
-**Humidity Alert:** Displays the current alert state (On/Off).
-**Humidity Sensor Name:** Allows the user to view and edit the sensor name.
-**Humidity Sensor Low Threshold:** Allows the user to view and edit the sensor low threshold, when the value is below this parameter the sensor alert will be set to the value On.
-**Humidity Sensor High Threshold:** Allows the user to view and edit the sensor high threshold, when the value is above this parameter the sensor alert will be set to the value On. 

### Dry Contact (1, 2, 3, 4) Pages

This page displays information about the dry contact sensor and allows the user to configure it:

-**Dry Contact Status:** Displays the current status (Open/Closed).
-**Dry Contact Alert:** Displays the current alert state (On/Off).
-**Dry Contact Sensor Name:** Allows the user to view and edit the sensor name.
-**Dry Contact Sensor Alert Status:** Allows the user to view and edit the value that will set the alert status to On or Off. i.e. If set to Alert when Open, the alarm value will be on if the status value is Open.

### Water Page

This page displays information about the water sensor and allows the user to configure it:

-**Water Status:** Displays the current status (Open/Closed).
-**Water Alert:** Displays the current alert state (On/Off).
-**Water Sensor Name:** Allows the user to view and edit the sensor name.
-**Water Sensor Alert Status:** Allows the user to view and edit the value that will set the alert status to On or Off. i.e. If set to Alert when Open, the alarm value will be on if the status value is Open.

### Configuration

This page provide the user a set of parameters that enable or disable the polling of each sensor.
Disabling the polling of any sensor will remove the sensor from the **Summary table** and will hide the page.
Enabling the polling of any sensor will add the sensor to the **Summary table** and will show the page again.

By default Temperature 2 Sensor and Humidity 2 Sensor will be hidden.

