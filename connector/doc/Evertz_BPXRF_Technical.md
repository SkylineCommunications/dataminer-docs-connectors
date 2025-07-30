---
uid: Connector_help_Evertz_BPXRF_Technical
---

# Evertz BPXRF

## About

This connector monitors the input and output of different Evertz cards inside a single chassis. The following cards are supported:

- Evertz 7703PA
- Evertz 7703BPX

15 slots are available, which means that 14 cards can be added. Slot zero is reserved for the frame carrier.

Data is polled via SNMP.

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version  | -        | -             |
| 1.1.0.x [SLC Main] | OID changes/parameter description changes      | 1.0.0.6  | No polling may happen for existing tables. |

## Configuration

### Connections

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the destination, e.g. *10.11.12.13*.

SNMP Settings:

- **Port number**: The IP port of the destination, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

## Usage

The Evertz BPXRF connector displays information about the two kinds of supported cards. For each detected card, a child element will be created under the main element.

The connector provides six data pages. The first three pages are used for the monitoring of the 7703PA card, while the other pages are used for the monitoring of the 7703BPX card.

### General PA

This page displays data about the **Input Power** and miscellaneous data about the card, such as **Type**, **Firmware**, etc.

### Fault PA

This page lists all the alarms that can be reported by the 7703PA card. For each alarm, you can enable or disable the traps.

Note that traps are not currently supported by this connector: nothing will happen if a trap is received.

### Control PA

This page allows you to set different parameters such as **Gain** and **Output Level**.

### General PX

This page displays data about the **Input Power** and miscellaneous data about the card, such as **Card Type**, **Current Active Channel**, etc.

### Fault BPX

This page lists all the alarms that can be reported by the card 7703BPX. For each alarm, you can enable or disable the traps.

Note that traps are not currently supported by this connector: nothing will happen if a trap is received.

### Control BPX

This page allows you to set different parameters such as **Threshold** and **Delay**.
