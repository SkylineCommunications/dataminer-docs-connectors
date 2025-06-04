---
uid: Connector_help_Arista_eOS_Manager
---

# Arista eOS Manager

The Arista Manager connector can monitor all Arista systems running the **Arista EOS** operating system.

This connector can be used to monitor operational state data at the global **interface** level. **Platform** parameters are available for **PSU**, **Fan**, and **Temperature**. **ACL**, **LLDP**, **BGP**, and **PTP** information is shown on the respective pages. On the **Explorer** page, you can fill in one or more API commands and immediately view the response.

**gNMI** is used to retrieve device information. **HTTP** communication is used to retrieve information that is available in the Arista Command API.

> [!IMPORTANT]
> When gNMI is used to retrieve device information:
>
> - The Communication Gateway DxM must be installed on the DataMiner Agent (DMA).
> - Configure the connector to run with its own **SLProtocol** and **SLScripting** processes (see [Configuring separate SLProtocol and SLScripting instances for a specific protocol](https://aka.dataminer.services/configuring-separate-slprotocol-and-slscripting-instances)).
> - Limit the number of elements for one DataMiner Agent to approximately 60.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware | OpenConfig |
|---------|--------------------|------------|
| 1.0.0.x | From eOS 4.25.1.F  | 3.6.0      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | Yes             | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *80*
- **Bus address**: *ByPassProxy*
- **Timeout on a single command (ms)**: *45000* (avoids timeouts in slow responses)

### Initialization

#### Configuration of credentials for eAPI communication

On the **Element Settings** page, fill in the **eAPI Settings** and click **Log In** to establish the eAPI communication.

#### Configuration of credentials for OpenConfig communication

On the **Element Settings** page, fill in the **OpenConfig Settings** and click **Connect** to establish the OpenConfig communication.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Communication Settings

On the **Communication Manager** page, you can adjust how the data is retrieved. If it is possible to retrieve the data from different connections, you can configure this using the **Type** parameter (e.g. gNMI, HTTP, etc.).

When gNMI is used, you can choose to "Subscribe" or to "poll" the data. You can change this using the **Method** parameter. For "Subscribe", you can configure an **Interval** of *0* or *On Change*. The latter will push the data to the connecter whenever it changes. For other values, it will send the data every configured interval.

You can delete a selected custom subscription from the table by right-clicking it and selecting **Delete Subscription**.

### Explorer

On the Explorer page, you can execute a command through the command API. This includes configuration commands. To do so, fill in the command in the **API Commands** box and click the **Send** button. You can execute multiple commands with one call, using a semicolon as separator, e.g. *show interfaces;show clock*.

The result will be displayed in the **API Response** box.

The **Request Viewer** button displays the standalone parameter **API Request**, which shows the full request that is going to be sent based on the commands added by the user.

## DataMiner Connectivity Framework

The **1.0.0.x** range of the Arista eOS Manager connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).

### Interfaces

#### Dynamic interfaces

Physical dynamic interfaces:

- **Interfaces**: Physical interfaces, type **inout** (in/out/inout).
