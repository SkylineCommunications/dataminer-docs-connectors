---
uid: Connector_help_AVELTEC_CVC_Box_Connect
---

# AVELTEC CVC Box Connect

The CVC Box Connect regulation system manages heating, ventilation, and air conditioning (HVAC) functions in a modular and adaptable way.
## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.1	|Initial development|-         |-         |


#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

#### Polling Manager

This page contains a polling table where it is possible to change the interval and state of each polling group to cater to your specific use case. It also displays the last polled time and a Poll button that can be used to manually trigger the polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

    General: Contains the device information, users table, and trap configuration table.
    Alarm Control: Displays the alarms page, and their state.
    Installer Control: Contains the device configuration page.
    User Control: Contains user page that has current readings.
    Statistics:Contains the readings statistics for inside and outside temperature and humidity.
    Polling Manager: Contains the polling manager that enables or disables groups.
    Web Interface : Contains SNMP trap and trap destination settings.


