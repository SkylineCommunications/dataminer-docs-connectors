---
uid: Connector_help_Teleste_AC8000
---

# Teleste AC8000

The AC8000 is a dual active output node that can work alone or be operated parallel.

## About

This connector uses **Serial** connection to poll data from the AC8000 device.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 2.0.0.x \[SLC Main\] | Initial version | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 4.8.13                     |

### Configuration

#### Connections

Serial Connection – Main
This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP of the AC8000 device.
- **IP port**: The IP port of the AC8000 device.

### Usage

The connector uses serial commands to request and push information to and from the node. This communication can be seen in the Stream Viewer.

The Alarm Limits, Status, and Alarms pages contain the most important parameters for monitoring.

The Spectrum page can be used to monitor and import real-time spectrum measurements that are being performed on the node.
