---
uid: Connector_help_TAG_Video_Systems_Media_Control_System_(MCS)
---

# TAG Video Systems Media Control System (MCS)

This is an HTTP-based connector that can be used to monitor and configure the **TAG Media Control System Platform**.

## About

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version  | -            | -                 |
|-----------|------------------|--------------|-------------------|
| 1.0.1.x   | Driver Overhaul  | 1.0.0.7      | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | API Version: 5.0       |
| 1.0.1.x   |                        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   |                     |                         |                       |                         |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization

Specify the following input configuration on the **Communication** page of the element:

- **Username**: Name of the user used in the HTTP login operation.
- **Password**: Password of the user used in the HTTP login operation.

## How to Use

REST API calls are used to establish communication with the device. Custom right-click context menus have been implemented on several tables which allows data manipulation and changes.

Certain sets, such as the layouts and channel configuration outside of the context menus are stored into the **Tag Sets** page.

Note: SNMP traps are received in a hidden connection and are connected over port 162 in order to automatically update table information with new events.
