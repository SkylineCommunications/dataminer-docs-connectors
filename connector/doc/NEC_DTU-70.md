---
uid: Connector_help_NEC_DTU-70
---

# NEC DTU-70

The **DTU-70** is a liquid-cooled digital UHF TV transmitter. It incorporates a web server and SNMP agent, enabling monitoring and control of transmitter operations via a remote PC with a web browser, while also allowing an SNMP manager to monitor and control from a different location at the same time.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 7.3.5                  |

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

This page displays two tables: **DPA Status Table** and **DPA Alarms Table**.

### Cooling

This page displays the cooling information and cooling alarm status parameters.

### Configuration

On this page, you can configure the **exciter**, **pump**, and **heat exchanger**.
