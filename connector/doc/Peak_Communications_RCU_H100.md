---
uid: Connector_help_Peak_Communications_RCU_H100
---

# Peak Communications RCU H100

The purpose of this connector is to manage and monitor the Peak Communications RCU H100 redundancy switching system. This system provides control over redundant units and ensures operational continuity by managing redundancy modes, unit statuses, and fault conditions.

The Peak Communications RCU H100 operates through a serial-based interface and supports both manual and automated operations for redundancy switching. It facilitates monitoring and control of connected units via a set of discrete commands and responses, allowing the management of system modes and monitoring of faults.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
| ------- | ------------------ |
| 1.0.0.x | SocketServer 11.17 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
| ------- | --------------- | ------------------- | ----------------- | ------------------- |
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port**: TCP/IP
- **IP port**: 8004
- **Bus address**: The bus address of the device (default: *32*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Monitoring and Management

The Peak Communications RCU H100 connector enables monitoring and management of redundancy settings, fault statuses, and operational modes. Key features include:

- **Fault Monitoring page**: Provides a detailed view of faults, including power supply faults, environmental faults, and general hardware issues.
- **Unit Status page**: Displays real-time information about connected units, such as the validity, online status, and CAN Bus connection status.
- **General page**: Offers system-wide information, including the unit type, serial number, operational status, and redundancy mode.

To monitor communication between the element and the device, use the Stream Viewer tool in DataMiner:

1. Right-click the element in the Surveyor.
1. Select **View** > **Stream Viewer**.
1. For healthy elements, you should see groups 1-4 for polling the data, and groups 5-6 for write commands.
