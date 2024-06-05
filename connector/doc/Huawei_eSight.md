---
uid: Connector_help_Huawei_eSight
---

# Huawei eSight

eSight is an enterprise-oriented O&M management solution. It implements converged management and provides centralized management, visualized monitoring, and analysis for enterprise ICT devices.
This connector purpose is to monitor the devices information and status, and the alarms currently present in the system.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                                   |
|-----------|------------------------------------------------------|
| 1.0.0.x   | 21.2.0 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

**HTTP CONNECTION:**

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

For the connector to retrieve the desired information, it is necessary to set the proper credentials (username/password) in the **General page** once the element is initialized.

### Redundancy

There is no redundancy defined.

## How to use

In the **General** page, the parameters (username/password) required for login to the API can be found.

The **Devices** page shows the relevant information about each device within the system and its status.

The **Alarms** page contains every alarm which has not been uncleared yet, the serial number attached to it, its severity, description, and more relevant information about it.
