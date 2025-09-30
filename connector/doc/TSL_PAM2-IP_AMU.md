---
uid: Connector_help_TSL_PAM2-IP_AMU
---

# TSL PAM2-IP AMU

This device is an **Audio Monitoring Unit** (AMU) for precision audio, on IP networks. It supports Primary and Secondary Dante ports, SDI, AES and Analogue connections, so it can be used on traditional structures.

The protocol gets and sets data on the device through an HTTP API.

## About

### Version Info

| Range              | Key Features                  | Based on | System Impact |
|--------------------|-------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Audio control<br>- SFP data | -        | -             |

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
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

## How to use

### General

This page contains both the **audio configuration** and the **SFP data**.
