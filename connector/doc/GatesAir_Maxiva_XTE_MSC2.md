---
uid: Connector_help_GatesAir_Maxiva_XTE_MSC2
---

# GatesAir Maxiva XTE MSC2

The GatesAir Maxiva XTE Multi-System Controller (MSC2) monitors and controls transmitter systems and controls RF switching. The MSC2 supports a range of backup options, including 1+1, full N+1, and dual-transmitter installations.

This connector monitors the activity of the GatesAir Maxiva XTE MSC2 device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial Version  | \-           | \-                |
| 2.0.0.x \[SLC Main\] | Supports only N+1 Parameters  | 1.0.0.4 | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | \-                     |
| 2.0.0.x   | 06.00.0032 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |
| 2.0.0.x   | No                  | Yes                     | \-                    | \-                      |

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

## How to use (1.0.0.x)

The **General** page displays information about the system such as the **Controller Status**, the **Switch State**, and the **Control State**. On the **Configuration** subpage, you can configure the **system parameters** and enable the **controller events**.

On the **Transmitter** page, you can check the current status of the **Alarm** parameters and the current values of transmission parameters like the **Frequency**, **Power**, and **VSWR**. On the **Events** and **Configuration** subpages, you can set the transmitter definition parameters.

## How to use (2.0.0.x)
The **General** page displays information about the system such as the **Controller Status**, the **Switch State**, and the **Control State**. On the **Configuration** subpage, you can configure the **system parameters** and enable the **controller events**.

On the **Main Transmitter** page, you can see configurable general info on the main transmitters. 
The **Main TX Status** subpage will show the statuses of the transmitters. 
The **Main TX Events** subpage allows you to enable/disable trap generation.
The **Main TX Auto Restore** subpage displays configurable Auto Restore parameters.

The **Reserve Transmitter** page shows the statuses and measurements parameters.
The **Reserve TX Configuration** subpage allows you to set Reserve TX parameters.
The **Reserve TX Trap Events** subpage allows you to enable/disable trap generation.

The **Input Switch** page shows configurable Input Switch parameters.
The **Failed Verifications** page shows parameters related to tests conducted on the system.
The **Auto Verify** subpage displays configurable Auto Verify parameters.
The **Auto Restore** subpage allows Auto Restore configuration.

The following describes the usage of DVB. As **DVB, DAB and FM have the same page/subpage layout.**, DAB and FM's usage will follow DVB.

The **DVB** page shows configurable DVB parameters.
The subpages that it contains [**Main TX (DVB)**, **Reserve TX (DVB)**, **TX A (DVB)**, **TX B (DVB)**] displays configurable DVB parameters for Main TX, Reserve TX, TX A and TX B.

The **DVB Events** page allows you to enable/disable trap generation.
The subpages that it contains [**Main TX Events (DVB)**, **Reserve TX Events (DVB)**, **TX A Events (DVB)**, **TX B Events (DVB)**] displays configurable DVB trap generation for Main TX, Reserve TX, TX A and TX B.

The **DVB Event Priority** page allows you to set trap priority.
The subpages that it contains [**Main TX Event Priority (DVB)**, **Reserve TX Event Priority (DVB)**, **TX A Event Priority (DVB)**, **TX B Event Priority (DVB)**] allows you to set DVB trap priority for Main TX, Reserve TX, TX A and TX B.