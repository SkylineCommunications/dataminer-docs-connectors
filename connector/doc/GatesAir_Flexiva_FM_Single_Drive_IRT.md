---
uid: Connector_help_GatesAir_Flexiva_FM_Single_Drive_IRT
---

# GatesAir Flexiva FM Single Drive IRT

The GatesAir Flexiva FM Single Drive IRT is a redundant FM transmission system. This connector can be used to monitor this system. The connector has a page with general information and two pop-up pages for the configuration of traps. The connector uses SNMP to retrieve and configure data.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

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

The **General** page displays the **Transmitter** status, **Pr‚sence RF**, **Local Mode**, **Faute** (Fault Status) and **Warning** status, etc. Use the **Refresh Table** button to trigger the immediate polling of these parameters. Some information is bundled in the **Table Service**. You can also define a **Description** for the single table entry.

There is a page button that will display the **Trap** **configuration** for each of the previously mentioned parameters. As these parameters are not polled automatically, use the **Refresh Traps** button to update them.

A second page button displays the **Trap Handler** subpage, which allows you to enable or disable **Trap Handling** and to set the **Trap Delta**.

Note: A received trap will only trigger a parameter update if **Trap Handling** is enabled and the difference between the trap event counter and the previous trap event counter is more than the value of the **Trap Delta** parameter.

The **Status** page displays a variety of parameters concerning the **Drive**, **Exciter**, **Transmitter**, **Output**, **System**, **Power Supply**, and **Power Amplifier.** Use the **Refresh** button to trigger the immediate polling of these parameters.

The Status page also contains a page button that displays the **Status Traps Configuration** for some of the previously mentioned parameters.
