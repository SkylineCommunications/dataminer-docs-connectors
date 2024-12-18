---
uid: Connector_help_Kratos_RF_Switching_System
---

# Kratos RF Switching System

The purpose of this connector is to manage and monitor RF signals for satellite communication systems using the Kratos RF Switching System's control. The system facilitates routing of RF signals between devices such as Block Upconverters (BUCs) and Solid State Power Amplifiers (SSPAs) by controlling multiple RF switches.

The Kratos RF Switching System operates through a TCP/IP-based interface using an ASCII command protocol. It supports both manual and automated operations, allowing for flexible control over switch positions and system modes. The web interface provides an intuitive platform for status monitoring, firmware updates, and device configuration.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
| ------- | ------------------ |
| 1.0.0.x | 1.14               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
| ------- | --------------- | ------------------- | ----------------- | ------------------- |
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port:** TCP/IP
- **IP port**: 4567

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector communicates with the system using commands and responses to set or retrieve information related to system operation modes, RF switch positions, and device statuses. Monitoring and operational details are distributed across the following pages:

- **General:** Displays system-wide operational information, including redundancy modes, operation modes, and alarms.
- **HPA (High Power Amplifier):** Focuses on High Power Amplifier statuses, including alarms and inhibit statuses for SSPA devices.
- **Switch State and Positions:** Provides details about RF switch positions, their statuses, and related control options.

To monitor the communication between the element and the device, you can use the built-in Stream Viewer tool in DataMiner:

1. Right-click the element in the Surveyor.
1. Select **View** > **Stream Viewer**.
1. For healthy elements, you should see groups 1-5 for polling the data, and groups 6-7 for write commands

After every successful set, the system will immediately trigger a get operation to retrieve the updated state. Any unsuccessful responses will be logged in the system and displayed as part of the connector's error reporting. If the connector receives an unrecognized response, it will generate a detailed error message in the element logs, specifying the invalid or unknown response format. This ensures that unhandled cases are documented for troubleshooting.
