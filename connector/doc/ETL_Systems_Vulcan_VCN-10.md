---
uid: Connector_help_ETL_Systems_Vulcan_VCN-10
---

# ETL Systems Vulcan VCN-10

The **ETL Systems Vulcan VCN-10** connector can be used to display and configure information of the ETL Systems Vulcan VCN-10 device.

## About

This connector can be used to monitor and control the **ETL Systems Vulcan VCN-10** device. The connector supports one serial connection to communicate with the device.

The connector also features alarm monitoring and trending.

### Version Info

| Range   | Key Features                                          | Based on | System Impact                                    |
|---------|-------------------------------------------------------|----------|--------------------------------------------------|
| 1.0.0.x | Initial version.                                      | -        | -                                                |
| 1.0.1.x | Matrix size changed from 1024x1024 to 128x128.        | -        | **Ports.xml file will no longer be compatible.** |
| 1.0.2.x | DCF implemented.                                      | -        | -                                                |
| 1.0.3.x | Name added in Parameter Group, which will affect DCF. | -        | -                                                |

### Product Info

| Range   | Supported Firmware Version |
|---------|----------------------------|
| 1.0.1.x | E405 Version 01.03         |

### System Info

| Range           | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x         | No              | Yes                 | -                 |                     |
| 1.0.1.x         | No              | Yes                 | -                 |                     |
| 1.0.2.x         | Yes             | Yes                 | -                 |                     |
| 1.0.3.x         | Yes             | Yes                 | -                 |                     |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP or URL of the destination, e.g. *81.144.135.46.*
- **IP port**: The port of the destination e.g. *4000*.
- **Bus address**: This field is optional.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page displays general information about the device, such as the System Name, Firmware Version, and System Version.

### Matrix Page

This page displays the matrix containing the connections on the device.

The following actions are possible on the matrix:

- Setting a new connection by clicking the desired connection. Note that this can disconnect a previous connection.
- Locking an output by right-clicking the output and then clicking **Lock**. Note that the device does not support locking an input, so if you try to use that option, nothing will happen on the device.
- Blocking a connection by right-clicking in the matrix, selecting the **Edit** option, and then selecting the relevant connection on the pop-up page.
- Editing the labels by right-clicking in the matrix, selecting the **Edit** option, and then changing the field description of the relevant output or input on the pop-up page.

This page also contains a **Reset Labels** button. Click this button to send a command to the device that will reset all the matrix labels to the default values.

Finally, the page contains a **Show Route** page button. Click this button and then choose the relevant output to check the route. The result will be displayed in the parameters **Input**, **Mid Matrix Card**, **Mid Matrix Input**, and **Mid Matrix Output.**

### Interfaces Page

This page displays the Input and Output tables. Both tables contain the indexes and labels. The Output table also contain a column for the connected input.

### Matrix Status Page

This page displays a table with the general status of the matrix cards. It also contains three page buttons:

- **OMC Status:** Displays the Mid Matrix Output status.
- **MMC Status:** Displays the Mid Matrix Card status.
- **IMC Status:** Displays the Mid Matrix Input status.

### System Status Page

This page displays the general status of the device. It contains information such as the Power Supply status, Communication status, and Chassis CPU temperature.

The following two buttons can also be found on this page:

- **Initialize monitoring:** Activates chassis monitoring by the device.
- **Clear Alarms:** Sends a command to clear all the alarms on the device.

Finally, the page contains two page buttons:

- **Fan Status:** Shows the status of the various fans on the device.
- **Temp. Status:** Shows the temperature of various elements on the device.

### Configuration Page

This page is divided in three different sections:

- **Matrix Configuration:** Allows you to configure parameters related to the matrix, e.g. Number of Outputs, Control Mode.
- **Ethernet Configuration:** Allows you to configure the Ethernet, e.g. Speed.
- **Network Configuration:** Allows you to configure the network, e.g. Matrix IP Address, Default Gateway, etc.

The page also contains two different page buttons:

- **Advanced Config.:** Allows you to adjust advanced configuration settings. Note that advanced configuration changes will reset the device.
- **Maintenance:** Allows you to configure the IMC and OMC communication cards.

### Web Interface

This is the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
