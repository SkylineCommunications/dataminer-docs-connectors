---
uid: Connector_help_Asentria_SiteBoss_220
---

# Asentria SiteBoss 220

The **Asentria SiteBoss 220** connector is an SNMP connector that is used to monitor **Assentria SiteBoss 220** appliance that is a device for monitoring in remote equipment locations.

The device supports remote environmental monitoring such as temperature, humidity, water, smoke, entry, motion, and airflow within remote locations through the use of a variety of external sensors. It delivers alarms either by SNMP Traps or by polling of **Assentria SiteBoss 220's** MIB.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.9.2.r1.588           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The port of the connection device, by default *161.*

SNMP Settings:

- **Get community string**: The community string required to read from the device. The default value is *public*.
- **Set community string**: The community string required to set to the device. The default value is *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General Page

On this page, you can find configurable general system information such as **Serial Number, Version, Build, Site Name**, and **Product Name**.

There are also configurable time-related parameters such as **Device Date** and **Device Time** and the option to enable **Adjust for Daylight Savings**.

### Events Page

On this page, you can find the **Event Sensor Points** table, which organizes four basic attributes of points. A point is a particular sensor on an event sensor (e.g. temperature, humidity, contact closure 2, relay 5, etc.). The four point attributes are its name, whether it is in its event state, the point's value as a number, and its value as a string.

On this page you can also find page buttons to the sensor configuration pages regarding **Temperature**, **Humidity**, **Analog Input** and **Relay**.

#### Temperature Configuration Subpage

On this subpage, you can find the **Event Sensor Temperature Configuration**. This table displays three basic attributes of temperature sensor points:

- The configuration item (e.g. enable, name, etc.).
- The event sensor on which this point resides.
- The point number (always 1 for temperature sensors).

#### Humidity Configuration Subpage

On this subpage, you can find the **Event Sensor Humidity Configuration**. This table displays three basic attributes of humidity points:

- The configuration item (e.g. enable, name, etc.).
- The event sensor on which this point resides.
- The point number (always 1 for humidity sensors).

#### Analog Input Configuration Subpage

On this subpage, you can find the **Event Sensor Analog Input Configuration Table**. This table displays three basic attributes of analog input points:

- The configuration item (e.g. enable, name, etc.).
- The event sensor on which this point resides.
- The point number.

#### Relay Configuration Subpage

On this subpage, you can find the **Event Sensor Relay Configuration Table**. This table displays three basic attributes of relay points:

- The configuration item (e.g., enable, name, etc.).
- The event sensor on which this point resides.
- The point number.

### Networking Page

On this page you can find all the information regarding network information like **IP Address, Subnet Mask**, **Router Address**, **SNMP Read Community string**, **SNMP Write Community** string, and **SNMP Trap Community** string.

### Alerts Page

This page contains configurable alert settings.

Under the General Alert Settings, you can find the **System Alert Actions**. These define the actions that occur when the system needs to alert the user. You can also configure if the **PowerUp Alert** is enabled, if **Return to Normal Alerts** is enabled, and what the **Individual Alert Repeat Frequency** should be (in minutes).

This page also contains the **Email Alerts** configuration. Here you can configure the **Email Server**, the **Email Domain**, if **SMTP Authentication** is enabled, the **Email Authentication Username**, and the **Email Authentication Password.** You can also check which email addresses are configured, in the **Email Addresses table.**

Finally, there is also the **SNMP Alerts** configuration, where you can check which **SNMP Servers** are configured.

### Traps Page

On this page, you can find **Traps table** with the received traps from the device (e.g. PowerUp Trap, Contact Trap, Temperature Trap, Humidity Trap, and Test Trap).

### Web Interface Page

On this page, you can access the web interface. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
