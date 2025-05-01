---
uid: Connector_help_Dialight_INEM
---

# Dialight INEM

## About

The **Dialight INEM** (Integrated Network Card with Embedded Monitoring) is designed for seamless connectivity and remote monitoring of obstruction lighting systems. It enables direct Ethernet integration or wireless modem support, ensuring reliable performance for medium and high-intensity lighting setups.

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

## How to use

The element consists of the following data pages:

- **General**: Contains System information through System OIDs.
- **Status**: Contains a page button that includes the folliwng sub pages:
    - **AOL Beacons**: Contains the **High Aol Group** table.
    - **High Intensity Beacons**: Contains the **High Side Marker Group**, **High Relay Group**, **High Beacon Group**, **Module 1**, **Module 2**, and **Module 3** tables.
    - **Side Marker Beacons**: Contains the **Side Marker Group** table.
    - **D1RW**: Contains the **D1RW Group** table.
    - **Relay Beacons**: Contains the **Relay Group** table.

- **Events**: Contains the **Common Alarms** table.
- **High Main**: Contains various High Intensity parameters.
- **Medium 1 Main**: Contains various Medium Parameters
