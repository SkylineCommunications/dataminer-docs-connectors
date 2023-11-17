---
uid: Connector_help_GatesAir_Maxiva_XTE_MSC2
---

# GatesAir Maxiva XTE MSC2

The GatesAir Maxiva XTE Multi-System Controller (MSC2) monitors and controls transmitter systems and controls RF switching. The MSC2 supports a range of backup options, including 1+1, full N+1, and dual-transmitter installations.

This connector monitors the activity of the GatesAir Maxiva XTE MSC2 device.

## About

### Version Info

| Range              | Key Features                     | Based on | System Impact |
|--------------------|----------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version.                 | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

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

- The connector will work for both 1+1 and n+1 systems. As both of them are mutually exclusive from one another, only one system type will be polled and displayed at any time.

- The **General** page allows the user to toggle **page visibility and polling** between 1+1 and n+1. It also displays common information between 1+1 and n+1 about the system.

### 1+1

- The **1+1 System Info** page displays information about the 1+1 system such as the **Controller Status**, the **Switch State**, and the **Control State**. On the **Configuration** subpage, you can configure the **system parameters** and enable the **controller events**.

- On the **Transmitter A/B** page, you can check the current status of the **Alarm** parameters and the current values of transmission parameters like the **Frequency**, **Power**, and **VSWR**. On the **Events** and **Configuration** subpages, you can set the transmitter definition parameters.

### N+1

- The **n+1 System Info** page displays information about the n+1 system such as the **Controller Status**, the **Switch State**, and the **Control State**. On the **n+1 Configuration** subpage, you can configure the **system parameters** and enable the **controller events**.

- On the **Main Transmitter** page, you can see configurable general info on the main transmitters.

  - The **Main TX Status** subpage shows status information for the transmitters.

  - The **Main TX Events** subpage allows you to enable/disable trap generation.

  - The **Main TX Auto Restore** subpage contains configurable auto-restore parameters.

- The **Reserve Transmitter** page shows status and measurement parameters for the reserve transmitter.

  - The **Reserve TX Configuration** subpage allows you to set reserve TX parameters.

  - The **Reserve TX Trap Events** subpage allows you to enable/disable trap generation.

- The **Input Switch** page contains configurable input switch parameters.

- The **Failed Verifications** page shows parameters related to tests conducted on the system.

  - The **Auto Verify** subpage contains configurable auto-verification parameters.

  - The **Auto Restore** subpage allows you to configure auto-restore settings.

- The **DVB** page contains configurable DVB parameters. Its subpages contain configurable DVB parameters for Main TX, Reserve TX, TX A, and TX B.

- The **DVB Events** page allows you to enable/disable trap generation. Its subpages contain configurable DVB trap generation parameters for Main TX, Reserve TX, TX A, and TX B.

- The **DVB Event Priority** page allows you to set trap priority. Its subpages allow you to set DVB trap priority for Main TX, Reserve TX, TX A, and TX B.

- The pages and subpages for **DAB** and **FM** are very similar to the DVB pages mentioned above.