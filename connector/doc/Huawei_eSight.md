---
uid: Connector_help_Huawei_eSight
---

# Huawei eSight

eSight is an enterprise-oriented O&M management solution. It implements converged management and provides centralized management, visualized monitoring, and analysis for enterprise ICT devices.

With this connector, you can monitor device information, status information, and alarms for this solution.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 21.2.0             |

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

To make sure the connector can retrieve information, go to the **General** page of the element and enter the username and password to log in to the API.

## How to use

The **General** page contains the parameters to log in to the API, as required during element initialization.

The **Devices** page shows the relevant information about each device within the system and its status.

The **Alarms** page contains every alarm that has not been cleared yet, the serial number attached to it, its severity, its description, and other relevant information.
