---
uid: Connector_help_TAG_Video_Systems_Media_Control_System_(MCS)
---

# TAG Video Systems Media Control System (MCS)

This is an HTTP-based connector that can be used to monitor and configure the **TAG Media Control System Platform**.

## About

### Version Info

| Range              | Key Features       | Based on | System Impact |
|--------------------|--------------------|----------|---------------|
| 1.0.0.x            | Initial version    | -        | -             |
| 1.0.1.x [SLC Main] | Connector overhaul | 1.0.0.7  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | API Version: 5.0       |
| 1.0.1.x   | API Version: 5.0       |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

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

REST API calls are used to establish communication with the device. For several of the tables, you can right-click the table to access a context menu that allows data manipulation and changes.

Certain settings, such as the layouts and channel configuration outside of the context menus, are stored on the **Tag Sets** page.

Note that SNMP traps are received via a hidden connection using port 162 in order to automatically update table information with new events.
