---
uid: Connector_help_IRT_IFC_Series
---

# IRT IFC Series

This connector is used to monitor and configure an IRT IFC Series device.

The **IRT IFC Series** is an intelligent frequency converter. It is used for satellite transmission.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.11.22                |

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

This connector contains the following pages: **General**, **Configuration**, **Devices**, and **Redundancy**, as well as a **Web Interface** page.

- The **Redundancy** page is the default page. Here you can find the information on the type of redundancy and also on the redundancy members. On this page, you can change the **Switchover Mode** and set individual redundancy members to *active* or *standby*. Note that setting the status of individual members is only possible when the **Switchover Mode** is set to *Manual*.

- The **General** page displays general information about the connector such as the **Name** and **Location** of the device.

- On the **Configuration** page, you can configure the parameters of the individual modules.

- The **Device** page contains information on all of the available modules that are available, including the **Temperature**, **Input/Output Power**, etc.

When the connector is working properly, every table on every page should be populated accordingly and with the correct resolutions. You can double-check this by looking at the parameters on the web interface.

If everything works correctly, in the Stream Viewer you will be able to see groups **100**, **1000**, **2000**, **3000**, **4000**, **5000**, and **6000**.

- Groups **1000**, **5000**, and **6000** represent parameters that are checked every 10 seconds.
- Groups **100**, **2000**, **3000**, and **4000** are checked every 10 minutes.
- If there is a polling error with any of the groups, the Stream Viewer will return **GENERIC ERROR** in the response from the device.
