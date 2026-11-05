---
uid: Connector_help_xFusion_iBMC_Technical
---

# xFusion iBMC

## About

The xFusion iBMC or Intelligent Baseboard Management Controller is an embedded server management system that is used to manage servers throughout their lifecycle. The connector integration makes it possible to monitor the service.

### Product Info

| Range     | Supported Firmware                                        |
|-----------|-----------------------------------------------------------|
| 1.0.0.x   | 3.08.05.39 (U82) iBMC SW on xFusion FusionServer 1288H V7 |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP or URL of the device.
- **IP port**: The IP port of the device, by default *161*.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

On the **General** and **System** page, you can find information related to the system.

The **CPU**, **Memory**, **Hard Disk**, **Fans**, **Power**, **Network**, **PCIe**, and **SD Card** pages show the overall alarm status for that respective aspect of the system and contain a table with detailed information.

The **Sensors** and **Temperature** pages display the detailed sensor readings and thresholds.

The **Alarms** page contain the **Active Alarms Table**. This table displays a list of all Active Alarms received from the server. If a de-assert event is received for a specific event, that event will automatically be removed from the table. Note that the connector was developed and tested with the device configured to use "OID" mode for the trap notification settings. We therefore recommend using the connector in combination with the **Trap OID mode** on the device itself.

On a subpage, the **Trap Table** is included, where you can view all incoming traps from the server with their raw information. It is possible to limit the number of traps by a maximum number of traps or number of days.
