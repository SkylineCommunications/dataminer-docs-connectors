---
uid: Connector_help_IRT_IFC_Series
---

# IRT IFC Series

This connector is used to monitor and configure an **IRT IFC Series** device.
The **IRT IFC Series** is a Intelligent Frequency Converter and it is used for satellite transmission.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. By default *public*.
- **Set community string**: The community string used when setting values on the device. By default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector contains four following pages: **General**, **Configuration**, **Devices** and **Redundancy**.
Also it contains a **Web Interface** page.

**Redundancy** page is the default one and on that page you can find the information on type of redundancy and also on the
members of redundancy. 
It is possible on that page to change the **Switchover Mode** as well as setting individual members of redundancy in *active* or *standby* states.
(Setting the individual members status will only be available when the **Switchover Mode** is set to *manual*).

The **General** page displays generic information about the connector (**Name**, **Location**, etc.).

On the **Configuration** page user can configure the parameters of the individual modules.

The **Device** page contains informations on all of the modules that are available (**Temperature**, **Input/Output Power**, etc.).

When the connector is working properly, every table on every page should be populated accordingly and with the correct resolutions.
That all can be double checked by looking at the parameters in the web interface.

If everything works correctly, in the stream viewer you will be able to see Groups **100**,**1000**,**2000**,**3000**,**4000**,**5000** and **6000**.
Groups **1000**, **5000** and **6000** represent parameters that are checked every 10 seconds,
while the groups **100**, **2000**, **3000** and **4000** are checked every 10 minutes.

If there is a polling error with any of the groups, the stream viewer will return **GENERIC ERROR** in the response from the device.