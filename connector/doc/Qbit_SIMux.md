---
uid: Connector_help_Qbit_SIMux
---

# Qbit SIMux

The **Qbit SI Multiplexer** is used to configure the service information data within transport streams on individual PID level. Per PID, it is possible to define which of the multiple inputs will be used, by using the PID groups available on the device.

The **Qbit SIMux** connector shows status information for the device and can be used to configure the device.

## About

### Version Info

| Range                | Key Features     | Based On     | System Impact    |
|----------------------|------------------|--------------|------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.0-rc10+d5360f1f      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

### Initialization

To be able to access the device, specify a correct username and password on the **General** > **Authentication** page.

## How to use

The following pages are available:

- The **General** page contains system parameters.
- On the **Versions** page, you can find the current image and software versions.
- The **Interfaces** page shows a list of all available interfaces.
- The **Inputs** page contains a table with different types of inputs and the included PID configurations.
- The **PID Groups** page contains a table with all PID groups.
- The **Outputs** page contains a list of all configured outputs. An output must have a reference to a PID group (in the PID Groups table).

Most of the tables have a right-click menu available that offers extra functionality such as adding, editing, or deleting an entry.
