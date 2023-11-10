---
uid: Connector_help_NEC_DTL-30
---

# NEC DTL-30

The **DTL-30** is an air-cooled digital UHF TV transmitter. It incorporates a web server and SNMP agent, enabling monitoring and control of transmitter operations via a remote PC with a web browser, while also allowing an SNMP manager to monitor and control from a different location at the same time.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 8.2.5                  |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays the status parameters, most notably the **TX Forward Power** and **TX Reflected Power**. It also contains a page button to the **System Information** subpage.

### TX Overview

This page displays the alarm status parameters.

### PA Overview

This page displays two tables: **PA Status Table** and **PA Alarms Table**.

### DPA Overview

This page displays the **DPA Status Table**.

### Configuration

On this page, you can configure the **exciter**, **pump**, and **heat exchanger**.
