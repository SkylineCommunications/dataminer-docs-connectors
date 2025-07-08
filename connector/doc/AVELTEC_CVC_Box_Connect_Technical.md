---
uid: Connector_help_AVELTEC_CVC_Box_Connect_Technical
---

# AVELTEC CVC Box Connect


## About
The CVC Box Connect regulation system manages heating, ventilation, and air conditioning (HVAC) functions in a modular and adaptable way.

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

In the **_Polling Settings_** page, the **_Polling Manager_** table displays all the possible polling groups, which allow for manual polling, as well as the intervals that set the interval of the timer that will automatically poll the group(s).
All the polled information, and parameters that are settable, will be in their appropriate pages.
