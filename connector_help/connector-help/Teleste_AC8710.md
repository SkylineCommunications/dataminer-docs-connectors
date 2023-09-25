---
uid: Connector_help_Teleste_AC8710
---

# Teleste AC8710

The AC8710 is a dual active output node, based on fixed receiver as well as modular return path transmitter.

This connector uses a **serial** connection to poll data from the AC8710 device.

## About

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main] | Initial version | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 2.9.2.r1.588                  |

## Configuration

### Connections

#### Serial Connection – Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the AC8000 device.
- **IP port**: The IP port of the AC8000 device.

### Usage

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The Alarm Limits, Status, and Alarms pages contain the most important parameters for monitoring.
