---
uid: Connector_help_Amagi_Cloudport_Service_Manager
---

# Amagi CLOUDPORT Service Manager

The Amagi CLOUDPORT Service Manager is a playout server that manages broadcast or OTT channels over IP, satellite, and FAST OTT platforms.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device, by default *443*.
- **Device address**: The device address, by default *ByPassProxy*.

### Initialization

Specify the **Username** and **Password** on the **General** page. The connector will automatically send requests using these credentials and will report the response code in the **HTTP Request Status** parameter.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created using this connector has the following data pages:

- **General**: This page displays general information such as the **Customer Name** and **Health Status**. You can also specify the **Username** and **Password** here.
- **Service Monitor**: This page displays the **Cloudport Services** table.
- **Cloudport Control**: This page contains various switchover-related parameters as well as the **Switchover** and **Fix** buttons and the **Poll Switchover Status Flag**. The flag will remain active from the moment a switchover starts until it is complete.
- **Logging**: This page contains the **Incident History Logs** table, which can be filled with the **Retrieve Logs** button. Do note that the Max Logs parameter has to have a value for this to be successful.
- **Web Interface**: This page contains the web interface.
