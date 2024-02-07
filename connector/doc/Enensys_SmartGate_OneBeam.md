---
uid: Connector_help_Enensys_SmartGate_OneBeam
---

# Enensys SmartGate OneBeam

The purpose of this connector is to monitor and control SmartGate-OneBeam devices through SNMP.

The Enensys SmartGate-OneBeam is a Digital Video Broadcasting – Terrestrial (DVB-T/T2) gateway for Direct-To-Home (DTH) TV. It is the control stream generator of the Enensys OneBeam solution.

OneBeam was built to reduce satellite OPEX costs by delivering Direct-To-Home TV and Digital Terrestrial TV (DTT) distribution over one satellite feed.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 5.1                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **SNMP version**: SNMPv1
- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: 161

SNMP Settings:

- **Get community string**: The community string used when reading values from the device.
- **Set community string**: The community string used when setting values on the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector uses SNMP to retrieve its data.

To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting **View** > **Stream Viewer**.

A healthy element will show groups 1000, 1200, 1400, 1600, 1800, and 2000 in the Stream Viewer.

### General Page

The General page contains basic device information and GPS-related parameters.

### Alarms Page

Each row in the **Current Alarms** table represents an alarm that comes from the SmartGate. Alarms will persist for as long as they are active.

The **Time** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

### ASI Page

This page contains information related to the two Asynchronous Serial Interface inputs (ASI1 and ASI2) and the single ASI output.

### IP Page

Everything related to IP is listed in the tables **IP Statistics** and **IP Configuration**.

It is possible to change the **IP Processing** state, the **Ethernet Port**, the **Input Mode**, the **Destination Address**, and the **Destination Port**.
