---
uid: Connector_help_GatesAir_Maxiva_XTE_DVBT2_Transmitter
---

# GatesAir Maxiva XTE DVBT2 Transmitter

This connector monitors the activity of the GatesAir Maxiva XTE DVBT2 Transmitter.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | E.3.3.0                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

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

## General

The General page displays information related to the **System**, the **Transmitter** and the **Exciter**.

## Alarms

This page displays the device **Alarms.** On the subpage **Event Configuration** it is possible to configure the traps.

## Transmitter

This page displays information about the device transmitter. More information is displayed on the **Switch** and **Versions** subpages.

## DVBT2 Modulator

This page displays the parameters and the tables related to the **DVBT2 Modulator**.

## DVBT2 Alarms

On this page it is possible to check and configure the **DVBT2 Alarms**.
