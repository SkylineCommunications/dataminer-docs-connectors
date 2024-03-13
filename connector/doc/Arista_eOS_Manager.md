---
uid: Connector_help_Arista_eOS_Manager
---

# Arista eOS Manager

The Arista eOS Manager connector can monitor Arista switches of type **7010T** and **7050SX:**

- **7010 series**: 1U low power (52 W) line-rate 1 Gb top-of-rack switch, with 4x10 Gb uplinks.
- **7050 series**: 1U low-latency cut-through line-rate 10 Gb and 40 Gb switches. Higher port density than the 7100 series, with a minimum of 52 x 10 GbE ports but slightly increased latency (1.2s or less).

## About

This connector can be used to monitor operational state data at the global **interface** level. **Platform** parameters are available for **PSU**, **Fan** and **Temperature**. **ACL**, **LLDP**, **BGP** and **PTP** information  are shown on the respective pages. On the **Explorer** page, you can fill in one or more API commands and immediately view the response.

- **gNMI** is used to retrieve device information.
- **HTTP** communication is used to retrieve information that is available in the Arista Command API.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version.         |-         |-         |

### Product Info

|Range  |Supported Firmware  |OpenConfig  |
|---------|---------|---------|
|1.0.0.x     |From eOS 4.25.1.F         |3.6.0         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |Yes       |Yes         |-         |-   |

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
On the Element Settings Page, fill in the eAPI Settings and push Log In to establish the eAPI communication.

#### Configuration of credentials for OpenConfig communication
On the Element Settings Page, fill in the OpenConfig Settings and push Connect to establish the OpenConfig communication.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Communication Settings

On the  **Communication Manager** page it is possible to adjust how the data is retrieved. If it is possible to retrieve the data from different connections it can be configured on the **Type** parameter (e.g. GNMI, HTTP,...).

When using GNMI it is possible to choose to "Subscribe" or to "poll" the data, this can be changed on the **Method** parameter. For "Subscribe" it is possible to configure an **Interval** of 0 or On Change, this will push the data when it changes to the connecter. For other values it will send the data every configured interval.

Right clicking on the table will provide you with the options to:

- **Add Subscription** provide a user friendly **Description**, **Commands** (e.g. interfaces/interface/state/admin-status) and a interval.
- **Delete Subscription** this will delete the selected **Custom Subsription**.

### Explorer

On this page, you can execute a command through the command API. This includes configuration commands. To do so, fill in the command in the **API Commands** box and click the **Send** button. You can execute multiple commands with one call, e.g. by filling in *show interfaces;show clock*.

The result will be displayed in the **API Response** box.

- **Request Viewer:** Displays the standalone parameter **API Request** which shows the full Request that is going to be sent based on the commands added by the user.

## Dataminer Connectivity Framework

The **1.0.0.x** range of the Arista eOS Manager connector supports the usage of DCF.

**DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).**



### Interfaces

#### Dynamic interfaces

Physical dynamic interfaces:

- **Interfaces**: Physical interfaces, type **inout** (in / out / inout).
