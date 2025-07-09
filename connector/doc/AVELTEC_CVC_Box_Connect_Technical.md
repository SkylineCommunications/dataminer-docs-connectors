---
uid: Connector_help_AVELTEC_CVC_Box_Connect_Technical
---

# AVELTEC CVC Box Connect

## About

The CVC Box Connect regulation system manages heating, ventilation, and air conditioning (HVAC) functions in a modular and adaptable way.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the **Polling Settings** page, the **Polling Manager** table displays all the possible polling groups. You can manually trigger polling here with the Poll button, and you can configure the intervals for the timer that will automatically poll the groups. This way, you can adjust the polling to match your specific use case. The page also displays the last polled time.

All the polled information, as well as configurable parameters, are displayed on the appropriate data pages of the element.
